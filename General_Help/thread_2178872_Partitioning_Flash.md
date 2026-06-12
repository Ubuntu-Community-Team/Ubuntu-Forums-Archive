---
title: "Partitioning Flash"
date: 2013-10-05
forum: General Help
---

### Post by koh2 on 2013-10-05
I'm trying to partition a 16GB microsd to have its original FAT32 partition and add a ~2GB ext3 partition. Ability to symlink with internal Android storage is the goal.

Some parted output of the virgin microsd...```
Disk /dev/mmcblk0: 15.9 GB, 15931539456 bytes
255 heads, 63 sectors/track, 1936 cylinders, total 31116288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1            8192    31116287    15554048    c  W95 FAT32 (LBA)

Command (m for help): u
Changing display/entry units to cylinders (DEPRECATED!)

Command (m for help): p   

Disk /dev/mmcblk0: 15.9 GB, 15931539456 bytes
255 heads, 63 sectors/track, 1936 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        1937    15554048    c  W95 FAT32 (LBA)
```
I'd like to use GParted for simplicity, but when I try to resize the FAT32 by leaving the Free Space Preceding the same and just reduce the size, I have a problem:

It doubles the size of the Free Space Preceding. This ticks me off. Didn't the microsd designers choose a certain Start for a reason? What's the best recommendation for achieving my goal? Thanks!

---

### Post by oldfred on 2013-10-06
You are displaying in cylinders. SSD & flash drive so not even have cylinders, but BIOS stopped using cylinders when hard drives went over 8GB many years ago. The use LBA or large block allocation.

But SSD (and flash?) are block devices and you best read & write entire blocks. If start and size of partition is not on 8 sector boundries you will have issues.

 [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)
Alignment 2048 sectors Advanced Format drives
[http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)
Technical details - from 2010 so now newer kernel resolve linux issues
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

Boot loaders like grub also need room after the first sector or MBR for additional boot code. If too small you will get grub install errors.

---

### Post by koh2 on 2013-10-13
Thank you Fred!

I'm also trying to learn about what the Linaro folks are doing...
[http://www.google.com/search?q=linaro+partition+flash](http://www.google.com/search?q=linaro+partition+flash)
...but alas for my particular task here I decided to leave the uSD as FAT32 like from the factory. I'm gonna research this more. Anybody else have some FAT32+ext3 flash partitioning wisdom?

---

