---
title: "adsl modem driver"
date: 2008-05-25
forum: General Help
---

### Post by ivanii on 2008-05-25
I've been using cable modem and had no problem with Ubuntu, but now I am switching to ADSL just to see that it needs some drivers.

I've got CD with Linux drivers, but no manual what to do with them. There are subfolders with drivers for Fedora Core 3, Mandrake 10.1 and Suse Linux 9.2. Which one of them should I use, and how to install them anyway?

---

### Post by diablo75 on 2008-05-25
You very likely do not need a driver.  It's a modem with an Ethernet interface, just like your current modem, right?  Which means all you do is plug it in and turn it on.  Nothing else to it usually.

---

### Post by ivanii on 2008-05-25
Unfortunately, this one has USB connection, so I need to install driver. On Windows I actually need to make connection, just like on dialup

---

### Post by &amp;wP*!) on 2008-05-25
> **ivanii said:**
> Unfortunately, this one has USB connection, so I need to install driver. On Windows I actually need to make connection, just like on dialup
Just plug the USB and do a fresh install (if possible).
Or just plug the USB onto a computer where Ubuntu installed.

Try to access internet. If not, send us the output of **dmesg**.

---

### Post by ivanii on 2008-05-25
> **pencuse said:**
> Just plug the USB and do a fresh install (if possible).
Or just plug the USB onto a computer where Ubuntu installed.

Try to access internet. If not, send us the output of **dmesg**.

I really wouldn't like to do fresh install, so here is dmesg:
```

[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 245488) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245488
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245488
[    0.000000] On node 0 totalpages: 245488
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 125 pages used for memmap
[    0.000000]   HighMem zone: 15987 pages, LIFO batch:3
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F75E0 checksum 0
[    0.000000] ACPI: RSDP 000F75E0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3BEF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3BEF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3BEF3180, 7FF6 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BEF0000, 0040
[    0.000000] ACPI: SSDT 3BEFB280, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: MCFG 3BEFB3C0, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243571
[    0.000000] Kernel command line: root=UUID=8355e57a-3d96-4c51-9780-c107af507a26 ro quiet splash
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1803.751 MHz processor.
[   25.892572] spurious 8259A interrupt: IRQ7.
[   25.895736] Console: colour VGA+ 80x25
[   25.895739] console [tty0] enabled
[   25.896071] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.896654] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.916590] Memory: 961056k/981952k available (2157k kernel code, 20288k reserved, 998k data, 364k init, 64448k highmem)
[   25.916598] virtual kernel memory layout:
[   25.916599]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   25.916600]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.916602]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   25.916603]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   25.916604]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   25.916605]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   25.916606]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   25.916610] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.916646] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   25.996576] Calibrating delay using timer specific routine.. 3610.95 BogoMIPS (lpj=7221904)
[   25.996603] Security Framework initialized
[   25.996608] SELinux:  Disabled at boot.
[   25.996623] AppArmor: AppArmor initialized
[   25.996627] Failure registering capabilities with primary security module.
[   25.996635] Mount-cache hash table entries: 512
[   25.996752] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019 00000000
[   25.996762] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.996764] CPU: L2 Cache: 256K (64 bytes/line)
[   25.996767] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 00000019 00000000
[   25.996777] Compat vDSO mapped to ffffe000.
[   25.996788] Checking 'hlt' instruction... OK.
[   26.012837] SMP alternatives: switching to UP code
[   26.013967] Freeing SMP alternatives: 11k freed
[   26.014086] Early unpacking initramfs... done
[   26.367267] ACPI: Core revision 20070126
[   26.367348] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.370868] ACPI: setting ELCR to 0200 (from 0820)
[   26.372050] CPU0: AMD Sempron(tm) Processor 3400+ stepping 02
[   26.372055] SMP motherboard not detected.
[   26.476069] Brought up 1 CPUs
[   26.476087] CPU0 attaching sched-domain:
[   26.476089]  domain 0: span 01
[   26.476091]   groups: 01
[   26.476261] net_namespace: 64 bytes
[   26.476268] Booting paravirtualized kernel on bare hardware
[   26.476741] Time: 15:48:50  Date: 05/25/08
[   26.476766] NET: Registered protocol family 16
[   26.476929] EISA bus registered
[   26.476962] ACPI: bus type pci registered
[   26.483616] PCI: PCI BIOS revision 3.00 entry at 0xf1ff0, last bus=4
[   26.483618] PCI: Using configuration type 1
[   26.483620] Setting up standard PCI resources
[   26.489285] ACPI: EC: Look up EC in DSDT
[   26.498118] ACPI: Interpreter enabled
[   26.498121] ACPI: (supports S0 S1 S3 S4 S5)
[   26.498135] ACPI: Using PIC for interrupt routing
[   26.512093] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.513151] PCI: Transparent bridge - 0000:00:10.0
[   26.513172] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.513504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   26.659960] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.660198] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.660433] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.660668] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
[   26.660909] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.661143] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.661378] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[   26.661611] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.661846] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[   26.662080] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.662315] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[   26.662548] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.662783] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[   26.663017] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.663252] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.663488] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   26.663724] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   26.663962] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.664198] ACPI: PCI Interrupt Link [LSID] (IRQs *5 7 9 10 11 14 15)
[   26.664436] ACPI: PCI Interrupt Link [LFID] (IRQs *5 7 9 10 11 14 15)
[   26.664707] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   26.664975] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   26.665236] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   26.665496] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   26.665756] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   26.666017] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   26.666278] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   26.666538] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   26.666800] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   26.667062] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   26.667323] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   26.667585] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   26.667852] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   26.668115] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   26.668376] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   26.668638] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   26.668906] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   26.669168] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   26.669430] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   26.669692] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   26.669954] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   26.670122] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.670149] pnp: PnP ACPI init
[   26.670159] ACPI: bus type pnp registered
[   26.678288] pnpacpi: exceeded the max number of mem resources: 12
[   26.678414] pnp: PnP ACPI: found 16 devices
[   26.678417] ACPI: ACPI bus type pnp unregistered
[   26.678420] PnPBIOS: Disabled by ACPI PNP
[   26.678612] PCI: Using ACPI for IRQ routing
[   26.678618] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.783674] NET: Registered protocol family 8
[   26.783676] NET: Registered protocol family 20
[   26.783736] AppArmor: AppArmor Filesystem Enabled
[   26.787662] Time: tsc clocksource has been installed.
[   26.795686] system 00:01: ioport range 0x4000-0x407f has been reserved
[   26.795689] system 00:01: ioport range 0x4080-0x40ff has been reserved
[   26.795692] system 00:01: ioport range 0x4400-0x447f has been reserved
[   26.795695] system 00:01: ioport range 0x4480-0x44ff has been reserved
[   26.795697] system 00:01: ioport range 0x4800-0x487f has been reserved
[   26.795700] system 00:01: ioport range 0x4880-0x48ff has been reserved
[   26.795703] system 00:01: ioport range 0x2000-0x207f has been reserved
[   26.795705] system 00:01: ioport range 0x2080-0x20ff has been reserved
[   26.795709] system 00:01: iomem range 0x3c000000-0x3fffffff could not be reserved
[   26.795715] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   26.795718] system 00:02: ioport range 0x800-0x87f has been reserved
[   26.795721] system 00:02: ioport range 0x290-0x297 has been reserved
[   26.795732] system 00:0e: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   26.795738] system 00:0f: iomem range 0xf0000-0xf3fff could not be reserved
[   26.795741] system 00:0f: iomem range 0xf4000-0xf7fff could not be reserved
[   26.795744] system 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
[   26.795747] system 00:0f: iomem range 0xfc000-0xfffff could not be reserved
[   26.795750] system 00:0f: iomem range 0x3bef0000-0x3befffff could not be reserved
[   26.795753] system 00:0f: iomem range 0xffff0000-0xffffffff could not be reserved
[   26.795756] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   26.795759] system 00:0f: iomem range 0x100000-0x3beeffff could not be reserved
[   26.795761] system 00:0f: iomem range 0x3bf00000-0x3fefffff could not be reserved
[   26.795764] system 00:0f: iomem range 0xfec00000-0xfec00fff could not be reserved
[   26.795767] system 00:0f: iomem range 0xfee00000-0xfeefffff could not be reserved
[   26.795770] system 00:0f: iomem range 0xfefff000-0xfeffffff could not be reserved


[   26.826104] PCI: Bridge: 0000:00:02.0
[   26.826106]   IO window: a000-afff
[   26.826109]   MEM window: fd800000-fd8fffff
[   26.826112]   PREFETCH window: fd700000-fd7fffff
[   26.826114] PCI: Bridge: 0000:00:03.0
[   26.826116]   IO window: 8000-8fff
[   26.826118]   MEM window: fde00000-fdefffff
[   26.826121]   PREFETCH window: fdd00000-fddfffff
[   26.826123] PCI: Bridge: 0000:00:04.0
[   26.826125]   IO window: b000-bfff
[   26.826127]   MEM window: fdc00000-fdcfffff
[   26.826130]   PREFETCH window: fd900000-fd9fffff
[   26.826132] PCI: Bridge: 0000:00:10.0
[   26.826134]   IO window: 9000-9fff
[   26.826138]   MEM window: fdb00000-fdbfffff
[   26.826140]   PREFETCH window: fda00000-fdafffff
[   26.826155] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   26.826162] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   26.826169] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   26.826177] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   26.826188] NET: Registered protocol family 2
[   26.863645] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.863925] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.864790] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.865217] TCP: Hash tables configured (established 131072 bind 65536)
[   26.865220] TCP reno registered
[   26.875688] checking if image is initramfs... it is
[   27.327034] Switched to high resolution mode on CPU 0
[   27.557097] Freeing initrd memory: 7702k freed
[   27.557601] audit: initializing netlink socket (disabled)
[   27.557613] audit(1211730530.536:1): initialized
[   27.557750] highmem bounce pool size: 64 pages
[   27.559319] VFS: Disk quotas dquot_6.5.1
[   27.559384] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.559501] io scheduler noop registered
[   27.559503] io scheduler anticipatory registered
[   27.559505] io scheduler deadline registered
[   27.559515] io scheduler cfq registered (default)
[   27.559532] Boot video device is 0000:00:05.0
[   27.574745] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   27.574767] assign_interrupt_mode Found MSI capability
[   27.574786] Allocate Port Service[0000:00:02.0:pcie00]
[   27.574846] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   27.574867] assign_interrupt_mode Found MSI capability
[   27.574882] Allocate Port Service[0000:00:03.0:pcie00]
[   27.574933] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   27.574954] assign_interrupt_mode Found MSI capability
[   27.574968] Allocate Port Service[0000:00:04.0:pcie00]
[   27.575150] isapnp: Scanning for PnP cards...
[   27.927907] isapnp: No Plug & Play device found
[   27.952139] Real Time Clock Driver v1.12ac
[   27.952240] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.952360] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.952505] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   27.953003] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.953280] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   27.953941] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.954001] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   27.954086] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   27.954089] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   27.954451] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.970159] mice: PS/2 mouse device common for all mice
[   27.970262] EISA: Probing bus 0 at eisa.0
[   27.970271] Cannot allocate resource for EISA slot 2
[   27.970276] Cannot allocate resource for EISA slot 4
[   27.970286] Cannot allocate resource for EISA slot 8
[   27.970288] EISA: Detected 0 cards.
[   27.970291] cpuidle: using governor ladder
[   27.970292] cpuidle: using governor menu
[   27.970377] NET: Registered protocol family 1
[   27.970402] Using IPI No-Shortcut mode
[   27.970434] registered taskstats version 1
[   27.970553]   Magic number: 8:251:842
[   27.970647]   hash matches device ptyu8
[   27.970658]   hash matches device ptyrb
[   27.970718] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   27.970720] EDD information not available.
[   27.970941] Freeing unused kernel memory: 364k freed
[   27.998093] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   29.242056] fuse init (API version 7.9)
[   29.258925] ACPI: Fan [FAN] (on)
[   29.265840] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.267652] ACPI: Thermal Zone [THRM] (40 C)
[   30.501765] usbcore: registered new interface driver usbfs
[   30.501788] usbcore: registered new interface driver hub
[   30.510869] usbcore: registered new device driver usb
[   30.523017] SCSI subsystem initialized
[   30.554684] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   30.555120] ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 5
[   30.555123] PCI: setting IRQ 5 as level-triggered
[   30.555128] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUBA] -> GSI 5 (level, low) -> IRQ 5
[   30.555142] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   30.555145] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   30.555439] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   30.555454] ohci_hcd 0000:00:0b.0: irq 5, io mem 0xfe02f000
[   30.593448] libata version 3.00 loaded.
[   30.612833] usb usb1: configuration #1 chosen from 1 choice
[   30.612860] hub 1-0:1.0: USB hub found
[   30.612869] hub 1-0:1.0: 8 ports detected
[   30.715200] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 11
[   30.715206] PCI: setting IRQ 11 as level-triggered
[   30.715210] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 11 (level, low) -> IRQ 11
[   30.715223] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   30.715226] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   30.715257] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   30.715287] ehci_hcd 0000:00:0b.1: debug port 1
[   30.715291] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   30.715300] ehci_hcd 0000:00:0b.1: irq 11, io mem 0xfe02e000
[   30.726548] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.726681] usb usb2: configuration #1 chosen from 1 choice
[   30.726707] hub 2-0:1.0: USB hub found
[   30.726713] hub 2-0:1.0: 8 ports detected
[   30.766586] Floppy drive(s): fd0 is 1.44M
[   30.790301] FDC 0 is a post-1991 82077
[   30.830613] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   30.831004] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 11
[   30.831008] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 11 (level, low) -> IRQ 11
[   30.831014] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   31.350178] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:17:31:f6:49:8f
[   31.350184] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   31.350303] pata_amd 0000:00:0d.0: version 0.3.10
[   31.350361] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   31.351638] scsi0 : pata_amd
[   31.352678] scsi1 : pata_amd
[   31.353355] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[   31.353358] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[   31.669641] ata1.00: ATAPI: _NEC DVD_RW ND-4571A, 1-01, max UDMA/33
[   31.729224] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   31.841357] ata1.00: configured for UDMA/33
[   31.942154] usb 1-1: configuration #1 chosen from 1 choice
[   32.009465] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-4571A  1-01 PQ: 0 ANSI: 5
[   32.011973] sata_nv 0000:00:0e.0: version 3.5
[   32.012358] ACPI: PCI Interrupt Link [LSID] enabled at IRQ 5
[   32.012361] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSID] -> GSI 5 (level, low) -> IRQ 5
[   32.012402] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   32.026710] scsi2 : sata_nv
[   32.028128] scsi3 : sata_nv
[   32.028355] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 5
[   32.028359] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 5
[   32.308466] usb 1-3: new full speed USB device using ohci_hcd and address 3
[   32.336434] ata3: SATA link down (SStatus 0 SControl 300)
[   32.511454] usb 1-3: configuration #1 chosen from 1 choice
[   32.514513] usbcore: registered new interface driver hiddev
[   32.521639] input: Genius Ergo Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/input/input2
[   32.540230] input,hidraw0: USB HID v1.10 Mouse [Genius Ergo Mouse] on usb-0000:00:0b.0-1
[   32.540252] usbcore: registered new interface driver usbhid
[   32.540256] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.811827] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   32.820067] ata4.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   32.820070] ata4.00: 488397168 sectors, multi 1: LBA48 
[   32.828061] ata4.00: configured for UDMA/133
[   32.828179] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   32.828617] ACPI: PCI Interrupt Link [LFID] enabled at IRQ 5
[   32.828621] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LFID] -> GSI 5 (level, low) -> IRQ 5
[   32.828664] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   32.829064] scsi4 : sata_nv
[   32.829244] scsi5 : sata_nv
[   32.829442] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 5
[   32.829446] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 5
[   33.139398] ata5: SATA link down (SStatus 0 SControl 300)
[   33.458971] ata6: SATA link down (SStatus 0 SControl 300)
[   33.471354] ACPI: PCI Interrupt Link [LNK4] enabled at IRQ 5
[   33.471359] ACPI: PCI Interrupt 0000:04:05.0[A] -> Link [LNK4] -> GSI 5 (level, low) -> IRQ 5
[   33.521080] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[fdbff000-fdbff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   33.538994] Driver 'sr' needs updating - please use bus_type methods
[   33.543984] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   33.543990] Uniform CD-ROM driver Revision: 3.20
[   33.544045] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   33.549211] Driver 'sd' needs updating - please use bus_type methods
[   33.550773] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   33.550788] sd 3:0:0:0: [sda] Write Protect is off
[   33.550791] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.550807] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.550901] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   33.550910] sd 3:0:0:0: [sda] Write Protect is off
[   33.550912] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.550926] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.550929]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   33.552263] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   33.558886]  sda1 sda2 < sda5 sda6 > sda3
[   33.590155] sd 3:0:0:0: [sda] Attached SCSI disk
[   33.917513] Attempting manual resume
[   33.917518] swsusp: Resume From Partition 8:6
[   33.917520] PM: Checking swsusp image.
[   33.917702] PM: Resume from disk failed.
[   33.950169] kjournald starting.  Commit interval 5 seconds
[   33.950183] EXT3-fs: mounted filesystem with ordered data mode.
[   34.793335] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000c2806d]
[   40.448967] input: Power Button (FF) as /devices/virtual/input/input3
[   40.461853] ACPI: Power Button (FF) [PWRF]
[   40.461967] input: Power Button (CM) as /devices/virtual/input/input4
[   40.473845] ACPI: Power Button (CM) [PWRB]
[   40.693641] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.745589] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.608073] Linux agpgart interface v0.102
[   43.738203] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   43.738231] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   44.087075] nvidia: module license 'NVIDIA' taints kernel.
[   44.684518] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   46.027852] parport_pc 00:0a: reported by Plug and Play ACPI
[   46.027883] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   46.081108] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 11
[   46.081113] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNK7] -> GSI 11 (level, low) -> IRQ 11
[   46.081121] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   46.081373] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   46.093593] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 5
[   46.093598] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 5 (level, low) -> IRQ 5
[   46.093622] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   48.441471] lp0: using parport0 (interrupt-driven).
[   48.507058] Adding 2425772k swap on /dev/sda6.  Priority:-1 extents:1 across:2425772k
[   49.046102] EXT3 FS on sda3, internal journal
[   50.287595] ip_tables: (C) 2000-2006 Netfilter Core Team
[   50.673623] No dock devices found.
[   50.972757] powernow-k8: Found 1 AMD Sempron(tm) Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[   50.972792] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x8
[   50.972794] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   51.715014] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   51.715019] apm: overridden by ACPI.
[   51.830835] ppdev: user-space parallel port driver
[   51.928848] audit(1211723355.577:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5141 profile="/usr/sbin/cupsd" namespace="default"
[   52.211496] NET: Registered protocol family 10
[   52.211700] lo: Disabled Privacy Extensions
[   94.506081] Marking TSC unstable due to: cpufreq changes.
[   94.512175] Time: acpi_pm clocksource has been installed.
[   94.815935] Clocksource tsc unstable (delta = -137878364 ns)
[   99.072371] Bluetooth: Core ver 2.11
[   99.080460] NET: Registered protocol family 31
[   99.080467] Bluetooth: HCI device and connection manager initialized
[   99.080474] Bluetooth: HCI socket layer initialized
[   99.184178] Bluetooth: L2CAP ver 2.9
[   99.184186] Bluetooth: L2CAP socket layer initialized
[   99.246565] Bluetooth: RFCOMM socket layer initialized
[   99.246593] Bluetooth: RFCOMM TTY layer initialized
[   99.246597] Bluetooth: RFCOMM ver 1.8
[  101.351026] NET: Registered protocol family 17
[  116.096474] eth0: no IPv6 routers present
[   94.859406] UDF-fs: No VRS found
[   94.921456] ISO 9660 Extensions: Microsoft Joliet Level 3
[   95.078972] ISOFS: changing to secondary root
[ 2848.053878] eth0: link down.
[ 2852.278753] usb 1-3: USB disconnect, address 3
[ 2855.102537] usb 1-3: new full speed USB device using ohci_hcd and address 4
[ 2855.318138] usb 1-3: configuration #1 chosen from 1 choice

```

---

### Post by &amp;wP*!) on 2008-05-25
> ```

[   94.921456] ISO 9660 Extensions: Microsoft Joliet Level 3
[   95.078972] ISOFS: changing to secondary root
[ 2848.053878] eth0: link down.
[ 2852.278753] usb 1-3: USB disconnect, address 3
[ 2855.102537] usb 1-3: new full speed USB device using ohci_hcd and address 4
[ 2855.318138] usb 1-3: configuration #1 chosen from 1 choice

```

I think you need additional software/driver installation for this device, because your motherboard and thus your operating system sees that you have plugged hardware, but it could not find any driver for this.

To show what I mean, I have plugged of my webcam from USB port, and connected a Bluetooth adapter to my USB port. What I expect as a user from operating system, is, that it detects the hardware, even with name:
```
[20304.055786] usb 4-2: USB disconnect, address 2
[20317.628739] usb 4-2: new full speed USB device using uhci_hcd and address 3
[20317.799646] usb 4-2: configuration #1 chosen from 1 choice
**[20318.075385] Bluetooth: HCI USB driver ver 2.9**
[20318.077505] usbcore: registered new interface driver hci_usb
ubutku@hostubuntu:~$ 

```

I have looked at your dmesg report and I have found that you are using a USB mouse. Your hardware and operating system detect it correctly:
```

[   32.511454] usb 1-3: configuration #1 chosen from 1 choice
[   32.514513] usbcore: registered new interface driver hiddev
[B][   32.521639] input: Genius Ergo Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/input/input2
[   32.540230] input,hidraw0: USB HID v1.10 Mouse [Genius Ergo Mouse] on usb-0000:00:0b.0-1[/B]

```

Short speaking, when you plug a USB device, you must see after
```
[ 2855.318138] usb 1-3: configuration #1 chosen from 1 choice
```
another message about the hardware. If yes, then that means that your operating system can use device, without any installation. Your USB mouse and my Bluetooth-USB adapter are examples for this.

Unfortunately your USB modem is not recognized. That means, you cannot connect internet using this modem. Try to install the driver. Due to architecture of Linux, you must compile the driver or link the driver to the kernel. That means, you need to modify the kernel just for your modem, which is not simple task. It might cost a lot of time for you to run it correctly. Take a look at the drivers in your CD. If they are source codes then I am afraid you must do this...

If not, buy an Ethernet ADSL modem. Ethernet-based modems do not need installation like this. USB has this disadvantage, sorry...

---

### Post by ivanii on 2008-05-25
> **pencuse said:**
> 
Unfortunately your USB modem is not recognized. That means, you cannot connect internet using this modem. Try to install the driver. Due to architecture of Linux, you must compile the driver or link the driver to the kernel. That means, you need to modify the kernel just for your modem, which is not simple task. It might cost a lot of time for you to run it correctly. Take a look at the drivers in your CD. If they are source codes then I am afraid you must do this...

I see folders ControlPanelApplicationBinnary (gsi_cfg) and USBAnnexBinnary (file GUModem.ko)

Is it source code or what?

---

### Post by &amp;wP*!) on 2008-05-25
> **ivanii said:**
> I see folders ControlPanelApplicationBinnary (gsi_cfg) and USBAnnexBinnary (file GUModem.ko)

Is it source code or what?

I see you wanna use this USB modem instead of buying an Ethernet one. In this case you have think about that you must spend time for this, because compiling a device driver for Linux kernel is not easy. I think you have a lot of tools to play with:
[http://www.linuxquestions.org/questions/fedora-35/prolink-h9601-usb-adsl-modem-578151/](http://www.linuxquestions.org/questions/fedora-35/prolink-h9601-usb-adsl-modem-578151/)

Don't be lazy, google for "how to compile kernel for a driver" and how to use this USB modem. Search filenames on internet. I am pretty sure you will find the answer **yes** or **no**.

There are very few USB modem users in the world... I wish you find a quick solution.

---

### Post by ivanii on 2008-05-26
Well, I prefer USB over ethernet, as ethernet has its own power supply, so USB is more green solution than ethernet, as it doesn't consume power unless when computer is on.

I will have to think what is best trade-off for me.

---

