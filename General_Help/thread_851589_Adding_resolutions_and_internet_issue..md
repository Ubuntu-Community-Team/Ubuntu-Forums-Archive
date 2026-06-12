---
title: "Adding resolutions and internet issue."
date: 2008-07-06
forum: General Help
---

### Post by Abhlanc on 2008-07-06
Recently installed Ubuntu for the first time on a computer I just built, and I've been customizing it to my preferences.  The monitor resolution I want of course isn't anywhere on the list of resolutions I can use, so I've been looking into how to add more resolutions.  All of the guides tell me to go into my xorg.conf file and find the section detailing my monitor with the resolutions I can use and add in the ones I want.  Something like:  ```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display":
        Depth        16
        Modes      "1280x1024" "1024x768"
    EndSubSection
EndSection
```

The problem is that I don't have any of these specific identifiers or other stuff in my file for me to add the resolutions I want onto.  I've already tried adding in the missing stuff, but all it does is force my computer to run in low graphics mode at an even lower resolution.  My file looks like:  ```
Section "InputDevice"
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
```

Does anyone have any idea on how I'm supposed to change the file so I can get the resolutions I want?

The second problem is that the internet on this computer just stops working completely sometimes.  Resetting once or twice seems to fix the issue, but I'd like to fix the problem completely so I don't have to deal with it.  The internet works fine on the other computers in the house even when this happens so it's not a modem or router issue, and I don't believe it's an issue with my hardware.

I'm *guessing* this is the right section for resolution issues.

---

### Post by Ms_Angel_D on 2008-07-07
Hi Abhlanc, I too had issues with my nvidia card when installing ubuntu I fixed it like this.


in the terminal I ran
```
sudo apt-get install nvidia-settings
```

then I went to System > Hardware Drivers and made sure the Nvidia Accelerated Graphics Driver was enabled

then in the terminal I ran

```
sudo nvidia-settings
```

from the window that opened I went to the

X Server Display Configuration section

 and selected my perferred resolution then clicked Apply, and then I clicked

Save to X Configuration File

and that solved my resolution issues. Hope this helps!

Angel

---

### Post by Abhlanc on 2008-07-07
I have the new ATi HD4850 video card, though.  I attempted to do the same thing you did except applied to ATi cards, but when I enter "sudo apt-get install ati-settings" it says "E: Couldn't find package ati-settings".  I found I can successfully download the Nvidia settings, but that doesn't help me, of course.

---

### Post by Abhlanc on 2008-07-09
Bump.

---

### Post by snakeyez11 on 2008-07-09
Are you using the proprietary driver?  If so try:

```
sudo aticonfig --initial
```

Then edit your xorg.conf and add the resolutions you need.

---

### Post by Ms_Angel_D on 2008-07-14
Sorry I didn't realize that you we're using an ATI card so yeah my instructions won't help. :(

---

