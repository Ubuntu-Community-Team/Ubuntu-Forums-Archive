---
title: "Attempting dual boot on Acer Aspire One D150 Netbook"
date: 2013-06-24
forum: General Help
---

### Post by gilliam86 on 2013-06-24
Hello, and thanks for reading :)

I have an Acer Aspire One D150 Netbook that I decided I was going to do some testing on with the Android-x86 project. (This is why there is/was no other OS on my Netbook at this point.)

So after many failed attempts to get the Android-x86 project to work, I decided that while I'm tinkering, I'll get Ubuntu a shot.

I like it fine enough, but I really would like to have Windows XP on here again.

I used GParted to partition the HD, I made a 350g NTFS Partition, and a 50g EXT4 (or 3, not quite sure anymore) partition for Ubuntu.

At this point when the laptop came on I got a black screen that says "Error 15".  No more details or text other than that.

After many frustrated attempts to try and install Windows XP (2 different versions, different USB drives, and different programs to create the bootable USB drives (UNetBootin and Rufus)) all have/had the same result: Nothing.

So at this point I have to know if this laptop is a brick or what, and I install Ubuntu with no issues whatsoever onto the 2nd partition.

Now here I am, trying to install Windows XP (At this point I'll use 7 again, I don't care, but I'm at work so I can't ... acquire Win7 this very minute) onto the first partition (Because I read that Windows likes to be at the front/first).  I even read that I should delete the 350g NTFS partition and leave it as unallocated space, and tried that, it did nothing different.

I've tried all the steps before with the different copies of XP, different USB drives, and different programs, all to the same effect, the computer always, regardless of what I tell it to do in BIOs or how many times I select the USB drive from the F12 menu, goes to GRUB, I never even see the Windows intall menu.  

All the google-fu I've done keeps telling me how simple it is to just make a bootable USB with WinXP on it and run the repair tool to fix my boot manager but I can't even get past grub, much less into the install/repair menu.

So please, help me Ubuntu Forums, you're my only hope.

---

### Post by oldfred on 2013-06-26
Error 15 is from grub legacy which you must still have in MBR. Windows will overwrite it on install anyway.

You said you created a NTFS partition. Is it a primary partition sda1 thru sda4 and does it have the boot flag (or active partition in Windows)? Then Windows should install.
Otherwise you need unallocated space and an available primary partition. Often best to let XP be sda1.

---

