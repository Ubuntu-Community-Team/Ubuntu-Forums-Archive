---
title: "LVM: Two segments of same LV on same disk"
date: 2017-11-10
forum: General Help
---

### Post by super1395 on 2017-11-10
I while ago I transferred my root partition from a HDD to an SSD, and somewhere along the line of using LVM, my SSD, which has holds root and swap, now has two segments of the same LV (root) in it. But the segments are on the same disk. I have no idea how else to explain it, so I hope the console output helps clear it up.

lvdisplay
```
  --- Logical volume ---  LV Path                /dev/xxx-vg/root
  LV Name                root
  VG Name                xxx-vg
  LV UUID                2waY2K-7WKq-hZd0-U1Yh-HSk7-NoUj-YEdPbK
  LV Write Access        read/write
  LV Creation host, time xxx, 2013-08-20 10:04:57 -0600
  LV Status              available
  # open                 1
  LV Size                236.47 GiB
  Current LE             60537
**  Segments               2**
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

```

lvs --segments
```
  LV     VG             Attr       #Str Type   SSize   PE Ranges
  home_1 xxx-vg -wi-ao----    1 linear 465.76g /dev/sdb5:0-119233
  home_1 xxx-vg -wi-ao----    1 linear 931.51g /dev/sda5:0-238465
**  root   xxx-vg -wi-ao----    1 linear  60.00g /dev/sdc5:0-15359**
**  root   xxx-vg -wi-ao----    1 linear 176.47g /dev/sdc5:15808-60984**
  swap_1 xxx-vg -wi-ao----    1 linear   1.75g /dev/sdc5:15360-15807


```

As you can see the root LV is split across two segments, a 60g one, and a 176.47g one, but its all on one disk, sdc5. How can I merge these two segments so I only have one root segment?

---

### Post by DuckHook on 2017-11-10
I am by no stretch of the imagination a LVM expert, but here is my understanding:

LVMs are designed to bridge separate physical segments and treat them as one partition. That's their fundamental essence and reason for being. I have no idea why your SSD split into two physical partitions, but this appears to be what has happened. Consequently, your LVM now bridges both.

You can change it back to one physically contiguous whole by backing up everything, repartitioning your SSD, creating a new LVM structure, then restoring everything to the new structure. I know of no other shortcut. Even if one were proposed, I would worry about its efficacy and danger to my data.

---

