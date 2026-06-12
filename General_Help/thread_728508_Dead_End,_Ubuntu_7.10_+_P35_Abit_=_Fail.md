---
title: "Dead End, Ubuntu 7.10 + P35 Abit = Fail"
date: 2008-03-18
forum: General Help
---

### Post by PopnPaul on 2008-03-18
Okay here we go.

My linux only accesse my 2 hard drives if they are on port 5, and on port 6.

So I have one hard drive on port 6 with GRUB and Windows on it.
I have one hard drive on port 5 with Ubuntu Linux Gutsy Gibbon 7.10 and GRUB finds it, and boots it.

Now,if they go into port 1/2 linux will not boot. This happens with Abit mobo and p35 chipsets as I have found through searching the forum.

When I plug in my third 160gb hdd into port 1 or 2 GRUB returns Error 17. When I use SUPER GRUB to bypass it and boot linux, linux hangs on the orange loading bar.

What do I do?

---

### Post by Rocket2DMn on 2008-03-19
Even though you told GRUB to load to the new hard disk location, you may need to edit your /etc/fstab file.  This can be done from the LiveCD by mounting your root partition and changing its entries appropriately by using the output of
```
sudo fdisk -l
ls -l /dev/disk/by-uuid/
```
You would have to mount the partition, then make sure you access the correct fstab file (not the LiveCD one), so it would be like 
```
[gksudo] gedit /path/to/mount/point/etc/fstab
```
gksudo may not be needed from the LiveCD.
Using UUIDs is nice because it doesn't rely on hd* or sd* values which are subject to change, esp. if you move drives around.

---

### Post by PopnPaul on 2008-03-19
Problem is, I have an 8800GT and the 8800 series hangs when using the live cd. So I have to use alt. Moreover, when I plug in the third hard drive I get errors like, Could not set xfer mask error.

---

### Post by Rocket2DMn on 2008-03-19
I'm aware of the LiveCD problem with some of these nvidia cards.  If you select the vesa driver, you should be able to get into X, then install the proprietary nvidia drivers.
When do these xfer mask errors appear - during bootup? In a log file?  Can you load into Ubuntu with the 3rd hard drive after changing your fstab to use UUIDs?

---

