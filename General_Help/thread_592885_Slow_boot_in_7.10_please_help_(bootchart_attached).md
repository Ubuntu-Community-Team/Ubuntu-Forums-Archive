---
title: "Slow boot in 7.10: please help (bootchart attached)"
date: 2007-10-26
forum: General Help
---

### Post by mthakur2006 on 2007-10-26
Hi,
I have recently upgraded to Gutsy and everything was going fine until I decided to format my disk again and I used this partitioning setup:

/ - 10 GB - reiserfs
/boot - 32 MB - ext2
/home - 29.5 GB - ext3
swap - 510.7 MB

with ext3 as / partition, i was getting 27 second boot time but my desktop was less responsive than it is with reiserfs. i have pinpointed that reiserfsck becomes a zombie process and that slows the boot process. any way to eliminate that?

here is my dmesg:

```

$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f7df000 (usable)
[    0.000000]  BIOS-e820: 000000002f7e0000 - 000000002f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f7fffc0 - 000000002f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 194527) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   194527
[    0.000000]   HighMem    194527 ->   194527
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   194527
[    0.000000] On node 0 totalpages: 194527
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1487 pages used for memmap
[    0.000000]   Normal zone: 188944 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E5010 checksum 0
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 LENOVO)
[    0.000000] ACPI: RSDT 2F7FC804, 0030 (r1 LENOVO TP-60          15 ABCD    10200)
[    0.000000] ACPI: FACP 2F7FFB00, 0074 (r1 LENOVO FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 2F7FCA20, 30DD (r1 LENOVO TP-60          15 INTL  2002036)
[    0.000000] ACPI: FACS 2F7FFFC0, 0040
[    0.000000] ACPI: APIC 2F7FFB90, 0068 (r1 STUPID MAPIC_00 30307830 ABCD    10200)
[    0.000000] ACPI: SSDT 2F7FC834, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f800000:d0700000)
[    0.000000] Built 1 zonelists.  Total pages: 193008
[    0.000000] Kernel command line: root=UUID=e6fce4a1-94c8-43f9-920a-1c027cc04bd4 ro splash rootflags=data=writeback
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1496.272 MHz processor.
[   26.962600] Console: colour VGA+ 80x25
[   26.965943] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.966588] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.992088] Memory: 759564k/778108k available (2015k kernel code, 17800k reserved, 916k data, 364k init, 0k highmem)
[   26.992202] virtual kernel memory layout:
[   26.992204]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   26.992205]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.992207]     vmalloc : 0xf0000000 - 0xff7fe000   ( 247 MB)
[   26.992208]     lowmem  : 0xc0000000 - 0xef7df000   ( 759 MB)
[   26.992210]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   26.992211]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   26.992213]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   26.992751] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.992922] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   27.073003] Calibrating delay using timer specific routine.. 2995.95 BogoMIPS (lpj=5991900)
[   27.073159] Security Framework v1.0.0 initialized
[   27.073233] SELinux:  Disabled at boot.
[   27.073310] Mount-cache hash table entries: 512
[   27.073513] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   27.073527] CPU: L1 I cache: 32K, L1 D cache: 32K
[   27.073628] CPU: L2 cache: 1024K
[   27.073691] CPU: After all inits, caps: afe9fbff 00000000 00000000 00002040 00000000 00000000 00000000
[   27.073701] Compat vDSO mapped to ffffe000.
[   27.073776] Checking 'hlt' instruction... OK.
[   27.089160] SMP alternatives: switching to UP code
[   27.089434] Freeing SMP alternatives: 11k freed
[   27.089796] Early unpacking initramfs... done
[   27.478965] ACPI: Core revision 20070126
[   27.479096] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.580297] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
[   27.580466] Total of 1 processors activated (2995.95 BogoMIPS).
[   27.580728] ENABLING IO-APIC IRQs
[   27.581017] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   27.728736] Brought up 1 CPUs
[   27.728925] Booting paravirtualized kernel on bare hardware
[   27.729065] Time: 22:03:28  Date: 09/26/107
[   27.729158] NET: Registered protocol family 16
[   27.729314] EISA bus registered
[   27.729390] ACPI: bus type pci registered
[   27.729510] PCI: PCI BIOS revision 2.10 entry at 0xea704, last bus=1
[   27.729582] PCI: Using configuration type 1
[   27.729648] Setting up standard PCI resources
[   27.731917] ACPI: EC: Look up EC in DSDT
[   27.732347] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   27.733284] ACPI: Interpreter enabled
[   27.733350] ACPI: (supports S0 S3 S4 S5)
[   27.733590] ACPI: Using IOAPIC for interrupt routing
[   27.785379] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   27.785495] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.785568] PCI: Probing PCI hardware (bus 00)
[   27.786280] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   27.786355] PCI quirk: region 1300-133f claimed by ICH6 GPIO
[   27.787165] PCI: Transparent bridge - 0000:00:1e.0
[   27.787322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.787659] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   27.793683] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   27.794287] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   27.794831] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   27.795427] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[   27.795972] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   27.796515] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   27.797090] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   27.797687] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[   27.798237] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.798317] pnp: PnP ACPI init
[   27.798386] ACPI: bus type pnp registered
[   27.821015] pnp: PnP ACPI: found 7 devices
[   27.821083] ACPI: ACPI bus type pnp unregistered
[   27.821152] PnPBIOS: Disabled by ACPI PNP
[   27.821263] PCI: Using ACPI for IRQ routing
[   27.821331] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.826303] NET: Registered protocol family 8
[   27.826369] NET: Registered protocol family 20
[   27.826501] pnp: 00:03: ioport range 0x800-0x80f has been reserved
[   27.826574] pnp: 00:03: ioport range 0x1000-0x107f has been reserved
[   27.826647] pnp: 00:03: iomem range 0xe0000-0xfffff could not be reserved
[   27.826722] pnp: 00:03: iomem range 0xf0008000-0xf000bfff has been reserved
[   27.826796] pnp: 00:03: iomem range 0xe0000000-0xefffffff has been reserved
[   27.826870] pnp: 00:03: iomem range 0xfff80000-0xffffffff could not be reserved
[   27.828647] Time: tsc clocksource has been installed.
[   27.857259] PCI: Bus 2, cardbus bridge: 0000:01:04.0
[   27.857328]   IO window: 0000c400-0000c4ff
[   27.857397]   IO window: 0000c800-0000c8ff
[   27.857466]   PREFETCH window: 90000000-93ffffff
[   27.857538]   MEM window: c4000000-c7ffffff
[   27.857607] PCI: Bridge: 0000:00:1e.0
[   27.857672]   IO window: c000-dfff
[   27.857739]   MEM window: c0000000-cfffffff
[   27.857808]   PREFETCH window: 90000000-9fffffff
[   27.857892] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   27.857914] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.858056] NET: Registered protocol family 2
[   27.896643] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.896798] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   27.898917] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   27.899845] TCP: Hash tables configured (established 131072 bind 65536)
[   27.899921] TCP reno registered
[   27.908787] checking if image is initramfs... it is
[   28.360388] Switched to high resolution mode on CPU 0
[   28.668856] Freeing initrd memory: 7047k freed
[   28.669352] audit: initializing netlink socket (disabled)
[   28.669439] audit(1193436208.140:1): initialized
[   28.671647] VFS: Disk quotas dquot_6.5.1
[   28.671772] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   28.671956] io scheduler noop registered
[   28.672022] io scheduler anticipatory registered
[   28.672088] io scheduler deadline registered
[   28.672188] io scheduler cfq registered (default)
[   28.672269] Boot video device is 0000:00:02.0
[   28.672503] isapnp: Scanning for PnP cards...
[   29.026698] isapnp: No Plug & Play device found
[   29.061251] Real Time Clock Driver v1.12ac
[   29.061440] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.062414] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 17
[   29.062550] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   29.063189] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.063532] input: Macintosh mouse button emulation as /class/input/input0
[   29.063683] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   29.092293] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.092368] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.092619] mice: PS/2 mouse device common for all mice
[   29.094301] EISA: Probing bus 0 at eisa.0
[   29.094374] Cannot allocate resource for EISA slot 1
[   29.094468] EISA: Detected 0 cards.
[   29.094643] TCP cubic registered
[   29.094724] NET: Registered protocol family 1
[   29.094818] Using IPI No-Shortcut mode
[   29.095086]   Magic number: 11:825:98
[   29.095543] Freeing unused kernel memory: 364k freed
[   29.115958] input: AT Translated Set 2 keyboard as /class/input/input1
[   30.321216] AppArmor: AppArmor initialized<5>audit(1193436209.640:2):  type=1505 info="AppArmor initialized" pid=1302
[   30.338640] fuse init (API version 7.8)
[   30.343139] Failure registering capabilities with primary security module.
[   30.359922] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   30.359931] ACPI: Processor [CPU0] (supports 8 throttling states)
[   30.883043] usbcore: registered new interface driver usbfs
[   30.883072] usbcore: registered new interface driver hub
[   30.883095] usbcore: registered new device driver usb
[   30.884009] USB Universal Host Controller Interface driver v3.0
[   30.884087] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   30.884099] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   30.884104] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   30.884329] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   30.884363] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001200
[   30.884495] usb usb1: configuration #1 chosen from 1 choice
[   30.884528] hub 1-0:1.0: USB hub found
[   30.884534] hub 1-0:1.0: 2 ports detected
[   30.986938] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   30.986955] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   30.986960] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   30.986991] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   30.987025] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001220
[   30.987133] usb usb2: configuration #1 chosen from 1 choice
[   30.987161] hub 2-0:1.0: USB hub found
[   30.987168] hub 2-0:1.0: 2 ports detected
[   31.050874] SCSI subsystem initialized
[   31.056754] libata version 2.21 loaded.
[   31.066038] 8139too Fast Ethernet driver 0.9.28
[   31.090901] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   31.090917] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   31.090922] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   31.090950] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   31.090985] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001240
[   31.091102] usb usb3: configuration #1 chosen from 1 choice
[   31.091132] hub 3-0:1.0: USB hub found
[   31.091139] hub 3-0:1.0: 2 ports detected
[   31.194821] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   31.194837] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   31.194842] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   31.194868] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   31.194904] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001260
[   31.195018] usb usb4: configuration #1 chosen from 1 choice
[   31.195048] hub 4-0:1.0: USB hub found
[   31.195055] hub 4-0:1.0: 2 ports detected
[    4.104000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.112000] Time: acpi_pm clocksource has been installed.
[    4.112000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[    4.112000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[    4.112000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.112000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.112000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.112000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.112000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.112000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0x30000000
[    4.116000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.116000] usb usb5: configuration #1 chosen from 1 choice
[    4.116000] hub 5-0:1.0: USB hub found
[    4.116000] hub 5-0:1.0: 8 ports detected
[    4.220000] ata_piix 0000:00:1f.1: version 2.11
[    4.220000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[    4.220000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.220000] scsi0 : ata_piix
[    4.220000] scsi1 : ata_piix
[    4.220000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14
[    4.220000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15
[    4.548000] ata1.00: ATA-6: HTS541040G9AT00, MB2IA60A, max UDMA/100
[    4.548000] ata1.00: 78140160 sectors, multi 16: LBA 
[    4.548000] ata1.01: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, 1.00, max UDMA/33
[    4.564000] ata1.00: configured for UDMA/100
[    4.736000] ata1.01: configured for UDMA/33
[    4.900000] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2I PQ: 0 ANSI: 5
[    4.908000] scsi 0:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N 1.00 PQ: 0 ANSI: 5
[    4.908000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 20 (level, low) -> IRQ 17
[    4.960000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[c0002800-c0002fff]  Max Packet=[1024]  IR/IT contexts=[4/8]
[    4.980000] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[    4.980000] eth0: RealTek RTL8139 at 0xf0078000, 00:0f:b0:c9:ff:07, IRQ 21
[    4.980000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.984000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.988000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.992000] sd 0:0:0:0: [sda] Write Protect is off
[    4.992000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.992000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.992000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.992000] sd 0:0:0:0: [sda] Write Protect is off
[    4.992000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.992000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.992000]  sda: sda1 sda2 sda3 sda4
[    5.036000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.040000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.040000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    5.068000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.068000] Uniform CD-ROM driver Revision: 3.20
[    5.068000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.336000] Attempting manual resume
[    5.336000] swsusp: Resume From Partition 8:3
[    5.336000] PM: Checking swsusp image.
[    5.336000] PM: Resume from disk failed.
[    5.348000] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[    5.348000] ReiserFS: sda2: using writeback data mode
[    5.360000] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    5.360000] ReiserFS: sda2: checking transaction log (sda2)
[    5.416000] ReiserFS: sda2: Using r5 hash to sort names
[    6.236000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f658e402897]
[   11.668000] Clocksource tsc unstable (delta = -303635755 ns)
[   13.740000] Linux agpgart interface v0.102 (c) Dave Jones
[   13.840000] agpgart: Detected an Intel 915GM Chipset.
[   13.840000] agpgart: Detected 7932K stolen memory.
[   13.860000] agpgart: AGP aperture is 256M @ 0xa0000000
[   14.540000] Yenta: CardBus bridge found at 0000:01:04.0 [17aa:2075]
[   14.540000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   14.540000] Yenta: Routing CardBus interrupts to PCI
[   14.540000] Yenta TI: socket 0000:01:04.0, mfunc 0x10511212, devctl 0x44
[   14.552000] sdhci: Secure Digital Host Controller Interface driver
[   14.552000] sdhci: Copyright(c) Pierre Ossman
[   14.564000] intel_rng: FWH not detected
[   14.592000] iTCO_vendor_support: vendor-support=0
[   14.596000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.596000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   14.596000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.732000] ieee80211_crypt: registered algorithm 'NULL'
[   14.772000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   14.772000] Socket status: 30000006
[   14.772000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xdfff
[   14.772000] cs: IO port probe 0xc000-0xdfff: clean.
[   14.772000] pcmcia: parent PCI bridge Memory window: 0xc0000000 - 0xcfffffff
[   14.772000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff
[   14.772000] sdhci: SDHCI controller found at 0000:01:04.2 [1524:0550] (rev 1)
[   14.772000] ACPI: PCI Interrupt 0000:01:04.2[B] -> GSI 17 (level, low) -> IRQ 22
[   14.772000] mmc0: SDHCI at 0xc0000100 irq 22 DMA
[   14.776000] sdhci: SDHCI controller found at 0000:01:04.4 [1524:0551] (rev 1)
[   14.776000] ACPI: PCI Interrupt 0000:01:04.4[B] -> GSI 17 (level, low) -> IRQ 22
[   14.776000] mmc1: SDHCI at 0xc0000200 irq 22 PIO
[   14.800000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.800000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.216000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   15.216000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.272000] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 22 (level, low) -> IRQ 23
[   15.272000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   15.804000] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)
[   15.864000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 22
[   15.864000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   15.892000] cs: IO port probe 0x100-0x3af: clean.
[   15.896000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.896000] cs: IO port probe 0x820-0x8ff: clean.
[   15.896000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.896000] cs: IO port probe 0xa00-0xaff: clean.
[   16.500000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x200000
[   16.584000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   16.692000] intel8x0_measure_ac97_clock: measured 55410 usecs
[   16.692000] intel8x0: clocking to 48000
[   17.040000] loop: module loaded
[   17.076000] lp: driver loaded but no devices found
[   17.152000] Adding 489972k swap on /dev/sda3.  Priority:-1 extents:1 across:489972k
[   25.932000] kjournald starting.  Commit interval 5 seconds
[   25.932000] EXT3 FS on sda4, internal journal
[   25.932000] EXT3-fs: mounted filesystem with ordered data mode.
[   26.712000] ACPI: AC Adapter [ACAD] (off-line)
[   26.728000] No dock devices found.
[   26.824000] input: Power Button (FF) as /class/input/input3
[   26.824000] ACPI: Power Button (FF) [PWRF]
[   26.872000] input: Lid Switch as /class/input/input4
[   26.876000] ACPI: Lid Switch [LID0]
[   26.920000] input: Power Button (CM) as /class/input/input5
[   26.928000] ACPI: Power Button (CM) [PWRB]
[   27.164000] ACPI: Battery Slot [BAT1] (battery present)
[   27.176000] ACPI: Video Device [GFX1] (multi-head: yes  rom: no  post: no)
[   27.176000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   28.588000] eth0: link down
[   28.592000] ppdev: user-space parallel port driver
[   28.788000] audit(1193432636.677:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=6245 profile="/usr/sbin/cupsd"
[   29.160000] Failure registering capabilities with primary security module.
[   32.200000] [drm] Initialized drm 1.1.0 20060810
[   32.204000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.204000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   63.448000] NET: Registered protocol family 17
[   63.988000] ieee80211_crypt: registered algorithm 'CCMP'
[   70.872000] NET: Registered protocol family 10
[   70.872000] lo: Disabled Privacy Extensions
[   70.872000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   81.124000] eth1: no IPv6 routers present

```
Thanks.

---

### Post by dabl on 2007-10-26
32MB is really squeezing the /boot partition -- I think the last time I looked it takes about 28MB for one kernel, for a new installation.  I made my /boot partition 200MB so I don't have to think about it as I add new kernels (and boot splash images).  :)

BTW, you can get by comfortably with 6GB for your root partition (in case you're looking for space).

;-)

---

### Post by mthakur2006 on 2007-10-26
> **dabl said:**
> 32MB is really squeezing the /boot partition -- I think the last time I looked it takes about 28MB for one kernel, for a new installation.  I made my /boot partition 200MB so I don't have to think about it as I add new kernels (and boot splash images).  :)

BTW, you can get by comfortably with 6GB for your root partition (in case you're looking for space).

;-)

okay thanks, i will keep that in mind next time round :D
any clue about shaving off that 4 seconds from that boot time?
thanks.

---

### Post by barbolani on 2007-12-30
My bootchart was very similar to yours, with the addition of a second "zombie" time because I've two reiser partitions, the one for / and the one for /home. Also, my total boot time was 50 seconds.

What I've done is change the /etc/fstab parameters for the two reiser partitions. Where it was

```

# /dev/hda6 -- converted during upgrade to edgy
UUID=[my / UUID] / reiserfs nouser,notail,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda7 -- converted during upgrade to edgy
UUID=[my /homeUUID] /home reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2

```

I've changed them to 

```

# /dev/hda6 -- converted during upgrade to edgy
UUID=[my / UUID] / reiserfs nouser,notail,atime,auto,rw,dev,exec,suid 0 0
# /dev/hda7 -- converted during upgrade to edgy
UUID=[my /homeUUID] /home reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 0

```

The last parameter of each fstab line tells if you want to check the filesystem before mounting. Notice that on the / partition there was an 1 and in the /home partition a value of 2. Setting in both cases them to 0 means supposedly "don't check before mounting"

With this change my boot time is now, according to bootchart, 30 seconds.

Now, I'm not sure if I'm placing myself at risk in case something corrupts the / or /home filesystems. Before changing the parameters, I had two files updated in /var/log/fsck, called "checkfs" and "checkroot" Seems that "checkfs" is still updated after booting, but "checkroot" is no longer being done.

Any advice on whether is safe or not to leave the last fstab parameter at "0"

---

