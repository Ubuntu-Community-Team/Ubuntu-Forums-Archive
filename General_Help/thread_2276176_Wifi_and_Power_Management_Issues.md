---
title: "Wifi and Power Management Issues"
date: 2015-04-30
forum: General Help
---

### Post by s_spiff on 2015-04-30
Just got a Lenovo Y40 - 80 and installed Xubuntu on it. Ethernet works great, wifi doesn't connect. It's not disabled (I searched on stackoverflow and ubuntu forums for Y40 Wifi issues. Everyone seems to have their wireless card disabled.. No such issues here). 

Another quirky bit is that I have an apple magic mouse connected via bluetooth. Works well except for occasionally dropping the connection. I just figured that the battery of the mouse is showing up in the power management console, which is weird. And every time the mouse reconnects, I get a notification about how it's discharging.


Anyone have any suggestions on how to resolve these two issues?

---

### Post by Geoffrey_Arndt on 2015-04-30
Well, the mouse charge level is a normal "feature" of the power mgmt console . . in addition to the laptop battery charge level.   

Re drops for wireless mouse . . . what model?   I find the "M325" Logitech mini-mouse works perfect with the several laptops I've used (Logitech is Linux friendly).

Re Wireless - - what chipset do you have (broadcom, ralink, realtek, athereos, etc.)?    Am assuming you went thru the regular routine in the "Software & Updates" program tabs "Additional Drivers" and did the updates/installs?

---

### Post by s_spiff on 2015-04-30
I'm using a Magic Mouse by Apple actually. other mice require me to plug a dongle into the usb slot. 


As for the wireless, I did the apt-get update. Nothing showed up on additional drivers except my amd radeon graphics card driver

if I run lspci -nn I get the following:

```


lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Broadwell-U Host Bridge -OPI [8086:1604] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09)
00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Wildcat Point-LP USB xHCI Controller [8086:9cb1] (rev 03)
00:16.0 Communication controller [0780]: Intel Corporation Wildcat Point-LP MEI Controller #1 [8086:9cba] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation Wildcat Point-LP High Definition Audio Controller [8086:9ca0] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 [8086:9c90] (rev e3)
00:1c.1 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 [8086:9c92] (rev e3)
00:1c.2 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 [8086:9c94] (rev e3)
00:1c.3 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 [8086:9c96] (rev e3)
00:1c.4 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 [8086:9c98] (rev e3)
00:1d.0 USB controller [0c03]: Intel Corporation Wildcat Point-LP USB EHCI Controller [8086:9ca6] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation Wildcat Point-LP LPC Controller [8086:9cc3] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] [8086:9c83] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation Wildcat Point-LP SMBus Controller [8086:9ca2] (rev 03)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5249 PCI Express Card Reader [10ec:5249] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
04:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
05:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M / R9 M275X] [1002:6820] (rev ff)


```

Based on this output I'm guessing I have a Intel Wireless 3160 controller?

---

### Post by sandyd on 2015-04-30
Moved to General Help

---

### Post by Geoffrey_Arndt on 2015-05-01
Re wireless . . . yes, Intel's A/C.    Should have kernel level support (plug n play) in Ubuntu 15.04.

---

