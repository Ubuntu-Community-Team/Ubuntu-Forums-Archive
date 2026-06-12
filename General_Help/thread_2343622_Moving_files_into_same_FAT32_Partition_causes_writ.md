---
title: "Moving files into same FAT32 Partition causes write byte by byte"
date: 2016-11-17
forum: General Help
---

### Post by Marco_Ros on 2016-11-17
Hello,
I have noticed that Moving files into the same FAT32 Partition (flash memory, causes writing the file byte by byte, as if I were copying it, making the process extremely slow.
In general, moving a file into the same partition, only updates the FAT without actually moving the file into another group of clusters into the partition.

UBUNTU 16.04 LTS /64BITS
Intel® Core™2 Duo CPU T7300 @ 2.00GHz × 2 
Intel® 965GM

---

### Post by DuckHook on 2016-11-18
Flash ROM like USB sticks, flash cards, etc, do not access the file table the same way as hard disk media. To reduce write fatigue, flash memory uses algorithms so that writes are allocated evenly across the physical substrate. A simplistic algorithm could end up rewriting each move, rather than simply fiddling with the File Allocation Table, which is, after all, just a virtual allocation table on flash media. Different USB sticks use different algorithms. These algorithms are hardwired into the USB stick controller and cannot be changed. You might get better results with a different USB stick/flash card that has a more intelligent algorithm.

---

