---
title: "[SOLVED] Feisty freezing and crashing!!  Last straw!!!!!"
date: 2007-08-07
forum: General Help
---

### Post by Slimo on 2007-08-07
Hey I am in desperate need of help!  My Ubuntu Feisty install randomly crashes and the screen locks up.  If I have music playing, the music will keep playing but the screen will lock, then the mouse stop, then finally the screen will go completely black - ctrl+alt+backspace does nothing, I have to do a hard restart.

Then when I do a hard restart, the screen often will be buggy - hard to explain but there are lines and symbols all over the place (i.e. on the boot up screens)

This happens in the Gnome Failsafe session as well.  I have done a clean install - but the same problem still occurs!!

I know there are other (possibly) related posts but none of them seem to have the same issues as myself.  I have an ATI Radeon 9800, using fglrx drivers.

I am not sure if the problem is my monitor, graphics card, linux kernel, etc...

If anyone can offer any assitance please do!!  I am nearing the end of my tether with this problem, and I don't want to revert to Windows, but if I can't get a reliable OS then I will have to.

Thanks

---

### Post by fatdaddy on 2007-08-07
Hey,

Don't look at ubuntu as the problem.  I run 4 box's on ubuntu including an ole laptop.  If it wont run right  on ubuntu then it probably wont work with windoze.

Having been repairing computers since 68, and that is 1968 I would think you are experiencing a video card or display logic problem.  If you computer has a removable video card, try replacing it and see how it runs.

That would be the 1st thing I would do and try.  Possably you have a friend or your local LUG could lone you a card.

Best of luck

Zack

---

### Post by Slimo on 2007-08-07
Thanks for your quick reply.

I think if the graphics card really was the problem I would definitely get an nvidia one, however I have been running Ubuntu with my Radeon 9800 for 6 months now, and the freezing and display problems have only started in the last month or so.

From that I thought it was most likely a driver or kernel issue - maybe some sort of virus?

I will bear your suggestion in mind but would rather not spend money on something that won't fix the problem 100%.  I will check with my friends to see if any of them have a replacement graphics card though.

Thanks

---

### Post by stuarticus on 2007-08-07
Sounds like a motherboard fault to me (see a lot of them overclocking) was it running windows ok?

 Get UBCD and run some h/w tests.

---

### Post by Slimo on 2007-08-07
I never had problems like this in Windows.  At the moment Ubuntu will run fine for about 5 - 10 mins and then freeze and crash.  I have had my motherboard for about 5 years so it is quite old but the problems have only started recently as I said.

What are h/w tests?

---

### Post by totheresq001 on 2007-08-08
Try booting your system and running from the live cd to see if it locks up.  You coulld also use a Knoppix disk.  If it boots up and runs without problem it is a hardware issue and you can troubleshoot from there

---

### Post by Slimo on 2007-08-08
Thanks guys.

I booted from the Live CD last night and everything worked fine - no crashes or problems in the hour or so I used it.  Booting normally however, the average time before a freeze/crash is about 10 minutes.

So do we think it is hardware related?

---

### Post by Cryptic1911 on 2007-08-08
I would almost say this is a videocard (hardware) problem myself, but it seems kinda odd that you can run OK from a live cd. After you install, what do you change? anything video related? and are you using compiz/beryl at all?

---

### Post by apetresc on 2007-08-08
Is there anything interesting in /var/log/syslog or /var/log/Xorg.0.log after one of these crashes?

---

### Post by Slimo on 2007-08-08
I have used Compiz Fusion in the past, and it has run fine.  Also, the crashes occur even if I login to the Gnome Failsafe session.
I enabled the ATI restricted drivers once I reinstalled because without them the screen looked pretty hazy.

---

### Post by tgalati4 on 2007-08-08
If you suspect the motherboard, then go into the BIOS and run the system at 1/2 speed.  It could also be the power supply crapping out.

---

### Post by Slimo on 2007-08-08
Here is the Xorg.0.log output:

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux simon-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 10 00:19:55 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "PHILIPS 107S"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
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
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 10de,01a4 card 0000,0000 rev b2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01ac card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ad card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01aa card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,01b2 card 10de,0c11 rev c3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,01b4 card 10de,0c11 rev c1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,01c2 card 10de,0c11 rev c3 class 0c,03,10 hdr 00
(II) PCI: 00:03:0: chip 10de,01c2 card 10de,0c11 rev c3 class 0c,03,10 hdr 00
(II) PCI: 00:04:0: chip 10de,01c3 card 1043,0c11 rev c2 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,01b0 card 1043,0c11 rev c2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,01b1 card 1043,8384 rev c2 class 04,01,00 hdr 80
(II) PCI: 00:08:0: chip 10de,01b8 card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,01bc card 10de,0c11 rev c3 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01b7 card 0000,0000 rev b2 class 06,04,00 hdr 01
(II) PCI: 01:07:0: chip 14f1,1053 card 144f,1047 rev 08 class 07,80,00 hdr 00
(II) PCI: 02:00:0: chip 1002,4148 card 1787,8504 rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,4168 card 1787,8505 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdd7fffff (0x800000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xf7ffffff (0x18000000) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc R350 AH [Radeon 9800] rev 0, Mem @ 0xf0000000/27, 0xdc800000/16, I/O @ 0x9800/8, BIOS @ 0xeffe0000/17
(--) PCI: (2:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800] (Secondary) rev 0, Mem @ 0xe0000000/27, 0xdc000000/16
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
	[0] -1	0	0xdd000000 - 0xdd00ffff (0x10000) MX[B]
	[1] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[2] -1	0	0xde000000 - 0xde07ffff (0x80000) MX[B]
	[3] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[4] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[5] -1	0	0xdf800000 - 0xdf800fff (0x1000) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[10] -1	0	0xdc800000 - 0xdc80ffff (0x10000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[15] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[17] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[18] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[19] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[20] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdd000000 - 0xdd00ffff (0x10000) MX[B]
	[1] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[2] -1	0	0xde000000 - 0xde07ffff (0x80000) MX[B]
	[3] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[4] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[5] -1	0	0xdf800000 - 0xdf800fff (0x1000) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[10] -1	0	0xdc800000 - 0xdc80ffff (0x10000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[15] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[17] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[18] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[19] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[20] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
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
	[4] -1	0	0xdd000000 - 0xdd00ffff (0x10000) MX[B]
	[5] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[6] -1	0	0xde000000 - 0xde07ffff (0x80000) MX[B]
	[7] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[8] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[9] -1	0	0xdf800000 - 0xdf800fff (0x1000) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[14] -1	0	0xdc800000 - 0xdc80ffff (0x10000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[21] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[23] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[24] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[25] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[26] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4148) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdd000000 - 0xdd00ffff (0x10000) MX[B]
	[5] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[6] -1	0	0xde000000 - 0xde07ffff (0x80000) MX[B]
	[7] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[8] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[9] -1	0	0xdf800000 - 0xdf800fff (0x1000) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[14] -1	0	0xdc800000 - 0xdc80ffff (0x10000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[21] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[23] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[24] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[25] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[26] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e4ac8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdd000000 - 0xdd00ffff (0x10000) MX[B]
	[5] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[6] -1	0	0xde000000 - 0xde07ffff (0x80000) MX[B]
	[7] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[8] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[9] -1	0	0xdf800000 - 0xdf800fff (0x1000) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[14] -1	0	0xdc800000 - 0xdc80ffff (0x10000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[24] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[26] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[27] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[28] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[29] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9800 SE" (Chipset = 0x4148)
(--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x8504)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xf0000000
(--) fglrx(0): MMIO registers at 0xdc800000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI R350
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: PHL  Model: e005  Serial#: 324621
(II) fglrx(0): Year: 2002  Week: 19
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 31  vert.: 23
(II) fglrx(0): Gamma: 2.87
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing not preferred mode in violation of standard!(II) fglrx(0): redX: 0.620 redY: 0.345   greenX: 0.290 greenY: 0.610
(II) fglrx(0): blueX: 0.155 blueY: 0.065   whiteX: 0.283 whiteY: 0.297
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 100  vid: 26673
(II) fglrx(0): #5: hsize: 800  vsize 600  refresh: 100  vid: 26693
(II) fglrx(0): #6: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #7: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 25.2 MHz   Image Size:  306 x 230 mm
(II) fglrx(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) fglrx(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) fglrx(0): Serial No:  BZ  324621
(II) fglrx(0): Monitor name: PHILIPS 107S
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 71 kHz, PixClock max 110 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00410c05e00df40400
(II) fglrx(0): 	130c0103681f17bbe8d5f89e584a9c27
(II) fglrx(0): 	10484cadee0031594559615981803168
(II) fglrx(0): 	45688140714fd60980a0205e63101060
(II) fglrx(0): 	520832e61000001a000000ff0020425a
(II) fglrx(0): 	20203332343632310a20000000fc0050
(II) fglrx(0): 	48494c49505320313037530a000000fd
(II) fglrx(0): 	0032a01e470b000a202020202020002c
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 43 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.17  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.40  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0): *Mode "640x350": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "640x350"   25.18  640 656 752 800  350 387 389 449 +vsync
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (310, 230) mm
(--) fglrx(0): DPI set to (104, 113)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.17  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.40  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0): *Mode "640x350": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "640x350"   25.18  640 656 752 800  350 387 389 449 +vsync
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
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
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdc800000 - 0xdc80ffff (0x10000) MX[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdd000000 - 0xdd00ffff (0x10000) MX[B]
	[7] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[8] -1	0	0xde000000 - 0xde07ffff (0x80000) MX[B]
	[9] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[10] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[11] -1	0	0xdf800000 - 0xdf800fff (0x1000) MX[B]
	[12] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[13] -1	0	0xdc000000 - 0xdc00ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[16] -1	0	0xdc800000 - 0xdc80ffff (0x10000) MX[B](B)
	[17] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[27] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[29] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[30] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[31] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[32] -1	0	0x00009800 - 0x000098ff (0x100) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7bea000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f000217 bridge: 0x10de/0x01a4
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000314
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xf8000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000314)
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x00701000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Interrupt handler installed at IRQ 19.
(II) fglrx(0): Exposed events to the /proc interface
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
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
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

And the Syslog output:

```
Aug  9 07:33:45 simon-desktop syslogd 1.4.1#20ubuntu4: restart.
Aug  9 07:33:45 simon-desktop anacron[5776]: Job `cron.daily' terminated
Aug  9 07:33:45 simon-desktop anacron[5776]: Normal exit (1 job run)
Aug  9 07:36:12 simon-desktop gconfd (root-6495): starting (version 2.18.0.1), pid 6495 user 'root'
Aug  9 07:36:12 simon-desktop gconfd (root-6495): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  9 07:36:12 simon-desktop gconfd (root-6495): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug  9 07:36:12 simon-desktop gconfd (root-6495): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  9 07:36:12 simon-desktop gconfd (root-6495): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  9 07:36:12 simon-desktop gconfd (root-6495): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  9 07:36:42 simon-desktop gconfd (root-6495): SIGHUP received, reloading all databases
Aug  9 07:36:42 simon-desktop gconfd (root-6495): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  9 07:36:42 simon-desktop gconfd (root-6495): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug  9 07:36:42 simon-desktop gconfd (root-6495): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  9 07:36:42 simon-desktop gconfd (root-6495): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  9 07:36:42 simon-desktop gconfd (root-6495): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  9 07:36:42 simon-desktop gconfd (root-6495): GConf server is not in use, shutting down.
Aug  9 07:36:42 simon-desktop gconfd (root-6495): Exiting
Aug  9 07:38:30 simon-desktop gconfd (simon-5957): Exiting
Aug  9 07:38:31 simon-desktop kernel: [  741.080894] [fglrx] Internal AGP support requested, but kernel AGP support active.
Aug  9 07:38:31 simon-desktop kernel: [  741.080909] [fglrx] Have to use kernel AGP support to avoid conflicts.
Aug  9 07:38:31 simon-desktop kernel: [  741.080915] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Aug  9 07:38:31 simon-desktop kernel: [  741.081458] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Aug  9 07:38:31 simon-desktop kernel: [  741.081605] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Aug  9 07:38:31 simon-desktop kernel: [  741.081769] agpgart: Putting AGP V2 device at 0000:02:00.0 into 4x mode
Aug  9 07:38:31 simon-desktop kernel: [  741.081905] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Aug  9 07:38:31 simon-desktop kernel: [  741.096099] [fglrx] total      GART = 67108864
Aug  9 07:38:31 simon-desktop kernel: [  741.096111] [fglrx] free       GART = 51113984
Aug  9 07:38:31 simon-desktop kernel: [  741.096114] [fglrx] max single GART = 51113984
Aug  9 07:38:31 simon-desktop kernel: [  741.096117] [fglrx] total      LFB  = 134217728
Aug  9 07:38:31 simon-desktop kernel: [  741.096119] [fglrx] free       LFB  = 116387840
Aug  9 07:38:31 simon-desktop kernel: [  741.096122] [fglrx] max single LFB  = 116387840
Aug  9 07:38:31 simon-desktop kernel: [  741.096124] [fglrx] total      Inv  = 0
Aug  9 07:38:31 simon-desktop kernel: [  741.096126] [fglrx] free       Inv  = 0
Aug  9 07:38:31 simon-desktop kernel: [  741.096128] [fglrx] max single Inv  = 0
Aug  9 07:38:31 simon-desktop kernel: [  741.096130] [fglrx] total      TIM  = 0
Aug  9 07:38:40 simon-desktop gconfd (simon-6671): starting (version 2.18.0.1), pid 6671 user 'simon'
Aug  9 07:38:40 simon-desktop gconfd (simon-6671): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  9 07:38:40 simon-desktop gconfd (simon-6671): Resolved address "xml:readwrite:/home/simon/.gconf" to a writable configuration source at position 1
Aug  9 07:38:40 simon-desktop gconfd (simon-6671): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  9 07:38:40 simon-desktop gconfd (simon-6671): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  9 07:38:40 simon-desktop gconfd (simon-6671): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  9 07:38:41 simon-desktop gconfd (simon-6671): Resolved address "xml:readwrite:/home/simon/.gconf" to a writable configuration source at position 0
Aug 10 00:19:51 simon-desktop syslogd 1.4.1#20ubuntu4: restart.
Aug 10 00:19:51 simon-desktop kernel: Inspecting /boot/System.map-2.6.20-16-generic
Aug 10 00:19:51 simon-desktop kernel: Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.
Aug 10 00:19:51 simon-desktop kernel: Symbols match kernel version 2.6.20.
Aug 10 00:19:51 simon-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] sanitize start
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] sanitize end
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 0000000000080000 end: 0000000000080000 type: 1
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001feec000 end: 000000001ffec000 type: 1
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() start: 000000001ffec000 size: 0000000000003000 end: 000000001ffef000 type: 3
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() start: 000000001ffef000 size: 0000000000010000 end: 000000001ffff000 type: 2
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() start: 000000001ffff000 size: 0000000000001000 end: 0000000020000000 type: 4
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000000080000 (usable)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] 511MB LOWMEM available.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 131052) 0 entries of 256 used
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Zone PFN ranges:
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]   DMA             0 ->     4096
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]   Normal       4096 ->   131052
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]   HighMem    131052 ->   131052
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]     0:        0 ->   131052
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] On node 0 totalpages: 131052
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]   Normal zone: 125965 pages, LIFO batch:31
Aug 10 00:19:51 simon-desktop kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] DMI 2.3 present.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f8090
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: RSDT (v001 ASUS   A7N266VM 0x42302e31 MSFT 0x31313031) @ 0x1ffec000
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: FADT (v001 ASUS   A7N266VM 0x42302e31 MSFT 0x31313031) @ 0x1ffec100
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: BOOT (v001 ASUS   A7N266VM 0x42302e31 MSFT 0x31313031) @ 0x1ffec040
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: MADT (v001 ASUS   A7N266VM 0x42302e31 MSFT 0x31313031) @ 0x1ffec080
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: DSDT (v001   ASUS A7N266VM 0x00001000 MSFT 0x0100000b) @ 0x00000000
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Processor #0 6:6 APIC version 16
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Aug 10 00:19:51 simon-desktop kernel: [    0.000000] Detected 1529.429 MHz processor.
Aug 10 00:19:51 simon-desktop kernel: [   11.876821] Built 1 zonelists.  Total pages: 130029
Aug 10 00:19:51 simon-desktop kernel: [   11.876826] Kernel command line: root=UUID=c73b62a5-6589-439d-9968-6d427d7f8402 ro quiet splash
Aug 10 00:19:51 simon-desktop kernel: [   11.877039] mapped APIC to ffffd000 (fee00000)
Aug 10 00:19:51 simon-desktop kernel: [   11.877043] mapped IOAPIC to ffffc000 (fec00000)
Aug 10 00:19:51 simon-desktop kernel: [   11.877047] Enabling fast FPU save and restore... done.
Aug 10 00:19:51 simon-desktop kernel: [   11.877050] Enabling unmasked SIMD FPU exception support... done.
Aug 10 00:19:51 simon-desktop kernel: [   11.877064] Initializing CPU#0
Aug 10 00:19:51 simon-desktop kernel: [   11.877139] PID hash table entries: 2048 (order: 11, 8192 bytes)
Aug 10 00:19:51 simon-desktop kernel: [   11.878431] Console: colour VGA+ 80x25
Aug 10 00:19:51 simon-desktop kernel: [   11.878885] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 10 00:19:51 simon-desktop kernel: [   11.879244] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 10 00:19:51 simon-desktop kernel: [   11.895407] Memory: 508476k/524208k available (1992k kernel code, 14972k reserved, 900k data, 328k init, 0k highmem)
Aug 10 00:19:51 simon-desktop kernel: [   11.895420] virtual kernel memory layout:
Aug 10 00:19:51 simon-desktop kernel: [   11.895422]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Aug 10 00:19:51 simon-desktop kernel: [   11.895424]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 10 00:19:51 simon-desktop kernel: [   11.895425]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Aug 10 00:19:51 simon-desktop kernel: [   11.895427]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
Aug 10 00:19:51 simon-desktop kernel: [   11.895429]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Aug 10 00:19:51 simon-desktop kernel: [   11.895430]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
Aug 10 00:19:51 simon-desktop kernel: [   11.895432]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
Aug 10 00:19:51 simon-desktop kernel: [   11.895436] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 10 00:19:51 simon-desktop kernel: [   11.973071] Calibrating delay using timer specific routine.. 3061.40 BogoMIPS (lpj=6122800)
Aug 10 00:19:51 simon-desktop kernel: [   11.973126] Security Framework v1.0.0 initialized
Aug 10 00:19:51 simon-desktop kernel: [   11.973135] SELinux:  Disabled at boot.
Aug 10 00:19:51 simon-desktop kernel: [   11.973157] Mount-cache hash table entries: 512
Aug 10 00:19:51 simon-desktop kernel: [   11.973345] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
Aug 10 00:19:51 simon-desktop kernel: [   11.973357] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 10 00:19:51 simon-desktop kernel: [   11.973360] CPU: L2 Cache: 256K (64 bytes/line)
Aug 10 00:19:51 simon-desktop kernel: [   11.973364] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
Aug 10 00:19:51 simon-desktop kernel: [   11.973377] Compat vDSO mapped to ffffe000.
Aug 10 00:19:51 simon-desktop kernel: [   11.973383] Remapping vsyscall page to ffffe000
Aug 10 00:19:51 simon-desktop kernel: [   11.973395] Checking 'hlt' instruction... OK.
Aug 10 00:19:51 simon-desktop kernel: [   11.989220] SMP alternatives: switching to UP code
Aug 10 00:19:51 simon-desktop kernel: [   11.989551] Freeing SMP alternatives: 11k freed
Aug 10 00:19:51 simon-desktop kernel: [   11.989886] Early unpacking initramfs... done
Aug 10 00:19:51 simon-desktop kernel: [   12.379998] ACPI: Core revision 20060707
Aug 10 00:19:51 simon-desktop kernel: [   12.380749] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Aug 10 00:19:51 simon-desktop kernel: [   12.382371] CPU0: AMD Athlon(TM) XP 1800+ stepping 02
Aug 10 00:19:51 simon-desktop kernel: [   12.382398] Total of 1 processors activated (3061.40 BogoMIPS).
Aug 10 00:19:51 simon-desktop kernel: [   12.382584] ENABLING IO-APIC IRQs
Aug 10 00:19:51 simon-desktop kernel: [   12.382786] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Aug 10 00:19:51 simon-desktop kernel: [   12.528707] Brought up 1 CPUs
Aug 10 00:19:51 simon-desktop kernel: [   12.529032] Booting paravirtualized kernel on bare hardware
Aug 10 00:19:51 simon-desktop kernel: [   12.529119] Time: 12:19:15  Date: 07/09/107
Aug 10 00:19:51 simon-desktop kernel: [   12.529165] NET: Registered protocol family 16
Aug 10 00:19:51 simon-desktop kernel: [   12.529297] EISA bus registered
Aug 10 00:19:51 simon-desktop kernel: [   12.529303] ACPI: bus type pci registered
Aug 10 00:19:51 simon-desktop kernel: [   12.530414] PCI: PCI BIOS revision 2.10 entry at 0xf1b40, last bus=2
Aug 10 00:19:51 simon-desktop kernel: [   12.530417] PCI: Using configuration type 1
Aug 10 00:19:51 simon-desktop kernel: [   12.530419] Setting up standard PCI resources
Aug 10 00:19:51 simon-desktop kernel: [   12.539794] ACPI: Interpreter enabled
Aug 10 00:19:51 simon-desktop kernel: [   12.539800] ACPI: Using IOAPIC for interrupt routing
Aug 10 00:19:51 simon-desktop kernel: [   12.540917] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 18) *5
Aug 10 00:19:51 simon-desktop kernel: [   12.541342] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 18) *0, disabled.
Aug 10 00:19:51 simon-desktop kernel: [   12.541759] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 18) *0, disabled.
Aug 10 00:19:51 simon-desktop kernel: [   12.542172] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 18) *5
Aug 10 00:19:51 simon-desktop kernel: [   12.542589] ACPI: PCI Interrupt Link [LNKE] (IRQs 19) *11
Aug 10 00:19:51 simon-desktop kernel: [   12.543011] ACPI: PCI Interrupt Link [LNKF] (IRQs 20 21 22) *5
Aug 10 00:19:51 simon-desktop kernel: [   12.543426] ACPI: PCI Interrupt Link [LNKU] (IRQs 20 21 22) *5
Aug 10 00:19:51 simon-desktop kernel: [   12.543853] ACPI: PCI Interrupt Link [LNKI] (IRQs 20 21 22) *5
Aug 10 00:19:51 simon-desktop kernel: [   12.544268] ACPI: PCI Interrupt Link [LNKJ] (IRQs 20 21 22) *5
Aug 10 00:19:51 simon-desktop kernel: [   12.544705] ACPI: PCI Interrupt Link [LNKK] (IRQs 20 21 22) *11
Aug 10 00:19:51 simon-desktop kernel: [   12.545125] ACPI: PCI Interrupt Link [LNKM] (IRQs 20 21 22) *0, disabled.
Aug 10 00:19:51 simon-desktop kernel: [   12.545272] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 10 00:19:51 simon-desktop kernel: [   12.545280] PCI: Probing PCI hardware (bus 00)
Aug 10 00:19:51 simon-desktop kernel: [   12.545713] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Aug 10 00:19:51 simon-desktop kernel: [   12.547663] Boot video device is 0000:02:00.0
Aug 10 00:19:51 simon-desktop kernel: [   12.547762] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 10 00:19:51 simon-desktop kernel: [   12.550555] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Aug 10 00:19:51 simon-desktop kernel: [   12.550830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
Aug 10 00:19:51 simon-desktop kernel: [   12.557243] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 10 00:19:51 simon-desktop kernel: [   12.557262] pnp: PnP ACPI init
Aug 10 00:19:51 simon-desktop kernel: [   12.564596] pnp: PnP ACPI: found 18 devices
Aug 10 00:19:51 simon-desktop kernel: [   12.564603] PnPBIOS: Disabled by ACPI PNP
Aug 10 00:19:51 simon-desktop kernel: [   12.564720] PCI: Using ACPI for IRQ routing
Aug 10 00:19:51 simon-desktop kernel: [   12.564726] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 10 00:19:51 simon-desktop kernel: [   12.571879] NET: Registered protocol family 8
Aug 10 00:19:51 simon-desktop kernel: [   12.571882] NET: Registered protocol family 20
Aug 10 00:19:51 simon-desktop kernel: [   12.572263] pnp: 00:02: ioport range 0xe400-0xe4fe could not be reserved
Aug 10 00:19:51 simon-desktop kernel: [   12.572268] pnp: 00:02: ioport range 0xe4ff-0xe4ff has been reserved
Aug 10 00:19:51 simon-desktop kernel: [   12.572271] pnp: 00:02: ioport range 0xcf0-0xcf3 could not be reserved
Aug 10 00:19:51 simon-desktop kernel: [   12.572296] pnp: 00:0f: ioport range 0x370-0x371 has been reserved
Aug 10 00:19:51 simon-desktop kernel: [   12.572704] PCI: Bridge: 0000:00:08.0
Aug 10 00:19:51 simon-desktop kernel: [   12.572708]   IO window: b000-bfff
Aug 10 00:19:51 simon-desktop kernel: [   12.572714]   MEM window: dd000000-dd7fffff
Aug 10 00:19:51 simon-desktop kernel: [   12.572719]   PREFETCH window: disabled.
Aug 10 00:19:51 simon-desktop kernel: [   12.572725] PCI: Bridge: 0000:00:1e.0
Aug 10 00:19:51 simon-desktop kernel: [   12.572728]   IO window: 9000-9fff
Aug 10 00:19:51 simon-desktop kernel: [   12.572733]   MEM window: dc000000-dcffffff
Aug 10 00:19:51 simon-desktop kernel: [   12.572737]   PREFETCH window: e0000000-f7ffffff
Aug 10 00:19:51 simon-desktop kernel: [   12.572751] PCI: Setting latency timer of device 0000:00:08.0 to 64
Aug 10 00:19:51 simon-desktop kernel: [   12.572758] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Aug 10 00:19:51 simon-desktop kernel: [   12.572796] NET: Registered protocol family 2
Aug 10 00:19:51 simon-desktop kernel: [   12.612701] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Aug 10 00:19:51 simon-desktop kernel: [   12.612819] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Aug 10 00:19:51 simon-desktop kernel: [   12.613056] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Aug 10 00:19:51 simon-desktop kernel: [   12.613180] TCP: Hash tables configured (established 16384 bind 8192)
Aug 10 00:19:51 simon-desktop kernel: [   12.613183] TCP reno registered
Aug 10 00:19:51 simon-desktop kernel: [   12.624747] checking if image is initramfs... it is
Aug 10 00:19:51 simon-desktop kernel: [   13.366982] Freeing initrd memory: 6778k freed
Aug 10 00:19:51 simon-desktop kernel: [   13.367239] Simple Boot Flag at 0x3f set to 0x1
Aug 10 00:19:51 simon-desktop kernel: [   13.367650] audit: initializing netlink socket (disabled)
Aug 10 00:19:51 simon-desktop kernel: [   13.367671] audit(1186661956.568:1): initialized
Aug 10 00:19:51 simon-desktop kernel: [   13.367816] VFS: Disk quotas dquot_6.5.1
Aug 10 00:19:51 simon-desktop kernel: [   13.367846] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 10 00:19:51 simon-desktop kernel: [   13.367912] io scheduler noop registered
Aug 10 00:19:51 simon-desktop kernel: [   13.367916] io scheduler anticipatory registered
Aug 10 00:19:51 simon-desktop kernel: [   13.367919] io scheduler deadline registered
Aug 10 00:19:51 simon-desktop kernel: [   13.367929] io scheduler cfq registered (default)
Aug 10 00:19:51 simon-desktop kernel: [   13.368276] isapnp: Scanning for PnP cards...
Aug 10 00:19:51 simon-desktop kernel: [   13.722223] isapnp: No Plug & Play device found
Aug 10 00:19:51 simon-desktop kernel: [   13.759835] Real Time Clock Driver v1.12ac
Aug 10 00:19:51 simon-desktop kernel: [   13.759903] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 10 00:19:51 simon-desktop kernel: [   13.760047] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 10 00:19:51 simon-desktop kernel: [   13.760372] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Aug 10 00:19:51 simon-desktop kernel: [   13.761265] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 10 00:19:51 simon-desktop kernel: [   13.761697] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Aug 10 00:19:51 simon-desktop kernel: [   13.762080] mice: PS/2 mouse device common for all mice
Aug 10 00:19:51 simon-desktop kernel: [   13.762821] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 10 00:19:51 simon-desktop kernel: [   13.763151] input: Macintosh mouse button emulation as /class/input/input0
Aug 10 00:19:51 simon-desktop kernel: [   13.763195] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 10 00:19:51 simon-desktop kernel: [   13.763200] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 10 00:19:51 simon-desktop kernel: [   13.763478] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 10 00:19:51 simon-desktop kernel: [   13.767178] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 10 00:19:51 simon-desktop kernel: [   13.767188] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 10 00:19:51 simon-desktop kernel: [   13.767422] EISA: Probing bus 0 at eisa.0
Aug 10 00:19:51 simon-desktop kernel: [   13.767453] Cannot allocate resource for EISA slot 5
Aug 10 00:19:51 simon-desktop kernel: [   13.767469] EISA: Detected 0 cards.
Aug 10 00:19:51 simon-desktop kernel: [   13.797566] TCP cubic registered
Aug 10 00:19:51 simon-desktop kernel: [   13.797574] NET: Registered protocol family 1
Aug 10 00:19:51 simon-desktop kernel: [   13.797605] Using IPI No-Shortcut mode
Aug 10 00:19:51 simon-desktop kernel: [   13.797688] ACPI: (supports S0 S1 S4 S5)
Aug 10 00:19:51 simon-desktop kernel: [   13.797743]   Magic number: 3:231:329
Aug 10 00:19:51 simon-desktop kernel: [   13.797933]   hash matches device tty50
Aug 10 00:19:51 simon-desktop kernel: [   13.798421] Freeing unused kernel memory: 328k freed
Aug 10 00:19:51 simon-desktop kernel: [   13.799683] Time: tsc clocksource has been installed.
Aug 10 00:19:51 simon-desktop kernel: [   13.811212] input: AT Translated Set 2 keyboard as /class/input/input1
Aug 10 00:19:51 simon-desktop kernel: [   15.082841] Capability LSM initialized
Aug 10 00:19:51 simon-desktop kernel: [   15.922343] usbcore: registered new interface driver usbfs
Aug 10 00:19:51 simon-desktop kernel: [   15.922377] usbcore: registered new interface driver hub
Aug 10 00:19:51 simon-desktop kernel: [   15.922410] usbcore: registered new device driver usb
Aug 10 00:19:51 simon-desktop kernel: [   15.923450] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 10 00:19:51 simon-desktop kernel: [   15.923993] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 22
Aug 10 00:19:51 simon-desktop kernel: [   15.924006] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKU] -> GSI 22 (level, high) -> IRQ 16
Aug 10 00:19:51 simon-desktop kernel: [   15.924023] PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug 10 00:19:51 simon-desktop kernel: [   15.924028] ohci_hcd 0000:00:02.0: OHCI Host Controller
Aug 10 00:19:51 simon-desktop kernel: [   15.924241] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Aug 10 00:19:51 simon-desktop kernel: [   15.924268] ohci_hcd 0000:00:02.0: irq 16, io mem 0xdf800000
Aug 10 00:19:51 simon-desktop kernel: [   15.963066] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
Aug 10 00:19:51 simon-desktop kernel: [   16.009741] usb usb1: configuration #1 chosen from 1 choice
Aug 10 00:19:51 simon-desktop kernel: [   16.009778] hub 1-0:1.0: USB hub found
Aug 10 00:19:51 simon-desktop kernel: [   16.009795] hub 1-0:1.0: 3 ports detected
Aug 10 00:19:51 simon-desktop kernel: [   16.110200] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKU] -> GSI 22 (level, high) -> IRQ 16
Aug 10 00:19:51 simon-desktop kernel: [   16.110224] PCI: Setting latency timer of device 0000:00:03.0 to 64
Aug 10 00:19:51 simon-desktop kernel: [   16.110229] ohci_hcd 0000:00:03.0: OHCI Host Controller
Aug 10 00:19:51 simon-desktop kernel: [   16.110262] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
Aug 10 00:19:51 simon-desktop kernel: [   16.110284] ohci_hcd 0000:00:03.0: irq 16, io mem 0xdf000000
Aug 10 00:19:51 simon-desktop kernel: [   16.168103] usb usb2: configuration #1 chosen from 1 choice
Aug 10 00:19:51 simon-desktop kernel: [   16.168148] hub 2-0:1.0: USB hub found
Aug 10 00:19:51 simon-desktop kernel: [   16.168165] hub 2-0:1.0: 3 ports detected
Aug 10 00:19:51 simon-desktop kernel: [   16.191839] Floppy drive(s): fd0 is 1.44M
Aug 10 00:19:51 simon-desktop kernel: [   16.266280] FDC 0 is a post-1991 82077
Aug 10 00:19:51 simon-desktop kernel: [   16.270682] ACPI: PCI Interrupt Link [LNKI] enabled at IRQ 21
Aug 10 00:19:51 simon-desktop kernel: [   16.270697] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKI] -> GSI 21 (level, high) -> IRQ 17
Aug 10 00:19:51 simon-desktop kernel: [   16.270706] PCI: Setting latency timer of device 0000:00:04.0 to 64
Aug 10 00:19:51 simon-desktop kernel: [   16.789740] eth0: forcedeth.c: subsystem: 01043:0c11 bound to 0000:00:04.0
Aug 10 00:19:51 simon-desktop kernel: [   16.790167] NFORCE: IDE controller at PCI slot 0000:00:09.0
Aug 10 00:19:51 simon-desktop kernel: [   16.790199] NFORCE: chipset revision 195
Aug 10 00:19:51 simon-desktop kernel: [   16.790203] NFORCE: not 100%% native mode: will probe irqs later
Aug 10 00:19:51 simon-desktop kernel: [   16.790209] NFORCE: BIOS didn't set cable bits correctly. Enabling workaround.
Aug 10 00:19:51 simon-desktop kernel: [   16.790216] NFORCE: 0000:00:09.0 (rev c3) UDMA100 controller
Aug 10 00:19:51 simon-desktop kernel: [   16.790231]     ide0: BM-DMA at 0xa800-0xa807, BIOS settings: hda:DMA, hdb:pio
Aug 10 00:19:51 simon-desktop kernel: [   16.790246]     ide1: BM-DMA at 0xa808-0xa80f, BIOS settings: hdc:DMA, hdd:DMA
Aug 10 00:19:51 simon-desktop kernel: [   16.790258] Probing IDE interface ide0...
Aug 10 00:19:51 simon-desktop kernel: [   17.077383] hda: ST3250824A, ATA DISK drive
Aug 10 00:19:51 simon-desktop kernel: [   17.749160] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Aug 10 00:19:51 simon-desktop kernel: [   17.750733] Probing IDE interface ide1...
Aug 10 00:19:51 simon-desktop kernel: [   18.484332] hdc: SAMSUNG CD-R/RW DRIVE SW-224B, ATAPI CD/DVD-ROM drive
Aug 10 00:19:51 simon-desktop kernel: [   19.267748] hdd: TSSTcorpDVD-ROM SH-D162C, ATAPI CD/DVD-ROM drive
Aug 10 00:19:51 simon-desktop kernel: [   19.324102] ide1 at 0x170-0x177,0x376 on irq 15
Aug 10 00:19:51 simon-desktop kernel: [   19.348686] SCSI subsystem initialized
Aug 10 00:19:51 simon-desktop kernel: [   19.356062] libata version 2.20 loaded.
Aug 10 00:19:51 simon-desktop kernel: [   19.377096] hda: max request size: 512KiB
Aug 10 00:19:51 simon-desktop kernel: [   19.425881] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
Aug 10 00:19:51 simon-desktop kernel: [   19.450166] hda: cache flushes supported
Aug 10 00:19:51 simon-desktop kernel: [   19.450228]  hda: hda1 hda2 hda3
Aug 10 00:19:51 simon-desktop kernel: [   19.479609] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
Aug 10 00:19:51 simon-desktop kernel: [   19.479621] Uniform CD-ROM driver Revision: 3.20
Aug 10 00:19:51 simon-desktop kernel: [   19.481275] hdd: ATAPI 48X DVD-ROM drive, 256kB Cache, UDMA(33)
Aug 10 00:19:51 simon-desktop kernel: [   19.774649] Attempting manual resume
Aug 10 00:19:51 simon-desktop kernel: [   19.774655] swsusp: Resume From Partition 3:1
Aug 10 00:19:51 simon-desktop kernel: [   19.774657] PM: Checking swsusp image.
Aug 10 00:19:51 simon-desktop kernel: [   19.774892] PM: Resume from disk failed.
Aug 10 00:19:51 simon-desktop kernel: [   19.795163] EXT3-fs: INFO: recovery required on readonly filesystem.
Aug 10 00:19:51 simon-desktop kernel: [   19.795169] EXT3-fs: write access will be enabled during recovery.
Aug 10 00:19:51 simon-desktop kernel: [   29.979411] kjournald starting.  Commit interval 5 seconds
Aug 10 00:19:51 simon-desktop kernel: [   29.979440] EXT3-fs: recovery complete.
Aug 10 00:19:51 simon-desktop kernel: [   29.996261] EXT3-fs: mounted filesystem with ordered data mode.
Aug 10 00:19:51 simon-desktop kernel: [   38.255861] NET: Registered protocol family 17
Aug 10 00:19:51 simon-desktop kernel: [   39.522893] Linux agpgart interface v0.102 (c) Dave Jones
Aug 10 00:19:51 simon-desktop kernel: [   39.541922] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 10 00:19:51 simon-desktop kernel: [   39.544203] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 10 00:19:51 simon-desktop kernel: [   39.769700] agpgart: Detected NVIDIA nForce chipset
Aug 10 00:19:51 simon-desktop kernel: [   39.774421] agpgart: AGP aperture is 64M @ 0xf8000000
Aug 10 00:19:51 simon-desktop kernel: [   40.104562] input: PC Speaker as /class/input/input2
Aug 10 00:19:51 simon-desktop kernel: [   40.189984] parport: PnPBIOS parport detected.
Aug 10 00:19:51 simon-desktop kernel: [   40.190049] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Aug 10 00:19:51 simon-desktop kernel: [   40.322009] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
Aug 10 00:19:51 simon-desktop kernel: [   40.642875] PCI: Enabling device 0000:00:06.0 (0005 -> 0007)
Aug 10 00:19:51 simon-desktop kernel: [   40.643484] ACPI: PCI Interrupt Link [LNKK] enabled at IRQ 20
Aug 10 00:19:51 simon-desktop kernel: [   40.643496] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKK] -> GSI 20 (level, high) -> IRQ 18
Aug 10 00:19:51 simon-desktop kernel: [   40.643536] PCI: Setting latency timer of device 0000:00:06.0 to 64
Aug 10 00:19:51 simon-desktop kernel: [   40.959438] intel8x0_measure_ac97_clock: measured 52699 usecs
Aug 10 00:19:51 simon-desktop kernel: [   40.959443] intel8x0: clocking to 47429
Aug 10 00:19:51 simon-desktop kernel: [   41.114527] fuse init (API version 7.8)
Aug 10 00:19:51 simon-desktop kernel: [   41.139625] lp0: using parport0 (interrupt-driven).
Aug 10 00:19:51 simon-desktop kernel: [   41.185549] Adding 1052216k swap on /dev/disk/by-uuid/1980a34d-0620-408f-ad3e-4d23194308d7.  Priority:-1 extents:1 across:1052216k
Aug 10 00:19:51 simon-desktop kernel: [   41.298901] EXT3 FS on hda2, internal journal
Aug 10 00:19:51 simon-desktop kernel: [   41.483080] NET: Registered protocol family 10
Aug 10 00:19:51 simon-desktop kernel: [   41.483206] lo: Disabled Privacy Extensions
Aug 10 00:19:51 simon-desktop kernel: [   41.958362] kjournald starting.  Commit interval 5 seconds
Aug 10 00:19:51 simon-desktop kernel: [   41.958572] EXT3 FS on hda3, internal journal
Aug 10 00:19:51 simon-desktop kernel: [   41.958579] EXT3-fs: mounted filesystem with ordered data mode.
Aug 10 00:19:51 simon-desktop kernel: [   47.420239] Using specific hotkey driver
Aug 10 00:19:51 simon-desktop kernel: [   47.495247] No dock devices found.
Aug 10 00:19:51 simon-desktop kernel: [   47.570418] ibm_acpi: ec object not found
Aug 10 00:19:51 simon-desktop kernel: [   47.742677] input: Power Button (FF) as /class/input/input4
Aug 10 00:19:51 simon-desktop kernel: [   47.748868] ACPI: Power Button (FF) [PWRF]
Aug 10 00:19:51 simon-desktop kernel: [   47.790108] input: Power Button (CM) as /class/input/input5
Aug 10 00:19:51 simon-desktop kernel: [   47.796327] ACPI: Power Button (CM) [PWRB]
Aug 10 00:19:51 simon-desktop kernel: [   47.840768] pcc_acpi: loading...
Aug 10 00:19:55 simon-desktop dhcdbd: Started up.
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^Istarting... 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'forcedeth'. 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Successfully dropped root privileges.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: avahi-daemon 0.6.17 starting up.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Successfully called chroot().
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Successfully dropped remaining capabilities.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: No service found in /etc/avahi/services.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.1.3.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: New relevant interface eth0.IPv4 for mDNS.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Network interface enumeration completed.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Registering new address record for fe80::2e0:18ff:fe79:cc99 on eth0.*.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Registering new address record for 10.1.1.3 on eth0.IPv4.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IDeactivating device eth0. 
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Withdrawing address record for 10.1.1.3 on eth0.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.1.1.3.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 10 00:19:55 simon-desktop avahi-daemon[4695]: Withdrawing address record for fe80::2e0:18ff:fe79:cc99 on eth0.
Aug 10 00:19:55 simon-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Aug 10 00:19:55 simon-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IWill activate connection 'eth0'. 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IDevice eth0 activation scheduled... 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IActivation (eth0) started... 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Aug 10 00:19:55 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Aug 10 00:19:56 simon-desktop NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Aug 10 00:19:56 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Aug 10 00:19:56 simon-desktop NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Aug 10 00:19:56 simon-desktop kernel: [   53.519460] ppdev: user-space parallel port driver
Aug 10 00:19:56 simon-desktop kernel: [   53.526406] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Aug 10 00:19:56 simon-desktop kernel: [   53.536200] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
Aug 10 00:19:56 simon-desktop kernel: [   53.536625] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
Aug 10 00:19:57 simon-desktop kernel: [   53.819173] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 19
Aug 10 00:19:57 simon-desktop kernel: [   53.819189] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKE] -> GSI 19 (level, high) -> IRQ 19
Aug 10 00:19:57 simon-desktop hpiod: 1.7.3 accepting connections at 2208... 
Aug 10 00:19:57 simon-desktop NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Aug 10 00:20:00 simon-desktop kernel: [   57.183635] [fglrx] Internal AGP support requested, but kernel AGP support active.
Aug 10 00:20:00 simon-desktop kernel: [   57.183645] [fglrx] Have to use kernel AGP support to avoid conflicts.
Aug 10 00:20:00 simon-desktop kernel: [   57.183651] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Aug 10 00:20:00 simon-desktop kernel: [   57.183779] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Aug 10 00:20:00 simon-desktop kernel: [   57.183796] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Aug 10 00:20:00 simon-desktop kernel: [   57.183844] agpgart: Putting AGP V2 device at 0000:02:00.0 into 4x mode
Aug 10 00:20:00 simon-desktop kernel: [   57.183859] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Aug 10 00:20:00 simon-desktop kernel: [   57.195412] [fglrx] total      GART = 67108864
Aug 10 00:20:00 simon-desktop kernel: [   57.195419] [fglrx] free       GART = 51113984
Aug 10 00:20:00 simon-desktop kernel: [   57.195422] [fglrx] max single GART = 51113984
Aug 10 00:20:00 simon-desktop kernel: [   57.195425] [fglrx] total      LFB  = 134217728
Aug 10 00:20:00 simon-desktop kernel: [   57.195427] [fglrx] free       LFB  = 116387840
Aug 10 00:20:00 simon-desktop kernel: [   57.195430] [fglrx] max single LFB  = 116387840
Aug 10 00:20:00 simon-desktop kernel: [   57.195432] [fglrx] total      Inv  = 0
Aug 10 00:20:00 simon-desktop kernel: [   57.195434] [fglrx] free       Inv  = 0
Aug 10 00:20:00 simon-desktop kernel: [   57.195436] [fglrx] max single Inv  = 0
Aug 10 00:20:00 simon-desktop kernel: [   57.195438] [fglrx] total      TIM  = 0
Aug 10 00:20:01 simon-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Aug 10 00:20:01 simon-desktop dhclient: DHCPACK from 10.1.1.1
Aug 10 00:20:01 simon-desktop dhclient: bound to 10.1.1.3 -- renewal in 1559 seconds.
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Aug 10 00:20:01 simon-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Aug 10 00:20:01 simon-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug 10 00:20:01 simon-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^I  address 10.1.1.3 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^I  netmask 255.0.0.0 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^I  broadcast 10.255.255.255 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^I  gateway 10.1.1.1 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^I  nameserver 10.1.1.1 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^I  hostname 'simon-desktop' 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Aug 10 00:20:01 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Aug 10 00:20:01 simon-desktop avahi-daemon[4695]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.1.3.
Aug 10 00:20:01 simon-desktop avahi-daemon[4695]: IP_ADD_MEMBERSHIP failed: No such device
Aug 10 00:20:01 simon-desktop avahi-daemon[4695]: Registering new address record for 10.1.1.3 on eth0.IPv4.
Aug 10 00:20:01 simon-desktop avahi-daemon[4695]: Withdrawing address record for 10.1.1.3 on eth0.
Aug 10 00:20:01 simon-desktop avahi-daemon[4695]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.1.3.
Aug 10 00:20:01 simon-desktop avahi-daemon[4695]: New relevant interface eth0.IPv4 for mDNS.
Aug 10 00:20:01 simon-desktop avahi-daemon[4695]: Registering new address record for 10.1.1.3 on eth0.IPv4.
Aug 10 00:20:01 simon-desktop kernel: [   57.746888] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 10 00:20:01 simon-desktop kernel: [   57.746896] apm: overridden by ACPI.
Aug 10 00:20:01 simon-desktop hcid[4999]: Bluetooth HCI daemon
Aug 10 00:20:01 simon-desktop kernel: [   58.120789] Bluetooth: Core ver 2.11
Aug 10 00:20:01 simon-desktop kernel: [   58.120888] NET: Registered protocol family 31
Aug 10 00:20:01 simon-desktop kernel: [   58.120891] Bluetooth: HCI device and connection manager initialized
Aug 10 00:20:01 simon-desktop kernel: [   58.120897] Bluetooth: HCI socket layer initialized
Aug 10 00:20:01 simon-desktop NetworkManager: <debug info>^I[1186662001.589035] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 10 00:20:01 simon-desktop hcid[4999]: Starting SDP server
Aug 10 00:20:01 simon-desktop kernel: [   58.192634] Bluetooth: L2CAP ver 2.8
Aug 10 00:20:01 simon-desktop kernel: [   58.192641] Bluetooth: L2CAP socket layer initialized
Aug 10 00:20:01 simon-desktop kernel: [   58.377703] Bluetooth: RFCOMM socket layer initialized
Aug 10 00:20:01 simon-desktop kernel: [   58.377729] Bluetooth: RFCOMM TTY layer initialized
Aug 10 00:20:01 simon-desktop kernel: [   58.377731] Bluetooth: RFCOMM ver 1.8
Aug 10 00:20:01 simon-desktop anacron[5039]: Anacron 2.3 started on 2007-08-10
Aug 10 00:20:01 simon-desktop anacron[5039]: Will run job `cron.daily' in 5 min.
Aug 10 00:20:01 simon-desktop anacron[5039]: Jobs will be executed sequentially
Aug 10 00:20:01 simon-desktop /usr/sbin/cron[5066]: (CRON) INFO (pidfile fd = 3)
Aug 10 00:20:01 simon-desktop /usr/sbin/cron[5067]: (CRON) STARTUP (fork ok)
Aug 10 00:20:01 simon-desktop /usr/sbin/cron[5067]: (CRON) INFO (Running @reboot jobs)
Aug 10 00:20:02 simon-desktop NetworkManager: <information>^IClearing nscd hosts cache. 
Aug 10 00:20:02 simon-desktop NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Aug 10 00:20:02 simon-desktop NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Aug 10 00:20:02 simon-desktop NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Aug 10 00:20:02 simon-desktop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 10 00:20:03 simon-desktop avahi-daemon[4695]: Registering new address record for fe80::2e0:18ff:fe79:cc99 on eth0.*.
Aug 10 00:20:12 simon-desktop kernel: [   69.054472] eth0: no IPv6 routers present
Aug  9 12:20:04 simon-desktop ntpdate[5187]: step time server 82.211.81.145 offset -43208.979527 sec
Aug  9 12:20:06 simon-desktop gconfd (simon-5236): starting (version 2.18.0.1), pid 5236 user 'simon'
Aug  9 12:20:06 simon-desktop gconfd (simon-5236): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  9 12:20:06 simon-desktop gconfd (simon-5236): Resolved address "xml:readwrite:/home/simon/.gconf" to a writable configuration source at position 1
Aug  9 12:20:06 simon-desktop gconfd (simon-5236): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  9 12:20:06 simon-desktop gconfd (simon-5236): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  9 12:20:06 simon-desktop gconfd (simon-5236): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  9 12:20:12 simon-desktop gconfd (simon-5236): Resolved address "xml:readwrite:/home/simon/.gconf" to a writable configuration source at position 0
Aug  9 12:20:20 simon-desktop gconfd (simon-5236): Failed to send buffer
```

Again, any help would be so greatly appreciated!!!

---

### Post by balloons on 2007-08-08
appears your running the ati proprietary driver. i'm guessing the live cd works because it's using the vga (non-accelerated driver) this sounds like a driver problem. if you reinstall and don't enable ati driver (use open source one, or vga) and see if it still occurs.

---

### Post by Slimo on 2007-08-09
I installed the ati open source driver and so far no crashes - only about 3 hours of run time but seems to be working much better compared to before.

The first time I rebooted after installing the open source driver the Ubuntu boot screen (with the loading bar) was a bit jumpy, ended up showing 2 bars on the screen (in a sort of freezing, moving around way) and I had to reboot.  Apart from that doesn't seem to be any problems.

I won't mark this thread as solved until I get a few more hours run time but so far so good!!  Thanks so much everyone for all your help and advice!

---

### Post by balloons on 2007-08-09
I'm glad to hear it. Whether or not it turns out to be the driver - this is why proprietery drivers are not a good thing - who can fix a problem like this without access to the source? if the vendor doesn't want to release source, then at least release specs. ATI's linux driver is one of the worst as far as graphics go. Although, they seem committed to fixing it. Still specs would be better.

---

### Post by Slimo on 2007-08-12
I've had a few days of computer use now and the only crashes have been when the screensaver has come up - slightly annoying (may be related to power management settings?  have had trouble with this before) but the open source drivers make general comp use much better than before!

Thanks everyone for your help - and if you have any solutions to the power/screensaver issue that would be great  :-)

---

### Post by juice19 on 2007-08-13
I have the same problem I am pretty sure, I have ATI Radeon 9100IGP  mobility.


How do I switch the drivers in Ubuntu,  I know how to do this in windows but Ubuntu is still new to me.  Thanks for the help.

---

### Post by Slimo on 2007-08-13
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

This is the guide I used to install the open source ati driver.  Hope it helps!

---

### Post by Slimo on 2007-08-30
Thanks to all for your help and guidance.
The problem has been solved - I have had a lot of computer problems lately and buy getting a new NVidia card and a larger power supply my system is running perfectly now.
I think the crashing was probably caused by my old ATI card which had a faulty fan so the card was overheating and crashing constantly.

Thanks again!!  My faith in Ubuntu is well and truly restored

---

