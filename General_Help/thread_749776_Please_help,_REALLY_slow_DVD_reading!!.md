---
title: "Please help, REALLY slow DVD reading!!"
date: 2008-04-08
forum: General Help
---

### Post by fishbulb15 on 2008-04-08
I have read a lot of posts on this forum and others and I can't seem to make any sense of this. I am experiencing extremely long download times from my DVD ROM and writer drives(I have 2 ). Can someone please suggest something to help me please. 

Here is a bunch of information I saw that were useful on other posts:

%sudo hdparm -tT /dev/scd0
```
/dev/scd0:
 Timing cached reads:   512 MB in  2.00 seconds = 255.63 MB/sec
 Timing buffered disk reads:    8 MB in  3.27 seconds =   2.44 MB/sec

```
%hdparm -i /dev/scd0
```

/dev/scd0:

 Model=SONY    DVD RW DRU-530A                 , FwRev=2.1g    , SerialNo=                    
 Config={ Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=1024kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:383,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode

```

lshw:
```
  *-cdrom:0
       description: DVD writer
       product: DVD RW DRU-530A
       vendor: SONY
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 2.1g
       serial: 3SONY    DVD RW DRU-530A 2.1g
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM LTD163
       vendor: LITEON
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: GV3Y
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
```

dmesg:
```
[    0.000000] Linux version 2.6.24-15-generic (buildd@rothera) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Apr 4 03:48:31 UTC 2008 (Ubuntu 2.6.24-15.26-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffeb000 (usable)
[    0.000000]  BIOS-e820: 000000001ffeb000 - 000000001ffef000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131051) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131051
[    0.000000]   HighMem    131051 ->   131051
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131051
[    0.000000] On node 0 totalpages: 131051
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125964 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F65C0 checksum 0
[    0.000000] ACPI: RSDP 000F65C0, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 1FFEB000, 002C (r1 ASUS   P4T      30303031 MSFT 31313031)
[    0.000000] ACPI: FACP 1FFEB080, 0074 (r1 ASUS   P4T      30303031 MSFT 31313031)
[    0.000000] ACPI: DSDT 1FFEB100, 30D5 (r1   ASUS P4T          1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1FFFF000, 0040
[    0.000000] ACPI: BOOT 1FFEB040, 0028 (r1 ASUS   P4T      30303031 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130028
[    0.000000] Kernel command line: root=UUID=ab49da4a-81c0-4ec5-9c93-0ee8c50f2d64 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0140d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1707.671 MHz processor.
[   49.080955] Console: colour VGA+ 80x25
[   49.080962] console [tty0] enabled
[   49.081301] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   49.081682] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   49.100769] Memory: 507796k/524204k available (2164k kernel code, 15892k reserved, 1006k data, 364k init, 0k highmem)
[   49.100784] virtual kernel memory layout:
[   49.100785]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   49.100787]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   49.100789]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   49.100791]     lowmem  : 0xc0000000 - 0xdffeb000   ( 511 MB)
[   49.100793]       .init : 0xc041f000 - 0xc047a000   ( 364 kB)
[   49.100795]       .data : 0xc031d2ad - 0xc0418dc4   (1006 kB)
[   49.100797]       .text : 0xc0100000 - 0xc031d2ad   (2164 kB)
[   49.100801] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   49.100853] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   49.180792] Calibrating delay using timer specific routine.. 3419.03 BogoMIPS (lpj=6838076)
[   49.180827] Security Framework initialized
[   49.180838] SELinux:  Disabled at boot.
[   49.180858] AppArmor: AppArmor initialized
[   49.180864] Failure registering capabilities with primary security module.
[   49.180877] Mount-cache hash table entries: 512
[   49.181087] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   49.181108] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   49.181113] CPU: L2 cache: 256K
[   49.181116] CPU: Hyper-Threading is disabled
[   49.181120] CPU: After all inits, caps: 3febf9ff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[   49.181138] Compat vDSO mapped to ffffe000.
[   49.181158] Checking 'hlt' instruction... OK.
[   49.197407] SMP alternatives: switching to UP code
[   49.199965] Freeing SMP alternatives: 11k freed
[   49.200165] Early unpacking initramfs... done
[   49.719092] ACPI: Core revision 20070126
[   49.719162] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   49.721094] ACPI: setting ELCR to 0200 (from 0e00)
[   49.721339] CPU0: Intel(R) Pentium(R) 4 CPU 1700MHz stepping 0a
[   49.721349] SMP motherboard not detected.
[   49.721352] Local APIC not detected. Using dummy APIC emulation.
[   49.721433] Brought up 1 CPUs
[   49.721458] CPU0 attaching sched-domain:
[   49.721463]  domain 0: span 01
[   49.721466]   groups: 01
[   49.721781] net_namespace: 64 bytes
[   49.721797] Booting paravirtualized kernel on bare hardware
[   49.722821] Time: 18:18:56  Date: 04/05/08
[   49.722921] NET: Registered protocol family 16
[   49.723306] EISA bus registered
[   49.723330] ACPI: bus type pci registered
[   49.725757] PCI: PCI BIOS revision 2.10 entry at 0xf0e10, last bus=2
[   49.725762] PCI: Using configuration type 1
[   49.725764] Setting up standard PCI resources
[   49.733215] ACPI: EC: Look up EC in DSDT
[   49.736432] ACPI: Interpreter enabled
[   49.736438] ACPI: (supports S0 S1 S4 S5)
[   49.736461] ACPI: Using PIC for interrupt routing
[   49.747987] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   49.748359] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[   49.748369] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[   49.749181] PCI: Transparent bridge - 0000:00:1e.0
[   49.749219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   49.749333] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   49.749415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   49.771192] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   49.771333] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   49.771454] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   49.771591] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   49.771710] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   49.771830] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   49.771950] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   49.772086] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   49.772340] Linux Plug and Play Support v0.97 (c) Adam Belay
[   49.772400] pnp: PnP ACPI init
[   49.772418] ACPI: bus type pnp registered
[   49.777011] pnp: PnP ACPI: found 14 devices
[   49.777017] ACPI: ACPI bus type pnp unregistered
[   49.777024] PnPBIOS: Disabled by ACPI PNP
[   49.777455] PCI: Using ACPI for IRQ routing
[   49.777461] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   49.800128] NET: Registered protocol family 8
[   49.800132] NET: Registered protocol family 20
[   49.800262] AppArmor: AppArmor Filesystem Enabled
[   49.804111] Time: tsc clocksource has been installed.
[   49.812190] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   49.812196] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   49.812201] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[   49.812207] system 00:00: iomem range 0xfff80000-0xffffffff could not be reserved
[   49.812221] system 00:02: ioport range 0x3f0-0x3f1 has been reserved
[   49.812226] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   49.812238] system 00:03: ioport range 0xe400-0xe47f has been reserved
[   49.812244] system 00:03: ioport range 0xec00-0xec3f has been reserved
[   49.812250] system 00:03: ioport range 0xec80-0xec8f has been reserved
[   49.843003] PCI: Bridge: 0000:00:01.0
[   49.843007]   IO window: disabled.
[   49.843015]   MEM window: ee000000-efdfffff
[   49.843020]   PREFETCH window: eff00000-f7ffffff
[   49.843030] PCI: Bridge: 0000:00:1e.0
[   49.843034]   IO window: c000-dfff
[   49.843042]   MEM window: ed800000-edffffff
[   49.843048]   PREFETCH window: efe00000-efefffff
[   49.843063] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   49.843074] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   49.843094] NET: Registered protocol family 2
[   49.880161] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   49.880581] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   49.880683] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   49.880790] TCP: Hash tables configured (established 16384 bind 16384)
[   49.880797] TCP reno registered
[   49.892265] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   50.372732]  it is
[   50.901880] Freeing initrd memory: 7265k freed
[   50.902105] Simple Boot Flag at 0x3a set to 0x1
[   50.902648] audit: initializing netlink socket (disabled)
[   50.902667] audit(1207419537.804:1): initialized
[   50.906217] VFS: Disk quotas dquot_6.5.1
[   50.906363] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   50.906633] io scheduler noop registered
[   50.906638] io scheduler anticipatory registered
[   50.906641] io scheduler deadline registered
[   50.906673] io scheduler cfq registered (default)
[   50.906728] Boot video device is 0000:01:00.0
[   50.907263] isapnp: Scanning for PnP cards...
[   51.261280] isapnp: No Plug & Play device found
[   51.348672] Real Time Clock Driver v1.12ac
[   51.348824] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   51.348990] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   51.349291] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   51.350885] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   51.351626] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   51.353137] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   51.353259] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   51.353449] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   51.356200] serio: i8042 KBD port at 0x60,0x64 irq 1
[   51.356211] serio: i8042 AUX port at 0x60,0x64 irq 12
[   51.362550] mice: PS/2 mouse device common for all mice
[   51.362782] EISA: Probing bus 0 at eisa.0
[   51.362825] EISA: Detected 0 cards.
[   51.362830] cpuidle: using governor ladder
[   51.362833] cpuidle: using governor menu
[   51.362982] NET: Registered protocol family 1
[   51.363033] Using IPI No-Shortcut mode
[   51.363080] registered taskstats version 1
[   51.363203]   Magic number: 4:542:341
[   51.363384] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   51.363386] EDD information not available.
[   51.363859] Freeing unused kernel memory: 364k freed
[   51.398349] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   52.774840] fuse init (API version 7.9)
[   52.814368] ACPI: Invalid PBLK length [5]
[   53.832906] SCSI subsystem initialized
[   53.866868] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   53.866876] PCI: setting IRQ 11 as level-triggered
[   53.866882] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   53.866895] 3c59x: Donald Becker and others.
[   53.866903] 0000:02:07.0: 3Com PCI 3c905C Tornado at e083a000.
[   53.964870] usbcore: registered new interface driver usbfs
[   53.964909] usbcore: registered new interface driver hub
[   53.988539] usbcore: registered new device driver usb
[   54.011395] USB Universal Host Controller Interface driver v3.0
[   54.011913] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   54.011918] PCI: setting IRQ 9 as level-triggered
[   54.011922] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   54.011938] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   54.011944] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   54.012438] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   54.012476] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000b400
[   54.012722] usb usb1: configuration #1 chosen from 1 choice
[   54.012766] hub 1-0:1.0: USB hub found
[   54.012776] hub 1-0:1.0: 2 ports detected
[   54.023364] libata version 3.00 loaded.
[   54.115847] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[   54.115855] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[   54.115871] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   54.115877] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   54.115926] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   54.115957] uhci_hcd 0000:00:1f.4: irq 9, io base 0x0000b000
[   54.116157] usb usb2: configuration #1 chosen from 1 choice
[   54.116197] hub 2-0:1.0: USB hub found
[   54.116207] hub 2-0:1.0: 2 ports detected
[   54.156670] Floppy drive(s): fd0 is 1.44M
[   54.174443] FDC 0 is a National Semiconductor PC87306
[   54.219466] ata_piix 0000:00:1f.1: version 2.12
[   54.219544] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   54.226474] scsi0 : ata_piix
[   54.235355] scsi1 : ata_piix
[   54.236159] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
[   54.236164] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
[   54.564036] ata1.00: ATA-5: WDC WD600BB-75BSA0, 12.08C12, max UDMA/100
[   54.564046] ata1.00: 117231408 sectors, multi 16: LBA 
[   54.564096] ata1.01: ATAPI: IOMEGA  ZIP 250       ATAPI       Floppy, 41.S, max UDMA/33, CDB intr
[   54.579945] ata1.00: configured for UDMA/100
[   54.750802] ata1.01: configured for UDMA/33
[   55.458017] ata2.00: ATAPI: SONY    DVD RW DRU-530A, 2.1g, max UDMA/33
[   55.458061] ata2.01: ATAPI: LITEON  DVD-ROM LTD163, GV3Y, max UDMA/33
[   55.629782] ata2.00: configured for UDMA/33
[   55.793576] ata2.01: configured for UDMA/33
[   55.793772] scsi 0:0:0:0: Direct-Access     ATA      WDC WD600BB-75BS 12.0 PQ: 0 ANSI: 5
[   55.797664] scsi 0:0:1:0: Direct-Access     IOMEGA   ZIP 250          41.S PQ: 0 ANSI: 5
[   55.798922] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DRU-530A  2.1g PQ: 0 ANSI: 5
[   55.799775] scsi 1:0:1:0: CD-ROM            LITEON   DVD-ROM LTD163   GV3Y PQ: 0 ANSI: 5
[   55.839957] Driver 'sd' needs updating - please use bus_type methods
[   55.840093] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   55.840116] sd 0:0:0:0: [sda] Write Protect is off
[   55.840121] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   55.840155] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   55.840249] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   55.840268] sd 0:0:0:0: [sda] Write Protect is off
[   55.840272] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   55.840304] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   55.840311]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   55.911818]  sda1 sda2 < sda5 >
[   55.934688] sd 0:0:0:0: [sda] Attached SCSI disk
[   55.937581] sd 0:0:1:0: [sdb] Attached SCSI removable disk
[   55.956169] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   55.956204] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   55.956233] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   55.956268] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   55.956856] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   55.956864] Uniform CD-ROM driver Revision: 3.20
[   55.956950] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   55.959800] sr1: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   55.959897] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   56.259511] Attempting manual resume
[   56.259518] swsusp: Resume From Partition 8:5
[   56.259521] PM: Checking swsusp image.
[   56.259744] PM: Resume from disk failed.
[   56.313302] kjournald starting.  Commit interval 5 seconds
[   56.313327] EXT3-fs: mounted filesystem with ordered data mode.
[   65.371600] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   65.438845] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   65.522306] Linux agpgart interface v0.102
[   65.586798] agpgart: Detected an Intel i850 Chipset.
[   65.590831] agpgart: AGP aperture is 64M @ 0xf8000000
[   65.658150] iTCO_vendor_support: vendor-support=0
[   65.722078] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   65.723063] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0xe460)
[   65.723142] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   65.885895] intel_rng: FWH not detected
[   66.125805] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   66.641268] input: Power Button (FF) as /devices/virtual/input/input3
[   66.656983] ACPI: Power Button (FF) [PWRF]
[   66.657175] input: Power Button (CM) as /devices/virtual/input/input4
[   66.672965] ACPI: Power Button (CM) [PWRB]
[   67.998160] nvidia: module license 'NVIDIA' taints kernel.
[   68.205423] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   68.205840] NVRM: loading NVIDIA Linux x86 Kernel Module  71.86.04  Mon Jan 21 11:22:18 PST 2008
[   68.971178] gameport: EMU10K1 is pci0000:02:09.1/gameport0, io 0xd000, speed 946kHz
[   69.705244] logips2pp: Detected unknown logitech mouse model 57
[   70.174173] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   70.191764] parport_pc 00:09: reported by Plug and Play ACPI
[   70.191877] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   70.554625] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   70.554633] PCI: setting IRQ 10 as level-triggered
[   70.554638] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   73.998252] lp0: using parport0 (interrupt-driven).
[   74.134180] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   74.814293] EXT3 FS on sda1, internal journal
[   76.077117] ip_tables: (C) 2000-2006 Netfilter Core Team
```

 sdparm -va /dev/scd0
```

    /dev/scd0: SONY      DVD RW DRU-530A   2.1g  [cd/dvd]
Read write error recovery [0x1] mode page [PS=0]:
  AWRE        0  [cha: n, def:  0]
  ARRE        0  [cha: n, def:  0]
  TB          0  [cha: y, def:  0]
  RC          0  [cha: y, def:  0]
  EER         0  [cha: n, def:  0]
  PER         0  [cha: y, def:  0]
  DTE         0  [cha: n, def:  0]
  DCR         0  [cha: y, def:  0]
  RRC        10  [cha: y, def: 10]
  COR_S       0  [cha: n, def:  0]
  HOC         0  [cha: n, def:  0]
  DSOC        0  [cha: n, def:  0]
  EMCDR       0  [cha: n, def:  0]
  WRC        10  [cha: y, def: 10]
  ERTL      650  [cha: y, def:650]
>> Disconnect-reconnect (SPC + transports) mode page [0x2] not found
>> Mount rainier reWritable (MMC) mode page [0x3] not found
Write parameters (MMC) [0x5] mode page [PS=0]:
  BUFE        0  [cha: y, def:  0]
  LS_V        0  [cha: y, def:  0]
  TST_W       0  [cha: y, def:  0]
  WR_T        1  [cha: y, def:  1]
  MULTI_S     3  [cha: y, def:  3]
  FP          0  [cha: y, def:  0]
  COPY        0  [cha: y, def:  0]
  TRACK_M     4  [cha: y, def:  4]
  DBT         8  [cha: y, def:  8]
  LINK_S      0  [cha: y, def:  0]
  IAC         0  [cha: y, def:  0]
  SESS_F      0  [cha: y, def:  0]
  PACK_S      0  [cha: y, def:  0]
  APL       150  [cha: y, def:150]
>> Control mode page [0xa] not found
>> Control extension mode subpage [0xa,0x1] not found
>> SAT pATA control mode subpage [0xa,0xf1] not found
>> Protocol specific logical unit mode page [0x18] not found
>> Protocol specific port mode page [0x19] not found
Power condition [0x1a] mode page [PS=0]:
  IDLE        1  [cha: y, def:  1]
  STANDBY     1  [cha: y, def:  1]
  ICT       600  [cha: y, def:600]
  SCT       1200  [cha: y, def:1200]
>> Informational exceptions control mode page [0x1c] not found
Timeout and protect (MMC) [0x1d] mode page [PS=0]:
  G3E         0  [cha: n, def:  0]
  TMOE        0  [cha: n, def:  0]
  DISP        0  [cha: n, def:  0]
  SWPP        0  [cha: n, def:  0]
  G1MT        0  [cha: y, def:  0]
  G2MT        0  [cha: y, def:  0]
CD/DVD (MM) capabilities and mechanical status (MMC) [0x2a] mode page [PS=0]:
  D_RAM_R     0  [cha: n, def:  0]
  D_R_R       1  [cha: n, def:  1]
  D_ROM_R     1  [cha: n, def:  1]
  METH2       1  [cha: n, def:  1]
  CD_RW_R     1  [cha: n, def:  1]
  CD_R_R      1  [cha: n, def:  1]
  D_RAM_W     0  [cha: n, def:  0]
  D_R_W       1  [cha: n, def:  1]
  TST_WR      1  [cha: n, def:  1]
  CD_RW_W     1  [cha: n, def:  1]
  CD_R_W      1  [cha: n, def:  1]
  BUF         1  [cha: n, def:  1]
  MULT_S      1  [cha: n, def:  1]
  M2F2        1  [cha: n, def:  1]
  M2F1        1  [cha: n, def:  1]
  DP_2        0  [cha: n, def:  0]
  DP_1        1  [cha: n, def:  1]
  COMP        0  [cha: n, def:  0]
  AUDIO_P     1  [cha: n, def:  1]
  RBC         0  [cha: n, def:  0]
  UPC         1  [cha: n, def:  1]
  ISRC        1  [cha: n, def:  1]
  C2PS        1  [cha: n, def:  1]
  RW_DC       1  [cha: n, def:  1]
  RW_S        1  [cha: n, def:  1]
  CDDA_SA     1  [cha: n, def:  1]
  CDDA_CS     1  [cha: n, def:  1]
  LMT         1  [cha: n, def:  1]
  EJECT       1  [cha: n, def:  1]
  PJ          0  [cha: n, def:  0]
  LS          1  [cha: n, def:  0]
  LOCK        1  [cha: n, def:  1]
  RWILI       1  [cha: n, def:  1]
  SCC         0  [cha: n, def:  0]
  SSS         0  [cha: n, def:  0]
  CSDP        0  [cha: n, def:  0]
  SCM         1  [cha: n, def:  1]
  SVL         1  [cha: n, def:  1]
  NVLS      256  [cha: n, def:256]
  BSS       2048  [cha: n, def:2048]
  LENGTH      0  [cha: n, def:  0]
  LSBF        0  [cha: n, def:  0]
  RCK         0  [cha: n, def:  0]
  BCKF        0  [cha: n, def:  0]
  CMRS        0  [cha: n, def:  1]
  RCS         0  [cha: n, def:  0]
  CWSS        0  [cha: n, def:4233]

```

 hdparm -d1 /dev/scd0
```

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
```

---

### Post by UrbanFallout on 2008-07-06
Same problem on my Acer 5024WLMi.

I think DMA needs to be enabled, but I have no idea how this is done when the DVD drive is treated as a SCSI device (in Hardy) rather than an IDE device as it was before. Hence the hdparm command not working: these only apply to IDE devices I think. 

I think we need to to do the equivalent of "hdparm -d1" with sdparm, but a quick read of the man page doesn't explain how.

Can anybody else shed some light on this problem?

Thanks in advance

---

### Post by UrbanFallout on 2008-07-06
Issue solved.

Type the following:
```
 sudo gedit /etc/modprobe.d/aliases 
```

And add the following lines to the bottom of the file:
```

## Turn on DMA for DVD ############################
alias ata_generic off
alias pata_atiixp on

```

I'm not quite sure why this works, but I think there is something wrong with the generic ATA module. If anyone can better explain why this is please feel free to add a comment below.

Note this worked when I had the following symptom when running
```
 dmesg | grep ata 
```
one of the lines was:
> 
ata2.00: simplex DMA is claimed by other device, disabling DMA


---

### Post by !nkubus on 2008-07-16
> **UrbanFallout said:**
> Issue solved.

Type the following:
```
 sudo gedit /etc/modprobe.d/aliases 
```

And add the following lines to the bottom of the file:
```

## Turn on DMA for DVD ############################
alias ata_generic off
alias pata_atiixp on

```

I'm not quite sure why this works, but I think there is something wrong with the generic ATA module. If anyone can better explain why this is please feel free to add a comment below.

Note this worked when I had the following symptom when running
```
 dmesg | grep ata 
```
one of the lines was:

That is GOLD it fixed my issues
Thanks a lot

---

### Post by !nkubus on 2008-07-18
Actually it works for 1 or 2 burning sessions and my drives are getting busy, and unreachable after this.

Anybody is having such an issue?

---

