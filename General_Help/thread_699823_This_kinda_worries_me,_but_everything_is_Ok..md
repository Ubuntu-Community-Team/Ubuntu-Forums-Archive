---
title: "This kinda worries me, but everything is Ok."
date: 2008-02-17
forum: General Help
---

### Post by LiNuXxToOthEMaX on 2008-02-17
So I watching the KDE 4.0 Keynote on Google, and while I was doing that I was just messing around with my cube, and I exited the video, like minimized, and then all of a sudden it went to a black screen, kinda like the one right before it boots up, and took me back to the login screen. Any ideas? Am I done for? haha, should I be worried though?

---

### Post by LiNuXxToOthEMaX on 2008-02-17
bump oh and it hasnt done it anymore, just wondering? sorry for the bump

---

### Post by kool_kat_os on 2008-02-17
EDIT: Forgot to read the second post . srry

---

### Post by LiNuXxToOthEMaX on 2008-02-17
> **kool_kat_os said:**
> EDIT: Forgot to read the second post . srry

Np, just wanting to see what I should do :(

---

### Post by xeth_delta on 2008-02-17
> **LiNuXxToOthEMaX said:**
> Np, just wanting to see what I should do :(

To me it sounds like an X11 server crash. You may want to look at the logs (/var/log/Xorg.0.log), if you are curious. The lines describing errors start with EE.

---

### Post by LiNuXxToOthEMaX on 2008-02-17
> **xeth_delta said:**
> To me it sounds like an X11 server crash. You may want to look at the logs (/var/log/Xorg.0.log), if you are curious. The lines describing errors start with EE.

does this mean, i'm screwed haha

---

### Post by xeth_delta on 2008-02-17
> **LiNuXxToOthEMaX said:**
> does this mean, i'm screwed haha

I don't think so. Isn't your system working properly now?

---

### Post by LiNuXxToOthEMaX on 2008-02-17
> **xeth_delta said:**
> I don't think so. Isn't your system working properly now?

ya, how would i check these logs

---

### Post by xeth_delta on 2008-02-17
> **LiNuXxToOthEMaX said:**
> ya, how would i check these logs

Use your favourite text editor and open the file I mentioned. You can do that from the command line, too:
```
nano /var/log/Xorg.0.log
```
or, if you want to use a GUI based text editor, for Gnome:
```
gedit /var/log/Xorg.0.log
```
or, if you use KDE
```
kate /var/log/Xorg.0.log
```

---

### Post by LiNuXxToOthEMaX on 2008-02-17
> **LiNuXxToOthEMaX said:**
> ya, how would i check these logs

sorry about that heres my log

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux codename-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 17 16:20:00 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV40 [GeForce 6800 GT]"
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
(II) Loader magic: 0x81e9800
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
(II) PCI: 00:00:0: chip 8086,2560 card 8086,2560 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 107b,2009 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 107b,2009 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 107b,2009 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 107b,2009 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 107b,2009 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 107b,2009 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 107b,2009 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0045 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,4320 card 1737,0015 rev 03 class 02,80,00 hdr 00
(II) PCI: 02:02:0: chip 14e4,4212 card 14e4,0002 rev 00 class 07,03,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1039 card 107b,2009 rev 82 class 02,00,00 hdr 00
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
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa900000 - 0xfe9fffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd2600000 - 0xf26fffff (0x20100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0206 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf2700000 - 0xf27fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV40 [GeForce 6800 GT] rev 161, Mem @ 0xfd000000/24, 0xe0000000/28, 0xfc000000/24, BIOS @ 0xfe9e0000/17
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
(II) PCI Memory resource overlap reduced 0xf4000000 from 0xf7ffffff to 0xf3ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[1] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[2] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[3] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[4] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[5] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[7] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[8] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000d880 - 0x0000d8bf (0x40) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[14] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[23] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[1] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[2] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[3] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[4] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[5] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[7] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[8] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000d880 - 0x0000d8bf (0x40) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[14] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[23] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
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
	[4] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[5] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[7] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[8] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[12] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d880 - 0x0000d8bf (0x40) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[29] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
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
	[4] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[5] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[7] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[8] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[12] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d880 - 0x0000d8bf (0x40) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[29] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[5] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[7] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[8] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[12] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000d880 - 0x0000d8bf (0x40) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[32] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 GT (NV40) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.40.02.15.05
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 GT at PCI:1:0:0:
(--) NVIDIA(0):     LKM (CRT-1)
(--) NVIDIA(0): LKM (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (101, 108); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[8] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[9] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[10] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[11] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[12] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[13] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[14] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[15] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[16] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000d880 - 0x0000d8bf (0x40) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[26] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[35] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[36] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
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
SetClientVersion: 0 9
```

not sure, but if any help ill paypal 10 bucks thanks!

---

### Post by xeth_delta on 2008-02-17
Hehe, thanks for the offer, but we are here to offer help voluntarily, it is an altruistic action :) So, no need for the paypal offer :)

Now, to the log, I am not able to see any error. Crashes can happen from time to time, even if it is on a rather rare basis. It is possible that some program crashed the X server, and hence you were sent back to the log-in screen.

You could also try having a look at /var/log/Xorg.0.log.old

---

### Post by LiNuXxToOthEMaX on 2008-02-17
> **xeth_delta said:**
> Hehe, thanks for the offer, but we are here to offer help voluntarely, it is an altruistic action :) So, no need for the paypal offer :)

Now, to the log, I am not able to see any error. Crashes can happen from time to time, even if it is on a rather rare basis. It is possible that some program crashed the X server, and hence you were sent back to the log-in screen.

yeah, it went to a black screen, then it said ubuntu log in, and i logged in, but I rebooted, and havnt had any problems yet

---

### Post by xeth_delta on 2008-02-17
> **LiNuXxToOthEMaX said:**
> yeah, it went to a black screen, then it said ubuntu log in, and i logged in, but I rebooted, and havnt had any problems yet

What drivers are you using? The proprietary or the open source ones?
For now I wouldn't worry too much about the problem, but maybe someone else with a different point of view will post later.
If the problem can be repeated, the first thing to check would be to see if there is a misconfiguration in X server.

---

### Post by LiNuXxToOthEMaX on 2008-02-17
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux codename-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 17 15:30:43 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV40 [GeForce 6800 GT]"
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
(II) Loader magic: 0x81e9800
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
(II) PCI: 00:00:0: chip 8086,2560 card 8086,2560 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 107b,2009 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 107b,2009 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 107b,2009 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 107b,2009 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 107b,2009 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 107b,2009 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 107b,2009 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0045 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,4320 card 1737,0015 rev 03 class 02,80,00 hdr 00
(II) PCI: 02:02:0: chip 14e4,4212 card 14e4,0002 rev 00 class 07,03,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1039 card 107b,2009 rev 82 class 02,00,00 hdr 00

cut about half of it out, but anything interesting?

---

### Post by xeth_delta on 2008-02-17
I cannot see any error message in there. Try doing the same things you were when the crash happened, see if it can be repeated.

---

### Post by LiNuXxToOthEMaX on 2008-02-17
> **xeth_delta said:**
> I cannot see any error message in there. Try doing the same things you were when the crash happened, see if it can be repeated.

tried watching the same video, did the cube thing, closed it, opened it only thing i ended up doing was freezing firefox, not a major crash or w.e

---

### Post by LiNuXxToOthEMaX on 2008-02-17
> **LiNuXxToOthEMaX said:**
> tried watching the same video, did the cube thing, closed it, opened it only thing i ended up doing was freezing firefox, not a major crash or w.e

but yeah, im still running fine so iunno

---

### Post by xeth_delta on 2008-02-17
> **LiNuXxToOthEMaX said:**
> but yeah, im still running fine so iunno

Right now I'm out of ideas, let's wait and see. Perhaps another user will post some more thoughts in the meantime.

Good luck!

---

### Post by Crafty Kisses on 2008-02-18
> **LiNuXxToOthEMaX said:**
> So I watching the KDE 4.0 Keynote on Google, and while I was doing that I was just messing around with my cube, and I exited the video, like minimized, and then all of a sudden it went to a black screen, kinda like the one right before it boots up, and took me back to the login screen. Any ideas? Am I done for? haha, should I be worried though?

Hmmm, anyone got any more info on this? Sounds interesting. I'd like to help, but this has also happened to me, and I'm stumped.

---

