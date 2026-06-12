---
title: "Can't Generate xorg.conf"
date: 2016-05-05
forum: General Help
---

### Post by Spency on 2016-05-05
Followed instructions from here: [https://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file](https://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file)
Have done this before several times on this very machine with this very same version of ubuntu. Now it doesn't seem to work. 

I was unable to add the log as an attachment to this post, so here it is:
```
[  1477.193] X.Org X Server 1.17.2
Release Date: 2015-06-16
[  1477.193] X Protocol Version 11, Revision 0
[  1477.193] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[  1477.193] Current Operating System: Linux Silverback 4.2.0-35-generic #40-Ubuntu SMP Tue Mar 15 22:15:45 UTC 2016 x86_64
[  1477.193] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-35-generic.efi.signed root=UUID=954c61d0-0ec2-4838-bc7c-908d0be7d25f ro noprompt persistent quiet splash vt.handoff=7
[  1477.194] Build Date: 12 November 2015  05:33:29PM
[  1477.194] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
[  1477.194] Current version of pixman: 0.32.6
[  1477.194] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  1477.194] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1477.194] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May  5 04:33:48 2016
[  1477.194] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1477.196] (==) No Layout section.  Using the first Screen section.
[  1477.196] (==) No screen section available. Using defaults.
[  1477.196] (**) |-->Screen "Default Screen Section" (0)
[  1477.196] (**) |   |-->Monitor "<default monitor>"
[  1477.197] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  1477.197] (==) Automatically adding devices
[  1477.197] (==) Automatically enabling devices
[  1477.197] (==) Automatically adding GPU devices
[  1477.197] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1477.197] 	Entry deleted from font path.
[  1477.197] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1477.197] 	Entry deleted from font path.
[  1477.197] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1477.197] 	Entry deleted from font path.
[  1477.197] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1477.197] 	Entry deleted from font path.
[  1477.197] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1477.197] 	Entry deleted from font path.
[  1477.197] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[  1477.197] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1477.197] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1477.197] (II) Loader magic: 0x562cf8037d40
[  1477.197] (II) Module ABI versions:
[  1477.197] 	X.Org ANSI C Emulation: 0.4
[  1477.197] 	X.Org Video Driver: 19.0
[  1477.197] 	X.Org XInput driver : 21.0
[  1477.198] 	X.Org Server Extension : 9.0
[  1477.199] (II) xfree86: Adding drm device (/dev/dri/card0)
[  1477.201] (--) PCI:*(0:1:0:0) 1002:68c0:106b:00d2 rev 0, Mem @ 0xc0000000/268435456, 0xd0400000/131072, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[  1477.201] (II) LoadModule: "glx"
[  1477.202] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1477.207] (II) Module glx: vendor="X.Org Foundation"
[  1477.207] 	compiled for 1.17.2, module version = 1.0.0
[  1477.207] 	ABI class: X.Org Server Extension, version 9.0
[  1477.207] (==) AIGLX enabled
[  1477.207] (==) Matched fglrx as autoconfigured driver 0
[  1477.207] (==) Matched ati as autoconfigured driver 1
[  1477.207] (==) Matched fglrx as autoconfigured driver 2
[  1477.207] (==) Matched ati as autoconfigured driver 3
[  1477.207] (==) Matched modesetting as autoconfigured driver 4
[  1477.207] (==) Matched fbdev as autoconfigured driver 5
[  1477.208] (==) Matched vesa as autoconfigured driver 6
[  1477.208] (==) Assigned the driver to the xf86ConfigLayout
[  1477.208] (II) LoadModule: "fglrx"
[  1477.208] (WW) Warning, couldn't open module fglrx
[  1477.208] (II) UnloadModule: "fglrx"
[  1477.208] (II) Unloading fglrx
[  1477.208] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  1477.209] (II) LoadModule: "ati"
[  1477.209] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  1477.209] (II) Module ati: vendor="X.Org Foundation"
[  1477.209] 	compiled for 1.17.2, module version = 7.7.99
[  1477.209] 	Module class: X.Org Video Driver
[  1477.209] 	ABI class: X.Org Video Driver, version 19.0
[  1477.209] (II) LoadModule: "radeon"
[  1477.210] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  1477.210] (II) Module radeon: vendor="X.Org Foundation"
[  1477.210] 	compiled for 1.17.2, module version = 7.7.99
[  1477.210] 	Module class: X.Org Video Driver
[  1477.210] 	ABI class: X.Org Video Driver, version 19.0
[  1477.210] (II) LoadModule: "modesetting"
[  1477.210] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1477.211] (II) Module modesetting: vendor="X.Org Foundation"
[  1477.211] 	compiled for 1.17.2, module version = 1.17.2
[  1477.211] 	Module class: X.Org Video Driver
[  1477.211] 	ABI class: X.Org Video Driver, version 19.0
[  1477.211] (II) LoadModule: "fbdev"
[  1477.211] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1477.211] (II) Module fbdev: vendor="X.Org Foundation"
[  1477.211] 	compiled for 1.17.1, module version = 0.4.4
[  1477.211] 	Module class: X.Org Video Driver
[  1477.211] 	ABI class: X.Org Video Driver, version 19.0
[  1477.211] (II) LoadModule: "vesa"
[  1477.212] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1477.212] (II) Module vesa: vendor="X.Org Foundation"
[  1477.212] 	compiled for 1.17.1, module version = 2.3.4
[  1477.212] 	Module class: X.Org Video Driver
[  1477.212] 	ABI class: X.Org Video Driver, version 19.0
[  1477.212] (==) Matched fglrx as autoconfigured driver 0
[  1477.212] (==) Matched ati as autoconfigured driver 1
[  1477.212] (==) Matched fglrx as autoconfigured driver 2
[  1477.212] (==) Matched ati as autoconfigured driver 3
[  1477.212] (==) Matched modesetting as autoconfigured driver 4
[  1477.212] (==) Matched fbdev as autoconfigured driver 5
[  1477.212] (==) Matched vesa as autoconfigured driver 6
[  1477.212] (==) Assigned the driver to the xf86ConfigLayout
[  1477.212] (II) LoadModule: "fglrx"
[  1477.213] (WW) Warning, couldn't open module fglrx
[  1477.213] (II) UnloadModule: "fglrx"
[  1477.213] (II) Unloading fglrx
[  1477.213] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  1477.213] (II) LoadModule: "ati"
[  1477.213] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  1477.214] (II) Module ati: vendor="X.Org Foundation"
[  1477.214] 	compiled for 1.17.2, module version = 7.7.99
[  1477.214] 	Module class: X.Org Video Driver
[  1477.214] 	ABI class: X.Org Video Driver, version 19.0
[  1477.214] (II) LoadModule: "modesetting"
[  1477.214] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1477.214] (II) Module modesetting: vendor="X.Org Foundation"
[  1477.214] 	compiled for 1.17.2, module version = 1.17.2
[  1477.214] 	Module class: X.Org Video Driver
[  1477.214] 	ABI class: X.Org Video Driver, version 19.0
[  1477.214] (II) UnloadModule: "modesetting"
[  1477.214] (II) Unloading modesetting
[  1477.214] (II) Failed to load module "modesetting" (already loaded, 0)
[  1477.214] (II) LoadModule: "fbdev"
[  1477.215] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1477.215] (II) Module fbdev: vendor="X.Org Foundation"
[  1477.215] 	compiled for 1.17.1, module version = 0.4.4
[  1477.215] 	Module class: X.Org Video Driver
[  1477.215] 	ABI class: X.Org Video Driver, version 19.0
[  1477.215] (II) UnloadModule: "fbdev"
[  1477.215] (II) Unloading fbdev
[  1477.215] (II) Failed to load module "fbdev" (already loaded, 0)
[  1477.215] (II) LoadModule: "vesa"
[  1477.215] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1477.215] (II) Module vesa: vendor="X.Org Foundation"
[  1477.215] 	compiled for 1.17.1, module version = 2.3.4
[  1477.215] 	Module class: X.Org Video Driver
[  1477.215] 	ABI class: X.Org Video Driver, version 19.0
[  1477.215] (II) UnloadModule: "vesa"
[  1477.215] (II) Unloading vesa
[  1477.215] (II) Failed to load module "vesa" (already loaded, 0)
[  1477.215] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
	HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[  1477.229] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  1477.229] (II) FBDEV: driver for framebuffer: fbdev
[  1477.229] (II) VESA: driver for VESA chipsets: vesa
[  1477.229] (++) using VT number 7


[  1477.251] (II) [KMS] Kernel modesetting enabled.
[  1477.251] (WW) Falling back to old probe method for modesetting
[  1477.251] (WW) Falling back to old probe method for fbdev
[  1477.251] (II) Loading sub module "fbdevhw"
[  1477.251] (II) LoadModule: "fbdevhw"
[  1477.252] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1477.252] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1477.252] 	compiled for 1.17.2, module version = 0.0.2
[  1477.252] 	ABI class: X.Org Video Driver, version 19.0
[  1477.252] (WW) Falling back to old probe method for vesa
[  1477.253] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  1477.253] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  1477.253] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  1477.253] (==) RADEON(0): Default visual is TrueColor
[  1477.253] (==) RADEON(0): RGB weight 888
[  1477.253] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  1477.253] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 5000 Series" (ChipID = 0x68c0)
[  1477.253] (II) Loading sub module "fb"
[  1477.253] (II) LoadModule: "fb"
[  1477.253] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1477.254] (II) Module fb: vendor="X.Org Foundation"
[  1477.254] 	compiled for 1.17.2, module version = 1.0.0
[  1477.254] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1477.254] (II) Loading sub module "dri2"
[  1477.254] (II) LoadModule: "dri2"
[  1477.254] (II) Module "dri2" already built-in
[  1477.254] (II) Loading sub module "exa"
[  1477.254] (II) LoadModule: "exa"
[  1477.254] (II) Loading /usr/lib/xorg/modules/libexa.so
[  1477.255] (II) Module exa: vendor="X.Org Foundation"
[  1477.255] 	compiled for 1.17.2, module version = 2.6.0
[  1477.255] 	ABI class: X.Org Video Driver, version 19.0
[  1477.255] (II) RADEON(0): KMS Color Tiling: enabled
[  1477.255] (II) RADEON(0): KMS Color Tiling 2D: enabled
[  1477.255] (II) RADEON(0): KMS Pageflipping: enabled
[  1477.255] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  1477.278] (II) RADEON(0): Output eDP has no monitor section
[  1477.284] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[  1477.307] (II) RADEON(0): EDID for output eDP
[  1477.307] (II) RADEON(0): Manufacturer: APP  Model: 9cde  Serial#: 0
[  1477.307] (II) RADEON(0): Year: 2010  Week: 22
[  1477.307] (II) RADEON(0): EDID Version: 1.4
[  1477.307] (II) RADEON(0): Digital Display Input
[  1477.307] (II) RADEON(0): 8 bits per channel
[  1477.308] (II) RADEON(0): Digital interface is DisplayPort
[  1477.308] (II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[  1477.308] (II) RADEON(0): Gamma: 2.20
[  1477.308] (II) RADEON(0): DPMS capabilities: Off
[  1477.308] (II) RADEON(0): Supported color encodings: RGB 4:4:4 
[  1477.308] (II) RADEON(0): First detailed timing is preferred mode
[  1477.308] (II) RADEON(0): Preferred mode is native pixel format and refresh rate
[  1477.308] (II) RADEON(0): redX: 0.653 redY: 0.334   greenX: 0.300 greenY: 0.620
[  1477.308] (II) RADEON(0): blueX: 0.146 blueY: 0.050   whiteX: 0.312 whiteY: 0.329
[  1477.308] (II) RADEON(0): Manufacturer's mask: 0
[  1477.308] (II) RADEON(0): Supported detailed timing:
[  1477.308] (II) RADEON(0): clock: 138.5 MHz   Image Size:  475 x 267 mm
[  1477.308] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[  1477.308] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[  1477.308] (II) RADEON(0): Unknown vendor-specific block 2
[  1477.308] (II) RADEON(0): Monitor name: Color LCD
[  1477.308] (II) RADEON(0): EDID (in hex):
[  1477.308] (II) RADEON(0): 	00ffffffffffff000610de9c00000000
[  1477.308] (II) RADEON(0): 	16140104a5301b78226fb1a7554c9e25
[  1477.308] (II) RADEON(0): 	0c505400000001010101010101010101
[  1477.308] (II) RADEON(0): 	0101010101011a3680a070381f403020
[  1477.308] (II) RADEON(0): 	3500db0b1100001a0000000201061001
[  1477.308] (II) RADEON(0): 	0a010000000000000000000000fc0043
[  1477.308] (II) RADEON(0): 	6f6c6f72204c43440a20202000000000
[  1477.308] (II) RADEON(0): 	00000000000000000000000000000048
[  1477.308] (II) RADEON(0): Printing probed modes for output eDP
[  1477.308] (II) RADEON(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  1477.308] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1477.308] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[  1477.308] (II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[  1477.308] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1477.308] (II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[  1477.308] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[  1477.308] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[  1477.308] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[  1477.309] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[  1477.309] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[  1477.309] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[  1477.309] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[  1477.309] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[  1477.309] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[  1477.316] (II) RADEON(0): EDID for output DisplayPort-0
[  1477.316] (II) RADEON(0): Output eDP connected
[  1477.316] (II) RADEON(0): Output DisplayPort-0 disconnected
[  1477.316] (II) RADEON(0): Using exact sizes for initial modes
[  1477.316] (II) RADEON(0): Output eDP using initial mode 1920x1080
[  1477.316] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  1477.316] (II) RADEON(0): mem size init: gart size :3fdde000 vram size: s:20000000 visible:1f3b8000
[  1477.316] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[  1477.316] (==) RADEON(0): DPI set to (96, 96)
[  1477.316] (II) Loading sub module "ramdac"
[  1477.316] (II) LoadModule: "ramdac"
[  1477.316] (II) Module "ramdac" already built-in
[  1477.316] (II) UnloadModule: "modesetting"
[  1477.316] (II) Unloading modesetting
[  1477.317] (II) UnloadModule: "fbdev"
[  1477.317] (II) Unloading fbdev
[  1477.317] (II) UnloadSubModule: "fbdevhw"
[  1477.317] (II) Unloading fbdevhw
[  1477.317] (II) UnloadModule: "vesa"
[  1477.317] (II) Unloading vesa
[  1477.317] (--) Depth 24 pixmap format is 32 bpp
[  1477.317] (II) RADEON(0): [DRI2] Setup complete
[  1477.317] (II) RADEON(0): [DRI2]   DRI driver: r600
[  1477.317] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[  1477.317] (II) RADEON(0): Front buffer size: 8160K
[  1477.317] (II) RADEON(0): VRAM usage limit set to 453110K
[  1477.318] (==) RADEON(0): DRI3 disabled
[  1477.318] (==) RADEON(0): Backing store enabled
[  1477.318] (II) RADEON(0): Direct rendering enabled
[  1477.318] (II) EXA(0): Driver allocated offscreen pixmaps
[  1477.318] (II) EXA(0): Driver registered support for the following operations:
[  1477.318] (II)         Solid
[  1477.318] (II)         Copy
[  1477.318] (II)         Composite (RENDER acceleration)
[  1477.318] (II)         UploadToScreen
[  1477.318] (II)         DownloadFromScreen
[  1477.318] (II) RADEON(0): Acceleration enabled
[  1477.318] (==) RADEON(0): DPMS enabled
[  1477.318] (==) RADEON(0): Silken mouse enabled
[  1477.318] (II) RADEON(0): Set up textured video
[  1477.318] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[  1477.318] (II) RADEON(0): [XvMC] Extension initialized.
[  1477.318] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1477.318] (--) RandR disabled
[  1477.333] (II) SELinux: Disabled on system
[  1477.375] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  1477.375] (II) AIGLX: enabled GLX_ARB_create_context
[  1477.375] (II) AIGLX: enabled GLX_ARB_create_context_profile
[  1477.375] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[  1477.375] (II) AIGLX: enabled GLX_INTEL_swap_event
[  1477.375] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  1477.375] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[  1477.375] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[  1477.375] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  1477.375] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[  1477.381] (II) AIGLX: Loaded and initialized r600
[  1477.381] (II) GLX: Initialized DRI2 GL provider for screen 0
[  1477.382] (II) RADEON(0): Setting screen physical size to 508 x 285
[  1477.406] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1477.443] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  1477.444] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1477.444] (II) LoadModule: "evdev"
[  1477.444] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1477.446] (II) Module evdev: vendor="X.Org Foundation"
[  1477.446] 	compiled for 1.17.1, module version = 2.9.2
[  1477.446] 	Module class: X.Org XInput Driver
[  1477.446] 	ABI class: X.Org XInput driver, version 21.0
[  1477.446] (II) Using input driver 'evdev' for 'Power Button'
[  1477.446] (**) Power Button: always reports core events
[  1477.446] (**) evdev: Power Button: Device: "/dev/input/event2"
[  1477.446] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1477.446] (--) evdev: Power Button: Found keys
[  1477.446] (II) evdev: Power Button: Configuring as keyboard
[  1477.446] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  1477.446] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1477.446] (**) Option "xkb_rules" "evdev"
[  1477.446] (**) Option "xkb_model" "pc105"
[  1477.446] (**) Option "xkb_layout" "us"
[  1477.448] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[  1477.448] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  1477.448] (II) Using input driver 'evdev' for 'Video Bus'
[  1477.448] (**) Video Bus: always reports core events
[  1477.448] (**) evdev: Video Bus: Device: "/dev/input/event3"
[  1477.448] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  1477.448] (--) evdev: Video Bus: Found keys
[  1477.448] (II) evdev: Video Bus: Configuring as keyboard
[  1477.448] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input3/event3"
[  1477.449] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[  1477.449] (**) Option "xkb_rules" "evdev"
[  1477.449] (**) Option "xkb_model" "pc105"
[  1477.449] (**) Option "xkb_layout" "us"
[  1477.450] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1477.450] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1477.450] (II) Using input driver 'evdev' for 'Power Button'
[  1477.450] (**) Power Button: always reports core events
[  1477.450] (**) evdev: Power Button: Device: "/dev/input/event0"
[  1477.450] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1477.450] (--) evdev: Power Button: Found keys
[  1477.450] (II) evdev: Power Button: Configuring as keyboard
[  1477.451] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[  1477.451] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[  1477.451] (**) Option "xkb_rules" "evdev"
[  1477.451] (**) Option "xkb_model" "pc105"
[  1477.451] (**) Option "xkb_layout" "us"
[  1477.452] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  1477.452] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  1477.452] (II) Using input driver 'evdev' for 'Sleep Button'
[  1477.452] (**) Sleep Button: always reports core events
[  1477.452] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[  1477.452] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[  1477.452] (--) evdev: Sleep Button: Found keys
[  1477.452] (II) evdev: Sleep Button: Configuring as keyboard
[  1477.453] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[  1477.453] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[  1477.453] (**) Option "xkb_rules" "evdev"
[  1477.453] (**) Option "xkb_model" "pc105"
[  1477.453] (**) Option "xkb_layout" "us"
[  1477.455] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event11)
[  1477.455] (II) No input driver specified, ignoring this device.
[  1477.455] (II) This device may have been added with another device file.
[  1477.457] (II) config/udev: Adding input device Corsair Corsair K65 Gaming Keyboard (/dev/input/event8)
[  1477.457] (**) Corsair Corsair K65 Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[  1477.457] (II) Using input driver 'evdev' for 'Corsair Corsair K65 Gaming Keyboard'
[  1477.457] (**) Corsair Corsair K65 Gaming Keyboard: always reports core events
[  1477.457] (**) evdev: Corsair Corsair K65 Gaming Keyboard: Device: "/dev/input/event8"
[  1477.457] (--) evdev: Corsair Corsair K65 Gaming Keyboard: Vendor 0x1b1c Product 0x1b07
[  1477.457] (--) evdev: Corsair Corsair K65 Gaming Keyboard: Found keys
[  1477.457] (II) evdev: Corsair Corsair K65 Gaming Keyboard: Configuring as keyboard
[  1477.457] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.4/1-1.4:1.0/0003:1B1C:1B07.0005/input/input8/event8"
[  1477.457] (II) XINPUT: Adding extended input device "Corsair Corsair K65 Gaming Keyboard" (type: KEYBOARD, id 10)
[  1477.457] (**) Option "xkb_rules" "evdev"
[  1477.457] (**) Option "xkb_model" "pc105"
[  1477.457] (**) Option "xkb_layout" "us"
[  1477.459] (II) config/udev: Adding input device Corsair Corsair K65 Gaming Keyboard (/dev/input/event9)
[  1477.459] (**) Corsair Corsair K65 Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[  1477.460] (II) Using input driver 'evdev' for 'Corsair Corsair K65 Gaming Keyboard'
[  1477.460] (**) Corsair Corsair K65 Gaming Keyboard: always reports core events
[  1477.460] (**) evdev: Corsair Corsair K65 Gaming Keyboard: Device: "/dev/input/event9"
[  1477.460] (--) evdev: Corsair Corsair K65 Gaming Keyboard: Vendor 0x1b1c Product 0x1b07
[  1477.460] (--) evdev: Corsair Corsair K65 Gaming Keyboard: Found 1 mouse buttons
[  1477.460] (--) evdev: Corsair Corsair K65 Gaming Keyboard: Found scroll wheel(s)
[  1477.460] (--) evdev: Corsair Corsair K65 Gaming Keyboard: Found relative axes
[  1477.460] (II) evdev: Corsair Corsair K65 Gaming Keyboard: Forcing relative x/y axes to exist.
[  1477.460] (--) evdev: Corsair Corsair K65 Gaming Keyboard: Found absolute axes
[  1477.460] (II) evdev: Corsair Corsair K65 Gaming Keyboard: Forcing absolute x/y axes to exist.
[  1477.460] (--) evdev: Corsair Corsair K65 Gaming Keyboard: Found keys
[  1477.460] (II) evdev: Corsair Corsair K65 Gaming Keyboard: Configuring as mouse
[  1477.460] (II) evdev: Corsair Corsair K65 Gaming Keyboard: Configuring as keyboard
[  1477.460] (II) evdev: Corsair Corsair K65 Gaming Keyboard: Adding scrollwheel support
[  1477.460] (**) evdev: Corsair Corsair K65 Gaming Keyboard: YAxisMapping: buttons 4 and 5
[  1477.460] (**) evdev: Corsair Corsair K65 Gaming Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1477.460] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.4/1-1.4:1.1/0003:1B1C:1B07.0006/input/input9/event9"
[  1477.460] (II) XINPUT: Adding extended input device "Corsair Corsair K65 Gaming Keyboard" (type: KEYBOARD, id 11)
[  1477.460] (**) Option "xkb_rules" "evdev"
[  1477.460] (**) Option "xkb_model" "pc105"
[  1477.460] (**) Option "xkb_layout" "us"
[  1477.461] (II) evdev: Corsair Corsair K65 Gaming Keyboard: initialized for relative axes.
[  1477.461] (WW) evdev: Corsair Corsair K65 Gaming Keyboard: ignoring absolute axes.
[  1477.461] (**) Corsair Corsair K65 Gaming Keyboard: (accel) keeping acceleration scheme 1
[  1477.461] (**) Corsair Corsair K65 Gaming Keyboard: (accel) acceleration profile 0
[  1477.461] (**) Corsair Corsair K65 Gaming Keyboard: (accel) acceleration factor: 2.000
[  1477.461] (**) Corsair Corsair K65 Gaming Keyboard: (accel) acceleration threshold: 4
[  1477.463] (II) config/udev: Adding input device Corsair Corsair K65 Gaming Keyboard (/dev/input/event10)
[  1477.463] (**) Corsair Corsair K65 Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[  1477.463] (II) Using input driver 'evdev' for 'Corsair Corsair K65 Gaming Keyboard'
[  1477.463] (**) Corsair Corsair K65 Gaming Keyboard: always reports core events
[  1477.463] (**) evdev: Corsair Corsair K65 Gaming Keyboard: Device: "/dev/input/event10"
[  1477.463] (--) evdev: Corsair Corsair K65 Gaming Keyboard: Vendor 0x1b1c Product 0x1b07
[  1477.463] (--) evdev: Corsair Corsair K65 Gaming Keyboard: Found keys
[  1477.463] (II) evdev: Corsair Corsair K65 Gaming Keyboard: Configuring as keyboard
[  1477.463] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.4/1-1.4:1.2/0003:1B1C:1B07.0007/input/input10/event10"
[  1477.463] (II) XINPUT: Adding extended input device "Corsair Corsair K65 Gaming Keyboard" (type: KEYBOARD, id 12)
[  1477.463] (**) Option "xkb_rules" "evdev"
[  1477.463] (**) Option "xkb_model" "pc105"
[  1477.463] (**) Option "xkb_layout" "us"
[  1477.465] (II) config/udev: Adding input device HDA Intel MID Line (/dev/input/event13)
[  1477.465] (II) No input driver specified, ignoring this device.
[  1477.465] (II) This device may have been added with another device file.
[  1477.466] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event14)
[  1477.466] (II) No input driver specified, ignoring this device.
[  1477.466] (II) This device may have been added with another device file.
[  1477.467] (II) config/udev: Adding input device HDA Intel MID SPDIF In (/dev/input/event15)
[  1477.467] (II) No input driver specified, ignoring this device.
[  1477.467] (II) This device may have been added with another device file.
[  1477.468] (II) config/udev: Adding input device Built-in iSight (/dev/input/event12)
[  1477.468] (**) Built-in iSight: Applying InputClass "evdev keyboard catchall"
[  1477.468] (II) Using input driver 'evdev' for 'Built-in iSight'
[  1477.468] (**) Built-in iSight: always reports core events
[  1477.468] (**) evdev: Built-in iSight: Device: "/dev/input/event12"
[  1477.468] (--) evdev: Built-in iSight: Vendor 0x5ac Product 0x8502
[  1477.468] (--) evdev: Built-in iSight: Found keys
[  1477.469] (II) evdev: Built-in iSight: Configuring as keyboard
[  1477.469] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1/2-1.1:1.0/input/input12/event12"
[  1477.469] (II) XINPUT: Adding extended input device "Built-in iSight" (type: KEYBOARD, id 13)
[  1477.469] (**) Option "xkb_rules" "evdev"
[  1477.469] (**) Option "xkb_model" "pc105"
[  1477.469] (**) Option "xkb_layout" "us"
[  1477.471] (II) config/udev: Adding input device Apple Computer, Inc. IR Receiver (/dev/input/event4)
[  1477.471] (**) Apple Computer, Inc. IR Receiver: Applying InputClass "evdev keyboard catchall"
[  1477.471] (II) Using input driver 'evdev' for 'Apple Computer, Inc. IR Receiver'
[  1477.471] (**) Apple Computer, Inc. IR Receiver: always reports core events
[  1477.471] (**) evdev: Apple Computer, Inc. IR Receiver: Device: "/dev/input/event4"
[  1477.471] (--) evdev: Apple Computer, Inc. IR Receiver: Vendor 0x5ac Product 0x8242
[  1477.471] (--) evdev: Apple Computer, Inc. IR Receiver: Found keys
[  1477.471] (II) evdev: Apple Computer, Inc. IR Receiver: Configuring as keyboard
[  1477.471] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2:1.0/0003:05AC:8242.0001/input/input4/event4"
[  1477.471] (II) XINPUT: Adding extended input device "Apple Computer, Inc. IR Receiver" (type: KEYBOARD, id 14)
[  1477.471] (**) Option "xkb_rules" "evdev"
[  1477.471] (**) Option "xkb_model" "pc105"
[  1477.471] (**) Option "xkb_layout" "us"
[  1477.473] (II) config/udev: Adding input device Razer Razer DeathAdder 2013 (/dev/input/event5)
[  1477.474] (**) Razer Razer DeathAdder 2013: Applying InputClass "evdev pointer catchall"
[  1477.474] (II) Using input driver 'evdev' for 'Razer Razer DeathAdder 2013'
[  1477.474] (**) Razer Razer DeathAdder 2013: always reports core events
[  1477.474] (**) evdev: Razer Razer DeathAdder 2013: Device: "/dev/input/event5"
[  1477.528] (--) evdev: Razer Razer DeathAdder 2013: Vendor 0x1532 Product 0x37
[  1477.528] (--) evdev: Razer Razer DeathAdder 2013: Found 9 mouse buttons
[  1477.528] (--) evdev: Razer Razer DeathAdder 2013: Found scroll wheel(s)
[  1477.528] (--) evdev: Razer Razer DeathAdder 2013: Found relative axes
[  1477.528] (--) evdev: Razer Razer DeathAdder 2013: Found x and y relative axes
[  1477.528] (II) evdev: Razer Razer DeathAdder 2013: Configuring as mouse
[  1477.528] (II) evdev: Razer Razer DeathAdder 2013: Adding scrollwheel support
[  1477.528] (**) evdev: Razer Razer DeathAdder 2013: YAxisMapping: buttons 4 and 5
[  1477.528] (**) evdev: Razer Razer DeathAdder 2013: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1477.528] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.4/2-1.4:1.0/0003:1532:0037.0002/input/input5/event5"
[  1477.528] (II) XINPUT: Adding extended input device "Razer Razer DeathAdder 2013" (type: MOUSE, id 15)
[  1477.528] (II) evdev: Razer Razer DeathAdder 2013: initialized for relative axes.
[  1477.528] (**) Razer Razer DeathAdder 2013: (accel) keeping acceleration scheme 1
[  1477.528] (**) Razer Razer DeathAdder 2013: (accel) acceleration profile 0
[  1477.528] (**) Razer Razer DeathAdder 2013: (accel) acceleration factor: 2.000
[  1477.528] (**) Razer Razer DeathAdder 2013: (accel) acceleration threshold: 4
[  1477.529] (II) config/udev: Adding input device Razer Razer DeathAdder 2013 (/dev/input/mouse0)
[  1477.529] (II) No input driver specified, ignoring this device.
[  1477.529] (II) This device may have been added with another device file.
[  1477.530] (II) config/udev: Adding input device Razer Razer DeathAdder 2013 (/dev/input/event6)
[  1477.530] (**) Razer Razer DeathAdder 2013: Applying InputClass "evdev keyboard catchall"
[  1477.530] (II) Using input driver 'evdev' for 'Razer Razer DeathAdder 2013'
[  1477.530] (**) Razer Razer DeathAdder 2013: always reports core events
[  1477.530] (**) evdev: Razer Razer DeathAdder 2013: Device: "/dev/input/event6"
[  1477.531] (--) evdev: Razer Razer DeathAdder 2013: Vendor 0x1532 Product 0x37
[  1477.531] (--) evdev: Razer Razer DeathAdder 2013: Found 1 mouse buttons
[  1477.531] (--) evdev: Razer Razer DeathAdder 2013: Found scroll wheel(s)
[  1477.531] (--) evdev: Razer Razer DeathAdder 2013: Found relative axes
[  1477.531] (II) evdev: Razer Razer DeathAdder 2013: Forcing relative x/y axes to exist.
[  1477.531] (--) evdev: Razer Razer DeathAdder 2013: Found absolute axes
[  1477.531] (--) evdev: Razer Razer DeathAdder 2013: Found absolute multitouch axes
[  1477.531] (--) evdev: Razer Razer DeathAdder 2013: Found keys
[  1477.531] (II) evdev: Razer Razer DeathAdder 2013: Configuring as mouse
[  1477.531] (II) evdev: Razer Razer DeathAdder 2013: Configuring as keyboard
[  1477.531] (II) evdev: Razer Razer DeathAdder 2013: Adding scrollwheel support
[  1477.531] (**) evdev: Razer Razer DeathAdder 2013: YAxisMapping: buttons 4 and 5
[  1477.531] (**) evdev: Razer Razer DeathAdder 2013: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1477.531] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.4/2-1.4:1.1/0003:1532:0037.0003/input/input6/event6"
[  1477.531] (II) XINPUT: Adding extended input device "Razer Razer DeathAdder 2013" (type: KEYBOARD, id 16)
[  1477.531] (**) Option "xkb_rules" "evdev"
[  1477.531] (**) Option "xkb_model" "pc105"
[  1477.531] (**) Option "xkb_layout" "us"
[  1477.531] (II) evdev: Razer Razer DeathAdder 2013: initialized for relative axes.
[  1477.531] (WW) evdev: Razer Razer DeathAdder 2013: ignoring absolute axes.
[  1477.531] (**) Razer Razer DeathAdder 2013: (accel) keeping acceleration scheme 1
[  1477.531] (**) Razer Razer DeathAdder 2013: (accel) acceleration profile 0
[  1477.532] (**) Razer Razer DeathAdder 2013: (accel) acceleration factor: 2.000
[  1477.532] (**) Razer Razer DeathAdder 2013: (accel) acceleration threshold: 4
[  1477.533] (II) config/udev: Adding input device Razer Razer DeathAdder 2013 (/dev/input/event7)
[  1477.533] (**) Razer Razer DeathAdder 2013: Applying InputClass "evdev keyboard catchall"
[  1477.533] (II) Using input driver 'evdev' for 'Razer Razer DeathAdder 2013'
[  1477.533] (**) Razer Razer DeathAdder 2013: always reports core events
[  1477.533] (**) evdev: Razer Razer DeathAdder 2013: Device: "/dev/input/event7"
[  1477.533] (--) evdev: Razer Razer DeathAdder 2013: Vendor 0x1532 Product 0x37
[  1477.533] (--) evdev: Razer Razer DeathAdder 2013: Found keys
[  1477.533] (II) evdev: Razer Razer DeathAdder 2013: Configuring as keyboard
[  1477.533] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.4/2-1.4:1.2/0003:1532:0037.0004/input/input7/event7"
[  1477.533] (II) XINPUT: Adding extended input device "Razer Razer DeathAdder 2013" (type: KEYBOARD, id 17)
[  1477.533] (**) Option "xkb_rules" "evdev"
[  1477.533] (**) Option "xkb_model" "pc105"
[  1477.533] (**) Option "xkb_layout" "us"
[  1479.332] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  1479.332] (II) RADEON(0): Printing DDC gathered Modelines:
[  1479.332] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  1479.745] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  1479.745] (II) RADEON(0): Printing DDC gathered Modelines:
[  1479.745] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  1484.131] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  1484.131] (II) RADEON(0): Printing DDC gathered Modelines:
[  1484.131] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  1484.193] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  1484.193] (II) RADEON(0): Printing DDC gathered Modelines:
[  1484.193] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  1484.892] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  1484.892] (II) RADEON(0): Printing DDC gathered Modelines:
[  1484.892] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  1485.084] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1485.308] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  1485.308] (II) RADEON(0): Printing DDC gathered Modelines:
[  1485.308] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  1486.823] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1486.886] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1488.274] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  1488.274] (II) RADEON(0): Printing DDC gathered Modelines:
[  1488.274] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  1488.523] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[  1502.432] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  1502.432] (II) RADEON(0): Printing DDC gathered Modelines:
[  1502.432] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  1502.465] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  1502.465] (II) RADEON(0): Printing DDC gathered Modelines:
[  1502.465] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  1535.843] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  1535.843] (II) RADEON(0): Printing DDC gathered Modelines:
[  1535.843] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  2893.129] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  2893.129] (II) RADEON(0): Printing DDC gathered Modelines:
[  2893.129] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  2893.165] (II) RADEON(0): EDID vendor "APP", prod id 40158
[  2893.165] (II) RADEON(0): Printing DDC gathered Modelines:
[  2893.165] (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
```

---

