---
title: "Resize / file system and create /home in existing raid 1"
date: 2008-05-05
forum: General Help
---

### Post by tpinheiro on 2008-05-05
Hi!

I'm running Ubuntu 7.10 x64. Currently, my system is setup as follows:

-  / is in a Raid 1 array (/dev/md0) consisting of two partitions - sda1 and sdb1 (ca. 148 GB);

-  swap in Raid 0 (/dev/md1) - sda2 and sdb2 of ca. 1 GB each giving me 2 GB in total:

-  sda and sdb are two disks of 160GB:

-  I do not have a separate /home file system.

I would like to correct this situation by doing the following:
   
-  resize the partition containing the / file system to 27 GB keeping it in RAID 1 (/dev/md0);
-  create a new partition of 120GB to mount /home, also in RAID 1 (/dev/md2);
-  change swap from a RAID 0 to a RAID 1, resizing it to 2GB (/dev/md1).

Can this be done without reinstalling everything from scratch?

Output of /proc/mdstat:
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid0 sda2[0] sdb2[1]
      2023936 blocks 64k chunks
      
md0 : active raid1 sda1[0] sdb1[1]
      155276160 blocks [2/2] [UU]
      
unused devices: <none>
/proc/mdstat 

```

Output of /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=b3dd64e4-786f-496b-b9e3-c42da731e113 /               ext3    defaults,errors=remount-ro 0       1
# /dev/md1
UUID=d9f45f6b-025f-42e7-9ebf-27cddc6fa27b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Output of mdadm --detail /dev/md0:
```

/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Feb 25 13:25:15 2008
     Raid Level : raid1
     Array Size : 155276160 (148.08 GiB 159.00 GB)
  Used Dev Size : 155276160 (148.08 GiB 159.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon May  5 18:14:31 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : c39b647f:cb4f0780:05770ebd:8c404dcc
         Events : 0.18

    Number   Major   Minor   RaidDevice State
       0       8      145        0      active sync   /dev/sda1
       1       8      161        1      active sync   /dev/sdb1

```

Output of mdadm --detail /dev/md1:
```

/dev/md1:
        Version : 00.90.03
  Creation Time : Mon Feb 25 13:25:23 2008
     Raid Level : raid0
     Array Size : 2023936 (1976.83 MiB 2072.51 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon May  5 01:17:47 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : cd9a2299:6e3e0036:8ebd1878:1deccd4a
         Events : 0.7

    Number   Major   Minor   RaidDevice State
       0       8      146        0      active sync   /dev/sda2
       1       8      162        1      active sync   /dev/sdb2

```

I would really appreciate your help. If you need further info from me please just say so and I will try to post it as soon as possible.

Thanks.

Cheers,
Tiago

---

### Post by fahadsadah on 2008-05-05
I would recommend booting from the live-cd, and then running GParted (System->Administration->Partition Editor).
GParted can be installed on a regular ubuntu install, but it is not recommended to resize the root disk while a system is booted from it!

---

### Post by tpinheiro on 2008-05-07
Hi fahadsadah,

Thanks for your reply. :)

However, I think in my case just using parted (or Gparted) would not solve my problem due to the RAID. There must be something more that I need to do...

Still in need of some help,
Tiago

---

