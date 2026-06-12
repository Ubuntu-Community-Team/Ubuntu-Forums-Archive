---
title: "problems after upgrade"
date: 2013-11-01
forum: General Help
---

### Post by TimEnid on 2013-11-01
I upgrade from 13.04 to 13.10 yesterday. Not thru live CD, i got the prompt and installed it that way. Ever since then, after about 10 minutes of having my pc on, it freezes. I try to restart, and when click the option in the upper right corner, the screen just blinks and does nothing. This forces me to have to reboot by pressing my power button. No programs are running. I havent installed anything new. And its not my hardware because everything was running great prior to the upgrade. Please let me know what information you need from me so i can try to resolve this issue. I would hate to have to install the OS all over again. Thanks.

---

### Post by fantab on 2013-11-01
Look at the logs. /var/logs especially loot at xorg.log. If you see any WW or EE the report back.
If you had installed any Proprietory Drivers then re-install those.

---

### Post by TimEnid on 2013-11-02
> **fantab said:**
> Look at the logs. /var/logs especially loot at xorg.log. If you see any WW or EE the report back.
If you had installed any Proprietory Drivers then re-install those.
From xorg.1.log
```
[  3943.231] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[  3943.231] X Protocol Version 11, Revision 0
[  3943.231] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[  3943.231] Current Operating System: Linux tdpough 3.8.0-32-generic #47-Ubuntu SMP Tue Oct 1 22:35:23 UTC 2013 x86_64
[  3943.231] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-32-generic root=UUID=1c22b68a-5563-4f05-9302-29d92a627f0d ro quiet splash vt.handoff=7
[  3943.231] Build Date: 16 October 2013  04:35:36PM
[  3943.231] xorg-server 2:1.13.3-0ubuntu6.2 (For technical support please see http://www.ubuntu.com/support) 
[  3943.231] Current version of pixman: 0.28.2
[  3943.231] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  3943.231] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3943.231] (==) Log file: "/var/log/Xorg.1.log", Time: Sat Oct 26 13:23:49 2013
[  3943.231] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3943.231] (==) No Layout section.  Using the first Screen section.
[  3943.231] (==) No screen section available. Using defaults.
[  3943.231] (**) |-->Screen "Default Screen Section" (0)
[  3943.231] (**) |   |-->Monitor "<default monitor>"
[  3943.232] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  3943.232] (==) Automatically adding devices
[  3943.232] (==) Automatically enabling devices
[  3943.232] (==) Automatically adding GPU devices
[  3943.232] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3943.232] 	Entry deleted from font path.
[  3943.232] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  3943.232] 	Entry deleted from font path.
[  3943.232] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  3943.232] 	Entry deleted from font path.
[  3943.232] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  3943.232] 	Entry deleted from font path.
[  3943.232] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  3943.232] 	Entry deleted from font path.
[  3943.232] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  3943.232] 	Entry deleted from font path.
[  3943.232] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[  3943.232] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  3943.232] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  3943.232] (II) Loader magic: 0x7f8d3a807d20
[  3943.232] (II) Module ABI versions:
[  3943.232] 	X.Org ANSI C Emulation: 0.4
[  3943.232] 	X.Org Video Driver: 13.1
[  3943.232] 	X.Org XInput driver : 18.0
[  3943.232] 	X.Org Server Extension : 7.0
[  3943.232] (II) config/udev: Adding drm device (/dev/dri/card0)
[  3943.235] (--) PCI:*(0:3:0:0) 1002:68be:1682:2982 rev 0, Mem @ 0xd0000000/268435456, 0xfbbc0000/131072, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
[  3943.235] (II) Open ACPI successful (/var/run/acpid.socket)
[  3943.235] Initializing built-in extension Generic Event Extension
[  3943.235] Initializing built-in extension SHAPE
[  3943.235] Initializing built-in extension MIT-SHM
[  3943.235] Initializing built-in extension XInputExtension
[  3943.235] Initializing built-in extension XTEST
[  3943.235] Initializing built-in extension BIG-REQUESTS
[  3943.235] Initializing built-in extension SYNC
[  3943.235] Initializing built-in extension XKEYBOARD
[  3943.235] Initializing built-in extension XC-MISC
[  3943.235] Initializing built-in extension SECURITY
[  3943.235] Initializing built-in extension XINERAMA
[  3943.235] Initializing built-in extension XFIXES
[  3943.235] Initializing built-in extension RENDER
[  3943.235] Initializing built-in extension RANDR
[  3943.235] Initializing built-in extension COMPOSITE
[  3943.235] Initializing built-in extension DAMAGE
[  3943.235] Initializing built-in extension MIT-SCREEN-SAVER
[  3943.235] Initializing built-in extension DOUBLE-BUFFER
[  3943.235] Initializing built-in extension RECORD
[  3943.235] Initializing built-in extension DPMS
[  3943.235] Initializing built-in extension X-Resource
[  3943.235] Initializing built-in extension XVideo
[  3943.235] Initializing built-in extension XVideo-MotionCompensation
[  3943.235] Initializing built-in extension SELinux
[  3943.235] Initializing built-in extension XFree86-VidModeExtension
[  3943.235] Initializing built-in extension XFree86-DGA
[  3943.235] Initializing built-in extension XFree86-DRI
[  3943.235] Initializing built-in extension DRI2
[  3943.235] (II) LoadModule: "glx"
[  3943.235] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  3943.236] (II) Module glx: vendor="X.Org Foundation"
[  3943.236] 	compiled for 1.13.3, module version = 1.0.0
[  3943.236] 	ABI class: X.Org Server Extension, version 7.0
[  3943.236] (==) AIGLX enabled
[  3943.236] Loading extension GLX
[  3943.236] (==) Matched fglrx as autoconfigured driver 0
[  3943.236] (==) Matched ati as autoconfigured driver 1
[  3943.236] (==) Matched fglrx as autoconfigured driver 2
[  3943.236] (==) Matched ati as autoconfigured driver 3
[  3943.236] (==) Matched vesa as autoconfigured driver 4
[  3943.236] (==) Matched modesetting as autoconfigured driver 5
[  3943.236] (==) Matched fbdev as autoconfigured driver 6
[  3943.236] (==) Assigned the driver to the xf86ConfigLayout
[  3943.236] (II) LoadModule: "fglrx"
[  3943.236] (WW) Warning, couldn't open module fglrx
[  3943.236] (II) UnloadModule: "fglrx"
[  3943.236] (II) Unloading fglrx
[  3943.236] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  3943.236] (II) LoadModule: "ati"
[  3943.236] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  3943.236] (II) Module ati: vendor="X.Org Foundation"
[  3943.236] 	compiled for 1.13.3, module version = 7.1.0
[  3943.236] 	Module class: X.Org Video Driver
[  3943.236] 	ABI class: X.Org Video Driver, version 13.1
[  3943.236] (II) LoadModule: "radeon"
[  3943.236] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  3943.237] (II) Module radeon: vendor="X.Org Foundation"
[  3943.237] 	compiled for 1.13.3, module version = 7.1.0
[  3943.237] 	Module class: X.Org Video Driver
[  3943.237] 	ABI class: X.Org Video Driver, version 13.1
[  3943.237] (II) LoadModule: "vesa"
[  3943.237] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  3943.237] (II) Module vesa: vendor="X.Org Foundation"
[  3943.237] 	compiled for 1.12.99.902, module version = 2.3.2
[  3943.237] 	Module class: X.Org Video Driver
[  3943.237] 	ABI class: X.Org Video Driver, version 13.0
[  3943.237] (II) LoadModule: "modesetting"
[  3943.237] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  3943.237] (II) Module modesetting: vendor="X.Org Foundation"
[  3943.237] 	compiled for 1.13.3, module version = 0.7.0
[  3943.237] 	Module class: X.Org Video Driver
[  3943.237] 	ABI class: X.Org Video Driver, version 13.1
[  3943.237] (II) LoadModule: "fbdev"
[  3943.237] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3943.237] (II) Module fbdev: vendor="X.Org Foundation"
[  3943.237] 	compiled for 1.12.99.902, module version = 0.4.3
[  3943.237] 	Module class: X.Org Video Driver
[  3943.237] 	ABI class: X.Org Video Driver, version 13.0
[  3943.237] (==) Matched fglrx as autoconfigured driver 0
[  3943.237] (==) Matched ati as autoconfigured driver 1
[  3943.237] (==) Matched fglrx as autoconfigured driver 2
[  3943.237] (==) Matched ati as autoconfigured driver 3
[  3943.237] (==) Matched vesa as autoconfigured driver 4
[  3943.237] (==) Matched modesetting as autoconfigured driver 5
[  3943.237] (==) Matched fbdev as autoconfigured driver 6
[  3943.237] (==) Assigned the driver to the xf86ConfigLayout
[  3943.237] (II) LoadModule: "fglrx"
[  3943.238] (WW) Warning, couldn't open module fglrx
[  3943.238] (II) UnloadModule: "fglrx"
[  3943.238] (II) Unloading fglrx
[  3943.238] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  3943.238] (II) LoadModule: "ati"
[  3943.238] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  3943.238] (II) Module ati: vendor="X.Org Foundation"
[  3943.238] 	compiled for 1.13.3, module version = 7.1.0
[  3943.238] 	Module class: X.Org Video Driver
[  3943.238] 	ABI class: X.Org Video Driver, version 13.1
[  3943.238] (II) LoadModule: "vesa"
[  3943.238] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  3943.238] (II) Module vesa: vendor="X.Org Foundation"
[  3943.238] 	compiled for 1.12.99.902, module version = 2.3.2
[  3943.238] 	Module class: X.Org Video Driver
[  3943.238] 	ABI class: X.Org Video Driver, version 13.0
[  3943.238] (II) UnloadModule: "vesa"
[  3943.238] (II) Unloading vesa
[  3943.238] (II) Failed to load module "vesa" (already loaded, 0)
[  3943.238] (II) LoadModule: "modesetting"
[  3943.238] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  3943.238] (II) Module modesetting: vendor="X.Org Foundation"
[  3943.238] 	compiled for 1.13.3, module version = 0.7.0
[  3943.238] 	Module class: X.Org Video Driver
[  3943.238] 	ABI class: X.Org Video Driver, version 13.1
[  3943.238] (II) UnloadModule: "modesetting"
[  3943.238] (II) Unloading modesetting
[  3943.238] (II) Failed to load module "modesetting" (already loaded, 0)
[  3943.238] (II) LoadModule: "fbdev"
[  3943.238] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3943.238] (II) Module fbdev: vendor="X.Org Foundation"
[  3943.238] 	compiled for 1.12.99.902, module version = 0.4.3
[  3943.238] 	Module class: X.Org Video Driver
[  3943.238] 	ABI class: X.Org Video Driver, version 13.0
[  3943.238] (II) UnloadModule: "fbdev"
[  3943.238] (II) Unloading fbdev
[  3943.238] (II) Failed to load module "fbdev" (already loaded, 0)
[  3943.238] (II) RADEON: Driver for ATI Radeon chipsets:
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
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE
[  3943.241] (II) VESA: driver for VESA chipsets: vesa
[  3943.241] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  3943.241] (II) FBDEV: driver for framebuffer: fbdev
[  3943.241] (++) using VT number 8


[  3943.341] (II) [KMS] Kernel modesetting enabled.
[  3943.341] (WW) Falling back to old probe method for vesa
[  3943.341] (WW) Falling back to old probe method for modesetting
[  3943.341] (WW) Falling back to old probe method for fbdev
[  3943.341] (II) Loading sub module "fbdevhw"
[  3943.341] (II) LoadModule: "fbdevhw"
[  3943.341] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  3943.342] (II) Module fbdevhw: vendor="X.Org Foundation"
[  3943.342] 	compiled for 1.13.3, module version = 0.0.2
[  3943.342] 	ABI class: X.Org Video Driver, version 13.1
[  3943.342] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  3943.342] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  3943.342] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  3943.342] (==) RADEON(0): Default visual is TrueColor
[  3943.342] (==) RADEON(0): RGB weight 888
[  3943.342] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  3943.342] (--) RADEON(0): Chipset: "ATI Radeon HD 5700 Series" (ChipID = 0x68be)
[  3943.342] (II) Loading sub module "dri2"
[  3943.342] (II) LoadModule: "dri2"
[  3943.342] (II) Module "dri2" already built-in
[  3943.342] (II) Loading sub module "exa"
[  3943.342] (II) LoadModule: "exa"
[  3943.342] (II) Loading /usr/lib/xorg/modules/libexa.so
[  3943.342] (II) Module exa: vendor="X.Org Foundation"
[  3943.342] 	compiled for 1.13.3, module version = 2.6.0
[  3943.342] 	ABI class: X.Org Video Driver, version 13.1
[  3943.342] (II) RADEON(0): KMS Color Tiling: enabled
[  3943.342] (II) RADEON(0): KMS Color Tiling 2D: enabled
[  3943.342] (II) RADEON(0): KMS Pageflipping: enabled
[  3943.342] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  3943.356] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[  3943.358] (II) RADEON(0): Output HDMI-0 has no monitor section
[  3943.380] (II) RADEON(0): Output DVI-0 has no monitor section
[  3943.410] (II) RADEON(0): Output DVI-1 has no monitor section
[  3943.424] (II) RADEON(0): EDID for output DisplayPort-0
[  3943.426] (II) RADEON(0): EDID for output HDMI-0
[  3943.448] (II) RADEON(0): EDID for output DVI-0
[  3943.478] (II) RADEON(0): EDID for output DVI-1
[  3943.478] (II) RADEON(0): Manufacturer: DEL  Model: a038  Serial#: 825307477
[  3943.478] (II) RADEON(0): Year: 2009  Week: 19
[  3943.478] (II) RADEON(0): EDID Version: 1.3
[  3943.478] (II) RADEON(0): Digital Display Input
[  3943.478] (II) RADEON(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[  3943.478] (II) RADEON(0): Gamma: 2.20
[  3943.478] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[  3943.478] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  3943.478] (II) RADEON(0): Default color space is primary color space
[  3943.478] (II) RADEON(0): First detailed timing is preferred mode
[  3943.478] (II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[  3943.478] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[  3943.478] (II) RADEON(0): Supported established timings:
[  3943.478] (II) RADEON(0): 720x400@70Hz
[  3943.478] (II) RADEON(0): 640x480@60Hz
[  3943.478] (II) RADEON(0): 640x480@75Hz
[  3943.478] (II) RADEON(0): 800x600@60Hz
[  3943.479] (II) RADEON(0): 800x600@75Hz
[  3943.479] (II) RADEON(0): 1024x768@60Hz
[  3943.479] (II) RADEON(0): 1024x768@75Hz
[  3943.479] (II) RADEON(0): 1280x1024@75Hz
[  3943.479] (II) RADEON(0): Manufacturer's mask: 0
[  3943.479] (II) RADEON(0): Supported standard timings:
[  3943.479] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[  3943.479] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  3943.479] (II) RADEON(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[  3943.479] (II) RADEON(0): Supported detailed timing:
[  3943.479] (II) RADEON(0): clock: 148.5 MHz   Image Size:  531 x 298 mm
[  3943.479] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[  3943.479] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[  3943.479] (II) RADEON(0): Serial No: M500F959111U
[  3943.479] (II) RADEON(0): Monitor name: DELL S2409W
[  3943.479] (II) RADEON(0): Ranges: V min: 50 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[  3943.479] (II) RADEON(0): EDID (in hex):
[  3943.479] (II) RADEON(0): 	00ffffffffffff0010ac38a055313131
[  3943.479] (II) RADEON(0): 	1313010380351e78eeee91a3544c9926
[  3943.479] (II) RADEON(0): 	0f5054a54b00714f8180d1c001010101
[  3943.479] (II) RADEON(0): 	010101010101023a801871382d40582c
[  3943.479] (II) RADEON(0): 	4500132a2100001e000000ff004d3530
[  3943.479] (II) RADEON(0): 	3046393539313131550a000000fc0044
[  3943.479] (II) RADEON(0): 	454c4c205332343039570a20000000fd
[  3943.479] (II) RADEON(0): 	00324c1e5311000a2020202020200011
[  3943.479] (II) RADEON(0): Printing probed modes for output DVI-1
[  3943.479] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  3943.479] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3943.479] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3943.479] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3943.479] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[  3943.479] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3943.479] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3943.479] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3943.479] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3943.479] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3943.479] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3943.479] (II) RADEON(0): Output DisplayPort-0 disconnected
[  3943.479] (II) RADEON(0): Output HDMI-0 disconnected
[  3943.479] (II) RADEON(0): Output DVI-0 disconnected
[  3943.479] (II) RADEON(0): Output DVI-1 connected
[  3943.479] (II) RADEON(0): Using exact sizes for initial modes
[  3943.479] (II) RADEON(0): Output DVI-1 using initial mode 1920x1080
[  3943.479] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  3943.479] (II) RADEON(0): mem size init: gart size :1fdef000 vram size: s:40000000 visible:3f7d7000
[  3943.479] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[  3943.479] (==) RADEON(0): DPI set to (96, 96)
[  3943.479] (II) Loading sub module "fb"
[  3943.479] (II) LoadModule: "fb"
[  3943.479] (II) Loading /usr/lib/xorg/modules/libfb.so
[  3943.479] (II) Module fb: vendor="X.Org Foundation"
[  3943.479] 	compiled for 1.13.3, module version = 1.0.0
[  3943.479] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3943.479] (II) Loading sub module "ramdac"
[  3943.479] (II) LoadModule: "ramdac"
[  3943.479] (II) Module "ramdac" already built-in
[  3943.479] (II) UnloadModule: "vesa"
[  3943.479] (II) Unloading vesa
[  3943.479] (II) UnloadModule: "modesetting"
[  3943.479] (II) Unloading modesetting
[  3943.480] (II) UnloadModule: "fbdev"
[  3943.480] (II) Unloading fbdev
[  3943.480] (II) UnloadSubModule: "fbdevhw"
[  3943.480] (II) Unloading fbdevhw
[  3943.480] (--) Depth 24 pixmap format is 32 bpp
[  3943.480] (II) RADEON(0): [DRI2] Setup complete
[  3943.480] (II) RADEON(0): [DRI2]   DRI driver: r600
[  3943.480] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[  3943.480] (II) RADEON(0): Front buffer size: 8640K
[  3943.480] (II) RADEON(0): VRAM usage limit set to 928335K
[  3943.480] (==) RADEON(0): Backing store disabled
[  3943.480] (II) RADEON(0): Direct rendering enabled
[  3943.480] (II) EXA(0): Driver allocated offscreen pixmaps
[  3943.480] (II) EXA(0): Driver registered support for the following operations:
[  3943.480] (II)         Solid
[  3943.480] (II)         Copy
[  3943.480] (II)         Composite (RENDER acceleration)
[  3943.480] (II)         UploadToScreen
[  3943.480] (II)         DownloadFromScreen
[  3943.480] (II) RADEON(0): Acceleration enabled
[  3943.480] (==) RADEON(0): DPMS enabled
[  3943.480] (==) RADEON(0): Silken mouse enabled
[  3943.480] (II) RADEON(0): Set up textured video
[  3943.480] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[  3943.480] (II) RADEON(0): [XvMC] Extension initialized.
[  3943.480] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  3943.481] (--) RandR disabled
[  3943.487] (II) SELinux: Disabled on system
[  3943.497] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  3943.497] (II) AIGLX: enabled GLX_INTEL_swap_event
[  3943.498] (II) AIGLX: enabled GLX_ARB_create_context
[  3943.498] (II) AIGLX: enabled GLX_ARB_create_context_profile
[  3943.498] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[  3943.498] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  3943.498] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  3943.498] (II) AIGLX: Loaded and initialized r600
[  3943.498] (II) GLX: Initialized DRI2 GL provider for screen 0
[  3943.499] (II) RADEON(0): Setting screen physical size to 508 x 285
[  3943.505] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3943.507] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  3943.507] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  3943.507] (II) LoadModule: "evdev"
[  3943.507] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3943.507] (II) Module evdev: vendor="X.Org Foundation"
[  3943.507] 	compiled for 1.13.3, module version = 2.7.3
[  3943.507] 	Module class: X.Org XInput Driver
[  3943.508] 	ABI class: X.Org XInput driver, version 18.0
[  3943.508] (II) Using input driver 'evdev' for 'Power Button'
[  3943.508] (**) Power Button: always reports core events
[  3943.508] (**) evdev: Power Button: Device: "/dev/input/event1"
[  3943.508] (--) evdev: Power Button: Vendor 0 Product 0x1
[  3943.508] (--) evdev: Power Button: Found keys
[  3943.508] (II) evdev: Power Button: Configuring as keyboard
[  3943.508] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  3943.508] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  3943.508] (**) Option "xkb_rules" "evdev"
[  3943.508] (**) Option "xkb_model" "pc105"
[  3943.508] (**) Option "xkb_layout" "us"
[  3943.508] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  3943.508] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  3943.508] (II) Using input driver 'evdev' for 'Power Button'
[  3943.508] (**) Power Button: always reports core events
[  3943.508] (**) evdev: Power Button: Device: "/dev/input/event0"
[  3943.508] (--) evdev: Power Button: Vendor 0 Product 0x1
[  3943.508] (--) evdev: Power Button: Found keys
[  3943.508] (II) evdev: Power Button: Configuring as keyboard
[  3943.508] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[  3943.508] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  3943.508] (**) Option "xkb_rules" "evdev"
[  3943.508] (**) Option "xkb_model" "pc105"
[  3943.508] (**) Option "xkb_layout" "us"
[  3943.508] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[  3943.508] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[  3943.509] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event13)
[  3943.509] (II) No input driver specified, ignoring this device.
[  3943.509] (II) This device may have been added with another device file.
[  3943.509] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event10)
[  3943.509] (II) No input driver specified, ignoring this device.
[  3943.509] (II) This device may have been added with another device file.
[  3943.509] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event11)
[  3943.509] (II) No input driver specified, ignoring this device.
[  3943.509] (II) This device may have been added with another device file.
[  3943.509] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event12)
[  3943.509] (II) No input driver specified, ignoring this device.
[  3943.509] (II) This device may have been added with another device file.
[  3943.509] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event5)
[  3943.509] (II) No input driver specified, ignoring this device.
[  3943.509] (II) This device may have been added with another device file.
[  3943.509] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event6)
[  3943.509] (II) No input driver specified, ignoring this device.
[  3943.509] (II) This device may have been added with another device file.
[  3943.510] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event7)
[  3943.510] (II) No input driver specified, ignoring this device.
[  3943.510] (II) This device may have been added with another device file.
[  3943.510] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event8)
[  3943.510] (II) No input driver specified, ignoring this device.
[  3943.510] (II) This device may have been added with another device file.
[  3943.510] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event9)
[  3943.510] (II) No input driver specified, ignoring this device.
[  3943.510] (II) This device may have been added with another device file.
[  3943.510] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/event2)
[  3943.510] (**) Logitech USB Trackball: Applying InputClass "evdev pointer catchall"
[  3943.510] (II) Using input driver 'evdev' for 'Logitech USB Trackball'
[  3943.510] (**) Logitech USB Trackball: always reports core events
[  3943.510] (**) evdev: Logitech USB Trackball: Device: "/dev/input/event2"
[  3943.510] (--) evdev: Logitech USB Trackball: Vendor 0x46d Product 0xc408
[  3943.510] (--) evdev: Logitech USB Trackball: Found 9 mouse buttons
[  3943.510] (--) evdev: Logitech USB Trackball: Found relative axes
[  3943.510] (--) evdev: Logitech USB Trackball: Found x and y relative axes
[  3943.510] (II) evdev: Logitech USB Trackball: Configuring as mouse
[  3943.510] (**) evdev: Logitech USB Trackball: YAxisMapping: buttons 4 and 5
[  3943.510] (**) evdev: Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  3943.510] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input2/event2"
[  3943.510] (II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE, id 8)
[  3943.510] (II) evdev: Logitech USB Trackball: initialized for relative axes.
[  3943.510] (**) Logitech USB Trackball: (accel) keeping acceleration scheme 1
[  3943.510] (**) Logitech USB Trackball: (accel) acceleration profile 0
[  3943.510] (**) Logitech USB Trackball: (accel) acceleration factor: 2.000
[  3943.510] (**) Logitech USB Trackball: (accel) acceleration threshold: 4
[  3943.511] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/mouse0)
[  3943.511] (II) No input driver specified, ignoring this device.
[  3943.511] (II) This device may have been added with another device file.
[  3943.511] (II) config/udev: Adding input device Microsoft Microsoft® Digital Media Pro Keyboard (/dev/input/event3)
[  3943.511] (**) Microsoft Microsoft® Digital Media Pro Keyboard: Applying InputClass "evdev keyboard catchall"
[  3943.511] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Digital Media Pro Keyboard'
[  3943.511] (**) Microsoft Microsoft® Digital Media Pro Keyboard: always reports core events
[  3943.511] (**) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Device: "/dev/input/event3"
[  3943.511] (--) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Vendor 0x45e Product 0xb0
[  3943.511] (--) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Found keys
[  3943.511] (II) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Configuring as keyboard
[  3943.511] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input3/event3"
[  3943.511] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Digital Media Pro Keyboard" (type: KEYBOARD, id 9)
[  3943.511] (**) Option "xkb_rules" "evdev"
[  3943.511] (**) Option "xkb_model" "pc105"
[  3943.511] (**) Option "xkb_layout" "us"
[  3943.511] (II) config/udev: Adding input device Microsoft Microsoft® Digital Media Pro Keyboard (/dev/input/event4)
[  3943.511] (**) Microsoft Microsoft® Digital Media Pro Keyboard: Applying InputClass "evdev keyboard catchall"
[  3943.511] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Digital Media Pro Keyboard'
[  3943.511] (**) Microsoft Microsoft® Digital Media Pro Keyboard: always reports core events
[  3943.511] (**) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Device: "/dev/input/event4"
[  3943.511] (--) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Vendor 0x45e Product 0xb0
[  3943.511] (--) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Found 1 mouse buttons
[  3943.511] (--) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Found scroll wheel(s)
[  3943.511] (--) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Found relative axes
[  3943.511] (--) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Found absolute axes
[  3943.511] (--) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Found absolute multitouch axes
[  3943.511] (--) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Found x and y absolute axes
[  3943.511] (--) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Found keys
[  3943.511] (II) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Forcing relative x/y axes to exist.
[  3943.511] (II) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Configuring as mouse
[  3943.511] (II) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Configuring as keyboard
[  3943.511] (II) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: Adding scrollwheel support
[  3943.511] (**) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: YAxisMapping: buttons 4 and 5
[  3943.511] (**) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  3943.511] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input4/event4"
[  3943.511] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Digital Media Pro Keyboard" (type: KEYBOARD, id 10)
[  3943.511] (**) Option "xkb_rules" "evdev"
[  3943.511] (**) Option "xkb_model" "pc105"
[  3943.512] (**) Option "xkb_layout" "us"
[  3943.512] (II) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: initialized for relative axes.
[  3943.512] (WW) evdev: Microsoft Microsoft® Digital Media Pro Keyboard: ignoring absolute axes.
[  3943.512] (**) Microsoft Microsoft® Digital Media Pro Keyboard: (accel) keeping acceleration scheme 1
[  3943.512] (**) Microsoft Microsoft® Digital Media Pro Keyboard: (accel) acceleration profile 0
[  3943.512] (**) Microsoft Microsoft® Digital Media Pro Keyboard: (accel) acceleration factor: 2.000
[  3943.512] (**) Microsoft Microsoft® Digital Media Pro Keyboard: (accel) acceleration threshold: 4
[  3943.512] (II) config/udev: Adding input device Microsoft Microsoft® Digital Media Pro Keyboard (/dev/input/js0)
[  3943.512] (II) No input driver specified, ignoring this device.
[  3943.512] (II) This device may have been added with another device file.
[  3943.715] (II) RADEON(0): EDID vendor "DEL", prod id 41016
[  3943.715] (II) RADEON(0): Using EDID range info for horizontal sync
[  3943.715] (II) RADEON(0): Using EDID range info for vertical refresh
[  3943.715] (II) RADEON(0): Printing DDC gathered Modelines:
[  3943.715] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  3943.715] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3943.715] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3943.715] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3943.715] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3943.715] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3943.715] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3943.715] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3943.715] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3943.715] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3943.715] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3943.715] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  3943.830] (II) RADEON(0): EDID vendor "DEL", prod id 41016
[  3943.830] (II) RADEON(0): Using hsync ranges from config file
[  3943.830] (II) RADEON(0): Using vrefresh ranges from config file
[  3943.830] (II) RADEON(0): Printing DDC gathered Modelines:
[  3943.830] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  3943.830] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3943.830] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3943.830] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3943.830] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3943.830] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3943.831] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3943.831] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3943.831] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3943.831] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3943.831] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3943.831] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  3954.131] (II) RADEON(0): EDID vendor "DEL", prod id 41016
[  3954.131] (II) RADEON(0): Using hsync ranges from config file
[  3954.131] (II) RADEON(0): Using vrefresh ranges from config file
[  3954.131] (II) RADEON(0): Printing DDC gathered Modelines:
[  3954.131] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  3954.131] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3954.131] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3954.131] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3954.131] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3954.131] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3954.131] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3954.131] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3954.131] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3954.131] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3954.131] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3954.131] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  3954.367] (II) RADEON(0): EDID vendor "DEL", prod id 41016
[  3954.367] (II) RADEON(0): Using hsync ranges from config file
[  3954.367] (II) RADEON(0): Using vrefresh ranges from config file
[  3954.367] (II) RADEON(0): Printing DDC gathered Modelines:
[  3954.367] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  3954.367] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3954.367] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3954.367] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3954.367] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3954.367] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3954.367] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3954.367] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3954.367] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3954.367] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3954.367] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3954.367] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  3954.635] (II) RADEON(0): EDID vendor "DEL", prod id 41016
[  3954.635] (II) RADEON(0): Using hsync ranges from config file
[  3954.635] (II) RADEON(0): Using vrefresh ranges from config file
[  3954.635] (II) RADEON(0): Printing DDC gathered Modelines:
[  3954.635] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  3954.635] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3954.635] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3954.635] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3954.635] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3954.635] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3954.635] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3954.635] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3954.635] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3954.635] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3954.635] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3954.635] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  3954.771] (II) RADEON(0): EDID vendor "DEL", prod id 41016
[  3954.771] (II) RADEON(0): Using hsync ranges from config file
[  3954.771] (II) RADEON(0): Using vrefresh ranges from config file
[  3954.771] (II) RADEON(0): Printing DDC gathered Modelines:
[  3954.771] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  3954.771] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3954.771] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3954.771] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3954.771] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3954.771] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3954.771] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3954.771] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3954.771] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3954.771] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3954.771] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3954.771] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  3955.229] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[  3975.179] (II) RADEON(0): EDID vendor "DEL", prod id 41016
[  3975.179] (II) RADEON(0): Using hsync ranges from config file
[  3975.179] (II) RADEON(0): Using vrefresh ranges from config file
[  3975.179] (II) RADEON(0): Printing DDC gathered Modelines:
[  3975.179] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  3975.179] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3975.179] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3975.179] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3975.179] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3975.179] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3975.179] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3975.179] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3975.179] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3975.179] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3975.179] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3975.179] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)

```

---

### Post by TimEnid on 2013-11-03
Anyone?

---

### Post by fantab on 2013-11-03
This might help: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

