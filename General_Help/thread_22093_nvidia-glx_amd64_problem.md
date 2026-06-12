---
title: "nvidia-glx amd64 problem"
date: 2005-03-25
forum: General Help
---

### Post by henla464 on 2005-03-25
Hello

After I upgraded to Hoary I can't get the binary xorg nvidia driver to work.

Trying to fix it I did the following (to no avail)
Uninstalled nvidia-glx:
```
sudo apt-get remove nvidia-glx
sudo apt-get remove nvidia-settings
``` 

and then rebooted and installed nvidia-glx again using the commands:

```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
``` 


but since I have altered my xorg.conf file it complaines. I changed it back the way I believe it was from the beginning (adding: Load "dri" and removing: Load "glx"). I then ran:

```
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
sudo nvidia-glx-config enable
``` 

The config file now looks like this:

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
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
``` 


I now restarted. When the xserver starts I se the nvidia logo appear for a second before it crashes. This is the content of the log file (see next post):

---

### Post by henla464 on 2005-03-25
(continue from last post)

```
( == )  Keyboard :  CustomKeycode disabled
( ** )  |-->Input Device "Configured Mouse"
( WW )  The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
( WW )  The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
( WW )  `fonts.dir' not found ( or not valid )  in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	( Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID" ) .
( ** )  FontPath set to "unix/ : 7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/ : unscaled,/usr/lib/X11/fonts/75dpi/ : unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
( == )  RgbPath set to "/usr/X11R6/lib/X11/rgb"
( == )  ModulePath set to "/usr/X11R6/lib/modules"
( WW )  Open APM failed ( /dev/apm_bios )  ( No such file or directory ) 
( II )  Module ABI versions : 
	X.Org ANSI C Emulation :  0.2
	X.Org Video Driver :  0.7
	X.Org XInput driver  :  0.4
	X.Org Server Extension  :  0.2
	X.Org Font Renderer  :  0.4
( II )  Loader running on linux
( II )  LoadModule :  "bitmap"
( II )  Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
( II )  Module bitmap :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class :  X.Org Font Renderer
	ABI class :  X.Org Font Renderer, version 0.4
( II )  Loading font Bitmap
( II )  LoadModule :  "pcidata"
( II )  Loading /usr/X11R6/lib/modules/libpcidata.a
( II )  Module pcidata :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class :  X.Org Video Driver, version 0.7
( -- )  using VT number 7

( II )  PCI :  PCI scan ( all values are in hex ) 
( II )  PCI :  00 : 00 : 0 :  chip 10de,00d1 card 1297,a550 rev a4 class 06,00,00 hdr 00
( II )  PCI :  00 : 01 : 0 :  chip 10de,00d0 card 1297,a550 rev a6 class 06,01,00 hdr 80
( II )  PCI :  00 : 01 : 1 :  chip 10de,00d4 card 1297,a550 rev a4 class 0c,05,00 hdr 80
( II )  PCI :  00 : 02 : 0 :  chip 10de,00d7 card 1297,a550 rev a5 class 0c,03,10 hdr 80
( II )  PCI :  00 : 02 : 1 :  chip 10de,00d7 card 1297,a550 rev a5 class 0c,03,10 hdr 80
( II )  PCI :  00 : 02 : 2 :  chip 10de,00d8 card 1297,a550 rev a2 class 0c,03,20 hdr 80
( II )  PCI :  00 : 05 : 0 :  chip 10de,00d6 card 1297,a550 rev a5 class 02,00,00 hdr 00
( II )  PCI :  00 : 06 : 0 :  chip 10de,00da card 1297,a550 rev a2 class 04,01,00 hdr 00
( II )  PCI :  00 : 08 : 0 :  chip 10de,00d5 card 1297,a550 rev a5 class 01,01,8a hdr 00
( II )  PCI :  00 : 0a : 0 :  chip 10de,00dd card 0000,0000 rev a2 class 06,04,00 hdr 01
( II )  PCI :  00 : 0b : 0 :  chip 10de,00d2 card 0000,0000 rev a4 class 06,04,00 hdr 01
( II )  PCI :  00 : 18 : 0 :  chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
( II )  PCI :  00 : 18 : 1 :  chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
( II )  PCI :  00 : 18 : 2 :  chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
( II )  PCI :  00 : 18 : 3 :  chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
( II )  PCI :  01 : 06 : 0 :  chip 1106,3044 card 1106,3044 rev 80 class 0c,00,10 hdr 00
( II )  PCI :  01 : 07 : 0 :  chip 1095,3512 card 1095,6512 rev 01 class 01,04,00 hdr 00
( II )  PCI :  02 : 00 : 0 :  chip 10de,0322 card 1682,203c rev a1 class 03,00,00 hdr 00
( II )  PCI :  End of PCI scan
( II )  Host-to-PCI bridge : 
( II )  Bus 0 :  bridge is at ( 0 : 0 : 0 ) , ( 0,0,2 ) , BCTRL :  0x0008 ( VGA_EN is set ) 
( II )  Bus 0 I/O range : 
	<0] -1	0	0x00000000 - 0x0000ffff ( 0x10000 )  IX<B]
( II )  Bus 0 non-prefetchable memory range : 
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
( II )  Bus 0 prefetchable memory range : 
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
( II )  PCI-to-ISA bridge : 
( II )  Bus -1 :  bridge is at ( 0 : 1 : 0 ) , ( 0,-1,-1 ) , BCTRL :  0x0008 ( VGA_EN is set ) 
( II )  PCI-to-PCI bridge : 
( II )  Bus 1 :  bridge is at ( 0 : 10 : 0 ) , ( 0,1,1 ) , BCTRL :  0x0006 ( VGA_EN is cleared ) 
( II )  Bus 1 I/O range : 
	<0] -1	0	0x00009000 - 0x000090ff ( 0x100 )  IX<B]
	<1] -1	0	0x00009400 - 0x000094ff ( 0x100 )  IX<B]
	<2] -1	0	0x00009800 - 0x000098ff ( 0x100 )  IX<B]
	<3] -1	0	0x00009c00 - 0x00009cff ( 0x100 )  IX<B]
	<4] -1	0	0x0000a000 - 0x0000a0ff ( 0x100 )  IX<B]
	<5] -1	0	0x0000a400 - 0x0000a4ff ( 0x100 )  IX<B]
	<6] -1	0	0x0000a800 - 0x0000a8ff ( 0x100 )  IX<B]
	<7] -1	0	0x0000ac00 - 0x0000acff ( 0x100 )  IX<B]
( II )  Bus 1 non-prefetchable memory range : 
	<0] -1	0	0xe6000000 - 0xe7ffffff ( 0x2000000 )  MX<B]
( II )  PCI-to-PCI bridge : 
( II )  Bus 2 :  bridge is at ( 0 : 11 : 0 ) , ( 0,2,2 ) , BCTRL :  0x000f ( VGA_EN is set ) 
( II )  Bus 2 non-prefetchable memory range : 
	<0] -1	0	0xe4000000 - 0xe5ffffff ( 0x2000000 )  MX<B]
( II )  Bus 2 prefetchable memory range : 
	<0] -1	0	0xd0000000 - 0xdfffffff ( 0x10000000 )  MX<B]
( II )  Host-to-PCI bridge : 
( II )  Bus -1 :  bridge is at ( 0 : 24 : 0 ) , ( -1,-1,2 ) , BCTRL :  0x0008 ( VGA_EN is set ) 
( II )  Bus -1 I/O range : 
	<0] -1	0	0x00000000 - 0x0000ffff ( 0x10000 )  IX<B]
( II )  Bus -1 non-prefetchable memory range : 
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
( II )  Bus -1 prefetchable memory range : 
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
( II )  Host-to-PCI bridge : 
( II )  Bus -1 :  bridge is at ( 0 : 24 : 1 ) , ( -1,-1,2 ) , BCTRL :  0x0008 ( VGA_EN is set ) 
( II )  Bus -1 I/O range : 
	<0] -1	0	0x00000000 - 0x0000ffff ( 0x10000 )  IX<B]
( II )  Bus -1 non-prefetchable memory range : 
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
( II )  Bus -1 prefetchable memory range : 
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
( II )  Host-to-PCI bridge : 
( II )  Bus -1 :  bridge is at ( 0 : 24 : 2 ) , ( -1,-1,2 ) , BCTRL :  0x0008 ( VGA_EN is set ) 
( II )  Bus -1 I/O range : 
	<0] -1	0	0x00000000 - 0x0000ffff ( 0x10000 )  IX<B]
( II )  Bus -1 non-prefetchable memory range : 
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
( II )  Bus -1 prefetchable memory range : 
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
( II )  Host-to-PCI bridge : 
( II )  Bus -1 :  bridge is at ( 0 : 24 : 3 ) , ( -1,-1,2 ) , BCTRL :  0x0008 ( VGA_EN is set ) 
( II )  Bus -1 I/O range : 
	<0] -1	0	0x00000000 - 0x0000ffff ( 0x10000 )  IX<B]
( II )  Bus -1 non-prefetchable memory range : 
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
( II )  Bus -1 prefetchable memory range : 
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
( -- )  PCI : *( 2 : 0 : 0 )  nVidia Corporation NV34 <GeForce FX 5200] rev 161, Mem @ 0xe4000000/24, 0xd0000000/28
( II )  Addressable bus resource ranges are
	<0] -1	0	0x00000000 - 0xffffffff ( 0x100000000 )  MX<B]
	<1] -1	0	0x00000000 - 0x0000ffff ( 0x10000 )  IX<B]
( II )  OS-reported resource ranges : 
	<0] -1	0	0xffe00000 - 0xffffffff ( 0x200000 )  MX<B]( B ) 
	<1] -1	0	0x00100000 - 0x3fffffff ( 0x3ff00000 )  MX<B]E( B ) 
	<2] -1	0	0x000f0000 - 0x000fffff ( 0x10000 )  MX<B]
	<3] -1	0	0x000c0000 - 0x000effff ( 0x30000 )  MX<B]
	<4] -1	0	0x00000000 - 0x0009ffff ( 0xa0000 )  MX<B]
	<5] -1	0	0x0000ffff - 0x0000ffff ( 0x1 )  IX<B]
	<6] -1	0	0x00000000 - 0x000000ff ( 0x100 )  IX<B]
( II )  PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
( II )  Active PCI resource ranges : 
	<0] -1	0	0xe7000000 - 0xe70001ff ( 0x200 )  MX<B]
	<1] -1	0	0xe7001000 - 0xe70017ff ( 0x800 )  MX<B]
	<2] -1	0	0xe8001000 - 0xe8001fff ( 0x1000 )  MX<B]
	<3] -1	0	0xe8000000 - 0xe8000fff ( 0x1000 )  MX<B]
	<4] -1	0	0xe8004000 - 0xe80040ff ( 0x100 )  MX<B]
	<5] -1	0	0xe8003000 - 0xe8003fff ( 0x1000 )  MX<B]
	<6] -1	0	0xe8002000 - 0xe8002fff ( 0x1000 )  MX<B]
	<7] -1	0	0xe0000000 - 0xdfffffff ( 0x0 )  MX<B]O
	<8] -1	0	0xd0000000 - 0xdfffffff ( 0x10000000 )  MX<B]( B ) 
	<9] -1	0	0xe4000000 - 0xe4ffffff ( 0x1000000 )  MX<B]( B ) 
	<10] -1	0	0x0000a400 - 0x0000a40f ( 0x10 )  IX<B]
	<11] -1	0	0x0000a000 - 0x0000a003 ( 0x4 )  IX<B]
	<12] -1	0	0x00009c00 - 0x00009c07 ( 0x8 )  IX<B]
	<13] -1	0	0x00009800 - 0x00009803 ( 0x4 )  IX<B]
	<14] -1	0	0x00009400 - 0x00009407 ( 0x8 )  IX<B]
	<15] -1	0	0x00009000 - 0x0000907f ( 0x80 )  IX<B]
	<16] -1	0	0x0000f000 - 0x0000f00f ( 0x10 )  IX<B]
	<17] -1	0	0x0000bc00 - 0x0000bc7f ( 0x80 )  IX<B]
	<18] -1	0	0x0000b800 - 0x0000b8ff ( 0x100 )  IX<B]
	<19] -1	0	0x0000b400 - 0x0000b407 ( 0x8 )  IX<B]
	<20] -1	0	0x00004c40 - 0x00004c7f ( 0x40 )  IX<B]
	<21] -1	0	0x00004c00 - 0x00004c3f ( 0x40 )  IX<B]
( II )  Active PCI resource ranges after removing overlaps : 
	<0] -1	0	0xe7000000 - 0xe70001ff ( 0x200 )  MX<B]
	<1] -1	0	0xe7001000 - 0xe70017ff ( 0x800 )  MX<B]
	<2] -1	0	0xe8001000 - 0xe8001fff ( 0x1000 )  MX<B]
	<3] -1	0	0xe8000000 - 0xe8000fff ( 0x1000 )  MX<B]
	<4] -1	0	0xe8004000 - 0xe80040ff ( 0x100 )  MX<B]
	<5] -1	0	0xe8003000 - 0xe8003fff ( 0x1000 )  MX<B]
	<6] -1	0	0xe8002000 - 0xe8002fff ( 0x1000 )  MX<B]
	<7] -1	0	0xe0000000 - 0xdfffffff ( 0x0 )  MX<B]O
	<8] -1	0	0xd0000000 - 0xdfffffff ( 0x10000000 )  MX<B]( B ) 
	<9] -1	0	0xe4000000 - 0xe4ffffff ( 0x1000000 )  MX<B]( B ) 
	<10] -1	0	0x0000a400 - 0x0000a40f ( 0x10 )  IX<B]
	<11] -1	0	0x0000a000 - 0x0000a003 ( 0x4 )  IX<B]
	<12] -1	0	0x00009c00 - 0x00009c07 ( 0x8 )  IX<B]
	<13] -1	0	0x00009800 - 0x00009803 ( 0x4 )  IX<B]
	<14] -1	0	0x00009400 - 0x00009407 ( 0x8 )  IX<B]
	<15] -1	0	0x00009000 - 0x0000907f ( 0x80 )  IX<B]
	<16] -1	0	0x0000f000 - 0x0000f00f ( 0x10 )  IX<B]
	<17] -1	0	0x0000bc00 - 0x0000bc7f ( 0x80 )  IX<B]
	<18] -1	0	0x0000b800 - 0x0000b8ff ( 0x100 )  IX<B]
	<19] -1	0	0x0000b400 - 0x0000b407 ( 0x8 )  IX<B]
	<20] -1	0	0x00004c40 - 0x00004c7f ( 0x40 )  IX<B]
	<21] -1	0	0x00004c00 - 0x00004c3f ( 0x40 )  IX<B]
( II )  OS-reported resource ranges after removing overlaps with PCI : 
	<0] -1	0	0xffe00000 - 0xffffffff ( 0x200000 )  MX<B]( B ) 
	<1] -1	0	0x00100000 - 0x3fffffff ( 0x3ff00000 )  MX<B]E( B ) 
	<2] -1	0	0x000f0000 - 0x000fffff ( 0x10000 )  MX<B]
	<3] -1	0	0x000c0000 - 0x000effff ( 0x30000 )  MX<B]
	<4] -1	0	0x00000000 - 0x0009ffff ( 0xa0000 )  MX<B]
	<5] -1	0	0x0000ffff - 0x0000ffff ( 0x1 )  IX<B]
	<6] -1	0	0x00000000 - 0x000000ff ( 0x100 )  IX<B]
( II )  All system resource ranges : 
	<0] -1	0	0xffe00000 - 0xffffffff ( 0x200000 )  MX<B]( B ) 
	<1] -1	0	0x00100000 - 0x3fffffff ( 0x3ff00000 )  MX<B]E( B ) 
	<2] -1	0	0x000f0000 - 0x000fffff ( 0x10000 )  MX<B]
	<3] -1	0	0x000c0000 - 0x000effff ( 0x30000 )  MX<B]
	<4] -1	0	0x00000000 - 0x0009ffff ( 0xa0000 )  MX<B]
	<5] -1	0	0xe7000000 - 0xe70001ff ( 0x200 )  MX<B]
	<6] -1	0	0xe7001000 - 0xe70017ff ( 0x800 )  MX<B]
	<7] -1	0	0xe8001000 - 0xe8001fff ( 0x1000 )  MX<B]
	<8] -1	0	0xe8000000 - 0xe8000fff ( 0x1000 )  MX<B]
	<9] -1	0	0xe8004000 - 0xe80040ff ( 0x100 )  MX<B]
	<10] -1	0	0xe8003000 - 0xe8003fff ( 0x1000 )  MX<B]
	<11] -1	0	0xe8002000 - 0xe8002fff ( 0x1000 )  MX<B]
	<12] -1	0	0xe0000000 - 0xdfffffff ( 0x0 )  MX<B]O
	<13] -1	0	0xd0000000 - 0xdfffffff ( 0x10000000 )  MX<B]( B ) 
	<14] -1	0	0xe4000000 - 0xe4ffffff ( 0x1000000 )  MX<B]( B ) 
	<15] -1	0	0x0000ffff - 0x0000ffff ( 0x1 )  IX<B]
	<16] -1	0	0x00000000 - 0x000000ff ( 0x100 )  IX<B]
	<17] -1	0	0x0000a400 - 0x0000a40f ( 0x10 )  IX<B]
	<18] -1	0	0x0000a000 - 0x0000a003 ( 0x4 )  IX<B]
	<19] -1	0	0x00009c00 - 0x00009c07 ( 0x8 )  IX<B]
	<20] -1	0	0x00009800 - 0x00009803 ( 0x4 )  IX<B]
	<21] -1	0	0x00009400 - 0x00009407 ( 0x8 )  IX<B]
	<22] -1	0	0x00009000 - 0x0000907f ( 0x80 )  IX<B]
	<23] -1	0	0x0000f000 - 0x0000f00f ( 0x10 )  IX<B]
	<24] -1	0	0x0000bc00 - 0x0000bc7f ( 0x80 )  IX<B]
	<25] -1	0	0x0000b800 - 0x0000b8ff ( 0x100 )  IX<B]
	<26] -1	0	0x0000b400 - 0x0000b407 ( 0x8 )  IX<B]
	<27] -1	0	0x00004c40 - 0x00004c7f ( 0x40 )  IX<B]
	<28] -1	0	0x00004c00 - 0x00004c3f ( 0x40 )  IX<B]
( II )  LoadModule :  "bitmap"
( II )  Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
( II )  Loading font Bitmap
( II )  LoadModule :  "dbe"
( II )  Loading /usr/X11R6/lib/modules/extensions/libdbe.a
( II )  Module dbe :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class :  X.Org Server Extension
	ABI class :  X.Org Server Extension, version 0.2
( II )  Loading extension DOUBLE-BUFFER
( II )  LoadModule :  "ddc"
( II )  Loading /usr/X11R6/lib/modules/libddc.a
( II )  Module ddc :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class :  X.Org Video Driver, version 0.7
( II )  LoadModule :  "dri"
( II )  Loading /usr/X11R6/lib/modules/extensions/libdri.a
( II )  Module dri :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class :  X.Org Server Extension, version 0.2
( II )  Loading sub module "drm"
( II )  LoadModule :  "drm"
( II )  Loading /usr/X11R6/lib/modules/linux/libdrm.a
( II )  Module drm :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class :  X.Org Server Extension, version 0.2
( II )  Loading extension XFree86-DRI
( II )  LoadModule :  "extmod"
( II )  Loading /usr/X11R6/lib/modules/extensions/libextmod.a
( II )  Module extmod :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class :  X.Org Server Extension
	ABI class :  X.Org Server Extension, version 0.2
( II )  Loading extension SHAPE
( II )  Loading extension MIT-SUNDRY-NONSTANDARD
( II )  Loading extension BIG-REQUESTS
( II )  Loading extension SYNC
( II )  Loading extension MIT-SCREEN-SAVER
( II )  Loading extension XC-MISC
( II )  Loading extension XFree86-VidModeExtension
( II )  Loading extension XFree86-Misc
( II )  Loading extension XFree86-DGA
( II )  Loading extension DPMS
( II )  Loading extension FontCache
( II )  Loading extension TOG-CUP
( II )  Loading extension Extended-Visual-Information
( II )  Loading extension XVideo
( II )  Loading extension XVideo-MotionCompensation
( II )  Loading extension X-Resource
( II )  LoadModule :  "freetype"
( II )  Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
( II )  Module freetype :  vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class :  X.Org Font Renderer
	ABI class :  X.Org Font Renderer, version 0.4
( II )  Loading font FreeType
( II )  LoadModule :  "glx"
( II )  Loading /usr/X11R6/lib/modules/extensions/libglx.so
( II )  Module glx :  vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.6629
	Module class :  XFree86 Server Extension
	ABI class :  XFree86 Server Extension, version 0.1
( II )  Loading extension GLX
( II )  LoadModule :  "int10"
( II )  Loading /usr/X11R6/lib/modules/linux/libint10.a
( II )  Module int10 :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class :  X.Org Video Driver, version 0.7
( II )  LoadModule :  "record"
( II )  Loading /usr/X11R6/lib/modules/extensions/librecord.a
( II )  Module record :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class :  X.Org Server Extension
	ABI class :  X.Org Server Extension, version 0.2
( II )  Loading extension RECORD
( II )  LoadModule :  "type1"
( II )  Loading /usr/X11R6/lib/modules/fonts/libtype1.a
( II )  Module type1 :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class :  X.Org Font Renderer
	ABI class :  X.Org Font Renderer, version 0.4
( II )  Loading font Type1
( II )  Loading font CID
( II )  LoadModule :  "vbe"
( II )  Loading /usr/X11R6/lib/modules/libvbe.a
( II )  Module vbe :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class :  X.Org Video Driver, version 0.7
( II )  LoadModule :  "nvidia"
( II )  Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
( II )  Module nvidia :  vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.6629
	Module class :  XFree86 Video Driver
( II )  LoadModule :  "keyboard"
( II )  Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
( II )  Module keyboard :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class :  X.Org XInput Driver
	ABI class :  X.Org XInput driver, version 0.4
( II )  LoadModule :  "mouse"
( II )  Loading /usr/X11R6/lib/modules/input/mouse_drv.o
( II )  Module mouse :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class :  X.Org XInput Driver
	ABI class :  X.Org XInput driver, version 0.4
( II )  NVIDIA X Driver  1.0-6629  Wed Nov  3 11 : 44 : 46 PST 2004
( II )  NVIDIA Unified Driver for all NVIDIA GPUs
( II )  Primary Device is :  PCI 02 : 00 : 0
( -- )  Chipset NVIDIA GPU found
( II )  resource ranges after xf86ClaimFixedResources(  )  call : 
	<0] -1	0	0xffe00000 - 0xffffffff ( 0x200000 )  MX<B]( B ) 
	<1] -1	0	0x00100000 - 0x3fffffff ( 0x3ff00000 )  MX<B]E( B ) 
	<2] -1	0	0x000f0000 - 0x000fffff ( 0x10000 )  MX<B]
	<3] -1	0	0x000c0000 - 0x000effff ( 0x30000 )  MX<B]
	<4] -1	0	0x00000000 - 0x0009ffff ( 0xa0000 )  MX<B]
	<5] -1	0	0xe7000000 - 0xe70001ff ( 0x200 )  MX<B]
	<6] -1	0	0xe7001000 - 0xe70017ff ( 0x800 )  MX<B]
	<7] -1	0	0xe8001000 - 0xe8001fff ( 0x1000 )  MX<B]
	<8] -1	0	0xe8000000 - 0xe8000fff ( 0x1000 )  MX<B]
	<9] -1	0	0xe8004000 - 0xe80040ff ( 0x100 )  MX<B]
	<10] -1	0	0xe8003000 - 0xe8003fff ( 0x1000 )  MX<B]
	<11] -1	0	0xe8002000 - 0xe8002fff ( 0x1000 )  MX<B]
	<12] -1	0	0xe0000000 - 0xdfffffff ( 0x0 )  MX<B]O
	<13] -1	0	0xd0000000 - 0xdfffffff ( 0x10000000 )  MX<B]( B ) 
	<14] -1	0	0xe4000000 - 0xe4ffffff ( 0x1000000 )  MX<B]( B ) 
	<15] -1	0	0x0000ffff - 0x0000ffff ( 0x1 )  IX<B]
	<16] -1	0	0x00000000 - 0x000000ff ( 0x100 )  IX<B]
	<17] -1	0	0x0000a400 - 0x0000a40f ( 0x10 )  IX<B]
	<18] -1	0	0x0000a000 - 0x0000a003 ( 0x4 )  IX<B]
	<19] -1	0	0x00009c00 - 0x00009c07 ( 0x8 )  IX<B]
	<20] -1	0	0x00009800 - 0x00009803 ( 0x4 )  IX<B]
	<21] -1	0	0x00009400 - 0x00009407 ( 0x8 )  IX<B]
	<22] -1	0	0x00009000 - 0x0000907f ( 0x80 )  IX<B]
	<23] -1	0	0x0000f000 - 0x0000f00f ( 0x10 )  IX<B]
	<24] -1	0	0x0000bc00 - 0x0000bc7f ( 0x80 )  IX<B]
	<25] -1	0	0x0000b800 - 0x0000b8ff ( 0x100 )  IX<B]
	<26] -1	0	0x0000b400 - 0x0000b407 ( 0x8 )  IX<B]
	<27] -1	0	0x00004c40 - 0x00004c7f ( 0x40 )  IX<B]
	<28] -1	0	0x00004c00 - 0x00004c3f ( 0x40 )  IX<B]
( II )  resource ranges after probing : 
	<0] -1	0	0xffe00000 - 0xffffffff ( 0x200000 )  MX<B]( B ) 
	<1] -1	0	0x00100000 - 0x3fffffff ( 0x3ff00000 )  MX<B]E( B ) 
	<2] -1	0	0x000f0000 - 0x000fffff ( 0x10000 )  MX<B]
	<3] -1	0	0x000c0000 - 0x000effff ( 0x30000 )  MX<B]
	<4] -1	0	0x00000000 - 0x0009ffff ( 0xa0000 )  MX<B]
	<5] -1	0	0xe7000000 - 0xe70001ff ( 0x200 )  MX<B]
	<6] -1	0	0xe7001000 - 0xe70017ff ( 0x800 )  MX<B]
	<7] -1	0	0xe8001000 - 0xe8001fff ( 0x1000 )  MX<B]
	<8] -1	0	0xe8000000 - 0xe8000fff ( 0x1000 )  MX<B]
	<9] -1	0	0xe8004000 - 0xe80040ff ( 0x100 )  MX<B]
	<10] -1	0	0xe8003000 - 0xe8003fff ( 0x1000 )  MX<B]
	<11] -1	0	0xe8002000 - 0xe8002fff ( 0x1000 )  MX<B]
	<12] -1	0	0xe0000000 - 0xdfffffff ( 0x0 )  MX<B]O
	<13] -1	0	0xd0000000 - 0xdfffffff ( 0x10000000 )  MX<B]( B ) 
	<14] -1	0	0xe4000000 - 0xe4ffffff ( 0x1000000 )  MX<B]( B ) 
	<15] 0	0	0x000a0000 - 0x000affff ( 0x10000 )  MS<B]
	<16] 0	0	0x000b0000 - 0x000b7fff ( 0x8000 )  MS<B]
	<17] 0	0	0x000b8000 - 0x000bffff ( 0x8000 )  MS<B]
	<18] -1	0	0x0000ffff - 0x0000ffff ( 0x1 )  IX<B]
	<19] -1	0	0x00000000 - 0x000000ff ( 0x100 )  IX<B]
	<20] -1	0	0x0000a400 - 0x0000a40f ( 0x10 )  IX<B]
	<21] -1	0	0x0000a000 - 0x0000a003 ( 0x4 )  IX<B]
	<22] -1	0	0x00009c00 - 0x00009c07 ( 0x8 )  IX<B]
	<23] -1	0	0x00009800 - 0x00009803 ( 0x4 )  IX<B]
	<24] -1	0	0x00009400 - 0x00009407 ( 0x8 )  IX<B]
	<25] -1	0	0x00009000 - 0x0000907f ( 0x80 )  IX<B]
	<26] -1	0	0x0000f000 - 0x0000f00f ( 0x10 )  IX<B]
	<27] -1	0	0x0000bc00 - 0x0000bc7f ( 0x80 )  IX<B]
	<28] -1	0	0x0000b800 - 0x0000b8ff ( 0x100 )  IX<B]
	<29] -1	0	0x0000b400 - 0x0000b407 ( 0x8 )  IX<B]
	<30] -1	0	0x00004c40 - 0x00004c7f ( 0x40 )  IX<B]
	<31] -1	0	0x00004c00 - 0x00004c3f ( 0x40 )  IX<B]
	<32] 0	0	0x000003b0 - 0x000003bb ( 0xc )  IS<B]
	<33] 0	0	0x000003c0 - 0x000003df ( 0x20 )  IS<B]
( II )  Setting vga for screen 0.
( ** )  NVIDIA( 0 )  :  Depth 24, ( -- )  framebuffer bpp 32
( == )  NVIDIA( 0 )  :  RGB weight 888
( == )  NVIDIA( 0 )  :  Default visual is TrueColor
( == )  NVIDIA( 0 )  :  Using gamma correction ( 1.0, 1.0, 1.0 ) 
( -- )  NVIDIA( 0 )  :  Linear framebuffer at 0xD0000000
( -- )  NVIDIA( 0 )  :  MMIO registers at 0xE4000000
( II )  NVIDIA( 0 )  :  NVIDIA GPU detected as :  GeForce FX 5200
( -- )  NVIDIA( 0 )  :  VideoBIOS :  04.34.20.27.02
( -- )  NVIDIA( 0 )  :  Interlaced video modes are supported on this GPU
( II )  NVIDIA( 0 )  :  Detected AGP rate :  8X
( -- )  NVIDIA( 0 )  :  VideoRAM :  262144 kBytes
( II )  NVIDIA( 0 )  :  Connected display device( s )  :  CRT-0
( -- )  NVIDIA( 0 )  :  Display device CRT-0 :  maximum pixel clock at  8 bpp :  400 MHz
( -- )  NVIDIA( 0 )  :  Display device CRT-0 :  maximum pixel clock at 16 bpp :  400 MHz
( -- )  NVIDIA( 0 )  :  Display device CRT-0 :  maximum pixel clock at 32 bpp :  400 MHz
( II )  Loading sub module "ddc"
( II )  LoadModule :  "ddc"
( II )  Reloading /usr/X11R6/lib/modules/libddc.a
( WW )  NVIDIA( 0 )  :  Failure reading EDID parameters for display device CRT-0
( II )  NVIDIA( 0 )  :  Generic Monitor :  Using hsync range of 30.00-70.00 kHz
( II )  NVIDIA( 0 )  :  Generic Monitor :  Using vrefresh range of 50.00-160.00 Hz
( II )  NVIDIA( 0 )  :  Clock range :   12.00 to 400.00 MHz
( II )  NVIDIA( 0 )  :  Not using default mode "1280x960" ( hsync out of range ) 
( II )  NVIDIA( 0 )  :  Not using default mode "640x480" ( hsync out of range ) 
( II )  NVIDIA( 0 )  :  Not using default mode "1280x1024" ( hsync out of range ) 
( II )  NVIDIA( 0 )  :  Not using default mode "640x512" ( hsync out of range ) 
( II )  NVIDIA( 0 )  :  Not using default mode "1280x1024" ( hsync out of range ) 
( II )  NVIDIA( 0 )  :  Not using default mode "640x512" ( hsync out of range ) 
/ REMOVED SOME LINES HERE
( II )  NVIDIA( 0 )  :  Not using default mode "1024x768" ( hsync out of range ) 
( II )  NVIDIA( 0 )  :  Not using default mode "1400x1050" ( width too large for virtual size ) 
( II )  NVIDIA( 0 )  :  Not using default mode "1440x900" ( width too large for virtual size ) 
( WW )  NVIDIA( 0 )  :  Not using mode "1152x768" : 
( WW )  NVIDIA( 0 )  :    horizontal sync start ( 1178 )  not a multiple of 8
( WW )  NVIDIA( 0 )  :  Not using mode "576x384" : 
( WW )  NVIDIA( 0 )  :    horizontal sync start ( 589 )  not a multiple of 8
( WW )  NVIDIA( 0 )  :  Not using mode "360x200" : 
( WW )  NVIDIA( 0 )  :    horizontal sync start ( 378 )  not a multiple of 8
( ** )  NVIDIA( 0 )  :  Validated modes for display device CRT-0 : 
( ** )  NVIDIA( 0 )  :       Default mode "1280x1024" :  108.0 MHz, 64.0 kHz, 60.0 Hz
( ** )  NVIDIA( 0 )  :       Default mode "1280x960" :  108.0 MHz, 60.0 kHz, 60.0 Hz
( ** )  NVIDIA( 0 )  :       Default mode "1024x768" :  94.5 MHz, 68.7 kHz, 85.0 Hz
( ** )  NVIDIA( 0 )  :       Default mode "800x600" :  56.3 MHz, 53.7 kHz, 85.1 Hz
( ** )  NVIDIA( 0 )  :       Default mode "640x480" :  36.0 MHz, 43.3 kHz, 85.0 Hz
/ REMOVED SOME LINES HERE
( ** )  NVIDIA( 0 )  :       Default mode "320x240" :  12.6 MHz, 31.5 kHz, 60.1 Hz ( D ) 
( ** )  NVIDIA( 0 )  :       Default mode "320x200" :  15.8 MHz, 37.9 kHz, 85.3 Hz ( D ) 
( ** )  NVIDIA( 0 )  :       Default mode "320x175" :  15.8 MHz, 37.9 kHz, 85.3 Hz ( D ) 
( II )  NVIDIA( 0 )  :  Virtual screen size determined to be 1280 x 1024
( ++ )  NVIDIA( 0 )  :  DPI set to ( 100, 100 ) 
( II )  Loading sub module "fb"
( II )  LoadModule :  "fb"
( II )  Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a : fbmmx.o" :   No symbols found
( II )  Module fb :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class :  X.Org ANSI C Emulation, version 0.2
( II )  Loading sub module "ramdac"
( II )  LoadModule :  "ramdac"
( II )  Loading /usr/X11R6/lib/modules/libramdac.a
( II )  Module ramdac :  vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class :  X.Org Video Driver, version 0.7
( -- )  Depth 24 pixmap format is 32 bpp
( II )  do I need RAC?  No, I don't.
( II )  resource ranges after preInit : 
	<0] 0	0	0xd0000000 - 0xdfffffff ( 0x10000000 )  MX<B]
	<1] 0	0	0xe4000000 - 0xe4ffffff ( 0x1000000 )  MX<B]
	<2] -1	0	0xffe00000 - 0xffffffff ( 0x200000 )  MX<B]( B ) 
	<3] -1	0	0x00100000 - 0x3fffffff ( 0x3ff00000 )  MX<B]E( B ) 
	<4] -1	0	0x000f0000 - 0x000fffff ( 0x10000 )  MX<B]
	<5] -1	0	0x000c0000 - 0x000effff ( 0x30000 )  MX<B]
	<6] -1	0	0x00000000 - 0x0009ffff ( 0xa0000 )  MX<B]
	<7] -1	0	0xe7000000 - 0xe70001ff ( 0x200 )  MX<B]
	<8] -1	0	0xe7001000 - 0xe70017ff ( 0x800 )  MX<B]
	<9] -1	0	0xe8001000 - 0xe8001fff ( 0x1000 )  MX<B]
	<10] -1	0	0xe8000000 - 0xe8000fff ( 0x1000 )  MX<B]
	<11] -1	0	0xe8004000 - 0xe80040ff ( 0x100 )  MX<B]
	<12] -1	0	0xe8003000 - 0xe8003fff ( 0x1000 )  MX<B]
	<13] -1	0	0xe8002000 - 0xe8002fff ( 0x1000 )  MX<B]
	<14] -1	0	0xe0000000 - 0xdfffffff ( 0x0 )  MX<B]O
	<15] -1	0	0xd0000000 - 0xdfffffff ( 0x10000000 )  MX<B]( B ) 
	<16] -1	0	0xe4000000 - 0xe4ffffff ( 0x1000000 )  MX<B]( B ) 
	<17] 0	0	0x000a0000 - 0x000affff ( 0x10000 )  MS<B]( OprD ) 
	<18] 0	0	0x000b0000 - 0x000b7fff ( 0x8000 )  MS<B]( OprD ) 
	<19] 0	0	0x000b8000 - 0x000bffff ( 0x8000 )  MS<B]( OprD ) 
	<20] -1	0	0x0000ffff - 0x0000ffff ( 0x1 )  IX<B]
	<21] -1	0	0x00000000 - 0x000000ff ( 0x100 )  IX<B]
	<22] -1	0	0x0000a400 - 0x0000a40f ( 0x10 )  IX<B]
	<23] -1	0	0x0000a000 - 0x0000a003 ( 0x4 )  IX<B]
	<24] -1	0	0x00009c00 - 0x00009c07 ( 0x8 )  IX<B]
	<25] -1	0	0x00009800 - 0x00009803 ( 0x4 )  IX<B]
	<26] -1	0	0x00009400 - 0x00009407 ( 0x8 )  IX<B]
	<27] -1	0	0x00009000 - 0x0000907f ( 0x80 )  IX<B]
	<28] -1	0	0x0000f000 - 0x0000f00f ( 0x10 )  IX<B]
	<29] -1	0	0x0000bc00 - 0x0000bc7f ( 0x80 )  IX<B]
	<30] -1	0	0x0000b800 - 0x0000b8ff ( 0x100 )  IX<B]
	<31] -1	0	0x0000b400 - 0x0000b407 ( 0x8 )  IX<B]
	<32] -1	0	0x00004c40 - 0x00004c7f ( 0x40 )  IX<B]
	<33] -1	0	0x00004c00 - 0x00004c3f ( 0x40 )  IX<B]
	<34] 0	0	0x000003b0 - 0x000003bb ( 0xc )  IS<B]( OprU ) 
	<35] 0	0	0x000003c0 - 0x000003df ( 0x20 )  IS<B]( OprU ) 
( II )  NVIDIA( 0 )  :  Setting mode "1280x1024"
( II )  Loading extension NV-GLX
( II )  NVIDIA( 0 )  :  NVIDIA 3D Acceleration Architecture Initialized
( II )  NVIDIA( 0 )  :  Using the NVIDIA 2D acceleration architecture
( == )  NVIDIA( 0 )  :  Backing store disabled
( == )  NVIDIA( 0 )  :  Silken mouse enabled
( ** )  Option "dpms"
( ** )  NVIDIA( 0 )  :  DPMS enabled
( II )  Loading extension NV-CONTROL
( == )  RandR enabled
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
( II )  Initializing built-in extension MIT-SHM
( II )  Initializing built-in extension XInputExtension
( II )  Initializing built-in extension XTEST
( II )  Initializing built-in extension XKEYBOARD
( II )  Initializing built-in extension LBX
( II )  Initializing built-in extension XC-APPGROUP
( II )  Initializing built-in extension SECURITY
( II )  Initializing built-in extension XINERAMA
( II )  Initializing built-in extension XFIXES
( II )  Initializing built-in extension XFree86-Bigfont
( II )  Initializing built-in extension RENDER
( II )  Initializing built-in extension RANDR
( II )  Initializing built-in extension COMPOSITE
( II )  Initializing built-in extension DAMAGE
( II )  Initializing built-in extension XEVIE
( II )  Initializing extension GLX

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error : 
Caught signal 11.  Server aborting
``` 

Does anyone have any clue why it does not work?

---

### Post by henla464 on 2005-03-28
Commenting out Load "glx" in the config file made it work!

But doesn't commenting out "glx" disable something important?

---

### Post by roodhoedje on 2005-03-28
Don't load dri that seems to be to problem he can't find libdri. 

And if I'm correct nvidia doesn't use dri but I think it uses glx  :p .

---

### Post by henla464 on 2005-03-28
I tried to just comment out dri but that didn't help. Now I have both glx and dri commented out and that works.

---

### Post by henla464 on 2005-03-31
Thanks ubuntu devels!!

apt-get upgrade solved this today. Probably the new nvidia driver fixed it.

 :-D

---

### Post by Ubiquitous on 2005-04-22
I just installed hoary for the first time this morning on an amd64 system and ran into the exact same issues:

Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!

Turned out I didn't have nvidia-settings installed.  Once I did the apt-get of that and enabled glx, everything is working great.  It appears that nvidia settings is a dependency, but isn't indicated as such (or I missed it somehow).

---

