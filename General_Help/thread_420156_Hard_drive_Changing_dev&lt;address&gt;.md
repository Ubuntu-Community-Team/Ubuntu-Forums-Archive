---
title: "Hard drive Changing /dev/&lt;address&gt;"
date: 2007-04-23
forum: General Help
---

### Post by balasarius on 2007-04-23
OK here is my dilemma...

the /dev/ addresses of my hard drives changing back and forth.  every time I shutdown the computer and power up again the address change  for this....

> Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9683    77778666   83  Linux
/dev/sda2            9684        9964     2257132+   5  Extended
/dev/sda5            9684        9964     2257101   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        8924    51199155    7  HPFS/NTFS
/dev/sdb3            8925       36481   221351602+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    5  Extended
/dev/sdc5               1       60801   488383969+  83  Linux


to this....
> 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    5  Extended
/dev/sda5               1       60801   488383969+  83  Linux

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        8924    51199155    7  HPFS/NTFS
/dev/sdb3            8925       36481   221351602+   7  HPFS/NTFS


Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9683    77778666   83  Linux
/dev/sdc2            9684        9964     2257132+   5  Extended
/dev/sdc5            9684        9964     2257101   82  Linux swap / Solaris

and other random configurations

which is starting to really grate on my nerves as the fstab file is static so  two of the hard drive sometime don´t mount.  strange thing is the 81.9 GB hard drive is the O/S drive and that alway mount regardless but the 300Gb and 500Gb  are the one that don´t  always mount....

here is my current fstab in case it helps.. 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=38af337d-1d28-44b3-9cd8-db16e4f4d891 /               ext3    defaults,errors=remount-ro 0
/dev/sdc5    /media/Sata ext3    defaults,errors=remount-ro 0
/dev/sdb1    /media/NTFS-Music ntfs  nls=utf8,umask=0222 0    0     1
/dev/sdb2    /media/NTFS-Download ntfs  nls=utf8,umask=0222 0    0     1
/dev/sdb3    /media/NTFS-Video ntfs  nls=utf8,umask=0222 0    0     1
# /dev/sda5
UUID=ac82c43b-eeb2-4dbf-9f27-36f569b966bb none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

and Thank in advance for any help in solving this annoying problem

---

