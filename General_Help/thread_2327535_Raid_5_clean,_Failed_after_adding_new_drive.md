---
title: "Raid 5 clean, Failed after adding new drive"
date: 2016-06-12
forum: General Help
---

### Post by Chesties on 2016-06-12
I am following up on a thread I already posted and was solved. [My raid 5 setup was indeed salvageable]("http://ubuntuforums.org/showthread.php?t=2326892"). Thanks for the help on that one. And now I am somewhat stuck again.

So, once I was able to see the data on my array, i pulled off the important stuff. I then ordered a new drive to replace the failed one. mdadm recognized the failed drive as "removed", so I shutdown my machine and replaced the drive. Once I fired it back up I partitioned the new drive using the following command:

```
sudo sfdisk -d /dev/sdb | sudo sfdisk /dev/sda
```

I wanted to mimic the exact same partition of the other drives in the array with the new one i added. Once that was complete I added the new drive to the array:

```
mdadm --manage /dev/md0 --add /dev/sda1
```

It appeared to work as it seemed to be syncing. I let that run over night. However, now that it is complete, the array does not seem correct:

cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[1] sda1[3](S) sdc1[2](F)
      3906763776 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/1] [_U_]
```

sudo mdadm --detail /dev/md0
```
/dev/md0:
        Version : 1.2
  Creation Time : Thu Jul 25 15:12:48 2013
     Raid Level : raid5
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Sat Jun 11 21:47:23 2016
          State : clean, FAILED 
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : server1:0  (local to host server1)
           UUID : eb865610:64f74d3c:6a663c47:f5195d77
         Events : 2634

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed

       2       8       33        -      faulty spare   /dev/sdc1
       3       8        1        -      spare   /dev/sda1

```

sudo mdadm --examine /dev/sda1
```
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : eb865610:64f74d3c:6a663c47:f5195d77
           Name : server1:0  (local to host server1)
  Creation Time : Thu Jul 25 15:12:48 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5b84c193:e377e7e8:fda00743:b443df3a

    Update Time : Sun Jun 12 00:00:05 2016
       Checksum : da6c683d - correct
         Events : 2636

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : spare
   Array State : .A. ('A' == active, '.' == missing)
```

sudo mdadm --examine /dev/sdb1
```
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : eb865610:64f74d3c:6a663c47:f5195d77
           Name : server1:0  (local to host server1)
  Creation Time : Thu Jul 25 15:12:48 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 8feeed8a:7c186672:b339e906:b7e31a82

    Update Time : Sun Jun 12 00:00:05 2016
       Checksum : 6634abc1 - correct
         Events : 2636

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .A. ('A' == active, '.' == missing)

```

sudo mdadm --examine /dev/sdc1
```
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : eb865610:64f74d3c:6a663c47:f5195d77
           Name : server1:0  (local to host server1)
  Creation Time : Thu Jul 25 15:12:48 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b57b3ba1:177d9fa1:87f5528e:62091b0f

    Update Time : Fri Jun 10 17:22:36 2016
       Checksum : c024cb10 - correct
         Events : 2624

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing)

```

Looks like the new drive, sda1 was added as a spare and sdc1 is seen as failed. Any thoughts on why this happened? I would love to be able to sort this out and fix it, but I will definitely need to lean on the community for this. One small note is that sdc1 SMART indicates a few bad sectors on the drive and, if i am not mistaken, had some bad sectors prior to me adding a new drive to the array and syncing. Not sure if this complicates things.

Perhaps I have bitten off more than i can chew. So definitely appreciate any help. If it is something that can't be resolved because of what i did/didn't do, I won't be crushed. Was able to get the important data off the array, so I can always start anew. If anything, this whole process has taught me a lot about mdadm, linux, and raids in general.

Thanks in advance for the help!

---

