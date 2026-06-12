---
title: "[SOLVED] Error message at installing lx split"
date: 2008-07-02
forum: General Help
---

### Post by arashiko28 on 2008-07-02
Lx split is the Linux version of the Hj split of windows. It is supposed to be installed just by tiyping make and make install. but on make, I get this error: > :~/lxsplit-0.1.1$ make
gcc -c -W -O2 -DNO_DEBUG  -o func.o func.c
func.c:1:20: error: stdlib.h: No such file or directory
func.c:2:20: error: unistd.h: No such file or directory
func.c:3:19: error: stdio.h: No such file or directory
func.c: In function &#8216;strip_path&#8217;:
func.c:13: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
func.c:22: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
func.c: In function &#8216;shorten_path&#8217;:
func.c:41: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
func.c:44: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
make: *** [func.o] Error 1


What's missing or doing wrong?

SOLVED! found .deb package googling :)

---

