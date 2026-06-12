---
title: "Interesting disk format challenge"
date: 2012-12-31
forum: General Help
---

### Post by nainsurvolte on 2012-12-31
Ok, so I screwed up a partition on 2 disks. But now for some reason, fdisk and parted sees both drives as 512/512, when they should be in fact 512/4096 (logical/physical).

Is there a way without zeroing the partition or removing superblocks to make then 512/4096 again?

Also, I think the drives believe they are twice there size. When I mount the array in which they were, I see way too much partitions. But when I run parted, the partition are right. What can make palimpsest see that much partition when parted an fdisk sees the right ones?

Thanks

---

### Post by nainsurvolte on 2013-01-02
Little update on this one.

I did not found any magical solution. For now, I took advantage to the fact that I have 2 exact same drives that I could use for an experiment. What did I do? I simply formatted the 2 new drives as before, same partition (starting sector and ending sector) and I dd'ed the data from the old ones to the new ones.

For one disk, I ran testdisk on both the one with a 512/512 (Logical/Physical) and the new one 512/4096 and it did not give a big difference. Still in the process to check for the second one.

Although I did found why the drive looked twice its size: partition of the drive is all messed up. It sees HFS partition when I never did such partition and the partitions seems to address sectors outside the drive.

If I don`t have more success with the other one, I will throw the towell and strat fresh for all of them.

---

