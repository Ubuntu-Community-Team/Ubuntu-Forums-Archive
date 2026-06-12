---
title: "Can't get 2 x 1440p monitor at correct resolution"
date: 2017-03-16
forum: General Help
---

### Post by gingabyte on 2017-03-16
So... I have 2 x 1440p monitors. One connected over HDMI and the other over DP. Both work fine at 1440 under windows (Intel drivers)
Under ubuntu the monitor connected over DP works at 1440 but the other will only go to 1080
Is there anything I can do about this?

Motherboard is h81l-plus
16.04.2
Thanks

---

### Post by QIII on 2017-03-16
Hello!

We need more information.  

Who is the manufacturer of your motherboard?

Who is the manufacturer and what models are your monitors.

Most importantly:  Who is the manufacturer and what is the model of your graphics card?  Are you using an open-source driver or a proprietary driver?

---

### Post by gingabyte on 2017-03-16
Asus [COLOR=#000000]h81l-plus - onboard graphics
Monitors are [/COLOR][h=1]ASUS PB258Q[/h]Cheers

---

### Post by him610 on 2017-03-16
From the command line, please run...
```
inxi -b
```
and report the results

---

### Post by gingabyte on 2017-03-17
```
System:    Host: Chris-Desktop Kernel: 4.8.0-36-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: HP product: HP EliteDesk 800 G2 DM 35W
           Mobo: HP model: 8055 v: KBC Version 05.22
           Bios: HP v: N21 Ver. 02.19 date: 06/01/2016
CPU:       Quad core Intel Core i5-6500T (-MCP-) speed/max: 899/3100 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 2560x1440@59.95hz, 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 12.0.6
Network:   Card: Intel Ethernet Connection (2) I219-LM driver: e1000e
Drives:    HDD Total Size: 256.1GB (5.6% used)
Info:      Processes: 264 Uptime: 1:33 Memory: 2619.7/7863.5MB
           Client: Shell (bash) inxi: 2.2.35 
chris@Chris-Desktop:~$ ^C
chris@Chris-Desktop:~$ 
```

---

