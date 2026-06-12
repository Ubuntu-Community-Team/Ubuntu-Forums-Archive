---
title: "NTFS-3G Issue"
date: 2007-06-15
forum: General Help
---

### Post by tkaplan1983 on 2007-06-15
Hey all,

I have a Internal IDE 260GB WD drive.  It is currently mounted through Ubuntu 7.04.  Right now the way I can get to it is via /media/Local Disk.  However I want to mount it so I can read/write/execute.  So I downloaded and installed NTFS-3G and it installed without any issues.

So I tried their command:
tkaplan@pirate:~$ sudo mount -t ntfs-3g /dev/hdb1 /mnt/data
fusermount: failed to access mountpoint /mnt/data: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 (Local Disk)

and thats the errors im getting.  If anyone can help me out that would be grrrreat.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   488397167   244198552+   7  HPFS/NTFS

---

### Post by tkaplan1983 on 2007-06-15
Actually I figured it out and if anyone else get this problem this is how to fix it.  Check the disk in your GUI and right click it and click unmount.  Then retry mounting it and it should work.

---

