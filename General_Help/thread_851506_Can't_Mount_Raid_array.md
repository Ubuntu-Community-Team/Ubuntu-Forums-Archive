---
title: "Can't Mount Raid array"
date: 2008-07-06
forum: General Help
---

### Post by kublikhan on 2008-07-06
I recently upgraded from Ubuntu 7.1 to 8.04. I also upgraded to a new machine, moving my software raid5(3 drives) to the new machine and reinstalling the OS fresh(OS drive is separate from raid array). However I can no longer mount my raid array. mdadm reports the array is active with a status of clean, but mount reports bad superblock/bad magic number. It's been awhile since I setup this array and I'm not even sure I remember what the file system was. I think it was xfs, but just to be sure I also tried every other filesystem listed in proc/filesystems. None of them worked. I even tried booting off of the Ubuntu 7.1 and 8.04 livecd's and mounting there and it did not work. Here's the output of various utils I ran:

fdisk -l:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 3220 MB, 3220438528 bytes
255 heads, 63 sectors/track, 391 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf40017e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         367     2945336   83  Linux
Partition 1 has different physical/logical endings:
     phys=(366, 254, 63) logical=(366, 173, 46)
/dev/sdd2             368         388      163852    5  Extended
Partition 2 has different physical/logical endings:
     phys=(390, 0, 63) logical=(387, 101, 41)
Partition 2 does not end on cylinder boundary.
/dev/sdd5             368         391      192748+  82  Linux swap / Solaris

Disk /dev/md0: 2000.4 GB, 2000409329664 bytes
2 heads, 4 sectors/track, 488381184 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System



mdadm -D /dev/md0:
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Dec  8 06:47:10 2007
     Raid Level : raid5
     Array Size : 1953524736 (1863.03 GiB 2000.41 GB)
  Used Dev Size : 976762368 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul  6 22:05:48 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           UUID : 6eb76328:0a457049:b4334d25:7342fff0
         Events : 0.8

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc


mount -t xfs /dev/md0 /beast
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

last section of dmesg:
[  791.136907] raid6: int32x1    412 MB/s
[  791.204950] raid6: int32x2    436 MB/s
[  791.272801] raid6: int32x4    415 MB/s
[  791.340701] raid6: int32x8    300 MB/s
[  791.408667] raid6: mmxx1      873 MB/s
[  791.476580] raid6: mmxx2     1616 MB/s
[  791.544565] raid6: sse1x1     805 MB/s
[  791.612453] raid6: sse1x2    1265 MB/s
[  791.680406] raid6: sse2x1    1302 MB/s
[  791.748301] raid6: sse2x2    1685 MB/s
[  791.748305] raid6: using algorithm sse2x2 (1685 MB/s)
[  791.748310] md: raid6 personality registered for level 6
[  791.748313] md: raid5 personality registered for level 5
[  791.748316] md: raid4 personality registered for level 4
[  791.756849] raid5: device sda operational as raid disk 0
[  791.756857] raid5: device sdc operational as raid disk 2
[  791.756861] raid5: device sdb operational as raid disk 1
[  791.759114] raid5: allocated 3170kB for md0
[  791.759119] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
[  791.759123] RAID5 conf printout:
[  791.759125]  --- rd:3 wd:3
[  791.759128]  disk 0, o:1, dev:sda
[  791.759131]  disk 1, o:1, dev:sdb
[  791.759134]  disk 2, o:1, dev:sdc
[ 2763.850899] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[ 2763.856024] SGI XFS Quota Management subsystem
[ 2763.859398] XFS: bad magic number
[ 2763.859404] XFS: SB validate failed

xfs_check /dev/md0:
xfs_check: unexpected XFS SB magic number 0xeb489042
xfs_check: size check failed
xfs_check: read failed: Invalid argument
xfs_check: data size check failed
cache_node_purge: refcount was 1, not zero (node=0x80dd670)
xfs_check: cannot read root inode (117)
cache_node_purge: refcount was 1, not zero (node=0x80dd810)
xfs_check: cannot read realtime bitmap inode (22)
Segmentation fault

---

### Post by kublikhan on 2008-07-08
Incase anyone else runs into this problem, I managed to resolve the issue. The filesystem was indeed XFS and I was able to repair the superblock with xfs_repair /dev/md0. I recommend trying this first to see if you can mount. This was insufficient for me as my log was damaged as well. I had to run repair again with: xfs_repair -L /dev_md0. Note: THIS MAY CAUSE DATA CORRUPTION! Only do this as a last resort. But since I tried everything else and was about to give up, I had nothing else to lose. Success! I can finally mount the file system. There was about a dozen files in the "lost+found" directory, presumably those are corrupted and unrecoverable files. But at least I got back the majority of my data. I still do not know what damaged my file system in the first place. Could be some file corruption issue with Raid 5 and XFS. Could be from an unclean mount, like hard powering off the machine instead of a clean shutdown(I did this a few times, Doh!).

---

