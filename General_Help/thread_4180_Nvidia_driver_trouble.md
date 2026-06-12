---
title: "Nvidia driver trouble"
date: 2004-11-12
forum: General Help
---

### Post by renoir98 on 2004-11-12
Hi all,
i have an Nvidia Geforce2 Mx400 video card on my box,
so i installed and enabled the binary driver "nvidia-glx 1.0.6111".
After doing this i'm experiencing a strange issue.
I boot the system but the process stops right before loading X and the result is a black
screen.
So i type Ctl-Alt-Canc and the system halts,then reboot and everything goes fine.
Shortly i have to boot twice to start working on my box :-(
This is my XF86Config-4 file:
```

        Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	HorizSync	30-71
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I know this is already been experienced by other users but it seems that a solution has not been found yet....
Thanks in advance,ronnie.

---

### Post by Marauder1 on 2004-11-12
This is the way i installed my Geforce3 ti-200 :

For NVIDIA Video Drivers: (from a console )
------------------------
A. sudo apt-get install nvidia-glx
B. sudo nvidia-glx-config enable
C. sudo reboot

Note: (optional): If you are going to compile 3d applications, you will want to install the nvidia-glx-dev package, like sudo apt-get install nvidia-glx-dev
Note: (optional): the nvidia-settings package provides a control panel to configure graphics card options such as gamma correction. Install: sudo apt-get install nvidia-settings.

hopes it helps !!!

---

### Post by jdong on 2004-11-12
If you installed NVidia manually without apt, make sure you edit **/etc/modules** to include the entry **nvidia**, then run **update-modules**.

---

### Post by dubdubdub on 2004-11-12
I have had ongoing troubles trying to get these drivers to work here: [http://www.ubuntuforums.org/showthread.php?t=3917](http://www.ubuntuforums.org/showthread.php?t=3917)

Hopefully someone can help out?

I understand that the new drivers haven't been released yet. Isn't there something I can "roll back" to make the drivers work...or is that more work than waiting for a new driver?

---

### Post by renoir98 on 2004-11-13
[QUOTE=Marauder1]This is the way i installed my Geforce3 ti-200 :

For NVIDIA Video Drivers: (from a console )
------------------------
A. sudo apt-get install nvidia-glx
B. sudo nvidia-glx-config enable
C. sudo reboot

Note: (optional): If you are going to compile 3d applications, you will want to install the nvidia-glx-dev package, like sudo apt-get install nvidia-glx-dev
Note: (optional): the nvidia-settings package provides a control panel to configure graphics card options such as gamma correction. Install: sudo apt-get install nvidia-settings.

hopes it helps !!![/QUOTE]

I did this but still have the problem;
i'll try to install a previuos version,if i find it somewhere.... :?

---

### Post by Marauder1 on 2004-11-14
Maybe you can try that link in the Ubuntu forum :

[http://www.ubuntuforums.org/showthread.php?t=4214](http://www.ubuntuforums.org/showthread.php?t=4214)

And see what others are trying to do ....

See ya !!1

---

