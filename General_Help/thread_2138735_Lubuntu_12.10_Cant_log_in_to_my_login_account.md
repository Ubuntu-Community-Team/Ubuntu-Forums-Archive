---
title: "Lubuntu 12.10 Cant log in to my login account"
date: 2013-04-25
forum: General Help
---

### Post by Locus Kiesselbachi on 2013-04-25
There is actually two problems:
1.Sometimes desktop GUI does not load. Mostly after fresh computer start, not restart.
2.This time I tried to mess around to catch the bug, but after restart it was fresh/new desktop with no user added items.
*One problem made another: 1->2!


This is what I have done:
Problem1
I start computer and it loads black screen with mouse pointer (it can be moved). I switch with "Ctrl+Alt+F6" to lower tty.
Now I can enter my root login and password.
Command line opens...
I type "startx"

now it says...(something like that)
bla-bla ...check "var/log/Xorg.1.log" ...bla bla
Server terminated with error(1) closing log file
Xinit:giving up
Xinit:unable to connect to x server: Connection
Xinit server error.refused.

the "var/log/Xorg.1.log":)
```
[   149.412] X.Org X Server 1.13.0
Release Date: 2012-09-05
[   149.416] X Protocol Version 11, Revision 0
[   149.417] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[   149.419] Current Operating System: Linux blackice 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
[   149.419] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-17-generic root=UUID=9e3b5833-7c11-4181-bd58-e8b1a6fbdb5b ro quiet splash vt.handoff=7
[   149.421] Build Date: 27 November 2012  07:44:35AM
[   149.421] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[   149.422] Current version of pixman: 0.26.0
[   149.423]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   149.423] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   149.426] (==) Log file: "/var/log/Xorg.1.log", Time: Thu Apr 25 09:28:21 2013
[   149.426] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   149.426] (==) No Layout section.  Using the first Screen section.
[   149.426] (==) No screen section available. Using defaults.
[   149.426] (**) |-->Screen "Default Screen Section" (0)
[   149.426] (**) |   |-->Monitor "<default monitor>"
[   149.427] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   149.427] (==) Automatically adding devices
[   149.427] (==) Automatically enabling devices
[   149.427] (==) Automatically adding GPU devices
[   149.427] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   149.427]     Entry deleted from font path.
[   149.427] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   149.427]     Entry deleted from font path.
[   149.427] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   149.427]     Entry deleted from font path.
[   149.427] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   149.427]     Entry deleted from font path.
[   149.427] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   149.427]     Entry deleted from font path.
[   149.427] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   149.427]     Entry deleted from font path.
[   149.427] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   149.427] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   149.427] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   149.427] (II) Loader magic: 0x7ff9bcc7bc40
[   149.427] (II) Module ABI versions:
[   149.427]     X.Org ANSI C Emulation: 0.4
[   149.427]     X.Org Video Driver: 13.0
[   149.427]     X.Org XInput driver : 18.0
[   149.427]     X.Org Server Extension : 7.0
[   149.427] (II) config/udev: Adding drm device (/dev/dri/card0)
[   149.427] setversion 1.4 failed
[   149.428] (--) PCI:*(0:7:0:0) 1002:683d:1043:0429 rev 0, Mem @ 0xe0000000/268435456, 0xf7a00000/262144, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
[   149.428] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[   149.429] Initializing built-in extension Generic Event Extension
[   149.429] Initializing built-in extension SHAPE
[   149.430] Initializing built-in extension MIT-SHM
[   149.431] Initializing built-in extension XInputExtension
[   149.431] Initializing built-in extension XTEST
[   149.432] Initializing built-in extension BIG-REQUESTS
[   149.433] Initializing built-in extension SYNC
[   149.433] Initializing built-in extension XKEYBOARD
[   149.434] Initializing built-in extension XC-MISC
[   149.434] Initializing built-in extension SECURITY
[   149.435] Initializing built-in extension XINERAMA
[   149.436] Initializing built-in extension XFIXES
[   149.436] Initializing built-in extension RENDER
[   149.437] Initializing built-in extension RANDR
[   149.437] Initializing built-in extension COMPOSITE
[   149.438] Initializing built-in extension DAMAGE
[   149.439] Initializing built-in extension MIT-SCREEN-SAVER
[   149.439] Initializing built-in extension DOUBLE-BUFFER
[   149.440] Initializing built-in extension RECORD
[   149.441] Initializing built-in extension DPMS
[   149.441] Initializing built-in extension X-Resource
[   149.442] Initializing built-in extension XVideo
[   149.442] Initializing built-in extension XVideo-MotionCompensation
[   149.443] Initializing built-in extension XFree86-VidModeExtension
[   149.444] Initializing built-in extension XFree86-DGA
[   149.444] Initializing built-in extension XFree86-DRI
[   149.445] Initializing built-in extension DRI2
[   149.445] (II) LoadModule: "glx"
[   149.445] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   149.445] (II) Module glx: vendor="X.Org Foundation"
[   149.445]     compiled for 1.13.0, module version = 1.0.0
[   149.445]     ABI class: X.Org Server Extension, version 7.0
[   149.445] (==) AIGLX enabled
[   149.446] Loading extension GLX
[   149.446] (==) Matched fglrx as autoconfigured driver 0
[   149.446] (==) Matched ati as autoconfigured driver 1
[   149.446] (==) Matched vesa as autoconfigured driver 2
[   149.446] (==) Matched modesetting as autoconfigured driver 3
[   149.446] (==) Matched fbdev as autoconfigured driver 4
[   149.446] (==) Assigned the driver to the xf86ConfigLayout
[   149.446] (II) LoadModule: "fglrx"
[   149.446] (WW) Warning, couldn't open module fglrx
[   149.446] (II) UnloadModule: "fglrx"
[   149.446] (II) Unloading fglrx
[   149.446] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   149.446] (II) LoadModule: "ati"
[   149.446] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   149.446] (II) Module ati: vendor="X.Org Foundation"
[   149.446]     compiled for 1.13.0, module version = 6.99.99
[   149.446]     Module class: X.Org Video Driver
[   149.446]     ABI class: X.Org Video Driver, version 13.0
[   149.446] (II) LoadModule: "radeon"
[   149.446] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   149.446] (II) Module radeon: vendor="X.Org Foundation"
[   149.446]     compiled for 1.13.0, module version = 6.99.99
[   149.446]     Module class: X.Org Video Driver
[   149.446]     ABI class: X.Org Video Driver, version 13.0
[   149.446] (II) LoadModule: "vesa"
[   149.446] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   149.446] (II) Module vesa: vendor="X.Org Foundation"
[   149.446]     compiled for 1.12.99.902, module version = 2.3.2
[   149.446]     Module class: X.Org Video Driver
[   149.446]     ABI class: X.Org Video Driver, version 13.0
[   149.446] (II) LoadModule: "modesetting"
[   149.446] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   149.446] (II) Module modesetting: vendor="X.Org Foundation"
[   149.446]     compiled for 1.13.0, module version = 0.5.0
[   149.446]     Module class: X.Org Video Driver
[   149.446]     ABI class: X.Org Video Driver, version 13.0
[   149.446] (II) LoadModule: "fbdev"
[   149.446] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   149.446] (II) Module fbdev: vendor="X.Org Foundation"
[   149.446]     compiled for 1.12.99.902, module version = 0.4.3
[   149.447]     Module class: X.Org Video Driver
[   149.447]     ABI class: X.Org Video Driver, version 13.0
[   149.447] (==) Matched fglrx as autoconfigured driver 0
[   149.447] (==) Matched ati as autoconfigured driver 1
[   149.447] (==) Matched vesa as autoconfigured driver 2
[   149.447] (==) Matched modesetting as autoconfigured driver 3
[   149.447] (==) Matched fbdev as autoconfigured driver 4
[   149.447] (==) Assigned the driver to the xf86ConfigLayout
[   149.447] (II) LoadModule: "fglrx"
[   149.447] (WW) Warning, couldn't open module fglrx
[   149.447] (II) UnloadModule: "fglrx"
[   149.447] (II) Unloading fglrx
[   149.447] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   149.447] (II) LoadModule: "ati"
[   149.447] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   149.447] (II) Module ati: vendor="X.Org Foundation"
[   149.447]     compiled for 1.13.0, module version = 6.99.99
[   149.447]     Module class: X.Org Video Driver
[   149.447]     ABI class: X.Org Video Driver, version 13.0
[   149.447] (II) LoadModule: "vesa"
[   149.447] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   149.447] (II) Module vesa: vendor="X.Org Foundation"
[   149.447]     compiled for 1.12.99.902, module version = 2.3.2
[   149.447]     Module class: X.Org Video Driver
[   149.447]     ABI class: X.Org Video Driver, version 13.0
[   149.447] (II) UnloadModule: "vesa"
[   149.447] (II) Unloading vesa
[   149.447] (II) Failed to load module "vesa" (already loaded, 0)
[   149.447] (II) LoadModule: "modesetting"
[   149.447] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   149.447] (II) Module modesetting: vendor="X.Org Foundation"
[   149.447]     compiled for 1.13.0, module version = 0.5.0
[   149.447]     Module class: X.Org Video Driver
[   149.447]     ABI class: X.Org Video Driver, version 13.0
[   149.447] (II) UnloadModule: "modesetting"
[   149.447] (II) Unloading modesetting
[   149.447] (II) Failed to load module "modesetting" (already loaded, 0)
[   149.447] (II) LoadModule: "fbdev"
[   149.447] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   149.447] (II) Module fbdev: vendor="X.Org Foundation"
[   149.447]     compiled for 1.12.99.902, module version = 0.4.3
[   149.447]     Module class: X.Org Video Driver
[   149.447]     ABI class: X.Org Video Driver, version 13.0
[   149.447] (II) UnloadModule: "fbdev"
[   149.447] (II) Unloading fbdev
[   149.447] (II) Failed to load module "fbdev" (already loaded, 0)
[   149.447] (II) RADEON: Driver for ATI Radeon chipsets:
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
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
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
    ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE
[   149.449] (II) VESA: driver for VESA chipsets: vesa
[   149.449] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   149.449] (II) FBDEV: driver for framebuffer: fbdev
[   149.449] (--) using VT number 8


[   149.452] (II) [KMS] Kernel modesetting enabled.
[   149.452] (WW) Falling back to old probe method for vesa
[   149.452] (WW) Falling back to old probe method for modesetting
[   149.452] (WW) Falling back to old probe method for fbdev
[   149.452] (II) Loading sub module "fbdevhw"
[   149.452] (II) LoadModule: "fbdevhw"
[   149.452] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   149.452] (II) Module fbdevhw: vendor="X.Org Foundation"
[   149.452]     compiled for 1.13.0, module version = 0.0.2
[   149.452]     ABI class: X.Org Video Driver, version 13.0
[   149.452] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   149.452] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[   149.452] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   149.452] (==) RADEON(0): Default visual is TrueColor
[   149.452] (==) RADEON(0): RGB weight 888
[   149.452] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[   149.452] (--) RADEON(0): Chipset: "VERDE" (ChipID = 0x683d)
[   149.452] (EE) RADEON(0): [drm] failed to set drm interface version.
[   149.452] (EE) RADEON(0): Kernel modesetting setup failed
[   149.452] (II) UnloadModule: "radeon"
[   149.452] (EE) Screen(s) found, but none have a usable configuration.
[   149.452] 
Fatal server error:
[   149.452] no screens found
[   149.452] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   149.452] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   149.452] (EE) 
[   149.465] Server terminated with error (1). Closing log file.



```

Problem NR 2:
Automatic log in does not work! It worked before. I installed Lubuntu as "Log in automaticaly", it is one of the options when you start installing this OS.

After that, I did in "problem1"
entered to command line
"reboot"
have to be root
"sudo reboot"
NOW it reboots to this place where it asks if I want to log in as quest or root.
It lets to log in as quest - but thats not my desktop - no icons, no startbar items.
It DOES NOT log in as root - flickers this login/password window and nothing happens (not that screen flicker you get with faulty monitor or graphics card) and I cannot get to login as root.


PC have no propriatary videodrivers installed. Lubuntu natively uses graphicscard.
**PC specs:**
HD7770-DC-1GD5-V2
Two hard-drives - one has Lubuntu and other win7. Lubuntu HD is boot priority set in BIOS.
3370K
Z77X-UD3H

---

### Post by r.stiltskin on 2013-04-25
I don't see your graphics card listed among the ones supported by the open source radeon driver.  Here's a "How-To" for installing the latest AMD proprietary driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by Locus Kiesselbachi on 2013-04-25
> **r.stiltskin said:**
> I don't see your graphics card listed among the ones supported by the open source radeon driver.  Here's a "How-To" for installing the latest AMD proprietary driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
ok, but why I cant log in to my account, but can in to quest account.
When I log in to my account it flashes black screen with white text in upper left corner - it flashes too fast to read whats written in there.
How to open my account again?
I am sorry, my first post was not so clear.

---

### Post by steeldriver on 2013-04-25
If your guest session starts OK then I think it's unlikely to be a driver issue

> **Locus Kiesselbachi said:**
> 
I start computer and it loads black screen with mouse pointer (it can be moved). I switch with "Ctrl+Alt+F6" to lower tty.
Now I can enter my [COLOR=#ff0000]root login and password[/COLOR].
Command line opens...
[COLOR=#ff0000]I type "startx"[/COLOR]

now it says...(something like that)
bla-bla ...check "var/log/Xorg.1.log" ...bla bla
Server terminated with error(1) closing log file
Xinit:giving up
Xinit:unable to connect to x server: Connection
Xinit server error.refused.


So when you switch to a virtual terminal (Ctrl-Alt-F6) the current X server session (however broken) stays running in TTY7, so you won't be able to start a new X session (at least, not on the same display). Also, afaik 'startx' doesn't really work for Unity sessions.

Depending on whether you really used the root account or actually used sudo you may also have messed up your .Xauthority file - which in itself will prevent your GUI session from starting up.

As a frist step I'd suggest logging in as your regular user at the Ctlr-Alt-F6 virtual terminal and then checking the following things (1) the ownership of your user's home dir (2) ownership and permissions of the user's hidden Xauthority and ICEauthority files:

```

ls -ld $HOME

ls -l $HOME/.{ICE,X}authority

```

---

### Post by Locus Kiesselbachi on 2013-04-25
> **steeldriver said:**
> If your guest session starts OK then I think it's unlikely to be a driver issue



So when you switch to a virtual terminal (Ctrl-Alt-F6) the current X server session (however broken) stays running in TTY7, so you won't be able to start a new X session (at least, not on the same display). Also, afaik 'startx' doesn't really work for Unity sessions.

Depending on whether you really used the root account or actually used sudo you may also have messed up your .Xauthority file - which in itself will prevent your GUI session from starting up.

As a frist step I'd suggest logging in as your regular user at the Ctlr-Alt-F6 virtual terminal and then checking the following things (1) the ownership of your user's home dir (2) ownership and permissions of the user's hidden Xauthority and ICEauthority files:

```

ls -ld $HOME

ls -l $HOME/.{ICE,X}authority

```
ok I will try it out.

In meanwhile I show what I found.
I tried to look my home folder via quest account - "permission denied"
so I opened terminal and cd to home folder
```

/home$ ls
ls: cannot open directory .: Permission denied
:/home$ sudo ls
sudo: unable to change to sudoers gid: Operation not permitted
```

"Operation not permitted" - ??? well ..yea Im now "quest" afterall. :-(


edit
```

ls -ld **$**HOME

ls -l **$**HOME/.{ICE,X}authority

```
sry I cant insert the command, because I have estonian keyboard layout by default and cant make **$** (dollar sign) in (CTRL-ALT-F6) console. I looked [**this thread**]("http://ubuntuforums.org/showthread.php?t=1786314") for keyboard layout change, but didnt help me.
```
**sudo loadkeys us**
```
gives: cannot open file us
```
**sudo loadkeys uk**
```
gives: cannot open file uk
```
**set xkbmap us**
```
does nothing

---

### Post by r.stiltskin on 2013-04-25
Have you tried to log into your primary user account in TTY6?

---

### Post by Locus Kiesselbachi on 2013-04-25
> **r.stiltskin said:**
> Have you tried to log into your primary user account in TTY6?
Yes, it works . . no problem at all.

*hey... Do you know how to change keyboard layout in (Ctrl+Alt+Fx) console?
edit
**$**...it should be under "4", but gives this ->"¤"

---

### Post by steeldriver on 2013-04-25
if you can't use $HOME in the Ctrl-Alt-F6 virtual terminal then use either ~ or the full pathname e.g.

```
ls -l ~/.Xauthority
```

```
ls -l /home/*yourusername*/.Xauthority
```

---

### Post by Locus Kiesselbachi on 2013-04-25
> **steeldriver said:**
> if you can't use $HOME in the Ctrl-Alt-F6 virtual terminal then use either ~ or the full pathname e.g.

```
ls -l ~/.Xauthority
```

```
ls -l /home/*yourusername*/.Xauthority
```
hmm...
```
ls -l ~/.Xauthority
```
could not make proper "**~**" sign, it appeared above not in middle. X(  awww...
```
ls -l /home/yourusername/.Xauthority
```
gave this:
-rw------- 1 root root 53 Apr 25 09:28 /home/*myusername*/.Xauthonity


awaiting more suggestions

---

### Post by steeldriver on 2013-04-25
OK so you have a root-owned .Xauthority - easiest thing is to just remove it

```
rm /home/*yourusername*/.Xauthority
```

Then Ctrl-Alt-F7 back to the GUI login screen and try again

---

### Post by r.stiltskin on 2013-04-25
EDIT: follow **steeldriver**'s suggestion first.  After that, if you're still having problems:


> **Locus Kiesselbachi said:**
> Yes, it works . . no problem at all.

*hey... Do you know how to change keyboard layout in (Ctrl+Alt+Fx) console?
edit
**$**...it should be under "4", but gives this ->"¤"

Don't know.  But one thing at a time.

Your lightdm.conf looks non-standard.  According to this [Lubuntu Wiki]("https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#For_release_12.04_and_on_.28LightDM.29") it should just say
```
[SeatDefaults]
autologin-user=<YOUR USER>
autologin-user-timeout=0
user-session=Lubuntu
greeter-session=lightdm-gtk-greeter

```
You can use **sudo nano /etc/lightdm/lightdm.conf** in the TTY terminal and edit yours accordingly.

And if that still doesn't work, I notice that in your lightdm.conf and the one in the Wiki, there is an uppercase 'L' in Lubuntu.  In mine, it says "xubuntu".  Note the lowercase 'x'.  So you might want to try changing the 'L' to an 'l'.

And if that still doesn't solve the login problem, you can **sudo apt-get install **--**reinstall lightdm** in the TTY and that should at least get you back to a default configuration.

---

### Post by Locus Kiesselbachi on 2013-04-25
> **steeldriver said:**
> OK so you have a root-owned .Xauthority - easiest thing is to just remove it

```
rm /home/*yourusername*/.Xauthority
```

Then Ctrl-Alt-F7 back to the GUI login screen and try again
Thank you! Thank you!
It helped.

I could get to my account.
I made restart and it automatically logged in to my account. It gave some system error and asked if I want to send error report. Error was about that greeter was closed unexpectadly (acutally Im happy about it).
After second restart everything was normal again.

Now I have one question left... WTF happened? Why did OS acted like that in the first place?

LK

---

### Post by Locus Kiesselbachi on 2013-04-25
> **r.stiltskin said:**
> EDIT: follow **steeldriver**'s suggestion first.  After that, if you're still having problems:




Don't know.  But one thing at a time.

Your lightdm.conf looks non-standard.  According to this [Lubuntu Wiki]("https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#For_release_12.04_and_on_.28LightDM.29") it should just say
```
[SeatDefaults]
autologin-user=<YOUR USER>
autologin-user-timeout=0
user-session=Lubuntu
greeter-session=lightdm-gtk-greeter

```
You can use **sudo nano /etc/lightdm/lightdm.conf** in the TTY terminal and edit yours accordingly.

And if that still doesn't work, I notice that in your lightdm.conf and the one in the Wiki, there is an uppercase 'L' in Lubuntu.  In mine, it says "xubuntu".  Note the lowercase 'x'.  So you might want to try changing the 'L' to an 'l'.

And if that still doesn't solve the login problem, you can **sudo apt-get install **--**reinstall lightdm** in the TTY and that should at least get you back to a default configuration.
I guess you have looked my othrer** [thread]("http://ubuntuforums.org/showthread.php?t=2138785&p=12618515#post12618515")** about lightdm.conf.
lightdm.conf
```
[SeatDefaults]autologin-guest=false
autologin-user=epicehho
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu
```

edit:
It now works and I checked my lightdm.conf again, looks same ... so I guess it wasnt a main problem.

---

