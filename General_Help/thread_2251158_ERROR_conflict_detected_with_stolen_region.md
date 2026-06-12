---
title: "ERROR conflict detected with stolen region"
date: 2014-11-01
forum: General Help
---

### Post by pc.maint on 2014-11-01
I have a similar error [to [http://ubuntuforums.org/showthread.php?t=2218287]](http://ubuntuforums.org/showthread.php?t=2218287]) on my system since adding a new video card. I have on-board Intel graphics driving one monitor and a NVIDA card driving another monitor. The system boots and runs, then after a while (could be hours or days), the system hangs, totally unresponsive with this error message on one of the monitors:

[   13.390800] [drm:i915_stolen_to_physical] *ERROR* conflict detected with stolen region: [0xbba00000 - 0xbfa00000]

I think this is some sort of conflict between the two display interfaces as this system ran OK before installing the new card.

Very annoying as this system normally runs 24/7 with no problems.

If anyone has any ideas, I would be grateful. Thanks...


System details are as follows:

-------------------------------------------------------------------------------
Installation details:
---------------------
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
---------------------------------------
List of PCI devices:
--------------------
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fc8 (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
03:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
04:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
05:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
06:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
08:00.0 IDE interface: Marvell Technology Group Ltd. 88SE9172 SATA III 6Gb/s RAID Controller (rev 11)
-------------------------------------------------------------------------------

---

### Post by oldos2er on 2014-11-02
Post moved to its own thread.

---

