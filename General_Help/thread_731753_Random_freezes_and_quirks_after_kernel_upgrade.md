---
title: "Random freezes and quirks after kernel upgrade"
date: 2008-03-22
forum: General Help
---

### Post by ruzkie on 2008-03-22
Hello i  am having massive problems with my computer hanging after the last reboot (kernel upgrade)
I have to switch from tty1>tty7 where X is when i a) start gdm b) login to gnome (i have gdm disabled as a service so don't worry)
If i don't switch it just sits there for an infinite amount of time not just from the tty1 to 7 but need to do it back and forth for gdm and gnome to appear.
and even when i am  in X i get completely random freezes (mostly with mplayer so far)
which i have no idea about what's causing it

lspci>
00:00.0 Host bridge: VIA Technologies, Inc. KT880 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 08)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:13.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:13.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:13.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

dmesg>

[    0.000000] Linux version 2.6.24-12-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu4)) #1 SMP Wed Mar 12 23:01:54 UTC 2008 (Ubuntu 2.6.24-12.22-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004ff40000 (usable)
[    0.000000]  BIOS-e820: 000000004ff40000 - 000000004ff50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004ff50000 - 0000000050000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[    0.000000] 383MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 327488) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   327488
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   327488
[    0.000000] On node 0 totalpages: 327488
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 766 pages used for memmap
[    0.000000]   HighMem zone: 97346 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F9190 checksum 0
[    0.000000] ACPI: RSDP 000F9190, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 4FF40000, 0030 (r1 A M I  OEMRSDT   1000602 MSFT       97)
[    0.000000] ACPI: FACP 4FF40200, 0081 (r2 A M I  OEMFACP   1000602 MSFT       97)
[    0.000000] ACPI: DSDT 4FF40350, 373D (r1  A0008 A0008705      705 INTL  2002026)
[    0.000000] ACPI: FACS 4FF50000, 0040
[    0.000000] ACPI: APIC 4FF40300, 004A (r1 A M I  OEMAPIC   1000602 MSFT       97)
[    0.000000] ACPI: OEMB 4FF50040, 003F (r1 A M I  OEMBIOS   1000602 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:af7c0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324930
[    0.000000] Kernel command line: root=UUID=611ea16a-1257-4913-8d18-e96b6d54c3e2 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1666.510 MHz processor.
[   40.467395] Console: colour VGA+ 80x25
[   40.467399] console [tty0] enabled
[   40.468129] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   40.469386] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   40.526502] Memory: 1285816k/1309952k available (2164k kernel code, 22864k reserved, 1007k data, 364k init, 392448k highmem)
[   40.526512] virtual kernel memory layout:
[   40.526514]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   40.526515]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   40.526517]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   40.526518]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   40.526520]       .init : 0xc041f000 - 0xc047a000   ( 364 kB)
[   40.526521]       .data : 0xc031d1bd - 0xc0418dc4   (1007 kB)
[   40.526523]       .text : 0xc0100000 - 0xc031d1bd   (2164 kB)
[   40.526527] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   40.526583] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   40.606558] Calibrating delay using timer specific routine.. 3337.08 BogoMIPS (lpj=6674162)
[   40.606601] Security Framework initialized
[   40.606610] SELinux:  Disabled at boot.
[   40.606633] AppArmor: AppArmor initialized
[   40.606638] Failure registering capabilities with primary security module.
[   40.606650] Mount-cache hash table entries: 512
[   40.606825] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   40.606837] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   40.606841] CPU: L2 Cache: 256K (64 bytes/line)
[   40.606844] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000 00000000
[   40.606858] Compat vDSO mapped to ffffe000.
[   40.606873] Checking 'hlt' instruction... OK.
[   40.622817] SMP alternatives: switching to UP code
[   40.624093] Freeing SMP alternatives: 11k freed
[   40.624251] Early unpacking initramfs... done
[   41.029213] ACPI: Core revision 20070126
[   41.029301] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   41.042836] CPU0: AMD Sempron(tm)  2000+ stepping 01
[   41.042865] Total of 1 processors activated (3337.08 BogoMIPS).
[   41.043588] ENABLING IO-APIC IRQs
[   41.043913] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   41.190221] Brought up 1 CPUs
[   41.190286] CPU0 attaching sched-domain:
[   41.190290]  domain 0: span 01
[   41.190292]   groups: 01
[   41.190528] net_namespace: 64 bytes
[   41.190538] Booting paravirtualized kernel on bare hardware
[   41.191136] Time: 11:14:57  Date: 03/22/08
[   41.191209] NET: Registered protocol family 16
[   41.191468] EISA bus registered
[   41.191504] ACPI: bus type pci registered
[   41.191947] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   41.191950] PCI: Using configuration type 1
[   41.191952] Setting up standard PCI resources
[   41.200763] ACPI: EC: Look up EC in DSDT
[   41.204684] ACPI: Interpreter enabled
[   41.204688] ACPI: (supports S0 S1 S3 S4 S5)
[   41.204706] ACPI: Using IOAPIC for interrupt routing
[   41.212529] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   41.213491] PCI: enabled onboard AC97/MC97 devices
[   41.213896] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   41.223755] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   41.223876] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 10 11 14 15)
[   41.223989] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 14 15)
[   41.224101] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 14 15)
[   41.224213] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   41.224327] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   41.224440] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   41.224552] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   41.224695] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  0A, should be 05 [20070126]
[   41.224703] Linux Plug and Play Support v0.97 (c) Adam Belay
[   41.224751] pnp: PnP ACPI init
[   41.224763] ACPI: bus type pnp registered
[   41.228860] pnp: PnP ACPI: found 11 devices
[   41.228864] ACPI: ACPI bus type pnp unregistered
[   41.228869] PnPBIOS: Disabled by ACPI PNP
[   41.229174] PCI: Using ACPI for IRQ routing
[   41.229178] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   41.238189] NET: Registered protocol family 8
[   41.238192] NET: Registered protocol family 20
[   41.238286] AppArmor: AppArmor Filesystem Enabled
[   41.242127] Time: tsc clocksource has been installed.
[   41.250174] system 00:06: ioport range 0x3e0-0x3e7 has been reserved
[   41.250179] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   41.250182] system 00:06: ioport range 0x800-0x87f has been reserved
[   41.250185] system 00:06: ioport range 0x400-0x41f has been reserved
[   41.250195] system 00:07: iomem range 0xfec80000-0xfec800ff has been reserved
[   41.250199] system 00:07: iomem range 0xfec00000-0xfec00fff has been reserved
[   41.250202] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[   41.250206] system 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
[   41.250212] system 00:08: ioport range 0x480-0x487 has been reserved
[   41.250216] system 00:08: ioport range 0xc00-0xc7f has been reserved
[   41.250225] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[   41.250229] system 00:0a: iomem range 0xc0000-0xdffff could not be reserved
[   41.250232] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[   41.250236] system 00:0a: iomem range 0x100000-0x4fffffff could not be reserved
[   41.250239] system 00:0a: iomem range 0x0-0x0 could not be reserved
[   41.280758] PCI: Bridge: 0000:00:01.0
[   41.280761]   IO window: d000-dfff
[   41.280766]   MEM window: fd300000-fd8fffff
[   41.280770]   PREFETCH window: abf00000-cbefffff
[   41.280793] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   41.280809] NET: Registered protocol family 2
[   41.318186] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   41.318632] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   41.320324] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   41.321173] TCP: Hash tables configured (established 131072 bind 65536)
[   41.321178] TCP reno registered
[   41.330260] checking if image is initramfs... it is
[   41.781767] Switched to high resolution mode on CPU 0
[   42.097824] Freeing initrd memory: 7692k freed
[   42.098640] audit: initializing netlink socket (disabled)
[   42.098659] audit(1206184497.460:1): initialized
[   42.098872] highmem bounce pool size: 64 pages
[   42.101156] VFS: Disk quotas dquot_6.5.1
[   42.101257] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   42.101428] io scheduler noop registered
[   42.101451] io scheduler anticipatory registered
[   42.101454] io scheduler deadline registered
[   42.101467] io scheduler cfq registered (default)
[   42.101487] PCI: VIA PCI bridge detected. Disabling DAC.
[   42.101498] PCI: Firmware left 0000:00:0d.0 e100 interrupts enabled, disabling
[   42.101561] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   42.101573] Boot video device is 0000:01:00.0
[   42.101933] isapnp: Scanning for PnP cards...
[   42.455680] isapnp: No Plug & Play device found
[   42.490761] Real Time Clock Driver v1.12ac
[   42.490885] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   42.491024] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.491785] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.492743] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   42.492832] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   42.493012] PNP: No PS/2 controller found. Probing ports directly.
[   42.495111] serio: i8042 KBD port at 0x60,0x64 irq 1
[   42.495117] serio: i8042 AUX port at 0x60,0x64 irq 12
[   42.501287] mice: PS/2 mouse device common for all mice
[   42.501440] EISA: Probing bus 0 at eisa.0
[   42.501450] Cannot allocate resource for EISA slot 1
[   42.501480] EISA: Detected 0 cards.
[   42.501485] cpuidle: using governor ladder
[   42.501487] cpuidle: using governor menu
[   42.501661] NET: Registered protocol family 1
[   42.501697] Using IPI No-Shortcut mode
[   42.501742] registered taskstats version 1
[   42.501890]   Magic number: 0:966:226
[   42.501973]   hash matches device ttyrd
[   42.502135] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   42.502137] EDD information not available.
[   42.502589] Freeing unused kernel memory: 364k freed
[   43.800944] fuse init (API version 7.9)
[   44.551589] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 16
[   44.551630] skge 1.13 addr 0xfe400000 irq 16 chip Yukon-Lite rev 7
[   44.551943] skge eth0: addr 00:11:2f:1e:34:fd
[   44.595875] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   44.595881] e100: Copyright(c) 1999-2006 Intel Corporation
[   44.595968] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 16 (level, low) -> IRQ 17
[   44.614066] e100: 0000:00:0d.0: e100_eeprom_load: EEPROM corrupted
[   44.614081] ACPI: PCI interrupt for device 0000:00:0d.0 disabled
[   44.663674] SCSI subsystem initialized
[   44.697506] e100: probe of 0000:00:0d.0 failed with error -11
[   44.748196] libata version 3.00 loaded.
[   44.764058] usbcore: registered new interface driver usbfs
[   44.764094] usbcore: registered new interface driver hub
[   44.791343] usbcore: registered new device driver usb
[   44.803399] pata_via 0000:00:0f.1: version 0.3.3
[   44.803448] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 18
[   44.823270] scsi0 : pata_via
[   44.847772] scsi1 : pata_via
[   44.849431] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   44.849435] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   44.860281] USB Universal Host Controller Interface driver v3.0
[   45.067620] ata1.00: ATA-6: ST3160023A, 8.01, max UDMA/100
[   45.067626] ata1.00: 312581808 sectors, multi 16: LBA48 
[   45.083543] ata1.00: configured for UDMA/100
[   45.403186] ata2.00: ATAPI: _NEC DVD_RW ND-3540A, 1.01, max UDMA/33
[   45.574956] ata2.00: configured for UDMA/33
[   45.575121] scsi 0:0:0:0: Direct-Access     ATA      ST3160023A       8.01 PQ: 0 ANSI: 5
[   45.576339] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-3540A  1.01 PQ: 0 ANSI: 5
[   45.579581] sata_via 0000:00:0f.0: version 2.3
[   45.579614] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 18
[   45.579680] sata_via 0000:00:0f.0: routed to hard irq line 10
[   45.583507] scsi2 : sata_via
[   45.584670] scsi3 : sata_via
[   45.584748] ata3: SATA max UDMA/133 cmd 0xefe0 ctl 0xefac bmdma 0xef90 irq 18
[   45.584752] ata4: SATA max UDMA/133 cmd 0xefa0 ctl 0xefa8 bmdma 0xef98 irq 18
[   45.786483] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   45.998314] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   46.009003] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 19
[   46.009019] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   46.009395] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   46.009433] uhci_hcd 0000:00:10.0: irq 19, io base 0x0000ee80
[   46.009612] usb usb1: configuration #1 chosen from 1 choice
[   46.009643] hub 1-0:1.0: USB hub found
[   46.009651] hub 1-0:1.0: 2 ports detected
[   46.110384] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 19
[   46.110402] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   46.110432] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   46.110457] uhci_hcd 0000:00:10.1: irq 19, io base 0x0000eea0
[   46.110598] usb usb2: configuration #1 chosen from 1 choice
[   46.110626] hub 2-0:1.0: USB hub found
[   46.110634] hub 2-0:1.0: 2 ports detected
[   46.214291] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 19
[   46.214309] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   46.214341] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   46.214365] uhci_hcd 0000:00:10.2: irq 19, io base 0x0000eec0
[   46.214505] usb usb3: configuration #1 chosen from 1 choice
[   46.214537] hub 3-0:1.0: USB hub found
[   46.214544] hub 3-0:1.0: 2 ports detected
[   46.318199] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 19
[   46.318217] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   46.318255] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   46.318279] uhci_hcd 0000:00:10.3: irq 19, io base 0x0000ef40
[   46.318416] usb usb4: configuration #1 chosen from 1 choice
[   46.318444] hub 4-0:1.0: USB hub found
[   46.318451] hub 4-0:1.0: 2 ports detected
[   46.422602] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 19
[   46.422621] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   46.422662] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   46.422711] ehci_hcd 0000:00:10.4: irq 19, io mem 0xfe800000
[   46.434026] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   46.434212] usb usb5: configuration #1 chosen from 1 choice
[   46.434244] hub 5-0:1.0: USB hub found
[   46.434254] hub 5-0:1.0: 8 ports detected
[   46.538431] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 20
[   46.588248] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[feb00000-feb007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   46.616058] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   46.616067] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   46.632535] Driver 'sd' needs updating - please use bus_type methods
[   46.632655] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   46.632673] sd 0:0:0:0: [sda] Write Protect is off
[   46.632677] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.632699] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.632759] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   46.632773] sd 0:0:0:0: [sda] Write Protect is off
[   46.632776] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.632795] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.632802]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   46.644025]  sda1 sda2 < sda5 >
[   46.670655] sd 0:0:0:0: [sda] Attached SCSI disk
[   46.679187] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   46.679215] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   46.681077] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   46.681086] Uniform CD-ROM driver Revision: 3.20
[   46.681168] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   46.946882] Attempting manual resume
[   46.946887] swsusp: Resume From Partition 8:5
[   46.946889] PM: Checking swsusp image.
[   46.947127] PM: Resume from disk failed.
[   46.965839] EXT3-fs: INFO: recovery required on readonly filesystem.
[   46.965846] EXT3-fs: write access will be enabled during recovery.
[   47.832840] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   47.876937] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0151003eb5]
[   48.014850] usb 2-1: configuration #1 chosen from 1 choice
[   48.256766] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   48.512392] usb 2-2: configuration #1 chosen from 1 choice
[   48.518469] usbcore: registered new interface driver hiddev
[   48.533593] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input1
[   48.548390] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-1
[   48.592501] input:   USB Keyboard as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input2
[   48.604279] input,hidraw1: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:10.1-2
[   48.690202] input:   USB Keyboard as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.1/input/input3
[   48.700196] input,hidraw2: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:10.1-2
[   48.700220] usbcore: registered new interface driver usbhid
[   48.700226] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   48.997451] kjournald starting.  Commit interval 5 seconds
[   48.997476] EXT3-fs: sda1: orphan cleanup on readonly fs
[   48.997485] ext3_orphan_cleanup: deleting unreferenced inode 16777878
[   48.997559] ext3_orphan_cleanup: deleting unreferenced inode 11075602
[   48.997568] EXT3-fs: sda1: 2 orphan inodes deleted
[   48.997571] EXT3-fs: recovery complete.
[   49.081953] EXT3-fs: mounted filesystem with ordered data mode.
[   59.799916] Linux agpgart interface v0.102
[   59.851347] agpgart: Detected VIA KT880 chipset
[   59.853567] agpgart: AGP aperture is 32M @ 0xe0000000
[   59.983171] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   60.031262] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   60.674777] input: Power Button (FF) as /devices/virtual/input/input4
[   60.690525] ACPI: Power Button (FF) [PWRF]
[   60.690699] input: Power Button (CM) as /devices/virtual/input/input5
[   60.706528] ACPI: Power Button (CM) [PWRB]
[   60.706725] input: Sleep Button (CM) as /devices/virtual/input/input6
[   60.718510] ACPI: Sleep Button (CM) [SLPB]
[   63.736832] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   63.736848] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 21
[   63.936115] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   64.359781] parport_pc 00:05: reported by Plug and Play ACPI
[   64.359826] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   64.487501] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   64.991347] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   64.991373] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   64.991699] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 16
[   64.994061] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[   65.019246] gameport: EMU10K1 is pci0000:00:13.1/gameport0, io 0xef88, speed 1217kHz
[   65.025387] PCI: Enabling device 0000:00:11.5 (0000 -> 0001)
[   65.025397] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 21
[   65.025540] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   65.537018] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   65.543165] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   65.549338] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   65.555474] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   67.668664] lp0: using parport0 (interrupt-driven).
[   67.731843] it87: Found IT8712F chip at 0xc00, revision 5
[   67.896185] Adding 3791300k swap on /dev/sda5.  Priority:-1 extents:1 across:3791300k
[   68.564533] EXT3 FS on sda1, internal journal
[   68.760238] device-mapper: uevent: version 1.0.3
[   68.760281] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   70.551072] ip_tables: (C) 2000-2006 Netfilter Core Team
[   74.407689] skge eth0: enabling interface
[   75.033439] NET: Registered protocol family 10
[   75.034334] lo: Disabled Privacy Extensions
[   75.035278] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   76.093473] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   76.094671] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   80.586096] NET: Registered protocol family 17
[   94.967008] eth0: no IPv6 routers present
[  392.078095] [drm] Initialized drm 1.1.0 20060810
[  392.092502] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[  392.092657] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[  393.614968] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  393.615826] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  393.616533] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  393.886038] [drm] Setting GART location based on new memory map
[  393.886053] [drm] Loading R300 Microcode
[  393.886094] [drm] writeback test succeeded in 1 usecs
[  411.651163] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  411.651187] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  411.651256] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  411.651269] [drm] Loading R300 Microcode
[  566.205908] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  566.205934] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  566.206003] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  566.206017] [drm] Loading R300 Microcode
[ 1179.587296] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[ 1179.587321] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 1179.587391] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 1179.587404] [drm] Loading R300 Microcode
[ 1433.097966] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[ 1433.097990] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 1433.098060] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 1433.098073] [drm] Loading R300 Microcode
[ 1612.415461] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[ 1612.415485] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 1612.415555] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 1612.415569] [drm] Loading R300 Microcode

---

### Post by keratos on 2008-03-22
I note a few problems here, including a problem with one of your filesystems (formatted ext3) and an audio codec problem (which might explain mplayer issue).

Its pretty safe to say that your kernel config and rebuild is incorrect.

I hope you remembered to keep your old linux kernel, config and directories intact and used separate dirs for building your new one. If so then just boot the old kernel at boot time.

---

### Post by ruzkie on 2008-03-22
I haven't built the kernel myself and audio works just fine with my audigy. so should i make a bug report against the ubuntu -generic kernel? im using 2.6.24-12-generic
ok meanwhile ill just use the previous kernel and with freezes i mean my computer just hangs, straight up. usb devices die and then it takes a few seconds before it's completely dead and i have to reboot

---

