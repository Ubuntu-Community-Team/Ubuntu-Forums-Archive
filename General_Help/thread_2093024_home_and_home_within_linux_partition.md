---
title: "/home and /home within linux partition"
date: 2012-12-09
forum: General Help
---

### Post by claven123 on 2012-12-09
So, I finally got my ubuntu dual boot to work!!!

During the set up and installation process I installed 12.10 with normal partitions, but I did not set up a separate /home data partition.

Later, during the process I did make a larger /home partition to store data.

The question is this.... how will programs I use know to access the separate /home partition?  Won't the programs want to use the native /home linux partition?



D

---

### Post by oldos2er on 2012-12-09
See [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
You'll need to edit your fstab to mount the newer partition as /home.

---

