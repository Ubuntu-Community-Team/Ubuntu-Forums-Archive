---
title: "Removing software RAID1 and merging two disks into one without data loss?"
date: 2018-10-18
forum: General Help
---

### Post by eurusd on 2018-10-18
is that possible?
I am running out of space, I need to free up secondary ssd and merge it into one

how to do it without killing data?

also will it work after a reboot?

```

oot@Ubuntu-1604-xenial-64-minimal ~ # fdisk -l
Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xb32c040f


Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1           2048  33556479  33554432   16G fd Linux raid autodetect
/dev/sda2       33556480  34605055   1048576  512M fd Linux raid autodetect
/dev/sda3       34605056 500116143 465511088  222G fd Linux raid autodetect




Disk /dev/sdb: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb20b70c2


Device     Boot    Start       End   Sectors  Size Id Type
/dev/sdb1           2048  33556479  33554432   16G fd Linux raid autodetect
/dev/sdb2       33556480  34605055   1048576  512M fd Linux raid autodetect
/dev/sdb3       34605056 500116143 465511088  222G fd Linux raid autodetect




Disk /dev/md0: 16 GiB, 17163091968 bytes, 33521664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/md1: 511.4 MiB, 536281088 bytes, 1047424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/md2: 221.9 GiB, 238207434752 bytes, 465248896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
root@Ubuntu-1604-xenial-64-minimal ~ # 


inimal ~ # lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sdb       8:16   0 238.5G  0 disk  
&#9500;&#9472;sdb2    8:18   0   512M  0 part  
&#9474; &#9492;&#9472;md1   9:1    0 511.4M  0 raid1 /boot
&#9500;&#9472;sdb3    8:19   0   222G  0 part  
&#9474; &#9492;&#9472;md2   9:2    0 221.9G  0 raid1 /
&#9492;&#9472;sdb1    8:17   0    16G  0 part  
  &#9492;&#9472;md0   9:0    0    16G  0 raid1 
sda       8:0    0 238.5G  0 disk  
&#9500;&#9472;sda2    8:2    0   512M  0 part  
&#9474; &#9492;&#9472;md1   9:1    0 511.4M  0 raid1 /boot
&#9500;&#9472;sda3    8:3    0   222G  0 part  
&#9474; &#9492;&#9472;md2   9:2    0 221.9G  0 raid1 /
&#9492;&#9472;sda1    8:1    0    16G  0 part  
  &#9492;&#9472;md0   9:0    0    16G  0 raid1 


9:0    0    16G  0 raid1 
root@Ubuntu-1604-xenial-64-minimal ~ # cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdb3[1] sda3[0]
      232624448 blocks super 1.2 [2/2] [UU]
      bitmap: 2/2 pages [8KB], 65536KB chunk


md1 : active raid1 sdb2[1] sda2[0]
      523712 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sdb1[1] sda1[0]
      16760832 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>



one>
root@Ubuntu-1604-xenial-64-minimal ~ # mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Apr  6 01:48:56 2018
     Raid Level : raid1
     Array Size : 16760832 (15.98 GiB 17.16 GB)
  Used Dev Size : 16760832 (15.98 GiB 17.16 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Thu Sep 27 02:04:04 2018
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : rescue:0
           UUID : b7d19f48:d6ce7ffc:fb539e37:6921a56c
         Events : 37


    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
root@Ubuntu-1604-xenial-64-minimal ~ # mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Fri Apr  6 01:48:56 2018
     Raid Level : raid1
     Array Size : 523712 (511.52 MiB 536.28 MB)
  Used Dev Size : 523712 (511.52 MiB 536.28 MB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Thu Oct 18 23:11:41 2018
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : rescue:1
           UUID : dd86205e:91541582:208de392:2fa35095
         Events : 37


    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
root@Ubuntu-1604-xenial-64-minimal ~ # mdadm --detail /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Fri Apr  6 01:48:56 2018
     Raid Level : raid1
     Array Size : 232624448 (221.85 GiB 238.21 GB)
  Used Dev Size : 232624448 (221.85 GiB 238.21 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Fri Oct 19 00:34:01 2018
          State : active 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : rescue:2
           UUID : 312e465a:a213ea1c:9b899327:3769bce2
         Events : 2018


    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
root@Ubuntu-1604-xenial-64-minimal ~ # mdadm --detail /dev/md3
mdadm: cannot open /dev/md3: No such file or directory
root@Ubuntu-1604-xenial-64-minimal ~ #
```

---

### Post by TheFu on 2018-10-19
Please wrap the first post in "code tags" so things line up correctly.

If you can't afford to lose any data, then make a know-you-can-restore backup.  Period.

I would expect to backup the data in the manner required, then reset the "RAID"-ness of the 2 SSDs, then create new partitions (I'd use GPT) and add those to PEs, VGs, and LVs as required.  These are all LVM2 ideas.  LVs can be considered partitions for almost all uses, but this stuff works easily only for data storage.  If you are planning to use these devices for the OS, things get complicated quickly.

LVM is the best tested, enterprise way, to merge storage across different physical storage devices.  There are others, which I've never used, but each has a vocal following.   

With LVM, you can either append or stripe.  Both are dangerous, since if any single storage device in the LVM LV fails, all the data on all the disks is impacted.  In the early 2000s, I lost 80% of my data using LVM with concatenation after 1 disk failed.

I learned my lesson and got *backup religion* since then and haven't lost any data since, even with multiple disk failures.

---

### Post by eurusd on 2018-10-21
incorrect answer

---

### Post by QIII on 2018-10-21
Would you care to share the correct answer?

---

