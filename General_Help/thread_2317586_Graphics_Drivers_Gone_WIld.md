---
title: "Graphics Drivers Gone WIld"
date: 2016-03-17
forum: General Help
---

### Post by uRock on 2016-03-17
I made the mistake of installing the XORG AMD/ATI driver listed in Additional Drivers, now I can't get back to my old driver.

The one that is now installed has a much lower resolution and it only supports a single monitor.

Output of lspci```
uRock@uRock:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
03:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe (rev 01)
```
```
uRock@uRock:~$ uname -r
4.2.0-34-generic

``` I'd be grateful for any help getting the AMD Catalyst driver going.

---

### Post by deadflowr on 2016-03-17
So, you switched from AMD's fglrx driver to  the Xorg driver?

Did you remove the xorg.conf file?
I had that issue once, and the cause was that the xorg.conf file was still be read, and the since the information in it was bunk, the system balked.
Removing the file cleared it up, for me.

(I think a full reboot was needed. instead of a quick X killing)

---

### Post by uRock on 2016-03-17
I will give it a try.

Cheers & Beers!

---

### Post by uRock on 2016-03-18
That didn't work, so I went ahead an reinstalled ubuntu. I wanted to get back to the 3.* kernel, so it was for the best to do it.

---

