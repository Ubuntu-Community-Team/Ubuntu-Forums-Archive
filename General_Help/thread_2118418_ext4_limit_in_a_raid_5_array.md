---
title: "ext4 limit in a raid 5 array"
date: 2013-02-21
forum: General Help
---

### Post by arieunier on 2013-02-21
hi there
I've added a new disk to my raid 5 array, following the tutorial here ( [http://zackreed.me/articles/48-adding-an-extra-disk-to-an-mdadm-array](http://zackreed.me/articles/48-adding-an-extra-disk-to-an-mdadm-array) )

I've ran into one problem in the end, as i can't expand the array size .. Seems i reached the maximum ext4 size (16TB).
```
root@data:/home/koko# resize2fs /dev/md0
resize2fs 1.42.5 (29-jul-2012)
resize2fs: New size too large to be expressed in 32 bits
Is there any way to fix this ?

Some information :
koko@DATA:~$ uname -a
Linux DATA 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
koko@DATA:~$ df -k
Filesystem       1K-blocks       Used   Available Use% Mounted on
/dev/sdb1        230169780    4512844   213964904   3% /
udev               7932692          4     7932688   1% /dev
tmpfs              3176840       1456     3175384   1% /run
none                  5120          0        5120   0% /run/lock
none               7942100        152     7941948   1% /run/shm
none                102400         16      102384   1% /run/user
/dev/md0       14535239968 2601889504 11933350464  18% /storage
koko@DATA:~$ sudo mdadm --detail /dev/md0 
/dev/md0:
        Version : 1.2
  Creation Time : Sat Feb  9 16:57:14 2013
     Raid Level : raid5
     Array Size : 17580812160 (16766.37 GiB 18002.75 GB)
  Used Dev Size : 2930135360 (2794.39 GiB 3000.46 GB)
   Raid Devices : 7
  Total Devices : 7
    Persistence : Superblock is persistent

    Update Time : Thu Feb 21 11:31:17 2013
          State : clean 
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : DATA:0
           UUID : aed04bbb:c2f54929:5e59ae48:bd8aa971
         Events : 416355

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       2       8       64        2      active sync   /dev/sde
       3       8       80        3      active sync   /dev/sdf
       4       8       96        4      active sync   /dev/sdg
       6       8      112        5      active sync   /dev/sdh
       7       8        0        6      active sync   /dev/sda
```

---

### Post by albandy on 2013-02-21
This article explains how to solve it
[http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/](http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/)
But I think the correct way is creating multiple LVM partitions in the raid disk, so you can join it.

---

### Post by arieunier on 2013-02-21
> **albandy said:**
> Read this article: [http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/](http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/)

Well i already read this before posting.
Seems like it's not entirely safe to proceed this way, and not entirely supported.
Seems like the best solution would be to create the array with the right size at the beginning.

It seems that the kernel 3.7 contains the correct fixes to extend the FS, but i'm not ready to migrate yet, as i've seen a few problem during the upgrade on various forums.

---

### Post by arieunier on 2013-02-22
Out of curiosity, would it be possible to remove one of the array of my raid 5  ?
I could remove one of the 3Tb drive, copy data to it, and recreate the raid with another file system.

/dev/md0:
        Version : 1.2
  Creation Time : Sat Feb  9 16:57:14 2013
     Raid Level : raid5
     Array Size : 17580812160 (16766.37 GiB 18002.75 GB)
  Used Dev Size : 2930135360 (2794.39 GiB 3000.46 GB)
   Raid Devices : 7
  Total Devices : 7
    Persistence : Superblock is persistent

    Update Time : Fri Feb 22 23:48:47 2013
          State : clean 
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : DATA:0
           UUID : aed04bbb:c2f54929:5e59ae48:bd8aa971
         Events : 416355

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       2       8       64        2      active sync   /dev/sde
       3       8       80        3      active sync   /dev/sdf
       4       8       96        4      active sync   /dev/sdg
       6       8      112        5      active sync   /dev/sdh
       7       8        0        6      active sync   /dev/sda
koko@DATA:~$ df -k
Filesystem       1K-blocks       Used   Available Use% Mounted on
/dev/sdb1        230169780    4523168   213954580   3% /
udev               7932692          4     7932688   1% /dev
tmpfs              3176840       3028     3173812   1% /run
none                  5120          0        5120   0% /run/lock
none               7942100        152     7941948   1% /run/shm
none                102400         12      102388   1% /run/user
/dev/md0       14535239968 2703123804 11832116164  19% /storage
koko@DATA:~$ 

The diff between the Array Size displayed by mdadm and the df -k is around 3 045 572 192 bytes, so around 3tb. So this clearly shows it's not used by the array.


Would that work ?

---

