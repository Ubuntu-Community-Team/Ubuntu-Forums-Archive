---
title: "Ubuntu gpu driver issue"
date: 2024-03-01
forum: General Help
---

### Post by mennashazly on 2024-03-01
Hi,

I have Ubuntu 20.04 and I couldn't connect my laptop to external monitor it didn't detect HDMI So, I tried to download amdgpu driver as my laptop has "AMD® Ryzen 5 4500u with radeon graphics × 6" but then everything got worse I stuck at 1024x768 resolution and still can't connect to HDMI and cannot boot without nomodeset parameter otherwise I will be stuck at boot black screen. I even did a fresh install but the problem persists. I need help please.

---

### Post by TheFu on 2024-03-01
Which kernel and GPU driver is used?

I don't have a laptop, but I do have Ryzen 5600G using monitors over HDMI (not DisplayPort) with 20.04:

```
$ inxi -G
Graphics:
  Device-1: AMD driver: amdgpu v: kernel 
  Display: x11 server: X.Org 1.20.13 driver: **amdgpu**,ati 
  unloaded: fbdev,modesetting,vesa resolution: 1920x1200~60Hz 
  OpenGL: renderer: AMD RENOIR (DRM 3.42.0 5.15.0-97-generic LLVM 12.0.0) 
  v: 4.6 Mesa 21.2.6
```

I had to get to a 5.10.x kernel before the AMD GPU driver would be used.  With the 5.4.x kernel, it used only the F/LOSS drivers, since my APU was too new. I don't know about 4500u support or when that was added to the kernel.  I'm currently using the HWE kernel, 5.15.x, as you can see above.

If I need to change the output, I'd use **lxrandr**. This only works with X11. I don't know how to do with with Wayland.

---

### Post by mennashazly on 2024-03-02
I have the same kernel.
Code:```

inxi -G
Graphics:
  Device-1: AMD Renoir driver: N/A 
  Display: x11 server: X.Org 1.20.13 driver: ati,fbdev 
  unloaded: modesetting,radeon,vesa resolution: 1024x768~76Hz 
  OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6
```

But as you can see amdgpu isn't identified and the resolution is stuck at 1024x768 and I don't have graphics card other than the one integrated in the processor and there is no drivers available for this processor to linux does that mean I'm just stuck with this setting here?

---

### Post by TheFu on 2024-03-02
So, it seems you need to find if any kernel has the AMD drivers for your APU at all.  [https://www.phoronix.com/review/4500u-windows-linux](https://www.phoronix.com/review/4500u-windows-linux) seems to say that 5.8+ supports it, so perhaps something extra is required?  IDK.

AMD drivers. [https://community.amd.com/t5/processors/where-can-i-find-drivers-of-amd-ryzen-5-4500u-for-ubuntu/m-p/171427/highlight/true](https://community.amd.com/t5/processors/where-can-i-find-drivers-of-amd-ryzen-5-4500u-for-ubuntu/m-p/171427/highlight/true) is from 2020, but seems folks there running the HWE kernels have good GPU performance.  Maybe search these forums for agreeny's posts on Ryzen?

---

### Post by him610 on 2024-03-02
@mennashazly
Your plight caught my attention as I have three systems with AMD APU w/Radeon iGFX. My systems date from 2016, 2022, and 2023 - no issues with any of the three.

There are Linux® Drivers for AMD Radeon™ and Radeon PRO™ Graphics at the AMD website, [https://www.amd.com/en/support/linux-drivers]("https://www.amd.com/en/support/linux-drivers")

The software is all fairly new (from this year); I don't know how it is installed but you may want to look in to it.
Your decision.

---

### Post by ajgreeny on 2024-03-02
Your kernel may be to old for the required AMD driver but so far you have not mentioned what kernel version you are actually using.
Installinga later HWE kernel version may be all that's needed but before jumping into action show us the output of terminal command 
**inxi -Fzx**
Please use code tags when pasting that output.
See my signature below for a [B][How-to/B] of code tags.

---

### Post by mennashazly on 2024-03-02
> **ajgreeny said:**
> Your kernel may be to old for the required AMD  driver but so far you have not mentioned what kernel version you are  actually using.
Installinga later HWE kernel version may be all that's needed but before  jumping into action show us the output of terminal command 
**inxi -Fzx**
Please use code tags when pasting that output.
See my signature below for a [B][How-to/B] of code tags.

Here is the output:

```

inxi -Fzx
System:
  Kernel: 6.5.0-21-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Micro-Star product: Modern 14 B4MW v: REV:1.0
    serial: <superuser required>
  Mobo: Micro-Star model: MS-14DK v: REV:1.0 serial: <superuser required>
    UEFI: American Megatrends v: E14DKAMS.114 date: 06/02/2021
Battery:
  ID-1: BAT1 charge: 24.7 Wh (98.4%) condition: 25.1/37.8 Wh (66.3%)
    volts: 12.1 min: 11.4 model: MSI BIF0_9 status: Not charging
CPU:
  Info: 6-core model: AMD Ryzen 5 4500U with Radeon Graphics bits: 64
    type: MCP arch: Zen 2 rev: 1 cache: L1: 384 KiB L2: 3 MiB L3: 8 MiB
  Speed (MHz): avg: 1562 high: 2375 min/max: 1400/2375 boost: enabled
    cores: 1: 1400 2: 1397 3: 1400 4: 1400 5: 1400 6: 2375 bogomips: 28447
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: AMD Renoir vendor: Micro-Star MSI driver: N/A bus-ID: 03:00.0
  Device-2: Acer HD Webcam type: USB driver: uvcvideo bus-ID: 3-4:2
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: ati,vesa
    unloaded: fbdev,modesetting,radeon gpu: N/A resolution: 1920x1080~77Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits) v: 4.5 Mesa
    24.1~git2403020600.63d2aa~oibaf~j (git-63d2aa4 2024-03-02 jammy-oibaf-ppa)
    direct render: Yes
Audio:
  Device-1: AMD Renoir Radeon High Definition Audio driver: snd_hda_intel
    v: kernel bus-ID: 03:00.1
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    vendor: Micro-Star MSI driver: N/A bus-ID: 03:00.5
  Device-3: AMD Family 17h HD Audio vendor: Micro-Star MSI
    driver: snd_hda_intel v: kernel bus-ID: 03:00.6
  Sound Server-1: ALSA v: k6.5.0-21-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8822CE 802.11ac PCIe Wireless Network Adapter
    vendor: AzureWave driver: rtw_8822ce v: N/A port: f000 bus-ID: 02:00.0
  IF: wlp2s0 state: up mac: <filter>
Bluetooth:
  Device-1: IMC Networks Bluetooth Radio type: USB driver: btusb v: 0.8
    bus-ID: 1-1:2
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.1
Drives:
  Local Storage: total: 238.47 GiB used: 9.05 GiB (3.8%)
  ID-1: /dev/nvme0n1 vendor: Kingston model: OM8PDP3256B-AI1
    size: 238.47 GiB temp: 37.9 C
Partition:
  ID-1: / size: 123.33 GiB used: 8.61 GiB (7.0%) fs: ext4 dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 474.9 MiB used: 6.1 MiB (1.3%) fs: vfat
    dev: /dev/nvme0n1p1
  ID-3: /home size: 109.82 GiB used: 444.7 MiB (0.4%) fs: ext4
    dev: /dev/nvme0n1p5
Swap:
  Alert: No swap data was found.
Sensors:
  System Temperatures: cpu: 38.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 246 Uptime: 4m Memory: 7.15 GiB used: 1.14 GiB (15.9%)
  Init: systemd runlevel: 5 Compilers: gcc: N/A Packages: 1727 Shell: Bash
  v: 5.1.16 inxi: 3.3.13

```

Also I saw on other forums some talking about Xorg failing to load amdgpu and loading vesa instead so I will drop the Xorg log also if it might help
```
[   177.297] (--) Log file renamed from "/var/log/Xorg.pid-2214.log" to "/var/log/Xorg.0.log"
[   177.297] 
X.Org X Server 1.21.1.4
X Protocol Version 11, Revision 0
[   177.297] Current Operating System: Linux menna-Modern-14-B4MW 6.5.0-21-generic #21~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Feb  9 13:32:52 UTC 2 x86_64
[   177.297] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=8e3391af-a68f-4cd8-9624-bd6175b03fed ro quiet splash nomodeset vt.handoff=7
[   177.297] xorg-server 2:21.1.4-2ubuntu1.7~22.04.8 (For technical support please see http://www.ubuntu.com/support) 
[   177.297] Current version of pixman: 0.40.0
[   177.297]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   177.297] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   177.297] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar  3 00:42:46 2024
[   177.297] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   177.297] (==) No Layout section.  Using the first Screen section.
[   177.297] (==) No screen section available. Using defaults.
[   177.297] (**) |-->Screen "Default Screen Section" (0)
[   177.297] (**) |   |-->Monitor "<default monitor>"
[   177.297] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   177.297] (==) Automatically adding devices
[   177.297] (==) Automatically enabling devices
[   177.298] (==) Automatically adding GPU devices
[   177.298] (==) Automatically binding GPU devices
[   177.298] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   177.298] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   177.298]     Entry deleted from font path.
[   177.298] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   177.298]     Entry deleted from font path.
[   177.298] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   177.298]     Entry deleted from font path.
[   177.298] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   177.298]     Entry deleted from font path.
[   177.298] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   177.298]     Entry deleted from font path.
[   177.298] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   177.298] (==) ModulePath set to "/usr/lib/xorg/modules"
[   177.298] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   177.298] (II) Loader magic: 0x55f3d99b5020
[   177.298] (II) Module ABI versions:
[   177.298]     X.Org ANSI C Emulation: 0.4
[   177.298]     X.Org Video Driver: 25.2
[   177.298]     X.Org XInput driver : 24.4
[   177.298]     X.Org Server Extension : 10.0
[   177.298] (++) using VT number 1

[   177.299] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c4
[   177.301] (--) PCI:*(3@0:0:0) 1002:1636:1462:12c8 rev 195, Mem @ 0xd0000000/268435456, 0xe0000000/2097152, 0xfe700000/524288, I/O @ 0x0000e000/256
[   177.301] (II) LoadModule: "glx"
[   177.301] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   177.302] (II) Module glx: vendor="X.Org Foundation"
[   177.302]     compiled for 1.21.1.4, module version = 1.0.0
[   177.302]     ABI class: X.Org Server Extension, version 10.0
[   177.302] (==) Matched ati as autoconfigured driver 0
[   177.302] (==) Matched modesetting as autoconfigured driver 1
[   177.302] (==) Matched fbdev as autoconfigured driver 2
[   177.302] (==) Matched vesa as autoconfigured driver 3
[   177.302] (==) Assigned the driver to the xf86ConfigLayout
[   177.302] (II) LoadModule: "ati"
[   177.302] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   177.302] (II) Module ati: vendor="X.Org Foundation"
[   177.302]     compiled for 1.21.1.3, module version = 19.1.0
[   177.302]     Module class: X.Org Video Driver
[   177.302]     ABI class: X.Org Video Driver, version 25.2
[   177.564] (II) LoadModule: "radeon"
[   177.564] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   177.564] (II) Module radeon: vendor="X.Org Foundation"
[   177.564]     compiled for 1.21.1.3, module version = 19.1.0
[   177.564]     Module class: X.Org Video Driver
[   177.564]     ABI class: X.Org Video Driver, version 25.2
[   177.564] (II) LoadModule: "modesetting"
[   177.564] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   177.564] (II) Module modesetting: vendor="X.Org Foundation"
[   177.564]     compiled for 1.21.1.4, module version = 1.21.1
[   177.564]     Module class: X.Org Video Driver
[   177.564]     ABI class: X.Org Video Driver, version 25.2
[   177.564] (II) LoadModule: "fbdev"
[   177.564] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   177.564] (II) Module fbdev: vendor="X.Org Foundation"
[   177.564]     compiled for 1.21.1.3, module version = 0.5.0
[   177.564]     Module class: X.Org Video Driver
[   177.564]     ABI class: X.Org Video Driver, version 25.2
[   177.564] (II) LoadModule: "vesa"
[   177.565] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   177.565] (II) Module vesa: vendor="X.Org Foundation"
[   177.565]     compiled for 1.21.1.3, module version = 2.5.0
[   177.565]     Module class: X.Org Video Driver
[   177.565]     ABI class: X.Org Video Driver, version 25.2
[   177.565] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
    ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
    ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
    ATI Radeon X600 (RV380), ATI FireGL V3200 (RV380),
    ATI Radeon IGP320 (A3), ATI Radeon IGP330/340/350 (A4),
    ATI Radeon 9500, ATI Radeon 9600TX, ATI FireGL Z1, ATI Radeon 9800SE,
    ATI Radeon 9800, ATI FireGL X2, ATI Radeon 9600, ATI Radeon 9600SE,
    ATI Radeon 9600XT, ATI FireGL T2, ATI Radeon 9650, ATI FireGL RV360,
    ATI Radeon 7000 IGP (A4+), ATI Radeon 8500 AIW,
    ATI Radeon IGP320M (U1), ATI Radeon IGP330M/340M/350M (U2),
    ATI Radeon Mobility 7000 IGP, ATI Radeon 9000/PRO, ATI Radeon 9000,
    ATI Radeon X800 (R420), ATI Radeon X800PRO (R420),
    ATI Radeon X800SE (R420), ATI FireGL X3 (R420),
    ATI Radeon Mobility 9800 (M18), ATI Radeon X800 SE (R420),
    ATI Radeon X800XT (R420), ATI Radeon X800 VE (R420),
    ATI Radeon X850 (R480), ATI Radeon X850 XT (R480),
    ATI Radeon X850 SE (R480), ATI Radeon X850 PRO (R480),
    ATI Radeon X850 XT PE (R480), ATI Radeon Mobility M7,
    ATI Mobility FireGL 7800 M7, ATI Radeon Mobility M6,
    ATI FireGL Mobility 9000 (M9), ATI Radeon Mobility 9000 (M9),
    ATI Radeon 9700 Pro, ATI Radeon 9700/9500Pro, ATI FireGL X1,
    ATI Radeon 9800PRO, ATI Radeon 9800XT,
    ATI Radeon Mobility 9600/9700 (M10/M11),
    ATI Radeon Mobility 9600 (M10), ATI Radeon Mobility 9600 (M11),
    ATI FireGL Mobility T2 (M10), ATI FireGL Mobility T2e (M11),
    ATI Radeon, ATI FireGL 8700/8800, ATI Radeon 8500, ATI Radeon 9100,
    ATI Radeon 7500, ATI Radeon VE/7000, ATI ES1000,
    ATI Radeon Mobility X300 (M22), ATI Radeon Mobility X600 SE (M24C),
    ATI FireGL M22 GL, ATI Radeon X800 (R423), ATI Radeon X800PRO (R423),
    ATI Radeon X800LE (R423), ATI Radeon X800SE (R423),
    ATI Radeon X800 XTP (R430), ATI Radeon X800 XL (R430),
    ATI Radeon X800 SE (R430), ATI Radeon X800 (R430),
    ATI FireGL V7100 (R423), ATI FireGL V5100 (R423),
    ATI FireGL unknown (R423), ATI Mobility FireGL V5000 (M26),
    ATI Mobility Radeon X700 XL (M26), ATI Mobility Radeon X700 (M26),
    ATI Radeon X550XTX, ATI Radeon 9100 IGP (A5),
    ATI Radeon Mobility 9100 IGP (U3), ATI Radeon XPRESS 200,
    ATI Radeon XPRESS 200M, ATI Radeon 9250, ATI Radeon 9200,
    ATI Radeon 9200SE, ATI FireMV 2200, ATI Radeon X300 (RV370),
    ATI Radeon X600 (RV370), ATI Radeon X550 (RV370),
    ATI FireGL V3100 (RV370), ATI FireMV 2200 PCIE (RV370),
    ATI Radeon Mobility 9200 (M9+), ATI Mobility Radeon X800 XT (M28),
    ATI Mobility FireGL V5100 (M28), ATI Mobility Radeon X800 (M28),
    ATI Radeon X850, ATI unknown Radeon / FireGL (R480),
    ATI Radeon X800XT (R423), ATI FireGL V5000 (RV410),
    ATI Radeon X700 XT (RV410), ATI Radeon X700 PRO (RV410),
    ATI Radeon X700 SE (RV410), ATI Radeon X700 (RV410),
    ATI Radeon X1800, ATI Mobility Radeon X1800 XT,
    ATI Mobility Radeon X1800, ATI Mobility FireGL V7200,
    ATI FireGL V7200, ATI FireGL V5300, ATI Mobility FireGL V7100,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1550 64-bit,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI FireGL V3300,
    ATI FireGL V3350, ATI Mobility Radeon X1450,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1650, ATI Mobility FireGL V5200,
    ATI Mobility Radeon X1600, ATI Radeon X1300 XT/X1600 Pro,
    ATI FireGL V3400, ATI Mobility FireGL V5250,
    ATI Mobility Radeon X1700, ATI Mobility Radeon X1700 XT,
    ATI FireGL V5200, ATI Radeon X2300HD, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI AMD Stream Processor,
    ATI RV560, ATI Mobility Radeon X1900, ATI Radeon X1950 GT, ATI RV570,
    ATI FireGL V7400, ATI Radeon 9100 PRO IGP,
    ATI Radeon Mobility 9200 IGP, ATI Radeon X1200, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro,
    ATI Radeon HD 2900 GT, ATI FireGL V8650, ATI FireGL V8600,
    ATI FireGL V7600, ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon HD 4850 x2, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI FirePro RV770,
    AMD FireStream 9270, AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI FirePro M7750, ATI M98, ATI Mobility Radeon HD 4650,
    ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
    ATI FirePro M5750, ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI RV610,
    ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
    ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI Radeon HD 2350,
    ATI Mobility Radeon HD 2400 XT, ATI Mobility Radeon HD 2400,
    ATI RADEON E2400, ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI Mobility Radeon HD 3870,
    ATI Mobility Radeon HD 3870 X2, ATI Radeon HD3870 X2,
    ATI FireGL V7700, ATI Radeon HD3690, AMD Firestream 9170,
    ATI Radeon HD 4550, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI FirePro V3700,
    ATI FireMV 2450, ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon 3000 Graphics, SUMO, SUMO2,
    ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI Radeon HD 5670, ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
    REDWOOD, ATI Mobility Radeon Graphics, CEDAR, ATI FirePro 2270,
    ATI Radeon HD 5450, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6700 Series, TURKS, CAICOS,
    ARUBA, TAHITI, PITCAIRN, VERDE, OLAND, HAINAN, BONAIRE, KABINI,
    MULLINS, KAVERI, HAWAII
[   177.567] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   177.567] (II) FBDEV: driver for framebuffer: fbdev
[   177.567] (II) VESA: driver for VESA chipsets: vesa
[   177.568] (EE) open /dev/dri/card0: No such file or directory
[   177.568] (WW) Falling back to old probe method for modesetting
[   177.568] (EE) open /dev/dri/card0: No such file or directory
[   177.568] (II) Loading sub module "fbdevhw"
[   177.568] (II) LoadModule: "fbdevhw"
[   177.568] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   177.568] (II) Module fbdevhw: vendor="X.Org Foundation"
[   177.568]     compiled for 1.21.1.4, module version = 0.0.2
[   177.568]     ABI class: X.Org Video Driver, version 25.2
[   177.568] (EE) Unable to find a valid framebuffer device
[   177.568] (WW) Falling back to old probe method for fbdev
[   177.568] (II) Loading sub module "fbdevhw"
[   177.568] (II) LoadModule: "fbdevhw"
[   177.568] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   177.568] (II) Module fbdevhw: vendor="X.Org Foundation"
[   177.568]     compiled for 1.21.1.4, module version = 0.0.2
[   177.568]     ABI class: X.Org Video Driver, version 25.2
[   177.568] (II) FBDEV(2): using default device
[   177.568] vesa: Refusing to run on UEFI
[   177.568] (EE) Screen 0 deleted because of no matching config section.
[   177.568] (II) UnloadModule: "modesetting"
[   177.568] (EE) Screen 0 deleted because of no matching config section.
[   177.568] (II) UnloadModule: "fbdev"
[   177.568] (II) UnloadSubModule: "fbdevhw"
[   177.568] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   177.568] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[   177.568] (==) FBDEV(0): RGB weight 888
[   177.568] (==) FBDEV(0): Default visual is TrueColor
[   177.568] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   177.568] (II) FBDEV(0): hardware: EFI VGA (video memory: 8100kB)
[   177.568] (DB) xf86MergeOutputClassOptions unsupported bus type 0
[   177.568] (II) FBDEV(0): checking modes against framebuffer device...
[   177.568] (II) FBDEV(0): checking modes against monitor...
[   177.568] (II) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[   177.568] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[   177.568] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[   177.568] (==) FBDEV(0): DPI set to (96, 96)
[   177.568] (II) Loading sub module "fb"
[   177.568] (II) LoadModule: "fb"
[   177.568] (II) Module "fb" already built-in
[   177.568] (**) FBDEV(0): using shadow framebuffer
[   177.568] (II) Loading sub module "shadow"
[   177.568] (II) LoadModule: "shadow"
[   177.568] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   177.568] (II) Module shadow: vendor="X.Org Foundation"
[   177.568]     compiled for 1.21.1.4, module version = 1.1.0
[   177.568]     ABI class: X.Org ANSI C Emulation, version 0.4
[   177.568] (II) UnloadModule: "radeon"
[   177.568] (II) Unloading radeon
[   177.569] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[   177.569] (==) FBDEV(0): Backing store enabled
[   177.569] (==) FBDEV(0): DPMS enabled
[   177.569] (II) Initializing extension Generic Event Extension
[   177.569] (II) Initializing extension SHAPE
[   177.569] (II) Initializing extension MIT-SHM
[   177.569] (II) Initializing extension XInputExtension
[   177.569] (II) Initializing extension XTEST
[   177.569] (II) Initializing extension BIG-REQUESTS
[   177.569] (II) Initializing extension SYNC
[   177.569] (II) Initializing extension XKEYBOARD
[   177.569] (II) Initializing extension XC-MISC
[   177.569] (II) Initializing extension SECURITY
[   177.569] (II) Initializing extension XFIXES
[   177.569] (II) Initializing extension RENDER
[   177.570] (II) Initializing extension RANDR
[   177.570] (II) Initializing extension COMPOSITE
[   177.570] (II) Initializing extension DAMAGE
[   177.570] (II) Initializing extension MIT-SCREEN-SAVER
[   177.570] (II) Initializing extension DOUBLE-BUFFER
[   177.570] (II) Initializing extension RECORD
[   177.570] (II) Initializing extension DPMS
[   177.570] (II) Initializing extension Present
[   177.570] (II) Initializing extension DRI3
[   177.570] (II) Initializing extension X-Resource
[   177.570] (II) Initializing extension XVideo
[   177.570] (II) Initializing extension XVideo-MotionCompensation
[   177.570] (II) Initializing extension SELinux
[   177.570] (II) SELinux: Disabled on system
[   177.570] (II) Initializing extension GLX
[   177.570] (II) AIGLX: Screen 0 is not DRI2 capable
[   177.588] (II) IGLX: Loaded and initialized swrast
[   177.588] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   177.588] (II) Initializing extension XFree86-VidModeExtension
[   177.588] (II) Initializing extension XFree86-DGA
[   177.588] (II) Initializing extension XFree86-DRI
[   177.588] (II) Initializing extension DRI2
[   177.615] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   177.615] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[   177.615] (II) LoadModule: "libinput"
[   177.615] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[   177.616] (II) Module libinput: vendor="X.Org Foundation"
[   177.616]     compiled for 1.20.14, module version = 1.2.1
[   177.616]     Module class: X.Org XInput Driver
[   177.616]     ABI class: X.Org XInput driver, version 24.1
[   177.616] (II) Using input driver 'libinput' for 'Power Button'
[   177.617] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 24 paused 0
[   177.617] (**) Power Button: always reports core events
[   177.617] (**) Option "Device" "/dev/input/event3"
[   177.619] (II) event3  - Power Button: is tagged by udev as: Keyboard
[   177.619] (II) event3  - Power Button: device is a keyboard
[   177.619] (II) event3  - Power Button: device removed
[   177.619] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   177.619] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   177.619] (**) Option "xkb_model" "pc105"
[   177.619] (**) Option "xkb_layout" "us"
[   177.620] (II) event3  - Power Button: is tagged by udev as: Keyboard
[   177.620] (II) event3  - Power Button: device is a keyboard
[   177.620] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   177.620] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[   177.620] (II) Using input driver 'libinput' for 'Video Bus'
[   177.621] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 27 paused 0
[   177.621] (**) Video Bus: always reports core events
[   177.621] (**) Option "Device" "/dev/input/event5"
[   177.623] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[   177.623] (II) event5  - Video Bus: device is a keyboard
[   177.623] (II) event5  - Video Bus: device removed
[   177.623] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:14/LNXVIDEO:00/input/input7/event5"
[   177.623] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   177.624] (**) Option "xkb_model" "pc105"
[   177.624] (**) Option "xkb_layout" "us"
[   177.625] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[   177.626] (II) event5  - Video Bus: device is a keyboard
[   177.627] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   177.627] (II) No input driver specified, ignoring this device.
[   177.627] (II) This device may have been added with another device file.
[   177.628] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   177.628] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[   177.628] (II) Using input driver 'libinput' for 'Power Button'
[   177.629] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 28 paused 0
[   177.629] (**) Power Button: always reports core events
[   177.629] (**) Option "Device" "/dev/input/event1"
[   177.630] (II) event1  - Power Button: is tagged by udev as: Keyboard
[   177.630] (II) event1  - Power Button: device is a keyboard
[   177.630] (II) event1  - Power Button: device removed
[   177.631] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[   177.631] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[   177.631] (**) Option "xkb_model" "pc105"
[   177.631] (**) Option "xkb_layout" "us"
[   177.632] (II) event1  - Power Button: is tagged by udev as: Keyboard
[   177.632] (II) event1  - Power Button: device is a keyboard
[   177.633] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   177.633] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[   177.633] (II) Using input driver 'libinput' for 'Sleep Button'
[   177.634] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 29 paused 0
[   177.634] (**) Sleep Button: always reports core events
[   177.634] (**) Option "Device" "/dev/input/event2"
[   177.635] (II) event2  - Sleep Button: is tagged by udev as: Keyboard
[   177.635] (II) event2  - Sleep Button: device is a keyboard
[   177.636] (II) event2  - Sleep Button: device removed
[   177.636] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[   177.636] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[   177.636] (**) Option "xkb_model" "pc105"
[   177.636] (**) Option "xkb_layout" "us"
[   177.637] (II) event2  - Sleep Button: is tagged by udev as: Keyboard
[   177.637] (II) event2  - Sleep Button: device is a keyboard
[   177.638] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event10)
[   177.638] (II) No input driver specified, ignoring this device.
[   177.638] (II) This device may have been added with another device file.
[   177.639] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event12)
[   177.639] (II) No input driver specified, ignoring this device.
[   177.639] (II) This device may have been added with another device file.
[   177.640] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event13)
[   177.640] (II) No input driver specified, ignoring this device.
[   177.640] (II) This device may have been added with another device file.
[   177.640] (II) config/udev: Adding input device gpio-keys (/dev/input/event11)
[   177.640] (II) No input driver specified, ignoring this device.
[   177.640] (II) This device may have been added with another device file.
[   177.641] (II) config/udev: Adding input device ELAN0300:00 04F3:30AA Mouse (/dev/input/event7)
[   177.641] (**) ELAN0300:00 04F3:30AA Mouse: Applying InputClass "libinput pointer catchall"
[   177.641] (II) Using input driver 'libinput' for 'ELAN0300:00 04F3:30AA Mouse'
[   177.642] (II) systemd-logind: got fd for /dev/input/event7 13:71 fd 30 paused 0
[   177.642] (**) ELAN0300:00 04F3:30AA Mouse: always reports core events
[   177.642] (**) Option "Device" "/dev/input/event7"
[   177.644] (II) event7  - ELAN0300:00 04F3:30AA Mouse: is tagged by udev as: Mouse Pointingstick
[   177.645] (II) event7  - ELAN0300:00 04F3:30AA Mouse: device is a pointer
[   177.646] (II) event7  - ELAN0300:00 04F3:30AA Mouse: device removed
[   177.646] (**) Option "config_info" "udev:/sys/devices/platform/AMDI0010:01/i2c-0/i2c-ELAN0300:00/0018:04F3:30AA.0001/input/input12/event7"
[   177.646] (II) XINPUT: Adding extended input device "ELAN0300:00 04F3:30AA Mouse" (type: MOUSE, id 10)
[   177.646] (**) Option "AccelerationScheme" "none"
[   177.646] (**) ELAN0300:00 04F3:30AA Mouse: (accel) selected scheme none/0
[   177.646] (**) ELAN0300:00 04F3:30AA Mouse: (accel) acceleration factor: 2.000
[   177.646] (**) ELAN0300:00 04F3:30AA Mouse: (accel) acceleration threshold: 4
[   177.648] (II) event7  - ELAN0300:00 04F3:30AA Mouse: is tagged by udev as: Mouse Pointingstick
[   177.649] (II) event7  - ELAN0300:00 04F3:30AA Mouse: device is a pointer
[   177.650] (II) config/udev: Adding input device ELAN0300:00 04F3:30AA Mouse (/dev/input/mouse0)
[   177.650] (II) No input driver specified, ignoring this device.
[   177.650] (II) This device may have been added with another device file.
[   177.651] (II) config/udev: Adding input device ELAN0300:00 04F3:30AA Touchpad (/dev/input/event9)
[   177.651] (**) ELAN0300:00 04F3:30AA Touchpad: Applying InputClass "libinput touchpad catchall"
[   177.651] (II) Using input driver 'libinput' for 'ELAN0300:00 04F3:30AA Touchpad'
[   177.653] (II) systemd-logind: got fd for /dev/input/event9 13:73 fd 31 paused 0
[   177.653] (**) ELAN0300:00 04F3:30AA Touchpad: always reports core events
[   177.653] (**) Option "Device" "/dev/input/event9"
[   177.654] (II) event9  - ELAN0300:00 04F3:30AA Touchpad: is tagged by udev as: Touchpad
[   177.656] (II) event9  - ELAN0300:00 04F3:30AA Touchpad: device is a touchpad
[   177.656] (II) event9  - ELAN0300:00 04F3:30AA Touchpad: device removed
[   177.657] (**) Option "config_info" "udev:/sys/devices/platform/AMDI0010:01/i2c-0/i2c-ELAN0300:00/0018:04F3:30AA.0001/input/input14/event9"
[   177.657] (II) XINPUT: Adding extended input device "ELAN0300:00 04F3:30AA Touchpad" (type: TOUCHPAD, id 11)
[   177.658] (**) Option "AccelerationScheme" "none"
[   177.658] (**) ELAN0300:00 04F3:30AA Touchpad: (accel) selected scheme none/0
[   177.658] (**) ELAN0300:00 04F3:30AA Touchpad: (accel) acceleration factor: 2.000
[   177.658] (**) ELAN0300:00 04F3:30AA Touchpad: (accel) acceleration threshold: 4
[   177.658] (II) event9  - ELAN0300:00 04F3:30AA Touchpad: is tagged by udev as: Touchpad
[   177.659] (II) event9  - ELAN0300:00 04F3:30AA Touchpad: device is a touchpad
[   177.660] (II) config/udev: Adding input device ELAN0300:00 04F3:30AA Touchpad (/dev/input/mouse1)
[   177.660] (II) No input driver specified, ignoring this device.
[   177.660] (II) This device may have been added with another device file.
[   177.660] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   177.660] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[   177.660] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[   177.661] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 32 paused 0
[   177.661] (**) AT Translated Set 2 keyboard: always reports core events
[   177.661] (**) Option "Device" "/dev/input/event4"
[   177.661] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[   177.661] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[   177.662] (II) event4  - AT Translated Set 2 keyboard: device removed
[   177.662] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   177.662] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[   177.662] (**) Option "xkb_model" "pc105"
[   177.662] (**) Option "xkb_layout" "us"
[   177.663] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[   177.663] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[   177.663] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[   177.663] (**) ETPS/2 Elantech Touchpad: Applying InputClass "libinput touchpad catchall"
[   177.663] (II) Using input driver 'libinput' for 'ETPS/2 Elantech Touchpad'
[   177.664] (II) systemd-logind: got fd for /dev/input/event8 13:72 fd 33 paused 0
[   177.664] (**) ETPS/2 Elantech Touchpad: always reports core events
[   177.664] (**) Option "Device" "/dev/input/event8"
[   177.664] (II) event8  - ETPS/2 Elantech Touchpad: is tagged by udev as: Touchpad
[   177.665] (II) event8  - ETPS/2 Elantech Touchpad: device is a touchpad
[   177.665] (II) event8  - ETPS/2 Elantech Touchpad: device removed
[   177.665] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event8"
[   177.665] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[   177.666] (**) Option "AccelerationScheme" "none"
[   177.666] (**) ETPS/2 Elantech Touchpad: (accel) selected scheme none/0
[   177.666] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[   177.666] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[   177.667] (II) event8  - ETPS/2 Elantech Touchpad: is tagged by udev as: Touchpad
[   177.667] (II) event8  - ETPS/2 Elantech Touchpad: device is a touchpad
[   177.668] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse2)
[   177.668] (II) No input driver specified, ignoring this device.
[   177.668] (II) This device may have been added with another device file.
[   177.669] (II) config/udev: Adding input device MSI WMI hotkeys (/dev/input/event6)
[   177.669] (**) MSI WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[   177.669] (II) Using input driver 'libinput' for 'MSI WMI hotkeys'
[   177.670] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 34 paused 0
[   177.670] (**) MSI WMI hotkeys: always reports core events
[   177.670] (**) Option "Device" "/dev/input/event6"
[   177.671] (II) event6  - MSI WMI hotkeys: is tagged by udev as: Keyboard
[   177.671] (II) event6  - MSI WMI hotkeys: device is a keyboard
[   177.671] (II) event6  - MSI WMI hotkeys: device removed
[   177.671] (**) Option "config_info" "udev:/sys/devices/virtual/input/input11/event6"
[   177.671] (II) XINPUT: Adding extended input device "MSI WMI hotkeys" (type: KEYBOARD, id 14)
[   177.671] (**) Option "xkb_model" "pc105"
[   177.671] (**) Option "xkb_layout" "us"
[   177.671] (II) event6  - MSI WMI hotkeys: is tagged by udev as: Keyboard
[   177.671] (II) event6  - MSI WMI hotkeys: device is a keyboard
[   252.072] (**) Option "fd" "24"
[   252.072] (II) event3  - Power Button: device removed
[   252.073] (**) Option "fd" "27"
[   252.073] (II) event5  - Video Bus: device removed
[   252.074] (**) Option "fd" "28"
[   252.074] (II) event1  - Power Button: device removed
[   252.074] (**) Option "fd" "29"
[   252.074] (II) event2  - Sleep Button: device removed
[   252.075] (**) Option "fd" "30"
[   252.075] (II) event7  - ELAN0300:00 04F3:30AA Mouse: device removed
[   252.076] (**) Option "fd" "31"
[   252.076] (II) event9  - ELAN0300:00 04F3:30AA Touchpad: device removed
[   252.076] (**) Option "fd" "32"
[   252.076] (II) event4  - AT Translated Set 2 keyboard: device removed
[   252.077] (**) Option "fd" "33"
[   252.077] (II) event8  - ETPS/2 Elantech Touchpad: device removed
[   252.078] (**) Option "fd" "34"
[   252.078] (II) event6  - MSI WMI hotkeys: device removed
[   252.079] (II) systemd-logind: got pause for 13:69
[   252.080] (II) systemd-logind: got pause for 13:73
[   252.080] (II) systemd-logind: got pause for 13:70
[   252.080] (II) systemd-logind: got pause for 13:72
[   252.080] (II) systemd-logind: got pause for 13:65
[   252.080] (II) systemd-logind: got pause for 13:67
[   252.080] (II) systemd-logind: got pause for 13:71
[   252.080] (II) systemd-logind: got pause for 13:68
[   252.080] (II) systemd-logind: got pause for 13:66
[   252.111] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 260 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.111] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 251 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.112] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 265 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.112] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 265 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.112] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 272 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.113] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 278 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.113] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 274 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.113] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 276 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.113] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 280 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.113] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 237 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.114] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 254 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.114] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 254 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.114] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 254 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.115] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 283 called but device is disabled.
This driver cannot change properties on a disabled device
[   252.115] (II) libinput: ETPS/2 Elantech Touchpad: SetProperty on 285 called but device is disabled.
This driver cannot change properties on a disabled device
[   262.014] (II) UnloadModule: "libinput"
[   262.014] (II) systemd-logind: releasing fd for 13:70
[   262.041] (II) UnloadModule: "libinput"
[   262.041] (II) systemd-logind: releasing fd for 13:72
[   262.060] (II) UnloadModule: "libinput"
[   262.060] (II) systemd-logind: releasing fd for 13:68
[   262.080] (II) UnloadModule: "libinput"
[   262.080] (II) systemd-logind: releasing fd for 13:73
[   262.116] (II) UnloadModule: "libinput"
[   262.116] (II) systemd-logind: releasing fd for 13:71
[   262.136] (II) UnloadModule: "libinput"
[   262.136] (II) systemd-logind: releasing fd for 13:66
[   262.168] (II) UnloadModule: "libinput"
[   262.168] (II) systemd-logind: releasing fd for 13:65
[   262.192] (II) UnloadModule: "libinput"
[   262.192] (II) systemd-logind: releasing fd for 13:69
[   262.212] (II) UnloadModule: "libinput"
[   262.212] (II) systemd-logind: releasing fd for 13:67
[   262.246] (II) Server terminated successfully (0). Closing log file.
```

Would appreciate any help I'm going mad because of this x_X I also tried Windows to make sure that hardware was fine and it was working flawlessly.

---

### Post by TheFu on 2024-03-02
You said you had the same kernel as me.  You do not.
You also said you were running 20.04. You are not.

---

### Post by Yellow Pasque on 2024-03-02
> [   177.297] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=8e3391af-a68f-4cd8-9624-bd6175b03fed ro quiet splash **nomodeset** vt.handoff=7

Booting with 'nomodeset' guarantees the correct amdgpu driver doesn't get loaded. The Xorg log won't tell us anything useful in that case. Remove that from the boot line and reboot. If amdgpu module isn't loaded, see what happens when you try it manually:
```
sudo modprobe -v amdgpu
```

---

### Post by mennashazly on 2024-03-02
> **TheFu said:**
> You said you had the same kernel as me.  You do not.
You also said you were running 20.04. You are not.

Yes, sorry for the confusion I reinstalled a fresh installation of ubuntu22.04 to see if everything will be fixed, but the problem persits.

---

### Post by Rovano on 2024-03-05
You provide little information. We don't know your in-between steps and stuff.

Here someone solved it simply.
[https://forum.zorin.com/t/unknown-display-after-update-amd-ryzen-5-4500u/16489/12](https://forum.zorin.com/t/unknown-display-after-update-amd-ryzen-5-4500u/16489/12)
Shortly. Used the in-kernel driver instead of the AMD driver. He kicked it out of the system.

---

### Post by snowcrash1 on 2024-08-23
this random guy told me I should switch the video card so it works out of the box, since There Are Alternatives...  (drivers are a pain to develop) ... that work out of the box like even, because that's why we pay system76 so much money, is because the drivers work for stuff they're purchasing, researching, and finding modsets for the kernel, right?  Its called a battle tune that we need drivers, so, you know video is pretty important and we fought with NVidia and others for years to provide drivers, Or We'll Have To Buy Something Else.  there was nothing else we could do.

my problem is acpi function is buggy, but I stopped buy with my two cents
He said I should get an Apple Radeon 6770M MXM Card, and it'll just work

---

