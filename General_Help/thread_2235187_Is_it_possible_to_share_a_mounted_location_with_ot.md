---
title: "Is it possible to share a mounted location with other computers"
date: 2014-07-19
forum: General Help
---

### Post by greavette on 2014-07-19
Not sure if I've described what I want to do properly in the Subject...here's the scoop:

I'm using Berryboot. I've created an image based on Debian and it's working well. But here's what I want to accomplish.

From within the running Debian image running on Berryboot, I can mount where the Berryboot images are using this code:
$ sudo mount /dev/mmcblk0p2 /mnt
$ ls /mnt/images

Now I want to share my /mnt folder with my other computers in the house (Windows/Linux Computers). My plan is to build a new image on the Windows Computer. Connect from the Windows Computer to the share (/mnt) on the Debian Computer. This way when my new image is made I simply copy the new image to the /mnt/images folder...I update the default file in /mnt/data to use my new image that I've just copied. I reboot and now use the new image I've just put on Berryboot.

So I know I can mount the /dev/mmcblk0p2 folder already.  Not sure how to mount this at start but I'm assuming I would add a line to /etc/fstab.  But then how to I make this /mnt location shared for my computers on the network to access?  Is this possible?


Thoughts? Would this work for me?

---

### Post by yancek on 2014-07-19
I have no idea what "BerryBoot" is or does but the common way to share files on different Linux computers is 'nfs', netword file system and from Linux to windows 'samba'.  There are an incredible number of tutorials on both so just do an online search and look for something detailed enough that you understand.

---

### Post by greavette on 2014-07-19
Thank you for the reply.  For simplicity sake lets say I have a USB stick put into my linux computer.  What I'm looking for is confirmation that I can successfully do the following two steps:

First mount the USB drive to /mnt
Then share that mounted /mnt folder.

I've done both individually but never together.  And I would set it up to be done one after another (first mount then share it).  Is this going to work on a regular (past a reboot if setup at start) basis as long as, in this example, the USB drive is seen.  Or is this going to fail?

Or is it possible to setup in one step instead of two to share that usb stick directly.  If so, what is the instruction to do that?  


Thank you.

---

### Post by yancek on 2014-07-19
You can create a mount point under mount for your usb, for example:  mkdir /mnt/flash  You can then export that partition in nfs with an entry in the /etc/exportfs file.
To have it permanent, you can put an entry in the /etc/fstab file for that partition.

Some possible problems in trying to do this automatically could happen if you use a different flash drive, if you use multiple flash drives simultaneously or plug the flash into a different usb port.  All potentially create complications.

You could create the mount point and then have a simple bash script to mount rather than having an entry in fstab.  Depends on whether you expect to be regularly using multiple flash drives simultaneously.

---

### Post by kurt18947 on 2014-07-19
I wanted to do something similar with a USB drive.  I found a router with a USB port that can function as a USB print server or storage.  I configured the router as an extender and can access storage devices plugged into the USB port.  This model - Western Digital N600 and all Western Digital routers are discontinued so even though they can still be found I wouldn't recommend one.  I also was not able to read & write directly using Nautilus but Filezilla works perfectly.  Win 7 saw the storage in explorer.  Just another possiblity.

---

