---
title: "How to step through rcS.d on startup?"
date: 2006-09-01
forum: General Help
---

### Post by ultralame on 2006-09-01
I believe I am having a networking problem related to something in rcS.d.

What I would like to do is boot into the bare minium single-user system and then manually run the scripts in rcS.d.  It does not help to boot into single-user, because the rcS scripts have already run.

Is this possible?
What's the best way?  (I would rather not edit rcS.d unless that's what is required).

---

### Post by pgreening on 2008-01-02
You may want to use init=/bin/bash as a kernel parameter.  this may drop you to a shell a little earlier than you want, but by reading /etc/inittab*(see note) you should be able to get to where you want. 
to use init=/bin/bash, interupt the grub boot process and append init=/bin/bash to the kernel command string, then continue booting.  you may want to remove the splash and quiet options if they are there.  This change is not persistant across boots.

*Note, ubuntu uses upstart by default, which does not use an /etc/inittab file so your system may not have this file to explain what its doing durring startup.  Also, I've seen upstart cause problems, so installing sysv-init may solve your issue.  On the other hand, changing stuff on an already  misbehaving box may not be the best idea.
good luck!

---

