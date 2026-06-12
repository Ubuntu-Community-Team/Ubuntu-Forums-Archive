---
title: "Drive Not Ready, Not Found And Continuous System Errors On 12.04 &amp; 13.04"
date: 2013-05-02
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-05-02
Hello,

I've been having continuous system errors on 12.04 & 13.04. I have 12.04 on my system and 13.04 on a thumb drive. I was surprized to have it happen on 13.04 because I was launching it from a Flash Drive.

I have to assume that there is some incompatibility with Ubuntu and my system. I have a Dell Inspiron 5520 with a third generation I7, 8GB RAM & a 1TB HDD.

Does anyone have some insight as to what may be happening?

Thanks Hannibal

---

### Post by dabl on 2013-05-02
What, exactly, are the errors that you are seeing?

If it boots at all (either/or hdd or USB flash drive), then if you open a terminal and run "dmesg", that is probably the first place to look for a problem with your hardware and the booted kernel.

Beyond that, we'll have to see the error message to know where to investigate further.

---

### Post by coljohnhannibalsmith on 2013-05-04
Here's the output from "dmesg" on the destination drive after cloning:

```
[    1.304667] pnp 00:05: [io  0x1000-0x100f]
[    1.304668] pnp 00:05: [io  0xffff]
[    1.304669] pnp 00:05: [io  0xffff]
[    1.304671] pnp 00:05: [io  0x0400-0x0453]
[    1.304672] pnp 00:05: [io  0x0458-0x047f]
[    1.304674] pnp 00:05: [io  0x0500-0x057f]
[    1.304675] pnp 00:05: [io  0x164e-0x164f]
[    1.304677] pnp 00:05: [io  0xfd60-0xfd63]
[    1.304712] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.304714] system 00:05: [io  0x1000-0x100f] has been reserved
[    1.304716] system 00:05: [io  0xffff] has been reserved
[    1.304718] system 00:05: [io  0xffff] has been reserved
[    1.304722] system 00:05: [io  0x0400-0x0453] has been reserved
[    1.304724] system 00:05: [io  0x0458-0x047f] has been reserved
[    1.304726] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.304728] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.304730] system 00:05: [io  0xfd60-0xfd63] has been reserved
[    1.304733] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.304741] pnp 00:06: [io  0x0070-0x0077]
[    1.304746] pnp 00:06: [irq 8]
[    1.304765] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.304788] pnp 00:07: [io  0x0454-0x0457]
[    1.304818] system 00:07: [io  0x0454-0x0457] has been reserved
[    1.304820] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.304834] pnp 00:08: [io  0x0060]
[    1.304837] pnp 00:08: [io  0x0064]
[    1.304842] pnp 00:08: [irq 1]
[    1.304862] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.304877] pnp 00:09: [irq 12]
[    1.304897] pnp 00:09: Plug and Play ACPI device, IDs DLL0569 PNP0f13 (active)
[    1.322460] Freeing initrd memory: 20856k freed
[    1.362685] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.362687] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
[    1.362689] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    1.362691] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    1.362692] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    1.362694] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.362695] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
[    1.362697] pnp 00:0a: [mem 0xff000000-0xff000fff]
[    1.362699] pnp 00:0a: [mem 0xff010000-0xffffffff]
[    1.362700] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.362702] pnp 00:0a: [mem 0xafa00000-0xafa00fff]
[    1.362744] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.362746] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.362748] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.362750] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.362753] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    1.362755] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.362757] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.362759] system 00:0a: [mem 0xff000000-0xff000fff] has been reserved
[    1.362762] system 00:0a: [mem 0xff010000-0xffffffff] could not be reserved
[    1.362764] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.362766] system 00:0a: [mem 0xafa00000-0xafa00fff] has been reserved
[    1.362769] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.363005] pnp 00:0b: [mem 0x20000000-0x201fffff]
[    1.363007] pnp 00:0b: [mem 0x40004000-0x40004fff]
[    1.363053] system 00:0b: [mem 0x20000000-0x201fffff] has been reserved
[    1.363055] system 00:0b: [mem 0x40004000-0x40004fff] has been reserved
[    1.363058] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.363083] pnp: PnP ACPI: found 12 devices
[    1.363084] ACPI: ACPI bus type pnp unregistered
[    1.369415] PCI: max bus depth: 1 pci_try_num: 2
[    1.369438] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.369442] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.369451] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
[    1.369458] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.369464] pci 0000:00:1c.1:   bridge window [mem 0xc0500000-0xc05fffff]
[    1.369485] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.369492] pci 0000:00:1c.0: setting latency timer to 64
[    1.369502] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.369507] pci 0000:00:1c.1: setting latency timer to 64
[    1.369511] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.369513] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.369515] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.369517] pci_bus 0000:00: resource 7 [mem 0xafa00000-0xfeafffff]
[    1.369519] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    1.369522] pci_bus 0000:01: resource 2 [mem 0xc0400000-0xc04fffff 64bit pref]
[    1.369524] pci_bus 0000:02: resource 1 [mem 0xc0500000-0xc05fffff]
[    1.369551] NET: Registered protocol family 2
[    1.369717] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.370421] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.371546] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.371671] TCP: Hash tables configured (established 524288 bind 65536)
[    1.371673] TCP reno registered
[    1.371687] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.371719] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.371800] NET: Registered protocol family 1
[    1.371812] pci 0000:00:02.0: Boot video device
[    1.371829] pci 0000:00:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.373071] pci 0000:00:14.0: PCI INT A disabled
[    1.373083] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.386567] pci 0000:00:1a.0: PCI INT A disabled
[    1.386589] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.402540] pci 0000:00:1d.0: PCI INT A disabled
[    1.402581] PCI: CLS 64 bytes, default 64
[    1.402583] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.402585] Placing 64MB software IO TLB between ffff8800a6ab8000 - ffff8800aaab8000
[    1.402587] software IO TLB at phys 0xa6ab8000 - 0xaaab8000
[    1.402604] Simple Boot Flag at 0x44 set to 0x1
[    1.403184] audit: initializing netlink socket (disabled)
[    1.403191] type=2000 audit(1367668535.168:1): initialized
[    1.427819] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.429655] VFS: Disk quotas dquot_6.5.2
[    1.429699] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.430102] fuse init (API version 7.17)
[    1.430178] msgmni has been set to 15770
[    1.430499] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.430525] io scheduler noop registered
[    1.430527] io scheduler deadline registered
[    1.430552] io scheduler cfq registered (default)
[    1.430725] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.430740] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.430780] intel_idle: MWAIT substates: 0x21120
[    1.430782] intel_idle: v0.4 model 0x3A
[    1.430783] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.430852] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.430890] ACPI: AC Adapter [ACAD] (off-line)
[    1.430982] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0
[    1.430987] ACPI: Power Button [PWRB]
[    1.431027] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    1.431049] ACPI: Lid Switch [LID0]
[    1.431084] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.431087] ACPI: Power Button [PWRF]
[    1.431140] ACPI: Fan [FAN0] (off)
[    1.431167] ACPI: Fan [FAN1] (off)
[    1.431193] ACPI: Fan [FAN2] (off)
[    1.431217] ACPI: Fan [FAN3] (off)
[    1.431245] ACPI: Fan [FAN4] (off)
[    1.538544] thermal LNXTHERM:00: registered as thermal_zone0
[    1.538548] ACPI: Thermal Zone [TZ00] (28 C)
[    1.538713] thermal LNXTHERM:01: registered as thermal_zone1
[    1.538715] ACPI: Thermal Zone [TZ01] (30 C)
[    1.538730] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.538737] ACPI: Battery Slot [BAT1] (battery present)
[    1.538763] ERST: Table is not found!
[    1.538764] GHES: HEST is not enabled!
[    1.538823] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.630651] Linux agpgart interface v0.103
[    1.630722] agpgart-intel 0000:00:00.0: Intel Ivybridge Chipset
[    1.630855] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.632364] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.632481] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[    1.633649] brd: module loaded
[    1.634256] loop: module loaded
[    1.634363] ahci 0000:00:1f.2: version 3.0
[    1.634383] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.634428] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.650183] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.650186] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.650192] ahci 0000:00:1f.2: setting latency timer to 64
[    1.658554] scsi0 : ahci
[    1.658630] scsi1 : ahci
[    1.658694] scsi2 : ahci
[    1.658756] scsi3 : ahci
[    1.658818] scsi4 : ahci
[    1.658876] scsi5 : ahci
[    1.658955] ata1: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617100 irq 40
[    1.658956] ata2: DUMMY
[    1.658959] ata3: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617200 irq 40
[    1.658961] ata4: DUMMY
[    1.658962] ata5: DUMMY
[    1.658963] ata6: DUMMY
[    1.659295] Fixed MDIO Bus: probed
[    1.659309] tun: Universal TUN/TAP device driver, 1.6
[    1.659310] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.659351] PPP generic driver version 2.4.2
[    1.659433] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.659448] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.659462] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.659466] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.659501] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.659526] ehci_hcd 0000:00:1a.0: debug port 2
[    1.663414] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.663428] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc0619000
[    1.678114] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.678230] hub 1-0:1.0: USB hub found
[    1.678234] hub 1-0:1.0: 2 ports detected
[    1.678285] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.678299] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.678302] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.678340] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.678361] ehci_hcd 0000:00:1d.0: debug port 2
[    1.682245] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.682258] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xc0618000
[    1.698084] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.698186] hub 2-0:1.0: USB hub found
[    1.698189] hub 2-0:1.0: 2 ports detected
[    1.698236] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.698245] uhci_hcd: USB Universal Host Controller Interface driver
[    1.698268] xhci_hcd 0000:00:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.698294] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.698298] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.698334] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.698420] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.698461] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    1.698560] xHCI xhci_add_endpoint called for root hub
[    1.698562] xHCI xhci_check_bandwidth called for root hub
[    1.698588] hub 3-0:1.0: USB hub found
[    1.698596] hub 3-0:1.0: 4 ports detected
[    1.698642] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.698681] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.698747] xHCI xhci_add_endpoint called for root hub
[    1.698749] xHCI xhci_check_bandwidth called for root hub
[    1.698768] hub 4-0:1.0: USB hub found
[    1.698775] hub 4-0:1.0: 4 ports detected
[    1.738077] ACPI: Battery Slot [BAT1] (battery present)
[    1.750048] usbcore: registered new interface driver libusual
[    1.750080] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.772920] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.772925] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.773008] mousedev: PS/2 mouse device common for all mice
[    1.775040] rtc_cmos 00:06: RTC can wake from S4
[    1.775139] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.775167] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.775229] device-mapper: uevent: version 1.0.3
[    1.775284] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.775476] cpuidle: using governor ladder
[    1.775772] cpuidle: using governor menu
[    1.775773] EFI Variables Facility v0.08 2004-May-17
[    1.775941] TCP cubic registered
[    1.776025] NET: Registered protocol family 10
[    1.776371] NET: Registered protocol family 17
[    1.776374] Registering the dns_resolver key type
[    1.776487] PM: Hibernation image not present or could not be loaded.
[    1.776501] registered taskstats version 1
[    1.783812]   Magic number: 13:349:933
[    1.783817] mdio_bus 0: hash matches
[    1.783921] rtc_cmos 00:06: setting system clock to 2013-05-04 11:55:36 UTC (1367668536)
[    1.785138] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.785139] EDD information not available.
[    1.793699] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.977753] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.983755] ata3.00: ATAPI: PLDS DVD+/-RW DS-8A8SH, KD11, max UDMA/100
[    1.984840] ata3.00: configured for UDMA/100
[    1.985720] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.989744] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.100381] ata1.00: ATA-9: ST1000LM014-1EJ164, SM11, max UDMA/133
[    2.100388] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.122384] hub 1-1:1.0: USB hub found
[    2.122620] hub 1-1:1.0: 6 ports detected
[    2.144635] ata1.00: configured for UDMA/133
[    2.144879] scsi 0:0:0:0: Direct-Access     ATA      ST1000LM014-1EJ1 SM11 PQ: 0 ANSI: 5
[    2.145033] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.145035] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.145038] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.145075] sd 0:0:0:0: [sda] Write Protect is off
[    2.145078] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.145094] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.146408]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.147205] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.149750] scsi 2:0:0:0: CD-ROM            PLDS     DVD+-RW DS-8A8SH KD11 PQ: 0 ANSI: 5
[    2.154152] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.154158] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.154382] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.154472] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.155873] Freeing unused kernel memory: 920k freed
[    2.155965] Write protecting the kernel read-only data: 12288k
[    2.159547] Freeing unused kernel memory: 1596k freed
[    2.162269] Freeing unused kernel memory: 1188k freed
[    2.175639] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    2.175992] zram: num_devices not specified. Using default: 1
[    2.175994] zram: Creating 1 devices ...
[    2.178636] udevd[133]: starting version 175
[    2.191005] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.191026] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.191068] r8169 0000:01:00.0: setting latency timer to 64
[    2.191155] r8169 0000:01:00.0: irq 42 for MSI/MSI-X
[    2.191546] r8169 0000:01:00.0: eth0: RTL8105e at 0xffffc90000c36000, d4:be:d9:44:03:ce, XID 00c00000 IRQ 42
[    2.193252] [drm] Initialized drm 1.1.0 20060810
[    2.195628] wmi: Mapper loaded
[    2.197974] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.197980] i915 0000:00:02.0: setting latency timer to 64
[    2.199887] Adding 4039192k swap on /dev/zram0.  Priority:100 extents:1 across:4039192k SS
[    2.233309] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.245405] mtrr: type mismatch for b0000000,10000000 old: write-back new: write-combining
[    2.245407] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    2.245636] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    2.245648] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.245649] [drm] Driver supports precise vblank timestamp query.
[    2.246004] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.365845] hub 2-1:1.0: USB hub found
[    2.365934] hub 2-1:1.0: 8 ports detected
[    2.401123] Refined TSC clocksource calibration: 2095.240 MHz.
[    2.401127] Switching to clocksource tsc
[    2.437276] usb 1-1.3: new high-speed USB device number 3 using ehci_hcd
[    2.601017] usb 1-1.5: new high-speed USB device number 4 using ehci_hcd
[    2.823471] fbcon: inteldrmfb (fb0) is primary device
[    2.823508] Console: switching to colour frame buffer device 170x48
[    2.823534] fb0: inteldrmfb frame buffer device
[    2.823535] drm: registered panic notifier
[    2.848642] usb 2-1.5: new full-speed USB device number 3 using ehci_hcd
[    2.869292] ACPI Warning: _BQC returned an invalid level (20110623/video-494)
[    2.869403] acpi device:30: registered as cooling_device13
[    2.869571] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    2.869678] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.869706] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.442705] Btrfs loaded
[    3.446430] xor: automatically using best checksumming function: generic_sse
[    3.463437]    generic_sse: 13612.000 MB/sec
[    3.463439] xor: using function: generic_sse (13612.000 MB/sec)
[    3.463962] device-mapper: dm-raid45: initialized v0.2594b
[    8.508506] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    8.508508] EXT4-fs (sda5): write access will be enabled during recovery
[    8.980498] EXT4-fs (sda5): recovery complete
[    9.007838] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   12.163889] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.166540] udevd[463]: starting version 175
[   12.173372] lp: driver loaded but no devices found
[   12.259825] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   12.260104] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.260111] mei 0000:00:16.0: setting latency timer to 64
[   12.260170] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[   12.270559] type=1400 audit(1367686547.001:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=667 comm="apparmor_parser"
[   12.270900] type=1400 audit(1367686547.001:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=667 comm="apparmor_parser"
[   12.271075] type=1400 audit(1367686547.001:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=667 comm="apparmor_parser"
[   12.271933] cfg80211: Calling CRDA to update world regulatory domain
[   12.276710] Bluetooth: Core ver 2.16
[   12.276724] NET: Registered protocol family 31
[   12.276726] Bluetooth: HCI device and connection manager initialized
[   12.276728] Bluetooth: HCI socket layer initialized
[   12.276730] Bluetooth: L2CAP socket layer initialized
[   12.276740] Bluetooth: SCO socket layer initialized
[   12.276955] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   12.277175] usbcore: registered new interface driver btusb
[   12.279594] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   12.280328] Linux video capture interface: v2.00
[   12.280455] Initializing rts5139 USB card reader driver...
[   12.280688] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_E4HD (0c45:644a)
[   12.281269] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.281272] Copyright(c) 2003-2011 Intel Corporation
[   12.281332] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.281363] iwlwifi 0000:02:00.0: setting latency timer to 64
[   12.281388] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   12.281391] iwlwifi 0000:02:00.0: pci_resource_base = ffffc900117d8000
[   12.281393] iwlwifi 0000:02:00.0: HW Revision ID = 0xC4
[   12.281514] iwlwifi 0000:02:00.0: irq 45 for MSI/MSI-X
[   12.281590] iwlwifi 0000:02:00.0: Detected 2000 Series 2x2 BGN/BT, REV=0xC8
[   12.281691] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   12.283360] scsi6 : SCSI emulation for RTS5139 USB card reader
[   12.283538] usbcore: registered new interface driver rts5139
[   12.283540] Realtek rts5139 USB card reader support registered.
[   12.283569] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   12.283919] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   12.285046] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   12.297612] device-mapper: multipath: version 1.3.1 loaded
[   12.298166] iwlwifi 0000:02:00.0: device EEPROM VER=0x81c, CALIB=0x6
[   12.298170] iwlwifi 0000:02:00.0: Device SKU: 0X150
[   12.298172] iwlwifi 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   12.299383] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.300379] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.300433] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   12.300457] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   12.301021] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.307304] input: Laptop_Integrated_Webcam_E4HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input5
[   12.307382] usbcore: registered new interface driver uvcvideo
[   12.307385] USB Video Class driver (1.1.1)
[   12.326190] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   12.335687] cfg80211: World regulatory domain updated:
[   12.335690] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.335692] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.335695] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.335697] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.335699] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.335701] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.338287] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1
[   12.338486] Registered led device: phy0-led
[   12.338518] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   12.341217] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.366945] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   12.483335] RPC: Registered named UNIX socket transport module.
[   12.483338] RPC: Registered udp transport module.
[   12.483340] RPC: Registered tcp transport module.
[   12.483342] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   12.486917] FS-Cache: Loaded
[   12.493594] init: failsafe main process (966) killed by TERM signal
[   12.493784] FS-Cache: Netfs 'nfs' registered for caching
[   12.496362] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   12.574325] ppdev: user-space parallel port driver
[   12.585768] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.585771] Bluetooth: BNEP filters: protocol multicast
[   12.588497] Bluetooth: RFCOMM TTY layer initialized
[   12.588502] Bluetooth: RFCOMM socket layer initialized
[   12.588504] Bluetooth: RFCOMM ver 1.11
[   12.597347] type=1400 audit(1367686547.325:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1074 comm="apparmor_parser"
[   12.597737] type=1400 audit(1367686547.325:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1074 comm="apparmor_parser"
[   12.609801] type=1400 audit(1367686547.337:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1111 comm="apparmor_parser"
[   12.610475] type=1400 audit(1367686547.341:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1115 comm="apparmor_parser"
[   12.611019] type=1400 audit(1367686547.341:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1119 comm="apparmor_parser"
[   12.611094] type=1400 audit(1367686547.341:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1115 comm="apparmor_parser"
[   12.611519] type=1400 audit(1367686547.341:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1116 comm="apparmor_parser"
[   12.665515] init: alsa-restore main process (1158) terminated with status 19
[   12.829274] r8169 0000:01:00.0: eth0: link down
[   12.829762] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.830019] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.831461] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   12.839025] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   12.839210] hda_codec: CX20590: BIOS auto-probing.
[   12.842458] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   12.843113] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   12.843172] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   12.843234] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.843282] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.870937] psmouse serio1: elantech: Synaptics capabilities query result 0x79, 0x17, 0x0c.
[   13.013727] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input10
[   13.101032] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   13.108614] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   13.197416] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.198251] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.369009] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 16000000, was 12060000
[   13.928026] init: anacron main process (1196) killed by TERM signal
[   14.365611] init: plymouth-stop pre-start process (1893) terminated with status 1
[   15.358380] wlan0: authenticate with 00:22:55:c4:c5:30 (try 1)
[   15.359939] wlan0: authenticated
[   15.365654] wlan0: associate with 00:22:55:c4:c5:30 (try 1)
[   15.367230] wlan0: RX AssocResp from 00:22:55:c4:c5:30 (capab=0x401 status=0 aid=66)
[   15.367233] wlan0: associated
[   15.371164] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.586490] wlan0: no IPv6 routers present
[  157.010727] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 16070000, was 16000000
[  316.687288] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 00070000, was 16070000

```

---

