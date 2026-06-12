---
title: "Can't access shared memory."
date: 2005-09-03
forum: General Help
---

### Post by MdaG on 2005-09-03
I'm trying to run syndaemon so that I can disable my touchpad while typing. It helps to avoid accidently inserting code/text where it's not suppose to be. When I try to run syndaemon I get the following.
```

$ sudo syndaemon
Can't access shared memory area. SHMConfig disabled?
```

df gives the following output:
```
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             22715204   8102152  14613052  36% /
tmpfs                   388144         0    388144   0% /dev/shm
/dev/hdc               6375376   6375376         0 100% /media/cdrom0
/dev                  22715204   8102152  14613052  36% /.dev
none                      5120      2836      2284  56% /dev
```

And at last. This is my xorg.conf:
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
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
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
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
	Option          "SendCoreEvents"       	"true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
	Option		"TouchpadOff"		"1"
	Option		"SHMConfig"		"on"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Does any know how I get to run syndaemon. I don't get this "non access" on my Gentoo system.

---

### Post by MdaG on 2005-09-07
*bump*
I still haven't figured out how to proceed. Anyone?  :-?

---

### Post by bcknapp on 2007-05-31
I am having the same problem and I want to be able to do what you're trying for the same reason.

---

