---
title: "GCC compiler"
date: 2007-12-17
forum: General Help
---

### Post by 7raTEYdCql on 2007-12-17
I need a GCC compiler for my ubuntu.

And i do not understand something.
What is the difference between the package manager and the add or remove program list.
Can i download from the package manager and the add or remove program lists.
Which one should i download from.

---

### Post by yabbadabbadont on 2007-12-17
You can use either one.  They are just two different graphical interfaces to the command line package manager that does the real work behind the scenes.  :)

By the way, the package that you probably want to install is called "build-essential".  It contains the most frequently needed/used command line tools for C and C++ development in Linux.

---

### Post by Aseld on 2007-12-17
The package manager offers more control, while some find Add/Remove Programs easier. To install gcc and all that's needed to compile programs:

```
sudo aptitude install build-essential
```

---

