---
title: "c compiler for ubuntu?"
date: 2007-07-13
forum: General Help
---

### Post by aalr1986 on 2007-07-13
I downloaded a couple of C compilers for Ubuntu, and well, I don't really know what to do with them, cause they don't appear on the apps section, in my main menu.

how do I use them?!!?!?

(i'm in Kubuntu Feisty Fawn)

---

### Post by tribaal on 2007-07-13
Easy enough:

Just install the "build-essential" package (sudo aptitude install build-essential).
Then you'll have the GNU C/C++ compiler installed (gcc)

Hope this helps!

- trib'

---

### Post by scxtt on 2007-07-13
what did you download?  not all of them are GUI apps - like gcc for example is a CLI compiler ...

---

### Post by aalr1986 on 2007-07-13
I did download the GCC compiler, but like, it doesn't appear anywhere, and I don't know how to use it. It is installed, but what do I do, if it doesn't appear in my main menu?

---

### Post by Ex-Cyber on 2007-07-13
The compiler itself is only responsible for consuming source code and generating an executable program. Usually it is indirectly invoked from a terminal through the "make" program, which processes "makefiles" that describe how to compile the various parts of the program. Some developers use tools to generate makefiles, and some simply write them by hand. For the simplest programs (like those found in the early portions of C tutorials), the compiler is sometimes invoked directly like so:

```
gcc -o myprogram myprogram.c
```

 If you want a full-blown graphical development environment you'll have to install one separately. One example of a popular KDE development environment is KDevelop, but I've never used it and so can't offer an opinion on it.

---

