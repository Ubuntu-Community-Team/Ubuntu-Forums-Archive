---
title: "Btrfs, quota and space usage"
date: 2015-11-23
forum: General Help
---

### Post by el_rico on 2015-11-23
Hello,

I'm having problems determining the space used on my Btrfs FS for each subvolume. I've enabled quota with ```
btrfs quota enable
``` and a rescan with ```
btrfs quota rescan /
```. 

I get strange results (or results I cannot interpret) from ```
btrfs qgroup show /
```:
```

qgroupid         rfer         excl 
--------         ----         ---- 
0/5          16.00KiB     16.00KiB 
0/257         4.11GiB    165.93MiB 
0/258       188.70MiB     73.09MiB 
0/265        16.00KiB     16.00KiB 
0/266       596.35MiB    596.35MiB 
0/267        16.00KiB     16.00KiB 
0/268       428.00KiB    428.00KiB 
0/269         4.04GiB    100.62MiB 
0/270       137.70MiB     22.09MiB

```

The exclusive size is to me obviously wrong: volume 0/257 is my root subvolume (not a snapshot of anything): exclusive space should be the whole space. Same for 0/258 (/home subvolume). For the other ones, it's more coherent (e.g. 0/266 which is /var/cache).

What am I doing wrong (I suspect a common beginner issue...)? Is there a way to understand what's happening?

Thanks!

---

