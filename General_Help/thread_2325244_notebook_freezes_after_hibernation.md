---
title: "notebook freezes after hibernation"
date: 2016-05-20
forum: General Help
---

### Post by bobptz on 2016-05-20
Hi
 

 I have an acer notebook with ubuntu 14.04 LTS that frequently freezes when it goes into hibernation mode.  I lift up the screen, the power light is already on, I press the power button and there is no response.  I also notice that the notebook is hot, as if it was in operation mode.
 

 The only way to boot it is to remove the power cord and battery and then press the power button.
 

 Here is a copy of the syslog at a time when this happened last time:
 [http://www.pastebin.ca/3603562](http://www.pastebin.ca/3603562)
 

 It seems that the system froze on May 18 23:46:13 and booted back on May 19 00:35:26.
 Anybody can shed some light as to why it happened?

---

### Post by X-RED_Tech on 2016-05-20
Are you really hibernating or suspending? Huge difference...

---

### Post by bobptz on 2016-05-21
Not 100% sure.  I close the screen and put the notebook in my bag.    Isn't this hibernation?  

Is there a test I can do to check?

---

### Post by X-RED_Tech on 2016-05-22
Actually that's suspension.

Such issues are usually related with graphics drivers. If you have nvidia or AMD perhaps it's a good idea to try the proprietary drivers. If not please post the hardware specs.

---

### Post by bobptz on 2016-05-22
One more symptom is that I go to open my laptop and it has run out of battery.  Obviously it was not shut, although I had closed the screen.

```

$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
04:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 10)

```

---

### Post by bobptz on 2016-05-26
Can somebody spot a problem with the specs?  Do you see a problem with the VGA?

---

### Post by him610 on 2016-05-26
Not enough info. How about running this harmless command from a terminal...

*inxi -b*

---

### Post by bobptz on 2016-05-26
No problem.  Ask anything.  I am not proficient with linux.

```
~$ inxi -b
System:    Host: vasiliki-acer Kernel: 3.19.0-59-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Acer product: V5-131 version: V2.17
           Mobo: Acer model: Mimic version: Type2 - Board Version Bios: Acer version: V2.17 date: 03/22/2013
CPU:       Dual core Intel Celeron CPU 1007U (-MCP-) clocked at 989.355 MHz 
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller 
           X.Org: 1.17.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile GLX Version: 3.0 Mesa 10.5.9
Network:   Card-1: Broadcom NetLink BCM57785 Gigabit Ethernet PCIe driver: tg3 
           Card-2: Broadcom BCM4313 802.11bgn Wireless Network Adapter driver: wl 
Drives:    HDD Total Size: 320.1GB (20.7% used)
Info:      Processes: 253 Uptime: 13:44 Memory: 1441.3/5788.6MB Client: Shell (bash) inxi: 1.9.17 

```

---

### Post by bobptz on 2016-06-05
I post the info you asked me guys.  The problem persists.  I am afraid some day the laptop will burn.

---

