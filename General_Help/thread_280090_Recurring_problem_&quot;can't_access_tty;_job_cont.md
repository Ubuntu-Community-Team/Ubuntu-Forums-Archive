---
title: "Recurring problem: &quot;can't access tty; job control turned off&quot;"
date: 2006-10-18
forum: General Help
---

### Post by noerrorsfound on 2006-10-18
I keep having to reinstall Ubuntu, because after a few reboots, I'm presented with only a BusyBox console stating:
> can't access tty; job control turned off
I always install the 187 updates and can reboot fine, but if I reboot the next day, Ubuntu won't start.

I'm installing from an official Ubuntu CD from Shipit, but it's an old version (6.06) which is why I have to download so many updates. :)

I have Windows on a 20 gig hard drive (primary) and Ubuntu is on a 60 gig (secondary). During the installation I just choose to format and install Ubuntu.

---

### Post by K.Mandla on 2006-10-19
Does your problem resemble this one?

[http://www.ubuntuforums.org/showthread.php?t=279884](http://www.ubuntuforums.org/showthread.php?t=279884)

---

### Post by noerrorsfound on 2006-10-19
Yes.

---

### Post by noerrorsfound on 2006-10-29
Yesterday night I reinstalled, downloaded the 209 megs of upgrades, and then let the 6.10 upgrade (500+ megs) run overnight. After a boot to XP and back, Ubuntu wouldn't start again. For some reason I thought that upgrading would solve my problem.:rolleyes: The upgrade worked well though...

I have Windows XP on one hard drive and Ubuntu on another. I unplugged the Win XP drive and then the grub menu wouldn't start for some reason. Then I unplug the Ubuntu drive and plug back in the XP one and it says GRUB error 21, which is weird because I installed Ubuntu on a different hard drive so why would grub be on the xp drive?

I plug the ubuntu drive in and then grub works :-s.

Does this have anything to do with the problem? I'll probably try reinstalling Ubuntu again, but this time with just the Ubuntu drive plugged in.

Ubuntu seems to only stop working after using Windows and then trying to restart.

---

### Post by noerrorsfound on 2006-11-08
Well, all had been going fine until just recently when I went into Windows to try and transfer some files to my Ubuntu HD (and both apps I tried failed). Now I'm stuck at this screen again.](*,)

---

### Post by ZetaPhoenix on 2006-11-15
> **noerrorsfound said:**
> Yesterday night I reinstalled, downloaded the 209 megs of upgrades, and then let the 6.10 upgrade (500+ megs) run overnight. After a boot to XP and back, Ubuntu wouldn't start again. For some reason I thought that upgrading would solve my problem.:rolleyes: The upgrade worked well though...

I have Windows XP on one hard drive and Ubuntu on another. I unplugged the Win XP drive and then the grub menu wouldn't start for some reason. Then I unplug the Ubuntu drive and plug back in the XP one and it says GRUB error 21, which is weird because I installed Ubuntu on a different hard drive so why would grub be on the xp drive?

I plug the ubuntu drive in and then grub works :-s.

Does this have anything to do with the problem? I'll probably try reinstalling Ubuntu again, but this time with just the Ubuntu drive plugged in.

Ubuntu seems to only stop working after using Windows and then trying to restart.
noerrorsfound:

To fix the boot prolbem, use the Win XP install cd and launch the recovery console.

Then change to c: (cd c: )
run fixmbr, fixboot, and then bootcfg and rescan and select one as the deafault

> **noerrorsfound said:**
> Well, all had been going fine until just recently when I went into Windows to try and transfer some files to my Ubuntu HD (and both apps I tried failed). Now I'm stuck at this screen again.](*,)
funny, I did the same thing and now I get this error when trying to boot off the USB Ubuntu disk also.

-Jon

---

### Post by yarayara on 2008-01-16
I have the same problem an it is very annoying, what to I do??

I install Ubuntu Feisty 7.04 from a CD I got from a magazine; this, because it doesnt work any other way (i.e. download from the internet). Added to this, I have to install it in text mode, because the graphic mode wont work. Ok, so far, any of this matters.

My problem comes after the update. I download tons of Megabytes, restart and then I wont work anymore.

I press ESC and select the kernel 2.6.20-15 (the one from the CD) and it boots ok. If I select the new one 2.16.20-16, it wont boot.

I found a thread were it says I should go to /ext/boot/menu.lst or something like that and edit a file with a similar name.

Now Im no expert, just a guy who wants to quit Win$ucks. 

The line I edited looks from this

kernel		/boot/vmlinuz-2.6.20-16 root=(bunch of code) ro quiet splash

to this

kernel		/boot/vmlinuz-2.6.20-16 root=/dev/hda1 ro quiet splash

When I reboot with version 16 it wont start, so I go back to 15... but then it doenst works any longer. now Im afraid to do any update!!  Ive been through this at least 6 times (im tired of reinstalling ubuntu).

what should I do?

thanks,
yarayara

---

