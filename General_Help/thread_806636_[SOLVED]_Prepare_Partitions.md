---
title: "[SOLVED] Prepare Partitions"
date: 2008-05-25
forum: General Help
---

### Post by Jack Shankle on 2008-05-25
Hi, Hope this is being posted in the correct place.

Hardware - Dell T3400 - 2g ram - 80G hard drive
Software - Windows Vista Business
           System Commander by Avenquest (partition creation
                                          software)

I already have 2 Windows Vistas installed. I used System Commander to partition the drive. The 1st partition is 25G, the 2nd partition is 23g and the free space is 23G and empty. I have downloaded the Desktop version of Ubuntu 8.04 and created a live CD. This all worked fine. 
Got to the "Prepare Partition" screen:
     /dev/sda
     /dev/sda1   fat16       57m      33m
     /dev/sda2   ntfs      1283m    1100m
     /dev/sda3   ntfs     27266m   19900m
     /dev/sda4   ntfs     24116m   13500m
     unusable             27275M

Anything I select gives the following message:
   "No root file system is defined"

I would think the place to put Ubuntu would be the unusable partition. Hope someone can help. Thanks.

---

### Post by sdennie on 2008-05-25
I believe you can only have 4 primary partitions on a disk.  The /dev/sda1 and /dev/sda2 partitions are probably Dell mediadirect or restore disks so, if you know you won't need them (and, I mean you really know it), you could delete one or both to free a spot for the linux partition (you'd have to make extended/logical partitions if you only deleted one of them).  However, you may have to use gparted to physically move the ntfs partitions on the disk because of where the free disk space is likely located (I'm not positive about this though).  If that's the case, it will probably take several hours to move the partitions.

---

### Post by Jack Shankle on 2008-05-25
Here is what I did to make the install work in my configuration.

I uninstalled the "Recovery Partition". Since it was at the beginning of the drive and I had plenty of space, I did not have to relocate the partitions. I also turned off the System Recovery in Windows. I have a much better recovery system from Acronis True Image and don't need the duplication.

This reduced the Primary Partitions to 3 and I was able then to install Ubuntu.
Hope this helps somebody.

---

