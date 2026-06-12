---
title: "Harddrive size and mounted partition"
date: 2007-08-06
forum: General Help
---

### Post by Nordkraft on 2007-08-06
Hi there!

I've recently installed a new hd on my computer. The size of the drive is 250 GB of which I have made a ext3 partition of 210 GB for use with my Ubuntu installation. When I made the partitioning (have tried both GPartEd and fdisk) I assigned the 210 GB to the partition but when I mount the partition afterwards, 10 GBs seem to dissappear! I know that the formatted size of hds are lower than the factory listing of the size, but I've not heard of hd space dissappearing when mounting. Any info or suggestions?

Cheers!

---

### Post by mcduck on 2007-08-06
> **Nordkraft said:**
> Hi there!

I've recently installed a new hd on my computer. The size of the drive is 250 GB of which I have made a ext3 partition of 210 GB for use with my Ubuntu installation. When I made the partitioning (have tried both GPartEd and fdisk) I assigned the 210 GB to the partition but when I mount the partition afterwards, 10 GBs seem to dissappear! I know that the formatted size of hds are lower than the factory listing of the size, but I've not heard of hd space dissappearing when mounting. Any info or suggestions?

Cheers!

5% of disk space is reserved for root user only. If it's not your system disk you can adjust the limit with tune2fs command. Also the filesystem itself needs some space for journaling etc.

---

### Post by Nordkraft on 2007-08-06
Cheers for the answer!

It's not my system disk in fact, just a storage area so to speak. I'll try to use tune2fs then and set the reserved blocks percentage.

---

### Post by Nordkraft on 2007-08-06
worked like a charm...

---

