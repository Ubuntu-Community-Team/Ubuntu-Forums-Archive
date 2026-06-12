---
title: "Xubuntu 7.04 + Multiseat xorg.conf"
date: 2008-02-20
forum: General Help
---

### Post by bumcheekcity on 2008-02-20
[http://netpatia.blogspot.com/2006/09/multiseat-iii-xorgconf.html](http://netpatia.blogspot.com/2006/09/multiseat-iii-xorgconf.html)

My xorg.conf follows at the end of this post. I'm trying to set up a  multiseat computer as per the website above, and I've created my xorg.conf following the same rules as his. I've got two graphics cards, an ATI 9550 and a PCI one that identifies itself as a Trident something, but The Trident one didn't seem to work, so I went to using both Monitors on the ATI one, which didn't work either. Then I changed it back to the Trident one, and it's still not working (I just changed the names under the "Devices" section).

My Dell monitor, which was the first recognised, has worked from the start, but the second, a 17" TFT monitor, hasnt worked on the multiseat configuration though. The screen itself DOES work, and the card DOES work (both outputs) although I dont actually know about the Trident one, but it worked when I last used it. 

I can't see where I've gone wrong. When I load this up, the Dell Screen loads up, and I log on. I can use either Keyboard or Mouse, they both work on the one monitor. The other screen though, stays black. Can anyone give me any further advice on how to work this?

```

#####################################
THIS IS NOT MY CURRENT XORG.CONF FILE
SEE BELOW FOR THE CURRENT ONE
#####################################

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
#	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

# ------------------------------------------------------------------------
# Input devices
# ------------------------------------------------------------------------

Section "InputDevice"
  Identifier  "Keyboard-base"
  Driver      "kbd"
EndSection

Section "InputDevice"
  Identifier  "Mouse-base"
  Driver      "mouse"
  Option      "Device" "/dev/input/mice"
EndSection

# ------------------------------------------------------------------------
# PCI devices
# ------------------------------------------------------------------------

Section "Device"
	Identifier	"Card0" #ATI
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection


Section "Device"
	Identifier	"Card2" #ATI
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Device"
	Identifier	"Card1" #TridentSection "DRI"
	Driver		"trident"
EndSection

# ------------------------------------------------------------------------
# Monitor section: Most of the parameters are optional
# ------------------------------------------------------------------------

Section "Monitor"
	Identifier	"Monitor0" #Dell
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1" #V7
EndSection

# ------------------------------------------------------------------------
# Screen section: Pairing video cards and monitors
# ------------------------------------------------------------------------

Section "Screen"
	Identifier	"Screen0"
	Device		"Card0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device 		"Card1"
	Monitor		"Monitor1"
	
	SubSection  "Display"
		Depth  24
		Modes  "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

# ------------------------------------------------------------------------
# Layout section
# ------------------------------------------------------------------------

Section "ServerLayout"
  Identifier   "Multihead"
  Screen 0     "Screen0" 0 0
  Screen 1     "Screen1" LeftOf "Screen0"
  InputDevice  "Keyboard-base" "CoreKeyboard"
  InputDevice  "Mouse-base" "CorePointer"
EndSection

# ------------------------------------------------------------------------
# Additional sections
# ------------------------------------------------------------------------

# Xephyr can not use DRI, so it is not enabled
# Section "DRI"
#   Mode 0666
# EndSection

Section "ServerFlags"
  # Xinerama does not affect this configuration, so it is not enabled
# Option "Xinerama" "on"

  # Even if mouse detection fails, X will start
  Option "AllowMouseOpenFail" "yes"

  # VT switching is disabled
  Option "DontVTSwitch" "yes"

  # X restart (Ctrl+Alt+Backspace) is disabled
  Option "DontZap" "yes"
EndSection

```

---

### Post by bumcheekcity on 2008-02-20
Still having problems with this. The monitor is definately (on the second output on the ATI card) working during BIOS. But it wouldn't work on the PCI card anyway, because it's disabled during BIOS. I still cant get the multiseat to work on either card though.

---

### Post by bumcheekcity on 2008-02-20
Update: I changed my BIOS to display through AGP, then PCI (as opposed to AGP, then onboard VGA), and it seems to have helped. With this new xorg.conf, I get the same on my monitor connected to the ATI card, and the monitor connected to the Trident Card STILL gicves me a black screen, but the light on the mnitor is Green, not Orange. It gives me this confusing black-butt-on screen at 720x400@70Hz. I'm wondering if that's any help.

```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
#	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

# ------------------------------------------------------------------------
# Input devices
# ------------------------------------------------------------------------

Section "InputDevice"
  Identifier  "Keyboard-base"
  Driver      "kbd"
EndSection

Section "InputDevice"
  Identifier  "Mouse-base"
  Driver      "mouse"
  Option      "Device" "/dev/input/mice"
EndSection

# ------------------------------------------------------------------------
# PCI devices
# ------------------------------------------------------------------------

Section "Device"
	Identifier	"Card0" #ATI
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection


Section "Device"
	Identifier	"Card2" #ATI
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Device"
	Identifier	"Card1" #TridentSection "DRI"
	Driver		"trident"
	BusID		"PCI:2:4:0"
EndSection

# ------------------------------------------------------------------------
# Monitor section: Most of the parameters are optional
# ------------------------------------------------------------------------

Section "Monitor"
	Identifier	"Monitor0" #Dell
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1" #V7
	Option		"DPMS"
	VertRefresh	60.0
	HorizSync	31.5 - 90.0
EndSection

# ------------------------------------------------------------------------
# Screen section: Pairing video cards and monitors
# ------------------------------------------------------------------------

Section "Screen"
	Identifier	"Screen0"
	Device		"Card0"
	Monitor		"Monitor0"
	DefaultDepth	24
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
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device 		"Card1"
	Monitor		"Monitor1"
	
	SubSection  "Display"
		Depth  16
		Modes  "1280x1024"
	EndSubSection
EndSection

# ------------------------------------------------------------------------
# Layout section
# ------------------------------------------------------------------------

Section "ServerLayout"
  Identifier   "Multihead"
  Screen 0     "Screen0" 0 0
  Screen 1     "Screen1" LeftOf "Screen0"
  InputDevice  "Keyboard-base" "CoreKeyboard"
  InputDevice  "Mouse-base" "CorePointer"
EndSection

# ------------------------------------------------------------------------
# Additional sections
# ------------------------------------------------------------------------

# Xephyr can not use DRI, so it is not enabled
# Section "DRI"
	#   Mode 0666
# EndSection

Section "ServerFlags"
	# Xinerama does not affect this configuration, so it is not enabled
	# Option "Xinerama" "on"
	
	# Even if mouse detection fails, X will start
	Option "AllowMouseOpenFail" "yes"
	
	# VT switching is disabled
	Option "DontVTSwitch" "yes"
	
	# X restart (Ctrl+Alt+Backspace) is disabled
	Option "DontZap" "yes"
EndSection

```

---

### Post by bumcheekcity on 2008-02-20
Still desparately looking for help from anyone with experience of multiseat computing, or even just with more experience in Linux than me. Final bump before sleep.

---

### Post by tinsami1 on 2008-02-20
Open a terminal window.  Then from the command line issue the command: lspci

Then copy-and-paste the output here.

Also, see [https://wiki.ubuntu.com/MultiseatX](https://wiki.ubuntu.com/MultiseatX)

---

### Post by bumcheekcity on 2008-02-21
lspci:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
02:04.0 VGA compatible controller: Trident Microsystems TGUI 9440 (rev e3)
02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

---

### Post by tinsami1 on 2008-02-21
Add

```
BusID "PCI:2:04:0"
```

to your Trident's Device Section.

---

### Post by tinsami1 on 2008-02-21
> **bumcheekcity said:**
> Update: I changed my BIOS to display through AGP, then PCI (as opposed to AGP, then onboard VGA), and it seems to have helped. With this new xorg.conf, I get the same on my monitor connected to the ATI card, and the monitor connected to the Trident Card STILL gicves me a black screen, but the light on the mnitor is Green, not Orange. It gives me this confusing black-butt-on screen at 720x400@70Hz. I'm wondering if that's any help.

Oops...  I didn't notice your last post already had the BusID keyword.  My bad.

It could be that the monitor cannot handle the resolution your Trident is setting it to.

Have you tried it with just the Trident video card?  Do a: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It will backup your existing xorg.conf and create a new one.  Look at xorg.conf and see if it detected and used the Trident card and the correct Monitor settings.  Then test this by restarting your X server.  If it works, restore your previous xorg.conf, but copy the Device and Monitor sections from the working xorg.conf.

---

### Post by tinsami1 on 2008-02-21
If it still doesn't work, reply with /var/log/Xorg.0.log attached.

---

### Post by bumcheekcity on 2008-02-21
I went to this website

[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

and it told me to go to this one to do "Xephyr's Solution"

[http://en.wikibooks.org/wiki/Multiterminal_with_Xephyr](http://en.wikibooks.org/wiki/Multiterminal_with_Xephyr)

as I didn't have nVidia hardware. And now, it's loaded linux, and told me to press a button on the Keyboard associated with the Dell monitor, and then the Mouse. (Admittedly, it told me that in Spanish, but I got the gist). Then, when I did, the screen went black for 45secs, and it started into X. JUST the dell monitor. Through all of it, the flatpanel still did nothing. 

Well, not nothing, the flatpanel ACTUALLY has a small grey line, you know like you get on DOS prompts, in the top-right corner. It's just flashing on and off. Both keyboard and mice work on the Dell monitor ATM. I'll do the reconfiguring as you suggested above now.

EDIT: I did the reconfiguration like you suggested, and it did NOT detect the trident card at all, even though it works (confirmed now, at least in BIOS, it gives correct output), and it's recognised in the lspci command still. The xorg.conf file it generates is as such, and the requested log file is included below it:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL P1130"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"DELL P1130"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux rpc-ac3442 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 21 09:07:23 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Multihead"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Card1"
(**) |-->Input Device "Keyboard-base"
(==) |-->Input Device "Mouse-base"
(==) |-->Input Device "Keyboard-base"
(WW) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(WW) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "DontVTSwitch" "yes"
(**) Option "DontZap" "yes"
(**) Option "AllowMouseOpenFail" "yes"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 8086,24d0 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 8086,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 8086,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 8086,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 8086,24d0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 8086,24d0 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 8086,24d1 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 8086,24d0 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1919,1001 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4153 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4173 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:04:0: chip 1023,9440 card 0000,0000 rev e3 class 03,00,00 hdr 00
(II) PCI: 02:09:0: chip 10ec,8169 card 10ec,8169 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 1106,3044 card 1106,3044 rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe500000 - 0xfe5fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd7f00000 - 0xf7efffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe600000 - 0xfeafffff (0x500000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x40000000 - 0x400fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AS [Radeon 9550] rev 0, Mem @ 0xe8000000/27, 0xfe5f0000/16, I/O @ 0xa800/8, BIOS @ 0xfe5c0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary) rev 0, Mem @ 0xe0000000/27, 0xfe5e0000/16
(--) PCI: (2:4:0) Trident Microsystems TGUI 9440 rev 227, Mem @ 0xfe800000/21, 0xfeaf0000/16, BIOS @ 0xfeae0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[1] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[10] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[31] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[1] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[2] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[1] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[10] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[31] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[1] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[2] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[5] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[14] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[17] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[18] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[40] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) ATI: ATI driver (version 6.6.3) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
	ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
	ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
	ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
	ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
	ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
	ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
	ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
	ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
	ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
	ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) TRIDENT: driver for Trident chipsets: tvga9000, tvga9000i, tvga8900c,
	tvga8900d, tvga9200cxr, tgui9400cxi, cyber9320, cyber9388, cyber9397,
	cyber9397dvd, cyber9520, cyber9525dvd, cyberblade/e4, tgui9420dgi,
	tgui9440agi, tgui9660, tgui9680, providia9682, providia9685,
	cyber9382, cyber9385, 3dimage975, 3dimage985, blade3d, cyberbladei7,
	cyberbladei7d, cyberbladei1, cyberbladei1d, cyberbladeAi1,
	cyberbladeAi1d, bladeXP, cyberbladeXPAi1, cyberbladeXP4, XP5
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "Card0".
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9600 AS (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[5] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[14] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[17] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[18] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[40] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(--) Chipset tgui9440agi found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[5] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[14] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[17] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[18] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[40] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[5] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[14] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[17] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[18] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[31] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[32] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[34] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[35] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[36] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[37] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[41] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[42] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[43] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[44] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[45] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[46] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
	[47] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[48] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[49] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[50] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xfe5f0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) RADEON(0): Assuming overlay scaler buffer width is 1536
(==) RADEON(0): X server will not keep DPI constant for all screen sizes
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(WW) RADEON(0): Bad V_BIOS checksum
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9600 AS (AGP)" (ChipID = 0x4153)
(--) RADEON(0): Linear framebuffer at 0xe8000000
(--) RADEON(0): BIOS at 0xfe5c0000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): VBE DDC probing on port 1 ::: 
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(WW) RADEON(0): Bad V_BIOS checksum
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): VESA BIOS detected
(II) RADEON(0): VESA VBE Version 2.0
(II) RADEON(0): VESA VBE Total Mem: 16384 kB
(II) RADEON(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) RADEON(0): VESA VBE OEM Software Rev: 1.0
(II) RADEON(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) RADEON(0): VESA VBE OEM Product: V350
(II) RADEON(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) RADEON(0): VESA VBE DDC supported
(II) RADEON(0): VESA VBE DDC Level 2
(II) RADEON(0): VESA VBE DDC transfer in appr. 2 sec.
(II) RADEON(0): VESA VBE DDC read successfully
(II) RADEON(0): DDC info nullified on port 1 :::
(II) RADEON(0): Analog device indicated in DDC but port 2 CRT physically connected
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 5000  Serial#: 825242182
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 85  vid: 22897
(II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #5: hsize: 1800  vsize 1440  refresh: 75  vid: 36802
(II) RADEON(0): #6: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  364 x 291 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 48  V max: 170 Hz, H min: 30  H max: 130 kHz, PixClock max 290 MHz
(II) RADEON(0): Monitor name: DELL P1130
(II) RADEON(0): Serial No: 6D252221102F
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac005046323031
(II) RADEON(0): 	050c01030e281e962b0cc9a057479b27
(II) RADEON(0): 	12484ca44380a959a94f615971594559
(II) RADEON(0): 	c28f31590101863d00c05100304040a0
(II) RADEON(0): 	13006c231100001e000000fd0030aa1e
(II) RADEON(0): 	821d000a202020202020000000fc0044
(II) RADEON(0): 	454c4c2050313133300a2020000000ff
(II) RADEON(0): 	003644323532323231313032460a00a3
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=25000
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Monitor0: Using hsync range of 30.00-130.00 kHz
(II) RADEON(0): Monitor0: Using vrefresh range of 48.00-170.00 Hz
(II) RADEON(0): Clock range:  20.00 to 400.00 MHz
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(--) RADEON(0): Virtual size is 1280x1024 (pitch 1280)
(**) RADEON(0): *Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
(**) RADEON(0): *Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) RADEON(0): Modeline "1152x864"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
(**) RADEON(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) RADEON(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) RADEON(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) RADEON(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) RADEON(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) RADEON(0):  Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1280x960"  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync
(**) RADEON(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) RADEON(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) RADEON(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) RADEON(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) RADEON(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) RADEON(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) RADEON(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) RADEON(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) RADEON(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) RADEON(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) RADEON(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RADEON(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) RADEON(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) RADEON(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) RADEON(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) RADEON(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) RADEON(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) RADEON(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) RADEON(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) RADEON(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RADEON(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(--) RADEON(0): Display dimensions: (400, 300) mm
(--) RADEON(0): DPI set to (81, 86)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(II) TRIDENT(1): Creating default Display subsection in Screen section
	"Screen1" for depth/fbbpp 24/32
(==) TRIDENT(1): Depth 24, (==) framebuffer bpp 32
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(II) TRIDENT(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Reloading /usr/lib/xorg/modules//libramdac.so
(==) TRIDENT(1): RGB weight 888
(==) TRIDENT(1): Default visual is TrueColor
(==) TRIDENT(1): Using gamma correction (1.0, 1.0, 1.0)
(==) TRIDENT(1): Using XAA for acceleration
(==) TRIDENT(1): Linear framebuffer at 0xFE800000
(--) TRIDENT(1): IO registers at 0xFEAF0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) TRIDENT(1): initializing int10
(II) Attempted to read BIOS 64KB from /sys/bus/pci/devices/0000:02:04.0/rom: got 32KB
(II) TRIDENT(1): VESA BIOS detected
(II) TRIDENT(1): VESA VBE Version 1.2
(II) TRIDENT(1): VESA VBE Total Mem: 1024 kB
(II) TRIDENT(1): VESA VBE OEM: TRIDENT MICROSYSTEMS INC.
(--) TRIDENT(1): Revision is 1
(--) TRIDENT(1): Found TGUI9440AGi chip
(--) TRIDENT(1): RAM type is Standard DRAM
(--) TRIDENT(1): Using SW cursor
(--) TRIDENT(1): VideoRAM: 1024 kByte
(--) TRIDENT(1): Memory Clock is 56.48 MHz
(==) TRIDENT(1): Min pixel clock is 12 MHz
(--) TRIDENT(1): Max pixel clock is 25 MHz
(II) TRIDENT(1): Monitor1: Using hsync range of 31.50-90.00 kHz
(II) TRIDENT(1): Monitor1: Using vrefresh value of 60.00 Hz
(WW) TRIDENT(1): Unable to estimate virtual size
(II) TRIDENT(1): Clock range:  12.00 to  25.18 MHz
(II) TRIDENT(1): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "720x400" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1280x960" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1280x960" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1280x1024" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x512" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1280x1024" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x512" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1280x1024" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x512" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1792x1344" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "896x672" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1792x1344" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "896x672" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1856x1392" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "928x696" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1856x1392" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "928x696" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "960x720" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "960x720" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "832x624" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1280x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1280x800" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1152x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "700x525" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "700x525" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "700x525" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "700x525" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1440x900" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "720x450" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1024" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x512" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1680x1050" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "840x525" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1920x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "960x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1920x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "960x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "960x720" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(WW) TRIDENT(1): Mode pool is empty
(EE) TRIDENT(1): No valid modes found
(II) UnloadModule: "trident"
(II) UnloadModule: "int10"
(II) UnloadModule: "vbe"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "vgahw"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B]
	[1] 1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B]
	[2] 0	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B]
	[3] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[9] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[10] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[11] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[12] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[13] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[14] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[15] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[18] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[19] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[20] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[21] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[22] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[26] 0	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[33] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[34] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[35] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[36] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[37] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[38] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[39] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[41] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[42] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[43] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[44] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[45] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[46] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[47] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[48] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
	[49] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[50] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(**) RADEON(0): RADEONScreenInit e8000000 0
(**) RADEON(0): Map: 0xe8000000, 0x08000000
(==) RADEON(0): Write-combining range (0xe8000000,0x8000000)
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81faf08)
(**) RADEON(0): Read: 0x0030000c 0x00030065 0x00000000
(**) RADEON(0): Read: rd=12, fd=101, pd=3
(**) RADEON(0): RADEONSaveMode returns 0x81faf08
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x08000000
(**) RADEON(0):   MC_FB_LOCATION   : 0xefffe800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1280x1024     157.50  1280 1344 1504 1728  1024 1025 1028 1072 (24,32) +H +V
1280x1024     157.50  1280 1344 1504 1728  1024 1025 1028 1072 (24,32) +H +V
(**) RADEON(0): Pitch = 10485920 bytes (virtualX = 1280, displayWidth = 1280)
(**) RADEON(0): dc=15750, of=31500, fd=140, pd=2
(**) RADEON(0): RADEONInit returns 0x81fb8b8
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fb8b8)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xefffe800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x0001008c 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=12, fd=140, pd=1
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 202b7c7c
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1024) to (1280,1026)
(II) RADEON(0): Largest offscreen area available: 1280 x 7165
(**) RADEON(0): Initializing backing store
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 160
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1026)
(II) RADEON(0): Largest offscreen area available: 1280 x 7161
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: DRI module not loaded
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "Protocol" "standard"
(**) Keyboard-base: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard-base: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard-base: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard-base: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard-base: CustomKeycodes disabled
(**) Mouse-base: Device: "/dev/input/mice"
(==) Mouse-base: Protocol: "Auto"
(**) Option "CorePointer"
(**) Mouse-base: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Mouse-base: Emulate3Buttons, Emulate3Timeout: 50
(**) Mouse-base: ZAxisMapping: buttons 4 and 5
(**) Mouse-base: Buttons: 9
(**) Option "CoreKeyboard"
(**) Keyboard-base: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard-base: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard-base: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard-base: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard-base: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard-base: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Keyboard-base" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Mouse-base" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard-base" (type: KEYBOARD)
(--) Mouse-base: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse-base: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): RADEONSaveScreen(2)
(II) 3rd Button detected: disabling emulate3Button

```

---

### Post by bumcheekcity on 2008-02-21
Epic bump?

---

### Post by tinsami1 on 2008-02-22
Here's your problem:

```
(EE) TRIDENT(1): No valid modes found
```


Try swapping the monitors physically and in the Screen sections.  If that still doesn't work, post /var/log/Xorg.0.log again.

---

### Post by bumcheekcity on 2008-02-22
Swapping the monitors physically gets me the LCD (now on the ATI card) working fine, with both keyboards and mice, and the CRT, on the Trident card, giving me a grey, otherwise blank, screen with just the blinking DOS-Style cursor on the top-left.

Then, swapping the monitors in the "Screen" section, just changing every instance of Identifier, Device, Monitor to the different number each time, gives me no change at all on the above situation, the LCD working, the CRT giving me the blank screen. Log file included.

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux rpc-ac3442 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 22 08:45:48 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Multihead"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Card1"
(**) |-->Input Device "Keyboard-base"
(==) |-->Input Device "Mouse-base"
(==) |-->Input Device "Keyboard-base"
(WW) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(WW) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "DontVTSwitch" "yes"
(**) Option "DontZap" "yes"
(**) Option "AllowMouseOpenFail" "yes"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 8086,24d0 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 8086,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 8086,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 8086,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 8086,24d0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 8086,24d0 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 8086,24d1 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 8086,24d0 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1919,1001 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4153 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4173 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:04:0: chip 1023,9440 card 0000,0000 rev e3 class 03,00,00 hdr 00
(II) PCI: 02:09:0: chip 10ec,8169 card 10ec,8169 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 1106,3044 card 1106,3044 rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe500000 - 0xfe5fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd7f00000 - 0xf7efffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe600000 - 0xfeafffff (0x500000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x40000000 - 0x400fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AS [Radeon 9550] rev 0, Mem @ 0xe8000000/27, 0xfe5f0000/16, I/O @ 0xa800/8, BIOS @ 0xfe5c0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary) rev 0, Mem @ 0xe0000000/27, 0xfe5e0000/16
(--) PCI: (2:4:0) Trident Microsystems TGUI 9440 rev 227, Mem @ 0xfe800000/21, 0xfeaf0000/16, BIOS @ 0xfeae0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[1] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[10] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[31] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[1] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[2] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[1] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[10] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[31] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[1] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[2] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[5] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[14] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[17] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[18] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[40] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) ATI: ATI driver (version 6.6.3) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
	ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
	ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
	ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
	ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
	ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
	ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
	ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
	ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
	ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
	ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) TRIDENT: driver for Trident chipsets: tvga9000, tvga9000i, tvga8900c,
	tvga8900d, tvga9200cxr, tgui9400cxi, cyber9320, cyber9388, cyber9397,
	cyber9397dvd, cyber9520, cyber9525dvd, cyberblade/e4, tgui9420dgi,
	tgui9440agi, tgui9660, tgui9680, providia9682, providia9685,
	cyber9382, cyber9385, 3dimage975, 3dimage985, blade3d, cyberbladei7,
	cyberbladei7d, cyberbladei1, cyberbladei1d, cyberbladeAi1,
	cyberbladeAi1d, bladeXP, cyberbladeXPAi1, cyberbladeXP4, XP5
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "Card0".
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9600 AS (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[5] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[14] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[17] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[18] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[40] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(--) Chipset tgui9440agi found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[5] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[14] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[17] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[18] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[40] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[5] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[14] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[17] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[18] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[31] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[32] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[34] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[35] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[36] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[37] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[41] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[42] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[43] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[44] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[45] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[46] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
	[47] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[48] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[49] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[50] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xfe5f0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) RADEON(0): Assuming overlay scaler buffer width is 1536
(==) RADEON(0): X server will not keep DPI constant for all screen sizes
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(WW) RADEON(0): Bad V_BIOS checksum
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9600 AS (AGP)" (ChipID = 0x4153)
(--) RADEON(0): Linear framebuffer at 0xe8000000
(--) RADEON(0): BIOS at 0xfe5c0000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): VBE DDC probing on port 1 ::: 
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(WW) RADEON(0): Bad V_BIOS checksum
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): VESA BIOS detected
(II) RADEON(0): VESA VBE Version 2.0
(II) RADEON(0): VESA VBE Total Mem: 16384 kB
(II) RADEON(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) RADEON(0): VESA VBE OEM Software Rev: 1.0
(II) RADEON(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) RADEON(0): VESA VBE OEM Product: V350
(II) RADEON(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) RADEON(0): VESA VBE DDC supported
(II) RADEON(0): VESA VBE DDC Level 2
(II) RADEON(0): VESA VBE DDC transfer in appr. 2 sec.
(II) RADEON(0): VESA VBE DDC read failed
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): VBE DDC probing on port 2 ::: 
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(WW) RADEON(0): Bad V_BIOS checksum
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): VESA BIOS detected
(II) RADEON(0): VESA VBE Version 2.0
(II) RADEON(0): VESA VBE Total Mem: 16384 kB
(II) RADEON(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) RADEON(0): VESA VBE OEM Software Rev: 1.0
(II) RADEON(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) RADEON(0): VESA VBE OEM Product: V350
(II) RADEON(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) RADEON(0): VESA VBE DDC supported
(II) RADEON(0): VESA VBE DDC Level 2
(II) RADEON(0): VESA VBE DDC transfer in appr. 2 sec.
(II) RADEON(0): VESA VBE DDC read failed
(II) RADEON(0): DDC Type: 3, Detected Type: 0
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=25000
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Monitor0: Using default hsync range of 31.50-37.90 kHz
(II) RADEON(0): Monitor0: Using default vrefresh range of 50.00-70.00 Hz
(WW) RADEON(0): Unable to estimate virtual size
(II) RADEON(0): Clock range:  20.00 to 400.00 MHz
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (hsync out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "832x624" (hsync out of range)
(II) RADEON(0): Not using default mode "416x312" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x768" (hsync out of range)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (hsync out of range)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (hsync out of range)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) RADEON(0): Virtual size is 800x600 (pitch 832)
(**) RADEON(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RADEON(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RADEON(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RADEON(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(==) RADEON(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(**) TRIDENT(1): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(II) TRIDENT(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Reloading /usr/lib/xorg/modules//libramdac.so
(==) TRIDENT(1): RGB weight 888
(==) TRIDENT(1): Default visual is TrueColor
(==) TRIDENT(1): Using gamma correction (1.0, 1.0, 1.0)
(==) TRIDENT(1): Using XAA for acceleration
(==) TRIDENT(1): Linear framebuffer at 0xFE800000
(--) TRIDENT(1): IO registers at 0xFEAF0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) TRIDENT(1): initializing int10
(II) Attempted to read BIOS 64KB from /sys/bus/pci/devices/0000:02:04.0/rom: got 32KB
(II) TRIDENT(1): VESA BIOS detected
(II) TRIDENT(1): VESA VBE Version 1.2
(II) TRIDENT(1): VESA VBE Total Mem: 1024 kB
(II) TRIDENT(1): VESA VBE OEM: TRIDENT MICROSYSTEMS INC.
(--) TRIDENT(1): Revision is 1
(--) TRIDENT(1): Found TGUI9440AGi chip
(--) TRIDENT(1): RAM type is Standard DRAM
(--) TRIDENT(1): Using SW cursor
(--) TRIDENT(1): VideoRAM: 1024 kByte
(--) TRIDENT(1): Memory Clock is 56.48 MHz
(==) TRIDENT(1): Min pixel clock is 12 MHz
(--) TRIDENT(1): Max pixel clock is 25 MHz
(II) TRIDENT(1): Monitor1: Using hsync range of 31.50-90.00 kHz
(II) TRIDENT(1): Monitor1: Using vrefresh value of 60.00 Hz
(II) TRIDENT(1): Clock range:  12.00 to  25.18 MHz
(II) TRIDENT(1): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "720x400" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1280x960" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1280x960" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x480" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1280x1024" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x512" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1280x1024" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x512" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1280x1024" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x512" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1792x1344" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "896x672" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1792x1344" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "896x672" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1856x1392" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "928x696" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1856x1392" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "928x696" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "960x720" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "960x720" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "832x624" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1280x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1280x800" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1152x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) TRIDENT(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "700x525" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "700x525" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "700x525" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "700x525" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1440x900" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "720x450" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1600x1024" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "800x512" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1680x1050" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "840x525" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1920x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "960x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1920x1200" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "960x600" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "960x720" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) TRIDENT(1): Not using default mode "1024x768" (insufficient memory for mode)
(WW) TRIDENT(1): Mode pool is empty
(EE) TRIDENT(1): No valid modes found
(II) UnloadModule: "trident"
(II) UnloadModule: "int10"
(II) UnloadModule: "vbe"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "vgahw"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B]
	[1] 1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B]
	[2] 0	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B]
	[3] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xfeadf000 - 0xfeadf7ff (0x800) MX[B]
	[9] -1	0	0xfeadfc00 - 0xfeadfcff (0x100) MX[B]
	[10] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[11] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[12] -1	0	0x40100000 - 0x401003ff (0x400) MX[B]
	[13] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[14] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[15] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0xfe5c0000 - 0xfe5dffff (0x20000) MX[B](B)
	[18] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[19] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[20] -1	0	0x40020000 - 0x4002ffff (0x10000) MX[B](B)
	[21] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[22] -1	0	0xfe800000 - 0xfe9fffff (0x200000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[26] 0	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[33] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[34] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[35] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[36] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[37] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[38] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[39] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[41] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[42] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[43] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[44] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[45] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[46] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[47] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[48] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
	[49] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[50] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(**) RADEON(0): RADEONScreenInit e8000000 0
(**) RADEON(0): Map: 0xe8000000, 0x08000000
(==) RADEON(0): Write-combining range (0xe8000000,0x8000000)
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81faf08)
(**) RADEON(0): Read: 0x0030000c 0x00030065 0x00000000
(**) RADEON(0): Read: rd=12, fd=101, pd=3
(**) RADEON(0): RADEONSaveMode returns 0x81faf08
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x08000000
(**) RADEON(0):   MC_FB_LOCATION   : 0xefffe800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
800x600        40.00   800  840  968 1056   600  601  605  628 (24,32) +H +V
800x600        40.00   800  840  968 1056   600  601  605  628 (24,32) +H +V
(**) RADEON(0): Pitch = 6815848 bytes (virtualX = 800, displayWidth = 832)
(**) RADEON(0): dc=4000, of=32000, fd=142, pd=8
(**) RADEON(0): RADEONInit returns 0x81fb8b8
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fb8b8)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xefffe800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x0003008e 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=12, fd=142, pd=3
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 200b7c7c
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): Memory manager initialized to (0,0) (832,8191)
(II) RADEON(0): Reserved area from (0,600) to (832,610)
(II) RADEON(0): Largest offscreen area available: 832 x 7581
(**) RADEON(0): Initializing backing store
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 104
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		28 256x256 slots
		13 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 610)
(II) RADEON(0): Largest offscreen area available: 832 x 7576
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: DRI module not loaded
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "Protocol" "standard"
(**) Keyboard-base: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard-base: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard-base: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard-base: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard-base: CustomKeycodes disabled
(**) Mouse-base: Device: "/dev/input/mice"
(==) Mouse-base: Protocol: "Auto"
(**) Option "CorePointer"
(**) Mouse-base: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Mouse-base: Emulate3Buttons, Emulate3Timeout: 50
(**) Mouse-base: ZAxisMapping: buttons 4 and 5
(**) Mouse-base: Buttons: 9
(**) Option "CoreKeyboard"
(**) Keyboard-base: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard-base: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard-base: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard-base: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard-base: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard-base: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Keyboard-base" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Mouse-base" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard-base" (type: KEYBOARD)
(--) Mouse-base: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse-base: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): RADEONSaveScreen(2)
(II) 3rd Button detected: disabling emulate3Button

```

---

### Post by bumcheekcity on 2008-02-22
Again, I just want to iterate that the screen that doesnt work (now, the CRT, plugged into the Trident), actually has a green power light, and is thinking it's on, it's just not displaying anything useful save for the faux-bios prompt.

---

### Post by tinsami1 on 2008-02-22
```
(II) TRIDENT(1): VESA BIOS detected
(II) TRIDENT(1): VESA VBE Version 1.2
(II) TRIDENT(1): VESA VBE Total Mem: 1024 kB
(II) TRIDENT(1): VESA VBE OEM: TRIDENT MICROSYSTEMS INC.
(--) TRIDENT(1): Revision is 1
(--) TRIDENT(1): Found TGUI9440AGi chip
(--) TRIDENT(1): RAM type is Standard DRAM
(--) TRIDENT(1): Using SW cursor
(--) TRIDENT(1): VideoRAM: 1024 kByte
```

Your Trident Card only has 1MB of memory as detected.  Is this correct?  If not, then you have to put VideoRAM <correct video memory size> in the Device section of your Trident card.  If the 1MB is correct, you can only get a low resolution settings.

But anyway, I noticed that you ATI radeon is seen as two PCI cards PCI:1:0:0 and PCI:1:0:1.   You can configure X to use these two instead.

---

### Post by bumcheekcity on 2008-02-22
I'll be brutally honest, I don't know how much memory the Trident card has. It's just a PCI card that I know works. I'll try putting the things through the ATI card on BusIDs 1:0:0 and 1:0:0 and see if that works.

Edit: Haha! Well, it kind of works. I get a total replication of my screen on both screens (now both running out of the ATI card). Both keyboards, both mice work. Now, I just need them to be SEPARATE...

---

### Post by tinsami1 on 2008-02-22
> **bumcheekcity said:**
> I'll be brutally honest, I don't know how much memory the Trident card has. It's just a PCI card that I know works. I'll try putting the things through the ATI card on BusIDs 1:0:0 and 1:0:0 and see if that works.

Edit: Haha! Well, it kind of works. I get a total replication of my screen on both screens (now both running out of the ATI card). Both keyboards, both mice work. Now, I just need them to be SEPARATE...

Use PCI:1:0:[COLOR="Red"]**0**[/COLOR] and PCI:1:0:[COLOR="Red"]**1**[/COLOR].

You may also need to add Option "Clone" "Off" in the Device Section for both.

Like this:

```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550] **[COLOR="Red"]LCD[/COLOR]**"
	Driver		"ati"
	BusID		"PCI:1:0:[COLOR="Red"]**0**[/COLOR]"
	Option		"Clone"		"Off"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550] [COLOR="Red"]**VGA**[/COLOR]"
	Driver		"ati"
	BusID		"PCI:1:0:[COLOR="Red"]**1**[/COLOR]"
	Option		"Clone"		"Off"
	Screen		1
EndSection
```


PS.  As for the Trident card -- the best you can do with it is 640x480 at Depth 24 or 800x600 at Depth 16.   It might still be usable as a full screen video player while you work off the ATI card.

---

### Post by bumcheekcity on 2008-02-23
Nope, still no luck, working both off the ATI card. I've added what you recommended, and completed EXACTLY the rest of the steps in the walkthrough in the first post I made, and nothing works, they're still just cloning output. :(

---

### Post by tinsami1 on 2008-02-28
Try adding the ff. to both Device sections:
```
Option "MonitorLayout" "TMDS,CRT"
Option "MergedFB" "Off"  (also try "On")
Option "VGAAccess" "Off"
```

---

