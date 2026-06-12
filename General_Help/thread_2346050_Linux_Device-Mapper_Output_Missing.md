---
title: "Linux Device-Mapper Output Missing"
date: 2016-12-10
forum: General Help
---

### Post by cooperjay on 2016-12-10
Hello all:

I'm new to Ubuntu but not completely new to Linux.  I am running the latest Ubuntu Mate LTS Version 16.04.  I have also installed both Fuseext2 and LVM.

I have a Seagate 3TB NAS drive that failed.  I purchased a hard drive enclosure which converts SATA to USB.  I plug in the USB and the system recognizes the drive.  I see all the partitions in gparted.  When I run the command:

sudo parted -l 

I get all the drives listed, but I don't get a linux device-mapper output.  Given there is an LVM2 partition I would expect such an output.  I clearly can't mount the drive without the linux device mapper output.  Can someone please help?

Thanks in advance for any suggestions.

Jay

---

### Post by oldfred on 2016-12-11
Parted does not work on LVM partition, but it should have shown it as LVM?

Do not know LVM, but seen commands like this to mount the LVM:
 sudo apt-get install lvm2
sudo vgchange -ay

---

### Post by cooperjay on 2016-12-13
All:

I eventually re-installed fuse and fuseext2.   I also installed lvm2.  It all worked after that.

Jay

---

