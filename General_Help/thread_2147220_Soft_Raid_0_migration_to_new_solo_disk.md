---
title: "Soft Raid 0 migration to new solo disk"
date: 2013-05-21
forum: General Help
---

### Post by egrimisu on 2013-05-21
Hi guys,
I would like to migrate a raid0 setup ( bootable) to a non raid disk setup. the raid are 2x1tb and the new drive is 2tb. How to do it?

using ubuntu 11.04 and happy with it :)

---

### Post by SaturnusDJ on 2013-05-22
Two ways I guess:

1. From md device to sd device using a tool like dd. Everything is copied included unnecessary information. Probably no verification. Chances are the array size is bigger than the single disk, so data won't fit.
2. Filesystem to filesystem. More work, but way more flexible. You will be able to choose a new folder structure and selectively transfer data. Might need reinstall of OS first.

---

### Post by egrimisu on 2013-05-22
Hi, and thanks for the quick post, well reinstalling the os is not an option for me, so i think i'll stick to dd, i don't know how to use but i'll search for some info around the web. Any tips that i shall follow? what shall i keep in mind? do i need to reinstall or reconfigure grub? 
if you have some advice please feel free to post :)

> **SaturnusDJ said:**
> Two ways I guess:

1. From md device to sd device using a tool like dd. Everything is copied included unnecessary information. Probably no verification. Chances are the array size is bigger than the single disk, so data won't fit.
2. Filesystem to filesystem. More work, but way more flexible. You will be able to choose a new folder structure and selectively transfer data. Might need reinstall of OS first.

---

### Post by SaturnusDJ on 2013-05-22
An exact copy of data should not need a reinstall of anything.
A little more detail might be useful. What partitions do you have now?

You should compare available space on the md and sd devices.

---

### Post by egrimisu on 2013-05-22
Thanks,
Well i can't compare space, hdd will arrive tommorow.

if i remember well the raid was made like this, the logs down will confirm.
sda1 and sdb1 in raid1 - boot partition
sda2 and sdb2 in raid0 - / partition in ext4
sda3 and sdb3 in raid0 - swap partition

----------------------------------------------------------------

fdisk -l list the folowing:


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002cd4d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      247808   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sda2              31      121486   975586304   fd  Linux raid autodetect
/dev/sda3          121486      121602      926720   fd  Linux raid autodetect


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x218de4ce


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      247808   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdb2              31      121486   975586304   fd  Linux raid autodetect
/dev/sdb3          121486      121602      926720   fd  Linux raid autodetect


Disk /dev/md1: 1998.0 GB, 1998000619520 bytes
2 heads, 4 sectors/track, 487793120 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000


Disk /dev/md1 doesn't contain a valid partition table


Disk /dev/md0: 253 MB, 253689856 bytes
2 heads, 4 sectors/track, 61936 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table


Disk /dev/md2: 1897 MB, 1897791488 bytes
2 heads, 4 sectors/track, 463328 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000


Disk /dev/md2 doesn't contain a valid partition table

----------------------------------------------------------------------

mdadm -D /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Thu Aug 26 09:43:50 2010
     Raid Level : raid1
     Array Size : 247744 (241.98 MiB 253.69 MB)
  Used Dev Size : 247744 (241.98 MiB 253.69 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent


    Update Time : Wed May 22 23:44:56 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           UUID : 6172f614:e653ad0c:292481f4:27ef2d03
         Events : 0.223


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1


--------

mdadm -D /dev/md1
/dev/md1:
        Version : 0.90
  Creation Time : Thu Aug 26 09:43:53 2010
     Raid Level : raid0
     Array Size : 1951172480 (1860.78 GiB 1998.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent


    Update Time : Thu Aug 26 09:43:53 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


     Chunk Size : 64K


           UUID : d75d7e6c:8124b415:d14d2323:e150785e
         Events : 0.1


    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8        2        1      active sync   /dev/sda2

---------

mdadm -D /dev/md2
/dev/md2:
        Version : 0.90
  Creation Time : Thu Aug 26 09:43:56 2010
     Raid Level : raid0
     Array Size : 1853312 (1810.18 MiB 1897.79 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent


    Update Time : Thu Aug 26 09:43:56 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


     Chunk Size : 64K


           UUID : 4b7da158:1545b6d1:5a675af2:7363c641
         Events : 0.1


    Number   Major   Minor   RaidDevice State
       0       8       19        0      active sync   /dev/sdb3
       1       8        3        1      active sync   /dev/sda3








> **SaturnusDJ said:**
> An exact copy of data should not need a reinstall of anything.
A little more detail might be useful. What partitions do you have now?

You should compare available space on the md and sd devices.

---

### Post by SaturnusDJ on 2013-05-22
In that case you will need to create the right size partitions before copying content of the old setup.
A problem here might be you need to create a GPT table.
Another could be that your new hdd is one with 4k sized sectors.
I don't know much about GRUB but it's likely it won't find the new root location. That should be easy to fix however.

I realize I have not been able to help you in a practical way. I hope someone else will provide a bit more clarification.

---

### Post by egrimisu on 2013-05-23
yes of course the new disk is 4k, so wainting for more advice. thanks

---

### Post by egrimisu on 2013-05-23
still wainting for help :) Thanks

---

### Post by egrimisu on 2013-06-17
some tips anyone?

---

### Post by SaturnusDJ on 2013-06-17
Ok, read this full post before starting:

Run parted to align-check:
```

parted /dev/md0 align-check m 1

```

Good result is '1 aligned'.

Then compare the sizes:
```

parted /dev/md0 u b print
parted /dev/sdc u b print

```
[SIZE=1]Assuming the new device is /dev/sdc[/SIZE]

If it fits, start copy:
```

dd if=/dev/md0 of=/dev/sdc bs=1M

```

Then kill the mdadm superblocks:
```

mdadm --zero-superblock /dev/sdc

```
[SIZE=1]Assuming the new device is /dev/sdc[/SIZE]

This is totally a theory. I have no idea if it will work.
It's not dangerous for your current array, that is if you don't make a typo and the disks are 100% healthy because in the dd proces every bit of them will be copied.

I still recommend doing a filesystem to filesystem copy.

---

### Post by egrimisu on 2013-06-19
Hi and thanks for the reply, what well actually i have md0 md1 and md2 (3 partition, 1 boot, 1 / , and 1 swap), in this case shall i use:
dd if=/dev/md0 of=/dev/sdc1 bs=1M
dd if=/dev/md1 of=/dev/sdc2 bs=1M
dd if=/dev/md2 of=/dev/sdc3 bs=1M
??

Thanks in advance

---

### Post by egrimisu on 2013-06-20
Well i did what i have written upper and after that i have flaged sdc1 as boot, of course the system did not boot but now i'm trying to reinstall grub from a live cd. be back with news.

---

### Post by egrimisu on 2013-06-21
Things went bad, i couldn't get grub to work properly, maybe because the structure of the disk changed a bit, anyway i managed to boot manualy specifying in grub kernel and initrd and then upgraded from v 11.04 to 12.04 and the upgrade reinstalled grub properly.
When using the md setup the partitions were defined in grub.cfg as /dev/md0..2 , since i upgrated the disk setup from 2x1tb to 1x2tb i believe that the disk was converted to gpt since in the new grub.cfg file the drive is defined as gpt hd0 or something like this.

Anyway, things are right now, thanks guys for the help.

---

