---
title: "mdadm RAID1 always has dirty bitmap, never flushes."
date: 2018-02-27
forum: General Help
---

### Post by Lin_Mast on 2018-02-27
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial
4.4.0-116-generic #140-Ubuntu SMP Mon Feb 12 21:23:04 UTC 2018 x86_64

I have a couple of mdadm software RAID1 partitions set up on my box.

One in particular always has dirty bitmap blocks that never seem to flush. This partition is formated ext4 and is my main root '/' partition.

```
md0 : active raid1 sda1[0] sdb1[1]
      209584128 blocks super 1.2 [2/2] [UU]
      bitmap: 2/2 pages [8KB], 65536KB chunk

```

and mdadm -X /dev/sd[ab]1 gives:

```
[$ sudo mdadm -X /dev/sd[ab]1
        Filename : /dev/sda1
           Magic : 6d746962
         Version : 4
            UUID : ab78f416:1855040e:afe36e94:25b632c4
          Events : 1272
  Events Cleared : 1272
           State : OK
       Chunksize : 64 MB
          Daemon : 5s flush period
      Write Mode : Normal
       Sync Size : 209584128 (199.88 GiB 214.61 GB)
          Bitmap : 3198 bits (chunks), 5 dirty (0.2%)
        Filename : /dev/sdb1
           Magic : 6d746962
         Version : 4
            UUID : ab78f416:1855040e:afe36e94:25b632c4
          Events : 1272
  Events Cleared : 1272
           State : OK
       Chunksize : 64 MB
          Daemon : 5s flush period
      Write Mode : Normal
       Sync Size : 209584128 (199.88 GiB 214.61 GB)
          Bitmap : 3198 bits (chunks), 5 dirty (0.2%)

```

Is this normal that these dirty blocks never seem to flush?  It doesn't seem to cause any problems, but does anyone know a cause or if there is a solution?

---

