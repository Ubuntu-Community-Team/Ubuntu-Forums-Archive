---
title: "Home directory switches to read only when copying a large folder from C drive"
date: 2013-05-30
forum: General Help
---

### Post by Dugachug on 2013-05-30
This hasn't happened in older versions but happened twice while copying a 3.5gb folder from my windows partition. Is this a known bug?

---

### Post by efflandt on 2013-05-30
Whenever a partition remounts read-only it is likely because the system is having trouble reading it, and it is just trying to protect you from corrupting the partition.

Check the tail end of dmesg for any disk related errors (type **dmesg** in a terminal). Or if you want to scroll through dmesg, use **dmesg | less** (the thing in the middle is a vertical bar or pipe, to pipe it to less).

While hard drive failure can be rare, it can happen. Many years ago I had a 2.5 GB drive begin to fail when it got more than 3/4 full. More recently Ubuntu on the last 100 GB of a 3 year old 1 TB drive began remounting read-only due to errors. Bits near the center of disks are physically smaller and more packed together due to the smaller diameter there, so that can be most difficult for a marginal drive to read. Drives automatically map good sectors in place of bad sectors (independent of the OS), but once all the error sites are used up, the drive can only get worse.

I managed to fix it for awhile using e2fsck with the switch to test and lock out badblocks (from separate SSD drive), but eventually Linux started spontaneously mounting read-only again. Win7 was on a part of the drive that did not have issues yet (and I had already shrunk it to make more room for Linux), so I used Acronis to image the OEM and Win7 partitions to transfer to a new drive. 64-bit Ubuntu 12.04.2 I installed fresh on a 250 GB partition and copied over my old /home dir using an eSata caddy (about 80 GB) without issue.  So there should be no general issues copying large or many files between partitions or drives in Linux.

---

