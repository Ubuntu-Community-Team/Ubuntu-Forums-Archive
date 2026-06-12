---
title: "I want my hard drive back"
date: 2006-10-27
forum: General Help
---

### Post by lolwhites on 2006-10-27
The other day I decided to take the plunge and install Ubuntu 6.06 instead of just using the Live CD.

When I got the the penultimate stage (just after saying how much space to allocate to the Linux partition), I cancelled the installation as I had second thought about how much space to give it). Although I hadn't completed the installation, when I rebooted in XP, Windows chkdsk discovered lots of "Errors" on the hard drive, which it corrected. When It started in Windows I discovered that I had lost about 10 Gb of space - I had had 38.8 GB, now I had only 27. When I boot Ubuntu from the CD, it doesn't see the lost space either.

I checked out this thread [http://ubuntuforums.org/showthread.php?t=283376](http://ubuntuforums.org/showthread.php?t=283376) and tried to follow the advice. Unfortunately, although both QTParted and the Recovery Console can see the lost space, I can't work out how to delete it or free it up again; basically I don't get a Delete option when highlight it (QTParted says it's hidden, Recovery Console refers to it as "unallocated".

How can I recover this space?

---

### Post by doobit on 2006-10-27
If it's unallocated, that means that you go to the stage where QParted had shrunk the NTFS partition to make space for a new one, but had not yet created the new partition. To get the space back you need to actually create a new partition there using QParted, Gparted, or some other Parted-like program, or CFdisk, and then format it for your OS of choice. Once you create a partition, you then need to tell the program to write and save the partition table. Then you can use Linux to format it, if you want to install Ubuntu, or boot with the Windows CD with the R option to format NTFS for Windows.
I don't know why there would have been errors unless you didn't defragment first before you began the process.

---

### Post by lolwhites on 2006-10-27
I gave QTParted another go and it let me increase the size of my hda1 partition, so I got my space back after all. I had just been trying to do the wrong thing :oops: Now to defragment and reinstall Ubuntu...

---

