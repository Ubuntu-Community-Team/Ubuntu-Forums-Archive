---
title: "Technical Partitioning Question"
date: 2013-01-30
forum: General Help
---

### Post by Sutur on 2013-01-30
Hello,

I have about 180Gb of data on an apple laptop, and I want to copy it all to my ext3 external HDD.

Apple won't write to ext3 faster than 600Kb/s, which is woefully slow and probably quite unsafe.

My solution is this:

[LIST=1]
[*]Create an apple partition on the external drive.
[*]Copy the data from the laptop to that partition.
[*]Copy the data from the apple partition to the ext3 partition with a *real* OS.
[*]Format the apple partition as ext3 and then merge it back again.
[/LIST]

Is the above plan the safest method of getting my files off this horrible MacBook, as I have no backup of the data currently on the drive...

---

