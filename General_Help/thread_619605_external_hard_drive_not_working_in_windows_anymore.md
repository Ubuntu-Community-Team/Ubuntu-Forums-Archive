---
title: "external hard drive not working in windows anymore but works in ubuntu fine"
date: 2007-11-21
forum: General Help
---

### Post by 244f on 2007-11-21
i have an external USB drive that is formatted in ntfs, i installed ubuntu recently and have been using it, but dualboot into windows also.
the external does not work in windows anymore, i got an error saying the file system is corrupt and the directory unaccessible.. but when i log into ubuntu, the hard drive works fine.
whats the deal? :confused:

---

### Post by piotrwoj on 2007-11-21
> **244f said:**
> i have an external USB drive that is formatted in ntfs, i installed ubuntu recently and have been using it, but dualboot into windows also.
the external does not work in windows anymore, i got an error saying the file system is corrupt and the directory unaccessible.. but when i log into ubuntu, the hard drive works fine.
whats the deal? :confused:
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.
What shows fdisk -l ?
-----------------------------
[Meble dla Dzieci](http://www.spok.pl/)

---

### Post by 244f on 2007-11-21
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedb03fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS



i opened up gparted and theres a warning symbol next to the drive, i click information and it says warning: unable to read the contents of the file system!

i don't get whats going on :[

---

### Post by 244f on 2007-11-21
I fixed it.

i went into windows, opened up command prompt and did chkdsk e: /f   where e is the external drive
it repaired the file system and it is working now
hurrah!

---

