---
title: "Buggy X @ ubuntu 16.04LTS"
date: 2016-05-09
forum: General Help
---

### Post by nuno13 on 2016-05-09
Hi,

My X windows are messy on ubuntu 16.04LTS, sometimes text is hidden, sometimes it only shows a part of it... any idea what it could be? I had no problems on 12.04LTS.

[IMG]http://s32.postimg.org/p1y6uvtqd/messy_x_2.png[/IMG]

Regards.

---

### Post by $yl9pAR%t on 2016-05-09
Some info about your computer probably would be helpful. Please, paste here output of:

```
inxi -b
```

---

### Post by nuno13 on 2016-05-10
> **mefisto888 said:**
> Some info about your computer probably would be helpful. Please, paste here output of:

```
inxi -b
```

System:    Host: aumkara Kernel: 4.4.0-22-generic x86_64 (64 bit) Desktop: Unity 7.4.0
           Distro: Ubuntu 16.04 xenial
Machine:   System: Dell (portable) product: Latitude E5550 v: 01
           Mobo: Dell model: 06DJY6 v: A00 Bios: Dell v: A06 date: 04/10/2015
CPU:       Dual core Intel Core i5-5300U (-HT-MCP-) speed/max: 2300/2900 MHz
Graphics:  Card: Intel Broadwell-U Integrated Graphics
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa) Resolution: 1920x1080@60.02hz
           GLX Renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2) GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: Intel Ethernet Connection (3) I218-LM driver: e1000e
           Card-2: Intel Wireless 7265 driver: iwlwifi
Drives:    HDD Total Size: 500.1GB (27.7% used)
Info:      Processes: 314 Uptime: 23:58 Memory: 4380.4/7874.8MB Client: Shell (bash) inxi: 2.2.35

---

### Post by cmcanulty on 2016-05-10
I have had similar issues for a few years and this always fixes it. Change the system font (in xubuntu it is in settings manager-appearance-fonts) then I can change right back to my preferred font and all is OK. Seems to happen every few weeks or so.Fairly irritating bug though.

---

### Post by nuno13 on 2016-05-10
> **cmcanulty said:**
> I have had similar issues for a few years and this always fixes it. Change the system font (in xubuntu it is in settings manager-appearance-fonts) then I can change right back to my preferred font and all is OK. Seems to happen every few weeks or so.Fairly irritating bug though.

I've tried to change the font but it didn't fix the problem...

---

### Post by speartip on 2016-05-10
Have you checked in additional drivers, to see if there is a proprietary graphics driver available, that might resolve your issue.

---

### Post by nuno13 on 2016-05-10
> **speartip said:**
> Have you checked in additional drivers, to see if there is a proprietary graphics driver available, that might resolve your issue.

I only have this:
[IMG]http://s32.postimg.org/sy9nu6nrp/additionaldrivers.png[/IMG]

---

### Post by speartip on 2016-05-10
Looks like you're already using the proprietary driver. In that case change to "do not use the device" & reboot, see if using open source drivers helps.
If not you can always revert back again.

---

### Post by nuno13 on 2016-05-10
That's CPU, not graphics.

---

### Post by speartip on 2016-05-10
> **nuno13 said:**
> That's CPU, not graphics.
You're correct. Sorry, my fault for not reading it properly. 
In that case i'm out of ideas.

---

