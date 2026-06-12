---
title: "C++ Compiler for using XMGrace"
date: 2008-06-20
forum: General Help
---

### Post by mehak07 on 2008-06-20
Hello,
I need to use the program XMGrace on ubuntu. and I need to set up C++ compiler. I am new to ubuntu and am completely unaware as to how to set up a C++ compiler on Ubuntu 8.04.

---

### Post by Rocket2DMn on 2008-06-21
To properly install the compiler, you need to install the metapackage build-essential which comes with a bunch of compilers and libraries for compiling a bunch of different types of code.  Get it by running
```
sudo apt-get install build-essential
```
It includes gcc and g++.

---

