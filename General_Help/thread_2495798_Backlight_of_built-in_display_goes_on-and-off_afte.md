---
title: "Backlight of built-in display goes on-and-off after changing brightness (intel gpu)"
date: 2024-03-02
forum: General Help
---

### Post by patrik-t on 2024-03-02
Hello!

After fresh installation, brightness of the built-in display is at maximum. If I decrease brightness to 50%, it goes 2 seconds full black, then 2 seconds max brightness and the cycle repeats. If I set it to 25%, it goes 3 seconds full black and 1 second max brightness etc. If I set to 100% again, the on-and-off cycle stops and the display stays on all the time. Can you help me please?

It's a Lenovo IdeaPad Flex 5 laptop with Linux Mint Cinnamon 21.3 (I also tried Ubuntu 23.10, Ubuntu 22.04, Ubuntu 20.04 and Xubuntu all had the same issue).
I used to have Ubuntu 20.04 and brightness control used to work (nvidia card turned off). Now it doesn't work with 20.04 either (maybe something got upgraded?). Brightness control works properly if I dual boot to Windows of course.

1) I have disabled my nvidia graphics card in the BIOS menu, so this is strictly related to integrated intel graphics
2) I'm changing brightness like this:
```

echo 40000000 | sudo tee /sys/class/backlight/intel_backlight/brightness

```
(40000000 for 50% because /sys/class/backlight/intel_backlight/max_brightness is around 80000000)
3) I upgraded kernel from 5.15 to 6.5.0-oem, it did not help
4) I have updated BIOS firmware recently, it did not help

System:
```

[COLOR=#000000]System:[/COLOR]  Host: p-IdeaPad-Flex-5 Kernel: 6.5.0-1015-oem x86_64 bits: 64
    Desktop: Cinnamon 6.0.4 Distro: Linux Mint 21.3 Virginia
Machine:
  Type: Convertible System: LENOVO product: 81X3 v: IdeaPad Flex 5 15IIL05
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40700 WIN
    serial: <superuser required> UEFI: LENOVO v: ECCN46WW date: 08/23/2023
Battery:
  ID-1: BAT0 charge: 26.7 Wh (59.5%) condition: 44.9/52.5 Wh (85.6%)
    volts: 11.8 min: 11.5
CPU:
  Info: quad core Intel Core i5-1035G1 [MT MCP] speed (MHz): avg: 400
    min/max: 400/3600
Graphics:
  Device-1: Intel Iris Plus Graphics G1 driver: i915 v: kernel
  Device-2: Acer Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics (ICL GT1)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2
Network:
  Device-1: Intel Ice Lake-LP PCH CNVi WiFi driver: iwlwifi
Drives:
  Local Storage: total: 476.94 GiB used: 10.68 GiB (2.2%)
Info:
  Processes: 258 Uptime: 37m Memory: 7.42 GiB used: 1.12 GiB (15.0%)
  Shell: Bash inxi: 3.3.13
```


Maybe I could try an older xserver-xorg-video-intel driver? Unfortunately I don't know how to do that, apt offers only a single version of this package.

Note: cross-posted here: [https://forums.linuxmint.com/viewtopic.php?t=415103](https://forums.linuxmint.com/viewtopic.php?t=415103)

---

### Post by patrik-t on 2024-03-22
Update: loading default BIOS settings in the BIOS menu fixed this issue.

---

