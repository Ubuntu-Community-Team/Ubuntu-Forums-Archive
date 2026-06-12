---
title: "resizing ubuntu partition"
date: 2007-07-12
forum: General Help
---

### Post by Nessa on 2007-07-12
my Ubuntu owns an 80GB drive. All of it. I want to make ubuntu smaller but I run into an error using the ubuntu live cd. I don't have a cd writer so I can't burn the Gparted cd. What are my other options?

---

### Post by bdtgp on 2007-07-12
You can try the GNOME Partition Editor.  Its located here:

Applications>Add/Remove and then in All Open Source Applications (upper right drop down menu) then scroll down till you see it.  It can be a useful tool.

---

### Post by Nessa on 2007-07-12
I've already tried that. It seems that you can't partition a mounted drive and you can't unmount the drive where the OS is running.

---

### Post by merlinus on 2007-07-12
I do not believe this will work.  You cannot resize a mounted partition, and since nessa's installation uses the entire disk, it cannot be unmounted.

Seems strange, however, that the partitioner on the live cd will not work.  Did you try resizing from right to left?  Were there any error messages?

-merlin

---

### Post by Nessa on 2007-07-12
Right to left... I don't think so. The data is on the leftmost portion of the partition. Will that be ok?

---

### Post by merlinus on 2007-07-12
You should definitely back-up any important data before doing any kind of partitioning.  One never knows....

But depending upon how much of the 80G you want to free up, should be no problem.

Good luck!

-merlin

---

### Post by Nessa on 2007-07-12
Not much to back up. Just installed it yesterday. Will give it a go. Thanks! :)

---

### Post by Nessa on 2007-07-13
Can't resize it from right to left. 

After resizing the partitions. I did notice the the drive was somehow re-mounted. So I unmounted it again and was able to resize the partitions.

Mission accomplished. Thank you all!

---

