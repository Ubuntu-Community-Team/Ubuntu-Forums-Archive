---
title: "Problem I created with an old USB memory stick"
date: 2008-06-10
forum: General Help
---

### Post by Ulysses on 2008-06-10
Hello

I found an old IBM USB memory stock - 32Mb - that actually had alot of old data I would have liked to recover

Problem is, I ejected it without properly unmounting it, and now it won't remount

I have tried to google this problem and check the forum but it appears that either 

[1] This is something so simple to solve, that no one has ever asked the question
[2] That this cannot be solved and it is best to move on and just get another stick

Problem is, some of the data on that stick would be absolutely awesome to have and I would dearly love to restore it.

Please help.

RAR

---

### Post by bluepowder7 on 2008-06-10
do you have a windows box that you can try to plug it into?  then properly unplug, and try back with ubuntu?

---

### Post by Ulysses on 2008-06-10
Hello

Yup. First thing I did when it went south.
But when it reads it, it reads it as empty.

And then when I plug it into my Ubuntu box, it doesn't read it at all

Is there any hope?

RAR

---

### Post by dudude on 2008-06-11
If the stick is detected by the system (you can tell by using dmesg), then you might be able to use a program like photorec to recover many of the files off of the device.

I had a similar problem with an external hard disk that became corrupted. The file system was NTFS.

---

### Post by Ulysses on 2008-06-11
Hello

Ran dmesg in terminal
Got alot of data. Not sure if I should post it all here or if it will all be so much gobbledy gook. I am not even sure what all of it means. But whatever can be done to get it fixed would be amazing and remarkable.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 4 16:35:01 UTC 2008 (Ubuntu 2.6.24-19.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dffc000 (usable)
[    0.000000]  BIOS-e820: 000000001dffc000 - 000000001dfff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001dfff000 - 000000001e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 122876) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   122876
[    0.000000]   HighMem    122876 ->   122876
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   122876
[    0.000000] On node 0 totalpages: 122876
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 927 pages used for memmap
[    0.000000]   Normal zone: 117853 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5700 checksum 0
[    0.000000] ACPI: RSDP 000F5700, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 1DFFC000, 0030 (r1 ASUS   P4S800MX 42302E31 MSFT 31313031)
[    0.000000] ACPI: FACP 1DFFC0C0, 0074 (r1 ASUS   P4S800MX 42302E31 MSFT 31313031)
[    0.000000] ACPI: DSDT 1DFFC134, 26E7 (r1   ASUS P4S800MX     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1DFFF000, 0040
[    0.000000] ACPI: BOOT 1DFFC030, 0028 (r1 ASUS   P4S800MX 42302E31 MSFT 31313031)
[    0.000000] ACPI: APIC 1DFFC058, 005A (r1 ASUS   P4S800MX 42302E31 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 128, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121917
[    0.000000] Kernel command line: root=UUID=5430de00-01db-4ddb-9efc-cb9ee2d25add ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2800.896 MHz processor.
[   19.562660] Console: colour VGA+ 80x25
[   19.562665] console [tty0] enabled
[   19.562954] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.563226] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.572346] Memory: 474884k/491504k available (2177k kernel code, 16104k reserved, 1006k data, 368k init, 0k highmem)
[   19.572356] virtual kernel memory layout:
[   19.572357]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   19.572358]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.572359]     vmalloc : 0xde800000 - 0xff7fe000   ( 527 MB)
[   19.572360]     lowmem  : 0xc0000000 - 0xddffc000   ( 479 MB)
[   19.572361]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   19.572362]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   19.572363]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   19.572366] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.572405] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   19.652298] Calibrating delay using timer specific routine.. 5606.70 BogoMIPS (lpj=11213408)
[   19.652324] Security Framework initialized
[   19.652330] SELinux:  Disabled at boot.
[   19.652345] AppArmor: AppArmor initialized
[   19.652350] Failure registering capabilities with primary security module.
[   19.652359] Mount-cache hash table entries: 512
[   19.652491] Initializing cgroup subsys ns
[   19.652495] Initializing cgroup subsys cpuacct
[   19.652507] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   19.652521] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   19.652523] CPU: L2 cache: 512K
[   19.652526] CPU: Hyper-Threading is disabled
[   19.652528] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   19.652540] Compat vDSO mapped to ffffe000.
[   19.652554] Checking 'hlt' instruction... OK.
[   19.668668] SMP alternatives: switching to UP code
[   19.670523] Freeing SMP alternatives: 11k freed
[   19.670661] Early unpacking initramfs... done
[   20.010082] ACPI: Core revision 20070126
[   20.010137] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.011276] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   20.011318] Total of 1 processors activated (5606.70 BogoMIPS).
[   20.011421] ENABLING IO-APIC IRQs
[   20.011601] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.155546] Brought up 1 CPUs
[   20.155569] CPU0 attaching sched-domain:
[   20.155572]  domain 0: span 01
[   20.155574]   groups: 01
[   20.155785] net_namespace: 64 bytes
[   20.155796] Booting paravirtualized kernel on bare hardware
[   20.156329] Time:  3:23:00  Date: 06/11/08
[   20.156359] NET: Registered protocol family 16
[   20.156588] EISA bus registered
[   20.156612] ACPI: bus type pci registered
[   20.158624] PCI: PCI BIOS revision 2.10 entry at 0xf10c0, last bus=1
[   20.158627] PCI: Using configuration type 1
[   20.158641] Setting up standard PCI resources
[   20.163454] ACPI: EC: Look up EC in DSDT
[   20.168725] ACPI: Interpreter enabled
[   20.168729] ACPI: (supports S0 S1 S4 S5)
[   20.168744] ACPI: Using IOAPIC for interrupt routing
[   20.175032] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.175233] Enabling SiS 96x SMBus.
[   20.175954] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.176095] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   20.177396] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   20.177472] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   20.177553] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   20.177635] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   20.177716] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   20.177797] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   20.177867] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   20.177947] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   20.178073] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.178110] pnp: PnP ACPI init
[   20.178120] ACPI: bus type pnp registered
[   20.182611] pnp: PnP ACPI: found 15 devices
[   20.182615] ACPI: ACPI bus type pnp unregistered
[   20.182620] PnPBIOS: Disabled by ACPI PNP
[   20.182873] PCI: Using ACPI for IRQ routing
[   20.182876] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.199438] NET: Registered protocol family 8
[   20.199440] NET: Registered protocol family 20
[   20.199521] AppArmor: AppArmor Filesystem Enabled
[   20.203421] Time: tsc clocksource has been installed.
[   20.211454] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   20.211457] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   20.211460] system 00:00: iomem range 0x100000-0x1dffffff could not be reserved
[   20.211463] system 00:00: iomem range 0xfec00000-0xfec000ff could not be reserved
[   20.211466] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   20.211474] system 00:02: ioport range 0xe400-0xe47f has been reserved
[   20.211476] system 00:02: ioport range 0xe480-0xe4ff has been reserved
[   20.211479] system 00:02: ioport range 0xe600-0xe61f has been reserved
[   20.211481] system 00:02: ioport range 0x480-0x48f has been reserved
[   20.211485] system 00:02: iomem range 0xffee0000-0xffefffff has been reserved
[   20.211492] system 00:03: iomem range 0xfffe0000-0xffffffff could not be reserved
[   20.211498] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   20.211512] system 00:0e: ioport range 0x295-0x296 has been reserved
[   20.241935] PCI: Bridge: 0000:00:01.0
[   20.241939]   IO window: d000-dfff
[   20.241945]   MEM window: e7800000-e7ffffff
[   20.241950]   PREFETCH window: f0000000-febfffff
[   20.241965] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.241978] NET: Registered protocol family 2
[   20.279387] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   20.279626] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   20.279705] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   20.279781] TCP: Hash tables configured (established 16384 bind 16384)
[   20.279783] TCP reno registered
[   20.291424] checking if image is initramfs... it is
[   20.742555] Switched to high resolution mode on CPU 0
[   20.956956] Freeing initrd memory: 7721k freed
[   20.957169] Simple Boot Flag at 0x3a set to 0x1
[   20.957623] audit: initializing netlink socket (disabled)
[   20.957642] audit(1213154580.280:1): initialized
[   20.960120] VFS: Disk quotas dquot_6.5.1
[   20.960200] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.960362] io scheduler noop registered
[   20.960364] io scheduler anticipatory registered
[   20.960366] io scheduler deadline registered
[   20.960378] io scheduler cfq registered (default)
[   20.990107] Boot video device is 0000:01:00.0
[   20.990411] isapnp: Scanning for PnP cards...
[   21.343633] isapnp: No Plug & Play device found
[   21.378789] Real Time Clock Driver v1.12ac
[   21.378896] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.379019] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.379903] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.380747] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.380824] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.380997] PNP: No PS/2 controller found. Probing ports directly.
[   21.381299] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.381305] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.385737] mice: PS/2 mouse device common for all mice
[   21.385878] EISA: Probing bus 0 at eisa.0
[   21.385908] Cannot allocate resource for EISA slot 8
[   21.385910] EISA: Detected 0 cards.
[   21.385913] cpuidle: using governor ladder
[   21.385915] cpuidle: using governor menu
[   21.386019] NET: Registered protocol family 1
[   21.386053] Using IPI No-Shortcut mode
[   21.386092] registered taskstats version 1
[   21.386176]   Magic number: 12:961:360
[   21.386309] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.386311] EDD information not available.
[   21.386657] Freeing unused kernel memory: 368k freed
[   22.618945] fuse init (API version 7.9)
[   22.644985] ACPI: Invalid PBLK length [5]
[   22.645028] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.282506] SCSI subsystem initialized
[   23.342173] libata version 3.00 loaded.
[   23.362167] usbcore: registered new interface driver usbfs
[   23.362196] usbcore: registered new interface driver hub
[   23.371068] usbcore: registered new device driver usb
[   23.374892] sis900.c: v1.08.10 Apr. 2 2006
[   23.374961] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
[   23.376273] 0000:00:04.0: VIA 6103 PHY transceiver found at address 1.
[   23.386953] 0000:00:04.0: Using transceiver found at address 1 as default
[   23.392944] eth0: SiS 900 PCI Fast Ethernet at 0x8800, IRQ 16, 00:11:2f:44:33:dd
[   23.393877] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 17
[   23.393937] ACPI: PCI interrupt for device 0000:00:02.5 disabled
[   23.398032] pata_sis 0000:00:02.5: version 0.5.2
[   23.398066] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 17
[   23.400983] scsi0 : pata_sis
[   23.407574] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.420082] scsi1 : pata_sis
[   23.420534] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xa400 irq 14
[   23.420538] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xa408 irq 15
[   23.529960] Floppy drive(s): fd0 is 1.44M
[   23.549800] FDC 0 is a post-1991 82077
[   23.615601] ata1.00: ATA-7: ST3320620A, 3.AAE, max UDMA/100
[   23.615606] ata1.00: 625142448 sectors, multi 16: LBA48 
[   23.681886] ata1.00: configured for UDMA/100
[   24.001252] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4160B, A306, max UDMA/66
[   24.172954] ata2.00: configured for UDMA/66
[   24.173096] scsi 0:0:0:0: Direct-Access     ATA      ST3320620A       3.AA PQ: 0 ANSI: 5
[   24.176808] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4160B A306 PQ: 0 ANSI: 5
[   24.179138] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   24.179152] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   24.179517] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   24.179536] ohci_hcd 0000:00:03.0: irq 20, io mem 0xe7000000
[   24.234742] usb usb1: configuration #1 chosen from 1 choice
[   24.234774] hub 1-0:1.0: USB hub found
[   24.234783] hub 1-0:1.0: 3 ports detected
[   24.336549] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 18
[   24.336569] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   24.336596] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   24.336614] ohci_hcd 0000:00:03.1: irq 18, io mem 0xe6800000
[   24.394452] usb usb2: configuration #1 chosen from 1 choice
[   24.394481] hub 2-0:1.0: USB hub found
[   24.394490] hub 2-0:1.0: 3 ports detected
[   24.496630] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[   24.496648] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   24.496685] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[   24.496722] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   24.496735] ehci_hcd 0000:00:03.3: irq 19, io mem 0xe6000000
[   24.639918] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   24.651902] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.652052] usb usb3: configuration #1 chosen from 1 choice
[   24.652081] hub 3-0:1.0: USB hub found
[   24.652090] hub 3-0:1.0: 6 ports detected
[   24.767432] Driver 'sd' needs updating - please use bus_type methods
[   24.767536] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   24.767552] sd 0:0:0:0: [sda] Write Protect is off
[   24.767555] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.767577] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.767638] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   24.767650] sd 0:0:0:0: [sda] Write Protect is off
[   24.767653] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.767673] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.767678]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.790182]  sda2 < sda5 > sda3
[   24.813472] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.820270] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.820293] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   24.827648] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.827654] Uniform CD-ROM driver Revision: 3.20
[   24.827719] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.313083] usb 1-1: new full speed USB device using ohci_hcd and address 3
[   26.515872] usb 1-1: configuration #1 chosen from 1 choice
[   26.518829] hub 1-1:1.0: USB hub found
[   26.521770] hub 1-1:1.0: 4 ports detected
[   26.948006] usb 1-2: new low speed USB device using ohci_hcd and address 4
[   27.160778] usb 1-2: configuration #1 chosen from 1 choice
[   27.471119] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   27.684885] usb 2-1: configuration #1 chosen from 1 choice
[   27.990241] usb 2-2: new low speed USB device using ohci_hcd and address 3
[   28.203010] usb 2-2: configuration #1 chosen from 1 choice
[   28.422527] usb 1-1.1: new full speed USB device using ohci_hcd and address 5
[   28.542444] usb 1-1.1: configuration #1 chosen from 1 choice
[   28.555337] usbcore: registered new interface driver hiddev
[   28.560566] input: MOUSE SYSTEM U+P mouse as /devices/pci0000:00/0000:00:03.0/usb1/1-2/1-2:1.0/input/input1
[   28.565331] input,hidraw0: USB HID v1.00 Mouse [MOUSE SYSTEM U+P mouse] on usb-0000:00:03.0-2
[   28.571542] input: Logitech USB Multimedia Keyboard as /devices/pci0000:00/0000:00:03.1/usb2/2-1/2-1:1.0/input/input2
[   28.585272] input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Multimedia Keyboard] on usb-0000:00:03.1-1
[   28.598306] input: Logitech USB Multimedia Keyboard as /devices/pci0000:00/0000:00:03.1/usb2/2-1/2-1:1.1/input/input3
[   28.609221] input,hidraw2: USB HID v1.10 Device [Logitech USB Multimedia Keyboard] on usb-0000:00:03.1-1
[   28.617746] input:   TABLET DEVICE as /devices/pci0000:00/0000:00:03.1/usb2/2-2/2-2:1.0/input/input4
[   28.629272] input,hiddev96,hidraw3: USB HID v1.00 Mouse [  TABLET DEVICE] on usb-0000:00:03.1-2
[   28.629297] usbcore: registered new interface driver usbhid
[   28.629301] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.289711] kjournald starting.  Commit interval 5 seconds
[   30.289725] EXT3-fs: mounted filesystem with ordered data mode.
[   39.603322] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   39.794794] parport_pc 00:0b: reported by Plug and Play ACPI
[   39.794903] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   39.830298] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.870229] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.924539] Linux agpgart interface v0.102
[   40.135493] agpgart: Detected SiS chipset - id:1633
[   40.139771] agpgart: AGP aperture is 64M @ 0xe8000000
[   40.176796] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
[   40.323181] input: Power Button (FF) as /devices/virtual/input/input6
[   40.349386] ACPI: Power Button (FF) [PWRF]
[   40.349477] input: Power Button (CM) as /devices/virtual/input/input7
[   40.377355] ACPI: Power Button (CM) [PWRB]
[   41.790990] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 21
[   42.102473] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1094
[   42.102493] usbcore: registered new interface driver usblp
[   42.210184] intel8x0_measure_ac97_clock: measured 52354 usecs
[   42.210189] intel8x0: clocking to 48000
[   44.040782] lp0: using parport0 (interrupt-driven).
[   44.492940] EXT3 FS on sda3, internal journal
[   44.636497] device-mapper: uevent: version 1.0.3
[   44.636533] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   45.606608] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.362270] No dock devices found.
[   48.829511] NET: Registered protocol family 10
[   48.830050] lo: Disabled Privacy Extensions
[   49.156543] ppdev: user-space parallel port driver
[   49.348091] audit(1213154609.416:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5141 profile="/usr/sbin/cupsd" namespace="default"
[   49.392965] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   49.392972] apm: overridden by ACPI.
[   49.569796] RPC: Registered udp transport module.
[   49.569803] RPC: Registered tcp transport module.
[   49.617851] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   49.691597] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   49.703039] NFSD: starting 90-second grace period
[   55.323197] Bluetooth: Core ver 2.11
[   55.324064] NET: Registered protocol family 31
[   55.324069] Bluetooth: HCI device and connection manager initialized
[   55.324074] Bluetooth: HCI socket layer initialized
[   55.363931] Bluetooth: L2CAP ver 2.9
[   55.363937] Bluetooth: L2CAP socket layer initialized
[   55.438667] Bluetooth: RFCOMM socket layer initialized
[   55.438946] Bluetooth: RFCOMM TTY layer initialized
[   55.438950] Bluetooth: RFCOMM ver 1.8
[   57.536849] NET: Registered protocol family 17
[   58.195758] eth0: Media Link On 100mbps full-duplex 
[   72.143450] eth0: no IPv6 routers present
[   77.921786] UDF-fs: Partition marked readonly; forcing readonly mount
[   77.960089] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD_VIDEO', timestamp 2004/04/13 11:34 (1f10)
```

If this helps, that would be awesome.
But I won't get to anything until tomorrow or the next day. I gotta be up for work in four and a half hours.

RAR

---

### Post by dudude on 2008-06-11
Plug the device in and then unplug it. There should be some lines at the bottom of the dmesg output that say some stuff about USB devices.

Here are the final few lines of output when I plugged in and unplugged my working USB stick.

```
[14621.223786] usb 1-4: new high speed USB device using ehci_hcd and address 3
[14621.358786] usb 1-4: configuration #1 chosen from 1 choice
[14621.431390] usbcore: registered new interface driver libusual
[14621.461423] Initializing USB Mass Storage driver...
[14621.461500] scsi6 : SCSI emulation for USB Mass Storage devices
[14621.461547] usbcore: registered new interface driver usb-storage
[14621.461549] USB Mass Storage support registered.
[14621.461639] usb-storage: device found at 3
[14621.461641] usb-storage: waiting for device to settle before scanning
[14622.610688] usb 1-4: USB disconnect, address 3
```

The main reason for doing this is just to make sure that the computer actually sees the device, though maybe not read it.

---

### Post by Rhubarb on 2008-06-11
photorec is very good at restoring files from corrupted / deleted media.
You can get it by installing the testdisk package in Synaptic.

To use photorec, read the man page for it:
```
man photorec
```

---

### Post by dudude on 2008-06-11
Just make sure that photorec is set to detect the right file types for your device if you have something other than the usual pictures and documents stored on it.

---

### Post by Ulysses on 2008-06-11
Hey

Okay. Check it out. Plugged and unplugged it.

```
84409.278261] Initializing USB Mass Storage driver...
[84409.280450] scsi2 : SCSI emulation for USB Mass Storage devices
[84409.282220] usbcore: registered new interface driver usb-storage
[84409.282229] USB Mass Storage support registered.
[84409.282750] usb-storage: device found at 6
[84409.282754] usb-storage: waiting for device to settle before scanning
[84414.273734] usb-storage: device scan complete
[84414.282708] scsi 2:0:0:0: Direct-Access     IBM      Memory Key       1.01 PQ: 0 ANSI: 0 CCS
[84414.304664] sd 2:0:0:0: [sdb] 64000 512-byte hardware sectors (33 MB)
[84414.316661] sd 2:0:0:0: [sdb] Write Protect is off
[84414.316670] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[84414.316673] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[84414.338600] sd 2:0:0:0: [sdb] 64000 512-byte hardware sectors (33 MB)
[84414.350590] sd 2:0:0:0: [sdb] Write Protect is off
[84414.350599] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[84414.350602] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[84414.350612]  sdb: sdb1
[84414.375604] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[84414.375672] sd 2:0:0:0: Attached scsi generic sg2 type 0
[84418.972782] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.972792] end_request: I/O error, dev sdb, sector 537
[84418.973254] FAT: Directory bread(block 505) failed
[84418.973313] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973317] end_request: I/O error, dev sdb, sector 538
[84418.973325] FAT: Directory bread(block 506) failed
[84418.973362] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973365] end_request: I/O error, dev sdb, sector 539
[84418.973371] FAT: Directory bread(block 507) failed
[84418.973407] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973410] end_request: I/O error, dev sdb, sector 540
[84418.973417] FAT: Directory bread(block 508) failed
[84418.973451] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973455] end_request: I/O error, dev sdb, sector 541
[84418.973461] FAT: Directory bread(block 509) failed
[84418.973496] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973499] end_request: I/O error, dev sdb, sector 542
[84418.973505] FAT: Directory bread(block 510) failed
[84418.973540] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973543] end_request: I/O error, dev sdb, sector 543
[84418.973549] FAT: Directory bread(block 511) failed
[84418.973595] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973598] end_request: I/O error, dev sdb, sector 544
[84418.973604] FAT: Directory bread(block 512) failed
[84418.973641] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973644] end_request: I/O error, dev sdb, sector 545
[84418.973650] FAT: Directory bread(block 513) failed
[84418.973686] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973689] end_request: I/O error, dev sdb, sector 546
[84418.973695] FAT: Directory bread(block 514) failed
[84418.973744] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973748] end_request: I/O error, dev sdb, sector 547
[84418.973754] FAT: Directory bread(block 515) failed
[84418.973790] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973793] end_request: I/O error, dev sdb, sector 548
[84418.973799] FAT: Directory bread(block 516) failed
[84418.973835] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973839] end_request: I/O error, dev sdb, sector 549
[84418.973845] FAT: Directory bread(block 517) failed
[84418.973880] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973884] end_request: I/O error, dev sdb, sector 550
[84418.973890] FAT: Directory bread(block 518) failed
[84418.973924] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973928] end_request: I/O error, dev sdb, sector 551
[84418.973934] FAT: Directory bread(block 519) failed
[84418.973973] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.973977] end_request: I/O error, dev sdb, sector 552
[84418.973983] FAT: Directory bread(block 520) failed
[84418.974019] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.974022] end_request: I/O error, dev sdb, sector 553
[84418.974028] FAT: Directory bread(block 521) failed
[84418.974062] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.974066] end_request: I/O error, dev sdb, sector 554
[84418.974073] FAT: Directory bread(block 522) failed
[84418.974108] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.974111] end_request: I/O error, dev sdb, sector 555
[84418.974117] FAT: Directory bread(block 523) failed
[84418.974153] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.974156] end_request: I/O error, dev sdb, sector 556
[84418.979156] FAT: Directory bread(block 524) failed
[84418.979226] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979230] end_request: I/O error, dev sdb, sector 557
[84418.979240] FAT: Directory bread(block 525) failed
[84418.979276] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979280] end_request: I/O error, dev sdb, sector 558
[84418.979286] FAT: Directory bread(block 526) failed
[84418.979321] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979325] end_request: I/O error, dev sdb, sector 559
[84418.979331] FAT: Directory bread(block 527) failed
[84418.979372] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979376] end_request: I/O error, dev sdb, sector 560
[84418.979382] FAT: Directory bread(block 528) failed
[84418.979417] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979421] end_request: I/O error, dev sdb, sector 561
[84418.979427] FAT: Directory bread(block 529) failed
[84418.979461] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979464] end_request: I/O error, dev sdb, sector 562
[84418.979470] FAT: Directory bread(block 530) failed
[84418.979504] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979507] end_request: I/O error, dev sdb, sector 563
[84418.979513] FAT: Directory bread(block 531) failed
[84418.979548] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979551] end_request: I/O error, dev sdb, sector 564
[84418.979557] FAT: Directory bread(block 532) failed
[84418.979592] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979596] end_request: I/O error, dev sdb, sector 565
[84418.979601] FAT: Directory bread(block 533) failed
[84418.979636] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979639] end_request: I/O error, dev sdb, sector 566
[84418.979645] FAT: Directory bread(block 534) failed
[84418.979680] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[84418.979683] end_request: I/O error, dev sdb, sector 567
[84418.979689] FAT: Directory bread(block 535) failed
[84418.982230] usb 1-1.4: USB disconnect, address 6
[84419.074865] FAT: Directory bread(block 504) failed
[84419.074879] FAT: Directory bread(block 505) failed
[84419.074886] FAT: Directory bread(block 506) failed
[84419.074893] FAT: Directory bread(block 507) failed
[84419.074899] FAT: Directory bread(block 508) failed
[84419.074905] FAT: Directory bread(block 509) failed
[84419.074911] FAT: Directory bread(block 510) failed
[84419.074917] FAT: Directory bread(block 511) failed
[84419.074928] FAT: Directory bread(block 512) failed
[84419.074936] FAT: Directory bread(block 513) failed
[84419.074942] FAT: Directory bread(block 514) failed
[84419.074949] FAT: Directory bread(block 515) failed
[84419.074955] FAT: Directory bread(block 516) failed
[84419.074961] FAT: Directory bread(block 517) failed
[84419.074967] FAT: Directory bread(block 518) failed
[84419.074973] FAT: Directory bread(block 519) failed
[84419.074983] FAT: Directory bread(block 520) failed
[84419.074990] FAT: Directory bread(block 521) failed
[84419.074996] FAT: Directory bread(block 522) failed
[84419.075002] FAT: Directory bread(block 523) failed
[84419.075009] FAT: Directory bread(block 524) failed
[84419.075015] FAT: Directory bread(block 525) failed
[84419.075021] FAT: Directory bread(block 526) failed
[84419.075028] FAT: Directory bread(block 527) failed
[84419.075037] FAT: Directory bread(block 528) failed
[84419.075044] FAT: Directory bread(block 529) failed
[84419.075050] FAT: Directory bread(block 530) failed
[84419.075057] FAT: Directory bread(block 531) failed
[84419.075063] FAT: Directory bread(block 532) failed
[84419.075069] FAT: Directory bread(block 533) failed
[84419.075075] FAT: Directory bread(block 534) failed
[84419.075082] FAT: Directory bread(block 535) failed
[84419.075205] FAT: Directory bread(block 504) failed
[84419.075212] FAT: Directory bread(block 505) failed
[84419.075218] FAT: Directory bread(block 506) failed
[84419.075224] FAT: Directory bread(block 507) failed
[84419.075230] FAT: Directory bread(block 508) failed
[84419.075236] FAT: Directory bread(block 509) failed
[84419.075242] FAT: Directory bread(block 510) failed
[84419.075248] FAT: Directory bread(block 511) failed
[84419.075254] FAT: Directory bread(block 512) failed
[84419.075260] FAT: Directory bread(block 513) failed
[84419.075266] FAT: Directory bread(block 514) failed
[84419.075272] FAT: Directory bread(block 515) failed
[84419.075278] FAT: Directory bread(block 516) failed
[84419.075283] FAT: Directory bread(block 517) failed
[84419.075289] FAT: Directory bread(block 518) failed
[84419.075295] FAT: Directory bread(block 519) failed
[84419.075301] FAT: Directory bread(block 520) failed
[84419.075307] FAT: Directory bread(block 521) failed
[84419.075313] FAT: Directory bread(block 522) failed
[84419.075319] FAT: Directory bread(block 523) failed
[84419.075325] FAT: Directory bread(block 524) failed
[84419.075331] FAT: Directory bread(block 525) failed
[84419.075337] FAT: Directory bread(block 526) failed
[84419.075343] FAT: Directory bread(block 527) failed
[84419.075349] FAT: Directory bread(block 528) failed
[84419.075355] FAT: Directory bread(block 529) failed
[84419.075361] FAT: Directory bread(block 530) failed
[84419.075367] FAT: Directory bread(block 531) failed
[84419.075373] FAT: Directory bread(block 532) failed
[84419.075379] FAT: Directory bread(block 533) failed
[84419.075385] FAT: Directory bread(block 534) failed
[84419.075391] FAT: Directory bread(block 535) failed
[84419.075433] FAT: Directory bread(block 504) failed
[84419.075439] FAT: Directory bread(block 505) failed
[84419.075446] FAT: Directory bread(block 506) failed
[84419.075452] FAT: Directory bread(block 507) failed
[84419.075458] FAT: Directory bread(block 508) failed
[84419.075464] FAT: Directory bread(block 509) failed
[84419.075470] FAT: Directory bread(block 510) failed
[84419.075476] FAT: Directory bread(block 511) failed
[84419.075482] FAT: Directory bread(block 512) failed
[84419.075488] FAT: Directory bread(block 513) failed
[84419.075494] FAT: Directory bread(block 514) failed
[84419.075500] FAT: Directory bread(block 515) failed
[84419.075506] FAT: Directory bread(block 516) failed
[84419.075512] FAT: Directory bread(block 517) failed
[84419.075518] FAT: Directory bread(block 518) failed
[84419.075524] FAT: Directory bread(block 519) failed
[84419.075530] FAT: Directory bread(block 520) failed
[84419.075536] FAT: Directory bread(block 521) failed
[84419.075542] FAT: Directory bread(block 522) failed
[84419.075548] FAT: Directory bread(block 523) failed
[84419.075554] FAT: Directory bread(block 524) failed
[84419.075559] FAT: Directory bread(block 525) failed
[84419.075565] FAT: Directory bread(block 526) failed
[84419.075571] FAT: Directory bread(block 527) failed
[84419.075577] FAT: Directory bread(block 528) failed
[84419.075583] FAT: Directory bread(block 529) failed
[84419.075589] FAT: Directory bread(block 530) failed
[84419.075595] FAT: Directory bread(block 531) failed
[84419.075601] FAT: Directory bread(block 532) failed
[84419.075607] FAT: Directory bread(block 533) failed
[84419.075613] FAT: Directory bread(block 534) failed
[84419.075619] FAT: Directory bread(block 535) failed
[84419.075659] FAT: Directory bread(block 504) failed
[84419.075666] FAT: Directory bread(block 505) failed
[84419.075672] FAT: Directory bread(block 506) failed
[84419.075679] FAT: Directory bread(block 507) failed
[84419.075685] FAT: Directory bread(block 508) failed
[84419.075691] FAT: Directory bread(block 509) failed
[84419.075698] FAT: Directory bread(block 510) failed
[84419.075704] FAT: Directory bread(block 511) failed
[84419.075711] FAT: Directory bread(block 512) failed
[84419.075717] FAT: Directory bread(block 513) failed
[84419.075723] FAT: Directory bread(block 514) failed
[84419.075729] FAT: Directory bread(block 515) failed
[84419.075735] FAT: Directory bread(block 516) failed
[84419.075741] FAT: Directory bread(block 517) failed
[84419.075747] FAT: Directory bread(block 518) failed
[84419.075753] FAT: Directory bread(block 519) failed
[84419.075758] FAT: Directory bread(block 520) failed
[84419.075764] FAT: Directory bread(block 521) failed
[84419.075770] FAT: Directory bread(block 522) failed
[84419.075776] FAT: Directory bread(block 523) failed
[84419.075782] FAT: Directory bread(block 524) failed
[84419.075788] FAT: Directory bread(block 525) failed
[84419.075794] FAT: Directory bread(block 526) failed
[84419.075799] FAT: Directory bread(block 527) failed
[84419.075805] FAT: Directory bread(block 528) failed
[84419.075811] FAT: Directory bread(block 529) failed
[84419.075817] FAT: Directory bread(block 530) failed
[84419.075822] FAT: Directory bread(block 531) failed
[84419.075828] FAT: Directory bread(block 532) failed
[84419.075834] FAT: Directory bread(block 533) failed
[84419.075840] FAT: Directory bread(block 534) failed
[84419.075846] FAT: Directory bread(block 535) failed
[84419.075886] FAT: Directory bread(block 504) failed
[84419.075893] FAT: Directory bread(block 505) failed
[84419.075899] FAT: Directory bread(block 506) failed
[84419.075905] FAT: Directory bread(block 507) failed
[84419.075911] FAT: Directory bread(block 508) failed
[84419.075917] FAT: Directory bread(block 509) failed
[84419.075924] FAT: Directory bread(block 510) failed
[84419.075930] FAT: Directory bread(block 511) failed
[84419.075936] FAT: Directory bread(block 512) failed
[84419.075942] FAT: Directory bread(block 513) failed
[84419.075948] FAT: Directory bread(block 514) failed
[84419.075954] FAT: Directory bread(block 515) failed
[84419.075960] FAT: Directory bread(block 516) failed
[84419.075966] FAT: Directory bread(block 517) failed
[84419.075972] FAT: Directory bread(block 518) failed
[84419.075978] FAT: Directory bread(block 519) failed
[84419.075984] FAT: Directory bread(block 520) failed
[84419.075990] FAT: Directory bread(block 521) failed
[84419.075996] FAT: Directory bread(block 522) failed
[84419.076002] FAT: Directory bread(block 523) failed
[84419.076008] FAT: Directory bread(block 524) failed
[84419.076015] FAT: Directory bread(block 525) failed
[84419.076021] FAT: Directory bread(block 526) failed
[84419.076027] FAT: Directory bread(block 527) failed
[84419.076033] FAT: Directory bread(block 528) failed
[84419.076039] FAT: Directory bread(block 529) failed
[84419.076045] FAT: Directory bread(block 530) failed
[84419.076051] FAT: Directory bread(block 531) failed
[84419.076057] FAT: Directory bread(block 532) failed
[84419.076063] FAT: Directory bread(block 533) failed
[84419.076069] FAT: Directory bread(block 534) failed
[84419.076075] FAT: Directory bread(block 535) failed
[84419.076111] FAT: Directory bread(block 504) failed
[84419.076118] FAT: Directory bread(block 505) failed
[84419.076124] FAT: Directory bread(block 506) failed
[84419.076130] FAT: Directory bread(block 507) failed
[84419.076137] FAT: Directory bread(block 508) failed
[84419.076143] FAT: Directory bread(block 509) failed
[84419.076149] FAT: Directory bread(block 510) failed
[84419.076155] FAT: Directory bread(block 511) failed
[84419.076161] FAT: Directory bread(block 512) failed
[84419.076167] FAT: Directory bread(block 513) failed
[84419.076173] FAT: Directory bread(block 514) failed
[84419.076179] FAT: Directory bread(block 515) failed
[84419.076185] FAT: Directory bread(block 516) failed
[84419.076191] FAT: Directory bread(block 517) failed
[84419.076197] FAT: Directory bread(block 518) failed
[84419.076203] FAT: Directory bread(block 519) failed
[84419.076209] FAT: Directory bread(block 520) failed
[84419.076215] FAT: Directory bread(block 521) failed
[84419.076221] FAT: Directory bread(block 522) failed
[84419.076227] FAT: Directory bread(block 523) failed
[84419.076233] FAT: Directory bread(block 524) failed
[84419.076239] FAT: Directory bread(block 525) failed
[84419.076245] FAT: Directory bread(block 526) failed
[84419.076251] FAT: Directory bread(block 527) failed
[84419.076257] FAT: Directory bread(block 528) failed
[84419.076263] FAT: Directory bread(block 529) failed
[84419.076269] FAT: Directory bread(block 530) failed
[84419.076275] FAT: Directory bread(block 531) failed
[84419.076281] FAT: Directory bread(block 532) failed
[84419.076287] FAT: Directory bread(block 533) failed
[84419.076293] FAT: Directory bread(block 534) failed
[84419.076298] FAT: Directory bread(block 535) failed
[84419.076332] FAT: Directory bread(block 504) failed
[84419.076339] FAT: Directory bread(block 505) failed
[84419.076345] FAT: Directory bread(block 506) failed
[84419.076352] FAT: Directory bread(block 507) failed
[84419.076358] FAT: Directory bread(block 508) failed
[84419.076364] FAT: Directory bread(block 509) failed
[84419.076370] FAT: Directory bread(block 510) failed
[84419.076376] FAT: Directory bread(block 511) failed
[84419.076382] FAT: Directory bread(block 512) failed
[84419.076388] FAT: Directory bread(block 513) failed
[84419.076394] FAT: Directory bread(block 514) failed
[84419.076400] FAT: Directory bread(block 515) failed
[84419.076406] FAT: Directory bread(block 516) failed
[84419.076411] FAT: Directory bread(block 517) failed
[84419.076417] FAT: Directory bread(block 518) failed
[84419.076423] FAT: Directory bread(block 519) failed
[84419.076429] FAT: Directory bread(block 520) failed
[84419.076435] FAT: Directory bread(block 521) failed
[84419.076441] FAT: Directory bread(block 522) failed
[84419.076447] FAT: Directory bread(block 523) failed
[84419.076452] FAT: Directory bread(block 524) failed
[84419.076458] FAT: Directory bread(block 525) failed
[84419.076464] FAT: Directory bread(block 526) failed
[84419.076470] FAT: Directory bread(block 527) failed
[84419.076476] FAT: Directory bread(block 528) failed
[84419.076481] FAT: Directory bread(block 529) failed
[84419.076487] FAT: Directory bread(block 530) failed
[84419.076493] FAT: Directory bread(block 531) failed
[84419.076499] FAT: Directory bread(block 532) failed
[84419.076506] FAT: Directory bread(block 533) failed
[84419.076512] FAT: Directory bread(block 534) failed
[84419.076518] FAT: Directory bread(block 535) failed
[84419.076552] FAT: Directory bread(block 504) failed
[84419.076559] FAT: Directory bread(block 505) failed
[84419.076565] FAT: Directory bread(block 506) failed
[84419.076572] FAT: Directory bread(block 507) failed
[84419.076578] FAT: Directory bread(block 508) failed
[84419.076584] FAT: Directory bread(block 509) failed
[84419.076590] FAT: Directory bread(block 510) failed
[84419.076596] FAT: Directory bread(block 511) failed
[84419.076602] FAT: Directory bread(block 512) failed
[84419.076609] FAT: Directory bread(block 513) failed
[84419.076615] FAT: Directory bread(block 514) failed
[84419.076621] FAT: Directory bread(block 515) failed
[84419.076627] FAT: Directory bread(block 516) failed
[84419.076633] FAT: Directory bread(block 517) failed
[84419.076640] FAT: Directory bread(block 518) failed
[84419.076646] FAT: Directory bread(block 519) failed
[84419.076652] FAT: Directory bread(block 520) failed
[84419.076658] FAT: Directory bread(block 521) failed
[84419.076664] FAT: Directory bread(block 522) failed
[84419.076670] FAT: Directory bread(block 523) failed
[84419.076676] FAT: Directory bread(block 524) failed
[84419.076682] FAT: Directory bread(block 525) failed
[84419.076688] FAT: Directory bread(block 526) failed
[84419.076694] FAT: Directory bread(block 527) failed
[84419.076700] FAT: Directory bread(block 528) failed
[84419.076706] FAT: Directory bread(block 529) failed
[84419.076712] FAT: Directory bread(block 530) failed
[84419.076719] FAT: Directory bread(block 531) failed
[84419.076725] FAT: Directory bread(block 532) failed
[84419.076731] FAT: Directory bread(block 533) failed
[84419.076736] FAT: Directory bread(block 534) failed
[84419.076743] FAT: Directory bread(block 535) failed
[84419.076806] FAT: Directory bread(block 504) failed
[84419.076813] FAT: Directory bread(block 505) failed
[84419.076819] FAT: Directory bread(block 506) failed
[84419.076825] FAT: Directory bread(block 507) failed
[84419.076831] FAT: Directory bread(block 508) failed
[84419.076837] FAT: Directory bread(block 509) failed
[84419.076844] FAT: Directory bread(block 510) failed
[84419.076850] FAT: Directory bread(block 511) failed
[84419.076855] FAT: Directory bread(block 512) failed
[84419.076861] FAT: Directory bread(block 513) failed
[84419.076867] FAT: Directory bread(block 514) failed
[84419.076873] FAT: Directory bread(block 515) failed
[84419.076879] FAT: Directory bread(block 516) failed
[84419.076885] FAT: Directory bread(block 517) failed
[84419.076891] FAT: Directory bread(block 518) failed
[84419.076897] FAT: Directory bread(block 519) failed
[84419.076903] FAT: Directory bread(block 520) failed
[84419.076909] FAT: Directory bread(block 521) failed
[84419.076915] FAT: Directory bread(block 522) failed
[84419.076921] FAT: Directory bread(block 523) failed
[84419.076928] FAT: Directory bread(block 524) failed
[84419.076934] FAT: Directory bread(block 525) failed
[84419.076940] FAT: Directory bread(block 526) failed
[84419.076946] FAT: Directory bread(block 527) failed
[84419.076952] FAT: Directory bread(block 528) failed
[84419.076958] FAT: Directory bread(block 529) failed
[84419.076964] FAT: Directory bread(block 530) failed
[84419.076970] FAT: Directory bread(block 531) failed
[84419.076976] FAT: Directory bread(block 532) failed
[84419.076982] FAT: Directory bread(block 533) failed
[84419.076988] FAT: Directory bread(block 534) failed
[84419.076994] FAT: Directory bread(block 535) failed
[84419.077067] FAT: Directory bread(block 504) failed
[84419.077074] FAT: Directory bread(block 505) failed
[84419.077080] FAT: Directory bread(block 506) failed
[84419.077086] FAT: Directory bread(block 507) failed
[84419.077092] FAT: Directory bread(block 508) failed
[84419.077098] FAT: Directory bread(block 509) failed
[84419.077104] FAT: Directory bread(block 510) failed
[84419.077110] FAT: Directory bread(block 511) failed
[84419.077116] FAT: Directory bread(block 512) failed
[84419.077122] FAT: Directory bread(block 513) failed
[84419.077128] FAT: Directory bread(block 514) failed
[84419.077134] FAT: Directory bread(block 515) failed
[84419.077140] FAT: Directory bread(block 516) failed
[84419.077145] FAT: Directory bread(block 517) failed
[84419.077151] FAT: Directory bread(block 518) failed
[84419.077157] FAT: Directory bread(block 519) failed
[84419.077163] FAT: Directory bread(block 520) failed
[84419.077169] FAT: Directory bread(block 521) failed
[84419.077175] FAT: Directory bread(block 522) failed
[84419.077181] FAT: Directory bread(block 523) failed
[84419.077187] FAT: Directory bread(block 524) failed
[84419.077192] FAT: Directory bread(block 525) failed
[84419.077198] FAT: Directory bread(block 526) failed
[84419.077204] FAT: Directory bread(block 527) failed
[84419.077210] FAT: Directory bread(block 528) failed
[84419.077216] FAT: Directory bread(block 529) failed
[84419.077222] FAT: Directory bread(block 530) failed
[84419.077228] FAT: Directory bread(block 531) failed
[84419.077234] FAT: Directory bread(block 532) failed
[84419.077240] FAT: Directory bread(block 533) failed
[84419.077245] FAT: Directory bread(block 534) failed
[84419.077251] FAT: Directory bread(block 535) failed
[84419.077308] FAT: Directory bread(block 504) failed
[84419.077315] FAT: Directory bread(block 505) failed
[84419.077321] FAT: Directory bread(block 506) failed
[84419.077327] FAT: Directory bread(block 507) failed
[84419.077333] FAT: Directory bread(block 508) failed
[84419.077340] FAT: Directory bread(block 509) failed
[84419.077346] FAT: Directory bread(block 510) failed
[84419.077352] FAT: Directory bread(block 511) failed
[84419.077358] FAT: Directory bread(block 512) failed
[84419.077364] FAT: Directory bread(block 513) failed
[84419.077370] FAT: Directory bread(block 514) failed
[84419.077376] FAT: Directory bread(block 515) failed
[84419.077382] FAT: Directory bread(block 516) failed
[84419.077388] FAT: Directory bread(block 517) failed
[84419.077393] FAT: Directory bread(block 518) failed
[84419.077399] FAT: Directory bread(block 519) failed
[84419.077405] FAT: Directory bread(block 520) failed
[84419.077411] FAT: Directory bread(block 521) failed
[84419.077417] FAT: Directory bread(block 522) failed
[84419.077423] FAT: Directory bread(block 523) failed
[84419.077429] FAT: Directory bread(block 524) failed
[84419.077435] FAT: Directory bread(block 525) failed
[84419.077441] FAT: Directory bread(block 526) failed
[84419.077447] FAT: Directory bread(block 527) failed
[84419.077452] FAT: Directory bread(block 528) failed
[84419.077458] FAT: Directory bread(block 529) failed
[84419.077464] FAT: Directory bread(block 530) failed
[84419.077470] FAT: Directory bread(block 531) failed
[84419.077476] FAT: Directory bread(block 532) failed
[84419.077482] FAT: Directory bread(block 533) failed
[84419.077488] FAT: Directory bread(block 534) failed
[84419.077494] FAT: Directory bread(block 535) failed
[84419.703043] FAT: FAT read failed (blocknr 8)
[84419.784802] scsi 2:0:0:0: rejecting I/O to dead device
```

I'm guessing that this is not at all good information

Is it at all recoverable? I haven't tried photorec yet.

RAR

---

### Post by Ulysses on 2008-06-11
Hello

Used Synaptic. Got photorec. Ran it in terminal. Does not see the usb key at all.

Hoboy. Any help would be appreciated.

I'm not that smart, but I'm motivated

RAR

---

### Post by dudude on 2008-06-12
It seems that photorec only works with mostly working drives, so instead you should use ddrescue.

```
sudo apt-get install ddrescue
```

From your dmesg output it looks like the device is showing up at /dev/sdb, so, in my case I would type

```
sudo dd_rescue /dev/sdb /home/robert/Desktop/image.img
```

Of course, changing the second location to wherever you want it to be.

This will image your device. To see the contents of the image, type something like
```

sudo mkdir /media/stick
sudo mount -o loop /path/to/file/image.img /media/stick
```

The contents that were recovered from the stick should appear at /media/stick if you look there in Nautilus or the terminal. 

This worked for me, but let me know if something went wrong:)

---

### Post by dudude on 2008-06-12
Also, it's likely that you did, but make sure that you ran photorec as root.

If the previous method failed use foremost.
```

sudo apt-get install foremost
```

then,

```
mkdir ~/Desktop/recover
sudo foremost -i /path/to/file/image.img -o ~/Desktop/recover

```

To make the files accessible, 

```
sudo chown -R USERNAME.USERNAME ~/Desktop/recover
```

Replacing USERNAME with your username.

This will get the most common file types. If it does not get all of the files that you know were on the device, then try using magicrescue or something else maybe.

---

