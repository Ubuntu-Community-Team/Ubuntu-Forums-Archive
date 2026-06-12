---
title: "Help with ubuntu 14.04 / Hp x2 detachable 10-n101ns (no audio)"
date: 2016-01-24
forum: General Help
---

### Post by antonio60 on 2016-01-24
Hello, excuse my spelling, I'm using google translator ...


I installed Ubuntu 14.04 on an HP Pavilion x2 detachable 10-n101ns acquired recently. With the 3.13 kernel works well, but does not recognize sound card, network card wifi, battery, micro, camera ... When upgrading Kernel to 4.4 I managed to recognize the network card and touch screen, but still does not recognize the battery , speakers, camera ... etc. In other kernel versions from 4.0 recognizes the battery, network card, battery and touch screen, but the system remains frozen after a few minutes or be used randomly in terms of time.
Can someone help me please? A greeting.

---

### Post by antonio60 on 2016-01-24
antonio@antonio-HP-Pavilion-x2-Detachable:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Device 2280 (rev 22)
	Subsystem: Hewlett-Packard Company Device 813e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Kernel driver in use: iosf_mbi_pci


00:02.0 VGA compatible controller: Intel Corporation Device 22b0 (rev 22) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 813e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 313
	Region 0: Memory at 90000000 (64-bit, non-prefetchable) [size=16M]
	Region 2: Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 1000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915


00:03.0 Multimedia controller: Intel Corporation Device 22b8 (rev 22)
	Subsystem: Hewlett-Packard Company Device 813e
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at 91000000 (32-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>


00:0a.0 Non-VGA unclassified device: Intel Corporation Device 22d8 (rev 22)
	Subsystem: Hewlett-Packard Company Device 813e
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at 9193c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>


00:0b.0 Signal processing controller: Intel Corporation Device 22dc (rev 22)
	Subsystem: Device 7270:8086
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 311
	Region 0: Memory at 91918000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: proc_thermal


00:14.0 USB controller: Intel Corporation Device 22b5 (rev 22) (prog-if 30 [XHCI])
	Subsystem: Hewlett-Packard Company Device 813e
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 116
	Region 0: Memory at 91900000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd


00:1a.0 Encryption controller: Intel Corporation Device 2298 (rev 22)
	Subsystem: Hewlett-Packard Company Device 813e
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 312
	Region 0: Memory at 91800000 (32-bit, non-prefetchable) [size=1M]
	Region 1: Memory at 91700000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: mei_txe


00:1c.0 PCI bridge: Intel Corporation Device 22c8 (rev 22) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: 91600000-916fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:1f.0 ISA bridge: Intel Corporation Device 229c (rev 22)
	Subsystem: Hewlett-Packard Company Device 813e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich


01:00.0 Network controller: Intel Corporation Device 3165 (rev 81)
	Subsystem: Intel Corporation Device 4010
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 314
	Region 0: Memory at 91600000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi

---

### Post by antonio60 on 2016-01-25
Can anyone help me get the PC to detect the sound card?

---

