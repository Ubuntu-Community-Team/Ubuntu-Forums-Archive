---
title: "create partition"
date: 2006-07-28
forum: General Help
---

### Post by mathon on 2006-07-28
hello,

I want to change the swap partition which is the device /dev/hda6 with 514007MB on my system:

I want to make two partitions from this swap partition with equal size (so each partition should then have half of the 514017 MB), one should be formatted with ext3 and the other should be the swap partition.

I want to use fdisk for that. I think first I have to switch off the swapp partition and then I have to remove this swap partition and then create two new and format the new partitions with the filesystem.

But how can I remove with fdisk this swap partition and create two new one each with 257008 size and one with ext3 filesystem and one with swap? :confused: 

Regards

---

### Post by rbalfour on 2006-07-28
Boot your computer up with the Dapper install CD when you get to the Desktop
Use. System > administration > Gnome Partition Editor

You can't resize mount partition. Besides, this is the easy point and click way..

---

### Post by mathon on 2006-07-28
But I would like to learn it how it works from the console. Do you know that too? :(

---

