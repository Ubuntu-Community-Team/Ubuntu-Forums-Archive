---
title: "Testdisk - how to add partition"
date: 2008-05-17
forum: General Help
---

### Post by professor-g on 2008-05-17
using testdisk to (try and) recover external harddrive.
Accidentally erased partition - but not the data.

Using testdisk - it goes through both quick and deeper search.
Finds no partition (since I erased it).
It asks me if I want to add a partition.
I go through the steps - adding start and ending cylinders and heads.
Add the type (fat32 - as it was useing used for both windows and linux works)

Nothing happens.

Any ideas?

Thanks in advance,


G.

---

### Post by professor-g on 2008-05-17
In response to my previous queries (figured it out):

You can successfully add the partition by ensuring that you make the starting head = 1.

You should have the following in the partition table :

0 1 1 #### 254 63

#### = dependent on drive size

Also added MBR to the start of the disk.
Now it cant be seen, but still cant be accessed - any ideas ?
This Windows machine is asking me if I want to format it when I want to access the drive.
I doubt I will have any different luck when I put it on my machine (in linux).


Help ?
Thx in advance,


G.

---

