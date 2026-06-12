---
title: "Using Mac to install an Ubuntu USB installer for a Windows laptop."
date: 2018-09-22
forum: General Help
---

### Post by 1jarwolf on 2018-09-22
Alright so...I was doing somethings that probably should not have been doing on my Windows laptop...and well...let's just say I got the [COLOR=#0000cd]blue screen of death[/COLOR].

I do have a backup laptop. It's an 08' Macbook which works pretty good but EW! I HATE Mac OS! 

I am wanting to install an Ubuntu USB installer for my Windows PC by using my Macbook, However, Unetbootin is not doing the job. I've formatted the USB to Exfat as well as the ms-dos FAT, it did not want to boot into my Windows. Is it the GUID partition ? I am clueless and at this point, screwed. I prefer NOT to use this Mac.

Help would be much appreciated. I did know there was a SLIGHTLY same post about this however it was years ago and not exactly the same problem as I am having.

UPDATE: At this point, I am now trying "Master boot record" with "MS-DOS Fat". At this point, let's assume that it still does not work. If it does, I will inform everyone at what steps I did so others with the same possible issue would also have it solved.

Alright so, the UPDATE comment worked however, now when I press "*Try Ubuntu without installing" or any of the other 3 options this is what I get...''

[COLOR=#ff0000][B]"error: invalid magic number.
 error: you need to load kernel first.

 Press any key to continue..."[/B][/COLOR]

---

### Post by westie457 on 2018-09-22
Try using this to make transfer the ISO to your USB stick. [https://etcher.io/](https://etcher.io/)

---

### Post by yancek on 2018-09-22
> I am wanting to install an Ubuntu USB installer for my Windows PC by using my Macbook

Unetbootin has 3 versions, one to be used on a windows system, one on a Linux system and one for a Mac.  Make sure you use the correct one for the Mac.

> I've formatted the USB to Exfat as well as the ms-dos FAT, 

The unetbootin page indicates that if you are having problems you should use FAT32/vfat filesystem.  Don't know if exfat will work.

> t did not want to boot into my Windows.

What did not want to boot into your windows?  If you are trying to create a bootable usb with Ubuntu on it to install, how does windows come into the picture?  Did your attempt to use unetbootin on the Mac appear to succeed, no error messages during the creation of the bootable usb?  

Which windows OS do you have on the computer?  UEFI or Legacy/CSM?

---

### Post by 1jarwolf on 2018-09-22
Hello there! Yes, I have the mac version of Unetbootin. For some reason, it does not show fat32/vfat anywhere. My Windows laptop crashed and I can't recover it. I am using my Mac laptop in attempt to create a bootable Ubuntu USB to install over my Windows. I believe my laptop has both Legacy and EFEI. It appears that EFEI works better though. "I[COLOR=#000000][I]t did not want to boot into my Windows." as in, the bootable usb is not booting up. I will try etcher, I do hope that works.

UPDATE: It appears that Etcher is also not working. I am going to re download the ISO. Perhaps it was corrupt when downloaded.[/I][/COLOR]

---

### Post by 1jarwolf on 2018-09-22
UPDATE to you both! I believe I have successfully got it booted and I am currently installing it. I ended up using etcher and it seems to be working thus far. Another great reason why I am sticking with Linux now, the community that actually helps others! Thank you so very much westie457 and yancek!

---

