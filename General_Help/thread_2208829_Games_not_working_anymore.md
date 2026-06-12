---
title: "Games not working anymore"
date: 2014-03-02
forum: General Help
---

### Post by christophe.maillot on 2014-03-02
Dears,

since some times, the games I installed (supertuxkart, Lincity, and few others) do not work anymore ... 
when i click on the logo it blinks few seconds and stop ... and the game do not open.
What to do first ? I ran a sudo apt-get update but did not changed anything ...

thanks

C

---

### Post by Impavidus on 2014-03-02
Try starting them from a terminal. It may give a useful error message.

---

### Post by christophe.maillot on 2014-03-03
... thanks, sorry but I don't remember the command line to start a software from the terminal ... not done it since very long time ...

---

### Post by Impavidus on 2014-03-03
In case of Lincity (actually, Lincity NG if you're using 12.04), the command is ```
lincity-ng
```

---

### Post by christophe.maillot on 2014-03-04
here is what I get when typing "lincity-ng" in a terminal :

```
p....@k...:~$ lincity-ng
Starting lincity-ng (version 2.0)...
[/home/peggy/.lincity-ng] is in the search path.
[/usr/share/games/lincity-ng] is in the search path.
[/home/peggy/.lincity-ng] is the write directory.
Language is "fr_FR".
 fast = 9
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13
p...@k...:~$ 
```

---

### Post by christophe.maillot on 2014-03-04
and here is what I get whe typing "supertuxkart" in terminal :


```
p...@k...:~$ supertuxkart
Irrlicht Engine version 1.7.2
Linux 3.2.0-59-generic #90-Ubuntu SMP Tue Jan 7 22:43:51 UTC 2014 x86_64
[FileManager] Data files will be fetched from: '/usr/share/games/supertuxkart/'
[IrrDriver] Creating NULL device
Irrlicht Engine version 1.7.2
Linux 3.2.0-59-generic #90-Ubuntu SMP Tue Jan 7 22:43:51 UTC 2014 x86_64
[IrrDriver] Trying OpenGL rendering.
[IrrDriver] Tring to create device with 32 bits
[IrrDriver Temp Logger] Level 1: X Error: BadRequest (invalid request code or no such operation)
[IrrDriver Temp Logger] Level 1: From call : unknown
[IrrDriver Temp Logger] Level 1: X Error: BadRequest (invalid request code or no such operation)
[IrrDriver Temp Logger] Level 1: From call : unknown
[IrrDriver Temp Logger] Level 1: X Error: BadRequest (invalid request code or no such operation)
[IrrDriver Temp Logger] Level 1: From call : unknown
[IrrDriver Temp Logger] Level 1: No GLX support available. OpenGL driver will not work.
[IrrDriver Temp Logger] Level 2: Fatal error, could not get visual.
Erreur de segmentation (core dumped)
p...@k...:~$ 

```

---

### Post by Impavidus on 2014-03-04
So, there is a problem whilst initialising the graphical output. I don't really know about that. I hope someone else can help you further.

---

### Post by christophe.maillot on 2014-03-04
ok ... someone else caan hep me please ... ?
fyi : my graph card is an integrated ATI Radeon HD 3000 GPU (integrated onto a motherboard ASUS M5A78L-M/USB3

thanks

---

### Post by Yellow Pasque on 2014-03-04
Looks like driver is messed up (if I had to guess, you mistakenly tried to install fglrx/Catalyst)
Show the contents of /var/log/Xorg.0.log file (use [ code ][ /code ] tags).

---

### Post by christophe.maillot on 2014-03-04
```
[226313.518] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[226313.518] X Protocol Version 11, Revision 0
[226313.518] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[226313.518] Current Operating System: Linux kezako 3.2.0-59-generic #90-Ubuntu SMP Tue Jan 7 22:43:51 UTC 2014 x86_64
[226313.518] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-59-generic root=UUID=9dce2e4d-b4fb-476c-a8a7-6bafed4242b0 ro quiet splash vt.handoff=7
[226313.518] Build Date: 16 October 2013  04:41:23PM
[226313.518] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[226313.518] Current version of pixman: 0.30.2
[226313.518]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[226313.518] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[226313.519] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar  4 00:08:34 2014
[226313.519] (==) Using config file: "/etc/X11/xorg.conf"
[226313.519] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[226313.520] (==) No Layout section.  Using the first Screen section.
[226313.520] (**) |-->Screen "Default Screen" (0)
[226313.520] (**) |   |-->Monitor "<default monitor>"
[226313.520] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[226313.520] (==) Automatically adding devices
[226313.520] (==) Automatically enabling devices
[226313.520] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[226313.520]     Entry deleted from font path.
[226313.520] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[226313.520]     Entry deleted from font path.
[226313.520] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[226313.520]     Entry deleted from font path.
[226313.520] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[226313.520]     Entry deleted from font path.
[226313.520] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[226313.520]     Entry deleted from font path.
[226313.520] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[226313.520]     Entry deleted from font path.
[226313.520] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[226313.521] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[226313.521] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[226313.521] (II) Loader magic: 0x7fd59d062b00
[226313.521] (II) Module ABI versions:
[226313.521]     X.Org ANSI C Emulation: 0.4
[226313.521]     X.Org Video Driver: 11.0
[226313.521]     X.Org XInput driver : 16.0
[226313.521]     X.Org Server Extension : 6.0
[226313.522] (--) PCI:*(0:1:5:0) 1002:9616:1043:8388 rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, 0xfe900000/1048576, I/O @ 0x0000d000/256
[226313.522] (II) Open ACPI successful (/var/run/acpid.socket)
[226313.522] (II) "extmod" will be loaded by default.
[226313.522] (II) "dbe" will be loaded by default.
[226313.522] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[226313.522] (II) "record" will be loaded by default.
[226313.522] (II) "dri" will be loaded by default.
[226313.522] (II) "dri2" will be loaded by default.
[226313.522] (II) LoadModule: "glx"
[226313.523] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[226313.524] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[226313.524]     compiled for 6.9.0, module version = 1.0.0
[226313.524] (II) Loading extension GLX
[226313.524] (II) LoadModule: "extmod"
[226313.525] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[226313.526] (II) Module extmod: vendor="X.Org Foundation"
[226313.526]     compiled for 1.11.3, module version = 1.0.0
[226313.526]     Module class: X.Org Server Extension
[226313.526]     ABI class: X.Org Server Extension, version 6.0
[226313.526] (II) Loading extension MIT-SCREEN-SAVER
[226313.526] (II) Loading extension XFree86-VidModeExtension
[226313.526] (II) Loading extension XFree86-DGA
[226313.526] (II) Loading extension DPMS
[226313.526] (II) Loading extension XVideo
[226313.526] (II) Loading extension XVideo-MotionCompensation
[226313.526] (II) Loading extension X-Resource
[226313.526] (II) LoadModule: "dbe"
[226313.527] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[226313.527] (II) Module dbe: vendor="X.Org Foundation"
[226313.527]     compiled for 1.11.3, module version = 1.0.0
[226313.527]     Module class: X.Org Server Extension
[226313.527]     ABI class: X.Org Server Extension, version 6.0
[226313.527] (II) Loading extension DOUBLE-BUFFER
[226313.527] (II) LoadModule: "record"
[226313.528] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[226313.528] (II) Module record: vendor="X.Org Foundation"
[226313.528]     compiled for 1.11.3, module version = 1.13.0
[226313.528]     Module class: X.Org Server Extension
[226313.528]     ABI class: X.Org Server Extension, version 6.0
[226313.528] (II) Loading extension RECORD
[226313.528] (II) LoadModule: "dri"
[226313.528] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[226313.528] (II) Module dri: vendor="X.Org Foundation"
[226313.528]     compiled for 1.11.3, module version = 1.0.0
[226313.528]     ABI class: X.Org Server Extension, version 6.0
[226313.528] (II) Loading extension XFree86-DRI
[226313.528] (II) LoadModule: "dri2"
[226313.529] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[226313.529] (II) Module dri2: vendor="X.Org Foundation"
[226313.529]     compiled for 1.11.3, module version = 1.2.0
[226313.529]     ABI class: X.Org Server Extension, version 6.0
[226313.529] (II) Loading extension DRI2
[226313.529] (==) Matched fglrx as autoconfigured driver 0
[226313.529] (==) Matched ati as autoconfigured driver 1
[226313.529] (==) Matched vesa as autoconfigured driver 2
[226313.529] (==) Matched fbdev as autoconfigured driver 3
[226313.529] (==) Assigned the driver to the xf86ConfigLayout
[226313.529] (II) LoadModule: "fglrx"
[226313.529] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[226313.543] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[226313.543]     compiled for 1.4.99.906, module version = 13.10.10
[226313.543]     Module class: X.Org Video Driver
[226313.543] (II) Loading sub module "fglrxdrm"
[226313.543] (II) LoadModule: "fglrxdrm"
[226313.543] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[226313.543] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[226313.543]     compiled for 1.4.99.906, module version = 13.10.10
[226313.543] (II) LoadModule: "ati"
[226313.544] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[226313.544] (II) Module ati: vendor="X.Org Foundation"
[226313.544]     compiled for 1.11.3, module version = 6.14.99
[226313.544]     Module class: X.Org Video Driver
[226313.544]     ABI class: X.Org Video Driver, version 11.0
[226313.544] (II) LoadModule: "radeon"
[226313.544] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[226313.544] (II) Module radeon: vendor="X.Org Foundation"
[226313.544]     compiled for 1.11.3, module version = 6.14.99
[226313.544]     Module class: X.Org Video Driver
[226313.544]     ABI class: X.Org Video Driver, version 11.0
[226313.544] (II) LoadModule: "vesa"
[226313.544] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[226313.544] (II) Module vesa: vendor="X.Org Foundation"
[226313.544]     compiled for 1.11.3, module version = 2.3.0
[226313.544]     Module class: X.Org Video Driver
[226313.544]     ABI class: X.Org Video Driver, version 11.0
[226313.544] (II) LoadModule: "fbdev"
[226313.545] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[226313.545] (II) Module fbdev: vendor="X.Org Foundation"
[226313.545]     compiled for 1.11.3, module version = 0.4.2
[226313.545]     ABI class: X.Org Video Driver, version 11.0
[226313.545] (II) AMD Proprietary Linux Driver Version Identifier:13.10.10
[226313.545] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.101                   
[226313.545] (II) AMD Proprietary Linux Driver Build Date: May 23 2013 15:49:35
[226313.545] (II) RADEON: Driver for ATI Radeon chipsets:
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
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
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
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[226313.547] (II) VESA: driver for VESA chipsets: vesa
[226313.547] (II) FBDEV: driver for framebuffer: fbdev
[226313.547] (++) using VT number 7

[226313.547] (WW) Falling back to old probe method for fglrx
[226313.553] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[226313.662] ukiDynamicMajor: failed to open /proc/ati/major
[226313.665] (EE) No supported AMD display adapters were found
[226313.665] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[226313.665] (II) [KMS] drm report modesetting isn't supported.
[226313.665] (WW) Falling back to old probe method for vesa
[226313.665] (WW) Falling back to old probe method for fbdev
[226313.665] (II) Loading sub module "fbdevhw"
[226313.665] (II) LoadModule: "fbdevhw"
[226313.666] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[226313.666] (II) Module fbdevhw: vendor="X.Org Foundation"
[226313.666]     compiled for 1.11.3, module version = 0.0.2
[226313.666]     ABI class: X.Org Video Driver, version 11.0
[226313.667] (II) RADEON(0): TOTO SAYS 00000000feaf0000
[226313.667] (II) RADEON(0): MMIO registers at 0x00000000feaf0000: size 64KB
[226313.667] (II) RADEON(0): PCI bus 1 card 5 func 0
[226313.667] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[226313.667] (**) RADEON(0): Depth 24, (--) framebuffer bpp 32
[226313.667] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[226313.667] (==) RADEON(0): Default visual is TrueColor
[226313.667] (II) Loading sub module "vgahw"
[226313.667] (II) LoadModule: "vgahw"
[226313.668] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[226313.668] (II) Module vgahw: vendor="X.Org Foundation"
[226313.668]     compiled for 1.11.3, module version = 0.1.0
[226313.668]     ABI class: X.Org Video Driver, version 11.0
[226313.668] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[226313.668] (==) RADEON(0): RGB weight 888
[226313.668] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[226313.668] (--) RADEON(0): Chipset: "ATI Radeon 3000 Graphics" (ChipID = 0x9616)
[226313.668] (--) RADEON(0): Linear framebuffer at 0x00000000d0000000
[226313.669] (II) RADEON(0): PCI card detected
[226313.669] (II) Loading sub module "int10"
[226313.669] (II) LoadModule: "int10"
[226313.670] (II) Loading /usr/lib/xorg/modules/libint10.so
[226313.670] (II) Module int10: vendor="X.Org Foundation"
[226313.670]     compiled for 1.11.3, module version = 1.0.0
[226313.670]     ABI class: X.Org Video Driver, version 11.0
[226313.670] (II) RADEON(0): initializing int10
[226313.677] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[226313.678] (II) RADEON(0): ATOM BIOS detected
[226313.678] (II) RADEON(0): ATOM BIOS Rom: 
[226313.678]     SubsystemVendorID: 0x1002 SubsystemID: 0x1002
[226313.678]     IOBaseAddress: 0xd000
[226313.678]     Filename: M4A76DVI.002
[226313.678]     BIOS Bootup Message:  
B27722_RS780C RS780 DDR2 200e/500m                                           

[226313.678] (II) RADEON(0): Framebuffer space used by Firmware (kb): 16
[226313.678] (II) RADEON(0): Start of VRAM area used by Firmware: 0xfffc000
[226313.678] (II) RADEON(0): AtomBIOS requests 16kB of VRAM scratch space
[226313.678] (II) RADEON(0): AtomBIOS VRAM scratch base: 0xfffc000
[226313.678] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[226313.678] (II) RADEON(0): Default Engine Clock: 350000
[226313.678] (II) RADEON(0): Default Memory Clock: 667000
[226313.678] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[226313.678] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[226313.678] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
[226313.678] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
[226313.678] (II) RADEON(0): Maximum Pixel Clock: 400000
[226313.678] (II) RADEON(0): Reference Clock: 14320
[226313.679] drmOpenDevice: node name is /dev/dri/card0
[226313.689] [drm] failed to load kernel module "radeon"
[226313.690] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[226313.690] (II) RADEON(0): using shadow framebuffer
[226313.690] (II) Loading sub module "shadow"
[226313.690] (II) LoadModule: "shadow"
[226313.691] (II) Loading /usr/lib/xorg/modules/libshadow.so
[226313.691] (II) Module shadow: vendor="X.Org Foundation"
[226313.691]     compiled for 1.11.3, module version = 1.1.0
[226313.691]     ABI class: X.Org ANSI C Emulation, version 0.4
[226313.691] (II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
[226313.691] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
[226313.691] (II) RADEON(0): Color tiling disabled
[226313.691] (II) Loading sub module "ddc"
[226313.691] (II) LoadModule: "ddc"
[226313.691] (II) Module "ddc" already built-in
[226313.691] (II) Loading sub module "i2c"
[226313.691] (II) LoadModule: "i2c"
[226313.691] (II) Module "i2c" already built-in
[226313.691] (II) RADEON(0): PLL parameters: rf=1432 rd=12 min=90000 max=120000; xclk=40000
[226313.691] (II) RADEON(0): Output VGA-0 has no monitor section
[226313.691] (II) RADEON(0): I2C bus "VGA-0" initialized.
[226313.691] (II) RADEON(0): Output DVI-0 has no monitor section
[226313.691] (II) RADEON(0): I2C bus "DVI-0" initialized.
[226313.691] (II) RADEON(0): Port0:
[226313.691]   XRANDR name: VGA-0
[226313.691]   Connector: VGA
[226313.691]   CRT1: INTERNAL_KLDSCP_DAC1
[226313.691]   DDC reg: 0x7e40
[226313.691] (II) RADEON(0): Port1:
[226313.691]   XRANDR name: DVI-0
[226313.692]   Connector: DVI-D
[226313.692]   DFP3: INTERNAL_KLDSCP_LVTMA
[226313.692]   DDC reg: 0x7e50
[226313.692] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[226313.742] (II) RADEON(0): EDID for output VGA-0
[226313.742] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[226313.742] (II) RADEON(0): Year: 2005  Week: 40
[226313.742] (II) RADEON(0): EDID Version: 1.3
[226313.742] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[226313.742] (II) RADEON(0): Sync:  Separate
[226313.742] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[226313.742] (II) RADEON(0): Gamma: 2.07
[226313.742] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[226313.742] (II) RADEON(0): First detailed timing is preferred mode
[226313.742] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[226313.742] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[226313.742] (II) RADEON(0): Supported established timings:
[226313.742] (II) RADEON(0): 720x400@70Hz
[226313.742] (II) RADEON(0): 640x480@60Hz
[226313.742] (II) RADEON(0): 640x480@75Hz
[226313.742] (II) RADEON(0): 800x600@60Hz
[226313.742] (II) RADEON(0): 800x600@75Hz
[226313.742] (II) RADEON(0): 1024x768@60Hz
[226313.742] (II) RADEON(0): 1024x768@70Hz
[226313.742] (II) RADEON(0): 1024x768@75Hz
[226313.742] (II) RADEON(0): 1280x1024@75Hz
[226313.742] (II) RADEON(0): Manufacturer's mask: 0
[226313.742] (II) RADEON(0): Supported standard timings:
[226313.742] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[226313.742] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[226313.742] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[226313.742] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[226313.742] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[226313.742] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[226313.742] (II) RADEON(0): Supported detailed timing:
[226313.742] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[226313.742] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[226313.742] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[226313.742] (II) RADEON(0): Serial No: ETL4008012
[226313.742] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[226313.742] (II) RADEON(0): Monitor name: Acer AL1751
[226313.743] (II) RADEON(0): EDID (in hex):
[226313.743] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[226313.743] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[226313.743] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[226313.743] (II) RADEON(0):     454001010101302a009851002a403070
[226313.743] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[226313.743] (II) RADEON(0):     343030383031320a2020000000fd0037
[226313.743] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[226313.743] (II) RADEON(0):     004163657220414c313735310a20009b
[226313.743] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[226313.743] (II) RADEON(0): Using EDID range info for horizontal sync
[226313.743] (II) RADEON(0): Using EDID range info for vertical refresh
[226313.743] (II) RADEON(0): Printing DDC gathered Modelines:
[226313.743] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[226313.743] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[226313.743] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[226313.743] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[226313.743] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[226313.743] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[226313.743] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[226313.743] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[226313.743] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[226313.743] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[226313.743] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[226313.743] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[226313.743] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[226313.743] (II) RADEON(0): Year: 2005  Week: 40
[226313.743] (II) RADEON(0): EDID Version: 1.3
[226313.743] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[226313.743] (II) RADEON(0): Sync:  Separate
[226313.743] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[226313.743] (II) RADEON(0): Gamma: 2.07
[226313.743] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[226313.743] (II) RADEON(0): First detailed timing is preferred mode
[226313.743] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[226313.743] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[226313.743] (II) RADEON(0): Supported established timings:
[226313.743] (II) RADEON(0): 720x400@70Hz
[226313.743] (II) RADEON(0): 640x480@60Hz
[226313.743] (II) RADEON(0): 640x480@75Hz
[226313.743] (II) RADEON(0): 800x600@60Hz
[226313.743] (II) RADEON(0): 800x600@75Hz
[226313.743] (II) RADEON(0): 1024x768@60Hz
[226313.743] (II) RADEON(0): 1024x768@70Hz
[226313.743] (II) RADEON(0): 1024x768@75Hz
[226313.743] (II) RADEON(0): 1280x1024@75Hz
[226313.743] (II) RADEON(0): Manufacturer's mask: 0
[226313.743] (II) RADEON(0): Supported standard timings:
[226313.743] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[226313.743] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[226313.743] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[226313.743] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[226313.743] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[226313.743] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[226313.743] (II) RADEON(0): Supported detailed timing:
[226313.743] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[226313.743] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[226313.743] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[226313.743] (II) RADEON(0): Serial No: ETL4008012
[226313.743] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[226313.743] (II) RADEON(0): Monitor name: Acer AL1751
[226313.743] (II) RADEON(0): EDID (in hex):
[226313.743] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[226313.743] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[226313.743] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[226313.743] (II) RADEON(0):     454001010101302a009851002a403070
[226313.743] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[226313.743] (II) RADEON(0):     343030383031320a2020000000fd0037
[226313.743] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[226313.743] (II) RADEON(0):     004163657220414c313735310a20009b
[226313.743] finished output detect: 0
[226313.743] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[226313.746] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[226313.746] finished output detect: 1
[226313.746] finished all detect
[226313.796] (II) RADEON(0): EDID for output VGA-0
[226313.796] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[226313.796] (II) RADEON(0): Year: 2005  Week: 40
[226313.796] (II) RADEON(0): EDID Version: 1.3
[226313.796] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[226313.796] (II) RADEON(0): Sync:  Separate
[226313.796] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[226313.796] (II) RADEON(0): Gamma: 2.07
[226313.796] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[226313.796] (II) RADEON(0): First detailed timing is preferred mode
[226313.796] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[226313.796] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[226313.796] (II) RADEON(0): Supported established timings:
[226313.796] (II) RADEON(0): 720x400@70Hz
[226313.796] (II) RADEON(0): 640x480@60Hz
[226313.796] (II) RADEON(0): 640x480@75Hz
[226313.796] (II) RADEON(0): 800x600@60Hz
[226313.796] (II) RADEON(0): 800x600@75Hz
[226313.796] (II) RADEON(0): 1024x768@60Hz
[226313.796] (II) RADEON(0): 1024x768@70Hz
[226313.796] (II) RADEON(0): 1024x768@75Hz
[226313.796] (II) RADEON(0): 1280x1024@75Hz
[226313.796] (II) RADEON(0): Manufacturer's mask: 0
[226313.796] (II) RADEON(0): Supported standard timings:
[226313.796] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[226313.796] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[226313.796] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[226313.796] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[226313.796] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[226313.796] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[226313.796] (II) RADEON(0): Supported detailed timing:
[226313.796] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[226313.796] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[226313.796] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[226313.796] (II) RADEON(0): Serial No: ETL4008012
[226313.796] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[226313.796] (II) RADEON(0): Monitor name: Acer AL1751
[226313.796] (II) RADEON(0): EDID (in hex):
[226313.796] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[226313.796] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[226313.796] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[226313.796] (II) RADEON(0):     454001010101302a009851002a403070
[226313.796] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[226313.796] (II) RADEON(0):     343030383031320a2020000000fd0037
[226313.796] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[226313.796] (II) RADEON(0):     004163657220414c313735310a20009b
[226313.796] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[226313.796] (II) RADEON(0): Using hsync ranges from config file
[226313.796] (II) RADEON(0): Using vrefresh ranges from config file
[226313.796] (II) RADEON(0): Printing DDC gathered Modelines:
[226313.796] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[226313.796] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[226313.796] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[226313.796] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[226313.796] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[226313.796] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[226313.796] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[226313.796] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[226313.796] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[226313.796] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[226313.796] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[226313.796] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[226313.796] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[226313.796] (II) RADEON(0): Year: 2005  Week: 40
[226313.796] (II) RADEON(0): EDID Version: 1.3
[226313.796] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[226313.796] (II) RADEON(0): Sync:  Separate
[226313.796] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[226313.796] (II) RADEON(0): Gamma: 2.07
[226313.796] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[226313.796] (II) RADEON(0): First detailed timing is preferred mode
[226313.796] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[226313.796] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[226313.796] (II) RADEON(0): Supported established timings:
[226313.796] (II) RADEON(0): 720x400@70Hz
[226313.796] (II) RADEON(0): 640x480@60Hz
[226313.796] (II) RADEON(0): 640x480@75Hz
[226313.796] (II) RADEON(0): 800x600@60Hz
[226313.796] (II) RADEON(0): 800x600@75Hz
[226313.796] (II) RADEON(0): 1024x768@60Hz
[226313.796] (II) RADEON(0): 1024x768@70Hz
[226313.796] (II) RADEON(0): 1024x768@75Hz
[226313.796] (II) RADEON(0): 1280x1024@75Hz
[226313.796] (II) RADEON(0): Manufacturer's mask: 0
[226313.796] (II) RADEON(0): Supported standard timings:
[226313.796] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[226313.796] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[226313.796] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[226313.796] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[226313.796] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[226313.796] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[226313.796] (II) RADEON(0): Supported detailed timing:
[226313.796] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[226313.796] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[226313.796] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[226313.796] (II) RADEON(0): Serial No: ETL4008012
[226313.796] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[226313.796] (II) RADEON(0): Monitor name: Acer AL1751
[226313.796] (II) RADEON(0): EDID (in hex):
[226313.796] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[226313.796] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[226313.796] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[226313.796] (II) RADEON(0):     454001010101302a009851002a403070
[226313.796] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[226313.796] (II) RADEON(0):     343030383031320a2020000000fd0037
[226313.796] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[226313.796] (II) RADEON(0):     004163657220414c313735310a20009b
[226313.796] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[226313.796] (II) RADEON(0): Printing probed modes for output VGA-0
[226313.796] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[226313.796] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[226313.796] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[226313.796] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[226313.796] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[226313.796] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[226313.796] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[226313.796] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[226313.796] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[226313.796] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[226313.799] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[226313.799] (II) RADEON(0): EDID for output DVI-0
[226313.799] (II) RADEON(0): Output VGA-0 connected
[226313.799] (II) RADEON(0): Output DVI-0 disconnected
[226313.799] (II) RADEON(0): Using exact sizes for initial modes
[226313.799] (II) RADEON(0): Output VGA-0 using initial mode 1280x1024
[226313.799] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[226313.799] (**) RADEON(0): Display dimensions: (340, 270) mm
[226313.799] (**) RADEON(0): DPI set to (95, 120)
[226313.799] (II) Loading sub module "fb"
[226313.799] (II) LoadModule: "fb"
[226313.800] (II) Loading /usr/lib/xorg/modules/libfb.so
[226313.800] (II) Module fb: vendor="X.Org Foundation"
[226313.800]     compiled for 1.11.3, module version = 1.0.0
[226313.800]     ABI class: X.Org ANSI C Emulation, version 0.4
[226313.800] (II) Loading sub module "ramdac"
[226313.800] (II) LoadModule: "ramdac"
[226313.800] (II) Module "ramdac" already built-in
[226313.800] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[226313.800] (II) UnloadModule: "fglrx"
[226313.800] (II) Unloading fglrx
[226313.800] (II) UnloadModule: "fglrxdrm"
[226313.800] (II) Unloading fglrxdrm
[226313.800] (II) UnloadModule: "vesa"
[226313.800] (II) Unloading vesa
[226313.800] (II) UnloadModule: "fbdev"
[226313.800] (II) Unloading fbdev
[226313.800] (II) UnloadModule: "fbdevhw"
[226313.800] (II) Unloading fbdevhw
[226313.800] (--) Depth 24 pixmap format is 32 bpp
[226313.800] (II) RADEON(0): RADEONScreenInit d0000000 0 0
[226313.824] Output CRT1 disable success
[226313.824] Blank CRTC 0 success
[226313.824] Disable CRTC memreq 0 success
[226313.824] Disable CRTC 0 success
[226313.824] Blank CRTC 1 success
[226313.824] Disable CRTC memreq 1 success
[226313.824] Disable CRTC 1 success
[226313.824] (II) RADEON(0): Dynamic Power Management Disabled
[226313.825] (II) RADEON(0): RADEONInitMemoryMap() : 
[226313.825] (II) RADEON(0):   mem_size         : 0x10000000
[226313.825] (II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0
[226313.825] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[226313.825] (II) RADEON(0): Depth moves disabled by default
[226313.825] (II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
[226313.825] (II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
[226313.825] (II) RADEON(0): Largest offscreen area available: 1280 x 6909
[226313.825] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[226313.825] (II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0 0x00cf00c0
[226313.825] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[226313.835] (==) RADEON(0): Backing store disabled
[226313.835] (WW) RADEON(0): Direct rendering disabled
[226313.835] (EE) RADEON(0): Acceleration initialization failed
[226313.835] (II) RADEON(0): Acceleration disabled
[226313.835] (==) RADEON(0): DPMS enabled
[226313.835] (==) RADEON(0): Silken mouse enabled
[226313.835] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00643000
[226313.835] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00648000
[226313.835] (II) RADEON(0): Largest offscreen area available: 1280 x 6901
[226313.835] (II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
[226313.849] Output CRT1 disable success
[226313.849] Output DIG0 transmitter setup success
[226313.849] Blank CRTC 0 success
[226313.849] Disable CRTC memreq 0 success
[226313.849] Disable CRTC 0 success
[226313.849] Blank CRTC 1 success
[226313.849] Disable CRTC memreq 1 success
[226313.849] Disable CRTC 1 success
[226313.849] Output CRT1 disable success
[226313.849] Blank CRTC 0 success
[226313.849] Disable CRTC memreq 0 success
[226313.849] Disable CRTC 0 success
[226313.849] Set CRTC 0 Source success
[226313.849] Mode 1280x1024 - 1688 1066 5
[226313.849] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[226313.849] (II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0 0x00cf00c0
[226313.849] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[226313.859] Picked PLL 0
[226313.860] before 10800
[226313.860] after 10800
[226313.860] best_freq: 108050
[226313.860] best_feedback_div: 166
[226313.860] best_frac_feedback_div: 0
[226313.860] best_ref_div: 2
[226313.860] best_post_div: 11
[226313.860] (II) RADEON(0): crtc(0) Clock: mode 108000, PLL 1080500
[226313.860] (II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0xA6(166), fracfbdiv 0, pdiv 11
[226313.863] Set CRTC 0 PLL success
[226313.863] Set CRTC Timing success
[226313.863] Set CRTC 0 Overscan success
[226313.863] Not using RMX
[226313.863] scaler 0 setup success
[226313.863] Set CRTC 0 Source success
[226313.863] crtc 0 YUV disable setup success
[226313.863] Output DAC1 setup success
[226313.864] Output CRT1 enable success
[226313.864] Enable CRTC 0 success
[226313.864] Enable CRTC memreq 0 success
[226313.864] Unblank CRTC 0 success
[226313.864] Output DIG0 transmitter setup success
[226313.864] Blank CRTC 1 success
[226313.864] Disable CRTC memreq 1 success
[226313.864] Disable CRTC 1 success
[226313.864] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[226313.864] (--) RandR disabled
[226313.864] (II) Initializing built-in extension Generic Event Extension
[226313.864] (II) Initializing built-in extension SHAPE
[226313.864] (II) Initializing built-in extension MIT-SHM
[226313.864] (II) Initializing built-in extension XInputExtension
[226313.864] (II) Initializing built-in extension XTEST
[226313.864] (II) Initializing built-in extension BIG-REQUESTS
[226313.864] (II) Initializing built-in extension SYNC
[226313.864] (II) Initializing built-in extension XKEYBOARD
[226313.864] (II) Initializing built-in extension XC-MISC
[226313.864] (II) Initializing built-in extension SECURITY
[226313.864] (II) Initializing built-in extension XINERAMA
[226313.864] (II) Initializing built-in extension XFIXES
[226313.864] (II) Initializing built-in extension RENDER
[226313.864] (II) Initializing built-in extension RANDR
[226313.864] (II) Initializing built-in extension COMPOSITE
[226313.865] (II) Initializing built-in extension DAMAGE
[226313.878] (EE) GLX error: Can not get required symbols.
[226313.878] (II) RADEON(0): Setting screen physical size to 338 x 270
[226313.887] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[226313.889] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[226313.889] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[226313.889] (II) LoadModule: "evdev"
[226313.889] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[226313.890] (II) Module evdev: vendor="X.Org Foundation"
[226313.890]     compiled for 1.11.3, module version = 2.7.0
[226313.890]     Module class: X.Org XInput Driver
[226313.890]     ABI class: X.Org XInput driver, version 16.0
[226313.890] (II) Using input driver 'evdev' for 'Power Button'
[226313.890] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[226313.890] (**) Power Button: always reports core events
[226313.890] (**) evdev: Power Button: Device: "/dev/input/event1"
[226313.890] (--) evdev: Power Button: Vendor 0 Product 0x1
[226313.890] (--) evdev: Power Button: Found keys
[226313.890] (II) evdev: Power Button: Configuring as keyboard
[226313.890] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[226313.890] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[226313.890] (**) Option "xkb_rules" "evdev"
[226313.890] (**) Option "xkb_model" "pc105"
[226313.890] (**) Option "xkb_layout" "fr"
[226313.890] (**) Option "xkb_variant" "oss"
[226313.891] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[226313.892] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[226313.892] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[226313.892] (II) Using input driver 'evdev' for 'Power Button'
[226313.892] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[226313.892] (**) Power Button: always reports core events
[226313.892] (**) evdev: Power Button: Device: "/dev/input/event0"
[226313.892] (--) evdev: Power Button: Vendor 0 Product 0x1
[226313.892] (--) evdev: Power Button: Found keys
[226313.892] (II) evdev: Power Button: Configuring as keyboard
[226313.892] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[226313.892] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[226313.892] (**) Option "xkb_rules" "evdev"
[226313.892] (**) Option "xkb_model" "pc105"
[226313.892] (**) Option "xkb_layout" "fr"
[226313.892] (**) Option "xkb_variant" "oss"
[226313.892] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event2)
[226313.892] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[226313.892] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[226313.892] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[226313.893] (**) Logitech USB Keyboard: always reports core events
[226313.893] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event2"
[226313.893] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[226313.893] (--) evdev: Logitech USB Keyboard: Found keys
[226313.893] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[226313.893] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input2/event2"
[226313.893] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 8)
[226313.893] (**) Option "xkb_rules" "evdev"
[226313.893] (**) Option "xkb_model" "pc105"
[226313.893] (**) Option "xkb_layout" "fr"
[226313.893] (**) Option "xkb_variant" "oss"
[226313.893] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event3)
[226313.893] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[226313.893] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[226313.893] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[226313.893] (**) Logitech USB Keyboard: always reports core events
[226313.893] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event3"
[226313.893] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[226313.893] (--) evdev: Logitech USB Keyboard: Found absolute axes
[226313.893] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[226313.893] (--) evdev: Logitech USB Keyboard: Found keys
[226313.893] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[226313.893] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[226313.893] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input3/event3"
[226313.893] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 9)
[226313.893] (**) Option "xkb_rules" "evdev"
[226313.893] (**) Option "xkb_model" "pc105"
[226313.893] (**) Option "xkb_layout" "fr"
[226313.893] (**) Option "xkb_variant" "oss"
[226313.894] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[226313.894] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[226313.894] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[226313.894] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[226313.894] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[226313.894] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event4)
[226313.894] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[226313.894] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[226313.894] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[226313.894] (**) Logitech USB Optical Mouse: always reports core events
[226313.894] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event4"
[226313.894] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[226313.894] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[226313.894] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[226313.894] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[226313.894] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[226313.894] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[226313.894] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[226313.894] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[226313.894] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[226313.894] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4/event4"
[226313.894] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 10)
[226313.894] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[226313.894] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[226313.894] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[226313.894] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[226313.894] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[226313.895] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[226313.895] (II) No input driver specified, ignoring this device.
[226313.895] (II) This device may have been added with another device file.
[226313.895] (II) config/udev: Adding input device HDA ATI SB Line-Out CLFE (/dev/input/event10)
[226313.895] (II) No input driver specified, ignoring this device.
[226313.895] (II) This device may have been added with another device file.
[226313.895] (II) config/udev: Adding input device HDA ATI SB Line-Out Surround (/dev/input/event11)
[226313.895] (II) No input driver specified, ignoring this device.
[226313.895] (II) This device may have been added with another device file.
[226313.895] (II) config/udev: Adding input device HDA ATI SB Line-Out Front (/dev/input/event12)
[226313.895] (II) No input driver specified, ignoring this device.
[226313.895] (II) This device may have been added with another device file.
[226313.895] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event5)
[226313.895] (II) No input driver specified, ignoring this device.
[226313.895] (II) This device may have been added with another device file.
[226313.895] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event6)
[226313.895] (II) No input driver specified, ignoring this device.
[226313.895] (II) This device may have been added with another device file.
[226313.896] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event7)
[226313.896] (II) No input driver specified, ignoring this device.
[226313.896] (II) This device may have been added with another device file.
[226313.896] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event8)
[226313.896] (II) No input driver specified, ignoring this device.
[226313.896] (II) This device may have been added with another device file.
[226313.896] (II) config/udev: Adding input device HDA ATI SB Line-Out Side (/dev/input/event9)
[226313.896] (II) No input driver specified, ignoring this device.
[226313.896] (II) This device may have been added with another device file.
[226314.275] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[226314.275] (II) RADEON(0): Using hsync ranges from config file
[226314.275] (II) RADEON(0): Using vrefresh ranges from config file
[226314.275] (II) RADEON(0): Printing DDC gathered Modelines:
[226314.275] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[226314.275] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[226314.275] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[226314.275] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[226314.275] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[226314.275] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[226314.275] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[226314.275] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[226314.275] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[226314.275] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[226314.275] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[226314.275] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[226314.275] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[226314.275] (II) RADEON(0): Year: 2005  Week: 40
[226314.275] (II) RADEON(0): EDID Version: 1.3
[226314.275] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[226314.275] (II) RADEON(0): Sync:  Separate
[226314.275] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[226314.275] (II) RADEON(0): Gamma: 2.07
[226314.275] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[226314.275] (II) RADEON(0): First detailed timing is preferred mode
[226314.275] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[226314.275] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[226314.275] (II) RADEON(0): Supported established timings:
[226314.275] (II) RADEON(0): 720x400@70Hz
[226314.275] (II) RADEON(0): 640x480@60Hz
[226314.275] (II) RADEON(0): 640x480@75Hz
[226314.275] (II) RADEON(0): 800x600@60Hz
[226314.275] (II) RADEON(0): 800x600@75Hz
[226314.275] (II) RADEON(0): 1024x768@60Hz
[226314.275] (II) RADEON(0): 1024x768@70Hz
[226314.275] (II) RADEON(0): 1024x768@75Hz
[226314.275] (II) RADEON(0): 1280x1024@75Hz
[226314.275] (II) RADEON(0): Manufacturer's mask: 0
[226314.275] (II) RADEON(0): Supported standard timings:
[226314.275] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[226314.275] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[226314.275] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[226314.275] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[226314.275] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[226314.275] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[226314.275] (II) RADEON(0): Supported detailed timing:
[226314.275] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[226314.275] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[226314.275] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[226314.275] (II) RADEON(0): Serial No: ETL4008012
[226314.275] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[226314.275] (II) RADEON(0): Monitor name: Acer AL1751
[226314.275] (II) RADEON(0): EDID (in hex):
[226314.275] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[226314.275] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[226314.275] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[226314.275] (II) RADEON(0):     454001010101302a009851002a403070
[226314.275] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[226314.275] (II) RADEON(0):     343030383031320a2020000000fd0037
[226314.275] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[226314.275] (II) RADEON(0):     004163657220414c313735310a20009b
[226314.275] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[226314.278] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[226314.646] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[226314.647] (II) RADEON(0): Using hsync ranges from config file
[226314.647] (II) RADEON(0): Using vrefresh ranges from config file
[226314.647] (II) RADEON(0): Printing DDC gathered Modelines:
[226314.647] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[226314.647] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[226314.647] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[226314.647] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[226314.647] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[226314.647] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[226314.647] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[226314.647] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[226314.647] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[226314.647] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[226314.647] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[226314.647] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[226314.647] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[226314.647] (II) RADEON(0): Year: 2005  Week: 40
[226314.647] (II) RADEON(0): EDID Version: 1.3
[226314.647] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[226314.647] (II) RADEON(0): Sync:  Separate
[226314.647] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[226314.647] (II) RADEON(0): Gamma: 2.07
[226314.647] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[226314.647] (II) RADEON(0): First detailed timing is preferred mode
[226314.647] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[226314.647] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[226314.647] (II) RADEON(0): Supported established timings:
[226314.647] (II) RADEON(0): 720x400@70Hz
[226314.647] (II) RADEON(0): 640x480@60Hz
[226314.647] (II) RADEON(0): 640x480@75Hz
[226314.647] (II) RADEON(0): 800x600@60Hz
[226314.647] (II) RADEON(0): 800x600@75Hz
[226314.647] (II) RADEON(0): 1024x768@60Hz
[226314.647] (II) RADEON(0): 1024x768@70Hz
[226314.647] (II) RADEON(0): 1024x768@75Hz
[226314.647] (II) RADEON(0): 1280x1024@75Hz
[226314.647] (II) RADEON(0): Manufacturer's mask: 0
[226314.647] (II) RADEON(0): Supported standard timings:
[226314.647] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[226314.647] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[226314.647] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[226314.647] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[226314.647] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[226314.647] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[226314.647] (II) RADEON(0): Supported detailed timing:
[226314.647] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[226314.647] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[226314.647] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[226314.647] (II) RADEON(0): Serial No: ETL4008012
[226314.647] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[226314.647] (II) RADEON(0): Monitor name: Acer AL1751
[226314.647] (II) RADEON(0): EDID (in hex):
[226314.647] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[226314.647] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[226314.647] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[226314.647] (II) RADEON(0):     454001010101302a009851002a403070
[226314.647] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[226314.647] (II) RADEON(0):     343030383031320a2020000000fd0037
[226314.647] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[226314.647] (II) RADEON(0):     004163657220414c313735310a20009b
[226314.647] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[226314.650] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[226323.496] Output CRT1 disable success
[226323.507] Blank CRTC 0 success
[226323.507] Disable CRTC memreq 0 success
[226323.507] Disable CRTC 0 success
[226323.507] Blank CRTC 1 success
[226323.507] Disable CRTC memreq 1 success
[226323.507] Disable CRTC 1 success
[226323.507] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[226323.507] (II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0 0x00cf00c0
[226323.507] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000
[226323.517] (II) RADEON(0): avivo_restore !
[226323.618] Enable CRTC 0 success
[226323.618] Enable CRTC memreq 0 success
[226323.618] Unblank CRTC 0 success
[226329.866] (II) Open ACPI successful (/var/run/acpid.socket)
[226329.877] Output CRT1 disable success
[226329.877] Output DIG0 transmitter setup success
[226329.880] Blank CRTC 0 success
[226329.880] Disable CRTC memreq 0 success
[226329.897] Disable CRTC 0 success
[226329.897] Blank CRTC 1 success
[226329.897] Disable CRTC memreq 1 success
[226329.897] Disable CRTC 1 success
[226329.897] Output CRT1 disable success
[226329.897] Blank CRTC 0 success
[226329.897] Disable CRTC memreq 0 success
[226329.897] Disable CRTC 0 success
[226329.897] Set CRTC 0 Source success
[226329.897] Mode 1280x1024 - 1688 1066 5
[226329.897] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[226329.897] (II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0 0x00cf00c0
[226329.897] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[226329.907] Picked PLL 0
[226329.907] before 10800
[226329.907] after 10800
[226329.907] best_freq: 108050
[226329.907] best_feedback_div: 166
[226329.907] best_frac_feedback_div: 0
[226329.907] best_ref_div: 2
[226329.907] best_post_div: 11
[226329.907] (II) RADEON(0): crtc(0) Clock: mode 108000, PLL 1080500
[226329.907] (II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0xA6(166), fracfbdiv 0, pdiv 11
[226329.910] Set CRTC 0 PLL success
[226329.910] Set CRTC Timing success
[226329.910] Set CRTC 0 Overscan success
[226329.910] Not using RMX
[226329.910] scaler 0 setup success
[226329.910] Set CRTC 0 Source success
[226329.910] crtc 0 YUV disable setup success
[226329.910] Output DAC1 setup success
[226329.910] Output CRT1 enable success
[226329.910] Enable CRTC 0 success
[226329.910] Enable CRTC memreq 0 success
[226329.910] Unblank CRTC 0 success
[226329.910] Output DIG0 transmitter setup success
[226329.910] Blank CRTC 1 success
[226329.910] Disable CRTC memreq 1 success
[226329.910] Disable CRTC 1 success
[226329.960] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[226329.960] (II) RADEON(0): Using hsync ranges from config file
[226329.960] (II) RADEON(0): Using vrefresh ranges from config file
[226329.960] (II) RADEON(0): Printing DDC gathered Modelines:
[226329.960] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[226329.960] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[226329.960] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[226329.960] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[226329.960] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[226329.960] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[226329.960] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[226329.960] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[226329.960] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[226329.960] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[226329.960] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[226329.960] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[226329.960] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[226329.960] (II) RADEON(0): Year: 2005  Week: 40
[226329.960] (II) RADEON(0): EDID Version: 1.3
[226329.960] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[226329.960] (II) RADEON(0): Sync:  Separate
[226329.960] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[226329.960] (II) RADEON(0): Gamma: 2.07
[226329.960] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[226329.960] (II) RADEON(0): First detailed timing is preferred mode
[226329.960] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[226329.960] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[226329.960] (II) RADEON(0): Supported established timings:
[226329.960] (II) RADEON(0): 720x400@70Hz
[226329.960] (II) RADEON(0): 640x480@60Hz
[226329.960] (II) RADEON(0): 640x480@75Hz
[226329.960] (II) RADEON(0): 800x600@60Hz
[226329.960] (II) RADEON(0): 800x600@75Hz
[226329.960] (II) RADEON(0): 1024x768@60Hz
[226329.960] (II) RADEON(0): 1024x768@70Hz
[226329.960] (II) RADEON(0): 1024x768@75Hz
[226329.960] (II) RADEON(0): 1280x1024@75Hz
[226329.960] (II) RADEON(0): Manufacturer's mask: 0
[226329.960] (II) RADEON(0): Supported standard timings:
[226329.960] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[226329.960] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[226329.960] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[226329.960] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[226329.960] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[226329.960] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[226329.960] (II) RADEON(0): Supported detailed timing:
[226329.960] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[226329.960] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[226329.960] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[226329.960] (II) RADEON(0): Serial No: ETL4008012
[226329.960] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[226329.960] (II) RADEON(0): Monitor name: Acer AL1751
[226329.960] (II) RADEON(0): EDID (in hex):
[226329.960] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[226329.960] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[226329.960] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[226329.960] (II) RADEON(0):     454001010101302a009851002a403070
[226329.960] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[226329.960] (II) RADEON(0):     343030383031320a2020000000fd0037
[226329.960] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[226329.960] (II) RADEON(0):     004163657220414c313735310a20009b
[226329.960] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[226329.963] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[226934.721] Output CRT1 disable success
[226934.736] Blank CRTC 0 success
[226934.736] Disable CRTC memreq 0 success
[226934.753] Disable CRTC 0 success
[226934.753] Blank CRTC 1 success
[226934.753] Disable CRTC memreq 1 success
[226934.753] Disable CRTC 1 success
[226960.677] Enable CRTC 0 success
[226960.677] Enable CRTC memreq 0 success
[226960.677] Unblank CRTC 0 success
[226960.677] Output CRT1 enable success
[226960.677] Output CRT1 disable success
[226960.677] Blank CRTC 0 success
[226960.677] Disable CRTC memreq 0 success
[226960.693] Disable CRTC 0 success
[239109.314] Enable CRTC 0 success
[239109.314] Enable CRTC memreq 0 success
[239109.314] Unblank CRTC 0 success
[239109.314] Output CRT1 enable success
[239124.670] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[239124.670] (II) RADEON(0): Using hsync ranges from config file
[239124.670] (II) RADEON(0): Using vrefresh ranges from config file
[239124.670] (II) RADEON(0): Printing DDC gathered Modelines:
[239124.670] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[239124.670] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[239124.670] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[239124.670] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[239124.670] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[239124.670] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[239124.670] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[239124.670] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[239124.670] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[239124.670] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[239124.670] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[239124.670] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[239124.670] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[239124.670] (II) RADEON(0): Year: 2005  Week: 40
[239124.670] (II) RADEON(0): EDID Version: 1.3
[239124.670] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[239124.670] (II) RADEON(0): Sync:  Separate
[239124.670] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[239124.670] (II) RADEON(0): Gamma: 2.07
[239124.670] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[239124.670] (II) RADEON(0): First detailed timing is preferred mode
[239124.670] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[239124.670] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[239124.670] (II) RADEON(0): Supported established timings:
[239124.670] (II) RADEON(0): 720x400@70Hz
[239124.670] (II) RADEON(0): 640x480@60Hz
[239124.670] (II) RADEON(0): 640x480@75Hz
[239124.670] (II) RADEON(0): 800x600@60Hz
[239124.670] (II) RADEON(0): 800x600@75Hz
[239124.670] (II) RADEON(0): 1024x768@60Hz
[239124.670] (II) RADEON(0): 1024x768@70Hz
[239124.670] (II) RADEON(0): 1024x768@75Hz
[239124.670] (II) RADEON(0): 1280x1024@75Hz
[239124.670] (II) RADEON(0): Manufacturer's mask: 0
[239124.670] (II) RADEON(0): Supported standard timings:
[239124.670] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[239124.670] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[239124.670] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[239124.670] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[239124.670] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[239124.670] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[239124.670] (II) RADEON(0): Supported detailed timing:
[239124.670] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[239124.670] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[239124.670] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[239124.670] (II) RADEON(0): Serial No: ETL4008012
[239124.670] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[239124.670] (II) RADEON(0): Monitor name: Acer AL1751
[239124.670] (II) RADEON(0): EDID (in hex):
[239124.670] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[239124.670] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[239124.670] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[239124.670] (II) RADEON(0):     454001010101302a009851002a403070
[239124.670] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[239124.670] (II) RADEON(0):     343030383031320a2020000000fd0037
[239124.670] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[239124.670] (II) RADEON(0):     004163657220414c313735310a20009b
[239124.670] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[239124.674] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[239126.689] (II) XKB: reuse xkmfile /var/lib/xkb/server-C4EEEB2339CB62D111EF0238C126FD797045434D.xkm
[239130.912] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[239130.912] (II) RADEON(0): Using hsync ranges from config file
[239130.912] (II) RADEON(0): Using vrefresh ranges from config file
[239130.912] (II) RADEON(0): Printing DDC gathered Modelines:
[239130.912] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[239130.912] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[239130.912] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[239130.912] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[239130.912] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[239130.912] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[239130.912] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[239130.912] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[239130.912] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[239130.912] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[239130.912] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[239130.912] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[239130.912] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[239130.912] (II) RADEON(0): Year: 2005  Week: 40
[239130.912] (II) RADEON(0): EDID Version: 1.3
[239130.912] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[239130.912] (II) RADEON(0): Sync:  Separate
[239130.912] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[239130.912] (II) RADEON(0): Gamma: 2.07
[239130.912] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[239130.912] (II) RADEON(0): First detailed timing is preferred mode
[239130.912] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[239130.912] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[239130.912] (II) RADEON(0): Supported established timings:
[239130.912] (II) RADEON(0): 720x400@70Hz
[239130.912] (II) RADEON(0): 640x480@60Hz
[239130.912] (II) RADEON(0): 640x480@75Hz
[239130.912] (II) RADEON(0): 800x600@60Hz
[239130.912] (II) RADEON(0): 800x600@75Hz
[239130.912] (II) RADEON(0): 1024x768@60Hz
[239130.912] (II) RADEON(0): 1024x768@70Hz
[239130.912] (II) RADEON(0): 1024x768@75Hz
[239130.912] (II) RADEON(0): 1280x1024@75Hz
[239130.912] (II) RADEON(0): Manufacturer's mask: 0
[239130.912] (II) RADEON(0): Supported standard timings:
[239130.912] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[239130.912] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[239130.912] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[239130.912] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[239130.912] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[239130.912] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[239130.912] (II) RADEON(0): Supported detailed timing:
[239130.912] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[239130.912] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[239130.912] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[239130.912] (II) RADEON(0): Serial No: ETL4008012
[239130.912] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[239130.912] (II) RADEON(0): Monitor name: Acer AL1751
[239130.912] (II) RADEON(0): EDID (in hex):
[239130.912] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[239130.912] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[239130.912] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[239130.912] (II) RADEON(0):     454001010101302a009851002a403070
[239130.912] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[239130.912] (II) RADEON(0):     343030383031320a2020000000fd0037
[239130.912] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[239130.912] (II) RADEON(0):     004163657220414c313735310a20009b
[239130.912] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[239130.916] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[239148.726] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[239148.726] (II) RADEON(0): Using hsync ranges from config file
[239148.726] (II) RADEON(0): Using vrefresh ranges from config file
[239148.726] (II) RADEON(0): Printing DDC gathered Modelines:
[239148.726] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[239148.726] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[239148.726] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[239148.726] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[239148.726] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[239148.726] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[239148.726] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[239148.726] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[239148.726] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[239148.726] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[239148.726] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[239148.726] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[239148.726] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[239148.726] (II) RADEON(0): Year: 2005  Week: 40
[239148.726] (II) RADEON(0): EDID Version: 1.3
[239148.726] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[239148.726] (II) RADEON(0): Sync:  Separate
[239148.726] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[239148.726] (II) RADEON(0): Gamma: 2.07
[239148.726] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[239148.726] (II) RADEON(0): First detailed timing is preferred mode
[239148.726] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[239148.726] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[239148.726] (II) RADEON(0): Supported established timings:
[239148.726] (II) RADEON(0): 720x400@70Hz
[239148.726] (II) RADEON(0): 640x480@60Hz
[239148.726] (II) RADEON(0): 640x480@75Hz
[239148.726] (II) RADEON(0): 800x600@60Hz
[239148.726] (II) RADEON(0): 800x600@75Hz
[239148.726] (II) RADEON(0): 1024x768@60Hz
[239148.726] (II) RADEON(0): 1024x768@70Hz
[239148.726] (II) RADEON(0): 1024x768@75Hz
[239148.726] (II) RADEON(0): 1280x1024@75Hz
[239148.726] (II) RADEON(0): Manufacturer's mask: 0
[239148.726] (II) RADEON(0): Supported standard timings:
[239148.726] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[239148.726] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[239148.726] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[239148.726] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[239148.726] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[239148.726] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[239148.726] (II) RADEON(0): Supported detailed timing:
[239148.726] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[239148.726] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[239148.726] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[239148.727] (II) RADEON(0): Serial No: ETL4008012
[239148.727] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[239148.727] (II) RADEON(0): Monitor name: Acer AL1751
[239148.727] (II) RADEON(0): EDID (in hex):
[239148.727] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[239148.727] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[239148.727] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[239148.727] (II) RADEON(0):     454001010101302a009851002a403070
[239148.727] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[239148.727] (II) RADEON(0):     343030383031320a2020000000fd0037
[239148.727] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[239148.727] (II) RADEON(0):     004163657220414c313735310a20009b
[239148.727] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[239148.730] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[240078.980] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[240078.980] (II) RADEON(0): Using hsync ranges from config file
[240078.980] (II) RADEON(0): Using vrefresh ranges from config file
[240078.980] (II) RADEON(0): Printing DDC gathered Modelines:
[240078.980] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[240078.980] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[240078.980] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[240078.980] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[240078.980] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[240078.980] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[240078.980] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[240078.980] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[240078.980] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[240078.980] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[240078.980] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[240078.980] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[240078.980] (II) RADEON(0): Manufacturer: ACR  Model: ad40  Serial#: 1409289203
[240078.980] (II) RADEON(0): Year: 2005  Week: 40
[240078.980] (II) RADEON(0): EDID Version: 1.3
[240078.980] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[240078.980] (II) RADEON(0): Sync:  Separate
[240078.980] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[240078.980] (II) RADEON(0): Gamma: 2.07
[240078.980] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[240078.980] (II) RADEON(0): First detailed timing is preferred mode
[240078.980] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
[240078.980] (II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
[240078.980] (II) RADEON(0): Supported established timings:
[240078.980] (II) RADEON(0): 720x400@70Hz
[240078.980] (II) RADEON(0): 640x480@60Hz
[240078.980] (II) RADEON(0): 640x480@75Hz
[240078.980] (II) RADEON(0): 800x600@60Hz
[240078.980] (II) RADEON(0): 800x600@75Hz
[240078.980] (II) RADEON(0): 1024x768@60Hz
[240078.980] (II) RADEON(0): 1024x768@70Hz
[240078.980] (II) RADEON(0): 1024x768@75Hz
[240078.980] (II) RADEON(0): 1280x1024@75Hz
[240078.980] (II) RADEON(0): Manufacturer's mask: 0
[240078.980] (II) RADEON(0): Supported standard timings:
[240078.980] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[240078.980] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[240078.980] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[240078.980] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[240078.980] (II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
[240078.980] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[240078.980] (II) RADEON(0): Supported detailed timing:
[240078.980] (II) RADEON(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[240078.980] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[240078.980] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[240078.980] (II) RADEON(0): Serial No: ETL4008012
[240078.980] (II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[240078.980] (II) RADEON(0): Monitor name: Acer AL1751
[240078.980] (II) RADEON(0): EDID (in hex):
[240078.980] (II) RADEON(0):     00ffffffffffff00047240adf30b0054
[240078.980] (II) RADEON(0):     280f010368221b6b2ac0f5a3574a9c23
[240078.980] (II) RADEON(0):     114f54a54f00818f8180614f6140454f
[240078.980] (II) RADEON(0):     454001010101302a009851002a403070
[240078.980] (II) RADEON(0):     1300540e1100001e000000ff0045544c
[240078.980] (II) RADEON(0):     343030383031320a2020000000fd0037
[240078.980] (II) RADEON(0):     4b1e530e000a202020202020000000fc
[240078.980] (II) RADEON(0):     004163657220414c313735310a20009b
[240078.980] (II) RADEON(0): EDID vendor "ACR", prod id 44352
[240078.983] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[240109.542] Output CRT1 disable success
[240109.557] Blank CRTC 0 success
[240109.557] Disable CRTC memreq 0 success
[240109.574] Disable CRTC 0 success
[240109.574] Blank CRTC 1 success
[240109.574] Disable CRTC memreq 1 success
[240109.574] Disable CRTC 1 success
[240109.574] Output CRT1 disable success
[240109.574] Blank CRTC 0 success
[240109.574] Disable CRTC memreq 0 success
[240109.574] Disable CRTC 0 success
[240556.287] Enable CRTC 0 success
[240556.287] Enable CRTC memreq 0 success
[240556.287] Unblank CRTC 0 success
[240556.287] Output CRT1 enable success
[242115.020] Output CRT1 disable success
[242115.021] Blank CRTC 0 success
[242115.021] Disable CRTC memreq 0 success
[242115.038] Disable CRTC 0 success
[242115.038] Blank CRTC 1 success
[242115.038] Disable CRTC memreq 1 success
[242115.038] Disable CRTC 1 success
[242115.038] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[242115.038] (II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0 0x00cf00c0
[242115.038] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000
[242115.048] (II) RADEON(0): avivo_restore !
[242115.148] Enable CRTC 0 success
[242115.148] Enable CRTC memreq 0 success
[242115.148] Unblank CRTC 0 success

```

---

### Post by Yellow Pasque on 2014-03-04
Okay, so you're running Ubuntu 12.04 and though your card is still supported by proprietary fglrx/Catalyst driver, you need the Legacy driver. You installed a version of Catalyst that does not support your card.

The first thing you want to do is completely remove that version of fglrx. Run the following commands (some will probably fail, but just keep going):
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
```

At this point, you should restart your system and you should have working 3D with the open-source driver. It's up to you whether that is sufficent or not. If you still want to have a go at installing fglrx/Catalyst:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4 lib32gcc1
cd ~/; mkdir catalyst; cd catalyst
wget --referer='http://support.amd.com/en-us/download/desktop?os=Linux+x86' http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
unzip amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
chmod +x amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run
sudo sh amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

---

### Post by christophe.maillot on 2014-03-04
The first thing you want to do is completely remove that version of  fglrx. Run the following commands (some will probably fail, but just  keep going):
 	Code:
 	```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati 

```

thank you Temüjin ... the above did it, games work again properly, but my computer seems to be a bit slow ... probably get better next restart ... 

one point : after closing lincity-ng the display on my screen got a bit ****ed up (very big font and icons)

what about the second part of code ? would that help with the problem I experience with Lincity ?

thanks

---

### Post by Yellow Pasque on 2014-03-04
It sounds like Lincity didn't reset the resolution. I don't think that 's a driver problem.

---

### Post by christophe.maillot on 2014-03-05
ok ... thanks a lot for your help Gengis ... marked as solved !

:-)

---

