---
title: "US Keyboard - cannot get rid of dead keys"
date: 2008-02-22
forum: General Help
---

### Post by marktyler on 2008-02-22
Hi, I using a Dell bluetooth multimedia keyboard (US 104 key layout) and I cannot seem to get it setup properly in Ubuntu (7.10). For keyboard model I´ve tried Dell USB Multimedia and Generic 104-key pc with US English layout and I cannot get rid of deadkeys. Double quotes come out wrong and I have to double-tap for a single quote. I´ve tried autodetect on dpkg-reconfigure etc and nothing works. To be honest it´s really starting to p*ss me off as this sort of thing should be dead simple and not so inconvenient - it´s almost enough to make me try and install OSX just to get rid of windows.

Some additional output that may be of use is below. Thanks for your help.

```
 xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us", "nodeadkeys", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us", "nodeadkeys", ""

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = pc104
 options = []
 overrideSettings = true
```

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 2407WFP"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"DELL 2407WFP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by der_joachim on 2008-02-23
Tihis has been posted several times as a bug. That was in 2005, so I do not think that it would be useful to link to the bug reports. 

Anyhoo, what happens if you entirely erase (or safer: comment out)  the XkbVariant line from your xorg.conf and restart X? I have an entirely different layout variant and have no trouble with deadkeys whatsoever, so you may want to play with these a bit.

I understand that you run Gnome. Note that you have to configure the Gnome KB applet as well. I do not use Gnome, so I cannot help you there.

---

### Post by marktyler on 2008-02-24
I´ve tried with and without the variant setting, with and without settings in the gnome config and most variations of US layout all to know avail. I know it&#347; ok when I plug in a UK keyboard (small portable one) but not with the Dell US version. Just thought this wouldn´t be an issue with most things tech originating in the US.

---

### Post by der_joachim on 2008-02-25
It may be a long shot (haven't tried it myself, so be warned), but have you tried the following lline:
```

Option		"XkbModel"	"dellusbmm"

```

instead of

```

Option		"XkbModel"	"pc104"

```

? This explicitly tells xorg that you are using a Dell USB Multimedia keyboard. Hopefully xorg will listen somewhat better now. 

Good luck.

---

### Post by marktyler on 2008-02-26
Yep, tried that one but to no avail. I´m starting to think the keyboard is more hassle than it´s worth as it was always disappearing under windows courtesy of bluetooth being flakey. Honestly thought it´d be easier than this to setup. I´m pretty sure it worked first off in Fedora.

---

### Post by der_joachim on 2008-02-26
Hmmmm.... Maybe [this thread]("http://ubuntuforums.org/showthread.php?t=52952") is of more help?

---

### Post by marktyler on 2008-02-27
Hi, maybe I´m missing something here but what should the settings read for my keyboard - it´s a dell multimedia keyboard, US 104 key, without the need for deadkeys which I cannot seem to be able to turn off. Oh to be able to type a single quote!

---

### Post by izak on 2008-04-14
I have the exact same problem.

---

