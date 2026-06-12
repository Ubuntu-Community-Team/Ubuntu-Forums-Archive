---
title: "[SOLVED] XP &amp;amp; Ubuntu Dual-Boot problem"
date: 2008-01-13
forum: General Help
---

### Post by alexkillen on 2008-01-13
I know this topic has a number of threads going but I after reading a number of these I still can't fix my problem.

- I had a PC with 1 hdd and XP Home installed.
- I installed a 2nd hdd and installed ubuntu 7.10 on it

Everything worked fine until I tried to boot up XP from the GRUB menu, which gave me an "NTOSKRNL.exe file is missing or corrupt" error.

After much searching through forums i got the solution which was to use the XP install cd, enter recovery mode and then run "bootcfg /rebuild" and select the XP OS. 

This worked.  However when I next booted up into Ubuntu, and then after tried to boot into XP I got the same error.

My problem now is that while "bootcfg /rebuild" fixes the problem, booting into Ubuntu brings it right back again.

Any help would be greatly appreciated, also I am a complete Linux noob so please keep answers clear. Thanks.

---

### Post by Sef on 2008-01-13
Read this from [Computer Hope's site]("http://www.computerhope.com/issues/ch000646.htm").

---

### Post by alexkillen on 2008-01-16
I got it in the end. I just reinstalled GRUB and changed the menu.lst file so that that windows entry had the **rootnoverify** keyword instead of **root**. I can't remember where I found the fixes, but if whoever posted them reads this then thanks.

---

