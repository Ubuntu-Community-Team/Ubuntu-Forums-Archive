---
title: "xorg.0.log keeps growing"
date: 2016-06-02
forum: General Help
---

### Post by Ashok_Narendranath on 2016-06-02
xorg.0.log file keeps growing and ultimately causes the system to crash. 

[  xxxx.xxxx] reporting 10 7 27 221 statement is constantly added.

Please help me fix this.

```
xorg.0.log

[    22.572] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[    22.572] X Protocol Version 11, Revision 0
[    22.572] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    22.572] Current Operating System: Linux vaisagh-Alienware-X51-R2 3.16.0-71-generic #92~14.04.1-Ubuntu SMP Thu May 12 23:31:46 UTC 2016 x86_64
[    22.572] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-71-generic.efi.signed root=UUID=8524f180-34be-4f41-aae3-f633e6611b79 ro quiet splash vt.handoff=7
[    22.572] Build Date: 12 February 2015  11:11:26PM
[    22.572] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.572] Current version of pixman: 0.30.2
[    22.572]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    22.572] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.572] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  2 14:25:41 2016
[    22.591] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.592] (==) No Layout section.  Using the first Screen section.
[    22.592] (==) No screen section available. Using defaults.
[    22.592] (**) |-->Screen "Default Screen Section" (0)
[    22.592] (**) |   |-->Monitor "<default monitor>"
[    22.592] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    22.592] (==) Automatically adding devices
[    22.592] (==) Automatically enabling devices
[    22.592] (==) Automatically adding GPU devices
[    22.592] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.592]     Entry deleted from font path.
[    22.592] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.592]     Entry deleted from font path.
[    22.592] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.592]     Entry deleted from font path.
[    22.592] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.592]     Entry deleted from font path.
[    22.592] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.592]     Entry deleted from font path.
[    22.592] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    22.592] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.592] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.592] (II) Loader magic: 0x7f1abb33dc80
[    22.592] (II) Module ABI versions:
[    22.592]     X.Org ANSI C Emulation: 0.4
[    22.592]     X.Org Video Driver: 18.0
[    22.592]     X.Org XInput driver : 21.0
[    22.592]     X.Org Server Extension : 8.0
[    22.592] (II) xfree86: Adding drm device (/dev/dri/card1)
[    22.592] (II) xfree86: Adding drm device (/dev/dri/card0)
[    22.593] (--) PCI:*(0:0:2:0) 8086:0412:1028:05d7 rev 6, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    22.593] (--) PCI: (0:1:0:0) 1002:6811:1028:0b00 rev 129, Mem @ 0xe0000000/268435456, 0xf7c00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    22.593] (II) LoadModule: "glx"
[    22.632] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.270] (II) Module glx: vendor="X.Org Foundation"
[    23.270]     compiled for 1.16.0, module version = 1.0.0
[    23.270]     ABI class: X.Org Server Extension, version 8.0
[    23.270] (==) AIGLX enabled
[    23.270] (==) Matched intel as autoconfigured driver 0
[    23.270] (==) Matched fglrx as autoconfigured driver 1
[    23.270] (==) Matched ati as autoconfigured driver 2
[    23.270] (==) Matched intel as autoconfigured driver 3
[    23.270] (==) Matched modesetting as autoconfigured driver 4
[    23.270] (==) Matched fbdev as autoconfigured driver 5
[    23.270] (==) Matched vesa as autoconfigured driver 6
[    23.270] (==) Assigned the driver to the xf86ConfigLayout
[    23.270] (II) LoadModule: "intel"
[    23.270] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    23.450] (II) Module intel: vendor="X.Org Foundation"
[    23.450]     compiled for 1.16.0, module version = 2.99.914
[    23.450]     Module class: X.Org Video Driver
[    23.450]     ABI class: X.Org Video Driver, version 18.0
[    23.450] (II) LoadModule: "fglrx"
[    23.453] (WW) Warning, couldn't open module fglrx
[    23.453] (II) UnloadModule: "fglrx"
[    23.453] (II) Unloading fglrx
[    23.453] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    23.453] (II) LoadModule: "ati"
[    23.453] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    23.469] (II) Module ati: vendor="X.Org Foundation"
[    23.469]     compiled for 1.16.0, module version = 7.4.0
[    23.470]     Module class: X.Org Video Driver
[    23.470]     ABI class: X.Org Video Driver, version 18.0
[    23.470] (II) LoadModule: "radeon"
[    23.470] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    23.595] (II) Module radeon: vendor="X.Org Foundation"
[    23.595]     compiled for 1.16.0, module version = 7.4.0
[    23.595]     Module class: X.Org Video Driver
[    23.595]     ABI class: X.Org Video Driver, version 18.0
[    23.595] (II) LoadModule: "modesetting"
[    23.595] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.628] (II) Module modesetting: vendor="X.Org Foundation"
[    23.628]     compiled for 1.16.0, module version = 0.9.0
[    23.628]     Module class: X.Org Video Driver
[    23.628]     ABI class: X.Org Video Driver, version 18.0
[    23.628] (II) LoadModule: "fbdev"
[    23.628] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.638] (II) Module fbdev: vendor="X.Org Foundation"
[    23.638]     compiled for 1.16.0, module version = 0.4.4
[    23.638]     Module class: X.Org Video Driver
[    23.638]     ABI class: X.Org Video Driver, version 18.0
[    23.638] (II) LoadModule: "vesa"
[    23.638] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.658] (II) Module vesa: vendor="X.Org Foundation"
[    23.658]     compiled for 1.16.0, module version = 2.3.3
[    23.658]     Module class: X.Org Video Driver
[    23.658]     ABI class: X.Org Video Driver, version 18.0
[    23.658] (==) Matched intel as autoconfigured driver 0
[    23.658] (==) Matched fglrx as autoconfigured driver 1
[    23.658] (==) Matched ati as autoconfigured driver 2
[    23.658] (==) Matched intel as autoconfigured driver 3
[    23.658] (==) Matched modesetting as autoconfigured driver 4
[    23.658] (==) Matched fbdev as autoconfigured driver 5
[    23.658] (==) Matched vesa as autoconfigured driver 6
[    23.658] (==) Assigned the driver to the xf86ConfigLayout
[    23.658] (II) LoadModule: "intel"
[    23.658] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    23.658] (II) Module intel: vendor="X.Org Foundation"
[    23.658]     compiled for 1.16.0, module version = 2.99.914
[    23.658]     Module class: X.Org Video Driver
[    23.658]     ABI class: X.Org Video Driver, version 18.0
[    23.658] (II) UnloadModule: "intel"
[    23.658] (II) Unloading intel
[    23.658] (II) Failed to load module "intel" (already loaded, 32538)
[    23.658] (II) LoadModule: "fglrx"
[    23.658] (WW) Warning, couldn't open module fglrx
[    23.658] (II) UnloadModule: "fglrx"
[    23.658] (II) Unloading fglrx
[    23.658] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    23.658] (II) LoadModule: "ati"
[    23.658] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    23.658] (II) Module ati: vendor="X.Org Foundation"
[    23.658]     compiled for 1.16.0, module version = 7.4.0
[    23.658]     Module class: X.Org Video Driver
[    23.658]     ABI class: X.Org Video Driver, version 18.0
[    23.658] (II) LoadModule: "modesetting"
[    23.658] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.658] (II) Module modesetting: vendor="X.Org Foundation"
[    23.658]     compiled for 1.16.0, module version = 0.9.0
[    23.658]     Module class: X.Org Video Driver
[    23.658]     ABI class: X.Org Video Driver, version 18.0
[    23.658] (II) UnloadModule: "modesetting"
[    23.658] (II) Unloading modesetting
[    23.658] (II) Failed to load module "modesetting" (already loaded, 0)
[    23.658] (II) LoadModule: "fbdev"
[    23.658] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.658] (II) Module fbdev: vendor="X.Org Foundation"
[    23.658]     compiled for 1.16.0, module version = 0.4.4
[    23.658]     Module class: X.Org Video Driver
[    23.658]     ABI class: X.Org Video Driver, version 18.0
[    23.658] (II) UnloadModule: "fbdev"
[    23.658] (II) Unloading fbdev
[    23.658] (II) Failed to load module "fbdev" (already loaded, 0)
[    23.658] (II) LoadModule: "vesa"
[    23.658] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.658] (II) Module vesa: vendor="X.Org Foundation"
[    23.658]     compiled for 1.16.0, module version = 2.3.3
[    23.658]     Module class: X.Org Video Driver
[    23.658]     ABI class: X.Org Video Driver, version 18.0
[    23.658] (II) UnloadModule: "vesa"
[    23.658] (II) Unloading vesa
[    23.658] (II) Failed to load module "vesa" (already loaded, 0)
[    23.658] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    23.693] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    23.693] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    23.693] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    23.693] (II) RADEON: Driver for ATI Radeon chipsets:
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
    VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
    HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[    23.695] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    23.695] (II) FBDEV: driver for framebuffer: fbdev
[    23.695] (II) VESA: driver for VESA chipsets: vesa
[    23.695] (++) using VT number 7

[    23.710] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    23.710] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-utopic 2:2.99.914-1~exp1ubuntu4.5~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[    23.710] (II) intel(0): SNA compiled for use with valgrind
[    23.710] (II) [KMS] Kernel modesetting enabled.
[    23.710] (WW) Falling back to old probe method for modesetting
[    23.710] (WW) Falling back to old probe method for fbdev
[    23.710] (II) Loading sub module "fbdevhw"
[    23.710] (II) LoadModule: "fbdevhw"
[    23.710] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.724] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.725]     compiled for 1.16.0, module version = 0.0.2
[    23.725]     ABI class: X.Org Video Driver, version 18.0
[    23.725] (WW) Falling back to old probe method for vesa
[    23.738] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    23.738] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[    23.738] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    23.738] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    23.738] (==) intel(0): RGB weight 888
[    23.738] (==) intel(0): Default visual is TrueColor
[    23.738] (II) intel(0): Output VGA1 has no monitor section
[    23.738] (II) intel(0): Output HDMI1 has no monitor section
[    23.738] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    23.738] (II) intel(0): Output VIRTUAL1 has no monitor section
[    23.738] (--) intel(0): Output HDMI1 using initial mode 1920x1080 on pipe 0
[    23.738] (==) intel(0): TearFree disabled
[    23.738] (==) intel(0): DPI set to (96, 96)
[    23.738] (II) Loading sub module "dri2"
[    23.738] (II) LoadModule: "dri2"
[    23.738] (II) Module "dri2" already built-in
[    23.738] (II) Loading sub module "present"
[    23.738] (II) LoadModule: "present"
[    23.738] (II) Module "present" already built-in
[    23.738] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[    23.738] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    23.738] (==) RADEON(G0): Default visual is TrueColor
[    23.738] (==) RADEON(G0): RGB weight 888
[    23.738] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[    23.738] (--) RADEON(G0): Chipset: "PITCAIRN" (ChipID = 0x6811)
[    23.738] (II) Loading sub module "dri2"
[    23.738] (II) LoadModule: "dri2"
[    23.738] (II) Module "dri2" already built-in
[    23.738] (II) Loading sub module "glamoregl"
[    23.738] (II) LoadModule: "glamoregl"
[    23.738] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    24.059] (II) Module glamoregl: vendor="X.Org Foundation"
[    24.059]     compiled for 1.16.0, module version = 1.0.0
[    24.059]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.059] (II) glamor: OpenGL accelerated X.org driver based.
[    27.926] (II) glamor: EGL version 1.4 (DRI2):
[    28.050] (II) RADEON(G0): glamor detected, initialising EGL layer.
[    28.050] (II) RADEON(G0): KMS Color Tiling: enabled
[    28.050] (II) RADEON(G0): KMS Color Tiling 2D: enabled
[    28.050] (II) RADEON(G0): KMS Pageflipping: enabled
[    28.050] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[    28.056] (II) RADEON(G0): Output DisplayPort-1-0 has no monitor section
[    28.057] (II) RADEON(G0): Output HDMI-1-1 has no monitor section
[    28.068] (II) RADEON(G0): Output DVI-1-0 has no monitor section
[    28.075] (II) RADEON(G0): Output DVI-1-0 has no monitor section
[    28.080] (II) RADEON(G0): EDID for output DisplayPort-1-0
[    28.081] (II) RADEON(G0): EDID for output HDMI-1-1
[    28.092] (II) RADEON(G0): EDID for output DVI-1-0
[    28.093] (II) RADEON(G0): EDID for output DVI-1-0
[    28.093] (II) RADEON(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    28.093] (II) RADEON(G0): mem size init: gart size :3fbde000 vram size: s:100000000 visible:ffcc0000
[    28.093] (==) RADEON(G0): DPI set to (96, 96)
[    28.093] (II) Loading sub module "fb"
[    28.093] (II) LoadModule: "fb"
[    28.093] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.093] (II) Module fb: vendor="X.Org Foundation"
[    28.093]     compiled for 1.16.0, module version = 1.0.0
[    28.093]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.093] (II) Loading sub module "ramdac"
[    28.093] (II) LoadModule: "ramdac"
[    28.093] (II) Module "ramdac" already built-in
[    28.093] (II) UnloadModule: "modesetting"
[    28.093] (II) Unloading modesetting
[    28.093] (II) UnloadModule: "fbdev"
[    28.093] (II) Unloading fbdev
[    28.094] (II) UnloadSubModule: "fbdevhw"
[    28.094] (II) Unloading fbdevhw
[    28.094] (II) UnloadModule: "vesa"
[    28.094] (II) Unloading vesa
[    28.094] (==) Depth 24 pixmap format is 32 bpp
[    28.094] (II) RADEON(G0): [DRI2] Setup complete
[    28.094] (II) RADEON(G0): [DRI2]   DRI driver: radeonsi
[    28.094] (II) RADEON(G0): [DRI2]   VDPAU driver: radeonsi
[    28.094] (II) RADEON(G0): Front buffer size: 3072K
[    28.094] (II) RADEON(G0): VRAM usage limit set to 3769027K
[    28.094] (==) RADEON(G0): Backing store enabled
[    28.094] (II) RADEON(G0): Direct rendering enabled
[    28.219] (II) RADEON(G0): Use GLAMOR acceleration.
[    28.219] (II) RADEON(G0): Acceleration enabled
[    28.219] (==) RADEON(G0): DPMS enabled
[    28.219] (==) RADEON(G0): Silken mouse enabled
[    28.220] (II) RADEON(G0): Set up textured video (glamor)
[    28.220] (II) RADEON(G0): [XvMC] Associated with GLAMOR Textured Video.
[    28.220] (EE) RADEON(G0): [XvMC] Failed to initialize extension.
[    28.220] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.237] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    28.237] (==) intel(0): Backing store enabled
[    28.237] (==) intel(0): Silken mouse enabled
[    28.237] (II) intel(0): HW Cursor enabled
[    28.237] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.237] (==) intel(0): DPMS enabled
[    28.237] (II) intel(0): [DRI2] Setup complete
[    28.237] (II) intel(0): [DRI2]   DRI driver: i965
[    28.237] (II) intel(0): [DRI2]   VDPAU driver: i965
[    28.237] (II) intel(0): direct rendering: DRI2 enabled
[    28.237] (II) intel(0): hardware support for Present enabled
[    28.237] (==) intel(0): display hotplug detection enabled
[    28.237] (--) RandR disabled
[    28.320] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    28.320] (II) AIGLX: enabled GLX_ARB_create_context
[    28.320] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    28.320] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    28.320] (II) AIGLX: enabled GLX_INTEL_swap_event
[    28.320] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    28.320] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    28.320] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    28.320] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    28.320] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    28.320] (II) AIGLX: Loaded and initialized i965
[    28.320] (II) GLX: Initialized DRI2 GL provider for screen 0
[    28.331] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[    28.340] (II) intel(0): Setting screen physical size to 508 x 285
[    28.344] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.345] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.345] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.345] (II) LoadModule: "evdev"
[    28.346] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.364] (II) Module evdev: vendor="X.Org Foundation"
[    28.364]     compiled for 1.16.0, module version = 2.9.0
[    28.364]     Module class: X.Org XInput Driver
[    28.364]     ABI class: X.Org XInput driver, version 21.0
[    28.364] (II) Using input driver 'evdev' for 'Power Button'
[    28.364] (**) Power Button: always reports core events
[    28.364] (**) evdev: Power Button: Device: "/dev/input/event1"
[    28.364] (--) evdev: Power Button: Vendor 0 Product 0x1
[    28.364] (--) evdev: Power Button: Found keys
[    28.364] (II) evdev: Power Button: Configuring as keyboard
[    28.364] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    28.364] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    28.364] (**) Option "xkb_rules" "evdev"
[    28.364] (**) Option "xkb_model" "pc105"
[    28.364] (**) Option "xkb_layout" "us"
[    28.365] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    28.365] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.365] (II) Using input driver 'evdev' for 'Video Bus'
[    28.365] (**) Video Bus: always reports core events
[    28.365] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    28.365] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    28.365] (--) evdev: Video Bus: Found keys
[    28.365] (II) evdev: Video Bus: Configuring as keyboard
[    28.365] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8/event5"
[    28.365] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    28.365] (**) Option "xkb_rules" "evdev"
[    28.365] (**) Option "xkb_model" "pc105"
[    28.365] (**) Option "xkb_layout" "us"
[    28.365] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    28.365] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.365] (II) Using input driver 'evdev' for 'Power Button'
[    28.365] (**) Power Button: always reports core events
[    28.365] (**) evdev: Power Button: Device: "/dev/input/event0"
[    28.365] (--) evdev: Power Button: Vendor 0 Product 0x1
[    28.365] (--) evdev: Power Button: Found keys
[    28.365] (II) evdev: Power Button: Configuring as keyboard
[    28.365] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    28.365] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    28.365] (**) Option "xkb_rules" "evdev"
[    28.365] (**) Option "xkb_model" "pc105"
[    28.365] (**) Option "xkb_layout" "us"
[    28.365] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event7)
[    28.365] (II) No input driver specified, ignoring this device.
[    28.365] (II) This device may have been added with another device file.
[    28.365] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event8)
[    28.366] (II) No input driver specified, ignoring this device.
[    28.366] (II) This device may have been added with another device file.
[    28.366] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event9)
[    28.366] (II) No input driver specified, ignoring this device.
[    28.366] (II) This device may have been added with another device file.
[    28.366] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event10)
[    28.366] (II) No input driver specified, ignoring this device.
[    28.366] (II) This device may have been added with another device file.
[    28.366] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event11)
[    28.366] (II) No input driver specified, ignoring this device.
[    28.366] (II) This device may have been added with another device file.
[    28.366] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event6)
[    28.366] (II) No input driver specified, ignoring this device.
[    28.366] (II) This device may have been added with another device file.
[    28.366] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event20)
[    28.366] (II) No input driver specified, ignoring this device.
[    28.366] (II) This device may have been added with another device file.
[    28.366] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event2)
[    28.366] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    28.366] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    28.366] (**) USB Optical Mouse: always reports core events
[    28.366] (**) evdev: USB Optical Mouse: Device: "/dev/input/event2"
[    28.366] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d65
[    28.366] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    28.366] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    28.366] (--) evdev: USB Optical Mouse: Found relative axes
[    28.366] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    28.366] (II) evdev: USB Optical Mouse: Configuring as mouse
[    28.366] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    28.366] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    28.366] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.366] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/0003:0461:4D65.0001/input/input5/event2"
[    28.366] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 9)
[    28.366] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    28.366] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    28.366] (**) USB Optical Mouse: (accel) acceleration profile 0
[    28.366] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    28.366] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    28.367] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    28.367] (II) No input driver specified, ignoring this device.
[    28.367] (II) This device may have been added with another device file.
[    28.367] (II) config/udev: Adding input device Lite-On Technology Corp. USB Multimedia Keyboard (/dev/input/event3)
[    28.367] (**) Lite-On Technology Corp. USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[    28.367] (II) Using input driver 'evdev' for 'Lite-On Technology Corp. USB Multimedia Keyboard'
[    28.367] (**) Lite-On Technology Corp. USB Multimedia Keyboard: always reports core events
[    28.367] (**) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Device: "/dev/input/event3"
[    28.367] (--) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Vendor 0x4ca Product 0x27
[    28.367] (--) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Found keys
[    28.367] (II) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Configuring as keyboard
[    28.367] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/0003:04CA:0027.0002/input/input6/event3"
[    28.367] (II) XINPUT: Adding extended input device "Lite-On Technology Corp. USB Multimedia Keyboard" (type: KEYBOARD, id 10)
[    28.367] (**) Option "xkb_rules" "evdev"
[    28.367] (**) Option "xkb_model" "pc105"
[    28.367] (**) Option "xkb_layout" "us"
[    28.367] (II) config/udev: Adding input device Lite-On Technology Corp. USB Multimedia Keyboard (/dev/input/event4)
[    28.367] (**) Lite-On Technology Corp. USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[    28.367] (II) Using input driver 'evdev' for 'Lite-On Technology Corp. USB Multimedia Keyboard'
[    28.367] (**) Lite-On Technology Corp. USB Multimedia Keyboard: always reports core events
[    28.367] (**) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Device: "/dev/input/event4"
[    28.367] (--) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Vendor 0x4ca Product 0x27
[    28.367] (--) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Found 20 mouse buttons
[    28.367] (--) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Found keys
[    28.367] (II) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Forcing relative x/y axes to exist.
[    28.367] (II) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Configuring as mouse
[    28.367] (II) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: Configuring as keyboard
[    28.367] (**) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: YAxisMapping: buttons 4 and 5
[    28.367] (**) evdev: Lite-On Technology Corp. USB Multimedia Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.367] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/0003:04CA:0027.0003/input/input7/event4"
[    28.367] (II) XINPUT: Adding extended input device "Lite-On Technology Corp. USB Multimedia Keyboard" (type: KEYBOARD, id 11)
[    28.367] (**) Option "xkb_rules" "evdev"
[    28.367] (**) Option "xkb_model" "pc105"
[    28.367] (**) Option "xkb_layout" "us"
[    28.367] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event12)
[    28.367] (II) No input driver specified, ignoring this device.
[    28.367] (II) This device may have been added with another device file.
[    28.367] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event13)
[    28.368] (II) No input driver specified, ignoring this device.
[    28.368] (II) This device may have been added with another device file.
[    28.368] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event14)
[    28.368] (II) No input driver specified, ignoring this device.
[    28.368] (II) This device may have been added with another device file.
[    28.368] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event15)
[    28.368] (II) No input driver specified, ignoring this device.
[    28.368] (II) This device may have been added with another device file.
[    28.368] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event16)
[    28.368] (II) No input driver specified, ignoring this device.
[    28.368] (II) This device may have been added with another device file.
[    28.368] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event17)
[    28.368] (II) No input driver specified, ignoring this device.
[    28.368] (II) This device may have been added with another device file.
[    28.368] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event18)
[    28.368] (II) No input driver specified, ignoring this device.
[    28.368] (II) This device may have been added with another device file.
[    28.368] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event19)
[    28.368] (II) No input driver specified, ignoring this device.
[    28.368] (II) This device may have been added with another device file.
[    28.861] reporting 10 7 1 9
[    29.772] reporting 10 7 1 9
[    29.838] (II) intel(0): EDID vendor "DEL", prod id 53390
[    29.838] (II) intel(0): Using EDID range info for horizontal sync
[    29.838] (II) intel(0): Using EDID range info for vertical refresh
[    29.838] (II) intel(0): Printing DDC gathered Modelines:
[    29.838] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    29.838] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    29.838] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    29.838] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    29.838] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    29.838] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    29.838] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    29.838] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    29.838] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.838] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    29.838] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    29.838] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    29.838] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    29.838] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.838] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    29.838] (II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    29.838] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    29.838] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    29.838] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    29.838] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    29.838] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    29.838] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    29.838] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    29.838] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    29.923] reporting 10 7 27 221
[    29.930] reporting 10 7 27 221
[    29.933] reporting 10 7 27 221
[    30.050] reporting 10 7 27 221
[    30.085] reporting 10 7 27 221
[    30.573] reporting 10 7 27 221
[    30.637] reporting 10 7 27 221
[    30.725] reporting 10 7 27 221
[    30.726] reporting 10 7 27 221
[    31.041] reporting 10 7 27 221
[    31.048] reporting 10 7 27 221
[    31.064] reporting 10 7 27 221
[    31.077] reporting 10 7 27 221
[    46.313] reporting 10 7 27 221
[    46.557] reporting 10 7 27 221
[    46.558] reporting 10 7 27 221
[    46.764] reporting 10 7 27 221
[    47.301] reporting 10 7 27 221
[    47.359] reporting 10 7 27 221
[    47.386] reporting 10 7 27 221
[    47.567] reporting 10 7 27 221
[    47.748] reporting 10 7 27 221
[    47.748] reporting 10 7 27 221
[    48.313] reporting 10 7 27 221
[    48.314] reporting 10 7 27 221
[    48.355] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.384] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.618] reporting 10 7 27 221
[    48.647] reporting 10 7 27 221
[    48.750] reporting 10 7 27 221
[    48.756] reporting 10 7 27 221
[    48.921] reporting 10 7 27 221
[    51.266] reporting 10 7 27 221
[    51.321] reporting 10 7 27 221
[    52.024] reporting 10 7 27 221
[    52.107] reporting 10 7 27 221
[    52.333] reporting 10 7 27 221
[    58.822] reporting 10 7 27 221
[    65.166] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    66.700] reporting 10 7 27 221
[    66.827] reporting 10 7 27 221
[    69.789] reporting 10 7 27 221
[    69.860] reporting 10 7 27 221
[    80.398] reporting 10 7 27 221
[    80.398] reporting 10 7 27 221
[    81.132] reporting 10 7 27 221
[   100.855] reporting 10 7 27 221
[   106.922] reporting 10 7 27 221
[   107.949] reporting 10 7 27 221
[   111.632] reporting 10 7 27 221
[   125.269] reporting 10 7 27 221
[   149.128] reporting 10 7 27 221
[   149.507] reporting 10 7 27 221
[   156.079] reporting 10 7 27 221
[   162.311] reporting 10 7 27 221
[   367.718] reporting 10 7 27 221
[   379.697] reporting 10 7 27 221
[   785.621] reporting 10 7 27 221
[   815.181] reporting 10 7 27 221
[   825.701] reporting 10 7 27 221
[  1119.356] reporting 10 7 27 221
[  1119.386] reporting 10 7 27 221
[  1626.551] reporting 10 7 27 221
[  1626.797] reporting 10 7 27 221
[  1673.246] reporting 10 7 27 221
[  1673.320] reporting 10 7 27 221
[  1739.447] reporting 10 7 27 221
[  1745.571] reporting 10 7 27 221
[  1746.840] reporting 10 7 27 221
[  1748.144] reporting 10 7 27 221
[  1760.716] reporting 10 7 27 221
[  1764.125] reporting 10 7 27 221
[  1764.202] reporting 10 7 27 221
[  1909.029] reporting 10 7 27 221
[  1909.058] reporting 10 7 27 221
[  1983.719] reporting 10 7 27 221
[  2029.361] reporting 10 7 27 221
[  2044.639] reporting 10 7 27 221
[  2066.095] reporting 10 7 27 221
[  2152.717] reporting 10 7 27 221
[  2178.570] reporting 10 7 27 221
[  2178.801] reporting 10 7 27 221
[  2181.453] reporting 10 7 27 221
[  2194.970] reporting 10 7 27 221
[  2210.205] reporting 10 7 27 221
[  2369.934] reporting 10 7 27 221
[  2690.791] reporting 10 7 27 221
[  2756.831] reporting 10 7 27 221
[  2829.350] reporting 10 7 27 221
[  2866.771] reporting 10 7 27 221
[  4028.558] reporting 10 7 27 221
[  4081.704] reporting 10 7 27 221
[  4182.312] reporting 10 7 27 221
[  4182.342] reporting 10 7 27 221
[  4306.142] reporting 10 7 27 221
[  4322.123] reporting 10 7 27 221
[  4484.337] reporting 10 7 27 221
[  4484.573] reporting 10 7 27 221
[  4488.346] reporting 10 7 27 221
[  4521.726] reporting 10 7 27 221
```

$ lspci | grep VGA

```
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Curacao PRO [Radeon R7 370 / R9 270/370 OEM] (rev 81)
```

  	 	 	 	   [TABLE]
 	 	 	[TR]
 		[TD="width: 197, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]Base[/SIZE][/FONT] 						
 		[/TD]
 		[TD="width: 444, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]**Alienware 			X51 Base**[/SIZE][/FONT]
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 197, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]Operating 			System[/SIZE][/FONT]  			
 		[/TD]
 		[TD="width: 444, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]**Ubuntu 			14.04 LTS**[/SIZE][/FONT]
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 197, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]Memory[/SIZE][/FONT] 						
 		[/TD]
 		[TD="width: 444, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]**8GB 			Dual Channel DDR3 at 1600Mhz (2x4GB)**[/SIZE][/FONT]
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 197, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]Keyboard[/SIZE][/FONT] 						
 		[/TD]
 		[TD="width: 444, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]**Alienware 			Standard USB 2.0 Keyboard (English)**[/SIZE][/FONT]
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 197, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]Video 			Card[/SIZE][/FONT]  			
 		[/TD]
 		[TD="width: 444, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]**AMD 			Radeon&#8482; R9 370 with 4GB total GDDR5**[/SIZE][/FONT]
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 197, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]Wireless 			Driver[/SIZE][/FONT]  			
 		[/TD]
 		[TD="width: 444, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]**WLAN 			Card DW1550 Driver**[/SIZE][/FONT]
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 197, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]Hard 			Drive[/SIZE][/FONT]  			
 		[/TD]
 		[TD="width: 444, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]**1TB 			7200 RPM SATA 6Gb/s**[/SIZE][/FONT]
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 197, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]Wireless[/SIZE][/FONT] 						
 		[/TD]
 		[TD="width: 444, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]**Dell 			Wireless 1550 (2x2 11ac combo with Bluetooth)**[/SIZE][/FONT]
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 197, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]Processor[/SIZE][/FONT] 						
 		[/TD]
 		[TD="width: 444, bgcolor: #ffffff"] 			[FONT=Arial][SIZE=1]**4th 			Generation Intel® Core&#8482; i5-4460 processor (6MB Cache, up to 			3.4GHz)**[/SIZE][/FONT]
 		[/TD]
 	[/TR]
 [/TABLE]

---

### Post by howefield on 2016-06-02
Not to answer you question but to help you make more easily read questions, please use code tags when posting output from a log or terminal output.

[http://ubuntuforums.org/showthread.php?t=2054969&p=12231647&viewfull=1#post12231647](http://ubuntuforums.org/showthread.php?t=2054969&p=12231647&viewfull=1#post12231647)

---

### Post by ajgreeny on 2016-06-02
Which version of Ubuntu do you have?

I see in the log that **fglrx**, the now deprecated driver for AMD cards, is mentioned but if you are using 16.04 that may be the reason for your problem.

If I am correct remove the proprietary fglrx driver by running ```
sudo apt-get purge fglrx* 
``` and see if that helps.

A lot more info about your hardware would have helped me and others to assist you better.
See [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475) for how to post a query better.

---

### Post by Ashok_Narendranath on 2016-06-02
I've updated the details, thank you for your help.

---

