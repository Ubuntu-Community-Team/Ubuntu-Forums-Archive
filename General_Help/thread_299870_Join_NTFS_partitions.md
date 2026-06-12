---
title: "Join NTFS partitions"
date: 2006-11-14
forum: General Help
---

### Post by heinouskyle on 2006-11-14
I'm trying to join two NTFS partitions with GParted, and it seems that's the only thing I can't do. I have NTFS read/write support installed (ntfs-3g). I can make and delete partitions, but I can't resize or join them.

Thank you for any help.

---

### Post by dcstar on 2006-11-15
> **heinouskyle said:**
> I'm trying to join two NTFS partitions with GParted, and it seems that's the only thing I can't do. I have NTFS read/write support installed (ntfs-3g). I can make and delete partitions, but I can't resize or join them.

Thank you for any help.

You cannot "join" partitions with any tool, you will have to copy the data off one of them, delete it and then resize the remaining NTFS partition into adjacent free space (with another tool, possibly).

Then copy the saved data from the other partition.

---

### Post by zgornel on 2006-11-15
> **dcstar said:**
> You cannot "join" partitions with any tool, you will have to copy the data off one of them, delete it and then resize the remaining NTFS partition into adjacent free space (with another tool, possibly).

Then copy the saved data from the other partition.
Actually, if I remember, Partition Magic allowed you to join partitions: the contents of one became a folder of the newly resulted partition. I don't think ntfs is supported at that scale in linux.

---

### Post by heinouskyle on 2006-11-15
Gparted won't let me move or resize the partition either. It's getting quite annoying. I tried Partition Magic and it really messed things up. I had to boot from a live cd and reinstall GRUB.

---

