---
title: "Cross-compiling for Windows in Edgy"
date: 2007-03-28
forum: General Help
---

### Post by Commodore Guff on 2007-03-28
I maintain the Windows port of a certain GIMP plug-in, but my Windows installation is currently in a very bad mood, so I'm out of luck on that front.  However, I've heard that it's possible to cross-compile, but couldn't find much.  Anyone able to help?

---

### Post by lamego on 2007-03-28
Try reading this
[http://www.kegel.com/crosstool/crosstool-0.43/doc/crosstool-howto.html](http://www.kegel.com/crosstool/crosstool-0.43/doc/crosstool-howto.html)

---

### Post by Commodore Guff on 2007-03-28
> **lamego said:**
> Try reading this
[http://www.kegel.com/crosstool/crosstool-0.43/doc/crosstool-howto.html](http://www.kegel.com/crosstool/crosstool-0.43/doc/crosstool-howto.html)

Thanks, but, erm, I'm not really sure how to use any of that. :confused:

---

### Post by Commodore Guff on 2007-03-29
Anyone?

---

### Post by WW on 2007-03-29
**mingw32** is a cross-compiler that can compile in Linux for a Windows target.  Get the packages **mingw32**, **mingw32-binutils**, and **mingw32-runtime**.  For example,
```

sudo apt-get install mingw32 mingw32-binutils mingw32-runtime

```
On my x86 computer, the commands provided by these packages begin with **i586-mingw32-msvc-**.  For example, the C cross-compiler is **i586-mingw32msvc-gcc**.

Suppose you have this file:
```

/* hello.c */

#include <stdio.h>

main()
{
    printf("Hello, world!\n");
}

```
You can compile and run it in linux like this:
```

$ i586-mingw32msvc-gcc hello.c -o hello.exe
$ wine hello.exe
Hello, world!
$

```
Note that I used **wine** to run the program.

(Note: I am running dapper; I assume this will also work in edgy.)

---

### Post by Commodore Guff on 2007-03-29
Thank you, WW.  I had gotten the packages, but had no idea how to use them.

I'll have to try it out later, but I'm pretty sure it'll work.

---

