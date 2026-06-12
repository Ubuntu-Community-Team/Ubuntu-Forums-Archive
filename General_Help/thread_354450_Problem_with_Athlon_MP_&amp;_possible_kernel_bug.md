---
title: "Problem with Athlon MP &amp; possible kernel bug?"
date: 2007-02-06
forum: General Help
---

### Post by skoalbrother on 2007-02-06
Hello,

fp.  Athlon MP 1.2 x2, 1gb RAM, MS-6501, Ubuntu Server 6.10.  

I've recently switched from Centos 4.4 to Ubuntu 6.10 Server and have several messages spewed onto the console.

[42949384.160000] "amd76xrom" amd76xrom_init_one(): Unable to register resource 0xffff0000-0xffffffff - kernel bug?
[42949384.510000] shpchp: shpc_init: cannot reserve MMIO region
[42949384.510000] shpchp: shpc_init: cannot reserve MMIO region

Are these really a kernel bug or a configuration/bios problem? 

Thanks,
Donnie

Complete dmesg output below:

[42949372.960000] Linux version 2.6.17-10-server (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:47:26 UTC 2006 (Ubuntu 2.6.17-10.33-server)
[42949372.960000] BIOS-provided physical RAM map:
[42949372.960000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[42949372.960000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[42949372.960000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[42949372.960000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[42949372.960000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[42949372.960000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[42949372.960000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[42949372.960000] 127MB HIGHMEM available.
[42949372.960000] 896MB LOWMEM available.
[42949372.960000] found SMP MP-table at 000f4b00
[42949372.960000] On node 0 totalpages: 262128
[42949372.960000]   DMA zone: 4096 pages, LIFO batch:0
[42949372.960000]   Normal zone: 225280 pages, LIFO batch:31
[42949372.960000]   HighMem zone: 32752 pages, LIFO batch:7
[42949372.960000] DMI 2.2 present.
[42949372.960000] ACPI: RSDP (v000 AMD2P                                 ) @ 0x000f6470
[42949372.960000] ACPI: RSDT (v001 AMD2P  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[42949372.960000] ACPI: FADT (v001 AMD2P  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[42949372.960000] ACPI: MADT (v001 AMD2P  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff6480
[42949372.960000] ACPI: DSDT (v001 AMD2P  AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[42949372.960000] ACPI: PM-Timer IO Port: 0x608
[42949372.960000] ACPI: Local APIC address 0xfee00000
[42949372.960000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[42949372.960000] Processor #0 6:6 APIC version 16
[42949372.960000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[42949372.960000] Processor #1 6:6 APIC version 16
[42949372.960000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[42949372.960000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[42949372.960000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[42949372.960000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[42949372.960000] ACPI: IRQ0 used by override.
[42949372.960000] ACPI: IRQ2 used by override.
[42949372.960000] ACPI: IRQ9 used by override.
[42949372.960000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[42949372.960000] Using ACPI (MADT) for SMP configuration information
[42949372.960000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[42949372.960000] Built 1 zonelists
[42949372.960000] Kernel command line: root=/dev/hda3 ro quiet splash
[42949372.960000] mapped APIC to ffffd000 (fee00000)
[42949372.960000] mapped IOAPIC to ffffc000 (fec00000)
[42949372.960000] Enabling fast FPU save and restore... done.
[42949372.960000] Enabling unmasked SIMD FPU exception support... done.
[42949372.960000] Initializing CPU#0
[42949372.960000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[42949372.960000] Detected 1200.074 MHz processor.
[42949372.960000] Using pmtmr for high-res timesource
[42949372.960000] Console: colour VGA+ 80x25
[42949373.950000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[42949373.950000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[42949374.000000] Memory: 1029900k/1048512k available (1903k kernel code, 17900k reserved, 1069k data, 312k init, 131008k highmem)
[42949374.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[42949374.150000] Calibrating delay using timer specific routine.. 2402.82 BogoMIPS (lpj=12014126)
[42949374.150000] Security Framework v1.0.0 initialized
[42949374.150000] SELinux:  Disabled at boot.
[42949374.150000] Mount-cache hash table entries: 512
[42949374.150000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[42949374.150000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[42949374.150000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[42949374.150000] CPU: L2 Cache: 256K (64 bytes/line)
[42949374.150000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[42949374.150000] Checking 'hlt' instruction... OK.
[42949374.190000] SMP alternatives: switching to UP code
[42949374.190000] checking if image is initramfs... it is
[42949374.860000] Freeing initrd memory: 5106k freed
[42949374.860000] ACPI: Core revision 20060707
[42949374.920000] ACPI: Looking for DSDT ... not found!
[42949374.930000] CPU0: AMD Athlon(tm)  stepping 02
[42949374.930000] SMP alternatives: switching to SMP code
[42949374.930000] Booting processor 1/1 eip 3000
[42949374.940000] Initializing CPU#1
[42949375.090000] Calibrating delay using timer specific routine.. 2400.33 BogoMIPS (lpj=12001662)
[42949375.090000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[42949375.090000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[42949375.090000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[42949375.090000] CPU: L2 Cache: 256K (64 bytes/line)
[42949375.090000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[42949375.090000] CPU1: AMD Athlon(tm) MP stepping 02
[42949375.090000] Total of 2 processors activated (4803.15 BogoMIPS).
[42949375.090000] ENABLING IO-APIC IRQs
[42949375.090000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[42949375.300000] checking TSC synchronization across 2 CPUs: passed.
[42949375.310000] Brought up 2 CPUs
[42949375.360000] migration_cost=10000
[42949375.360000] NET: Registered protocol family 16
[42949375.360000] EISA bus registered
[42949375.360000] ACPI: bus type pci registered
[42949375.420000] PCI: PCI BIOS revision 2.10 entry at 0xfb130, last bus=2
[42949375.420000] PCI: Using configuration type 1
[42949375.420000] Setting up standard PCI resources
[42949375.420000] mtrr: your CPUs had inconsistent fixed MTRR settings
[42949375.420000] mtrr: probably your BIOS does not setup all CPUs.
[42949375.420000] mtrr: corrected configuration.
[42949375.460000] ACPI: Interpreter enabled
[42949375.460000] ACPI: Using IOAPIC for interrupt routing
[42949375.460000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[42949375.460000] PCI: Probing PCI hardware (bus 00)
[42949375.460000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[42949375.460000] Boot video device is 0000:01:05.0
[42949375.460000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[42949375.480000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.OP2P._PRT]
[42949375.480000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPP._PRT]
[42949375.480000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[42949375.480000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[42949375.480000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[42949375.480000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[42949375.490000] Linux Plug and Play Support v0.97 (c) Adam Belay
[42949375.490000] pnp: PnP ACPI init
[42949375.490000] pnp: PnP ACPI: found 14 devices
[42949375.490000] PnPBIOS: Disabled by ACPI PNP
[42949375.490000] PCI: Using ACPI for IRQ routing
[42949375.490000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[42949375.500000] PCI: Bridge: 0000:00:01.0
[42949375.500000]   IO window: disabled.
[42949375.500000]   MEM window: f4000000-f5ffffff
[42949375.500000]   PREFETCH window: e8000000-efffffff
[42949375.500000] PCI: Bridge: 0000:00:10.0
[42949375.500000]   IO window: disabled.
[42949375.500000]   MEM window: f7000000-f70fffff
[42949375.500000]   PREFETCH window: disabled.
[42949375.500000] NET: Registered protocol family 2
[42949375.620000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[42949375.620000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[42949375.620000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[42949375.620000] TCP: Hash tables configured (established 131072 bind 65536)
[42949375.620000] TCP reno registered
[42949375.620000] audit: initializing netlink socket (disabled)
[42949375.620000] audit(1170718933.620:1): initialized
[42949375.620000] highmem bounce pool size: 64 pages
[42949375.620000] VFS: Disk quotas dquot_6.5.1
[42949375.620000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[42949375.620000] Initializing Cryptographic API
[42949375.620000] io scheduler noop registered
[42949375.620000] io scheduler anticipatory registered
[42949375.620000] io scheduler deadline registered (default)
[42949375.620000] io scheduler cfq registered
[42949375.620000] BIOS failed to enable PCI standards compliance, fixing this error.
[42949375.620000] isapnp: Scanning for PnP cards...
[42949375.980000] isapnp: No Plug & Play device found
[42949376.010000] Real Time Clock Driver v1.12ac
[42949376.010000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[42949376.010000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949376.020000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949376.020000] mice: PS/2 mouse device common for all mice
[42949376.020000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[42949376.020000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[42949376.020000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[42949376.020000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[42949376.020000] serio: i8042 AUX port at 0x60,0x64 irq 12
[42949376.020000] serio: i8042 KBD port at 0x60,0x64 irq 1
[42949376.020000] EISA: Probing bus 0 at eisa.0
[42949376.020000] EISA: Detected 0 cards.
[42949376.020000] TCP bic registered
[42949376.020000] NET: Registered protocol family 1
[42949376.020000] NET: Registered protocol family 8
[42949376.020000] NET: Registered protocol family 20
[42949376.020000] Starting balanced_irq
[42949376.020000] Using IPI No-Shortcut mode
[42949376.020000] ACPI: (supports S0 S1 S3 S4 S5)
[42949376.020000] Freeing unused kernel memory: 312k freed
[42949376.070000] input: AT Translated Set 2 keyboard as /class/input/input0
[42949376.100000] Capability LSM initialized
[42949376.930000] AMD7441: IDE controller at PCI slot 0000:00:07.1
[42949376.930000] AMD7441: chipset revision 4
[42949376.930000] AMD7441: not 100% native mode: will probe irqs later
[42949376.930000] AMD7441: 0000:00:07.1 (rev 04) UDMA100 controller
[42949376.930000]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:pio
[42949376.930000]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:pio
[42949376.930000] Probing IDE interface ide0...
[42949377.240000] hda: WDC WD800JB-00FMA0, ATA DISK drive
[42949377.960000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[42949377.960000] Probing IDE interface ide1...
[42949378.740000] hdc: CW099D ATAPI CD-R/RW, ATAPI CD/DVD-ROM drive
[42949379.100000] ide1 at 0x170-0x177,0x376 on irq 15
[42949379.110000] hda: max request size: 128KiB
[42949379.110000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[42949379.110000] hda: cache flushes supported
[42949379.110000]  hda: hda1 hda2 hda3
[42949379.130000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[42949379.130000] Uniform CD-ROM driver Revision: 3.20
[42949379.620000] megaraid cmm: 2.20.2.6 (Release Date: Mon Mar 7 00:01:03 EST 2005)
[42949379.630000] SCSI subsystem initialized
[42949379.630000] megaraid: 2.20.4.8 (Release Date: Mon Apr 11 12:27:22 EST 2006)
[42949379.630000] megaraid: probe new device 0x1000:0x1960:0x1000:0x4523: bus 0:slot 8:func 0
[42949379.630000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 169
[42949379.670000] megaraid: fw version:[713R] bios version:[G121]
[42949379.770000] scsi0 : LSI Logic MegaRAID driver
[42949379.770000] scsi[0]: scanning scsi channel 0 [Phy 0] for non-raid devices
[42949379.840000] usbcore: registered new driver usbfs
[42949379.840000] usbcore: registered new driver hub
[42949379.850000] ieee1394: Initialized config rom entry `ip1394'
[42949379.850000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 177
[42949379.910000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[177]  MMIO=[f7004000-f70047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[42949379.910000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[42949379.910000] ACPI: PCI Interrupt 0000:02:00.0[D] -> GSI 19 (level, low) -> IRQ 185
[42949379.910000] ohci_hcd 0000:02:00.0: OHCI Host Controller
[42949379.910000] ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 1
[42949379.910000] ohci_hcd 0000:02:00.0: irq 185, io mem 0xf7005000
[42949379.970000] usb usb1: configuration #1 chosen from 1 choice
[42949379.970000] hub 1-0:1.0: USB hub found
[42949379.970000] hub 1-0:1.0: 4 ports detected
[42949380.100000] scsi[0]: scanning scsi channel 1 [virtual] for logical drives
[42949380.110000] Attempting manual resume
[42949380.130000] kjournald starting.  Commit interval 5 seconds
[42949380.130000] EXT3-fs: mounted filesystem with ordered data mode.
[42949381.230000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00309526b0084040]
[42949384.160000] "amd76xrom" amd76xrom_init_one(): Unable to register resource 0xffff0000-0xffffffff - kernel bug?
[42949384.200000] CFI: Found no "amd76xrom" @ffff0000 device at location zero
[42949384.220000] JEDEC: Found no "amd76xrom" @ffff0000 device at location zero
[42949384.220000] CFI: Found no "amd76xrom" @ffff0000 device at location zero
[42949384.220000] JEDEC: Found no "amd76xrom" @ffff0000 device at location zero
[42949384.220000] CFI: Found no "amd76xrom" @ffff0000 device at location zero
[42949384.220000] JEDEC: Found no "amd76xrom" @ffff0000 device at location zero
[42949384.360000] Linux agpgart interface v0.101 (c) Dave Jones
[42949384.370000] agpgart: Detected AMD 760MP chipset
[42949384.380000] agpgart: AGP aperture is 64M @ 0xf0000000
[42949384.400000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[42949384.510000] shpchp: HPC vendor_id 1022 device_id 700d ss_vid 0 ss_did 0
[42949384.510000] shpchp: shpc_init: cannot reserve MMIO region
[42949384.510000] shpchp: HPC vendor_id 1022 device_id 7448 ss_vid 0 ss_did 0
[42949384.510000] shpchp: shpc_init: cannot reserve MMIO region
[42949384.510000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[42949384.590000] hw_random: AMD768 system management I/O registers at 0x600.
[42949384.590000] hw_random hardware driver 1.0.0 loaded
[42949384.640000] ns83820.c: National Semiconductor DP83820 10/100/1000 driver.
[42949384.640000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 193
[42949384.640000] eth0: ns83820.c: 0x22c: 00000000, subsystem: 0000:0000
[42949384.670000] eth0: detected 64 bit PCI data bus.
[42949384.670000] eth0: using 64 bit addressing.
[42949384.670000] eth0: ns83820 v0.22: DP83820 v1.2: 00:4f:4a:00:15:3c io=0xf7110000 irq=193 f=h,sg
[42949384.750000] input: PC Speaker as /class/input/input1
[42949384.770000] Floppy drive(s): fd0 is 1.44M
[42949384.790000] FDC 0 is a post-1991 82077
[42949384.890000] eth0: link now 1000 mbps, full duplex and up.
[42949385.100000] parport: PnPBIOS parport detected.
[42949385.100000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[42949385.310000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[42949385.430000] ts: Compaq touchscreen protocol output
[42949385.840000] ACPI: PCI Interrupt 0000:00:07.5[B] -> GSI 17 (level, low) -> IRQ 193
[42949386.110000] NET: Registered protocol family 10
[42949386.110000] lo: Disabled Privacy Extensions
[42949386.110000] IPv6 over IPv4 tunneling driver
[42949386.170000] intel8x0_measure_ac97_clock: measured 51858 usecs
[42949386.170000] intel8x0: clocking to 48000
[42949386.350000] lp0: using parport0 (interrupt-driven).
[42949386.380000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[42949386.380000] ieee1394: sbp2: Try serialize_io=0 for better performance
[42949386.570000] Adding 4000176k swap on /dev/disk/by-uuid/26bb4cd5-6c02-42a6-baf9-9396467eac6b.  Priority:-1 extents:1 across:4000176k
[42949386.660000] EXT3 FS on hda3, internal journal
[42949386.940000] kjournald starting.  Commit interval 5 seconds
[42949386.940000] EXT3 FS on hda1, internal journal
[42949386.940000] EXT3-fs: mounted filesystem with ordered data mode.
[42949396.900000] eth0: no IPv6 routers present

---

### Post by squideekie on 2008-01-24
I have the same error message on startup, i'm aslo running an ms-6501 with dual athlon xp 2400+ cpu's. Let me know if yuo find anything else out.

---

### Post by fig_wright on 2008-06-20
See bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/39602]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/39602")

---

