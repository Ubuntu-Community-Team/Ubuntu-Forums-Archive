---
title: "Odd partitioning problem."
date: 2007-01-22
forum: General Help
---

### Post by Megatog615 on 2007-01-22
I just made a new partition for my home folder. It is a 120GB partition, and it somehow is 69% full(according to df), and according to gparted, it only has 12GB left. My home folder only contains 16.9GB of data. There is something horribly wrong here, and I should have at least 100GB left.

I tried a fsck -f /dev/hdb1(the partiton in question) on the Dapper Live CD and it turned up nothing. Is there a way to fix this without moving my data back to the original root partition and recreating the new home partition?

Besides my home directory, there is nothing else in the partition. What could possibly be taking up so much space, and why is df only reporting 69% full when gparted is reporting somewhere along the lines of 90% full?

---

