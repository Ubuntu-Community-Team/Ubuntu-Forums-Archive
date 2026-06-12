---
title: "Graphics problem after upgrade to 18.04"
date: 2019-01-27
forum: General Help
---

### Post by dfpd62 on 2019-01-27
Hi Folks,

Just upgraded to 18.04 and have found issues with I presume is the graphics driver.
the machine boots OK to a blank purple screen, if I press enter and type my password I get my normal desktop wallpaper and reselution.
the problem is that i have nothing else, no icons, no sidebar, no info bar at the top of the screen.
the only thing that works is right clicking on the desktop and choosing "Terminal" I can work from there and it works pretty well.
at Reboot I can choose rescue and start with failsafe graphics, that works as it should but with low reselution, icons,sidebar and activities bar work too.
this may give information that I dont fully understand
```
dd@dd-desktop:~$ sudo lshw -C video
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:c0000-dffff

```
I recon the first 2 lines "Display UNCLAIMED"
"vga compatible controller" mean i'm missing the correct Driver.

All the advice i have found relates to the "fglrx" driver which i believe should not be used after 14.04. (BinaryDriverHowto/AMD)


Any advice on what driver to install would be appreciated as I have not found anything in "Additional Drivers" in the Software centre.

Thanks in advance for any help. D

---

### Post by dmnur on 2019-01-27
> product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
**Caicos** cards should be fully supported by **xserver-xorg-video-radeon** (see [here](https://help.ubuntu.com/community/RadeonDriver#Fully_supported)).

For us to see what driver Xorg tries to use, please post your X log: **/var/log/Xorg.0.log**

---

### Post by dfpd62 on 2019-01-27
```
[    30.067] (--) Log file renamed from "/var/log/Xorg.pid-1610.log" to "/var/log/Xorg.0.log"
[    30.067] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[    30.067] X Protocol Version 11, Revision 0
[    30.067] Build Operating System: Linux 4.4.0-138-generic x86_64 Ubuntu
[    30.067] Current Operating System: Linux dd-desktop 4.15.0-43-generic #46-Ubuntu SMP Thu Dec 6 14:45:28 UTC 2018 x86_64
[    30.067] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-43-generic root=UUID=9608e06e-826b-414e-a731-43bd417a7e7a ro recovery nomodeset
[    30.067] Build Date: 25 October 2018  04:11:27PM
[    30.068] xorg-server 2:1.19.6-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    30.068] Current version of pixman: 0.34.0
[    30.068] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    30.068] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.068] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 27 12:57:24 2019
[    30.068] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.069] (==) No Layout section.  Using the first Screen section.
[    30.069] (==) No screen section available. Using defaults.
[    30.069] (**) |-->Screen "Default Screen Section" (0)
[    30.069] (**) |   |-->Monitor "<default monitor>"
[    30.069] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    30.069] (==) Automatically adding devices
[    30.069] (==) Automatically enabling devices
[    30.069] (==) Automatically adding GPU devices
[    30.069] (==) Automatically binding GPU devices
[    30.069] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    30.069] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.069] 	Entry deleted from font path.
[    30.069] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    30.069] 	Entry deleted from font path.
[    30.070] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    30.070] 	Entry deleted from font path.
[    30.070] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    30.070] 	Entry deleted from font path.
[    30.070] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    30.070] 	Entry deleted from font path.
[    30.070] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    30.070] (==) ModulePath set to "/usr/lib/xorg/modules"
[    30.070] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.070] (II) Loader magic: 0x55afc2a63020
[    30.070] (II) Module ABI versions:
[    30.070] 	X.Org ANSI C Emulation: 0.4
[    30.070] 	X.Org Video Driver: 23.0
[    30.070] 	X.Org XInput driver : 24.1
[    30.070] 	X.Org Server Extension : 10.0
[    30.070] (++) using VT number 1

[    30.072] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c2
[    30.076] (--) PCI:*(0:1:0:0) 1002:6779:174b:e204 rev 0, Mem @ 0xc0000000/268435456, 0xfea20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    30.076] (II) LoadModule: "glx"
[    30.076] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.077] (II) Module glx: vendor="X.Org Foundation"
[    30.077] 	compiled for 1.19.6, module version = 1.0.0
[    30.077] 	ABI class: X.Org Server Extension, version 10.0
[    30.077] (==) Matched ati as autoconfigured driver 0
[    30.077] (==) Matched modesetting as autoconfigured driver 1
[    30.077] (==) Matched fbdev as autoconfigured driver 2
[    30.077] (==) Matched vesa as autoconfigured driver 3
[    30.077] (==) Assigned the driver to the xf86ConfigLayout
[    30.077] (II) LoadModule: "ati"
[    30.077] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    30.077] (II) Module ati: vendor="X.Org Foundation"
[    30.077] 	compiled for 1.19.6, module version = 18.0.1
[    30.077] 	Module class: X.Org Video Driver
[    30.077] 	ABI class: X.Org Video Driver, version 23.0
[    30.141] (II) LoadModule: "radeon"
[    30.142] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    30.144] (II) Module radeon: vendor="X.Org Foundation"
[    30.144] 	compiled for 1.19.6, module version = 18.0.1
[    30.144] 	Module class: X.Org Video Driver
[    30.144] 	ABI class: X.Org Video Driver, version 23.0
[    30.144] (II) LoadModule: "modesetting"
[    30.144] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.144] (II) Module modesetting: vendor="X.Org Foundation"
[    30.144] 	compiled for 1.19.6, module version = 1.19.6
[    30.144] 	Module class: X.Org Video Driver
[    30.144] 	ABI class: X.Org Video Driver, version 23.0
[    30.144] (II) LoadModule: "fbdev"
[    30.145] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.145] (II) Module fbdev: vendor="X.Org Foundation"
[    30.145] 	compiled for 1.19.3, module version = 0.4.4
[    30.145] 	Module class: X.Org Video Driver
[    30.145] 	ABI class: X.Org Video Driver, version 23.0
[    30.145] (II) LoadModule: "vesa"
[    30.145] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.145] (II) Module vesa: vendor="X.Org Foundation"
[    30.145] 	compiled for 1.19.3, module version = 2.3.4
[    30.145] 	Module class: X.Org Video Driver
[    30.145] 	ABI class: X.Org Video Driver, version 23.0
[    30.145] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
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
[    30.149] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.149] (II) FBDEV: driver for framebuffer: fbdev
[    30.149] (II) VESA: driver for VESA chipsets: vesa
[    30.149] xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
[    30.150] (II) [KMS] drm report modesetting isn't supported.
[    30.150] (EE) open /dev/dri/card0: No such file or directory
[    30.150] (WW) Falling back to old probe method for modesetting
[    30.150] (EE) open /dev/dri/card0: No such file or directory
[    30.150] (II) Loading sub module "fbdevhw"
[    30.150] (II) LoadModule: "fbdevhw"
[    30.150] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.150] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.150] 	compiled for 1.19.6, module version = 0.0.2
[    30.150] 	ABI class: X.Org Video Driver, version 23.0
[    30.150] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[    30.150] (II) FBDEV(2): using default device
[    30.150] (WW) Falling back to old probe method for vesa
[    30.150] (EE) Screen 0 deleted because of no matching config section.
[    30.150] (II) UnloadModule: "radeon"
[    30.150] (EE) Screen 0 deleted because of no matching config section.
[    30.150] (II) UnloadModule: "modesetting"
[    30.150] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    30.150] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    30.150] (==) FBDEV(0): RGB weight 888
[    30.150] (==) FBDEV(0): Default visual is TrueColor
[    30.150] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.150] (II) FBDEV(0): hardware: EFI VGA (video memory: 3072kB)
[    30.150] (II) FBDEV(0): checking modes against framebuffer device...
[    30.150] (II) FBDEV(0): checking modes against monitor...
[    30.150] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    30.150] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz
[    30.150] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz b)
[    30.150] (==) FBDEV(0): DPI set to (96, 96)
[    30.150] (II) Loading sub module "fb"
[    30.150] (II) LoadModule: "fb"
[    30.151] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.151] (II) Module fb: vendor="X.Org Foundation"
[    30.151] 	compiled for 1.19.6, module version = 1.0.0
[    30.151] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.151] (**) FBDEV(0): using shadow framebuffer
[    30.151] (II) Loading sub module "shadow"
[    30.151] (II) LoadModule: "shadow"
[    30.151] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    30.152] (II) Module shadow: vendor="X.Org Foundation"
[    30.152] 	compiled for 1.19.6, module version = 1.1.0
[    30.152] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.152] (II) UnloadModule: "vesa"
[    30.152] (II) Unloading vesa
[    30.152] (==) Depth 24 pixmap format is 32 bpp
[    30.152] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    30.154] (==) FBDEV(0): Backing store enabled
[    30.154] (==) FBDEV(0): DPMS enabled
[    30.154] (==) RandR enabled
[    30.158] (II) SELinux: Disabled on system
[    30.158] (II) AIGLX: Screen 0 is not DRI2 capable
[    30.158] (EE) AIGLX: reverting to software rendering
[    30.197] (II) IGLX: enabled GLX_MESA_copy_sub_buffer
[    30.198] (II) IGLX: Loaded and initialized swrast
[    30.198] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    30.243] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    30.243] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.243] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    30.243] (II) LoadModule: "libinput"
[    30.243] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    30.249] (II) Module libinput: vendor="X.Org Foundation"
[    30.249] 	compiled for 1.19.6, module version = 0.27.1
[    30.250] 	Module class: X.Org XInput Driver
[    30.250] 	ABI class: X.Org XInput driver, version 24.1
[    30.250] (II) Using input driver 'libinput' for 'Power Button'
[    30.252] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 22 paused 0
[    30.253] (**) Power Button: always reports core events
[    30.253] (**) Option "Device" "/dev/input/event1"
[    30.253] (**) Option "_source" "server/udev"
[    30.254] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    30.254] (II) event1  - Power Button: device is a keyboard
[    30.254] (II) event1  - Power Button: device removed
[    30.254] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    30.254] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.254] (**) Option "xkb_model" "pc105"
[    30.254] (**) Option "xkb_layout" "gb"
[    30.272] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    30.272] (II) event1  - Power Button: device is a keyboard
[    30.273] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.273] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.273] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    30.273] (II) Using input driver 'libinput' for 'Power Button'
[    30.274] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 25 paused 0
[    30.274] (**) Power Button: always reports core events
[    30.274] (**) Option "Device" "/dev/input/event0"
[    30.274] (**) Option "_source" "server/udev"
[    30.274] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    30.274] (II) event0  - Power Button: device is a keyboard
[    30.274] (II) event0  - Power Button: device removed
[    30.274] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    30.274] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    30.274] (**) Option "xkb_model" "pc105"
[    30.274] (**) Option "xkb_layout" "gb"
[    30.275] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    30.275] (II) event0  - Power Button: device is a keyboard
[    30.275] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event7)
[    30.275] (II) No input driver specified, ignoring this device.
[    30.275] (II) This device may have been added with another device file.
[    30.276] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/event3)
[    30.276] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    30.276] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "libinput keyboard catchall"
[    30.276] (II) Using input driver 'libinput' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    30.277] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 26 paused 0
[    30.277] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    30.277] (**) Option "Device" "/dev/input/event3"
[    30.277] (**) Option "_source" "server/udev"
[    30.278] (II) event3  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: is tagged by udev as: Keyboard
[    30.278] (II) event3  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device is a keyboard
[    30.278] (II) event3  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device removed
[    30.278] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.0/0003:045E:0745.0001/input/input3/event3"
[    30.278] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: KEYBOARD, id 8)
[    30.278] (**) Option "xkb_model" "pc105"
[    30.278] (**) Option "xkb_layout" "gb"
[    30.279] (II) event3  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: is tagged by udev as: Keyboard
[    30.279] (II) event3  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device is a keyboard
[    30.279] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/event4)
[    30.279] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev pointer catchall"
[    30.279] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    30.279] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "libinput pointer catchall"
[    30.279] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "libinput keyboard catchall"
[    30.279] (II) Using input driver 'libinput' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    30.280] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 27 paused 0
[    30.280] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    30.280] (**) Option "Device" "/dev/input/event4"
[    30.280] (**) Option "_source" "server/udev"
[    30.281] (II) event4  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: is tagged by udev as: Keyboard Mouse
[    30.281] (II) event4  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device is a pointer
[    30.281] (II) event4  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device is a keyboard
[    30.281] (II) event4  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device removed
[    30.281] (II) libinput: Microsoft Microsoft® 2.4GHz Transceiver v8.0: needs a virtual subdevice
[    30.281] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.1/0003:045E:0745.0002/input/input4/event4"
[    30.281] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: MOUSE, id 9)
[    30.281] (**) Option "AccelerationScheme" "none"
[    30.281] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) selected scheme none/0
[    30.281] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration factor: 2.000
[    30.281] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration threshold: 4
[    30.282] (II) event4  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: is tagged by udev as: Keyboard Mouse
[    30.282] (II) event4  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device is a pointer
[    30.282] (II) event4  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device is a keyboard
[    30.283] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/mouse0)
[    30.283] (II) No input driver specified, ignoring this device.
[    30.283] (II) This device may have been added with another device file.
[    30.283] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/event5)
[    30.283] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    30.283] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "libinput keyboard catchall"
[    30.283] (II) Using input driver 'libinput' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    30.284] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 28 paused 0
[    30.284] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    30.284] (**) Option "Device" "/dev/input/event5"
[    30.284] (**) Option "_source" "server/udev"
[    30.285] (II) event5  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: is tagged by udev as: Keyboard
[    30.285] (II) event5  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device is a keyboard
[    30.285] (II) event5  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device removed
[    30.285] (II) libinput: Microsoft Microsoft® 2.4GHz Transceiver v8.0: needs a virtual subdevice
[    30.285] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:045E:0745.0003/input/input5/event5"
[    30.285] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: MOUSE, id 10)
[    30.285] (**) Option "AccelerationScheme" "none"
[    30.285] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) selected scheme none/0
[    30.285] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration factor: 2.000
[    30.285] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration threshold: 4
[    30.286] (II) event5  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: is tagged by udev as: Keyboard
[    30.286] (II) event5  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device is a keyboard
[    30.286] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event10)
[    30.286] (II) No input driver specified, ignoring this device.
[    30.286] (II) This device may have been added with another device file.
[    30.287] (II) config/udev: Adding input device HDA ATI SB Line Out (/dev/input/event11)
[    30.287] (II) No input driver specified, ignoring this device.
[    30.287] (II) This device may have been added with another device file.
[    30.287] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event12)
[    30.287] (II) No input driver specified, ignoring this device.
[    30.287] (II) This device may have been added with another device file.
[    30.288] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event8)
[    30.288] (II) No input driver specified, ignoring this device.
[    30.288] (II) This device may have been added with another device file.
[    30.288] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event9)
[    30.288] (II) No input driver specified, ignoring this device.
[    30.288] (II) This device may have been added with another device file.
[    30.288] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event6)
[    30.288] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    30.288] (**) Eee PC WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[    30.288] (II) Using input driver 'libinput' for 'Eee PC WMI hotkeys'
[    30.289] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 29 paused 0
[    30.289] (**) Eee PC WMI hotkeys: always reports core events
[    30.289] (**) Option "Device" "/dev/input/event6"
[    30.289] (**) Option "_source" "server/udev"
[    30.290] (II) event6  - Eee PC WMI hotkeys: is tagged by udev as: Keyboard
[    30.290] (II) event6  - Eee PC WMI hotkeys: device is a keyboard
[    30.290] (II) event6  - Eee PC WMI hotkeys: device removed
[    30.290] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input6/event6"
[    30.290] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)
[    30.290] (**) Option "xkb_model" "pc105"
[    30.290] (**) Option "xkb_layout" "gb"
[    30.291] (II) event6  - Eee PC WMI hotkeys: is tagged by udev as: Keyboard
[    30.291] (II) event6  - Eee PC WMI hotkeys: device is a keyboard
[    30.291] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    30.291] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.291] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[    30.292] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    30.292] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 30 paused 0
[    30.292] (**) AT Translated Set 2 keyboard: always reports core events
[    30.292] (**) Option "Device" "/dev/input/event2"
[    30.292] (**) Option "_source" "server/udev"
[    30.293] (II) event2  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    30.293] (II) event2  - AT Translated Set 2 keyboard: device is a keyboard
[    30.293] (II) event2  - AT Translated Set 2 keyboard: device removed
[    30.293] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    30.293] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    30.293] (**) Option "xkb_model" "pc105"
[    30.293] (**) Option "xkb_layout" "gb"
[    30.294] (II) event2  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    30.294] (II) event2  - AT Translated Set 2 keyboard: device is a keyboard
[    30.300] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev pointer catchall"
[    30.300] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    30.300] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "libinput pointer catchall"
[    30.300] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "libinput keyboard catchall"
[    30.300] (II) Using input driver 'libinput' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    30.300] (II) systemd-logind: returning pre-existing fd for /dev/input/event4 13:68
[    30.300] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    30.300] (**) Option "Device" "/dev/input/event4"
[    30.300] (**) Option "_source" "_driver/libinput"
[    30.300] (II) libinput: Microsoft Microsoft® 2.4GHz Transceiver v8.0: is a virtual subdevice
[    30.300] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.1/0003:045E:0745.0002/input/input4/event4"
[    30.300] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: KEYBOARD, id 13)
[    30.300] (**) Option "xkb_model" "pc105"
[    30.300] (**) Option "xkb_layout" "gb"
[    30.300] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    30.300] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "libinput keyboard catchall"
[    30.300] (II) Using input driver 'libinput' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    30.300] (II) systemd-logind: returning pre-existing fd for /dev/input/event5 13:69
[    30.300] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    30.300] (**) Option "Device" "/dev/input/event5"
[    30.300] (**) Option "_source" "_driver/libinput"
[    30.300] (II) libinput: Microsoft Microsoft® 2.4GHz Transceiver v8.0: is a virtual subdevice
[    30.300] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:045E:0745.0003/input/input5/event5"
[    30.300] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: KEYBOARD, id 14)
[    30.300] (**) Option "xkb_model" "pc105"
[    30.300] (**) Option "xkb_layout" "gb"
[    44.738] (**) Option "fd" "22"
[    44.738] (II) event1  - Power Button: device removed
[    44.738] (**) Option "fd" "25"
[    44.738] (II) event0  - Power Button: device removed
[    44.739] (**) Option "fd" "26"
[    44.739] (II) event3  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device removed
[    44.740] (**) Option "fd" "27"
[    44.740] (**) Option "fd" "28"
[    44.741] (**) Option "fd" "29"
[    44.741] (II) event6  - Eee PC WMI hotkeys: device removed
[    44.742] (**) Option "fd" "30"
[    44.742] (II) event2  - AT Translated Set 2 keyboard: device removed
[    44.742] (**) Option "fd" "27"
[    44.742] (II) event4  - Microsoft Microsoft® 2.4GHz Transceiver v8.0: device removed
[    44.743] (**) Option "fd" "28"
[    44.743] (II) event5  - Microsoft Micro
```

---

### Post by dmnur on 2019-01-27
> ```

[ 30.150] (II) [KMS] drm report modesetting isn't supported.
[ 30.150] (EE) open /dev/dri/card0: No such file or directory
[ 30.150] (WW) Falling back to old probe method for modesetting
[ 30.150] (EE) open /dev/dri/card0: No such file or directory

```
**radeon** driver fails to load because KMS is not supported. Probably it's just turned off.

Please provide output of these commands:
```

$ cat /proc/cmdline
$ lsmod | grep radeon
$ grep -r radeon /etc/modprobe.d

```

Also, when pasting output to your forum message, please use the **[NOPARSE][code][/NOPARSE]** BB code. See [here](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168) for instructions.

---

### Post by dfpd62 on 2019-01-27
```
dd@dd-desktop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.15.0-43-generic root=UUID=9608e06e-826b-414e-a731-43bd417a7e7a ro recovery nomodeset
dd@dd-desktop:~$ lsmod | grep radeon
dd@dd-desktop:~$ grep -r radeon /etc/modprobe.d
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist radeonfb
```

---

### Post by dfpd62 on 2019-01-29
what a dummy i am, the pc was booted to safe graphics when  I ran those last commands, here are the results after a normal boot, Dooooh

```

dd@dd-desktop:~$ lsmod |grep radeon
radeon               1470464  20
i2c_algo_bit           16384  1 radeon
ttm                   106496  1 radeon
drm_kms_helper        172032  1 radeon
drm                   401408  16 drm_kms_helper,radeon,ttm

```

So it seems to be the proper driver :-(

---

### Post by dfpd62 on 2019-01-29
```

dd@dd-desktop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.15.0-44-generic root=UUID=9608e06e-826b-414e-a731-43bd417a7e7a ro quiet splash vt.handoff=1

```

---

### Post by dfpd62 on 2019-01-29
```

dd@dd-desktop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.15.0-44-generic root=UUID=9608e06e-826b-414e-a731-43bd417a7e7a ro quiet splash vt.handoff=1

```

---

### Post by dmnur on 2019-02-08
Sorry for the delay.

After some research, I found that it's not your configuration or driver issue. Actually, [this is the known bug](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1766137).
To fix, upgrade your system. In particular you'll need **gdm3** upgraded to **3.28.2-0ubuntu1.1** or a later version.

There is also a workaround you can use before the upgrade:
> After typing an incorrect password, click Cancel, then click your name, then enter your password again.

If that helped or you already resolved your issue earlier (in this case please tell what you've done), please mark this thread as **solved**. See instructions [here](https://ubuntuforums.org/showthread.php?t=726150&p=4527051#post4527051).

---

