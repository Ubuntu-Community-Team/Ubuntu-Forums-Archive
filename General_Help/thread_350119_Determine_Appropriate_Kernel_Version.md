---
title: "Determine Appropriate Kernel Version"
date: 2007-01-31
forum: General Help
---

### Post by jamieballin on 2007-01-31
Hi,

I installed Kubuntu on a Pentium4 32-bit machine, and it uses the i386 kernel architecture. How can I check which architecture I should be using? A friend suggested looking in /proc/config, but that doesn't exist (presumably because I'm not in the business of compiling kernels!).

Thanks!

---

### Post by NiceGuyUK on 2007-01-31
A Pentium 4 should easily cope with the i686 version.  i386 kernel will always work for you as it is a "catch-all" for all Intel architectures (32 bit), but you'll get better performance out of i686

---

