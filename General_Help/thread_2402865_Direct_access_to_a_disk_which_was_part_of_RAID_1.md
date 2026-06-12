---
title: "Direct access to a disk which was part of RAID 1"
date: 2018-10-05
forum: General Help
---

### Post by buonboy on 2018-10-05
Hello,
my (QNAP) NAS is not working anymore and I need to access my data. I tried with some Recovery Software in Windows, but they can't see my directories structure. So i'm trying with Ubuntu.
There are two WD RED 8TB and I can connect one of them at time to my Laptop with Ubuntu.
Under Disks I see the volume has 5 partitions, all of them Partition Data: Basic Type and Content: Linux RAID Member (version 1.0).

fdisk -l:
**Disk /dev/sdb: 7,3 TiB, 8001563222016 bytes, 15628053168 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: 41F79514-1F45-47BA-BFA1-45F2FE9602CD

**Device**     **      Start** **        End** **    Sectors** **  Size** **Type**
/dev/sdb1           40     1060289     1060250 517,7M Microsoft basic data
/dev/sdb2      1060296     2120579     1060284 517,7M Microsoft basic data
/dev/sdb3      2120584 15610264109 15608143526   7,3T Microsoft basic data
/dev/sdb4  15610264112 15611324399     1060288 517,7M Microsoft basic data
/dev/sdb5  15611324408 15628031999    16707592     8G Microsoft basic data

**Disk /dev/md13: 448,1 MiB, 469893120 bytes, 917760 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

**Disk /dev/md256: 517,7 MiB, 542834688 bytes, 1060224 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

**Disk /dev/md1: 7,3 TiB, 7991369334784 bytes, 15608143232 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

**Disk /dev/md322: 6,9 GiB, 7408779264 bytes, 14470272 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

**Disk /dev/md9: 517,6 MiB, 542769152 bytes, 1060096 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


mdadm --examine /dev/sdb3
        
Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : 2e881376:26727080:eb4b694c:a4ec3ed2
           Name : 1
  Creation Time : Fri Aug 10 14:15:35 2018
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 15608143240 (7442.54 GiB 7991.37 GB)
     Array Size : 7804071616 (7442.54 GiB 7991.37 GB)
  Used Dev Size : 15608143232 (7442.54 GiB 7991.37 GB)
   Super Offset : 15608143504 sectors
   Unused Space : before=0 sectors, after=264 sectors
          State : clean
    Device UUID : d85a8d70:5d753f6d:5891a6b1:f1bc9252

    Update Time : Fri Sep 28 19:15:21 2018
  Bad Block Log : 512 entries available at offset -8 sectors
       Checksum : 3e379ee1 - correct
         Events : 221

   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

Under files I can access md9 and md13, but not md1. How can I do to access it? I have to assemble?
Thanks a lot.

---

### Post by buonboy on 2018-10-11
In Linux i got the following error (for both HDDs):
WARNING: Unrecognized segment type tier-thin-pool
LV tp1, segment 1 invalid: does not support flag ERROR_WHEN_FULL. for tier-thin-pool segment.
Internal error: LV segments corrupted in tp1.

Any idea?

---

### Post by dbergst on 2018-10-12
I found this posting which potentially provides a solution for the issue you are experiencing.

[https://blog.sleeplessbeastie.eu/2012/05/08/how-to-mount-software-raid1-member-using-mdadm/](https://blog.sleeplessbeastie.eu/2012/05/08/how-to-mount-software-raid1-member-using-mdadm/)

---

