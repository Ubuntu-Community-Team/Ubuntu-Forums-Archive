---
title: "slow starting"
date: 2008-02-03
forum: General Help
---

### Post by gishaust on 2008-02-03
hi everyone,

I have installed xubuntu on my machine and it works great once it starts. It takes  4mins to start I have 191meg of ram  and I don't know the cpu. How do I  know if the machine is slow to start because of the ram or something needs to the fixed.

gishaust

---

### Post by gmaniac on 2008-02-03
from a console, paste the output of ```
dmesg
```

---

### Post by gishaust on 2008-02-03
Sorry for the late reply  this is what dmesg reported

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bf70000 (usable)
[    0.000000]  BIOS-e820: 000000000bf70000 - 000000000bf7c000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000bf7c000 - 000000000bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000bf80000 - 000000000c000000 (reserved)
[    0.000000]  BIOS-e820: 000000001bf80000 - 000000001c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 191MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 49008) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    49008
[    0.000000]   HighMem     49008 ->    49008
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    49008
[    0.000000] On node 0 totalpages: 49008
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 350 pages used for memmap
[    0.000000]   Normal zone: 44562 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6AD0 checksum 0
[    0.000000] ACPI: RSDP 000F6AD0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0BF752A8, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 0BF7BF64, 0074 (r1 ATI    Salmon    6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 0BF752D4, 6C90 (r1    ATI MS2_1535  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 0BF7CFC0, 0040
[    0.000000] ACPI: BOOT 0BF7BFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3f80000)
[    0.000000] Built 1 zonelists.  Total pages: 48626
[    0.000000] Kernel command line: root=UUID=d253e5cb-e673-4b28-935c-76245a225c23 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0118c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 2591.836 MHz processor.
[   13.841062] Console: colour VGA+ 80x25
[   13.841385] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.841761] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   13.852710] Memory: 182796k/196032k available (2015k kernel code, 12688k reserved, 916k data, 364k init, 0k highmem)
[   13.852738] virtual kernel memory layout:
[   13.852739]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   13.852740]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.852744]     vmalloc : 0xcc800000 - 0xff7fe000   ( 815 MB)
[   13.852745]     lowmem  : 0xc0000000 - 0xcbf70000   ( 191 MB)
[   13.852746]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   13.852750]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   13.852751]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   13.852757] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.852868] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.932914] Calibrating delay using timer specific routine.. 5191.18 BogoMIPS (lpj=10382360)
[   13.933011] Security Framework v1.0.0 initialized
[   13.933040] SELinux:  Disabled at boot.
[   13.933082] Mount-cache hash table entries: 512
[   13.933594] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[   13.933634] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   13.933640] CPU: L2 cache: 128K
[   13.933649] CPU: Hyper-Threading is disabled
[   13.933655] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00004400 00000000 00000000
[   13.933684] Compat vDSO mapped to ffffe000.
[   13.933736] Checking 'hlt' instruction... OK.
[   13.949276] SMP alternatives: switching to UP code
[   13.950171] Freeing SMP alternatives: 11k freed
[   13.951093] Early unpacking initramfs... done
[   14.664234] ACPI: Core revision 20070126
[   14.664478] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.669117] ACPI: setting ELCR to 0200 (from 0420)
[   14.671629] CPU0: Intel(R) Celeron(R) CPU 2.60GHz stepping 09
[   14.671641] SMP motherboard not detected.
[   14.671644] Local APIC not detected. Using dummy APIC emulation.
[   14.671730] Brought up 1 CPUs
[   14.672015] Booting paravirtualized kernel on bare hardware
[   14.672169] Time:  4:08:49  Date: 01/04/108
[   14.672232] NET: Registered protocol family 16
[   14.672532] EISA bus registered
[   14.672570] ACPI: bus type pci registered
[   14.731292] PCI: PCI BIOS revision 2.10 entry at 0xfd89b, last bus=2
[   14.731298] PCI: Using configuration type 1
[   14.731302] Setting up standard PCI resources
[   14.737841] ACPI: EC: Look up EC in DSDT
[   14.739667] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   14.770405] ACPI: Interpreter enabled
[   14.770417] ACPI: (supports S0 S3 S4 S5)
[   14.770451] ACPI: Using PIC for interrupt routing
[   14.790261] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   14.973168] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.973191] PCI: Probing PCI hardware (bus 00)
[   14.973892] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[   14.973900] PCI quirk: region 8040-805f claimed by ali7101 SMB
[   14.974425] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.974531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   14.979077] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
[   14.979325] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
[   14.979562] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 *10)
[   14.979799] ACPI: PCI Interrupt Link [LNK3] (IRQs 7 *10)
[   14.980033] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
[   14.980273] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 *11)
[   14.980512] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
[   14.980795] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
[   14.981050] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 10) *0, disabled.
[   14.981443] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.981491] pnp: PnP ACPI init
[   14.981518] ACPI: bus type pnp registered
[   14.988592] pnp: PnP ACPI: found 11 devices
[   14.988603] ACPI: ACPI bus type pnp unregistered
[   14.988611] PnPBIOS: Disabled by ACPI PNP
[   14.988849] PCI: Using ACPI for IRQ routing
[   14.988859] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.991805] NET: Registered protocol family 8
[   14.991811] NET: Registered protocol family 20
[   14.992090] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[   14.992097] pnp: 00:07: ioport range 0x480-0x48f has been reserved
[   14.992100] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   14.992103] pnp: 00:07: ioport range 0x4d6-0x4d6 has been reserved
[   14.992107] pnp: 00:07: ioport range 0x8000-0x807f could not be reserved
[   14.992113] pnp: 00:07: iomem range 0xd0009000-0xd0009fff has been reserved
[   14.992735] Time: tsc clocksource has been installed.
[   15.023848] PCI: Bridge: 0000:00:01.0
[   15.023857]   IO window: 9000-9fff
[   15.023861]   MEM window: d0300000-d03fffff
[   15.023865]   PREFETCH window: d8000000-dfffffff
[   15.023870] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[   15.023872]   IO window: 00001800-000018ff
[   15.023876]   IO window: 00001c00-00001cff
[   15.023880]   PREFETCH window: 20000000-23ffffff
[   15.023884]   MEM window: 24000000-27ffffff
[   15.023914] PCI: Enabling device 0000:00:0a.0 (0005 -> 0007)
[   15.024261] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[   15.024270] PCI: setting IRQ 11 as level-triggered
[   15.024274] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[   15.024316] NET: Registered protocol family 2
[   15.060829] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   15.060942] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[   15.061079] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   15.061208] TCP: Hash tables configured (established 8192 bind 8192)
[   15.061216] TCP reno registered
[   15.072987] checking if image is initramfs... it is
[   15.524710] Switched to high resolution mode on CPU 0
[   15.766340] Freeing initrd memory: 7071k freed
[   15.766623] Simple Boot Flag at 0x37 set to 0x1
[   15.767344] audit: initializing netlink socket (disabled)
[   15.767377] audit(1202098129.624:1): initialized
[   15.775849] VFS: Disk quotas dquot_6.5.1
[   15.776088] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.776475] io scheduler noop registered
[   15.776481] io scheduler anticipatory registered
[   15.776483] io scheduler deadline registered
[   15.776615] io scheduler cfq registered (default)
[   15.776641] Activating ISA DMA hang workarounds.
[   15.776688] Boot video device is 0000:01:05.0
[   15.777335] isapnp: Scanning for PnP cards...
[   16.131959] isapnp: No Plug & Play device found
[   16.368832] Real Time Clock Driver v1.12ac
[   16.369200] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.370113] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   16.372938] PCI: Enabling device 0000:00:08.0 (0000 -> 0003)
[   16.373302] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
[   16.373311] PCI: setting IRQ 10 as level-triggered
[   16.373314] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK6] -> GSI 10 (level, low) -> IRQ 10
[   16.379513] 0000:00:08.0: ttyS0 at I/O 0x1428 (irq = 10) is a 8250
[   16.382913] 0000:00:08.0: ttyS2 at I/O 0x1440 (irq = 10) is a 8250
[   16.385250] 0000:00:08.0: ttyS3 at I/O 0x1450 (irq = 10) is a 8250
[   16.385968] Couldn't register serial port 0000:00:08.0: -28
[   16.388529] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.388974] input: Macintosh mouse button emulation as /class/input/input0
[   16.389344] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   16.391748] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.391761] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.392694] mice: PS/2 mouse device common for all mice
[   16.393251] EISA: Probing bus 0 at eisa.0
[   16.393271] Cannot allocate resource for EISA slot 1
[   16.393274] Cannot allocate resource for EISA slot 2
[   16.393300] Cannot allocate resource for EISA slot 8
[   16.393302] EISA: Detected 0 cards.
[   16.393497] TCP cubic registered
[   16.393559] NET: Registered protocol family 1
[   16.393620] Using IPI No-Shortcut mode
[   16.394076]   Magic number: 12:758:109
[   16.395351] Freeing unused kernel memory: 364k freed
[   16.460487] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.921063] AppArmor: AppArmor initialized<5>audit(1202098131.624:2):  type=1505 info="AppArmor initialized" pid=1142
[   18.038043] fuse init (API version 7.8)
[   18.051353] Failure registering capabilities with primary security module.
[   18.170037] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   18.572030] ACPI: Thermal Zone [THRM] (44 C)
[   30.208123] usbcore: registered new interface driver usbfs
[   30.208191] usbcore: registered new interface driver hub
[   30.208286] usbcore: registered new device driver usb
[   30.210038] USB Universal Host Controller Interface driver v3.0
[   30.210574] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[   30.210584] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[   30.210608] uhci_hcd 0000:00:0b.0: UHCI Host Controller
[   30.211093] uhci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   30.211144] uhci_hcd 0000:00:0b.0: irq 10, io base 0x00002000
[   30.211460] usb usb1: configuration #1 chosen from 1 choice
[   30.211530] hub 1-0:1.0: USB hub found
[   30.211557] hub 1-0:1.0: 2 ports detected
[   30.313164] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 10
[   30.313175] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNK3] -> GSI 10 (level, low) -> IRQ 10
[   30.313199] uhci_hcd 0000:00:0b.1: UHCI Host Controller
[   30.313298] uhci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   30.313338] uhci_hcd 0000:00:0b.1: irq 10, io base 0x00002020
[   30.313581] usb usb2: configuration #1 chosen from 1 choice
[   30.313647] hub 2-0:1.0: USB hub found
[   30.313678] hub 2-0:1.0: 2 ports detected
[   30.678382] PCI: Enabling device 0000:00:0b.2 (0010 -> 0012)
[   30.678402] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[   30.678430] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[   30.678494] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 3
[   30.678562] ehci_hcd 0000:00:0b.2: irq 11, io mem 0xd0003000
[   30.678571] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   30.678762] usb usb3: configuration #1 chosen from 1 choice
[   30.678838] hub 3-0:1.0: USB hub found
[   30.678861] hub 3-0:1.0: 4 ports detected
[   30.823506] PCI: Enabling device 0000:00:0c.0 (0010 -> 0012)
[   30.823523] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[   30.873704] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0003800-d0003fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   30.889725] SCSI subsystem initialized
[   30.901431] libata version 2.21 loaded.
[   30.913708] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.913720] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.915412] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[   30.915447] ACPI: Unable to derive IRQ for device 0000:00:10.0
[   30.915450] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[   30.915465] ALI15X3: chipset revision 196
[   30.915468] ALI15X3: not 100% native mode: will probe irqs later
[   30.915493]     ide0: BM-DMA at 0x2040-0x2047, BIOS settings: hda:DMA, hdb:pio
[   30.915517]     ide1: BM-DMA at 0x2048-0x204f, BIOS settings: hdc:pio, hdd:pio
[   30.915535] Probing IDE interface ide0...
[   31.212451] hda: ST93012A, ATA DISK drive
[   31.298704] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[   31.298709]   originally by Donald Becker <becker@scyld.com>
[   31.298711]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[   31.317105] Floppy drive(s): fd0 is 1.44M
[   31.350229] FDC 0 is a post-1991 82077
[   31.884089] hda: selected mode 0x45
[   31.890026] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   32.144256] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000e7f71a0730185]
[   32.566664] Probing IDE interface ide1...
[   33.299869] hdc: SONY CD-RW/DVD-ROM CRX830E, ATAPI CD/DVD-ROM drive
[   33.971504] hdc: selected mode 0x22
[   33.971651] ide1 at 0x170-0x177,0x376 on irq 15
[   33.973345] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[   33.973355] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
[   33.975844] natsemi eth0: NatSemi DP8381[56] at 0xd0008000 (0000:00:12.0), 00:0e:7f:73:19:72, IRQ 10, port TP.
[   33.993652] hda: max request size: 128KiB
[   34.012888] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   34.014492] hda: cache flushes supported
[   34.014615]  hda: hda1 hda2 < hda5 >
[   34.325303] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, (U)DMA
[   34.325318] Uniform CD-ROM driver Revision: 3.20
[   35.844661] Attempting manual resume
[   35.844671] swsusp: Resume From Partition 3:5
[   35.844673] PM: Checking swsusp image.
[   35.942948] PM: Resume from disk failed.
[   36.578926] kjournald starting.  Commit interval 5 seconds
[   36.578964] EXT3-fs: mounted filesystem with ordered data mode.
[  132.963512] Linux agpgart interface v0.102 (c) Dave Jones
[  132.965937] agpgart: Detected Ati IGP345M chipset
[  132.976375] agpgart: AGP aperture is 64M @ 0xd4000000
[  132.986991] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  132.990409] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  133.012618] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0850]
[  133.012645] Yenta O2: res at 0x94/0xD4: 00/ea
[  133.012648] Yenta O2: enabling read prefetch/write burst
[  133.140719] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[  133.140726] Socket status: 30000007
[  134.887750] PCI: Enabling device 0000:00:06.0 (0005 -> 0007)
[  134.888134] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[  134.888142] PCI: setting IRQ 5 as level-triggered
[  134.888147] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNK7] -> GSI 5 (level, low) -> IRQ 5
[  135.070047] input: PC Speaker as /class/input/input2
[  135.478570] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[  135.589771] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[  135.589777] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[  135.599955] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[  135.599961] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[  135.624822] parport_pc 00:09: reported by Plug and Play ACPI
[  135.624904] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  135.901558] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[  135.983124] cs: IO port probe 0x3e0-0x4ff: clean.
[  135.984254] cs: IO port probe 0x820-0x8ff: clean.
[  135.985151] cs: IO port probe 0xc00-0xcf7: clean.
[  135.986433] cs: IO port probe 0xa00-0xaff: clean.
[  137.554852] AC'97 1 does not respond - RESET
[  137.570851] AC'97 1 access is not valid [0xffffffff], removing mixer.
[  137.570864] ali mixer 1 creating error.
[  138.822130] lp0: using parport0 (interrupt-driven).
[  139.812892] Adding 554200k swap on /dev/hda5.  Priority:-1 extents:1 across:554200k
[  141.514098] EXT3 FS on hda1, internal journal
[  153.099978] No dock devices found.
[  153.222982] ACPI: Battery Slot [BAT1] (battery present)
[  153.470978] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  153.974476] input: Power Button (FF) as /class/input/input4
[  153.984446] ACPI: Power Button (FF) [PWRF]
[  154.030481] input: Power Button (CM) as /class/input/input5
[  154.031147] ACPI: Power Button (CM) [PWRB]
[  154.054374] input: Lid Switch as /class/input/input6
[  154.055048] ACPI: Lid Switch [LID]
[  154.350538] ACPI: AC Adapter [ACAD] (on-line)
[  165.857873] eth0: DSPCFG accepted after 0 usec.
[  165.857892] eth0: link up.
[  165.857906] eth0: Setting full-duplex based on negotiated link capability.
[  166.914143] ppdev: user-space parallel port driver
[  167.869450] audit(1202098282.544:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4794 profile="/usr/sbin/cupsd"
[  168.124656] apm: BIOS not found.
[  170.830673] Failure registering capabilities with primary security module.
[  177.200252] NET: Registered protocol family 17
[  170.728000] Marking TSC unstable due to: possible TSC halt in C2.
[  170.732000] Time: acpi_pm clocksource has been installed.
[  171.988000] mtrr: no more MTRRs available
[  171.988000] mtrr: no more MTRRs available
[  171.988000] mtrr: no more MTRRs available
[  171.988000] mtrr: no more MTRRs available
[  171.988000] mtrr: no more MTRRs available
[  171.988000] mtrr: no more MTRRs available
[  179.688000] NET: Registered protocol family 10
[  179.692000] lo: Disabled Privacy Extensions
[  190.244000] eth0: no IPv6 routers present
[  330.276000] eth0: Autonegotiation advertising 0x5e1  partner 0x00.
[  330.276000] eth0: link down.
[  333.068000] eth0: Autonegotiation advertising 0x5e1  partner 0x45e1.
[  333.068000] eth0: link up.
[  333.068000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  333.072000] eth0: Autonegotiation advertising 0x5e1  partner 0x45e1.
[  343.592000] eth0: no IPv6 routers present
[  372.212000] eth0: no IPv6 routers present

---

