---
title: "Can't boot to greeter on laptop without power brick"
date: 2020-12-28
forum: General Help
---

### Post by skraaj on 2020-12-28
Hi all, I have a slight problem with booting to GUI. If I boot my laptop without the power brick plugged in I can't get to the greeter screen, I get black background instead of the usual violet for the greeter and I see an unresponsive mouse pointer. Sometimes my screen shows literal garbage instead of even that black background (like visual noise). If I reboot with power brick on then all's fine. I read somewhere that this has been an issue for a while, but maybe someone has a solution? This makes my laptop into a desktop if I want to use Ubuntu.


I dual boot Win10/20.04, laptop - ASUS TUF FX505DT-AL086, Ryzen 5 3550H, Vega 8 + GTX 1650, 16GB RAM, 970 EVO 500GB (Ubuntu), ADATA SU800 (Win10), separate SSDs for OSes both installed in UEFI mode, default greeter and DE, no packages modifying those have been installed, I have network shares in fstab, but removing those do not change the issue. sudo apt update / upgrade done.

---

### Post by CelticWarrior on 2020-12-28
Welcome.

> [COLOR=#000000]I dual boot Win10/20.04, laptop, separate SSDs for Win10 and Ubuntu 20.04, **grub on disk with Ubuntu**[/COLOR]
What you mean by the bold part above, exactly?
In any modern system OSes should be installed in UEFI mode therefore regardless of the amount of drives typically only one ESP (EFI System Partition) is used and that one is already there in the original drive with the preinstalled Windows. Have you by any chance installed Ubuntu in Legacy mode? That may very well be the cause of your reported strange behavior.

---

### Post by skraaj on 2020-12-28
Thanks for the reply, I got a laptop without OS and replaced stock drives so there's no preinstalled anything. 

First I plugged in one drive and installed Ubuntu, then took it out, put second in and installed Win10, put back the drive with Ubuntu, changed boot order to start with Ubuntu drive, ran update-grub and all works great, except for that booting issue. That's why I wrote that grub's on the disk with Ubuntu, just in case it matters somehow. I honestly noticed the problem few months after the install since up until that point I used it more as a desktop than a mobile device. Did the same thing on my actual desktop and works fine without any issues as well, but that one requires mains power so I can't check if the problem is there as well. 

Installation process seems convoluted, I know, but I'd rather take drives in and out than repeat the installation if I select a wrong drive.

---

### Post by CelticWarrior on 2020-12-28
If you're installing OSes then you should know what you're doing and that includes where to install each one.

And again, if the computer is like 10 years old or newer it has UEFI, not BIOS, and should be installed in UEFI mode and for better results the drive with the original ESP should be kept.

Also please hardware specifications.

---

### Post by skraaj on 2020-12-28
ASUS TUF FX505DT-AL086, Ryzen 5 3550H, Vega 8 + GTX 1650, 16GB RAM, 970 EVO 500GB (Ubuntu), ADATA SU800 (Win10), both installed in UEFI mode. Generally all's working fine and as expected, save for that booting issue. 

Any specific log I should look at? I doubt there will be anything as this is a freeze and all I can do is to shut down holding power button. Maybe some more power settings apart from what's in Settings menu?

---

### Post by skraaj on 2021-03-17
Update on the issue. 

Cause &#8211; external monitor plugged into the HDMI port. Somehow without the power brick it defaults to external monitor for some reason and built-in is stuck on... something - sometimes loading splash screen, sometimes visual noise.
Solution &#8211; do not plug anything to HDMI without the power brick.

Been able to replicate the issue to check if it actually persists.

I'm guessing it because driver select / nVidia drivers, leaving the reply in case anyone's having the same issue. Topic can be safely closed.

---

