---
title: "Recovering a RAID-5 after disk failure"
date: 2015-05-06
forum: General Help
---

### Post by Patrick_Ott on 2015-05-06
Hi,

I have to admit I am a bit lost and might be in over my head at this point. Hence, rather than taking the risk of actually destroying my RAIDs content, I reach out to you. Last week one disk in my RAID-5 (4x2TB) failed on me. I replaced it with a 3TB disk and after I forced it to assemble it did so and began to rebuild the degraded array. So far so good. The Raid is a LVM and the content is encrypted with cryptsetup.

Normally my Ubuntu would jump in and show me the 6TB drive symbol with a lock on it and I could unlock it there, or by doing so on the command line but that does not seem possible anymore. The problem appears to be that the volume group is gone (at least it is not listed under /dev) anymore and without that I have no idea how to mount the whole thing. 

The Raid seems in good shape: 

```

sudo mdadm --detail /dev/md0


/dev/md0:
        Version : 1.2
  Creation Time : Sat Aug 16 16:30:56 2014
     Raid Level : raid5
     Array Size : 5860147200 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 1953382400 (1862.89 GiB 2000.26 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Sun May  3 19:40:22 2015
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 1024K


           Name : PatsNAS:0
           UUID : f2168602:42710fea:38bb0b14:26c6f826
         Events : 21939


    Number   Major   Minor   RaidDevice State
       5       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       4       8       49        3      active sync   /dev/sdd1

```

and

```

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd1[4] sdc1[2] sdb1[1] sda1[5]
      5860147200 blocks super 1.2 level 5, 1024k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

```

I was about to run a "pvcreate /dev/md0" to re-create the volume but stopped there as I might have been in the process of destroying my data. 

I would appreciate any help with this issue.

Best
Pat

---

### Post by Patrick_Ott on 2015-05-07
Really, nobody can help? :(

---

### Post by tgalati4 on 2015-05-08
Are any of the disk drives "Green" drives?  It can take a while to resyncronize the data after replacing a failed disk.  How full was your data pool?  What were the SMART parameters of the drive that failed?

---

