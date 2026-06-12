---
title: "Recent update breaks AC'97 sound"
date: 2008-02-09
forum: General Help
---

### Post by tibiker1966 on 2008-02-09
Anyone else having this problem?

After applying the latest update to my laptop running on 7.04, sound no longer works.

Here's a troubling log message I am now seeing in dmesg:

[   34.060000] AC'97 1 does not respond - RESET
[   34.072000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   34.072000] ali mixer 1 creating error.

Anyone else seeing this - or is it time for a new laptop? 

More info:

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 320 M


00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
	Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Audio
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at 8400 [size=256]
	Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

---

### Post by yannn on 2008-04-11
pretty much the same problem here. i do have sound though. my problem is that the modem doesn't work. i'm using kubuntu 7.10.

my dmesg messages:
> [  233.012000] AC'97 1 does not respond - RESET
[  233.012000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[  233.068000] intel8x0_measure_ac97_clock: measured 55353 usecs
[  322.532000] AC'97 1 does not respond - RESET
[  322.532000] AC'97 1 access is not valid [0xffffffff], removing mixer.

---

### Post by santhony on 2008-05-28
same problem here also, I have M5451 PCI AC-Link Controller , which doesnt' work anymore..

Any fix to this??

---

