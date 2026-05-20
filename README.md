# From Zero to GenLayer: An Introductory GenLayer Tutorial

**دليل شامل للمبتدئين لإنشاء أول Intelligent Contract على GenLayer**

![GenLayer](https://genlayer.com/logo.png) <!-- غيرها برابط صورة أفضل لاحقاً -->

## 📋 ما ستتعلمه في هذا الـ Tutorial

- مفهوم **Intelligent Contracts** و GenLayer
- تثبيت GenLayer Studio + CLI
- كتابة Intelligent Contract بـ **Python**
- نشر الـ Contract واختباره
- فهم **Optimistic Democracy Consensus** و **Equivalence Principle**
- ربط الـ Contract بـ Frontend (genlayer-js)

## 🛠️ المتطلبات

- Docker (v26 أو أحدث)
- Node.js (للـ CLI)
- GenLayer Studio (موصى به)

## 🚀 الخطوات

### Step 1: تشغيل GenLayer Studio
افتح [GenLayer Studio](https://studio.genlayer.com) في المتصفح.

### Step 2: Intelligent Contract (Hello World)

أنشئ ملف `contracts/HelloWorld.py` وضع فيه الكود التالي:

```python
# { "Depends": "py-genlayer:1jb45aa8ynh2a9c9xn3b7qqh8sm5q93hwfp7jqmwsfhh8jpz09h6" }

from genlayer import *

class HelloWorld(gl.Contract):
    greeting: str

    def __init__(self):
        self.greeting = "Hello, GenLayer! مرحبا بك في عصر Intelligent Contracts 🚀"

    @gl.public.view
    def get_greeting(self) -> str:
        return self.greeting

    @gl.public.write
    def set_greeting(self, new_greeting: str):
        old = self.greeting
        self.greeting = new_greeting
        print(f"✅ Changed greeting from '{old}' to '{new_greeting}'")

    @gl.public.write
    def print_greeting(self):
        print("📢 Current greeting:", self.greeting)
