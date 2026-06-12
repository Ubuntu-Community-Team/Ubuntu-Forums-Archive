---
title: "Boot hang @ Cd-rom driver"
date: 2007-05-30
forum: General Help
---

### Post by Culito on 2007-05-30
Hey folks, wondered if you had any ideas on this.
About 90% of the time, my system boots fine.  The other 10%, it locks up on boot at this spot:

[   21.068862] Uniform CD-ROM driver Revision: 3.20

Good thing my boot splash doesn't work, but that's for another post.  Here's my entire dmesg if it helps.

[   13.974916] CPU: L2 Cache: 64K (64 bytes/line)
[   13.974968] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[   13.974997] Compat vDSO mapped to ffffe000.
[   13.975060] Remapping vsyscall page to ffffe000
[   13.975131] Checking 'hlt' instruction... OK.
[   13.990158] SMP alternatives: switching to UP code
[   13.990960] Freeing SMP alternatives: 11k freed
[   13.991697] Early unpacking initramfs... done
[   14.712428] CPU0: AMD Duron(tm) Processor stepping 01
[   14.712551] SMP motherboard not detected.
[   14.712603] Local APIC not detected. Using dummy APIC emulation.
[   14.712772] Brought up 1 CPUs
[   14.713507] Booting paravirtualized kernel on bare hardware
[   14.713765] Time: 23:37:47  Date: 04/30/107
[   14.713969] NET: Registered protocol family 16
[   14.714355] EISA bus registered
[   14.716938] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[   14.716994] PCI: Using configuration type 1
[   14.717043] Setting up standard PCI resources
[   14.719365] ACPI: Interpreter disabled.
[   14.719440] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.719513] pnp: PnP ACPI: disabled
[   14.719568] PnPBIOS: Scanning system for PnP BIOS support...
[   14.719724] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7d60
[   14.719782] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6b24, dseg 0xf0000
[   14.721386] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[   14.721613] PCI: Probing PCI hardware
[   14.721677] PCI: Probing PCI hardware (bus 00)
[   14.722474] Boot video device is 0000:01:00.0
[   14.723477] PCI: Using IRQ router SIS [1039/0018] at 0000:00:01.0
[   14.725425] NET: Registered protocol family 8
[   14.725477] NET: Registered protocol family 20
[   14.726576] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[   14.726649] PCI: Bridge: 0000:00:02.0
[   14.726698]   IO window: b000-bfff
[   14.726752]   MEM window: cfe00000-cfefffff
[   14.726804]   PREFETCH window: bfc00000-cfcfffff
[   14.726874] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   14.726947] NET: Registered protocol family 2
[   14.754095] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   14.754390] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   14.754827] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   14.755087] TCP: Hash tables configured (established 8192 bind 4096)
[   14.755143] TCP reno registered
[   14.766219] checking if image is initramfs... it is
[   16.128043] Freeing initrd memory: 6779k freed
[   16.129247] audit: initializing netlink socket (disabled)
[   16.129350] audit(1180568269.440:1): initialized
[   16.129763] VFS: Disk quotas dquot_6.5.1
[   16.129864] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.130067] io scheduler noop registered
[   16.130148] io scheduler anticipatory registered
[   16.130229] io scheduler deadline registered
[   16.130327] io scheduler cfq registered (default)
[   16.131049] isapnp: Scanning for PnP cards...
[   16.484617] isapnp: No Plug & Play device found
[   16.657967] Real Time Clock Driver v1.12ac
[   16.658206] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.658490] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.662178] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.663431] mice: PS/2 mouse device common for all mice
[   16.664942] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.665590] input: Macintosh mouse button emulation as /class/input/input0
[   16.665748] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   16.665809] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   16.666388] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   16.666878] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.666939] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.667315] EISA: Probing bus 0 at eisa.0
[   16.667418] EISA: Detected 0 cards.
[   16.667680] TCP cubic registered
[   16.667739] NET: Registered protocol family 1
[   16.667842] Using IPI No-Shortcut mode
[   16.667937]   Magic number: 7:271:657
[   16.669402] Time: tsc clocksource has been installed.
[   16.669782] Freeing unused kernel memory: 328k freed
[   16.691017] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.304045] Capability LSM initialized
[   17.474965] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   19.301927] SCSI subsystem initialized
[   19.314534] libata version 2.20 loaded.
[   19.323656] pata_sis 0000:00:00.1: version 0.5.1
[   19.323914] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ff00 irq 14
[   19.324083] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ff08 irq 15
[   19.324172] scsi0 : pata_sis
[   19.370626] usbcore: registered new interface driver usbfs
[   19.370757] usbcore: registered new interface driver hub
[   19.370871] usbcore: registered new device driver usb
[   19.373370] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.493171] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   19.493258] ata1.00: ATA-4: QUANTUM FIREBALL CR4.3A, A5U.1200, max UDMA/66
[   19.493314] ata1.00: 8418816 sectors, multi 16: LBA 
[   19.494465] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   19.494530] ata1.01: ATA-5: WDC WD400BB-00GFA0, 09.01B09, max UDMA/100
[   19.494585] ata1.01: 78165360 sectors, multi 16: LBA 
[   19.501098] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   19.501172] ata1.00: configured for UDMA/66
[   19.510187] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   19.510277] ata1.01: configured for UDMA/100
[   19.510366] scsi1 : pata_sis
[   19.555963] sis900.c: v1.08.10 Apr. 2 2006
[   19.766485] Floppy drive(s): fd0 is 1.44M
[   19.786028] FDC 0 is a post-1991 82077
[   19.985070] ata2.00: ATAPI, max UDMA/33
[   20.149034] ata2.00: configured for UDMA/33
[   20.149520] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM FIREBALL A5U. PQ: 0 ANSI: 5
[   20.150882] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400BB-00GF 09.0 PQ: 0 ANSI: 5
[   20.153284] scsi 1:0:0:0: CD-ROM            DVD+R/RW DX082D           11SB PQ: 0 ANSI: 5
[   20.162587] PCI: setting IRQ 11 as level-triggered
[   20.162601] PCI: Found IRQ 11 for device 0000:00:01.2
[   20.162679] PCI: Sharing IRQ 11 with 0000:00:01.3
[   20.162766] ohci_hcd 0000:00:01.2: OHCI Host Controller
[   20.163292] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[   20.163411] ohci_hcd 0000:00:01.2: irq 11, io mem 0xcfffa000
[   20.197692] SCSI device sda: 8418816 512-byte hdwr sectors (4310 MB)
[   20.197803] sda: Write Protect is off
[   20.197855] sda: Mode Sense: 00 3a 00 00
[   20.197892] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.198656] SCSI device sda: 8418816 512-byte hdwr sectors (4310 MB)
[   20.198728] sda: Write Protect is off
[   20.198778] sda: Mode Sense: 00 3a 00 00
[   20.198810] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.198881]  sda:<3>ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   20.206928] ata1.00: (BMDMA stat 0x64)
[   20.206989] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[   20.206993]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   20.207148] ata1: soft resetting port
[   20.219453] usb usb1: configuration #1 chosen from 1 choice
[   20.219593] hub 1-0:1.0: USB hub found
[   20.219673] hub 1-0:1.0: 3 ports detected
[   20.320922] PCI: Found IRQ 11 for device 0000:00:01.3
[   20.321008] PCI: Sharing IRQ 11 with 0000:00:01.2
[   20.321097] ohci_hcd 0000:00:01.3: OHCI Host Controller
[   20.321210] ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
[   20.321308] ohci_hcd 0000:00:01.3: irq 11, io mem 0xcfffb000
[   20.369854] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   20.378717] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   20.379341] usb usb2: configuration #1 chosen from 1 choice
[   20.379470] hub 2-0:1.0: USB hub found
[   20.379550] hub 2-0:1.0: 3 ports detected
[   20.384943] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   20.385030] ata1.00: configured for UDMA/66
[   20.393806] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   20.393871] ata1.01: configured for UDMA/100
[   20.393969] ata1: EH complete
[   20.397133] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   20.397188] ata1.00: (BMDMA stat 0x64)
[   20.397246] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[   20.397250]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   20.397402] ata1: soft resetting port
[   20.481221] PCI: setting IRQ 10 as level-triggered
[   20.481233] PCI: Found IRQ 10 for device 0000:00:01.1
[   20.481316] PCI: Sharing IRQ 10 with 0000:00:0b.0
[   20.482218] 0000:00:01.1: VIA 6103 PHY transceiver found at address 1.
[   20.490609] 0000:00:01.1: Using transceiver found at address 1 as default
[   20.491394] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 10, 00:07:95:37:8a:1b.
[   20.561928] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   20.568936] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   20.576941] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   20.577028] ata1.00: configured for UDMA/66
[   20.585762] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   20.585828] ata1.01: configured for UDMA/100
[   20.585926] ata1: EH complete
[   20.587469] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   20.587524] ata1.00: (BMDMA stat 0x64)
[   20.587581] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[   20.587585]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   20.587737] ata1: soft resetting port
[   20.749773] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   20.756766] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   20.764737] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   20.764804] ata1.00: configured for UDMA/66
[   20.773699] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   20.773763] ata1.01: configured for UDMA/100
[   20.773853] ata1: EH complete
[   20.777814] ata1.00: limiting speed to UDMA/44:PIO4
[   20.777870] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   20.777924] ata1.00: (BMDMA stat 0x64)
[   20.777981] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[   20.777985]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   20.778129] ata1: soft resetting port
[   20.941726] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   20.948694] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   20.956722] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   20.956789] ata1.00: configured for UDMA/44
[   20.965648] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   20.965711] ata1.01: configured for UDMA/100
[   20.965807] ata1: EH complete
[   20.968271]  sda1
[   20.968386] SCSI device sda: 8418816 512-byte hdwr sectors (4310 MB)
[   20.968669] sd 0:0:0:0: Attached scsi disk sda
[   20.970041] sda: Write Protect is off
[   20.970107] sda: Mode Sense: 00 3a 00 00
[   20.970204] SCSI device sdb: 78165360 512-byte hdwr sectors (40021 MB)
[   20.970286] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.970379] sdb: Write Protect is off
[   20.970428] sdb: Mode Sense: 00 3a 00 00
[   20.970478] SCSI device sda: 8418816 512-byte hdwr sectors (4310 MB)
[   20.970544] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.970760] sda: Write Protect is off
[   20.970810] sda: Mode Sense: 00 3a 00 00
[   20.970854] SCSI device sdb: 78165360 512-byte hdwr sectors (40021 MB)
[   20.970928] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.971012] sdb: Write Protect is off
[   20.971060] sdb: Mode Sense: 00 3a 00 00
[   20.971107] SCSI device sdb: 78165360 512-byte hdwr sectors (40021 MB)
[   20.971173] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.971242]  sdb:<5>sdb: Write Protect is off
[   20.971486] sdb: Mode Sense: 00 3a 00 00
[   20.990335]  sdb1 sdb2 <<5>SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.034474]  sdb5 >
[   21.034922] sd 0:0:1:0: Attached scsi disk sdb
[   21.048397] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.048536] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   21.048638] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   21.068775] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
**[   21.068862] Uniform CD-ROM driver Revision: 3.20**
[   21.069115] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.584620] Attempting manual resume
[   21.584679] swsusp: Resume From Partition 8:21
[   21.584684] PM: Checking swsusp image.
[   21.585104] PM: Resume from disk failed.
[   21.658946] kjournald starting.  Commit interval 5 seconds
[   21.659050] EXT3-fs: mounted filesystem with ordered data mode.
[   21.875188] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   21.875263] ata1.01: (BMDMA stat 0x64)
[   21.875323] ata1.01: cmd c8/00:20:ef:82:ab/00:00:00:00:00/f0 tag 0 cdb 0x0 data 16384 in
[   21.875327]          res 51/84:00:0e:83:ab/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
[   21.875482] ata1: soft resetting port
[   22.037446] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   22.044473] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   22.052436] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   22.052502] ata1.00: configured for UDMA/44
[   22.061412] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   22.061476] ata1.01: configured for UDMA/100
[   22.061543] ata1: EH complete
[   22.066738] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   22.066795] ata1.01: (BMDMA stat 0x64)
[   22.066852] ata1.01: cmd c8/00:20:ef:82:ab/00:00:00:00:00/f0 tag 0 cdb 0x0 data 16384 in
[   22.066856]          res 51/84:00:0e:83:ab/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
[   22.066998] ata1: soft resetting port
[   22.229345] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   22.236388] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   22.244385] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   22.244450] ata1.00: configured for UDMA/44
[   22.253363] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   22.253427] ata1.01: configured for UDMA/100
[   22.253482] ata1: EH complete
[   22.253611] SCSI device sda: 8418816 512-byte hdwr sectors (4310 MB)
[   22.258361] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   22.258416] ata1.01: (BMDMA stat 0x64)
[   22.258471] ata1.01: cmd c8/00:20:ef:82:ab/00:00:00:00:00/f0 tag 0 cdb 0x0 data 16384 in
[   22.258475]          res 51/84:00:0e:83:ab/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
[   22.259114] ata1: soft resetting port
[   22.421293] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   22.428381] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   22.436349] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   22.436414] ata1.00: configured for UDMA/44
[   22.445318] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   22.445382] ata1.01: configured for UDMA/100
[   22.445437] ata1: EH complete
[   22.445568] sda: Write Protect is off
[   22.445618] sda: Mode Sense: 00 3a 00 00
[   22.449956] ata1.01: limiting speed to UDMA/66:PIO4
[   22.450009] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   22.450064] ata1.01: (BMDMA stat 0x64)
[   22.450118] ata1.01: cmd c8/00:20:ef:82:ab/00:00:00:00:00/f0 tag 0 cdb 0x0 data 16384 in
[   22.450123]          res 51/84:00:0e:83:ab/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
[   22.450264] ata1: soft resetting port
[   22.613280] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   22.620312] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   22.628294] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   22.628359] ata1.00: configured for UDMA/44
[   22.637183] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   22.637247] ata1.01: configured for UDMA/66
[   22.637303] ata1: EH complete
[   22.641581] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   22.641636] ata1.01: (BMDMA stat 0x64)
[   22.641691] ata1.01: cmd c8/00:20:ef:82:ab/00:00:00:00:00/f0 tag 0 cdb 0x0 data 16384 in
[   22.641695]          res 51/84:00:0e:83:ab/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
[   22.641835] ata1: soft resetting port
[   22.805167] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   22.812254] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   22.820275] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   22.820339] ata1.00: configured for UDMA/44
[   22.829158] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   22.829222] ata1.01: configured for UDMA/66
[   22.829277] ata1: EH complete
[   22.829393] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.833202] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   22.833257] ata1.01: (BMDMA stat 0x64)
[   22.833312] ata1.01: cmd c8/00:20:ef:82:ab/00:00:00:00:00/f0 tag 0 cdb 0x0 data 16384 in
[   22.833316]          res 51/84:00:0e:83:ab/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
[   22.833456] ata1: soft resetting port
[   22.997117] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   23.004236] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   23.012199] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   23.012264] ata1.00: configured for UDMA/44
[   23.021100] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   23.021164] ata1.01: configured for UDMA/66
[   23.021227] sd 0:0:1:0: SCSI error: return code = 0x08000002
[   23.021282] sdb: Current [descriptor]: sense key: Aborted Command
[   23.021398]     Additional sense: Scsi parity error
[   23.021528] Descriptor sense data with sense descriptors (in hex):
[   23.021612]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   23.022188]         00 ab 83 0e 
[   23.022390] end_request: I/O error, dev sdb, sector 11240175
[   23.022467] ata1: EH complete
[   23.032944] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   23.033002] ata1.01: (BMDMA stat 0x64)
[   23.033058] ata1.01: cmd c8/00:08:ef:82:ab/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[   23.033063]          res 51/84:00:f6:82:ab/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
[   23.033206] ata1: soft resetting port
[   23.197061] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   23.204194] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   23.212152] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   23.212216] ata1.00: configured for UDMA/44
[   23.221045] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   23.221109] ata1.01: configured for UDMA/66
[   23.221165] ata1: EH complete
[   23.224487] ata1.01: limiting speed to UDMA/33:PIO4
[   23.224540] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   23.224594] ata1.01: (BMDMA stat 0x64)
[   23.224649] ata1.01: cmd c8/00:08:ef:82:ab/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[   23.224653]          res 51/84:00:f6:82:ab/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
[   23.224791] ata1: soft resetting port
[   23.389010] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   23.396114] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   23.404106] ata1.00: ata_hpa_resize 1: sectors = 8418816, hpa_sectors = 8418816
[   23.404170] ata1.00: configured for UDMA/44
[   23.413043] ata1.01: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   23.413108] ata1.01: configured for UDMA/33
[   23.413162] ata1: EH complete
[   23.415986] SCSI device sdb: 78165360 512-byte hdwr sectors (40021 MB)
[   23.416549] sdb: Write Protect is off
[   23.416611] sdb: Mode Sense: 00 3a 00 00
[   23.430876] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.432461] SCSI device sda: 8418816 512-byte hdwr sectors (4310 MB)
[   23.432677] sda: Write Protect is off
[   23.432729] sda: Mode Sense: 00 3a 00 00
[   23.433071] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.444680] SCSI device sdb: 78165360 512-byte hdwr sectors (40021 MB)
[   23.445463] sdb: Write Protect is off
[   23.445514] sdb: Mode Sense: 00 3a 00 00
[   23.445794] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.874658] NET: Registered protocol family 17
[   40.120371] eth0: Media Link On 100mbps full-duplex 
[   41.706861] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.712376] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.989631] Linux agpgart interface v0.102 (c) Dave Jones
[   42.606924] agpgart: Detected SiS 730 chipset
[   42.616116] agpgart: AGP aperture is 64M @ 0xd0000000
[   43.293326] input: PC Speaker as /class/input/input2
[   43.389085] parport: PnPBIOS parport detected.
[   43.389213] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   43.771700] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   44.066608] PCI: Found IRQ 10 for device 0000:00:0b.0
[   44.066691] PCI: Sharing IRQ 10 with 0000:00:01.1
[   44.662537] lp0: using parport0 (interrupt-driven).
[   44.708396] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   44.817157] fuse init (API version 7.8)
[   44.948459] Adding 698788k swap on /dev/disk/by-uuid/74b960c3-faba-4550-a85b-742fe7a4c60c.  Priority:-1 extents:1 across:698788k
[   45.183249] EXT3 FS on sdb1, internal journal
[   45.579635] NET: Registered protocol family 10
[   45.579945] lo: Disabled Privacy Extensions
[   45.799847] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   49.122294] powernow_k7: Unknown symbol acpi_processor_notify_smm
[   49.122473] powernow_k7: Unknown symbol acpi_processor_unregister_performance
[   49.122692] powernow_k7: Unknown symbol acpi_processor_register_performance
[   49.186464] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   49.186643] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   49.186888] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   49.187030] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   53.794801] ppdev: user-space parallel port driver
[   55.097629] [drm] Initialized drm 1.1.0 20060810
[   55.137504] [drm] Initialized sis 1.2.1 20060704 on minor 0
[   55.139892] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   55.140694] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   55.141186] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   56.866791] Bluetooth: Core ver 2.11
[   56.866987] NET: Registered protocol family 31
[   56.866993] Bluetooth: HCI device and connection manager initialized
[   56.867005] Bluetooth: HCI socket layer initialized
[   56.930034] Bluetooth: L2CAP ver 2.8
[   56.930050] Bluetooth: L2CAP socket layer initialized
[   57.124595] Bluetooth: RFCOMM socket layer initialized
[   57.124647] Bluetooth: RFCOMM TTY layer initialized
[   57.124653] Bluetooth: RFCOMM ver 1.8
[   67.381306] eth0: no IPv6 routers present
[  936.047923] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  936.048211] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[  936.048435] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[ 6013.330047] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 6013.330354] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[ 6013.330590] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
culito@HAL9000:~$

---

### Post by Culito on 2007-06-05
Had to ctrl+alt+del about a dozen times this morning to get it to finally start up.

---

### Post by elninja on 2007-11-05
I have the same problems. Any chance you found a solution?

---

### Post by Culito on 2007-11-27
The upgrade to Edgy seems to have fixed the problem.

---

