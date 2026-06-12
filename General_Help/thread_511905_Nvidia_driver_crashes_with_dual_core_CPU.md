---
title: "Nvidia driver crashes with dual core CPU?"
date: 2007-07-28
forum: General Help
---

### Post by PatrickMay16 on 2007-07-28
I just got a dual core Opteron processor. Before that, nvidia's drivers worked fine for me. But now, when I play a game or do something intensive with the video card (eg. Unreal 2003, yabause, etc), after a while the screen may freeze but the mouse can still move. It's not possible to use ctrl+alt+backspace or ctrl+alt+f*.

I can still get in through ssh. This turns up in the output of dmesg:
```

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000005fdf0000 end: 000000005fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000005fef0000 size: 0000000000003000 end: 000000005fef3000 type: 4
[    0.000000] copy_e820_map() start: 000000005fef3000 size: 000000000000d000 end: 000000005ff00000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fef0000 (usable)
[    0.000000]  BIOS-e820: 000000005fef0000 - 000000005fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005fef3000 - 000000005ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 638MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f36a0
[    0.000000] Entering add_active_range(0, 0, 392944) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   392944
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   392944
[    0.000000] On node 0 totalpages: 392944
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1277 pages used for memmap
[    0.000000]   HighMem zone: 162291 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 VIAK8T                                ) @ 0x000f77d0
[    0.000000] ACPI: RSDT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fef3040
[    0.000000] ACPI: FADT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fef30c0
[    0.000000] ACPI: BOOT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fef8180
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x5fef82c0
[    0.000000] ACPI: MADT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fef8200
[    0.000000] ACPI: DSDT (v001 VIAK8T AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5ff00000:9ed00000)
[    0.000000] Detected 2393.088 MHz processor.
[   18.567895] Built 1 zonelists.  Total pages: 389875
[   18.567898] Kernel command line: root=UUID=f43fcb76-43d7-4ac3-a3e0-e096b45fa819 ro quiet splash
[   18.568003] mapped APIC to ffffd000 (fee00000)
[   18.568005] mapped IOAPIC to ffffc000 (fec00000)
[   18.568008] Enabling fast FPU save and restore... done.
[   18.568010] Enabling unmasked SIMD FPU exception support... done.
[   18.568016] Initializing CPU#0
[   18.568085] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   18.570421] Console: colour VGA+ 80x25
[   18.570837] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.571203] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.606401] Memory: 1545692k/1571776k available (1992k kernel code, 24924k reserved, 900k data, 328k init, 654272k highmem)
[   18.606409] virtual kernel memory layout:
[   18.606409]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.606410]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.606411]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.606412]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.606413]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   18.606415]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   18.606416]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   18.606418] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.683844] Calibrating delay using timer specific routine.. 4791.52 BogoMIPS (lpj=9583055)
[   18.683876] Security Framework v1.0.0 initialized
[   18.683882] SELinux:  Disabled at boot.
[   18.683894] Mount-cache hash table entries: 512
[   18.684006] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[   18.684013] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.684015] CPU: L2 Cache: 1024K (64 bytes/line)
[   18.684018] CPU 0(2) -> Core 0
[   18.684019] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[   18.684028] Compat vDSO mapped to ffffe000.
[   18.684032] Remapping vsyscall page to ffffe000
[   18.684040] Checking 'hlt' instruction... OK.
[   18.699926] SMP alternatives: switching to UP code
[   18.700278] Early unpacking initramfs... done
[   18.974635] ACPI: Core revision 20060707
[   18.978719] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   19.139585] CPU0: AMD Dual Core AMD Opteron(tm) Processor 175    stepping 02
[   19.139604] SMP alternatives: switching to SMP code
[   19.139650] Booting processor 1/1 eip 3000
[   19.150124] Initializing CPU#1
[   19.230933] Calibrating delay using timer specific routine.. 4785.96 BogoMIPS (lpj=9571922)
[   19.230939] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[   19.230944] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   19.230946] CPU: L2 Cache: 1024K (64 bytes/line)
[   19.230948] CPU 1(2) -> Core 1
[   19.230949] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[   19.230873] CPU1: AMD Dual Core AMD Opteron(tm) Processor 175    stepping 02
[   19.230889] Total of 2 processors activated (9577.48 BogoMIPS).
[   19.231394] ENABLING IO-APIC IRQs
[   19.231717] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   19.378346] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -140 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 140 usecs TSC skew, fixed it up.
[    0.003996] Brought up 2 CPUs
[    0.156718] migration_cost=593
[    0.156913] Booting paravirtualized kernel on bare hardware
[    0.157009] Time: 15:19:01  Date: 06/28/107
[    0.157039] NET: Registered protocol family 16
[    0.157102] EISA bus registered
[    0.157105] ACPI: bus type pci registered
[    0.164685] PCI: PCI BIOS revision 2.10 entry at 0xfa090, last bus=1
[    0.164687] PCI: Using configuration type 1
[    0.164688] Setting up standard PCI resources
[    0.174304] ACPI: Interpreter enabled
[    0.174308] ACPI: Using IOAPIC for interrupt routing
[    0.174790] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.174793] PCI: Probing PCI hardware (bus 00)
[    0.175760] Boot video device is 0000:01:00.0
[    0.175799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.237122] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
[    0.237410] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.237700] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[    0.237980] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.238245] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.238505] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.238774] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 *10 11 12)
[    0.239040] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 *10 11 12)
[    0.239453] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[    0.239855] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.240157] ACPI: PCI Interrupt Link [ALKC] (IRQs *22), disabled.
[    0.240513] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
[    0.242505] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.242513] pnp: PnP ACPI init
[    0.246285] pnp: PnP ACPI: found 13 devices
[    0.246288] PnPBIOS: Disabled by ACPI PNP
[    0.246321] PCI: Using ACPI for IRQ routing
[    0.246323] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.270397] NET: Registered protocol family 8
[    0.270398] NET: Registered protocol family 20
[    0.270691] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[    0.270693] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[    0.270911] PCI: Bridge: 0000:00:01.0
[    0.270913]   IO window: disabled.
[    0.270916]   MEM window: f8000000-faffffff
[    0.270919]   PREFETCH window: e0000000-efffffff
[    0.270931] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.270965] NET: Registered protocol family 2
[    0.311384] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.311489] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.312053] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.312362] TCP: Hash tables configured (established 131072 bind 65536)
[    0.312364] TCP reno registered
[    0.323410] checking if image is initramfs... it is
[    0.865310] Freeing initrd memory: 8093k freed
[    0.865415] Simple Boot Flag at 0x37 set to 0x1
[    1.416000] audit: initializing netlink socket (disabled)
[    1.416000] audit(1185635941.600:1): initialized
[    1.416000] highmem bounce pool size: 64 pages
[    1.416000] VFS: Disk quotas dquot_6.5.1
[    1.416000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.416000] io scheduler noop registered
[    1.416000] io scheduler anticipatory registered
[    1.416000] io scheduler deadline registered
[    1.416000] io scheduler cfq registered (default)
[    1.420000] isapnp: Scanning for PnP cards...
[    1.772000] isapnp: No Plug & Play device found
[    1.788000] Real Time Clock Driver v1.12ac
[    1.788000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.788000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.788000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.788000] mice: PS/2 mouse device common for all mice
[    1.788000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.788000] input: Macintosh mouse button emulation as /class/input/input0
[    1.788000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.788000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.788000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.792000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.792000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.792000] EISA: Probing bus 0 at eisa.0
[    1.792000] Cannot allocate resource for EISA slot 4
[    1.792000] Cannot allocate resource for EISA slot 5
[    1.792000] EISA: Detected 0 cards.
[    1.820000] TCP cubic registered
[    1.820000] NET: Registered protocol family 1
[    1.820000] Starting balanced_irq
[    1.820000] Using IPI No-Shortcut mode
[    1.820000] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.820000] ACPI: (supports S0 S3 S4 S5)
[    1.820000]   Magic number: 15:970:336
[    1.820000]   hash matches device ttyzb
[    1.820000]   hash matches device tty57
[    1.824000] Time: acpi_pm clocksource has been installed.
[    1.824000] Freeing unused kernel memory: 328k freed
[    2.996000] Capability LSM initialized
[    3.008000] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[    3.092000] md: linear personality registered for level -1
[    3.096000] md: multipath personality registered for level -4
[    3.096000] md: raid0 personality registered for level 0
[    3.100000] md: raid1 personality registered for level 1
[    3.104000] raid5: automatically using best checksumming function: pIII_sse
[    3.124000]    pIII_sse  :  7329.000 MB/sec
[    3.124000] raid5: using function: pIII_sse (7329.000 MB/sec)
[    3.192000] raid6: int32x1   1019 MB/s
[    3.260000] raid6: int32x2   1038 MB/s
[    3.328000] raid6: int32x4    861 MB/s
[    3.396000] raid6: int32x8    644 MB/s
[    3.464000] raid6: mmxx1     1923 MB/s
[    3.532000] raid6: mmxx2     3563 MB/s
[    3.600000] raid6: sse1x1    1795 MB/s
[    3.668000] raid6: sse1x2    2882 MB/s
[    3.736000] raid6: sse2x1    3025 MB/s
[    3.804000] raid6: sse2x2    3875 MB/s
[    3.804000] raid6: using algorithm sse2x2 (3875 MB/s)
[    3.804000] md: raid6 personality registered for level 6
[    3.804000] md: raid5 personality registered for level 5
[    3.804000] md: raid4 personality registered for level 4
[    3.804000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[    3.804000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    3.804000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[    3.804000] VP_IDE: chipset revision 6
[    3.804000] VP_IDE: not 100% native mode: will probe irqs later
[    3.804000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[    3.804000]     ide0: BM-DMA at 0xe300-0xe307, BIOS settings: hda:DMA, hdb:DMA
[    3.804000]     ide1: BM-DMA at 0xe308-0xe30f, BIOS settings: hdc:DMA, hdd:pio
[    3.804000] Probing IDE interface ide0...
[    3.816000] usbcore: registered new interface driver usbfs
[    3.816000] usbcore: registered new interface driver hub
[    3.816000] SCSI subsystem initialized
[    3.828000] usbcore: registered new device driver usb
[    3.832000] Floppy drive(s): fd0 is 1.44M
[    3.836000] libata version 2.20 loaded.
[    3.848000] USB Universal Host Controller Interface driver v3.0
[    3.852000] FDC 0 is a post-1991 82077
[    3.852000] ieee1394: Initialized config rom entry `ip1394'
[    3.868000] md: raid10 personality registered for level 10
[    4.220000] hda: Maxtor 6Y080L0, ATA DISK drive
[    4.500000] hdb: Maxtor 6Y120P0, ATA DISK drive
[    4.556000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.588000] Probing IDE interface ide1...
[    5.452000] hdc: AOPEN CRW5232/AAO PRO, ATAPI CD/DVD-ROM drive
[    6.124000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.124000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
[    6.124000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    6.124000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    6.124000] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000e400
[    6.124000] usb usb1: configuration #1 chosen from 1 choice
[    6.124000] hub 1-0:1.0: USB hub found
[    6.124000] hub 1-0:1.0: 2 ports detected
[    6.228000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 17
[    6.228000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    6.228000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 2
[    6.228000] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfb021000
[    6.228000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.228000] usb usb2: configuration #1 chosen from 1 choice
[    6.228000] hub 2-0:1.0: USB hub found
[    6.228000] hub 2-0:1.0: 8 ports detected
[    6.332000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 23 (level, low) -> IRQ 18
[    6.384000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[fb022000-fb0227ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.392000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 17
[    6.392000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    6.392000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    6.392000] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000e500
[    6.392000] usb usb3: configuration #1 chosen from 1 choice
[    6.392000] hub 3-0:1.0: USB hub found
[    6.392000] hub 3-0:1.0: 2 ports detected
[    6.496000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 17
[    6.496000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    6.496000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    6.496000] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000e600
[    6.496000] usb usb4: configuration #1 chosen from 1 choice
[    6.496000] hub 4-0:1.0: USB hub found
[    6.496000] hub 4-0:1.0: 2 ports detected
[    6.600000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 17
[    6.600000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    6.600000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    6.600000] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000e700
[    6.600000] usb usb5: configuration #1 chosen from 1 choice
[    6.600000] hub 5-0:1.0: USB hub found
[    6.600000] hub 5-0:1.0: 2 ports detected
[    6.704000] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
[    6.704000] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
[    6.704000] Copyright (c) 2004 Red Hat Inc.
[    6.704000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 22 (level, low) -> IRQ 19
[    6.704000] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter
[    6.704000] eth0: Ethernet Address: 00:50:8D:D1:30:33
[    6.720000] sata_via 0000:00:0f.0: version 2.1
[    6.720000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[    6.720000] sata_via 0000:00:0f.0: routed to hard irq line 11
[    6.720000] ata1: SATA max UDMA/133 cmd 0x0001dd00 ctl 0x0001de02 bmdma 0x0001e100 irq 16
[    6.720000] ata2: SATA max UDMA/133 cmd 0x0001df00 ctl 0x0001e002 bmdma 0x0001e108 irq 16
[    6.720000] scsi0 : sata_via
[    6.724000] usb 2-8: new high speed USB device using ehci_hcd and address 2
[    6.856000] usb 2-8: configuration #1 chosen from 1 choice
[    6.856000] hub 2-8:1.0: USB hub found
[    6.856000] hub 2-8:1.0: 4 ports detected
[    6.924000] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    6.932000] ATA: abnormal status 0x7F on port 0x0001dd07
[    6.932000] scsi1 : sata_via
[    7.136000] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    7.144000] ATA: abnormal status 0x7F on port 0x0001df07
[    7.152000] hda: max request size: 128KiB
[    7.152000] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[    7.152000] hda: cache flushes supported
[    7.152000]  hda: hda1
[    7.160000] hdb: max request size: 128KiB
[    7.160000] hdb: 240121728 sectors (122942 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(133)
[    7.160000] hdb: cache flushes supported
[    7.160000]  hdb: hdb1 hdb2 < hdb5 >
[    7.192000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.192000] Uniform CD-ROM driver Revision: 3.20
[    7.388000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.388000] EXT3-fs: write access will be enabled during recovery.
[    7.480000] kjournald starting.  Commit interval 5 seconds
[    7.480000] EXT3-fs: recovery complete.
[    7.480000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.664000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508d0000d03033]
[    7.928000] usb 2-8.3: new high speed USB device using ehci_hcd and address 3
[    8.020000] usb 2-8.3: configuration #1 chosen from 1 choice
[   20.368000] Velocity is AUTO mode
[   20.540000] NET: Registered protocol family 10
[   20.540000] lo: Disabled Privacy Extensions
[   20.540000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.200000] gameport: EMU10K1 is pci0000:00:08.1/gameport0, io 0xe800, speed 1193kHz
[   21.264000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.268000] agpgart: Detected AGP bridge 0
[   21.272000] agpgart: AGP aperture is 128M @ 0xf0000000
[   21.468000] parport: PnPBIOS parport detected.
[   21.468000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   21.492000] input: GenPS/2 Genius Mouse as /class/input/input2
[   21.536000] input: PC Speaker as /class/input/input3
[   21.576000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.576000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.700000] nvidia: module license 'NVIDIA' taints kernel.
[   21.952000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   21.952000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   22.016000] usbcore: registered new interface driver libusual
[   22.020000] eth0: Link autonegation speed 100M bps full duplex
[   22.020000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.088000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 20
[   22.156000] Initializing USB Mass Storage driver...
[   22.156000] scsi2 : SCSI emulation for USB Mass Storage devices
[   22.156000] usbcore: registered new interface driver usb-storage
[   22.156000] USB Mass Storage support registered.
[   22.156000] usb-storage: device found at 3
[   22.156000] usb-storage: waiting for device to settle before scanning
[   22.264000] Intel ISA PCIC probe: not found.
[   22.348000] lp0: using parport0 (interrupt-driven).
[   22.484000] Adding 1502036k swap on /dev/disk/by-uuid/110a63a9-dfa2-4a29-85f6-0f4f4269c19c.  Priority:-1 extents:1 across:1502036k
[   22.568000] EXT3 FS on hdb1, internal journal
[   23.096000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   23.124000] NTFS volume version 3.0.
[   23.936000] input: Power Button (FF) as /class/input/input4
[   23.936000] ACPI: Power Button (FF) [PWRF]
[   23.936000] input: Power Button (CM) as /class/input/input5
[   23.936000] ACPI: Power Button (CM) [PWRB]
[   23.976000] Using specific hotkey driver
[   24.016000] No dock devices found.
[   24.048000] ibm_acpi: ec object not found
[   24.164000] pcc_acpi: loading...
[   27.156000] usb-storage: device scan complete
[   27.156000] scsi 2:0:0:0: Direct-Access     Generic  IC1230-M      CF 0.1E PQ: 0 ANSI: 0 CCS
[   27.160000] scsi 2:0:0:1: Direct-Access     Generic  IC1230-M      MS 0.1E PQ: 0 ANSI: 0 CCS
[   27.372000] scsi 2:0:0:2: Direct-Access     Generic  IC1230-M  MMC/SD 0.1E PQ: 0 ANSI: 0 CCS
[   27.372000] scsi 2:0:0:3: Direct-Access     Generic  IC1230-M      SM 0.1E PQ: 0 ANSI: 0 CCS
[   27.408000] sd 2:0:0:0: Attached scsi removable disk sda
[   27.408000] sd 2:0:0:1: Attached scsi removable disk sdb
[   27.412000] SCSI device sdc: 499712 512-byte hdwr sectors (256 MB)
[   27.412000] sdc: Write Protect is off
[   27.412000] sdc: Mode Sense: 4b 00 00 08
[   27.412000] sdc: assuming drive cache: write through
[   27.412000] SCSI device sdc: 499712 512-byte hdwr sectors (256 MB)
[   27.416000] sdc: Write Protect is off
[   27.416000] sdc: Mode Sense: 4b 00 00 08
[   27.416000] sdc: assuming drive cache: write through
[   27.416000]  sdc: sdc1
[   27.416000] sd 2:0:0:2: Attached scsi removable disk sdc
[   27.416000] sd 2:0:0:3: Attached scsi removable disk sdd
[   27.436000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   27.436000] sd 2:0:0:1: Attached scsi generic sg1 type 0
[   27.436000] sd 2:0:0:2: Attached scsi generic sg2 type 0
[   27.436000] sd 2:0:0:3: Attached scsi generic sg3 type 0
[   30.564000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   30.564000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   30.564000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   31.624000] ppdev: user-space parallel port driver
[   32.056000] apm: BIOS not found.
[   32.712000] eth0: no IPv6 routers present
[   33.432000] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   33.432000] vboxdrv: Successfully done.
[   33.884000] Bluetooth: Core ver 2.11
[   33.884000] NET: Registered protocol family 31
[   33.884000] Bluetooth: HCI device and connection manager initialized
[   33.884000] Bluetooth: HCI socket layer initialized
[   33.908000] Bluetooth: L2CAP ver 2.8
[   33.908000] Bluetooth: L2CAP socket layer initialized
[   34.028000] Bluetooth: RFCOMM socket layer initialized
[   34.028000] Bluetooth: RFCOMM TTY layer initialized
[   34.028000] Bluetooth: RFCOMM ver 1.8
[   77.900000] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   78.076000] usb 4-2: configuration #1 chosen from 1 choice
[   78.172000] usbcore: registered new interface driver xpad
[   78.172000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   78.184000] usbcore: registered new interface driver hiddev
[   78.288000] input: Saitek PLC Cyborg Force Rumble Pad as /class/input/input6
[   78.288000] input: USB HID v1.10 Joystick [Saitek PLC Cyborg Force Rumble Pad] on usb-0000:00:10.2-2
[   78.288000] usbcore: registered new interface driver usbhid
[   78.288000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[ 8864.692000] NVRM: Xid (0001:00): 8, Channel 00000002
[ 8864.692000] NVRM: Xid (0001:00): 29,  L1 -> L0
[ 8876.736000] NVRM: Xid (0001:00): 8, Channel 00000020
[ 8876.736000] NVRM: Xid (0001:00): 29,  L0 -> L0
[ 8889.780000] NVRM: Xid (0001:00): 8, Channel 00000020
[ 8902.828000] NVRM: Xid (0001:00): 8, Channel 00000020
[ 8914.872000] NVRM: Xid (0001:00): 8, Channel 00000020
[ 8927.916000] NVRM: Xid (0001:00): 8, Channel 00000020
[ 8939.944000] NVRM: Xid (0001:00): 8, Channel 00000020
[ 8952.988000] NVRM: Xid (0001:00): 8, Channel 00000020
[ 8965.036000] NVRM: Xid (0001:00): 8, Channel 00000020
[ 8978.080000] NVRM: Xid (0001:00): 8, Channel 00000020
[ 8991.124000] NVRM: Xid (0001:00): 8, Channel 00000020
[ 9013.600000] BUG: soft lockup detected on CPU#1!
[ 9013.600000]  [<c015354c>] softlockup_tick+0x9c/0xf0
[ 9013.600000]  [<c0130643>] update_process_times+0x33/0x80
[ 9013.600000]  [<c01154b0>] smp_apic_timer_interrupt+0x70/0x80
[ 9013.600000]  [<c01042f8>] apic_timer_interrupt+0x28/0x30
[ 9013.600000]  [<f916d8ec>] _nv002718rm+0x14/0x18 [nvidia]
[ 9013.600000]  [<f92edb65>] _nv005692rm+0x75/0xa0 [nvidia]
[ 9013.600000]  [<c01154b5>] smp_apic_timer_interrupt+0x75/0x80
[ 9013.600000]  [<f92e5121>] _nv006552rm+0x181/0x594 [nvidia]
[ 9013.600000]  [<f915aeba>] _nv002933rm+0x26/0x2c [nvidia]
[ 9013.600000]  [<f92edb65>] _nv005692rm+0x75/0xa0 [nvidia]
[ 9013.600000]  [<f92e70a1>] _nv007696rm+0x195/0x1cc [nvidia]
[ 9013.600000]  [<f92e7090>] _nv007696rm+0x184/0x1cc [nvidia]
[ 9013.600000]  [<f92edb65>] _nv005692rm+0x75/0xa0 [nvidia]
[ 9013.600000]  [<f92ee0d0>] _nv005894rm+0x28/0x44 [nvidia]
[ 9013.600000]  [<f92e743e>] _nv006655rm+0x102/0x1bc [nvidia]
[ 9013.600000]  [<f92ee197>] _nv005892rm+0x23/0x28 [nvidia]
[ 9013.600000]  [<f9351d8c>] _nv004295rm+0xb8/0xc4 [nvidia]
[ 9013.600000]  [<f92ccc6b>] _nv006557rm+0x4f/0x13c [nvidia]
[ 9013.600000]  [<f92ccc80>] _nv006557rm+0x64/0x13c [nvidia]
[ 9013.600000]  [<f913deb7>] _nv009861rm+0x13/0x38 [nvidia]
[ 9013.600000]  [<f92e769d>] _nv006462rm+0x45/0xc8 [nvidia]
[ 9013.600000]  [<f913deb7>] _nv009861rm+0x13/0x38 [nvidia]
[ 9013.600000]  [<f92cf343>] _nv006585rm+0x1f/0x28 [nvidia]
[ 9013.600000]  [<f913deb7>] _nv009861rm+0x13/0x38 [nvidia]
[ 9013.600000]  [<f9141cef>] _nv009864rm+0x1f/0x130 [nvidia]
[ 9013.600000]  [<f914171a>] _nv009828rm+0x16/0x34 [nvidia]
[ 9013.600000]  [<f9141cef>] _nv009864rm+0x1f/0x130 [nvidia]
[ 9013.600000]  [<f916a04e>] _nv001952rm+0x32/0x244 [nvidia]
[ 9013.600000]  [<f9141787>] _nv009886rm+0x4f/0xd4 [nvidia]
[ 9013.600000]  [<f914f670>] _nv002043rm+0x3d0/0x400 [nvidia]
[ 9013.600000]  [<f914f64a>] _nv002043rm+0x3aa/0x400 [nvidia]
[ 9013.600000]  [<f913ecbf>] _nv009799rm+0x83/0xc4 [nvidia]
[ 9013.600000]  [<f913f3ae>] _nv009857rm+0x22/0x50 [nvidia]
[ 9013.600000]  [<f914ed9a>] _nv002038rm+0x86/0x274 [nvidia]
[ 9013.600000]  [<f913eb72>] _nv009850rm+0x16/0x3c [nvidia]
[ 9013.600000]  [<f914ec6a>] _nv002041rm+0x72/0x11c [nvidia]
[ 9013.600000]  [<f914e9dd>] _nv002044rm+0x3d/0x258 [nvidia]
[ 9013.600000]  [<f916bcb3>] _nv002687rm+0x1b/0x20 [nvidia]
[ 9013.600000]  [<f917324a>] _nv002020rm+0x52/0x78 [nvidia]
[ 9013.600000]  [<f917323d>] _nv002020rm+0x45/0x78 [nvidia]
[ 9013.600000]  [<f916c20a>] _nv002769rm+0x12/0x18 [nvidia]
[ 9013.600000]  [<f91749ea>] rm_free_unused_clients+0x2e/0x7c [nvidia]
[ 9013.600000]  [<f9174a18>] rm_free_unused_clients+0x5c/0x7c [nvidia]
[ 9013.600000]  [<c011e678>] __wake_up+0x38/0x50
[ 9013.600000]  [<f93ef167>] nv_kern_ctl_close+0x6c/0x8a [nvidia]
[ 9013.600000]  [<f93f09ae>] nv_kern_close+0x40/0x2f6 [nvidia]
[ 9013.600000]  [<c0177757>] __fput+0xa7/0x190
[ 9013.600000]  [<c0174af7>] filp_close+0x47/0x80
[ 9013.600000]  [<c01281af>] put_files_struct+0x8f/0xb0
[ 9013.600000]  [<c0129324>] do_exit+0x134/0x800
[ 9013.600000]  [<c0130180>] lock_timer_base+0x20/0x50
[ 9013.600000]  [<c01302b8>] __mod_timer+0x98/0xb0
[ 9013.600000]  [<c0129a16>] do_group_exit+0x26/0x80
[ 9013.600000]  [<c0133149>] get_signal_to_deliver+0x2a9/0x420
[ 9013.600000]  [<c0102803>] do_notify_resume+0x93/0x720
[ 9013.600000]  [<c0261bfe>] ide_intr+0xce/0x1f0
[ 9013.600000]  [<c0106c19>] timer_interrupt+0x59/0xb0
[ 9013.600000]  [<c01538d0>] handle_IRQ_event+0x30/0x60
[ 9013.600000]  [<c0155027>] handle_edge_irq+0x67/0x130
[ 9013.600000]  [<c0105b75>] do_IRQ+0x45/0x80
[ 9013.600000]  [<c010334b>] work_notifysig+0x13/0x18
[ 9013.600000]  =======================
```

I'm not sure what to do with this. Is this an nvidia driver bug? Or is something else the matter? Does anyone know what might help?

BTW, this is with nvidia driver 1.0-9631

---

### Post by MrHippocampus on 2007-07-28
Ive had something similar to this problem, although that was because my graphics card was dying :'(. There were a few posts about it on the [nvidia linux forum]("http://http://www.nvnews.net/vbulletin/forumdisplay.php?f=14"). So I suggest looking/posting on there (if you do post read the FAQ about bug reports!)

edit: I'm sure your card is fine, I just neglected to fix a capacitor which lost its footing on my card, my own fault really....

---

### Post by PatrickMay16 on 2007-07-28
I just found now that it doesn't matter if I'm doing video intensive things at all, it just crashed while I was typing up a forum post in firefox.

---

### Post by PatrickMay16 on 2007-08-08
Just so everyone knows, it turns out that the problem was, I had set the CPU speed higher than the factory setting. I changed it to its factory setting, and then it began working correctly. 
Then I spoke with a friend who knows how to overclock properly, and he helped me out. Now I have it running 300MHz over the factory speed and it's working stable.

---

