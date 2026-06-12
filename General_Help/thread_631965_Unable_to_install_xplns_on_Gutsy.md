---
title: "Unable to install xplns on Gutsy"
date: 2007-12-05
forum: General Help
---

### Post by sierra_bravo on 2007-12-05
Hi
I was trying to install my old favorite astronomy program, xplns (which is only available in binary format). I am getting the following dependencies. Is there any way that I can fix these dependencies from within Gutsy?

TIA

s.b.

-----------------
$ sudo rpm -ivh xplns-3.3.1-1glibc21.i386.rpm 
error: Failed dependencies:
        /bin/sh is needed by xplns-3.3.1-1glibc21.i386
        ld-linux.so.2 is needed by xplns-3.3.1-1glibc21.i386
        libICE.so.6 is needed by xplns-3.3.1-1glibc21.i386
        libSM.so.6 is needed by xplns-3.3.1-1glibc21.i386
        libX11.so.6 is needed by xplns-3.3.1-1glibc21.i386
        libXext.so.6 is needed by xplns-3.3.1-1glibc21.i386
        libXp.so.6 is needed by xplns-3.3.1-1glibc21.i386
        libXt.so.6 is needed by xplns-3.3.1-1glibc21.i386
        libc.so.6 is needed by xplns-3.3.1-1glibc21.i386
        libm.so.6 is needed by xplns-3.3.1-1glibc21.i386
        libc.so.6(GLIBC_2.0) is needed by xplns-3.3.1-1glibc21.i386
        libc.so.6(GLIBC_2.1) is needed by xplns-3.3.1-1glibc21.i386

---

