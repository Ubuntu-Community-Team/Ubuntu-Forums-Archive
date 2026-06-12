---
title: "Can't mount RAid1 after upgrade from 15.04 to 15.10 (2x checksum error?)"
date: 2015-11-04
forum: General Help
---

### Post by dobin2 on 2015-11-04
Hi, first time posting :-)

I had a raid1 array with two SSD's, and upgraded from ubuntu 15.04 to 15.10. Now i can't mount it anymore :-( Can't really figure out why, does someone has any pointers?

Seems like the checksums for both drives are bad?


mdadm:
> # mdadm -A /dev/md0 /dev/sda1 /dev/sdb1
mdadm: failed to RUN_ARRAY /dev/md0: Invalid argument

dmesg:
```
[ 3376.528560] md/raid1:md0: active with 2 out of 2 mirrors
[ 3376.528625] md0: invalid bitmap file superblock: bad magic
[ 3376.528629] md0: bitmap file superblock:
[ 3376.528631]          magic: 454c4946
[ 3376.528633]        version: 196656
[ 3376.528637]           uuid: 0d5a50ca.00000000.00010001.00010038
[ 3376.528639]         events: 257
[ 3376.528641] events cleared: 0
[ 3376.528643]          state: 00000000
[ 3376.528645]      chunksize: 512 B
[ 3376.528647]   daemon sleep: 16s
[ 3376.528649]      sync size: 234298880 KB
[ 3376.528651] max write behind: 96
[ 3376.528655] md0: failed to create bitmap (-22)
[ 3376.528762] md: md0 stopped.
[ 3376.528768] md: unbind<sda1>
[ 3376.542241] md: export_rdev(sda1)
[ 3376.542288] md: unbind<sdb1>
[ 3376.562379] md: export_rdev(sdb1)

```
mdadm of sda1:

```
# mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f4a72870:1601857f:0036cff2:943ccb0b
           Name : unreal:0  (local to host unreal)
  Creation Time : Sun Sep 27 15:47:16 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 468597809 (223.44 GiB 239.92 GB)
     Array Size : 234298880 (223.44 GiB 239.92 GB)
  Used Dev Size : 468597760 (223.44 GiB 239.92 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=49 sectors
          State : clean
    Device UUID : b53055c8:03f1a1c6:a7b16325:ac2bbe8e


    Update Time : Thu Oct  8 18:59:26 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 540252a3 - expected 540252a2
         Events : 257




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

```

mdadm of sdb1:
```
# mdadm -E /dev/sdb1/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f4a72870:1601857f:0036cff2:943ccb0b
           Name : unreal:0  (local to host unreal)
  Creation Time : Sun Sep 27 15:47:16 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 468597809 (223.44 GiB 239.92 GB)
     Array Size : 234298880 (223.44 GiB 239.92 GB)
  Used Dev Size : 468597760 (223.44 GiB 239.92 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=49 sectors
          State : clean
    Device UUID : 18f83a74:679fc414:d1f88fc3:a69993c2


    Update Time : Thu Oct  8 18:59:26 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 200c7d8f - expected 200c7d8e
         Events : 257




   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)



```


I initially created it it like this:
```
# mdadm -E /dev/sda1
# mdadm -Cv /dev/md0 -l1 -n2 /dev/sda1 /dev/sdb1 
mdadm: /dev/sda1 appears to be part of a raid array:
       level=raid0 devices=0 ctime=Thu Jan  1 01:00:00 1970
mdadm: partition table exists on /dev/sda1 but will be lost or
       meaningless after creating array
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: /dev/sdb1 appears to be part of a raid array:
       level=raid0 devices=0 ctime=Thu Jan  1 01:00:00 1970
mdadm: partition table exists on /dev/sdb1 but will be lost or
       meaningless after creating array
mdadm: size set to 234298880K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.


```

---

### Post by dobin2 on 2015-11-04
Humm. I did again:

> # mdadm -Cv /dev/md0 -l1 -n2 /dev/sda1 /dev/sdb1 
# luksFormat -c aes-xts-plain64 -s 512 -h sha512 -y /dev/md0

with the same password... all data was still available after a luksOpen... lol!

---

