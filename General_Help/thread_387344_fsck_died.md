---
title: "fsck died"
date: 2007-03-18
forum: General Help
---

### Post by dveble on 2007-03-18
I have dual boot  ubuntu 6.10 and win XP.
 I use two hard disks, one for os, other for data and backups.
After accidental power cut, during ubuntu's fsck  at the start up,
i can not manage anymore to 
mount my second hard disk, from ubuntu, or from xp.
all my folders in my media folder are still there, but nothing inside
there is all my data/work and backups. 
all my folders in my media folder are still there

is there any way to fix that?
tanx in advance.

here is my  checkfs log:

```
Log of fsck -C -R -A -a 
Sun Mar 18 12:26:26 2007

fsck 1.39 (29-May-2006)
open UUID=60DA-A085:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open UUID=60FB-667B:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open UUID=2044-6351:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open UUID=343E-EE4C:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
fsck.ext3: Unable to resolve 'UUID=289e45ff-e170-4856-9bcd-5dc33deae52b'

fsck.ext3: Unable to resolve 'UUID=fb1b5ed8-e715-44f2-9196-42d649278fb0'

fsck died with exit status 9

Sun Mar 18 12:26:26 2007
----------------
```

and my fstab :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=00f06f53-3b18-4a90-babb-aebd0b2761a9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0C4CD3064CD2EA0A /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=289e45ff-e170-4856-9bcd-5dc33deae52b /media/hdb1     ext3    defaults        0       2
# /dev/hdb3
UUID=fb1b5ed8-e715-44f2-9196-42d649278fb0 /media/hdb3     ext3    defaults        0       2
# /dev/hdb5
UUID=60DA-A085  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=60FB-667B  /media/hdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=2044-6351  /media/hdb7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb8
UUID=343E-EE4C  /media/hdb8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=0abed625-2c63-4b5d-a132-7f19b8da288b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```


 sudo fdisk -l

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2452    19695658+   7  HPFS/NTFS
/dev/hda2            2453        6397    31688212+  83  Linux
/dev/hda3            6398        6659     2104515   82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table

```

---

### Post by dveble on 2007-03-18
fixed, :D
Maible this helps to someone,
but, after searching through forums i manage to fix this by:

1. unplug hard disk.
2. boot/reboot.
3. plug hard disk back
4  boot.

and it works now.
ufff..

---

