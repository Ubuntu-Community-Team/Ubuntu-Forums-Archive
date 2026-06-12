---
title: "Properly connecting and mounting a cell phone via command line"
date: 2015-10-24
forum: General Help
---

### Post by aaronschillings on 2015-10-24
I'm running Kubuntu 14.04 and have been away from my laptop for several months.  I'm having a hard time remembering how to be able to type commands to my phone via the terminal.  When I plug my phone in via usb cable and run lsusb, I can see that the phone is being read.  I just can't remember how to "switch" to the proper mount point to be able to do what I'm trying to do.  Not even sure if this is the right forum for this question, but any help would be much appreciated!

---

### Post by yancek on 2015-10-24
You need to get the device using fdisk with the phone attached and/or using sudo blkid to get the UUID.  It should also show under /media/aaron (assuming your user name is aaron) and you can get the uuid there.  You can then copy files or whatever by using that mount point as the destination.

---

