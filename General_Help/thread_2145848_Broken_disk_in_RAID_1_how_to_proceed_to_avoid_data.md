---
title: "Broken disk in RAID 1: how to proceed to avoid data loss?"
date: 2013-05-16
forum: General Help
---

### Post by dodiko on 2013-05-16
Some days ago Ubuntu (12.04) notified me that 1 of the 2 disks in my raid 1 array was failing. Yesterday, I removed the failing disk for a warranty shipment. Next, I tried to boot Ubuntu with only 1 disk as I thought Ubuntu would only warn me that my raid setup was not working. Instead, it first complained libgcrypt could not find /dev/md-3 and then it failed to mount /var and /home (/ is on a separate SSD). If I run dmraid -s it shows this error:  ERROR: isw: wrong number of devices in RAID set "isw.... on /dev/sdb" status: inconsistent  As I did not expect Ubuntu to break by degrading the RAID setup, I did not made backups of all my recent data. Thus, I tried to connect the failing disk again and reboot to make the backups before warranty shipping the failing disk. However, the BIOS added a rebuild status to my RAID setup, telling my operating system will rebuild the array. Ubuntu still did not boot and no rebuild was started (I assume because the disk is broken?)  1) Is this a known bug in Ubuntu 12.04 and is this fixed in a later release? (if a RAID 1 setup is degraded, Ubuntu should still mount the drive that is left)  2) Is it actually possibly to mount a degraded Raid 1? Does a howto exist?  3) [most important] Does a straightforward guide exist to recover from a degraded RAID 1 setup? For sure, I do not want to risk any data loss. Or will Ubuntu automatically start rebuilding the array when a new empty disk is added without me needing to do the hard work? (I hope this part of RAID support is already conforming the the Ubuntu philosophy of userfriendlyness)  Thqnks for the helpful replies!

---

### Post by dragonfly41 on 2013-05-17
Testdisk might help you in data recovery.

Here is one cgsecurity  thread on Raid0 recovery but in your case you'll have to read up more on Raid1 recovery tools.  
Some are listed in this thread.

[http://forum.cgsecurity.org/phpBB3/recovering-raid0-t1404.html](http://forum.cgsecurity.org/phpBB3/recovering-raid0-t1404.html)

---

