---
title: "Unexpected shutdown and data loss"
date: 2008-02-28
forum: General Help
---

### Post by cadillacman on 2008-02-28
System has been fine ( sorta ) for 2 months. Sometimes the system will freeze ... absolute stop, then it reboots on it's own, fine most of the time. My Win2K will do this sometimes too ...so there is likely a hardware problem. 

HOWEVER ...TWICE now, there has been a major data loss. When ubunbto rebooted it 'reverted' ( sorry, best term I can imagine ) to a previous 'state'. That is, the desktop settings were as of 7 weeks ago, and any and all data, downloaded or created was GONE. That included 2000 e-mails the second time it happened. Software installs were gone, but system changes and updates seemed to be intact.

Really odd... was that the second time this happened, it performed the reboot again within 10 minutes and then all the data that was missing re-appeared. Settings, software, downloads, emails .... all where I thought they should be.

So ... cause issues aside ... I'm interested in any ideas as to where the data 'went' and why/how to recover if it doesn't magically re-appear on it's own.

---

### Post by pointone on 2008-02-29
Are you using a separate/shared home partition?

---

### Post by cadillacman on 2008-02-29
1 home dir - permissions are drwxr-xr-x
1 subfolder 'mine' ( home icon ) permissions same as above

I am the only user on the system
There is only 1 partition, and the swap on the drive

I'm sensing that a separate folder might have existed  ? or still does ? where the other settings and data are located ?

---

### Post by pointone on 2008-02-29
Post the output of "cat /etc/fstab" and "sudo fdisk -l".

---

### Post by cadillacman on 2008-02-29
Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0a64543
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1044     8385898+  82  Linux swap / Solaris
/dev/sdb2            1045       24321   186972502+  83  Linux

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce3f7b47
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1044     8385898+  82  Linux swap / Solaris
/dev/sdc2            1045       24321   186972502+  83  Linux

2 Drives The second one is an 'old' NortonGost backup of the first .. supose that one is started up on those odd times !!!!?

---

### Post by cadillacman on 2008-02-29
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdc        /media/sdc      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by pointone on 2008-02-29
Very strange. I'm at a loss here besides a failing hard drive, or some user error (were you messing around with permissions on your home folder, for example?)

---

### Post by cadillacman on 2008-03-03
I thank you much for the insight. I think you pointed me in the right direction with the fstab query.

This motherboard has a sporadic fault , where the drive ID's as know by the bios get lost after the OS has booted up. Sounds strange but I've see my Win2K do this and stay running, except it could not find drives it had already mapped. My paging file is always on a separate HD from my OS, and suddenly it would be 'non-existant'

At times Win2K seizes, now instead ... and I think it's because it can't handle having a linux drive substituted for something it was expecting was NTFS.

If I restart ububto on the 'other drive' it of corse starts on the good drive because the grub is edited to all the correct mounts, when I ghosted. But if the BIOS is screwy, then it would point to the incorrect one.

I've re-ghosted .... with an intentionally different visual setup to test my theory.
Time will tell me.
Thanks for your time

---

