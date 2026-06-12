---
title: "Ubuntu and windows dual boot problems [RAID]"
date: 2007-03-26
forum: General Help
---

### Post by truthsifter on 2007-03-26
So, I decided today i'd finally get around to getting my windows box to dual boot with ubuntu.  I quickly ran into a problem.  My windows drive is a VIA raid 0 of 2 160GB drives, and the installer didn't recognize it(it thought they were two separate hard drives).  Thusly, it didn't think to install grub on the windows partition.  When the computer boots up, it just goes straight to windows.

The 2 solutions i could think of were
Get grub installed on my raid (somehow..)
or
add ubuntu as a listing on the boot.ini in the windows boot loader(tried this and couldn't find good instructions.. needless to say it didn't work)

Does anyone know where i can find how-to's on either of these subjects for feisty?  Or does anyone else have any suggestions?

---

### Post by syzygy86 on 2007-04-04
I'm currently having the same problem.  I have two drives in RAID 0 that I'm using for my Windows system, and another single drive I want to use for Ubuntu.  Same issue here with GRUB seeing the RAID array as 2 drives (I expect this since its an onboard software RAID).  If I install Ubuntu on the single drive, when I go to reboot, GRUB throws an error, even when trying to boot into Ubuntu.  The only way to get into Ubuntu is to remove the two RAID drives (not too bad with hot-swap trays, but still annoying).

From what I have been reading on various forums, this setup does not seem to be supported, mainly because of the software RAID required.  If there is anyone who knows of a solution, I too would love some suggestions.

---

### Post by hush on 2007-04-04
man me too... I had winxp set up on RAID 0 for gaming, I guess Linux doesn't have support for anything like that yet?

---

### Post by DemaSRV on 2007-04-15
It doesn't seem like there are any solutions to this.  I'm having a similar problem, I have 2x 160GB drives in a RAID 0 with win set up, and i want to install linux on a seperate drive but I can't get Grub to work on the RAID.

---

### Post by Grafik on 2007-04-17
I've also got a similar problem...

I have 4-300GB HDDs running a RAID 5 and a seperate 80GB HDD running Edgy and each time I boot, I have to go into my BIOS and tell my PC which OS i would like to boot into. this can get QUITE annoying and I wish there was some way to fix the GRUB Loader so it can identify my system partition in my RAID so I can have the dual-boot option without the burden of having to check the BIOS every time :(

---

### Post by hush on 2007-04-17
> **Grafik said:**
> I've also got a similar problem...

I have 4-300GB HDDs running a RAID 5 and a seperate 80GB HDD running Edgy and each time I boot, I have to go into my BIOS and tell my PC which OS i would like to boot into. this can get QUITE annoying and I wish there was some way to fix the GRUB Loader so it can identify my system partition in my RAID so I can have the dual-boot option without the burden of having to check the BIOS every time :(
man that sounds pretty frustrating, I've never heard of anyone having that kind of trouble before
surely somebody out there knows how to help us?

---

### Post by zveroboy on 2007-10-09
Assuming that you have some free (unpartitioned) space on your raid array (or can resize your current partition) then follow instructions at the following link - it worked for me.

[https://help.ubuntu.com/community/FakeRaidHowto?highlight=%28raid%29](https://help.ubuntu.com/community/FakeRaidHowto?highlight=%28raid%29)

Good luck.

---

