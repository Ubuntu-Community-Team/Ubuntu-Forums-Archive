---
title: "Problem with partitions"
date: 2007-04-20
forum: General Help
---

### Post by tetrisj on 2007-04-20
Hi,
I run a dual boot system with all 3 partitions (ntfs,ext3,swap) on the same HD.
Recently I needed more space for Ubuntu. so using PartitionManager:
- I created a new partition from the free space at the end of my ntfs partition
- I resized the ext3 partiotion so it will contatin the free space.

Now my ext3 partition is 1GB larger but the free space is the same.
When i check the disk space using the disk space analyser it shows the 'capacity' is still the same it was before.
When I check the partition with gparted it shows the newly added space as part of the used space and so does Partition Magic.

Someone here knows if there is  something i can do to recover that lost space?
(besides reformatting the partition :) )

---

### Post by indytim on 2007-04-20
Get a copy of GParted Live.  Boot to it and do your partition updates from a non-ops boot state.

[GParted]("http://gparted.sourceforge.net/index.php")

IndyTim

---

### Post by tetrisj on 2007-04-20
What changes should i do to the partitions?
The free space somehow dissapeared inside my ext3 partition.
It's as though the partition is larger but Ubuntu dosn't know it.....

---

### Post by tetrisj on 2007-04-20
Someone, please?

---

