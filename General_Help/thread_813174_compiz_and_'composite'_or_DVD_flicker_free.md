---
title: "compiz and 'composite' or DVD flicker free?"
date: 2008-05-30
forum: General Help
---

### Post by Fenris_rising on 2008-05-30
hi all
small question. im running HH 8,04 and ive got my dvd running commercial dvds. compiz isnt installed as i have had a few problems with it not doing certian things. anyway i have had to disable "composite" in my xorg file as it causes flickering of the dvd picture. with composite disabled i cant set my visual effects to normal or extra as the error refering to composite pops up. so what do you do to have the effects and flicker free dvd playback? i have been reading bucket loads on here but a lot of it goes over my head. heres my zorg.conf if it helps. i used envy ng to install my video drivers. ATI driver version 2.1.7412 release is installed. in section 'device' i have added by hand some items.

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option		"TexturedVideo"	"on"
	Option		"UseFastTLS"	"0"
	Option		"BlockSignalsOnLock"	"on"
	Option		"KernelModuleParm"	"locked-userpages=0"
	Option		"ForceGenericCPU"	"off"
	Option		"XAANoOffscreenPixmaps"	"on"
	Option		"BackingStore"	"on"
	
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"disable"
EndSection

---

