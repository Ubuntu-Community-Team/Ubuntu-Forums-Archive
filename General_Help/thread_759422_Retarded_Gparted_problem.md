---
title: "Retarded Gparted problem"
date: 2008-04-19
forum: General Help
---

### Post by OoooMatron on 2008-04-19
I am trying to clean up some space on the beginning of the drive and want to delete a logical parititon but it won't let me because my root driver has a higher logical number than it and I must umount all logical drivers higher :confused:

Can't believe this is a problem in this day and age. Even partition magic could handle this stuff 10 years ago.

Why should I have to boot the live cd to achieve this?

---

### Post by Rocket2DMn on 2008-04-19
Logical partitions are a little different than normal partitions, they are handled more in software than in hardware.  The partitions cannot be mounted when you fiddle with them, so that is why we need either the LiveCD or the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
I think the Ubuntu LiveCD mounts the swap space which can cause problems, so you have to either unmount swap from the LiveCD or just use the GParted LiveCD.
If you are using a partition under a logical partition, I don't think you can delete the logical/extended partition without deleting everything that falls under it (can't convert to physical).

---

### Post by CyberCeed on 2008-04-19
I always use Parted Magic for this purpose... a small .iso that can be downloaded quickly, boots quickly, and can run entirely in memory and even eject the CD to free up the CD/DVD ROM. You can find a link to the latest version, 2.1 I believe, at disrowatch.com ... Hope you like it as much as I do!
Cheers... CyberCeed

---

### Post by OoooMatron on 2008-04-19
yeah the annoying thing is ive only got 1 dvd drive between 2 computers because the old one broke. im cosntantly swapping the damn things over:D

---

### Post by Rocket2DMn on 2008-04-19
GParted allows you to make a Live USB drive, so if you have a USB flash drive available you can use that to boot from instead of a CD.  GParted LiveCD is pretty small, so it should fit on a small flash drive.  You just have to be able to boot from USB in your BIOS / boot options.

---

### Post by OoooMatron on 2008-04-19
Yeah, good point, i can try it now i have a new board. (The old one didn't like it).

---

