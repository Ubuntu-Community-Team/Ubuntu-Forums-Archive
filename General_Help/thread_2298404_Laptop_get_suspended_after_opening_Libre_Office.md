---
title: "Laptop get suspended after opening Libre Office"
date: 2015-10-10
forum: General Help
---

### Post by Audy_Maulizar on 2015-10-10
My laptop goes into login screen everytime I open LibreOffice.


Anybody have an idea about this ? I run Ubuntu 15.04 on Lenovo G40.

---

### Post by bapoumba on 2015-10-11
Does this happen when opening Libreoffice or opening a specific file ?

Please try opening LO from the command line and see if you get any errors :
[https://help.libreoffice.org/Common/Starting_the_Software_With_Parameters](https://help.libreoffice.org/Common/Starting_the_Software_With_Parameters)

---

### Post by Audy_Maulizar on 2015-10-16
It happens everytime I open the application.

Tried your suggestion but the problem persists.

---

### Post by bapoumba on 2015-10-17
Hmm, did you get any error messages ?

---

### Post by Audy_Maulizar on 2015-10-17
Yes, I think it have something to do with xorg.

Here is what I got from the log files.

```
[ 15921.795] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[ 15921.795] X Protocol Version 11, Revision 0
[ 15921.795] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[ 15921.795] Current Operating System: Linux audy-Lenovo-G40-45 3.19.0-30-generic #34-Ubuntu SMP Fri Oct 2 22:08:41 UTC 2015 x86_64
[ 15921.795] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic root=UUID=4dbe0179-f8a9-484c-b32d-059badef95d1 ro quiet splash vt.handoff=7
[ 15921.795] Build Date: 11 September 2015  10:30:58AM
[ 15921.795] xorg-server 2:1.17.1-0ubuntu3.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[ 15921.795] Current version of pixman: 0.32.6
[ 15921.795]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[ 15921.795] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 15921.796] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 17 14:46:37 2015
[ 15921.888] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 15922.145] (==) No Layout section.  Using the first Screen section.
[ 15922.145] (==) No screen section available. Using defaults.
[ 15922.145] (**) |-->Screen "Default Screen Section" (0)
[ 15922.145] (**) |   |-->Monitor "<default monitor>"
[ 15922.146] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[ 15922.146] (==) Automatically adding devices
[ 15922.146] (==) Automatically enabling devices
[ 15922.146] (==) Automatically adding GPU devices
[ 15922.269] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 15922.269]     Entry deleted from font path.
[ 15922.269] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 15922.269]     Entry deleted from font path.
[ 15922.269] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 15922.269]     Entry deleted from font path.
[ 15922.310] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 15922.311]     Entry deleted from font path.
[ 15922.311] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 15922.311]     Entry deleted from font path.
[ 15922.311] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[ 15922.311] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 15922.311] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 15922.311] (II) Loader magic: 0x7efbf7fe3d80
[ 15922.311] (II) Module ABI versions:
[ 15922.311]     X.Org ANSI C Emulation: 0.4
[ 15922.311]     X.Org Video Driver: 19.0
[ 15922.311]     X.Org XInput driver : 21.0
[ 15922.311]     X.Org Server Extension : 9.0
[ 15922.312] (II) xfree86: Adding drm device (/dev/dri/card0)
[ 15922.313] (II) xfree86: Adding drm device (/dev/dri/card1)
[ 15923.204] (--) PCI:*(0:0:1:0) 1002:9851:17aa:381a rev 5, Mem @ 0xe0000000/268435456, 0xf0000000/8388608, 0xf0d00000/262144, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
[ 15923.205] (--) PCI: (0:1:0:0) 1002:666f:17aa:381a rev 0, Mem @ 0xd0000000/268435456, 0xf0c00000/262144, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[ 15923.205] (II) LoadModule: "glx"
[ 15923.265] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 15923.282] (II) Module glx: vendor="X.Org Foundation"
[ 15923.282]     compiled for 1.17.1, module version = 1.0.0
[ 15923.282]     ABI class: X.Org Server Extension, version 9.0
[ 15923.282] (==) AIGLX enabled
[ 15923.282] (==) Matched fglrx as autoconfigured driver 0
[ 15923.282] (==) Matched ati as autoconfigured driver 1
[ 15923.282] (==) Matched fglrx as autoconfigured driver 2
[ 15923.283] (==) Matched ati as autoconfigured driver 3
[ 15923.283] (==) Matched fglrx as autoconfigured driver 4
[ 15923.283] (==) Matched ati as autoconfigured driver 5
[ 15923.283] (==) Matched modesetting as autoconfigured driver 6
[ 15923.283] (==) Matched fbdev as autoconfigured driver 7
[ 15923.283] (==) Matched vesa as autoconfigured driver 8
[ 15923.283] (==) Assigned the driver to the xf86ConfigLayout
[ 15923.283] (II) LoadModule: "fglrx"
[ 15923.283] (WW) Warning, couldn't open module fglrx
[ 15923.283] (II) UnloadModule: "fglrx"
[ 15923.283] (II) Unloading fglrx
[ 15923.283] (EE) Failed to load module "fglrx" (module does not exist, 0)
[ 15923.283] (II) LoadModule: "ati"
[ 15923.283] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 15923.284] (II) Module ati: vendor="X.Org Foundation"
[ 15923.284]     compiled for 1.17.1, module version = 7.5.0
[ 15923.284]     Module class: X.Org Video Driver
[ 15923.284]     ABI class: X.Org Video Driver, version 19.0
[ 15923.284] (II) LoadModule: "radeon"
[ 15923.284] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 15923.297] (II) Module radeon: vendor="X.Org Foundation"
[ 15923.297]     compiled for 1.17.1, module version = 7.5.0
[ 15923.297]     Module class: X.Org Video Driver
[ 15923.297]     ABI class: X.Org Video Driver, version 19.0
[ 15923.297] (II) LoadModule: "modesetting"
[ 15923.298] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 15923.313] (II) Module modesetting: vendor="X.Org Foundation"
[ 15923.313]     compiled for 1.17.1, module version = 1.17.1
[ 15923.313]     Module class: X.Org Video Driver
[ 15923.313]     ABI class: X.Org Video Driver, version 19.0
[ 15923.313] (II) LoadModule: "fbdev"
[ 15923.313] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 15923.321] (II) Module fbdev: vendor="X.Org Foundation"
[ 15923.321]     compiled for 1.17.1, module version = 0.4.4
[ 15923.321]     Module class: X.Org Video Driver
[ 15923.321]     ABI class: X.Org Video Driver, version 19.0
[ 15923.321] (II) LoadModule: "vesa"
[ 15923.321] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 15923.327] (II) Module vesa: vendor="X.Org Foundation"
[ 15923.327]     compiled for 1.17.1, module version = 2.3.3
[ 15923.327]     Module class: X.Org Video Driver
[ 15923.327]     ABI class: X.Org Video Driver, version 19.0
[ 15923.327] (==) Matched fglrx as autoconfigured driver 0
[ 15923.327] (==) Matched ati as autoconfigured driver 1
[ 15923.327] (==) Matched fglrx as autoconfigured driver 2
[ 15923.327] (==) Matched ati as autoconfigured driver 3
[ 15923.327] (==) Matched fglrx as autoconfigured driver 4
[ 15923.327] (==) Matched ati as autoconfigured driver 5
[ 15923.327] (==) Matched modesetting as autoconfigured driver 6
[ 15923.327] (==) Matched fbdev as autoconfigured driver 7
[ 15923.327] (==) Matched vesa as autoconfigured driver 8
[ 15923.327] (==) Assigned the driver to the xf86ConfigLayout
[ 15923.327] (II) LoadModule: "fglrx"
[ 15923.328] (WW) Warning, couldn't open module fglrx
[ 15923.328] (II) UnloadModule: "fglrx"
[ 15923.328] (II) Unloading fglrx
[ 15923.328] (EE) Failed to load module "fglrx" (module does not exist, 0)
[ 15923.328] (II) LoadModule: "ati"
[ 15923.328] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 15923.328] (II) Module ati: vendor="X.Org Foundation"
[ 15923.328]     compiled for 1.17.1, module version = 7.5.0
[ 15923.328]     Module class: X.Org Video Driver
[ 15923.328]     ABI class: X.Org Video Driver, version 19.0
[ 15923.328] (II) LoadModule: "modesetting"
[ 15923.328] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 15923.328] (II) Module modesetting: vendor="X.Org Foundation"
[ 15923.328]     compiled for 1.17.1, module version = 1.17.1
[ 15923.328]     Module class: X.Org Video Driver
[ 15923.328]     ABI class: X.Org Video Driver, version 19.0
[ 15923.328] (II) UnloadModule: "modesetting"
[ 15923.328] (II) Unloading modesetting
[ 15923.328] (II) Failed to load module "modesetting" (already loaded, 0)
[ 15923.328] (II) LoadModule: "fbdev"
[ 15923.329] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 15923.329] (II) Module fbdev: vendor="X.Org Foundation"
[ 15923.329]     compiled for 1.17.1, module version = 0.4.4
[ 15923.329]     Module class: X.Org Video Driver
[ 15923.329]     ABI class: X.Org Video Driver, version 19.0
[ 15923.329] (II) UnloadModule: "fbdev"
[ 15923.329] (II) Unloading fbdev
[ 15923.329] (II) Failed to load module "fbdev" (already loaded, 0)
[ 15923.329] (II) LoadModule: "vesa"
[ 15923.329] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 15923.329] (II) Module vesa: vendor="X.Org Foundation"
[ 15923.329]     compiled for 1.17.1, module version = 2.3.3
[ 15923.329]     Module class: X.Org Video Driver
[ 15923.329]     ABI class: X.Org Video Driver, version 19.0
[ 15923.329] (II) UnloadModule: "vesa"
[ 15923.329] (II) Unloading vesa
[ 15923.329] (II) Failed to load module "vesa" (already loaded, 0)
[ 15923.329] (II) RADEON: Driver for ATI Radeon chipsets:
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
[ 15923.342] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[ 15923.342] (II) FBDEV: driver for framebuffer: fbdev
[ 15923.342] (II) VESA: driver for VESA chipsets: vesa
[ 15923.342] (++) using VT number 7

[ 15923.343] (II) [KMS] Kernel modesetting enabled.
[ 15923.343] (II) [KMS] Kernel modesetting enabled.
[ 15923.343] (WW) Falling back to old probe method for modesetting
[ 15923.343] (WW) Falling back to old probe method for fbdev
[ 15923.343] (II) Loading sub module "fbdevhw"
[ 15923.343] (II) LoadModule: "fbdevhw"
[ 15923.343] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 15923.355] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 15923.355]     compiled for 1.17.1, module version = 0.0.2
[ 15923.355]     ABI class: X.Org Video Driver, version 19.0
[ 15923.355] (WW) Falling back to old probe method for vesa
[ 15923.355] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[ 15923.355] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[ 15923.355] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[ 15923.355] (==) RADEON(0): Default visual is TrueColor
[ 15923.355] (==) RADEON(0): RGB weight 888
[ 15923.355] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[ 15923.356] (--) RADEON(0): Chipset: "MULLINS" (ChipID = 0x9851)
[ 15923.356] (II) Loading sub module "dri2"
[ 15923.356] (II) LoadModule: "dri2"
[ 15923.356] (II) Module "dri2" already built-in
[ 15923.356] (II) Loading sub module "glamoregl"
[ 15923.356] (II) LoadModule: "glamoregl"
[ 15923.356] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[ 15923.384] (II) Module glamoregl: vendor="X.Org Foundation"
[ 15923.384]     compiled for 1.17.1, module version = 1.0.0
[ 15923.385]     ABI class: X.Org ANSI C Emulation, version 0.4
[ 15923.385] (II) glamor: OpenGL accelerated X.org driver based.
[ 15923.435] (II) glamor: EGL version 1.4 (DRI2):
[ 15923.438] (II) RADEON(0): glamor detected, initialising EGL layer.
[ 15923.438] (II) RADEON(0): KMS Color Tiling: enabled
[ 15923.438] (II) RADEON(0): KMS Color Tiling 2D: enabled
[ 15923.438] (II) RADEON(0): KMS Pageflipping: enabled
[ 15923.439] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[ 15923.475] (II) RADEON(0): Output eDP has no monitor section
[ 15923.477] (II) RADEON(0): Output HDMI-0 has no monitor section
[ 15923.500] (II) RADEON(0): Output VGA-0 has no monitor section
[ 15923.536] (II) RADEON(0): EDID for output eDP
[ 15923.536] (II) RADEON(0): Manufacturer: AUO  Model: 323c  Serial#: 0
[ 15923.536] (II) RADEON(0): Year: 2013  Week: 0
[ 15923.536] (II) RADEON(0): EDID Version: 1.4
[ 15923.536] (II) RADEON(0): Digital Display Input
[ 15923.536] (II) RADEON(0): 6 bits per channel
[ 15923.536] (II) RADEON(0): Digital interface is DisplayPort
[ 15923.536] (II) RADEON(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[ 15923.536] (II) RADEON(0): Gamma: 2.20
[ 15923.536] (II) RADEON(0): No DPMS capabilities specified
[ 15923.536] (II) RADEON(0): Supported color encodings: RGB 4:4:4 
[ 15923.536] (II) RADEON(0): First detailed timing is preferred mode
[ 15923.536] (II) RADEON(0): Preferred mode is native pixel format and refresh rate
[ 15923.536] (II) RADEON(0): redX: 0.588 redY: 0.346   greenX: 0.327 greenY: 0.542
[ 15923.536] (II) RADEON(0): blueX: 0.151 blueY: 0.143   whiteX: 0.313 whiteY: 0.329
[ 15923.537] (II) RADEON(0): Manufacturer's mask: 0
[ 15923.537] (II) RADEON(0): Supported detailed timing:
[ 15923.537] (II) RADEON(0): clock: 71.0 MHz   Image Size:  309 x 173 mm
[ 15923.537] (II) RADEON(0): h_active: 1366  h_sync: 1404  h_sync_end 1426 h_blank_end 1482 h_border: 0
[ 15923.537] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 798 v_border: 0
[ 15923.537] (II) RADEON(0): Unknown vendor-specific block f
[ 15923.537] (II) RADEON(0):  AUO
[ 15923.537] (II) RADEON(0):  B140XTN03.2
[ 15923.537] (II) RADEON(0): EDID (in hex):
[ 15923.537] (II) RADEON(0):     00ffffffffffff0006af3c3200000000
[ 15923.537] (II) RADEON(0):     00170104951f117802afe59658538a26
[ 15923.537] (II) RADEON(0):     24505400000001010101010101010101
[ 15923.537] (II) RADEON(0):     010101010101bc1b567450001e302616
[ 15923.537] (II) RADEON(0):     360035ad100000180000000f00000000
[ 15923.537] (II) RADEON(0):     00000000000000000020000000fe0041
[ 15923.537] (II) RADEON(0):     554f0a202020202020202020000000fe
[ 15923.537] (II) RADEON(0):     004231343058544e30332e32200a0078
[ 15923.537] (II) RADEON(0): Printing probed modes for output eDP
[ 15923.537] (II) RADEON(0): Modeline "1366x768"x60.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15923.537] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[ 15923.537] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[ 15923.537] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[ 15923.537] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[ 15923.537] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[ 15923.537] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[ 15923.537] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[ 15923.539] (II) RADEON(0): EDID for output HDMI-0
[ 15923.564] (II) RADEON(0): EDID for output VGA-0
[ 15923.564] (II) RADEON(0): Output eDP connected
[ 15923.564] (II) RADEON(0): Output HDMI-0 disconnected
[ 15923.564] (II) RADEON(0): Output VGA-0 disconnected
[ 15923.564] (II) RADEON(0): Using exact sizes for initial modes
[ 15923.564] (II) RADEON(0): Output eDP using initial mode 1366x768
[ 15923.564] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 15923.564] (II) RADEON(0): mem size init: gart size :3fb69000 vram size: s:20000000 visible:1f250000
[ 15923.564] (==) RADEON(0): DPI set to (96, 96)
[ 15923.564] (II) Loading sub module "fb"
[ 15923.564] (II) LoadModule: "fb"
[ 15923.564] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 15923.572] (II) Module fb: vendor="X.Org Foundation"
[ 15923.572]     compiled for 1.17.1, module version = 1.0.0
[ 15923.572]     ABI class: X.Org ANSI C Emulation, version 0.4
[ 15923.572] (II) Loading sub module "ramdac"
[ 15923.572] (II) LoadModule: "ramdac"
[ 15923.572] (II) Module "ramdac" already built-in
[ 15923.572] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[ 15923.572] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[ 15923.572] (==) RADEON(G0): Default visual is TrueColor
[ 15923.572] (==) RADEON(G0): RGB weight 888
[ 15923.572] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[ 15923.572] (--) RADEON(G0): Chipset: "HAINAN" (ChipID = 0x666f)
[ 15923.572] (II) Loading sub module "dri2"
[ 15923.572] (II) LoadModule: "dri2"
[ 15923.572] (II) Module "dri2" already built-in
[ 15923.572] (II) Loading sub module "glamoregl"
[ 15923.572] (II) LoadModule: "glamoregl"
[ 15923.573] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[ 15923.573] (II) Module glamoregl: vendor="X.Org Foundation"
[ 15923.573]     compiled for 1.17.1, module version = 1.0.0
[ 15923.573]     ABI class: X.Org ANSI C Emulation, version 0.4
[ 15923.573] (II) glamor: OpenGL accelerated X.org driver based.
[ 15923.576] (II) glamor: EGL version 1.4 (DRI2):
[ 15923.578] (II) RADEON(G0): glamor detected, initialising EGL layer.
[ 15923.578] (II) RADEON(G0): KMS Color Tiling: enabled
[ 15923.578] (II) RADEON(G0): KMS Color Tiling 2D: enabled
[ 15923.578] (II) RADEON(G0): KMS Pageflipping: enabled
[ 15923.578] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[ 15923.578] (II) RADEON(G0): mem size init: gart size :3fbcf000 vram size: s:80000000 visible:7fabe000
[ 15923.578] (==) RADEON(G0): DPI set to (96, 96)
[ 15923.578] (II) Loading sub module "fb"
[ 15923.578] (II) LoadModule: "fb"
[ 15923.578] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 15923.579] (II) Module fb: vendor="X.Org Foundation"
[ 15923.579]     compiled for 1.17.1, module version = 1.0.0
[ 15923.579]     ABI class: X.Org ANSI C Emulation, version 0.4
[ 15923.579] (==) RADEON(G0): Using gamma correction (1.0, 1.0, 1.0)
[ 15923.579] (II) Loading sub module "ramdac"
[ 15923.579] (II) LoadModule: "ramdac"
[ 15923.579] (II) Module "ramdac" already built-in
[ 15923.579] (II) UnloadModule: "modesetting"
[ 15923.579] (II) Unloading modesetting
[ 15923.579] (II) UnloadModule: "fbdev"
[ 15923.579] (II) Unloading fbdev
[ 15923.579] (II) UnloadSubModule: "fbdevhw"
[ 15923.579] (II) Unloading fbdevhw
[ 15923.579] (II) UnloadModule: "vesa"
[ 15923.579] (II) Unloading vesa
[ 15923.579] (--) Depth 24 pixmap format is 32 bpp
[ 15923.579] (II) RADEON(G0): [DRI2] Setup complete
[ 15923.579] (II) RADEON(G0): [DRI2]   DRI driver: radeonsi
[ 15923.579] (II) RADEON(G0): [DRI2]   VDPAU driver: radeonsi
[ 15923.580] (II) RADEON(G0): Front buffer size: 3072K
[ 15923.580] (II) RADEON(G0): VRAM usage limit set to 1879826K
[ 15923.580] (==) RADEON(G0): Backing store enabled
[ 15923.580] (II) RADEON(G0): Direct rendering enabled
[ 15923.688] (II) RADEON(G0): Use GLAMOR acceleration.
[ 15923.688] (II) RADEON(G0): Acceleration enabled
[ 15923.688] (==) RADEON(G0): DPMS enabled
[ 15923.688] (==) RADEON(G0): Silken mouse enabled
[ 15923.688] (II) RADEON(G0): Set up textured video (glamor)
[ 15923.688] (II) RADEON(G0): [XvMC] Associated with GLAMOR Textured Video.
[ 15923.688] (EE) RADEON(G0): [XvMC] Failed to initialize extension.
[ 15923.688] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 15923.688] (II) RADEON(0): [DRI2] Setup complete
[ 15923.688] (II) RADEON(0): [DRI2]   DRI driver: radeonsi
[ 15923.688] (II) RADEON(0): [DRI2]   VDPAU driver: radeonsi
[ 15923.688] (II) RADEON(0): Front buffer size: 4224K
[ 15923.688] (II) RADEON(0): VRAM usage limit set to 455414K
[ 15923.689] (==) RADEON(0): Backing store enabled
[ 15923.689] (II) RADEON(0): Direct rendering enabled
[ 15923.788] (II) RADEON(0): Use GLAMOR acceleration.
[ 15923.788] (II) RADEON(0): Acceleration enabled
[ 15923.788] (==) RADEON(0): DPMS enabled
[ 15923.788] (==) RADEON(0): Silken mouse enabled
[ 15923.788] (II) RADEON(0): Set up textured video (glamor)
[ 15923.788] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[ 15923.788] (II) RADEON(0): [XvMC] Extension initialized.
[ 15923.788] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 15923.789] (--) RandR disabled
[ 15923.798] (II) SELinux: Disabled on system
[ 15923.801] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 15923.801] (II) AIGLX: enabled GLX_ARB_create_context
[ 15923.801] (II) AIGLX: enabled GLX_ARB_create_context_profile
[ 15923.801] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[ 15923.801] (II) AIGLX: enabled GLX_INTEL_swap_event
[ 15923.801] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[ 15923.801] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[ 15923.801] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[ 15923.801] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[ 15923.802] (II) AIGLX: Loaded and initialized radeonsi
[ 15923.802] (II) GLX: Initialized DRI2 GL provider for screen 0
[ 15923.848] (II) RADEON(0): Setting screen physical size to 361 x 203
[ 15923.929] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 15923.936] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[ 15923.936] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 15923.936] (II) LoadModule: "evdev"
[ 15923.936] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15923.937] (II) Module evdev: vendor="X.Org Foundation"
[ 15923.937]     compiled for 1.16.0, module version = 2.9.0
[ 15923.937]     Module class: X.Org XInput Driver
[ 15923.937]     ABI class: X.Org XInput driver, version 21.0
[ 15923.937] (II) Using input driver 'evdev' for 'Power Button'
[ 15923.937] (**) Power Button: always reports core events
[ 15923.937] (**) evdev: Power Button: Device: "/dev/input/event2"
[ 15923.937] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 15923.937] (--) evdev: Power Button: Found keys
[ 15923.937] (II) evdev: Power Button: Configuring as keyboard
[ 15923.937] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[ 15923.937] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 15923.937] (**) Option "xkb_rules" "evdev"
[ 15923.937] (**) Option "xkb_model" "pc105"
[ 15923.937] (**) Option "xkb_layout" "us"
[ 15923.938] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[ 15923.938] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 15923.938] (II) Using input driver 'evdev' for 'Video Bus'
[ 15923.938] (**) Video Bus: always reports core events
[ 15923.938] (**) evdev: Video Bus: Device: "/dev/input/event5"
[ 15923.938] (--) evdev: Video Bus: Vendor 0 Product 0x6
[ 15923.938] (--) evdev: Video Bus: Found keys
[ 15923.938] (II) evdev: Video Bus: Configuring as keyboard
[ 15923.938] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6/event5"
[ 15923.938] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[ 15923.938] (**) Option "xkb_rules" "evdev"
[ 15923.938] (**) Option "xkb_model" "pc105"
[ 15923.939] (**) Option "xkb_layout" "us"
[ 15923.939] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[ 15923.939] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 15923.939] (II) Using input driver 'evdev' for 'Video Bus'
[ 15923.940] (**) Video Bus: always reports core events
[ 15923.940] (**) evdev: Video Bus: Device: "/dev/input/event6"
[ 15923.940] (--) evdev: Video Bus: Vendor 0 Product 0x6
[ 15923.940] (--) evdev: Video Bus: Found keys
[ 15923.940] (II) evdev: Video Bus: Configuring as keyboard
[ 15923.940] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input7/event6"
[ 15923.940] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[ 15923.940] (**) Option "xkb_rules" "evdev"
[ 15923.940] (**) Option "xkb_model" "pc105"
[ 15923.940] (**) Option "xkb_layout" "us"
[ 15923.941] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 15923.941] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 15923.941] (II) Using input driver 'evdev' for 'Power Button'
[ 15923.941] (**) Power Button: always reports core events
[ 15923.941] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 15923.941] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 15923.941] (--) evdev: Power Button: Found keys
[ 15923.941] (II) evdev: Power Button: Configuring as keyboard
[ 15923.941] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[ 15923.941] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[ 15923.941] (**) Option "xkb_rules" "evdev"
[ 15923.941] (**) Option "xkb_model" "pc105"
[ 15923.941] (**) Option "xkb_layout" "us"
[ 15923.942] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[ 15923.942] (II) No input driver specified, ignoring this device.
[ 15923.942] (II) This device may have been added with another device file.
[ 15923.943] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event8)
[ 15923.943] (II) No input driver specified, ignoring this device.
[ 15923.943] (II) This device may have been added with another device file.
[ 15923.944] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event11)
[ 15923.944] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[ 15923.944] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[ 15923.944] (**) Lenovo EasyCamera: always reports core events
[ 15923.944] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event11"
[ 15923.944] (--) evdev: Lenovo EasyCamera: Vendor 0x13d3 Product 0x5727
[ 15923.944] (--) evdev: Lenovo EasyCamera: Found keys
[ 15923.944] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[ 15923.944] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb4/4-1/4-1.2/4-1.2:1.0/input/input12/event11"
[ 15923.944] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 10)
[ 15923.944] (**) Option "xkb_rules" "evdev"
[ 15923.944] (**) Option "xkb_model" "pc105"
[ 15923.944] (**) Option "xkb_layout" "us"
[ 15923.945] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event9)
[ 15923.945] (II) No input driver specified, ignoring this device.
[ 15923.945] (II) This device may have been added with another device file.
[ 15923.945] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event10)
[ 15923.945] (II) No input driver specified, ignoring this device.
[ 15923.945] (II) This device may have been added with another device file.
[ 15923.946] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event7)
[ 15923.946] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[ 15923.946] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[ 15923.946] (**) Ideapad extra buttons: always reports core events
[ 15923.946] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event7"
[ 15923.946] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[ 15923.946] (--) evdev: Ideapad extra buttons: Found keys
[ 15923.946] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[ 15923.946] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.3/PNP0C09:00/VPC2004:00/input/input8/event7"
[ 15923.946] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 11)
[ 15923.946] (**) Option "xkb_rules" "evdev"
[ 15923.946] (**) Option "xkb_model" "pc105"
[ 15923.946] (**) Option "xkb_layout" "us"
[ 15923.947] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[ 15923.947] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 15923.947] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 15923.947] (**) AT Translated Set 2 keyboard: always reports core events
[ 15923.947] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[ 15923.947] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[ 15923.947] (--) evdev: AT Translated Set 2 keyboard: Found keys
[ 15923.947] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[ 15923.947] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[ 15923.947] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[ 15923.947] (**) Option "xkb_rules" "evdev"
[ 15923.947] (**) Option "xkb_model" "pc105"
[ 15923.948] (**) Option "xkb_layout" "us"
[ 15923.948] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[ 15923.948] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[ 15923.948] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[ 15923.948] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[ 15923.948] (II) LoadModule: "synaptics"
[ 15923.949] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 15923.949] (II) Module synaptics: vendor="X.Org Foundation"
[ 15923.949]     compiled for 1.16.0, module version = 1.8.99
[ 15923.949]     Module class: X.Org XInput Driver
[ 15923.949]     ABI class: X.Org XInput driver, version 21.0
[ 15923.949] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[ 15923.949] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 15923.949] (**) Option "Device" "/dev/input/event4"
[ 15923.972] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1240 - 5702 (res 51)
[ 15923.972] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 964 - 4886 (res 98)
[ 15923.972] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[ 15923.972] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[ 15923.972] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[ 15923.972] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[ 15923.972] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 15923.972] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 15923.996] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[ 15923.996] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[ 15923.996] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[ 15923.996] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[ 15923.996] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.034
[ 15923.996] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[ 15923.996] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[ 15923.996] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[ 15923.996] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[ 15923.996] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 15923.997] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[ 15923.997] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[ 15924.656] reporting 2 3 8 60
[ 15925.996] reporting 2 3 8 60
[ 15926.005] reporting 2 3 8 60
[ 15926.095] reporting 2 3 8 60
[ 15926.568] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15926.568] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15926.568] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15926.632] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15926.633] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15926.633] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15926.660] reporting 2 3 8 60
[ 15926.949] reporting 2 3 8 60
[ 15926.986] reporting 2 3 8 60
[ 15926.988] reporting 2 3 8 60
[ 15927.085] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15927.085] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15927.085] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15927.148] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15927.148] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15927.148] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15927.176] reporting 2 3 8 60
[ 15927.431] reporting 2 3 8 60
[ 15927.475] reporting 2 3 8 60
[ 15934.001] reporting 2 3 8 60
[ 15934.184] reporting 2 3 8 60
[ 15934.215] reporting 2 3 8 60
[ 15934.245] reporting 2 3 8 60
[ 15934.305] reporting 2 3 8 60
[ 15934.553] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15934.553] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15934.553] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15934.616] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15934.617] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15934.617] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15934.644] reporting 2 3 8 60
[ 15934.673] reporting 2 3 8 60
[ 15934.686] reporting 2 3 8 60
[ 15934.687] reporting 2 3 8 60
[ 15934.938] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 15934.985] reporting 2 3 8 60
[ 15935.044] reporting 2 3 8 60
[ 15935.313] reporting 2 3 8 60
[ 15935.476] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15935.476] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15935.476] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15935.541] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15935.541] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15935.541] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15935.568] reporting 2 3 8 60
[ 15935.943] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15935.943] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15935.943] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15935.976] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 15936.001] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 15936.291] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15936.292] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15936.292] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15936.552] reporting 2 3 8 60
[ 15936.597] reporting 2 3 8 60
[ 15936.618] reporting 2 3 8 60
[ 15938.319] reporting 2 3 8 60
[ 15938.551] reporting 2 3 8 60
[ 15938.714] reporting 2 3 8 60
[ 15940.936] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[ 15951.574] reporting 2 3 8 60
[ 15951.616] reporting 2 3 8 60
[ 15951.893] reporting 2 3 8 60
[ 15953.321] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15953.321] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15953.321] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15953.385] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15953.385] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15953.385] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15953.412] reporting 2 3 8 60
[ 15953.449] (II) RADEON(0): EDID vendor "AUO", prod id 12860
[ 15953.450] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15953.450] (II) RADEON(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1482  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[ 15953.530] reporting 2 3 8 60
[ 15996.538] reporting 2 3 8 60
[ 16022.318] reporting 2 3 8 60
[ 16047.908] reporting 2 3 8 60
[ 16156.377] reporting 2 3 8 60

```

---

### Post by ajgreeny on 2015-10-17
But what about error messages in terminal after opening LO with command such as **libreoffice --writer**?

The only error I can see in your xorg log is about failing to load fglrx but that should not normally force a suspension of the OS.  What graphic card do you have?

---

