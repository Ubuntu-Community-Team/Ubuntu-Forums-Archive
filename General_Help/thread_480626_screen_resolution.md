---
title: "screen resolution"
date: 2007-06-21
forum: General Help
---

### Post by Alek900 on 2007-06-21
how can i change the screen resolution to a resolution thats not in the screen resolution options??

---

### Post by avik on 2007-06-21
Open up a Terminal window, and type in:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

When it asks for the resolution, choose the resolution you want.

---

### Post by r0ck80y on 2007-06-21
As root, open /etc/X11/xorg.conf file. In the "Screen" section where you have something like this written:```

 SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
```
add along the 'Modes' line the resolution you want. Say if u want 1280x1024, edit the modes line as:```

Modes    "1280x1024"  "1024x768" "800x600" "640x480"
```
Be careful! Dont put a resolution that isnt supported by your monitor.
Save file and login again or reboot

---

### Post by Happy_Man on 2007-06-21
Do you have a Nvidia card? If so, open up a terminal (Applications --> Accessories --> Terminal) and type ```
sudo nvidia-settings
``` That will give you an option to change resolution. If not, still, open a terminal and type: ```
gksudo gedit /etc/X11/xorg.conf
``` go down to the section that looks like this: > Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 420]"
	Monitor		"DELL E171FPb"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

And add in the resolutions that you want following the proper format.

---

### Post by Alek900 on 2007-06-21
thanks all, the resolution is now correct :D

---

