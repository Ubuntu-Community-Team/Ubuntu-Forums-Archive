---
title: "Slooooowww  boot.... help!"
date: 2007-05-07
forum: General Help
---

### Post by ld50 on 2007-05-07
up until now I have had too many major problems with Ubuntu to worry about the boot time but it is getting annoying.  Anyone know what is going on? Looks to me that it is with the SATA devices starting up. Here is the info that I have.

```

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fe80000 end: 000000003ff80000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003ff80000 size: 000000000000e000 end: 000000003ff8e000 type: 3
[    0.000000] copy_e820_map() start: 000000003ff8e000 size: 0000000000052000 end: 000000003ffe0000 type: 4
[    0.000000] copy_e820_map() start: 000000003ffe0000 size: 0000000000020000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff80000 (usable)
[    0.000000]  BIOS-e820: 000000003ff80000 - 000000003ff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff8e000 - 000000003ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ffe0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262016) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262016
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262016
[    0.000000] On node 0 totalpages: 262016
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32385 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000faf20
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x09000626 MSFT 0x00000097) @ 0x3ff80000
[    0.000000] ACPI: FADT (v001 A M I  OEMFACP  0x09000626 MSFT 0x00000097) @ 0x3ff80200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x09000626 MSFT 0x00000097) @ 0x3ff80390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x09000626 MSFT 0x00000097) @ 0x3ff8e040
[    0.000000] ACPI: HPET (v001 A M I  OEMHPET  0x09000626 MSFT 0x00000097) @ 0x3ff894c0
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x09000626 MSFT 0x00000097) @ 0x3ff89500
[    0.000000] ACPI: DSDT (v001  A0543 A0543000 0x00000000 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb00000)
[    0.000000] Detected 3118.025 MHz processor.
[   36.353134] Built 1 zonelists.  Total pages: 259969
[   36.353138] Kernel command line: root=/dev/md1 ro quiet splash
[   36.353222] mapped APIC to ffffd000 (fee00000)
[   36.353223] mapped IOAPIC to ffffc000 (fec00000)
[   36.353225] Enabling fast FPU save and restore... done.
[   36.353227] Enabling unmasked SIMD FPU exception support... done.
[   36.353232] Initializing CPU#0
[   36.353281] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   36.354025] Console: colour VGA+ 80x25
[   36.354220] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   36.354403] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   36.369726] Memory: 1027612k/1048064k available (1992k kernel code, 19724k reserved, 893k data, 328k init, 130560k highmem)
[   36.369731] virtual kernel memory layout:
[   36.369731]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   36.369732]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   36.369732]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   36.369733]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   36.369734]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   36.369734]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   36.369735]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   36.369737] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   36.369826] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   36.369830] hpet0: 3 64-bit timers, 14318180 Hz
[   36.370831] Using HPET for base-timer
[   36.449722] Calibrating delay using timer specific routine.. 6239.73 BogoMIPS (lpj=12479474)
[   36.449745] Security Framework v1.0.0 initialized
[   36.449749] SELinux:  Disabled at boot.
[   36.449757] Mount-cache hash table entries: 512
[   36.449838] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   36.449842] monitor/mwait feature present.
[   36.449843] using mwait in idle threads.
[   36.449846] CPU: L1 I cache: 32K, L1 D cache: 32K
[   36.449847] CPU: L2 cache: 4096K
[   36.449848] CPU: Physical Processor ID: 0
[   36.449849] CPU: Processor Core ID: 0
[   36.449850] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   36.449855] Compat vDSO mapped to ffffe000.
[   36.449857] Remapping vsyscall page to ffffe000
[   36.449864] Checking 'hlt' instruction... OK.
[   36.465754] SMP alternatives: switching to UP code
[   36.465945] Early unpacking initramfs... done
[   36.640230] ACPI: Core revision 20060707
[   36.640427] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   36.654752] CPU0: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[   36.654767] SMP alternatives: switching to SMP code
[   36.654819] Booting processor 1/1 eip 3000
[   36.685697] Initializing CPU#1
[   36.765301] Calibrating delay using timer specific routine.. 6235.68 BogoMIPS (lpj=12471360)
[   36.765305] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   36.765308] monitor/mwait feature present.
[   36.765309] CPU: L1 I cache: 32K, L1 D cache: 32K
[   36.765310] CPU: L2 cache: 4096K
[   36.765312] CPU: Physical Processor ID: 0
[   36.765313] CPU: Processor Core ID: 1
[   36.765313] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   36.765766] CPU1: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[   36.765778] Total of 2 processors activated (12475.41 BogoMIPS).
[   36.765915] ENABLING IO-APIC IRQs
[   36.766072] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   36.913105] checking TSC synchronization across 2 CPUs: passed.
[    0.003996] Brought up 2 CPUs
[    0.068061] migration_cost=569
[    0.068226] Booting paravirtualized kernel on bare hardware
[    0.068278] Time: 14:22:57  Date: 04/07/107
[    0.068295] NET: Registered protocol family 16
[    0.068349] EISA bus registered
[    0.068352] ACPI: bus type pci registered
[    0.068449] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.068450] PCI: Using configuration type 1
[    0.068451] Setting up standard PCI resources
[    0.080358] ACPI: Interpreter enabled
[    0.080360] ACPI: Using IOAPIC for interrupt routing
[    0.080937] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.080942] PCI: Probing PCI hardware (bus 00)
[    0.081413] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.081416] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.081574] Boot video device is 0000:05:00.0
[    0.081978] PCI: Transparent bridge - 0000:00:1e.0
[    0.082021] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.083507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.083696] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.083886] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.084269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.084429] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.087406] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.087558] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.087708] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.087860] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.088014] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.088164] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.088315] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.088467] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.088530] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.088537] pnp: PnP ACPI init
[    0.090321] pnp: PnP ACPI: found 13 devices
[    0.090323] PnPBIOS: Disabled by ACPI PNP
[    0.090349] PCI: Using ACPI for IRQ routing
[    0.090350] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.097693] NET: Registered protocol family 8
[    0.097695] NET: Registered protocol family 20
[    0.098123] pnp: 00:06: ioport range 0x290-0x297 has been reserved
[    0.098283] PCI: Bridge: 0000:00:01.0
[    0.098285]   IO window: c000-cfff
[    0.098287]   MEM window: ff900000-ff9fffff
[    0.098289]   PREFETCH window: cff00000-efefffff
[    0.098291] PCI: Bridge: 0000:00:1c.0
[    0.098291]   IO window: disabled.
[    0.098294]   MEM window: disabled.
[    0.098297]   PREFETCH window: cfe00000-cfefffff
[    0.098300] PCI: Bridge: 0000:00:1c.3
[    0.098301]   IO window: b000-bfff
[    0.098304]   MEM window: ff800000-ff8fffff
[    0.098306]   PREFETCH window: disabled.
[    0.098309] PCI: Bridge: 0000:00:1c.4
[    0.098311]   IO window: a000-afff
[    0.098314]   MEM window: ff700000-ff7fffff
[    0.098316]   PREFETCH window: disabled.
[    0.098319] PCI: Bridge: 0000:00:1e.0
[    0.098320]   IO window: disabled.
[    0.098323]   MEM window: ff600000-ff6fffff
[    0.098325]   PREFETCH window: disabled.
[    0.098334] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.098337] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.098348] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.098351] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.098363] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[    0.098366] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.098377] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[    0.098380] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.098387] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.098404] NET: Registered protocol family 2
[    0.147824] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.147878] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.148200] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.148381] TCP: Hash tables configured (established 131072 bind 65536)
[    0.148382] TCP reno registered
[    0.163843] checking if image is initramfs... it is
[    0.508620] Freeing initrd memory: 7005k freed
[    0.509096] audit: initializing netlink socket (disabled)
[    0.509111] audit(1178547777.112:1): initialized
[    0.509177] highmem bounce pool size: 64 pages
[    0.509233] VFS: Disk quotas dquot_6.5.1
[    0.509247] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.509288] io scheduler noop registered
[    0.509289] io scheduler anticipatory registered
[    0.509290] io scheduler deadline registered
[    0.509296] io scheduler cfq registered (default)
[    0.509473] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.509493] assign_interrupt_mode Found MSI capability
[    0.509495] Allocate Port Service[0000:00:01.0:pcie00]
[    0.509545] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.509573] assign_interrupt_mode Found MSI capability
[    0.509575] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.509597] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.509660] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.509687] assign_interrupt_mode Found MSI capability
[    0.509688] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.509751] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.509778] assign_interrupt_mode Found MSI capability
[    0.509780] Allocate Port Service[0000:00:1c.4:pcie00]
[    0.509882] isapnp: Scanning for PnP cards...
[    0.862194] isapnp: No Plug & Play device found
[    0.873777] Real Time Clock Driver v1.12ac
[    0.873901] hpet_resources: 0xfed00000 is busy
[    0.873913] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    0.874009] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.874361] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.874454] mice: PS/2 mouse device common for all mice
[    0.874775] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    0.874871] input: Macintosh mouse button emulation as /class/input/input0
[    0.874892] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    0.874894] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    0.875053] PNP: No PS/2 controller found. Probing ports directly.
[    0.877145] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.877147] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.877206] EISA: Probing bus 0 at eisa.0
[    0.877228] EISA: Detected 0 cards.
[    0.907280] TCP cubic registered
[    0.907287] NET: Registered protocol family 1
[    0.907303] Starting balanced_irq
[    0.907307] Using IPI No-Shortcut mode
[    0.907372] ACPI: (supports S0 S1 S3 S4 S5)
[    0.907399]   Magic number: 7:824:383
[    0.907557] Freeing unused kernel memory: 328k freed
[    0.910785] Time: tsc clocksource has been installed.
[    2.029127] Capability LSM initialized
[    2.049315] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.049359] ACPI: Processor [CPU2] (supports 8 throttling states)
[    2.049363] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.049367] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.082698] md: raid1 personality registered for level 1
[    2.085891] md: md1 stopped.
[    2.286187] usbcore: registered new interface driver usbfs
[    2.286204] usbcore: registered new interface driver hub
[    2.286218] usbcore: registered new device driver usb
[    2.286777] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[    2.286787] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    2.286789] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.286888] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.286908] ehci_hcd 0000:00:1d.7: debug port 1
[    2.286912] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    2.286918] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffafbc00
[    2.290801] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.290872] usb usb1: configuration #1 chosen from 1 choice
[    2.290887] hub 1-0:1.0: USB hub found
[    2.290890] hub 1-0:1.0: 8 ports detected
[    2.293131] USB Universal Host Controller Interface driver v3.0
[    2.303476] SCSI subsystem initialized
[    2.311113] libata version 2.20 loaded.
[    2.311134] ieee1394: Initialized config rom entry `ip1394'
[    2.399891] ata_piix 0000:00:1f.1: version 2.10ac1
[    2.399905] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 19
[    2.399920] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    2.399950] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    2.399966] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    2.399980] scsi0 : ata_piix
[    2.740555] ata1.00: ATAPI, max UDMA/66
[    2.771770] ata1.01: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    2.771772] ata1.01: ATA-7: ST3120814A, 2AAA, max UDMA/100
[    2.771773] ata1.01: 234441648 sectors, multi 16: LBA48 
[    2.832206] usb 1-7: new high speed USB device using ehci_hcd and address 3
[    2.940288] ata1.00: configured for UDMA/66
[    2.977332] usb 1-7: configuration #1 chosen from 1 choice
[    2.977551] hub 1-7:1.0: USB hub found
[    2.977787] hub 1-7:1.0: 4 ports detected
[    2.979602] ata1.01: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    2.979604] ata1.01: configured for UDMA/100
[    2.979610] scsi1 : ata_piix
[    3.146399] ATA: abnormal status 0x7F on port 0x00010177
[    3.147138] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DRU-800A  KY01 PQ: 0 ANSI: 5
[    3.147297] scsi 0:0:1:0: Direct-Access     ATA      ST3120814A       2AAA PQ: 0 ANSI: 5
[    3.147999] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[    3.148007] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.148010] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.148023] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.148043] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000e480
[    3.148092] usb usb2: configuration #1 chosen from 1 choice
[    3.148109] hub 2-0:1.0: USB hub found
[    3.148112] hub 2-0:1.0: 2 ports detected
[    3.152933] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    3.153725] sda: Write Protect is off
[    3.153726] sda: Mode Sense: 00 3a 00 00
[    3.155410] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.157007] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    3.158114] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    3.158115] Uniform CD-ROM driver Revision: 3.20
[    3.158136] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.158139] sda: Write Protect is off
[    3.158140] sda: Mode Sense: 00 3a 00 00
[    3.158148] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.158150]  sda: sda1
[    3.177137] sd 0:0:1:0: Attached scsi disk sda
[    3.178992] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    3.179005] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    3.255709] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 20
[    3.255717] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.255720] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.255733] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.255754] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000e800
[    3.255803] usb usb3: configuration #1 chosen from 1 choice
[    3.255817] hub 3-0:1.0: USB hub found
[    3.255820] hub 3-0:1.0: 2 ports detected
[    3.307851] usb 1-7.3: new high speed USB device using ehci_hcd and address 4
[    3.363546] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[    3.363552] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.363554] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.363569] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.363590] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000e880
[    3.363637] usb usb4: configuration #1 chosen from 1 choice
[    3.363651] hub 4-0:1.0: USB hub found
[    3.363656] hub 4-0:1.0: 2 ports detected
[    3.417860] usb 1-7.3: configuration #1 chosen from 1 choice
[    3.471397] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
[    3.471403] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.471405] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.471416] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.471436] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000ec00
[    3.471484] usb usb5: configuration #1 chosen from 1 choice
[    3.471497] hub 5-0:1.0: USB hub found
[    3.471500] hub 5-0:1.0: 2 ports detected
[    3.579321] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 22
[    3.628971] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[ff6ff800-ff6fffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.629020] ahci 0000:00:1f.2: version 2.1
[    3.629041] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
[    3.659101] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    3.848175] usb 2-2: configuration #1 chosen from 1 choice
[    3.982677] usbcore: registered new interface driver hiddev
[    3.996041] input: Logitech USB Receiver as /class/input/input1
[    3.996048] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-2
[    4.024010] input: Logitech USB Receiver as /class/input/input2
[    4.024131] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[    4.024136] usbcore: registered new interface driver usbhid
[    4.024138] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    4.633812] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.633816] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    4.633818] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part 
[    4.633864] ata3: SATA max UDMA/133 cmd 0xf8864900 ctl 0x00000000 bmdma 0x00000000 irq 23
[    4.633899] ata4: SATA max UDMA/133 cmd 0xf8864980 ctl 0x00000000 bmdma 0x00000000 irq 23
[    4.633934] ata5: SATA max UDMA/133 cmd 0xf8864a00 ctl 0x00000000 bmdma 0x00000000 irq 23
[    4.633968] ata6: SATA max UDMA/133 cmd 0xf8864a80 ctl 0x00000000 bmdma 0x00000000 irq 23
[    4.633974] scsi2 : ahci
[    4.905529] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000f4da9d]
[    5.121155] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.121699] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[    5.121701] ata3.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    5.121702] ata3.00: 488397168 sectors, multi 16: LBA48 
[    5.122291] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[    5.122292] ata3.00: configured for UDMA/133
[    5.122297] scsi3 : ahci
[    5.608502] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   35.572408] ata4.00: qc timeout (cmd 0xec)
[   35.572412] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x104)
[   43.545767] ata4: port is slow to respond, please be patient (Status 0x80)
[   66.530983] ata4: port failed to respond (30 secs, Status 0x80)
[   66.530986] ata4: COMRESET failed (device not ready)
[   66.530989] ata4: hardreset failed, retrying in 5 secs
[   72.399147] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   72.399211] ata4.00: ATA-6: Config  Disk, RGL10364, max UDMA/133
[   72.399213] ata4.00: 640 sectors, multi 1: LBA 
[   72.399278] ata4.00: configured for UDMA/133
[   72.399285] scsi4 : ahci
[   72.882498] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   72.883036] ata5.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   72.883038] ata5.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   72.883040] ata5.00: 488397168 sectors, multi 16: LBA48 
[   72.883641] ata5.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   72.883642] ata5.00: configured for UDMA/133
[   72.883646] scsi5 : ahci
[   73.198066] ata6: SATA link down (SStatus 0 SControl 300)
[   73.198141] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   73.198182] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   73.198188] sdb: Write Protect is off
[   73.198189] sdb: Mode Sense: 00 3a 00 00
[   73.198197] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   73.198225] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   73.198230] sdb: Write Protect is off
[   73.198231] sdb: Mode Sense: 00 3a 00 00
[   73.198240] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   73.198241]  sdb: sdb1 sdb2 sdb3 sdb4
[   73.217350] sd 2:0:0:0: Attached scsi disk sdb
[   73.217372] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   73.217646] scsi 3:0:0:0: Direct-Access     ATA      Config  Disk     RGL1 PQ: 0 ANSI: 5
[   73.217672] SCSI device sdc: 640 512-byte hdwr sectors (0 MB)
[   73.217677] sdc: Write Protect is off
[   73.217678] sdc: Mode Sense: 00 3a 00 00
[   73.217685] SCSI device sdc: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   73.217708] SCSI device sdc: 640 512-byte hdwr sectors (0 MB)
[   73.217712] sdc: Write Protect is off
[   73.217713] sdc: Mode Sense: 00 3a 00 00
[   73.217721] SCSI device sdc: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   73.217723]  sdc: unknown partition table
[   73.218194] sd 3:0:0:0: Attached scsi disk sdc
[   73.218212] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   73.218444] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   73.218469] SCSI device sdd: 488397168 512-byte hdwr sectors (250059 MB)
[   73.218474] sdd: Write Protect is off
[   73.218475] sdd: Mode Sense: 00 3a 00 00
[   73.218484] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   73.218506] SCSI device sdd: 488397168 512-byte hdwr sectors (250059 MB)
[   73.218510] sdd: Write Protect is off
[   73.218511] sdd: Mode Sense: 00 3a 00 00
[   73.218521] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   73.218523]  sdd: sdd1 sdd2 sdd3 sdd4
[   73.227402] sd 4:0:0:0: Attached scsi disk sdd
[   73.227419] sd 4:0:0:0: Attached scsi generic sg4 type 0
[   73.301028] md: md1 stopped.
[   73.509465] md: md1 stopped.
[   73.546351] md: bind<sdd2>
[   73.546442] md: bind<sdb2>
[   73.550543] raid1: raid set md1 active with 1 out of 1 mirrors
[   73.623855] kjournald starting.  Commit interval 5 seconds
[   73.623862] EXT3-fs: mounted filesystem with ordered data mode.
[   79.877122] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   79.914832] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   79.988939] input: PC Speaker as /class/input/input3
[   80.041214] iTCO_vendor_support: vendor-support=0
[   80.041765] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   80.041817] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   80.041837] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   80.057015] intel_rng: FWH not detected
[   80.261566] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[   80.261577] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   80.261597] sky2 0000:03:00.0: v1.13 addr 0xff8fc000 irq 17 Yukon-EC (0xb6) rev 2
[   80.261868] sky2 eth0: addr 00:18:f3:ab:82:d8
[   80.261883] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   80.261889] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   80.261905] sky2 0000:02:00.0: v1.13 addr 0xff7fc000 irq 16 Yukon-EC (0xb6) rev 2
[   80.262025] sky2 eth1: addr 00:18:f3:ab:79:de
[   80.413164] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 17
[   80.413176] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   80.641323] wmaster0: Selected rate control algorithm 'simple'
[   80.685632] wiphy0: hwaddr 00:15:af:0a:b1:d0, rtl8187 V1 + rtl8225z2
[   80.685642] usbcore: registered new interface driver rtl8187
[   81.288328] lp: driver loaded but no devices found
[   81.751848] EXT3 FS on md1, internal journal
[   81.857190] md: md0 stopped.
[   81.922698] md: bind<sdd1>
[   81.922800] md: bind<sdb1>
[   81.995124] raid1: raid set md0 active with 1 out of 1 mirrors
[   81.996374] md: md2 stopped.
[   82.046461] md: bind<sdd3>
[   82.046553] md: bind<sdb3>
[   82.064662] raid1: raid set md2 active with 1 out of 1 mirrors
[   82.064754] md: md3 stopped.
[   82.086277] md: bind<sdd4>
[   82.086364] md: bind<sdb4>
[   82.105231] raid1: raid set md3 active with 1 out of 1 mirrors
[   82.349398] kjournald starting.  Commit interval 5 seconds
[   82.354093] EXT3 FS on md0, internal journal
[   82.354095] EXT3-fs: mounted filesystem with ordered data mode.
[   82.369605] kjournald starting.  Commit interval 5 seconds
[   82.374132] EXT3 FS on md3, internal journal
[   82.374134] EXT3-fs: mounted filesystem with ordered data mode.
[   82.384462] Adding 1951800k swap on /dev/disk/by-uuid/817a9fa4-d544-4f80-ad12-1ee7def56fab.  Priority:-1 extents:1 across:1951800k

```

---

