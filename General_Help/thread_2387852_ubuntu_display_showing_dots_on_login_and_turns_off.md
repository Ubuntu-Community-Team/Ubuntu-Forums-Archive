---
title: "ubuntu display showing dots on login and turns off automatically"
date: 2018-03-24
forum: General Help
---

### Post by uandro on 2018-03-24
[COLOR=#111111][FONT=Ubuntu]Sometimes when I login to ubuntu I get following screen, and it gets stuck there and I have to force close my pc again and again until ubuntu boot normally [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR][IMG]https://i.stack.imgur.com/Gydfb.jpg[/IMG][COLOR=#111111][FONT=Ubuntu]
Even when ubuntu boots normally sometimes there is one more strange problem. For sometime pc runs normal but suddenly display suddenly turns off for a second and turns on and then freezes to one screen and after that laptop stops responding, and if any video was being played sound comes as normal while the laptop is not responsive. My laptop had heating issues,so I got my fan cleaned from repair shop and now it does not have any heating issue. My laptop model is Dell Inspiron N5010 and runs ubuntu 16.04. Please suggest any solution.[/FONT][/COLOR]

---

### Post by Bashing-om on 2018-03-24
uandro; Hello -

Graphic's driver issue ??

Let's see what X thinks.
post back - Between Code Tags - the outputs of terminal commands:
```

sudo lshw -C display
inxi -GCS
cat /var/log/gpu-manager.log
cat /var/log/Xorg.0.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

I expect that the 'inxi' tool will have to be installed.
```

sudo apt update
sudo apt upgrade
sudo apt install inxi

```

We see here what tale gets told ->

[INDENT][INDENT]where we go from here
[/INDENT][/INDENT]

---

### Post by uandro on 2018-03-25
Out put for `[COLOR=#000000][FONT=&amp]sudo lshw -C display[/FONT][/COLOR]`
```

 *-display               
       description: VGA compatible controller
       product: Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:16 memory:c0000000-cfffffff memory:fbe20000-fbe3ffff ioport:e000(size=256) memory:fbe00000-fbe1ffff

```

Output for `[COLOR=#000000][FONT=&amp]inxi -GCS[/FONT][/COLOR]`
```

System:    Host: dell-pc Kernel: 4.4.0-116-generic x86_64 (64 bit)
           Desktop: Unity 7.4.5  Distro: Ubuntu 16.04 xenial
CPU:       Dual core Intel Core i5 M 480 (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2661 MHz 1: 1729 MHz 2: 1729 MHz 3: 1197 MHz
           4: 1197 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.64hz
           GLX Renderer: llvmpipe (LLVM 5.0, 128 bits)
           GLX Version: 3.0 Mesa 17.2.8

```

Output for `[COLOR=#000000][FONT=&amp]cat var/log/gpu-manager.log[/FONT][/COLOR]`
```

cat: var/log/gpu-manager.log: No such file or directory

```

Output for `[COLOR=#000000][FONT=&amp]cat /var/log/Xorg.0.log[/FONT][/COLOR]`

```

[    29.173] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    29.173] X Protocol Version 11, Revision 0
[    29.173] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[    29.173] Current Operating System: Linux dell-pc 4.4.0-116-generic #140-Ubuntu SMP Mon Feb 12 21:23:04 UTC 2018 x86_64
[    29.173] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-116-generic root=UUID=69a53f68-a73a-44e2-adb7-f3fea630c419 ro quiet splash vt.handoff=7
[    29.173] Build Date: 13 October 2017  01:57:05PM
[    29.173] xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support) 
[    29.173] Current version of pixman: 0.33.6
[    29.174]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.174] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.174] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 25 23:03:59 2018
[    29.191] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.230] (==) No Layout section.  Using the first Screen section.
[    29.230] (==) No screen section available. Using defaults.
[    29.230] (**) |-->Screen "Default Screen Section" (0)
[    29.230] (**) |   |-->Monitor "<default monitor>"
[    29.279] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.279] (==) Automatically adding devices
[    29.279] (==) Automatically enabling devices
[    29.279] (==) Automatically adding GPU devices
[    29.279] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    29.279] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.279]     Entry deleted from font path.
[    29.279] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.279]     Entry deleted from font path.
[    29.279] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.279]     Entry deleted from font path.
[    29.279] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.279]     Entry deleted from font path.
[    29.279] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.279]     Entry deleted from font path.
[    29.279] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.279] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.279] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.279] (II) Loader magic: 0x5593c9fc9dc0
[    29.279] (II) Module ABI versions:
[    29.279]     X.Org ANSI C Emulation: 0.4
[    29.279]     X.Org Video Driver: 20.0
[    29.279]     X.Org XInput driver : 22.1
[    29.279]     X.Org Server Extension : 9.0
[    29.280] (++) using VT number 7


[    29.280] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    29.281] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.283] (--) PCI:*(0:1:0:0) 1002:68c1:1028:0447 rev 0, Mem @ 0xc0000000/268435456, 0xfbe20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    29.283] (II) LoadModule: "glx"
[    29.334] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.493] (II) Module glx: vendor="X.Org Foundation"
[    29.493]     compiled for 1.18.4, module version = 1.0.0
[    29.493]     ABI class: X.Org Server Extension, version 9.0
[    29.493] (==) AIGLX enabled
[    29.493] (==) Matched ati as autoconfigured driver 0
[    29.493] (==) Matched ati as autoconfigured driver 1
[    29.493] (==) Matched modesetting as autoconfigured driver 2
[    29.493] (==) Matched fbdev as autoconfigured driver 3
[    29.493] (==) Matched vesa as autoconfigured driver 4
[    29.493] (==) Assigned the driver to the xf86ConfigLayout
[    29.493] (II) LoadModule: "ati"
[    29.511] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    29.518] (II) Module ati: vendor="X.Org Foundation"
[    29.518]     compiled for 1.18.3, module version = 7.7.0
[    29.518]     Module class: X.Org Video Driver
[    29.518]     ABI class: X.Org Video Driver, version 20.0
[    29.518] (II) LoadModule: "radeon"
[    29.518] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    29.533] (II) Module radeon: vendor="X.Org Foundation"
[    29.533]     compiled for 1.18.3, module version = 7.7.0
[    29.533]     Module class: X.Org Video Driver
[    29.533]     ABI class: X.Org Video Driver, version 20.0
[    29.533] (II) LoadModule: "modesetting"
[    29.533] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.558] (II) Module modesetting: vendor="X.Org Foundation"
[    29.558]     compiled for 1.18.4, module version = 1.18.4
[    29.558]     Module class: X.Org Video Driver
[    29.558]     ABI class: X.Org Video Driver, version 20.0
[    29.558] (II) LoadModule: "fbdev"
[    29.559] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.564] (II) Module fbdev: vendor="X.Org Foundation"
[    29.564]     compiled for 1.18.1, module version = 0.4.4
[    29.564]     Module class: X.Org Video Driver
[    29.564]     ABI class: X.Org Video Driver, version 20.0
[    29.564] (II) LoadModule: "vesa"
[    29.564] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.565] (II) Module vesa: vendor="X.Org Foundation"
[    29.565]     compiled for 1.18.1, module version = 2.3.4
[    29.565]     Module class: X.Org Video Driver
[    29.565]     ABI class: X.Org Video Driver, version 20.0
[    29.565] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    29.569] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    29.569] (II) FBDEV: driver for framebuffer: fbdev
[    29.569] (II) VESA: driver for VESA chipsets: vesa
[    29.576] (II) [KMS] Kernel modesetting enabled.
[    29.576] (WW) Falling back to old probe method for modesetting
[    29.576] (WW) Falling back to old probe method for fbdev
[    29.576] (II) Loading sub module "fbdevhw"
[    29.576] (II) LoadModule: "fbdevhw"
[    29.576] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.584] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.584]     compiled for 1.18.4, module version = 0.0.2
[    29.584]     ABI class: X.Org Video Driver, version 20.0
[    29.584] (WW) Falling back to old probe method for vesa
[    29.585] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    29.585] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    29.585] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    29.585] (==) RADEON(0): Default visual is TrueColor
[    29.585] (==) RADEON(0): RGB weight 888
[    29.585] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    29.585] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 5000 Series" (ChipID = 0x68c1)
[    29.585] (II) Loading sub module "fb"
[    29.585] (II) LoadModule: "fb"
[    29.585] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.598] (II) Module fb: vendor="X.Org Foundation"
[    29.598]     compiled for 1.18.4, module version = 1.0.0
[    29.598]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.598] (II) RADEON(0): GPU accel disabled or not working, using shadowfb for KMS
[    29.598] (II) Loading sub module "shadow"
[    29.598] (II) LoadModule: "shadow"
[    29.598] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    29.599] (II) Module shadow: vendor="X.Org Foundation"
[    29.599]     compiled for 1.18.4, module version = 1.1.0
[    29.599]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.599] (II) RADEON(0): KMS Color Tiling: disabled
[    29.599] (II) RADEON(0): KMS Color Tiling 2D: disabled
[    29.599] (II) RADEON(0): KMS Pageflipping: enabled
[    29.599] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    29.724] (II) RADEON(0): Output LVDS has no monitor section
[    29.725] (II) RADEON(0): Output HDMI-0 has no monitor section
[    29.800] (II) RADEON(0): Output VGA-0 has no monitor section
[    29.928] (II) RADEON(0): EDID for output LVDS
[    29.928] (II) RADEON(0): Printing probed modes for output LVDS
[    29.928] (II) RADEON(0): Modeline "1366x768"x59.6   69.30  1366 1398 1430 1486  768 770 774 782 -hsync -vsync (46.6 kHz eP)
[    29.928] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    29.928] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    29.928] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    29.928] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    29.928] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    29.928] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    29.928] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    29.929] (II) RADEON(0): EDID for output HDMI-0
[    30.004] (II) RADEON(0): EDID for output VGA-0
[    30.004] (II) RADEON(0): Output LVDS connected
[    30.004] (II) RADEON(0): Output HDMI-0 disconnected
[    30.004] (II) RADEON(0): Output VGA-0 disconnected
[    30.004] (II) RADEON(0): Using exact sizes for initial modes
[    30.004] (II) RADEON(0): Output LVDS using initial mode 1366x768 +0+0
[    30.004] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    30.004] (II) RADEON(0): mem size init: gart size :40000000 vram size: s:40000000 visible:f981000
[    30.004] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    30.004] (==) RADEON(0): DPI set to (96, 96)
[    30.004] (II) Loading sub module "ramdac"
[    30.004] (II) LoadModule: "ramdac"
[    30.004] (II) Module "ramdac" already built-in
[    30.004] (II) UnloadModule: "modesetting"
[    30.004] (II) Unloading modesetting
[    30.004] (II) UnloadModule: "fbdev"
[    30.004] (II) Unloading fbdev
[    30.004] (II) UnloadSubModule: "fbdevhw"
[    30.004] (II) Unloading fbdevhw
[    30.004] (II) UnloadModule: "vesa"
[    30.004] (II) Unloading vesa
[    30.004] (--) Depth 24 pixmap format is 32 bpp
[    30.021] (II) RADEON(0): Front buffer size: 4224K
[    30.021] (II) RADEON(0): VRAM usage limit set to 226054K
[    30.026] (==) RADEON(0): DRI3 disabled
[    30.026] (==) RADEON(0): Backing store enabled
[    30.026] (WW) RADEON(0): Direct rendering disabled
[    30.026] (II) RADEON(0): Acceleration disabled
[    30.026] (==) RADEON(0): DPMS enabled
[    30.026] (==) RADEON(0): Silken mouse enabled
[    30.027] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    30.028] (--) RandR disabled
[    30.032] (II) SELinux: Disabled on system
[    30.032] (II) AIGLX: Screen 0 is not DRI2 capable
[    30.032] (EE) AIGLX: reverting to software rendering
[    33.282] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    33.282] (II) AIGLX: Loaded and initialized swrast
[    33.282] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    33.283] (II) RADEON(0): Setting screen physical size to 361 x 203
[    33.580] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    33.580] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.580] (II) LoadModule: "evdev"
[    33.580] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.609] (II) Module evdev: vendor="X.Org Foundation"
[    33.609]     compiled for 1.18.1, module version = 2.10.1
[    33.609]     Module class: X.Org XInput Driver
[    33.609]     ABI class: X.Org XInput driver, version 22.1
[    33.609] (II) Using input driver 'evdev' for 'Power Button'
[    33.609] (**) Power Button: always reports core events
[    33.609] (**) evdev: Power Button: Device: "/dev/input/event3"
[    33.609] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.609] (--) evdev: Power Button: Found keys
[    33.609] (II) evdev: Power Button: Configuring as keyboard
[    33.609] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    33.609] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.609] (**) Option "xkb_rules" "evdev"
[    33.609] (**) Option "xkb_model" "pc105"
[    33.609] (**) Option "xkb_layout" "us"
[    33.610] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    33.610] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    33.610] (II) Using input driver 'evdev' for 'Video Bus'
[    33.610] (**) Video Bus: always reports core events
[    33.610] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    33.610] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    33.610] (--) evdev: Video Bus: Found keys
[    33.610] (II) evdev: Video Bus: Configuring as keyboard
[    33.610] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input6/event5"
[    33.610] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    33.610] (**) Option "xkb_rules" "evdev"
[    33.610] (**) Option "xkb_model" "pc105"
[    33.610] (**) Option "xkb_layout" "us"
[    33.611] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    33.611] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.611] (II) Using input driver 'evdev' for 'Power Button'
[    33.611] (**) Power Button: always reports core events
[    33.611] (**) evdev: Power Button: Device: "/dev/input/event0"
[    33.611] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.611] (--) evdev: Power Button: Found keys
[    33.611] (II) evdev: Power Button: Configuring as keyboard
[    33.611] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    33.611] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    33.611] (**) Option "xkb_rules" "evdev"
[    33.611] (**) Option "xkb_model" "pc105"
[    33.611] (**) Option "xkb_layout" "us"
[    33.611] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    33.611] (II) No input driver specified, ignoring this device.
[    33.611] (II) This device may have been added with another device file.
[    33.612] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    33.612] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    33.612] (II) Using input driver 'evdev' for 'Sleep Button'
[    33.612] (**) Sleep Button: always reports core events
[    33.612] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    33.612] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    33.612] (--) evdev: Sleep Button: Found keys
[    33.612] (II) evdev: Sleep Button: Configuring as keyboard
[    33.612] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:01/input/input2/event2"
[    33.612] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    33.612] (**) Option "xkb_rules" "evdev"
[    33.612] (**) Option "xkb_model" "pc105"
[    33.612] (**) Option "xkb_layout" "us"
[    33.612] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event9)
[    33.612] (II) No input driver specified, ignoring this device.
[    33.612] (II) This device may have been added with another device file.
[    33.613] (II) config/udev: Adding input device Laptop_Integrated_Webcam_1.3M (/dev/input/event8)
[    33.613] (**) Laptop_Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
[    33.613] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_1.3M'
[    33.613] (**) Laptop_Integrated_Webcam_1.3M: always reports core events
[    33.613] (**) evdev: Laptop_Integrated_Webcam_1.3M: Device: "/dev/input/event8"
[    33.613] (--) evdev: Laptop_Integrated_Webcam_1.3M: Vendor 0xc45 Product 0x641d
[    33.613] (--) evdev: Laptop_Integrated_Webcam_1.3M: Found keys
[    33.613] (II) evdev: Laptop_Integrated_Webcam_1.3M: Configuring as keyboard
[    33.613] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input13/event8"
[    33.613] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_1.3M" (type: KEYBOARD, id 10)
[    33.613] (**) Option "xkb_rules" "evdev"
[    33.613] (**) Option "xkb_model" "pc105"
[    33.613] (**) Option "xkb_layout" "us"
[    33.613] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event10)
[    33.613] (II) No input driver specified, ignoring this device.
[    33.613] (II) This device may have been added with another device file.
[    33.614] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event11)
[    33.614] (II) No input driver specified, ignoring this device.
[    33.614] (II) This device may have been added with another device file.
[    33.614] (II) config/udev: Adding input device HID 413c:8161 (/dev/input/event6)
[    33.614] (**) HID 413c:8161: Applying InputClass "evdev keyboard catchall"
[    33.614] (II) Using input driver 'evdev' for 'HID 413c:8161'
[    33.614] (**) HID 413c:8161: always reports core events
[    33.614] (**) evdev: HID 413c:8161: Device: "/dev/input/event6"
[    33.614] (--) evdev: HID 413c:8161: Vendor 0x413c Product 0x8161
[    33.614] (--) evdev: HID 413c:8161: Found keys
[    33.614] (II) evdev: HID 413c:8161: Configuring as keyboard
[    33.614] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/0003:413C:8161.0001/input/input8/event6"
[    33.614] (II) XINPUT: Adding extended input device "HID 413c:8161" (type: KEYBOARD, id 11)
[    33.614] (**) Option "xkb_rules" "evdev"
[    33.614] (**) Option "xkb_model" "pc105"
[    33.614] (**) Option "xkb_layout" "us"
[    33.615] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    33.615] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    33.615] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    33.615] (**) AT Translated Set 2 keyboard: always reports core events
[    33.615] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    33.615] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    33.615] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    33.615] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    33.615] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    33.615] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    33.615] (**) Option "xkb_rules" "evdev"
[    33.615] (**) Option "xkb_model" "pc105"
[    33.615] (**) Option "xkb_layout" "us"
[    33.616] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    33.616] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    33.616] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[    33.616] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    33.616] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    33.616] (II) LoadModule: "synaptics"
[    33.616] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    33.617] (II) Module synaptics: vendor="X.Org Foundation"
[    33.617]     compiled for 1.18.1, module version = 1.8.2
[    33.617]     Module class: X.Org XInput Driver
[    33.617]     ABI class: X.Org XInput driver, version 22.1
[    33.617] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    33.617] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    33.617] (**) Option "Device" "/dev/input/event7"
[    33.664] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    33.664] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5650 (res 51)
[    33.664] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4710 (res 90)
[    33.664] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    33.664] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    33.664] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    33.664] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    33.664] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    33.664] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    33.688] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    33.688] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    33.688] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    33.688] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    33.688] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    33.688] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    33.688] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    33.688] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    33.688] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    33.688] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    33.688] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    33.688] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    33.690] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event12)
[    33.690] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    33.690] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    33.690] (**) Dell WMI hotkeys: always reports core events
[    33.690] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event12"
[    33.690] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    33.690] (--) evdev: Dell WMI hotkeys: Found keys
[    33.690] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    33.690] (**) Option "config_info" "udev:/sys/devices/virtual/input/input14/event12"
[    33.690] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[    33.690] (**) Option "xkb_rules" "evdev"
[    33.690] (**) Option "xkb_model" "pc105"
[    33.690] (**) Option "xkb_layout" "us"



```

---

### Post by Bashing-om on 2018-03-25
uandro; Hummm ...

I honestly do not know ATI graphic's well enough to know that there is a issue, there are a few points that stick out in the Xorg.0.log file. But I see nothing that will interfere seriously with the driver's functioning.

I had a miss-type on the command " cat var/log/gpu-manager.log " I missed the leading slash.
should be:
cat /var/log/gpu-manager.log`

What results when you activate the guest account ? Maybe we can isolate this to a config issue in your session account.,


[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by uandro on 2018-03-28
My system is dual boot system with both windows 10 and ubuntu. I was also facing problem in booting windows 10 too. I updated graphics driver on windows 10 and it solved problem for both windows 10 and ubuntu. I have used my system for four days and I have not seen any problem. It would be interesting to know how updating graphics driver on windows 10 solved issue on ubuntu too.

---

### Post by rbmorse on 2018-03-29
I'm just guessing that the windows driver update may have included an update for the video BIOS or a microcode update for the graphics processor, but I don't know that for sure.

---

