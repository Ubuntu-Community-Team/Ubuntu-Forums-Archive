---
title: "LVM on RAID Failing"
date: 2005-03-21
forum: General Help
---

### Post by tonym on 2005-03-21
Until recently I was running a Hoary AMD system with LVM physical volumes on a RAID1 device.  Recently I have been seeing some strange behaviour - getting messages saying there are duplicate PV's and only one is being used.

What appears to be happening is that LVM is starting before RAID and finding the two RAID mirror partitions separately.  It correctly identifies thay have the same ID and only activates one.  Thus LVM is running on one of the mirrors only and updates one only leading to corruptions.

This appears to have started with the 2.6.10 kernel but I'm not 100% sure.

Regards

Tony Middleton

UPDATE:  I now believe that this is caused by [Bug 5421](https://bugzilla.ubuntu.com/show_bug.cgi?id=5421)

---

### Post by tonym on 2005-04-04
As a result of the above I've now switched to using EVMS and that appears to work fine,  so far.

---

