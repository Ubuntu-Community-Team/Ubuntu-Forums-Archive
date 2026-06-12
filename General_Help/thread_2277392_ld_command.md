---
title: "ld command"
date: 2015-05-08
forum: General Help
---

### Post by Omar_BEDDALI on 2015-05-08
How does linux ld command deals with  functions defined in include files ?

---

### Post by QIII on 2015-05-08
Moved to General Help.

The Resolution Center is for general Forum Administrative issues such as name changes, resolution of moderation errors, account queries, etc.

---

### Post by Holger_Gehrke on 2015-05-08
It doesn't. 'ld' is the linker, it takes various object files and / or libraries and produces an executable (or a library). Include files are used by the compiler, depending on language they are either compiled into (part of) the object files or reference functions defined in a library.
For details see 'man ld' and 'info ld'.

---

### Post by Omar_BEDDALI on 2015-05-08
Let me be more precise. I used cc -c to compile separately a certain number of modules, some of them containing the 2 functions printf() and scanf() that where included  by #include <stdio.h>. After that I obtained the same number of .o modules which I linked together with cc -o. All was right. The trouble took place when I tried to replace the second step of the job (cc -o) by the command ld which I supposed ,like you, will find that the compiler has done his part by including the functions  printf and scanf. It did not. ld signaled that printf and scanf where  undefined.

---

### Post by Holger_Gehrke on 2015-05-08
Most of the basic functions of C are defined in libc (and referenced by various header files), so you need to tell the linker to use that library; the option -lc (-l**foo**: link library lib**foo**.so or lib**foo**.a in the standard library directories) should get you at least one step closer to your goal.

---

### Post by Omar_BEDDALI on 2015-05-09
Thanks Holger_Gehreke.

---

