---
title: "Resizing Partitions and Editing GRUB"
date: 2007-06-05
forum: General Help
---

### Post by DeathOnJuice on 2007-06-05
Hey, everyone. I currently run Ubuntu on an ext3 filesystem, but I want to run MythTV. I've decided to create either an additional Ubuntu install with an XFS or JFS filesystem or a KnoppMyth install. (As a side question, can anybody tell me which would be a better choice?)

The only problem is, I need to resize my NTFS Windows XP partition to get this to work. I know I can use GParted, but are there any precautions I should take other than defragging and backing up my data?

The other problem is adding this new install to GRUB. The Ubuntu install always seems to make a perfect GRUB menu. However, I can foresee three issues. One is that I wouldn't be able to tell the two Ubuntu installs apart. I could just edit the names in menu.lst, right? The second is that I don't know where I would store GRUB; I know that some of it goes in the MBR, but I also have a /boot/grub and I don't know what partition to put this on. I really don't get how that works. Finally, the one time I overwrote GRUB with the Windows bootloader, I could NOT set it back up inside Ubuntu or with the LiveCD. Although it seemed to know how to do it during the install, I was getting errors left and right when Ubuntu was already installed and I ended up reinstalling. Besides, I'm not sure KnoppMyth will work as well. In case of problems, could someone give me a good GRUB guide? I have a SATA hard drive.

Thanks so much!

---

### Post by H.E. Pennypacker on 2007-06-05
> The only problem is, I need to resize my NTFS Windows XP partition to get this to work. I know I can use GParted, but are there any precautions I should take other than defragging and backing up my data?


Well, one word of advice is that resizing is always risky.  It's actually more risky than general work on partitions.  As you already know, don't forget to backup.  When you are done resizing a partition, your partition table become corrupted.  In that case, an application like TestDisk (available via Synaptic) could prove very help.  Before you get anything done, also download SystemRescueCD ([http://www.sysresccd.org](http://www.sysresccd.org)), just to be on the safe side.  You're going into shady areas, and it's a good idea to be ready for anything.

> One is that I wouldn't be able to tell the two Ubuntu installs apart. 

In that case, you can edit the file, and give each partition whatever name you'd like.  Prevents confusion.

> The second is that I don't know where I would store GRUB

Since you already have Ubuntu, it's already where it is supposed to be (at the very forefront of the partition table).  

> I also have a /boot/grub and I don't know what partition to put this on. 

You're not moving Grub anywhere.  It just says /boot/grub/, because that's where it goes, but that is irrelevant to where it actually goes on a partition table.  

> Finally, the one time I overwrote GRUB with the Windows bootloader, I could NOT set it back up inside Ubuntu or with the LiveCD.

If you followed correct procedures on fixing GRUB, you should have been fine witha  LiveCD.  

> In case of problems, could someone give me a good GRUB guide?

At this point, let's hope nothing will go wrong.  If something does go wrong, you will be able to find a specific guide for your error/problem.

Don't forget to follow MythTV's proper guide on installation, and before you go ahead with MythTV, read its reviews, because I hear it can be difficult to set up.  Good luck.

---

### Post by DeathOnJuice on 2007-06-05
OK, after reading some documentation, I'm even more confused. It says on this guide:

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

To set up partitions as /, swap, and /var/lib. But if I do this, what's to stop my other Ubuntu system from mounting these partitions? Does GRUB manage all this? It looks like my partition table will look something like this, some of which is impossible:

Partition           Mount As
/dev/sda1        /media/windows
/dev/sda4        /
/dev/sda6        /var/lib
/dev/sda2        /
/dev/sda3        (Extended)
/dev/sda5        (Swap)

...I'm confused. Could I set GRUB up to use two hard drives instead? Sounds a lot easier. How?

---

### Post by confused57 on 2007-06-05
This is the best grub guide I've found:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

One thing I thought I'd mention is that grub is incompatible with XFS filesystems...you'd have to use lilo.  I'm not familiar with the other 2 you're considering using.

---

