---
title: "How to fix Ubuntu Budgie window glitch."
date: 2018-05-24
forum: General Help
---

### Post by neutron183 on 2018-05-24
This is the issue I have everything else works fine until I size the window horizontally check video below.
I have amd A4 3300m core 2 duo. 

[https://youtu.be/JINF6ugNzBQ](https://youtu.be/JINF6ugNzBQ)

---

### Post by cruzer001 on 2018-05-24
Could you need a driver upgrade?  How bout posting your system specs.

```
inxi -b
```

---

### Post by neutron183 on 2018-05-24
Thanks cruzer001 here is my specs. 

System:    Host: Linux-PC-HP Kernel: 4.15.0-22-generic x86_64 bits: 64
           Desktop: Budgie 10.4  Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: Hewlett-Packard product: HP Pavilion g7 Notebook PC v: 0691120000204610000620100 serial: N/A
           Mobo: Hewlett-Packard model: 3568 v: 21.46 serial: N/A
           BIOS: Insyde v: F.6A date: 05/13/2013
CPU:       Dual core AMD A4-3300M APU with Radeon HD Graphics (-MCP-)
           speed/max: 799/1900 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Sumo [Radeon HD 6480G]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1600x900@60.12hz
           OpenGL: renderer: AMD SUMO (DRM 2.50.0 / 4.15.0-22-generic, LLVM 6.0.0)
           version: 3.3 Mesa 18.0.0-rc5
Network:   Card-1: Realtek RTL8188CE 802.11b/g/n WiFi Adapter
           driver: rtl8192ce
           Card-2: Realtek RTL810xE PCIE Fast Ethernet controller
           driver: r8169
Drives:    HDD Total Size: 1000.2GB (0.9% used)
Info:      Processes: 184 Uptime: 28 min Memory: 833.0/3418.9MB
           Client: Shell (bash) inxi: 2.3.56

---

### Post by cruzer001 on 2018-05-25
Hello

The only thing I have came up with is this similar bug report against "mutter".

[https://bugs.launchpad.net/ubuntubudgie/+bug/1767264](https://bugs.launchpad.net/ubuntubudgie/+bug/1767264)

---

