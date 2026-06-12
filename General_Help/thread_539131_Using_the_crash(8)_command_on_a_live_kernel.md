---
title: "Using the crash(8) command on a live kernel"
date: 2007-08-30
forum: General Help
---

### Post by Steve_Pate on 2007-08-30
Has anyone got this to work? I have:

  $ uname -r
  2.6.20-16-generic

and I installed the following:

  $ sudo apt-get install linux-image-debug-2.6.20-16-generic

But when I run up crash, it complains that there is a mismatch between the debug kernel and the running kernel:

  $ sudo crash  /boot/System.map-2.6.20-16-generic  /boot/vmlinux-dbg-2.6.20-16-generic 
  ...
  blah blah
  ...
  crash: /boot/System.map-2.6.20-16-generic and /dev/mem do not match!

Anyone got any ideas?

---

### Post by precek on 2007-10-05
got the same problem.

---

