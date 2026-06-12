---
title: "Partition Types for New Install"
date: 2013-01-13
forum: General Help
---

### Post by cforput on 2013-01-13
I want to set up my laptop to dual boot with Windows Vista,  Ubuntu and a 3rd partition to store my data so regardless of which OS I boot into, I can access my files. I can get the dual boot set up fine. My questions is what is the best type of file system to use for the shared data partition?

Also some directions on how to partition as I get into the GpartEd part of the Ubuntu installation would be appreciated.

---

### Post by john rosswrock on 2013-01-13
> **cforput said:**
> I want to set up my laptop to dual boot with Windows Vista,  Ubuntu and a 3rd partition to store my data so regardless of which OS I boot into, I can access my files. I can get the dual boot set up fine. My questions is what is the best type of file system to use for the shared data partition?

 you can see the link below and choose anyone of the and partion your harddisk [http://en.wikipedia.org/wiki/List_of_disk_partitioning_software](http://en.wikipedia.org/wiki/List_of_disk_partitioning_software)  and intsall ubuntu while in windows... also the third partition you want , make sure it is fat32 as it will be read by both windows and ubuntu easyly

---

### Post by Impavidus on 2013-01-13
Assuming Vista is already installed, make unallocated space on your disk and make sure you have at most three primary partitions (best done using windows tools, reboot a couple of times to give windows chance to run any checks and repairs it deems necessary) and then reboot using a live cd. You can create new partitions using gparted, which is included on the live cd. When installing, you can choose manual partitioning (choose "something else") and run the partition editor from there.

The best option for the shared data partition is NTFS, as Linux can read and write that one as well. Better not write with Linux to the Windows system partition. FAT32 isn't really suited for big modern drives.

---

