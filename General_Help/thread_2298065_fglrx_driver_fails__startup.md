---
title: "fglrx driver fails  startup"
date: 2015-10-08
forum: General Help
---

### Post by rschanzenbacher on 2015-10-08
I am trying to install fglrx and have been failing to get it to start X afterwards. I am trying to get steam to work. I need the drivers and the open source source don't work. Here is my X.org Log:

```

[    27.677] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    27.677] X Protocol Version 11, Revision 0
[    27.677] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[    27.677] Current Operating System: Linux ryan-laptop-ubuntu 3.19.0-30-generic #34-Ubuntu SMP Fri Oct 2 22:08:41 UTC 2015 x86_64
[    27.677] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic.efi.signed root=UUID=148aa027-7beb-4f54-8894-b7fe83f8b390 ro quiet splash vt.handoff=7
[    27.677] Build Date: 11 September 2015  10:30:58AM
[    27.677] xorg-server 2:1.17.1-0ubuntu3.1 (For technical support please see http://www.ubuntu.com/support) 
[    27.677] Current version of pixman: 0.32.6
[    27.677]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    27.677] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.678] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct  8 21:57:23 2015
[    27.684] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.685] (==) No Layout section.  Using the first Screen section.
[    27.685] (==) No screen section available. Using defaults.
[    27.685] (**) |-->Screen "Default Screen Section" (0)
[    27.685] (**) |   |-->Monitor "<default monitor>"
[    27.685] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    27.685] (==) Automatically adding devices
[    27.685] (==) Automatically enabling devices
[    27.685] (==) Automatically adding GPU devices
[    27.685] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.685]     Entry deleted from font path.
[    27.685] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.685]     Entry deleted from font path.
[    27.685] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.685]     Entry deleted from font path.
[    27.686] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.686]     Entry deleted from font path.
[    27.686] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.686]     Entry deleted from font path.
[    27.686] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    27.686] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.686] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.686] (II) Loader magic: 0x7fcfb5d0bd80
[    27.686] (II) Module ABI versions:
[    27.686]     X.Org ANSI C Emulation: 0.4
[    27.686]     X.Org Video Driver: 19.0
[    27.686]     X.Org XInput driver : 21.0
[    27.686]     X.Org Server Extension : 9.0
[    27.686] (II) xfree86: Adding drm device (/dev/dri/card0)
[    27.688] (--) PCI:*(0:0:1:0) 1002:9903:1025:0696 rev 0, Mem @ 0xe0000000/268435456, 0xf0400000/262144, I/O @ 0x00004000/256
[    27.689] (II) LoadModule: "glx"
[    27.699] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.810] (II) Module glx: vendor="X.Org Foundation"
[    27.810]     compiled for 1.17.1, module version = 1.0.0
[    27.810]     ABI class: X.Org Server Extension, version 9.0
[    27.810] (==) AIGLX enabled
[    27.810] (==) Matched fglrx as autoconfigured driver 0
[    27.810] (==) Matched ati as autoconfigured driver 1
[    27.810] (==) Matched fglrx as autoconfigured driver 2
[    27.810] (==) Matched ati as autoconfigured driver 3
[    27.810] (==) Matched modesetting as autoconfigured driver 4
[    27.810] (==) Matched fbdev as autoconfigured driver 5
[    27.810] (==) Matched vesa as autoconfigured driver 6
[    27.811] (==) Assigned the driver to the xf86ConfigLayout
[    27.811] (II) LoadModule: "fglrx"
[    27.811] (WW) Warning, couldn't open module fglrx
[    27.811] (II) UnloadModule: "fglrx"
[    27.811] (II) Unloading fglrx
[    27.811] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    27.811] (II) LoadModule: "ati"
[    27.811] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    27.812] (II) Module ati: vendor="X.Org Foundation"
[    27.812]     compiled for 1.17.1, module version = 7.5.0
[    27.812]     Module class: X.Org Video Driver
[    27.812]     ABI class: X.Org Video Driver, version 19.0
[    27.812] (II) LoadModule: "radeon"
[    27.812] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    27.821] (II) Module radeon: vendor="X.Org Foundation"
[    27.821]     compiled for 1.17.1, module version = 7.5.0
[    27.821]     Module class: X.Org Video Driver
[    27.821]     ABI class: X.Org Video Driver, version 19.0
[    27.821] (II) LoadModule: "modesetting"
[    27.821] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    27.822] (II) Module modesetting: vendor="X.Org Foundation"
[    27.822]     compiled for 1.17.1, module version = 1.17.1
[    27.822]     Module class: X.Org Video Driver
[    27.822]     ABI class: X.Org Video Driver, version 19.0
[    27.822] (II) LoadModule: "fbdev"
[    27.822] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.822] (II) Module fbdev: vendor="X.Org Foundation"
[    27.822]     compiled for 1.17.1, module version = 0.4.4
[    27.822]     Module class: X.Org Video Driver
[    27.822]     ABI class: X.Org Video Driver, version 19.0
[    27.822] (II) LoadModule: "vesa"
[    27.822] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.822] (II) Module vesa: vendor="X.Org Foundation"
[    27.822]     compiled for 1.17.1, module version = 2.3.3
[    27.822]     Module class: X.Org Video Driver
[    27.822]     ABI class: X.Org Video Driver, version 19.0
[    27.822] (==) Matched fglrx as autoconfigured driver 0
[    27.822] (==) Matched ati as autoconfigured driver 1
[    27.822] (==) Matched fglrx as autoconfigured driver 2
[    27.822] (==) Matched ati as autoconfigured driver 3
[    27.822] (==) Matched modesetting as autoconfigured driver 4
[    27.822] (==) Matched fbdev as autoconfigured driver 5
[    27.822] (==) Matched vesa as autoconfigured driver 6
[    27.822] (==) Assigned the driver to the xf86ConfigLayout
[    27.822] (II) LoadModule: "fglrx"
[    27.823] (WW) Warning, couldn't open module fglrx
[    27.823] (II) UnloadModule: "fglrx"
[    27.823] (II) Unloading fglrx
[    27.823] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    27.823] (II) LoadModule: "ati"
[    27.823] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    27.823] (II) Module ati: vendor="X.Org Foundation"
[    27.823]     compiled for 1.17.1, module version = 7.5.0
[    27.823]     Module class: X.Org Video Driver
[    27.823]     ABI class: X.Org Video Driver, version 19.0
[    27.823] (II) LoadModule: "modesetting"
[    27.823] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    27.823] (II) Module modesetting: vendor="X.Org Foundation"
[    27.823]     compiled for 1.17.1, module version = 1.17.1
[    27.823]     Module class: X.Org Video Driver
[    27.823]     ABI class: X.Org Video Driver, version 19.0
[    27.823] (II) UnloadModule: "modesetting"
[    27.823] (II) Unloading modesetting
[    27.824] (II) Failed to load module "modesetting" (already loaded, 0)
[    27.824] (II) LoadModule: "fbdev"
[    27.824] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.824] (II) Module fbdev: vendor="X.Org Foundation"
[    27.824]     compiled for 1.17.1, module version = 0.4.4
[    27.824]     Module class: X.Org Video Driver
[    27.824]     ABI class: X.Org Video Driver, version 19.0
[    27.824] (II) UnloadModule: "fbdev"
[    27.824] (II) Unloading fbdev
[    27.824] (II) Failed to load module "fbdev" (already loaded, 0)
[    27.824] (II) LoadModule: "vesa"
[    27.824] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.824] (II) Module vesa: vendor="X.Org Foundation"
[    27.824]     compiled for 1.17.1, module version = 2.3.3
[    27.824]     Module class: X.Org Video Driver
[    27.824]     ABI class: X.Org Video Driver, version 19.0
[    27.824] (II) UnloadModule: "vesa"
[    27.824] (II) Unloading vesa
[    27.824] (II) Failed to load module "vesa" (already loaded, 0)
[    27.824] (II) RADEON: Driver for ATI Radeon chipsets:
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
    HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[    27.842] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    27.843] (II) FBDEV: driver for framebuffer: fbdev
[    27.843] (II) VESA: driver for VESA chipsets: vesa
[    27.843] (++) using VT number 7

[    27.843] (II) [KMS] Kernel modesetting enabled.
[    27.843] (WW) Falling back to old probe method for modesetting
[    27.843] (WW) Falling back to old probe method for fbdev
[    27.843] (II) Loading sub module "fbdevhw"
[    27.843] (II) LoadModule: "fbdevhw"
[    27.843] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    27.843] (II) Module fbdevhw: vendor="X.Org Foundation"
[    27.843]     compiled for 1.17.1, module version = 0.0.2
[    27.843]     ABI class: X.Org Video Driver, version 19.0
[    27.843] (WW) Falling back to old probe method for vesa
[    27.843] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    27.843] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    27.844] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    27.844] (==) RADEON(0): Default visual is TrueColor
[    27.844] (==) RADEON(0): RGB weight 888
[    27.844] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    27.844] (--) RADEON(0): Chipset: "ARUBA" (ChipID = 0x9903)
[    27.844] (II) Loading sub module "dri2"
[    27.844] (II) LoadModule: "dri2"
[    27.844] (II) Module "dri2" already built-in
[    27.844] (II) Loading sub module "exa"
[    27.844] (II) LoadModule: "exa"
[    27.844] (II) Loading /usr/lib/xorg/modules/libexa.so
[    27.859] (II) Module exa: vendor="X.Org Foundation"
[    27.859]     compiled for 1.17.1, module version = 2.6.0
[    27.859]     ABI class: X.Org Video Driver, version 19.0
[    27.859] (II) RADEON(0): KMS Color Tiling: enabled
[    27.859] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    27.859] (II) RADEON(0): KMS Pageflipping: enabled
[    27.859] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    29.381] (II) RADEON(0): Output eDP has no monitor section
[    29.555] (II) RADEON(0): Output VGA-0 has no monitor section
[    29.557] (II) RADEON(0): Output HDMI-0 has no monitor section
[    31.585] (II) RADEON(0): EDID for output eDP
[    31.585] (II) RADEON(0): Manufacturer: LGD  Model: 351  Serial#: 0
[    31.585] (II) RADEON(0): Year: 2011  Week: 0
[    31.585] (II) RADEON(0): EDID Version: 1.3
[    31.585] (II) RADEON(0): Digital Display Input
[    31.585] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    31.585] (II) RADEON(0): Gamma: 2.20
[    31.585] (II) RADEON(0): No DPMS capabilities specified
[    31.585] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    31.585] (II) RADEON(0): First detailed timing is preferred mode
[    31.585] (II) RADEON(0): redX: 0.623 redY: 0.369   greenX: 0.346 greenY: 0.610
[    31.585] (II) RADEON(0): blueX: 0.148 blueY: 0.098   whiteX: 0.313 whiteY: 0.329
[    31.585] (II) RADEON(0): Manufacturer's mask: 0
[    31.585] (II) RADEON(0): Supported detailed timing:
[    31.585] (II) RADEON(0): clock: 72.3 MHz   Image Size:  344 x 194 mm
[    31.585] (II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1527 h_border: 0
[    31.585] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    31.585] (II) RADEON(0):  LG Display
[    31.585] (II) RADEON(0):  LP156WH4-TPA1
[    31.585] (II) RADEON(0): EDID (in hex):
[    31.585] (II) RADEON(0):     00ffffffffffff0030e4510300000000
[    31.585] (II) RADEON(0):     00150103802213780aa9059f5e589c26
[    31.585] (II) RADEON(0):     19505400000001010101010101010101
[    31.585] (II) RADEON(0):     0101010101013e1c56a1500016303020
[    31.585] (II) RADEON(0):     350058c2100000190000000000000000
[    31.585] (II) RADEON(0):     00000000000000000000000000fe004c
[    31.585] (II) RADEON(0):     4720446973706c61790a2020000000fe
[    31.585] (II) RADEON(0):     004c503135365748342d5450413100f0
[    31.585] (II) RADEON(0): Printing probed modes for output eDP
[    31.585] (II) RADEON(0): Modeline "1366x768"x59.9   72.30  1366 1414 1446 1527  768 771 776 790 -hsync -vsync (47.3 kHz eP)
[    31.585] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    31.585] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    31.585] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    31.585] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    31.585] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    31.585] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    31.585] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    31.754] (II) RADEON(0): EDID for output VGA-0
[    31.757] (II) RADEON(0): EDID for output HDMI-0
[    31.757] (II) RADEON(0): Output eDP connected
[    31.757] (II) RADEON(0): Output VGA-0 disconnected
[    31.757] (II) RADEON(0): Output HDMI-0 disconnected
[    31.757] (II) RADEON(0): Using exact sizes for initial modes
[    31.757] (II) RADEON(0): Output eDP using initial mode 1366x768
[    31.757] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    31.757] (II) RADEON(0): mem size init: gart size :3fdce000 vram size: s:20000000 visible:1f765000
[    31.757] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    31.757] (==) RADEON(0): DPI set to (96, 96)
[    31.757] (II) Loading sub module "fb"
[    31.757] (II) LoadModule: "fb"
[    31.757] (II) Loading /usr/lib/xorg/modules/libfb.so
[    31.758] (II) Module fb: vendor="X.Org Foundation"
[    31.758]     compiled for 1.17.1, module version = 1.0.0
[    31.758]     ABI class: X.Org ANSI C Emulation, version 0.4
[    31.758] (II) Loading sub module "ramdac"
[    31.758] (II) LoadModule: "ramdac"
[    31.758] (II) Module "ramdac" already built-in
[    31.758] (II) UnloadModule: "modesetting"
[    31.758] (II) Unloading modesetting
[    31.758] (II) UnloadModule: "fbdev"
[    31.758] (II) Unloading fbdev
[    31.758] (II) UnloadSubModule: "fbdevhw"
[    31.758] (II) Unloading fbdevhw
[    31.758] (II) UnloadModule: "vesa"
[    31.758] (II) Unloading vesa
[    31.758] (--) Depth 24 pixmap format is 32 bpp
[    31.758] (II) RADEON(0): [DRI2] Setup complete
[    31.758] (II) RADEON(0): [DRI2]   DRI driver: r600
[    31.758] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    31.758] (II) RADEON(0): Front buffer size: 4128K
[    31.758] (II) RADEON(0): VRAM usage limit set to 460155K
[    31.758] (==) RADEON(0): Backing store enabled
[    31.758] (II) RADEON(0): Direct rendering enabled
[    31.759] (II) EXA(0): Driver allocated offscreen pixmaps
[    31.759] (II) EXA(0): Driver registered support for the following operations:
[    31.759] (II)         Solid
[    31.759] (II)         Copy
[    31.759] (II)         Composite (RENDER acceleration)
[    31.759] (II)         UploadToScreen
[    31.759] (II)         DownloadFromScreen
[    31.759] (II) RADEON(0): Acceleration enabled
[    31.759] (==) RADEON(0): DPMS enabled
[    31.759] (==) RADEON(0): Silken mouse enabled
[    31.759] (II) RADEON(0): Set up textured video
[    31.759] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    31.759] (II) RADEON(0): [XvMC] Extension initialized.
[    31.759] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    31.759] (--) RandR disabled
[    31.767] (II) SELinux: Disabled on system
[    32.476] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    32.476] (II) AIGLX: enabled GLX_ARB_create_context
[    32.476] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    32.476] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    32.476] (II) AIGLX: enabled GLX_INTEL_swap_event
[    32.476] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    32.476] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    32.476] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    32.476] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    32.477] (II) AIGLX: Loaded and initialized r600
[    32.477] (II) GLX: Initialized DRI2 GL provider for screen 0
[    33.864] (II) RADEON(0): Setting screen physical size to 361 x 203
[    33.897] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.928] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    33.928] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.928] (II) LoadModule: "evdev"
[    33.928] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.947] (II) Module evdev: vendor="X.Org Foundation"
[    33.947]     compiled for 1.16.0, module version = 2.9.0
[    33.947]     Module class: X.Org XInput Driver
[    33.947]     ABI class: X.Org XInput driver, version 21.0
[    33.947] (II) Using input driver 'evdev' for 'Power Button'
[    33.947] (**) Power Button: always reports core events
[    33.947] (**) evdev: Power Button: Device: "/dev/input/event3"
[    33.948] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.948] (--) evdev: Power Button: Found keys
[    33.948] (II) evdev: Power Button: Configuring as keyboard
[    33.948] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    33.948] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.948] (**) Option "xkb_rules" "evdev"
[    33.948] (**) Option "xkb_model" "pc105"
[    33.948] (**) Option "xkb_layout" "us"
[    33.949] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    33.949] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    33.949] (II) Using input driver 'evdev' for 'Video Bus'
[    33.949] (**) Video Bus: always reports core events
[    33.949] (**) evdev: Video Bus: Device: "/dev/input/event9"
[    33.949] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    33.949] (--) evdev: Video Bus: Found keys
[    33.949] (II) evdev: Video Bus: Configuring as keyboard
[    33.949] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10/event9"
[    33.949] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    33.949] (**) Option "xkb_rules" "evdev"
[    33.949] (**) Option "xkb_model" "pc105"
[    33.949] (**) Option "xkb_layout" "us"
[    33.950] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    33.950] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.950] (II) Using input driver 'evdev' for 'Power Button'
[    33.950] (**) Power Button: always reports core events
[    33.950] (**) evdev: Power Button: Device: "/dev/input/event0"
[    33.950] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.950] (--) evdev: Power Button: Found keys
[    33.950] (II) evdev: Power Button: Configuring as keyboard
[    33.950] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    33.950] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    33.950] (**) Option "xkb_rules" "evdev"
[    33.950] (**) Option "xkb_model" "pc105"
[    33.950] (**) Option "xkb_layout" "us"
[    33.951] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    33.951] (II) No input driver specified, ignoring this device.
[    33.951] (II) This device may have been added with another device file.
[    33.951] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    33.951] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    33.951] (II) Using input driver 'evdev' for 'Sleep Button'
[    33.951] (**) Sleep Button: always reports core events
[    33.951] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    33.951] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    33.951] (--) evdev: Sleep Button: Found keys
[    33.951] (II) evdev: Sleep Button: Configuring as keyboard
[    33.951] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    33.951] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    33.951] (**) Option "xkb_rules" "evdev"
[    33.951] (**) Option "xkb_model" "pc105"
[    33.951] (**) Option "xkb_layout" "us"
[    33.952] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event10)
[    33.952] (II) No input driver specified, ignoring this device.
[    33.952] (II) This device may have been added with another device file.
[    33.953] (II) config/udev: Adding input device Turtle Beach Turtle Beach PX22 (/dev/input/event5)
[    33.953] (**) Turtle Beach Turtle Beach PX22: Applying InputClass "evdev keyboard catchall"
[    33.953] (II) Using input driver 'evdev' for 'Turtle Beach Turtle Beach PX22'
[    33.953] (**) Turtle Beach Turtle Beach PX22: always reports core events
[    33.953] (**) evdev: Turtle Beach Turtle Beach PX22: Device: "/dev/input/event5"
[    33.953] (--) evdev: Turtle Beach Turtle Beach PX22: Vendor 0x10f5 Product 0x290
[    33.953] (--) evdev: Turtle Beach Turtle Beach PX22: Found keys
[    33.953] (II) evdev: Turtle Beach Turtle Beach PX22: Configuring as keyboard
[    33.953] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.3/0003:10F5:0290.0001/input/input7/event5"
[    33.953] (II) XINPUT: Adding extended input device "Turtle Beach Turtle Beach PX22" (type: KEYBOARD, id 10)
[    33.953] (**) Option "xkb_rules" "evdev"
[    33.953] (**) Option "xkb_model" "pc105"
[    33.953] (**) Option "xkb_layout" "us"
[    33.954] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    33.954] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    33.954] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    33.954] (**) Logitech USB Receiver: always reports core events
[    33.954] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event6"
[    34.008] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[    34.008] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[    34.008] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    34.008] (--) evdev: Logitech USB Receiver: Found relative axes
[    34.008] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    34.008] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    34.008] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    34.008] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    34.008] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    34.008] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb5/5-1/5-1:1.0/0003:046D:C52F.0002/input/input8/event6"
[    34.008] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 11)
[    34.008] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    34.009] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    34.009] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    34.009] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    34.009] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    34.009] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    34.009] (II) No input driver specified, ignoring this device.
[    34.009] (II) This device may have been added with another device file.
[    34.010] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[    34.010] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    34.010] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    34.010] (**) Logitech USB Receiver: always reports core events
[    34.010] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event7"
[    34.010] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[    34.010] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[    34.010] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    34.010] (--) evdev: Logitech USB Receiver: Found relative axes
[    34.010] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[    34.010] (--) evdev: Logitech USB Receiver: Found absolute axes
[    34.010] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[    34.010] (--) evdev: Logitech USB Receiver: Found keys
[    34.010] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    34.010] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    34.010] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    34.010] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    34.010] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    34.010] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb5/5-1/5-1:1.1/0003:046D:C52F.0003/input/input9/event7"
[    34.010] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 12)
[    34.010] (**) Option "xkb_rules" "evdev"
[    34.010] (**) Option "xkb_model" "pc105"
[    34.010] (**) Option "xkb_layout" "us"
[    34.011] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    34.011] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[    34.011] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    34.011] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    34.011] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    34.011] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    34.011] (II) config/udev: Adding input device HD WebCam (/dev/input/event15)
[    34.012] (**) HD WebCam: Applying InputClass "evdev keyboard catchall"
[    34.012] (II) Using input driver 'evdev' for 'HD WebCam'
[    34.012] (**) HD WebCam: always reports core events
[    34.012] (**) evdev: HD WebCam: Device: "/dev/input/event15"
[    34.012] (--) evdev: HD WebCam: Vendor 0x1bcf Product 0x2c18
[    34.012] (--) evdev: HD WebCam: Found keys
[    34.012] (II) evdev: HD WebCam: Configuring as keyboard
[    34.012] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb4/4-1/4-1:1.0/input/input16/event15"
[    34.012] (II) XINPUT: Adding extended input device "HD WebCam" (type: KEYBOARD, id 13)
[    34.012] (**) Option "xkb_rules" "evdev"
[    34.012] (**) Option "xkb_model" "pc105"
[    34.012] (**) Option "xkb_layout" "us"
[    34.013] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event11)
[    34.013] (II) No input driver specified, ignoring this device.
[    34.013] (II) This device may have been added with another device file.
[    34.013] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event12)
[    34.013] (II) No input driver specified, ignoring this device.
[    34.013] (II) This device may have been added with another device file.
[    34.013] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    34.013] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    34.013] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    34.014] (**) AT Translated Set 2 keyboard: always reports core events
[    34.014] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    34.014] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    34.014] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    34.014] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    34.014] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    34.014] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    34.014] (**) Option "xkb_rules" "evdev"
[    34.014] (**) Option "xkb_model" "pc105"
[    34.014] (**) Option "xkb_layout" "us"
[    34.014] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[    34.015] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    34.015] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    34.015] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    34.015] (II) LoadModule: "synaptics"
[    34.015] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    34.015] (II) Module synaptics: vendor="X.Org Foundation"
[    34.015]     compiled for 1.16.0, module version = 1.8.99
[    34.015]     Module class: X.Org XInput Driver
[    34.015]     ABI class: X.Org XInput driver, version 21.0
[    34.015] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    34.015] (**) ETPS/2 Elantech Touchpad: always reports core events
[    34.015] (**) Option "Device" "/dev/input/event8"
[    34.024] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2728 (res 0)
[    34.024] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1116 (res 0)
[    34.024] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    34.024] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    34.024] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    34.024] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    34.024] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    34.024] (**) ETPS/2 Elantech Touchpad: always reports core events
[    34.036] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event8"
[    34.036] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 15)
[    34.036] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    34.036] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    34.036] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.068
[    34.036] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    34.037] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    34.037] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    34.037] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    34.037] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    34.037] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    34.037] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    34.040] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event13)
[    34.040] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    34.040] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    34.040] (**) Acer WMI hotkeys: always reports core events
[    34.040] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event13"
[    34.040] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    34.040] (--) evdev: Acer WMI hotkeys: Found keys
[    34.040] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    34.040] (**) Option "config_info" "udev:/sys/devices/virtual/input/input14/event13"
[    34.040] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 16)
[    34.040] (**) Option "xkb_rules" "evdev"
[    34.040] (**) Option "xkb_model" "pc105"
[    34.040] (**) Option "xkb_layout" "us"
[    34.041] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event14)
[    34.041] (II) No input driver specified, ignoring this device.
[    34.041] (II) This device may have been added with another device file.
[    34.041] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[    34.041] (II) No input driver specified, ignoring this device.
[    34.041] (II) This device may have been added with another device file.
[    39.174] (II) RADEON(0): EDID vendor "LGD", prod id 849
[    39.174] (II) RADEON(0): Printing DDC gathered Modelines:
[    39.174] (II) RADEON(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1527  768 771 776 790 -hsync -vsync (47.3 kHz eP)
[    42.539] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    46.657] (II) RADEON(0): EDID vendor "LGD", prod id 849
[    46.657] (II) RADEON(0): Printing DDC gathered Modelines:
[    46.657] (II) RADEON(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1527  768 771 776 790 -hsync -vsync (47.3 kHz eP)
[    48.031] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    56.310] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    58.547] (II) RADEON(0): EDID vendor "LGD", prod id 849
[    58.548] (II) RADEON(0): Printing DDC gathered Modelines:
[    58.548] (II) RADEON(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1527  768 771 776 790 -hsync -vsync (47.3 kHz eP)
[    59.754] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    63.452] (II) RADEON(0): EDID vendor "LGD", prod id 849
[    63.452] (II) RADEON(0): Printing DDC gathered Modelines:
[    63.452] (II) RADEON(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1527  768 771 776 790 -hsync -vsync (47.3 kHz eP)
[    63.965] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm


```

---

### Post by QIII on 2015-10-08
Hello!

A bit more information would be helpful.

What release of Ubuntu are you using?  What model of graphics adapter? How are you installing the driver?

---

### Post by rschanzenbacher on 2015-10-08
Ubuntu Gnome 15.04 ; AMD Radeon HD 7640G Graphics ; Using the additional drivers dialogue. I already tried booing using nomodeset also. Sorry I'm really tired. ;)

---

### Post by QIII on 2015-10-08
After you installed the driver, did you do

```
sudo amdconfig --initial 
```

---

### Post by rschanzenbacher on 2015-10-08
I'll try.

Didn't Work. Gonna try downloading from ATI site.

---

### Post by QIII on 2015-10-08
Did you reboot after issuing that command?

---

### Post by P-I H on 2015-10-09
I am using Steam with the open source driver for Radeon.
To get it to work I run this command in a terminal.
```
find ~/.steam/root/ \( -name "libgcc_s.so*" -o -name "libstdc++.so*" -o -name "libxcb.so*" \) -print -delete
```

There are some explanations on this site [https://wiki.archlinux.org/index.php/Steam](https://wiki.archlinux.org/index.php/Steam)

---

