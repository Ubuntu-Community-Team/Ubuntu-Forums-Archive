---
title: "[SOLVED] Command to figure out the file system type of a partition?"
date: 2008-06-23
forum: General Help
---

### Post by caljohnsmith on 2008-06-23
Is there any easy command to find the file system type of a partition? Here is some interesting results that I don't quite understand:

```
john@TECH5321:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5100    40960048+   7  HPFS/NTFS
/dev/sda2            5108        7695    20788110   83  Linux
/dev/sda3            9608        9729      979965   82  Linux swap / Solaris
/dev/sda4   *        7696        9607    15358140   83  Linux

john@TECH5321:~$ sudo file -s /dev/sda*
/dev/sda:  x86 boot sector; partition 2: ID=0x83, starthead 254, startsector 82043955, 41576220 sectors; partition 3: ID=0x82, starthead 254, startsector 154336455, 1959930 sectors; partition 4: ID=0x83, active, starthead 254, startsector 123620175, 30716280 sectors, code offset 0x48
/dev/sda1: x86 boot sector, code offset 0x52, OEM-ID "NTFS    ", sectors/cluster 8, reserved sectors 0, Media descriptor 0xf8, heads 15, hidden sectors 63, dos < 4.0 BootSector (0x80)
/dev/sda2: Linux rev 1.0 ext3 filesystem data (needs journal recovery) (large files)
/dev/sda3: Linux/i386 swap file (new style) 1 (4K pages) size 244990 pages
/dev/sda4: x86 boot sector; GRand Unified Bootloader, stage1 version 0x3, 1st sector stage2 0x87c5057, code offset 0x48

```
Note that "fdisk -l" does not give the actual file system type (ext3, etc), yet "file -s" does EXCEPT for my sda4 partition, which is Mandriva 2008. Note that the Mandriva 2008 has Grub intalled into its partition's boot sector, whereas Ubuntu (sda2) does not.

If I load up gparted it tells me correctly that sda2 and sda4 are both ext3 file systems. Isn't there a way to determine it from the CLI? Thanks for any help.

---

### Post by sdennie on 2008-06-23
If they are all mounted, try:

```

cat /proc/mounts

```

or

```

df -T

```

---

### Post by bodhi.zazen on 2008-06-23
If they are mounted, just type :

```
mount
```

Either way :

```
sudo blkid
```

---

### Post by ibutho on 2008-06-23
A good command for finding out filesystem types is 
```
sudo parted -l
```
It shows you whether a partitions filesystem type is ext3, reiserfs, ntfs, etc.

---

### Post by bodhi.zazen on 2008-06-23
> **ibutho said:**
> A good command for finding out filesystem types is 
```
sudo parted -l
```
It shows you whether a partitions filesystem type is ext3, reiserfs, ntfs, etc.

```
sudo parted /dev/sda print
```

Much longer the blkid. Be careful with parted :twisted:

---

### Post by caljohnsmith on 2008-06-23
Thanks so much for the replies everyone, I think that "sudo blkid" and "sudo parted /dev/sda print" give the most precise results for determining file system types and will serve my needs the best. :)

---

