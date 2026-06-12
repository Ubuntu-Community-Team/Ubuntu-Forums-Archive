---
title: "error unmounting /dev/sdb5: target is busy (udisks-error-quark, 14)"
date: 2020-11-04
forum: General Help
---

### Post by sliwkahax on 2020-11-04
Hi, i was trying to resize the disk cuz i wanted to have one partition.
Whenever i try to resize this error pops out.

[h=1]error unmounting /dev/sdb1: target is busy (udisks-error-quark, 14)[/h]Can i forcibly unmount the disk without any damage happening to the pc?

---

### Post by Impavidus on 2020-11-04
You cannot unmount a partition when it's in use. So stop whatever is using it, or at least make sure those applications no longer use that partition. Note that the partition where the currently running operating system is installed is always in use, so you cannot unmount that. If you want to resize that, use a live disk.

---

### Post by ajgreeny on 2020-11-04
It's impossible to know with the little information you have given us.

Let's see the output of command ```
sudo fdisk -l ;mount
``` as I suspect you are trying to resize partitions that are mounted and/or in use.

You can not change partitions of the OS you are currently using and it is most commonly done using a live USB system. 
All the *buntu family of OSs have gparted in the live USB so you can probably use the USB you used to install the system, assuming you installed it in the first place.

---

### Post by sliwkahax on 2020-11-04
I wanted to make 2 partitions, one for linux, one for windows.
I have one partition rn the one for linux.
Whenever im in the windows installation i can't make a partition out of the linux drive cuz it says that its an unknown type.
Is there a way to make a partition?
Thanks.

---

### Post by CelticWarrior on 2020-11-04
You don't need to "make a partition" for Linux and certainly not from Windows. You can, from Windows, shrink Windows partitions to make room for another OS. The installer will then use that unallocated space to create the partitions it needs.

---

### Post by ajgreeny on 2020-11-05
Even if you do create a partition in Windows it will probably be unusable for Linux as Windows generally creates dynamic partitions which are completely useless for Linux.

As CW says, just leave the space unallocated and the Ubuntu installer will find it and can be pointed to it very easily by using the "Something Else" option, ie, manual partitioning, when you get to that stage of installing.

---

