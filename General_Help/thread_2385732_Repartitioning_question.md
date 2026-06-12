---
title: "Repartitioning question"
date: 2018-02-23
forum: General Help
---

### Post by faiuwle on 2018-02-23
I have a dual boot laptop running Ubuntu in an ext4 partition and Windows 7 in an NTFS partition. I gave Ubuntu 50 Gb and figured that would be fine, but I discovered a game I installed needs a lot of space and is taking up a lot of that partition.  I have over 300 Gb free on my Windows partition, so I would like to move over another 50 or maybe 100 Gb to Ubuntu.  Gparted shows the partitions being next to each other (although the ext4 partition is in an extended partition, and the NTFS partition is not).  I seem to recall, when I first got this computer there was something weird going on with the partition table due to there being a factory-installed recovery partition for Windows, and Windows not having cleaned up after itself properly when partitioning.  From what I remember, the advice I got here was to use the Windows 7 partitioning utility to partition the disk for use with Ubuntu, and I believe that was what worked.  What I want to know is, can i use the Windows 7 partitioning utility to move disk space from one partition to the other, without screwing up my Ubuntu installation?

---

### Post by RobGoss on 2018-02-24
You would have to use the **Windows partition tool** to resize the Windows partition to give the **Ubuntu** partition more space, then boot your machine up using the live desktop and use Gparted to reclaim the unallocated space.

Please refer to this tutorial for guidance
[https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions](https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions)

Make sure you have everything completely backed up just in case something goes wrong and a recovery disk for Windows

---

### Post by faiuwle on 2018-02-24
Ok, thanks, I'm pretty sure I know how to do that.  I as said, the recovery for Windows on this computer is a recovery partition, rather than a disk.

But I definitely remember having trouble using gparted before because of whatever Windows did to the partition table, so I guess if that doesn't work I will post here again.

---

### Post by HermanAB on 2018-02-25
Backup, backup, backup...

---

