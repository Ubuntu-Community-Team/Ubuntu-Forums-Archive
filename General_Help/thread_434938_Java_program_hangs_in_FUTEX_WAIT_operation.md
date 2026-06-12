---
title: "Java program hangs in FUTEX_WAIT operation"
date: 2007-05-06
forum: General Help
---

### Post by boekhold on 2007-05-06
Hi all,

I have a java program that hangs on Ubuntu 7.04 Feisty Fawn. When I do 
an strace -p pid I can see it is stuck on a futex(..., FUTEX_WAIT,...) 
operation. I have seen a similar error reported on:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107012](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107012)

I can't be sure that this is the same issue (would I be able to verify 
this somehow?), but it sure looks the same.

This is on an i386 ubuntu, P4 with HT enabled, using the 'standard' 
ubuntu generic & i386 kernels, and also with a 2.6.21.1 kernel custom 
compiled. Java version is 1.5.0 from Sun.

I haven't tried this same program on 6.xx yet (having some disk space 
issues), but the same program works fine on both Windows XP sp2 and 
Solaris 2.8. Other java programs (and I've only tried a few) work 
without problems on 7.04 using the same JRE version.

Any ideas?

Regards, Maarten

---

### Post by boekhold on 2007-05-07
Hi all,

I've re-installed my system with Ubuntu 6.06, and now this Java application is working correctly.

I'm up and running for the moment, but still interested in how I could get this running on 7.04, as I'd really like to keep working with Feisty.

Maarten

---

