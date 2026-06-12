---
title: "Problems with the graphics on my laptop"
date: 2019-10-02
forum: General Help
---

### Post by daniel-pbt on 2019-10-02
Since I changed version 16: 04 by 18:04, I have problems with the graphics on my laptop. Attached photos. What can I do?
My graphics card information:
[COLOR=#000000][FONT=Courier 10 Pitch]lspci -vnn | grep VGA -A 12 (Terminal)[/FONT][/COLOR]

01:00.0 VGAcompatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI]Park [Mobility Radeon HD 5430/5450/5470] [1002:68e0](prog-if 00 [VGA controller])

[ATTACH=CONFIG]284128[/ATTACH][ATTACH=CONFIG]284129[/ATTACH]

Thanks in any case

---

### Post by cruzer001 on 2019-10-03
Have you checked for errors?
```
dmesg | egrep 'drm|radeon'
```

---

### Post by daniel-pbt on 2019-10-05
Well look, I hadn't.
These are the results:


daniel@daniel-K52Dr:~$ dmesg | egrep 'drm | radeon'
[    4.692637] [drm] radeon kernel modesetting enabled.
[    4.714681] fb: switching to radeondrmfb from VESA VGA
[    4.715603] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    4.715605] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[    4.715824] [drm] radeon: 1024M of VRAM memory ready
[    4.715826] [drm] radeon: 1024M of GTT memory ready.
[    4.764320] [drm] radeon: dpm initialized
[    4.766675] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    4.782825] radeon 0000:01:00.0: WB enabled
[    4.782828] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0x        (ptrval)
[    4.782830] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0x        (ptrval)
[    4.783559] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0x        (ptrval)
[    4.783564] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    4.783614] radeon 0000:01:00.0: radeon: using MSI.
[    4.783637] [drm] radeon: irq initialized.
[    6.087630] fbcon: radeondrmfb (fb0) is primary device
[    6.087778] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    6.113874] [drm] Initialized radeon 2.50.0 20080528 for 0000:01:00.0 on minor 0
[ 1349.416601] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[ 1349.422190] radeon 0000:01:00.0: WB enabled
[ 1349.422194] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0x00000000b87866c6
[ 1349.422196] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0x00000000863ed530
[ 1349.422925] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0x00000000ea4c4133

[CENTER][FONT=Roboto]But I don't understand the messages that appear.[/FONT][[FONT=Roboto]Should I do something after the results that the terminal has returned?



[/FONT]
[/CENTER]

---

### Post by mörgæs on 2019-10-05
I'm writing from a computer with a graphics processor close to yours (Mobility Radeon HD 4650/5165) and all works fine in Lubuntu 18.04. Could you try a live boot of this one for comparison?

---

### Post by daniel-pbt on 2019-10-06
[ATTACH=CONFIG]284155[/ATTACH]


[FONT=arial]I just tried it, and I haven't noticed any problems. Perhaps in a photo that I attached, the firefox icon appears somewhat strange, although I do not know if the same thing happens to you[/FONT]

---

### Post by mörgæs on 2019-10-06
Then you at least know that a fresh install of Lubuntu will give a good result. 

I'm not familiar with Ubuntu so I can't help you here, sorry.

---

### Post by mastablasta on 2019-10-07
are you using Wayland maybe? would it help if you switched over to X sever?

how do any full screen apps behave (e.g. games?). what happens if you run for example phoronix test suite? the chip you have should have descent opensource driver support.

---

### Post by daniel-pbt on 2019-10-07
[COLOR=#777777][FONT=Roboto][COLOR=rgba(0, 0, 0, 0.54)]Traducir del: inglés
[/COLOR]


3007/5000

[CENTER]
[/CENTER]





[/FONT][/COLOR]
[COLOR=#777777][FONT=Roboto][CENTER]
[/CENTER]

[COLOR=rgba(0, 0, 0, 0.87)]Forgive my ignorance, but I don't know what Wayland or Xserver are.
I have passed the Phoronic Test, these are the results:
Interactive Shell

Generating Shell Cache ...
Refreshing OpenBenchmarking.org Repository Cache ...

  PROCESSOR: AMD Phenom II N830 Triple-Core @ 2.10GHz
    Core Count: 3
    Extensions: SSE 4a
    Cache Size: 512 KB
    Microcode: 0x10000c8
    Scaling Driver: acpi-cpufreq ondemand

  GRAPHICS: ASUS AMD Mobility Radeon HD 5430/5450/5470 1GB
    OpenGL: 3.3 Mesa 19.3.0-devel (git-a1ff8db 2019-09-26 bionic-oibaf-ppa) (LLVM 9.0.0)
    Display Driver: modesetting 1.19.6
    Screen: 1366x768

  MOTHERBOARD: ASUS K52Dr v1.0
    BIOS Version: K52Dr.206
    Chipset: AMD RS880
    Audio: Realtek ALC269VB
    Network: JMicron JMC250 PCI + Qualcomm Atheros AR9285

  MEMORY: 4096MB

  DISK: 120GB SanDisk SDSSDA12 + 32GB SC32G
    File-System: ext4
    Mount Options: data = ordered errors = remount-ro relatime rw
    Disk Scheduler: CFQ

  OPERATING SYSTEM: Ubuntu 18.04
    Kernel: 4.15.0-65-generic (x86_64)
    Desktop: GNOME Shell 3.28.3
    Display Server: X Server 1.19.6
    Compiler: GCC 7.4.0
    Security: l1tf: Not affected
                      + mds: Not affected
                      + meltdown: Not affected
                      + spec_store_bypass: Not affected
                      + specter_v1: Mitigation of usercopy / swapgs barriers and __user pointer sanitization
                      + specter_v2: Mitigation of Full AMD retpoline STIBP: disabled RSB filling


     CPU Temperature: 70.00 C CPU Usage (Summary): 41.38%
     GPU Temperature: 64.00 C Memory Usage: 2460 MB
  System Temperature: 68.00 C System Uptime 25 M
I don't understand much, but I don't see anything weird
On the other hand, the applications where I notice these problems, are those that appear in the previous photos (calendar, shutdown menu for example), Freecad, .. Games I have none :([/COLOR]



[/FONT][/COLOR]

---

### Post by mastablasta on 2019-10-08
[https://wayland.freedesktop.org/](https://wayland.freedesktop.org/)
> [COLOR=#000000][FONT=&quot]Wayland is intended as a simpler replacement for X, easier to develop and maintain. GNOME and KDE are expected to be ported to it.
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]
Wayland is a protocol for a compositor to talk to its clients as well as a C library implementation of that protocol. The compositor can be a standalone display server running on Linux kernel modesetting and evdev input devices, an X application, or a wayland client itself. The clients can be traditional applications, X servers (rootless or fullscreen) or other display servers.[/FONT][/COLOR]

in any case you can switch between both in Ubuntu (i believe before logging in). But for example Kubuntu comes with the old X server by default. Likely the Lubuntu also comes with X server by default. and since it works...

i asked about games because they are more demanding for GPU. just to see if something is overheating or if the GPU maybe had damaged ram or if there is a driver issue. phoronic has a couple of GPU test where it runs a demo from the game. that is more or less the same.

---

