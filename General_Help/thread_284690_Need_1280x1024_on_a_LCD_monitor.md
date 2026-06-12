---
title: "Need 1280x1024 on a LCD monitor"
date: 2006-10-26
forum: General Help
---

### Post by brianfast on 2006-10-26
Ok, I have been digging through these forums and none of the methods work. The last one I tried made X unable to load and it said my error was on line 222 where I put in 1280x1024.

I have a 17 inch LCD and a Nvidia geforce 6600. I have messed around in gedit (nano doesnt show any text???)

Am I missing drivers or something? How come is it so hard to do this on linux when on windows I can just select whatever resolution I want. I previously used Morphix but when I got a new monitor the resolution became unbearable so I had to go back to windows. PLEASE TELL ME UBUNTU is different.

---

### Post by lazyart on 2006-10-26
sudo gedit /etc/X11/xorg.conf

replace your Subsection "Display" with this:

	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

and save it.  hit control-alt-backspace to restart X.

---

### Post by CatKiller on 2006-10-26
> **brianfast said:**
> (nano doesnt show any text???)

That will be because you've opened a new file. Be careful with your typing - case is significant.

---

### Post by brianfast on 2006-10-26
That changed nothing...

Come on there must be someone here who knows what they are doing. My eyes are dying.

---

### Post by beerfan on 2006-10-26
> **brianfast said:**
> That changed nothing...

Come on there must be someone here who knows what they are doing. My eyes are dying.

Have you tried the "resolution" manager in preferences? I'm guessing you did and it doesn't include your preferred resolution, which is odd because Ubuntu always defaults to 1280x1024 for me when I install it. If it isn't there then you're stuck editing the xorg.conf file as instructed above. It sucks but that's the way it is.

---

### Post by bg1256 on 2006-10-26
Post # 2 will solve your problems.

sudo gedit /etc/X11/xorg.conf


> Opens a file; look for this
Depth 24
Modes "1152x864" "1024x768" "800x600" "640x480"
EndSubSection

and add: "1280x1024" after Modes.

ctr+alt+backspace and you're good to go.

Then go into system preferences screen res. and change it.

---

### Post by brianfast on 2006-10-26
It doesn't work. I mentioned that in my last post. I have tryed the screen resolution tool and xorg.conf.

---

### Post by beerfan on 2006-10-26
> **brianfast said:**
> It doesn't work. I mentioned that in my last post. I have tryed the screen resolution tool and xorg.conf.

What is the native resolution of your LCD? It might be wise to stick with that if it isn't 1280x1024.

---

### Post by brianfast on 2006-10-26
1280x1024

---

### Post by brianfast on 2006-10-26
This is my xorg.conf


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
	Load	"i2c"
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
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
Depth 1
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
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

---

### Post by kvonb on 2006-10-26
You need a frequency range, look in your documentation that came with your nice shiny new screen for the scan ranges.

I have a Sony 21inch, so mine are: (from my /etc/X11/xorg.conf)

Section "Monitor"
          Identifier   "aticonfig-Monitor[0]"
          Option	     "VendorName" "ATI Proprietary Driver"
          Option	     "ModelName" "Generic Autodetecting Monitor"
          Option	     "DPMS" "true"
          HorizSync    28.0 - 121.0
          VertRefresh  43.0 - 160.0
          ModeLine     "1600x1200@85" 83.9 1280 1312 1624 1656 800 816 824 841
EndSection

DON'T try using my scan ranges, it might damage your screen, but add the HorizSync and VertRefresh lines with your values filled in.

As for the modeline, I have no idea how to generate it but it seems to make X use the higher frequency ranges.  I can't remember where I got it either :)

Also I suggest changing the line: Driver "vesa" to Driver "nv" to get better graphics.

Actually, search these forums on how to setup nvidia cards, there is a lot of help available.

Regards, Kev :)

Oh yes, and also add the Option	 "DPMS" "true" line.

---

### Post by rhodry on 2006-10-27
> **brianfast said:**
> That changed nothing...

Come on there must be someone here who knows what they are doing. My eyes are dying.

I would suggest it is something you have done or are doing that is causing the problem. I have the same setup as you, i.e. (Samsung) 17in LCD monitor driven by Nvidia geforce 6600.

My Dapper install detected everything ok except I did not get a 60MHz option; so I added the Modeline and extra 1280x1024 entry you see in my xorg.conf extract below.

It works, so you need to calmly persevere.

xorg.conf extract..............

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	Modeline	"1280x1024_60.00"  108.88 1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024_60.00" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024_60.00" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024_60.00" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024_60.00" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024_60.00" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_60.00" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Cheers,
Rhodry

---

### Post by dyrer on 2006-10-29
This is my xorg.conf
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"nVidia 6600"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	131072
	Option "IgnoreEDID" "true"
EndSection

Section "Monitor"
	Identifier "Generic Monitor"
	Option "DPMS"
	Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
	HorizSync 30-75
	VertRefresh 56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia 6600"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
	Depth 1
		Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 4
		Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 8
		Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 15
		Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 16
		Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Depth 24
		Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
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

[B]
I need to make it work on 1280x1025 60Hz[/B]

---

### Post by jimmyk on 2006-10-29
There is a nice walk-through here if you are still having trouble

[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration]("https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration")

---

### Post by Demon012 on 2006-10-29
Try opening a terminal and typing:

> sudo dpkg-reconfigure xserver-xorg

Choose to use the nv or nvidia drivers (the nv is the open source driver but doesn't have great 3d performance). Then when it comes to the resolutions part go through the resolutions and select the ones you want to use via space bar (the ones you want by the sounds of it is 1280x1024, 1024x768, 800x600, 640x480). Then continue on to the monitor setup section and choose medium difficulty and fill in the details of your monitor. 

After that has finished either restart your computer or save anything and everything you are doing and press ctrl + alt + backspace to restart the xserver.

You should then hopefully have 1280x1024 with 24bit colour (same as 32bit) with 60hz refresh rate.

---

### Post by jdunn on 2006-10-29
I see your display is set to "generic monitor".  Maybe you could try a 'modeline' in your xorg.conf.  You'll need some specs from the display's operator/user manual.  Back up your xorg.conf before making the changes.

These two sites calculate the modelines for you.  I haven't actually tried them out.
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
[http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)

*update*  I also see you are using an LCD display.  Are you using a DVI input?  Maybe set your display type to "generic flatpanel".

---

### Post by brianfast on 2006-10-29
No, I am using analog. Does that mean generic flatscreen won't work?

I added a moduleline but it isn't working:

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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Load	"i2c"
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
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
        Modeline "1280x2024@60i" 113.21 1280 1312 1736 1768 2024 2070 2081 2127 interlace
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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

---

### Post by rictus007 on 2006-10-29
Well I have a similar case... LCD monitor 15", video card working OK and after doing all the recomendations of the forums.... I just was not able to get the resolution I want.  I try everything like you...and I just end uninstalling ubuntu on my desktop.. I'm just using it on my laptop.

---

### Post by shashikm on 2006-11-08
Even I have the same problem 
I guess when I installed i was using CRT 15" monitor. Now I have aacer 1717 17" LCD 1280x1024 
even I am not able to choose the reolution. but IF I use ubuntu live CD iget 1280x1024 resolution...
so my conclusion is that I need to X server to dectect my LCD now I do not KNOW HOW TO DO THIS...
searched for some command but in vain....

kindly help

shashi

---

### Post by mistab1034 on 2006-11-08
> **brianfast said:**
> 
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection
EndSection

Have you tried installing nvidia drivers for your card? You can find posts on how to do it if you search.

---

