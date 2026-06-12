---
title: "login freeze/slowdown"
date: 2008-01-07
forum: General Help
---

### Post by chudder on 2008-01-07
This is a slightly different problem it appears as opposed some other similar ones.  If this problem has been solved, please just direct me.  For the past 2 days I've had problems logging in.  Yesteday as soon as I type my login name after booting it freezes and takes a few whole minutes to display the words and then half the time the password prompt is at regular process speed the other half the same as the login name speed.  
Today it took a while (a few minutes) to display the login screen but the typing was normal speed for both name and password.  
I don't know what is causing this.  I enabled scrolling and double tapping in my touchpad last week but this wasn't a problem.  I also enabled the syndaemon, a process to disable the scrolling and tapping when typing is taking place but again this hasn't interfered with logging in until yesterday and today.  

This the output after typing dmesg in the terminal.

```
[    5.532000] USB Universal Host Controller Interface driver v3.0
[    5.656000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    5.656000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.656000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    5.656000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    5.656000] scsi0 : ata_piix
[    5.716000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[    5.716000] e100: Copyright(c) 1999-2006 Intel Corporation
[    5.732000] ieee1394: Initialized config rom entry `ip1394'
[    5.820000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    5.820000] ata1.00: ATA-7: TOSHIBA MK1234GSX, AH001A, max UDMA/100
[    5.820000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.828000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    5.828000] ata1.00: configured for UDMA/100
[    5.828000] scsi1 : ata_piix
[    6.148000] ata2.00: ATAPI, max UDMA/33
[    6.312000] ata2.00: configured for UDMA/33
[    6.312000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1234GS AH00 PQ: 0 ANSI: 5
[    6.312000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.50 PQ: 0 ANSI: 5
[    6.312000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    6.312000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    6.312000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    6.316000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    6.316000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[    6.316000] usb usb1: configuration #1 chosen from 1 choice
[    6.316000] hub 1-0:1.0: USB hub found
[    6.316000] hub 1-0:1.0: 2 ports detected
[    6.420000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    6.420000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    6.420000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    6.420000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    6.420000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    6.420000] usb usb2: configuration #1 chosen from 1 choice
[    6.420000] hub 2-0:1.0: USB hub found
[    6.420000] hub 2-0:1.0: 2 ports detected
[    6.524000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    6.524000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    6.524000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    6.524000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    6.524000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    6.524000] usb usb3: configuration #1 chosen from 1 choice
[    6.524000] hub 3-0:1.0: USB hub found
[    6.524000] hub 3-0:1.0: 2 ports detected
[    6.628000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    6.628000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    6.628000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    6.628000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    6.628000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    6.628000] usb usb4: configuration #1 chosen from 1 choice
[    6.628000] hub 4-0:1.0: USB hub found
[    6.628000] hub 4-0:1.0: 2 ports detected
[    6.732000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    6.732000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    6.732000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.732000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    6.732000] ehci_hcd 0000:00:1d.7: debug port 1
[    6.732000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    6.732000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdc444000
[    6.736000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.736000] usb usb5: configuration #1 chosen from 1 choice
[    6.736000] hub 5-0:1.0: USB hub found
[    6.736000] hub 5-0:1.0: 8 ports detected
[    6.840000] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 16
[    6.888000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[dc006000-dc0067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.888000] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[    6.916000] e100: eth0: e100_probe: addr 0xdc005000, irq 21, MAC addr 00:A0:D1:43:96:8C
[    6.932000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    6.932000] sda: Write Protect is off
[    6.932000] sda: Mode Sense: 00 3a 00 00
[    6.932000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.932000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    6.932000] sda: Write Protect is off
[    6.932000] sda: Mode Sense: 00 3a 00 00
[    6.932000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.932000]  sda: sda1 sda2 sda3
[    6.980000] sd 0:0:0:0: Attached scsi disk sda
[    6.988000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.988000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    6.992000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.992000] Uniform CD-ROM driver Revision: 3.20
[    6.992000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.200000] Attempting manual resume
[    7.200000] swsusp: Resume From Partition 8:2
[    7.200000] PM: Checking swsusp image.
[    7.200000] PM: Resume from disk failed.
[    7.216000] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[    7.216000] ReiserFS: sda1: using ordered data mode
[    7.236000] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    7.236000] ReiserFS: sda1: checking transaction log (sda1)
[    7.272000] ReiserFS: sda1: Using r5 hash to sort names
[    8.160000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d143968c]
[   19.136000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.140000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.340000] intel_rng: FWH not detected
[   19.392000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.392000] agpgart: Detected an Intel 945GM Chipset.
[   19.396000] agpgart: Detected 7932K stolen memory.
[   19.416000] agpgart: AGP aperture is 256M @ 0xc0000000
[   20.136000] ieee80211_crypt: registered algorithm 'NULL'
[   20.140000] iTCO_vendor_support: vendor-support=0
[   20.144000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   20.168000] Yenta: CardBus bridge found at 0000:07:06.0 [1179:ff10]
[   20.168000] Yenta: Enabling burst memory read transactions
[   20.168000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.168000] Yenta: Routing CardBus interrupts to PCI
[   20.168000] Yenta TI: socket 0000:07:06.0, mfunc 0x01a01b22, devctl 0x66
[   20.400000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   20.400000] Socket status: 30000006
[   20.400000] Yenta: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[   20.400000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   20.400000] cs: IO port probe 0x4000-0x4fff: clean.
[   20.400000] pcmcia: parent PCI bridge Memory window: 0xdc000000 - 0xdc0fffff
[   20.400000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   20.428000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   20.428000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   20.468000] ACPI: PCI Interrupt 0000:07:06.2[A] -> GSI 18 (level, low) -> IRQ 18
[   20.500000] sdhci: Secure Digital Host Controller Interface driver
[   20.500000] sdhci: Copyright(c) Pierre Ossman
[   20.500000] sdhci: SDHCI controller found at 0000:07:06.3 [104c:803c] (rev 0)
[   20.500000] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 18
[   20.500000] mmc0: SDHCI at 0xdc006800 irq 18 DMA
[   20.544000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   20.544000] synaptics: Toshiba Satellite A105 detected, limiting rate to 40pps.
[   20.556000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   20.556000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   20.556000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   20.556000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   20.556000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   20.584000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   20.584000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   20.584000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.956000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   20.956000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   21.044000] cs: IO port probe 0x100-0x3af: clean.
[   21.048000] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x407 0x4d0-0x4d7
[   21.048000] cs: IO port probe 0x820-0x8ff: clean.
[   21.048000] cs: IO port probe 0xc00-0xcf7: clean.
[   21.052000] cs: IO port probe 0xa00-0xaff: clean.
[   21.632000] fuse init (API version 7.8)
[   21.708000] lp: driver loaded but no devices found
[   21.812000] ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 19 (level, low) -> IRQ 19
[   21.976000] Adding 2048276k swap on /dev/disk/by-uuid/d3c0b653-abeb-44ee-888a-a2de55201e32.  Priority:-1 extents:1 across:2048276k
[   22.572000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   23.060000] ieee80211_crypt: registered algorithm 'WEP'
[   24.476000] NET: Registered protocol family 17
[   46.116000] ReiserFS: sda3: found reiserfs format "3.6" with standard journal
[   46.116000] ReiserFS: sda3: using ordered data mode
[   46.120000] ReiserFS: sda3: journal params: device sda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   46.120000] ReiserFS: sda3: checking transaction log (sda3)
[   46.176000] ReiserFS: sda3: Using r5 hash to sort names
[   51.228000] Using specific hotkey driver
[   51.300000] ACPI: AC Adapter [ADP0] (off-line)
[   51.324000] ACPI: ACPI Dock Station Driver 
[   51.420000] input: Power Button (FF) as /class/input/input3
[   51.420000] ACPI: Power Button (FF) [PWRF]
[   51.420000] input: Lid Switch as /class/input/input4
[   51.420000] ACPI: Lid Switch [LID]
[   51.424000] input: Power Button (CM) as /class/input/input5
[   51.424000] ACPI: Power Button (CM) [PWRB]
[   51.648000] ibm_acpi: ec object not found
[   51.704000] ACPI: Battery Slot [BAT0] (battery present)
[   51.724000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   51.724000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   51.776000] pcc_acpi: loading...
[   53.772000] ppdev: user-space parallel port driver
[   54.128000] [drm] Initialized drm 1.1.0 20060810
[   54.240000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   54.240000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   54.468000] apm: BIOS not found.
[   56.348000] Bluetooth: Core ver 2.11
[   56.348000] NET: Registered protocol family 31
[   56.348000] Bluetooth: HCI device and connection manager initialized
[   56.348000] Bluetooth: HCI socket layer initialized
[   56.388000] Bluetooth: L2CAP ver 2.8
[   56.388000] Bluetooth: L2CAP socket layer initialized
[   56.608000] Bluetooth: RFCOMM socket layer initialized
[   56.608000] Bluetooth: RFCOMM TTY layer initialized
[   56.608000] Bluetooth: RFCOMM ver 1.8
[   72.048000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   72.048000] ata1.00: (BMDMA stat 0x24)
[   72.048000] ata1.00: cmd c8/00:90:17:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 73728 in
[   72.048000]          res 51/40:29:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[   72.056000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   72.064000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   72.064000] ata1.00: configured for UDMA/100
[   72.064000] ata1: EH complete
[   78.804000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   78.804000] ata1.00: (BMDMA stat 0x24)
[   78.804000] ata1.00: cmd c8/00:90:17:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 73728 in
[   78.804000]          res 51/01:29:7e:90:dc/00:00:00:00:00/e0 Emask 0x1 (device error)
[   78.812000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   78.820000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   78.820000] ata1.00: configured for UDMA/100
[   78.820000] ata1: EH complete
[   85.560000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   85.560000] ata1.00: (BMDMA stat 0x24)
[   85.560000] ata1.00: cmd c8/00:90:17:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 73728 in
[   85.560000]          res 51/40:29:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[   85.568000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   85.576000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   85.576000] ata1.00: configured for UDMA/100
[   85.576000] ata1: EH complete
[   92.324000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   92.324000] ata1.00: (BMDMA stat 0x24)
[   92.324000] ata1.00: cmd c8/00:90:17:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 73728 in
[   92.324000]          res 51/40:29:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[   92.332000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   92.340000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   92.340000] ata1.00: configured for UDMA/100
[   92.340000] ata1: EH complete
[   99.092000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   99.092000] ata1.00: (BMDMA stat 0x24)
[   99.092000] ata1.00: cmd c8/00:90:17:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 73728 in
[   99.092000]          res 51/40:29:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[   99.100000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   99.108000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   99.108000] ata1.00: configured for UDMA/100
[   99.108000] ata1: EH complete
[  105.848000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  105.848000] ata1.00: (BMDMA stat 0x24)
[  105.848000] ata1.00: cmd c8/00:90:17:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 73728 in
[  105.848000]          res 51/40:29:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  105.856000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  105.864000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  105.864000] ata1.00: configured for UDMA/100
[  105.864000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  105.864000] sda: Current [descriptor]: sense key: Medium Error
[  105.864000]     Additional sense: Unrecovered read error - auto reallocate failed
[  105.864000] Descriptor sense data with sense descriptors (in hex):
[  105.864000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  105.864000]         00 dc 90 7e 
[  105.864000] end_request: I/O error, dev sda, sector 14454910
[  105.864000] ata1: EH complete
[  105.868000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  105.868000] sda: Write Protect is off
[  105.868000] sda: Mode Sense: 00 3a 00 00
[  105.872000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  105.872000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  105.872000] sda: Write Protect is off
[  105.872000] sda: Mode Sense: 00 3a 00 00
[  105.872000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  112.824000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  112.824000] ata1.00: (BMDMA stat 0x24)
[  112.824000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  112.824000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  112.832000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  112.840000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  112.840000] ata1.00: configured for UDMA/100
[  112.840000] ata1: EH complete
[  119.600000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  119.600000] ata1.00: (BMDMA stat 0x24)
[  119.600000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  119.600000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  119.608000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  119.616000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  119.616000] ata1.00: configured for UDMA/100
[  119.616000] ata1: EH complete
[  126.368000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  126.368000] ata1.00: (BMDMA stat 0x24)
[  126.368000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  126.368000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  126.376000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  126.384000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  126.384000] ata1.00: configured for UDMA/100
[  126.384000] ata1: EH complete
[  133.124000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  133.124000] ata1.00: (BMDMA stat 0x24)
[  133.124000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  133.124000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  133.132000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  133.140000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  133.140000] ata1.00: configured for UDMA/100
[  133.140000] ata1: EH complete
[  139.880000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  139.880000] ata1.00: (BMDMA stat 0x24)
[  139.880000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  139.880000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  139.888000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  139.896000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  139.896000] ata1.00: configured for UDMA/100
[  139.896000] ata1: EH complete
[  146.644000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  146.644000] ata1.00: (BMDMA stat 0x24)
[  146.644000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  146.644000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  146.652000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  146.660000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  146.660000] ata1.00: configured for UDMA/100
[  146.660000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  146.660000] sda: Current [descriptor]: sense key: Medium Error
[  146.660000]     Additional sense: Unrecovered read error - auto reallocate failed
[  146.660000] Descriptor sense data with sense descriptors (in hex):
[  146.660000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  146.660000]         00 dc 90 7e 
[  146.660000] end_request: I/O error, dev sda, sector 14454910
[  146.660000] Buffer I/O error on device sda1, logical block 1806855
[  146.660000] ata1: EH complete
[  146.664000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  146.680000] sda: Write Protect is off
[  146.680000] sda: Mode Sense: 00 3a 00 00
[  146.696000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  146.700000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  146.700000] sda: Write Protect is off
[  146.700000] sda: Mode Sense: 00 3a 00 00
[  146.700000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  153.588000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  153.588000] ata1.00: (BMDMA stat 0x24)
[  153.588000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  153.588000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  153.596000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  153.604000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  153.604000] ata1.00: configured for UDMA/100
[  153.604000] ata1: EH complete
[  160.368000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  160.368000] ata1.00: (BMDMA stat 0x24)
[  160.368000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  160.368000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  160.376000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  160.384000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  160.384000] ata1.00: configured for UDMA/100
[  160.384000] ata1: EH complete
[  167.120000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  167.120000] ata1.00: (BMDMA stat 0x24)
[  167.120000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  167.120000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  167.128000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  167.136000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  167.136000] ata1.00: configured for UDMA/100
[  167.136000] ata1: EH complete
[  173.876000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  173.876000] ata1.00: (BMDMA stat 0x24)
[  173.876000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  173.876000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  173.884000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  173.892000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  173.892000] ata1.00: configured for UDMA/100
[  173.892000] ata1: EH complete
[  180.632000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  180.632000] ata1.00: (BMDMA stat 0x24)
[  180.632000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  180.632000]          res 51/40:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x9 (media error)
[  180.640000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  180.648000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  180.648000] ata1.00: configured for UDMA/100
[  180.648000] ata1: EH complete
[  187.388000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  187.388000] ata1.00: (BMDMA stat 0x24)
[  187.388000] ata1.00: cmd c8/00:08:77:90:dc/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  187.388000]          res 51/01:01:7e:90:dc/00:00:00:00:00/e0 Emask 0x1 (device error)
[  187.396000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  187.404000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  187.404000] ata1.00: configured for UDMA/100
[  187.404000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  187.404000] sda: Current [descriptor]: sense key: Medium Error
[  187.404000]     Additional sense: Address mark not found for data field
[  187.404000] Descriptor sense data with sense descriptors (in hex):
[  187.404000]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  187.404000]         00 dc 90 7e 
[  187.404000] end_request: I/O error, dev sda, sector 14454910
[  187.404000] Buffer I/O error on device sda1, logical block 1806855
[  187.404000] ata1: EH complete
[  187.408000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  187.408000] sda: Write Protect is off
[  187.408000] sda: Mode Sense: 00 3a 00 00
[  187.408000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  187.408000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  187.408000] sda: Write Protect is off
[  187.408000] sda: Mode Sense: 00 3a 00 00
[  187.408000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  187.716000] NET: Registered protocol family 10
[  187.716000] lo: Disabled Privacy Extensions
[  187.716000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  187.716000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  303.940000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  304.452000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  314.672000] eth1: no IPv6 routers present

```

Any help would be appreciated, thank you.

Chudder

---

### Post by chudder on 2008-01-07
now I had to wait a long time to go from the login screen to the desktop, the login screen was normal speed.  It seems to be changing.  The wait is always a few minutes which is unusual.  

Thanx

---

### Post by chudder on 2008-01-07
I think I fixed it!  I remembered that a few days ago I installed every and all lm-sensors related piece of software and I then uninstalled all of them and it seems to be working fine.  I'll keep this posted as new occurrences happen.

---

