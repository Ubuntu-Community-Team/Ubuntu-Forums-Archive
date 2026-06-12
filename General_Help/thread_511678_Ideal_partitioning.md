---
title: "Ideal partitioning"
date: 2007-07-28
forum: General Help
---

### Post by vishzilla on 2007-07-28
hi,
I want to know what is the ideal partitioning that should be done for my ubuntu. I've heard suggestions for keeping a separate /usr or /boot or /home partition. I also have xp installed. How should i partition ubuntu if i've the following 80 GB hard-drive configured
Primary Partition: NTFS for XP (28 GB)
Logical Partition: NTFS for XP (14 GB)
Rest of my HD space: Unallocated

Please help

---

### Post by Smu on 2007-07-28
If you tend to keep your NTFS partitions I'd make 3 new Ext3 partitions on the unallocated space:

7Gb -  /
1Gb -  Swap
30Gb -/home

---

### Post by az on 2007-07-28
Just use the installer as your drive is.  You will be offered the option of using the free space.  The installer will create a / and a swap for you.  You don't need anything else.  You don't run the risk of running out of space that way.  You have no need to put any directories on separate partitions.  It may be needed for some systems, but not on a desktop.

Some would insist on a separate home, but I think it's more trouble that benefit.  It was a lot more useful ten years ago, when there were not so many desktop applications used and drive space was more expensive.  Today, it is just a lot simpler and safer to keep a proper backup the conventional way (CD, DVD or separate hard disk).

---

