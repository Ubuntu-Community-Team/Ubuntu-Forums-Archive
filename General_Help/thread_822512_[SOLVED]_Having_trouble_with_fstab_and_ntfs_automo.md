---
title: "[SOLVED] Having trouble with fstab and ntfs automount"
date: 2008-06-08
forum: General Help
---

### Post by rudihawk on 2008-06-08
Hi, I am having trouble getting my Windows ntfs partition to automount. 

I have tried to follow the guide located here: [Ubuntu How To]("http://ubuntuforums.org/showthread.php?t=802699") 

However I am still struggling. The /dev/sda1 is the drive I am trying to mount. (is that correct?)

My fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=375f1cbf-8223-481a-b561-9a493b2b31f6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=f33b0590-c09a-42c5-a95e-aef135c9b632 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1	/media/hda2 	ntfs	defaults	0	0
```

The result of: sudo fdisk -l is: 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f591f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12812   102912358+   7  HPFS/NTFS
/dev/sda2           12813       19214    51424065   83  Linux
/dev/sda3           19215       19457     1951897+  82  Linux swap / Solaris

```

Any ideas?:confused:
Thanks

---

### Post by rudihawk on 2008-06-08
Nevermind. Solved it myself.

---

