---
title: "Undo Create Partition Table Gparted"
date: 2013-02-20
forum: General Help
---

### Post by angryhomer17 on 2013-02-20
I accidentally created a new partition table  in gparted while attempting to prepare part of the drive for a secure wipe. There were three partitions before I messed up.

/dev/sda1 was a few hundred meg boot/diag partition
/dev/sda2 was a ~10 GB  Win 7 recovery partition

The rest was unallocated free space (this was where I accidentally created a new partition table instead of just creating an empty partition.

How do I recover the first two partitions so I can reset the laptop to factory defaults before reselling?

I'm trying to attempt data rescue (through gparted) right now and it's taking forever. I'm assuming that does the same thing as:

```
gpart /dev/sda
```

[http://www.brzitwa.de/mb/gpart/index.html#help](http://www.brzitwa.de/mb/gpart/index.html#help)

Thanks for the help.

---

### Post by angryhomer17 on 2013-02-20
Brother rescued the partitions with his secret rescue disk from best buy. MRI rescue disk or something.

---

