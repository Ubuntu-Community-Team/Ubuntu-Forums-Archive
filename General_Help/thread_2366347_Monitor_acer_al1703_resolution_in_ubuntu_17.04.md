---
title: "Monitor acer al1703 resolution in ubuntu 17.04?"
date: 2017-07-16
forum: General Help
---

### Post by glearmonth on 2017-07-16
In English:

I have enormous problems in mi Pc.

I have an server HP WORKSTATION Z420 (XEON 1620 PROCESSOR, ATI RADEON HD5670 VIDEOCARD) and i canÂ´t change resolution (only let me change to 800x600 or 1024x768) in the monitor menu display "UNKNOW MONITOR" how can i do?

In the xorg.0.log file located in /var/log/xorg show this: (see below spanish text)
_________________________________________________________

En Espanol:

Yo tengo enormes problemas en mi Pc.

Yo tengo un servidor HP WORKSTATION Z420 (PROCESADO9R XEON 1620, TARJETA DE VIDEO ATI RADEON HD5670) Y Yo no puedo cambiar la resoluciÃ³n (SÃ³lo me deja cambiar 800x600xo 1024x768) En el menÃº de monitor muestra "UNKNOW MONITOR" Â¿QuÃ© puedo hacer?

En el archivo xorg.0.log localizado en /var/log/ muestra esto:
__________________________________________________________


[http://paste.ubuntu.com/25109445/plain/](http://paste.ubuntu.com/25109445/plain/)

[    48.264] 
X.Org X Server 1.19.3
Release Date: 2017-03-15
[    48.264] X Protocol Version 11, Revision 0
[    48.264] Build Operating System: Linux 4.4.0-70-generic x86_64 Ubuntu
[    48.264] Current Operating System: Linux unknow-Unknows 4.10.0-26-generic #30-Ubuntu SMP Tue Jun 27 09:30:12 UTC 2017 x86_64
[    48.264] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-26-generic root=UUID=05c5b871-3f2d-4663-b99d-c19a31a737e7 ro quiet splash vt.handoff=7
[    48.264] Build Date: 28 March 2017  06:16:52AM
[    48.264] xorg-server 2:1.19.3-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    48.264] Current version of pixman: 0.34.0
[    48.264] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    48.264] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    48.264] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 16 22:52:08 2017
[    48.270] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    48.270] (==) No Layout section.  Using the first Screen section.
[    48.270] (==) No screen section available. Using defaults.
[    48.270] (**) |-->Screen "Default Screen Section" (0)
[    48.270] (**) |   |-->Monitor "<default monitor>"
[    48.270] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    48.270] (==) Automatically adding devices
[    48.270] (==) Automatically enabling devices
[    48.270] (==) Automatically adding GPU devices
[    48.270] (==) Automatically binding GPU devices
[    48.270] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    48.270] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    48.270] 	Entry deleted from font path.
[    48.270] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    48.270] 	Entry deleted from font path.
[    48.270] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    48.270] 	Entry deleted from font path.
[    48.271] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    48.271] 	Entry deleted from font path.
[    48.271] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    48.271] 	Entry deleted from font path.
[    48.271] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    48.271] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    48.271] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    48.271] (II) Loader magic: 0x555f2581f020
[    48.271] (II) Module ABI versions:
[    48.271] 	X.Org ANSI C Emulation: 0.4
[    48.271] 	X.Org Video Driver: 23.0
[    48.271] 	X.Org XInput driver : 24.1
[    48.271] 	X.Org Server Extension : 10.0
[    48.271] (++) using VT number 7

[    48.271] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    48.272] (II) xfree86: Adding drm device (/dev/dri/card0)
[    48.274] (--) PCI:*(0:5:0:0) 1002:68d8:1682:3066 rev 0, Mem @ 0xd0000000/268435456, 0xefe20000/131072, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[    48.274] (II) LoadModule: "glx"
[    48.288] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    48.547] (II) Module glx: vendor="X.Org Foundation"
[    48.547] 	compiled for 1.19.3, module version = 1.0.0
[    48.547] 	ABI class: X.Org Server Extension, version 10.0
[    48.547] (II) Applying OutputClass "Radeon" to /dev/dri/card0
[    48.547] 	loading driver: radeon
[    48.547] (==) Matched radeon as autoconfigured driver 0
[    48.547] (==) Matched ati as autoconfigured driver 1
[    48.547] (==) Matched ati as autoconfigured driver 2
[    48.547] (==) Matched modesetting as autoconfigured driver 3
[    48.547] (==) Matched fbdev as autoconfigured driver 4
[    48.547] (==) Matched vesa as autoconfigured driver 5
[    48.547] (==) Assigned the driver to the xf86ConfigLayout
[    48.547] (II) LoadModule: "radeon"
[    48.548] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    48.575] (II) Module radeon: vendor="X.Org Foundation"
[    48.575] 	compiled for 1.19.3, module version = 7.9.0
[    48.575] 	Module class: X.Org Video Driver
[    48.575] 	ABI class: X.Org Video Driver, version 23.0
[    48.575] (II) LoadModule: "ati"
[    48.575] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    48.575] (II) Module ati: vendor="X.Org Foundation"
[    48.575] 	compiled for 1.19.3, module version = 7.9.0
[    48.575] 	Module class: X.Org Video Driver
[    48.575] 	ABI class: X.Org Video Driver, version 23.0
[    48.637] (II) LoadModule: "modesetting"
[    48.637] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    48.652] (II) Module modesetting: vendor="X.Org Foundation"
[    48.652] 	compiled for 1.19.3, module version = 1.19.3
[    48.652] 	Module class: X.Org Video Driver
[    48.652] 	ABI class: X.Org Video Driver, version 23.0
[    48.652] (II) LoadModule: "fbdev"
[    48.652] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    48.653] (II) Module fbdev: vendor="X.Org Foundation"
[    48.653] 	compiled for 1.19.3, module version = 0.4.4
[    48.653] 	Module class: X.Org Video Driver
[    48.653] 	ABI class: X.Org Video Driver, version 23.0
[    48.653] (II) LoadModule: "vesa"
[    48.653] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    48.653] (II) Module vesa: vendor="X.Org Foundation"
[    48.653] 	compiled for 1.19.3, module version = 2.3.4
[    48.653] 	Module class: X.Org Video Driver
[    48.653] 	ABI class: X.Org Video Driver, version 23.0
[    48.653] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
	ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
	ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
	ATI Radeon X600 (RV380), ATI FireGL V3200 (RV380),
	ATI Radeon IGP320 (A3), ATI Radeon IGP330/340/350 (A4),
	ATI Radeon 9500, ATI Radeon 9600TX, ATI FireGL Z1, ATI Radeon 9800SE,
	ATI Radeon 9800, ATI FireGL X2, ATI Radeon 9600, ATI Radeon 9600SE,
	ATI Radeon 9600XT, ATI FireGL T2, ATI Radeon 9650, ATI FireGL RV360,
	ATI Radeon 7000 IGP (A4+), ATI Radeon 8500 AIW,
	ATI Radeon IGP320M (U1), ATI Radeon IGP330M/340M/350M (U2),
	ATI Radeon Mobility 7000 IGP, ATI Radeon 9000/PRO, ATI Radeon 9000,
	ATI Radeon X800 (R420), ATI Radeon X800PRO (R420),
	ATI Radeon X800SE (R420), ATI FireGL X3 (R420),
	ATI Radeon Mobility 9800 (M18), ATI Radeon X800 SE (R420),
	ATI Radeon X800XT (R420), ATI Radeon X800 VE (R420),
	ATI Radeon X850 (R480), ATI Radeon X850 XT (R480),
	ATI Radeon X850 SE (R480), ATI Radeon X850 PRO (R480),
	ATI Radeon X850 XT PE (R480), ATI Radeon Mobility M7,
	ATI Mobility FireGL 7800 M7, ATI Radeon Mobility M6,
	ATI FireGL Mobility 9000 (M9), ATI Radeon Mobility 9000 (M9),
	ATI Radeon 9700 Pro, ATI Radeon 9700/9500Pro, ATI FireGL X1,
	ATI Radeon 9800PRO, ATI Radeon 9800XT,
	ATI Radeon Mobility 9600/9700 (M10/M11),
	ATI Radeon Mobility 9600 (M10), ATI Radeon Mobility 9600 (M11),
	ATI FireGL Mobility T2 (M10), ATI FireGL Mobility T2e (M11),
	ATI Radeon, ATI FireGL 8700/8800, ATI Radeon 8500, ATI Radeon 9100,
	ATI Radeon 7500, ATI Radeon VE/7000, ATI ES1000,
	ATI Radeon Mobility X300 (M22), ATI Radeon Mobility X600 SE (M24C),
	ATI FireGL M22 GL, ATI Radeon X800 (R423), ATI Radeon X800PRO (R423),
	ATI Radeon X800LE (R423), ATI Radeon X800SE (R423),
	ATI Radeon X800 XTP (R430), ATI Radeon X800 XL (R430),
	ATI Radeon X800 SE (R430), ATI Radeon X800 (R430),
	ATI FireGL V7100 (R423), ATI FireGL V5100 (R423),
	ATI FireGL unknown (R423), ATI Mobility FireGL V5000 (M26),
	ATI Mobility Radeon X700 XL (M26), ATI Mobility Radeon X700 (M26),
	ATI Radeon X550XTX, ATI Radeon 9100 IGP (A5),
	ATI Radeon Mobility 9100 IGP (U3), ATI Radeon XPRESS 200,
	ATI Radeon XPRESS 200M, ATI Radeon 9250, ATI Radeon 9200,
	ATI Radeon 9200SE, ATI FireMV 2200, ATI Radeon X300 (RV370),
	ATI Radeon X600 (RV370), ATI Radeon X550 (RV370),
	ATI FireGL V3100 (RV370), ATI FireMV 2200 PCIE (RV370),
	ATI Radeon Mobility 9200 (M9+), ATI Mobility Radeon X800 XT (M28),
	ATI Mobility FireGL V5100 (M28), ATI Mobility Radeon X800 (M28),
	ATI Radeon X850, ATI unknown Radeon / FireGL (R480),
	ATI Radeon X800XT (R423), ATI FireGL V5000 (RV410),
	ATI Radeon X700 XT (RV410), ATI Radeon X700 PRO (RV410),
	ATI Radeon X700 SE (RV410), ATI Radeon X700 (RV410),
	ATI Radeon X1800, ATI Mobility Radeon X1800 XT,
	ATI Mobility Radeon X1800, ATI Mobility FireGL V7200,
	ATI FireGL V7200, ATI FireGL V5300, ATI Mobility FireGL V7100,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1550 64-bit,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI FireGL V3300,
	ATI FireGL V3350, ATI Mobility Radeon X1450,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1650, ATI Mobility FireGL V5200,
	ATI Mobility Radeon X1600, ATI Radeon X1300 XT/X1600 Pro,
	ATI FireGL V3400, ATI Mobility FireGL V5250,
	ATI Mobility Radeon X1700, ATI Mobility Radeon X1700 XT,
	ATI FireGL V5200, ATI Radeon X2300HD, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI AMD Stream Processor,
	ATI RV560, ATI Mobility Radeon X1900, ATI Radeon X1950 GT, ATI RV570,
	ATI FireGL V7400, ATI Radeon 9100 PRO IGP,
	ATI Radeon Mobility 9200 IGP, ATI Radeon X1200, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro,
	ATI Radeon HD 2900 GT, ATI FireGL V8650, ATI FireGL V8600,
	ATI FireGL V7600, ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon HD 4850 x2, ATI FirePro V8750 (FireGL),
	ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
	ATI Mobility RADEON HD 4850 X2, ATI FirePro RV770,
	AMD FireStream 9270, AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI FirePro M7750, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI Radeon HD 2350,
	ATI Mobility Radeon HD 2400 XT, ATI Mobility Radeon HD 2400,
	ATI RADEON E2400, ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI Mobility Radeon HD 3870,
	ATI Mobility Radeon HD 3870 X2, ATI Radeon HD3870 X2,
	ATI FireGL V7700, ATI Radeon HD3690, AMD Firestream 9170,
	ATI Radeon HD 4550, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI FirePro V3700,
	ATI FireMV 2450, ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon 3000 Graphics, SUMO, SUMO2,
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
        ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
	REDWOOD, ATI Mobility Radeon Graphics, CEDAR, ATI FirePro 2270,
	ATI Radeon HD 5450, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6700 Series, TURKS, CAICOS,
	ARUBA, TAHITI, PITCAIRN, VERDE, OLAND, HAINAN, BONAIRE, KABINI,
	MULLINS, KAVERI, HAWAII
[    48.655] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    48.655] (II) FBDEV: driver for framebuffer: fbdev
[    48.655] (II) VESA: driver for VESA chipsets: vesa
[    48.656] (II) [KMS] Kernel modesetting enabled.
[    48.656] (WW) Falling back to old probe method for modesetting
[    48.656] (WW) Falling back to old probe method for fbdev
[    48.656] (II) Loading sub module "fbdevhw"
[    48.656] (II) LoadModule: "fbdevhw"
[    48.656] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    48.656] (II) Module fbdevhw: vendor="X.Org Foundation"
[    48.656] 	compiled for 1.19.3, module version = 0.0.2
[    48.656] 	ABI class: X.Org Video Driver, version 23.0
[    48.656] (WW) Falling back to old probe method for vesa
[    48.656] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    48.656] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    48.656] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    48.656] (==) RADEON(0): Default visual is TrueColor
[    48.657] (==) RADEON(0): RGB weight 888
[    48.657] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    48.657] (--) RADEON(0): Chipset: "ATI Radeon HD 5670" (ChipID = 0x68d8)
[    48.657] (II) Loading sub module "fb"
[    48.657] (II) LoadModule: "fb"
[    48.657] (II) Loading /usr/lib/xorg/modules/libfb.so
[    48.657] (II) Module fb: vendor="X.Org Foundation"
[    48.657] 	compiled for 1.19.3, module version = 1.0.0
[    48.657] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    48.657] (II) Loading sub module "dri2"
[    48.657] (II) LoadModule: "dri2"
[    48.657] (II) Module "dri2" already built-in
[    48.657] (II) Loading sub module "glamoregl"
[    48.657] (II) LoadModule: "glamoregl"
[    48.658] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    48.776] (II) Module glamoregl: vendor="X.Org Foundation"
[    48.776] 	compiled for 1.19.3, module version = 1.0.0
[    48.776] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    48.776] (II) glamor: OpenGL accelerated X.org driver based.
[    49.150] (II) glamor: EGL version 1.4 (DRI2):
[    49.163] (II) RADEON(0): glamor detected, initialising EGL layer.
[    49.164] (II) RADEON(0): KMS Color Tiling: enabled
[    49.164] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    49.164] (==) RADEON(0): TearFree property default: auto
[    49.164] (II) RADEON(0): KMS Pageflipping: enabled
[    49.165] (II) RADEON(0): Output HDMI-0 has no monitor section
[    49.180] (II) RADEON(0): Output DVI-0 has no monitor section
[    49.419] (II) RADEON(0): Output VGA-0 has no monitor section
[    49.420] (II) RADEON(0): EDID for output HDMI-0
[    49.436] (II) RADEON(0): EDID for output DVI-0
[    49.673] (II) RADEON(0): EDID for output VGA-0
[    49.673] (II) RADEON(0): Printing probed modes for output VGA-0
[    49.673] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.673] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.673] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    49.673] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    49.673] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.673] (II) RADEON(0): Output HDMI-0 disconnected
[    49.673] (II) RADEON(0): Output DVI-0 disconnected
[    49.673] (II) RADEON(0): Output VGA-0 connected
[    49.673] (II) RADEON(0): Using exact sizes for initial modes
[    49.673] (II) RADEON(0): Output VGA-0 using initial mode 1024x768 +0+0
[    49.673] (II) RADEON(0): mem size init: gart size :3fdde000 vram size: s:40000000 visible:f9b3000
[    49.673] (==) RADEON(0): DPI set to (96, 96)
[    49.673] (==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
[    49.673] (II) Loading sub module "ramdac"
[    49.673] (II) LoadModule: "ramdac"
[    49.673] (II) Module "ramdac" already built-in
[    49.673] (II) UnloadModule: "modesetting"
[    49.673] (II) Unloading modesetting
[    49.673] (II) UnloadModule: "fbdev"
[    49.673] (II) Unloading fbdev
[    49.673] (II) UnloadSubModule: "fbdevhw"
[    49.673] (II) Unloading fbdevhw
[    49.673] (II) UnloadModule: "vesa"
[    49.673] (II) Unloading vesa
[    49.673] (--) Depth 24 pixmap format is 32 bpp
[    49.673] (II) RADEON(0): [DRI2] Setup complete
[    49.673] (II) RADEON(0): [DRI2]   DRI driver: r600
[    49.673] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    49.673] (II) RADEON(0): Front buffer size: 3072K
[    49.673] (II) RADEON(0): VRAM usage limit set to 227271K
[    49.673] (II) RADEON(0): SYNC extension fences enabled
[    49.673] (II) RADEON(0): Present extension enabled
[    49.673] (==) RADEON(0): DRI3 enabled
[    49.674] (==) RADEON(0): Backing store enabled
[    49.674] (II) RADEON(0): Direct rendering enabled
[    49.696] (II) RADEON(0): Use GLAMOR acceleration.
[    49.696] (II) RADEON(0): Acceleration enabled
[    49.696] (==) RADEON(0): DPMS enabled
[    49.696] (==) RADEON(0): Silken mouse enabled
[    49.696] (II) RADEON(0): Set up textured video (glamor)
[    49.696] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[    49.696] (II) RADEON(0): [XvMC] Extension initialized.
[    49.696] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    49.696] (--) RandR disabled
[    49.698] (II) SELinux: Disabled on system
[    49.699] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    49.699] (II) AIGLX: enabled GLX_ARB_create_context
[    49.699] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    49.699] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    49.699] (II) AIGLX: enabled GLX_INTEL_swap_event
[    49.699] (II) AIGLX: enabled GLX_SGI_swap_control
[    49.699] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    49.699] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    49.699] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    49.699] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    49.699] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    49.700] (II) AIGLX: Loaded and initialized r600
[    49.700] (II) GLX: Initialized DRI2 GL provider for screen 0
[    49.701] (II) RADEON(0): Setting screen physical size to 270 x 203
[    49.846] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    49.847] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    49.847] (II) LoadModule: "libinput"
[    49.847] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    49.964] (II) Module libinput: vendor="X.Org Foundation"
[    49.964] 	compiled for 1.19.3, module version = 0.25.0
[    49.964] 	Module class: X.Org XInput Driver
[    49.964] 	ABI class: X.Org XInput driver, version 24.1
[    49.964] (II) Using input driver 'libinput' for 'Power Button'
[    49.964] (**) Power Button: always reports core events
[    49.964] (**) Option "Device" "/dev/input/event1"
[    49.964] (**) Option "_source" "server/udev"
[    49.965] (II) input device 'Power Button', /dev/input/event1 is tagged by udev as: Keyboard
[    49.965] (II) input device 'Power Button', /dev/input/event1 is a keyboard
[    49.984] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    49.984] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    49.984] (**) Option "xkb_model" "pc105"
[    49.984] (**) Option "xkb_layout" "es"
[    50.016] (II) input device 'Power Button', /dev/input/event1 is tagged by udev as: Keyboard
[    50.016] (II) input device 'Power Button', /dev/input/event1 is a keyboard
[    50.017] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    50.017] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    50.017] (II) Using input driver 'libinput' for 'Power Button'
[    50.017] (**) Power Button: always reports core events
[    50.017] (**) Option "Device" "/dev/input/event0"
[    50.017] (**) Option "_source" "server/udev"
[    50.017] (II) input device 'Power Button', /dev/input/event0 is tagged by udev as: Keyboard
[    50.017] (II) input device 'Power Button', /dev/input/event0 is a keyboard
[    50.032] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    50.032] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    50.032] (**) Option "xkb_model" "pc105"
[    50.032] (**) Option "xkb_layout" "es"
[    50.032] (II) input device 'Power Button', /dev/input/event0 is tagged by udev as: Keyboard
[    50.032] (II) input device 'Power Button', /dev/input/event0 is a keyboard
[    50.033] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event4)
[    50.033] (II) No input driver specified, ignoring this device.
[    50.033] (II) This device may have been added with another device file.
[    50.033] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[    50.033] (II) No input driver specified, ignoring this device.
[    50.033] (II) This device may have been added with another device file.
[    50.034] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event9)
[    50.034] (II) No input driver specified, ignoring this device.
[    50.034] (II) This device may have been added with another device file.
[    50.034] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event10)
[    50.034] (II) No input driver specified, ignoring this device.
[    50.034] (II) This device may have been added with another device file.
[    50.034] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event6)
[    50.034] (II) No input driver specified, ignoring this device.
[    50.034] (II) This device may have been added with another device file.
[    50.035] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[    50.035] (II) No input driver specified, ignoring this device.
[    50.035] (II) This device may have been added with another device file.
[    50.035] (II) config/udev: Adding input device Genius NetScroll + Traveler (/dev/input/event3)
[    50.035] (**) Genius NetScroll + Traveler: Applying InputClass "libinput pointer catchall"
[    50.035] (II) Using input driver 'libinput' for 'Genius NetScroll + Traveler'
[    50.035] (**) Genius NetScroll + Traveler: always reports core events
[    50.035] (**) Option "Device" "/dev/input/event3"
[    50.035] (**) Option "_source" "server/udev"
[    50.096] (II) input device 'Genius NetScroll + Traveler', /dev/input/event3 is tagged by udev as: Mouse
[    50.096] (II) input device 'Genius NetScroll + Traveler', /dev/input/event3 is a pointer caps
[    50.128] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:0458:002E.0001/input/input5/event3"
[    50.128] (II) XINPUT: Adding extended input device "Genius NetScroll + Traveler" (type: MOUSE, id 8)
[    50.128] (**) Option "AccelerationScheme" "none"
[    50.128] (**) Genius NetScroll + Traveler: (accel) selected scheme none/0
[    50.128] (**) Genius NetScroll + Traveler: (accel) acceleration factor: 2.000
[    50.128] (**) Genius NetScroll + Traveler: (accel) acceleration threshold: 4
[    50.188] (II) input device 'Genius NetScroll + Traveler', /dev/input/event3 is tagged by udev as: Mouse
[    50.188] (II) input device 'Genius NetScroll + Traveler', /dev/input/event3 is a pointer caps
[    50.189] (II) config/udev: Adding input device Genius NetScroll + Traveler (/dev/input/mouse0)
[    50.189] (II) No input driver specified, ignoring this device.
[    50.189] (II) This device may have been added with another device file.
[    50.190] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    50.190] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[    50.190] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    50.190] (**) AT Translated Set 2 keyboard: always reports core events
[    50.190] (**) Option "Device" "/dev/input/event2"
[    50.190] (**) Option "_source" "server/udev"
[    50.190] (II) input device 'AT Translated Set 2 keyboard', /dev/input/event2 is tagged by udev as: Keyboard
[    50.190] (II) input device 'AT Translated Set 2 keyboard', /dev/input/event2 is a keyboard
[    50.204] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    50.204] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    50.204] (**) Option "xkb_model" "pc105"
[    50.204] (**) Option "xkb_layout" "es"
[    50.205] (II) input device 'AT Translated Set 2 keyboard', /dev/input/event2 is tagged by udev as: Keyboard
[    50.205] (II) input device 'AT Translated Set 2 keyboard', /dev/input/event2 is a keyboard
[    50.207] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event5)
[    50.207] (**) HP WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[    50.207] (II) Using input driver 'libinput' for 'HP WMI hotkeys'
[    50.207] (**) HP WMI hotkeys: always reports core events
[    50.207] (**) Option "Device" "/dev/input/event5"
[    50.207] (**) Option "_source" "server/udev"
[    50.208] (II) input device 'HP WMI hotkeys', /dev/input/event5 is tagged by udev as: Keyboard
[    50.208] (II) input device 'HP WMI hotkeys', /dev/input/event5 is a keyboard
[    50.232] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event5"
[    50.232] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 10)
[    50.232] (**) Option "xkb_model" "pc105"
[    50.232] (**) Option "xkb_layout" "es"
[    50.233] (II) input device 'HP WMI hotkeys', /dev/input/event5 is tagged by udev as: Keyboard
[    50.233] (II) input device 'HP WMI hotkeys', /dev/input/event5 is a keyboard

---

