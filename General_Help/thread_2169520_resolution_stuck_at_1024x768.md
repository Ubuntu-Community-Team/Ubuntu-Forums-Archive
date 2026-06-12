---
title: "resolution stuck at 1024x768"
date: 2013-08-22
forum: General Help
---

### Post by ruudx on 2013-08-22
Actually in the beginning it was working fine at 1366x768. But then one day my computer hanged and I had to restart.

  Since then I'm stuck at 1024x768 with no other resolution options. I  have read answers of many relevant questions but none of the suggestions  work.

  I tried adding new modes through:

  
[LIST=1]
[*]cvt, xrandr
[*]modified xorg.conf by adding

  Modes  "1366x768"
[/LIST]
  and similar suggestions but none have worked. Any help would be appreciated. I am ready to furnish any other details if required.

p.s. - i'm new to this site so apologies if this thread is in the wrong forum or if i am required to ask for help in an already created thread.

---

### Post by deadflowr on 2013-08-22
It might help to know what graphics card you're running.

If either Nvidia and AMD, then they should have configuration programs available for you.

It might even help to re-install the drivers.

---

### Post by Yellow Pasque on 2013-08-22
Post /var/log/Xorg.0.log (use [ code ][ /code ] tags)

---

### Post by ruudx on 2013-08-27
[ 						 							@ ]("http://ubuntuforums.org/member.php?u=1276577")[**[COLOR=#000000]deadflowr[/COLOR]**]("http://ubuntuforums.org/member.php?u=1276577")
i have an amd graphics card. But i don't think that that is causing the problem. When i upgraded from ubuntu 12.04 to ubuntu 12.10 my resolution got stuck at 1024x768. I read somewhere that it was because of amd graphics drivers and the suggestion was to uninstall them. I did and it went back to normal 1366x768. Everything was working fine until suddenly one day my laptop hanged and since restarting i'm stuck at 1024x768 again with no other options. Anyway i could be wrong here though.
p.s. sorry for the late reply, i have been very busy the past few days.

---

### Post by ruudx on 2013-08-27
@Temujin 
The output of /var/log/Xorg.0.log is pretty big ~ 3000 lines. Do you want to filter some keywords or still want all of it?

---

### Post by Yellow Pasque on 2013-08-27
I want it all! :P
Actually, if there's repeating text at the end, you can cut that part out. Just make sure you use code tags (or pastebin.com)

---

### Post by ruudx on 2013-08-27
[ 						 							]("http://ubuntuforums.org/member.php?u=327594")@Temujin Here's the output:

```

[    28.341] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    28.341] X Protocol Version 11, Revision 0
[    28.341] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    28.341] Current Operating System: Linux kaushik-Inspiron-1440 3.5.0-39-generic #60-Ubuntu SMP Tue Aug 13 18:33:05 UTC 2013 x86_64
[    28.341] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-39-generic root=UUID=5bc20d06-6284-4645-bd20-65d58fd9a98c ro quiet splash nomodeset vt.handoff=7
[    28.341] Build Date: 11 April 2013  12:53:36PM
[    28.341] xorg-server 2:1.13.0-0ubuntu6.2 (For technical support please see http://www.ubuntu.com/support) 
[    28.341] Current version of pixman: 0.26.0
[    28.341]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    28.341] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.342] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 27 04:02:49 2013
[    28.342] (==) Using config file: "/etc/X11/xorg.conf"
[    28.342] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.342] (==) No Layout section.  Using the first Screen section.
[    28.342] (**) |-->Screen "Default Screen" (0)
[    28.342] (**) |   |-->Monitor "<default monitor>"
[    28.342] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    28.342] (==) Automatically adding devices
[    28.342] (==) Automatically enabling devices
[    28.342] (==) Automatically adding GPU devices
[    28.342] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.342]     Entry deleted from font path.
[    28.342] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.342]     Entry deleted from font path.
[    28.342] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.342]     Entry deleted from font path.
[    28.342] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.342]     Entry deleted from font path.
[    28.342] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.342]     Entry deleted from font path.
[    28.342] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    28.342] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.342] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.342] (II) Loader magic: 0x7f5fcaba5c40
[    28.342] (II) Module ABI versions:
[    28.342]     X.Org ANSI C Emulation: 0.4
[    28.342]     X.Org Video Driver: 13.0
[    28.342]     X.Org XInput driver : 18.0
[    28.342]     X.Org Server Extension : 7.0
[    28.343] (II) config/udev: Adding drm device (/dev/dri/card0)
[    28.345] (--) PCI:*(0:1:0:0) 1002:9552:1028:02cf rev 0, Mem @ 0xe0000000/268435456, 0xf6df0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[    28.345] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.345] Initializing built-in extension Generic Event Extension
[    28.345] Initializing built-in extension SHAPE
[    28.345] Initializing built-in extension MIT-SHM
[    28.345] Initializing built-in extension XInputExtension
[    28.345] Initializing built-in extension XTEST
[    28.345] Initializing built-in extension BIG-REQUESTS
[    28.345] Initializing built-in extension SYNC
[    28.345] Initializing built-in extension XKEYBOARD
[    28.345] Initializing built-in extension XC-MISC
[    28.345] Initializing built-in extension SECURITY
[    28.345] Initializing built-in extension XINERAMA
[    28.345] Initializing built-in extension XFIXES
[    28.345] Initializing built-in extension RENDER
[    28.345] Initializing built-in extension RANDR
[    28.345] Initializing built-in extension COMPOSITE
[    28.345] Initializing built-in extension DAMAGE
[    28.345] Initializing built-in extension MIT-SCREEN-SAVER
[    28.345] Initializing built-in extension DOUBLE-BUFFER
[    28.345] Initializing built-in extension RECORD
[    28.345] Initializing built-in extension DPMS
[    28.345] Initializing built-in extension X-Resource
[    28.345] Initializing built-in extension XVideo
[    28.345] Initializing built-in extension XVideo-MotionCompensation
[    28.345] Initializing built-in extension XFree86-VidModeExtension
[    28.345] Initializing built-in extension XFree86-DGA
[    28.345] Initializing built-in extension XFree86-DRI
[    28.345] Initializing built-in extension DRI2
[    28.345] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    28.345] (II) LoadModule: "glx"
[    28.439] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.439] (II) Module glx: vendor="X.Org Foundation"
[    28.439]     compiled for 1.13.0, module version = 1.0.0
[    28.439]     ABI class: X.Org Server Extension, version 7.0
[    28.439] (==) AIGLX enabled
[    28.439] Loading extension GLX
[    28.439] (==) Matched fglrx as autoconfigured driver 0
[    28.439] (==) Matched ati as autoconfigured driver 1
[    28.439] (==) Matched fglrx as autoconfigured driver 2
[    28.439] (==) Matched ati as autoconfigured driver 3
[    28.439] (==) Matched vesa as autoconfigured driver 4
[    28.439] (==) Matched modesetting as autoconfigured driver 5
[    28.439] (==) Matched fbdev as autoconfigured driver 6
[    28.439] (==) Assigned the driver to the xf86ConfigLayout
[    28.439] (II) LoadModule: "fglrx"
[    28.530] (WW) Warning, couldn't open module fglrx
[    28.530] (II) UnloadModule: "fglrx"
[    28.530] (II) Unloading fglrx
[    28.530] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    28.530] (II) LoadModule: "ati"
[    28.530] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    28.530] (II) Module ati: vendor="X.Org Foundation"
[    28.530]     compiled for 1.13.0, module version = 6.99.99
[    28.530]     Module class: X.Org Video Driver
[    28.530]     ABI class: X.Org Video Driver, version 13.0
[    28.530] (II) LoadModule: "radeon"
[    28.531] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    28.531] (II) Module radeon: vendor="X.Org Foundation"
[    28.531]     compiled for 1.13.0, module version = 6.99.99
[    28.531]     Module class: X.Org Video Driver
[    28.531]     ABI class: X.Org Video Driver, version 13.0
[    28.531] (II) LoadModule: "vesa"
[    28.531] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.531] (II) Module vesa: vendor="X.Org Foundation"
[    28.531]     compiled for 1.12.99.902, module version = 2.3.2
[    28.531]     Module class: X.Org Video Driver
[    28.531]     ABI class: X.Org Video Driver, version 13.0
[    28.531] (II) LoadModule: "modesetting"
[    28.531] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.531] (II) Module modesetting: vendor="X.Org Foundation"
[    28.531]     compiled for 1.13.0, module version = 0.5.0
[    28.531]     Module class: X.Org Video Driver
[    28.531]     ABI class: X.Org Video Driver, version 13.0
[    28.531] (II) LoadModule: "fbdev"
[    28.531] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.531] (II) Module fbdev: vendor="X.Org Foundation"
[    28.531]     compiled for 1.12.99.902, module version = 0.4.3
[    28.531]     Module class: X.Org Video Driver
[    28.531]     ABI class: X.Org Video Driver, version 13.0
[    28.531] (==) Matched fglrx as autoconfigured driver 0
[    28.532] (==) Matched ati as autoconfigured driver 1
[    28.532] (==) Matched fglrx as autoconfigured driver 2
[    28.532] (==) Matched ati as autoconfigured driver 3
[    28.532] (==) Matched vesa as autoconfigured driver 4
[    28.532] (==) Matched modesetting as autoconfigured driver 5
[    28.532] (==) Matched fbdev as autoconfigured driver 6
[    28.532] (==) Assigned the driver to the xf86ConfigLayout
[    28.532] (II) LoadModule: "fglrx"
[    28.532] (WW) Warning, couldn't open module fglrx
[    28.532] (II) UnloadModule: "fglrx"
[    28.532] (II) Unloading fglrx
[    28.532] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    28.532] (II) LoadModule: "ati"
[    28.532] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    28.532] (II) Module ati: vendor="X.Org Foundation"
[    28.532]     compiled for 1.13.0, module version = 6.99.99
[    28.532]     Module class: X.Org Video Driver
[    28.532]     ABI class: X.Org Video Driver, version 13.0
[    28.532] (II) LoadModule: "vesa"
[    28.532] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.532] (II) Module vesa: vendor="X.Org Foundation"
[    28.532]     compiled for 1.12.99.902, module version = 2.3.2
[    28.532]     Module class: X.Org Video Driver
[    28.532]     ABI class: X.Org Video Driver, version 13.0
[    28.532] (II) UnloadModule: "vesa"
[    28.532] (II) Unloading vesa
[    28.532] (II) Failed to load module "vesa" (already loaded, 0)
[    28.532] (II) LoadModule: "modesetting"
[    28.532] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.532] (II) Module modesetting: vendor="X.Org Foundation"
[    28.532]     compiled for 1.13.0, module version = 0.5.0
[    28.532]     Module class: X.Org Video Driver
[    28.533]     ABI class: X.Org Video Driver, version 13.0
[    28.533] (II) UnloadModule: "modesetting"
[    28.533] (II) Unloading modesetting
[    28.533] (II) Failed to load module "modesetting" (already loaded, 0)
[    28.533] (II) LoadModule: "fbdev"
[    28.533] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.533] (II) Module fbdev: vendor="X.Org Foundation"
[    28.533]     compiled for 1.12.99.902, module version = 0.4.3
[    28.533]     Module class: X.Org Video Driver
[    28.533]     ABI class: X.Org Video Driver, version 13.0
[    28.533] (II) UnloadModule: "fbdev"
[    28.533] (II) Unloading fbdev
[    28.533] (II) Failed to load module "fbdev" (already loaded, 0)
[    28.533] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    28.537] (II) VESA: driver for VESA chipsets: vesa
[    28.537] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    28.537] (II) FBDEV: driver for framebuffer: fbdev
[    28.537] (++) using VT number 7

[    28.537] (II) [KMS] drm report modesetting isn't supported.
[    28.537] (II) [KMS] drm report modesetting isn't supported.
[    28.537] (II) [KMS] drm report modesetting isn't supported.
[    28.537] (WW) Falling back to old probe method for modesetting
[    28.537] (WW) Falling back to old probe method for fbdev
[    28.537] (II) Loading sub module "fbdevhw"
[    28.537] (II) LoadModule: "fbdevhw"
[    28.537] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.537] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.537]     compiled for 1.13.0, module version = 0.0.2
[    28.537]     ABI class: X.Org Video Driver, version 13.0
[    28.537] (EE) Screen 0 deleted because of no matching config section.
[    28.537] (II) UnloadModule: "radeon"
[    28.537] (EE) Screen 0 deleted because of no matching config section.
[    28.537] (II) UnloadModule: "radeon"
[    28.537] (II) Loading sub module "vbe"
[    28.537] (II) LoadModule: "vbe"
[    28.538] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    28.538] (II) Module vbe: vendor="X.Org Foundation"
[    28.538]     compiled for 1.13.0, module version = 1.1.0
[    28.538]     ABI class: X.Org Video Driver, version 13.0
[    28.538] (II) Loading sub module "int10"
[    28.538] (II) LoadModule: "int10"
[    28.538] (II) Loading /usr/lib/xorg/modules/libint10.so
[    28.538] (II) Module int10: vendor="X.Org Foundation"
[    28.538]     compiled for 1.13.0, module version = 1.0.0
[    28.538]     ABI class: X.Org Video Driver, version 13.0
[    28.538] (II) VESA(0): initializing int10
[    30.035] (II) VESA(0): VESA BIOS detected
[    30.035] (II) VESA(0): VESA VBE Version 3.0
[    30.035] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    30.035] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    30.035] (II) VESA(0): VESA VBE OEM Software Rev: 11.22
[    30.035] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    30.035] (II) VESA(0): VESA VBE OEM Product: M92
[    30.035] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    30.047] (**) VESA(0): Depth 24, (--) framebuffer bpp 32
[    30.047] (==) VESA(0): RGB weight 888
[    30.047] (==) VESA(0): Default visual is TrueColor
[    30.047] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.047] (II) Loading sub module "ddc"
[    30.047] (II) LoadModule: "ddc"
[    30.047] (II) Module "ddc" already built-in
[    30.048] (II) VESA(0): VESA VBE DDC supported
[    30.048] (II) VESA(0): VESA VBE DDC Level 2
[    30.048] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    30.103] (II) VESA(0): VESA VBE DDC read successfully
[    30.103] (II) VESA(0): Manufacturer: AUO  Model: 193c  Serial#: 0
[    30.103] (II) VESA(0): Year: 2009  Week: 1
[    30.103] (II) VESA(0): EDID Version: 1.3
[    30.103] (II) VESA(0): Digital Display Input
[    30.103] (II) VESA(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[    30.103] (II) VESA(0): Gamma: 2.20
[    30.103] (II) VESA(0): No DPMS capabilities specified
[    30.103] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    30.103] (II) VESA(0): First detailed timing is preferred mode
[    30.103] (II) VESA(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[    30.103] (II) VESA(0): blueX: 0.150 blueY: 0.600   whiteX: 0.313 whiteY: 0.329
[    30.103] (II) VESA(0): Manufacturer's mask: 0
[    30.103] (II) VESA(0): Supported detailed timing:
[    30.103] (II) VESA(0): clock: 70.2 MHz   Image Size:  309 x 173 mm
[    30.103] (II) VESA(0): h_active: 1366  h_sync: 1404  h_sync_end 1426 h_blank_end 1456 h_border: 0
[    30.103] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[    30.103] (II) VESA(0): Unknown vendor-specific block f
[    30.103] (II) VESA(0):  AUO
[    30.103] (II) VESA(0):  B140XW01 V9
[    30.103] (II) VESA(0): EDID (in hex):
[    30.103] (II) VESA(0):     00ffffffffffff0006af3c1900000000
[    30.103] (II) VESA(0):     01130103801f11780ac8a59e57549226
[    30.103] (II) VESA(0):     99505400000001010101010101010101
[    30.103] (II) VESA(0):     0101010101016c1b565a500023302616
[    30.103] (II) VESA(0):     360035ad100000180000000f00000000
[    30.103] (II) VESA(0):     00000000000000000020000000fe0041
[    30.103] (II) VESA(0):     554f0a202020202020202020000000fe
[    30.103] (II) VESA(0):     004231343058573031205639200a00a7
[    30.103] (II) VESA(0): EDID vendor "AUO", prod id 6460
[    30.103] (II) VESA(0): Printing DDC gathered Modelines:
[    30.103] (II) VESA(0): Modeline "1366x768"x0.0   70.20  1366 1404 1426 1456  768 771 777 803 -hsync -vsync (48.2 kHz eP)
[    30.103] (II) VESA(0): Searching for matching VESA mode(s):
[    30.104] Mode: 100 (640x400)
[    30.104]     ModeAttributes: 0xbb
[    30.104]     WinAAttributes: 0x7
[    30.104]     WinBAttributes: 0x0
[    30.104]     WinGranularity: 64
[    30.104]     WinSize: 64
[    30.104]     WinASegment: 0xa000
[    30.104]     WinBSegment: 0x0
[    30.104]     WinFuncPtr: 0xc000536d
[    30.104]     BytesPerScanline: 640
[    30.104]     XResolution: 640
[    30.104]     YResolution: 400
[    30.104]     XCharSize: 8
[    30.104]     YCharSize: 16
[    30.104]     NumberOfPlanes: 1
[    30.104]     BitsPerPixel: 8
[    30.104]     NumberOfBanks: 1
[    30.104]     MemoryModel: 4
[    30.104]     BankSize: 0
[    30.104]     NumberOfImages: 63
[    30.104]     RedMaskSize: 0
[    30.104]     RedFieldPosition: 0
[    30.104]     GreenMaskSize: 0
[    30.104]     GreenFieldPosition: 0
[    30.104]     BlueMaskSize: 0
[    30.104]     BlueFieldPosition: 0
[    30.104]     RsvdMaskSize: 0
[    30.104]     RsvdFieldPosition: 0
[    30.104]     DirectColorModeInfo: 0
[    30.104]     PhysBasePtr: 0xe0000000
[    30.104]     LinBytesPerScanLine: 640
[    30.104]     BnkNumberOfImagePages: 63
[    30.104]     LinNumberOfImagePages: 63
[    30.104]     LinRedMaskSize: 0
[    30.104]     LinRedFieldPosition: 0
[    30.104]     LinGreenMaskSize: 0
[    30.104]     LinGreenFieldPosition: 0
[    30.104]     LinBlueMaskSize: 0
[    30.104]     LinBlueFieldPosition: 0
[    30.104]     LinRsvdMaskSize: 0
[    30.104]     LinRsvdFieldPosition: 0
[    30.104]     MaxPixelClock: 400000000
[    30.104] Mode: 101 (640x480)
[    30.104]     ModeAttributes: 0xbb
[    30.104]     WinAAttributes: 0x7
[    30.104]     WinBAttributes: 0x0
[    30.104]     WinGranularity: 64
[    30.104]     WinSize: 64
[    30.104]     WinASegment: 0xa000
[    30.104]     WinBSegment: 0x0
[    30.104]     WinFuncPtr: 0xc000536d
[    30.104]     BytesPerScanline: 640
[    30.104]     XResolution: 640
[    30.104]     YResolution: 480
[    30.104]     XCharSize: 8
[    30.104]     YCharSize: 16
[    30.104]     NumberOfPlanes: 1
[    30.104]     BitsPerPixel: 8
[    30.104]     NumberOfBanks: 1
[    30.104]     MemoryModel: 4
[    30.104]     BankSize: 0
[    30.104]     NumberOfImages: 50
[    30.104]     RedMaskSize: 0
[    30.104]     RedFieldPosition: 0
[    30.104]     GreenMaskSize: 0
[    30.104]     GreenFieldPosition: 0
[    30.104]     BlueMaskSize: 0
[    30.104]     BlueFieldPosition: 0
[    30.104]     RsvdMaskSize: 0
[    30.104]     RsvdFieldPosition: 0
[    30.104]     DirectColorModeInfo: 0
[    30.104]     PhysBasePtr: 0xe0000000
[    30.104]     LinBytesPerScanLine: 640
[    30.104]     BnkNumberOfImagePages: 50
[    30.104]     LinNumberOfImagePages: 50
[    30.104]     LinRedMaskSize: 0
[    30.104]     LinRedFieldPosition: 0
[    30.105]     LinGreenMaskSize: 0
[    30.105]     LinGreenFieldPosition: 0
[    30.105]     LinBlueMaskSize: 0
[    30.105]     LinBlueFieldPosition: 0
[    30.105]     LinRsvdMaskSize: 0
[    30.105]     LinRsvdFieldPosition: 0
[    30.105]     MaxPixelClock: 400000000
[    30.105] Mode: 103 (800x600)
[    30.105]     ModeAttributes: 0xbb
[    30.105]     WinAAttributes: 0x7
[    30.105]     WinBAttributes: 0x0
[    30.105]     WinGranularity: 64
[    30.105]     WinSize: 64
[    30.105]     WinASegment: 0xa000
[    30.105]     WinBSegment: 0x0
[    30.105]     WinFuncPtr: 0xc000536d
[    30.105]     BytesPerScanline: 832
[    30.105]     XResolution: 800
[    30.105]     YResolution: 600
[    30.105]     XCharSize: 8
[    30.105]     YCharSize: 14
[    30.105]     NumberOfPlanes: 1
[    30.105]     BitsPerPixel: 8
[    30.105]     NumberOfBanks: 1
[    30.105]     MemoryModel: 4
[    30.105]     BankSize: 0
[    30.105]     NumberOfImages: 31
[    30.105]     RedMaskSize: 0
[    30.105]     RedFieldPosition: 0
[    30.105]     GreenMaskSize: 0
[    30.105]     GreenFieldPosition: 0
[    30.105]     BlueMaskSize: 0
[    30.105]     BlueFieldPosition: 0
[    30.105]     RsvdMaskSize: 0
[    30.105]     RsvdFieldPosition: 0
[    30.105]     DirectColorModeInfo: 0
[    30.105]     PhysBasePtr: 0xe0000000
[    30.105]     LinBytesPerScanLine: 832
[    30.105]     BnkNumberOfImagePages: 31
[    30.105]     LinNumberOfImagePages: 31
[    30.105]     LinRedMaskSize: 0
[    30.105]     LinRedFieldPosition: 0
[    30.105]     LinGreenMaskSize: 0
[    30.105]     LinGreenFieldPosition: 0
[    30.105]     LinBlueMaskSize: 0
[    30.105]     LinBlueFieldPosition: 0
[    30.105]     LinRsvdMaskSize: 0
[    30.105]     LinRsvdFieldPosition: 0
[    30.105]     MaxPixelClock: 400000000
[    30.105] Mode: 105 (1024x768)
[    30.105]     ModeAttributes: 0xbb
[    30.105]     WinAAttributes: 0x7
[    30.105]     WinBAttributes: 0x0
[    30.105]     WinGranularity: 64
[    30.105]     WinSize: 64
[    30.105]     WinASegment: 0xa000
[    30.105]     WinBSegment: 0x0
[    30.105]     WinFuncPtr: 0xc000536d
[    30.105]     BytesPerScanline: 1024
[    30.105]     XResolution: 1024
[    30.105]     YResolution: 768
[    30.105]     XCharSize: 8
[    30.105]     YCharSize: 16
[    30.105]     NumberOfPlanes: 1
[    30.105]     BitsPerPixel: 8
[    30.105]     NumberOfBanks: 1
[    30.105]     MemoryModel: 4
[    30.105]     BankSize: 0
[    30.105]     NumberOfImages: 18
[    30.105]     RedMaskSize: 0
[    30.105]     RedFieldPosition: 0
[    30.105]     GreenMaskSize: 0
[    30.105]     GreenFieldPosition: 0
[    30.105]     BlueMaskSize: 0
[    30.105]     BlueFieldPosition: 0
[    30.105]     RsvdMaskSize: 0
[    30.105]     RsvdFieldPosition: 0
[    30.105]     DirectColorModeInfo: 0
[    30.106]     PhysBasePtr: 0xe0000000
[    30.106]     LinBytesPerScanLine: 1024
[    30.106]     BnkNumberOfImagePages: 18
[    30.106]     LinNumberOfImagePages: 18
[    30.106]     LinRedMaskSize: 0
[    30.106]     LinRedFieldPosition: 0
[    30.106]     LinGreenMaskSize: 0
[    30.106]     LinGreenFieldPosition: 0
[    30.106]     LinBlueMaskSize: 0
[    30.106]     LinBlueFieldPosition: 0
[    30.106]     LinRsvdMaskSize: 0
[    30.106]     LinRsvdFieldPosition: 0
[    30.106]     MaxPixelClock: 400000000
[    30.106] Mode: 107 (1280x1024)
[    30.106]     ModeAttributes: 0xba
[    30.106]     WinAAttributes: 0x7
[    30.106]     WinBAttributes: 0x0
[    30.106]     WinGranularity: 64
[    30.106]     WinSize: 64
[    30.106]     WinASegment: 0xa000
[    30.106]     WinBSegment: 0x0
[    30.106]     WinFuncPtr: 0xc000536d
[    30.106]     BytesPerScanline: 1280
[    30.106]     XResolution: 1280
[    30.106]     YResolution: 1024
[    30.106]     XCharSize: 8
[    30.106]     YCharSize: 16
[    30.106]     NumberOfPlanes: 1
[    30.106]     BitsPerPixel: 8
[    30.106]     NumberOfBanks: 1
[    30.106]     MemoryModel: 4
[    30.106]     BankSize: 0
[    30.106]     NumberOfImages: 11
[    30.106]     RedMaskSize: 0
[    30.106]     RedFieldPosition: 0
[    30.106]     GreenMaskSize: 0
[    30.106]     GreenFieldPosition: 0
[    30.106]     BlueMaskSize: 0
[    30.106]     BlueFieldPosition: 0
[    30.106]     RsvdMaskSize: 0
[    30.106]     RsvdFieldPosition: 0
[    30.106]     DirectColorModeInfo: 0
[    30.106]     PhysBasePtr: 0xe0000000
[    30.106]     LinBytesPerScanLine: 1280
[    30.106]     BnkNumberOfImagePages: 11
[    30.106]     LinNumberOfImagePages: 11
[    30.106]     LinRedMaskSize: 0
[    30.106]     LinRedFieldPosition: 0
[    30.106]     LinGreenMaskSize: 0
[    30.106]     LinGreenFieldPosition: 0
[    30.106]     LinBlueMaskSize: 0
[    30.106]     LinBlueFieldPosition: 0
[    30.106]     LinRsvdMaskSize: 0
[    30.106]     LinRsvdFieldPosition: 0
[    30.106]     MaxPixelClock: 400000000
[    30.106] Mode: 110 (640x480)
[    30.106]     ModeAttributes: 0xbb
[    30.106]     WinAAttributes: 0x7
[    30.106]     WinBAttributes: 0x0
[    30.106]     WinGranularity: 64
[    30.106]     WinSize: 64
[    30.106]     WinASegment: 0xa000
[    30.106]     WinBSegment: 0x0
[    30.106]     WinFuncPtr: 0xc000536d
[    30.106]     BytesPerScanline: 1280
[    30.106]     XResolution: 640
[    30.106]     YResolution: 480
[    30.106]     XCharSize: 8
[    30.106]     YCharSize: 16
[    30.106]     NumberOfPlanes: 1
[    30.106]     BitsPerPixel: 16
[    30.106]     NumberOfBanks: 1
[    30.106]     MemoryModel: 6
[    30.106]     BankSize: 0
[    30.106]     NumberOfImages: 24
[    30.106]     RedMaskSize: 5
[    30.106]     RedFieldPosition: 10
[    30.106]     GreenMaskSize: 5
[    30.106]     GreenFieldPosition: 5
[    30.107]     BlueMaskSize: 5
[    30.107]     BlueFieldPosition: 0
[    30.107]     RsvdMaskSize: 0
[    30.107]     RsvdFieldPosition: 0
[    30.107]     DirectColorModeInfo: 0
[    30.107]     PhysBasePtr: 0xe0000000
[    30.107]     LinBytesPerScanLine: 1280
[    30.107]     BnkNumberOfImagePages: 24
[    30.107]     LinNumberOfImagePages: 24
[    30.107]     LinRedMaskSize: 5
[    30.107]     LinRedFieldPosition: 10
[    30.107]     LinGreenMaskSize: 5
[    30.107]     LinGreenFieldPosition: 5
[    30.107]     LinBlueMaskSize: 5
[    30.107]     LinBlueFieldPosition: 0
[    30.107]     LinRsvdMaskSize: 0
[    30.107]     LinRsvdFieldPosition: 0
[    30.107]     MaxPixelClock: 400000000
[    30.107] Mode: 111 (640x480)
[    30.107]     ModeAttributes: 0xbb
[    30.107]     WinAAttributes: 0x7
[    30.107]     WinBAttributes: 0x0
[    30.107]     WinGranularity: 64
[    30.107]     WinSize: 64
[    30.107]     WinASegment: 0xa000
[    30.107]     WinBSegment: 0x0
[    30.107]     WinFuncPtr: 0xc000536d
[    30.107]     BytesPerScanline: 1280
[    30.107]     XResolution: 640
[    30.107]     YResolution: 480
[    30.107]     XCharSize: 8
[    30.107]     YCharSize: 16
[    30.107]     NumberOfPlanes: 1
[    30.107]     BitsPerPixel: 16
[    30.107]     NumberOfBanks: 1
[    30.107]     MemoryModel: 6
[    30.107]     BankSize: 0
[    30.107]     NumberOfImages: 24
[    30.107]     RedMaskSize: 5
[    30.107]     RedFieldPosition: 11
[    30.107]     GreenMaskSize: 6
[    30.107]     GreenFieldPosition: 5
[    30.107]     BlueMaskSize: 5
[    30.107]     BlueFieldPosition: 0
[    30.107]     RsvdMaskSize: 0
[    30.107]     RsvdFieldPosition: 0
[    30.107]     DirectColorModeInfo: 0
[    30.107]     PhysBasePtr: 0xe0000000
[    30.107]     LinBytesPerScanLine: 1280
[    30.107]     BnkNumberOfImagePages: 24
[    30.107]     LinNumberOfImagePages: 24
[    30.107]     LinRedMaskSize: 5
[    30.107]     LinRedFieldPosition: 11
[    30.107]     LinGreenMaskSize: 6
[    30.107]     LinGreenFieldPosition: 5
[    30.107]     LinBlueMaskSize: 5
[    30.107]     LinBlueFieldPosition: 0
[    30.107]     LinRsvdMaskSize: 0
[    30.107]     LinRsvdFieldPosition: 0
[    30.107]     MaxPixelClock: 400000000
[    30.107] Mode: 113 (800x600)
[    30.107]     ModeAttributes: 0xbb
[    30.107]     WinAAttributes: 0x7
[    30.107]     WinBAttributes: 0x0
[    30.107]     WinGranularity: 64
[    30.107]     WinSize: 64
[    30.107]     WinASegment: 0xa000
[    30.107]     WinBSegment: 0x0
[    30.107]     WinFuncPtr: 0xc000536d
[    30.107]     BytesPerScanline: 1600
[    30.107]     XResolution: 800
[    30.107]     YResolution: 600
[    30.107]     XCharSize: 8
[    30.107]     YCharSize: 14
[    30.107]     NumberOfPlanes: 1
[    30.107]     BitsPerPixel: 16
[    30.107]     NumberOfBanks: 1
[    30.108]     MemoryModel: 6
[    30.108]     BankSize: 0
[    30.108]     NumberOfImages: 16
[    30.108]     RedMaskSize: 5
[    30.108]     RedFieldPosition: 10
[    30.108]     GreenMaskSize: 5
[    30.108]     GreenFieldPosition: 5
[    30.108]     BlueMaskSize: 5
[    30.108]     BlueFieldPosition: 0
[    30.108]     RsvdMaskSize: 0
[    30.108]     RsvdFieldPosition: 0
[    30.108]     DirectColorModeInfo: 0
[    30.108]     PhysBasePtr: 0xe0000000
[    30.108]     LinBytesPerScanLine: 1600
[    30.108]     BnkNumberOfImagePages: 16
[    30.108]     LinNumberOfImagePages: 16
[    30.108]     LinRedMaskSize: 5
[    30.108]     LinRedFieldPosition: 10
[    30.108]     LinGreenMaskSize: 5
[    30.108]     LinGreenFieldPosition: 5
[    30.108]     LinBlueMaskSize: 5
[    30.108]     LinBlueFieldPosition: 0
[    30.108]     LinRsvdMaskSize: 0
[    30.108]     LinRsvdFieldPosition: 0
[    30.108]     MaxPixelClock: 400000000
[    30.108] Mode: 114 (800x600)
[    30.108]     ModeAttributes: 0xbb
[    30.108]     WinAAttributes: 0x7
[    30.108]     WinBAttributes: 0x0
[    30.108]     WinGranularity: 64
[    30.108]     WinSize: 64
[    30.108]     WinASegment: 0xa000
[    30.108]     WinBSegment: 0x0
[    30.108]     WinFuncPtr: 0xc000536d
[    30.108]     BytesPerScanline: 1600
[    30.108]     XResolution: 800
[    30.108]     YResolution: 600
[    30.108]     XCharSize: 8
[    30.108]     YCharSize: 14
[    30.108]     NumberOfPlanes: 1
[    30.108]     BitsPerPixel: 16
[    30.108]     NumberOfBanks: 1
[    30.108]     MemoryModel: 6
[    30.108]     BankSize: 0
[    30.108]     NumberOfImages: 16
[    30.108]     RedMaskSize: 5
[    30.108]     RedFieldPosition: 11
[    30.108]     GreenMaskSize: 6
[    30.108]     GreenFieldPosition: 5
[    30.108]     BlueMaskSize: 5
[    30.108]     BlueFieldPosition: 0
[    30.108]     RsvdMaskSize: 0
[    30.108]     RsvdFieldPosition: 0
[    30.108]     DirectColorModeInfo: 0
[    30.108]     PhysBasePtr: 0xe0000000
[    30.108]     LinBytesPerScanLine: 1600
[    30.108]     BnkNumberOfImagePages: 16
[    30.108]     LinNumberOfImagePages: 16
[    30.108]     LinRedMaskSize: 5
[    30.108]     LinRedFieldPosition: 11
[    30.108]     LinGreenMaskSize: 6
[    30.108]     LinGreenFieldPosition: 5
[    30.108]     LinBlueMaskSize: 5
[    30.108]     LinBlueFieldPosition: 0
[    30.108]     LinRsvdMaskSize: 0
[    30.108]     LinRsvdFieldPosition: 0
[    30.108]     MaxPixelClock: 400000000
[    30.108] Mode: 116 (1024x768)
[    30.108]     ModeAttributes: 0xbb
[    30.108]     WinAAttributes: 0x7
[    30.108]     WinBAttributes: 0x0
[    30.108]     WinGranularity: 64
[    30.108]     WinSize: 64
[    30.108]     WinASegment: 0xa000
[    30.108]     WinBSegment: 0x0
[    30.108]     WinFuncPtr: 0xc000536d
[    30.108]     BytesPerScanline: 2048
[    30.109]     XResolution: 1024
[    30.109]     YResolution: 768
[    30.109]     XCharSize: 8
[    30.109]     YCharSize: 16
[    30.109]     NumberOfPlanes: 1
[    30.109]     BitsPerPixel: 16
[    30.109]     NumberOfBanks: 1
[    30.109]     MemoryModel: 6
[    30.109]     BankSize: 0
[    30.109]     NumberOfImages: 9
[    30.109]     RedMaskSize: 5
[    30.109]     RedFieldPosition: 10
[    30.109]     GreenMaskSize: 5
[    30.109]     GreenFieldPosition: 5
[    30.109]     BlueMaskSize: 5
[    30.109]     BlueFieldPosition: 0
[    30.109]     RsvdMaskSize: 0
[    30.109]     RsvdFieldPosition: 0
[    30.109]     DirectColorModeInfo: 0
[    30.109]     PhysBasePtr: 0xe0000000
[    30.109]     LinBytesPerScanLine: 2048
[    30.109]     BnkNumberOfImagePages: 9
[    30.109]     LinNumberOfImagePages: 9
[    30.109]     LinRedMaskSize: 5
[    30.109]     LinRedFieldPosition: 10
[    30.109]     LinGreenMaskSize: 5
[    30.109]     LinGreenFieldPosition: 5
[    30.109]     LinBlueMaskSize: 5
[    30.109]     LinBlueFieldPosition: 0
[    30.109]     LinRsvdMaskSize: 0
[    30.109]     LinRsvdFieldPosition: 0
[    30.109]     MaxPixelClock: 400000000
[    30.109] Mode: 117 (1024x768)
[    30.109]     ModeAttributes: 0xbb
[    30.109]     WinAAttributes: 0x7
[    30.109]     WinBAttributes: 0x0
[    30.109]     WinGranularity: 64
[    30.109]     WinSize: 64
[    30.109]     WinASegment: 0xa000
[    30.109]     WinBSegment: 0x0
[    30.109]     WinFuncPtr: 0xc000536d
[    30.109]     BytesPerScanline: 2048
[    30.109]     XResolution: 1024
[    30.109]     YResolution: 768
[    30.109]     XCharSize: 8
[    30.109]     YCharSize: 16
[    30.109]     NumberOfPlanes: 1
[    30.109]     BitsPerPixel: 16
[    30.109]     NumberOfBanks: 1
[    30.109]     MemoryModel: 6
[    30.109]     BankSize: 0
[    30.109]     NumberOfImages: 9
[    30.109]     RedMaskSize: 5
[    30.109]     RedFieldPosition: 11
[    30.109]     GreenMaskSize: 6
[    30.109]     GreenFieldPosition: 5
[    30.109]     BlueMaskSize: 5
[    30.109]     BlueFieldPosition: 0
[    30.109]     RsvdMaskSize: 0
[    30.109]     RsvdFieldPosition: 0
[    30.109]     DirectColorModeInfo: 0
[    30.109]     PhysBasePtr: 0xe0000000
[    30.109]     LinBytesPerScanLine: 2048
[    30.109]     BnkNumberOfImagePages: 9
[    30.109]     LinNumberOfImagePages: 9
[    30.109]     LinRedMaskSize: 5
[    30.109]     LinRedFieldPosition: 11
[    30.109]     LinGreenMaskSize: 6
[    30.109]     LinGreenFieldPosition: 5
[    30.109]     LinBlueMaskSize: 5
[    30.109]     LinBlueFieldPosition: 0
[    30.109]     LinRsvdMaskSize: 0
[    30.109]     LinRsvdFieldPosition: 0
[    30.109]     MaxPixelClock: 400000000
[    30.109] Mode: 119 (1280x1024)
[    30.109]     ModeAttributes: 0xba
[    30.110]     WinAAttributes: 0x7
[    30.110]     WinBAttributes: 0x0
[    30.110]     WinGranularity: 64
[    30.110]     WinSize: 64
[    30.110]     WinASegment: 0xa000
[    30.110]     WinBSegment: 0x0
[    30.110]     WinFuncPtr: 0xc000536d
[    30.110]     BytesPerScanline: 2560
[    30.110]     XResolution: 1280
[    30.110]     YResolution: 1024
[    30.110]     XCharSize: 8
[    30.110]     YCharSize: 16
[    30.110]     NumberOfPlanes: 1
[    30.110]     BitsPerPixel: 16
[    30.110]     NumberOfBanks: 1
[    30.110]     MemoryModel: 6
[    30.110]     BankSize: 0
[    30.110]     NumberOfImages: 5
[    30.110]     RedMaskSize: 5
[    30.110]     RedFieldPosition: 10
[    30.110]     GreenMaskSize: 5
[    30.110]     GreenFieldPosition: 5
[    30.110]     BlueMaskSize: 5
[    30.110]     BlueFieldPosition: 0
[    30.110]     RsvdMaskSize: 0
[    30.110]     RsvdFieldPosition: 0
[    30.110]     DirectColorModeInfo: 0
[    30.110]     PhysBasePtr: 0xe0000000
[    30.110]     LinBytesPerScanLine: 2560
[    30.110]     BnkNumberOfImagePages: 5
[    30.110]     LinNumberOfImagePages: 5
[    30.110]     LinRedMaskSize: 5
[    30.110]     LinRedFieldPosition: 10
[    30.110]     LinGreenMaskSize: 5
[    30.110]     LinGreenFieldPosition: 5
[    30.110]     LinBlueMaskSize: 5
[    30.110]     LinBlueFieldPosition: 0
[    30.110]     LinRsvdMaskSize: 0
[    30.110]     LinRsvdFieldPosition: 0
[    30.110]     MaxPixelClock: 400000000
[    30.110] Mode: 11a (1280x1024)
[    30.110]     ModeAttributes: 0xba
[    30.110]     WinAAttributes: 0x7
[    30.110]     WinBAttributes: 0x0
[    30.110]     WinGranularity: 64
[    30.110]     WinSize: 64
[    30.110]     WinASegment: 0xa000
[    30.110]     WinBSegment: 0x0
[    30.110]     WinFuncPtr: 0xc000536d
[    30.110]     BytesPerScanline: 2560
[    30.110]     XResolution: 1280
[    30.110]     YResolution: 1024
[    30.110]     XCharSize: 8
[    30.110]     YCharSize: 16
[    30.110]     NumberOfPlanes: 1
[    30.110]     BitsPerPixel: 16
[    30.110]     NumberOfBanks: 1
[    30.110]     MemoryModel: 6
[    30.110]     BankSize: 0
[    30.110]     NumberOfImages: 5
[    30.110]     RedMaskSize: 5
[    30.110]     RedFieldPosition: 11
[    30.110]     GreenMaskSize: 6
[    30.110]     GreenFieldPosition: 5
[    30.110]     BlueMaskSize: 5
[    30.110]     BlueFieldPosition: 0
[    30.110]     RsvdMaskSize: 0
[    30.110]     RsvdFieldPosition: 0
[    30.110]     DirectColorModeInfo: 0
[    30.110]     PhysBasePtr: 0xe0000000
[    30.110]     LinBytesPerScanLine: 2560
[    30.110]     BnkNumberOfImagePages: 5
[    30.110]     LinNumberOfImagePages: 5
[    30.110]     LinRedMaskSize: 5
[    30.110]     LinRedFieldPosition: 11
[    30.110]     LinGreenMaskSize: 6
[    30.110]     LinGreenFieldPosition: 5
[    30.110]     LinBlueMaskSize: 5
[    30.110]     LinBlueFieldPosition: 0
[    30.110]     LinRsvdMaskSize: 0
[    30.110]     LinRsvdFieldPosition: 0
[    30.110]     MaxPixelClock: 400000000
[    30.111] Mode: 10d (320x200)
[    30.111]     ModeAttributes: 0xbb
[    30.111]     WinAAttributes: 0x7
[    30.111]     WinBAttributes: 0x0
[    30.111]     WinGranularity: 64
[    30.111]     WinSize: 64
[    30.111]     WinASegment: 0xa000
[    30.111]     WinBSegment: 0x0
[    30.111]     WinFuncPtr: 0xc000536d
[    30.111]     BytesPerScanline: 640
[    30.111]     XResolution: 320
[    30.111]     YResolution: 200
[    30.111]     XCharSize: 8
[    30.111]     YCharSize: 8
[    30.111]     NumberOfPlanes: 1
[    30.111]     BitsPerPixel: 16
[    30.111]     NumberOfBanks: 1
[    30.111]     MemoryModel: 6
[    30.111]     BankSize: 0
[    30.111]     NumberOfImages: 127
[    30.111]     RedMaskSize: 5
[    30.111]     RedFieldPosition: 10
[    30.111]     GreenMaskSize: 5
[    30.111]     GreenFieldPosition: 5
[    30.111]     BlueMaskSize: 5
[    30.111]     BlueFieldPosition: 0
[    30.111]     RsvdMaskSize: 0
[    30.111]     RsvdFieldPosition: 0
[    30.111]     DirectColorModeInfo: 0
[    30.111]     PhysBasePtr: 0xe0000000
[    30.111]     LinBytesPerScanLine: 640
[    30.111]     BnkNumberOfImagePages: 127
[    30.111]     LinNumberOfImagePages: 127
[    30.111]     LinRedMaskSize: 5
[    30.111]     LinRedFieldPosition: 10
[    30.111]     LinGreenMaskSize: 5
[    30.111]     LinGreenFieldPosition: 5
[    30.111]     LinBlueMaskSize: 5
[    30.111]     LinBlueFieldPosition: 0
[    30.111]     LinRsvdMaskSize: 0
[    30.111]     LinRsvdFieldPosition: 0
[    30.111]     MaxPixelClock: 400000000
[    30.111] Mode: 10e (320x200)
[    30.111]     ModeAttributes: 0xbb
[    30.111]     WinAAttributes: 0x7
[    30.111]     WinBAttributes: 0x0
[    30.111]     WinGranularity: 64
[    30.111]     WinSize: 64
[    30.111]     WinASegment: 0xa000
[    30.111]     WinBSegment: 0x0
[    30.111]     WinFuncPtr: 0xc000536d
[    30.111]     BytesPerScanline: 640
[    30.111]     XResolution: 320
[    30.111]     YResolution: 200
[    30.111]     XCharSize: 8
[    30.111]     YCharSize: 8
[    30.111]     NumberOfPlanes: 1
[    30.111]     BitsPerPixel: 16
[    30.111]     NumberOfBanks: 1
[    30.111]     MemoryModel: 6
[    30.111]     BankSize: 0
[    30.111]     NumberOfImages: 127
[    30.111]     RedMaskSize: 5
[    30.111]     RedFieldPosition: 11
[    30.111]     GreenMaskSize: 6
[    30.111]     GreenFieldPosition: 5
[    30.111]     BlueMaskSize: 5
[    30.111]     BlueFieldPosition: 0
[    30.111]     RsvdMaskSize: 0
[    30.111]     RsvdFieldPosition: 0
[    30.111]     DirectColorModeInfo: 0
[    30.111]     PhysBasePtr: 0xe0000000
[    30.111]     LinBytesPerScanLine: 640
[    30.111]     BnkNumberOfImagePages: 127
[    30.111]     LinNumberOfImagePages: 127
[    30.111]     LinRedMaskSize: 5
[    30.111]     LinRedFieldPosition: 11
[    30.111]     LinGreenMaskSize: 6
[    30.111]     LinGreenFieldPosition: 5
[    30.111]     LinBlueMaskSize: 5
[    30.111]     LinBlueFieldPosition: 0
[    30.111]     LinRsvdMaskSize: 0
[    30.111]     LinRsvdFieldPosition: 0
[    30.111]     MaxPixelClock: 400000000
[    30.112] *Mode: 120 (320x200)
[    30.112]     ModeAttributes: 0xbb
[    30.112]     WinAAttributes: 0x7
[    30.112]     WinBAttributes: 0x0
[    30.112]     WinGranularity: 64
[    30.112]     WinSize: 64
[    30.112]     WinASegment: 0xa000
[    30.112]     WinBSegment: 0x0
[    30.112]     WinFuncPtr: 0xc000536d
[    30.112]     BytesPerScanline: 1280
[    30.112]     XResolution: 320
[    30.112]     YResolution: 200
[    30.112]     XCharSize: 8
[    30.112]     YCharSize: 8
[    30.112]     NumberOfPlanes: 1
[    30.112]     BitsPerPixel: 32
[    30.112]     NumberOfBanks: 1
[    30.112]     MemoryModel: 6
[    30.112]     BankSize: 0
[    30.112]     NumberOfImages: 63
[    30.112]     RedMaskSize: 8
[    30.112]     RedFieldPosition: 16
[    30.112]     GreenMaskSize: 8
[    30.112]     GreenFieldPosition: 8
[    30.112]     BlueMaskSize: 8
[    30.112]     BlueFieldPosition: 0
[    30.112]     RsvdMaskSize: 0
[    30.112]     RsvdFieldPosition: 0
[    30.112]     DirectColorModeInfo: 0
[    30.112]     PhysBasePtr: 0xe0000000
[    30.112]     LinBytesPerScanLine: 1280
[    30.112]     BnkNumberOfImagePages: 63
[    30.112]     LinNumberOfImagePages: 63
[    30.112]     LinRedMaskSize: 8
[    30.112]     LinRedFieldPosition: 16
[    30.112]     LinGreenMaskSize: 8
[    30.112]     LinGreenFieldPosition: 8
[    30.112]     LinBlueMaskSize: 8
[    30.112]     LinBlueFieldPosition: 0
[    30.112]     LinRsvdMaskSize: 0
[    30.112]     LinRsvdFieldPosition: 0
[    30.112]     MaxPixelClock: 400000000
[    30.112] Mode: 193 (320x240)
[    30.112]     ModeAttributes: 0xbb
[    30.112]     WinAAttributes: 0x7
[    30.112]     WinBAttributes: 0x0
[    30.112]     WinGranularity: 64
[    30.112]     WinSize: 64
[    30.112]     WinASegment: 0xa000
[    30.112]     WinBSegment: 0x0
[    30.112]     WinFuncPtr: 0xc000536d
[    30.112]     BytesPerScanline: 320
[    30.112]     XResolution: 320
[    30.112]     YResolution: 240
[    30.112]     XCharSize: 8
[    30.112]     YCharSize: 8
[    30.112]     NumberOfPlanes: 1
[    30.112]     BitsPerPixel: 8
[    30.112]     NumberOfBanks: 1
[    30.112]     MemoryModel: 4
[    30.112]     BankSize: 0
[    30.112]     NumberOfImages: 127
[    30.112]     RedMaskSize: 0
[    30.112]     RedFieldPosition: 0
[    30.112]     GreenMaskSize: 0
[    30.112]     GreenFieldPosition: 0
[    30.112]     BlueMaskSize: 0
[    30.112]     BlueFieldPosition: 0
[    30.112]     RsvdMaskSize: 0
[    30.112]     RsvdFieldPosition: 0
[    30.112]     DirectColorModeInfo: 0
[    30.112]     PhysBasePtr: 0xe0000000
[    30.112]     LinBytesPerScanLine: 320
[    30.112]     BnkNumberOfImagePages: 127
[    30.112]     LinNumberOfImagePages: 127
[    30.112]     LinRedMaskSize: 0
[    30.112]     LinRedFieldPosition: 0
[    30.112]     LinGreenMaskSize: 0
[    30.112]     LinGreenFieldPosition: 0
[    30.112]     LinBlueMaskSize: 0
[    30.112]     LinBlueFieldPosition: 0
[    30.112]     LinRsvdMaskSize: 0
[    30.112]     LinRsvdFieldPosition: 0
[    30.112]     MaxPixelClock: 400000000
[    30.113] Mode: 195 (320x240)
[    30.113]     ModeAttributes: 0xbb
[    30.113]     WinAAttributes: 0x7
[    30.113]     WinBAttributes: 0x0
[    30.113]     WinGranularity: 64
[    30.113]     WinSize: 64
[    30.113]     WinASegment: 0xa000
[    30.113]     WinBSegment: 0x0
[    30.113]     WinFuncPtr: 0xc000536d
[    30.113]     BytesPerScanline: 640
[    30.113]     XResolution: 320
[    30.113]     YResolution: 240
[    30.113]     XCharSize: 8
[    30.113]     YCharSize: 8
[    30.113]     NumberOfPlanes: 1
[    30.113]     BitsPerPixel: 16
[    30.113]     NumberOfBanks: 1
[    30.113]     MemoryModel: 6
[    30.113]     BankSize: 0
[    30.113]     NumberOfImages: 84
[    30.113]     RedMaskSize: 5
[    30.113]     RedFieldPosition: 11
[    30.113]     GreenMaskSize: 6
[    30.113]     GreenFieldPosition: 5
[    30.113]     BlueMaskSize: 5
[    30.113]     BlueFieldPosition: 0
[    30.113]     RsvdMaskSize: 0
[    30.113]     RsvdFieldPosition: 0
[    30.113]     DirectColorModeInfo: 0
[    30.113]     PhysBasePtr: 0xe0000000
[    30.113]     LinBytesPerScanLine: 640
[    30.113]     BnkNumberOfImagePages: 84
[    30.113]     LinNumberOfImagePages: 84
[    30.113]     LinRedMaskSize: 5
[    30.113]     LinRedFieldPosition: 11
[    30.113]     LinGreenMaskSize: 6
[    30.113]     LinGreenFieldPosition: 5
[    30.113]     LinBlueMaskSize: 5
[    30.113]     LinBlueFieldPosition: 0
[    30.113]     LinRsvdMaskSize: 0
[    30.113]     LinRsvdFieldPosition: 0
[    30.113]     MaxPixelClock: 400000000
[    30.113] *Mode: 196 (320x240)
[    30.113]     ModeAttributes: 0xbb
[    30.113]     WinAAttributes: 0x7
[    30.113]     WinBAttributes: 0x0
[    30.113]     WinGranularity: 64
[    30.113]     WinSize: 64
[    30.113]     WinASegment: 0xa000
[    30.113]     WinBSegment: 0x0
[    30.113]     WinFuncPtr: 0xc000536d
[    30.113]     BytesPerScanline: 1280
[    30.113]     XResolution: 320
[    30.113]     YResolution: 240
[    30.113]     XCharSize: 8
[    30.113]     YCharSize: 8
[    30.113]     NumberOfPlanes: 1
[    30.113]     BitsPerPixel: 32
[    30.113]     NumberOfBanks: 1
[    30.113]     MemoryModel: 6
[    30.113]     BankSize: 0
[    30.113]     NumberOfImages: 50
[    30.113]     RedMaskSize: 8
[    30.113]     RedFieldPosition: 16
[    30.113]     GreenMaskSize: 8
[    30.113]     GreenFieldPosition: 8
[    30.113]     BlueMaskSize: 8
[    30.113]     BlueFieldPosition: 0
[    30.113]     RsvdMaskSize: 0
[    30.113]     RsvdFieldPosition: 0
[    30.113]     DirectColorModeInfo: 0
[    30.113]     PhysBasePtr: 0xe0000000
[    30.113]     LinBytesPerScanLine: 1280
[    30.113]     BnkNumberOfImagePages: 50
[    30.113]     LinNumberOfImagePages: 50
[    30.113]     LinRedMaskSize: 8
[    30.113]     LinRedFieldPosition: 16
[    30.113]     LinGreenMaskSize: 8
[    30.113]     LinGreenFieldPosition: 8
[    30.113]     LinBlueMaskSize: 8
[    30.113]     LinBlueFieldPosition: 0
[    30.113]     LinRsvdMaskSize: 0
[    30.113]     LinRsvdFieldPosition: 0
[    30.113]     MaxPixelClock: 400000000
[    30.114] Mode: 1b3 (512x384)
[    30.114]     ModeAttributes: 0xbb
[    30.114]     WinAAttributes: 0x7
[    30.114]     WinBAttributes: 0x0
[    30.114]     WinGranularity: 64
[    30.114]     WinSize: 64
[    30.114]     WinASegment: 0xa000
[    30.114]     WinBSegment: 0x0
[    30.114]     WinFuncPtr: 0xc000536d
[    30.114]     BytesPerScanline: 512
[    30.114]     XResolution: 512
[    30.114]     YResolution: 384
[    30.114]     XCharSize: 8
[    30.114]     YCharSize: 16
[    30.114]     NumberOfPlanes: 1
[    30.114]     BitsPerPixel: 8
[    30.114]     NumberOfBanks: 1
[    30.114]     MemoryModel: 4
[    30.114]     BankSize: 0
[    30.114]     NumberOfImages: 63
[    30.114]     RedMaskSize: 0
[    30.114]     RedFieldPosition: 0
[    30.114]     GreenMaskSize: 0
[    30.114]     GreenFieldPosition: 0
[    30.114]     BlueMaskSize: 0
[    30.114]     BlueFieldPosition: 0
[    30.114]     RsvdMaskSize: 0
[    30.114]     RsvdFieldPosition: 0
[    30.114]     DirectColorModeInfo: 0
[    30.114]     PhysBasePtr: 0xe0000000
[    30.114]     LinBytesPerScanLine: 512
[    30.114]     BnkNumberOfImagePages: 63
[    30.114]     LinNumberOfImagePages: 63
[    30.114]     LinRedMaskSize: 0
[    30.114]     LinRedFieldPosition: 0
[    30.114]     LinGreenMaskSize: 0
[    30.114]     LinGreenFieldPosition: 0
[    30.114]     LinBlueMaskSize: 0
[    30.114]     LinBlueFieldPosition: 0
[    30.114]     LinRsvdMaskSize: 0
[    30.114]     LinRsvdFieldPosition: 0
[    30.114]     MaxPixelClock: 400000000
[    30.114] Mode: 1b5 (512x384)
[    30.114]     ModeAttributes: 0xbb
[    30.114]     WinAAttributes: 0x7
[    30.114]     WinBAttributes: 0x0
[    30.114]     WinGranularity: 64
[    30.114]     WinSize: 64
[    30.114]     WinASegment: 0xa000
[    30.114]     WinBSegment: 0x0
[    30.114]     WinFuncPtr: 0xc000536d
[    30.114]     BytesPerScanline: 1024
[    30.114]     XResolution: 512
[    30.114]     YResolution: 384
[    30.114]     XCharSize: 8
[    30.114]     YCharSize: 16
[    30.114]     NumberOfPlanes: 1
[    30.114]     BitsPerPixel: 16
[    30.114]     NumberOfBanks: 1
[    30.114]     MemoryModel: 6
[    30.114]     BankSize: 0
[    30.114]     NumberOfImages: 35
[    30.114]     RedMaskSize: 5
[    30.114]     RedFieldPosition: 11
[    30.114]     GreenMaskSize: 6
[    30.114]     GreenFieldPosition: 5
[    30.114]     BlueMaskSize: 5
[    30.114]     BlueFieldPosition: 0
[    30.114]     RsvdMaskSize: 0
[    30.114]     RsvdFieldPosition: 0
[    30.114]     DirectColorModeInfo: 0
[    30.114]     PhysBasePtr: 0xe0000000
[    30.114]     LinBytesPerScanLine: 1024
[    30.114]     BnkNumberOfImagePages: 35
[    30.114]     LinNumberOfImagePages: 35
[    30.114]     LinRedMaskSize: 5
[    30.114]     LinRedFieldPosition: 11
[    30.114]     LinGreenMaskSize: 6
[    30.114]     LinGreenFieldPosition: 5
[    30.115]     LinBlueMaskSize: 5
[    30.115]     LinBlueFieldPosition: 0
[    30.115]     LinRsvdMaskSize: 0
[    30.115]     LinRsvdFieldPosition: 0
[    30.115]     MaxPixelClock: 400000000
[    30.115] *Mode: 1b6 (512x384)
[    30.115]     ModeAttributes: 0xbb
[    30.115]     WinAAttributes: 0x7
[    30.115]     WinBAttributes: 0x0
[    30.115]     WinGranularity: 64
[    30.115]     WinSize: 64
[    30.115]     WinASegment: 0xa000
[    30.115]     WinBSegment: 0x0
[    30.115]     WinFuncPtr: 0xc000536d
[    30.115]     BytesPerScanline: 2048
[    30.115]     XResolution: 512
[    30.115]     YResolution: 384
[    30.115]     XCharSize: 8
[    30.115]     YCharSize: 16
[    30.115]     NumberOfPlanes: 1
[    30.115]     BitsPerPixel: 32
[    30.115]     NumberOfBanks: 1
[    30.115]     MemoryModel: 6
[    30.115]     BankSize: 0
[    30.115]     NumberOfImages: 18
[    30.115]     RedMaskSize: 8
[    30.115]     RedFieldPosition: 16
[    30.115]     GreenMaskSize: 8
[    30.115]     GreenFieldPosition: 8
[    30.115]     BlueMaskSize: 8
[    30.115]     BlueFieldPosition: 0
[    30.115]     RsvdMaskSize: 0
[    30.115]     RsvdFieldPosition: 0
[    30.115]     DirectColorModeInfo: 0
[    30.115]     PhysBasePtr: 0xe0000000
[    30.115]     LinBytesPerScanLine: 2048
[    30.115]     BnkNumberOfImagePages: 18
[    30.115]     LinNumberOfImagePages: 18
[    30.115]     LinRedMaskSize: 8
[    30.115]     LinRedFieldPosition: 16
[    30.115]     LinGreenMaskSize: 8
[    30.115]     LinGreenFieldPosition: 8
[    30.115]     LinBlueMaskSize: 8
[    30.115]     LinBlueFieldPosition: 0
[    30.115]     LinRsvdMaskSize: 0
[    30.115]     LinRsvdFieldPosition: 0
[    30.115]     MaxPixelClock: 400000000
[    30.115] Mode: 1c3 (640x350)
[    30.115]     ModeAttributes: 0xbb
[    30.115]     WinAAttributes: 0x7
[    30.115]     WinBAttributes: 0x0
[    30.115]     WinGranularity: 64
[    30.115]     WinSize: 64
[    30.115]     WinASegment: 0xa000
[    30.115]     WinBSegment: 0x0
[    30.115]     WinFuncPtr: 0xc000536d
[    30.115]     BytesPerScanline: 640
[    30.115]     XResolution: 640
[    30.115]     YResolution: 350
[    30.115]     XCharSize: 8
[    30.115]     YCharSize: 14
[    30.115]     NumberOfPlanes: 1
[    30.115]     BitsPerPixel: 8
[    30.115]     NumberOfBanks: 1
[    30.115]     MemoryModel: 4
[    30.115]     BankSize: 0
[    30.115]     NumberOfImages: 63
[    30.115]     RedMaskSize: 0
[    30.115]     RedFieldPosition: 0
[    30.115]     GreenMaskSize: 0
[    30.115]     GreenFieldPosition: 0
[    30.115]     BlueMaskSize: 0
[    30.115]     BlueFieldPosition: 0
[    30.115]     RsvdMaskSize: 0
[    30.115]     RsvdFieldPosition: 0
[    30.116]     DirectColorModeInfo: 0
[    30.116]     PhysBasePtr: 0xe0000000
[    30.116]     LinBytesPerScanLine: 640
[    30.116]     BnkNumberOfImagePages: 63
[    30.116]     LinNumberOfImagePages: 63
[    30.116]     LinRedMaskSize: 0
[    30.116]     LinRedFieldPosition: 0
[    30.116]     LinGreenMaskSize: 0
[    30.116]     LinGreenFieldPosition: 0
[    30.116]     LinBlueMaskSize: 0
[    30.116]     LinBlueFieldPosition: 0
[    30.116]     LinRsvdMaskSize: 0
[    30.116]     LinRsvdFieldPosition: 0
[    30.116]     MaxPixelClock: 400000000
[    30.116] Mode: 1c5 (640x350)
[    30.116]     ModeAttributes: 0xbb
[    30.116]     WinAAttributes: 0x7
[    30.116]     WinBAttributes: 0x0
[    30.116]     WinGranularity: 64
[    30.116]     WinSize: 64
[    30.116]     WinASegment: 0xa000
[    30.116]     WinBSegment: 0x0
[    30.116]     WinFuncPtr: 0xc000536d
[    30.116]     BytesPerScanline: 1280
[    30.116]     XResolution: 640
[    30.116]     YResolution: 350
[    30.116]     XCharSize: 8
[    30.116]     YCharSize: 14
[    30.116]     NumberOfPlanes: 1
[    30.116]     BitsPerPixel: 16
[    30.116]     NumberOfBanks: 1
[    30.116]     MemoryModel: 6
[    30.116]     BankSize: 0
[    30.116]     NumberOfImages: 35
[    30.116]     RedMaskSize: 5
[    30.116]     RedFieldPosition: 11
[    30.116]     GreenMaskSize: 6
[    30.116]     GreenFieldPosition: 5
[    30.116]     BlueMaskSize: 5
[    30.116]     BlueFieldPosition: 0
[    30.116]     RsvdMaskSize: 0
[    30.116]     RsvdFieldPosition: 0
[    30.116]     DirectColorModeInfo: 0
[    30.116]     PhysBasePtr: 0xe0000000
[    30.116]     LinBytesPerScanLine: 1280
[    30.116]     BnkNumberOfImagePages: 35
[    30.116]     LinNumberOfImagePages: 35
[    30.116]     LinRedMaskSize: 5
[    30.116]     LinRedFieldPosition: 11
[    30.116]     LinGreenMaskSize: 6
[    30.116]     LinGreenFieldPosition: 5
[    30.116]     LinBlueMaskSize: 5
[    30.116]     LinBlueFieldPosition: 0
[    30.116]     LinRsvdMaskSize: 0
[    30.116]     LinRsvdFieldPosition: 0
[    30.116]     MaxPixelClock: 400000000
[    30.116] *Mode: 1c6 (640x350)
[    30.116]     ModeAttributes: 0xbb
[    30.116]     WinAAttributes: 0x7
[    30.116]     WinBAttributes: 0x0
[    30.116]     WinGranularity: 64
[    30.116]     WinSize: 64
[    30.116]     WinASegment: 0xa000
[    30.116]     WinBSegment: 0x0
[    30.116]     WinFuncPtr: 0xc000536d
[    30.116]     BytesPerScanline: 2560
[    30.116]     XResolution: 640
[    30.116]     YResolution: 350
[    30.116]     XCharSize: 8
[    30.116]     YCharSize: 14
[    30.116]     NumberOfPlanes: 1
[    30.116]     BitsPerPixel: 32
[    30.116]     NumberOfBanks: 1
[    30.116]     MemoryModel: 6
[    30.117]     BankSize: 0
[    30.117]     NumberOfImages: 17
[    30.117]     RedMaskSize: 8
[    30.117]     RedFieldPosition: 16
[    30.117]     GreenMaskSize: 8
[    30.117]     GreenFieldPosition: 8
[    30.117]     BlueMaskSize: 8
[    30.117]     BlueFieldPosition: 0
[    30.117]     RsvdMaskSize: 0
[    30.117]     RsvdFieldPosition: 0
[    30.117]     DirectColorModeInfo: 0
[    30.117]     PhysBasePtr: 0xe0000000
[    30.117]     LinBytesPerScanLine: 2560
[    30.117]     BnkNumberOfImagePages: 17
[    30.117]     LinNumberOfImagePages: 17
[    30.117]     LinRedMaskSize: 8
[    30.117]     LinRedFieldPosition: 16
[    30.117]     LinGreenMaskSize: 8
[    30.117]     LinGreenFieldPosition: 8
[    30.117]     LinBlueMaskSize: 8
[    30.117]     LinBlueFieldPosition: 0
[    30.117]     LinRsvdMaskSize: 0
[    30.117]     LinRsvdFieldPosition: 0
[    30.117]     MaxPixelClock: 400000000
[    30.117] Mode: 133 (720x400)
[    30.117]     ModeAttributes: 0xbb
[    30.117]     WinAAttributes: 0x7
[    30.117]     WinBAttributes: 0x0
[    30.117]     WinGranularity: 64
[    30.117]     WinSize: 64
[    30.117]     WinASegment: 0xa000
[    30.117]     WinBSegment: 0x0
[    30.117]     WinFuncPtr: 0xc000536d
[    30.117]     BytesPerScanline: 768
[    30.117]     XResolution: 720
[    30.117]     YResolution: 400
[    30.117]     XCharSize: 8
[    30.117]     YCharSize: 16
[    30.117]     NumberOfPlanes: 1
[    30.117]     BitsPerPixel: 8
[    30.117]     NumberOfBanks: 1
[    30.117]     MemoryModel: 4
[    30.117]     BankSize: 0
[    30.117]     NumberOfImages: 50
[    30.117]     RedMaskSize: 0
[    30.117]     RedFieldPosition: 0
[    30.117]     GreenMaskSize: 0
[    30.117]     GreenFieldPosition: 0
[    30.117]     BlueMaskSize: 0
[    30.117]     BlueFieldPosition: 0
[    30.117]     RsvdMaskSize: 0
[    30.117]     RsvdFieldPosition: 0
[    30.117]     DirectColorModeInfo: 0
[    30.117]     PhysBasePtr: 0xe0000000
[    30.117]     LinBytesPerScanLine: 768
[    30.117]     BnkNumberOfImagePages: 50
[    30.117]     LinNumberOfImagePages: 50
[    30.117]     LinRedMaskSize: 0
[    30.117]     LinRedFieldPosition: 0
[    30.117]     LinGreenMaskSize: 0
[    30.117]     LinGreenFieldPosition: 0
[    30.117]     LinBlueMaskSize: 0
[    30.117]     LinBlueFieldPosition: 0
[    30.117]     LinRsvdMaskSize: 0
[    30.117]     LinRsvdFieldPosition: 0
[    30.117]     MaxPixelClock: 400000000
[    30.117] Mode: 135 (720x400)
[    30.117]     ModeAttributes: 0xbb
[    30.117]     WinAAttributes: 0x7
[    30.117]     WinBAttributes: 0x0
[    30.117]     WinGranularity: 64
[    30.117]     WinSize: 64
[    30.117]     WinASegment: 0xa000
[    30.117]     WinBSegment: 0x0
[    30.117]     WinFuncPtr: 0xc000536d
[    30.117]     BytesPerScanline: 1472
[    30.118]     XResolution: 720
[    30.118]     YResolution: 400
[    30.118]     XCharSize: 8
[    30.118]     YCharSize: 16
[    30.118]     NumberOfPlanes: 1
[    30.118]     BitsPerPixel: 16
[    30.118]     NumberOfBanks: 1
[    30.118]     MemoryModel: 6
[    30.118]     BankSize: 0
[    30.118]     NumberOfImages: 27
[    30.118]     RedMaskSize: 5
[    30.118]     RedFieldPosition: 11
[    30.118]     GreenMaskSize: 6
[    30.118]     GreenFieldPosition: 5
[    30.118]     BlueMaskSize: 5
[    30.118]     BlueFieldPosition: 0
[    30.118]     RsvdMaskSize: 0
[    30.118]     RsvdFieldPosition: 0
[    30.118]     DirectColorModeInfo: 0
[    30.118]     PhysBasePtr: 0xe0000000
[    30.118]     LinBytesPerScanLine: 1472
[    30.118]     BnkNumberOfImagePages: 27
[    30.118]     LinNumberOfImagePages: 27
[    30.118]     LinRedMaskSize: 5
[    30.118]     LinRedFieldPosition: 11
[    30.118]     LinGreenMaskSize: 6
[    30.118]     LinGreenFieldPosition: 5
[    30.118]     LinBlueMaskSize: 5
[    30.118]     LinBlueFieldPosition: 0
[    30.118]     LinRsvdMaskSize: 0
[    30.118]     LinRsvdFieldPosition: 0
[    30.118]     MaxPixelClock: 400000000
[    30.118] *Mode: 136 (720x400)
[    30.118]     ModeAttributes: 0xbb
[    30.118]     WinAAttributes: 0x7
[    30.118]     WinBAttributes: 0x0
[    30.118]     WinGranularity: 64
[    30.118]     WinSize: 64
[    30.118]     WinASegment: 0xa000
[    30.118]     WinBSegment: 0x0
[    30.118]     WinFuncPtr: 0xc000536d
[    30.118]     BytesPerScanline: 2944
[    30.118]     XResolution: 720
[    30.118]     YResolution: 400
[    30.118]     XCharSize: 8
[    30.118]     YCharSize: 16
[    30.118]     NumberOfPlanes: 1
[    30.118]     BitsPerPixel: 32
[    30.118]     NumberOfBanks: 1
[    30.118]     MemoryModel: 6
[    30.118]     BankSize: 0
[    30.118]     NumberOfImages: 13
[    30.118]     RedMaskSize: 8
[    30.118]     RedFieldPosition: 16
[    30.118]     GreenMaskSize: 8
[    30.118]     GreenFieldPosition: 8
[    30.118]     BlueMaskSize: 8
[    30.118]     BlueFieldPosition: 0
[    30.118]     RsvdMaskSize: 0
[    30.118]     RsvdFieldPosition: 0
[    30.118]     DirectColorModeInfo: 0
[    30.118]     PhysBasePtr: 0xe0000000
[    30.118]     LinBytesPerScanLine: 2944
[    30.118]     BnkNumberOfImagePages: 13
[    30.118]     LinNumberOfImagePages: 13
[    30.118]     LinRedMaskSize: 8
[    30.118]     LinRedFieldPosition: 16
[    30.118]     LinGreenMaskSize: 8
[    30.118]     LinGreenFieldPosition: 8
[    30.118]     LinBlueMaskSize: 8
[    30.118]     LinBlueFieldPosition: 0
[    30.118]     LinRsvdMaskSize: 0
[    30.118]     LinRsvdFieldPosition: 0
[    30.118]     MaxPixelClock: 400000000
[    30.119] Mode: 153 (1152x864)
[    30.119]     ModeAttributes: 0xba
[    30.119]     WinAAttributes: 0x7
[    30.119]     WinBAttributes: 0x0
[    30.119]     WinGranularity: 64
[    30.119]     WinSize: 64
[    30.119]     WinASegment: 0xa000
[    30.119]     WinBSegment: 0x0
[    30.119]     WinFuncPtr: 0xc000536d
[    30.119]     BytesPerScanline: 1152
[    30.119]     XResolution: 1152
[    30.119]     YResolution: 864
[    30.119]     XCharSize: 8
[    30.119]     YCharSize: 16
[    30.119]     NumberOfPlanes: 1
[    30.119]     BitsPerPixel: 8
[    30.119]     NumberOfBanks: 1
[    30.119]     MemoryModel: 4
[    30.119]     BankSize: 0
[    30.119]     NumberOfImages: 15
[    30.119]     RedMaskSize: 0
[    30.119]     RedFieldPosition: 0
[    30.119]     GreenMaskSize: 0
[    30.119]     GreenFieldPosition: 0
[    30.119]     BlueMaskSize: 0
[    30.119]     BlueFieldPosition: 0
[    30.119]     RsvdMaskSize: 0
[    30.119]     RsvdFieldPosition: 0
[    30.119]     DirectColorModeInfo: 0
[    30.119]     PhysBasePtr: 0xe0000000
[    30.119]     LinBytesPerScanLine: 1152
[    30.119]     BnkNumberOfImagePages: 15
[    30.119]     LinNumberOfImagePages: 15
[    30.119]     LinRedMaskSize: 0
[    30.119]     LinRedFieldPosition: 0
[    30.119]     LinGreenMaskSize: 0
[    30.119]     LinGreenFieldPosition: 0
[    30.119]     LinBlueMaskSize: 0
[    30.119]     LinBlueFieldPosition: 0
[    30.119]     LinRsvdMaskSize: 0
[    30.119]     LinRsvdFieldPosition: 0
[    30.119]     MaxPixelClock: 400000000
[    30.119] Mode: 155 (1152x864)
[    30.119]     ModeAttributes: 0xba
[    30.119]     WinAAttributes: 0x7
[    30.119]     WinBAttributes: 0x0
[    30.119]     WinGranularity: 64
[    30.119]     WinSize: 64
[    30.119]     WinASegment: 0xa000
[    30.119]     WinBSegment: 0x0
[    30.119]     WinFuncPtr: 0xc000536d
[    30.119]     BytesPerScanline: 2304
[    30.119]     XResolution: 1152
[    30.119]     YResolution: 864
[    30.119]     XCharSize: 8
[    30.119]     YCharSize: 16
[    30.119]     NumberOfPlanes: 1
[    30.119]     BitsPerPixel: 16
[    30.119]     NumberOfBanks: 1
[    30.119]     MemoryModel: 6
[    30.119]     BankSize: 0
[    30.119]     NumberOfImages: 7
[    30.119]     RedMaskSize: 5
[    30.119]     RedFieldPosition: 11
[    30.119]     GreenMaskSize: 6
[    30.119]     GreenFieldPosition: 5
[    30.119]     BlueMaskSize: 5
[    30.119]     BlueFieldPosition: 0
[    30.119]     RsvdMaskSize: 0
[    30.119]     RsvdFieldPosition: 0
[    30.119]     DirectColorModeInfo: 0
[    30.119]     PhysBasePtr: 0xe0000000
[    30.119]     LinBytesPerScanLine: 2304
[    30.119]     BnkNumberOfImagePages: 7
[    30.119]     LinNumberOfImagePages: 7
[    30.119]     LinRedMaskSize: 5
[    30.119]     LinRedFieldPosition: 11
[    30.119]     LinGreenMaskSize: 6
[    30.119]     LinGreenFieldPosition: 5
[    30.119]     LinBlueMaskSize: 5
[    30.119]     LinBlueFieldPosition: 0
[    30.119]     LinRsvdMaskSize: 0
[    30.119]     LinRsvdFieldPosition: 0
[    30.119]     MaxPixelClock: 400000000
[    30.120] Mode: 156 (1152x864)
[    30.120]     ModeAttributes: 0xba
[    30.120]     WinAAttributes: 0x7
[    30.120]     WinBAttributes: 0x0
[    30.120]     WinGranularity: 64
[    30.120]     WinSize: 64
[    30.120]     WinASegment: 0xa000
[    30.120]     WinBSegment: 0x0
[    30.120]     WinFuncPtr: 0xc000536d
[    30.120]     BytesPerScanline: 4608
[    30.120]     XResolution: 1152
[    30.120]     YResolution: 864
[    30.120]     XCharSize: 8
[    30.120]     YCharSize: 16
[    30.120]     NumberOfPlanes: 1
[    30.120]     BitsPerPixel: 32
[    30.120]     NumberOfBanks: 1
[    30.120]     MemoryModel: 6
[    30.120]     BankSize: 0
[    30.120]     NumberOfImages: 3
[    30.120]     RedMaskSize: 8
[    30.120]     RedFieldPosition: 16
[    30.120]     GreenMaskSize: 8
[    30.120]     GreenFieldPosition: 8
[    30.120]     BlueMaskSize: 8
[    30.120]     BlueFieldPosition: 0
[    30.120]     RsvdMaskSize: 0
[    30.120]     RsvdFieldPosition: 0
[    30.120]     DirectColorModeInfo: 0
[    30.120]     PhysBasePtr: 0xe0000000
[    30.120]     LinBytesPerScanLine: 4608
[    30.120]     BnkNumberOfImagePages: 3
[    30.120]     LinNumberOfImagePages: 3
[    30.120]     LinRedMaskSize: 8
[    30.120]     LinRedFieldPosition: 16
[    30.120]     LinGreenMaskSize: 8
[    30.120]     LinGreenFieldPosition: 8
[    30.120]     LinBlueMaskSize: 8
[    30.120]     LinBlueFieldPosition: 0
[    30.120]     LinRsvdMaskSize: 0
[    30.120]     LinRsvdFieldPosition: 0
[    30.120]     MaxPixelClock: 400000000
[    30.120] Mode: 163 (1280x960)
[    30.120]     ModeAttributes: 0xba
[    30.120]     WinAAttributes: 0x7
[    30.120]     WinBAttributes: 0x0
[    30.120]     WinGranularity: 64
[    30.120]     WinSize: 64
[    30.120]     WinASegment: 0xa000
[    30.120]     WinBSegment: 0x0
[    30.120]     WinFuncPtr: 0xc000536d
[    30.120]     BytesPerScanline: 1280
[    30.120]     XResolution: 1280
[    30.120]     YResolution: 960
[    30.120]     XCharSize: 8
[    30.120]     YCharSize: 16
[    30.120]     NumberOfPlanes: 1
[    30.120]     BitsPerPixel: 8
[    30.120]     NumberOfBanks: 1
[    30.120]     MemoryModel: 4
[    30.120]     BankSize: 0
[    30.120]     NumberOfImages: 12
[    30.120]     RedMaskSize: 0
[    30.120]     RedFieldPosition: 0
[    30.120]     GreenMaskSize: 0
[    30.120]     GreenFieldPosition: 0
[    30.120]     BlueMaskSize: 0
[    30.120]     BlueFieldPosition: 0
[    30.120]     RsvdMaskSize: 0
[    30.120]     RsvdFieldPosition: 0
[    30.120]     DirectColorModeInfo: 0
[    30.120]     PhysBasePtr: 0xe0000000
[    30.120]     LinBytesPerScanLine: 1280
[    30.120]     BnkNumberOfImagePages: 12
[    30.120]     LinNumberOfImagePages: 12
[    30.120]     LinRedMaskSize: 0
[    30.120]     LinRedFieldPosition: 0
[    30.120]     LinGreenMaskSize: 0
[    30.120]     LinGreenFieldPosition: 0
[    30.120]     LinBlueMaskSize: 0
[    30.120]     LinBlueFieldPosition: 0
[    30.120]     LinRsvdMaskSize: 0
[    30.120]     LinRsvdFieldPosition: 0
[    30.120]     MaxPixelClock: 400000000
[    30.121] Mode: 165 (1280x960)
[    30.121]     ModeAttributes: 0xba
[    30.121]     WinAAttributes: 0x7
[    30.121]     WinBAttributes: 0x0
[    30.121]     WinGranularity: 64
[    30.121]     WinSize: 64
[    30.121]     WinASegment: 0xa000
[    30.121]     WinBSegment: 0x0
[    30.121]     WinFuncPtr: 0xc000536d
[    30.121]     BytesPerScanline: 2560
[    30.121]     XResolution: 1280
[    30.121]     YResolution: 960
[    30.121]     XCharSize: 8
[    30.121]     YCharSize: 16
[    30.121]     NumberOfPlanes: 1
[    30.121]     BitsPerPixel: 16
[    30.121]     NumberOfBanks: 1
[    30.121]     MemoryModel: 6
[    30.121]     BankSize: 0
[    30.121]     NumberOfImages: 5
[    30.121]     RedMaskSize: 5
[    30.121]     RedFieldPosition: 11
[    30.121]     GreenMaskSize: 6
[    30.121]     GreenFieldPosition: 5
[    30.121]     BlueMaskSize: 5
[    30.121]     BlueFieldPosition: 0
[    30.121]     RsvdMaskSize: 0
[    30.121]     RsvdFieldPosition: 0
[    30.121]     DirectColorModeInfo: 0
[    30.121]     PhysBasePtr: 0xe0000000
[    30.121]     LinBytesPerScanLine: 2560
[    30.121]     BnkNumberOfImagePages: 5
[    30.121]     LinNumberOfImagePages: 5
[    30.121]     LinRedMaskSize: 5
[    30.121]     LinRedFieldPosition: 11
[    30.121]     LinGreenMaskSize: 6
[    30.121]     LinGreenFieldPosition: 5
[    30.121]     LinBlueMaskSize: 5
[    30.121]     LinBlueFieldPosition: 0
[    30.121]     LinRsvdMaskSize: 0
[    30.121]     LinRsvdFieldPosition: 0
[    30.121]     MaxPixelClock: 400000000
[    30.121] Mode: 166 (1280x960)
[    30.121]     ModeAttributes: 0xba
[    30.121]     WinAAttributes: 0x7
[    30.121]     WinBAttributes: 0x0
[    30.121]     WinGranularity: 64
[    30.121]     WinSize: 64
[    30.121]     WinASegment: 0xa000
[    30.121]     WinBSegment: 0x0
[    30.121]     WinFuncPtr: 0xc000536d
[    30.121]     BytesPerScanline: 5120
[    30.121]     XResolution: 1280
[    30.121]     YResolution: 960
[    30.121]     XCharSize: 8
[    30.121]     YCharSize: 16
[    30.121]     NumberOfPlanes: 1
[    30.121]     BitsPerPixel: 32
[    30.121]     NumberOfBanks: 1
[    30.121]     MemoryModel: 6
[    30.121]     BankSize: 0
[    30.121]     NumberOfImages: 2
[    30.121]     RedMaskSize: 8
[    30.121]     RedFieldPosition: 16
[    30.121]     GreenMaskSize: 8
[    30.121]     GreenFieldPosition: 8
[    30.121]     BlueMaskSize: 8
[    30.121]     BlueFieldPosition: 0
[    30.121]     RsvdMaskSize: 0
[    30.121]     RsvdFieldPosition: 0
[    30.121]     DirectColorModeInfo: 0
[    30.121]     PhysBasePtr: 0xe0000000
[    30.121]     LinBytesPerScanLine: 5120
[    30.121]     BnkNumberOfImagePages: 2
[    30.121]     LinNumberOfImagePages: 2
[    30.121]     LinRedMaskSize: 8
[    30.121]     LinRedFieldPosition: 16
[    30.121]     LinGreenMaskSize: 8
[    30.121]     LinGreenFieldPosition: 8
[    30.121]     LinBlueMaskSize: 8
[    30.121]     LinBlueFieldPosition: 0
[    30.122]     LinRsvdMaskSize: 0
[    30.122]     LinRsvdFieldPosition: 0
[    30.122]     MaxPixelClock: 400000000
[    30.122] *Mode: 121 (640x480)
[    30.122]     ModeAttributes: 0xbb
[    30.122]     WinAAttributes: 0x7
[    30.122]     WinBAttributes: 0x0
[    30.122]     WinGranularity: 64
[    30.122]     WinSize: 64
[    30.122]     WinASegment: 0xa000
[    30.122]     WinBSegment: 0x0
[    30.122]     WinFuncPtr: 0xc000536d
[    30.122]     BytesPerScanline: 2560
[    30.122]     XResolution: 640
[    30.122]     YResolution: 480
[    30.122]     XCharSize: 8
[    30.122]     YCharSize: 16
[    30.122]     NumberOfPlanes: 1
[    30.122]     BitsPerPixel: 32
[    30.122]     NumberOfBanks: 1
[    30.122]     MemoryModel: 6
[    30.122]     BankSize: 0
[    30.122]     NumberOfImages: 12
[    30.122]     RedMaskSize: 8
[    30.122]     RedFieldPosition: 16
[    30.122]     GreenMaskSize: 8
[    30.122]     GreenFieldPosition: 8
[    30.122]     BlueMaskSize: 8
[    30.122]     BlueFieldPosition: 0
[    30.122]     RsvdMaskSize: 0
[    30.122]     RsvdFieldPosition: 0
[    30.122]     DirectColorModeInfo: 0
[    30.122]     PhysBasePtr: 0xe0000000
[    30.122]     LinBytesPerScanLine: 2560
[    30.122]     BnkNumberOfImagePages: 12
[    30.122]     LinNumberOfImagePages: 12
[    30.122]     LinRedMaskSize: 8
[    30.122]     LinRedFieldPosition: 16
[    30.122]     LinGreenMaskSize: 8
[    30.122]     LinGreenFieldPosition: 8
[    30.122]     LinBlueMaskSize: 8
[    30.122]     LinBlueFieldPosition: 0
[    30.122]     LinRsvdMaskSize: 0
[    30.122]     LinRsvdFieldPosition: 0
[    30.122]     MaxPixelClock: 400000000
[    30.122] *Mode: 122 (800x600)
[    30.122]     ModeAttributes: 0xbb
[    30.122]     WinAAttributes: 0x7
[    30.122]     WinBAttributes: 0x0
[    30.122]     WinGranularity: 64
[    30.122]     WinSize: 64
[    30.122]     WinASegment: 0xa000
[    30.122]     WinBSegment: 0x0
[    30.122]     WinFuncPtr: 0xc000536d
[    30.122]     BytesPerScanline: 3200
[    30.122]     XResolution: 800
[    30.122]     YResolution: 600
[    30.122]     XCharSize: 8
[    30.122]     YCharSize: 14
[    30.122]     NumberOfPlanes: 1
[    30.122]     BitsPerPixel: 32
[    30.122]     NumberOfBanks: 1
[    30.122]     MemoryModel: 6
[    30.122]     BankSize: 0
[    30.122]     NumberOfImages: 7
[    30.122]     RedMaskSize: 8
[    30.122]     RedFieldPosition: 16
[    30.122]     GreenMaskSize: 8
[    30.122]     GreenFieldPosition: 8
[    30.122]     BlueMaskSize: 8
[    30.122]     BlueFieldPosition: 0
[    30.122]     RsvdMaskSize: 0
[    30.123]     RsvdFieldPosition: 0
[    30.123]     DirectColorModeInfo: 0
[    30.123]     PhysBasePtr: 0xe0000000
[    30.123]     LinBytesPerScanLine: 3200
[    30.123]     BnkNumberOfImagePages: 7
[    30.123]     LinNumberOfImagePages: 7
[    30.123]     LinRedMaskSize: 8
[    30.123]     LinRedFieldPosition: 16
[    30.123]     LinGreenMaskSize: 8
[    30.123]     LinGreenFieldPosition: 8
[    30.123]     LinBlueMaskSize: 8
[    30.123]     LinBlueFieldPosition: 0
[    30.123]     LinRsvdMaskSize: 0
[    30.123]     LinRsvdFieldPosition: 0
[    30.123]     MaxPixelClock: 400000000
[    30.123] *Mode: 123 (1024x768)
[    30.123]     ModeAttributes: 0xbb
[    30.123]     WinAAttributes: 0x7
[    30.123]     WinBAttributes: 0x0
[    30.123]     WinGranularity: 64
[    30.123]     WinSize: 64
[    30.123]     WinASegment: 0xa000
[    30.123]     WinBSegment: 0x0
[    30.123]     WinFuncPtr: 0xc000536d
[    30.123]     BytesPerScanline: 4096
[    30.123]     XResolution: 1024
[    30.123]     YResolution: 768
[    30.123]     XCharSize: 8
[    30.123]     YCharSize: 16
[    30.123]     NumberOfPlanes: 1
[    30.123]     BitsPerPixel: 32
[    30.123]     NumberOfBanks: 1
[    30.123]     MemoryModel: 6
[    30.123]     BankSize: 0
[    30.123]     NumberOfImages: 4
[    30.123]     RedMaskSize: 8
[    30.123]     RedFieldPosition: 16
[    30.123]     GreenMaskSize: 8
[    30.123]     GreenFieldPosition: 8
[    30.123]     BlueMaskSize: 8
[    30.123]     BlueFieldPosition: 0
[    30.123]     RsvdMaskSize: 0
[    30.123]     RsvdFieldPosition: 0
[    30.123]     DirectColorModeInfo: 0
[    30.123]     PhysBasePtr: 0xe0000000
[    30.123]     LinBytesPerScanLine: 4096
[    30.123]     BnkNumberOfImagePages: 4
[    30.123]     LinNumberOfImagePages: 4
[    30.123]     LinRedMaskSize: 8
[    30.123]     LinRedFieldPosition: 16
[    30.123]     LinGreenMaskSize: 8
[    30.123]     LinGreenFieldPosition: 8
[    30.123]     LinBlueMaskSize: 8
[    30.123]     LinBlueFieldPosition: 0
[    30.123]     LinRsvdMaskSize: 0
[    30.123]     LinRsvdFieldPosition: 0
[    30.123]     MaxPixelClock: 400000000
[    30.123] Mode: 124 (1280x1024)
[    30.123]     ModeAttributes: 0xba
[    30.123]     WinAAttributes: 0x7
[    30.123]     WinBAttributes: 0x0
[    30.123]     WinGranularity: 64
[    30.123]     WinSize: 64
[    30.123]     WinASegment: 0xa000
[    30.123]     WinBSegment: 0x0
[    30.123]     WinFuncPtr: 0xc000536d
[    30.123]     BytesPerScanline: 5120
[    30.123]     XResolution: 1280
[    30.123]     YResolution: 1024
[    30.123]     XCharSize: 8
[    30.123]     YCharSize: 16
[    30.124]     NumberOfPlanes: 1
[    30.124]     BitsPerPixel: 32
[    30.124]     NumberOfBanks: 1
[    30.124]     MemoryModel: 6
[    30.124]     BankSize: 0
[    30.124]     NumberOfImages: 2
[    30.124]     RedMaskSize: 8
[    30.124]     RedFieldPosition: 16
[    30.124]     GreenMaskSize: 8
[    30.124]     GreenFieldPosition: 8
[    30.124]     BlueMaskSize: 8
[    30.124]     BlueFieldPosition: 0
[    30.124]     RsvdMaskSize: 0
[    30.124]     RsvdFieldPosition: 0
[    30.124]     DirectColorModeInfo: 0
[    30.124]     PhysBasePtr: 0xe0000000
[    30.124]     LinBytesPerScanLine: 5120
[    30.124]     BnkNumberOfImagePages: 2
[    30.124]     LinNumberOfImagePages: 2
[    30.124]     LinRedMaskSize: 8
[    30.124]     LinRedFieldPosition: 16
[    30.124]     LinGreenMaskSize: 8
[    30.124]     LinGreenFieldPosition: 8
[    30.124]     LinBlueMaskSize: 8
[    30.124]     LinBlueFieldPosition: 0
[    30.124]     LinRsvdMaskSize: 0
[    30.124]     LinRsvdFieldPosition: 0
[    30.124]     MaxPixelClock: 400000000
[    30.124] Mode: 143 (1400x1050)
[    30.124]     ModeAttributes: 0xba
[    30.124]     WinAAttributes: 0x7
[    30.124]     WinBAttributes: 0x0
[    30.124]     WinGranularity: 64
[    30.124]     WinSize: 64
[    30.124]     WinASegment: 0xa000
[    30.124]     WinBSegment: 0x0
[    30.124]     WinFuncPtr: 0xc000536d
[    30.124]     BytesPerScanline: 1408
[    30.124]     XResolution: 1400
[    30.124]     YResolution: 1050
[    30.124]     XCharSize: 8
[    30.124]     YCharSize: 16
[    30.124]     NumberOfPlanes: 1
[    30.124]     BitsPerPixel: 8
[    30.124]     NumberOfBanks: 1
[    30.124]     MemoryModel: 4
[    30.124]     BankSize: 0
[    30.124]     NumberOfImages: 10
[    30.124]     RedMaskSize: 0
[    30.124]     RedFieldPosition: 0
[    30.124]     GreenMaskSize: 0
[    30.124]     GreenFieldPosition: 0
[    30.124]     BlueMaskSize: 0
[    30.124]     BlueFieldPosition: 0
[    30.124]     RsvdMaskSize: 0
[    30.124]     RsvdFieldPosition: 0
[    30.124]     DirectColorModeInfo: 0
[    30.124]     PhysBasePtr: 0xe0000000
[    30.124]     LinBytesPerScanLine: 1408
[    30.124]     BnkNumberOfImagePages: 10
[    30.124]     LinNumberOfImagePages: 10
[    30.124]     LinRedMaskSize: 0
[    30.124]     LinRedFieldPosition: 0
[    30.124]     LinGreenMaskSize: 0
[    30.124]     LinGreenFieldPosition: 0
[    30.124]     LinBlueMaskSize: 0
[    30.124]     LinBlueFieldPosition: 0
[    30.124]     LinRsvdMaskSize: 0
[    30.124]     LinRsvdFieldPosition: 0
[    30.124]     MaxPixelClock: 400000000
[    30.124] Mode: 145 (1400x1050)
[    30.125]     ModeAttributes: 0xba
[    30.125]     WinAAttributes: 0x7
[    30.125]     WinBAttributes: 0x0
[    30.125]     WinGranularity: 64
[    30.125]     WinSize: 64
[    30.125]     WinASegment: 0xa000
[    30.125]     WinBSegment: 0x0
[    30.125]     WinFuncPtr: 0xc000536d
[    30.125]     BytesPerScanline: 2816
[    30.125]     XResolution: 1400
[    30.125]     YResolution: 1050
[    30.125]     XCharSize: 8
[    30.125]     YCharSize: 16
[    30.125]     NumberOfPlanes: 1
[    30.125]     BitsPerPixel: 16
[    30.125]     NumberOfBanks: 1
[    30.125]     MemoryModel: 6
[    30.125]     BankSize: 0
[    30.125]     NumberOfImages: 4
[    30.125]     RedMaskSize: 5
[    30.125]     RedFieldPosition: 11
[    30.125]     GreenMaskSize: 6
[    30.125]     GreenFieldPosition: 5
[    30.125]     BlueMaskSize: 5
[    30.125]     BlueFieldPosition: 0
[    30.125]     RsvdMaskSize: 0
[    30.125]     RsvdFieldPosition: 0
[    30.125]     DirectColorModeInfo: 0
[    30.125]     PhysBasePtr: 0xe0000000
[    30.125]     LinBytesPerScanLine: 2816
[    30.125]     BnkNumberOfImagePages: 4
[    30.125]     LinNumberOfImagePages: 4
[    30.125]     LinRedMaskSize: 5
[    30.125]     LinRedFieldPosition: 11
[    30.125]     LinGreenMaskSize: 6
[    30.125]     LinGreenFieldPosition: 5
[    30.125]     LinBlueMaskSize: 5
[    30.125]     LinBlueFieldPosition: 0
[    30.125]     LinRsvdMaskSize: 0
[    30.125]     LinRsvdFieldPosition: 0
[    30.125]     MaxPixelClock: 400000000
[    30.125] Mode: 146 (1400x1050)
[    30.125]     ModeAttributes: 0xba
[    30.125]     WinAAttributes: 0x7
[    30.125]     WinBAttributes: 0x0
[    30.125]     WinGranularity: 64
[    30.125]     WinSize: 64
[    30.125]     WinASegment: 0xa000
[    30.125]     WinBSegment: 0x0
[    30.125]     WinFuncPtr: 0xc000536d
[    30.125]     BytesPerScanline: 5632
[    30.125]     XResolution: 1400
[    30.125]     YResolution: 1050
[    30.125]     XCharSize: 8
[    30.125]     YCharSize: 16
[    30.125]     NumberOfPlanes: 1
[    30.125]     BitsPerPixel: 32
[    30.125]     NumberOfBanks: 1
[    30.125]     MemoryModel: 6
[    30.125]     BankSize: 0
[    30.125]     NumberOfImages: 1
[    30.125]     RedMaskSize: 8
[    30.125]     RedFieldPosition: 16
[    30.125]     GreenMaskSize: 8
[    30.125]     GreenFieldPosition: 8
[    30.125]     BlueMaskSize: 8
[    30.125]     BlueFieldPosition: 0
[    30.125]     RsvdMaskSize: 0
[    30.125]     RsvdFieldPosition: 0
[    30.125]     DirectColorModeInfo: 0
[    30.125]     PhysBasePtr: 0xe0000000
[    30.125]     LinBytesPerScanLine: 5632
[    30.125]     BnkNumberOfImagePages: 1
[    30.125]     LinNumberOfImagePages: 1
[    30.125]     LinRedMaskSize: 8
[    30.125]     LinRedFieldPosition: 16
[    30.125]     LinGreenMaskSize: 8
[    30.125]     LinGreenFieldPosition: 8
[    30.125]     LinBlueMaskSize: 8
[    30.125]     LinBlueFieldPosition: 0
[    30.125]     LinRsvdMaskSize: 0
[    30.125]     LinRsvdFieldPosition: 0
[    30.125]     MaxPixelClock: 400000000
[    30.126] Mode: 173 (1600x1200)
[    30.126]     ModeAttributes: 0xba
[    30.126]     WinAAttributes: 0x7
[    30.126]     WinBAttributes: 0x0
[    30.126]     WinGranularity: 64
[    30.126]     WinSize: 64
[    30.126]     WinASegment: 0xa000
[    30.126]     WinBSegment: 0x0
[    30.126]     WinFuncPtr: 0xc000536d
[    30.126]     BytesPerScanline: 1600
[    30.126]     XResolution: 1600
[    30.126]     YResolution: 1200
[    30.126]     XCharSize: 8
[    30.126]     YCharSize: 16
[    30.126]     NumberOfPlanes: 1
[    30.126]     BitsPerPixel: 8
[    30.126]     NumberOfBanks: 1
[    30.126]     MemoryModel: 4
[    30.126]     BankSize: 0
[    30.126]     NumberOfImages: 7
[    30.126]     RedMaskSize: 0
[    30.126]     RedFieldPosition: 0
[    30.126]     GreenMaskSize: 0
[    30.126]     GreenFieldPosition: 0
[    30.126]     BlueMaskSize: 0
[    30.126]     BlueFieldPosition: 0
[    30.126]     RsvdMaskSize: 0
[    30.126]     RsvdFieldPosition: 0
[    30.126]     DirectColorModeInfo: 0
[    30.126]     PhysBasePtr: 0xe0000000
[    30.126]     LinBytesPerScanLine: 1600
[    30.126]     BnkNumberOfImagePages: 7
[    30.126]     LinNumberOfImagePages: 7
[    30.126]     LinRedMaskSize: 0
[    30.126]     LinRedFieldPosition: 0
[    30.126]     LinGreenMaskSize: 0
[    30.126]     LinGreenFieldPosition: 0
[    30.126]     LinBlueMaskSize: 0
[    30.126]     LinBlueFieldPosition: 0
[    30.126]     LinRsvdMaskSize: 0
[    30.126]     LinRsvdFieldPosition: 0
[    30.126]     MaxPixelClock: 400000000
[    30.126] Mode: 175 (1600x1200)
[    30.126]     ModeAttributes: 0xba
[    30.126]     WinAAttributes: 0x7
[    30.126]     WinBAttributes: 0x0
[    30.126]     WinGranularity: 64
[    30.126]     WinSize: 64
[    30.126]     WinASegment: 0xa000
[    30.126]     WinBSegment: 0x0
[    30.126]     WinFuncPtr: 0xc000536d
[    30.126]     BytesPerScanline: 3200
[    30.126]     XResolution: 1600
[    30.126]     YResolution: 1200
[    30.126]     XCharSize: 8
[    30.126]     YCharSize: 16
[    30.126]     NumberOfPlanes: 1
[    30.126]     BitsPerPixel: 16
[    30.126]     NumberOfBanks: 1
[    30.126]     MemoryModel: 6
[    30.126]     BankSize: 0
[    30.126]     NumberOfImages: 3
[    30.126]     RedMaskSize: 5
[    30.126]     RedFieldPosition: 11
[    30.126]     GreenMaskSize: 6
[    30.126]     GreenFieldPosition: 5
[    30.126]     BlueMaskSize: 5
[    30.126]     BlueFieldPosition: 0
[    30.126]     RsvdMaskSize: 0
[    30.126]     RsvdFieldPosition: 0
[    30.126]     DirectColorModeInfo: 0
[    30.126]     PhysBasePtr: 0xe0000000
[    30.126]     LinBytesPerScanLine: 3200
[    30.126]     BnkNumberOfImagePages: 3
[    30.126]     LinNumberOfImagePages: 3
[    30.126]     LinRedMaskSize: 5
[    30.126]     LinRedFieldPosition: 11
[    30.126]     LinGreenMaskSize: 6
[    30.126]     LinGreenFieldPosition: 5
[    30.126]     LinBlueMaskSize: 5
[    30.126]     LinBlueFieldPosition: 0
[    30.126]     LinRsvdMaskSize: 0
[    30.126]     LinRsvdFieldPosition: 0
[    30.126]     MaxPixelClock: 400000000
[    30.127] Mode: 176 (1600x1200)
[    30.127]     ModeAttributes: 0xba
[    30.127]     WinAAttributes: 0x7
[    30.127]     WinBAttributes: 0x0
[    30.127]     WinGranularity: 64
[    30.127]     WinSize: 64
[    30.127]     WinASegment: 0xa000
[    30.127]     WinBSegment: 0x0
[    30.127]     WinFuncPtr: 0xc000536d
[    30.127]     BytesPerScanline: 6400
[    30.127]     XResolution: 1600
[    30.127]     YResolution: 1200
[    30.127]     XCharSize: 8
[    30.127]     YCharSize: 16
[    30.127]     NumberOfPlanes: 1
[    30.127]     BitsPerPixel: 32
[    30.127]     NumberOfBanks: 1
[    30.127]     MemoryModel: 6
[    30.127]     BankSize: 0
[    30.127]     NumberOfImages: 1
[    30.127]     RedMaskSize: 8
[    30.127]     RedFieldPosition: 16
[    30.127]     GreenMaskSize: 8
[    30.127]     GreenFieldPosition: 8
[    30.127]     BlueMaskSize: 8
[    30.127]     BlueFieldPosition: 0
[    30.127]     RsvdMaskSize: 0
[    30.127]     RsvdFieldPosition: 0
[    30.127]     DirectColorModeInfo: 0
[    30.127]     PhysBasePtr: 0xe0000000
[    30.127]     LinBytesPerScanLine: 6400
[    30.127]     BnkNumberOfImagePages: 1
[    30.127]     LinNumberOfImagePages: 1
[    30.127]     LinRedMaskSize: 8
[    30.127]     LinRedFieldPosition: 16
[    30.127]     LinGreenMaskSize: 8
[    30.127]     LinGreenFieldPosition: 8
[    30.127]     LinBlueMaskSize: 8
[    30.127]     LinBlueFieldPosition: 0
[    30.127]     LinRsvdMaskSize: 0
[    30.127]     LinRsvdFieldPosition: 0
[    30.127]     MaxPixelClock: 400000000
[    30.127] Mode: 183 (1792x1344)
[    30.127]     ModeAttributes: 0xba
[    30.127]     WinAAttributes: 0x7
[    30.127]     WinBAttributes: 0x0
[    30.127]     WinGranularity: 64
[    30.127]     WinSize: 64
[    30.127]     WinASegment: 0xa000
[    30.127]     WinBSegment: 0x0
[    30.127]     WinFuncPtr: 0xc000536d
[    30.127]     BytesPerScanline: 1792
[    30.127]     XResolution: 1792
[    30.127]     YResolution: 1344
[    30.127]     XCharSize: 8
[    30.127]     YCharSize: 16
[    30.127]     NumberOfPlanes: 1
[    30.127]     BitsPerPixel: 8
[    30.127]     NumberOfBanks: 1
[    30.127]     MemoryModel: 4
[    30.127]     BankSize: 0
[    30.127]     NumberOfImages: 5
[    30.127]     RedMaskSize: 0
[    30.127]     RedFieldPosition: 0
[    30.127]     GreenMaskSize: 0
[    30.127]     GreenFieldPosition: 0
[    30.127]     BlueMaskSize: 0
[    30.127]     BlueFieldPosition: 0
[    30.127]     RsvdMaskSize: 0
[    30.127]     RsvdFieldPosition: 0
[    30.127]     DirectColorModeInfo: 0
[    30.127]     PhysBasePtr: 0xe0000000
[    30.127]     LinBytesPerScanLine: 1792
[    30.127]     BnkNumberOfImagePages: 5
[    30.127]     LinNumberOfImagePages: 5
[    30.127]     LinRedMaskSize: 0
[    30.127]     LinRedFieldPosition: 0
[    30.127]     LinGreenMaskSize: 0
[    30.127]     LinGreenFieldPosition: 0
[    30.127]     LinBlueMaskSize: 0
[    30.127]     LinBlueFieldPosition: 0
[    30.127]     LinRsvdMaskSize: 0
[    30.127]     LinRsvdFieldPosition: 0
[    30.127]     MaxPixelClock: 400000000
[    30.128] Mode: 185 (1792x1344)
[    30.128]     ModeAttributes: 0xba
[    30.128]     WinAAttributes: 0x7
[    30.128]     WinBAttributes: 0x0
[    30.128]     WinGranularity: 64
[    30.128]     WinSize: 64
[    30.128]     WinASegment: 0xa000
[    30.128]     WinBSegment: 0x0
[    30.128]     WinFuncPtr: 0xc000536d
[    30.128]     BytesPerScanline: 3584
[    30.128]     XResolution: 1792
[    30.128]     YResolution: 1344
[    30.128]     XCharSize: 8
[    30.128]     YCharSize: 16
[    30.128]     NumberOfPlanes: 1
[    30.128]     BitsPerPixel: 16
[    30.128]     NumberOfBanks: 1
[    30.128]     MemoryModel: 6
[    30.128]     BankSize: 0
[    30.128]     NumberOfImages: 2
[    30.128]     RedMaskSize: 5
[    30.128]     RedFieldPosition: 11
[    30.128]     GreenMaskSize: 6
[    30.128]     GreenFieldPosition: 5
[    30.128]     BlueMaskSize: 5
[    30.128]     BlueFieldPosition: 0
[    30.128]     RsvdMaskSize: 0
[    30.128]     RsvdFieldPosition: 0
[    30.128]     DirectColorModeInfo: 0
[    30.128]     PhysBasePtr: 0xe0000000
[    30.128]     LinBytesPerScanLine: 3584
[    30.128]     BnkNumberOfImagePages: 2
[    30.128]     LinNumberOfImagePages: 2
[    30.128]     LinRedMaskSize: 5
[    30.128]     LinRedFieldPosition: 11
[    30.128]     LinGreenMaskSize: 6
[    30.128]     LinGreenFieldPosition: 5
[    30.128]     LinBlueMaskSize: 5
[    30.128]     LinBlueFieldPosition: 0
[    30.128]     LinRsvdMaskSize: 0
[    30.128]     LinRsvdFieldPosition: 0
[    30.128]     MaxPixelClock: 400000000
[    30.128] Mode: 186 (1792x1344)
[    30.128]     ModeAttributes: 0xba
[    30.128]     WinAAttributes: 0x7
[    30.128]     WinBAttributes: 0x0
[    30.128]     WinGranularity: 64
[    30.128]     WinSize: 64
[    30.128]     WinASegment: 0xa000
[    30.128]     WinBSegment: 0x0
[    30.128]     WinFuncPtr: 0xc000536d
[    30.128]     BytesPerScanline: 7168
[    30.128]     XResolution: 1792
[    30.128]     YResolution: 1344
[    30.128]     XCharSize: 8
[    30.128]     YCharSize: 16
[    30.128]     NumberOfPlanes: 1
[    30.128]     BitsPerPixel: 32
[    30.128]     NumberOfBanks: 1
[    30.128]     MemoryModel: 6
[    30.128]     BankSize: 0
[    30.128]     NumberOfImages: 1
[    30.128]     RedMaskSize: 8
[    30.128]     RedFieldPosition: 16
[    30.128]     GreenMaskSize: 8
[    30.128]     GreenFieldPosition: 8
[    30.128]     BlueMaskSize: 8
[    30.128]     BlueFieldPosition: 0
[    30.128]     RsvdMaskSize: 0
[    30.128]     RsvdFieldPosition: 0
[    30.128]     DirectColorModeInfo: 0
[    30.128]     PhysBasePtr: 0xe0000000
[    30.128]     LinBytesPerScanLine: 7168
[    30.128]     BnkNumberOfImagePages: 1
[    30.128]     LinNumberOfImagePages: 1
[    30.129]     LinRedMaskSize: 8
[    30.129]     LinRedFieldPosition: 16
[    30.129]     LinGreenMaskSize: 8
[    30.129]     LinGreenFieldPosition: 8
[    30.129]     LinBlueMaskSize: 8
[    30.129]     LinBlueFieldPosition: 0
[    30.129]     LinRsvdMaskSize: 0
[    30.129]     LinRsvdFieldPosition: 0
[    30.129]     MaxPixelClock: 400000000
[    30.129] Mode: 1d3 (1856x1392)
[    30.129]     ModeAttributes: 0xba
[    30.129]     WinAAttributes: 0x7
[    30.129]     WinBAttributes: 0x0
[    30.129]     WinGranularity: 64
[    30.129]     WinSize: 64
[    30.129]     WinASegment: 0xa000
[    30.129]     WinBSegment: 0x0
[    30.129]     WinFuncPtr: 0xc000536d
[    30.129]     BytesPerScanline: 1856
[    30.129]     XResolution: 1856
[    30.129]     YResolution: 1392
[    30.129]     XCharSize: 8
[    30.129]     YCharSize: 16
[    30.129]     NumberOfPlanes: 1
[    30.129]     BitsPerPixel: 8
[    30.129]     NumberOfBanks: 1
[    30.129]     MemoryModel: 4
[    30.129]     BankSize: 0
[    30.129]     NumberOfImages: 5
[    30.129]     RedMaskSize: 0
[    30.129]     RedFieldPosition: 0
[    30.129]     GreenMaskSize: 0
[    30.129]     GreenFieldPosition: 0
[    30.129]     BlueMaskSize: 0
[    30.129]     BlueFieldPosition: 0
[    30.129]     RsvdMaskSize: 0
[    30.129]     RsvdFieldPosition: 0
[    30.129]     DirectColorModeInfo: 0
[    30.129]     PhysBasePtr: 0xe0000000
[    30.129]     LinBytesPerScanLine: 1856
[    30.129]     BnkNumberOfImagePages: 5
[    30.129]     LinNumberOfImagePages: 5
[    30.129]     LinRedMaskSize: 0
[    30.129]     LinRedFieldPosition: 0
[    30.129]     LinGreenMaskSize: 0
[    30.129]     LinGreenFieldPosition: 0
[    30.129]     LinBlueMaskSize: 0
[    30.129]     LinBlueFieldPosition: 0
[    30.129]     LinRsvdMaskSize: 0
[    30.129]     LinRsvdFieldPosition: 0
[    30.129]     MaxPixelClock: 400000000
[    30.129] Mode: 1d5 (1856x1392)
[    30.129]     ModeAttributes: 0xba
[    30.129]     WinAAttributes: 0x7
[    30.129]     WinBAttributes: 0x0
[    30.129]     WinGranularity: 64
[    30.129]     WinSize: 64
[    30.129]     WinASegment: 0xa000
[    30.129]     WinBSegment: 0x0
[    30.129]     WinFuncPtr: 0xc000536d
[    30.129]     BytesPerScanline: 3712
[    30.129]     XResolution: 1856
[    30.129]     YResolution: 1392
[    30.129]     XCharSize: 8
[    30.129]     YCharSize: 16
[    30.129]     NumberOfPlanes: 1
[    30.129]     BitsPerPixel: 16
[    30.129]     NumberOfBanks: 1
[    30.129]     MemoryModel: 6
[    30.129]     BankSize: 0
[    30.129]     NumberOfImages: 2
[    30.130]     RedMaskSize: 5
[    30.130]     RedFieldPosition: 11
[    30.130]     GreenMaskSize: 6
[    30.130]     GreenFieldPosition: 5
[    30.130]     BlueMaskSize: 5
[    30.130]     BlueFieldPosition: 0
[    30.130]     RsvdMaskSize: 0
[    30.130]     RsvdFieldPosition: 0
[    30.130]     DirectColorModeInfo: 0
[    30.130]     PhysBasePtr: 0xe0000000
[    30.130]     LinBytesPerScanLine: 3712
[    30.130]     BnkNumberOfImagePages: 2
[    30.130]     LinNumberOfImagePages: 2
[    30.130]     LinRedMaskSize: 5
[    30.130]     LinRedFieldPosition: 11
[    30.130]     LinGreenMaskSize: 6
[    30.130]     LinGreenFieldPosition: 5
[    30.130]     LinBlueMaskSize: 5
[    30.130]     LinBlueFieldPosition: 0
[    30.130]     LinRsvdMaskSize: 0
[    30.130]     LinRsvdFieldPosition: 0
[    30.130]     MaxPixelClock: 400000000
[    30.130] Mode: 1d6 (1856x1392)
[    30.130]     ModeAttributes: 0xba
[    30.130]     WinAAttributes: 0x7
[    30.130]     WinBAttributes: 0x0
[    30.130]     WinGranularity: 64
[    30.130]     WinSize: 64
[    30.130]     WinASegment: 0xa000
[    30.130]     WinBSegment: 0x0
[    30.130]     WinFuncPtr: 0xc000536d
[    30.130]     BytesPerScanline: 7424
[    30.130]     XResolution: 1856
[    30.130]     YResolution: 1392
[    30.130]     XCharSize: 8
[    30.130]     YCharSize: 16
[    30.130]     NumberOfPlanes: 1
[    30.130]     BitsPerPixel: 32
[    30.130]     NumberOfBanks: 1
[    30.130]     MemoryModel: 6
[    30.130]     BankSize: 0
[    30.130]     NumberOfImages: 1
[    30.130]     RedMaskSize: 8
[    30.130]     RedFieldPosition: 16
[    30.130]     GreenMaskSize: 8
[    30.130]     GreenFieldPosition: 8
[    30.130]     BlueMaskSize: 8
[    30.130]     BlueFieldPosition: 0
[    30.130]     RsvdMaskSize: 0
[    30.130]     RsvdFieldPosition: 0
[    30.130]     DirectColorModeInfo: 0
[    30.130]     PhysBasePtr: 0xe0000000
[    30.130]     LinBytesPerScanLine: 7424
[    30.130]     BnkNumberOfImagePages: 1
[    30.130]     LinNumberOfImagePages: 1
[    30.130]     LinRedMaskSize: 8
[    30.130]     LinRedFieldPosition: 16
[    30.130]     LinGreenMaskSize: 8
[    30.130]     LinGreenFieldPosition: 8
[    30.130]     LinBlueMaskSize: 8
[    30.130]     LinBlueFieldPosition: 0
[    30.130]     LinRsvdMaskSize: 0
[    30.130]     LinRsvdFieldPosition: 0
[    30.130]     MaxPixelClock: 400000000
[    30.130] Mode: 1e3 (1920x1440)
[    30.130]     ModeAttributes: 0xba
[    30.130]     WinAAttributes: 0x7
[    30.130]     WinBAttributes: 0x0
[    30.130]     WinGranularity: 64
[    30.130]     WinSize: 64
[    30.130]     WinASegment: 0xa000
[    30.131]     WinBSegment: 0x0
[    30.131]     WinFuncPtr: 0xc000536d
[    30.131]     BytesPerScanline: 1920
[    30.131]     XResolution: 1920
[    30.131]     YResolution: 1440
[    30.131]     XCharSize: 8
[    30.131]     YCharSize: 16
[    30.131]     NumberOfPlanes: 1
[    30.131]     BitsPerPixel: 8
[    30.131]     NumberOfBanks: 1
[    30.131]     MemoryModel: 4
[    30.131]     BankSize: 0
[    30.131]     NumberOfImages: 4
[    30.131]     RedMaskSize: 0
[    30.131]     RedFieldPosition: 0
[    30.131]     GreenMaskSize: 0
[    30.131]     GreenFieldPosition: 0
[    30.131]     BlueMaskSize: 0
[    30.131]     BlueFieldPosition: 0
[    30.131]     RsvdMaskSize: 0
[    30.131]     RsvdFieldPosition: 0
[    30.131]     DirectColorModeInfo: 0
[    30.131]     PhysBasePtr: 0xe0000000
[    30.131]     LinBytesPerScanLine: 1920
[    30.131]     BnkNumberOfImagePages: 4
[    30.131]     LinNumberOfImagePages: 4
[    30.131]     LinRedMaskSize: 0
[    30.131]     LinRedFieldPosition: 0
[    30.131]     LinGreenMaskSize: 0
[    30.131]     LinGreenFieldPosition: 0
[    30.131]     LinBlueMaskSize: 0
[    30.131]     LinBlueFieldPosition: 0
[    30.131]     LinRsvdMaskSize: 0
[    30.131]     LinRsvdFieldPosition: 0
[    30.131]     MaxPixelClock: 400000000
[    30.131] Mode: 1e5 (1920x1440)
[    30.131]     ModeAttributes: 0xba
[    30.131]     WinAAttributes: 0x7
[    30.131]     WinBAttributes: 0x0
[    30.131]     WinGranularity: 64
[    30.131]     WinSize: 64
[    30.131]     WinASegment: 0xa000
[    30.131]     WinBSegment: 0x0
[    30.131]     WinFuncPtr: 0xc000536d
[    30.131]     BytesPerScanline: 3840
[    30.131]     XResolution: 1920
[    30.131]     YResolution: 1440
[    30.131]     XCharSize: 8
[    30.131]     YCharSize: 16
[    30.131]     NumberOfPlanes: 1
[    30.131]     BitsPerPixel: 16
[    30.131]     NumberOfBanks: 1
[    30.131]     MemoryModel: 6
[    30.131]     BankSize: 0
[    30.131]     NumberOfImages: 2
[    30.131]     RedMaskSize: 5
[    30.131]     RedFieldPosition: 11
[    30.131]     GreenMaskSize: 6
[    30.131]     GreenFieldPosition: 5
[    30.131]     BlueMaskSize: 5
[    30.131]     BlueFieldPosition: 0
[    30.131]     RsvdMaskSize: 0
[    30.131]     RsvdFieldPosition: 0
[    30.131]     DirectColorModeInfo: 0
[    30.131]     PhysBasePtr: 0xe0000000
[    30.131]     LinBytesPerScanLine: 3840
[    30.131]     BnkNumberOfImagePages: 2
[    30.131]     LinNumberOfImagePages: 2
[    30.131]     LinRedMaskSize: 5
[    30.131]     LinRedFieldPosition: 11
[    30.131]     LinGreenMaskSize: 6
[    30.131]     LinGreenFieldPosition: 5
[    30.131]     LinBlueMaskSize: 5
[    30.131]     LinBlueFieldPosition: 0
[    30.131]     LinRsvdMaskSize: 0
[    30.131]     LinRsvdFieldPosition: 0
[    30.131]     MaxPixelClock: 400000000
[    30.132] Mode: 1e6 (1920x1440)
[    30.132]     ModeAttributes: 0xba
[    30.132]     WinAAttributes: 0x7
[    30.132]     WinBAttributes: 0x0
[    30.132]     WinGranularity: 64
[    30.132]     WinSize: 64
[    30.132]     WinASegment: 0xa000
[    30.132]     WinBSegment: 0x0
[    30.132]     WinFuncPtr: 0xc000536d
[    30.132]     BytesPerScanline: 7680
[    30.132]     XResolution: 1920
[    30.132]     YResolution: 1440
[    30.132]     XCharSize: 8
[    30.132]     YCharSize: 16
[    30.132]     NumberOfPlanes: 1
[    30.132]     BitsPerPixel: 32
[    30.132]     NumberOfBanks: 1
[    30.132]     MemoryModel: 6
[    30.132]     BankSize: 0
[    30.132]     NumberOfImages: 1
[    30.132]     RedMaskSize: 8
[    30.132]     RedFieldPosition: 16
[    30.132]     GreenMaskSize: 8
[    30.132]     GreenFieldPosition: 8
[    30.132]     BlueMaskSize: 8
[    30.132]     BlueFieldPosition: 0
[    30.132]     RsvdMaskSize: 0
[    30.132]     RsvdFieldPosition: 0
[    30.132]     DirectColorModeInfo: 0
[    30.132]     PhysBasePtr: 0xe0000000
[    30.132]     LinBytesPerScanLine: 7680
[    30.132]     BnkNumberOfImagePages: 1
[    30.132]     LinNumberOfImagePages: 1
[    30.132]     LinRedMaskSize: 8
[    30.132]     LinRedFieldPosition: 16
[    30.132]     LinGreenMaskSize: 8
[    30.132]     LinGreenFieldPosition: 8
[    30.132]     LinBlueMaskSize: 8
[    30.132]     LinBlueFieldPosition: 0
[    30.132]     LinRsvdMaskSize: 0
[    30.132]     LinRsvdFieldPosition: 0
[    30.132]     MaxPixelClock: 400000000
[    30.132] 
[    30.132] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[    30.132] (II) VESA(0): <default monitor>: Using hsync value of 48.21 kHz
[    30.132] (II) VESA(0): <default monitor>: Using vrefresh value of 60.04 Hz
[    30.132] (II) VESA(0): Not using mode "1366x768" (no mode of this name)
[    30.132] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    30.132] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    30.132] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    30.132] (II) VESA(0): Not using built-in mode "720x400" (no mode of this name)
[    30.132] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[    30.132] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[    30.132] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    30.132] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    30.132] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    30.132] (II) VESA(0): <default monitor>: Using hsync value of 48.21 kHz
[    30.132] (II) VESA(0): <default monitor>: Using vrefresh value of 60.04 Hz
[    30.132] (II) VESA(0): Not using mode "1366x768" (no mode of this name)
[    30.132] (II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
[    30.132] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    30.132] (II) VESA(0): Not using built-in mode "720x400" (hsync out of range)
[    30.132] (II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
[    30.132] (II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
[    30.132] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    30.132] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    30.132] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    30.132] (**) VESA(0):  Built-in mode "1024x768"
[    30.132] (**) VESA(0): Display dimensions: (310, 170) mm
[    30.132] (**) VESA(0): DPI set to (83, 114)
[    30.132] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (123)
[    30.132] (**) VESA(0): Using "Shadow Framebuffer"
[    30.132] (II) Loading sub module "shadow"
[    30.132] (II) LoadModule: "shadow"
[    30.132] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    30.133] (II) Module shadow: vendor="X.Org Foundation"
[    30.133]     compiled for 1.13.0, module version = 1.1.0
[    30.133]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.133] (II) Loading sub module "fb"
[    30.133] (II) LoadModule: "fb"
[    30.133] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.133] (II) Module fb: vendor="X.Org Foundation"
[    30.133]     compiled for 1.13.0, module version = 1.0.0
[    30.133]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.133] (II) UnloadModule: "radeon"
[    30.133] (II) UnloadModule: "modesetting"
[    30.133] (II) Unloading modesetting
[    30.133] (II) UnloadModule: "fbdev"
[    30.133] (II) Unloading fbdev
[    30.133] (II) UnloadSubModule: "fbdevhw"
[    30.133] (II) Unloading fbdevhw
[    30.133] (==) Depth 24 pixmap format is 32 bpp
[    30.133] (II) Loading sub module "int10"
[    30.133] (II) LoadModule: "int10"
[    30.133] (II) Loading /usr/lib/xorg/modules/libint10.so
[    30.133] (II) Module int10: vendor="X.Org Foundation"
[    30.133]     compiled for 1.13.0, module version = 1.0.0
[    30.133]     ABI class: X.Org Video Driver, version 13.0
[    30.133] (II) VESA(0): initializing int10
[    31.613] (II) VESA(0): VESA BIOS detected
[    31.613] (II) VESA(0): VESA VBE Version 3.0
[    31.613] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    31.613] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    31.613] (II) VESA(0): VESA VBE OEM Software Rev: 11.22
[    31.613] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    31.613] (II) VESA(0): VESA VBE OEM Product: M92
[    31.613] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    31.614] (II) VESA(0): virtual address = 0x7f5fc4feb000,
    physical address = 0xe0000000, size = 16777216
[    31.626] (II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
[    31.626] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[    31.674] (==) VESA(0): Default visual is TrueColor
[    31.674] (==) VESA(0): Backing store disabled
[    31.674] (==) VESA(0): DPMS enabled
[    31.674] (==) RandR enabled
[    31.680] (II) AIGLX: Screen 0 is not DRI2 capable
[    31.680] (II) AIGLX: Screen 0 is not DRI capable
[    31.691] (II) AIGLX: Loaded and initialized swrast
[    31.691] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    31.717] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.720] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    31.720] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    31.720] (II) LoadModule: "evdev"
[    31.720] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.720] (II) Module evdev: vendor="X.Org Foundation"
[    31.720]     compiled for 1.13.0, module version = 2.7.3
[    31.720]     Module class: X.Org XInput Driver
[    31.720]     ABI class: X.Org XInput driver, version 18.0
[    31.720] (II) Using input driver 'evdev' for 'Video Bus'
[    31.721] (**) Video Bus: always reports core events
[    31.721] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    31.721] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    31.721] (--) evdev: Video Bus: Found keys
[    31.721] (II) evdev: Video Bus: Configuring as keyboard
[    31.721] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:33/LNXVIDEO:00/input/input6/event5"
[    31.721] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    31.721] (**) Option "xkb_rules" "evdev"
[    31.721] (**) Option "xkb_model" "pc105"
[    31.721] (**) Option "xkb_layout" "us"
[    31.721] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.721] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.721] (II) Using input driver 'evdev' for 'Power Button'
[    31.721] (**) Power Button: always reports core events
[    31.721] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.721] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.721] (--) evdev: Power Button: Found keys
[    31.721] (II) evdev: Power Button: Configuring as keyboard
[    31.721] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    31.721] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.721] (**) Option "xkb_rules" "evdev"
[    31.721] (**) Option "xkb_model" "pc105"
[    31.722] (**) Option "xkb_layout" "us"
[    31.722] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    31.722] (II) No input driver specified, ignoring this device.
[    31.722] (II) This device may have been added with another device file.
[    31.722] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    31.722] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    31.722] (II) Using input driver 'evdev' for 'Sleep Button'
[    31.722] (**) Sleep Button: always reports core events
[    31.722] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    31.722] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    31.722] (--) evdev: Sleep Button: Found keys
[    31.722] (II) evdev: Sleep Button: Configuring as keyboard
[    31.722] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    31.722] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    31.722] (**) Option "xkb_rules" "evdev"
[    31.722] (**) Option "xkb_model" "pc105"
[    31.722] (**) Option "xkb_layout" "us"
[    31.723] (II) config/udev: Adding drm device (/dev/dri/card0)
[    31.723] (II) config/udev: Adding input device HID 413c:8161 (/dev/input/event4)
[    31.723] (**) HID 413c:8161: Applying InputClass "evdev keyboard catchall"
[    31.723] (II) Using input driver 'evdev' for 'HID 413c:8161'
[    31.723] (**) HID 413c:8161: always reports core events
[    31.723] (**) evdev: HID 413c:8161: Device: "/dev/input/event4"
[    31.723] (--) evdev: HID 413c:8161: Vendor 0x413c Product 0x8161
[    31.723] (--) evdev: HID 413c:8161: Found keys
[    31.723] (II) evdev: HID 413c:8161: Configuring as keyboard
[    31.723] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input4/event4"
[    31.723] (II) XINPUT: Adding extended input device "HID 413c:8161" (type: KEYBOARD, id 9)
[    31.723] (**) Option "xkb_rules" "evdev"
[    31.723] (**) Option "xkb_model" "pc105"
[    31.723] (**) Option "xkb_layout" "us"
[    31.724] (II) config/udev: Adding input device Integrated_Webcam_1.3M (/dev/input/event7)
[    31.724] (**) Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
[    31.724] (II) Using input driver 'evdev' for 'Integrated_Webcam_1.3M'
[    31.724] (**) Integrated_Webcam_1.3M: always reports core events
[    31.724] (**) evdev: Integrated_Webcam_1.3M: Device: "/dev/input/event7"
[    31.724] (--) evdev: Integrated_Webcam_1.3M: Vendor 0xc45 Product 0x6400
[    31.724] (--) evdev: Integrated_Webcam_1.3M: Found keys
[    31.724] (II) evdev: Integrated_Webcam_1.3M: Configuring as keyboard
[    31.724] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input8/event7"
[    31.724] (II) XINPUT: Adding extended input device "Integrated_Webcam_1.3M" (type: KEYBOARD, id 10)
[    31.724] (**) Option "xkb_rules" "evdev"
[    31.724] (**) Option "xkb_model" "pc105"
[    31.724] (**) Option "xkb_layout" "us"
[    31.725] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
[    31.725] (II) No input driver specified, ignoring this device.
[    31.725] (II) This device may have been added with another device file.
[    31.725] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event11)
[    31.725] (II) No input driver specified, ignoring this device.
[    31.725] (II) This device may have been added with another device file.
[    31.726] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    31.726] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.726] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.726] (**) AT Translated Set 2 keyboard: always reports core events
[    31.726] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    31.726] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.726] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.726] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.726] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    31.726] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    31.726] (**) Option "xkb_rules" "evdev"
[    31.726] (**) Option "xkb_model" "pc105"
[    31.726] (**) Option "xkb_layout" "us"
[    31.726] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event9)
[    31.726] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    31.726] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    31.726] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    31.726] (II) LoadModule: "synaptics"
[    31.727] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    31.727] (II) Module synaptics: vendor="X.Org Foundation"
[    31.727]     compiled for 1.12.99.905, module version = 1.6.2
[    31.727]     Module class: X.Org XInput Driver
[    31.727]     ABI class: X.Org XInput driver, version 18.0
[    31.727] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    31.727] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    31.727] (**) Option "Device" "/dev/input/event9"
[    31.732] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    31.732] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    31.732] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    31.732] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    31.732] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    31.732] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    31.732] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    31.732] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    31.732] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    31.732] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event9"
[    31.732] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 12)
[    31.732] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    31.732] (**) synaptics: AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    31.732] (**) synaptics: AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    31.732] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    31.733] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    31.733] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    31.733] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    31.733] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    31.733] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    31.733] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    31.733] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event8)
[    31.733] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    31.733] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    31.733] (**) PS/2 Mouse: always reports core events
[    31.733] (**) evdev: PS/2 Mouse: Device: "/dev/input/event8"
[    31.733] (--) evdev: PS/2 Mouse: Vendor 0x2 Product 0x8
[    31.733] (--) evdev: PS/2 Mouse: Found 3 mouse buttons
[    31.733] (--) evdev: PS/2 Mouse: Found relative axes
[    31.733] (--) evdev: PS/2 Mouse: Found x and y relative axes
[    31.733] (II) evdev: PS/2 Mouse: Configuring as mouse
[    31.733] (**) evdev: PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    31.733] (**) evdev: PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.733] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input9/event8"
[    31.733] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE, id 13)
[    31.733] (II) evdev: PS/2 Mouse: initialized for relative axes.
[    31.734] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    31.734] (**) PS/2 Mouse: (accel) acceleration profile 0
[    31.734] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    31.734] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    31.734] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse0)
[    31.734] (II) No input driver specified, ignoring this device.
[    31.734] (II) This device may have been added with another device file.
[    31.736] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event6)
[    31.736] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    31.736] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    31.736] (**) Dell WMI hotkeys: always reports core events
[    31.736] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event6"
[    31.736] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    31.736] (--) evdev: Dell WMI hotkeys: Found keys
[    31.736] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    31.736] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event6"
[    31.736] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[    31.736] (**) Option "xkb_rules" "evdev"
[    31.736] (**) Option "xkb_model" "pc105"
[    31.736] (**) Option "xkb_layout" "us"
[   111.109] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[ 10822.492] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[ 12602.466] (II) Open ACPI successful (/var/run/acpid.socket)
[ 12602.630] (II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
[ 12603.160] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[ 16227.646] (II) Open ACPI successful (/var/run/acpid.socket)
[ 16227.646] (II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
[ 16227.713] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[ 16310.033] (II) Open ACPI successful (/var/run/acpid.socket)
[ 16310.033] (II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
[ 16310.132] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found

```

---

### Post by ruudx on 2013-09-03
No one with a solution yet :(.

---

### Post by Yellow Pasque on 2013-09-03
> [KMS] drm report modesetting isn't supported.
It's falling back on generic VESA driver because of that message. I don't know exactly why, but at least that gives you something specific to google...

---

