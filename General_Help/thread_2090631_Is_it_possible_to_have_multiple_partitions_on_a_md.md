---
title: "Is it possible to have multiple partitions on a mdadm RAID array?"
date: 2012-12-03
forum: General Help
---

### Post by KeithLM on 2012-12-03
A while back I created a RAID 6 array consisting of 5 2TB drives and formatted it with XFS and set up the block and stripe size appropriately.

Yesterday I added two more 2TB drives to the array and it is almost done reshaping the array.  While running that I realized that XFS is optimized for the number of drives, and so far as I can tell there is no way to change that after the fact.  Since I have less than 4TB of data that I need to maintain I thought perhaps I could format the new unused space on the array with ext4, copy the data, then remove the XFS partition and expand the ext4 partition over it.  But is that even possible?  I was viewing the RAID array as a single device and thinking that it had a partition on top of it, but then I realized it wasn't treated that way.

Anybody have any suggestions how to change the file system on the RAID array without losing all the data?

---

