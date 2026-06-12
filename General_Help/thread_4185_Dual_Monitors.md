---
title: "Dual Monitors"
date: 2004-11-12
forum: General Help
---

### Post by TravisNewman on 2004-11-12
I know this is possible, at least in theory ;)

I have a cheap crappy old monitor and a cheap crappy old video card to go along with it. I think it's a trident video card, and it's a compaq presario 1410 monitor (yes, a 14 inch monitor, I know, I know, it's crappy).

In order to get them working together, I suppose I just define another video adapter and another monitor, and then another screen using them, and then add it to the layout close to the bottom. Is that right?

Next up, how do I change the setup so that the old crappy monitor's desktop comes up above the one I'm using now? And how do I configure it so that when I play videos or 3d games or anything, that they'll go to the default monitor?

---

### Post by CompShrink on 2005-01-13
I am currently working on setting mine up again (was at home for winter break of college, and only had 1 monitor there) and I must say Ubuntu is annoying in this matter. Suse had a nice GUI interface (SaX2) to set up 2 (or more) monitors, in xineorama, clone, or independant sessions.

From what i've read in other posts in this forum, I need to do a bunch of config file editing. Now, while I can do that, it's annoying, and dualmonitor setups are already common enough this should be addressed.

---

### Post by JackDog on 2005-01-13
I know with twinview you can set it up to autodetect monitors. So if you startup with only one, Xinerama will be disabled and it will run correctly. If you startup with two, xinerama is enabled and it works fine. 

I would think xinerama would have the same config option. It simply has to do with detecting present monitors. You could also setup a profile script to either swap out config files for single or dual. Or you could definte two serverlayouts in the conf file and simply choose which one you want use on the command line (when starting X) or change the default server layout when the system boots.

---

### Post by jak on 2005-01-16
Is it possible for someone to write a How To for this? I've only been using Ubuntu for a very short while, and I'm getting to grips with it and the whole Linux way of working. Soon I'll be getting dual monitor setup and can only hope I can find out how.
But for now I'm going to see what I can find about xinerama.

---

### Post by woifi on 2005-01-16
[QUOTE=jak]Is it possible for someone to write a How To for this? I've only been using Ubuntu for a very short while, and I'm getting to grips with it and the whole Linux way of working. Soon I'll be getting dual monitor setup and can only hope I can find out how.
But for now I'm going to see what I can find about xinerama.[/QUOTE]
 hi!

dual monitors with linux isn't hard to realise. i have a 19" crt and a 15" tft on my ubuntu box and it works good for me. well, here's my XF86Config-4:
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
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"6 7"
	Option		"Resolution"		"100"
EndSection

Section "Device"
	Identifier	"geforce"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"	"true"
	Option		"NvAGP"		"3"
EndSection

Section "Device"
	Identifier	"matrox"
	Driver		"mga"
	BusID		"PCI:0:06:0"
EndSection

Section "Monitor"
	Identifier	"tft"
	HorizSync	30-60
	VertRefresh	56-75
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"crt"
	HorizSync	30-110
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"first"
	Device		"matrox"
	Monitor		"tft"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "second"
	Device "geforce"
	Monitor "crt"
	DefaultColorDepth 24
	SubSection "Display"
	  Depth 24
	  Modes "1280x980"   
	  ViewPort 0 0
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"first"
	Screen		"second" LeftOf "first"
	#Option		"Xinerama" "On"	
	Option		"Twinview" "On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

hth

woifi

---

### Post by tjz on 2005-01-22
I'm totally desperate. I know that dualhead works for my  matrox g400 DH, because a friend of mine could set it up under debian and kde. But kow I installed ubuntu and wanna use it. I messed around with the config file but nothing worked 

Any help to get two screen mode running is highly appreciated.

This is my config:

# XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

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
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
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
	Option		"XkbLayout"	"de"
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
	Identifier	"G400_1"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	#Screen		0
EndSection

Section "Device"
	Identifier	"G400_2"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	#Screen		1
EndSection

Section "Monitor"
	Identifier	"NOKIA 446PRO"
	HorizSync	30-107
	VertRefresh	50-150
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Dell"
	HorizSync	30-110
	VertRefresh	50-160
	Option 		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen 0"
	Device		"G400_1"
	Monitor		"NOKIA 446PRO"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen 1"
	Device		"G400_2"
	Monitor		"Dell"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen 0"
	Screen "Screen 1" LeftOf "Screen 0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	Option 		"Xinerama" "On"
	Option		"Twinview" "On"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by JackDog on 2005-01-23
Twinview is nvidia specific... You just need to use xinerama

---

### Post by tjz on 2005-01-24
I made it - hurray!

it works with twinview - I just had to uncomment the lines in the device section specifiying the screen.

I would love to have it working with xinerama, but since the two monitors have differnert resolutions I have to stick with twinview I think...

But I will try anyway

---

### Post by CompShrink on 2005-03-03
[QUOTE=tjz]I made it - hurray!

it works with twinview - I just had to uncomment the lines in the device section specifiying the screen.

I would love to have it working with xinerama, but since the two monitors have differnert resolutions I have to stick with twinview I think...

But I will try anyway[/QUOTE]
You can use Xinerama with two or more different resolution monitors, I have been for quite some time.

What confuses me is that my new second monitor (old one fried :sad: ) is running at 1400 resolution, when i have it set in my xf86config-4 file to only have the option of 1600. I know the monitor can go 1600, when I plug it inot my laptop it works at 1600, with a refresh rate higher than the one in my xf86config-4... 

I'm not on my own computer now, I'll post my conf file when i get back to my own computer.

---

### Post by CompShrink on 2005-03-03
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
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
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
	Option		"XkbModel"	"pc104"
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
	Identifier	"NVIDIA GeForce4 MX 420"
	Driver		"nv"
	Screen		0
	BusID		"PCI:0:6:0"
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce2 MX 400"
	Driver		"nv"
	Screen		0
	BusID		"1:5:0"
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	HorizSync	31-93
	VertRefresh	50-75
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor[1]"
	HorizSync	31-65
	VertRefresh	50-70
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"NVIDIA GeForce2 MX 400"
	Monitor		"Monitor[1]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce4 MX 420"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Option		"Xinerama" "on"
	Option		"Clone" "off"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Screen 	"Second Screen" RightOf "Default Screen"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by MajorNewby on 2005-04-16
Before I even start trying, I wanted to ask if it's even possible with my setup.  On my WinXP install (sorry, I had to let you know it already works  :neutral: ), I have an AGP slot for my primary monitor running an NVIDIA FX5500 w/ 256MB plus I have a PCI slot for my second monitor running an ATI Rage 128...  I've actually been running this for about 2 years (running dual-head gave me an FPS hit while gaming).  Anyway, seeing my setup with 2 monitors, 2 video cards of different makes, is it still possible to have a dual monitor setup the way I have it now??

[edit]
For those in the same situation as me, I did get it to work.  I simply added another screen and device to my xorg.conf with the appropriate setting for my ati card and monitor, then modified the last section in xorg.conf as follows:
```
Section "ServerLayout"
	Identifier	"Simple Layout"
	Screen		"Default Screen"
	Screen		"Screen 2" Rightof "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```
Anything I open of the secondary monitor opens and stays there - and my games still open on my primary monitor without stretching across both monitors are mirroring on the second monitor.  Good stuff...

---

### Post by tibetanpunk on 2007-05-04
I just got dual monitors set up today on Ubuntu fiesty amd64 using my Geforce FX 5700le...I installed the latest nvidia drivers, opened a terminal window typed:

**gksudo nvidia-settings** 

This opened up the nvidia control panel.
From there I was able to activate and configure my graphics card for dual monitors ('twinview' with second monitor set to 'right of', then hit apply) which was a fairly simple procedure to execute. 
The only problem I have is that all the programs open up between the 2 monitors which can be quite annoying, especially the shut down dialogue box as some of the options are missing and the windows can't be moved, I did read there was a patch for this, but so far I have only found it for the 32bit version of Ubuntu.
This set up will work with Beryl also as long as you can locate and enable the 'twinview' mode in Beryl, under 'desktop' options tab I think it was. You can set it up as one huge cube or two separate cubes, though I think that the two separate cubes are forced to rotate at the same time...You move one, they both move. Two individually moving cubes would be pretty funky.

Anyone know if there is a way to get applications to open in one window rather than across both in feisty amd64? Or how to stop them from opening halfway across both windows? That would be cool
Cheers.

---

