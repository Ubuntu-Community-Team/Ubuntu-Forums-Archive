---
title: "Removed my boot partition. Need to recreate it."
date: 2007-04-24
forum: General Help
---

### Post by talcite on 2007-04-24
So I was performing maintenance on my computer. Specifically, I took out a dying hard drive as a preventative measure. Turns out that hard drive had my boot partition on it, including grub. What do I do now? I would prefer not to put it back in, because it really is dying. 

I've gotten to the point where i've reinstalled grub, and set it up again (partially). I can still boot up using a super Grub USB, which is why i'm on right now. When I goto the grub menu and try to boot ubuntu, I get error 21. I'm quite sure that this has nothing to do with my drives being detected or not. For one... I don't even have a menu.lst in my new boot partition -_-'. Anyways... I'm out of ideas, I've tried using the super grub cd, and pretty much using the alternate CD to reinstall grub... although i'm not sure I did it properly. 

So what do I do now? Is there some way to reinstall feisty without wiping my files? I can back them up if necessary... but I'm on exams and this is really taking more time than I have.

---

### Post by phidia on 2007-04-24
The alternate cd does give you the option to re-install grub. Maybe you need to choose system rescue and then re-install grub-I don't remember the steps for sure but if you know which drive is the 1st drive in boot order and you install grub to that it should work.
One problem though is that in removing a drive it can change the rest of the hard drive's designations.  e.g. if the drive you removed was the 1st drive in bios now everything has changed or if the removed drive was ahead of the drive the ubuntu install is on-still changes that drives designation (#). Maybe do fdisk -l and then check your fstab?

---

### Post by talcite on 2007-04-25
thank you very much! I figured out how to do it. It turns out my boot partition is the ubuntu partiion 0.o

Oh well, so I went to that one, found everything working =P All I had to do was move the drive list back one position to (hd0,1) instead of (hd1,1) =P Silly me. 

Thanks! =D

---

### Post by phidia on 2007-04-25
Glad you got it working :)

---

