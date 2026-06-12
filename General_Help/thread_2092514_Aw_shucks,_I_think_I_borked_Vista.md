---
title: "Aw shucks, I think I borked Vista"
date: 2012-12-08
forum: General Help
---

### Post by sloe on 2012-12-08
Howdy y'all!

It's been quite some time since I first dabbled with Ubuntu - according to my "last visit" stat up there, it's been about 4.5 years :oops: I recently started toying around with my Android phone, and the reccomended development environment for that is Ubuntu 12.04 with the Android Developer Tools variant of Eclipse.

So, I took this HP Pavilion dv5 that my company so graciously loaned me a few years ago and decided to dual boot it. The HP has Vista Enterprise x64 on it, and I used the disk utilities within Vista to carve out a 20GB extended partition for Ubuntu, leaving a 202Gb primary partition for Vista and the 11Gb HP Recovery partition intact.

I've been playing around with Ubuntu exclusivly for almost a week, but something came up today which required I boot into the Vista load. So, I rebooted into the Grub2 loader, and selected the Vista entry on /dev/sda1. The screen went black like it was going to start the Vista load, and then popped right back into the Grub menu. Something in the grub.cfg file was confused and pointing the Vista load at Grub. On a whim, I tried the recovery partition, and it loaded just fine.

I've been combing through the forums, and trying everything I could find as I found it instead of gathering all the info and then starting, and I'm fairly certain I destroyed my Vista load, but I don't know how I did it. Here's the [boot-repair results](http://paste.ubuntu.com/1417790/) from before I attempted any repairs, and heres the [results](http://paste.ubuntu.com/1418356/) as they stand right now after I tried to fix it.

The current problem is that the system will not boot from the hard drive right now. I'm about to reinstall grub2 to fix that, but the Vista load will not start. I get a blank screen with a blinking cursor in the top left corner of the screen - that's it. If I were to reboot the computer right now without a CD in the tray, it would go to that cursor and stop. Here's the funny part - if I stick a Vista or Win7 CD in at that point, it will boot from the DVD, but it won't boot the Ubuntu disc without a cold restart.

I've tried every tip I could find to fix the Vista boot - I've gone into the recovery console and used 'bootrec.exe /fixmbr' 'bootrec.exe /fixboot' 'bootrec.exe /rebuildmbr' and 'bootsect /NT60 c:'. boot-repair now says that Vista is loaded in the MBR of sda1, and the disk is healthy. If that's so, why won't it boot?

I realize this is an Ubuntu forum, but as this started out as nothing more than a Grub problem and y'all seem to have all the answers anyhow, I thought I'd start here ;)

---

### Post by dcstar on 2012-12-08
> **sloe said:**
> 
........
If that's so, why won't it boot?


Because you need to install Grub into /dev/sda.

Reinstall Grub into /dev/sda and then worry about fixing Windows.

---

### Post by Kirk Schnable on 2012-12-08
> **dcstar said:**
> Because you need to install Grub into /dev/sda.

Reinstall Grub into /dev/sda and then worry about fixing Windows.

You might find this utility helpful in easily reinstalling GRUB. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Fixing the Windows boot loader might have negative side effects on GRUB. Here is some reading relevant to fixing that: (Boot Repair tool above can do it). [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by debodas on 2012-12-08
Reinstall Grub, the problem will be that grub doesn't know where your windows partition is. Grub should be on /dev/sda. Once it is, grub will know where your windows partition is and you should be able to boot into windows just fine.

---

### Post by oldfred on 2012-12-08
You may have run all the Windows fixes, did you include chkdsk? I am not sure if the standard fixboot does not just copy the backup NTFS boot sector back and not rebuild it. But to bootsec command should create a new one.

The issue probably is from your originally partitioning. Vista was the first system to change sda1 to sector 2048. XP always started at sector 63, as did Linux. Gparted did not change until about the same time as Windows 7 to start all new sda1 partitions at 2048. That is for better compatibility with SSD & the new 4K drives.

But the older Ubuntu installers would for whatever reason move the Vista start from 2048 to 63. Yours is at 63. Unless you installed Vista over XP it should be 2048. But usually Windows repairs would fix it, but in some cases MFT overlaps and either MFT repairs bork boot sector or boot sector repairs bork MFT.

       If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

    
I did see some comment where a third party Windows partition tool would move MFT to middle of partition. Not sure if that would now help or not.

---

