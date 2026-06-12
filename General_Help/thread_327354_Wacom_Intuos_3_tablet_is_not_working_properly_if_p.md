---
title: "Wacom Intuos 3 tablet is not working properly if plugged after X-server started"
date: 2006-12-29
forum: General Help
---

### Post by Dakmor on 2006-12-29
Ok, here is the situation:
USB Wacom Intuos 3 tablet works mostly perfectly (pressure, no problems with GIMP, etc.) Wacom-tools are installed. BUT if unplugged and plugged back it's not working properly - cursor is not moving while pen is away from the tablet (although it should). 
```
wacdump /dev/input/wacom
``` in this case gives a perfect picture - everything working properly. So I can only think of some problem with configuration of input devices in xorg.conf:
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse" "SendCoreEvents"
        InputDevice    "stylus" "AlwaysCore"
        InputDevice    "cursor" "AlwaysCore"
        InputDevice    "eraser" "AlwaysCore"
        InputDevice    "pad"
        InputDevice    "Synaptics Touchpad" "SendCoreEvents"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "Auto"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection


#################
# WACOM TABLET
#################

Section "InputDevice"
        Identifier  "pad"
        Driver      "wacom"
        Option      "USB" "on"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "pad"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "USB" "on"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "USB" "on"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "USB" "on"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
EndSection

########################
#  END WACOM
########################

```

I must say that I tried both in "SendCoreEvens" and "AlwaysCore" in ServerLayout section - no difference.

Can anybody suggest a workaround other that reloading X-Server each time I'm in a mood for drawing?

---

### Post by OpsVentus on 2006-12-29
Hello Dakmor,

if you have a look at the documentation(my source) [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)
Note 'Option "TPCButton" "on"'

So I would say try changing:
```

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

```
into:
```

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
        Option      "TPCButton" "on"
EndSection

```

Cheers,
Bart.

---

### Post by Dakmor on 2006-12-29
OpsVentus,

Thanks for the suggestion. For sure I'll try it and if it works report it here.
But I have a feeling that x-server treats tablet as a mouse when it's being plugged in...
BTW, Synaptic Touchpad has to do nothing with tablet - it's just the laptop touchpad.

---

### Post by vaporX88 on 2008-04-15
the fix provided by OpsVentus didn't work for me.  I have a graphire4 tablet hooked up to my Compal FL92 and on top of Dakmor's original problem, I seem to have another major issue.

My laptop won't boot properly (screen corruption as if graphics driver failed) without the tablet plugged in.

I've been doing a bit of research here and there but it always winds back down to my xorg.conf file.  here it is in all its flawed glory.  somebody please help!:confused:

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"TPCButton"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
  	Option        	"USB"	"on"
	Option		"Mode"	"absolute"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
  	Option        	"USB"	"on"
	Option		"Mode"	"absolute"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
  	Option        	"USB"	"on"
	Option		"Mode"	"relative"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
  	Option        	"USB"	"on"
	Option		"Mode"	"relative"
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	262144
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	60
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600M GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"	"CorePointer"
	InputDevice	"Generic Keyboard"	"CoreKeyboard"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection

Section "Module"
	Load		"glx"
EndSection
```

---

### Post by fragos on 2008-04-15
There is indeed some reason why the Wacom must be attached before starting X. I run a Wacom Graphire4, laser mouse and USB touchpad. Cursor control automatically changes to the divice I use. I leave my Wacom connected to USB on my desktop. Just as a matter of information, I power down when I leave the house or retire in the evening for security reasons.

---

