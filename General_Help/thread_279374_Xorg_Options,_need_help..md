---
title: "Xorg Options, need help."
date: 2006-10-17
forum: General Help
---

### Post by Kameli on 2006-10-17
Hello! :)

I just watched my xorg.conf, and i noticed there some interesting sections like =

Option		"XkbModel"	"pc105"

What this should be when i use Logitech Deluxe Access Keyboard?

And

Option		"Protocol"		"ImPS/2"

What this should be when i use Logitech MX518 USB?

And i have also wondered a long time about this =

BusID		"PCI:1:0:0"

So what that does? :) My friend has 5:0:0, and i also tried to change that but then my X didn't start, so i changed it to back. :)

Sorry about my very bad english. :)

---

### Post by woedend on 2006-10-17
Try using 
ExplorerPS/2
for mouse...i think youll find it work better.  Mine reads as follows:
Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

---

### Post by CatKiller on 2006-10-17
I can't answer many of your questions, but the BusID is the "address", if you like, of where in your computer the card is. So there's really no reason to expect that your card would be in the same place as your friend's. The exception is that AGP slots are often at 1:0:0, since that is a bus all on its own.

**man xorg.conf** may tell you information about all the options. If you're desperate to get things reconfigured differently, you could try **sudo dpkg-reconfigure xserver-xorg**. This will ask you a bunch of questions about your keyboard, mouse and graphics card and adjust your xorg.conf accordingly.

---

### Post by Kameli on 2006-10-18
Ok, thanks for posting. :)

I think my friend has 5:0:0 because he uses PCI-E and i AGP. =)

---

### Post by Kameli on 2006-10-18
:( My **Xorg.0.log** gives sad news to me :(
[B]
(WW) NVIDIA(0): Unable to read EDID for display device CRT-0
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from EDID.
[/B]
And
[B]
(WW) NVIDIA(0): Option "VideoOverlay" is not used
[/B]
And i have in **xorg.conf** following 

[B]
Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6600 GT]"
        Driver          "nvidia"
        Option          "VideoOverlay"          "on"
        Option          "NoLogo"                "1"
        BusID           "PCI:1:0:0"
EndSection
[/B]

As you see, there is

[B]
Option          "VideoOverlay"          "on"
[/B]
=)

I think you know what that does, but if not, it allows you use Hardware acceleration in videos =) i like when my CPU and GPU both are making nice powerfull work together =)

---

### Post by CatKiller on 2006-10-18
The fact that the card can't report the frequencies for the monitor isn't too much of a problem. If you aren't getting the resolutions/refresh rates that you think you should be, then you can find the HorizSync and VertRefresh rates for your monitor and put them in the Monitor section of your xorg.conf.

It's possible that the VideoOverlay option is for a different driver - the Ati one or the open source one, perhaps, and with the nVidia driver you don't need to specify it. You'd need to read the documentation (if it exists) for the driver that you're using to know for sure.

---

