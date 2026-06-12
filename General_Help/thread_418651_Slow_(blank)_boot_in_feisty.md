---
title: "Slow (blank) boot in feisty"
date: 2007-04-22
forum: General Help
---

### Post by t1m on 2007-04-22
Hi,
I installed Feisty fawn on thursday (April 19 07). When I turn on my computer I see grub loading, then somthing like "starting up...", then I get a blank screen for about 2-3 minuets, and finally I see the login screen.

I tried [this]("http://ubuntuforums.org/showthread.php?t=416719&highlight=very+slow+boot"), but it didn't help.

Here's what I get with *dmesg* in Konsole:
```

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000027d40000 end: 0000000027e40000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000027e40000 size: 0000000000010000 end: 0000000027e50000 type: 3
[    0.000000] copy_e820_map() start: 0000000027e50000 size: 00000000000b0000 end: 0000000027f00000 type: 4
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000027e40000 (usable)
[    0.000000]  BIOS-e820: 0000000027e40000 - 0000000027e50000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000027e50000 - 0000000027f00000 (ACPI NVS)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 638MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 163392) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   163392
[    0.000000]   HighMem    163392 ->   163392
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   163392
[    0.000000] On node 0 totalpages: 163392
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1244 pages used for memmap
[    0.000000]   Normal zone: 158052 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f70b0
[    0.000000] ACPI: RSDT (v001 GATEWA N1CPP057 0x20021016 MSFT 0x00000097) @ 0x27e40000
[    0.000000] ACPI: FADT (v002 GATEWA N1CPP057 0x20021016 MSFT 0x00000097) @ 0x27e40200
[    0.000000] ACPI: MADT (v001 GATEWA N1CPP057 0x20021016 MSFT 0x00000097) @ 0x27e40300
[    0.000000] ACPI: DSDT (v001 GATEWA N1CPP057 0x0000010a MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 27f00000:d8100000)
[    0.000000] Detected 1799.993 MHz processor.
[   12.996510] Built 1 zonelists.  Total pages: 162116
[   12.996518] Kernel command line: root=UUID=25f568cc-e990-4498-8028-d923027e6619 ro quiet splash
[   12.996749] mapped APIC to ffffd000 (fee00000)
[   12.996753] mapped IOAPIC to ffffc000 (fec00000)
[   12.996757] Enabling fast FPU save and restore... done.
[   12.996762] Enabling unmasked SIMD FPU exception support... done.
[   12.996777] Initializing CPU#0
[   12.996866] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   12.998606] Console: colour VGA+ 80x25
[   12.999534] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.001036] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.020989] Memory: 636608k/653568k available (1992k kernel code, 16388k reserved, 893k data, 328k init, 0k highmem)
[   13.021003] virtual kernel memory layout:
[   13.021005]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   13.021007]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.021008]     vmalloc : 0xe8800000 - 0xff7fe000   ( 367 MB)
[   13.021010]     lowmem  : 0xc0000000 - 0xe7e40000   ( 638 MB)
[   13.021011]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   13.021013]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   13.021015]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   13.021019] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.100712] Calibrating delay using timer specific routine.. 3603.59 BogoMIPS (lpj=7207183)
[   13.100786] Security Framework v1.0.0 initialized
[   13.100797] SELinux:  Disabled at boot.
[   13.100825] Mount-cache hash table entries: 512
[   13.101080] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   13.101102] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   13.101107] CPU: L2 cache: 128K
[   13.101110] CPU: Hyper-Threading is disabled
[   13.101114] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   13.101135] Compat vDSO mapped to ffffe000.
[   13.101141] Remapping vsyscall page to ffffe000
[   13.101161] Checking 'hlt' instruction... OK.
[   13.116853] SMP alternatives: switching to UP code
[   13.117279] Freeing SMP alternatives: 11k freed
[   13.117650] Early unpacking initramfs... done
[   13.571926] ACPI: Core revision 20060707
[   13.572209] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   13.575273] CPU0: Intel(R) Celeron(R) CPU 1.80GHz stepping 09
[   13.575336] Total of 1 processors activated (3603.59 BogoMIPS).
[   13.575482] ENABLING IO-APIC IRQs
[   13.575693] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.719859] Brought up 1 CPUs
[   13.720303] Booting paravirtualized kernel on bare hardware
[   13.720483] Time: 16:53:15  Date: 03/22/107
[   13.720544] NET: Registered protocol family 16
[   13.720770] EISA bus registered
[   13.720785] ACPI: bus type pci registered
[   13.720900] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   13.720903] PCI: Using configuration type 1
[   13.720906] Setting up standard PCI resources
[   13.741519] ACPI: Interpreter enabled
[   13.741527] ACPI: Using IOAPIC for interrupt routing
[   13.742586] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.742601] PCI: Probing PCI hardware (bus 00)
[   13.743124] Boot video device is 0000:00:02.0
[   13.743474] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   13.743477] * this clock source is slow. If you are sure your timer does not have
[   13.743478] * this bug, please use "acpi_pm_good" to disable the workaround
[   13.743535] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   13.743540] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   13.744002] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   13.744095] PCI: Transparent bridge - 0000:00:1e.0
[   13.744138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.747536] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   13.752685] ACPI: Power Resource [URP1] (off)
[   13.752891] ACPI: Power Resource [FDDP] (off)
[   13.753091] ACPI: Power Resource [LPTP] (off)
[   13.757953] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   13.758620] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   13.759315] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   13.760051] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   13.760715] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   13.761382] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   13.762059] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   13.762723] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   13.763391] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.763418] pnp: PnP ACPI init
[   13.770877] pnp: PnP ACPI: found 13 devices
[   13.770888] PnPBIOS: Disabled by ACPI PNP
[   13.771034] PCI: Using ACPI for IRQ routing
[   13.771040] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.774571] NET: Registered protocol family 8
[   13.774575] NET: Registered protocol family 20
[   13.776405] pnp: 00:0b: ioport range 0x400-0x47f could not be reserved
[   13.776413] pnp: 00:0b: ioport range 0x680-0x6ff has been reserved
[   13.776417] pnp: 00:0b: ioport range 0x480-0x4bf has been reserved
[   13.777430] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   13.777451] PCI: Bridge: 0000:00:1e.0
[   13.777455]   IO window: d000-dfff
[   13.777463]   MEM window: ff800000-ff8fffff
[   13.777469]   PREFETCH window: e6a00000-e6afffff
[   13.777487] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.777537] NET: Registered protocol family 2
[   13.815749] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.816127] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.817853] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.818750] TCP: Hash tables configured (established 131072 bind 65536)
[   13.818757] TCP reno registered
[   13.827843] checking if image is initramfs... it is
[   14.731424] Freeing initrd memory: 6777k freed
[   14.732473] audit: initializing netlink socket (disabled)
[   14.732497] audit(1177260795.816:1): initialized
[   14.732831] VFS: Disk quotas dquot_6.5.1
[   14.732872] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.732982] io scheduler noop registered
[   14.732989] io scheduler anticipatory registered
[   14.732992] io scheduler deadline registered
[   14.733022] io scheduler cfq registered (default)
[   14.733616] isapnp: Scanning for PnP cards...
[   15.087460] isapnp: No Plug & Play device found
[   15.221262] Real Time Clock Driver v1.12ac
[   15.221410] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.221708] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.223963] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.224720] mice: PS/2 mouse device common for all mice
[   15.226638] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.227245] input: Macintosh mouse button emulation as /class/input/input0
[   15.227355] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   15.227364] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.227815] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   15.227821] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   15.230907] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.230919] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.231308] EISA: Probing bus 0 at eisa.0
[   15.231358] EISA: Detected 0 cards.
[   15.261480] TCP cubic registered
[   15.261505] NET: Registered protocol family 1
[   15.261554] Using IPI No-Shortcut mode
[   15.261738] ACPI: (supports S0 S1 S3 S4 S5)
[   15.261820]   Magic number: 3:676:894
[   15.261962]   hash matches device ptyy4
[   15.262592] Freeing unused kernel memory: 328k freed
[   15.265384] Time: tsc clocksource has been installed.
[   15.276553] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.853932] Capability LSM initialized
[   17.431074] ACPI: Processor [CPU1] (supports 8 throttling states)
[   17.431093] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   27.591130] usbcore: registered new interface driver usbfs
[   27.591178] usbcore: registered new interface driver hub
[   27.591243] usbcore: registered new device driver usb
[   27.592809] USB Universal Host Controller Interface driver v3.0
[   27.592904] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.592923] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   27.592929] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   27.593126] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   27.593167] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800
[   27.593391] usb usb1: configuration #1 chosen from 1 choice
[   27.593450] hub 1-0:1.0: USB hub found
[   27.593467] hub 1-0:1.0: 2 ports detected
[   27.698177] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   27.698198] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   27.698204] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   27.698284] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   27.698322] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880
[   27.698500] usb usb2: configuration #1 chosen from 1 choice
[   27.698561] hub 2-0:1.0: USB hub found
[   27.698576] hub 2-0:1.0: 2 ports detected
[   27.789025] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   27.789031] e100: Copyright(c) 1999-2006 Intel Corporation
[   27.805991] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   27.806011] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   27.806017] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   27.806084] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   27.806122] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00
[   27.806322] usb usb3: configuration #1 chosen from 1 choice
[   27.806382] hub 3-0:1.0: USB hub found
[   27.806404] hub 3-0:1.0: 2 ports detected
[   27.914778] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   27.914806] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.914812] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.914883] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   27.914937] ehci_hcd 0000:00:1d.7: debug port 1
[   27.914946] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   27.914964] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa7fc00
[   27.918853] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.919024] usb usb4: configuration #1 chosen from 1 choice
[   27.919088] hub 4-0:1.0: USB hub found
[   27.919108] hub 4-0:1.0: 6 ports detected
[   27.937560] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   27.957933] SCSI subsystem initialized
[   27.967594] libata version 2.20 loaded.
[   28.026125] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   28.049426] e100: eth0: e100_probe: addr 0xff8fe000, irq 20, MAC addr 00:07:E9:E4:B0:A6
[   28.049895] ata_piix 0000:00:1f.1: version 2.10ac1
[   28.049919] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   28.049928] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   28.049955] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.050077] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   28.050150] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   28.050178] scsi0 : ata_piix
[   28.217550] ata1.00: ata_hpa_resize 1: sectors = 160086528, hpa_sectors = 160086528
[   28.217557] ata1.00: ATA-7: Maxtor 4R080L0, RAMC1TU0, max UDMA/133
[   28.217561] ata1.00: 160086528 sectors, multi 16: LBA
[   28.217570] ata1.00: limited to UDMA/33 due to 40-wire cable
[   28.230395] ata1.00: ata_hpa_resize 1: sectors = 160086528, hpa_sectors = 160086528
[   28.230405] ata1.00: configured for UDMA/33
[   28.230434] scsi1 : ata_piix
[   28.230738] Floppy drive(s): fd0 is 1.44M
[   28.252798] FDC 0 is a post-1991 82077
[   28.552930] ata2.00: ATAPI, max MWDMA2
[   28.720633] ata2.00: configured for MWDMA2
[   28.724714] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 4R080L0   RAMC PQ: 0 ANSI: 5
[   28.725793] scsi 1:0:0:0: CD-ROM            TEAC     CD-524EA         1.0A PQ: 0 ANSI: 5
[   28.752306] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   28.914304] usb 1-2: configuration #1 chosen from 1 choice
[   29.159671] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   29.346911] usb 3-1: configuration #1 chosen from 1 choice
[   29.503135] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[   29.503485] sda: Write Protect is off
[   29.503492] sda: Mode Sense: 00 3a 00 00
[   29.507466] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.511459] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[   29.515095] sda: Write Protect is off
[   29.515099] sda: Mode Sense: 00 3a 00 00
[   29.519060] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.519067]  sda: sda1 sda2 < sda5 >
[   29.577002] sd 0:0:0:0: Attached scsi disk sda
[   29.584793] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.584834] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   29.633911] sr0: scsi3-mmc drive: 24x/24x xa/form2 cdda tray
[   29.633920] Uniform CD-ROM driver Revision: 3.20
[   29.634015] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.887413] usbcore: registered new interface driver hiddev
[   29.901117] input: ARROW STRONG USB 3D Mouse as /class/input/input2
[   29.901169] input: USB HID v1.00 Mouse [ARROW STRONG USB 3D Mouse] on usb-0000:00:1d.2-1
[   29.901192] usbcore: registered new interface driver usbhid
[   29.901198] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   31.524221] Attempting manual resume
[   31.524228] swsusp: Resume From Partition 8:5
[   31.524231] PM: Checking swsusp image.
[   31.623762] PM: Resume from disk failed.
[   32.546393] kjournald starting.  Commit interval 5 seconds
[   32.546423] EXT3-fs: mounted filesystem with ordered data mode.
[  164.740737] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[  165.545504] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  165.559471] Linux agpgart interface v0.102 (c) Dave Jones
[  165.563068] agpgart: Detected an Intel 845G Chipset.
[  165.563211] agpgart: Detected 892K stolen memory.
[  165.581513] agpgart: AGP aperture is 128M @ 0xf0000000
[  165.594436] iTCO_vendor_support: vendor-support=0
[  165.596686] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  165.596911] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[  165.597013] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  166.156391] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  166.176104] intel_rng: Firmware space is locked read-only. If you can't or
[  166.176109] intel_rng: don't want to disable this in firmware setup, and if
[  166.176111] intel_rng: you are certain that your system has a functional
[  166.176113] intel_rng: RNG, try using the 'no_fwh_detect' option.
[  166.210395] input: PC Speaker as /class/input/input3
[  166.380430] parport: PnPBIOS parport detected.
[  166.380490] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  166.599508] usbcore: registered new interface driver snd-usb-audio
[  166.666726] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[  166.666779] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  166.979937] intel8x0_measure_ac97_clock: measured 54052 usecs
[  166.979943] intel8x0: clocking to 48000
[  167.224282] fuse init (API version 7.8)
[  167.262164] lp0: using parport0 (interrupt-driven).
[  167.324479] Adding 1879564k swap on /dev/disk/by-uuid/632cd178-6d5e-4084-ada0-fd6e8bb28287.  Priority:-1 extents:1 across:1879564k
[  167.526953] EXT3 FS on sda1, internal journal
[  168.691151] No dock devices found.
[  168.876472] Using specific hotkey driver
[  168.971031] input: Power Button (FF) as /class/input/input4
[  168.979520] ACPI: Power Button (FF) [PWRF]
[  169.035213] input: Sleep Button (CM) as /class/input/input5
[  169.043645] ACPI: Sleep Button (CM) [SLPB]
[  169.157153] ibm_acpi: ec object not found
[  169.217228] pcc_acpi: loading...
[  175.051423] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  175.611197] ppdev: user-space parallel port driver
[  176.844122] apm: BIOS not found.
[  177.870796] Bluetooth: Core ver 2.11
[  177.870929] NET: Registered protocol family 31
[  177.870933] Bluetooth: HCI device and connection manager initialized
[  177.870939] Bluetooth: HCI socket layer initialized
[  177.949601] Bluetooth: L2CAP ver 2.8
[  177.949608] Bluetooth: L2CAP socket layer initialized
[  178.039968] Bluetooth: RFCOMM socket layer initialized
[  178.039992] Bluetooth: RFCOMM TTY layer initialized
[  178.039996] Bluetooth: RFCOMM ver 1.8
[  178.244431] NET: Registered protocol family 17
[  179.990609] [drm] Initialized drm 1.1.0 20060810
[  180.017098] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  180.022307] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  180.061302] NET: Registered protocol family 10
[  180.061487] lo: Disabled Privacy Extensions
[  190.463195] eth0: no IPv6 routers present

```

Thankyou for your help.

---

### Post by cmfarley19 on 2007-04-22
Same problem here.  Any help is much appreciated.

---

### Post by t1m on 2007-05-02
It seems that boot up time is much faster if I press CONTROL + ALT + F6 (or F7...), which shows me what's happening.

Any ideas?

---

### Post by fordp on 2007-05-24
I have this problem too :(

It happened after a clean Feisty install.

My machine is a MSI Mega 180 with a new 320G Hard Drive.

That is an Nforce 2 based SFF and I have a Barton 2500 processor under clocked to make this machine stable.

I hope somebody can help.

---

### Post by applemacmad on 2007-06-01
Well, I can't help, but at least I can add my name to the list.

Dell Dimension 2400 with 845G mobo - 1gb of RAM.

Really slow, long boot with no logo :(

---

### Post by raul on 2007-06-01
ditto.

i stared it in recovery mode to see at what point it stalls. in my case it's in configuring network interfaces. same for everyone else?

---

### Post by whayong on 2007-06-01
None of you have boot-chart?  That will help figure out what's causing the slowing.  I found out mine was the usplash.  If you don't mind not having it, turn it off, or even remove it with synaptic.

---

### Post by raul on 2007-06-01
i edited my /etc/network/interfaces and feisty started up in less than 20 secs. however,  /etc/network/interfaces gets edited back every time i configure my wireless network manually. i started a thread for people with the same problem:

[http://ubuntuforums.org/showthread.php?p=2763575#post2763575](http://ubuntuforums.org/showthread.php?p=2763575#post2763575)

---

### Post by t1m on 2007-08-15
This is rather late to emphasize, but I find that if I just press CONTROL + ALT + F6 (or F7...) booting is at the proper speed. (you just won't get the nice image)
Hope it helps. ;)

---

