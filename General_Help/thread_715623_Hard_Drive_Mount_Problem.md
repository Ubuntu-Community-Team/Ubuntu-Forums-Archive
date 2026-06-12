---
title: "Hard Drive Mount Problem"
date: 2008-03-05
forum: General Help
---

### Post by Knyx on 2008-03-05
I had ubuntu installed on my computer previously with 2 hard drives.  One had the operating system and the other had all of my information.  Both formatted as ext3.

I just reinstalled and now when I try to mount my old drive it says it can't find the file system type.

```

sudo mount -t ext3 /dev/hdd /stuff

```

Gives the result:
Wrong fs type, bad option, bad superblock on /dev/hdd, missing codepage or helper program, or other error.

```

dmesg | tail

```

Gives:
VFS: Can't find ext3 filesystem on dev hdd

```

sudo fdisk -l /dev/hdd

```

Gives:
80.0GB
255 heads, 63 sectors/track, 9729 cylinders
units = cylinders of 16065 * 512
Disk Identifier: 0x00000000


I would greatly appreciate any help you all have because this drive has all of my data on it.

Regards,

Keith

---

### Post by louieb on 2008-03-05
Kind of surprised it did not mount automatically.
One thing. Haven't ever seen a partition named /dev/hdd
What I expect to see is /dev/sd@# ( some letter then some number).

What does ```
sudo fdisk -l
```show. If you can put it in your next post.

---

### Post by anaconda on 2008-03-05
> **louieb said:**
> Kind of surprised it did not mount automatically.
One thing. Haven't ever seen a partition named /dev/hdd
What I expect to see is /dev/sd@# ( some letter then some number).

What does ```
sudo fdisk -l
```show. If you can put it in your next post.

yep. the name of your partition is probably  /dev/sdX1 with X being some letter between a-m

or if you are using an older version of ubuntu it might be /dev/hdd1
Dabber and edgy still named IDE disks hda, hdb, hdc, hdd etc.. Feisty and newer name IDE diskd the same way than SATA disks sda, sdb, sdc..
 
"hdd" would be the hard disk
"hdd1" would be the first partition on that hard disk

Anyway the fdisk -l command will show you what names are used in your computer..

---

### Post by Knyx on 2008-03-05
This is on ubuntu 7.10 and the drive in question is an ide drive.

Maybe the data is gone?

```

sudo fdisk -l

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14430   115908943+  83  Linux
/dev/sda2           14431       14593     1309297+   5  Extended
/dev/sda5           14431       14593     1309266   82  Linux swap / Solaris

```

---

### Post by louieb on 2008-03-05
I would say the data is unreachable. The drive has not partitions. 
Two programs that might help recover your data. **Parted** - has the ability to guess what a partition table should look like. and **testdisk** a data recovery program. Both are available on the  [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

