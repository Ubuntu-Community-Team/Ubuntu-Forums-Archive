---
title: "Ubuntu on Dell Inspiron E1505 no audio"
date: 2008-05-05
forum: General Help
---

### Post by lyceum on 2008-05-05
I have a friend that bought a Dell Inspiron E1505 notebook with Ubuntu, worked great. She asked me to upgrade, so I did and it worked great. She was using a bit of space, so then I decided to just reinstall, as she would not loose anything. Now the audio does not work and the restricted driver manager does not find it :confused:

Here is the best part, the audio works on the live CD!

Any ideas on what to do here?

---

### Post by gjj391 on 2008-05-05
what audio driver is it?

---

### Post by lyceum on 2008-05-05
> **gjj391 said:**
> what audio driver is it?

Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

I tried the info here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) but it did not work.

Also, the  Intel Corporation PRO/Wireless 3945ABG Network Connection was not detected so it is not working either. Again, the odd thing is that they DO work with the live CD. I ran a test on the CD, it is good. I am lost here.

Not sure if it will help, but here is what I got when I ran lspci-v I am not sure if anything else is also not running.

> 
lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at eff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at eff8 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at efec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, fast devsel, latency 0
	Memory at eff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Memory behind bridge: efd00000-efdfffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: efa00000-efcfffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e01fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: ef900000-ef9fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Dell Unknown device 01bd
	Flags: medium devsel, IRQ 4
	I/O ports at 10c0 [size=32]

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Inspiron 6400
	Flags: bus master, fast devsel, latency 64, IRQ 22
	Memory at ef9fe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at ef9fd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at ef9fd400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
	Subsystem: Dell Unknown device 01bd
	Flags: medium devsel, IRQ 11
	Memory at ef9fd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
	Subsystem: Dell Unknown device 01bd
	Flags: medium devsel, IRQ 11
	Memory at ef9fd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1020
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at efdff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>


---

