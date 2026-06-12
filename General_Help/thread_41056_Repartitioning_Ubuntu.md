---
title: "Repartitioning Ubuntu?"
date: 2005-06-11
forum: General Help
---

### Post by Skye on 2005-06-11
Hey everyone.  I made the switch to Ubuntu awhile ago now, but recently i've wanted to try playing some of my old windows games again.  I got Cedega and point2play, but steam, call of duty, and BF 1942 simply refuse to work with cedega on my system, and i've gotten so fed up with that blasted program that I want to create a small windows partition on my machine to play these games natively in windows XP.

I did some searching around these forums on repartitioning Ubuntu, but all the threads I found were related to repartitioning Windows in order to put ubuntu on the machine.  I want to do the reverse of this, and i couldn't really find any guides on how to do this.

So I have a few questions:

1. Is it even possible to safely repartition Ubuntu to include a small (10-15 gig) partiton of empty space that I could later install windows on?  I have three partitions at the moment, "/", "/home", and swap. I will probably be creating the windows partition from my /home partition, if it matters.

2.  How would I install windows so that it doesn't screw up Grub?  Or, if windows insists on screwing up grub, how can i recover grub post-install so that it will be the primary bootloader, and windows will not automatically start when the computer boots?

I appreciate any help you guys can give, and if i've missed an obviously placed guide, just slap me around a bit and point me in the right direction.  Thanks.

---

### Post by FLeiXiuS on 2005-06-11
You may wanted to take a look at a program called QTparted.

Link: [http://qtparted.sourceforge.net/](http://qtparted.sourceforge.net/)

QT is a front end paritioner which is very very nifty.  If you've been on windows and have used Partition Magic, QT is almost a replica.  Fantastic opensource work there.   :-P

---

### Post by Skye on 2005-06-11
Thanks, I'll check that out.

Does anyone have a suggest as to the possible issue with Grub?

---

### Post by az on 2005-06-11
1 - Do this:
make a /newhome folder
copy everything in your home thre (including your user folder)
unmount your /home
change the name of the newhome folder to home
Edit your fstab to forget about your home partition - your home folder is now on your root partition.

2 - You will need to create free space or a fat 32 filesystem on the partition you want windows to use, otherwise it will wipe your disk.  Grub will be wiped, but you can always boot the installer, mount and root the ubuntupartitoin and chroot into it.  
sudo grub-install /dev/hda (if that is the appropriate disk).

Also, you cannot partition a drive if it is mounted (any partition, not just the one you are working on)  It is best to partition using a live cd like Knoppix or you can use the installer's text partitioner.  Works well.

---

### Post by Skye on 2005-06-11
I understand completely about the /newhome proceedure- thanks!

But, I don't entirely understand what you mean/the process for repartitioning of the disks.  Once i've moved my home over to the root partition, couldn't I unmount the old /home partition and turn it into free space using QTParted?  Or does that not work?

And, could you point me to a guide or explain a little bit more about recovering grub after the install?  I'm not quite sure I understand completely, and I don't want to risk blowing up my ubuntu install.

---

### Post by az on 2005-06-11
[QUOTE=Skye]I understand completely about the /newhome proceedure- thanks!

But, I don't entirely understand what you mean/the process for repartitioning of the disks.  Once i've moved my home over to the root partition, couldn't I unmount the old /home partition and turn it into free space using QTParted?  Or does that not work?

And, could you point me to a guide or explain a little bit more about recovering grub after the install?  I'm not quite sure I understand completely, and I don't want to risk blowing up my ubuntu install.[/QUOTE]


If you have a partition on a disk that you want to resize, you usually need to unmount every other partition on that disk as well to be able to proceed.  You cannot run QTparted from a disk that is not mounted.  That is why it is better to just run a partitioner from a live cd.

Also, windows will assume the disk is empty and wipe everyting off it unless there is a block of free space or a fat32 partition.  Make the space you created (by getting rip of the home partition) into a fat32 filesystem.  The windows installer should spot that and use it.
Windows will blow the mbr away, and grub wil not load when you boot.  You need to boot the installer and then chroot (change root) into the linux filesystem.  That makes you run your system from there instead of the ramdisk you loaded your OS from (when you boot the installer - it is an OS of it's own running in memory)
With me?
Then you run grub-install /dev/hda(if that is the drive we are talking about, not hdb or hdc...)  That will put grub back onto the mbr.

If I am still not clear it is because I am overworked...  I am just typing away, trying to be concise...  Please ask again if you need to.

---

### Post by Skye on 2005-06-12
Perfectly clear.  Thanks!

---

