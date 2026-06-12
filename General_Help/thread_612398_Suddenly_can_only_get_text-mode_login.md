---
title: "Suddenly can only get text-mode login"
date: 2007-11-13
forum: General Help
---

### Post by dadawan on 2007-11-13
I had already made a posting about this in Installation and Upgrades before I realized it was probably not the right forum, since I had already installed....  Sorry about that.

I just installed Ubuntu this week on my second drive, it seemed to be better than Windows in every way except MP3's.

BUT

Today there were some updates which asked to be installed. I agreed. One of them was XFree86 or something. Anyway after the upgrade completed no programs would come up. No error message, and I could switch desktops, but nothing would come up. So I rebooted, only to come up into a text mode logon. There is a message at the top of the screening saying:

kinit: name_to_dev_t

blah blah some long uuid number

kinit: trying to resume from ..... blah blah
Kinit: no resume image, doing normal boot.


I don't know if that is related or not. But I'll bet that update gronked my X11 hoogie, and I have no clue what to do. There is nothing unusual about my system that I can think of. I've got an NVidia 7600GS, and I was using the 'Restricted' driver, whatever that means.

After reading some other posts I tried startx.   It goes into graphics mode for a second, then back out to the text screen.

I get this message:

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing

Then nothing....

Here is the whole log file from /var/logs/Xorg.0.log

Thanks for any assistance...
```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Bauer 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 13 21:02:18 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation G70 [GeForce 7600 GS]"
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
(II) Loader magic: 0x81ea440
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1028,01d2 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1028,01d2 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01d2 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01d2 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01d2 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1028,01d2 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01d2 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1028,01d2 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1028,01d2 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01d2 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0392 card 10de,033e rev a1 class 03,00,00 hdr 00
(II) PCI: 03:02:0: chip 9710,9835 card 1000,0012 rev 01 class 07,80,00 hdr 00
(II) PCI: 03:03:0: chip 1106,3044 card 0010,0001 rev 46 class 0c,00,10 hdr 00
(II) PCI: 03:08:0: chip 8086,27dc card 1028,01ab rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xed000000 - 0xefefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xecf00000 - 0xecffffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xece00000 - 0xecefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xed000000/24, 0xd0000000/28, 0xee000000/24, I/O @ 0xdc80/7, BIOS @ 0xefe00000/17
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
	[0] -1	0	0xeceff000 - 0xecefffff (0x1000) MX[B]
	[1] -1	0	0xecefe800 - 0xecefefff (0x800) MX[B]
	[2] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[5] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[6] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[10] -1	0	0x0000cc80 - 0x0000ccff (0x80) IX[B]
	[11] -1	0	0x0000cc30 - 0x0000cc3f (0x10) IX[B]
	[12] -1	0	0x0000cc28 - 0x0000cc2f (0x8) IX[B]
	[13] -1	0	0x0000cc20 - 0x0000cc27 (0x8) IX[B]
	[14] -1	0	0x0000cc18 - 0x0000cc1f (0x8) IX[B]
	[15] -1	0	0x0000cc10 - 0x0000cc17 (0x8) IX[B]
	[16] -1	0	0x0000cc08 - 0x0000cc0f (0x8) IX[B]
	[17] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[18] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[29] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[30] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[31] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[32] -1	0	0x0000dc80 - 0x0000dcff (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xeceff000 - 0xecefffff (0x1000) MX[B]
	[1] -1	0	0xecefe800 - 0xecefefff (0x800) MX[B]
	[2] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[5] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[6] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[10] -1	0	0x0000cc80 - 0x0000ccff (0x80) IX[B]
	[11] -1	0	0x0000cc30 - 0x0000cc3f (0x10) IX[B]
	[12] -1	0	0x0000cc28 - 0x0000cc2f (0x8) IX[B]
	[13] -1	0	0x0000cc20 - 0x0000cc27 (0x8) IX[B]
	[14] -1	0	0x0000cc18 - 0x0000cc1f (0x8) IX[B]
	[15] -1	0	0x0000cc10 - 0x0000cc17 (0x8) IX[B]
	[16] -1	0	0x0000cc08 - 0x0000cc0f (0x8) IX[B]
	[17] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[18] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[29] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[30] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[31] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[32] -1	0	0x0000dc80 - 0x0000dcff (0x80) IX[B](B)
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
	[4] -1	0	0xeceff000 - 0xecefffff (0x1000) MX[B]
	[5] -1	0	0xecefe800 - 0xecefefff (0x800) MX[B]
	[6] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[9] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[10] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[16] -1	0	0x0000cc80 - 0x0000ccff (0x80) IX[B]
	[17] -1	0	0x0000cc30 - 0x0000cc3f (0x10) IX[B]
	[18] -1	0	0x0000cc28 - 0x0000cc2f (0x8) IX[B]
	[19] -1	0	0x0000cc20 - 0x0000cc27 (0x8) IX[B]
	[20] -1	0	0x0000cc18 - 0x0000cc1f (0x8) IX[B]
	[21] -1	0	0x0000cc10 - 0x0000cc17 (0x8) IX[B]
	[22] -1	0	0x0000cc08 - 0x0000cc0f (0x8) IX[B]
	[23] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[24] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[25] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[26] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[27] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[32] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[35] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[36] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[37] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[38] -1	0	0x0000dc80 - 0x0000dcff (0x80) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xeceff000 - 0xecefffff (0x1000) MX[B]
	[5] -1	0	0xecefe800 - 0xecefefff (0x800) MX[B]
	[6] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[9] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[10] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[16] -1	0	0x0000cc80 - 0x0000ccff (0x80) IX[B]
	[17] -1	0	0x0000cc30 - 0x0000cc3f (0x10) IX[B]
	[18] -1	0	0x0000cc28 - 0x0000cc2f (0x8) IX[B]
	[19] -1	0	0x0000cc20 - 0x0000cc27 (0x8) IX[B]
	[20] -1	0	0x0000cc18 - 0x0000cc1f (0x8) IX[B]
	[21] -1	0	0x0000cc10 - 0x0000cc17 (0x8) IX[B]
	[22] -1	0	0x0000cc08 - 0x0000cc0f (0x8) IX[B]
	[23] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[24] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[25] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[26] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[27] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[32] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[35] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[36] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[37] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[38] -1	0	0x0000dc80 - 0x0000dcff (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xeceff000 - 0xecefffff (0x1000) MX[B]
	[5] -1	0	0xecefe800 - 0xecefefff (0x800) MX[B]
	[6] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[9] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[10] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[19] -1	0	0x0000cc80 - 0x0000ccff (0x80) IX[B]
	[20] -1	0	0x0000cc30 - 0x0000cc3f (0x10) IX[B]
	[21] -1	0	0x0000cc28 - 0x0000cc2f (0x8) IX[B]
	[22] -1	0	0x0000cc20 - 0x0000cc27 (0x8) IX[B]
	[23] -1	0	0x0000cc18 - 0x0000cc1f (0x8) IX[B]
	[24] -1	0	0x0000cc10 - 0x0000cc17 (0x8) IX[B]
	[25] -1	0	0x0000cc08 - 0x0000cc0f (0x8) IX[B]
	[26] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[27] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[28] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[29] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[30] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[34] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[35] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[38] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[39] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[40] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[41] -1	0	0x0000dc80 - 0x0000dcff (0x80) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.16.02
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     DELL E196FP (CRT-0)
(--) NVIDIA(0): DELL E196FP (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xee000000 - 0xeeffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xed000000 - 0xedffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xeceff000 - 0xecefffff (0x1000) MX[B]
	[8] -1	0	0xecefe800 - 0xecefefff (0x800) MX[B]
	[9] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[10] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[11] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[12] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[13] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] 0	0	0x0000dc80 - 0x0000dcff (0x80) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[23] -1	0	0x0000cc80 - 0x0000ccff (0x80) IX[B]
	[24] -1	0	0x0000cc30 - 0x0000cc3f (0x10) IX[B]
	[25] -1	0	0x0000cc28 - 0x0000cc2f (0x8) IX[B]
	[26] -1	0	0x0000cc20 - 0x0000cc27 (0x8) IX[B]
	[27] -1	0	0x0000cc18 - 0x0000cc1f (0x8) IX[B]
	[28] -1	0	0x0000cc10 - 0x0000cc17 (0x8) IX[B]
	[29] -1	0	0x0000cc08 - 0x0000cc0f (0x8) IX[B]
	[30] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[31] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[32] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[33] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[34] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[35] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[36] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[37] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[38] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[39] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[41] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[42] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[43] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[44] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[45] -1	0	0x0000dc80 - 0x0000dcff (0x80) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
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
(II) Initializing extension GLX
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
```

---

