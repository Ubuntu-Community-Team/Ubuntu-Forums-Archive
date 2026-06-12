---
title: "Resolution problem"
date: 2006-07-03
forum: General Help
---

### Post by Rahu on 2006-07-03
I can't seem to get the resolution to go over 1024x768 witht he nvidia drivers(installed by automatix) installed. I can get it to 1280x1024 just fine by using the x configuration dealy + reboot, but then there is no hardware acceleration at all. I'm pretty new to messing with x, so i really have no idea what to try.

Thanks for any help :)

---

### Post by Dr. Nick on 2006-07-04
2 Options really

get it to the correct resoulition then manually edit the file /etc/X11/xorg.conf to change the driver from "nv" to "nvidia"

or 

get nvidia driver going in a low resoulition then try here
[http://ubuntuforums.org/showthread.php?t=193556](http://ubuntuforums.org/showthread.php?t=193556)

---

### Post by mstlyevil on 2006-07-04
[QUOTE=Rahu]I can't seem to get the resolution to go over 1024x768 witht he nvidia drivers(installed by automatix) installed. I can get it to 1280x1024 just fine by using the x configuration dealy + reboot, but then there is no hardware acceleration at all. I'm pretty new to messing with x, so i really have no idea what to try.

Thanks for any help :)[/QUOTE]

Another option is to exit GDM by typing Alt+F2 and then enter this comand in the terminal.

```
sudo dpkg-reconfigure xserver-xorg
```

A utility will open you can use to reconfigure xserver to use your proper driver and manually set you proper video resolution. I have an old pc this is the only way I can get everything to work correctly when I install Ubuntu.

---

### Post by Dr. Nick on 2006-07-04
[quote=mstlyevil]Another option is to exit GDM by typing Alt+F2 and then enter this comand in the terminal.

```
sudo dpkg-reconfigure xserver-xorg
``` 
A utility will open you can use to reconfigure xserver to use your proper driver and manually set you proper video resolution. I have an old pc this is the only way I can get everything to work correctly when I install Ubuntu.[/quote] 


True, If you take this dpkg-reconfigure route I believe it is possible to chose the "nvidia" driver from the list aslong as its installed; then you should be able to choose the higher res like before.

---

### Post by Rahu on 2006-07-04
Tried that, no good.
> (WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_60"; removing.

But that's only using nvidia as my driver, it works fine when using nv.

Heres my config if that helps any
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x1024_60" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x1024_60" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x1024_60" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x1024_60" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x1024_60" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x1024_60" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Rahu on 2006-07-04
Anyone have any idea on this? It's really annoying :o

---

### Post by Dr. Nick on 2006-07-04
ugh, your xorg config looks correct. The Geforce 2 looks to fall on the boarder line of cards supported by the nvidia-glx and nvidia-glx-legacy package. 

I dont know what version automatix uses, I would think the nvidia-glx which is for newer cards. Open up synaptic and search nvidia, If nvidia-glx is installed then mark it for uninstall and mark nvidia-glx-legacy for install and apply it and see if that helps.

If its like that already then switch it around, Basically what I am saying is switch nvidia-glx and legacy and see if that helps.

---

### Post by anjoze on 2006-07-05
Try to add the blue line:
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
    [COLOR="Blue"]Option	"Ignore EDID" "1"[/COLOR]

---

