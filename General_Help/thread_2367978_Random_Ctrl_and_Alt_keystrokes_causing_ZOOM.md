---
title: "Random Ctrl and Alt keystrokes causing ZOOM"
date: 2017-08-05
forum: General Help
---

### Post by crashk on 2017-08-05
I decided a couple weeks ago to swap my entire system to ubuntu. The problem I've been having since then is that whenever I'm trying to work some weird stuff happens.
I discover it is due to random keystrokes from ctrl and alt keys, My keyboard is working well.
This issue happened to me once before, and I solved it with an answer someone gave on this forum, I can't find it, tho, so I decided to create a new trend to it.
What I remember about the way to solve the issue is that the laptop's capslock key led would not turn on.

To describe my issue properly, let's start by saying that sometimes when I'm scrolling on a web browser it randomly zooms in and out, depending on whether I'm scrolling up or down. So, it must be a ctrl keystroke error.

While I'm typing this, sometimes when I press the 's' key it tells me to save the page, so it must be and Alt keystroke.

I'll try to be more specific in case someone needs to understand this in a better way.

Thanks.

---

### Post by Futant on 2017-08-05
Hi, the specs of your system might help, and the version number of your install. When you say this problem happened once before, was this is the last few weeks since you installed Ubuntu? If you can remember any more details that might be helpful. 

Are you sure your keyboard is working properly? Could the keys be sticking? Have you tried with a different keyboard (or checked yours in a different system)?

---

### Post by crashk on 2017-08-05
Thanks for replying.
I'm currently using ubuntu 16.04 LTS,
System Specs: HP 15 ab110la, which consists on AMD A10 processor, AMD R7 360M graphic processor, and the rest is basic stuff.
The laptop keyboard is working properly, I had windows a couple weeks ago, and everything was working perfectly.
I installed ubuntu a week ago, and the problem has happened since.
Back in time, almost 6 months, I had the same problem, I was dual-booting, and the problem only happened on ubuntu, I went ahead and searched for a solution, and oddly enough, I found it, but know, somehow I can't. So, that's why I decided to post is a thread.

---

### Post by Futant on 2017-08-06
Sounds like it could be a problem with Xorg, have a look at any errors in** /var/log/Xorg.0.log**, post the file on here as an attachment.

I'm by no means an expert, if I'm barking up the wrong tree let me know, someone.

Have you updated your system since installation? There's a slight possibility that might help.

---

### Post by crashk on 2017-08-06
Thanks for replying, again.

I'll post the entire log, cause I tried to find the error but I couldn't find anything.
```

[    41.501] (--) Log file renamed from "/var/log/Xorg.pid-1143.log" to "/var/log/Xorg.0.log"
[    41.552] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    41.552] X Protocol Version 11, Revision 0
[    41.552] Build Operating System: Linux 4.4.0-83-generic x86_64 Ubuntu
[    41.552] Current Operating System: Linux crash-HP-Pavilion-Notebook 4.4.0-89-generic #112-Ubuntu SMP Mon Jul 31 19:38:41 UTC 2017 x86_64
[    41.552] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-89-generic root=UUID=f02aa5f3-db5d-4081-b3d4-7d4791f46e64 ro quiet splash radeon.audio=1 vt.handoff=7
[    41.552] Build Date: 17 July 2017  05:05:12PM
[    41.553] xorg-server 2:1.18.4-0ubuntu0.3 (For technical support please see http://www.ubuntu.com/support) 
[    41.553] Current version of pixman: 0.33.6
[    41.553]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    41.553] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    41.553] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug  6 13:34:18 2017
[    41.553] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    41.879] (==) No Layout section.  Using the first Screen section.
[    41.879] (==) No screen section available. Using defaults.
[    41.879] (**) |-->Screen "Default Screen Section" (0)
[    41.879] (**) |   |-->Monitor "<default monitor>"
[    41.960] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    41.961] (==) Automatically adding devices
[    41.961] (==) Automatically enabling devices
[    41.961] (==) Automatically adding GPU devices
[    41.961] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    41.961] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    41.961]     Entry deleted from font path.
[    41.961] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    41.961]     Entry deleted from font path.
[    41.961] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    41.961]     Entry deleted from font path.
[    41.961] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    41.961]     Entry deleted from font path.
[    41.961] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    41.961]     Entry deleted from font path.
[    41.961] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    41.961] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    41.961] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    41.965] (II) Loader magic: 0x55cf38b60dc0
[    41.965] (II) Module ABI versions:
[    41.965]     X.Org ANSI C Emulation: 0.4
[    41.965]     X.Org Video Driver: 20.0
[    41.965]     X.Org XInput driver : 22.1
[    41.965]     X.Org Server Extension : 9.0
[    41.967] (++) using VT number 7

[    41.967] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    41.968] (II) xfree86: Adding drm device (/dev/dri/card0)
[    42.025] (II) xfree86: Adding drm device (/dev/dri/card1)
[    42.603] (--) PCI:*(0:0:1:0) 1002:9874:103c:80b5 rev 197, Mem @ 0xd0000000/268435456, 0xf0800000/8388608, 0xff700000/262144, I/O @ 0x0000f000/256, BIOS @ 0x????????/131072
[    42.604] (--) PCI: (0:4:0:0) 1002:6900:103c:80b5 rev 129, Mem @ 0xe0000000/268435456, 0xf0000000/2097152, 0xff300000/262144, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    42.604] (II) LoadModule: "glx"
[    42.637] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    44.304] (II) Module glx: vendor="X.Org Foundation"
[    44.304]     compiled for 1.18.4, module version = 1.0.0
[    44.304]     ABI class: X.Org Server Extension, version 9.0
[    44.304] (==) AIGLX enabled
[    44.304] (II) Applying OutputClass "AMDgpu" to /dev/dri/card0
[    44.304]     loading driver: amdgpu
[    44.304] (II) Applying OutputClass "AMDgpu" to /dev/dri/card1
[    44.304]     loading driver: amdgpu
[    44.304] (==) Matched amdgpu as autoconfigured driver 0
[    44.304] (==) Matched ati as autoconfigured driver 1
[    44.304] (==) Matched amdgpu as autoconfigured driver 2
[    44.304] (==) Matched ati as autoconfigured driver 3
[    44.304] (==) Matched ati as autoconfigured driver 4
[    44.304] (==) Matched modesetting as autoconfigured driver 5
[    44.304] (==) Matched fbdev as autoconfigured driver 6
[    44.304] (==) Matched vesa as autoconfigured driver 7
[    44.304] (==) Assigned the driver to the xf86ConfigLayout
[    44.304] (II) LoadModule: "amdgpu"
[    44.305] (II) Loading /usr/lib/xorg/modules/drivers/amdgpu_drv.so
[    44.890] (II) Module amdgpu: vendor="X.Org Foundation"
[    44.890]     compiled for 1.18.3, module version = 1.1.0
[    44.890]     Module class: X.Org Video Driver
[    44.890]     ABI class: X.Org Video Driver, version 20.0
[    44.890] (II) LoadModule: "ati"
[    44.891] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    44.893] (II) Module ati: vendor="X.Org Foundation"
[    44.893]     compiled for 1.18.3, module version = 7.7.0
[    44.893]     Module class: X.Org Video Driver
[    44.893]     ABI class: X.Org Video Driver, version 20.0
[    44.893] (II) LoadModule: "radeon"
[    44.894] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    44.996] (II) Module radeon: vendor="X.Org Foundation"
[    44.996]     compiled for 1.18.3, module version = 7.7.0
[    44.996]     Module class: X.Org Video Driver
[    44.996]     ABI class: X.Org Video Driver, version 20.0
[    44.996] (II) LoadModule: "modesetting"
[    44.997] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    45.050] (II) Module modesetting: vendor="X.Org Foundation"
[    45.050]     compiled for 1.18.4, module version = 1.18.4
[    45.050]     Module class: X.Org Video Driver
[    45.050]     ABI class: X.Org Video Driver, version 20.0
[    45.050] (II) LoadModule: "fbdev"
[    45.051] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    45.073] (II) Module fbdev: vendor="X.Org Foundation"
[    45.073]     compiled for 1.18.1, module version = 0.4.4
[    45.073]     Module class: X.Org Video Driver
[    45.073]     ABI class: X.Org Video Driver, version 20.0
[    45.073] (II) LoadModule: "vesa"
[    45.074] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    45.153] (II) Module vesa: vendor="X.Org Foundation"
[    45.153]     compiled for 1.18.1, module version = 2.3.4
[    45.153]     Module class: X.Org Video Driver
[    45.153]     ABI class: X.Org Video Driver, version 20.0
[    45.154] (II) AMDGPU: Driver for AMD Radeon chipsets: BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, TOPAZ, TOPAZ,
    TOPAZ, TOPAZ, TOPAZ, TONGA, TONGA, TONGA, TONGA, TONGA, TONGA, TONGA,
    TONGA, TONGA, CARRIZO, CARRIZO, CARRIZO, CARRIZO, CARRIZO, FIJI,
    STONEY, POLARIS11, POLARIS11, POLARIS11, POLARIS11, POLARIS11,
    POLARIS11, POLARIS10, POLARIS10
[    45.155] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    45.164] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    45.164] (II) FBDEV: driver for framebuffer: fbdev
[    45.164] (II) VESA: driver for VESA chipsets: vesa
[    45.226] (II) [KMS] Kernel modesetting enabled.
[    45.281] (II) [KMS] Kernel modesetting enabled.
[    45.282] (WW) Falling back to old probe method for modesetting
[    45.282] (WW) Falling back to old probe method for fbdev
[    45.282] (II) Loading sub module "fbdevhw"
[    45.282] (II) LoadModule: "fbdevhw"
[    45.282] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    45.324] (II) Module fbdevhw: vendor="X.Org Foundation"
[    45.324]     compiled for 1.18.4, module version = 0.0.2
[    45.324]     ABI class: X.Org Video Driver, version 20.0
[    45.324] (WW) Falling back to old probe method for vesa
[    45.324] (II) AMDGPU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    45.324] (==) AMDGPU(0): Depth 24, (--) framebuffer bpp 32
[    45.324] (II) AMDGPU(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    45.324] (==) AMDGPU(0): Default visual is TrueColor
[    45.324] (==) AMDGPU(0): RGB weight 888
[    45.324] (II) AMDGPU(0): Using 8 bits per RGB (8 bit DAC)
[    45.324] (--) AMDGPU(0): Chipset: "CARRIZO" (ChipID = 0x9874)
[    45.324] (II) Loading sub module "fb"
[    45.324] (II) LoadModule: "fb"
[    45.324] (II) Loading /usr/lib/xorg/modules/libfb.so
[    45.405] (II) Module fb: vendor="X.Org Foundation"
[    45.406]     compiled for 1.18.4, module version = 1.0.0
[    45.406]     ABI class: X.Org ANSI C Emulation, version 0.4
[    45.406] (II) Loading sub module "dri2"
[    45.406] (II) LoadModule: "dri2"
[    45.406] (II) Module "dri2" already built-in
[    52.634] (II) Loading sub module "glamoregl"
[    52.634] (II) LoadModule: "glamoregl"
[    52.634] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    52.696] (II) Module glamoregl: vendor="X.Org Foundation"
[    52.696]     compiled for 1.18.4, module version = 1.0.0
[    52.696]     ABI class: X.Org ANSI C Emulation, version 0.4
[    52.696] (II) glamor: OpenGL accelerated X.org driver based.
[    52.791] (II) glamor: EGL version 1.4 (DRI2):
[    52.877] (II) AMDGPU(0): glamor detected, initialising EGL layer.
[    52.877] (II) AMDGPU(0): KMS Pageflipping: enabled
[    52.881] (II) AMDGPU(0): Output eDP has no monitor section
[    52.945] (II) AMDGPU(0): Output HDMI-A-0 has no monitor section
[    52.960] (II) AMDGPU(0): EDID for output eDP
[    52.960] (II) AMDGPU(0): Manufacturer: LGD  Model: 493  Serial#: 0
[    52.960] (II) AMDGPU(0): Year: 2014  Week: 0
[    52.960] (II) AMDGPU(0): EDID Version: 1.4
[    52.960] (II) AMDGPU(0): Digital Display Input
[    52.960] (II) AMDGPU(0): 6 bits per channel
[    52.960] (II) AMDGPU(0): Digital interface is DisplayPort
[    52.960] (II) AMDGPU(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    52.960] (II) AMDGPU(0): Gamma: 2.20
[    52.960] (II) AMDGPU(0): No DPMS capabilities specified
[    52.960] (II) AMDGPU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    52.960] (II) AMDGPU(0): First detailed timing is preferred mode
[    52.960] (II) AMDGPU(0): Preferred mode is native pixel format and refresh rate
[    52.960] (II) AMDGPU(0): redX: 0.578 redY: 0.344   greenX: 0.337 greenY: 0.571
[    52.960] (II) AMDGPU(0): blueX: 0.159 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    52.960] (II) AMDGPU(0): Manufacturer's mask: 0
[    52.960] (II) AMDGPU(0): Supported detailed timing:
[    52.960] (II) AMDGPU(0): clock: 76.3 MHz   Image Size:  344 x 194 mm
[    52.960] (II) AMDGPU(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1610 h_border: 0
[    52.960] (II) AMDGPU(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    52.960] (II) AMDGPU(0): Supported detailed timing:
[    52.960] (II) AMDGPU(0): clock: 50.9 MHz   Image Size:  344 x 194 mm
[    52.960] (II) AMDGPU(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1610 h_border: 0
[    52.960] (II) AMDGPU(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    52.960] (II) AMDGPU(0): Unknown vendor-specific block 2
[    52.960] (II) AMDGPU(0): EDID (in hex):
[    52.960] (II) AMDGPU(0):     00ffffffffffff0030e4930400000000
[    52.960] (II) AMDGPU(0):     00180104952213780a05f59458569228
[    52.960] (II) AMDGPU(0):     1e505400000001010101010101010101
[    52.960] (II) AMDGPU(0):     010101010101d01d56f4500016303020
[    52.960] (II) AMDGPU(0):     350058c21000001be01356f450001630
[    52.960] (II) AMDGPU(0):     3020350058c21000001b000000000000
[    52.960] (II) AMDGPU(0):     00000000000000000000000000000002
[    52.960] (II) AMDGPU(0):     000c47ea0a3c6412161c6e000000005b
[    52.960] (II) AMDGPU(0): Printing probed modes for output eDP
[    52.960] (II) AMDGPU(0): Modeline "1366x768"x60.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    52.960] (II) AMDGPU(0): Modeline "1366x768"x40.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    52.960] (II) AMDGPU(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    52.960] (II) AMDGPU(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    52.960] (II) AMDGPU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    52.960] (II) AMDGPU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    52.960] (II) AMDGPU(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    52.960] (II) AMDGPU(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    52.960] (II) AMDGPU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    53.023] (II) AMDGPU(0): EDID for output HDMI-A-0
[    53.023] (II) AMDGPU(0): Manufacturer: MEI  Model: c32c  Serial#: 16843009
[    53.023] (II) AMDGPU(0): Year: 2012  Week: 0
[    53.023] (II) AMDGPU(0): EDID Version: 1.3
[    53.023] (II) AMDGPU(0): Digital Display Input
[    53.024] (II) AMDGPU(0): Indeterminate output size
[    53.024] (II) AMDGPU(0): Gamma: 2.20
[    53.024] (II) AMDGPU(0): No DPMS capabilities specified
[    53.024] (II) AMDGPU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    53.024] (II) AMDGPU(0): First detailed timing is preferred mode
[    53.024] (II) AMDGPU(0): redX: 0.640 redY: 0.345   greenX: 0.291 greenY: 0.635
[    53.024] (II) AMDGPU(0): blueX: 0.163 blueY: 0.093   whiteX: 0.288 whiteY: 0.296
[    53.024] (II) AMDGPU(0): Manufacturer's mask: 0
[    53.024] (II) AMDGPU(0): Supported detailed timing:
[    53.024] (II) AMDGPU(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    53.024] (II) AMDGPU(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    53.024] (II) AMDGPU(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    53.024] (II) AMDGPU(0): Supported detailed timing:
[    53.024] (II) AMDGPU(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    53.024] (II) AMDGPU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    53.024] (II) AMDGPU(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    53.024] (II) AMDGPU(0): Monitor name: Panasonic-TV
[    53.024] (II) AMDGPU(0): Ranges: V min: 23 V max: 61 Hz, H min: 15 H max: 68 kHz, PixClock max 155 MHz
[    53.024] (II) AMDGPU(0): Supported detailed timing:
[    53.024] (II) AMDGPU(0): clock: 148.5 MHz   Image Size:  698 x 392 mm
[    53.024] (II) AMDGPU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    53.024] (II) AMDGPU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    53.024] (II) AMDGPU(0): Supported detailed timing:
[    53.024] (II) AMDGPU(0): clock: 27.0 MHz   Image Size:  698 x 392 mm
[    53.024] (II) AMDGPU(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    53.024] (II) AMDGPU(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    53.024] (II) AMDGPU(0): Supported detailed timing:
[    53.024] (II) AMDGPU(0): clock: 27.0 MHz   Image Size:  523 x 392 mm
[    53.024] (II) AMDGPU(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    53.024] (II) AMDGPU(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    53.024] (II) AMDGPU(0): Supported detailed timing:
[    53.024] (II) AMDGPU(0): clock: 27.0 MHz   Image Size:  698 x 392 mm
[    53.024] (II) AMDGPU(0): h_active: 1440  h_sync: 1478  h_sync_end 1602 h_blank_end 1716 h_border: 0
[    53.024] (II) AMDGPU(0): v_active: 240  v_sync: 244  v_sync_end 247 v_blanking: 262 v_border: 0
[    53.024] (II) AMDGPU(0): Supported detailed timing:
[    53.024] (II) AMDGPU(0): clock: 27.0 MHz   Image Size:  523 x 392 mm
[    53.024] (II) AMDGPU(0): h_active: 1440  h_sync: 1478  h_sync_end 1602 h_blank_end 1716 h_border: 0
[    53.024] (II) AMDGPU(0): v_active: 240  v_sync: 244  v_sync_end 247 v_blanking: 262 v_border: 0
[    53.024] (II) AMDGPU(0): Number of EDID sections to follow: 1
[    53.024] (II) AMDGPU(0): EDID (in hex):
[    53.024] (II) AMDGPU(0):     00ffffffffffff0034a92cc301010101
[    53.024] (II) AMDGPU(0):     00160103800000780adaffa3584aa229
[    53.024] (II) AMDGPU(0):     17494b00000001010101010101010101
[    53.024] (II) AMDGPU(0):     010101010101011d007251d01e206e28
[    53.024] (II) AMDGPU(0):     5500ba882100001e011d8018711c1620
[    53.024] (II) AMDGPU(0):     582c2500ba882100009e000000fc0050
[    53.024] (II) AMDGPU(0):     616e61736f6e69632d54560a000000fd
[    53.024] (II) AMDGPU(0):     00173d0f440f000a2020202020200101
[    53.024] (II) AMDGPU(0):     02031b71498405102003020706012309
[    53.024] (II) AMDGPU(0):     070168030c003000b82d0f023a801871
[    53.024] (II) AMDGPU(0):     382d40582c4500ba882100001e8c0ad0
[    53.024] (II) AMDGPU(0):     8a20e02d10103e9600ba88210000188c
[    53.024] (II) AMDGPU(0):     0ad08a20e02d10103e96000b88210000
[    53.024] (II) AMDGPU(0):     188c0aa01451f01600267c4300ba8821
[    53.025] (II) AMDGPU(0):     0000988c0aa01451f01600267c43000b
[    53.025] (II) AMDGPU(0):     8821000098000000000000000000009b
[    53.025] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[    53.025] (II) AMDGPU(0): Printing probed modes for output HDMI-A-0
[    53.025] (II) AMDGPU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz eP)
[    53.025] (II) AMDGPU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "1920x1080"x24.0   74.18  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "1440x480i"x59.9   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "720x480i"x60.0   13.51  720 739 801 858  480 488 494 525 interlace -hsync -vsync (15.8 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "720x480i"x59.9   13.50  720 739 801 858  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    53.025] (II) AMDGPU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    53.025] (II) AMDGPU(0): Output eDP connected
[    53.025] (II) AMDGPU(0): Output HDMI-A-0 connected
[    53.025] (II) AMDGPU(0): Using spanning desktop for initial modes
[    53.025] (II) AMDGPU(0): Output eDP using initial mode 1366x768 +0+0
[    53.025] (II) AMDGPU(0): Output HDMI-A-0 using initial mode 1280x720 +1366+0
[    53.025] (II) AMDGPU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    53.025] (II) AMDGPU(0): mem size init: gart size :3f102000 vram size: s:20000000 visible:f643000
[    53.025] (==) AMDGPU(0): DPI set to (96, 96)
[    53.025] (II) Loading sub module "ramdac"
[    53.025] (II) LoadModule: "ramdac"
[    53.025] (II) Module "ramdac" already built-in
[    53.025] (==) AMDGPU(G0): Depth 24, (--) framebuffer bpp 32
[    53.025] (II) AMDGPU(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    53.025] (==) AMDGPU(G0): Default visual is TrueColor
[    53.025] (==) AMDGPU(G0): RGB weight 888
[    53.025] (II) AMDGPU(G0): Using 8 bits per RGB (8 bit DAC)
[    53.025] (--) AMDGPU(G0): Chipset: "TOPAZ" (ChipID = 0x6900)
[    53.582] (II) Loading sub module "fb"
[    53.582] (II) LoadModule: "fb"
[    53.582] (II) Loading /usr/lib/xorg/modules/libfb.so
[    53.582] (II) Module fb: vendor="X.Org Foundation"
[    53.582]     compiled for 1.18.4, module version = 1.0.0
[    53.582]     ABI class: X.Org ANSI C Emulation, version 0.4
[    53.582] (II) Loading sub module "dri2"
[    53.582] (II) LoadModule: "dri2"
[    53.582] (II) Module "dri2" already built-in
[    53.585] (II) Loading sub module "glamoregl"
[    53.585] (II) LoadModule: "glamoregl"
[    53.585] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    53.586] (II) Module glamoregl: vendor="X.Org Foundation"
[    53.586]     compiled for 1.18.4, module version = 1.0.0
[    53.586]     ABI class: X.Org ANSI C Emulation, version 0.4
[    53.586] (II) glamor: OpenGL accelerated X.org driver based.
[    53.587] (II) glamor: EGL version 1.4 (DRI2):
[    53.589] (II) AMDGPU(G0): glamor detected, initialising EGL layer.
[    53.589] (II) AMDGPU(G0): KMS Pageflipping: enabled
[    53.589] (II) AMDGPU(G0): mem size init: gart size :7f518000 vram size: s:80000000 visible:fbbe000
[    53.589] (==) AMDGPU(G0): DPI set to (96, 96)
[    53.589] (==) AMDGPU(G0): Using gamma correction (1.0, 1.0, 1.0)
[    53.589] (II) Loading sub module "ramdac"
[    53.589] (II) LoadModule: "ramdac"
[    53.589] (II) Module "ramdac" already built-in
[    53.589] (II) UnloadModule: "radeon"
[    53.589] (II) Unloading radeon
[    53.590] (II) UnloadModule: "modesetting"
[    53.590] (II) Unloading modesetting
[    53.590] (II) UnloadModule: "fbdev"
[    53.590] (II) Unloading fbdev
[    53.590] (II) UnloadSubModule: "fbdevhw"
[    53.590] (II) Unloading fbdevhw
[    53.590] (II) UnloadModule: "vesa"
[    53.590] (II) Unloading vesa
[    53.590] (--) Depth 24 pixmap format is 32 bpp
[    53.601] (II) AMDGPU(G0): [DRI2] Setup complete
[    53.601] (II) AMDGPU(G0): [DRI2]   DRI driver: radeonsi
[    53.601] (II) AMDGPU(G0): [DRI2]   VDPAU driver: radeonsi
[    53.601] (II) AMDGPU(G0): Front buffer pitch: 4096 bytes
[    53.617] (==) AMDGPU(G0): DRI3 disabled
[    53.617] (==) AMDGPU(G0): Backing store enabled
[    53.617] (II) AMDGPU(G0): Direct rendering enabled
[    54.168] (II) AMDGPU(G0): Use GLAMOR acceleration.
[    54.168] (II) AMDGPU(G0): Acceleration enabled
[    54.168] (==) AMDGPU(G0): DPMS enabled
[    54.168] (==) AMDGPU(G0): Silken mouse enabled
[    54.184] (II) AMDGPU(G0): Set up textured video (glamor)
[    54.184] (II) AMDGPU(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    54.184] (II) AMDGPU(0): [DRI2] Setup complete
[    54.184] (II) AMDGPU(0): [DRI2]   DRI driver: radeonsi
[    54.184] (II) AMDGPU(0): [DRI2]   VDPAU driver: radeonsi
[    54.185] (II) AMDGPU(0): Front buffer pitch: 10624 bytes
[    54.185] (==) AMDGPU(0): DRI3 disabled
[    54.185] (==) AMDGPU(0): Backing store enabled
[    54.185] (II) AMDGPU(0): Direct rendering enabled
[    54.313] (II) AMDGPU(0): Use GLAMOR acceleration.
[    54.313] (II) AMDGPU(0): Acceleration enabled
[    54.313] (==) AMDGPU(0): DPMS enabled
[    54.313] (==) AMDGPU(0): Silken mouse enabled
[    54.313] (II) AMDGPU(0): Set up textured video (glamor)
[    54.313] (II) AMDGPU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    54.457] (--) RandR disabled
[    54.484] (II) SELinux: Disabled on system
[    54.492] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    54.492] (II) AIGLX: enabled GLX_ARB_create_context
[    54.492] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    54.493] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    54.493] (II) AIGLX: enabled GLX_INTEL_swap_event
[    54.493] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    54.493] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    54.493] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    54.493] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    54.493] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    54.493] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    54.494] (II) AIGLX: Loaded and initialized radeonsi
[    54.494] (II) GLX: Initialized DRI2 GL provider for screen 0
[    54.496] (II) AMDGPU(0): Setting screen physical size to 700 x 203
[    54.729] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    54.729] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    54.729] (II) LoadModule: "evdev"
[    54.729] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    54.782] (II) Module evdev: vendor="X.Org Foundation"
[    54.782]     compiled for 1.18.1, module version = 2.10.1
[    54.782]     Module class: X.Org XInput Driver
[    54.782]     ABI class: X.Org XInput driver, version 22.1
[    54.782] (II) Using input driver 'evdev' for 'Power Button'
[    54.782] (**) Power Button: always reports core events
[    54.782] (**) evdev: Power Button: Device: "/dev/input/event2"
[    54.782] (--) evdev: Power Button: Vendor 0 Product 0x1
[    54.782] (--) evdev: Power Button: Found keys
[    54.782] (II) evdev: Power Button: Configuring as keyboard
[    54.782] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    54.782] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    54.782] (**) Option "xkb_rules" "evdev"
[    54.782] (**) Option "xkb_model" "pc105"
[    54.782] (**) Option "xkb_layout" "us"
[    54.784] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    54.784] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    54.784] (II) Using input driver 'evdev' for 'Video Bus'
[    54.784] (**) Video Bus: always reports core events
[    54.784] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    54.784] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    54.784] (--) evdev: Video Bus: Found keys
[    54.784] (II) evdev: Video Bus: Configuring as keyboard
[    54.784] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event4"
[    54.784] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    54.784] (**) Option "xkb_rules" "evdev"
[    54.784] (**) Option "xkb_model" "pc105"
[    54.784] (**) Option "xkb_layout" "us"
[    54.785] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    54.785] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    54.785] (II) Using input driver 'evdev' for 'Video Bus'
[    54.785] (**) Video Bus: always reports core events
[    54.785] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    54.785] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    54.785] (--) evdev: Video Bus: Found keys
[    54.786] (II) evdev: Video Bus: Configuring as keyboard
[    54.786] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0d/LNXVIDEO:01/input/input6/event5"
[    54.786] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    54.786] (**) Option "xkb_rules" "evdev"
[    54.786] (**) Option "xkb_model" "pc105"
[    54.786] (**) Option "xkb_layout" "us"
[    54.787] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    54.787] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    54.787] (II) Using input driver 'evdev' for 'Power Button'
[    54.787] (**) Power Button: always reports core events
[    54.787] (**) evdev: Power Button: Device: "/dev/input/event0"
[    54.787] (--) evdev: Power Button: Vendor 0 Product 0x1
[    54.787] (--) evdev: Power Button: Found keys
[    54.787] (II) evdev: Power Button: Configuring as keyboard
[    54.787] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    54.787] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    54.787] (**) Option "xkb_rules" "evdev"
[    54.787] (**) Option "xkb_model" "pc105"
[    54.787] (**) Option "xkb_layout" "us"
[    54.788] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    54.788] (II) No input driver specified, ignoring this device.
[    54.788] (II) This device may have been added with another device file.
[    54.789] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event13)
[    54.789] (II) No input driver specified, ignoring this device.
[    54.789] (II) This device may have been added with another device file.
[    54.790] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event14)
[    54.790] (II) No input driver specified, ignoring this device.
[    54.790] (II) This device may have been added with another device file.
[    54.790] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event15)
[    54.790] (II) No input driver specified, ignoring this device.
[    54.790] (II) This device may have been added with another device file.
[    54.791] (II) config/udev: Adding input device HP Truevision HD (/dev/input/event16)
[    54.791] (**) HP Truevision HD: Applying InputClass "evdev keyboard catchall"
[    54.791] (II) Using input driver 'evdev' for 'HP Truevision HD'
[    54.791] (**) HP Truevision HD: always reports core events
[    54.791] (**) evdev: HP Truevision HD: Device: "/dev/input/event16"
[    54.791] (--) evdev: HP Truevision HD: Vendor 0x5c8 Product 0x379
[    54.792] (--) evdev: HP Truevision HD: Found keys
[    54.792] (II) evdev: HP Truevision HD: Configuring as keyboard
[    54.792] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input17/event16"
[    54.792] (II) XINPUT: Adding extended input device "HP Truevision HD" (type: KEYBOARD, id 10)
[    54.792] (**) Option "xkb_rules" "evdev"
[    54.792] (**) Option "xkb_model" "pc105"
[    54.792] (**) Option "xkb_layout" "us"
[    54.793] (II) config/udev: Adding input device Logitech Logitech G710 Keyboard (/dev/input/event7)
[    54.793] (**) Logitech Logitech G710 Keyboard: Applying InputClass "evdev keyboard catchall"
[    54.793] (II) Using input driver 'evdev' for 'Logitech Logitech G710 Keyboard'
[    54.793] (**) Logitech Logitech G710 Keyboard: always reports core events
[    54.793] (**) evdev: Logitech Logitech G710 Keyboard: Device: "/dev/input/event7"
[    54.793] (--) evdev: Logitech Logitech G710 Keyboard: Vendor 0x46d Product 0xc24d
[    54.793] (--) evdev: Logitech Logitech G710 Keyboard: Found keys
[    54.793] (II) evdev: Logitech Logitech G710 Keyboard: Configuring as keyboard
[    54.793] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-3/2-3:1.0/0003:046D:C24D.0002/input/input9/event7"
[    54.793] (II) XINPUT: Adding extended input device "Logitech Logitech G710 Keyboard" (type: KEYBOARD, id 11)
[    54.793] (**) Option "xkb_rules" "evdev"
[    54.793] (**) Option "xkb_model" "pc105"
[    54.793] (**) Option "xkb_layout" "us"
[    54.795] (II) config/udev: Adding input device Logitech Logitech G710 Keyboard (/dev/input/event8)
[    54.795] (**) Logitech Logitech G710 Keyboard: Applying InputClass "evdev keyboard catchall"
[    54.795] (II) Using input driver 'evdev' for 'Logitech Logitech G710 Keyboard'
[    54.795] (**) Logitech Logitech G710 Keyboard: always reports core events
[    54.795] (**) evdev: Logitech Logitech G710 Keyboard: Device: "/dev/input/event8"
[    54.795] (--) evdev: Logitech Logitech G710 Keyboard: Vendor 0x46d Product 0xc24d
[    54.795] (--) evdev: Logitech Logitech G710 Keyboard: Found keys
[    54.795] (II) evdev: Logitech Logitech G710 Keyboard: Configuring as keyboard
[    54.795] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-3/2-3:1.1/0003:046D:C24D.0003/input/input10/event8"
[    54.795] (II) XINPUT: Adding extended input device "Logitech Logitech G710 Keyboard" (type: KEYBOARD, id 12)
[    54.795] (**) Option "xkb_rules" "evdev"
[    54.795] (**) Option "xkb_model" "pc105"
[    54.795] (**) Option "xkb_layout" "us"
[    54.796] (II) config/udev: Adding input device USB Optical Mouse  (/dev/input/event6)
[    54.796] (**) USB Optical Mouse : Applying InputClass "evdev pointer catchall"
[    54.796] (**) USB Optical Mouse : Applying InputClass "evdev keyboard catchall"
[    54.796] (II) Using input driver 'evdev' for 'USB Optical Mouse '
[    54.796] (**) USB Optical Mouse : always reports core events
[    54.796] (**) evdev: USB Optical Mouse : Device: "/dev/input/event6"
[    54.796] (--) evdev: USB Optical Mouse : Vendor 0x1bcf Product 0x53
[    54.796] (--) evdev: USB Optical Mouse : Found 9 mouse buttons
[    54.796] (--) evdev: USB Optical Mouse : Found scroll wheel(s)
[    54.796] (--) evdev: USB Optical Mouse : Found relative axes
[    54.796] (--) evdev: USB Optical Mouse : Found x and y relative axes
[    54.796] (--) evdev: USB Optical Mouse : Found absolute axes
[    54.796] (II) evdev: USB Optical Mouse : Forcing absolute x/y axes to exist.
[    54.796] (--) evdev: USB Optical Mouse : Found keys
[    54.796] (II) evdev: USB Optical Mouse : Configuring as mouse
[    54.796] (II) evdev: USB Optical Mouse : Configuring as keyboard
[    54.796] (II) evdev: USB Optical Mouse : Adding scrollwheel support
[    54.796] (**) evdev: USB Optical Mouse : YAxisMapping: buttons 4 and 5
[    54.796] (**) evdev: USB Optical Mouse : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    54.796] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1.1/1-1.1:1.0/0003:1BCF:0053.0001/input/input8/event6"
[    54.796] (II) XINPUT: Adding extended input device "USB Optical Mouse " (type: KEYBOARD, id 13)
[    54.797] (**) Option "xkb_rules" "evdev"
[    54.797] (**) Option "xkb_model" "pc105"
[    54.797] (**) Option "xkb_layout" "us"
[    54.797] (II) evdev: USB Optical Mouse : initialized for relative axes.
[    54.797] (WW) evdev: USB Optical Mouse : ignoring absolute axes.
[    54.797] (**) USB Optical Mouse : (accel) keeping acceleration scheme 1
[    54.797] (**) USB Optical Mouse : (accel) acceleration profile 0
[    54.797] (**) USB Optical Mouse : (accel) acceleration factor: 2.000
[    54.797] (**) USB Optical Mouse : (accel) acceleration threshold: 4
[    54.797] (II) config/udev: Adding input device USB Optical Mouse  (/dev/input/mouse0)
[    54.797] (II) No input driver specified, ignoring this device.
[    54.797] (II) This device may have been added with another device file.
[    54.798] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    54.798] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    54.798] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    54.798] (**) AT Translated Set 2 keyboard: always reports core events
[    54.798] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    54.798] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    54.798] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    54.798] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    54.798] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    54.798] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    54.798] (**) Option "xkb_rules" "evdev"
[    54.798] (**) Option "xkb_model" "pc105"
[    54.798] (**) Option "xkb_layout" "us"
[    54.798] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    54.798] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    54.798] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[    54.798] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    54.798] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    54.799] (II) LoadModule: "synaptics"
[    54.799] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    54.799] (II) Module synaptics: vendor="X.Org Foundation"
[    54.799]     compiled for 1.18.1, module version = 1.8.2
[    54.799]     Module class: X.Org XInput Driver
[    54.799]     ABI class: X.Org XInput driver, version 22.1
[    54.799] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    54.799] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    54.799] (**) Option "Device" "/dev/input/event9"
[    54.856] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    54.856] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1326 - 5656 (res 41)
[    54.856] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1200 - 4712 (res 58)
[    54.856] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    54.856] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    54.856] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    54.856] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    54.856] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    54.856] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    54.856] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    54.880] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event9"
[    54.880] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 15)
[    54.880] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    54.880] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    54.880] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[    54.880] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    54.880] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    54.880] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    54.880] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    54.881] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    54.881] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    54.882] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    54.882] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event11)
[    54.882] (II) No input driver specified, ignoring this device.
[    54.882] (II) This device may have been added with another device file.
[    54.883] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    54.883] (II) No input driver specified, ignoring this device.
[    54.883] (II) This device may have been added with another device file.
[    54.886] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event10)
[    54.886] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[    54.886] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[    54.887] (**) HP Wireless hotkeys: always reports core events
[    54.887] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event10"
[    54.887] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[    54.887] (--) evdev: HP Wireless hotkeys: Found keys
[    54.887] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[    54.887] (**) Option "config_info" "udev:/sys/devices/virtual/input/input11/event10"
[    54.887] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 16)
[    54.887] (**) Option "xkb_rules" "evdev"
[    54.887] (**) Option "xkb_model" "pc105"
[    54.887] (**) Option "xkb_layout" "us"
[    54.888] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event12)
[    54.888] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    54.888] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    54.888] (**) HP WMI hotkeys: always reports core events
[    54.888] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event12"
[    54.888] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    54.888] (--) evdev: HP WMI hotkeys: Found keys
[    54.888] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    54.888] (**) Option "config_info" "udev:/sys/devices/virtual/input/input13/event12"
[    54.888] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 17)
[    54.888] (**) Option "xkb_rules" "evdev"
[    54.888] (**) Option "xkb_model" "pc105"
[    54.888] (**) Option "xkb_layout" "us"
[    65.795] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[    65.795] (II) AMDGPU(0): Printing DDC gathered Modelines:
[    65.795] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    65.795] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    65.858] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[    65.862] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[    65.862] (II) AMDGPU(0): Printing DDC gathered Modelines:
[    65.862] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    65.862] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    65.925] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[    66.064] (II) AMDGPU(0): Allocate new frame buffer 3286x1080
[    66.065] (II) AMDGPU(0):  => pitch 13184 bytes
[    68.646] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[    68.646] (II) AMDGPU(0): Printing DDC gathered Modelines:
[    68.646] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    68.646] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    68.710] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[    68.714] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[    68.714] (II) AMDGPU(0): Printing DDC gathered Modelines:
[    68.714] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    68.714] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    68.777] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[   866.076] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[   866.076] (II) AMDGPU(0): Printing DDC gathered Modelines:
[   866.076] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[   866.076] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[   866.140] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[   866.145] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[   866.145] (II) AMDGPU(0): Printing DDC gathered Modelines:
[   866.145] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[   866.145] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[   866.209] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[   870.493] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[   870.493] (II) AMDGPU(0): Printing DDC gathered Modelines:
[   870.493] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[   870.493] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[   870.556] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[   870.560] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[   870.560] (II) AMDGPU(0): Printing DDC gathered Modelines:
[   870.560] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[   870.560] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[   870.625] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[   915.285] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[   915.285] (II) AMDGPU(0): Printing DDC gathered Modelines:
[   915.285] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[   915.285] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[   915.348] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[   915.352] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[   915.352] (II) AMDGPU(0): Printing DDC gathered Modelines:
[   915.352] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[   915.352] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[   915.417] (--) AMDGPU(0): HDMI max TMDS frequency 225000KHz
[  1192.842] (II) config/udev: Adding input device B8:69:C2:81:47:8D (/dev/input/event17)
[  1192.842] (**) B8:69:C2:81:47:8D: Applying InputClass "evdev keyboard catchall"
[  1192.842] (II) Using input driver 'evdev' for 'B8:69:C2:81:47:8D'
[  1192.842] (**) B8:69:C2:81:47:8D: always reports core events
[  1192.842] (**) evdev: B8:69:C2:81:47:8D: Device: "/dev/input/event17"
[  1192.843] (--) evdev: B8:69:C2:81:47:8D: Vendor 0 Product 0
[  1192.843] (--) evdev: B8:69:C2:81:47:8D: Found keys
[  1192.843] (II) evdev: B8:69:C2:81:47:8D: Configuring as keyboard
[  1192.843] (**) Option "config_info" "udev:/sys/devices/virtual/input/input18/event17"
[  1192.843] (II) XINPUT: Adding extended input device "B8:69:C2:81:47:8D" (type: KEYBOARD, id 18)
[  1192.843] (**) Option "xkb_rules" "evdev"
[  1192.843] (**) Option "xkb_model" "pc105"
[  1192.843] (**) Option "xkb_layout" "us"
[  1192.843] (WW) Option "xkb_variant" requires a string value
[  1192.843] (WW) Option "xkb_options" requires a string value
[  3893.215] (II) config/udev: removing device B8:69:C2:81:47:8D
[  3893.236] (II) evdev: B8:69:C2:81:47:8D: Close
[  3893.237] (II) UnloadModule: "evdev"
[  4031.915] (II) AMDGPU(0): EDID vendor "LGD", prod id 1171
[  4031.915] (II) AMDGPU(0): Printing DDC gathered Modelines:
[  4031.915] (II) AMDGPU(0): Modeline "1366x768"x0.0   76.32  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[  4031.915] (II) AMDGPU(0): Modeline "1366x768"x0.0   50.88  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[  4033.535] (II) AMDGPU(0): Allocate new frame buffer 1366x768
[  4033.535] (II) AMDGPU(0):  => pitch 5504 bytes
[  4252.231] (II) config/udev: Adding input device 18:22:7E:97:3D:AE (/dev/input/event17)
[  4252.231] (**) 18:22:7E:97:3D:AE: Applying InputClass "evdev keyboard catchall"
[  4252.231] (II) Using input driver 'evdev' for '18:22:7E:97:3D:AE'
[  4252.231] (**) 18:22:7E:97:3D:AE: always reports core events
[  4252.231] (**) evdev: 18:22:7E:97:3D:AE: Device: "/dev/input/event17"
[  4252.231] (--) evdev: 18:22:7E:97:3D:AE: Vendor 0 Product 0
[  4252.231] (--) evdev: 18:22:7E:97:3D:AE: Found keys
[  4252.231] (II) evdev: 18:22:7E:97:3D:AE: Configuring as keyboard
[  4252.231] (**) Option "config_info" "udev:/sys/devices/virtual/input/input19/event17"
[  4252.231] (II) XINPUT: Adding extended input device "18:22:7E:97:3D:AE" (type: KEYBOARD, id 18)
[  4252.231] (**) Option "xkb_rules" "evdev"
[  4252.231] (**) Option "xkb_model" "pc105"
[  4252.231] (**) Option "xkb_layout" "us"
[  4252.231] (WW) Option "xkb_variant" requires a string value
[  4252.231] (WW) Option "xkb_options" requires a string value
[  4276.210] (II) config/udev: removing device 18:22:7E:97:3D:AE
[  4276.228] (II) evdev: 18:22:7E:97:3D:AE: Close
[  4276.228] (II) UnloadModule: "evdev"
[ 32013.698] (II) config/udev: Adding input device B8:69:C2:81:47:8D (/dev/input/event17)
[ 32013.699] (**) B8:69:C2:81:47:8D: Applying InputClass "evdev keyboard catchall"
[ 32013.699] (II) Using input driver 'evdev' for 'B8:69:C2:81:47:8D'
[ 32013.699] (**) B8:69:C2:81:47:8D: always reports core events
[ 32013.699] (**) evdev: B8:69:C2:81:47:8D: Device: "/dev/input/event17"
[ 32013.699] (--) evdev: B8:69:C2:81:47:8D: Vendor 0 Product 0
[ 32013.699] (--) evdev: B8:69:C2:81:47:8D: Found keys
[ 32013.699] (II) evdev: B8:69:C2:81:47:8D: Configuring as keyboard
[ 32013.699] (**) Option "config_info" "udev:/sys/devices/virtual/input/input20/event17"
[ 32013.699] (II) XINPUT: Adding extended input device "B8:69:C2:81:47:8D" (type: KEYBOARD, id 18)
[ 32013.699] (**) Option "xkb_rules" "evdev"
[ 32013.699] (**) Option "xkb_model" "pc105"
[ 32013.699] (**) Option "xkb_layout" "us"
[ 32013.699] (WW) Option "xkb_variant" requires a string value
[ 32013.699] (WW) Option "xkb_options" requires a string value

```

I hope it works for something

---

### Post by Futant on 2017-08-07
That looks ok to me, though I'm not very experienced with log files. I'd say it's almost definitely a driver issue. First of all, if you haven't already, try updating. Open a terminal and enter:
```
sudo apt update
```
let it do it's thing, then:
```
sudo apt upgrade
```

If this doesn't help, a couple of questions - Do things work ok without the usb keyboard and mouse? Are you using the open source drivers or the proprietary ones? You can check in 'additional drivers'. Try using the other one (or one/all of the others if there are more options). [This page]("https://help.ubuntu.com/community/RadeonDriver") might be helpful.

You could also try reinstalling the input drivers. Open a terminal and enter: ```
sudo apt install --reinstall xserver-xorg-input-all
``` 

I've read around a bit and there are a few accounts of similar problems, including t[his bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1580732") , so it could be that you have an unsolved bug. If none of the above helps and no one else can think of anything, you should file a bug report (or add to an existing one if you find one).

---

