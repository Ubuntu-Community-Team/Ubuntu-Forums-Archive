---
title: "partition to backup my files?"
date: 2007-10-27
forum: General Help
---

### Post by vishzilla on 2007-10-27
I want to have a separate partition (not /home partition) to backup my personal files. I'm pretty confused!!!

---

### Post by Shazaam on 2007-10-28
You could use the Ubuntu livecd to shrink a partition to make room. Once you do that make a new ext3 partition in the unpartitioned space. Then you would use whatever backup solution you want. Just point it to the new partition. I have used "Simple Backup Restore" (in the repos) with a 10gig backup partition on another drive.

Partitioning info....
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

