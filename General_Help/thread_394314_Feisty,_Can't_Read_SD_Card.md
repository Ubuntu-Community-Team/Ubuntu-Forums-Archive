---
title: "Feisty, Can't Read SD Card?"
date: 2007-03-26
forum: General Help
---

### Post by tsav87 on 2007-03-26
Upgraded to Feisty, SD Card doesn't read.  What gives?

---

### Post by will_in_wi on 2007-03-26
can you open a terminal, type dmesg, and post the output?

---

### Post by tsav87 on 2007-03-26
```
[    0.073048] EISA bus registered
[    0.073051] ACPI: bus type pci registered
[    0.099701] PCI: PCI BIOS revision 2.10 entry at 0xfb4d6, last bus=14
[    0.099703] PCI: Using configuration type 1
[    0.099704] Setting up standard PCI resources
[    0.124486] ACPI: Interpreter enabled
[    0.124488] ACPI: Using IOAPIC for interrupt routing
[    0.125002] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.125009] PCI: Probing PCI hardware (bus 00)
[    0.125084] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.137065] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.137069] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.137276] Boot video device is 0000:01:00.0
[    0.138304] PCI: Transparent bridge - 0000:00:1e.0
[    0.138386] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.155932] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
[    0.156144] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[    0.156353] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.156561] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.156777] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.156987] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.157198] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.157409] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.157751] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.158697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.158911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.159106] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.159365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.159721] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.159729] pnp: PnP ACPI init
[    0.187438] pnp: PnP ACPI: found 11 devices
[    0.187441] PnPBIOS: Disabled by ACPI PNP
[    0.187477] PCI: Using ACPI for IRQ routing
[    0.187480] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.232498] NET: Registered protocol family 8
[    0.232500] NET: Registered protocol family 20
[    0.248151] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.248153] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[    0.248156] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[    0.248160] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.248162] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    0.248165] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    0.248167] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    0.248169] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.248172] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.248177] pnp: 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.248180] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    0.248182] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    0.248184] pnp: 00:08: ioport range 0x930-0x97f has been reserved
[    0.248422] PCI: Bridge: 0000:00:01.0
[    0.248424]   IO window: e000-efff
[    0.248427]   MEM window: dd000000-dfefffff
[    0.248430]   PREFETCH window: c0000000-cfffffff
[    0.248433] PCI: Bridge: 0000:00:1c.0
[    0.248434]   IO window: disabled.
[    0.248440]   MEM window: disabled.
[    0.248443]   PREFETCH window: disabled.
[    0.248449] PCI: Bridge: 0000:00:1c.1
[    0.248450]   IO window: disabled.
[    0.248456]   MEM window: dcf00000-dcffffff
[    0.248460]   PREFETCH window: disabled.
[    0.248465] PCI: Bridge: 0000:00:1c.3
[    0.248468]   IO window: d000-dfff
[    0.248474]   MEM window: dcc00000-dcefffff
[    0.248478]   PREFETCH window: d0000000-d01fffff
[    0.248484] PCI: Bridge: 0000:00:1e.0
[    0.248486]   IO window: disabled.
[    0.248491]   MEM window: dcb00000-dcbfffff
[    0.248495]   PREFETCH window: disabled.
[    0.248509] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.248514] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.248535] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.248541] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.248564] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    0.248569] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.248593] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[    0.248598] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.248611] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.248637] NET: Registered protocol family 2
[    0.291904] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.291995] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.292573] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.292868] TCP: Hash tables configured (established 131072 bind 65536)
[    0.292870] TCP reno registered
[    0.303968] checking if image is initramfs... it is
[    0.814288] Freeing initrd memory: 6748k freed
[    0.814450] Simple Boot Flag at 0x79 set to 0x1
[    0.814833] audit: initializing netlink socket (disabled)
[    0.814848] audit(1174949285.584:1): initialized
[    0.814933] highmem bounce pool size: 64 pages
[    0.815009] VFS: Disk quotas dquot_6.5.1
[    0.815027] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.815071] io scheduler noop registered
[    0.815073] io scheduler anticipatory registered
[    0.815075] io scheduler deadline registered
[    0.815085] io scheduler cfq registered (default)
[    0.815320] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.815350] assign_interrupt_mode Found MSI capability
[    0.815352] Allocate Port Service[0000:00:01.0:pcie00]
[    0.815425] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.815478] assign_interrupt_mode Found MSI capability
[    0.815480] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.815511] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.815629] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.815683] assign_interrupt_mode Found MSI capability
[    0.815685] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.815711] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.815820] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.815874] assign_interrupt_mode Found MSI capability
[    0.815876] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.815900] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.816055] isapnp: Scanning for PnP cards...
[    1.170352] isapnp: No Plug & Play device found
[    1.189087] Real Time Clock Driver v1.12ac
[    1.189140] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.189644] mice: PS/2 mouse device common for all mice
[    1.190116] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.190243] input: Macintosh mouse button emulation as /class/input/input0
[    1.190273] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.190276] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.190501] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.193220] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.193224] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.193312] EISA: Probing bus 0 at eisa.0
[    1.193321] Cannot allocate resource for EISA slot 1
[    1.193351] EISA: Detected 0 cards.
[    1.203474] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.223500] TCP cubic registered
[    1.223509] NET: Registered protocol family 1
[    1.223529] Starting balanced_irq
[    1.223535] Using IPI No-Shortcut mode
[    1.223644] ACPI: (supports S0 S3 S4 S5)
[    1.223686]   Magic number: 15:58:857
[    1.223757]   hash matches device ptyv9
[    1.223766]   hash matches device ptysc
[    1.223940] Freeing unused kernel memory: 328k freed
[    1.227411] Time: tsc clocksource has been installed.
[    2.384695] Capability LSM initialized
[    2.414621] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.414766] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.414938] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.414942] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.415283] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.415415] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.415611] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.415615] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.008000] ACPI: Thermal Zone [THM] (40 C)
[    3.012000] Time: acpi_pm clocksource has been installed.
[    3.264000] usbcore: registered new interface driver usbfs
[    3.264000] usbcore: registered new interface driver hub
[    3.264000] usbcore: registered new device driver usb
[    3.264000] USB Universal Host Controller Interface driver v3.0
[    3.264000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[    3.264000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.264000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.264000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.264000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000bf80
[    3.264000] usb usb1: configuration #1 chosen from 1 choice
[    3.264000] hub 1-0:1.0: USB hub found
[    3.264000] hub 1-0:1.0: 2 ports detected
[    3.332000] ieee1394: Initialized config rom entry `ip1394'
[    3.368000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[    3.368000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.368000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.368000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.368000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000bf60
[    3.372000] usb usb2: configuration #1 chosen from 1 choice
[    3.372000] hub 2-0:1.0: USB hub found
[    3.372000] hub 2-0:1.0: 2 ports detected
[    3.372000] SCSI subsystem initialized
[    3.376000] libata version 2.20 loaded.
[    3.476000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[    3.476000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.476000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.476000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.476000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000bf40
[    3.476000] usb usb3: configuration #1 chosen from 1 choice
[    3.476000] hub 3-0:1.0: USB hub found
[    3.476000] hub 3-0:1.0: 2 ports detected
[    3.580000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
[    3.580000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.580000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.580000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.580000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000bf20
[    3.580000] usb usb4: configuration #1 chosen from 1 choice
[    3.580000] hub 4-0:1.0: USB hub found
[    3.580000] hub 4-0:1.0: 2 ports detected
[    3.608000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.684000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[    3.684000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.684000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.684000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.684000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.684000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.684000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80000
[    3.688000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.688000] usb usb5: configuration #1 chosen from 1 choice
[    3.688000] hub 5-0:1.0: USB hub found
[    3.688000] hub 5-0:1.0: 8 ports detected
[    3.792000] b44.c:v1.01 (Jun 16, 2006)
[    3.792000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    3.792000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:15:c5:37:47:b6
[    3.792000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[    3.848000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dcbfd800-dcbfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.852000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.852000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.852000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[    3.852000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.852000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    3.852000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    3.852000] scsi0 : ata_piix
[    4.020000] ata1.00: ATA-7: ST910021AS, 8.02, max UDMA/133
[    4.020000] ata1.00: 192426570 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    4.032000] ata1.00: configured for UDMA/133
[    4.032000] scsi1 : ata_piix
[    4.132000] usb 1-1: device not accepting address 2, error -71
[    4.352000] ata2.00: ATAPI, max UDMA/33
[    4.520000] ata2.00: configured for UDMA/33
[    4.520000] scsi 0:0:0:0: Direct-Access     ATA      ST910021AS       8.02 PQ: 0 ANSI: 5
[    4.520000] scsi 1:0:0:0: CD-ROM            PHILIPS  DVD+-RW SDVD8820 AD15 PQ: 0 ANSI: 5
[    4.524000] SCSI device sda: 192426570 512-byte hdwr sectors (98522 MB)
[    4.524000] sda: Write Protect is off
[    4.524000] sda: Mode Sense: 00 3a 00 00
[    4.524000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.524000] SCSI device sda: 192426570 512-byte hdwr sectors (98522 MB)
[    4.524000] sda: Write Protect is off
[    4.524000] sda: Mode Sense: 00 3a 00 00
[    4.524000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.524000]  sda:<6>usb 5-1: new high speed USB device using ehci_hcd and address 2
[    4.592000]  sda1 sda2 < sda5 >
[    4.620000] sd 0:0:0:0: Attached scsi disk sda
[    4.624000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.624000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.640000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.640000] Uniform CD-ROM driver Revision: 3.20
[    4.640000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.688000] usb 5-1: configuration #1 chosen from 1 choice
[    4.688000] hub 5-1:1.0: USB hub found
[    4.688000] hub 5-1:1.0: 4 ports detected
[    4.824000] Attempting manual resume
[    4.824000] swsusp: Resume From Partition 8:5
[    4.824000] PM: Checking swsusp image.
[    4.824000] PM: Resume from disk failed.
[    4.860000] kjournald starting.  Commit interval 5 seconds
[    4.860000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.032000] usb 5-5: new high speed USB device using ehci_hcd and address 3
[    5.124000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[324fc0003b121141]
[    5.164000] usb 5-5: configuration #1 chosen from 1 choice
[    5.164000] hub 5-5:1.0: USB hub found
[    5.164000] hub 5-5:1.0: 4 ports detected
[    5.468000] usb 5-1.4: new full speed USB device using ehci_hcd and address 4
[    5.620000] usb 5-1.4: configuration #1 chosen from 1 choice
[    5.840000] usb 5-5.1: new high speed USB device using ehci_hcd and address 5
[    5.948000] usb 5-5.1: configuration #1 chosen from 1 choice
[    5.948000] hub 5-5.1:1.0: USB hub found
[    5.948000] hub 5-5.1:1.0: 4 ports detected
[    6.268000] usb 5-5.2: new high speed USB device using ehci_hcd and address 6
[    6.376000] usb 5-5.2: configuration #1 chosen from 1 choice
[    6.592000] usb 5-5.3: new low speed USB device using ehci_hcd and address 7
[    6.704000] usb 5-5.3: configuration #1 chosen from 1 choice
[    6.920000] usb 5-5.4: new low speed USB device using ehci_hcd and address 8
[    7.032000] usb 5-5.4: configuration #1 chosen from 1 choice
[    7.248000] usb 5-5.1.1: new high speed USB device using ehci_hcd and address 9
[    7.368000] usb 5-5.1.1: configuration #1 chosen from 1 choice
[    7.584000] usb 5-5.1.2: new full speed USB device using ehci_hcd and address 10
[    7.692000] usb 5-5.1.2: configuration #1 chosen from 1 choice
[    7.908000] usb 5-5.1.3: new full speed USB device using ehci_hcd and address 11
[    8.016000] usb 5-5.1.3: configuration #1 chosen from 1 choice
[    8.232000] usb 5-5.1.4: new full speed USB device using ehci_hcd and address 12
[    8.340000] usb 5-5.1.4: configuration #1 chosen from 1 choice
[   15.016000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.016000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.036000] iTCO_vendor_support: vendor-support=0
[   15.036000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   15.036000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   15.036000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.060000] intel_rng: FWH not detected
[   15.156000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.168000] agpgart: Detected an Intel 945GM Chipset.
[   15.184000] agpgart: AGP aperture is 256M @ 0x0
[   15.372000] input: PC Speaker as /class/input/input2
[   15.484000] sdhci: Secure Digital Host Controller Interface driver
[   15.484000] sdhci: Copyright(c) Pierre Ossman
[   15.484000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
[   15.484000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   15.488000] mmc0: SDHCI at 0xdcbfd400 irq 23 DMA
[   15.676000] nvidia: module license 'NVIDIA' taints kernel.
[   15.924000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.924000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   15.924000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   15.936000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xfa0b1, caps: 0xa04713/0x200000
[   15.976000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   16.068000] ieee80211_crypt: registered algorithm 'NULL'
[   16.088000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.088000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.132000] Bluetooth: Core ver 2.11
[   16.132000] NET: Registered protocol family 31
[   16.132000] Bluetooth: HCI device and connection manager initialized
[   16.132000] Bluetooth: HCI socket layer initialized
[   16.156000] usbcore: registered new interface driver usbserial
[   16.156000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   16.212000] NET: Registered protocol family 17
[   16.248000] mmcblk0: mmc0:8ff8 SD01G 992000KiB 
[   16.248000]  mmcblk0: p1
[   16.272000] Bluetooth: HCI USB driver ver 2.9
[   16.332000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   16.332000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   16.336000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   16.336000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   16.336000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.444000] usbcore: registered new interface driver hci_usb
[   16.476000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   16.476000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   16.684000] usbcore: registered new interface driver usbserial_generic
[   16.684000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   16.684000] usbcore: registered new interface driver hiddev
[   16.684000] input: DELL DELL USB Keyboard as /class/input/input4
[   16.688000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.7-5.3
[   16.688000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input5
[   16.688000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-5.4
[   16.784000] drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[   17.068000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   17.068000] b44: eth0: Flow control is off for TX and off for RX.
[   17.332000] eth1: register 'asix' at usb-0000:00:1d.7-5.1.1, ASIX AX88772 USB 2.0 Ethernet, 00:50:5b:07:0a:f0
[   17.332000] usbcore: registered new interface driver asix
[   17.332000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 10 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[   17.332000] usbcore: registered new interface driver usblp
[   17.332000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   17.332000] usbcore: registered new interface driver xpad
[   17.332000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   17.340000] usbcore: registered new interface driver libusual
[   17.340000] pl2303 5-5.1.3:1.0: pl2303 converter detected
[   17.340000] usb 5-5.1.3: pl2303 converter now attached to ttyUSB0
[   17.348000] Initializing USB Mass Storage driver...
[   17.348000] scsi2 : SCSI emulation for USB Mass Storage devices
[   17.348000] usb-storage: device found at 6
[   17.348000] usb-storage: waiting for device to settle before scanning
[   17.360000] usbcore: registered new interface driver snd-usb-audio
[   17.360000] usbcore: registered new interface driver usb-storage
[   17.360000] USB Mass Storage support registered.
[   17.360000] input: USB Audio as /class/input/input6
[   17.360000] input: USB HID v1.00 Device [USB Audio] on usb-0000:00:1d.7-5.1.4
[   17.360000] usbcore: registered new interface driver usbhid
[   17.360000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   17.360000] usbcore: registered new interface driver pl2303
[   17.360000] drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
[   17.364000] eth1: link down
[   17.712000] lp: driver loaded but no devices found
[   17.764000] fuse init (API version 7.8)
[   17.788000] Adding 3927852k swap on /dev/disk/by-uuid/faa95a38-b0cf-4edc-8143-4209df07391c.  Priority:-1 extents:1 across:3927852k
[   17.880000] EXT3 FS on sda1, internal journal
[   18.244000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   19.556000] NET: Registered protocol family 10
[   19.556000] lo: Disabled Privacy Extensions
[   19.556000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.556000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   20.292000] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   21.396000] ACPI: AC Adapter [AC] (on-line)
[   21.448000] ACPI: Battery Slot [BAT0] (battery present)
[   21.460000] input: Lid Switch as /class/input/input7
[   21.460000] ACPI: Lid Switch [LID]
[   21.460000] input: Power Button (CM) as /class/input/input8
[   21.460000] ACPI: Power Button (CM) [PBTN]
[   21.460000] input: Sleep Button (CM) as /class/input/input9
[   21.460000] ACPI: Sleep Button (CM) [SBTN]
[   21.564000] Using specific hotkey driver
[   21.608000] No dock devices found.
[   21.640000] ibm_acpi: ec object not found
[   21.732000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   21.732000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   21.732000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   21.748000] pcc_acpi: loading...
[   22.348000] usb-storage: device scan complete
[   22.352000] scsi 2:0:0:0: Direct-Access     TOSHIBA  MK6034GAX        AC10 PQ: 0 ANSI: 0 CCS
[   22.360000] SCSI device sdb: 117210240 512-byte hdwr sectors (60012 MB)
[   22.360000] sdb: Write Protect is off
[   22.360000] sdb: Mode Sense: 00 14 00 00
[   22.360000] sdb: assuming drive cache: write through
[   22.360000] SCSI device sdb: 117210240 512-byte hdwr sectors (60012 MB)
[   22.360000] sdb: Write Protect is off
[   22.360000] sdb: Mode Sense: 00 14 00 00
[   22.360000] sdb: assuming drive cache: write through
[   22.360000]  sdb: sdb1
[   22.812000] sd 2:0:0:0: Attached scsi disk sdb
[   22.812000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   29.152000] ppdev: user-space parallel port driver
[   32.840000] apm: BIOS not found.
[   33.468000] Bluetooth: L2CAP ver 2.8
[   33.468000] Bluetooth: L2CAP socket layer initialized
[   33.528000] Bluetooth: RFCOMM socket layer initialized
[   33.528000] Bluetooth: RFCOMM TTY layer initialized
[   33.528000] Bluetooth: RFCOMM ver 1.8
[   43.428000] eth0: no IPv6 routers present
[ 3007.428000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3007.428000]     Additional sense: Medium not present - tray closed
[ 3007.428000] end_request: I/O error, dev sr0, sector 0
[ 3007.428000] Buffer I/O error on device sr0, logical block 0
[ 3007.428000] Buffer I/O error on device sr0, logical block 1
[ 3007.428000] Buffer I/O error on device sr0, logical block 2
[ 3007.428000] Buffer I/O error on device sr0, logical block 3
[ 3007.428000] Buffer I/O error on device sr0, logical block 4
[ 3007.428000] Buffer I/O error on device sr0, logical block 5
[ 3007.428000] Buffer I/O error on device sr0, logical block 6
[ 3007.428000] Buffer I/O error on device sr0, logical block 7
[ 3007.428000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3007.428000]     Additional sense: Medium not present - tray closed
[ 3007.428000] end_request: I/O error, dev sr0, sector 0
[ 3007.428000] Buffer I/O error on device sr0, logical block 0
[ 3007.432000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3007.432000]     Additional sense: Medium not present - tray closed
[ 3007.432000] end_request: I/O error, dev sr0, sector 4
[ 3007.432000] Buffer I/O error on device sr0, logical block 1
[ 3037.476000] mmcblk0: mmc0:8000 SD01G 992000KiB 
[ 3037.476000]  mmcblk0: p1
[ 3235.624000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3235.624000]     Additional sense: Medium not present - tray closed
[ 3235.624000] end_request: I/O error, dev sr0, sector 0
[ 3235.624000] Buffer I/O error on device sr0, logical block 0
[ 3235.624000] Buffer I/O error on device sr0, logical block 1
[ 3235.624000] Buffer I/O error on device sr0, logical block 2
[ 3235.624000] Buffer I/O error on device sr0, logical block 3
[ 3235.624000] Buffer I/O error on device sr0, logical block 4
[ 3235.624000] Buffer I/O error on device sr0, logical block 5
[ 3235.624000] Buffer I/O error on device sr0, logical block 6
[ 3235.624000] Buffer I/O error on device sr0, logical block 7
[ 3235.628000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3235.628000]     Additional sense: Medium not present - tray closed
[ 3235.628000] end_request: I/O error, dev sr0, sector 0
[ 3235.628000] Buffer I/O error on device sr0, logical block 0
[ 3235.632000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3235.632000]     Additional sense: Medium not present - tray closed
[ 3235.632000] end_request: I/O error, dev sr0, sector 4
[ 3235.632000] Buffer I/O error on device sr0, logical block 1
[ 9720.244000] mmcblk0: mmc0:8000 SD01G 992000KiB 
[ 9720.244000]  mmcblk0: p1

```

---

### Post by tsav87 on 2007-03-27
bump

---

### Post by tsav87 on 2007-03-28
bumpa

---

### Post by fanatik on 2007-03-28
so it detects the device and it shows as /dev/sda with 1 partitions, sda1. can you now type **mount** and post the output so we can see how it has mounted that device?

Cheers,
James.

---

### Post by tsav87 on 2007-03-28
```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-13-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
```

---

### Post by fanatik on 2007-03-28
my mistake, its /dev/sdb1. Ok so it shows as mounting it read/write on /media/disk with a uid of 1000, which should be your id.

So on to directory permissions, can you paste the output from:

id
ls -ld /media/disk

then remove your card, and type:

ls -l /media

insert the card, then type:

touch /media/disk/testfile

Thanks,
James.

---

### Post by tsav87 on 2007-03-28
```
travis@travis-laptop:~$ id
uid=1000(travis) gid=1000(travis) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),115(fuse),1000(travis)
travis@travis-laptop:~$ ls -ld /media/disk
drwx------ 5 travis root 16384 1969-12-31 18:00 /media/disk
```

```
travis@travis-laptop:~$ ls -l /media
total 56
lrwxrwxrwx 1 root   root     6 2007-03-22 19:03 cdrom -> cdrom0
drwxr-xr-x 2 root   root  4096 2007-03-22 19:03 cdrom0
drwx------ 5 travis root 16384 1969-12-31 18:00 disk
lrwxrwxrwx 1 root   root     7 2007-03-22 19:03 floppy -> floppy0
drwxr-xr-x 2 root   root  4096 2007-03-22 19:03 floppy0
drwxr-xr-x 2 root   root  4096 2007-03-25 13:39 NIKON D80
drwxr-xr-x 2 root   root  4096 2007-03-23 16:42 sdc1
drwxr-xr-x 2 root   root  4096 2007-03-22 20:29 T-DRIVE
drwxr-xr-x 2 root   root  4096 2007-03-25 12:07 usbdisk
```

---

### Post by fanatik on 2007-03-28
OK seems good, so whats the issue? can you paste an example of what you are trying to do?

---

### Post by tsav87 on 2007-03-28
I am trying to open it, but it dosn't show up under the places tab.

---

### Post by tsav87 on 2007-03-28
I get this error now....

I also can't mount my external HD, same error.

---

### Post by tsav87 on 2007-03-28
Hm...I can SEE the EHD, but can't open it...

---

### Post by fanatik on 2007-03-29
it might be permission on the device itsself, can you paste in the output of 

ls -l /dev/sd*

---

### Post by tsav87 on 2007-03-29
It made color in the terminal, took A SS just in case that is relevant

---

### Post by fanatik on 2007-03-29
Thats fine, it just shows colour to tell you the type of file it is...

So for sdb* and sdc* (they are your sd card and external hdisk, right?) it has given you RW permissions through the plugdev group (your earlier id command showed you are a member of plugdev), so thats all ok.

If it's not working, then I have no idea now, sorry. I don't use Feisty, perhaps you should file a bug report? Or at least look for a similar one. It's still in testing so it's possible that is a bug.

James.

---

