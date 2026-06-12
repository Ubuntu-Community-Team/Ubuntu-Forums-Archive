---
title: "Corrupted screen on boot"
date: 2017-08-03
forum: General Help
---

### Post by andrzej1k1 on 2017-08-03
[COLOR=#111111][FONT=Ubuntu]My graphic card is AMD Radeon R9 280X and because Ubuntu 16.04 does not have `fglrx` I am using Oibaf's graphic drivers. Everything was working fine, but from today after boot I see white screen with random colors:
[/FONT][/COLOR][IMG]http://i.imgur.com/JnoZGNdg.jpg[/IMG]
[IMG]http://i.imgur.com/EZMb3wUg.jpg[/IMG]
[COLOR=#111111][FONT=Ubuntu]I do not have idea what caused this, because I don't remember doing updates or modifying files. I found temporary workaround: setting `nomodeset` in grub options, but this results in very low performance.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Could you help me?

**Xorg.0.log:**
[/FONT][/COLOR]```
[     4.294] X.Org X Server 1.18.4
Release Date: 2016-07-19
[     4.294] X Protocol Version 11, Revision 0
[     4.294] Build Operating System: Linux 4.4.0-83-generic x86_64 Ubuntu
[     4.294] Current Operating System: Linux andrew-desktop 4.4.0-87-generic #110-Ubuntu SMP Tue Jul 18 12:55:35 UTC 2017 x86_64
[     4.294] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-87-generic root=UUID=6aa22517-ef14-48db-aff7-606cf7aec584 ro
[     4.294] Build Date: 17 July 2017  05:05:12PM
[     4.294] xorg-server 2:1.18.4-0ubuntu0.3 (For technical support please see http://www.ubuntu.com/support) 
[     4.294] Current version of pixman: 0.33.6
[     4.294]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.294] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.294] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  3 11:37:38 2017
[     4.295] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.295] (==) No Layout section.  Using the first Screen section.
[     4.295] (==) No screen section available. Using defaults.
[     4.295] (**) |-->Screen "Default Screen Section" (0)
[     4.295] (**) |   |-->Monitor "<default monitor>"
[     4.295] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     4.296] (==) Automatically adding devices
[     4.296] (==) Automatically enabling devices
[     4.296] (==) Automatically adding GPU devices
[     4.296] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     4.296] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.296]     Entry deleted from font path.
[     4.299] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[     4.299] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.299] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.300] (II) Loader magic: 0x561dd161ddc0
[     4.300] (II) Module ABI versions:
[     4.300]     X.Org ANSI C Emulation: 0.4
[     4.300]     X.Org Video Driver: 20.0
[     4.300]     X.Org XInput driver : 22.1
[     4.300]     X.Org Server Extension : 9.0
[     4.300] (++) using VT number 7


[     4.301] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     4.301] (II) xfree86: Adding drm device (/dev/dri/card0)
[     4.302] (--) PCI:*(0:1:0:0) 1002:6798:1458:3001 rev 0, Mem @ 0xe0000000/268435456, 0xf7e00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[     4.302] (II) LoadModule: "glx"
[     4.308] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     4.319] (II) Module glx: vendor="X.Org Foundation"
[     4.319]     compiled for 1.18.4, module version = 1.0.0
[     4.319]     ABI class: X.Org Server Extension, version 9.0
[     4.319] (==) AIGLX enabled
[     4.319] (II) Applying OutputClass "Radeon" to /dev/dri/card0
[     4.319]     loading driver: radeon
[     4.319] (==) Matched radeon as autoconfigured driver 0
[     4.319] (==) Matched ati as autoconfigured driver 1
[     4.319] (==) Matched ati as autoconfigured driver 2
[     4.319] (==) Matched modesetting as autoconfigured driver 3
[     4.319] (==) Matched fbdev as autoconfigured driver 4
[     4.319] (==) Matched vesa as autoconfigured driver 5
[     4.319] (==) Assigned the driver to the xf86ConfigLayout
[     4.319] (II) LoadModule: "radeon"
[     4.320] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     4.324] (II) Module radeon: vendor="X.Org Foundation"
[     4.324]     compiled for 1.18.4, module version = 7.9.99
[     4.324]     Module class: X.Org Video Driver
[     4.324]     ABI class: X.Org Video Driver, version 20.0
[     4.324] (II) LoadModule: "ati"
[     4.324] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     4.324] (II) Module ati: vendor="X.Org Foundation"
[     4.324]     compiled for 1.18.4, module version = 7.9.99
[     4.324]     Module class: X.Org Video Driver
[     4.324]     ABI class: X.Org Video Driver, version 20.0
[     4.389] (II) LoadModule: "modesetting"
[     4.389] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.390] (II) Module modesetting: vendor="X.Org Foundation"
[     4.390]     compiled for 1.18.4, module version = 1.18.4
[     4.390]     Module class: X.Org Video Driver
[     4.390]     ABI class: X.Org Video Driver, version 20.0
[     4.390] (II) LoadModule: "fbdev"
[     4.390] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.390] (II) Module fbdev: vendor="X.Org Foundation"
[     4.390]     compiled for 1.18.1, module version = 0.4.4
[     4.390]     Module class: X.Org Video Driver
[     4.390]     ABI class: X.Org Video Driver, version 20.0
[     4.390] (II) LoadModule: "vesa"
[     4.390] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.390] (II) Module vesa: vendor="X.Org Foundation"
[     4.390]     compiled for 1.18.1, module version = 2.3.4
[     4.390]     Module class: X.Org Video Driver
[     4.390]     ABI class: X.Org Video Driver, version 20.0
[     4.390] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
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
    ATI Radeon HD 5670, ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
    REDWOOD, ATI Mobility Radeon Graphics, CEDAR, ATI FirePro 2270,
    ATI Radeon HD 5450, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6700 Series, TURKS, CAICOS,
    ARUBA, TAHITI, PITCAIRN, VERDE, OLAND, HAINAN, BONAIRE, KABINI,
    MULLINS, KAVERI, HAWAII
[     4.391] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.391] (II) FBDEV: driver for framebuffer: fbdev
[     4.391] (II) VESA: driver for VESA chipsets: vesa
[     4.397] (II) [KMS] Kernel modesetting enabled.
[     4.397] (WW) Falling back to old probe method for modesetting
[     4.397] (WW) Falling back to old probe method for fbdev
[     4.397] (II) Loading sub module "fbdevhw"
[     4.397] (II) LoadModule: "fbdevhw"
[     4.397] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.397] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.397]     compiled for 1.18.4, module version = 0.0.2
[     4.397]     ABI class: X.Org Video Driver, version 20.0
[     4.397] (WW) Falling back to old probe method for vesa
[     4.397] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     4.397] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[     4.397] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     4.397] (==) RADEON(0): Default visual is TrueColor
[     4.397] (==) RADEON(0): RGB weight 888
[     4.397] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[     4.397] (--) RADEON(0): Chipset: "TAHITI" (ChipID = 0x6798)
[     4.397] (II) Loading sub module "fb"
[     4.397] (II) LoadModule: "fb"
[     4.397] (II) Loading /usr/lib/xorg/modules/libfb.so
[     4.398] (II) Module fb: vendor="X.Org Foundation"
[     4.398]     compiled for 1.18.4, module version = 1.0.0
[     4.398]     ABI class: X.Org ANSI C Emulation, version 0.4
[     4.398] (II) Loading sub module "dri2"
[     4.398] (II) LoadModule: "dri2"
[     4.398] (II) Module "dri2" already built-in
[     4.398] (II) Loading sub module "glamoregl"
[     4.398] (II) LoadModule: "glamoregl"
[     4.398] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[     4.407] (II) Module glamoregl: vendor="X.Org Foundation"
[     4.407]     compiled for 1.18.4, module version = 1.0.0
[     4.407]     ABI class: X.Org ANSI C Emulation, version 0.4
[     4.407] (II) glamor: OpenGL accelerated X.org driver based.
[     4.556] (II) glamor: EGL version 1.5 (DRI2):
[     4.562] (II) RADEON(0): glamor detected, initialising EGL layer.
[     4.563] (II) RADEON(0): KMS Color Tiling: enabled
[     4.563] (II) RADEON(0): KMS Color Tiling 2D: enabled
[     4.563] (==) RADEON(0): TearFree property default: auto
[     4.563] (II) RADEON(0): KMS Pageflipping: enabled
[     4.568] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[     4.576] (II) RADEON(0): Output DisplayPort-1 has no monitor section
[     4.630] (II) RADEON(0): Output HDMI-0 has no monitor section
[     4.644] (II) RADEON(0): Output DVI-0 has no monitor section
[     4.652] (II) RADEON(0): EDID for output DisplayPort-0
[     4.660] (II) RADEON(0): EDID for output DisplayPort-1
[     4.714] (II) RADEON(0): EDID for output HDMI-0
[     4.714] (II) RADEON(0): Manufacturer: GSM  Model: 5ab8  Serial#: 16843009
[     4.714] (II) RADEON(0): Year: 2014  Week: 1
[     4.714] (II) RADEON(0): EDID Version: 1.3
[     4.714] (II) RADEON(0): Digital Display Input
[     4.714] (II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[     4.714] (II) RADEON(0): Gamma: 2.20
[     4.714] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[     4.714] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     4.714] (II) RADEON(0): First detailed timing is preferred mode
[     4.714] (II) RADEON(0): redX: 0.645 redY: 0.335   greenX: 0.305 greenY: 0.630
[     4.714] (II) RADEON(0): blueX: 0.148 blueY: 0.050   whiteX: 0.313 whiteY: 0.329
[     4.714] (II) RADEON(0): Supported established timings:
[     4.714] (II) RADEON(0): 720x400@70Hz
[     4.714] (II) RADEON(0): 640x480@60Hz
[     4.714] (II) RADEON(0): 640x480@75Hz
[     4.714] (II) RADEON(0): 800x600@60Hz
[     4.714] (II) RADEON(0): 800x600@75Hz
[     4.714] (II) RADEON(0): 1024x768@60Hz
[     4.714] (II) RADEON(0): 1024x768@75Hz
[     4.714] (II) RADEON(0): 1280x1024@75Hz
[     4.714] (II) RADEON(0): Manufacturer's mask: 0
[     4.714] (II) RADEON(0): Supported standard timings:
[     4.714] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     4.714] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     4.714] (II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     4.714] (II) RADEON(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     4.714] (II) RADEON(0): #4: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[     4.714] (II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     4.714] (II) RADEON(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     4.714] (II) RADEON(0): #7: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[     4.714] (II) RADEON(0): Supported detailed timing:
[     4.714] (II) RADEON(0): clock: 148.5 MHz   Image Size:  480 x 270 mm
[     4.714] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     4.714] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     4.714] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[     4.714] (II) RADEON(0): Monitor name: LG IPS FULLHD
[     4.714] (II) RADEON(0): Serial No: 
[     4.714] (II) RADEON(0): Supported detailed timing:
[     4.714] (II) RADEON(0): clock: 148.5 MHz   Image Size:  480 x 270 mm
[     4.714] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     4.714] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     4.714] (II) RADEON(0): Supported detailed timing:
[     4.714] (II) RADEON(0): clock: 74.2 MHz   Image Size:  480 x 270 mm
[     4.714] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     4.714] (II) RADEON(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     4.714] (II) RADEON(0): Supported detailed timing:
[     4.714] (II) RADEON(0): clock: 74.2 MHz   Image Size:  480 x 270 mm
[     4.714] (II) RADEON(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[     4.714] (II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     4.714] (II) RADEON(0): Supported detailed timing:
[     4.714] (II) RADEON(0): clock: 27.0 MHz   Image Size:  480 x 270 mm
[     4.714] (II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[     4.714] (II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[     4.714] (II) RADEON(0): Number of EDID sections to follow: 1
[     4.714] (II) RADEON(0): EDID (in hex):
[     4.714] (II) RADEON(0):     00ffffffffffff001e6db85a01010101
[     4.714] (II) RADEON(0):     0118010380301b78ea3135a5554ea126
[     4.714] (II) RADEON(0):     0c5054a54b00714f81809500b300a9c0
[     4.714] (II) RADEON(0):     810081c09040023a801871382d40582c
[     4.714] (II) RADEON(0):     4500e00e1100001e000000fd00384b1e
[     4.714] (II) RADEON(0):     530f000a202020202020000000fc004c
[     4.714] (II) RADEON(0):     47204950532046554c4c4844000000ff
[     4.714] (II) RADEON(0):     000a2020202020202020202020200164
[     4.714] (II) RADEON(0):     02031df14a900403011412051f101323
[     4.714] (II) RADEON(0):     0907078301000065030c001000023a80
[     4.714] (II) RADEON(0):     1871382d40582c4500e00e1100001e01
[     4.714] (II) RADEON(0):     1d8018711c1620582c2500e00e110000
[     4.714] (II) RADEON(0):     9e011d007251d01e206e285500e00e11
[     4.714] (II) RADEON(0):     00001e8c0ad08a20e02d10103e9600e0
[     4.714] (II) RADEON(0):     0e110000180000000000000000000000
[     4.714] (II) RADEON(0):     000000000000000000000000000000ae
[     4.714] (II) RADEON(0): Printing probed modes for output HDMI-0
[     4.714] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     4.714] (II) RADEON(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[     4.714] (II) RADEON(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[     4.714] (II) RADEON(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     4.714] (II) RADEON(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     4.714] (II) RADEON(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[     4.714] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     4.714] (II) RADEON(0): Modeline "1400x1050"x59.9  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz e)
[     4.714] (II) RADEON(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz e)
[     4.714] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     4.714] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     4.714] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     4.714] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     4.714] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     4.714] (II) RADEON(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     4.714] (II) RADEON(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     4.714] (II) RADEON(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     4.714] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     4.714] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     4.715] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     4.715] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     4.715] (II) RADEON(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     4.715] (II) RADEON(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     4.715] (II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     4.715] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     4.715] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     4.715] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     4.715] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     4.728] (II) RADEON(0): EDID for output DVI-0
[     4.728] (II) RADEON(0): Output DisplayPort-0 disconnected
[     4.728] (II) RADEON(0): Output DisplayPort-1 disconnected
[     4.728] (II) RADEON(0): Output HDMI-0 connected
[     4.728] (II) RADEON(0): Output DVI-0 disconnected
[     4.728] (II) RADEON(0): Using exact sizes for initial modes
[     4.728] (II) RADEON(0): Output HDMI-0 using initial mode 1920x1080 +0+0
[     4.728] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     4.728] (II) RADEON(0): mem size init: gart size :7fbcc000 vram size: s:c0000000 visible:bf12d000
[     4.728] (==) RADEON(0): DPI set to (96, 96)
[     4.728] (II) Loading sub module "ramdac"
[     4.728] (II) LoadModule: "ramdac"
[     4.728] (II) Module "ramdac" already built-in
[     4.728] (II) UnloadModule: "modesetting"
[     4.728] (II) Unloading modesetting
[     4.728] (II) UnloadModule: "fbdev"
[     4.728] (II) Unloading fbdev
[     4.728] (II) UnloadSubModule: "fbdevhw"
[     4.728] (II) Unloading fbdevhw
[     4.728] (II) UnloadModule: "vesa"
[     4.728] (II) Unloading vesa
[     4.728] (--) Depth 24 pixmap format is 32 bpp
[     4.729] (II) RADEON(0): [DRI2] Setup complete
[     4.729] (II) RADEON(0): [DRI2]   DRI driver: radeonsi
[     4.729] (II) RADEON(0): [DRI2]   VDPAU driver: radeonsi
[     4.729] (II) RADEON(0): Front buffer size: 8640K
[     4.729] (II) RADEON(0): VRAM usage limit set to 2809630K
[     4.730] (II) RADEON(0): SYNC extension fences enabled
[     4.730] (II) RADEON(0): Present extension enabled
[     4.730] (==) RADEON(0): DRI3 enabled
[     4.730] (==) RADEON(0): Backing store enabled
[     4.730] (II) RADEON(0): Direct rendering enabled
[     4.743] (II) RADEON(0): Use GLAMOR acceleration.
[     4.743] (II) RADEON(0): Acceleration enabled
[     4.743] (==) RADEON(0): DPMS enabled
[     4.743] (==) RADEON(0): Silken mouse enabled
[     4.744] (II) RADEON(0): Set up textured video (glamor)
[     4.744] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[     4.744] (II) RADEON(0): [XvMC] Extension initialized.
[     4.744] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     4.744] (--) RandR disabled
[     4.748] (II) SELinux: Disabled on system
[     4.749] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     4.749] (II) AIGLX: enabled GLX_ARB_create_context
[     4.749] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     4.749] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[     4.749] (II) AIGLX: enabled GLX_INTEL_swap_event
[     4.749] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     4.749] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     4.749] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     4.749] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[     4.749] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     4.749] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     4.750] (II) AIGLX: Loaded and initialized radeonsi
[     4.750] (II) GLX: Initialized DRI2 GL provider for screen 0
[     4.751] (II) RADEON(0): Setting screen physical size to 508 x 285
[     4.847] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     4.847] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.847] (II) LoadModule: "evdev"
[     4.847] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.849] (II) Module evdev: vendor="X.Org Foundation"
[     4.849]     compiled for 1.18.1, module version = 2.10.1
[     4.849]     Module class: X.Org XInput Driver
[     4.849]     ABI class: X.Org XInput driver, version 22.1
[     4.849] (II) Using input driver 'evdev' for 'Power Button'
[     4.849] (**) Power Button: always reports core events
[     4.849] (**) evdev: Power Button: Device: "/dev/input/event1"
[     4.849] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.849] (--) evdev: Power Button: Found keys
[     4.849] (II) evdev: Power Button: Configuring as keyboard
[     4.849] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     4.849] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     4.849] (**) Option "xkb_rules" "evdev"
[     4.849] (**) Option "xkb_model" "pc105"
[     4.849] (**) Option "xkb_layout" "pl"
[     4.849] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[     4.862] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     4.862] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.862] (II) Using input driver 'evdev' for 'Power Button'
[     4.862] (**) Power Button: always reports core events
[     4.862] (**) evdev: Power Button: Device: "/dev/input/event0"
[     4.862] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.862] (--) evdev: Power Button: Found keys
[     4.862] (II) evdev: Power Button: Configuring as keyboard
[     4.862] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     4.862] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     4.862] (**) Option "xkb_rules" "evdev"
[     4.862] (**) Option "xkb_model" "pc105"
[     4.862] (**) Option "xkb_layout" "pl"
[     4.862] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[     4.863] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event10)
[     4.863] (II) No input driver specified, ignoring this device.
[     4.863] (II) This device may have been added with another device file.
[     4.863] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event11)
[     4.863] (II) No input driver specified, ignoring this device.
[     4.863] (II) This device may have been added with another device file.
[     4.863] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event6)
[     4.863] (II) No input driver specified, ignoring this device.
[     4.863] (II) This device may have been added with another device file.
[     4.863] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event7)
[     4.863] (II) No input driver specified, ignoring this device.
[     4.864] (II) This device may have been added with another device file.
[     4.864] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event8)
[     4.864] (II) No input driver specified, ignoring this device.
[     4.864] (II) This device may have been added with another device file.
[     4.864] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event9)
[     4.864] (II) No input driver specified, ignoring this device.
[     4.864] (II) This device may have been added with another device file.
[     4.864] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event12)
[     4.864] (II) No input driver specified, ignoring this device.
[     4.864] (II) This device may have been added with another device file.
[     4.864] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event13)
[     4.864] (II) No input driver specified, ignoring this device.
[     4.864] (II) This device may have been added with another device file.
[     4.864] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event14)
[     4.864] (II) No input driver specified, ignoring this device.
[     4.864] (II) This device may have been added with another device file.
[     4.865] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event15)
[     4.865] (II) No input driver specified, ignoring this device.
[     4.865] (II) This device may have been added with another device file.
[     4.865] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event16)
[     4.865] (II) No input driver specified, ignoring this device.
[     4.865] (II) This device may have been added with another device file.
[     4.865] (II) config/udev: Adding input device COMPANY USB Device (/dev/input/event3)
[     4.865] (**) COMPANY USB Device: Applying InputClass "evdev keyboard catchall"
[     4.865] (II) Using input driver 'evdev' for 'COMPANY USB Device'
[     4.865] (**) COMPANY USB Device: always reports core events
[     4.865] (**) evdev: COMPANY USB Device: Device: "/dev/input/event3"
[     4.865] (--) evdev: COMPANY USB Device: Vendor 0x9da Product 0x1305
[     4.865] (--) evdev: COMPANY USB Device: Found keys
[     4.865] (II) evdev: COMPANY USB Device: Configuring as keyboard
[     4.865] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/0003:09DA:1305.0001/input/input3/event3"
[     4.865] (II) XINPUT: Adding extended input device "COMPANY USB Device" (type: KEYBOARD, id 8)
[     4.865] (**) Option "xkb_rules" "evdev"
[     4.865] (**) Option "xkb_model" "pc105"
[     4.865] (**) Option "xkb_layout" "pl"
[     4.865] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[     4.866] (II) config/udev: Adding input device COMPANY USB Device (/dev/input/event4)
[     4.866] (**) COMPANY USB Device: Applying InputClass "evdev pointer catchall"
[     4.866] (**) COMPANY USB Device: Applying InputClass "Set mouse acceleration to zero"
[     4.866] (II) Using input driver 'evdev' for 'COMPANY USB Device'
[     4.866] (**) COMPANY USB Device: always reports core events
[     4.866] (**) evdev: COMPANY USB Device: Device: "/dev/input/event4"
[     4.920] (--) evdev: COMPANY USB Device: Vendor 0x9da Product 0x1305
[     4.920] (--) evdev: COMPANY USB Device: Found 12 mouse buttons
[     4.920] (--) evdev: COMPANY USB Device: Found scroll wheel(s)
[     4.920] (--) evdev: COMPANY USB Device: Found relative axes
[     4.920] (--) evdev: COMPANY USB Device: Found x and y relative axes
[     4.920] (II) evdev: COMPANY USB Device: Configuring as mouse
[     4.920] (II) evdev: COMPANY USB Device: Adding scrollwheel support
[     4.920] (**) evdev: COMPANY USB Device: YAxisMapping: buttons 4 and 5
[     4.920] (**) evdev: COMPANY USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.920] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/0003:09DA:1305.0002/input/input4/event4"
[     4.920] (II) XINPUT: Adding extended input device "COMPANY USB Device" (type: MOUSE, id 9)
[     4.920] (II) evdev: COMPANY USB Device: initialized for relative axes.
[     4.920] (**) Option "AccelerationScheme" "none"
[     4.920] (**) COMPANY USB Device: (accel) selected scheme none/0
[     4.920] (**) Option "AccelerationNumerator" "0"
[     4.920] (**) Option "AccelerationDenominator" "1"
[     4.920] (**) Option "AccelerationThreshold" "4"
[     4.920] (**) COMPANY USB Device: (accel) acceleration factor: 0.000
[     4.920] (**) COMPANY USB Device: (accel) acceleration threshold: 4
[     4.920] (II) config/udev: Adding input device COMPANY USB Device (/dev/input/mouse0)
[     4.920] (II) No input driver specified, ignoring this device.
[     4.920] (II) This device may have been added with another device file.
[     4.921] (II) config/udev: Adding input device COMPANY USB Device (/dev/input/event5)
[     4.921] (**) COMPANY USB Device: Applying InputClass "evdev keyboard catchall"
[     4.921] (II) Using input driver 'evdev' for 'COMPANY USB Device'
[     4.921] (**) COMPANY USB Device: always reports core events
[     4.921] (**) evdev: COMPANY USB Device: Device: "/dev/input/event5"
[     4.921] (--) evdev: COMPANY USB Device: Vendor 0x9da Product 0x1305
[     4.921] (--) evdev: COMPANY USB Device: Found 1 mouse buttons
[     4.921] (--) evdev: COMPANY USB Device: Found scroll wheel(s)
[     4.921] (--) evdev: COMPANY USB Device: Found relative axes
[     4.921] (--) evdev: COMPANY USB Device: Found absolute axes
[     4.921] (--) evdev: COMPANY USB Device: Found absolute multitouch axes
[     4.921] (--) evdev: COMPANY USB Device: Fake MT device detected
[     4.921] (--) evdev: COMPANY USB Device: Found x and y absolute axes
[     4.921] (--) evdev: COMPANY USB Device: Found keys
[     4.921] (II) evdev: COMPANY USB Device: Forcing relative x/y axes to exist.
[     4.921] (II) evdev: COMPANY USB Device: Configuring as mouse
[     4.921] (II) evdev: COMPANY USB Device: Configuring as keyboard
[     4.921] (II) evdev: COMPANY USB Device: Adding scrollwheel support
[     4.921] (**) evdev: COMPANY USB Device: YAxisMapping: buttons 4 and 5
[     4.921] (**) evdev: COMPANY USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.921] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:09DA:1305.0003/input/input5/event5"
[     4.921] (II) XINPUT: Adding extended input device "COMPANY USB Device" (type: KEYBOARD, id 10)
[     4.921] (**) Option "xkb_rules" "evdev"
[     4.921] (**) Option "xkb_model" "pc105"
[     4.921] (**) Option "xkb_layout" "pl"
[     4.921] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[     4.921] (II) evdev: COMPANY USB Device: initialized for relative axes.
[     4.921] (WW) evdev: COMPANY USB Device: ignoring absolute axes.
[     4.921] (**) COMPANY USB Device: (accel) keeping acceleration scheme 1
[     4.921] (**) COMPANY USB Device: (accel) acceleration profile 0
[     4.921] (**) COMPANY USB Device: (accel) acceleration factor: 2.000
[     4.921] (**) COMPANY USB Device: (accel) acceleration threshold: 4
[     4.921] (II) config/udev: Adding input device COMPANY USB Device (/dev/input/js0)
[     4.921] (II) No input driver specified, ignoring this device.
[     4.921] (II) This device may have been added with another device file.
[     4.922] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event17)
[     4.922] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     4.922] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     4.922] (**) Eee PC WMI hotkeys: always reports core events
[     4.922] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event17"
[     4.922] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     4.922] (--) evdev: Eee PC WMI hotkeys: Found keys
[     4.922] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     4.922] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input17/event17"
[     4.922] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)
[     4.922] (**) Option "xkb_rules" "evdev"
[     4.922] (**) Option "xkb_model" "pc105"
[     4.922] (**) Option "xkb_layout" "pl"
[     4.922] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[     4.922] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[     4.922] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     4.922] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     4.922] (**) AT Translated Set 2 keyboard: always reports core events
[     4.922] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[     4.922] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     4.922] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     4.922] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     4.922] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[     4.922] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[     4.922] (**) Option "xkb_rules" "evdev"
[     4.922] (**) Option "xkb_model" "pc105"
[     4.922] (**) Option "xkb_layout" "pl"
[     4.922] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[     5.776] (II) RADEON(0): EDID vendor "GSM", prod id 23224
[     5.776] (II) RADEON(0): Using EDID range info for horizontal sync
[     5.776] (II) RADEON(0): Using EDID range info for vertical refresh
[     5.776] (II) RADEON(0): Printing DDC gathered Modelines:
[     5.776] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     5.776] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     5.776] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     5.776] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     5.776] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     5.776] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     5.776] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     5.776] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     5.776] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     5.776] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     5.776] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     5.776] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     5.776] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     5.776] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     5.776] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     5.776] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     5.776] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[     5.776] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     5.776] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     5.776] (II) RADEON(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz e)
[     5.776] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     5.776] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     5.776] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     5.776] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     5.776] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     5.776] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     6.014] (II) RADEON(0): EDID vendor "GSM", prod id 23224
[     6.014] (II) RADEON(0): Using hsync ranges from config file
[     6.014] (II) RADEON(0): Using vrefresh ranges from config file
[     6.014] (II) RADEON(0): Printing DDC gathered Modelines:
[     6.014] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     6.014] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     6.014] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     6.014] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     6.014] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     6.014] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     6.014] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     6.014] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     6.014] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     6.014] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     6.014] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     6.014] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     6.014] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     6.014] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     6.014] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     6.015] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     6.015] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[     6.015] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     6.015] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     6.015] (II) RADEON(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz e)
[     6.015] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     6.015] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     6.015] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     6.015] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     6.015] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     6.015] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    73.164] (II) AIGLX: Suspending AIGLX clients for VT switch
```

**Edit:** 
I fixed it [https://askubuntu.com/questions/942234/blank-screen-after-boot-on-radeon-r9-280x/942589#942589](https://askubuntu.com/questions/942234/blank-screen-after-boot-on-radeon-r9-280x/942589#942589)

---

