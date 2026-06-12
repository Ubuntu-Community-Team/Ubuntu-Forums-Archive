---
title: "[SOLVED] Compile problem - Someone educate me please!"
date: 2008-04-16
forum: General Help
---

### Post by nowhere@cox.net on 2008-04-16
Hi!
I have 7.10 i386 installed and I am compiling a pgm call uif2iso. It compiles fine without errors using make and make install. However, when I run it on a 1.3GB uif file, I get an  invalid argument error and if I run it on a 2.9GB file I get an error concerning LARGE_FILES not supported in my exe. 

The source came with a Win exe file precompiled. When I run it using Wine it works fine for both files so I KNOW I am not compiling it correctly or something is goofy with my system.

I have attached the source for the pgm. I was hoping some c experts could have a look and let me know if there is some kind of flag I need to set to get it to compile and work.

Thanks,
Eri

---

### Post by nowhere@cox.net on 2008-04-16
The author wrote me and provided a solution. For anyone else trying to use this pgm:
in uif2iso.c, replace
```
    #if defined(__MINGW32__)
```
with
```
    #if !defined(__MINGW32__)
```

there is only one line in the source code which is like that.

Unfortunately, it seems that some OS's must be forced to use the 64 bit file support.

Thanks Luigi!

Eric

---

### Post by groe0286 on 2008-04-27
This worked for me too, I'm also using Ubuntu 7.10!!! Thanks a lot!

---

