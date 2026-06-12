---
title: "Can't install Ubuntu"
date: 2008-02-25
forum: General Help
---

### Post by eagledrc on 2008-02-25
Hey,

I have a older computer, not my primary one, but the one that my mother and sister use, and when I used it, I installed Ubuntu (6.10 I believe) on a 3GB backup drive.  The computer has a 40GB HD, a 1.4ghz processor, 376MB of RAM, and Windows XP installed on the 40GB HD, which is almost full.  I started the computer everyday when all three of us used it, but now I don't use it very much, so they boot it up everyday and have to go through the GRUB menu.  I know how to disable the GRUB menu (sudo gedit /boot/grub/menu.lst default 0 to 4), but the Ubuntu install got corrupted or something and it won't boot.  Rather than try to fix it via system recovery, I just figured I would try to install 7.10 on the backup drive via live CD.  I tried to install it on the 3GB drive, but it said that it couldn't set up the swap space on that same drive.  It needs 256MB of swap space and 2GB to install, so it should have enough, but it couldn't.  I can't see that drive from the live CD to format it.  What can I do?  I just want to disable GRUB, but I can't boot into Ubuntu.

---

### Post by kshane on 2008-02-25
Give Super Grub a try.  I'm not sure if it will help, or not.  But, it does a lot of different things with Grub.  It's a very useful tool for any Grub issues.

Kevin

---

### Post by trippinnik on 2008-02-25
did you try the alternative installer? You should probably delete the old partition with Ubuntu on it and reformat that drive.  My guess is the drive is dead though.  it's not often a Linux install gets corrupted...

---

