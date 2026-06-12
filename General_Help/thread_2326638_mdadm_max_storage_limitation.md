---
title: "mdadm max storage limitation?"
date: 2016-06-03
forum: General Help
---

### Post by holli73 on 2016-06-03
hello,

i builded a new server with 16x 8TB disks and created a raid10 out of this - this should have given me 64TB on storage
but after the 35h creation when i mount the md device df -h shows only 16TB why?

```
Filesystem                       Size  Used Avail Use% Mounted on
udev                              32G     0   32G   0% /dev
tmpfs                            6.3G  9.7M  6.3G   1% /run
/dev/mapper/vm--server--vg-root  406G  4.0G  382G   2% /
tmpfs                             32G  140K   32G   1% /dev/shm
tmpfs                            5.0M     0  5.0M   0% /run/lock
tmpfs                             32G     0   32G   0% /sys/fs/cgroup
/dev/nvme0n1p1                   472M  101M  347M  23% /boot
cgmfs                            100K     0  100K   0% /run/cgmanager/fs
tmpfs                            6.3G   12K  6.3G   1% /run/user/1000
/dev/nvme1n1p1                   470G   74M  446G   1% /mnt/m.2.ssd
/dev/md0                          16T   24K   16T   1% /mnt/storage
```

this is ubuntu 16.04 in x64 mode:

```
Linux vm-server 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

fdisk shows f.ex:

```
Disk /dev/sde: 7.3 TiB, 8001563222016 bytes, 15628053168 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

from the mdadm it looks the limitation is there?

```
/dev/md0:        Version : 1.2
  Creation Time : Wed Jun  1 07:48:07 2016
     Raid Level : raid10
     Array Size : 17178808320 (16382.99 GiB 17591.10 GB)
  Used Dev Size : 2147351040 (2047.87 GiB 2198.89 GB)
   Raid Devices : 16
  Total Devices : 16
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Fri Jun  3 06:34:27 2016
          State : active
 Active Devices : 16
Working Devices : 16
 Failed Devices : 0
  Spare Devices : 0


         Layout : near=2
     Chunk Size : 512K
```

any idea how i can get the max size with mdadm?

thanks
holli

---

### Post by TheFu on 2016-06-03
According to the reading I´ve done, if you have a 64-bit Linux there is no practical limit on the size with LVM/MDADM.  Something like 8EB.  I´d ask more about the file system used and the limits it may have.

Did you happen to use an old fdisk to make partitions?  A version that doesn´t support GT 2G partitions? I switched to using **parted** a few years ago to ensure a number of things were handled automatically which fdisk didn´t do for a few years.

Of course, you can run mdadm using raw disks (no partitions).

Please post the exact commands used to create the array. I always keep those handy in a text file, so they can be recreated when/if a disk fails.

---

