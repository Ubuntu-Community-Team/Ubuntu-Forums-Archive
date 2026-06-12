---
title: "install and configure GTK+ library to make GUI application in C"
date: 2013-12-23
forum: General Help
---

### Post by aditya.mahesh.shar on 2013-12-23
Hi,  I am using ubuntu 12.04 .
I want to build a Graphic application using GTK library. Can some help me how can I install and configure GTK on my ubuntu and compile my programs successfully using gcc.

---

### Post by steeldriver on 2013-12-23
Hello and welcome to the forums

You should be able to get everything you need to get started by installing the **libgtk2.0-dev** meta package (or for version 3, libgtk-3-dev)

After that, you should be able to compile your code using the pkg-config utility to generate all the necessary include and libs e.g.

```
gcc *yourprog*.c -o *yourprog* `pkg-config --cflags --libs gtk+-2.0`
```

There is an online tutorial (with example programs) here --> [https://developer.gnome.org/gtk-tutorial/stable/](https://developer.gnome.org/gtk-tutorial/stable/)

---

