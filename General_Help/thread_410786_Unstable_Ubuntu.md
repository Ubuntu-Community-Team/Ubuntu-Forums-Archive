---
title: "Unstable Ubuntu"
date: 2007-04-16
forum: General Help
---

### Post by sirevert on 2007-04-16
Hi, I'm new to linux but I thought I give it a try after seeing pictures of Ubuntu and the new Gnome. I installed "Ubuntu 6.10 - the Edgy Ef" and everything worked flawless.

But, after a while the system gets unstable, slow mouse, not responding to commands *(nothing specific triggers this)

It's pretty much a clean install except for:
[LIST]
[*]enabled divx suppport with xine.
[*]enabled encryption for gaim.
[*]enabled all upgrades.
[/LIST]

I hope someone can give me some directions where to look to find the source for this problem ;) like i said I'm pretty new.

---

### Post by sirevert on 2007-04-22
1 week later, I replaced "Ubuntu 6.10 - the Edgy Ef" for Ubuntu 7.04 - the Feisty Fawn" It's running since last Thursday. But I'm still facing the same problems, after a while the system just stalls.

- Slow mouse.
- Not reacting to keys or clicks.
- Eventually the complete system hangs.

But this time I have some data from the event log which is related to it *(I think, it happened the moment the system became instable.

```
Apr 22 15:22:18 ubuntu kernel: [ 3032.530715] irq 10: nobody cared (try booting with the "irqpoll" option)
Apr 22 15:22:18 ubuntu kernel: [ 3032.530765]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Apr 22 15:22:18 ubuntu kernel: [ 3032.530788]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
Apr 22 15:22:18 ubuntu kernel: [ 3032.530799]  [<f887df32>] usb_hcd_irq+0x22/0x60 [usbcore]
Apr 22 15:22:18 ubuntu kernel: [ 3032.530864]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Apr 22 15:22:18 ubuntu kernel: [ 3032.530872]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
Apr 22 15:22:18 ubuntu kernel: [ 3032.530881]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Apr 22 15:22:18 ubuntu kernel: [ 3032.530894]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Apr 22 15:22:18 ubuntu kernel: [ 3032.530911]  =======================
Apr 22 15:22:18 ubuntu kernel: [ 3032.530913] handlers:
Apr 22 15:22:18 ubuntu kernel: [ 3032.530916] [<f887df10>] (usb_hcd_irq+0x0/0x60 [usbcore])
Apr 22 15:22:18 ubuntu kernel: [ 3032.530937] [<f887df10>] (usb_hcd_irq+0x0/0x60 [usbcore])
Apr 22 15:22:18 ubuntu kernel: [ 3032.530958] Disabling IRQ #10
```

Earlier today I  also managed to hit ctrl+alt+backspace just when it was about to happen again, which resulted in a load of errors at the prompt, which I should have written down, they were related to ata.00 and I got a load of disk-errors, yet I'm not using any ata disks, 2x sata on a low-budget raid-pci card with raid mode disabled since Ubuntu doesn't support it.

---

### Post by Arlanthir on 2007-04-22
It's been 2 days now since I installed feisty (no upgrade, fresh install) and it never happened again.. I hope it stays that way. In case it happens again, I'll post something ;)

---

### Post by eyelessfade on 2007-04-22
What kind of hardware do you have.
could you post a link to your "lspci", "lspci -vv", "dmesg"

---

### Post by sirevert on 2007-04-22
Voila, I hope it says more to you then it does to me ;)

```
lspci:
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
```
```

lspci -vv
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 8
        Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: e0000000-e1ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
        Subsystem: VIA Technologies, Inc. VT82C686/A PCI to ISA Bridge
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        Region 4: I/O ports at b000 [size=16]
        Capabilities: <access denied>

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin D routed to IRQ 10
        Region 4: I/O ports at b400 [size=32]
        Capabilities: <access denied>

00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin D routed to IRQ 10
        Region 4: I/O ports at b800 [size=32]
        Capabilities: <access denied>

00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin ? routed to IRQ 9
        Capabilities: <access denied>

00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
        Subsystem: Micro-Star International Co., Ltd. MS-6330 Onboard Audio
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 11
        Region 0: I/O ports at bc00 [size=256]
        Region 1: I/O ports at c000 [size=4]
        Region 2: I/O ports at c400 [size=4]
        Capabilities: <access denied>

00:09.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
        Subsystem: Silicon Image, Inc. SiI 3112 SATARaid Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at cc00 [size=8]
        Region 1: I/O ports at d000 [size=4]
        Region 2: I/O ports at d400 [size=8]
        Region 3: I/O ports at d800 [size=4]
        Region 4: I/O ports at dc00 [size=16]
        Region 5: Memory at e3000000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 50000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 17
        Region 0: I/O ports at e000 [size=256]
        Region 1: Memory at e3001000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 50080000 [disabled] [size=64K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01) (prog-if 00 [VGA])
        Subsystem: C.P. Technology Co. Ltd Unknown device 2063
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (2000ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at a000 [size=256]
        Region 2: Memory at e1000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e0000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
        Subsystem: C.P. Technology Co. Ltd Unknown device 2062
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (2000ns min), Cache Line Size: 32 bytes
        Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Region 1: Memory at e1010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
```
```

dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000003000 end: 000000003fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000003fff3000 size: 000000000000d000 end: 0000000040000000 type: 3
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f66c0
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 VIA694                                ) @ 0x000f80c0
[    0.000000] ACPI: RSDT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[    0.000000] ACPI: FADT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[    0.000000] ACPI: MADT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff5880
[    0.000000] ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:4 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfff0000)
[    0.000000] Detected 1394.588 MHz processor.
[   26.105369] Built 1 zonelists.  Total pages: 260081
[   26.105375] Kernel command line: root=UUID=6b650231-84cc-4ea3-a247-5845d1a3111e ro quiet splash
[   26.105623] mapped APIC to ffffd000 (fee00000)
[   26.105627] mapped IOAPIC to ffffc000 (fec00000)
[   26.105633] Enabling fast FPU save and restore... done.
[   26.105653] Initializing CPU#0
[   26.105775] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   26.106890] Console: colour VGA+ 80x25
[   26.108460] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.110917] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.172855] Memory: 1028060k/1048512k available (1992k kernel code, 19680k reserved, 893k data, 328k init, 131008k highmem)
[   26.172873] virtual kernel memory layout:
[   26.172875]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   26.172877]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.172879]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   26.172881]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   26.172883]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   26.172885]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   26.172887]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   26.172892] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.249719] Calibrating delay using timer specific routine.. 2791.79 BogoMIPS (lpj=5583594)
[   26.249801] Security Framework v1.0.0 initialized
[   26.249818] SELinux:  Disabled at boot.
[   26.249847] Mount-cache hash table entries: 512
[   26.250160] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000
[   26.250174] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.250178] CPU: L2 Cache: 256K (64 bytes/line)
[   26.250183] CPU: After all inits, caps: 0183fbff c1c7fbff 00000000 00000420 00000000 00000000 00000000
[   26.250207] Compat vDSO mapped to ffffe000.
[   26.250221] Remapping vsyscall page to ffffe000
[   26.250239] Checking 'hlt' instruction... OK.
[   26.265785] SMP alternatives: switching to UP code
[   26.266336] Freeing SMP alternatives: 11k freed
[   26.266752] Early unpacking initramfs... done
[   26.735054] ACPI: Core revision 20060707
[   26.742030] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   26.744480] CPU0: AMD Athlon(tm) processor stepping 04
[   26.744514] Total of 1 processors activated (2791.79 BogoMIPS).
[   26.745280] ENABLING IO-APIC IRQs
[   26.745638] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.889526] Brought up 1 CPUs
[   26.889977] Booting paravirtualized kernel on bare hardware
[   26.890095] Time: 16:34:31  Date: 03/22/107
[   26.890155] NET: Registered protocol family 16
[   26.890334] EISA bus registered
[   26.890342] ACPI: bus type pci registered
[   26.922859] PCI: PCI BIOS revision 2.10 entry at 0xfb590, last bus=1
[   26.922862] PCI: Using configuration type 1
[   26.922865] Setting up standard PCI resources
[   26.936768] ACPI: Interpreter enabled
[   26.936776] ACPI: Using IOAPIC for interrupt routing
[   26.937615] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.937626] PCI: Probing PCI hardware (bus 00)
[   26.937730] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   26.938195] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   26.938201] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   26.938427] Boot video device is 0000:01:00.0
[   26.938507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.953843] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[   26.954207] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   26.954613] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   26.955013] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   26.957755] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.957775] pnp: PnP ACPI init
[   26.961179] pnp: PnP ACPI: found 12 devices
[   26.961187] PnPBIOS: Disabled by ACPI PNP
[   26.961296] PCI: Using ACPI for IRQ routing
[   26.961302] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.986664] NET: Registered protocol family 8
[   26.986667] NET: Registered protocol family 20
[   26.987547] PCI: Bridge: 0000:00:01.0
[   26.987551]   IO window: a000-afff
[   26.987557]   MEM window: e0000000-e1ffffff
[   26.987562]   PREFETCH window: d0000000-dfffffff
[   26.987582] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.987632] NET: Registered protocol family 2
[   27.017560] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.018016] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   27.022695] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   27.025059] TCP: Hash tables configured (established 131072 bind 65536)
[   27.025067] TCP reno registered
[   27.033639] checking if image is initramfs... it is
[   27.921371] Freeing initrd memory: 6993k freed
[   27.922234] audit: initializing netlink socket (disabled)
[   27.922263] audit(1177259671.900:1): initialized
[   27.922379] highmem bounce pool size: 64 pages
[   27.922483] VFS: Disk quotas dquot_6.5.1
[   27.922528] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.922627] io scheduler noop registered
[   27.922632] io scheduler anticipatory registered
[   27.922635] io scheduler deadline registered
[   27.922646] io scheduler cfq registered (default)
[   27.922670] Applying VIA southbridge workaround.
[   27.922676] PCI: Enabling Via external APIC routing
[   27.923052] isapnp: Scanning for PnP cards...
[   28.277318] isapnp: No Plug & Play device found
[   28.319932] Real Time Clock Driver v1.12ac
[   28.320013] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.320205] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.320552] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.321678] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.322174] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.322581] mice: PS/2 mouse device common for all mice
[   28.323464] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.323921] input: Macintosh mouse button emulation as /class/input/input0
[   28.323974] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   28.323980] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.324305] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   28.324310] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   28.576786] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.577102] EISA: Probing bus 0 at eisa.0
[   28.577133] Cannot allocate resource for EISA slot 4
[   28.577137] Cannot allocate resource for EISA slot 5
[   28.577140] Cannot allocate resource for EISA slot 6
[   28.577153] EISA: Detected 0 cards.
[   28.607295] TCP cubic registered
[   28.607305] NET: Registered protocol family 1
[   28.607344] Using IPI No-Shortcut mode
[   28.607445] ACPI: (supports S0 S1 S4 S5)
[   28.607512]   Magic number: 3:367:591
[   28.607653]   hash matches device ptyc9
[   28.608556] Freeing unused kernel memory: 328k freed
[   28.608708] Time: tsc clocksource has been installed.
[   28.622751] input: AT Translated Set 2 keyboard as /class/input/input1
[   29.951376] Capability LSM initialized
[   30.803173] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   30.803206] VP_IDE: chipset revision 6
[   30.803210] VP_IDE: not 100% native mode: will probe irqs later
[   30.803225] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
[   30.803236]     ide0: BM-DMA at 0xb000-0xb007, BIOS settings: hda:pio, hdb:DMA
[   30.803256]     ide1: BM-DMA at 0xb008-0xb00f, BIOS settings: hdc:pio, hdd:pio
[   30.803269] Probing IDE interface ide0...
[   30.826533] usbcore: registered new interface driver usbfs
[   30.826588] usbcore: registered new interface driver hub
[   30.826627] usbcore: registered new device driver usb
[   30.828165] USB Universal Host Controller Interface driver v3.0
[   30.906224] SCSI subsystem initialized
[   30.913936] libata version 2.20 loaded.
[   30.927117] 8139too Fast Ethernet driver 0.9.28
[   31.047288] Floppy drive(s): fd0 is 1.44M
[   31.102876] FDC 0 is a post-1991 82077
[   31.975344] hdb: HL-DT-ST DVDRAM GSA-4120B, ATAPI CD/DVD-ROM drive
[   32.036694] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   32.037093] Probing IDE interface ide1...
[   32.613526] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   32.613547] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   32.613557] PCI: VIA VLink IRQ fixup for 0000:00:07.2, from 12 to 10
[   32.613590] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   32.614198] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   32.614245] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000b400
[   32.615265] usb usb1: configuration #1 chosen from 1 choice
[   32.615641] hub 1-0:1.0: USB hub found
[   32.615666] hub 1-0:1.0: 2 ports detected
[   32.635440] hdb: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   32.635458] Uniform CD-ROM driver Revision: 3.20
[   32.723065] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   32.723078] PCI: VIA VLink IRQ fixup for 0000:00:07.3, from 12 to 10
[   32.723110] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   32.723153] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   32.723184] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000b800
[   32.723350] usb usb2: configuration #1 chosen from 1 choice
[   32.723389] hub 2-0:1.0: USB hub found
[   32.723408] hub 2-0:1.0: 2 ports detected
[   32.831121] sata_sil 0000:00:09.0: version 2.2
[   32.831160] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 16
[   32.831309] ata1: SATA max UDMA/100 cmd 0xf884e080 ctl 0xf884e08a bmdma 0xf884e000 irq 16
[   32.831362] ata2: SATA max UDMA/100 cmd 0xf884e0c0 ctl 0xf884e0ca bmdma 0xf884e008 irq 16
[   32.831388] scsi0 : sata_sil
[   32.966714] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   33.148141] usb 1-1: configuration #1 chosen from 1 choice
[   33.302581] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   33.315763] ata1.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[   33.315774] ata1.00: ATA-7: Maxtor 6L300S0, BACE1G20, max UDMA/133
[   33.315778] ata1.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   33.327728] ata1.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[   33.327735] ata1.00: configured for UDMA/100
[   33.327744] ata1: EH pending after completion, repeating EH (cnt=4)
[   33.327767] scsi1 : sata_sil
[   33.538477] usbcore: registered new interface driver hiddev
[   33.552134] input: Logitech Trackball as /class/input/input2
[   33.552302] input: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:07.2-1
[   33.552337] usbcore: registered new interface driver usbhid
[   33.552343] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   33.798353] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   33.811543] ata2.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[   33.811554] ata2.00: ATA-7: Maxtor 6L300S0, BACE1G20, max UDMA/133
[   33.811558] ata2.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   33.823558] ata2.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[   33.823572] ata2.00: configured for UDMA/100
[   33.823583] ata2: EH pending after completion, repeating EH (cnt=4)
[   33.823827] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L300S0   BACE PQ: 0 ANSI: 5
[   33.824608] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6L300S0   BACE PQ: 0 ANSI: 5
[   33.824999] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 19 (level, low) -> IRQ 17
[   33.825299] eth0: RealTek RTL8139 at 0xf8844000, 00:50:fc:e6:be:04, IRQ 17
[   33.825302] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   33.830383] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   33.845931] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
[   33.845959] sda: Write Protect is off
[   33.845963] sda: Mode Sense: 00 3a 00 00
[   33.845985] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.846098] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
[   33.846111] sda: Write Protect is off
[   33.846114] sda: Mode Sense: 00 3a 00 00
[   33.846132] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.846138]  sda: sda1 sda2 sda3
[   33.887816] sd 0:0:0:0: Attached scsi disk sda
[   33.888052] SCSI device sdb: 586114704 512-byte hdwr sectors (300091 MB)
[   33.888073] sdb: Write Protect is off
[   33.888076] sdb: Mode Sense: 00 3a 00 00
[   33.888098] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.888169] SCSI device sdb: 586114704 512-byte hdwr sectors (300091 MB)
[   33.888181] sdb: Write Protect is off
[   33.888185] sdb: Mode Sense: 00 3a 00 00
[   33.888204] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.888209]  sdb: sdb1
[   33.908925] sd 1:0:0:0: Attached scsi disk sdb
[   33.916122] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   33.916292] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   34.199570] Attempting manual resume
[   34.199578] swsusp: Resume From Partition 8:3
[   34.199581] PM: Checking swsusp image.
[   34.199843] PM: Resume from disk failed.
[   34.240745] kjournald starting.  Commit interval 5 seconds
[   34.240767] EXT3-fs: mounted filesystem with ordered data mode.
[   41.134300] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[   42.622352] NET: Registered protocol family 17
[   44.345953] parport_pc: VIA 686A/8231 detected
[   44.345961] parport_pc: probing current configuration
[   44.345982] parport_pc: Current parallel port base: 0x378
[   44.346036] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   44.360827] Linux agpgart interface v0.102 (c) Dave Jones
[   44.363056] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   44.381874] agpgart: AGP aperture is 256M @ 0xc0000000
[   44.425935] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.428779] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.583396] parport_pc: VIA parallel port: io=0x378, irq=7
[   44.584371] input: PC Speaker as /class/input/input3
[   45.388975] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   45.388997] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   45.389006] PCI: VIA VLink IRQ fixup for 0000:00:07.5, from 10 to 11
[   45.389213] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   46.124817] fuse init (API version 7.8)
[   46.163912] lp0: using parport0 (interrupt-driven).
[   46.221736] Adding 996020k swap on /dev/disk/by-uuid/933f18bd-10d1-46f8-ba1b-216e4dd3bf38.  Priority:-1 extents:1 across:996020k
[   46.364958] EXT3 FS on sda2, internal journal
[   46.512248] NET: Registered protocol family 10
[   46.512420] lo: Disabled Privacy Extensions
[   46.738842] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   46.782151] NTFS volume version 3.0.
[   46.819689] NTFS volume version 3.0.
[   52.773535] powernow: No powernow capabilities detected
[   56.675987] eth0: no IPv6 routers present
[   57.856976] [drm] Initialized drm 1.1.0 20060810
[   57.872177] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[   57.877102] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   59.473114] ppdev: user-space parallel port driver
[   59.833686] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   59.833846] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   59.833988] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   60.179722] [drm] Setting GART location based on new memory map
[   60.179742] [drm] Loading R200 Microcode
[   60.179785] [drm] writeback test succeeded in 1 usecs
[   71.813122] eth0: no IPv6 routers present
```

Thanks,
Sirevert.

---

### Post by eyelessfade on 2007-04-22
Well it said me much, just not anything to help you. I know that it have been a lot of problems with the libata in the kernel, but that shouldn't have been a problem while you used edgy. But it seems that it might be your raid card. You might want to google after other people having the same problem with linux (not just ubuntu)

sorry I couldn't help you more

---

### Post by sirevert on 2007-04-24
I'm not able to make screen shots when this happens, but, I do have a digital photo camera :D
I hope this will clear things up.

It started with:
```
ATA1.00: failed to set xfermode (err_mask: 0x40)
```

then a load of other errors which i didn't capture in time and finally:
[http://img124.imageshack.us/img124/5784/hpim3296qq8.jpg]("http://img124.imageshack.us/img124/5784/hpim3296qq8.jpg")

---

### Post by Swab on 2007-04-24
Is the machine dual boot?  If so, do you have problems in the other OS?

---

### Post by sirevert on 2007-04-25
Yes it's dual boot and no I never had and still don't have any trouble on the old win2k.

---

### Post by tom56 on 2007-04-25
Is Windows on the same hard drive or a different one?

---

### Post by astralsin on 2007-04-25
i'm having the exact same problem.  sometimes the system will freeze hard and have to do a hard reboot which i dont like doing.  being the same problem, i dont think its the raid card's fault, as I don't implement raid.  here's my lspci

```
root@odin:/usr/src# lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)

```

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=0 UnitCnt=15 MastHost- DefDir- DUL-
		Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
		Link Control 1: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn+ LSEn+ ExtCTL- 64b-
		Link Config 1: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 1.03
		Link Frequency 0: 1.0GHz
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
		Link Frequency 1: 800MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [e0] HyperTransport: MSI Mapping

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR-

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [44] #00 [00fe]
	Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fd700000-fd7fffff
	Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <4us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 2
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
		Slot: Number 0, PowerLimit 0.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Off, PwrInd On, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <4us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 1
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
		Slot: Number 0, PowerLimit 0.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Off, PwrInd On, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fd900000-fd9fffff
	Prefetchable memory behind bridge: 00000000fd800000-00000000fd8fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <4us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s, Port 0
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x16
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
		Slot: Number 0, PowerLimit 0.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Off, PwrInd On, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-

00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2) (prog-if 00 [VGA])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 1401
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=9 UnitCnt=15 MastHost- DefDir- DUL-
		Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn+ LSEn+ ExtCTL- 64b-
		Link Config 0: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 1.03
		Link Frequency 0: 800MHz
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
		Link Frequency 1: 200MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3402
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3402
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 5
	Region 4: I/O ports at 1c00 [size=64]
	Region 5: I/O ports at 1c40 [size=64]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3402
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3402
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3402
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3402
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at f400 [size=16]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 5401
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at 09f0 [size=8]
	Region 1: I/O ports at 0bf0 [size=4]
	Region 2: I/O ports at 0970 [size=8]
	Region 3: I/O ports at 0b70 [size=4]
	Region 4: I/O ports at e000 [size=16]
	Region 5: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: fda00000-fdafffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [b8] Subsystem: Gammagraphx, Inc. Unknown device 0000
	Capabilities: [8c] HyperTransport: MSI Mapping

00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 8213
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin C routed to IRQ 16
	Region 0: I/O ports at dc00 [size=256]
	Region 1: I/O ports at d800 [size=256]
	Region 2: Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 2501
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at d400 [size=8]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=0 PME-

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: [80] HyperTransport: Host or Secondary Interface
		!!! Possibly incomplete decoding
		Command: WarmRst+ DblEnd-
		Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0
		Link Config: MLWI=16bit MLWO=16bit LWI=16bit LWO=16bit
		Revision ID: 1.02

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

04:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at cc00 [size=32]

```

Most of the time it happens overnight and I'll wake up to a frozen box.  I did notice however that when I first installed feisty, the screen saver was causing some of them.  i've since turned that off and the frequency of the freezes has subsided but they do still happen sometimes.

---

### Post by sirevert on 2007-04-25
> Is Windows on the same hard drive or a different one?
Win2k is on the same disk as Linux is.

> dont think its the raid card's fault, as I don't implement raid
Same here I'm not using its raid function.

---

### Post by tom56 on 2007-04-26
> **sirevert said:**
> Win2k is on the same disk as Linux is.

Well, that rules out hardware failure at least.

---

### Post by wj32 on 2007-04-26
Yes, something is wrong with your hardware. Looking at that screenshot, ext3 is screwing up because your SATA drives are getting buffer I/O errors.

---

### Post by tom56 on 2007-04-26
> **wj32 said:**
> Yes, something is wrong with your hardware. Looking at that screenshot, ext3 is screwing up because your SATA drives are getting buffer I/O errors.

No the hardware is fine because he says Windows (which is on the same drive) doesn't have any problems.

---

