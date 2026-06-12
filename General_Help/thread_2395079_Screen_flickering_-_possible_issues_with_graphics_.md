---
title: "Screen flickering - possible issues with graphics card broken?"
date: 2018-06-26
forum: General Help
---

### Post by larry2311 on 2018-06-26
I am seeing a similar, if not the same symptom on a older Lenovo laptop. Should I post here or a new thread?

---

### Post by slickymaster on 2018-06-26
Moved to a thread of its own.

Please provide some more information about your system, like distribution version, computer specs, etc.

---

### Post by larry2311 on 2018-06-26
```
$ inxi -bG
System:    Host: system01 Kernel: 4.13.0-45-generic x86_64 (64 bit)
           Desktop: Unity 7.4.5  Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO (portable) product: 7458AW4 v: ThinkPad X200
           Mobo: LENOVO model: 7458AW4
           Bios: LENOVO v: 6DET72WW (3.22 ) date: 10/25/2012
CPU:       Dual core Intel Core2 Duo P8600 (-MCP-)
           speed/max: 1616/2401 MHz
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa)
           Resolution: 1280x800@60.00hz, 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Mobile Intel GM45 Express
           GLX Version: 2.1 Mesa 17.2.8
Network:   Card-1: Intel 82567LM Gigabit Network Connection
           driver: e1000e
           Card-2: Intel Ultimate N WiFi Link 5300 driver: iwlwifi
Drives:    HDD Total Size: 2000.4GB (46.9% used)
Info:      Processes: 245 Uptime: 7 days Memory: 4727.9/7871.7MB
           Client: Shell (bash) inxi: 2.2.35 

```
```

$ lspci -nnk | egrep -i 'VGA|display'
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
```

---

### Post by larry2311 on 2018-06-26
The flickering occurs after a screen blank return, i.e. laptop screen and external monitor, screen blanks after timeout. On mouse move or key touch screen restores and has sections flashing/flickering. A mouse click on the flickering area(s) ceases the flickering.

---

### Post by larry2311 on 2018-07-01
Looks like no one else has any ideas, as well.

---

### Post by larry2311 on 2018-09-27
As no one has any pearls of wisdom, so I'll upgrade to Bionic and see if the Lenovo laptop with "Mobile Intel GM45 Express Chipset " graphics still has segments of the screen, screen flickering after resuming from a locked screen.

---

