---
title: "Issue with onboard audio on device Asus A8V-VM board"
date: 2008-04-26
forum: General Help
---

### Post by berlinbrown on 2008-04-26
I have tried everything with this board.  And I can't tell if it is the board or the drivers or something.

I have installed:

Ubuntu Heron:

And I have read this forum.
[http://ubuntuforums.org/showthread.php?t=260352](http://ubuntuforums.org/showthread.php?t=260352)

But, I am still not getting sound.  And I have been using this board for 2 years now.

It comes and goes and now it is in the gone part.  At least as of yesterday.

For those that have a similar board

Sometimes I go into the BIOS and reset the bios settings to the default, reboot and the sound will be detected and come back.

Sometimes, simply restarting will bring the sound back.

-------------------------

bbrown@houston:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
	Flags: bus master, medium devsel, latency 8
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
	Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
	Subsystem: Unknown device 0008:0000
	Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>

00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: ddf00000-dfffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
	Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 222
	I/O ports at d800 [size=8]
	I/O ports at d400 [size=4]
	I/O ports at d000 [size=8]
	I/O ports at c800 [size=4]
	I/O ports at c400 [size=16]
	Memory at ddeffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at c000 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at b800 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at b400 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at b000 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at ddeff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
	Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
	Flags: medium devsel
	Capabilities: <access denied>

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
	Subsystem: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
	Flags: bus master, medium devsel, latency 128
	Capabilities: <access denied>

00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0

00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: d0000000-d7ffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel

02:00.0 VGA compatible controller: nVidia Corporation NV37GL [Quadro FX 330/GeForce PCX 5300] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 9681
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at df000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at ddfe0000 [disabled] [size=128K]
	Capabilities: <access denied>

05:08.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
	Subsystem: D-Link System Inc Unknown device 1408
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at e800 [size=256]
	Memory at fbfffc00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at fb020000 [disabled] [size=64K]
	Capabilities: <access denied>

05:09.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Unknown device b309
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 23
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at fb000000 [disabled] [size=128K]
	Capabilities: <access denied>



I would get another card, but I am out of slots.

---

