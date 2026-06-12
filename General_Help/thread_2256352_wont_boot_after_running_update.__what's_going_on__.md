---
title: "wont boot after running update.  what's going on?  is there a fix for it?"
date: 2014-12-11
forum: General Help
---

### Post by pretty_whistle on 2014-12-11
I have Ubuntu 14.04 LTS.

I just ran an update and it found kernel headers so I installed it.  After reboot, the computer wouldn't load the desktop.  It stalled right after the login screen.

To fix it I had to restore a backup I had.

This is the second time in about 9 months that it wouldn't load the desktop after running an update for kernel headers.  What's up with that anyway?  Don't they check these updates before offering it to people??  (that's rhetorical by the way).

In any case, now I can't run updates anymore for fear of getting the bad kernel again unless anyone ran another update and got a fix for it........  Anyone?

---

### Post by nerdtron on 2014-12-11
For me, mostly I ran all software updates except the kernel headers. Kernel updates can be problematic when you run programs that alter the kernel or requie specific kernel modules like the proprietary video drivers.

---

### Post by ajgreeny on 2014-12-11
I am lucky/unlucky (you choose), as I have the intel integrated graphics only on my system which use the open source drivers and as a result I have never had any problems with kernel updates since I started using Ubuntu at version 5.04.

There are other ways round your problem with graphic drivers either using the command line or trying recovery mode with the low graphics mode GUI in that, and installing the proprietary driver from there.

---

