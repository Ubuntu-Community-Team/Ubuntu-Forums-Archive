---
title: "Is it possible to shrink/split a ZFS zpool?"
date: 2017-11-06
forum: General Help
---

### Post by danik56 on 2017-11-06
I have a 512GB SSD drive used entirely by a single ZFS zpool.
The zpool was originally created in partition /dev/nvme0n1p4.  The drive has a single partition.
ZFS status output:

root@ZITO-UBUNTU:/home/danik56# zpool status -v
  pool: zpool1
 state: ONLINE
  scan: scrub repaired 0 in 0h1m with 0 errors on Sun Oct  8 00:25:23 2017
config:


    NAME         STATE     READ WRITE CKSUM
    zpool1       ONLINE       0     0     0
      nvme0n1p4  ONLINE       0     0     0

The pool is mostly empty:

root@ZITO-UBUNTU:/home/danik56# zfs list
NAME                       USED  AVAIL  REFER  MOUNTPOINT
zpool1                    36.3G   394G    19K  /zpool1

My question is, whether it is possible to split the SSD into 2 zpools, shrinking ZPOOL1 into a smaller partition and allocating ZPOOL2 in the free space.
Would the SPLIT command do the trick ?

Thanks in advance...Dani Kalmar

---

