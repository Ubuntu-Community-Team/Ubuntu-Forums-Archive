---
title: "yo, where's the decent screen resolutions controls gone?!"
date: 2008-04-24
forum: General Help
---

### Post by brainstuff on 2008-04-24
Had a major faff (and learning curve) getting my Thinkpad T21 to give me the full 1400x1050 display it was capable of on 7.10 (in fact that taught me a lot about Recovery Mode :))  

...But now I'm on Xubuntu 8.04 and my familiar "Screens and Desktops" option is gone, and the slimline manager in "Applications -> Settings -> Settings Manager -> Display" is only giving me options of 800x640 and lower (despite the machine actually running in 1024x768 ). 

Here's my new xorg.conf (which is miniscule compared to my old one):

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
  SubSection "Display"
  depth 16
  virtual 1400 1050
  EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

...I've tried adding in the relevant bits from here: [http://ubuntuforums.org/showthread.php?t=60008](http://ubuntuforums.org/showthread.php?t=60008)
(and adding "1400x1050" as an option)
...but there's no change either in the desktop that comes up after restarting X or in the list of options in "Display Settings".

Any ideas?
Thanks

---

