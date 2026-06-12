---
title: "wrong resolutions in 8.04"
date: 2008-04-24
forum: General Help
---

### Post by yaywoop on 2008-04-24
Ok. I have an ATI RX700LE card and a LG Flatron L1811S 1280x1024 lcd.
I just installed ubuntu 8.04 and it is not displaying 1280x1024 as a supported resolution in the gnome screen resolution applet.
also in system>administration>hardware drivers, it shows ATI Fire GL as being enabled but not in use
at the moment I am using 1024x768, which is the highest res with the right aspect ratio. how do I get 1280x1024 to work?

edit: WTF is up with my xorg.conf?
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by vigleik on 2008-04-25
I (and a lot of other people, judging from the forum) had the same problem with a Nvidia card. The solution is to install the ATI driver (use apt-get or synaptic). Then you might possibly have to reboot, and the checkbox in system>administration>hardware drivers should be unchecked. Check it (and possiby reboot again, or just press ctrl-alt-backspace).

---

### Post by yaywoop on 2008-04-25
The ATI driver already is installed, but its "not in use" 
even if i try unticking and re ticking the box, then restarting the computer, it still shows "not in use"
see the screenshot

---

### Post by kriswillems on 2008-04-25
I had the same problem. xorg.conf is not used anymore as before, the drivers find out their own settings. I believe xorg.conf can only be used to override the settings detected by the driver.

This is what fixed my problem.
sudo apt-get update
sudo apt-get install xorg-driver-fglrx

I rebooted the computer after that.

The driver name in he hardware drivers window changed to:
ATI accelerated graphics driver (instead of ATI fire GL)
 
It was "not in use" and not "enabled"
I just enabled it and restarted the computer.

---

### Post by yaywoop on 2008-04-25
> **kriswillems said:**
> I had the same problem. xorg.conf is not used anymore as before, the drivers find out their own settings. I believe xorg.conf can only be used to override the settings detected by the driver.

This is what fixed my problem.
sudo apt-get update
sudo apt-get install xorg-driver-fglrx

I rebooted the computer after that.

The driver name in he hardware drivers window changed to:
ATI accelerated graphics driver (instead of ATI fire GL)
 
It was "not in use" and not "enabled"
I just enabled it and restarted the computer.

that did the shot. thanks!

---

### Post by vigleik on 2008-04-25
Aha, so installing the driver (sudo apt-get install xorg-driver-fglrx) and checking the box fixed it, just like I said.

There seems to be a bug in the restricted driver management, where it tells you that the driver is installed even if it's not. I should have been more clear in my first post.

---

### Post by vigleik on 2008-04-25
.

---

### Post by gary4gar on 2008-04-25
I am also stuck at 1024x768, whereas my nvidia cards supports 1280x1024

---

### Post by yaywoop on 2008-04-25
what driver are you using gary4gar?

> Aha, so installing the driver (sudo apt-get install xorg-driver-fglrx) and checking the box fixed it, just like I said.

There seems to be a bug in the restricted driver management, where it tells you that the driver is installed even if it's not. I should have been more clear in my first post.
although there is no reason the open fire gl driver shouldn't work. all the compiz effects worked with it. it just mis detected the resolution. 
maybe i should have played around with xorg.conf, but i don't know how it works in ubuntu, it doesn't seem to be used by default.

---

