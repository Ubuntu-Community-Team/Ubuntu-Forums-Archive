---
title: "MS intellimouse Explorer 2.0 w/tilt wheel - Not working"
date: 2007-03-13
forum: General Help
---

### Post by ChrisBatcho on 2007-03-13
I have tried a number of tutorials to get this mouse to work, but no luck. Perhaps someone can spot what I am doing wrong here.

I am using Ubuntu Edgy and I have an optical Intellimouse Explorer 2.0 w/tilt wheel. I'm not worried about the tilt wheel support (it never really worked well in windows XP) however I do want my side forward/back buttons to work. Some tutorials I have tried are:

[Howto #1](http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/)
[Howto #2](http://ubuntuforums.org/showthread.php?t=183547&highlight=microsoft+tilt+wheel+ms)
[Howto #3](http://katze-mit-wut.azundris.com/archives/126-Microsoft-IntelliMouse-Explorer-2.0,-linux,-xemacs,-and-x.org.html)
[Howto #4](http://www.linuxquestions.org/questions/showthread.php?t=373460)

Currently I have gotten nowhere. None of the tutorials have produced ANY effect. Here is some information from my settings and such:

xorg.conf
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse" "CorePointer"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/event3"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Buttons" "9"
	Option	    "ButtonMapping" "1 2 3 6 7 8 9"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "false"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "FPD1730"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "radeon"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "FPD1730"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
  Option "Composite" "Disable" 
EndSection
```

cat /proc/bus/input/devices
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=0f30 Product=010b Version=0101
N: Name="Jess Tech GGE909 PC Recoil Pad"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/class/input/input2
H: Handlers=event2 js0 
B: EV=b
B: KEY=fff 0 0 0 0 0 0 0 0 0
B: ABS=30027

I: Bus=0003 Vendor=045e Product=008c Version=0057
N: Name="Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse0 event3 ts0 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=1c3
```

What do I do?

EDIT: Mouse stopped working! Am updating from XP :(

---

### Post by ChrisBatcho on 2007-03-14
Bump for help.

At this point my mouse has completely gone bonkers in Ubuntu. When I move it magic happens. Icons move at random, the screen flickers, toolbars move, prompts for different things pop up and go away, and the pointer has a seizure.

I think I might have to just reinstall.

---

### Post by jonathan_c on 2007-03-15
I have the intellimouse from the "Desktop Optical Wireless 5000" Package.

It works just great here (w/o the mouse wheel tilt thing) with the following settings in xorg.conf
```

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option      "CorePointer"
    Option      "Device"        "/dev/input/mice"
    Option      "Protocol"      "ExplorerPS/2"
    Option      "ZAxisMapping"      "4 5"
#   Option      "Emulate3Buttons"   "true"
EndSection

```

cat /proc/bus/input/devices reveals
```

I: Bus=0003 Vendor=045e Product=00e3 Version=0053
N: Name="Microsft Microsoft Wireless Optical Desktop&#65533; 2.20"
P: Phys=usb-0000:00:10.0-1/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse0 event2 ts0 js0 
B: EV=10000f
B: KEY=c0002 400 0 c000000 1f0001 10f80 78407 ffe739fa d971d7ff febeffdf ffefffff ffffffff fffffffe
B: REL=fc3
B: ABS=ffffff01 701ff

```

It's not any different than yours. I haven't bothered with the tilt b/c I haven't found a use for it yet. If I do get it working I'll let you know :)

---

