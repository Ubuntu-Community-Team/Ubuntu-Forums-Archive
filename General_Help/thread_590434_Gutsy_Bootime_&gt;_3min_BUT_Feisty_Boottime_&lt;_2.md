---
title: "Gutsy Bootime &gt; 3min BUT Feisty Boottime &lt; 2"
date: 2007-10-24
forum: General Help
---

### Post by jrattner on 2007-10-24
Does anyone have any clues why my system takes OVER 3 minutes to boot in Gibbon, when previously in Feisty it took what seemed like less then a minute.

None of my hardware has changed.


Here is the output of dmesg.
> 
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef9000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef9000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7a70
[    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524016
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524016
[    0.000000] On node 0 totalpages: 524016
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F79C0 checksum 0
[    0.000000] ACPI: RSDP 000F79C0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 7FEF1A74, 0034 (r1 HP     3082      6040000  LTP        0)
[    0.000000] ACPI: FACP 7FEF8EC0, 0074 (r1 HP     3082      6040000 PTL         3)
[    0.000000] ACPI: DSDT 7FEF1AA8, 7418 (r1 HP     3082      6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FEF9FC0, 0040
[    0.000000] ACPI: MCFG 7FEF8F34, 003C (r1 HP     3082      6040000  LTP        0)
[    0.000000] ACPI: APIC 7FEF8F70, 0068 (r1 HP     3082      6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FEF8FD8, 0028 (r1     HP 3082      6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Built 1 zonelists.  Total pages: 519923
[    0.000000] Kernel command line: root=UUID=c1d16e7a-7cf7-4d7c-b40a-cdef9c425839 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3192.230 MHz processor.
[   19.993316] Console: colour VGA+ 80x25
[   19.993585] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   19.993910] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.096878] Memory: 2066592k/2096064k available (2015k kernel code, 28192k reserved, 916k data, 364k init, 1178560k highmem)
[   20.096889] virtual kernel memory layout:
[   20.096890]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   20.096891]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.096892]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   20.096893]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   20.096895]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   20.096896]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   20.096897]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   20.096900] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.096940] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.176768] Calibrating delay using timer specific routine.. 6456.75 BogoMIPS (lpj=12913504)
[   20.176796] Security Framework v1.0.0 initialized
[   20.176801] SELinux:  Disabled at boot.
[   20.176814] Mount-cache hash table entries: 512
[   20.176946] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[   20.176955] monitor/mwait feature present.
[   20.176958] using mwait in idle threads.
[   20.176965] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   20.176968] CPU: L2 cache: 2048K
[   20.176971] CPU: Physical Processor ID: 0
[   20.176973] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000
[   20.176984] Compat vDSO mapped to ffffe000.
[   20.177001] Checking 'hlt' instruction... OK.
[   20.192825] SMP alternatives: switching to UP code
[   20.193272] Early unpacking initramfs... done
[   20.495992] ACPI: Core revision 20070126
[   20.496063] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.517802] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[   20.517822] SMP alternatives: switching to SMP code
[   20.517917] Booting processor 1/1 eip 3000
[   20.528299] Initializing CPU#1
[   20.607711] Calibrating delay using timer specific routine.. 6384.53 BogoMIPS (lpj=12769065)
[   20.607722] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[   20.607729] monitor/mwait feature present.
[   20.607737] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   20.607740] CPU: L2 cache: 2048K
[   20.607743] CPU: Physical Processor ID: 0
[   20.607745] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000
[   20.608301] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[   20.608344] Total of 2 processors activated (12841.28 BogoMIPS).
[   20.608493] ENABLING IO-APIC IRQs
[   20.608678] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.755468] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   20.775436] Brought up 2 CPUs
[   20.933160] migration_cost=107
[   20.933337] Booting paravirtualized kernel on bare hardware
[   20.933406] Time: 20:17:28  Date: 09/24/107
[   20.933431] NET: Registered protocol family 16
[   20.933531] EISA bus registered
[   20.933537] ACPI: bus type pci registered
[   20.975041] PCI: PCI BIOS revision 2.10 entry at 0xfd95e, last bus=11
[   20.975043] PCI: Using configuration type 1
[   20.975046] Setting up standard PCI resources
[   20.985183] ACPI: EC: Look up EC in DSDT
[   20.985888] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   21.005536] ACPI: Interpreter enabled
[   21.005540] ACPI: (supports S0 S3 S4 S5)
[   21.005558] ACPI: Using IOAPIC for interrupt routing
[   21.010986] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   21.011044] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.011059] PCI: Probing PCI hardware (bus 00)
[   21.011663] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   21.011668] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   21.012411] PCI: Transparent bridge - 0000:00:1e.0
[   21.012524] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.012836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
[   21.012966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   21.013094] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   21.019731] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *10 11 14 15)
[   21.019827] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 10 11 14 15) *5
[   21.019920] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 10 *11 14 15)
[   21.020010] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 10 11 14 15) *7
[   21.020106] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 10 11 14 15) *7
[   21.020202] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 10 11 14 15) *0, disabled.
[   21.020298] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 10 *11 14 15)
[   21.020394] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 10 11 14 15) *7
[   21.020515] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.020530] pnp: PnP ACPI init
[   21.020540] ACPI: bus type pnp registered
[   21.022531] pnp: PnP ACPI: found 9 devices
[   21.022534] ACPI: ACPI bus type pnp unregistered
[   21.022538] PnPBIOS: Disabled by ACPI PNP
[   21.022595] PCI: Using ACPI for IRQ routing
[   21.022599] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.022604] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   21.022644] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   21.022681] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   21.043434] NET: Registered protocol family 8
[   21.043436] NET: Registered protocol family 20
[   21.043503] pnp: 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[   21.043511] pnp: 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[   21.043514] pnp: 00:02: iomem range 0xfed13000-0xfed13fff has been reserved
[   21.043517] pnp: 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[   21.043520] pnp: 00:02: iomem range 0xfed20000-0xfed8ffff has been reserved
[   21.046667] Time: tsc clocksource has been installed.
[   21.073858] PCI: Bridge: 0000:00:01.0
[   21.073862]   IO window: 4000-4fff
[   21.073867]   MEM window: b0100000-b01fffff
[   21.073871]   PREFETCH window: c0000000-cfffffff
[   21.073875] PCI: Bridge: 0000:00:1c.0
[   21.073877]   IO window: disabled.
[   21.073882]   MEM window: disabled.
[   21.073886]   PREFETCH window: disabled.
[   21.073898] PCI: Bus 12, cardbus bridge: 0000:0b:00.0
[   21.073901]   IO window: 00005400-000054ff
[   21.073905]   IO window: 00005800-000058ff
[   21.073911]   PREFETCH window: 88000000-8bffffff
[   21.073916]   MEM window: 8c000000-8fffffff
[   21.073920] PCI: Bridge: 0000:00:1e.0
[   21.073923]   IO window: 5000-5fff
[   21.073929]   MEM window: b0200000-b02fffff
[   21.073933]   PREFETCH window: 88000000-8bffffff
[   21.073951] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.073958] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.073978] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   21.073986] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.073998] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.074012] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.074027] NET: Registered protocol family 2
[   21.114630] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.114692] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   21.115593] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.115854] TCP: Hash tables configured (established 131072 bind 65536)
[   21.115857] TCP reno registered
[   21.126741] checking if image is initramfs... it is
[   21.573391] Switched to high resolution mode on CPU 0
[   21.573482] Switched to high resolution mode on CPU 1
[   21.722939] Freeing initrd memory: 7069k freed
[   21.723031] Simple Boot Flag at 0x36 set to 0x1
[   21.723531] audit: initializing netlink socket (disabled)
[   21.723544] audit(1193257048.304:1): initialized
[   21.723653] highmem bounce pool size: 64 pages
[   21.726148] VFS: Disk quotas dquot_6.5.1
[   21.726213] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.726318] io scheduler noop registered
[   21.726321] io scheduler anticipatory registered
[   21.726323] io scheduler deadline registered
[   21.726340] io scheduler cfq registered (default)
[   21.726436] Boot video device is 0000:01:00.0
[   21.726530] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.726574] assign_interrupt_mode Found MSI capability
[   21.726578] Allocate Port Service[0000:00:01.0:pcie00]
[   21.726671] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.726716] assign_interrupt_mode Found MSI capability
[   21.726719] Allocate Port Service[0000:00:1c.0:pcie00]
[   21.726760] Allocate Port Service[0000:00:1c.0:pcie02]
[   21.726941] isapnp: Scanning for PnP cards...
[   22.077767] isapnp: No Plug & Play device found
[   22.106577] Real Time Clock Driver v1.12ac
[   22.106682] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.107317] ACPI: PCI Interrupt 0000:00:1e.3[A] -> GSI 22 (level, low) -> IRQ 18
[   22.107325] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   22.108043] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.108262] input: Macintosh mouse button emulation as /class/input/input0
[   22.108358] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   22.110034] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.110042] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.110221] mice: PS/2 mouse device common for all mice
[   22.110359] EISA: Probing bus 0 at eisa.0
[   22.110367] Cannot allocate resource for EISA slot 1
[   22.110373] Cannot allocate resource for EISA slot 3
[   22.110375] Cannot allocate resource for EISA slot 4
[   22.110378] Cannot allocate resource for EISA slot 5
[   22.110390] EISA: Detected 0 cards.
[   22.110474] TCP cubic registered
[   22.110486] NET: Registered protocol family 1
[   22.110508] Using IPI No-Shortcut mode
[   22.110668]   Magic number: 11:669:296
[   22.110697]   hash matches device ttywd
[   22.110803]   hash matches device tty29
[   22.111002] Freeing unused kernel memory: 364k freed
[   22.140011] input: AT Translated Set 2 keyboard as /class/input/input1
[   23.725926] AppArmor: AppArmor initialized<5>audit(1193257050.304:2):  type=1505 info="AppArmor initialized" pid=1203
[   24.322523] fuse init (API version 7.8)
[   24.628667] Failure registering capabilities with primary security module.
[   25.232289] ACPI: Processor [CPU0] (supports 8 throttling states)
[   25.232314] ACPI: Processor [CPU1] (supports 8 throttling states)
[   25.319448] ACPI: Thermal Zone [THRM] (47 C)
[   28.651220] usbcore: registered new interface driver usbfs
[   28.651257] usbcore: registered new interface driver hub
[   28.651511] SCSI subsystem initialized
[   28.661591] libata version 2.21 loaded.
[   28.663895] ata_piix 0000:00:1f.1: version 2.11
[   28.663918] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   28.663956] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.664030] scsi0 : ata_piix
[   28.664087] scsi1 : ata_piix
[   28.664127] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00013c40 irq 14
[   28.664132] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00013c48 irq 15
[   28.680897] usbcore: registered new device driver usb
[   28.759009] USB Universal Host Controller Interface driver v3.0
[   28.918465] 8139too Fast Ethernet driver 0.9.28
[   29.051108] ata1.00: ATA-6: ST9808211A, 3.02, max UDMA/100
[   29.051116] ata1.00: 156301488 sectors, multi 16: LBA48 
[   29.051127] ata1.01: ATAPI: HL-DT-ST DVD-RW GCA-4080N, 0C35, max MWDMA2
[   29.067056] ata1.00: configured for UDMA/100
[   29.238629] ata1.01: configured for MWDMA2
[   29.238673] ata2: port disabled. ignoring.
[   29.238870] scsi 0:0:0:0: Direct-Access     ATA      ST9808211A       3.02 PQ: 0 ANSI: 5
[   29.242626] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RW GCA-4080N 0C35 PQ: 0 ANSI: 5
[   29.243021] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   29.243037] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   29.243043] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   29.243202] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   29.243237] ehci_hcd 0000:00:1d.7: debug port 1
[   29.243245] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   29.243258] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xb0000000
[   29.247143] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.247253] usb usb1: configuration #1 chosen from 1 choice
[   29.247283] hub 1-0:1.0: USB hub found
[   29.247291] hub 1-0:1.0: 8 ports detected
[   29.350056] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   29.350070] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.350075] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.350113] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   29.350139] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[   29.350271] usb usb2: configuration #1 chosen from 1 choice
[   29.350310] hub 2-0:1.0: USB hub found
[   29.350320] hub 2-0:1.0: 2 ports detected
[   29.453830] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   29.453841] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.453846] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.453875] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   29.453904] uhci_hcd 0000:00:1d.1: irq 21, io base 0x000038c0
[   29.454031] usb usb3: configuration #1 chosen from 1 choice
[   29.454068] hub 3-0:1.0: USB hub found
[   29.454076] hub 3-0:1.0: 2 ports detected
[   29.557573] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   29.557585] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.557590] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.557619] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   29.557648] uhci_hcd 0000:00:1d.2: irq 19, io base 0x000038e0
[   29.557771] usb usb4: configuration #1 chosen from 1 choice
[   29.557811] hub 4-0:1.0: USB hub found
[   29.557819] hub 4-0:1.0: 2 ports detected
[   29.661304] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   29.661316] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   29.661321] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   29.661352] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   29.661382] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003c00
[   29.661510] usb usb5: configuration #1 chosen from 1 choice
[   29.661548] hub 5-0:1.0: USB hub found
[   29.661556] hub 5-0:1.0: 2 ports detected
[   29.765195] ACPI: PCI Interrupt 0000:0b:00.2[C] -> GSI 22 (level, low) -> IRQ 18
[   29.815516] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[b0208000-b02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   29.815856] ACPI: PCI Interrupt 0000:0b:02.0[A] -> GSI 20 (level, low) -> IRQ 22
[   29.816272] eth0: RealTek RTL8139 at 0xf881e400, 00:c0:9f:a9:1b:7f, IRQ 22
[   29.816276] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   29.818435] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   29.875995] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   29.877251] sd 0:0:0:0: [sda] Write Protect is off
[   29.877257] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.877305] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.877387] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   29.877404] sd 0:0:0:0: [sda] Write Protect is off
[   29.877408] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.877436] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.877443]  sda: sda1 sda2 sda3 sda4
[   29.923283] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.932210] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.932239] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   29.965229] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   29.965237] Uniform CD-ROM driver Revision: 3.20
[   29.965318] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   30.052226] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   30.221137] usb 2-1: configuration #1 chosen from 1 choice
[   30.463203] usb 5-2: new low speed USB device using uhci_hcd and address 2
[   30.609498] Attempting manual resume
[   30.609505] swsusp: Resume From Partition 8:3
[   30.609510] PM: Checking swsusp image.
[   30.609765] PM: Resume from disk failed.
[   30.639136] usb 5-2: configuration #1 chosen from 1 choice
[   30.653614] usbcore: registered new interface driver hiddev
[   30.666143] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   30.666173] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.3-2
[   30.666190] usbcore: registered new interface driver usbhid
[   30.666195] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.694954] EXT3-fs: INFO: recovery required on readonly filesystem.
[   30.694962] EXT3-fs: write access will be enabled during recovery.
[   31.081841] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800285600097f8a]
[   33.072669] kjournald starting.  Commit interval 5 seconds
[   33.072693] EXT3-fs: recovery complete.
[   33.096626] EXT3-fs: mounted filesystem with ordered data mode.
[   50.571976] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.758084] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.868192] Yenta: CardBus bridge found at 0000:0b:00.0 [103c:3082]
[   50.868213] Yenta: Enabling burst memory read transactions
[   50.868219] Yenta: Using CSCINT to route CSC interrupts to PCI
[   50.868223] Yenta: Routing CardBus interrupts to PCI
[   50.868230] Yenta TI: socket 0000:0b:00.0, mfunc 0x01a01b22, devctl 0x64
[   50.892740] Linux agpgart interface v0.102 (c) Dave Jones
[   50.931528] intel_rng: FWH not detected
[   50.937283] ieee80211_crypt: registered algorithm 'NULL'
[   50.949626] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   50.949632] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   51.096572] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   51.096578] Socket status: 30000006
[   51.096584] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   51.096589] cs: IO port probe 0x5000-0x5fff: clean.
[   51.096947] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[   51.096952] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   51.594666] sdhci: Secure Digital Host Controller Interface driver
[   51.594671] sdhci: Copyright(c) Pierre Ossman
[   51.605787] sdhci: SDHCI controller found at 0000:0b:00.4 [104c:8034] (rev 0)
[   51.605806] PCI: Enabling device 0000:0b:00.4 (0000 -> 0002)
[   51.605814] ACPI: PCI Interrupt 0000:0b:00.4[A] -> GSI 16 (level, low) -> IRQ 16
[   51.605889] mmc0: SDHCI at 0xb0209000 irq 16 DMA
[   51.609961] mmc1: SDHCI at 0xb0208c00 irq 16 DMA
[   51.610010] mmc2: SDHCI at 0xb0208800 irq 16 DMA
[   51.712147] input: PC Speaker as /class/input/input3
[   51.763090] iTCO_vendor_support: vendor-support=0
[   51.957719] Bluetooth: Core ver 2.11
[   51.957809] NET: Registered protocol family 31
[   51.957814] Bluetooth: HCI device and connection manager initialized
[   51.957821] Bluetooth: HCI socket layer initialized
[   51.991058] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   51.991144] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x1060)
[   51.991186] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   52.036611] PCI: Enabling device 0000:0b:00.3 (0000 -> 0002)
[   52.036621] ACPI: PCI Interrupt 0000:0b:00.3[A] -> GSI 16 (level, low) -> IRQ 16
[   52.043982] Bluetooth: HCI USB driver ver 2.9
[   52.045674] usbcore: registered new interface driver hci_usb
[   52.066423] bcm43xx driver
[   52.066521] PCI: Enabling device 0000:0b:03.0 (0000 -> 0002)
[   52.066530] ACPI: PCI Interrupt 0000:0b:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[   52.441324] cs: IO port probe 0x100-0x3af: clean.
[   52.442682] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   52.443265] cs: IO port probe 0x820-0x8ff: clean.
[   52.443735] cs: IO port probe 0xc00-0xcf7: clean.
[   52.444359] cs: IO port probe 0xa00-0xaff: clean.
[   52.572947] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 22 (level, low) -> IRQ 18
[   52.572970] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   52.671332] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x80b1, caps: 0xa04713/0x20040a
[   52.704672] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   52.891335] intel8x0_measure_ac97_clock: measured 53571 usecs
[   52.891344] intel8x0: clocking to 48000
[   55.503438] lp: driver loaded but no devices found
[   56.736254] Adding 1871564k swap on /dev/sda3.  Priority:-1 extents:1 across:1871564k
[   58.565823] EXT3 FS on sda2, internal journal
[   64.047895] kjournald starting.  Commit interval 5 seconds
[   64.048095] EXT3 FS on sda4, internal journal
[   64.048105] EXT3-fs: mounted filesystem with ordered data mode.
[   76.605618] ACPI: AC Adapter [ACAD] (on-line)
[   77.016704] No dock devices found.
[   77.121226] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   77.135693] input: Power Button (FF) as /class/input/input5
[   77.135721] ACPI: Power Button (FF) [PWRF]
[   77.135825] input: Lid Switch as /class/input/input6
[   77.135844] ACPI: Lid Switch [LID0]
[   77.135906] input: Power Button (CM) as /class/input/input7
[   77.135933] ACPI: Power Button (CM) [PWRB]
[   77.135991] input: Sleep Button (CM) as /class/input/input8
[   77.136013] ACPI: Sleep Button (CM) [SLPB]
[   77.643724] ACPI: Battery Slot [BAT1] (battery present)
[   86.823124] eth0: link down
[   87.865659] ppdev: user-space parallel port driver
[   88.074676] audit(1193271515.663:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4880 profile="/usr/sbin/cupsd"
[   88.118117] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   88.118123] apm: disabled - APM is not SMP safe.
[   93.301391] Failure registering capabilities with primary security module.
[   94.739027] Bluetooth: L2CAP ver 2.8
[   94.739033] Bluetooth: L2CAP socket layer initialized
[   94.864671] Bluetooth: RFCOMM socket layer initialized
[   94.864753] Bluetooth: RFCOMM TTY layer initialized
[   94.864759] Bluetooth: RFCOMM ver 1.8
[  107.511843] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  107.514567] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[  107.514920] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[  107.542703] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  110.524710] [fglrx] total      GART = 130023424
[  110.524717] [fglrx] free       GART = 114032640
[  110.524722] [fglrx] max single GART = 114032640
[  110.524725] [fglrx] total      LFB  = 134086656
[  110.524728] [fglrx] free       LFB  = 115871744
[  110.524732] [fglrx] max single LFB  = 115871744
[  110.524736] [fglrx] total      Inv  = 134217728
[  110.524740] [fglrx] free       Inv  = 134217728
[  110.524743] [fglrx] max single Inv  = 134217728
[  110.524747] [fglrx] total      TIM  = 0
[  151.946132] NET: Registered protocol family 10
[  151.946237] lo: Disabled Privacy Extensions
[  151.946304] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  151.946329] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  172.137399] NET: Registered protocol family 17
[  172.626758] ieee80211_crypt: registered algorithm 'WEP'
[  172.708062] SoftMAC: Open Authentication completed with 00:1a:70:e3:8e:cc
[  172.720628] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  186.334930] eth1: no IPv6 routers present



---

### Post by pssturges on 2007-10-24
Hi,
I have the the exact same problem. Fiesty boot was real quick, now gutsy real slow with a long period of blank/black screen. Sorry I have no idea where to start looking to solve the problem, but perhaps there are others with the same problem.

Phil

---

### Post by jrattner on 2007-10-24
Same for me about a 2 to 3 minute blank screen

---

### Post by flameproof on 2007-10-24
Same problem.

I guess that something is eating up your RAM. After booting, does your system  is very slow too? 

Check SYSTEM MONITOR>PROCESSES and see if one application eats up all available RAM.

For it's SCIM-LAUNCHER and I am still not sure how to fix it.

---

### Post by yani1shu on 2007-10-24
Same problem on my end. No  one out there has any ideas?

Here is the result of dmesg:


dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe40000 (usable)
[    0.000000]  BIOS-e820: 000000003fe40000 - 000000003fe50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fe50000 - 000000003ff00000 (ACPI NVS)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 261696) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261696
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261696
[    0.000000] On node 0 totalpages: 261696
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 252 pages used for memmap
[    0.000000]   HighMem zone: 32068 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7530 checksum 0
[    0.000000] ACPI: RSDP 000F7530, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FE40000, 002C (r1 GATEWA N2DTM001 20020430 MSFT       97)
[    0.000000] ACPI: FACP 3FE40200, 0081 (r2 GATEWA N2DTM001 20020430 MSFT       97)
[    0.000000] ACPI: DSDT 3FE40400, 3EEC (r1 GATEWA N2DTM001      10A MSFT  100000D)
[    0.000000] ACPI: FACS 3FE50000, 0040
[    0.000000] ACPI: APIC 3FE40300, 0054 (r1 GATEWA N2DTM001 20020430 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:c0100000)
[    0.000000] Built 1 zonelists.  Total pages: 259652
[    0.000000] Kernel command line: root=UUID=8156718a-6399-4f43-8f1d-78a3e4f75c40 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2000.110 MHz processor.
[    8.490526] Console: colour VGA+ 80x25
[    8.491500] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.492459] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.538473] Memory: 1026044k/1046784k available (2015k kernel code, 19988k reserved, 916k data, 364k init, 129280k highmem)
[    8.538489] virtual kernel memory layout:
[    8.538490]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    8.538492]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.538493]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.538494]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.538496]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    8.538497]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    8.538499]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    8.538505] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.538576] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.618457] Calibrating delay using timer specific routine.. 4003.97 BogoMIPS (lpj=8007944)
[    8.618507] Security Framework v1.0.0 initialized
[    8.618524] SELinux:  Disabled at boot.
[    8.618542] Mount-cache hash table entries: 512
[    8.618799] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[    8.618818] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    8.618822] CPU: L2 cache: 512K
[    8.618825] CPU: Hyper-Threading is disabled
[    8.618829] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[    8.618847] Compat vDSO mapped to ffffe000.
[    8.618871] Checking 'hlt' instruction... OK.
[    8.633265] SMP alternatives: switching to UP code
[    8.633619] Freeing SMP alternatives: 11k freed
[    8.634065] Early unpacking initramfs... done
[    9.067249] ACPI: Core revision 20070126
[    9.067333] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.070101] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
[    9.070150] Total of 1 processors activated (4003.97 BogoMIPS).
[    9.070299] ENABLING IO-APIC IRQs
[    9.070500] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.217373] Brought up 1 CPUs
[    9.217543] Booting paravirtualized kernel on bare hardware
[    9.217630] Time:  8:01:15  Date: 09/25/107
[    9.217664] NET: Registered protocol family 16
[    9.217796] EISA bus registered
[    9.217814] ACPI: bus type pci registered
[    9.217929] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    9.217932] PCI: Using configuration type 1
[    9.217934] Setting up standard PCI resources
[    9.230987] ACPI: EC: Look up EC in DSDT
[    9.235595] ACPI: Interpreter enabled
[    9.235600] ACPI: (supports S0 S1 S3 S4 S5)
[    9.235633] ACPI: Using IOAPIC for interrupt routing
[    9.243436] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.243463] PCI: Probing PCI hardware (bus 00)
[    9.243993] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    9.243995] * this clock source is slow. If you are sure your timer does not have
[    9.243997] * this bug, please use "acpi_pm_good" to disable the workaround
[    9.244052] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    9.244057] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[    9.244381] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[    9.244466] PCI: Transparent bridge - 0000:00:1e.0
[    9.244496] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.244641] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    9.246543] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    9.246744] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    9.246940] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    9.247138] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    9.247334] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    9.247531] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.247730] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.247929] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    9.248117] ACPI: Power Resource [URP1] (off)
[    9.248165] ACPI: Power Resource [FDDP] (off)
[    9.248214] ACPI: Power Resource [LPTP] (off)
[    9.248231] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.248247] pnp: PnP ACPI init
[    9.248266] ACPI: bus type pnp registered
[    9.252749] pnp: PnP ACPI: found 13 devices
[    9.252753] ACPI: ACPI bus type pnp unregistered
[    9.252760] PnPBIOS: Disabled by ACPI PNP
[    9.252846] PCI: Using ACPI for IRQ routing
[    9.252851] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.256286] NET: Registered protocol family 8
[    9.256289] NET: Registered protocol family 20
[    9.256407] pnp: 00:0b: ioport range 0x400-0x47f has been reserved
[    9.256412] pnp: 00:0b: ioport range 0x680-0x6ff has been reserved
[    9.256415] pnp: 00:0b: ioport range 0x480-0x4bf has been reserved
[    9.256420] pnp: 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    9.256423] pnp: 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    9.256432] pnp: 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    9.256436] pnp: 00:0c: iomem range 0xc0000-0xdffff could not be reserved
[    9.256439] pnp: 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    9.256443] pnp: 00:0c: iomem range 0x100000-0x3fefffff could not be reserved
[    9.257246] Time: tsc clocksource has been installed.
[    9.286849] PCI: Bridge: 0000:00:1e.0
[    9.286854]   IO window: d000-dfff
[    9.286861]   MEM window: ff800000-ff8fffff
[    9.286867]   PREFETCH window: e6a00000-e6afffff
[    9.286886] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.286904] NET: Registered protocol family 2
[    9.325181] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.325403] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    9.327770] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.328451] TCP: Hash tables configured (established 131072 bind 65536)
[    9.328461] TCP reno registered
[    9.337342] checking if image is initramfs... it is
[    9.788229] Switched to high resolution mode on CPU 0
[   10.192534] Freeing initrd memory: 7122k freed
[   10.193080] audit: initializing netlink socket (disabled)
[   10.193103] audit(1193299275.116:1): initialized
[   10.193234] highmem bounce pool size: 64 pages
[   10.196161] VFS: Disk quotas dquot_6.5.1
[   10.196249] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.196406] io scheduler noop registered
[   10.196410] io scheduler anticipatory registered
[   10.196413] io scheduler deadline registered
[   10.196437] io scheduler cfq registered (default)
[   10.196459] Boot video device is 0000:00:02.0
[   10.196735] isapnp: Scanning for PnP cards...
[   10.550396] isapnp: No Plug & Play device found
[   10.586385] Real Time Clock Driver v1.12ac
[   10.586525] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.586692] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.587759] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.588060] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 18 (level, low) -> IRQ 16
[   10.589429] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.589746] input: Macintosh mouse button emulation as /class/input/input0
[   10.589867] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   10.589871] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   10.593242] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.593252] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.593526] mice: PS/2 mouse device common for all mice
[   10.593694] EISA: Probing bus 0 at eisa.0
[   10.593736] EISA: Detected 0 cards.
[   10.593881] TCP cubic registered
[   10.593897] NET: Registered protocol family 1
[   10.593929] Using IPI No-Shortcut mode
[   10.594148]   Magic number: 11:710:18
[   10.594169]   hash matches device ttycf
[   10.594989] Freeing unused kernel memory: 364k freed
[   10.638642] input: AT Translated Set 2 keyboard as /class/input/input1
[   11.919073] AppArmor: AppArmor initialized<5>audit(1193299277.116:2):  type=1505 info="AppArmor initialized" pid=1185
[   12.128345] fuse init (API version 7.8)
[   12.135798] Failure registering capabilities with primary security module.
[   12.247691] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.614150] usbcore: registered new interface driver usbfs
[   22.614193] usbcore: registered new interface driver hub
[   22.614232] usbcore: registered new device driver usb
[   22.615633] USB Universal Host Controller Interface driver v3.0
[   22.615726] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
[   22.615742] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.615748] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.615955] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.615988] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000e800
[   22.616161] usb usb1: configuration #1 chosen from 1 choice
[   22.616198] hub 1-0:1.0: USB hub found
[   22.616209] hub 1-0:1.0: 2 ports detected
[   22.719083] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   22.719102] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.719107] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.719145] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.719178] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e880
[   22.719323] usb usb2: configuration #1 chosen from 1 choice
[   22.719362] hub 2-0:1.0: USB hub found
[   22.719373] hub 2-0:1.0: 2 ports detected
[   22.822868] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 16
[   22.822885] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.822890] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.822930] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.822967] uhci_hcd 0000:00:1d.2: irq 16, io base 0x0000ec00
[   22.823106] usb usb3: configuration #1 chosen from 1 choice
[   22.823142] hub 3-0:1.0: USB hub found
[   22.823153] hub 3-0:1.0: 2 ports detected
[   22.927699] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   22.927721] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.927726] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.927780] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   22.927831] ehci_hcd 0000:00:1d.7: debug port 1
[   22.927840] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   22.927856] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa7fc00
[   22.958413] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   22.958430] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.958581] usb usb4: configuration #1 chosen from 1 choice
[   22.958619] hub 4-0:1.0: USB hub found
[   22.958629] hub 4-0:1.0: 6 ports detected
[   23.307012] SCSI subsystem initialized
[   23.389576] usb 4-2: new high speed USB device using ehci_hcd and address 2
[   23.449659] libata version 2.21 loaded.
[   23.452174] ata_piix 0000:00:1f.1: version 2.11
[   23.452193] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   23.452203] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 16
[   23.452263] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.452372] scsi0 : ata_piix
[   23.452433] scsi1 : ata_piix
[   23.452578] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   23.452583] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   23.522860] usb 4-2: configuration #1 chosen from 1 choice
[   23.614583] ata1.00: ATA-6: WDC WD2000JB-53EVA0, 15.05R15, max UDMA/100
[   23.614590] ata1.00: 390721968 sectors, multi 16: LBA48 
[   23.630560] ata1.00: configured for UDMA/100
[   23.671905] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   23.671911] e100: Copyright(c) 1999-2006 Intel Corporation
[   23.692565] Floppy drive(s): fd0 is 1.44M
[   23.712666] FDC 0 is a post-1991 82077
[   23.944490] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   24.112437] ata2.00: ATAPI: _NEC DVD_RW ND-3500AG, 2.07, max UDMA/33
[   24.112446] ata2.01: ATAPI: CRD-8483B, 1.08, max UDMA/33
[   24.128621] usb 3-1: configuration #1 chosen from 1 choice
[   24.284119] ata2.00: configured for UDMA/33
[   24.503651] ata2.01: configured for UDMA/33
[   24.511391] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JB-53E 15.0 PQ: 0 ANSI: 5
[   24.512364] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-3500AG 2.07 PQ: 0 ANSI: 5
[   24.512688] scsi 1:0:1:0: CD-ROM            LG       CD-ROM CRD-8483B 1.08 PQ: 0 ANSI: 5
[   24.515277] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   24.538560] e100: eth0: e100_probe: addr 0xff8fe000, irq 20, MAC addr 00:03:47:FB:67:07
[   24.716659] usbcore: registered new interface driver libusual
[   24.726303] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.726311] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.729189] Initializing USB Mass Storage driver...
[   24.729280] scsi2 : SCSI emulation for USB Mass Storage devices
[   24.729344] usb-storage: device found at 2
[   24.729347] usb-storage: waiting for device to settle before scanning
[   24.729373] usbcore: registered new interface driver usb-storage
[   24.729376] USB Mass Storage support registered.
[   24.860001] usbcore: registered new interface driver hiddev
[   24.886681] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   24.890649] sd 0:0:0:0: [sda] Write Protect is off
[   24.890653] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.896315] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00 as /class/input/input2
[   24.896331] input: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00] on usb-0000:00:1d.2-1
[   24.896362] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.898611] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   24.898969] sd 0:0:0:0: [sda] Write Protect is off
[   24.898973] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.901948] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.901954]  sda: sda1 sda2 < sda5 >
[   24.942254] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.945874] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   24.945880] Uniform CD-ROM driver Revision: 3.20
[   24.945951] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.949592] sr1: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   24.949635] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   24.958940] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00 as /class/input/input3
[   24.958991] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00] on usb-0000:00:1d.2-1
[   24.959012] usbcore: registered new interface driver usbhid
[   24.959017] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.011355] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.011391] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   25.011422] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   26.805262] Attempting manual resume
[   26.805267] swsusp: Resume From Partition 8:5
[   26.805270] PM: Checking swsusp image.
[   26.902701] PM: Resume from disk failed.
[   28.423777] kjournald starting.  Commit interval 5 seconds
[   28.423795] EXT3-fs: mounted filesystem with ordered data mode.
[   29.717299] usb-storage: device scan complete
[   29.721190] scsi 2:0:0:0: Direct-Access     WD       5000AAJ External 1.06 PQ: 0 ANSI: 0
[   29.757094] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   29.757917] sd 2:0:0:0: [sdb] Write Protect is off
[   29.757921] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   29.757925] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   29.761087] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   29.761911] sd 2:0:0:0: [sdb] Write Protect is off
[   29.761915] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   29.761917] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   29.761923]  sdb: sdb1
[   36.875295] sd 2:0:0:0: [sdb] Attached SCSI disk
[   36.875357] sd 2:0:0:0: Attached scsi generic sg3 type 0
[  123.359465] Linux agpgart interface v0.102 (c) Dave Jones
[  123.577734] agpgart: Detected an Intel 830M Chipset.
[  123.577878] agpgart: Detected 892K stolen memory.
[  123.595758] agpgart: AGP aperture is 128M @ 0xf0000000
[  123.708568] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[  123.866813] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[  123.866817]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[  123.866819]  you are certain that your <4>intel_rng: system has a functional
[  123.866821]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[  123.875904] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  123.878416] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  123.889706] iTCO_vendor_support: vendor-support=0
[  123.891179] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[  123.891257] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[  123.891295] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  125.542738] usbcore: registered new interface driver xpad
[  125.542744] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[  126.153445] input: PC Speaker as /class/input/input4
[  126.618706] parport_pc 00:09: reported by Plug and Play ACPI
[  126.618762] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  126.909200] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[  126.909230] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  127.278045] intel8x0_measure_ac97_clock: measured 54922 usecs
[  127.278051] intel8x0: clocking to 48000
[  129.465833] lp0: using parport0 (interrupt-driven).
[  129.991148] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[  132.284006] EXT3 FS on sda1, internal journal
[  144.467987] No dock devices found.
[  145.385991] input: Power Button (FF) as /class/input/input5
[  145.392304] ACPI: Power Button (FF) [PWRF]
[  145.437697] input: Sleep Button (CM) as /class/input/input6
[  145.444021] ACPI: Sleep Button (CM) [SLPB]
[  153.347065] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  153.938182] ppdev: user-space parallel port driver
[  154.381274] audit(1193299420.302:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5091 profile="/usr/sbin/cupsd"
[  154.457253] apm: BIOS not found.
[  155.460563] [drm] Initialized drm 1.1.0 20060810
[  155.491861] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[  155.495651] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  157.025133] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[  157.704092] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  157.814247] NFSD: starting 90-second grace period
[  159.533476] Failure registering capabilities with primary security module.
[  159.803315] Bluetooth: Core ver 2.11
[  159.803509] NET: Registered protocol family 31
[  159.803513] Bluetooth: HCI device and connection manager initialized
[  159.803518] Bluetooth: HCI socket layer initialized
[  159.829078] Bluetooth: L2CAP ver 2.8
[  159.829085] Bluetooth: L2CAP socket layer initialized
[  159.888194] Bluetooth: RFCOMM socket layer initialized
[  159.888358] Bluetooth: RFCOMM TTY layer initialized
[  159.888363] Bluetooth: RFCOMM ver 1.8
[  165.095892] NET: Registered protocol family 17
[  168.057425] NET: Registered protocol family 10
[  168.057698] lo: Disabled Privacy Extensions
[  178.649405] eth0: no IPv6 routers present
[  617.551005] UDP: short packet: From 64.30.2.130:9090 25649/73 to 192.168.1.102:46620

---

### Post by steveneddy on 2007-10-24
If you installed bootchart, you could look at the chart and determine where the problem lies.

After install, just reboot and upon login, look in /var/log/bootchart - view the log in Firefox and look down the chart to see what is running when the full cpu usage starts. Diag from there.

---

### Post by pssturges on 2007-10-24
> **flameproof said:**
> Same problem.

I guess that something is eating up your RAM. After booting, does your system  is very slow too? 

Check SYSTEM MONITOR>PROCESSES and see if one application eats up all available RAM.

For it's SCIM-LAUNCHER and I am still not sure how to fix it.

Once mine's booted, it runs very nicely. Just have to wait for it to boot....

Phil

---

### Post by jrattner on 2007-10-25
This is very discouraging...I timed my boot at 3:52 seconds...with is needless to say PATHETIC.

It seems like Gutsy has taken a step back in many ways...I wish I never upgraded.


For some hope I will try to install the boot chart as suggested to further diagnose this problem

---

### Post by jenhsun on 2007-10-25
Take a look at this thread
[http://ubuntuforums.org/showthread.php?t=586072](http://ubuntuforums.org/showthread.php?t=586072)
It could speed up the booting. I confirm about that.

---

### Post by pssturges on 2007-10-25
Yeah!

That fixed it!! Boot time down to approx 1min!

In summary:


- edit /etc/usplash.conf, change to 1024x768
- run sudo update-initramfs -u -k `uname -r`

That's it!

Hope that helps
Phil

---

