---
title: "External monitor not detected. Fresh install 22"
date: 2024-04-23
forum: General Help
---

### Post by Hachi-Roku on 2024-04-23
Hello legends!

External Monitor is not detected at all. Gui settings nor terminal. Terminal commands tell me Display port is empty (but it's plugged in and cable connections seem good)


Running ubuntu studio 22 with KDE plasma. Got a second montior connected via a display port. 
DP--> HDMI adapter cable ----> HDMI monitor port.


Monitor and HDMI cable elimination tests were successful.

Hunted for solutions but most seem to be for NVIDIA setups, which mine isn't.

I've disabled secure boot (one of the solutions found). No change.

Any ideas very much appreciated!!


```
System:
  Kernel: 6.5.0-26-lowlatency x86_64 bits: 64 compiler: N/A
    Desktop: KDE Plasma 5.24.7 tk: Qt 5.15.3 wm: kwin_x11 vt: 1 dm: SDDM
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: HP product: HP EliteBook 840 G3 v: N/A
    serial: <superuser required> Chassis: type: 10 serial: <superuser required>
  Mobo: HP model: 8079 v: KBC Version 85.79 serial: <superuser required>
    UEFI: HP v: N75 Ver. 01.57 date: 07/28/2022

Graphics:
  Device-1: Intel Skylake GT2 [HD Graphics 520]
    vendor: Hewlett-Packard EliteBook 840 G3 driver: i915 v: kernel ports:
    active: eDP-1 empty: DP-1, DP-2, HDMI-A-1, HDMI-A-2 bus-ID: 00:02.0
    chip-ID: 8086:1916 class-ID: 0300
  Device-2: Chicony HP HD Camera type: USB driver: uvcvideo bus-ID: 1-9:5
    chip-ID: 04f2:b51c class-ID: 0e02
  Display: x11 server: X.Org v: 1.21.1.4 compositor: kwin_x11 driver: X:
    loaded: modesetting unloaded: fbdev,vesa gpu: i915 display-ID: :0
    screens: 1
  Screen-1: 0 s-res: 1366x768 s-dpi: 96 s-size: 361x203mm (14.2x8.0")
    s-diag: 414mm (16.3")
 ** Monitor-1: eDP-1 **model: BOE Display res: 1366x768 hz: 60 dpi: 112
    size: 309x173mm (12.2x6.8") diag: 354mm (13.9") modes: 1366x768
  OpenGL: renderer: Mesa Intel HD Graphics 520 (SKL GT2)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2 direct render: Yes
```


xrandr output:

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 16384 x 16384
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1366x768      60.01*+  39.97  
...
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)

```

Not sure why it has 2 DP's and 2 HDMI's when I have 1 DP and don't have any HDMI port


Thank you!

---

