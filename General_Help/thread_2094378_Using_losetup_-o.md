---
title: "Using losetup -o"
date: 2012-12-13
forum: General Help
---

### Post by geir765 on 2012-12-13
Im trying to use losetup to mount a *.img file with two partitions. But every time the whole thing gets mounted.

running fdisk -lu /dev/loop1 gives:
```
Disk /dev/loop1: 292 MB, 292552704 bytes
255 heads, 63 sectors/track, 35 cylinders, total 571392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e6e660c

      Device Boot      Start         End      Blocks   Id  System
/dev/loop1p1            2048      133119       65536    c  W95 FAT32 (LBA)
/dev/loop1p2          133120      571391      219136   83  Linux

```I then take 2048*512 and run 
losetup -o 1048576 /dev/loop2 /dev/loop1
mkfs.vfat /dev/loop2

And a big 200M partition is mounted it should have been 64M. It works great when i use kpartx but not with losetup

Any ideas?

---

### Post by Rexilion on 2012-12-14
That's weird :/

Disk layout should be correct:

((133119&#8722;2048)&#8901;512)/1000000 = 67,108352 MB

((571391&#8722;133120)&#8901;512)/1000000 = 224,39475 MB

Maybe the img is a sparse file and losetup is using a way too big offset?

---

