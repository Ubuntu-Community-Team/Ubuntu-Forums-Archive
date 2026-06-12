---
title: "screen resolution options"
date: 2008-06-03
forum: General Help
---

### Post by sprightlyone on 2008-06-03
hi 
  why is there only 2 screen resolutions offered when i know my 21in monitor will support a lot more
 how do i gain access to the full range of resolutions  
  i would like to rectify this  it feels like my hardware is being strangled 
  how do i tweak video card properties etc. 
 does ubuntu play with the overclocking fraternity or is this a no no

thanks lyle

---

### Post by FuturePilot on 2008-06-03
What graphics card do you have?

---

### Post by EXCiD3 on 2008-06-03
If you've got an nvidia card, open terminal and run "sudo nvidia-settings" if you've got your graphics driver installed (System > Administration > Hardware Drivers) and you can use it to configure your card instead.

As far as I know you can do some overclocking with nvidia cards, not sure about ati. Theres really no reason to overclock in linux, everything runs faster than an overclocked windows box anyways! :)

---

### Post by sprightlyone on 2008-06-03
> **FuturePilot said:**
> What graphics card do you have?

hi 
   my graphics card is a Nvidia Geforce 6500 card 
 
using "If you've got an nvidia card, open terminal and run "sudo nvidia-settings" if you've got your graphics driver installed (System > Administration > Hardware Drivers) and you can use it to configure your card instead. "doesn`t seem to work presently 
thanks lyle

---

### Post by EXCiD3 on 2008-06-04
So do you have your graphics card driver installed? It will have a green check in the box on System > Administration > Hardware And Drivers.

---

### Post by sprightlyone on 2008-06-04
hi 
  in the package manager which files are needed to be downloaded to be installed to make up the nvidia drivers 
  everything i`ve d/l so far hasn`t been enough to appear in the h/ware &driver page 
  i seem to be stabbing in the dark when selecting files
thanks lyle

---

### Post by EXCiD3 on 2008-06-04
When you check the box to enable the driver, it should automatically download and install the packages you need. You're doing it the hard way! :)

---

### Post by sprightlyone on 2008-06-04
> **EXCiD3 said:**
> When you check the box to enable the driver, it should automatically download and install the packages you need. You're doing it the hard way! :)

hi 
 where should i be looking for ¨When you check the box to enable the driver¨
doesn`t appear in the hardware&driver window ?? so i assumed i had to download the packages first &then install them 
  i still not correctly installed as far as i can see
lyle

---

### Post by sprightlyone on 2008-06-04
hi 
  replies have dwindled to a stop but i still need to sort this issue
   what do i change ??
   if drivers are the issue i need to install correctly as the way i did it didn`t solve anything but messed everything up 
 
 lyle

---

### Post by sprightlyone on 2008-06-04
Bump

---

### Post by glennzo on 2008-06-04
> **sprightlyone said:**
> BumpIf it were me I'd be playing around with my **/etc/X11/xorg.conf** file, but that's just me. I'd worry about drivers later.

Back the file up before you make any changes.

Heres mine from a desktop with an NVidia card.
```
# Xorg configuration created by pyxf86config

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerFlags"
	Option "AIGLX" "off"
EndSection

Section "Extensions"
	Option "Composite" "False"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us+inet"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "radeon"
EndSection

[COLOR="Red"]Section "Monitor"
        Identifier   "T903"
        VendorName   "BenQ"
        ModelName    "ModelT903"
        HorizSync    31-82
        VertRefresh  56-76
EndSection[/COLOR]

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	[COLOR="Red"]Monitor    "T903"[/COLOR]
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		[COLOR="Red"]Modes "1280x1024"[/COLOR]
	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection
```
The text in red is what I added to the file. The modes line can contain higher resolutions to accomodate your monitor.

---

