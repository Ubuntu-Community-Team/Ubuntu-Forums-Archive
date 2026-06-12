---
title: "Expanding Windows Partition"
date: 2008-01-24
forum: General Help
---

### Post by Wan_Lin on 2008-01-24
Hi, when installing Ubuntu I misread the slider instructions in the install disc partitioning screen, making my Windows XP partition smaller than desired. I would like to make it bigger.

I have used GParted to repartition my Ubuntu partition smaller, leaving me with a large chunk of Unallocated Space. With GParted (using the GParted Live CD) I can increase the size of my Ubuntu partition into this space, but not my Windows XP partition.

How can I merge the unallocated space with my Windows XP partition?

Here is a screenshot of the GParted screen I see (taken from Ubuntu but it's the same in the GParted Live CD):
[IMG]http://img85.imageshack.us/img85/3594/screenshotqy1.png[/IMG]

The Windows partition is sda2. Can I not increase the size of the partition with the editor because it is not adjacent to the unallocated space (the Ubuntu partition, sda3, is between them)?? If so, how do I switch the places of sda2 and sda3? Please note I have 4 "primary" partitions and cannot make any more (I have the swap partition, windows, ubuntu, and a recovery partition which was built in to my sony laptop i am using).

Thanks very much in advance!

---

### Post by chewearn on 2008-01-25
Boot into liveCD, then you can move your ubuntu partition "upward" until it's flushed to the swap (make sure it's unmounted, else it's locked from changes); then the free space will be next to the winxp partition.  You should now be able to resize winxp partition.

---

### Post by Wan_Lin on 2008-01-25
thanks! that worked perfectly. currently switching stuff around now

---

