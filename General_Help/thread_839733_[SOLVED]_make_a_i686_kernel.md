---
title: "[SOLVED] make a i686 kernel?"
date: 2008-06-24
forum: General Help
---

### Post by MDSmith2 on 2008-06-24
Hello, Iwas reading around and wondering how to make a 686 kernel because all the tutorials (mainly lfs) say after you make the kernel, it will be in /arch/i386 or whatever arch you use but i can't find out how to choose other arches.
thanks

---

### Post by Habbit on 2008-06-24
Why do you want to choose another arch? i686 is a "machine type" inside the i386 architecture (in fact, it was recently merged with amd64 into x86, but you can still access arch/i386). The "i686" differences are applied when you select "processor type and subtype" in the kernel configuration and, in order to choose some faster code that wouldn't work on the i386 (for example, the INVLPG and CPUID instructions appeared on the 486) and to enable compiler optimizations for later processors (-march and/or -mtune).

---

### Post by MDSmith2 on 2008-06-24
thanks i got it from the lfs irc.

---

