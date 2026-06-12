---
title: "USB2 devices not found"
date: 2007-10-19
forum: General Help
---

### Post by UbuntuniX on 2007-10-19
At some point (during September, I think) Gutsy just suddenly stopped detecting USB2 devices.
My USB Wireless adaptor has been functioning fine throughout, though any camera or iPod I connect is not mounted. If I do mount it, I cannot seem to gain access to the device at all.

I don't really know much about how USB works or how it's handled.

If it helps, dmesg (iPod currently connected):
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.
3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT
 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5010
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
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F69D0 checksum 0
[    0.000000] ACPI: RSDP 000F69D0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FFF3000, 0034 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010
101)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010
101)
[    0.000000] ACPI: DSDT 3FFF30C0, 50CA (r1 NVIDIA AWRDACPI     1000 MSFT  1000
00C)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: SSDT 3FFF8240, 01C4 (r1 PTLTD  POWERNOW        1  LTP
  1)
[    0.000000] ACPI: MCFG 3FFF8440, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010
101)
[    0.000000] ACPI: APIC 3FFF81C0, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010
101)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b000
0000)
[    0.000000] Built 1 zonelists.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=01afcb1b-4f2a-4d5f-b08d-f010d00372
14 ro quiet splash noapic
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2009.198 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 1027752k/1048512k available (2015k kernel code, 20036k re
served, 916k data, 364k init, 131008k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor
mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, N
odes=1
[    0.084000] Calibrating delay using timer specific routine.. 4021.80 BogoMIPS
 (lpj=8043606)
[    0.084000] Security Framework v1.0.0 initialized
[    0.084000] SELinux:  Disabled at boot.
[    0.084000] Mount-cache hash table entries: 512
[    0.084000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 000
00000 00002001 00000000 0000001f
[    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.084000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.084000] CPU 0(2) -> Core 0
[    0.084000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 0
0002001 00000000 0000001f
[    0.084000] Compat vDSO mapped to ffffe000.
[    0.084000] Checking 'hlt' instruction... OK.
[    0.100000] SMP alternatives: switching to UP code
[    0.100000] Early unpacking initramfs... done
[    0.388000] ACPI: Core revision 20070126
[    0.388000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not
found.
[    0.392000] ACPI: setting ELCR to 0200 (from 8c20)
[    0.392000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.392000] SMP alternatives: switching to SMP code
[    0.392000] Booting processor 1/1 eip 3000
[    0.400000] Initializing CPU#1
[    0.484000] Calibrating delay using timer specific routine.. 4018.59 BogoMIPS
 (lpj=8037192)
[    0.484000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 000
00000 00002001 00000000 0000001f
[    0.484000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.484000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.484000] CPU 1(2) -> Core 1
[    0.484000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 0
0002001 00000000 0000001f
[    0.484000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.484000] Total of 2 processors activated (8040.39 BogoMIPS).
[    0.484000] Brought up 2 CPUs
[    0.500000] migration_cost=4000
[    0.500000] Booting paravirtualized kernel on bare hardware
[    0.500000] Time: 14:33:44  Date: 09/19/107
[    0.504000] NET: Registered protocol family 16
[    0.504000] EISA bus registered
[    0.504000] ACPI: bus type pci registered
[    0.508000] PCI: PCI BIOS revision 3.00 entry at 0xfb790, last bus=3
[    0.508000] PCI: Using configuration type 1
[    0.508000] Setting up standard PCI resources
[    0.512000] ACPI: EC: Look up EC in DSDT
[    0.520000] ACPI: Interpreter enabled
[    0.520000] ACPI: (supports S0 S1 S4 S5)
[    0.520000] ACPI: Using PIC for interrupt routing
[    0.528000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.528000] PCI: Probing PCI hardware (bus 00)
[    0.528000] PCI: Transparent bridge - 0000:00:0e.0
[    0.528000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.528000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.612000] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[    0.612000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[    0.612000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[    0.612000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.612000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.612000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.612000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 *10 11 14 15)
[    0.612000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 *15)
[    0.612000] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.612000] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 *15)
[    0.612000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[    0.612000] ACPI: PCI Interrupt Link [LMC1] (IRQs 5 7 9 10 *11 14 15)
[    0.612000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 *15)
[    0.612000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.612000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    0.612000] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.612000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.612000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.612000] ACPI: PCI Interrupt Link [LFID] (IRQs *5 7 9 10 11 14 15)
[    0.612000] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[    0.612000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.612000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.612000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [AMC1] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0, disabled.
[    0.616000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.616000] pnp: PnP ACPI init
[    0.616000] ACPI: bus type pnp registered
[    0.620000] pnp: PnP ACPI: found 14 devices
[    0.620000] ACPI: ACPI bus type pnp unregistered
[    0.620000] PnPBIOS: Disabled by ACPI PNP
[    0.620000] PCI: Using ACPI for IRQ routing
[    0.620000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps,
post a report
[    0.692000] NET: Registered protocol family 8
[    0.692000] NET: Registered protocol family 20
[    0.692000] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[    0.692000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.692000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.692000] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.692000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.692000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.692000] pnp: 00:0c: iomem range 0xf0000000-0xf7ffffff could not be reserv
ed
[    0.692000] pnp: 00:0d: iomem range 0xd6800-0xd7fff has been reserved
[    0.692000] pnp: 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.692000] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.692000] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.720000] PCI: Bridge: 0000:00:0e.0
[    0.720000]   IO window: 6000-6fff
[    0.720000]   MEM window: fb000000-fb0fffff
[    0.720000]   PREFETCH window: disabled.
[    0.720000] PCI: Bridge: 0000:00:12.0
[    0.720000]   IO window: 7000-7fff
[    0.720000]   MEM window: f8000000-faffffff
[    0.720000]   PREFETCH window: e0000000-efffffff
[    0.720000] PCI: Bridge: 0000:00:15.0
[    0.720000]   IO window: 8000-9fff
[    0.720000]   MEM window: fb100000-fb1fffff
[    0.720000]   PREFETCH window: disabled.
[    0.720000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.720000] PCI: Setting latency timer of device 0000:00:12.0 to 64
[    0.720000] PCI: Setting latency timer of device 0000:00:15.0 to 64
[    0.720000] NET: Registered protocol family 2
[    0.724000] Time: acpi_pm clocksource has been installed.
[    0.724000] Switched to high resolution mode on CPU 0
[    0.724000] Switched to high resolution mode on CPU 1
[    0.764000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.764000] TCP established hash table entries: 131072 (order: 8, 1572864 byt
es)
[    0.764000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.764000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.764000] TCP reno registered
[    0.780000] checking if image is initramfs... it is
[    1.348000] Freeing initrd memory: 7130k freed
[    1.348000] audit: initializing netlink socket (disabled)
[    1.348000] audit(1192804425.224:1): initialized
[    1.348000] highmem bounce pool size: 64 pages
[    1.352000] VFS: Disk quotas dquot_6.5.1
[    1.352000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.352000] io scheduler noop registered
[    1.352000] io scheduler anticipatory registered
[    1.352000] io scheduler deadline registered
[    1.352000] io scheduler cfq registered (default)
[    1.380000] Boot video device is 0000:02:00.0
[    1.380000] PCI: Setting latency timer of device 0000:00:12.0 to 64
[    1.380000] assign_interrupt_mode Found MSI capability
[    1.380000] Allocate Port Service[0000:00:12.0:pcie00]
[    1.380000] PCI: Setting latency timer of device 0000:00:15.0 to 64
[    1.380000] assign_interrupt_mode Found MSI capability
[    1.380000] Allocate Port Service[0000:00:15.0:pcie00]
[    1.380000] isapnp: Scanning for PnP cards...
[    1.732000] isapnp: No Plug & Play device found
[    1.752000] Real Time Clock Driver v1.12ac
[    1.752000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing
enabled
[    1.752000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.752000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.752000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[    1.752000] input: Macintosh mouse button emulation as /class/input/input0
[    1.752000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq
 1,12
[    1.752000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.752000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.752000] mice: PS/2 mouse device common for all mice
[    1.752000] EISA: Probing bus 0 at eisa.0
[    1.752000] Cannot allocate resource for EISA slot 1
[    1.752000] Cannot allocate resource for EISA slot 6
[    1.752000] Cannot allocate resource for EISA slot 7
[    1.752000] Cannot allocate resource for EISA slot 8
[    1.752000] EISA: Detected 0 cards.
[    1.752000] TCP cubic registered
[    1.752000] NET: Registered protocol family 1
[    1.752000] Using IPI No-Shortcut mode
[    1.752000]   Magic number: 11:964:586
[    1.752000]   hash matches device ptyc4
[    1.756000] Freeing unused kernel memory: 364k freed
[    1.780000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.968000] AppArmor: AppArmor initialized<5>audit(1192804426.724:2):  type=1
505 info="AppArmor initialized" pid=1272
[    2.976000] fuse init (API version 7.8)
[    2.984000] Failure registering capabilities with primary security module.
[    3.584000] SCSI subsystem initialized
[    3.604000] libata version 2.21 loaded.
[    3.604000] sata_nv 0000:00:0d.0: version 3.4
[    3.608000] ACPI: PCI Interrupt Link [LSID] enabled at IRQ 11
[    3.608000] PCI: setting IRQ 11 as level-triggered
[    3.608000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LSID] -> GSI 11 (lev
el, low) -> IRQ 11
[    3.608000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    3.608000] scsi0 : sata_nv
[    3.608000] scsi1 : sata_nv
[    3.608000] ata1: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001a002 bmdma 0x000
1ac00 irq 11
[    3.608000] ata2: SATA max UDMA/133 cmd 0x0001a400 ctl 0x0001a802 bmdma 0x000
1ac08 irq 11
[    3.612000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.612000] ide: Assuming 33MHz system bus speed for PIO modes; override with
 idebus=xx
[    3.636000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0
.60.
[    3.728000] usbcore: registered new interface driver usbfs
[    3.728000] usbcore: registered new interface driver hub
[    3.728000] usbcore: registered new device driver usb
[    3.728000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Dr
iver
[    3.756000] Floppy drive(s): fd0 is 1.44M
[    3.772000] FDC 0 is a post-1991 82077
[    3.920000] ata1: SATA link down (SStatus 0 SControl 300)
[    4.240000] ata2: SATA link down (SStatus 0 SControl 300)
[    4.248000] ACPI: PCI Interrupt Link [LFID] enabled at IRQ 5
[    4.248000] PCI: setting IRQ 5 as level-triggered
[    4.248000] ACPI: PCI Interrupt 0000:00:0d.1[B] -> Link [LFID] -> GSI 5 (leve
l, low) -> IRQ 5
[    4.248000] PCI: Setting latency timer of device 0000:00:0d.1 to 64
[    4.248000] scsi2 : sata_nv
[    4.248000] scsi3 : sata_nv
[    4.248000] ata3: SATA max UDMA/133 cmd 0x0001b000 ctl 0x0001b402 bmdma 0x000
1c000 irq 5
[    4.248000] ata4: SATA max UDMA/133 cmd 0x0001b800 ctl 0x0001bc02 bmdma 0x000
1c008 irq 5
[    4.560000] ata3: SATA link down (SStatus 0 SControl 300)
[    4.880000] ata4: SATA link down (SStatus 0 SControl 300)
[    4.888000] ACPI: PCI Interrupt Link [LSA2] enabled at IRQ 10
[    4.888000] PCI: setting IRQ 10 as level-triggered
[    4.888000] ACPI: PCI Interrupt 0000:00:0d.2[C] -> Link [LSA2] -> GSI 10 (lev
el, low) -> IRQ 10
[    4.888000] PCI: Setting latency timer of device 0000:00:0d.2 to 64
[    4.888000] scsi4 : sata_nv
[    4.888000] scsi5 : sata_nv
[    4.888000] ata5: SATA max UDMA/133 cmd 0x0001c400 ctl 0x0001c802 bmdma 0x000
1d400 irq 10
[    4.888000] ata6: SATA max UDMA/133 cmd 0x0001cc00 ctl 0x0001d002 bmdma 0x000
1d408 irq 10
[    5.200000] ata5: SATA link down (SStatus 0 SControl 300)
[    5.520000] ata6: SATA link down (SStatus 0 SControl 300)
[    5.528000] NFORCE-MCP55: IDE controller at PCI slot 0000:00:0c.0
[    5.528000] NFORCE-MCP55: chipset revision 161
[    5.528000] NFORCE-MCP55: not 100% native mode: will probe irqs later
[    5.528000] NFORCE-MCP55: BIOS didn't set cable bits correctly. Enabling work
around.
[    5.528000] NFORCE-MCP55: 0000:00:0c.0 (rev a1) UDMA133 controller
[    5.528000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DM
A
[    5.528000] Probing IDE interface ide0...
[    5.816000] hda: HDT722525DLAT80, ATA DISK drive
[    6.264000] hdb: LITE-ON COMBO SOHC-5235K, ATAPI CD/DVD-ROM drive
[    6.320000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    6.332000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 15
[    6.332000] PCI: setting IRQ 15 as level-triggered
[    6.332000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LMAC] -> GSI 15 (lev
el, low) -> IRQ 15
[    6.332000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    6.332000] forcedeth: using HIGHDMA
[    6.340000] hda: max request size: 512KiB
[    6.340000] hda: Host Protected Area detected.
[    6.340000]  current capacity is 488395055 sectors (250058 MB)
[    6.340000]  native  capacity is 488397168 sectors (250059 MB)
[    6.340000] hda: Host Protected Area disabled.
[    6.340000] hda: 488397168 sectors (250059 MB) w/7674KiB Cache, CHS=30401/255
/63, UDMA(133)
[    6.340000] hda: cache flushes supported
[    6.340000]  hda: hda1 hda2 hda3
[    6.372000] hdb: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.372000] Uniform CD-ROM driver Revision: 3.20
[    6.628000] kjournald starting.  Commit interval 5 seconds
[    6.628000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.856000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:10.0
[    6.856000] ACPI: PCI Interrupt Link [LMC1] enabled at IRQ 11
[    6.856000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LMC1] -> GSI 11 (lev
el, low) -> IRQ 11
[    6.856000] PCI: Setting latency timer of device 0000:00:11.0 to 64
[    6.856000] forcedeth: using HIGHDMA
[    7.380000] eth1: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:11.0
[    7.380000] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[    7.380000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 10
[    7.380000] ACPI: PCI Interrupt 0000:03:00.1[B] -> Link [LNK5] -> GSI 10 (lev
el, low) -> IRQ 10
[    7.380000] PCI: Setting latency timer of device 0000:03:00.1 to 64
[    7.380000] scsi6 : pata_jmicron
[    7.380000] scsi7 : pata_jmicron
[    7.380000] ata7: PATA max UDMA/100 cmd 0x00018000 ctl 0x00018402 bmdma 0x000
19000 irq 10
[    7.380000] ata8: PATA max UDMA/100 cmd 0x00018800 ctl 0x00018c02 bmdma 0x000
19008 irq 10
[    7.700000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 10
[    7.700000] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [LNK3] -> GSI 10 (lev
el, low) -> IRQ 10
[    7.700000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 5
[    7.700000] ACPI: PCI Interrupt 0000:00:0a.1[B] -> Link [LUB2] -> GSI 5 (leve
l, low) -> IRQ 5
[    7.700000] PCI: Setting latency timer of device 0000:00:0a.1 to 64
[    7.700000] ehci_hcd 0000:00:0a.1: EHCI Host Controller
[    7.700000] ehci_hcd 0000:00:0a.1: new USB bus registered, assigned bus numbe
r 1
[    7.704000] ehci_hcd 0000:00:0a.1: debug port 1
[    7.704000] PCI: cache line size of 64 is not supported by device 0000:00:0a.
1
[    7.704000] ehci_hcd 0000:00:0a.1: irq 5, io mem 0xfb205000
[    7.704000] ehci_hcd 0000:00:0a.1: USB 2.0 started, EHCI 1.00, driver 10 Dec
2004
[    7.704000] usb usb1: configuration #1 chosen from 1 choice
[    7.704000] hub 1-0:1.0: USB hub found
[    7.704000] hub 1-0:1.0: 10 ports detected
[    7.752000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[fb004000
-fb0047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.808000] ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 15
[    7.808000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LUBA] -> GSI 15 (lev
el, low) -> IRQ 15
[    7.808000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    7.808000] ohci_hcd 0000:00:0a.0: OHCI Host Controller
[    7.808000] ohci_hcd 0000:00:0a.0: new USB bus registered, assigned bus numbe
r 2
[    7.808000] ohci_hcd 0000:00:0a.0: irq 15, io mem 0xfb204000
[    7.864000] usb usb2: configuration #1 chosen from 1 choice
[    7.864000] hub 2-0:1.0: USB hub found
[    7.864000] hub 2-0:1.0: 10 ports detected
[    7.968000] ahci 0000:03:00.0: version 2.2
[    7.968000] ACPI: PCI Interrupt Link [LNK8] enabled at IRQ 15
[    7.968000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNK8] -> GSI 15 (lev
el, low) -> IRQ 15
[    8.048000] usb 1-9: new high speed USB device using ehci_hcd and address 2
[    8.180000] usb 1-9: configuration #1 chosen from 2 choices
[    8.420000] usb 1-10: new high speed USB device using ehci_hcd and address 3
[    8.552000] usb 1-10: configuration #1 chosen from 1 choice
[    8.972000] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 imp
l SATA mode
[    8.972000] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part
[    8.972000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    8.972000] scsi8 : ahci
[    8.972000] scsi9 : ahci
[    8.972000] ata9: SATA max UDMA/133 cmd 0xf88dc100 ctl 0x00000000 bmdma 0x000
00000 irq 15
[    8.972000] ata10: SATA max UDMA/133 cmd 0xf88dc180 ctl 0x00000000 bmdma 0x00
000000 irq 15
[    9.024000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0016e60000b79732]
[    9.284000] ata9: SATA link down (SStatus 0 SControl 300)
[    9.596000] ata10: SATA link down (SStatus 0 SControl 300)
[   15.176000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   15.176000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   15.244000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.244000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.736000] input: PC Speaker as /class/input/input2
[   15.800000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.836000] ieee80211_crypt: registered algorithm 'NULL'
[   15.840000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   15.840000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@li
nux.intel.com>
[   15.912000] usbcore: registered new interface driver libusual
[   15.920000] Initializing USB Mass Storage driver...
[   15.920000] scsi10 : SCSI emulation for USB Mass Storage devices
[   15.920000] usb-storage: device found at 2
[   15.920000] usb-storage: waiting for device to settle before scanning
[   15.920000] usbcore: registered new interface driver usb-storage
[   15.920000] USB Mass Storage support registered.
[   16.056000] input: PS2++ Logitech MX Mouse as /class/input/input3
[   16.060000] parport_pc 00:09: reported by Plug and Play ACPI
[   16.060000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.116000] nvidia: module license 'NVIDIA' taints kernel.
[   16.368000] usb 1-10: reset high speed USB device using ehci_hcd and address
3
[   16.368000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 10
[   16.368000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK7] -> GSI 10 (lev
el, low) -> IRQ 10
[   16.368000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   16.368000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 1
6 20:20:06 PDT 2007
[   16.600000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   16.600000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNK1] -> GSI 5 (leve
l, low) -> IRQ 5
[   16.600000] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   16.624000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 15
[   16.624000] ACPI: PCI Interrupt 0000:00:0e.1[B] -> Link [LAZA] -> GSI 15 (lev
el, low) -> IRQ 15
[   16.624000] PCI: Setting latency timer of device 0000:00:0e.1 to 64
[   16.648000] zd1211rw 1-10:1.0: firmware version 4725
[   16.688000] zd1211rw 1-10:1.0: zd1211b chip 0ace:1215 v4810 high 00-02-72 AL2
230_RF pa0 g--NS
[   16.692000] zd1211rw 1-10:1.0: eth2
[   16.692000] usbcore: registered new interface driver zd1211rw
[   17.668000] lp0: using parport0 (interrupt-driven).
[   18.024000] EXT3 FS on hda2, internal journal
[   19.380000] input: Power Button (FF) as /class/input/input4
[   19.380000] ACPI: Power Button (FF) [PWRF]
[   19.380000] input: Power Button (CM) as /class/input/input5
[   19.380000] ACPI: Power Button (CM) [PWRB]
[   19.432000] No dock devices found.
[   19.724000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 380
0+ processors (version 2.00.00)
[   19.724000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xa
[   19.724000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xc
[   19.724000] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   20.920000] usb-storage: device scan complete
[   20.924000] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 P
Q: 0 ANSI: 0
[   20.972000] sd 10:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[   20.980000] sd 10:0:0:0: [sda] Write Protect is off
[   20.980000] sd 10:0:0:0: [sda] Mode Sense: 68 00 00 08
[   20.980000] sd 10:0:0:0: [sda] Assuming drive cache: write through
[   20.988000] sd 10:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[   20.988000] sd 10:0:0:0: [sda] Write Protect is off
[   20.988000] sd 10:0:0:0: [sda] Mode Sense: 68 00 00 08
[   20.988000] sd 10:0:0:0: [sda] Assuming drive cache: write through
[   20.988000]  sda: sda1 sda2
[   20.992000] sd 10:0:0:0: [sda] Attached SCSI removable disk
[   21.008000] sd 10:0:0:0: Attached scsi generic sg0 type 0
[   21.016000] eth0: no link during initialization.
[   21.056000] eth1: no link during initialization.
[   21.244000] ppdev: user-space parallel port driver
[   21.520000] audit(1192800845.669:3):  type=1503 operation="inode_permission"                                                                                                    requested_mask="a" denied_mask="a" name="/dev/tty" pid=5220 profile="/usr/sbin/c                                                                                                   upsd"
[   23.636000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   23.636000] apm: disabled - APM is not SMP safe.
[   25.352000] Failure registering capabilities with primary security module.
[   25.552000] Bluetooth: Core ver 2.11
[   25.552000] NET: Registered protocol family 31
[   25.552000] Bluetooth: HCI device and connection manager initialized
[   25.552000] Bluetooth: HCI socket layer initialized
[   25.572000] Bluetooth: L2CAP ver 2.8
[   25.572000] Bluetooth: L2CAP socket layer initialized
[   25.632000] Bluetooth: RFCOMM socket layer initialized
[   25.632000] Bluetooth: RFCOMM TTY layer initialized
[   25.632000] Bluetooth: RFCOMM ver 1.8
[   25.720000] Clocksource tsc unstable (delta = -132024964 ns)
[  423.664000] NET: Registered protocol family 17
[  424.172000] SoftMAC: Open Authentication completed with 00:0f:cc:25:f4:78
[  424.228000] ieee80211_crypt: registered algorithm 'TKIP'
```

---

### Post by UbuntuniX on 2007-10-20
Bumpity bump.

---

### Post by UbuntuniX on 2007-10-21
> **UbuntuniX said:**
> Bumpity bump.

:(

---

### Post by UbuntuniX on 2007-10-23
> **UbuntuniX said:**
> :(

:(

---

### Post by maxx22 on 2007-10-27
Apparently the usb 2.0 driver is not so reliable in gutsy.  I've run into a similar issue.  I've found that unhooking the device, sudo rmmod ehci-hcd, sudo modprobe ehci-hcd, plug device in gets it going again.  If that doesn't work try plugging in after removing the ehci-hcd module.  That at least should work although it'd be dog slow using the usb 1.0 driver.

---

### Post by CarlAdam on 2007-10-28
Yeah, both my usb-stick and my cell-phone doesn't connect to my pc (via usb) after installing gutsy, Had no problem what so ever with feisty. Is there a bug-report on this? Anyone know if it is being worked on?

---

