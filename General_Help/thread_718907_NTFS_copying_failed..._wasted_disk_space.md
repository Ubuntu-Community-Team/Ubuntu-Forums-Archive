---
title: "NTFS copying failed... wasted disk space"
date: 2008-03-08
forum: General Help
---

### Post by arrow15 on 2008-03-08
Hi,

I tried to copy an ISO from my external NTFS drive to my windows NTFS partition in kubuntu. I've had no real problems in the past copying files between these two drives. The copy seemed to finish, but there is no file to be found in the windows partition. I cannot see it under kubuntu, nor can I see it under Windows, yet it is eating up over 4 GB of hard drive space (the free space count is significantly lower than before the copy). Is there any way for me to get rid of this missing file, or am I basically screwed into formatting the entire drive?

Thanks.

---

### Post by Super TWiT on 2008-03-09
Try booting into windows, right clicking on the drive that has the wasted space selecting properties, clicking on the tools tab, and selecting check disk.   Then, check the box that says something like check for file system errors, and click start.  You may also want to check the box that says Scan for and attempt recovery of bad sectors.  This will ensure that none of the sectors were corrupted.   It will say that it needs to start next time you boot windows, so you will need to reboot to start the scan.

---

