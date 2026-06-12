---
title: "[SOLVED] Dual moniters, different resolutions, 300px overshoot"
date: 2008-03-20
forum: General Help
---

### Post by jon.mithe on 2008-03-20
Hi,

Sorry for another post on dual monitors but I am struggling to find solutions to my problem.

I have a 22" widescreen on DVI and a 19" on the VGA, 22" being the main screen and 10" being a side screen to the left of it.

I have configured my xorg.conf and it all seems to be working bar 1 exception. On my 22" screen the mouse goes off the side of the right hand screen for a bit.  The menu bars appear normal but theres some extra room offscreen for some reason.

Resolution of my 22" is 1680x1050 and the resolution of my 19" is 1280x1024 = a combined width of 2960.  However, in the System>Preferences>Screen resolution it comes up as 3360x1050 -  i.e. there has been an extra 400px added.

If anyone knows why this may be a problem or how to go about to fix it that'd be great. I'm on the latest standard ubunutu version (uname -a 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux) and I have an ATI card.  A friend recommended aticonfig, in particular pairs mode, but every time it fails to write to the xorg saying "bad descriptor".  I'm guessing using those sort of features on the aticonfig is the way to go.

I'm looking for the 22" to be the main monitor, menubars etc, and the 19" to just sit on the side without any menu bars (i.e I do not want to spread my desktop across the both screens like i had 1 really big monitor)

Below is a copy of the interesting bits of my xorg.conf, any help would be most appreciated.

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Widescreen" 0 0
	Screen 	       "Squarescreen" LeftOf "Widescreen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Logitech MX1000" "CorePointer"	
EndSection

Section "Monitor"
	Identifier   "Primary Monitor"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Primary Driver"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal, reverse" 
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Squarescreen"
	Device     "Primary Driver"
	Monitor    "Primary Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Widescreen"
	Device     "Primary Driver"
	Monitor    "Primary Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection


```

(I used to have 2 19" screens and I used the "Option  "DesktopSetup" "horizontal, reverse" " in the device section to lay them out.  But I can only get my setup working using the LeftOf in the serverLayout, which I'm guessing is not a good way to go.)

---

### Post by jon.mithe on 2008-03-20
I tried setting via the aticonfig but I can not get it to edit the file becuase of that bad descriptor error. However, I did this manually but it crashes on startup and ubuntu has to go into the safe graphics config.

Could this be a driver issue?

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection


Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "DesktopSetup" "horizontal,reverse"
        Option      "PairModes" "1680x1050+1280x1024"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

---

### Post by TekNullOG on 2008-03-20
Me and my buddies have the same problem. We use the Big-Desktop for Ati dual display and it adds like extra pixels past the end of the 2nd screen.

It is really obvious when everything is full screen and the desktop switcher shows a blank space at the end of the screen. Also, when you take a screen shot, you can see how much is missing.

I never figured it out but it was never an issue for me. Everything works fine anyways.

---

### Post by jk-pc on 2008-03-21
Hey,

I have exactly the same problem.. Running fglrx and I used aticonf to configure my dual screen desktop as a "big desktop".
I have a 17" (running at 1280x1024) and a 22" widescreen (1680x1050)... Therefore the *theoretical* width should be 2960 - but its running at 3360x1050 !

As eightinches said, I can see the "extra" space on the right hand side when I'm taking a screenshot..
Also, tooltips seem to expand into this space as well (which is rather annoying!)

The panels and fullscreen-applications seem to adhere to the correct screen sizes - but why do tooltips just ignore this and go into this extra space?

Any ideas on how we could manually restrict the desktop to 2960x1050 ?

This problem also seems to occur for people who are trying to two screens at more than 3360x1050. 
It seems like fglrx is defaulting the resolution to this setting? Maybe it's a driver-specific issue that will be fixed in the next fglrx release?

jk-pc

---

