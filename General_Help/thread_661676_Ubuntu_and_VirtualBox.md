---
title: "Ubuntu and VirtualBox"
date: 2008-01-08
forum: General Help
---

### Post by feralin on 2008-01-08
I'm trying to install the latest version of Ubuntu on VirtualBox but I keep getting** the creation of swap space in partition #5 of SCSI1 (0,0,0) (sda) failed.** after partitioning in setup and can't figure out the solution to installing.  I have tried setting up a partition, swap space and a 254 megabyte partition manually but nothing seems to be working.

Any ideas?

---

### Post by mokshadaya on 2008-01-08
Well, there are several questions that I would begin with.  The first is why you would be doing any sort of partitioning when you are installing Ubuntu in VirtualBox.  VirtualBox will turn the OS into a file that can reside anywhere on your machine, no partitioning is needed.

Also, are you already at the limit of 4 primary partitions?  You can go crazy with logical partitions, however, you are limited with primary partitions.

Does this help?

---

### Post by Wiifreak on 2008-01-08
So you have Ubuntu.
Inside Ubuntu VirtualBox
Want to install New Ubuntu in VirtualBox.

Then you should create a new Virtual machine.
Recomended: 2,5 GB disk (deside yourself how much RAM)
Start the Virtual machine and mount the CD-ROM/ISO file.
Only create 1 partition for install and 1 swap (about 256-512MB)
Then set mountpoint on first partition (hda1) to "/".
Now try to install.
If this don't works, place al the errors and settings here.

---

### Post by feralin on 2008-01-08
Okay, we'll the setup seems to be running now that I only made one partition for the install and 1 for the swap.  I'm not sure what I was doing wrong before but the problem seems to no longer be in exsistent.  

31 percent!!!  It hasn't gotten this far before.  

Thanks for both replies.

---

