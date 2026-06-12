---
title: "[SOLVED] Partition Help, Again."
date: 2008-04-26
forum: General Help
---

### Post by tad1073 on 2008-04-26
I am back to square one. I did a fresh install of 7.10 and by mistake I created the mount point for sdc1 as media so I changed the mount point in fstab to /sdc1 the drive isn't anywhere to found.

```
:~$ sudo cat /etc/fstab
[sudo] password for thomas: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c39b7fd3-8030-43e6-801b-4d6e517db65d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=aef133ab-8491-4fa7-885d-e265b0eb4428 /home           ext3    defaults        0       2
# /dev/sdc1
UUID=0627eb73-1e93-4d49-9cbf-fb9f53125a08 /sdc1          ext3    defaults        0       2
# /dev/sda1
UUID=a90836c0-e6a6-4764-80fb-8372f0e4ad44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
:~$ sudo fdisk -l

Disk /dev/sda: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     2000061   82  Linux swap / Solaris
/dev/sda2   *         250        1106     6883852+  83  Linux

Disk /dev/sdb: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1203

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1106     8883913+  83  Linux

Disk /dev/sdc: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000eb9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1106     8883913+  83  Linux
```

---

### Post by sisco311 on 2008-04-26
The mount point must be a directory. Did you create it?
```
sudo mkdir /sdc1
```Or mount it in /media/sdc1.
```
sudo mkdir /media/sdc1
```> UUID=0627eb73-1e93-4d49-9cbf-fb9f53125a08 **/media/sdc1**          ext3    defaults        0       2

---

### Post by tad1073 on 2008-04-26
thanks for the info, it helped tremendously.

---

