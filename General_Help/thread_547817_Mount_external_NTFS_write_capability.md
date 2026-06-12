---
title: "Mount external NTFS write capability"
date: 2007-09-10
forum: General Help
---

### Post by stchman on 2007-09-10
Hello all, 

I have a 120GB NTFS formatted external hdd.  I know that you can use the ntfs-3g in your fstab to mount NTFS partitions for read/write.

My problem is that I have the ntfs-3g package installed but when I insert the NTFS formatted hdd Ubuntu mounts the drive as read only.

How do I tell Ubuntu to mount the external hdd as read/write?  I don't want to have to edit the fstab file each time.  

If this cannot be done easily I will just copy the data off of the drive and format it as either EXT3 or FAT32.

---

### Post by logos34 on 2007-09-10
use the gui configuration tool--it will edit fstab for you so that it automounts with write support:

**sudo apt-get install ntfs-config**
[B]
gksudo ntfs-config[/B]

>enable write support external device

---

