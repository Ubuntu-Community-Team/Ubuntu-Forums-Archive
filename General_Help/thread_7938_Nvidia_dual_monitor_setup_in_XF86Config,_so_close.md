---
title: "Nvidia dual monitor setup in XF86Config, so close"
date: 2004-12-12
forum: General Help
---

### Post by -luke- on 2004-12-12
I'm working away at getting my dual-head-card/dual monitor set up correctly, but I've hit a wall. The basic problem is that the 'nvidia' driver with TwinView enabled insists on putting the main gnome desktop on my 2nd monitor and leaving me with a big 20" LCD off to the side that just holds some windows now and then.

The setup is this:

GeForce4 Ti4200 dual head card, one DVI output, one analog VGA output.
Dell 2001FP connected to the DVI output. Ideally this would be where the desktop lives, currently it's just an extended portion of the screen.
Dell 1702FP connected to the analog VGA output, which is where the desktop insists on living
'nvidia' driver downloaded via synaptic.
All this with the 2.6.8.1-3-386 Warty version on a Pentium4. I'm new to linux, and I've quickly run up against my limits. 

Any suggestions on how to get the desktop to live on my 20" screen connected to the DVI output? 

Below is my current XF86Config file, which puts the main desktop out to the VGA head of my card. 
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
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
#	Load	"GLcore"
#	Load	"dri"
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
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200] 0"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"TwinView"
	Option		"MetaModes"		"DFP: 1280x1024,CRT: 1280x1024"
	Option 		"SecondMonitorHorizSync"	"CRT: 30-70"
	Option		"SecondMonitorVertRefresh"	"CRT: 50-160"
	Option		"TwinViewOrientation"		"LeftOf"
	Option		"ConnectMonitor"		"DFP"
	VideoRam	65536
#	Option		"UseFBDev"		"true"
Option "NvAGP" "3"
Option "DigitalVibrance" "0"
Option "TwinView" "1"
Option "SecondMonitorHorizSync" "30-70"
Option "SecondMonitorVertRefresh" "50-160"
Option "TwinViewOrientation" "RightOf"
Option "TVStandard" "NTSC-M"
Option "MetaModes" "1600x1200 @x,1280x1024 @x"
EndSection



Section "Monitor"
	Identifier	"DELL 2001FP"
	HorizSync	30-70
	VertRefresh	50-160
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier	"Screen 0"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4200] 0"
	Monitor		"DELL 2001FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection



Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen 0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

# Section "DRI"
#	Mode	0666
# EndSection

```

---

### Post by used2win32 on 2005-01-07
This looks like a configuration issue.

I hope the information below helps.



There needs to be a 'Device' section for each display, in other words, each output of your card.

Remember that display '0' is the primary display. 

--------------------------------------------------------
Section "Device"
Identifier "nvidia0"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 0
EndSection

Section "Device"
Identifier "nvidia1"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 1
EndSection
--------------------------------------------------------

And a screen section for each display.

--------------------------------------------------------
Section "Screen"
Identifier "nvidia0screen"
Device "nvidia0"
Monitor "dell M992"
DefaultDepth 24
Subsection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
ViewPort 0 0
EndSubsection
EndSection

Section "Screen"
Identifier "nvidia1screen"
Device "nvidia1"
Monitor "dell M992"
DefaultDepth 24
Subsection "Display"
Depth 24
Modes "1280x1024" "1024x768" "1152x864" "800x600" "640x480
ViewPort 0 0
EndSubsection
EndSection
--------------------------------------------------------


This option
--------------------------------------------------------
Option "TwinViewOrientation" "RightOf"
--------------------------------------------------------
Specifies where the second montor is in relation to the first.

The options are:

            "RightOf"  (the default)
            "LeftOf"
            "Above"
            "Below"
            "Clone"

---

### Post by used2win32 on 2005-01-09
I posted the message above when I was at work.  Attached are the relevant parts of my working xorg.conf file.  I should add that since I am on a dial-up ISP at home (we live several miles out of town) and can not download ISO's at work, I am waiting for my copy or Unbuntu.  In the meantime I am still running Slackware 10.  That is where this file is from...  For those who just want to see, I added a very small screenshot of a simple desktop.

---

### Post by JackDog on 2005-01-10
[QUOTE=used2win32]
There needs to be a 'Device' section for each display, in other words, each output of your card.
[/QUOTE]

Actually that is incorrect. In a twinview setup (as oppsed to native xinerama) You only need to define one device. In fact for older nvidia cards, there is only one device on the PCI bus. 

```
Section "Screen"
    Identifier  "DualScreen"
    Device      "NVidia"
    Monitor     "LCD"
    DefaultDepth 16
    Option "NvAGP" "0"
    Option "NoLogo" "true"
    Option "HWCursor" "true"
#    Option "ConnectedMonitor" "CRT-0, CRT-1"
    Option "ConnectedMonitor" "CRT, CRT"
    Option "TwinView" "true"
    Option "SecondMonitorHorizSync" "31.5 - 70"
    Option "SecondMonitorVertRefresh" "85"
    Option "MetaModes" "1280x1024, 1024x768; 1280x1024, 1280x1024; 1024x768, 1024x768; 1024x768, 800x600"
    Option "TwinViewOrientation" "LeftOf"
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600"
        ViewPort    0 0
    EndSubsection
EndSection
```

Use the commented out line to reverse the monitors. If your Monitors are backwards, use this line. By specifying a number after the keyword CRT you can manipulate the order of the detected monitors. 

```

    Option "ConnectedMonitor" "CRT-1, CRT-0"

```

That should reverse them please post back here if it doesnt. If you have twinview setup correctly it will transparently emulate xinerama and you should have separate dual desktops that gnome and KDE can recognize and use.

---

### Post by sonium on 2005-06-15
hi, it nearly works. the only thing I cant is reversing the order of my Monitors.

If I just do ```
ConnectedMonitor CRT-1
``` the monitor I want to use as primary works, but the other keeps black. Any other options I tried dont reverse anything.

here is my current xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
FontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
FontPath "/usr/lib/X11/fonts/misc"
FontPath "/usr/lib/X11/fonts/cyrillic"
FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/Type1"
FontPath "/usr/lib/X11/fonts/CID"
FontPath "/usr/lib/X11/fonts/Speedo"
FontPath "/usr/lib/X11/fonts/100dpi"
FontPath "/usr/lib/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"

Load "bitmap"
Load "dbe"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
# Load "GLcore"
# Load "dri"
Load "int10"
Load "record"
Load "speedo"
Load "type1"
Load "v4l"
Load "vbe"
Load "xtt"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xfree86"
Option "XkbModel" "pc101"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "nv4ti"
Driver "nvidia"
BusID "AGP:1:0:0"
VideoRam 65536
EndSection


Section "Monitor"
Identifier "dell M992"
HorizSync 30-70
VertRefresh 50-160
Option "DPMS"
EndSection


Section "Screen"
Identifier "DualScreen"
Device "nv4ti"
Monitor "dell M992"
DefaultDepth 16
Option "NvAGP" "1"
Option "NoLogo" "false"
Option "HWCursor" "true"
Option "ConnectedMonitor" "CRT-1, CRT-0"
Option "TwinView" "true"
Option "SecondMonitorHorizSync" "31.5 - 70"
Option "SecondMonitorVertRefresh" "85"
Option "MetaModes" "1280x1024, 1024x768; 1280x1024, 1280x1024; 1024x768, 1024x768; 1024x768, 800x600"
Option "TwinViewOrientation" "LeftOf"
Subsection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600"
ViewPort 0 0
EndSubsection
EndSection



Section "ServerLayout"
Identifier "Default Layout"
Screen "DualScreen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

# Section "DRI"
# Mode 0666
# EndSection

```

---

### Post by mattsm8 on 2005-10-23
Hi all

I managed to get it going in 4 simple steps, I documented it here: [http://www.glawing.com/forum/viewtopic.php?t=14]("http://www.glawing.com/forum/viewtopic.php?t=14")

have fun!    /mattsm8

---

### Post by Dustismo on 2005-10-27
I am having the same problem..  Did you ever get it resolved?

Thanks,
Dustin

---

