---
title: "Messed up install"
date: 2007-07-15
forum: General Help
---

### Post by helicrasher on 2007-07-15
Help needed from a relative newbie.  I installed 32 bit 7.04 on a freshly formatted pc, using about half the disk space. The menu.lst file showed the boot location as hd(0,0) which I believe is my drive /dev/hda1.

I then installed 64bit 7.04 using the other half of the disk, and the new menu.lst file showed both the 32 bit and now the 64 bits.  The location of the 64 is hd(0,4). When I'm logged in to the 32 bit, and check the menu.lst file, I don't see the 64 bit information, yet when I boot, it's all there.

This made me realize that it was on the 64 bit partition section.  Which I confirmed by checking that location, while using the 32 bit version. I've copied that menu.lst file to my 32 bit Desktop for backup.

So my question is, how do I go about removing the 64 bit install so that I can do a new Win2000 install into part of that space, maybe 6 gig, and then leave the other 30 gig or so free for the 32bit 7.04.

I'm afraid if I use QTparted as root and just change the Active Partition and delete the old hd(0,4) location, I will hammer my boot sector and will not be able to re-boot the machine at all.  When I start Win2000, it shows the partitions as "unknown" and has many lines of that. My guess is the 1st line is my partition 1, etc. and my comparing the partition data from QTparted to this Win2000 info, I can select the correct partition for my new drive C:.  Will this work and keep my dual-boot functionality?

Any thoughts on what I should do to fix my problem is appreciated.  I'm scared I will mess up and waste all the effort in getting my 32bit version setup and running well.

Thanks from a newbie.

---

### Post by kuja on 2007-07-16
> I'm afraid if I use QTparted as root and just change the Active Partition and delete the old hd(0,4) location, I will hammer my boot sector and will not be able to re-boot the machine at all.
It will be bad though perhaps not that bad. When you boot up grub is looking in the (hd0,4) /boot/grub/ - not the /boot/grub in (hd0,0). If (hd0,4) disappears, grub will give you an error code and leave you to fend for yourself. 

I'm not quite sure how to make it look in a diifferent partition, but yeah, don't delete it until you've got a solution.

---

### Post by strabes on 2007-07-16
just do that with QTparted and then reinstall grub. See the link in my signature for more info.

---

