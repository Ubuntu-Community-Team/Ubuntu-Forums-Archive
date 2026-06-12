---
title: "Xlib CLX missing error"
date: 2005-03-26
forum: General Help
---

### Post by pvoce on 2005-03-26
After installing nvidia-glx drivers, I receive the following error:)

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Can't create window.  Exiting.

The "load dri" and "load glx" statments in the xorg.conf are uncommented, so they should be loading.

Any ideas?

PV

---

### Post by alastair on 2005-03-26
If I recall, the NVidia drivers do NOT want "dri" loaded - so comment that line.

There should be a README installed for the NVidia drivers e.g. somewhere like :

/usr/share/doc/NVidia*

Take a look and check.

If problems persist - show :

/etc/X11/xorg.conf
/var/log/Xorg.0.log

---

### Post by pvoce on 2005-03-26
Thanks for the reply:)

2 initial culprits:

1:  I had "load dri" uncommented,

2: "nv" instead of "nvidia"...please note, this has been kept as "nvidia" so much of late I didnt bother to check:)

Now, however, I receive the "screens found but none have a usable configuration" error.

I rememeber find the missing info to rememdy that somewhere, but I cant seem to google it, nor find it at nvnews and other usual outlets.

FOr right now, I have the device listed as "nv", so as to use the desktop, but if you can remember some other info, I'd be more than happy:)

Here are the outputs of both xorg.conf and the log:

Section "Files"
 FontPath "unix/:7100"   # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
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
 #Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "vbe"
EndSection

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver  "keyboard"
 Option  "CoreKeyboard"
 Option  "XkbRules" "xorg"
 Option  "XkbModel" "pc104"
 Option  "XkbLayout" "us"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection

Section "Device"
 Identifier "NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
 Driver  "nv"  (I know this should be "nvidia", but X does not start)
 BusID  "PCI:1:0:0"
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 Option  "DPMS"
 HorizSync 30-70
 VertRefresh 50-160
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
 Monitor  "Generic Monitor"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
EndSection

Section "DRI"
 Mode 0666
EndSection


X log to follow....

---

### Post by pvoce on 2005-03-26
Xorg.0.log:

X Window System Version 6.8.2 (Ubuntu 6.8.2-5.1 20050317074038 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 i686 [ELF] 
Current Operating System: Linux patrick 2.6.10-5-386 #1 Thu Mar 24 14:43:04 GMT 2005 i686
Build Date: 17 March 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Thu Mar 24 14:43:04 GMT 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 26 21:06:19 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc104"
(**) XKB: model: "pc104"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3116 card 1106,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b091 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1106,3104 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1106,4161 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1106,0102 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0150 card 1102,1047 rev a3 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdde00000 - 0xdfefffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xcdd00000 - 0xddcfffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV15 [GeForce2 GTS/Pro] rev 163, Mem @ 0xde000000/24, 0xd0000000/27, BIOS @ 0xdfef0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdffffe00 - 0xdffffeff (0x100) MX[B]
	[1] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[9] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffffe00 - 0xdffffeff (0x100) MX[B]
	[1] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[9] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdffffe00 - 0xdffffeff (0x100) MX[B]
	[6] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.6629
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.6629
	Module class: XFree86 Video Driver
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-6629  Wed Nov  3 13:14:07 PST 2004
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdffffe00 - 0xdffffeff (0x100) MX[B]
	[6] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdffffe00 - 0xdffffeff (0x100) MX[B]
	[6] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xDE000000
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by alastair on 2005-03-27
[QUOTE=pvoce]
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
[/QUOTE]

Well this time it is not loading/initialising the nvidia driver. Not sure what this is but I suspect a "device" problem i.e. the driver wants devices like :

```

/dev/nvidia0
/dev/nvidiactl

```

See the nvidia README. Are they there? This /might/ be the problem.

If not, to create them we might need to do something like the following - because Hoary uses "udev" (dynamic devices) :

Edit : /etc/udev/links.conf

Add :

```

M nvidia0       c 195 0
M nvidiactl     c 195 255

```

I am not sure if this is the best way to do this. Probably best to reboot after and check these devices exist.

---

### Post by pvoce on 2005-03-27
I added the statements, but that did not help either.

I went ahead and used the nvidia-installer pkg and got it to work.  Please note for others who may run into this:  The source headers MUST be from the the EXACT kernel version.

2.6.10 does NOT work by itself.  The installer (and this is nvidia's doing) wants 2.6.10-5-386 or whichever version kernel you are using.  Thanks for help though:)

---

