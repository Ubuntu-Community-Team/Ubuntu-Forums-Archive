---
title: "Breezy, GRUB and Norton Ghost"
date: 2005-10-18
forum: General Help
---

### Post by hazza96 on 2005-10-18
Ok on my work computer we have a SOE that is installed using Norton Ghost. I was not involved in the creation but when I restored my PC recently I made the partition smaller so I had free space on the HDD to install Breezy.

All went well, I could boot into Breezy, download packages etc. I was then able to boot into XP no problems.

My problem was when I rebooted machine that's all it wants to do now. I don't even see the "GRUB loading..." or anything, just the BIOS screen, then a black screen, then the BIOS screen again, over and over again.

I had to download a bootdisk image from [http://www.bootdisk.com](http://www.bootdisk.com) and do the old "FDISK /MBR" to get it to boot at all.

Does anyone know what the problem is? Why would booting into Windows screw up GRUB so badly that it causes nothing but reboots? How do I stop it doing that? Do you have any other suggestions?

I see an item in startup called "ngctw32.exe", it is associated with Norton Ghost, I wonder if killing that will stop the GRUB problem.... ummmmm.... let you know...

---

### Post by hazza96 on 2005-10-18
Nope that didn't work, all I did was boot XP then reboot it without logging in and it did the same thing.

---

### Post by hazza96 on 2005-10-18
Well I just installed Breezy on my PC at home and it is working fine, I can boot into XP and back again no problems.

I guess I will have to go into rescue mode using the install CD and put GRUB onto a floppy so that when I want to run Ubuntu I just stick in the floppy and reboot.

---

