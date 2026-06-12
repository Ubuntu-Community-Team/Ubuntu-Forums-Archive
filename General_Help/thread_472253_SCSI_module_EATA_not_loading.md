---
title: "SCSI module EATA not loading"
date: 2007-06-12
forum: General Help
---

### Post by airblade on 2007-06-12
Hi!
I'm trying to install Ubuntu 7.04 on a old server with SCSI disks.

The installation goes smoothly, but stops when no disks are found. From here, i manually select the EATA driver, witch works perfectly. Generally; no problems.

When the new installation is starting up, it does not find my hard drives and loads Busybox.
After checking out /proc/modules, i find that the EATA module is not loaded at all, witch causes the disks not to be recognized.
Of course, if i load the eata module manually (insmod eata, or modprobe eata) the disks work. 

I have checked /etc/modules, witch contained eata, but does not load it.
I have updated the installation to the latest kernel (2.6.20-16), but with no luck.

WHY doesn't it load the eata module automatically?
Any ideas? 

--
This error is similar to this:
[http://ubuntuforums.org/showthread.php?t=327684](http://ubuntuforums.org/showthread.php?t=327684)

---

### Post by airblade on 2007-06-14
More info here: [http://bugs.launchpad.net/ubuntu/+bug/120426](http://bugs.launchpad.net/ubuntu/+bug/120426)

---

