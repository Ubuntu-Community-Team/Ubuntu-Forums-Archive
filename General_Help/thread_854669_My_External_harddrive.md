---
title: "My External harddrive"
date: 2008-07-09
forum: General Help
---

### Post by krooked on 2008-07-09
First thing i feel i should say is i have spent the past 4 hours searching the net and forums to see if i can fix this (as well as a few hours over the past 3 days), im sorry if its obvious for someone else.

What i have so far is i run sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefda485e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36241   291105801   83  Linux
/dev/sdb2           36242       36483     1943865   82  Linux swap / Solaris

The ntfs External drive when i boot (i use it on this ubuntu-only pc via Esata, as well as a XP laptop via usb) usually will either give me a "not proper permissions" or a "unproperly connected" error. I then will either force mount or standard mount. 

My question is depending on when its plugged in, during bootup, or after, and whether i have another drive hooked up it sometimes takes on Sda, Sdb, Sdc and so on. i have seen modification commands to edit the fstab for an auto-mount for the drive, but the command
/dev/sda1 /media/sda1 ntfs ro,users,noauto,uid=1000,gid=1000 0 0
is assuming it will always take the form of sda1. is there a way i can reserve a directory spot for this drive always, or a way to just grant my user login permissions to mount an ntfs and i can just right click and mount it upon startup?

---

