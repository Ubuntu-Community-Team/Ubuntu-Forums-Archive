---
title: "Install Problems"
date: 2007-04-06
forum: General Help
---

### Post by warsong on 2007-04-06
Hey all!
Im new to Unbuntu and Im currently trying to get it to install on my laptop that already has Win XP installed on it. My laptop is a Dell inspiron 6400. It has 160gig drive that right now is completely being used by my window partition. When i try to install ubuntu, i use the partition manager and take 20 gigs from windows partition and use that 20 gigs to make ext3 and a swap. My problem is that unbuntu pops up a message saying that the rest of my windows partition could become corrupt because of cluster sizes being irregular when I try to go to the next step of the installation. Is there a better way to do this? Should I deallocate the 20 gigs in windows first?
Also because its a Dell, there are already 3 primary partitions 2 being Dell recovery and the other being my ntfs for windows. Is it possible to install unbuntu on a logical partition?
Any help is greatly appreciated!

Thank you!

---

### Post by cisforcojo on 2007-04-06
I've HEARD Ubuntu's gparted is really really good and reliable but I'm still not sure I'd trust it.
I'm also not sure I'd trust resizing the partition in Windows either and then doing it. You run the risk of your MBR becoming screwing and not being able to boot into anything (until a reinstall). You CAN install Ubuntu onto a logical partition, even an external HD (if you computer can boot USB in BIOS).

What I would do if I was you is backup what you need backed up first, then try resizing the partition (windows/ubuntu, doesn't matter) then if it doesn't work, repartition your drive and do a fresh install of Windows on a smaller partition and then Ubuntu

---

### Post by ahaurw01 on 2007-04-06
Did you make sure to defragment your windows partition (while running windows) before the install? That might be the reason for the error message. I was more or less in your situation at first and after doing that, it installed without problems, dual boots fine, etc.
good luck!

---

### Post by warsong on 2007-04-06
Ill give these suggestions a shot! Thanks! I also noticed that partition magic can make ext3 and swap partitions do you think its a good idea to make them before hand then install ubuntu on those?

---

### Post by gozzerd on 2007-04-06
If you have access to a Partition Magic new enough to manipulate NTFS, this process is a done deal.  Rearrange your partitions however you like in PM, then do the Ubuntu install. The installer will see the available space and and give you the option of installing to the partitions of your choice, as long as you don't allow it to install over your entire drive. 

Defragging is probably not necessary using PM, if you have plenty of space for the new partition.  It will pick up the entire fragmented mess and move it out of the way. But it's good practice to defrag anyway. 

There should be no issue with unequal sector sizes this way. 

But you should back-up any critical data before starting this, and you should make a copy of your mbr on a floppy or something before and after changes. Then if something does go wrong, you can return to a good mbr  easily and still have a bootable machine.

The Linux way of doing this is using a a file utility called dd. PM may have a utility for doing this directly.  I don't know about that.  If you boot into the live cd, you could put in a new floppy, use a terminal (under applications/accessories) and enter

sudo dd if=/dev/hda1 of=/dev/fd0 bs=512 count=1

This assumes that ubuntu is seeing your hard drive as /dev/hda1 and your floppy as /dev/fd0. "if" means input file, "of" means output file. The "sudo" is giving you permission to access the block devices, meaning your drives, viewed as devices rather than file systems. This will copy your mbr to the first sector of the floppy. If you need to restore the mbr  from the floppy,  just reverse the source and destination devices

sudo dd if=/dev/fd0 of=/dev/hda1 bs=512 count=1

and your mbr is back where it started.

---

