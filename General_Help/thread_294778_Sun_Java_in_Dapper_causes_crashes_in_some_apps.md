---
title: "Sun Java in Dapper causes crashes in some apps"
date: 2006-11-07
forum: General Help
---

### Post by softgun on 2006-11-07
SUn java in dapper does not run some applications that run in the same sun java package in Breezy. The application crashes.

SUn java was installed with a deb and then set to become default.

When it was installed through the repositories in Dapper, same problem.


Any clues why not?
Here is part of the erroe message when the application crashes.

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0cb4bcd, pid=7965, tid=2961324976
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ebcd]
#


---------------  S Y S T E M  ---------------

OS:testing/unstable

uname:Linux 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
libc:glibc 2.3.6 NPTL 2.3.6 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.84 0.53 0.47

CPU:total 1 family 6, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 507116k(10948k free), swap 2048248k(2029132k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_06-b05) for linux-x86, built on Nov 10 2005 12:08:33 by java_re with gcc 3.2.1-7a (J2SE release)

---

