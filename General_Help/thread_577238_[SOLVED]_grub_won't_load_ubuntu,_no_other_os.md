---
title: "[SOLVED] grub won't load ubuntu, no other os"
date: 2007-10-16
forum: General Help
---

### Post by jay767 on 2007-10-16
I've run into a strange grub problem. Currently I only have Ubuntu installed on my computer, no other distro, no windows. When I try to boot from the hard drive I get grub in caps with a flashing cursor after it and a locked computer.

I searched the forums for "grub" but didn't find anything that helped. I'd like to have a functional desktop again without going back to Fedora sometime soon.

So far, I've checked my device.map, menu.lst and fstab, with nothing leaping out at me. My Ubuntu is on sda1, there's an sda2 (doesn't get mounted?) and an sda5 which is the swap. Grub is looking for the kernel on hd1,0 which is where it should be.

Something else I tried was based on a suggestion from another website. I mounted my sda1 Ubuntu file system and changed the menu.lst and fstab to remove uuid references  and use /dev/sdaX instead. While it didn't help, I don't think it messed anything else up, because I've got the same GRUB _ instead of booting.

Just wondering if anyone can point me in the right direction. Thanks,
Jay

---

### Post by forestpixie on 2007-10-16
how many drives have you got? - if Ubuntu is on sda1 which I assume is your first drive - grub isn't looking there, it's looking on the second hdd - hd1,0 is the first partition on the second hdd

---

### Post by logos34 on 2007-10-16
forestpixie is right--it should be (hd**0**,0).  So you'll have to correct menu.lst and [reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351") pointing to right drive.

note: sda2 is an extended partition holding swap...it doesn't show as mounting.

---

### Post by jay767 on 2007-10-16
Thanks guys. I do indeed have two drives, a 250 GB sata that I boot from and an 80 GB ide. From grub's device.map I found out that hd0 is the the ide drive (/dev/hda) and hd1 is the sata (/dev/sda). I was able to mount the filesystem under the livecd so I know it's on sda1 (which makes it hd1,0 right?)

What has me scratching my head is that BIOS is telling the sata drive (hd1) to boot as the first hard drive, that drive has the /boot, grub is looking on first partition of hd1 for Ubuntu (sda1) yet grub still won't fire up. Yet the grub that comes with Fedora works properly and boots up no problem.

I think I'll try to install Ubuntu 6.10 and see if that gets me anywhere. If not I'll download and try the alternate install for 7.04.

EDIT: I see what happened now. Even though the majority of grub is on hd1,0 (aka sda1) the actual bootloader resides in the boot sector of hd0, which is the drive DIDN'T want to boot from. If I boot from hda instead of sda Ubuntu loads normally. Whew! Thanks for your help everyone.

Question: Does grub always install to hd0 or is that a peculiarity of Ubuntu's installer? When I set up Fedora last time I was asked which disk I wanted to boot from, but that wasn't an option for me when installing Ubuntu.

Question: If I manage to install the bootloader to both hd0 and hd1 will I be able to boot from the drive I want to boot from?

---

### Post by jay767 on 2007-10-16
I installed grub into the mbr of the disk I want to boot from and now have error 17, can't mount the partition. I saw lots of posts about this so I'll do some digging and try to resolve it. Thanks for your help everyone.

Jay

---

### Post by jay767 on 2007-10-16
Huh. It's working now. I reinstalled grub, using hd1 as root instead of hd0, which led me to a grub error 17...

I had to go into grub's command line and find the root. Turns out it was hd0,0 since I set the first booted drive to sda. A quick edit and b for boot and I booted Ubuntu from the drive I wanted to.

Following someone else's directions I edited my menu.lst and changed the #groot=(hd0,0) then save and then run sudo update-grub. Voila, I'm booting off my sata drive and not the ide drive.

Hoody hoo.

Thanks for everyone's help!

---

### Post by logos34 on 2007-10-16
> **jay767 said:**
> I do indeed have two drives, a 250 GB sata that I boot from and an 80 GB ide.

oh.  thought you had only one from the wording of your initial post.
> 
Question: Does grub always install to hd0 or is that a peculiarity of Ubuntu's installer?

I think (hd0) is grub default not matter what distro you use.  could be wrong though

> Question: If I manage to install the bootloader to both hd0 and hd1 will I be able to boot from the drive I want to boot from?

yes, simply choose the boot drive in the Bios

---

