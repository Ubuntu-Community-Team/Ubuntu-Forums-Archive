---
title: "Unable to expand XFS partition on software RAID volume (error: data size unchanged)"
date: 2013-12-09
forum: General Help
---

### Post by cpufreak2589 on 2013-12-09
Hi there,

I'm attempting to expand my mdadm-managed RAID5 array by adding another 2tb drive to the mix (bringing the total to four). I have completed the drive addition and RAID reshaping without a hitch, and my mdadm --detail shows me now having 6tb of space (3x2tb usable with the last 2tb being parity).

```
 /dev/md0:
        Version : 1.2
  Creation Time : Fri Jul 22 17:13:28 2011
     Raid Level : raid5
     Array Size : 5860537344 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953512448 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent
    Update Time : Mon Dec  9 15:06:17 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 1024K

           Name : htpcbox:0  (local to host htpcbox)
           UUID : b2fee98b:a1be2e00:ebbc39a9:9050312e
         Events : 362190

    Number   Major   Minor   RaidDevice State
       4       8       64        0      active sync   /dev/sde
       1       8        1        1      active sync   /dev/sda1
       3       8       49        2      active sync   /dev/sdd1
       5       8       32        3      active sync   /dev/sdc

```

My current partition is 4tb and I'm wanting to expand it to all 6tb, which I thought was as simple as calling xfs_growfs. Unfortunately, it doesn't seem to do much of anything and the size remains the same. I also tried adding the -d flag to specify auto-expansion of the data segment, which also didn't do anything. I checked gparted to see if I could cheat and use the GUI, but it complains about my GPT table not being in the correct position and the array has having 6tb of empty space, so I thought it best to just ignore gparted entirely. 

```

#sudo xfs_growfs -d /dev/md0p1 
meta-data=/dev/md0p1             isize=256    agcount=32, agsize=30523648 blks
         =                       sectsz=512   attr=2
data     =                       bsize=4096   blocks=976756215, imaxpct=5
         =                       sunit=256    swidth=512 blks
naming   =version 2              bsize=4096   ascii-ci=0
log      =internal               bsize=4096   blocks=476936, version=2
         =                       sectsz=512   sunit=8 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
data size unchanged, skipping

``` with the -d flag only adding the last line about data size being unchanged. It fails equally poorly with no flags at all.

Does anyone have a suggestion as to why I can't expand my partition?

Thanks.

---

### Post by cpufreak2589 on 2013-12-10
Bumping in search of help.

---

