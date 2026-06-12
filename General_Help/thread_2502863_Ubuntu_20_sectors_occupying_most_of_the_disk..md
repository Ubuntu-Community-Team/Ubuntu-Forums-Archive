---
title: "Ubuntu 20 sectors occupying most of the disk."
date: 2024-12-03
forum: General Help
---

### Post by ankit2105 on 2024-12-03
Hi, 
Want to ask regarding ubuntu behavior.  I am observing in Ubuntu 20/22 that irrespective of free space in the disk (filesystem), the sectors are almost fully occupied.
Checked using df -h and fdisk -l, because of this behavior I am unable to create a new partition. Trying to find the reason for such behavior and how can this be resolved. 
Looking for ways, where i can create partition without resizing the disk partitions.

---

### Post by ajgreeny on 2024-12-03
Please show us the full output of those two commands to help us as your question is confusing and we do not have enough information.

Please use code tags for terminal output.
See my signature below for a  **code tags** how-to.

---

### Post by grahammechanical on 2024-12-03
> Looking for ways, where i can create partition without resizing the disk partitions.

You want the impossible. It is too late now. 

The only way to do what you want is to set things up right at the very beginning. (1) Start with an empty drive. Use GParted to give the drive a GUID partition Table (GPT). (2) Use GParted to create 2 partitions. a) An EFI System partition (ESP) 500-600 MB in size. b) A Ubuntu partition of a size chosen by you. 3) Leave the rest of the drive as unallocated space. 4) Install Ubuntu using the Manual Install option.

Now there is space in the drive (unallocated) in which to create partitions after Ubuntu been installed. I have done this myself. But when an operating system is installed to a drive and it takes up all the drive space, then the only option is to re-size/move partitions or even delete partitions. I have had to do this in the past when I wanted to dual boot Ubuntu with Microsoft Windows. I have also had to do this when I installed Ubuntu on a drive using the Erase disk and install Ubuntu option (the simple way) and then wanted to dual boot the drive with another version of Ubuntu.

Regards

---

