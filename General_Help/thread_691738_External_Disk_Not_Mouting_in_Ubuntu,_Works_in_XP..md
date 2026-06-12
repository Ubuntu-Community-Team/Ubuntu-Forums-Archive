---
title: "External Disk Not Mouting in Ubuntu, Works in XP."
date: 2008-02-08
forum: General Help
---

### Post by trevorgasm on 2008-02-08
For some reason, my my external hdd no longer gets mounted when i turn it on. It used to work, and still does in XP but not on the Ubuntu side of this laptop (HP Dv8000t). I have googled, and found nothing that has helped.

---

### Post by lank23 on 2008-02-08
check your settings under "system -> preferences -> removable drives and media" If you have the first three checks  on the storage tab it should work fine.

lank23

---

### Post by trevorgasm on 2008-02-08
all three are checked, no luck.

---

### Post by lank23 on 2008-02-08
what is your dmesg when you plug in the drive?

---

### Post by confused57 on 2008-02-08
Maybe something in this thread will help:
[http://ubuntuforums.org/showthread.php?t=688635](http://ubuntuforums.org/showthread.php?t=688635)

---

### Post by trevorgasm on 2008-02-09
hmm, checked that link, tried anything i thought would apply, no dice... thank you for the suggestion though.

---

### Post by lank23 on 2008-02-09
can you mount the drive from the terminal?
what format is the drive?

---

### Post by trevorgasm on 2008-02-09
Its NTFS. And if I "sudo fdisk -l" it does not show up. 
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5b6a5b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       12030    65914695   83  Linux
/dev/sda3           12031       12161     1052257+  82  Linux swap / Solaris

```

---

### Post by lank23 on 2008-02-09
what do you get in dmesg right after you plug it in.  If it is something about supper block it will not mount.

lank23

---

### Post by trevorgasm on 2008-02-09
Hmm, don't see anything about super block... do see other errors.
```
[   13.300000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   13.300000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.300000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.300000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.300000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001820
[   13.300000] usb usb2: configuration #1 chosen from 1 choice
[   13.300000] hub 2-0:1.0: USB hub found
[   13.300000] hub 2-0:1.0: 2 ports detected
[   13.404000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   13.404000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.404000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.404000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.404000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[   13.404000] usb usb3: configuration #1 chosen from 1 choice
[   13.404000] hub 3-0:1.0: USB hub found
[   13.404000] hub 3-0:1.0: 2 ports detected
[   13.500000] Clocksource tsc unstable (delta = -85822170 ns)
[   13.508000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   13.508000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   13.508000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   13.508000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   13.508000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[   13.508000] usb usb4: configuration #1 chosen from 1 choice
[   13.508000] hub 4-0:1.0: USB hub found
[   13.508000] hub 4-0:1.0: 2 ports detected
[   13.540000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   13.612000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   13.612000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.612000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.612000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   13.612000] ehci_hcd 0000:00:1d.7: debug port 1
[   13.612000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.612000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd2404000
[   13.656000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.656000] usb usb5: configuration #1 chosen from 1 choice
[   13.656000] hub 5-0:1.0: USB hub found
[   13.656000] hub 5-0:1.0: 8 ports detected
[   13.760000] ahci 0000:00:1f.2: version 2.2
[   13.760000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   14.068000] usb 1-1: device not accepting address 2, error -71
[   14.552000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   14.732000] usb 1-1: configuration #1 chosen from 1 choice
[   14.752000] usbcore: registered new interface driver hiddev
[   14.768000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[   14.768000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   14.768000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   14.768000] scsi0 : ahci
[   14.768000] scsi1 : ahci
[   14.768000] scsi2 : ahci
[   14.768000] scsi3 : ahci
[   14.768000] ata1: SATA max UDMA/133 cmd 0xf885c500 ctl 0x00000000 bmdma 0x00000000 irq 20
[   14.768000] ata2: SATA max UDMA/133 cmd 0xf885c580 ctl 0x00000000 bmdma 0x00000000 irq 20
[   14.768000] ata3: SATA max UDMA/133 cmd 0xf885c600 ctl 0x00000000 bmdma 0x00000000 irq 20
[   14.768000] ata4: SATA max UDMA/133 cmd 0xf885c680 ctl 0x00000000 bmdma 0x00000000 irq 20
[   14.768000] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input2
[   14.768000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1
[   14.768000] usbcore: registered new interface driver usbhid
[   14.768000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   15.252000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   15.252000] ata1.00: ATA-7: FUJITSU MHV2100BH, 892C, max UDMA/100
[   15.252000] ata1.00: 195371568 sectors, multi 16: LBA48 
[   15.252000] ata1.00: configured for UDMA/100
[   15.564000] ata2: SATA link down (SStatus 0 SControl 0)
[   15.876000] ata3: SATA link down (SStatus 0 SControl 0)
[   16.188000] ata4: SATA link down (SStatus 0 SControl 0)
[   16.188000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2100B 892C PQ: 0 ANSI: 5
[   16.188000] ACPI: PCI Interrupt 0000:08:06.1[B] -> GSI 19 (level, low) -> IRQ 20
[   16.236000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[d2007000-d20077ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   16.236000] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   16.244000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   16.244000] sd 0:0:0:0: [sda] Write Protect is off
[   16.244000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.244000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.244000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   16.244000] sd 0:0:0:0: [sda] Write Protect is off
[   16.244000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.244000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.244000]  sda:<6>e100: eth0: e100_probe: addr 0xd2006000, irq 21, MAC addr 00:16:D4:30:82:47
[   16.264000] ata_piix 0000:00:1f.1: version 2.11
[   16.264000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 20
[   16.264000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   16.264000] scsi4 : ata_piix
[   16.264000] scsi5 : ata_piix
[   16.264000] ata5: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011880 irq 14
[   16.264000] ata6: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011888 irq 15
[   16.324000]  sda1 sda2 sda3
[   16.348000] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.356000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   16.588000] ata5.00: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HQ04, max MWDMA2
[   16.640000] Attempting manual resume
[   16.640000] swsusp: Resume From Partition 8:3
[   16.640000] PM: Checking swsusp image.
[   16.644000] PM: Resume from disk failed.
[   16.660000] EXT3-fs: INFO: recovery required on readonly filesystem.
[   16.660000] EXT3-fs: write access will be enabled during recovery.
[   16.760000] ata5.00: configured for MWDMA2
[   16.760000] ata6: port disabled. ignoring.
[   16.764000] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N HQ04 PQ: 0 ANSI: 5
[   16.764000] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   16.796000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   16.796000] Uniform CD-ROM driver Revision: 3.20
[   16.796000] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   17.508000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[663f0200636b407e]
[   21.088000] kjournald starting.  Commit interval 5 seconds
[   21.088000] EXT3-fs: sda2: orphan cleanup on readonly fs
[   21.088000] ext3_orphan_cleanup: deleting unreferenced inode 1197379
[   21.556000] ext3_orphan_cleanup: deleting unreferenced inode 1163285
[   21.564000] EXT3-fs: sda2: 2 orphan inodes deleted
[   21.564000] EXT3-fs: recovery complete.
[   21.568000] EXT3-fs: mounted filesystem with ordered data mode.
[   28.928000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.928000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.120000] Linux agpgart interface v0.102 (c) Dave Jones
[   29.340000] intel_rng: FWH not detected
[   29.788000] nvidia: module license 'NVIDIA' taints kernel.
[   30.076000] ieee80211_crypt: registered algorithm 'NULL'
[   30.084000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   30.084000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   30.092000] iTCO_vendor_support: vendor-support=0
[   30.104000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   30.104000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   30.104000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.160000] Yenta: CardBus bridge found at 0000:08:06.0 [103c:30a5]
[   30.160000] Yenta: Enabling burst memory read transactions
[   30.160000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   30.160000] Yenta: Routing CardBus interrupts to ISA
[   30.160000] Yenta TI: socket 0000:08:06.0, mfunc 0x01aa1b22, devctl 0x64
[   30.216000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   30.216000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   30.392000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   30.392000] Socket status: 30000006
[   30.392000] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   30.392000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   30.392000] cs: IO port probe 0x3000-0x3fff: clean.
[   30.392000] pcmcia: parent PCI bridge Memory window: 0xd2000000 - 0xd20fffff
[   30.392000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   30.396000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   30.396000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   30.396000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.396000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   30.396000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   30.412000] sdhci: Secure Digital Host Controller Interface driver
[   30.412000] sdhci: Copyright(c) Pierre Ossman
[   30.480000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   30.480000] ACPI: PCI Interrupt 0000:08:06.2[C] -> GSI 22 (level, low) -> IRQ 22
[   30.484000] sdhci: SDHCI controller found at 0000:08:06.3 [104c:803c] (rev 0)
[   30.484000] ACPI: PCI Interrupt 0000:08:06.3[D] -> GSI 20 (level, low) -> IRQ 21
[   30.484000] mmc0: SDHCI at 0xd2007800 irq 21 PIO
[   30.720000] cs: IO port probe 0x100-0x3af: clean.
[   30.720000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   30.724000] cs: IO port probe 0x820-0x8ff: clean.
[   30.724000] cs: IO port probe 0xc00-0xcf7: clean.
[   30.724000] cs: IO port probe 0xa00-0xaff: clean.
[   30.868000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   30.868000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   30.912000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   30.980000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   31.404000] lp: driver loaded but no devices found
[   31.488000] Adding 979956k swap on /dev/sda3.  Priority:-1 extents:1 across:979956k
[   31.808000] EXT3 FS on sda2, internal journal
[   32.300000] ipw3945: Radio Frequency Kill Switch is On:
[   32.300000] Kill switch must be turned off for wireless networking to work.
[   33.208000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   33.224000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   33.240000] No dock devices found.
[   33.324000] ACPI: Battery Slot [BAT1] (battery present)
[   33.468000] ACPI: AC Adapter [ACAD] (on-line)
[   33.488000] input: Power Button (FF) as /class/input/input4
[   33.488000] ACPI: Power Button (FF) [PWRF]
[   33.488000] ACPI Error (evxfevnt-0186): Could not enable SleepButton event [20070126]
[   33.488000] ACPI Warning (evxface-0145): Could not enable fixed event 3 [20070126]
[   33.488000] input: Lid Switch as /class/input/input5
[   33.488000] ACPI: Lid Switch [LID]
[   33.488000] input: Power Button (CM) as /class/input/input6
[   33.488000] ACPI: Power Button (CM) [PWRB]
[   34.884000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   37.700000] ppdev: user-space parallel port driver
[   39.384000] apm: BIOS not found.
[   39.776000] Bluetooth: Core ver 2.11
[   39.776000] NET: Registered protocol family 31
[   39.776000] Bluetooth: HCI device and connection manager initialized
[   39.776000] Bluetooth: HCI socket layer initialized
[   39.800000] Bluetooth: L2CAP ver 2.8
[   39.800000] Bluetooth: L2CAP socket layer initialized
[   39.932000] Bluetooth: RFCOMM socket layer initialized
[   39.932000] Bluetooth: RFCOMM TTY layer initialized
[   39.932000] Bluetooth: RFCOMM ver 1.8
[   44.144000] NET: Registered protocol family 17
[  100.796000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[  100.928000] usb 5-6: configuration #1 chosen from 1 choice
[  101.032000] usbcore: registered new interface driver libusual
[  101.072000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  101.072000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  101.076000] Initializing USB Mass Storage driver...
[  101.076000] scsi6 : SCSI emulation for USB Mass Storage devices
[  101.076000] usb-storage: device found at 3
[  101.076000] usb-storage: waiting for device to settle before scanning
[  101.076000] usbcore: registered new interface driver usb-storage
[  101.076000] USB Mass Storage support registered.
[  106.076000] usb-storage: device scan complete
[  106.076000] scsi 6:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[  106.076000] sd 6:0:0:0: [sdb] 1981440 512-byte hardware sectors (1014 MB)
[  106.080000] sd 6:0:0:0: [sdb] Write Protect is off
[  106.080000] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  106.080000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  106.080000] sd 6:0:0:0: [sdb] 1981440 512-byte hardware sectors (1014 MB)
[  106.080000] sd 6:0:0:0: [sdb] Write Protect is off
[  106.080000] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  106.080000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  106.080000]  sdb: sdb1
[  106.208000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  106.208000] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  510.540000] usb 5-4: new high speed USB device using ehci_hcd and address 10
[  510.840000] usb 5-4: new high speed USB device using ehci_hcd and address 11
[  511.524000] usb 5-4: new high speed USB device using ehci_hcd and address 14
[  511.896000] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[  527.008000] usb 5-6: device descriptor read/64, error -110
[  542.224000] usb 5-6: device descriptor read/64, error -110
[  542.440000] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[  557.560000] usb 5-6: device descriptor read/64, error -110
[  572.776000] usb 5-6: device descriptor read/64, error -110
[  572.992000] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[  583.400000] usb 5-6: device not accepting address 3, error -110
[  583.512000] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[  593.920000] usb 5-6: device not accepting address 3, error -110
[  593.920000] sd 6:0:0:0: scsi: Device offlined - not ready after error recovery
[  593.920000] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  593.920000] end_request: I/O error, dev sdb, sector 22661
[  593.920000] sd 6:0:0:0: rejecting I/O to offline device
[  593.920000] sd 6:0:0:0: rejecting I/O to offline device
[  593.920000] sd 6:0:0:0: rejecting I/O to offline device
[  593.920000] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  593.920000] end_request: I/O error, dev sdb, sector 22901
[  593.920000] sd 6:0:0:0: rejecting I/O to offline device
[  593.920000] Buffer I/O error on device sdb1, logical block 485
[  593.920000] lost page write due to I/O error on sdb1
[  593.920000] Buffer I/O error on device sdb1, logical block 486
[  593.920000] lost page write due to I/O error on sdb1
[  593.920000] sd 6:0:0:0: rejecting I/O to offline device
[  593.920000] sd 6:0:0:0: rejecting I/O to offline device
[  593.920000] sd 6:0:0:0: rejecting I/O to offline device
[  594.032000] usb 5-4: new high speed USB device using ehci_hcd and address 15
[  594.088000] usb 5-6: USB disconnect, address 3
[  594.088000] FAT: unable to read inode block for updating (i_pos 7770)
[  594.204000] usb 5-6: new high speed USB device using ehci_hcd and address 16
[  609.316000] usb 5-6: device descriptor read/64, error -110
[  617.244000] scsi 6:0:0:0: rejecting I/O to dead device
[  618.252000] scsi 6:0:0:0: rejecting I/O to dead device
[  618.996000] scsi 6:0:0:0: rejecting I/O to dead device
[  619.636000] scsi 6:0:0:0: rejecting I/O to dead device
[  619.636000] FAT: unable to read inode block for updating (i_pos 7770)
[  624.532000] usb 5-6: device descriptor read/64, error -110
[  624.748000] usb 5-6: new high speed USB device using ehci_hcd and address 17
[  628.876000] ehci_hcd 0000:00:1d.7: port 6 reset error -110
[  628.876000] hub 5-0:1.0: hub_port_status failed (err = -32)
[  629.508000] usb 5-4: new high speed USB device using ehci_hcd and address 19
[  629.808000] usb 5-4: new high speed USB device using ehci_hcd and address 20
[  630.500000] usb 5-4: new high speed USB device using ehci_hcd and address 22
[  630.800000] usb 5-4: new high speed USB device using ehci_hcd and address 23
[  631.288000] usb 5-4: new high speed USB device using ehci_hcd and address 25
[  631.792000] usb 5-4: new high speed USB device using ehci_hcd and address 26
[  632.280000] usb 5-4: new high speed USB device using ehci_hcd and address 28
[  632.784000] usb 5-4: new high speed USB device using ehci_hcd and address 29
[  633.272000] usb 5-4: new high speed USB device using ehci_hcd and address 31
[  633.776000] usb 5-4: new high speed USB device using ehci_hcd and address 32
[  634.072000] usb 5-5: new high speed USB device using ehci_hcd and address 33
[  634.204000] usb 5-5: configuration #1 chosen from 1 choice
[  634.204000] scsi7 : SCSI emulation for USB Mass Storage devices
[  634.208000] usb-storage: device found at 33
[  634.208000] usb-storage: waiting for device to settle before scanning
[  634.824000] usb 5-4: new high speed USB device using ehci_hcd and address 36
[  635.316000] usb 5-4: new high speed USB device using ehci_hcd and address 38
[  635.820000] usb 5-4: new high speed USB device using ehci_hcd and address 39
[  636.872000] usb 5-4: new high speed USB device using ehci_hcd and address 44
[  637.364000] usb 5-4: new high speed USB device using ehci_hcd and address 46
[  637.868000] usb 5-4: new high speed USB device using ehci_hcd and address 47
[  638.920000] usb 5-4: new high speed USB device using ehci_hcd and address 52
[  639.208000] usb-storage: device scan complete
[  639.208000] scsi 7:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[  639.212000] sd 7:0:0:0: [sdb] 1981440 512-byte hardware sectors (1014 MB)
[  639.212000] sd 7:0:0:0: [sdb] Write Protect is off
[  639.212000] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  639.212000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  639.212000] sd 7:0:0:0: [sdb] 1981440 512-byte hardware sectors (1014 MB)
[  639.216000] sd 7:0:0:0: [sdb] Write Protect is off
[  639.216000] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  639.216000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  639.216000]  sdb: sdb1
[  639.340000] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  639.340000] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  639.412000] usb 5-4: new high speed USB device using ehci_hcd and address 54
[  639.916000] usb 5-4: new high speed USB device using ehci_hcd and address 55
[  640.972000] usb 5-4: new high speed USB device using ehci_hcd and address 60
[  641.460000] usb 5-4: new high speed USB device using ehci_hcd and address 62
[  641.964000] usb 5-4: new high speed USB device using ehci_hcd and address 63
[  642.452000] usb 5-4: new high speed USB device using ehci_hcd and address 65
[  643.148000] usb 5-4: new high speed USB device using ehci_hcd and address 67
[  643.316000] usb 5-5: reset high speed USB device using ehci_hcd and address 33
[  658.428000] usb 5-5: device descriptor read/64, error -110
[  666.312000] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[  666.312000] hub 5-0:1.0: hub_port_status failed (err = -32)
[  666.700000] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  666.700000] end_request: I/O error, dev sdb, sector 29909
[  666.700000] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  666.700000] end_request: I/O error, dev sdb, sector 30149
[  666.700000] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  666.700000] end_request: I/O error, dev sdb, sector 30181
[  666.700000] sd 7:0:0:0: [sdb] READ CAPACITY failed
[  666.700000] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  666.700000] sd 7:0:0:0: [sdb] Sense not available.
[  666.700000] sd 7:0:0:0: [sdb] Write Protect is off
[  666.700000] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  666.700000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  666.716000] sd 7:0:0:0: [sdb] READ CAPACITY failed
[  666.716000] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  666.716000] sd 7:0:0:0: [sdb] Sense not available.
[  666.724000] sd 7:0:0:0: [sdb] Write Protect is off
[  666.724000] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  666.724000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  666.740000] usb 5-5: USB disconnect, address 33
[  666.740000] Buffer I/O error on device sdb1, logical block 485
[  666.740000] lost page write due to I/O error on sdb1
[  666.740000] Buffer I/O error on device sdb1, logical block 486
[  666.740000] lost page write due to I/O error on sdb1
[  666.740000] Buffer I/O error on device sdb1, logical block 24005
[  666.740000] lost page write due to I/O error on sdb1
[  667.172000] usb 5-4: new high speed USB device using ehci_hcd and address 70
[  668.052000] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  668.352000] usb 5-4: new high speed USB device using ehci_hcd and address 72
[  669.044000] usb 5-4: new high speed USB device using ehci_hcd and address 74
[  669.344000] usb 5-4: new high speed USB device using ehci_hcd and address 75
[  670.224000] usb 5-4: new high speed USB device using ehci_hcd and address 78
[  670.524000] usb 5-4: new high speed USB device using ehci_hcd and address 79
[  671.388000] usb 5-4: new high speed USB device using ehci_hcd and address 83
[  672.268000] usb 5-4: new high speed USB device using ehci_hcd and address 86
[  672.568000] usb 5-4: new high speed USB device using ehci_hcd and address 87
[  672.868000] usb 5-4: new high speed USB device using ehci_hcd and address 88
[  673.780000] usb 5-4: new high speed USB device using ehci_hcd and address 89
[  674.268000] usb 5-4: new high speed USB device using ehci_hcd and address 91
[  674.772000] usb 5-4: new high speed USB device using ehci_hcd and address 92
[  675.260000] usb 5-4: new high speed USB device using ehci_hcd and address 94
[  675.752000] usb 5-4: new high speed USB device using ehci_hcd and address 96
[  676.428000] usb 5-4: new high speed USB device using ehci_hcd and address 99
[  677.308000] usb 5-4: new high speed USB device using ehci_hcd and address 102
[  678.360000] usb 5-4: new high speed USB device using ehci_hcd and address 107
[  678.864000] usb 5-4: new high speed USB device using ehci_hcd and address 108
[  679.352000] usb 5-4: new high speed USB device using ehci_hcd and address 110
[  680.224000] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  680.336000] usb 5-4: new high speed USB device using ehci_hcd and address 111
[  680.840000] usb 5-4: new high speed USB device using ehci_hcd and address 112
[  681.548000] usb 5-4: new high speed USB device using ehci_hcd and address 113
[  682.428000] usb 5-4: new high speed USB device using ehci_hcd and address 116
[  682.932000] usb 5-4: new high speed USB device using ehci_hcd and address 117
[  683.420000] usb 5-4: new high speed USB device using ehci_hcd and address 119
[  684.112000] usb 5-4: new high speed USB device using ehci_hcd and address 121
[  684.600000] usb 5-4: new high speed USB device using ehci_hcd and address 123
[  684.900000] usb 5-4: new high speed USB device using ehci_hcd and address 124
[  685.576000] usb 5-4: new high speed USB device using ehci_hcd and address 127
[  686.448000] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  686.748000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[  687.628000] usb 5-4: new high speed USB device using ehci_hcd and address 6
[  687.928000] usb 5-4: new high speed USB device using ehci_hcd and address 7
[  688.228000] usb 5-4: new high speed USB device using ehci_hcd and address 8
[  689.140000] usb 5-4: new high speed USB device using ehci_hcd and address 9
[  689.628000] usb 5-4: new high speed USB device using ehci_hcd and address 11
[  690.132000] usb 5-4: new high speed USB device using ehci_hcd and address 12
[  690.620000] usb 5-4: new high speed USB device using ehci_hcd and address 14
[  691.124000] usb 5-4: new high speed USB device using ehci_hcd and address 15
[  691.800000] usb 5-4: new high speed USB device using ehci_hcd and address 18
[  692.100000] usb 5-4: new high speed USB device using ehci_hcd and address 19
[  692.776000] usb 5-4: new high speed USB device using ehci_hcd and address 22
[  694.080000] usb 5-4: new high speed USB device using ehci_hcd and address 24
[  694.944000] usb 5-4: new high speed USB device using ehci_hcd and address 28
[  695.824000] usb 5-4: new high speed USB device using ehci_hcd and address 31
[  696.328000] usb 5-4: new high speed USB device using ehci_hcd and address 32
[  696.816000] usb 5-4: new high speed USB device using ehci_hcd and address 34
[  697.116000] usb 5-4: new high speed USB device using ehci_hcd and address 35
[  697.620000] usb 5-4: new high speed USB device using ehci_hcd and address 36
[  698.328000] usb 5-4: new high speed USB device using ehci_hcd and address 37
[  699.036000] usb 5-4: new high speed USB device using ehci_hcd and address 38
[  699.916000] usb 5-4: new high speed USB device using ehci_hcd and address 41
[  700.984000] usb 5-4: new high speed USB device using ehci_hcd and address 45
[  701.284000] usb 5-4: new high speed USB device using ehci_hcd and address 46
[  701.960000] usb 5-4: new high speed USB device using ehci_hcd and address 49
[  702.260000] usb 5-4: new high speed USB device using ehci_hcd and address 50
[  702.952000] usb 5-4: new high speed USB device using ehci_hcd and address 52
[  703.252000] usb 5-4: new high speed USB device using ehci_hcd and address 53
[  703.552000] usb 5-4: new high speed USB device using ehci_hcd and address 54
[  704.464000] usb 5-4: new high speed USB device using ehci_hcd and address 55
[  704.952000] usb 5-4: new high speed USB device using ehci_hcd and address 57
[  705.456000] usb 5-4: new high speed USB device using ehci_hcd and address 58
[  706.136000] usb 5-4: new high speed USB device using ehci_hcd and address 61
[  706.436000] usb 5-4: new high speed USB device using ehci_hcd and address 62
[  707.116000] usb 5-4: new high speed USB device using ehci_hcd and address 65
[  707.808000] usb 5-4: new high speed USB device using ehci_hcd and address 67
[  708.116000] usb 5-4: new high speed USB device using ehci_hcd and address 68
[  708.620000] usb 5-4: new high speed USB device using ehci_hcd and address 69
[  709.108000] usb 5-4: new high speed USB device using ehci_hcd and address 71
[  709.408000] usb 5-4: new high speed USB device using ehci_hcd and address 72
[  710.100000] usb 5-4: new high speed USB device using ehci_hcd and address 74
[  710.404000] usb 5-4: new high speed USB device using ehci_hcd and address 75
[  711.096000] usb 5-4: new high speed USB device using ehci_hcd and address 77
[  711.600000] usb 5-4: new high speed USB device using ehci_hcd and address 78
[  712.656000] usb 5-4: new high speed USB device using ehci_hcd and address 83
[  713.144000] usb 5-4: new high speed USB device using ehci_hcd and address 85
[  713.648000] usb 5-4: new high speed USB device using ehci_hcd and address 86
[  714.700000] usb 5-4: new high speed USB device using ehci_hcd and address 91
[  715.580000] usb 5-4: new high speed USB device using ehci_hcd and address 94
[  716.068000] usb 5-4: new high speed USB device using ehci_hcd and address 96
[  716.572000] usb 5-4: new high speed USB device using ehci_hcd and address 97
[  717.272000] usb 5-4: new high speed USB device using ehci_hcd and address 99
[  717.780000] usb 5-4: new high speed USB device using ehci_hcd and address 100
[  718.488000] usb 5-4: new high speed USB device using ehci_hcd and address 101
[  719.368000] usb 5-4: new high speed USB device using ehci_hcd and address 104
[  719.668000] usb 5-4: new high speed USB device using ehci_hcd and address 105
[  720.372000] usb 5-4: new high speed USB device using ehci_hcd and address 107
[  720.672000] usb 5-4: new high speed USB device using ehci_hcd and address 108
[  721.364000] usb 5-4: new high speed USB device using ehci_hcd and address 110
[  721.664000] usb 5-4: new high speed USB device using ehci_hcd and address 111
[  722.920000] usb 5-4: new high speed USB device using ehci_hcd and address 116
[  723.408000] usb 5-4: new high speed USB device using ehci_hcd and address 118
[  723.708000] usb 5-4: new high speed USB device using ehci_hcd and address 119
[  724.400000] usb 5-4: new high speed USB device using ehci_hcd and address 121
[  724.700000] usb 5-4: new high speed USB device using ehci_hcd and address 122
[  725.580000] usb 5-4: new high speed USB device using ehci_hcd and address 125
[  726.084000] usb 5-4: new high speed USB device using ehci_hcd and address 126
[  727.516000] usb 5-4: new high speed USB device using ehci_hcd and address 7
[  728.020000] usb 5-4: new high speed USB device using ehci_hcd and address 8
[  728.728000] usb 5-4: new high speed USB device using ehci_hcd and address 9
[  729.608000] usb 5-4: new high speed USB device using ehci_hcd and address 12
[  729.908000] usb 5-4: new high speed USB device using ehci_hcd and address 13
[  730.208000] usb 5-4: new high speed USB device using ehci_hcd and address 14
[  730.916000] usb 5-4: new high speed USB device using ehci_hcd and address 15
[  731.608000] usb 5-4: new high speed USB device using ehci_hcd and address 17
[  731.908000] usb 5-4: new high speed USB device using ehci_hcd and address 18
[  732.604000] usb 5-4: new high speed USB device using ehci_hcd and address 20
[  733.108000] usb 5-4: new high speed USB device using ehci_hcd and address 21
[  733.788000] usb 5-4: new high speed USB device using ehci_hcd and address 24
[  734.656000] usb 5-4: new high speed USB device using ehci_hcd and address 28
[  735.340000] usb 5-4: new high speed USB device using ehci_hcd and address 31
[  735.848000] usb 5-4: new high speed USB device using ehci_hcd and address 33
[  736.344000] usb 5-4: new high speed USB device using ehci_hcd and address 35
[  737.208000] usb 5-4: new high speed USB device using ehci_hcd and address 39
[  738.104000] usb 5-4: new high speed USB device using ehci_hcd and address 41
[  738.796000] usb 5-4: new high speed USB device using ehci_hcd and address 43
[  739.096000] usb 5-4: new high speed USB device using ehci_hcd and address 44
[  739.396000] usb 5-4: new high speed USB device using ehci_hcd and address 45
[  740.312000] usb 5-4: new high speed USB device using ehci_hcd and address 46
[  740.800000] usb 5-4: new high speed USB device using ehci_hcd and address 48
[  741.292000] usb 5-4: new high speed USB device using ehci_hcd and address 50
[  741.968000] usb 5-4: new high speed USB device using ehci_hcd and address 53
[  742.848000] usb 5-4: new high speed USB device using ehci_hcd and address 56
[  743.108000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[  743.108000] hub 5-0:1.0: hub_port_status failed (err = -32)
[  743.948000] usb 5-4: new high speed USB device using ehci_hcd and address 58
[  744.248000] usb 5-4: new high speed USB device using ehci_hcd and address 59
[  744.940000] usb 5-4: new high speed USB device using ehci_hcd and address 61
[  745.240000] usb 5-4: new high speed USB device using ehci_hcd and address 62
[  745.540000] usb 5-4: new high speed USB device using ehci_hcd and address 63
[  746.452000] usb 5-4: new high speed USB device using ehci_hcd and address 64
[  746.940000] usb 5-4: new high speed USB device using ehci_hcd and address 66
[  747.444000] usb 5-4: new high speed USB device using ehci_hcd and address 67
[  748.120000] usb 5-4: new high speed USB device using ehci_hcd and address 70
[  748.624000] usb 5-4: new high speed USB device using ehci_hcd and address 71
[  749.112000] usb 5-4: new high speed USB device using ehci_hcd and address 73
[  749.412000] usb 5-4: new high speed USB device using ehci_hcd and address 74
[  750.088000] usb 5-4: new high speed USB device using ehci_hcd and address 77
[  750.592000] usb 5-4: new high speed USB device using ehci_hcd and address 78
[  751.300000] usb 5-4: new high speed USB device using ehci_hcd and address 79
[  752.180000] usb 5-4: new high speed USB device using ehci_hcd and address 82
[  752.684000] usb 5-4: new high speed USB device using ehci_hcd and address 83
[  753.172000] usb 5-4: new high speed USB device using ehci_hcd and address 85
[  753.676000] usb 5-4: new high speed USB device using ehci_hcd and address 86
[  754.164000] usb 5-4: new high speed USB device using ehci_hcd and address 88
[  754.464000] usb 5-4: new high speed USB device using ehci_hcd and address 89
[  755.156000] usb 5-4: new high speed USB device using ehci_hcd and address 91
[  755.456000] usb 5-4: new high speed USB device using ehci_hcd and address 92
[  756.148000] usb 5-4: new high speed USB device using ehci_hcd and address 94
[  756.448000] usb 5-4: new high speed USB device using ehci_hcd and address 95
[  757.328000] usb 5-4: new high speed USB device using ehci_hcd and address 98
[  758.208000] usb 5-4: new high speed USB device using ehci_hcd and address 101
[  758.712000] usb 5-4: new high speed USB device using ehci_hcd and address 102
[  759.388000] usb 5-4: new high speed USB device using ehci_hcd and address 105
[  759.688000] usb 5-4: new high speed USB device using ehci_hcd and address 106
[  760.364000] usb 5-4: new high speed USB device using ehci_hcd and address 109
[  761.668000] usb 5-4: new high speed USB device using ehci_hcd and address 111
[  762.532000] usb 5-4: new high speed USB device using ehci_hcd and address 115
[  763.412000] usb 5-4: new high speed USB device using ehci_hcd and address 118
[  763.916000] usb 5-4: new high speed USB device using ehci_hcd and address 119
[  764.404000] usb 5-4: new high speed USB device using ehci_hcd and address 121
[  764.704000] usb 5-4: new high speed USB device using ehci_hcd and address 122
[  765.396000] usb 5-4: new high speed USB device using ehci_hcd and address 124
[  765.696000] usb 5-4: new high speed USB device using ehci_hcd and address 125
[  766.200000] usb 5-4: new high speed USB device using ehci_hcd and address 126
[  766.908000] usb 5-4: new high speed USB device using ehci_hcd and address 127
[  767.616000] usb 5-4: new high speed USB device using ehci_hcd and address 2
[  768.496000] usb 5-4: new high speed USB device using ehci_hcd and address 5
[  768.796000] usb 5-4: new high speed USB device using ehci_hcd and address 6
[  769.864000] usb 5-4: new high speed USB device using ehci_hcd and address 10

```

---

### Post by trevorgasm on 2008-02-09
bump.

---

### Post by lank23 on 2008-02-09
"FAT: unable to read inode block for updating (i_pos 7770)"

Seems like the partition table is corrupt. and or the cable is bad.

---

### Post by trevorgasm on 2008-02-09
Thanks for all of your responses.
I tried a different cable. Same results. Also, the drive works 100% OK on the windows side. 

Anyone have any ideas?

---

### Post by mrsteveman1 on 2008-02-09
Check /dev/ , does the block device (for the entire disk) appear and stay when the drive is connected?

I do notice that the end of your dmesg has ~40 usb connect messages so something is failing at the device level. It does say "maybe the cable is bad" so try another cable first.

Windows might be ignoring the problem and failing safe in some way, so you might not notice it in windows.

---

### Post by trevorgasm on 2008-02-09
thank you for your reply mrsteveman1, I am not exactly sure what to look for in /dev/. Nothing changes in /dev/ when the external is turned on, or shut off.

I have tried another cable.

Good point about windows possibly ignoring the error.

Thank you. The search goes on.

---

### Post by lank23 on 2008-02-09
what kind of case is the hard drive in?

---

### Post by trevorgasm on 2008-02-09
"Acomdata"

---

### Post by lank23 on 2008-02-09
what do you get from lsusb when the unit is plugged in and powered?

---

### Post by trevorgasm on 2008-02-09
only this:
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

---

### Post by lank23 on 2008-02-09
seems like the unit is no recognized.

---

### Post by trevorgasm on 2008-02-09
should i save what i can on the windows side? and reformat it?

---

### Post by mrsteveman1 on 2008-02-09
If lsusb isn't showing a connected USB device at all there won't be a block device for it in /dev/ anyway, but you would be looking for an extra /dev/sdb or sdc etc.

It does sound like the device isn't remaining connected in Linux at the moment, particularly because of all the errors in dmesg and all the connect notifications.

First thing would be to use a different cable, and also try connecting it to different machines. If the problem is with the device itself it wouldn't matter where its connected. 

The fact that it works fine in windows makes a lot of things unlikely, if it WEREN'T working in windows i would suspect the power supply for the drive or perhaps the drive itself, sometimes failing drives reset their interfaces and drop off the radar so to speak.

---

### Post by mrsteveman1 on 2008-02-09
Definitely get any important data off the drive so that failures or attempted mounts don't hurt anything.

Also you may want to check the device itself in windows with chkdsk

---

### Post by trevorgasm on 2008-02-09
thank you

---

### Post by dcstar on 2008-02-10
You should power off your machine and remove the battery (for 20-30 seconds), and then fire it all up again.

If the hardware powering the USB ports or the USB ports themselves have got "confused", then a normal power off may not reset them as a lot of systems keep powering the USB sub-system after the main system is off.

---

### Post by trevorgasm on 2008-02-10
I backed everything up. Reformatted the drive (ntfs again). Still not showing up on the linux side.

dcstar, I tried what you suggested, however it did not seem to work. Thank you.

---

### Post by lank23 on 2008-02-10
make a small partition say 3-5gb that is formatted to FAT16 and see what happens.

---

### Post by trevorgasm on 2008-02-11
Tried it. Yet again, not working.
I'm stumped. Thanks for your help so far.

---

### Post by davepars on 2008-02-12
not that this is likely to help but I have what seems to be the same problem so am following thread with much interest

Thanks to all

Newbie

---

### Post by lank23 on 2008-02-12
I just tried my external usb hard drive and it is also not auto mounting.  It did work before.  What I did find is once I plug it in I can go to "Places" -> "Computer" and I see the drive and if I double click on the drive it will mount and place an icon on the desktop.

lank23

---

### Post by trevorgasm on 2008-02-12
lank23, thanks, I will try that when I have finished writing this paper tonight. Thanks again.

---

### Post by trevorgasm on 2008-02-12
Stumped again...

---

### Post by lank23 on 2008-02-14
Today I installed a the new kernel update on my other laptop that was not auto mounting the external drive and now it works like a charm!  Not sure why but below are the logs from the updates that were installed.

```

Upgraded the following packages:
linux-headers-2.6.22-14 (2.6.22-14.51) to 2.6.22-14.52
linux-headers-2.6.22-14-generic (2.6.22-14.51) to 2.6.22-14.52
linux-image-2.6.22-14-generic (2.6.22-14.51) to 2.6.22-14.52

```

lank23

---

### Post by trevorgasm on 2008-02-15
Thanks for your repeated responses. I tried this too, to no avail. I do not understnad it.

---

### Post by trevorgasm on 2008-02-16
Quick update. Ubuntu, Mint, Fedora, Suse, and Debian all fail to detect my external hard drive. With XP it still works like a charm.

---

### Post by trevorgasm on 2008-02-18
quick bump for anyone that may still have some help to offer.

---

### Post by lank23 on 2008-02-25
trevorgasm;

you could try to erase the partition table / disk by using killdisk in windoze then use  disk manager to make a new partition and give it a try.  If you do this it will wipe the disk clean, so make sure you back up your data.

Once you do this post the output of the below with the unit plugged in.

```

sudo fdisk -l

lsusb

dmesg | tail | grep usb


```

lank23

---

### Post by sunseeker888 on 2008-03-16
HI 

I had the same problem, could not see the usb hard disk:lolflag:. I did switch to a different USB port, then dmseg and lsusb saw the device, which they did not before. But it would not still mount it, so I did manually, everything works like a charm now.

cd
wget [http://media.ubuntu-nl.org/scripts/diskmounter](http://media.ubuntu-nl.org/scripts/diskmounter)

The file diskmounter will now be in the current user's home directory.
Using the script

The script is non-interactive, and usage is simple. Type the following line.

sudo bash diskmounter


that  should do the trick.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by trevorgasm on 2008-03-20
Sunseeker, thanks so much for the reply, I'll try this as soon as I am done backing my stuff up again.

---

