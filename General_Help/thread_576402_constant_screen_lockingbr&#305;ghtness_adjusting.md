---
title: "constant screen locking/br&#305;ghtness adjusting"
date: 2007-10-15
forum: General Help
---

### Post by muzcuk on 2007-10-15
Hey there!
I've recently installed gutsy on my laptop, it is pretty much the same configuration as the System76 Darter Ultra. I have several problems;

I use an external monitor,keyboard and mouse by the way..

About every few minutes the system locks the screen by itself.. I unlock it and everything is fine.. My guess is it thinks its idle because I'm not using the built in keyboard. But what to do..?

The hotkeys for adjusting brightness do work, but in a weird way. When I push "brightness up" for several times, the brightness goes up for one step, than in the next step it is back to 0 and then in the next step it goes one step up from the last step, I hope I'm making th's clear, if there are 20 steps, 10 of them is set to 0, but the other 10 works just fine. Its something like 0 0 1 0 2 0 3 0 4 0 5 0 6 0...

Also the system is constantly changing the brightness by itself (somehow randomly, I suppose). 

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/128452](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/128452)

I believe this is what it is..

The card read is recognized but not working, and by not working I mean I haven't seen it doing anything useful besides being recognized. I'd expect it to automount when I stick in a card. Other things do automount. I'd try mounting it manually but I don't know which dev is it, any way to find out?

The battery indicator is messed up, it is never right and system crashes when the battery is over instead of warning me or shutting itself down or something. Right now it says "%0 charging, left 15 minutes" I think that gives you an idea.

Also, how do I change the console resolution. There must be a config file somewhere but I've been away from linux for a while so I don't remember where..

And here is the lspci output, in case it helps.Fingerprint reader and webcam are missing in there, fingerprint reader is not supported but web cam is, I also can see the webhardware informationcam in  tool, but it doesn't seem to be working, not with pidgin at least..

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
01:04.1 Generic system peripheral [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
01:04.2 FLASH memory: ENE Technology Inc Unknown device 0720
01:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

---

### Post by inversis on 2007-11-28
I have exactly the same problems, and the same chipset and graphic card on my laptop:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

I "solved" most of the light on and by setting power-management *baterie mode* and *charger mode* (? is this the English name for it?) with the same bright. (both o 69%)

Now the problem is the "0 1 0 2 0 3 ..." and some black screens that appear when idle for some seconds.

---

### Post by muzcuk on 2007-11-28
I also did the same thing but that is more of a workaround than a solution, I think system76 has (almost) solved the power management issues with my model and they are supposed to be releasing a new driver one of these days. I don't know if you are using a system76 computer (for some reason I've got the feeling that you don't) but even if you don't, the driver is open source so if you want it bad enough you should (somehow) be able to implement it to your system. That is of course after it is released.

I also had the black screen thing but it went away after disabling every power saving feature (hell, even the screen saver) I could find, so I don't know which particular one of them caused the problem. One of them did for sure. Also, even though I disabled everything, external screen still is turned off after 30 min. idle time and it comes back perfectly fine when I move the mouse. That is the only power saving feature my computer has at this point and I don't even know why/how it has it.. :)

By the way, dear system76 people, how is the driver coming? Daru2 will kick even more *** when it knows how much battery power it has left.. And (proper) suspention/hibernation would be so cool I can't even imagine.. Actually if I could use all the hardware that thing has it would kick *** like nothing else could.. (Forget about the MS reader and fingerprint reader, HDMI would be soooo cool..! But of course you don't have to forget about anything..!) Why doesn't intel write its own damn drivers anyways!?

And another question, is there any way I can use your drivers with gentoo? I bet there is but is there a relatively easy way or would I have to get my hands dirty with the source?

---

### Post by Aggrocrag on 2007-11-30
I too have the random change in screen brightness problems, both the periodic changes and the 01020304 levels as I adjust it.  I believe it started after I opened the screen about two hours ago.  This is my only complaint.  So far, I have owned this daru2 for less than a day, and I can't stop showing it off.

---

