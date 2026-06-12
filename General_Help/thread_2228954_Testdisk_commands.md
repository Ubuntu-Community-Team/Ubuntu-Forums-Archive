---
title: "Testdisk commands"
date: 2014-06-10
forum: General Help
---

### Post by tommy2k10 on 2014-06-10
First of all, apologies if this is in the wrong thread.
I am using Testdisk (from a System Rescue CD) to recover data from a laptop with a failing hard drive.  The HDD is on sda1, and my external drive is on sdb1.
Testdisk found 368 files on the hard drive, and I have tried to copy them to my external drive with no luck. (I have checked and they are not there!)
I have mounted windows as mount /dev/sda1 /win -t ntfs
and my external drive as mount /dev/sdb1 /usb -t ntfs-3g (as I want to write to it as well).
Firstly, is /usb -t ntfs-3g the right command?
Secondly, on the list of target folders, which folder do I choose to save the files in: /dev/sdb or /dev/sdb1?

---

