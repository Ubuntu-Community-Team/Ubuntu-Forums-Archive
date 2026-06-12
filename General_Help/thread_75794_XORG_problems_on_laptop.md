---
title: "XORG problems on laptop"
date: 2005-10-14
forum: General Help
---

### Post by fresch on 2005-10-14
Dear all,

I have used ubuntu 5.04 till now, have removed it and installed it new with 5.10. I used the same xorg.conf with NVIDIA drivers support (nvidia-glx). 

- the touchpad does have a strange behaviour, scrolling gtk-2 windows is random, clicking onto a tab work once over two - it was previously (5.04)  working well

- I cannot input language specific chars using the keyboard (they are e.g. éöüä), the altgr does not work and I don't get e.g. #¢¦ etc. -  while the rest (qwertz...) is ok

I switch back to 5.04  :???:  - however I hope you will have some answer to help. 
Thanks a lot,

NOTE
the hardware is a toshiba satellite 2410 w. xorg.conf as follows : 

Section "Module"
	#Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	#Option		"XkbDisable"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr_CH"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Generic Mouse"
	Driver		"mouse"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"AGP:01:00:0"
	# Override DDC 
	Option		"NoDDC" "1"
	Option		"IgnoreEDID" "1"
	# Important when using TFT  
	Option      	"GenerateRTList"   "0"
	Option      	"OverridePolarity" "1"
	# Switch AGP
	Option		"NvAGP" "3"
	# Some Pointer Eyecandy
	Option		 "CursorShadow" "1"
	Option		 "CursorShadowAlpha" "63"
	Option		 "CursorShadowYOffset" "2"
	Option		 "CursorShadowXOffset" "4"
	# Picture Improvement
	Option		"DigitalVibrance" "0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-60	
	VertRefresh	43-72	
	Option		"DPMS"
	Option		"NoDDC" "1"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24	
	# Override DDC 
	Option  "NoDDC" "1"
	# Switch AGP
	Option  "NvAgp" "3"
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

##	SECTION FOR TV - begin
Section "Screen"
	Identifier	"TV"
	Device		"Nvidia Geforce 4 420"
	Monitor		"Generic Monitor"
	DefaultDepth	 24
	SubSection "Display"
		Depth	 24
	EndSubSection
EndSection

Section "Device"
        Identifier      "Nvidia Geforce 4 420"
	Driver          "nvidia"
	BusID           "AGP:01:00:0"
	# Override DDC
	Option          "NoDDC" "1"
	Option          "IgnoreEDID" "1"
	# Important when using TFT
	Option          "GenerateRTList"   "0"
	Option          "OverridePolarity" "1"
	# Switch AGP
	Option		"NvAGP" "3"
	# Some Pointer Eyecandy
	Option		 "CursorShadow" "1"
	Option		 "CursorShadowAlpha" "63"
	Option		 "CursorShadowYOffset" "2"
	Option		 "CursorShadowXOffset" "4"
	# Picture Improvement
	Option		"DigitalVibrance" "0"
	# TV Twinview
	Option		"TwinView" "1"
	Option		"SecondMonitorHorizSync" "30-50"
	Option		"SecondMonitorVertRefresh" "60"
	Option		"TwinViewOrientation" "Clone"
	Option		"TVOutFormat" "COMPOSITE"
	Option		"ConnectedMonitor" "DFP,TV"
	Option		"TVStandard" "PAL-B"
	Option		 "MetaModes" "1024x768 @1024x768,1024x768 @1024x768; 800x600 @800x600,800x600 @800x600; 640x480 @640x480,640x480 @640x480"
EndSection
##	SECTION FOR TV - end 

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Generic Mouse"
EndSection

Section "ServerLayout"
	Identifier	"Twinview"
	Screen		"TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Generic Mouse"
EndSection


Section "DRI"
	Mode	0666
EndSection

---

### Post by oberon on 2005-10-14
You may want to check, but I believe that there some small changes to the conf file in Breezy.  Somthing about Keyboard being changed to KB or the other way around.  I think I remember seeing somthing about it in the Dev forums before the release.

-oberon

---

### Post by fresch on 2005-10-20
Thank you Oberon, I will go in that way!

---

