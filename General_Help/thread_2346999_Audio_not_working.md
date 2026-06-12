---
title: "Audio not working"
date: 2016-12-20
forum: General Help
---

### Post by hyburn on 2016-12-20
greetings,

my audio is not working

lspci:
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
***************
I have tried switching to the unkown proprietary driver and that did not fix it
tried plugging into different ports to ensure it was not a coding issue
and yes, volume is on... no speakers just headphones

walkthrough from:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

lspci -v | grep -A7 -i "audio" Results:
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
	Subsystem: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 33
	Memory at f7914000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller (prog-if 30 [XHCI])
--
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
	Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family HD Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at f7910000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0) (prog-if 00 [Normal decode])
--
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
	Subsystem: eVga.com. Corp. Device 3966
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

Not sure how to interpret this info.

also checked the alsa site:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

I progressed through a troubleshoot and it says that I may have found a bug. I submitted a bug report...

will keep this thread posted on the results

***************
Thanks

---

### Post by hyburn on 2016-12-20
I had the genius idea of testing the front plug... BOOM! its fixed. would this still be considered a code issue?

---

### Post by nothingspecial on 2016-12-21
Did you check alsamixer had everything turned up?

> **hyburn said:**
> I had the genius idea of testing the front plug... BOOM! its fixed. would this still be considered a code issue?


> **nothingspecial said:**
> I decided I needed a computer. My brother-in-law kindly donated his old one with Ubuntu 7.04 installed.

Everything was fine for a few months until I decided to move the computer to another room and upgrade to 7.10. I found that the sound no longer worked. This is when I discovered Ubuntu Forums. I asked for help and quickly learned all sorts of complicated linux stuff like compiling alsa and blacklisting modules, and how to partition and install an operating system.

In the end it turned out that when I had moved the computer I had plugged the speakers into the blue hole instead of the green one. 

---

