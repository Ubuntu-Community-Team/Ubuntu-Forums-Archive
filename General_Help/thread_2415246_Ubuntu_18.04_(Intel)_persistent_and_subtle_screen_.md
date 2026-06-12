---
title: "Ubuntu 18.04 (Intel) persistent and subtle screen flickering? HP Envy x360"
date: 2019-03-23
forum: General Help
---

### Post by zhet on 2019-03-23
I keep getting this subtle but persistent flickering issue and it is driving me insane. I have read several threads and I've tried the methods but it doesn't help. So here's what I've done so far without any success.

[LIST=1]
[*]I've changed my refresh rate below 60, I've done 59 and I've the lowest 40 but doesn't help.
[*]I've added the /etc/X11/xorg.conf.d with which still didn't work
```
Section "Device"
Identifier "Intel Graphics"
Driver "intel"
Option "TearFree" "true"
EndSection
```
[/LIST]
Here are the specs for my computer:
```
System: Host: dan-HP-ENVY-x360-Convertible-15m-cn0xxx Kernel: 4.18.0-16-generic x86_64 bits: 64 Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.2 LTS
Machine: Device: un-determined System: HP product: HP ENVY x360 Convertible 15m-cn0xxx v: Type1ProductConfigId serial: N/A Mobo: HP model: 8483 v: 70.28 serial: N/A UEFI: Insyde v: F.15 date: 07/12/2018
Battery BAT0: charge: 30.6 Wh 57.8% condition: 52.9/52.9 Wh (100%) hidpp__0: charge: N/A condition: NA/NA Wh
CPU: Quad core Intel Core i7-8550U (-MT-MCP-) speed/max: 798/4000 MHz
Graphics: Card: Intel UHD Graphics 620 Display Server: x11 (X.Org 1.20.1 ) driver: i915 Resolution: 1920x1080@40.00hz OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2) version: 4.5 Mesa 18.2.2
Network: Card: Intel Wireless 7265 driver: iwlwifi
Drives: HDD Total Size: 256.1GB (10.1% used)
Info: Processes: 319 Uptime: 37 min Memory: 2038.9/11751.1MB Client: Shell (bash) inxi: 2.3.56
```
If someone could help me, it would be greatly appreciated.

---

