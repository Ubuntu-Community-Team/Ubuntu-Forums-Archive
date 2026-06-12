---
title: "System just hangs"
date: 2008-06-21
forum: General Help
---

### Post by omar8 on 2008-06-21
I installed Ubuntu hardy heron today and for some reason at just random points it will just hang/freeze.
The first time it happened was after I was on for about 3 hours, then I restarted, it happened again about 20 mins.
Is there anyway I can find a log which specifies what is causing the issue?

---

### Post by cmnorton on 2008-06-21
Knowing a little more about your system configuration, especially your graphics card, and what you were doing at the time would help. 

The output of dmesg and tail /var/log/messages, tail /var/log/syslog, and tail /var/log/kern.log might have something to help you out.

---

### Post by omar8 on 2008-06-21
Sorry about that.
My system configuration:
Motherboard: Biostar K8VGA-M
Processor: AMD 64 3000+ @ 2.0Ghz     port754
Memory: 1gb
Graphics Card: Ati X1650Pro AGP 256mb
Hard drive: 80gb Maxtor

Dmesg Output:
```
omar@omar-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 4 16:35:01 UTC 2008 (Ubuntu 2.6.24-19.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5090
[    0.000000] Entering add_active_range(0, 0, 261872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261872
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261872
[    0.000000] On node 0 totalpages: 261872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32243 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI not present or invalid.
[    0.000000] ACPI: RSDP signature @ 0xC00F9170 checksum 0
[    0.000000] ACPI: RSDP 000F9170, 0014 (r0 VIAK8M)
[    0.000000] ACPI: RSDT 3FEF3040, 002C (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FEF30C0, 0074 (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FEF3180, 4FF8 (r1 VIAK8M AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEF0000, 0040
[    0.000000] ACPI: APIC 3FEF81C0, 005A (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] Processor #0 15:12 APIC version 17
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:bed00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259827
[    0.000000] Kernel command line: root=UUID=b1cd2091-10d4-4f17-a67f-00c40f059fbb ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1999.832 MHz processor.
[   14.271930] Console: colour VGA+ 80x25
[   14.271934] console [tty0] enabled
[   14.272665] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.273165] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.298344] Memory: 1026352k/1047488k available (2177k kernel code, 20436k reserved, 1006k data, 368k init, 129984k highmem)
[   14.298352] virtual kernel memory layout:
[   14.298353]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   14.298355]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.298356]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.298357]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.298358]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   14.298359]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   14.298360]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   14.298363] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.298411] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.378437] Calibrating delay using timer specific routine.. 4004.34 BogoMIPS (lpj=8008682)
[   14.378471] Security Framework initialized
[   14.378481] SELinux:  Disabled at boot.
[   14.378501] AppArmor: AppArmor initialized
[   14.378506] Failure registering capabilities with primary security module.
[   14.378515] Mount-cache hash table entries: 512
[   14.378656] Initializing cgroup subsys ns
[   14.378660] Initializing cgroup subsys cpuacct
[   14.378671] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   14.378679] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.378681] CPU: L2 Cache: 512K (64 bytes/line)
[   14.378685] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000 00000000
[   14.378696] Compat vDSO mapped to ffffe000.
[   14.378711] Checking 'hlt' instruction... OK.
[   14.394773] SMP alternatives: switching to UP code
[   14.396027] Freeing SMP alternatives: 11k freed
[   14.396146] Early unpacking initramfs... done
[   14.706437] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[   14.706459] Total of 1 processors activated (4004.34 BogoMIPS).
[   14.706964] ENABLING IO-APIC IRQs
[   14.707302] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   14.962462] Brought up 1 CPUs
[   14.962525] CPU0 attaching sched-domain:
[   14.962528]  domain 0: span 01
[   14.962530]   groups: 01
[   14.962690] net_namespace: 64 bytes
[   14.962694] Booting paravirtualized kernel on bare hardware
[   14.963131] Time: 20:15:09  Date: 06/21/08
[   14.963157] NET: Registered protocol family 16
[   14.963318] EISA bus registered
[   14.970984] PCI: PCI BIOS revision 2.10 entry at 0xfb820, last bus=1
[   14.970986] PCI: Using configuration type 1
[   14.970988] Setting up standard PCI resources
[   14.974694] ACPI: Interpreter disabled.
[   14.974697] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.974720] pnp: PnP ACPI: disabled
[   14.974723] PnPBIOS: Scanning system for PnP BIOS support...
[   14.974989] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc290
[   14.974995] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc2c0, dseg 0xf0000
[   14.975743] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   14.975915] PCI: Probing PCI hardware
[   14.975918] PCI: Probing PCI hardware (bus 00)
[   14.977826] PCI: Using IRQ router VIA [1106/3227] at 0000:00:11.0
[   14.977839] PCI->APIC IRQ transform: 0000:00:0f.0[B] -> IRQ 20
[   14.977842] PCI->APIC IRQ transform: 0000:00:0f.1[A] -> IRQ 20
[   14.977845] PCI->APIC IRQ transform: 0000:00:10.0[A] -> IRQ 21
[   14.977848] PCI->APIC IRQ transform: 0000:00:10.1[A] -> IRQ 21
[   14.977851] PCI->APIC IRQ transform: 0000:00:10.2[B] -> IRQ 21
[   14.977854] PCI->APIC IRQ transform: 0000:00:10.3[B] -> IRQ 21
[   14.977857] PCI->APIC IRQ transform: 0000:00:10.4[C] -> IRQ 21
[   14.977861] PCI->APIC IRQ transform: 0000:00:11.5[C] -> IRQ 22
[   14.977863] PCI->APIC IRQ transform: 0000:00:12.0[A] -> IRQ 23
[   14.977867] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 16
[   15.014473] NET: Registered protocol family 8
[   15.014475] NET: Registered protocol family 20
[   15.014532] AppArmor: AppArmor Filesystem Enabled
[   15.014563] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[   15.014566] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[   15.014569] system 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   15.014571] system 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   15.014574] system 00:07: iomem range 0x100000-0xffffff could not be reserved
[   15.014579] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[   15.014581] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[   15.014584] system 00:08: iomem range 0xf8000-0xfbfff could not be reserved
[   15.014586] system 00:08: iomem range 0xfc000-0xfffff could not be reserved
[   15.014592] system 00:0b: ioport range 0x3f0-0x3f1 has been reserved
[   15.014896] PCI: Bridge: 0000:00:01.0
[   15.014898]   IO window: c000-cfff
[   15.014902]   MEM window: f0000000-f00fffff
[   15.014905]   PREFETCH window: e0000000-efffffff
[   15.014919] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.014929] NET: Registered protocol family 2
[   15.018415] Time: tsc clocksource has been installed.
[   15.050496] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.050835] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.052125] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.052798] TCP: Hash tables configured (established 131072 bind 65536)
[   15.052801] TCP reno registered
[   15.062563] checking if image is initramfs... it is
[   15.658941] Freeing initrd memory: 7304k freed
[   15.659526] audit: initializing netlink socket (disabled)
[   15.659542] audit(1214079310.256:1): initialized
[   15.659681] highmem bounce pool size: 64 pages
[   15.661136] VFS: Disk quotas dquot_6.5.1
[   15.661205] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.661364] io scheduler noop registered
[   15.661366] io scheduler anticipatory registered
[   15.661367] io scheduler deadline registered
[   15.661376] io scheduler cfq registered (default)
[   15.661390] PCI: VIA PCI bridge detected. Disabling DAC.
[   15.661457] Boot video device is 0000:01:00.0
[   15.661651] isapnp: Scanning for PnP cards...
[   16.015831] isapnp: No Plug & Play device found
[   16.039186] Real Time Clock Driver v1.12ac
[   16.039248] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.039369] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.039930] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.040531] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.040594] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.040673] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   16.041059] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.041063] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.046551] mice: PS/2 mouse device common for all mice
[   16.046646] EISA: Probing bus 0 at eisa.0
[   16.046664] Cannot allocate resource for EISA slot 4
[   16.046680] EISA: Detected 0 cards.
[   16.046683] cpuidle: using governor ladder
[   16.046685] cpuidle: using governor menu
[   16.046771] NET: Registered protocol family 1
[   16.046792] Using IPI No-Shortcut mode
[   16.046825] registered taskstats version 1
[   16.046912]   Magic number: 12:419:296
[   16.046945]   hash matches device ttywd
[   16.047048]   hash matches device tty29
[   16.047067] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.047069] EDD information not available.
[   16.047432] Freeing unused kernel memory: 368k freed
[   16.078374] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.303458] fuse init (API version 7.9)
[   17.338861] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   17.610473] SCSI subsystem initialized
[   17.658296] libata version 3.00 loaded.
[   17.682337] usbcore: registered new interface driver usbfs
[   17.682360] usbcore: registered new interface driver hub
[   17.694344] sata_via 0000:00:0f.0: version 2.3
[   17.694412] sata_via 0000:00:0f.0: routed to hard irq line 11
[   17.698475] usbcore: registered new device driver usb
[   17.706965] scsi0 : sata_via
[   17.730765] scsi1 : sata_via
[   17.730817] ata1: SATA max UDMA/133 cmd 0xe100 ctl 0xe700 bmdma 0xe000 irq 20
[   17.730820] ata2: SATA max UDMA/133 cmd 0xe800 ctl 0xe900 bmdma 0xe008 irq 20
[   17.742262] USB Universal Host Controller Interface driver v3.0
[   17.772086] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   17.934258] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   17.970711] FDC 0 is a post-1991 82077
[   18.146247] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   18.160459] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   18.160714] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   18.160744] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000e300
[   18.160875] usb usb1: configuration #1 chosen from 1 choice
[   18.160896] hub 1-0:1.0: USB hub found
[   18.160901] hub 1-0:1.0: 2 ports detected
[   18.262347] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   18.262369] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   18.262392] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000e400
[   18.262499] usb usb2: configuration #1 chosen from 1 choice
[   18.262519] hub 2-0:1.0: USB hub found
[   18.262524] hub 2-0:1.0: 2 ports detected
[   18.366342] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   18.366369] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   18.366392] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e500
[   18.366498] usb usb3: configuration #1 chosen from 1 choice
[   18.366519] hub 3-0:1.0: USB hub found
[   18.366525] hub 3-0:1.0: 2 ports detected
[   18.470337] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   18.470364] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   18.470387] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e600
[   18.470488] usb usb4: configuration #1 chosen from 1 choice
[   18.470508] hub 4-0:1.0: USB hub found
[   18.470512] hub 4-0:1.0: 2 ports detected
[   18.574595] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   18.574621] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   18.574658] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf0100000
[   18.630240] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   18.642218] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.642323] usb usb5: configuration #1 chosen from 1 choice
[   18.642345] hub 5-0:1.0: USB hub found
[   18.642352] hub 5-0:1.0: 8 ports detected
[   18.750661] eth0: VIA Rhine II at 0xf0101000, 00:e0:4c:d8:4b:ee, IRQ 23.
[   18.751371] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   18.756312] pata_via 0000:00:0f.1: version 0.3.3
[   18.757035] scsi2 : pata_via
[   18.757505] scsi3 : pata_via
[   18.757531] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe200 irq 14
[   18.757534] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe208 irq 15
[   18.918662] ata3.00: ATA-6: WDC WD3000JB-00KFA0, 08.05J08, max UDMA/100
[   18.918667] ata3.00: 586072368 sectors, multi 16: LBA48 
[   18.918679] ata3.00: limited to UDMA/33 due to 40-wire cable
[   18.926494] ata3.00: configured for UDMA/33
[   19.254501] ata4.00: ATAPI: LITE-ON DVDRW SOHW-1673S, JS07, max UDMA/66
[   19.254683] ata4.01: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[   19.254686] ata4.01: 156250000 sectors, multi 16: LBA 
[   19.426367] ata4.00: configured for UDMA/66
[   19.442521] ata4.01: configured for UDMA/133
[   19.442627] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3000JB-00K 08.0 PQ: 0 ANSI: 5
[   19.443676] scsi 3:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1673S JS07 PQ: 0 ANSI: 5
[   19.443924] scsi 3:0:1:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[   19.454039] Driver 'sd' needs updating - please use bus_type methods
[   19.454130] sd 2:0:0:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
[   19.454143] sd 2:0:0:0: [sda] Write Protect is off
[   19.454145] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.454172] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.454212] sd 2:0:0:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
[   19.454219] sd 2:0:0:0: [sda] Write Protect is off
[   19.454222] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.454233] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.454237]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   19.474966]  sda1 sda2 < sda5 >
[   19.491085] sd 2:0:0:0: [sda] Attached SCSI disk
[   19.492040] sd 3:0:1:0: [sdb] 156250000 512-byte hardware sectors (80000 MB)
[   19.492452] sd 3:0:1:0: [sdb] Write Protect is off
[   19.492455] sd 3:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   19.493849] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   19.493853] Uniform CD-ROM driver Revision: 3.20
[   19.493898] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   19.493915] sd 3:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.493953] sd 3:0:1:0: [sdb] 156250000 512-byte hardware sectors (80000 MB)
[   19.493961] sd 3:0:1:0: [sdb] Write Protect is off
[   19.493963] sd 3:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   19.493975] sd 3:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.493979]  sdb: sdb2 < sdb5 sdb6 sdb7 >
[   19.546326] sd 3:0:1:0: [sdb] Attached SCSI disk
[   19.559397] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   19.559415] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   19.559430] sd 3:0:1:0: Attached scsi generic sg2 type 0
[   19.706152] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   19.843701] usb 5-2: configuration #1 chosen from 1 choice
[   19.858703] usbcore: registered new interface driver libusual
[   19.866945] Initializing USB Mass Storage driver...
[   19.868094] scsi4 : SCSI emulation for USB Mass Storage devices
[   19.868569] usbcore: registered new interface driver usb-storage
[   19.868573] USB Mass Storage support registered.
[   19.868668] usb-storage: device found at 2
[   19.868670] usb-storage: waiting for device to settle before scanning
[   19.977568] Attempting manual resume
[   19.977573] swsusp: Resume From Partition 8:22
[   19.977575] PM: Checking swsusp image.
[   19.977803] PM: Resume from disk failed.
[   19.992373] EXT3-fs: INFO: recovery required on readonly filesystem.
[   19.992378] EXT3-fs: write access will be enabled during recovery.
[   20.617591] kjournald starting.  Commit interval 5 seconds
[   20.617610] EXT3-fs: sdb7: orphan cleanup on readonly fs
[   20.617616] ext3_orphan_cleanup: deleting unreferenced inode 1327724
[   20.617654] ext3_orphan_cleanup: deleting unreferenced inode 557110
[   20.617660] EXT3-fs: sdb7: 2 orphan inodes deleted
[   20.617662] EXT3-fs: recovery complete.
[   20.650385] EXT3-fs: mounted filesystem with ordered data mode.
[   24.866042] usb-storage: device scan complete
[   24.866643] scsi 4:0:0:0: Direct-Access              USB DRIVE        2.00 PQ: 0 ANSI: 2
[   24.867874] sd 4:0:0:0: [sdc] 2035712 512-byte hardware sectors (1042 MB)
[   24.868499] sd 4:0:0:0: [sdc] Write Protect is off
[   24.868501] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   24.868503] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   24.871121] sd 4:0:0:0: [sdc] 2035712 512-byte hardware sectors (1042 MB)
[   24.871748] sd 4:0:0:0: [sdc] Write Protect is off
[   24.871750] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   24.871752] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   24.871755]  sdc: sdc1
[   24.872555] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   24.872583] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   31.566595] Linux agpgart interface v0.102
[   31.661529] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.701547] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.905498] agpgart: Detected AGP bridge 0
[   31.914569] agpgart: AGP aperture is 256M @ 0xd0000000
[   31.965531] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   32.559610] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   32.726427] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   32.781434] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   32.781470] [fglrx] ASYNCIO init succeed!
[   32.781635] [fglrx] PAT is enabled successfully!
[   32.789338] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   33.077803] parport_pc 00:0e: reported by Plug and Play BIOS
[   33.077854] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   33.446168] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   35.229987] lp0: using parport0 (interrupt-driven).
[   35.286027] Adding 995988k swap on /dev/sdb6.  Priority:-1 extents:1 across:995988k
[   35.821695] EXT3 FS on sdb7, internal journal
[   36.842932] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.292509] powernow_k8: Unknown symbol acpi_processor_notify_smm
[   37.292550] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[   37.292627] powernow_k8: Unknown symbol acpi_processor_register_performance
[   37.310300] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   37.310342] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   37.310469] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   37.310529] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   37.931687] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   38.186768] ppdev: user-space parallel port driver
[   38.272336] audit(1214075733.136:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4589 profile="/usr/sbin/cupsd" namespace="default"
[   41.291663] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   41.387685] Bluetooth: Core ver 2.11
[   41.388336] NET: Registered protocol family 31
[   41.388340] Bluetooth: HCI device and connection manager initialized
[   41.388344] Bluetooth: HCI socket layer initialized
[   41.450556] Bluetooth: L2CAP ver 2.9
[   41.450562] Bluetooth: L2CAP socket layer initialized
[   41.549558] Bluetooth: RFCOMM socket layer initialized
[   41.549577] Bluetooth: RFCOMM TTY layer initialized
[   41.549579] Bluetooth: RFCOMM ver 1.8
[   43.498920] NET: Registered protocol family 17
[   44.759541] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   44.759549] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   44.759554] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
[   44.760114] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   44.760269] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   44.760457] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   44.760603] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[   44.929221] [fglrx] Reserve Block - 0 offset =  0Xfffb000 length = 0X5000
[   44.929228] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   44.929231] [fglrx] Reserve Block - 2 offset =  0Xff7b000 length = 0X80000
[   45.031769] [fglrx] interrupt source 10000000 successfully enabled
[   45.031776] [fglrx] enable ID = 0x00000008
[   45.032084] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   47.506490] NET: Registered protocol family 10
[   47.506899] lo: Disabled Privacy Extensions
[   58.143903] eth0: no IPv6 routers present
[   65.463385] UDF-fs: No VRS found
[   65.559312] ISO 9660 Extensions: Microsoft Joliet Level 1
[   65.560226] ISOFS: changing to secondary root
omar@omar-desktop:~$ 

```

tail /var/log/messages output:
```
omar@omar-desktop:~$ tail /var/log/messages
Jun 21 20:15:39 omar-desktop kernel: [   45.032084] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Jun 21 20:15:41 omar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun 21 20:15:41 omar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun 21 20:15:41 omar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 21 20:15:41 omar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 21 20:15:41 omar-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun 21 20:15:42 omar-desktop kernel: [   47.506490] NET: Registered protocol family 10
Jun 21 20:15:42 omar-desktop kernel: [   47.506899] lo: Disabled Privacy Extensions
Jun 21 20:15:49 omar-desktop pulseaudio[5252]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 21 20:16:01 omar-desktop kernel: [   65.463385] UDF-fs: No VRS found
omar@omar-desktop:~$ 

```

tail /var/log/syslog output:
```
omar@omar-desktop:~$ tail /var/log/syslog
Jun 21 20:15:52 omar-desktop hcid[4850]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Jun 21 20:15:52 omar-desktop hcid[4850]: Default authorization agent (:1.20, /org/bluez/auth) registered
Jun 21 20:15:54 omar-desktop kernel: [   58.143903] eth0: no IPv6 routers present
Jun 21 20:15:57 omar-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Jun 21 20:15:57 omar-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun 21 20:16:01 omar-desktop kernel: [   65.463385] UDF-fs: No VRS found
Jun 21 20:16:01 omar-desktop kernel: [   65.559312] ISO 9660 Extensions: Microsoft Joliet Level 1
Jun 21 20:16:01 omar-desktop kernel: [   65.560226] ISOFS: changing to secondary root
Jun 21 20:16:02 omar-desktop hald: mounted /dev/sdc1 on behalf of uid 1000
Jun 21 20:17:01 omar-desktop /USR/SBIN/CRON[5454]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
omar@omar-desktop:~$ 

```

tail /var/log/kern.log output:
```
omar@omar-desktop:~$ tail /var/log/kern.log
Jun 21 20:15:39 omar-desktop kernel: [   44.929231] [fglrx] Reserve Block - 2 offset =  0Xff7b000 length = 0X80000
Jun 21 20:15:39 omar-desktop kernel: [   45.031769] [fglrx] interrupt source 10000000 successfully enabled
Jun 21 20:15:39 omar-desktop kernel: [   45.031776] [fglrx] enable ID = 0x00000008
Jun 21 20:15:39 omar-desktop kernel: [   45.032084] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Jun 21 20:15:42 omar-desktop kernel: [   47.506490] NET: Registered protocol family 10
Jun 21 20:15:42 omar-desktop kernel: [   47.506899] lo: Disabled Privacy Extensions
Jun 21 20:15:54 omar-desktop kernel: [   58.143903] eth0: no IPv6 routers present
Jun 21 20:16:01 omar-desktop kernel: [   65.463385] UDF-fs: No VRS found
Jun 21 20:16:01 omar-desktop kernel: [   65.559312] ISO 9660 Extensions: Microsoft Joliet Level 1
Jun 21 20:16:01 omar-desktop kernel: [   65.560226] ISOFS: changing to secondary root
omar@omar-desktop:~$ 

```

---

### Post by omar8 on 2008-06-21
I think it could be something to do with flash, because it has not crashed in a while and when it did, I was watching youtube each time.

---

### Post by omar8 on 2008-06-22
When I shut down the computer it also goes from that:

[CENTER]UBUNTU
|==========================================|[/CENTER]

to a message saying that the network manager has failed.
Anyone able to link these things to help me fix the installation?

---

### Post by cmnorton on 2008-06-22
This post

[http://ubuntuforums.org/showthread.php?t=836387](http://ubuntuforums.org/showthread.php?t=836387)

contains a reference to 8.04.1 hanging.

---

### Post by omar8 on 2008-06-22
Thanks, it says that it is a common problem and that it should be corrected later on, I think I might just try fedora until July :)
Well, at least I know it is not my fault.

---

### Post by cmnorton on 2008-06-22
Better yet, 7.10 is a good release. 

I have used Fedora for one of our test systems. I like Fedora, except one thing. Ubuntu updates are available for a long time. I was dismayed when Fedora 6 stopped getting updates. It's not their fault; I did not read the fine print.

For me, it is hard to change distros, especially when running on my workstation.

---

### Post by francesco44 on 2008-06-22
Hello everybody,

My system on a thinkpad X30 with a pentium M 1,2 mhz and 512 of memory......just HANG and FREEZE randomly (quite often in fact).

This is an "absolute bug" which forbid any professional use of 8.04

It should be corrected QUICKLY if UBUNTU wants to keep its reputation.

If I were Canonical or Mark S I would devote no less than 1 millions $ to the solution.....

By the way it is a very good system EXCEPT for that BUG....

No other solution than to rely on an older version (7,10?)....or Windows XP with shame and disgust...but we Have to be productive everyday.....

---

