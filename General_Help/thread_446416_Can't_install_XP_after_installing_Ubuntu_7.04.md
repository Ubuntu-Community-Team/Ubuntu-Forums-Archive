---
title: "Can't install XP after installing Ubuntu 7.04"
date: 2007-05-16
forum: General Help
---

### Post by opiv421 on 2007-05-16
Hey all. I've given Ubuntu a try and enjoyed my time with it however not being able to run the two programs I use the most (WoW and Newsleecher) has led back to XP for the time being... but I can't install it. Windows XP hangs when trying to install at the same spot every time, 22% at the installing network stage. My hardware is working fine, and I haven't changed anything since the last Windows install. The only explanation I can think of is that the previous Ubuntu install screwed something up? I also tried installing Vista but get an error preventing the install from finishing. I've reformatted the disk 3 times (2 quick format 1 regular). Ubuntu installs without a problem. I have no idea what could be causing this. Has anyone had similar problems or know of a solution to this? :confused:

---

### Post by aldenhg on 2007-05-16
I would guess that the problem has absolutely nothing to do with Ubuntu. It sounds to me like either a hardware issue or an issue with your Windows installation CD. If you can, try a different Windows disc. If it still craps out you should call MS and complain. They might hook you up with a newer CD that might work, but it might be best if you don't mention your foray into Ubuntu as they might (baselessly) use it as an excuse not to help you.

---

### Post by opiv421 on 2007-05-16
I don't think its a problem with the install cd, the problem occurs on both of my XP and Vista disks, and they have very little to no scratches on the bottom. I guess it has hardware related but I doesn't make sense that I had a healthy Windows XP install just a few days ago then it craps out after I install Ubuntu.

---

### Post by strabes on 2007-05-16
If you had ubuntu on your hard drive but then wiped the entire disk ubuntu could not be affecting anything anymore since it is no longer on your disk. Since you couldn't get those two programs to work might I suggest a dual boot? You'll be glad you did.

---

### Post by aldenhg on 2007-05-17
That's very strange. I'd recommend running memtest86 and drive fitness test (DFT) off of a CD to check you memory and hard drives. If they either comes up bad or hangs while running, you'll have your culprit. Otherwise, I'm out of ideas.

Except if both hang on the Network config, you could try replacing your network card. If you have onboard LAN, try getting a PCI network card (about $20 off newegg) and diabling the onboard LAN in the BIOS. I have a Marvell onboard ethernet port and it had problems in both windows and Linux. I got a PCI network card and everything was fixed.

---

