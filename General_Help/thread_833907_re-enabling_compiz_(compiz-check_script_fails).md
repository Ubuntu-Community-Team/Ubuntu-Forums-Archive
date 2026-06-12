---
title: "re-enabling compiz (compiz-check script fails)"
date: 2008-06-19
forum: General Help
---

### Post by dexter.deepak on 2008-06-19
this is my second post regarding the problem.
i have  blaclisted graphics card : intel965 series...but i manged to play compiz effects (all of them !!) by just trying "SKIP_CHECKS=yes compiz".
but after i remastered my system(through remastersys), i cant play these effects.i then heard about restricted drivers and i tried the "compiz-check" script somewhere in the community.

i tried the script ,and got the following output :

dpak@dpak-server:~$ ./compiz-check

Gathering information about your system...

Distribution: Ubuntu 7.10
Desktop environment: GNOME
Graphics chip: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
Driver in use: vesa
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system... [SKIP]

Checking for hardware/setup problems... [SKIP]

At least one check had to be skipped:
Error: vesa driver in use

Would you like to know more? (Y/n) Y

The vesa driver is not capable of running Compiz, you need to install the
proper driver for your graphics card.

Check if there's an alternate (proprietary) driver available? (Y/n) Y

...and the output of the above is a window saying that i need to install the foolowing:
linux-restricted-modules-2.6.22-14-server

but when i tried to install the above:
dpak@dpak-server:~$ sudo apt-get install linux-restricted-modules-2.6.22-14-server
[sudo] password for dpak:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.22-14-server

what to do ?? please help me this time ...or i am planning to shift from the ubuntu desktop...please !!

---

### Post by dexter.deepak on 2008-06-19
:mad:
F1 !!
F1 !!
:cry:

---

### Post by Forlong on 2008-06-21
Hi,

I just replied to your comment here: [http://ubuntuforums.org/showthread.php?p=5232352#post5232352](http://ubuntuforums.org/showthread.php?p=5232352#post5232352)
But we might as well do it in this thread.

Post your /etc/X11/xorg.conf and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by dexter.deepak on 2008-06-21
thanks a lot for replying !!
here is the o/p :


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
	Identifier	"Intel Corporation 82G965 Integrated Graphics Controller"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
	VideoRam	20000
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82G965 Integrated Graphics Controller"
	Monitor		"SyncMaster"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

---

### Post by dexter.deepak on 2008-06-21
i think that i dont have the right repositories enabled to find the package "linux-restricted-modules-2.6.22-14-server"

but i cant find the right repos anywhere ...maybe thats what i should look for !!

---

### Post by Forlong on 2008-06-21
Try changing this:
```
Section "Device"
	Identifier	"Intel Corporation 82G965 Integrated Graphics Controller"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
	VideoRam	20000
EndSection
```
to
```
Section "Device"
	Identifier	"Intel Corporation 82G965 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	VideoRam	20000
EndSection
```

To do that, you have to open that file being root, e.g.
```
gksu gedit /etc/X11/xorg.conf
```
Afterwards, reboot and try again.

---

### Post by dexter.deepak on 2008-06-21
i did try thrice...but the screen crashed and i was back on the login screen.
this way i was able to run compiz-check a bit further (through failsafe terminal), but i couldnt run compiz.
the o/p of compiz-check this time was :

dpak@dpak-server:~$ sh compiz-check
Gathering information about your system...

 Distribution:          Ubuntu 7.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Forlong on 2008-06-22
Well, you're at least finally using the intel driver.

Post your current **/etc/X11/xorg.conf** as well as your **/var/log/Xorg.0.log** -- and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by dexter.deepak on 2008-06-22
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
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"Intel Corporation 82G965 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82G965 Integrated Graphics Controller"
	Monitor		"SyncMaster"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```


```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.4)
Current Operating System: Linux dpak-server 2.6.22-14-server #1 SMP Tue Feb 12 08:27:05 UTC 2008 i686
Build Date: 13 June 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun 22 16:24:42 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "Intel Corporation 82G965 Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9960
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 8086,514d rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,29a2 card 8086,514d rev 02 class 03,00,00 hdr 00
(II) PCI: 00:03:0: chip 8086,29a4 card 8086,514d rev 02 class 07,80,00 hdr 80
(II) PCI: 00:19:0: chip 8086,104b card 8086,0001 rev 02 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 8086,514d rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 8086,514d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 8086,514d rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 8086,2113 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2841 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2843 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2845 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2847 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 8086,514d rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 8086,514d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 8086,514d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 8086,514d rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2810 card 8086,514d rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2820 card 8086,514d rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 8086,514d rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2825 card 8086,514d rev 02 class 01,01,85 hdr 00
(II) PCI: 02:00:0: chip 11ab,6101 card 11ab,6101 rev b1 class 01,01,8f hdr 00
(II) PCI: 06:03:0: chip 104c,8023 card 8086,514d rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x50400000 - 0x504fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x50100000 - 0x501fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:2), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x50500000 - 0x505fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:3), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x50600000 - 0x506fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:4), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0x50700000 - 0x507fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82G965 Integrated Graphics Controller rev 2, Mem @ 0x50200000/20, 0x40000000/28, I/O @ 0x2440/3
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
(II) Active PCI resource ranges:
	[0] -1	0	0x50000000 - 0x50003fff (0x4000) MX[B]
	[1] -1	0	0x50004000 - 0x500047ff (0x800) MX[B]
	[2] -1	0	0x50100000 - 0x501001ff (0x200) MX[B]
	[3] -1	0	0x50325800 - 0x503258ff (0x100) MX[B]
	[4] -1	0	0x50325000 - 0x503253ff (0x400) MX[B]
	[5] -1	0	0x50320000 - 0x50323fff (0x4000) MX[B]
	[6] -1	0	0x50325400 - 0x503257ff (0x400) MX[B]
	[7] -1	0	0x50324000 - 0x50324fff (0x1000) MX[B]
	[8] -1	0	0x50300000 - 0x5031ffff (0x20000) MX[B]
	[9] -1	0	0x50325900 - 0x5032590f (0x10) MX[B]
	[10] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[11] -1	0	0x50200000 - 0x502fffff (0x100000) MX[B](B)
	[12] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[13] -1	0	0x00001020 - 0x00001023 (0x4) IX[B]
	[14] -1	0	0x00001010 - 0x00001017 (0x8) IX[B]
	[15] -1	0	0x00001024 - 0x00001027 (0x4) IX[B]
	[16] -1	0	0x00001018 - 0x0000101f (0x8) IX[B]
	[17] -1	0	0x000020e0 - 0x000020ef (0x10) IX[B]
	[18] -1	0	0x000020f0 - 0x000020ff (0x10) IX[B]
	[19] -1	0	0x00002448 - 0x0000244b (0x4) IX[B]
	[20] -1	0	0x00002420 - 0x00002427 (0x8) IX[B]
	[21] -1	0	0x0000244c - 0x0000244f (0x4) IX[B]
	[22] -1	0	0x00002428 - 0x0000242f (0x8) IX[B]
	[23] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[24] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[25] -1	0	0x00002410 - 0x0000241f (0x10) IX[B]
	[26] -1	0	0x00002450 - 0x00002453 (0x4) IX[B]
	[27] -1	0	0x00002430 - 0x00002437 (0x8) IX[B]
	[28] -1	0	0x00002454 - 0x00002457 (0x4) IX[B]
	[29] -1	0	0x00002438 - 0x0000243f (0x8) IX[B]
	[30] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[31] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[32] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[33] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[34] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[35] -1	0	0x000020c0 - 0x000020df (0x20) IX[B]
	[36] -1	0	0x00002440 - 0x00002447 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x50000000 - 0x50003fff (0x4000) MX[B]
	[1] -1	0	0x50004000 - 0x500047ff (0x800) MX[B]
	[2] -1	0	0x50100000 - 0x501001ff (0x200) MX[B]
	[3] -1	0	0x50325800 - 0x503258ff (0x100) MX[B]
	[4] -1	0	0x50325000 - 0x503253ff (0x400) MX[B]
	[5] -1	0	0x50320000 - 0x50323fff (0x4000) MX[B]
	[6] -1	0	0x50325400 - 0x503257ff (0x400) MX[B]
	[7] -1	0	0x50324000 - 0x50324fff (0x1000) MX[B]
	[8] -1	0	0x50300000 - 0x5031ffff (0x20000) MX[B]
	[9] -1	0	0x50325900 - 0x5032590f (0x10) MX[B]
	[10] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[11] -1	0	0x50200000 - 0x502fffff (0x100000) MX[B](B)
	[12] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[13] -1	0	0x00001020 - 0x00001023 (0x4) IX[B]
	[14] -1	0	0x00001010 - 0x00001017 (0x8) IX[B]
	[15] -1	0	0x00001024 - 0x00001027 (0x4) IX[B]
	[16] -1	0	0x00001018 - 0x0000101f (0x8) IX[B]
	[17] -1	0	0x000020e0 - 0x000020ef (0x10) IX[B]
	[18] -1	0	0x000020f0 - 0x000020ff (0x10) IX[B]
	[19] -1	0	0x00002448 - 0x0000244b (0x4) IX[B]
	[20] -1	0	0x00002420 - 0x00002427 (0x8) IX[B]
	[21] -1	0	0x0000244c - 0x0000244f (0x4) IX[B]
	[22] -1	0	0x00002428 - 0x0000242f (0x8) IX[B]
	[23] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[24] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[25] -1	0	0x00002410 - 0x0000241f (0x10) IX[B]
	[26] -1	0	0x00002450 - 0x00002453 (0x4) IX[B]
	[27] -1	0	0x00002430 - 0x00002437 (0x8) IX[B]
	[28] -1	0	0x00002454 - 0x00002457 (0x4) IX[B]
	[29] -1	0	0x00002438 - 0x0000243f (0x8) IX[B]
	[30] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[31] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[32] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[33] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[34] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[35] -1	0	0x000020c0 - 0x000020df (0x20) IX[B]
	[36] -1	0	0x00002440 - 0x00002447 (0x8) IX[B](B)
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
	[4] -1	0	0x50000000 - 0x50003fff (0x4000) MX[B]
	[5] -1	0	0x50004000 - 0x500047ff (0x800) MX[B]
	[6] -1	0	0x50100000 - 0x501001ff (0x200) MX[B]
	[7] -1	0	0x50325800 - 0x503258ff (0x100) MX[B]
	[8] -1	0	0x50325000 - 0x503253ff (0x400) MX[B]
	[9] -1	0	0x50320000 - 0x50323fff (0x4000) MX[B]
	[10] -1	0	0x50325400 - 0x503257ff (0x400) MX[B]
	[11] -1	0	0x50324000 - 0x50324fff (0x1000) MX[B]
	[12] -1	0	0x50300000 - 0x5031ffff (0x20000) MX[B]
	[13] -1	0	0x50325900 - 0x5032590f (0x10) MX[B]
	[14] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[15] -1	0	0x50200000 - 0x502fffff (0x100000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[19] -1	0	0x00001020 - 0x00001023 (0x4) IX[B]
	[20] -1	0	0x00001010 - 0x00001017 (0x8) IX[B]
	[21] -1	0	0x00001024 - 0x00001027 (0x4) IX[B]
	[22] -1	0	0x00001018 - 0x0000101f (0x8) IX[B]
	[23] -1	0	0x000020e0 - 0x000020ef (0x10) IX[B]
	[24] -1	0	0x000020f0 - 0x000020ff (0x10) IX[B]
	[25] -1	0	0x00002448 - 0x0000244b (0x4) IX[B]
	[26] -1	0	0x00002420 - 0x00002427 (0x8) IX[B]
	[27] -1	0	0x0000244c - 0x0000244f (0x4) IX[B]
	[28] -1	0	0x00002428 - 0x0000242f (0x8) IX[B]
	[29] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[30] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[31] -1	0	0x00002410 - 0x0000241f (0x10) IX[B]
	[32] -1	0	0x00002450 - 0x00002453 (0x4) IX[B]
	[33] -1	0	0x00002430 - 0x00002437 (0x8) IX[B]
	[34] -1	0	0x00002454 - 0x00002457 (0x4) IX[B]
	[35] -1	0	0x00002438 - 0x0000243f (0x8) IX[B]
	[36] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[37] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[38] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[39] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[40] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[41] -1	0	0x000020c0 - 0x000020df (0x20) IX[B]
	[42] -1	0	0x00002440 - 0x00002447 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, 965G, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33
(II) Primary Device is: PCI 00:02:0
(--) Chipset 965G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x50003fff (0x4000) MX[B]
	[5] -1	0	0x50004000 - 0x500047ff (0x800) MX[B]
	[6] -1	0	0x50100000 - 0x501001ff (0x200) MX[B]
	[7] -1	0	0x50325800 - 0x503258ff (0x100) MX[B]
	[8] -1	0	0x50325000 - 0x503253ff (0x400) MX[B]
	[9] -1	0	0x50320000 - 0x50323fff (0x4000) MX[B]
	[10] -1	0	0x50325400 - 0x503257ff (0x400) MX[B]
	[11] -1	0	0x50324000 - 0x50324fff (0x1000) MX[B]
	[12] -1	0	0x50300000 - 0x5031ffff (0x20000) MX[B]
	[13] -1	0	0x50325900 - 0x5032590f (0x10) MX[B]
	[14] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[15] -1	0	0x50200000 - 0x502fffff (0x100000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[19] -1	0	0x00001020 - 0x00001023 (0x4) IX[B]
	[20] -1	0	0x00001010 - 0x00001017 (0x8) IX[B]
	[21] -1	0	0x00001024 - 0x00001027 (0x4) IX[B]
	[22] -1	0	0x00001018 - 0x0000101f (0x8) IX[B]
	[23] -1	0	0x000020e0 - 0x000020ef (0x10) IX[B]
	[24] -1	0	0x000020f0 - 0x000020ff (0x10) IX[B]
	[25] -1	0	0x00002448 - 0x0000244b (0x4) IX[B]
	[26] -1	0	0x00002420 - 0x00002427 (0x8) IX[B]
	[27] -1	0	0x0000244c - 0x0000244f (0x4) IX[B]
	[28] -1	0	0x00002428 - 0x0000242f (0x8) IX[B]
	[29] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[30] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[31] -1	0	0x00002410 - 0x0000241f (0x10) IX[B]
	[32] -1	0	0x00002450 - 0x00002453 (0x4) IX[B]
	[33] -1	0	0x00002430 - 0x00002437 (0x8) IX[B]
	[34] -1	0	0x00002454 - 0x00002457 (0x4) IX[B]
	[35] -1	0	0x00002438 - 0x0000243f (0x8) IX[B]
	[36] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[37] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[38] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[39] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[40] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[41] -1	0	0x000020c0 - 0x000020df (0x20) IX[B]
	[42] -1	0	0x00002440 - 0x00002447 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x50003fff (0x4000) MX[B]
	[5] -1	0	0x50004000 - 0x500047ff (0x800) MX[B]
	[6] -1	0	0x50100000 - 0x501001ff (0x200) MX[B]
	[7] -1	0	0x50325800 - 0x503258ff (0x100) MX[B]
	[8] -1	0	0x50325000 - 0x503253ff (0x400) MX[B]
	[9] -1	0	0x50320000 - 0x50323fff (0x4000) MX[B]
	[10] -1	0	0x50325400 - 0x503257ff (0x400) MX[B]
	[11] -1	0	0x50324000 - 0x50324fff (0x1000) MX[B]
	[12] -1	0	0x50300000 - 0x5031ffff (0x20000) MX[B]
	[13] -1	0	0x50325900 - 0x5032590f (0x10) MX[B]
	[14] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[15] -1	0	0x50200000 - 0x502fffff (0x100000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[22] -1	0	0x00001020 - 0x00001023 (0x4) IX[B]
	[23] -1	0	0x00001010 - 0x00001017 (0x8) IX[B]
	[24] -1	0	0x00001024 - 0x00001027 (0x4) IX[B]
	[25] -1	0	0x00001018 - 0x0000101f (0x8) IX[B]
	[26] -1	0	0x000020e0 - 0x000020ef (0x10) IX[B]
	[27] -1	0	0x000020f0 - 0x000020ff (0x10) IX[B]
	[28] -1	0	0x00002448 - 0x0000244b (0x4) IX[B]
	[29] -1	0	0x00002420 - 0x00002427 (0x8) IX[B]
	[30] -1	0	0x0000244c - 0x0000244f (0x4) IX[B]
	[31] -1	0	0x00002428 - 0x0000242f (0x8) IX[B]
	[32] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[33] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[34] -1	0	0x00002410 - 0x0000241f (0x10) IX[B]
	[35] -1	0	0x00002450 - 0x00002453 (0x4) IX[B]
	[36] -1	0	0x00002430 - 0x00002437 (0x8) IX[B]
	[37] -1	0	0x00002454 - 0x00002457 (0x4) IX[B]
	[38] -1	0	0x00002438 - 0x0000243f (0x8) IX[B]
	[39] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[40] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[41] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[42] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[43] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[44] -1	0	0x000020c0 - 0x000020df (0x20) IX[B]
	[45] -1	0	0x00002440 - 0x00002447 (0x8) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(**) intel(0): Depth 16, (--) framebuffer bpp 16
(==) intel(0): RGB weight 565
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965G
(--) intel(0): Chipset: "965G"
(--) intel(0): Linear framebuffer at 0x40000000
(--) intel(0): IO registers at addr 0x50200000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) intel(0): Output VGA using monitor section SyncMaster
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Manufacturer: SAM  Model: 1b7  Serial#: 1212231991
(II) intel(0): Year: 2007  Week: 25
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x870@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HHGP603620
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2db70137314148
(II) intel(0): 	191101030e221b782aaaa5a654549926
(II) intel(0): 	145054bfef8081808140714f01010101
(II) intel(0): 	010101010101302a009851002a403070
(II) intel(0): 	1300520e1100001e000000fd00384b1e
(II) intel(0): 	510e000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	00484847503630333632300a20200055
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Not using mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1280x1024
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 7676 kB stolen memory.
(==) intel(0): video overlay key set to 0x83e
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (340, 270) mm
(**) intel(0): DPI set to (95, 120)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000000 to 0x00000b00
(WW) intel(0): Register 0x70008 (PIPEACONF) changed from 0xc0000000 to 0x00000000
(WW) intel(0): PIPEACONF before: enabled, active
(WW) intel(0): PIPEACONF after: disabled, inactive
(WW) intel(0): Register 0x71008 (PIPEBCONF) changed from 0xc0000000 to 0x00000000
(WW) intel(0): PIPEBCONF before: enabled, active
(WW) intel(0): PIPEBCONF after: disabled, inactive
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x40000000 - 0x4fffffff (0x10000000) MS[B]
	[1] 0	0	0x50200000 - 0x502fffff (0x100000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0x50000000 - 0x50003fff (0x4000) MX[B]
	[7] -1	0	0x50004000 - 0x500047ff (0x800) MX[B]
	[8] -1	0	0x50100000 - 0x501001ff (0x200) MX[B]
	[9] -1	0	0x50325800 - 0x503258ff (0x100) MX[B]
	[10] -1	0	0x50325000 - 0x503253ff (0x400) MX[B]
	[11] -1	0	0x50320000 - 0x50323fff (0x4000) MX[B]
	[12] -1	0	0x50325400 - 0x503257ff (0x400) MX[B]
	[13] -1	0	0x50324000 - 0x50324fff (0x1000) MX[B]
	[14] -1	0	0x50300000 - 0x5031ffff (0x20000) MX[B]
	[15] -1	0	0x50325900 - 0x5032590f (0x10) MX[B]
	[16] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[17] -1	0	0x50200000 - 0x502fffff (0x100000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] 0	0	0x00002440 - 0x00002447 (0x8) IS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[25] -1	0	0x00001020 - 0x00001023 (0x4) IX[B]
	[26] -1	0	0x00001010 - 0x00001017 (0x8) IX[B]
	[27] -1	0	0x00001024 - 0x00001027 (0x4) IX[B]
	[28] -1	0	0x00001018 - 0x0000101f (0x8) IX[B]
	[29] -1	0	0x000020e0 - 0x000020ef (0x10) IX[B]
	[30] -1	0	0x000020f0 - 0x000020ff (0x10) IX[B]
	[31] -1	0	0x00002448 - 0x0000244b (0x4) IX[B]
	[32] -1	0	0x00002420 - 0x00002427 (0x8) IX[B]
	[33] -1	0	0x0000244c - 0x0000244f (0x4) IX[B]
	[34] -1	0	0x00002428 - 0x0000242f (0x8) IX[B]
	[35] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[36] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[37] -1	0	0x00002410 - 0x0000241f (0x10) IX[B]
	[38] -1	0	0x00002450 - 0x00002453 (0x4) IX[B]
	[39] -1	0	0x00002430 - 0x00002437 (0x8) IX[B]
	[40] -1	0	0x00002454 - 0x00002457 (0x4) IX[B]
	[41] -1	0	0x00002438 - 0x0000243f (0x8) IX[B]
	[42] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[43] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[44] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[45] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[46] -1	0	0x000020a0 - 0x000020bf (0x20) IX[B]
	[47] -1	0	0x000020c0 - 0x000020df (0x20) IX[B]
	[48] -1	0	0x00002440 - 0x00002447 (0x8) IX[B](B)
	[49] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[50] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 236800 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 947196 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(II) intel(0): Allocating 7104 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00041fff: exa G965 state buffer (64 kB)
(II) intel(0): 0x00050000-0x014c7fff: front buffer (20960 kB)
(II) intel(0): 0x0077f000:            end of stolen memory
(II) intel(0): 0x014c8000-0x014d7fff: xaa scratch (64 kB)
(II) intel(0): 0x014d8000-0x017f7fff: back buffer (3200 kB)
(II) intel(0): 0x017f8000-0x01b17fff: depth buffer (3200 kB)
(II) intel(0): 0x01b18000-0x03b17fff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] loaded kernel module for "i915" driver
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xf8caa000
(II) intel(0): [drm] mapped SAREA 0xf8caa000 to 0xb7fbd000
(II) intel(0): [drm] framebuffer handle = 0x40050000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): [drm] Registers = 0x50200000
(II) intel(0): [drm] ring buffer = 0x40000000
(II) intel(0): [drm] init sarea width,height = 1280 x 1280 (pitch 1280)
(II) intel(0): [drm] Back Buffer = 0x414d8000
(II) intel(0): [drm] Depth Buffer = 0x417f8000
(II) intel(0): [drm] textures = 0x41b18000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0x40000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0077f000 (pgoffset 1919)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x014c8000 (pgoffset 5320)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x014d8000 (pgoffset 5336)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x017f8000 (pgoffset 6136)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x01b18000 (pgoffset 6936)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 17
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 270
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc101"
(**) Generic Keyboard: XkbModel: "pc101"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Manufacturer: SAM  Model: 1b7  Serial#: 1212231991
(II) intel(0): Year: 2007  Week: 25
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x870@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HHGP603620
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2db70137314148
(II) intel(0): 	191101030e221b782aaaa5a654549926
(II) intel(0): 	145054bfef8081808140714f01010101
(II) intel(0): 	010101010101302a009851002a403070
(II) intel(0): 	1300520e1100001e000000fd00384b1e
(II) intel(0): 	510e000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	00484847503630333632300a20200055
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Not using mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Manufacturer: SAM  Model: 1b7  Serial#: 1212231991
(II) intel(0): Year: 2007  Week: 25
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x870@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HHGP603620
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2db70137314148
(II) intel(0): 	191101030e221b782aaaa5a654549926
(II) intel(0): 	145054bfef8081808140714f01010101
(II) intel(0): 	010101010101302a009851002a403070
(II) intel(0): 	1300520e1100001e000000fd00384b1e
(II) intel(0): 	510e000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	00484847503630333632300a20200055
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Not using mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Manufacturer: SAM  Model: 1b7  Serial#: 1212231991
(II) intel(0): Year: 2007  Week: 25
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x870@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HHGP603620
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2db70137314148
(II) intel(0): 	191101030e221b782aaaa5a654549926
(II) intel(0): 	145054bfef8081808140714f01010101
(II) intel(0): 	010101010101302a009851002a403070
(II) intel(0): 	1300520e1100001e000000fd00384b1e
(II) intel(0): 	510e000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	00484847503630333632300a20200055
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Not using mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Manufacturer: SAM  Model: 1b7  Serial#: 1212231991
(II) intel(0): Year: 2007  Week: 25
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x870@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HHGP603620
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2db70137314148
(II) intel(0): 	191101030e221b782aaaa5a654549926
(II) intel(0): 	145054bfef8081808140714f01010101
(II) intel(0): 	010101010101302a009851002a403070
(II) intel(0): 	1300520e1100001e000000fd00384b1e
(II) intel(0): 	510e000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	00484847503630333632300a20200055
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Not using mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Manufacturer: SAM  Model: 1b7  Serial#: 1212231991
(II) intel(0): Year: 2007  Week: 25
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x870@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HHGP603620
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2db70137314148
(II) intel(0): 	191101030e221b782aaaa5a654549926
(II) intel(0): 	145054bfef8081808140714f01010101
(II) intel(0): 	010101010101302a009851002a403070
(II) intel(0): 	1300520e1100001e000000fd00384b1e
(II) intel(0): 	510e000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	00484847503630333632300a20200055
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Not using mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Manufacturer: SAM  Model: 1b7  Serial#: 1212231991
(II) intel(0): Year: 2007  Week: 25
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x870@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HHGP603620
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2db70137314148
(II) intel(0): 	191101030e221b782aaaa5a654549926
(II) intel(0): 	145054bfef8081808140714f01010101
(II) intel(0): 	010101010101302a009851002a403070
(II) intel(0): 	1300520e1100001e000000fd00384b1e
(II) intel(0): 	510e000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	00484847503630333632300a20200055
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Not using mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
SetClientVersion: 0 9
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Manufacturer: SAM  Model: 1b7  Serial#: 1212231991
(II) intel(0): Year: 2007  Week: 25
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x870@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HHGP603620
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2db70137314148
(II) intel(0): 	191101030e221b782aaaa5a654549926
(II) intel(0): 	145054bfef8081808140714f01010101
(II) intel(0): 	010101010101302a009851002a403070
(II) intel(0): 	1300520e1100001e000000fd00384b1e
(II) intel(0): 	510e000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	00484847503630333632300a20200055
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Not using mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Manufacturer: SAM  Model: 1b7  Serial#: 1212231991
(II) intel(0): Year: 2007  Week: 25
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x870@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HHGP603620
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2db70137314148
(II) intel(0): 	191101030e221b782aaaa5a654549926
(II) intel(0): 	145054bfef8081808140714f01010101
(II) intel(0): 	010101010101302a009851002a403070
(II) intel(0): 	1300520e1100001e000000fd00384b1e
(II) intel(0): 	510e000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	00484847503630333632300a20200055
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Not using mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
```

---

### Post by Forlong on 2008-06-22
Hm... I don't see any obvious errors.

Try changing the **DefaultDepth** to **24** in the **Section "Screen"**

Then reboot and post the output of ```
compiz
``` in a terminal.

---

### Post by dexter.deepak on 2008-06-22
```
dpak@dpak-server:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
```

```
dpak@dpak-server:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0


```

---

### Post by Forlong on 2008-06-22
Why did you install Xgl?

And why does it say "Enabling Xgl with fglrx ATi drivers"?!

Did you install the proprietary fglrx driver?

---

### Post by dexter.deepak on 2008-06-22
i never knew !!:(
i just followed what i had read in some of the blogs..to anyhow run compiz on my comp.
 
so , should i uninstall Xgl ?

one more thing, i just installed hardy on my system, and i could feel some of the effects coming..
yet , when i tried running compiz / SKIP_CHECKS=yes compiz  , it gave the same errors.
is there a hope here ?

---

### Post by dexter.deepak on 2008-06-23
it seems that i may have ruined the system.
may be there is a chance on hardy...afterall it gives me atleast the "normal" effects, which i couldnt get on gutsy !!
the o/p :
```
pak@dpak-server:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:29a2 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

---

### Post by Forlong on 2008-06-23
Alright, I don't usually recommend this but just installing Hardy from scratch seems to be the best choice here.

If you do, **do not install anything and do not follow any random guide out there**.

Additionally, **do not run Compiz with checks skipped**

You shouldn't need any of that! Compiz should be working out of the box for you.

If it doesn't, come back here and ask for help before you do anything.

If it does and you want some mor fanciness, go here: [http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

---

### Post by dexter.deepak on 2008-06-23
thanks a lot for that brotherly support :popcorn:
i have a fresh system with hardy on it, and compiz runs flawlessly on it !!
...and the link you gave me, is one of my favourites since i started using ubuntu.

again..i would like to thank you for so much care.:guitar:

---

