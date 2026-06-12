---
title: "High CPU usage when moving mouse in Lubuntu"
date: 2015-01-28
forum: General Help
---

### Post by Brent_Santin on 2015-01-28
Hi, I'm using Lubuntu 14.04.1 (fresh install) on a Compaq Presario V2000 laptop (Pentium M running at about 1.8GHz, 1.5GB RAM, 60GB Hard drive).

I had noticed high CPU usage when loading web pages in Firefox (which wasn't unusual considering the age of the computer).  But what caught my interest was that even after the web-page had loaded, the CPU usage remained relatively high when I moved the mouse pointer over the web-page (i.e. 50%). So then I shut down all applications and just moved the mouse pointer along a "blank" desktop. I noticed that when moving the mouse pointer in constant circles, the CPU usage goes up to about 9-16%. Again; this is on a desktop with nothing else on it (except for the task manager which shows me the CPU usage). I tried loading a Lubuntu live CD and noticed the same spike when moving the mouse.

It seems strange that moving a simple mouse pointer should use 10% of the CPU.  Unless there is something not ideal happening with the graphics rendering/GPU and the CPU is having to re-draw the screen by brute force.  The graphics chipset is the Intel 82852/82855 family.

On the the same computer, when using Windows XP, similar mouse movement on a blank desktop only uses 1-3% CPU.

Any ideas?

---

### Post by kalehrl on 2015-01-28
What is the output of this command:
```
 grep "direct rendering" /var/log/Xorg.0.log
```

---

### Post by Brent_Santin on 2015-01-28
The output of that command is:

```

[    24.632] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    24.632] X Protocol Version 11, Revision 0
[    24.632] Build Operating System: Linux 3.2.0-70-generic i686 Ubuntu
[    24.632] Current Operating System: Linux santin-Presario-V2000-EP448UA-ABL 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:23:46 UTC 2014 i686
[    24.632] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-44-generic root=UUID=8a3b01e6-2943-49f2-a87c-d58d6a98cb03 ro quiet splash vt.handoff=7
[    24.633] Build Date: 10 December 2014  06:16:10PM
[    24.633] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[    24.633] Current version of pixman: 0.30.2
[    24.633]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    24.633] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.633] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 28 21:41:16 2015
[    24.637] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.691] (==) No Layout section.  Using the first Screen section.
[    24.691] (==) No screen section available. Using defaults.
[    24.691] (**) |-->Screen "Default Screen Section" (0)
[    24.691] (**) |   |-->Monitor "<default monitor>"
[    24.705] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    24.705] (==) Automatically adding devices
[    24.705] (==) Automatically enabling devices
[    24.705] (==) Automatically adding GPU devices
[    24.723] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.723]     Entry deleted from font path.
[    24.723] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.723]     Entry deleted from font path.
[    24.723] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.723]     Entry deleted from font path.
[    24.723] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    24.723]     Entry deleted from font path.
[    24.723] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.724]     Entry deleted from font path.
[    24.724] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.724]     Entry deleted from font path.
[    24.724] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[    24.724] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.724] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.724] (II) Loader magic: 0xb77e36c0
[    24.724] (II) Module ABI versions:
[    24.724]     X.Org ANSI C Emulation: 0.4
[    24.724]     X.Org Video Driver: 15.0
[    24.724]     X.Org XInput driver : 20.0
[    24.724]     X.Org Server Extension : 8.0
[    24.724] (II) xfree86: Adding drm device (/dev/dri/card0)
[    24.726] (--) PCI:*(0:1:5:0) 1002:5955:103c:3091 rev 0, Mem @ 0xc8000000/134217728, 0xc0100000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[    24.730] Initializing built-in extension Generic Event Extension
[    24.731] Initializing built-in extension SHAPE
[    24.731] Initializing built-in extension MIT-SHM
[    24.731] Initializing built-in extension XInputExtension
[    24.731] Initializing built-in extension XTEST
[    24.731] Initializing built-in extension BIG-REQUESTS
[    24.731] Initializing built-in extension SYNC
[    24.731] Initializing built-in extension XKEYBOARD
[    24.731] Initializing built-in extension XC-MISC
[    24.731] Initializing built-in extension SECURITY
[    24.731] Initializing built-in extension XINERAMA
[    24.731] Initializing built-in extension XFIXES
[    24.731] Initializing built-in extension RENDER
[    24.731] Initializing built-in extension RANDR
[    24.731] Initializing built-in extension COMPOSITE
[    24.731] Initializing built-in extension DAMAGE
[    24.731] Initializing built-in extension MIT-SCREEN-SAVER
[    24.731] Initializing built-in extension DOUBLE-BUFFER
[    24.731] Initializing built-in extension RECORD
[    24.731] Initializing built-in extension DPMS
[    24.731] Initializing built-in extension Present
[    24.731] Initializing built-in extension DRI3
[    24.731] Initializing built-in extension X-Resource
[    24.731] Initializing built-in extension XVideo
[    24.731] Initializing built-in extension XVideo-MotionCompensation
[    24.731] Initializing built-in extension SELinux
[    24.731] Initializing built-in extension XFree86-VidModeExtension
[    24.731] Initializing built-in extension XFree86-DGA
[    24.731] Initializing built-in extension XFree86-DRI
[    24.731] Initializing built-in extension DRI2
[    24.731] (II) LoadModule: "glx"
[    24.761] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.876] (II) Module glx: vendor="X.Org Foundation"
[    24.877]     compiled for 1.15.1, module version = 1.0.0
[    24.877]     ABI class: X.Org Server Extension, version 8.0
[    24.877] (==) AIGLX enabled
[    24.877] Loading extension GLX
[    24.877] (==) Matched fglrx as autoconfigured driver 0
[    24.877] (==) Matched ati as autoconfigured driver 1
[    24.877] (==) Matched fglrx as autoconfigured driver 2
[    24.877] (==) Matched ati as autoconfigured driver 3
[    24.877] (==) Matched modesetting as autoconfigured driver 4
[    24.877] (==) Matched fbdev as autoconfigured driver 5
[    24.877] (==) Matched vesa as autoconfigured driver 6
[    24.877] (==) Assigned the driver to the xf86ConfigLayout
[    24.877] (II) LoadModule: "fglrx"
[    24.879] (WW) Warning, couldn't open module fglrx
[    24.879] (II) UnloadModule: "fglrx"
[    24.879] (II) Unloading fglrx
[    24.879] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    24.879] (II) LoadModule: "ati"
[    24.880] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    24.882] (II) Module ati: vendor="X.Org Foundation"
[    24.882]     compiled for 1.15.1, module version = 7.3.0
[    24.882]     Module class: X.Org Video Driver
[    24.882]     ABI class: X.Org Video Driver, version 15.0
[    24.882] (II) LoadModule: "radeon"
[    24.882] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    24.929] (II) Module radeon: vendor="X.Org Foundation"
[    24.929]     compiled for 1.15.1, module version = 7.3.0
[    24.929]     Module class: X.Org Video Driver
[    24.929]     ABI class: X.Org Video Driver, version 15.0
[    24.929] (II) LoadModule: "modesetting"
[    24.929] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.933] (II) Module modesetting: vendor="X.Org Foundation"
[    24.933]     compiled for 1.15.0, module version = 0.8.1
[    24.933]     Module class: X.Org Video Driver
[    24.933]     ABI class: X.Org Video Driver, version 15.0
[    24.933] (II) LoadModule: "fbdev"
[    24.934] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.936] (II) Module fbdev: vendor="X.Org Foundation"
[    24.936]     compiled for 1.15.0, module version = 0.4.4
[    24.936]     Module class: X.Org Video Driver
[    24.936]     ABI class: X.Org Video Driver, version 15.0
[    24.936] (II) LoadModule: "vesa"
[    24.937] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.941] (II) Module vesa: vendor="X.Org Foundation"
[    24.941]     compiled for 1.15.0, module version = 2.3.3
[    24.941]     Module class: X.Org Video Driver
[    24.941]     ABI class: X.Org Video Driver, version 15.0
[    24.941] (==) Matched fglrx as autoconfigured driver 0
[    24.941] (==) Matched ati as autoconfigured driver 1
[    24.941] (==) Matched fglrx as autoconfigured driver 2
[    24.941] (==) Matched ati as autoconfigured driver 3
[    24.941] (==) Matched modesetting as autoconfigured driver 4
[    24.941] (==) Matched fbdev as autoconfigured driver 5
[    24.941] (==) Matched vesa as autoconfigured driver 6
[    24.941] (==) Assigned the driver to the xf86ConfigLayout
[    24.941] (II) LoadModule: "fglrx"
[    24.942] (WW) Warning, couldn't open module fglrx
[    24.942] (II) UnloadModule: "fglrx"
[    24.942] (II) Unloading fglrx
[    24.942] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    24.942] (II) LoadModule: "ati"
[    24.942] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    24.942] (II) Module ati: vendor="X.Org Foundation"
[    24.942]     compiled for 1.15.1, module version = 7.3.0
[    24.942]     Module class: X.Org Video Driver
[    24.942]     ABI class: X.Org Video Driver, version 15.0
[    24.942] (II) LoadModule: "modesetting"
[    24.942] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.942] (II) Module modesetting: vendor="X.Org Foundation"
[    24.942]     compiled for 1.15.0, module version = 0.8.1
[    24.942]     Module class: X.Org Video Driver
[    24.942]     ABI class: X.Org Video Driver, version 15.0
[    24.942] (II) UnloadModule: "modesetting"
[    24.942] (II) Unloading modesetting
[    24.942] (II) Failed to load module "modesetting" (already loaded, 0)
[    24.942] (II) LoadModule: "fbdev"
[    24.943] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.943] (II) Module fbdev: vendor="X.Org Foundation"
[    24.943]     compiled for 1.15.0, module version = 0.4.4
[    24.943]     Module class: X.Org Video Driver
[    24.943]     ABI class: X.Org Video Driver, version 15.0
[    24.943] (II) UnloadModule: "fbdev"
[    24.943] (II) Unloading fbdev
[    24.943] (II) Failed to load module "fbdev" (already loaded, 0)
[    24.943] (II) LoadModule: "vesa"
[    24.943] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.943] (II) Module vesa: vendor="X.Org Foundation"
[    24.943]     compiled for 1.15.0, module version = 2.3.3
[    24.943]     Module class: X.Org Video Driver
[    24.943]     ABI class: X.Org Video Driver, version 15.0
[    24.943] (II) UnloadModule: "vesa"
[    24.943] (II) Unloading vesa
[    24.943] (II) Failed to load module "vesa" (already loaded, 0)
[    24.943] (II) RADEON: Driver for ATI Radeon chipsets:
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
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII
[    24.952] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    24.952] (II) FBDEV: driver for framebuffer: fbdev
[    24.952] (II) VESA: driver for VESA chipsets: vesa
[    24.952] (++) using VT number 7

[    24.960] (II) [KMS] Kernel modesetting enabled.
[    24.960] (WW) Falling back to old probe method for modesetting
[    24.960] (WW) Falling back to old probe method for fbdev
[    24.960] (II) Loading sub module "fbdevhw"
[    24.960] (II) LoadModule: "fbdevhw"
[    24.961] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.964] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.964]     compiled for 1.15.1, module version = 0.0.2
[    24.964]     ABI class: X.Org Video Driver, version 15.0
[    24.964] (WW) Falling back to old probe method for vesa
[    24.964] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    24.965] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    24.965] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    24.965] (==) RADEON(0): Default visual is TrueColor
[    24.965] (==) RADEON(0): RGB weight 888
[    24.965] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    24.965] (--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5955 (PCIE)" (ChipID = 0x5955)
[    24.965] (II) Loading sub module "dri2"
[    24.965] (II) LoadModule: "dri2"
[    24.965] (II) Module "dri2" already built-in
[    24.965] (II) Loading sub module "exa"
[    24.965] (II) LoadModule: "exa"
[    24.965] (II) Loading /usr/lib/xorg/modules/libexa.so
[    24.972] (II) Module exa: vendor="X.Org Foundation"
[    24.973]     compiled for 1.15.1, module version = 2.6.0
[    24.973]     ABI class: X.Org Video Driver, version 15.0
[    24.973] (II) RADEON(0): KMS Color Tiling: enabled
[    24.973] (II) RADEON(0): KMS Color Tiling 2D: disabled
[    24.973] (II) RADEON(0): KMS Pageflipping: enabled
[    24.973] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    24.995] (II) RADEON(0): Output VGA-0 has no monitor section
[    24.995] (II) RADEON(0): Output LVDS has no monitor section
[    24.995] (II) RADEON(0): Output S-video has no monitor section
[    25.018] (II) RADEON(0): EDID for output VGA-0
[    25.019] (II) RADEON(0): EDID for output LVDS
[    25.019] (II) RADEON(0): Manufacturer: LPL  Model: 0  Serial#: 0
[    25.019] (II) RADEON(0): Year: 2005  Week: 0
[    25.019] (II) RADEON(0): EDID Version: 1.2
[    25.019] (II) RADEON(0): Digital Display Input
[    25.019] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 18
[    25.019] (II) RADEON(0): Gamma: 2.20
[    25.019] (II) RADEON(0): No DPMS capabilities specified
[    25.019] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.019] (II) RADEON(0): First detailed timing is preferred mode
[    25.019] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.327 greenY: 0.546
[    25.019] (II) RADEON(0): blueX: 0.160 blueY: 0.147   whiteX: 0.312 whiteY: 0.328
[    25.019] (II) RADEON(0): Manufacturer's mask: 0
[    25.019] (II) RADEON(0): Supported detailed timing:
[    25.019] (II) RADEON(0): clock: 68.2 MHz   Image Size:  305 x 1830 mm
[    25.019] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    25.019] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 790 v_border: 0
[    25.019] (II) RADEON(0):  LGPhilipsLCD
[    25.019] (II) RADEON(0):  LP140WX1-TL01
[    25.019] (II) RADEON(0): EDID (in hex):
[    25.019] (II) RADEON(0):     00ffffffffffff00320c000000000000
[    25.019] (II) RADEON(0):     000f0102801e12780a0f309758538b29
[    25.019] (II) RADEON(0):     25505400000001010101010101010101
[    25.019] (II) RADEON(0):     010101010101a91a00a0500016303020
[    25.019] (II) RADEON(0):     130031b7100000190000000000000000
[    25.019] (II) RADEON(0):     00000000000000000000000000fe004c
[    25.019] (II) RADEON(0):     475068696c6970734c43440a000000fe
[    25.019] (II) RADEON(0):     004c503134305758312d544c30310085
[    25.019] (WW) RADEON(0): Output LVDS: Strange aspect ratio (305/18300), consider adding a quirk
[    25.019] (II) RADEON(0): Printing probed modes for output LVDS
[    25.019] (II) RADEON(0): Modeline "1280x768"x60.0   68.25  1280 1328 1360 1440  768 769 772 790 -hsync -vsync (47.4 kHz eP)
[    25.019] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    25.019] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    25.019] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    25.019] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    25.019] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    25.019] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    25.019] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    25.019] (II) RADEON(0): EDID for output S-video
[    25.019] (II) RADEON(0): Output VGA-0 disconnected
[    25.019] (II) RADEON(0): Output LVDS connected
[    25.019] (II) RADEON(0): Output S-video disconnected
[    25.019] (II) RADEON(0): Using exact sizes for initial modes
[    25.019] (II) RADEON(0): Output LVDS using initial mode 1280x768
[    25.019] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.019] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:7c00000
[    25.019] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    25.019] (==) RADEON(0): DPI set to (96, 96)
[    25.019] (II) Loading sub module "fb"
[    25.020] (II) LoadModule: "fb"
[    25.020] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.027] (II) Module fb: vendor="X.Org Foundation"
[    25.027]     compiled for 1.15.1, module version = 1.0.0
[    25.027]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.027] (II) Loading sub module "ramdac"
[    25.027] (II) LoadModule: "ramdac"
[    25.027] (II) Module "ramdac" already built-in
[    25.027] (II) UnloadModule: "modesetting"
[    25.027] (II) Unloading modesetting
[    25.027] (II) UnloadModule: "fbdev"
[    25.027] (II) Unloading fbdev
[    25.027] (II) UnloadSubModule: "fbdevhw"
[    25.027] (II) Unloading fbdevhw
[    25.027] (II) UnloadModule: "vesa"
[    25.027] (II) Unloading vesa
[    25.028] (--) Depth 24 pixmap format is 32 bpp
[    25.037] (II) RADEON(0): [DRI2] Setup complete
[    25.037] (II) RADEON(0): [DRI2]   DRI driver: r300
[    25.037] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[    25.037] (II) RADEON(0): Front buffer size: 3840K
[    25.037] (II) RADEON(0): VRAM usage limit set to 110793K
[    25.046] (==) RADEON(0): Backing store enabled
[    25.046] (II) RADEON(0): Direct rendering enabled
[    25.046] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    25.047] (II) EXA(0): Driver allocated offscreen pixmaps
[    25.047] (II) EXA(0): Driver registered support for the following operations:
[    25.047] (II)         Solid
[    25.047] (II)         Copy
[    25.047] (II)         Composite (RENDER acceleration)
[    25.047] (II)         UploadToScreen
[    25.047] (II)         DownloadFromScreen
[    25.047] (II) RADEON(0): Acceleration enabled
[    25.047] (==) RADEON(0): DPMS enabled
[    25.047] (==) RADEON(0): Silken mouse enabled
[    25.052] (II) RADEON(0): Set up textured video
[    25.053] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    25.053] (II) RADEON(0): [XvMC] Extension initialized.
[    25.053] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.058] (--) RandR disabled
[    25.075] (II) SELinux: Disabled on system
[    25.780] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    25.780] (II) AIGLX: enabled GLX_ARB_create_context
[    25.780] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    25.780] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    25.780] (II) AIGLX: enabled GLX_INTEL_swap_event
[    25.780] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    25.780] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    25.780] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    25.780] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    25.781] (II) AIGLX: Loaded and initialized r300
[    25.781] (II) GLX: Initialized DRI2 GL provider for screen 0
[    25.783] (II) RADEON(0): Setting screen physical size to 338 x 203
[    25.829] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.843] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    25.844] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.844] (II) LoadModule: "evdev"
[    25.845] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.859] (II) Module evdev: vendor="X.Org Foundation"
[    25.859]     compiled for 1.15.0, module version = 2.8.2
[    25.859]     Module class: X.Org XInput Driver
[    25.859]     ABI class: X.Org XInput driver, version 20.0
[    25.859] (II) Using input driver 'evdev' for 'Power Button'
[    25.859] (**) Power Button: always reports core events
[    25.859] (**) evdev: Power Button: Device: "/dev/input/event3"
[    25.860] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.860] (--) evdev: Power Button: Found keys
[    25.860] (II) evdev: Power Button: Configuring as keyboard
[    25.860] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    25.860] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    25.860] (**) Option "xkb_rules" "evdev"
[    25.860] (**) Option "xkb_model" "pc105"
[    25.860] (**) Option "xkb_layout" "us"
[    25.861] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    25.861] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.861] (II) Using input driver 'evdev' for 'Video Bus'
[    25.861] (**) Video Bus: always reports core events
[    25.861] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    25.861] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    25.861] (--) evdev: Video Bus: Found keys
[    25.861] (II) evdev: Video Bus: Configuring as keyboard
[    25.861] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0e/LNXVIDEO:00/input/input7/event6"
[    25.861] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    25.861] (**) Option "xkb_rules" "evdev"
[    25.861] (**) Option "xkb_model" "pc105"
[    25.861] (**) Option "xkb_layout" "us"
[    25.863] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    25.863] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.863] (II) Using input driver 'evdev' for 'Power Button'
[    25.863] (**) Power Button: always reports core events
[    25.863] (**) evdev: Power Button: Device: "/dev/input/event0"
[    25.863] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.863] (--) evdev: Power Button: Found keys
[    25.863] (II) evdev: Power Button: Configuring as keyboard
[    25.863] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    25.863] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    25.863] (**) Option "xkb_rules" "evdev"
[    25.863] (**) Option "xkb_model" "pc105"
[    25.863] (**) Option "xkb_layout" "us"
[    25.864] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    25.865] (II) No input driver specified, ignoring this device.
[    25.865] (II) This device may have been added with another device file.
[    25.865] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    25.865] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.865] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.865] (**) Sleep Button: always reports core events
[    25.865] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    25.865] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    25.865] (--) evdev: Sleep Button: Found keys
[    25.865] (II) evdev: Sleep Button: Configuring as keyboard
[    25.865] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    25.865] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    25.865] (**) Option "xkb_rules" "evdev"
[    25.865] (**) Option "xkb_model" "pc105"
[    25.865] (**) Option "xkb_layout" "us"
[    25.867] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:05.0/drm/card0
[    25.867] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    25.867] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    25.867] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.867] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.867] (**) AT Translated Set 2 keyboard: always reports core events
[    25.868] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    25.868] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    25.868] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    25.868] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    25.868] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    25.868] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    25.868] (**) Option "xkb_rules" "evdev"
[    25.868] (**) Option "xkb_model" "pc105"
[    25.868] (**) Option "xkb_layout" "us"
[    25.869] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    25.869] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.869] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    25.869] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    25.869] (II) LoadModule: "synaptics"
[    25.869] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.880] (II) Module synaptics: vendor="X.Org Foundation"
[    25.880]     compiled for 1.15.0, module version = 1.7.4
[    25.880]     Module class: X.Org XInput Driver
[    25.880]     ABI class: X.Org XInput driver, version 20.0
[    25.880] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    25.880] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.880] (**) Option "Device" "/dev/input/event5"
[    25.880] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 63)
[    25.880] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 109)
[    25.880] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    25.880] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    25.880] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    25.880] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    25.881] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    25.881] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.881] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event5"
[    25.881] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    25.881] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    25.881] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    25.881] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    25.881] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    25.881] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    25.881] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    25.881] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    25.881] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    25.882] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    25.882] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    25.885] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[    25.885] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    25.885] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    25.886] (**) HP WMI hotkeys: always reports core events
[    25.886] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event7"
[    25.886] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    25.886] (--) evdev: HP WMI hotkeys: Found keys
[    25.886] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    25.886] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event7"
[    25.886] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[    25.886] (**) Option "xkb_rules" "evdev"
[    25.886] (**) Option "xkb_model" "pc105"
[    25.886] (**) Option "xkb_layout" "us"
[    63.065] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm


```

---

### Post by kalehrl on 2015-01-29
Direct rendering is active so the driver is loaded and operating fine.
The cause is somewhere else.

---

### Post by Brent_Santin on 2015-01-29
Would there be any way to tell if it was being caused be my Synaptic mouse pad (i.e. driver)?

Also, in the log quoted above, should this warning be of concern?

[    24.877] (II) LoadModule: "fglrx"
[    24.879] (WW) Warning, couldn't open module fglrx
[    24.879] (II) UnloadModule: "fglrx"
[    24.879] (II) Unloading fglrx
[    24.879] (EE) Failed to load module "fglrx" (module does not exist, 0)

---

### Post by Impavidus on 2015-01-29
> **kalehrl said:**
> What is the output of this command:
```
 grep "direct rendering" /var/log/Xorg.0.log
```

> **Brent_Santin said:**
> The output of that command is:

```

[    24.632] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    24.632] X Protocol Version 11, Revision 0
[    24.632] Build Operating System: Linux 3.2.0-70-generic i686 Ubuntu
[    24.632] Current Operating System: Linux santin-Presario-V2000-EP448UA-ABL 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:23:46 UTC 2014 i686
[    24.632] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-44-generic root=UUID=8a3b01e6-2943-49f2-a87c-d58d6a98cb03 ro quiet splash vt.handoff=7

(...)

```

That is not the output of that command. The suggested command will show the lines in /var/log/Xorg.0.log containing the string "direct rendering". You showed the entire log file and the string is not present, suggesting that direct rendering is not active. But I'm not very familiar with ATI graphics cards. I only have an old one in an old computer, which has always worked without manual tweaking.

---

### Post by Brent_Santin on 2015-01-29
Thanks for chiming in on this.

When I executed the command:
 grep "direct rendering" /var/log/Xorg.0.log

There was no ouput via the command line interface.  I just got a fresh $> input "ready" statement.  When I saw that no output was occuring, then I assumed he wanted to see the output of the logfile.

Ugh...I too suspect that direct rending is not active, as the machine seems very sluggish, especially when trying to render a web-page in Firefox. Any type of moving graphics on the web-page (i.e. animated gif) cause CPU usage to peak.  I would appreciate any help anyone can give to diagnose this problem.

PS: I should mention that I'm running this installation from a USB stick.  NOT a live USB, and actual installation to USB as if it were a hard drive.  I wanted to make sure Lubuntu ran well on this machine before I did a real installation.

---

### Post by Brent_Santin on 2015-01-29
Update: 

After looking online for ways to determine if direct rendering was working on my system, I found and executed the following test:

[B]santin@santin-Presario-V2000-EP448UA-ABL:~$ glxinfo | grep '^direct rendering:'
direct rendering: [COLOR=#ff0000]Yes[/COLOR]
santin@santin-Presario-V2000-EP448UA-ABL:~$ [/B]

So I assume this is a reliable test of direct rendering and I should suspect some other component is consuming CPU cycles when moving the mouse.

---

### Post by Brent_Santin on 2015-01-29
Second Update:

I believe this is definitely related to the driver software for the Synaptec touchpad.  I plugged in a USB mouse and when I wave the mouse pointer around on a blank desktop the CPU meter does not climb above 5%.  As soon as I touch the Synaptec touchpad to do the same thing, CPU jumps to between 10-15%.

I would rather not use a USB mouse, so is there any way to disable the special features of the touchpad to just make it a "generic" touchpad.  I don't need the special hand gestures.

---

### Post by Mike_Walsh on 2015-01-29
Hallo, Brent.

I, too, have tried full USB installs with the 'buntu flavours.....all four, in fact; Ubuntu, Kubuntu, Xubuntu AND Lubuntu. And in every case, I have found them to be somewhat on the slow side.

The only Linux distros that I have found to work perfectly from a flash drive are the Puppy Linux 'flavours'. The system files remain in a compressed state on the flash drive; upon boot-up, they decompress into RAM, and in fact the entire O/S sits, and works in, RAM...it's that small. And RAM is an extremely quick medium...the Puppies run incredibly fast.

The system will periodically save anything you've downloaded, altered, saved or changed to your personal 'save-file', which is created at first shut-down. It does this about every half hour or so, to cut down on wear of the flash memory.

And the advantage of this set-up is that you ALWAYS start off every session with pristine, unaltered, fresh system files.

But of course, this is of no interest to you, as you are only trying this out with a view to doing an HDD install...


Regards,

Mike.

---

### Post by BazBear on 2015-01-29
You could try the **Pointing Devices** app, it's in the Software Center. The only down side to this app is that, while you can set it to autostart on boot, it won't save your settings between sessions (at least on Lubuntu); but not really a big deal as you can simply open the GUI and uncheck and recheck the *Disable tapping and scrolling option* and you're good to go for the rest of the session. I've been using it on my Synaptic touch pad equipped netbook to shut off all of the annoying (to me) gestures/tap to click/edge scroll features for a couple of years now.

---

