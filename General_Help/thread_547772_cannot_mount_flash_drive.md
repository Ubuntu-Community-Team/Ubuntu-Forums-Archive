---
title: "cannot mount flash drive"
date: 2007-09-10
forum: General Help
---

### Post by notjohn101 on 2007-09-10
so one day i plug in my flash drive like i always do but i got this error

> Cannot mount volume.

Invalid mount option when attempting to mount the volume.

the flash drive is formated as fat32

thanks for the help

p.s. this also happens on my brothers psp or any other removable media w/ fat32

---

### Post by diatribe on 2007-09-10
what is the output of dmesg

---

### Post by notjohn101 on 2007-09-10
> boys@boys-linux:~$ dmesg | tail
[ 3836.220004] sdd: Mode Sense: 23 00 00 00
[ 3836.220007] sdd: assuming drive cache: write through
[ 3836.223089] SCSI device sdd: 4028416 512-byte hdwr sectors (2063 MB)
[ 3836.223707] sdd: Write Protect is off
[ 3836.223710] sdd: Mode Sense: 23 00 00 00
[ 3836.223712] sdd: assuming drive cache: write through
[ 3836.223715]  sdd: sdd1
[ 3836.281920] sd 6:0:0:0: Attached scsi removable disk sdd
[ 3836.281977] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 3836.640215] VFS: Can't find ext3 filesystem on dev sdd1.
boys@boys-linux:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fef0000 end: 000000007fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fff0000 size: 0000000000003000 end: 000000007fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000007fff3000 size: 000000000000d000 end: 0000000080000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4d60
[    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524272
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524272
[    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f6710
[    0.000000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x7fff3040
[    0.000000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x7fff30c0
[    0.000000] ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x7fff6800
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20040311) @ 0x7fff68d0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20040311) @ 0x7fff6d60
[    0.000000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Detected 3434.350 MHz processor.
[   30.558715] Built 1 zonelists.  Total pages: 520177
[   30.558719] Kernel command line: root=UUID=b3fb6933-e25e-434b-88f1-a5d1add88a6c ro quiet splash rootflags=data=writeback elevator=cfq
[   30.558861] mapped APIC to ffffd000 (fee00000)
[   30.558863] mapped IOAPIC to ffffc000 (fec00000)
[   30.558866] Enabling fast FPU save and restore... done.
[   30.558868] Enabling unmasked SIMD FPU exception support... done.
[   30.558876] Initializing CPU#0
[   30.558932] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   30.560794] Console: colour VGA+ 80x25
[   30.561101] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   30.561409] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   30.627942] Memory: 2067764k/2097088k available (1992k kernel code, 27928k reserved, 893k data, 328k init, 1179584k highmem)
[   30.627951] virtual kernel memory layout:
[   30.627952]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   30.627953]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   30.627954]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   30.627955]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   30.627956]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   30.627957]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   30.627958]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   30.627961] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.705389] Calibrating delay using timer specific routine.. 6805.18 BogoMIPS (lpj=13610368)
[   30.705428] Security Framework v1.0.0 initialized
[   30.705433] SELinux:  Disabled at boot.
[   30.705448] Mount-cache hash table entries: 512
[   30.705571] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001
[   30.705578] monitor/mwait feature present.
[   30.705580] using mwait in idle threads.
[   30.705586] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   30.705589] CPU: L2 cache: 2048K
[   30.705591] CPU: Physical Processor ID: 0
[   30.705593] CPU: Processor Core ID: 0
[   30.705594] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000e49d 00000000 00000001
[   30.705605] Compat vDSO mapped to ffffe000.
[   30.705608] Remapping vsyscall page to ffffe000
[   30.705622] Checking 'hlt' instruction... OK.
[   30.721329] SMP alternatives: switching to UP code
[   30.721675] Early unpacking initramfs... done
[   30.967913] ACPI: Core revision 20060707
[   30.972905] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   30.994059] CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04
[   30.994077] SMP alternatives: switching to SMP code
[   30.994177] Booting processor 1/1 eip 3000
[   31.004605] Initializing CPU#1
[   31.081415] Calibrating delay using timer specific routine.. 6800.85 BogoMIPS (lpj=13601718)
[   31.081423] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001
[   31.081428] monitor/mwait feature present.
[   31.081433] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   31.081435] CPU: L2 cache: 2048K
[   31.081437] CPU: Physical Processor ID: 0
[   31.081438] CPU: Processor Core ID: 1
[   31.081440] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000e49d 00000000 00000001
[   31.081859] CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04
[   31.081889] Total of 2 processors activated (13606.04 BogoMIPS).
[   31.082014] ENABLING IO-APIC IRQs
[   31.082181] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   31.227880] checking TSC synchronization across 2 CPUs: passed.
[    0.003962] Brought up 2 CPUs
[    0.285365] migration_cost=1041
[    0.285621] Booting paravirtualized kernel on bare hardware
[    0.285694] Time: 12:31:01  Date: 08/10/107
[    0.285722] NET: Registered protocol family 16
[    0.285799] EISA bus registered
[    0.285804] ACPI: bus type pci registered
[    0.309456] PCI: PCI BIOS revision 2.10 entry at 0xfacf0, last bus=2
[    0.309458] PCI: Using configuration type 1
[    0.309460] Setting up standard PCI resources
[    0.323121] ACPI: Interpreter enabled
[    0.323124] ACPI: Using IOAPIC for interrupt routing
[    0.323668] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.323672] PCI: Probing PCI hardware (bus 00)
[    0.324225] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.324228] PCI quirk: region 1080-10bf claimed by ICH4 GPIO
[    0.324444] Boot video device is 0000:01:00.0
[    0.324630] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[    0.324695] PCI: Transparent bridge - 0000:00:1e.0
[    0.324721] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.330602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.332956] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.333176] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
[    0.333392] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.333612] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.333829] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.334044] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.334262] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.334477] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.334651] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.334662] pnp: PnP ACPI init
[    0.336532] pnp: PnP ACPI: found 8 devices
[    0.336538] PnPBIOS: Disabled by ACPI PNP
[    0.336578] PCI: Using ACPI for IRQ routing
[    0.336581] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.351773] NET: Registered protocol family 8
[    0.351775] NET: Registered protocol family 20
[    0.352430] PCI: Bridge: 0000:00:01.0
[    0.352433]   IO window: disabled.
[    0.352437]   MEM window: ec000000-eeffffff
[    0.352441]   PREFETCH window: d0000000-dfffffff
[    0.352445] PCI: Bridge: 0000:00:1e.0
[    0.352448]   IO window: a000-afff
[    0.352453]   MEM window: ef000000-ef0fffff
[    0.352457]   PREFETCH window: e8000000-ebffffff
[    0.352473] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.352502] NET: Registered protocol family 2
[    0.388967] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.389091] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.389592] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.389842] TCP: Hash tables configured (established 131072 bind 65536)
[    0.389845] TCP reno registered
[    0.400931] checking if image is initramfs... it is
[    0.884892] Freeing initrd memory: 6998k freed
[    0.885558] audit: initializing netlink socket (disabled)
[    0.885574] audit(1189427461.632:1): initialized
[    0.885741] highmem bounce pool size: 64 pages
[    0.885897] VFS: Disk quotas dquot_6.5.1
[    0.885920] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.885975] io scheduler noop registered
[    0.885979] io scheduler anticipatory registered
[    0.885982] io scheduler deadline registered
[    0.885999] io scheduler cfq registered (default)
[    0.886315] isapnp: Scanning for PnP cards...
[    1.234301] isapnp: No Plug & Play device found
[    1.268288] Real Time Clock Driver v1.12ac
[    1.268357] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.269148] mice: PS/2 mouse device common for all mice
[    1.269943] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.270132] input: Macintosh mouse button emulation as /class/input/input0
[    1.270183] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.270188] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.270510] PNP: No PS/2 controller found. Probing ports directly.
[    1.270729] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.270735] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.270843] EISA: Probing bus 0 at eisa.0
[    1.270853] Cannot allocate resource for EISA slot 1
[    1.270885] EISA: Detected 0 cards.
[    1.300653] TCP cubic registered
[    1.300670] NET: Registered protocol family 1
[    1.300698] Starting balanced_irq
[    1.300713] Using IPI No-Shortcut mode
[    1.300786] ACPI: (supports S0 S1 S4 S5)
[    1.300827]   Magic number: 7:518:531
[    1.301063] Freeing unused kernel memory: 328k freed
[    1.302226] Time: tsc clocksource has been installed.
[    2.507137] Capability LSM initialized
[    2.539296] ACPI: Fan [FAN] (on)
[    2.542722] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.542763] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.542771] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.543521] ACPI: Thermal Zone [THRM] (22 C)
[    2.881331] SCSI subsystem initialized
[    2.893022] libata version 2.20 loaded.
[    2.895998] ata_piix 0000:00:1f.1: version 2.10ac1
[    2.896016] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 16
[    2.896032] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    2.896088] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[    2.896118] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[    2.896137] scsi0 : ata_piix
[    2.915682] usbcore: registered new interface driver usbfs
[    2.915702] usbcore: registered new interface driver hub
[    2.915726] usbcore: registered new device driver usb
[    2.916471] USB Universal Host Controller Interface driver v3.0
[    2.950202] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[    2.950205] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.958236] Floppy drive(s): fd0 is 1.44M
[    2.978301] FDC 0 is a post-1991 82077
[    3.058136] ata1.00: ata_hpa_resize 1: sectors = 39874367, hpa_sectors = 39876480
[    3.058142] ata1.00: Host Protected Area detected.
[    3.058144]      current size : 39874367 sectors (20415 MB)
[    3.058145]      native  size : 39876480 sectors (20416 MB)
[    3.065874] ata1.00: Native size increased to 39876480 sectors
[    3.065877] ata1.00: ATA-6: ST320410A, 3.34, max UDMA/100
[    3.065879] ata1.00: 39876480 sectors, multi 16: LBA 
[    3.077978] ata1.00: ata_hpa_resize 1: sectors = 39876480, hpa_sectors = 39876480
[    3.077982] ata1.00: configured for UDMA/100
[    3.077994] scsi1 : ata_piix
[    3.299695] ata2.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.299699] ata2.00: ATA-6: ST380013A, 3.54, max UDMA/100
[    3.299703] ata2.00: 156301488 sectors, multi 16: LBA48 
[    3.307630] ata2.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.307634] ata2.00: configured for UDMA/100
[    3.307740] scsi 0:0:0:0: Direct-Access     ATA      ST320410A        3.34 PQ: 0 ANSI: 5
[    3.308153] scsi 1:0:0:0: Direct-Access     ATA      ST380013A        3.54 PQ: 0 ANSI: 5
[    3.308480] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    3.308496] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 16
[    3.308511] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.308553] ata3: SATA max UDMA/133 cmd 0x0001c000 ctl 0x0001c402 bmdma 0x0001d000 irq 16
[    3.308590] ata4: SATA max UDMA/133 cmd 0x0001c800 ctl 0x0001cc02 bmdma 0x0001d008 irq 16
[    3.308602] scsi2 : ata_piix
[    3.470239] ata3.00: ata_hpa_resize 1: sectors = 78163247, hpa_sectors = 78165360
[    3.470245] ata3.00: Host Protected Area detected.
[    3.470247]      current size : 78163247 sectors (40019 MB)
[    3.470249]      native  size : 78165360 sectors (40020 MB)
[    3.477730] ata3.00: Native size increased to 78165360 sectors
[    3.477732] ata3.00: ATA-7: WDC WD400JD-22LSA0, 06.01D06, max UDMA/133
[    3.477735] ata3.00: 78165360 sectors, multi 16: LBA48 
[    3.485766] ata3.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[    3.485770] ata3.00: configured for UDMA/133
[    3.485779] scsi3 : ata_piix
[    3.650181] ATA: abnormal status 0x7F on port 0x0001c807
[    3.650268] scsi 2:0:0:0: Direct-Access     ATA      WDC WD400JD-22LS 06.0 PQ: 0 ANSI: 5
[    3.650769] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 17
[    3.650787] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.650792] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.650906] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.650939] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    3.650948] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xef100000
[    3.654780] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.654872] usb usb1: configuration #1 chosen from 1 choice
[    3.654901] hub 1-0:1.0: USB hub found
[    3.654907] hub 1-0:1.0: 8 ports detected
[    3.659193] SCSI device sda: 39876480 512-byte hdwr sectors (20417 MB)
[    3.659206] sda: Write Protect is off
[    3.659208] sda: Mode Sense: 00 3a 00 00
[    3.659225] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.659279] SCSI device sda: 39876480 512-byte hdwr sectors (20417 MB)
[    3.659289] sda: Write Protect is off
[    3.659292] sda: Mode Sense: 00 3a 00 00
[    3.659308] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.659310]  sda: sda1 sda2 < sda5 > sda3
[    3.705652] sd 0:0:0:0: Attached scsi disk sda
[    3.705705] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[    3.705717] sdb: Write Protect is off
[    3.705720] sdb: Mode Sense: 00 3a 00 00
[    3.705737] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.705777] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[    3.705787] sdb: Write Protect is off
[    3.705790] sdb: Mode Sense: 00 3a 00 00
[    3.705823] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.705827]  sdb: sdb1 sdb2 sdb3
[    3.714102] sd 1:0:0:0: Attached scsi disk sdb
[    3.714143] SCSI device sdc: 78165360 512-byte hdwr sectors (40021 MB)
[    3.714154] sdc: Write Protect is off
[    3.714156] sdc: Mode Sense: 00 3a 00 00
[    3.714172] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.714208] SCSI device sdc: 78165360 512-byte hdwr sectors (40021 MB)
[    3.714218] sdc: Write Protect is off
[    3.714221] sdc: Mode Sense: 00 3a 00 00
[    3.714237] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.714240]  sdc: sdc1
[    3.725710] sd 2:0:0:0: Attached scsi disk sdc
[    3.731116] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.731138] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    3.731156] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    3.759230] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 18
[    3.759243] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.759247] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.759270] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.759299] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bc00
[    3.759383] usb usb2: configuration #1 chosen from 1 choice
[    3.759407] hub 2-0:1.0: USB hub found
[    3.759414] hub 2-0:1.0: 2 ports detected
[    3.862109] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.862126] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.862129] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.862157] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.862182] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b000
[    3.862267] usb usb3: configuration #1 chosen from 1 choice
[    3.862292] hub 3-0:1.0: USB hub found
[    3.862298] hub 3-0:1.0: 2 ports detected
[    3.965022] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 16
[    3.965033] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.965038] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.965069] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.965090] uhci_hcd 0000:00:1d.2: irq 16, io base 0x0000b400
[    3.965169] usb usb4: configuration #1 chosen from 1 choice
[    3.965193] hub 4-0:1.0: USB hub found
[    3.965198] hub 4-0:1.0: 2 ports detected
[    4.064870] Attempting manual resume
[    4.064874] swsusp: Resume From Partition 8:5
[    4.064876] PM: Checking swsusp image.
[    4.065092] PM: Resume from disk failed.
[    4.068046] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 18
[    4.068056] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.068059] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.068083] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    4.068103] uhci_hcd 0000:00:1d.3: irq 18, io base 0x0000b800
[    4.068184] usb usb5: configuration #1 chosen from 1 choice
[    4.068210] hub 5-0:1.0: USB hub found
[    4.068217] hub 5-0:1.0: 2 ports detected
[    4.087596] kjournald starting.  Commit interval 5 seconds
[    4.087604] EXT3-fs: mounted filesystem with writeback data mode.
[    4.171246] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[    4.190100] e100: eth0: e100_probe: addr 0xef000000, irq 20, MAC addr 00:0F:EA:45:EA:03
[    4.547053] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.730930] usb 3-1: configuration #1 chosen from 1 choice
[    4.968145] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    5.143468] usb 3-2: configuration #1 chosen from 1 choice
[    5.384130] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    5.550107] usb 4-1: configuration #1 chosen from 1 choice
[    5.553015] hub 4-1:1.0: USB hub found
[    5.555953] hub 4-1:1.0: 2 ports detected
[    5.864624] usb 4-1.1: new full speed USB device using uhci_hcd and address 3
[    5.973513] usb 4-1.1: configuration #1 chosen from 1 choice
[    6.177249] usb 4-1.2: new full speed USB device using uhci_hcd and address 4
[    6.305927] usb 4-1.2: configuration #1 chosen from 1 choice
[   14.937652] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   15.930122] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.950949] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.964083] iTCO_vendor_support: vendor-support=0
[   15.965058] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   15.965120] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x1060)
[   15.965151] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.025515] Linux agpgart interface v0.102 (c) Dave Jones
[   16.130157] agpgart: Detected an Intel 865 Chipset.
[   16.136770] agpgart: AGP aperture is 128M @ 0xe0000000
[   16.150908] intel_rng: FWH not detected
[   16.214043] input: PC Speaker as /class/input/input1
[   16.401966] Linux video capture interface: v2.00
[   16.460785] nvidia: module license 'NVIDIA' taints kernel.
[   16.709045] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[   16.710169] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   16.800655] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7204
[   16.800675] usbcore: registered new interface driver hiddev
[   16.812313] ivtv:  ==================== START INIT IVTV ====================
[   16.812317] ivtv:  version 0.10.1 (tagged release) loading
[   16.812318] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
[   16.812320] ivtv:  In case of problems please include the debug info between
[   16.812322] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   16.812324] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   16.812391] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   16.812466] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 21
[   16.812476] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   16.866990] input: Logitech USB Receiver as /class/input/input2
[   16.867026] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   16.901469] input: Logitech USB Receiver as /class/input/input3
[   16.901579] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   16.901599] usbcore: registered new interface driver usbhid
[   16.901603] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   17.070559] drivers/usb/class/usblp.c: usblp1: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x043D pid 0x0014
[   17.070570] usbcore: registered new interface driver usblp
[   17.070573] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   17.427668] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   17.638268] ivtv0: Encoder revision: 0x02050032
[   17.638272] ivtv0: Recommended firmware version is 0x02060039.
[   17.700090] tveeprom 0-0050: Hauppauge model 26582, rev E6B2, serial# 10297762
[   17.700093] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   17.700096] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   17.700099] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   17.700101] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   17.700103] tveeprom 0-0050: has no radio, has no IR receiver, has no IR transmitter
[   17.700106] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   17.746872] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   17.795840] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   22.539223] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   22.658683] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   22.722599] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   22.722768] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   22.722967] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   22.723049] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   22.723270] tuner 0-0061: type set to 50 (TCL 2002N)
[   23.107427] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   23.107462] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 22
[   23.107481] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
[   23.120488] ivtv:  ====================  END INIT IVTV  ====================
[   23.243715] fuse init (API version 7.8)
[   23.298931] lp: driver loaded but no devices found
[   23.315215] ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 17 (level, low) -> IRQ 23
[   23.472398] it87: Found IT8712F chip at 0x290, revision 8
[   23.472405] it87: in3 is VCC (+5V)
[   23.583902] Adding 473876k swap on /dev/disk/by-uuid/e65b35d2-fe69-4a82-a8d2-73b0addd807f.  Priority:-1 extents:1 across:473876k
[   23.704718] EXT3 FS on sda1, internal journal
[   23.952970] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   23.983339] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   23.985452] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   24.089180] kjournald starting.  Commit interval 5 seconds
[   24.089549] EXT3 FS on sda3, internal journal
[   24.089555] EXT3-fs: mounted filesystem with ordered data mode.
[   25.906703] NET: Registered protocol family 17
[   29.956157] Using specific hotkey driver
[   30.030790] ibm_acpi: ec object not found
[   30.104933] No dock devices found.
[   30.147880] input: Power Button (FF) as /class/input/input4
[   30.148011] ACPI: Power Button (FF) [PWRF]
[   30.148731] input: Power Button (CM) as /class/input/input5
[   30.148852] ACPI: Power Button (CM) [PWRB]
[   30.199621] pcc_acpi: loading...
[   33.403605] NVRM: not using NVAGP, an AGPGART backend is loaded!
[   33.791468] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[   33.791525] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[   33.791549] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!
[   34.515343] ppdev: user-space parallel port driver
[   34.758266] NET: Registered protocol family 10
[   34.758352] lo: Disabled Privacy Extensions
[   45.490117] eth0: no IPv6 routers present
[ 3538.984916] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 3539.127066] usb 1-1: configuration #1 chosen from 1 choice
[ 3539.217727] usbcore: registered new interface driver libusual
[ 3539.229671] Initializing USB Mass Storage driver...
[ 3539.229767] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3539.229827] usb-storage: device found at 5
[ 3539.229830] usbcore: registered new interface driver usb-storage
[ 3539.229834] USB Mass Storage support registered.
[ 3539.229837] usb-storage: waiting for device to settle before scanning
[ 3544.179836] usb-storage: device scan complete
[ 3544.227579] scsi 4:0:0:0: Direct-Access     Memorex  TRAVELDRIVE 005B PMAP PQ: 0 ANSI: 0 CCS
[ 3544.471787] SCSI device sdd: 4028416 512-byte hdwr sectors (2063 MB)
[ 3544.472400] sdd: Write Protect is off
[ 3544.472404] sdd: Mode Sense: 23 00 00 00
[ 3544.472406] sdd: assuming drive cache: write through
[ 3544.475493] SCSI device sdd: 4028416 512-byte hdwr sectors (2063 MB)
[ 3544.476109] sdd: Write Protect is off
[ 3544.476112] sdd: Mode Sense: 23 00 00 00
[ 3544.476115] sdd: assuming drive cache: write through
[ 3544.476118]  sdd: sdd1
[ 3544.534318] sd 4:0:0:0: Attached scsi removable disk sdd
[ 3544.534376] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 3544.873573] VFS: Can't find ext3 filesystem on dev sdd1.
[ 3711.075617] usb 1-1: USB disconnect, address 5
[ 3716.866235] usb 1-2: new high speed USB device using ehci_hcd and address 6
[ 3717.008262] usb 1-2: configuration #1 chosen from 1 choice
[ 3717.008502] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3717.008550] usb-storage: device found at 6
[ 3717.008555] usb-storage: waiting for device to settle before scanning
[ 3721.958634] usb-storage: device scan complete
[ 3722.006123] scsi 5:0:0:0: Direct-Access     Memorex  TRAVELDRIVE 005B PMAP PQ: 0 ANSI: 0 CCS
[ 3722.250454] SCSI device sdd: 4028416 512-byte hdwr sectors (2063 MB)
[ 3722.251069] sdd: Write Protect is off
[ 3722.251073] sdd: Mode Sense: 23 00 00 00
[ 3722.251076] sdd: assuming drive cache: write through
[ 3722.254162] SCSI device sdd: 4028416 512-byte hdwr sectors (2063 MB)
[ 3722.254779] sdd: Write Protect is off
[ 3722.254782] sdd: Mode Sense: 23 00 00 00
[ 3722.254784] sdd: assuming drive cache: write through
[ 3722.254787]  sdd: sdd1
[ 3722.311994] sd 5:0:0:0: Attached scsi removable disk sdd
[ 3722.312056] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 3722.653483] VFS: Can't find ext3 filesystem on dev sdd1.
[ 3828.103034] usb 1-2: USB disconnect, address 6
[ 3830.838370] usb 1-2: new high speed USB device using ehci_hcd and address 7
[ 3830.980396] usb 1-2: configuration #1 chosen from 1 choice
[ 3830.980670] scsi6 : SCSI emulation for USB Mass Storage devices
[ 3830.980720] usb-storage: device found at 7
[ 3830.980725] usb-storage: waiting for device to settle before scanning
[ 3835.927311] usb-storage: device scan complete
[ 3835.974689] scsi 6:0:0:0: Direct-Access     Memorex  TRAVELDRIVE 005B PMAP PQ: 0 ANSI: 0 CCS
[ 3836.219382] SCSI device sdd: 4028416 512-byte hdwr sectors (2063 MB)
[ 3836.219997] sdd: Write Protect is off
[ 3836.220004] sdd: Mode Sense: 23 00 00 00
[ 3836.220007] sdd: assuming drive cache: write through
[ 3836.223089] SCSI device sdd: 4028416 512-byte hdwr sectors (2063 MB)
[ 3836.223707] sdd: Write Protect is off
[ 3836.223710] sdd: Mode Sense: 23 00 00 00
[ 3836.223712] sdd: assuming drive cache: write through
[ 3836.223715]  sdd: sdd1
[ 3836.281920] sd 6:0:0:0: Attached scsi removable disk sdd
[ 3836.281977] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 3836.640215] VFS: Can't find ext3 filesystem on dev sdd1.
boys@boys-linux:~$

i think this line has something to do with it 

[ 3836.640215] VFS: Can't find ext3 filesystem on dev sdd1.

---

### Post by notjohn101 on 2007-09-10
bump

---

### Post by notjohn101 on 2007-09-10
bump i really need this to work

---

### Post by Arwen on 2007-09-10
Do "lsusb" and then "fdisk -l".

---

### Post by Arwen on 2007-09-10
Paste the output and take a look at this->[http://forums.devshed.com/linux-help-33/cannot-mount-usb-flash-drive-4-device-files-and-error-339719.html](http://forums.devshed.com/linux-help-33/cannot-mount-usb-flash-drive-4-device-files-and-error-339719.html)

---

### Post by notjohn101 on 2007-09-10
ok thanks
> boys@boys-linux:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 043d:002d Lexmark International, Inc. X70/X73 Scan/Print/Copy
Bus 004 Device 004: ID 043d:0014 Lexmark International, Inc. 
Bus 004 Device 002: ID 043d:0029 Lexmark International, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:7204 Hewlett-Packard DeskJet 36xx
Bus 003 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 12f7:1e23  
Bus 001 Device 001: ID 0000:0000  
boys@boys-linux:~$ 

> boys@boys-linux:~$ fdisk -l

Disk /dev/sdd: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        7868     2014192    b  W95 FAT32
boys@boys-linux:~

---

### Post by notjohn101 on 2007-09-10
umm haha

i fixed it

turns out i might of added a /dev/sdd (my flash drive) to fstab....and added incorrect options so i just deleted and let it automount and it works

but thats for the help anyway

---

### Post by Arwen on 2007-09-10
Great!
U Welcome:-)

---

### Post by Arwen on 2007-09-11
Believe it or not.I had exactly the same problem today and I tried 3 different flash drives.I changed fstab till I freaked out,shut down and then logged in again and it by miracle could be finally mounted.But it's still a weird problem and if anyone has any idea what is causing this let us know plz.:-k

---

