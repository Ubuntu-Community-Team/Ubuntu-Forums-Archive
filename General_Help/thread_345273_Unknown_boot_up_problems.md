---
title: "Unknown boot up problems"
date: 2007-01-24
forum: General Help
---

### Post by M0nk3yM4n on 2007-01-24
Here is my var/log/messages

> 

Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:08: ioport range 0x900-0x90f has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:08: ioport range 0x910-0x91f has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:08: ioport range 0x920-0x92f has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:08: ioport range 0x930-0x93f has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] pnp: 00:08: ioport range 0x940-0x97f has been reserved
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] PCI: Bridge: 0000:00:01.0
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000]   IO window: d000-dfff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000]   MEM window: dd000000-dfefffff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000]   PREFETCH window: c0000000-cfffffff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] PCI: Bus 4, cardbus bridge: 0000:03:01.0
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000]   IO window: 00002000-000020ff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000]   IO window: 00002400-000024ff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000]   PREFETCH window: 50000000-51ffffff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000]   MEM window: 52000000-53ffffff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] PCI: Bridge: 0000:00:1e.0
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000]   IO window: 2000-2fff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000]   MEM window: dcf00000-dcffffff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000]   PREFETCH window: 50000000-51ffffff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 177
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.092000] NET: Registered protocol family 2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] TCP: Hash tables configured (established 131072 bind 65536)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] TCP reno registered
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] Simple Boot Flag at 0x79 set to 0x1
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] audit: initializing netlink socket (disabled)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] audit(1169594209.132:1): initialized
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] highmem bounce pool size: 64 pages
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] VFS: Disk quotas dquot_6.5.1
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] Initializing Cryptographic API
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] io scheduler noop registered
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] io scheduler anticipatory registered
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] io scheduler deadline registered
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] io scheduler cfq registered (default)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] assign_interrupt_mode Found MSI capability
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.132000] isapnp: Scanning for PnP cards...
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.488000] isapnp: No Plug & Play device found
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.508000] Real Time Clock Driver v1.12ac
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.508000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.508000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 201
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.508000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.508000] mice: PS/2 mouse device common for all mice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.508000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.508000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.508000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.508000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] EISA: Probing bus 0 at eisa.0
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] Cannot allocate resource for EISA slot 1
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] Cannot allocate resource for EISA slot 2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] EISA: Detected 0 cards.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] TCP bic registered
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] NET: Registered protocol family 1
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] NET: Registered protocol family 8
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] NET: Registered protocol family 20
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] Using IPI No-Shortcut mode
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] ACPI: (supports S0 S3 S4 S5)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.512000] Freeing unused kernel memory: 308k freed
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179574.520000] input: AT Translated Set 2 keyboard as /class/input/input0
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.580000] Capability LSM initialized
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.604000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.604000] ACPI: Processor [CPU0] (supports 8 throttling states)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.604000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.608000] ACPI: Thermal Zone [THM] (53 C)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.844000] SCSI subsystem initialized
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.848000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 201
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.848000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.848000] ahci: probe of 0000:00:1f.2 failed with error -12
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.852000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 201
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179575.852000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xBFA0 irq 14
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.016000] ata1: dev 0 ATA-6, max UDMA/100, 156301488 sectors: LBA48
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.016000] ata1(0): applying bridge limits
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.024000] ata1: dev 0 configured for UDMA/100
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.024000] scsi0 : ata_piix
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.024000]   Vendor: ATA       Model: Hitachi HTS72108  Rev: MC4O
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.024000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.024000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xBFA8 irq 15
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.344000] ata2: dev 0 ATAPI, max UDMA/33
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.508000] ata2: dev 0 configured for UDMA/33
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.508000] scsi1 : ata_piix
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.508000]   Vendor: SONY      Model: DVD+-RW DW-D56A   Rev: PDS7
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.508000]   Type:   CD-ROM                             ANSI SCSI revision: 05
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.524000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.524000] sda: Write Protect is off
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.524000] SCSI device sda: drive cache: write back
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.524000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.524000] sda: Write Protect is off
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.524000] SCSI device sda: drive cache: write back
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.524000]  sda: sda1 sda2 < sda5 sda6 > sda3
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.572000] sd 0:0:0:0: Attached scsi disk sda
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.840000] ide0: I/O resource 0x1F0-0x1F7 not free.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.840000] ide0: ports already in use, skipping probe
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.840000] ide1: I/O resource 0x170-0x177 not free.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.840000] ide1: ports already in use, skipping probe
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.864000] usbcore: registered new driver usbfs
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.864000] usbcore: registered new driver hub
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.864000] USB Universal Host Controller Interface driver v3.0
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.864000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.864000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.864000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.864000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000bf80
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.864000] usb usb1: configuration #1 chosen from 1 choice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.864000] hub 1-0:1.0: USB hub found
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.864000] hub 1-0:1.0: 2 ports detected
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.968000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 201
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.968000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.968000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.968000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x0000bf60
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.968000] usb usb2: configuration #1 chosen from 1 choice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.968000] hub 2-0:1.0: USB hub found
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179576.968000] hub 2-0:1.0: 2 ports detected
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.072000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.072000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.072000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.072000] uhci_hcd 0000:00:1d.2: irq 209, io base 0x0000bf40
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.072000] usb usb3: configuration #1 chosen from 1 choice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.072000] hub 3-0:1.0: USB hub found
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.072000] hub 3-0:1.0: 2 ports detected
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.176000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 177
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.176000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.176000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.176000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000bf20
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.176000] usb usb4: configuration #1 chosen from 1 choice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.176000] hub 4-0:1.0: USB hub found
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.176000] hub 4-0:1.0: 2 ports detected
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.208000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.284000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 169
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.284000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.284000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.284000] ehci_hcd 0000:00:1d.7: debug port 1
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.284000] ehci_hcd 0000:00:1d.7: irq 169, io mem 0xffa80800
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.288000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.288000] usb usb5: configuration #1 chosen from 1 choice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.288000] hub 5-0:1.0: USB hub found
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.288000] hub 5-0:1.0: 8 ports detected
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.392000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 209
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.452000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[209]  MMIO=[dcffc800-dcffcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.500000] Attempting manual resume
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.508000] EXT3-fs: INFO: recovery required on readonly filesystem.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179577.508000] EXT3-fs: write access will be enabled during recovery.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179578.416000] usb 5-1: new high speed USB device using ehci_hcd and address 2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179578.548000] usb 5-1: configuration #1 chosen from 1 choice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179578.548000] hub 5-1:1.0: USB hub found
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179578.548000] hub 5-1:1.0: 4 ports detected
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179579.404000] usb 5-1.2: new high speed USB device using ehci_hcd and address 6
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179579.476000] kjournald starting.  Commit interval 5 seconds
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179579.476000] EXT3-fs: recovery complete.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179579.476000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179579.496000] usb 5-1.2: configuration #1 chosen from 1 choice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179579.736000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179579.920000] usb 1-2: configuration #1 chosen from 1 choice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179580.164000] usb 3-1: new full speed USB device using uhci_hcd and address 2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179580.352000] usb 3-1: configuration #1 chosen from 1 choice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179580.652000] usb 4-2: new low speed USB device using uhci_hcd and address 2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179580.824000] usb 4-2: configuration #1 chosen from 1 choice
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179589.288000] NET: Registered protocol family 17
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179655.500000] input: PC Speaker as /class/input/input1
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179655.508000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179655.604000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179655.756000] Linux agpgart interface v0.101 (c) Dave Jones
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179655.780000] agpgart: Detected an Intel 915GM Chipset.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179655.796000] agpgart: AGP aperture is 256M @ 0x0
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.028000] input: PS/2 Mouse as /class/input/input2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.048000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.188000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 177
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.188000] Yenta: CardBus bridge found at 0000:03:01.0 [1028:01aa]
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.316000] Yenta: ISA IRQ mask 0x04b8, PCI irq 177
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.316000] Socket status: 30000820
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.316000] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.316000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.316000] cs: IO port probe 0x2000-0x2fff: clean.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.316000] pcmcia: parent PCI bridge Memory window: 0xdcf00000 - 0xdcffffff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.316000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.340000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x413C pid 0x5008
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.340000] usbcore: registered new driver usblp
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.340000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.416000] sdhci: Secure Digital Host Controller Interface driver, 0.12
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.416000] sdhci: Copyright(c) Pierre Ossman
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.416000] sdhci: SDHCI controller found at 0000:03:01.2 [1180:0822] (rev 17)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.416000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 201
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.416000] mmc0: SDHCI at 0xdcffc700 irq 201 DMA
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.516000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.516000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.604000] b44.c:v1.00 (Apr 7, 2006)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.604000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 209
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.608000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:12:3f:eb:d8:e8
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.656000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.656000]  1:0:0:0: Attached scsi generic sg1 type 5
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.828000] usbcore: registered new driver libusual
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.856000] usbcore: registered new driver hiddev
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.856000] hiddev96: USB HID v1.10 Device [Western Digital External HDD] on usb-0000:00:1d.7-1.2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.876000] input: Logitech USB Receiver as /class/input/input4
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.876000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-2
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.876000] usbcore: registered new driver usbhid
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.876000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.952000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.1dmq
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.952000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.952000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 201
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.952000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.968000] pccard: CardBus card inserted into slot 0
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179656.988000] ts: Compaq touchscreen protocol output
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.100000] nvidia: module license 'NVIDIA' taints kernel.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.132000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.132000] Uniform CD-ROM driver Revision: 3.20
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.368000] ipw2200: Radio Frequency Kill Switch is On:
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.368000] Kill switch must be turned off for wireless networking to work.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.368000] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.368000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.368000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.616000] Initializing USB Mass Storage driver...
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.620000] usbcore: registered new driver snd-usb-audio
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.636000] scsi2 : SCSI emulation for USB Mass Storage devices
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.636000] usbcore: registered new driver usb-storage
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.636000] USB Mass Storage support registered.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.892000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 169
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.964000] cs: IO port probe 0x100-0x3af: excluding 0x370-0x377
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.964000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.964000] cs: IO port probe 0x820-0x8ff: clean.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.968000] cs: IO port probe 0xc00-0xcf7: clean.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179657.968000] cs: IO port probe 0xa00-0xaff: clean.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179658.712000] intel8x0_measure_ac97_clock: measured 55525 usecs
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179658.712000] intel8x0: clocking to 48000
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179658.712000] PCI: Enabling device 0000:04:00.0 (0000 -> 0001)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179658.712000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 177
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179658.716000] Audigy2 value: Special config.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179659.004000] lp: driver loaded but no devices found
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179659.028000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179659.028000] ieee1394: sbp2: Try serialize_io=0 for better performance
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179659.068000] fuse init (API version 7.6)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179659.088000] Adding 337324k swap on /dev/disk/by-uuid/c98f3f32-9b92-4fce-aac7-b9199736d0de.  Priority:-1 extents:1 across:337324k
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179659.128000] EXT3 FS on sda3, internal journal
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179659.680000] b44: eth0: Link is up at 100 Mbps, full duplex.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179659.680000] b44: eth0: Flow control is off for TX and off for RX.
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179660.420000] ACPI: AC Adapter [AC] (on-line)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179660.740000] ACPI: Battery Slot [BAT0] (battery present)
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179660.756000] ACPI: Lid Switch [LID]
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179660.756000] ACPI: Power Button (CM) [PBTN]
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179660.756000] ACPI: Sleep Button (CM) [SBTN]
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179660.864000] pcc_acpi: loading...
Jan 23 23:18:12 m0nk3ym4n-laptop kernel: [17179660.944000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jan 23 23:18:12 m0nk3ym4n-laptop hpiod: 1.6.9 accepting connections at 2208... 
Jan 23 23:18:13 m0nk3ym4n-laptop kernel: [17179662.640000]   Vendor: WD        Model: 1600JB External   Rev: 0112
Jan 23 23:18:13 m0nk3ym4n-laptop kernel: [17179662.640000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan 23 23:18:13 m0nk3ym4n-laptop kernel: [17179662.660000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Jan 23 23:18:13 m0nk3ym4n-laptop kernel: [17179662.660000] sdb: Write Protect is off
Jan 23 23:18:13 m0nk3ym4n-laptop kernel: [17179662.664000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Jan 23 23:18:13 m0nk3ym4n-laptop kernel: [17179662.664000] sdb: Write Protect is off
Jan 23 23:18:13 m0nk3ym4n-laptop kernel: [17179662.664000]  sdb: sdb1
Jan 23 23:18:13 m0nk3ym4n-laptop kernel: [17179662.680000] sd 2:0:0:0: Attached scsi disk sdb
Jan 23 23:18:13 m0nk3ym4n-laptop kernel: [17179662.680000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jan 23 23:18:14 m0nk3ym4n-laptop kernel: [17179662.864000] apm: BIOS not found.
Jan 23 23:18:17 m0nk3ym4n-laptop kernel: [17179665.960000] NET: Registered protocol family 10
Jan 23 23:18:17 m0nk3ym4n-laptop kernel: [17179665.960000] lo: Disabled Privacy Extensions
Jan 23 23:18:17 m0nk3ym4n-laptop kernel: [17179665.960000] IPv6 over IPv4 tunneling driver
Jan 23 23:18:26 m0nk3ym4n-laptop dhcdbd: Started up.
Jan 23 23:18:26 m0nk3ym4n-laptop kernel: [17179674.100000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan 23 23:18:28 m0nk3ym4n-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jan 23 23:18:28 m0nk3ym4n-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jan 23 23:18:28 m0nk3ym4n-laptop kernel: [17179676.428000] Bluetooth: Core ver 2.8
Jan 23 23:18:28 m0nk3ym4n-laptop kernel: [17179676.428000] NET: Registered protocol family 31
Jan 23 23:18:28 m0nk3ym4n-laptop kernel: [17179676.428000] Bluetooth: HCI device and connection manager initialized
Jan 23 23:18:28 m0nk3ym4n-laptop kernel: [17179676.428000] Bluetooth: HCI socket layer initialized
Jan 23 23:18:28 m0nk3ym4n-laptop kernel: [17179676.460000] Bluetooth: L2CAP ver 2.8
Jan 23 23:18:28 m0nk3ym4n-laptop kernel: [17179676.460000] Bluetooth: L2CAP socket layer initialized
Jan 23 23:18:29 m0nk3ym4n-laptop kernel: [17179676.480000] Bluetooth: RFCOMM socket layer initialized
Jan 23 23:18:29 m0nk3ym4n-laptop kernel: [17179676.480000] Bluetooth: RFCOMM TTY layer initialized
Jan 23 23:18:29 m0nk3ym4n-laptop kernel: [17179676.480000] Bluetooth: RFCOMM ver 1.7
Jan 23 23:18:34 m0nk3ym4n-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jan 23 23:18:34 m0nk3ym4n-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jan 23 23:18:34 m0nk3ym4n-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jan 23 23:18:34 m0nk3ym4n-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jan 23 23:18:40 m0nk3ym4n-laptop gconfd (m0nk3ym4n-5119): starting (version 2.16.0), pid 5119 user 'm0nk3ym4n'
Jan 23 23:18:40 m0nk3ym4n-laptop gconfd (m0nk3ym4n-5119): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 23 23:18:40 m0nk3ym4n-laptop gconfd (m0nk3ym4n-5119): Resolved address "xml:readwrite:/home/m0nk3ym4n/.gconf" to a writable configuration source at position 1
Jan 23 23:18:40 m0nk3ym4n-laptop gconfd (m0nk3ym4n-5119): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 23 23:18:40 m0nk3ym4n-laptop gconfd (m0nk3ym4n-5119): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 23 23:18:40 m0nk3ym4n-laptop gconfd (m0nk3ym4n-5119): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 23 23:18:53 m0nk3ym4n-laptop kernel: [17179700.588000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Jan 23 23:18:53 m0nk3ym4n-laptop kernel: [17179700.796000] NTFS volume version 3.1.
Jan 23 23:18:53 m0nk3ym4n-laptop gconfd (m0nk3ym4n-5119): Resolved address "xml:readwrite:/home/m0nk3ym4n/.gconf" to a writable configuration source at position 0
Jan 23 23:20:42 m0nk3ym4n-laptop gconfd (root-5502): starting (version 2.16.0), pid 5502 user 'root'
Jan 23 23:20:42 m0nk3ym4n-laptop gconfd (root-5502): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 23 23:20:42 m0nk3ym4n-laptop gconfd (root-5502): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jan 23 23:20:42 m0nk3ym4n-laptop gconfd (root-5502): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 23 23:20:42 m0nk3ym4n-laptop gconfd (root-5502): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 23 23:20:42 m0nk3ym4n-laptop gconfd (root-5502): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 23 23:22:12 m0nk3ym4n-laptop gconfd (root-5502): GConf server is not in use, shutting down.
Jan 23 23:22:12 m0nk3ym4n-laptop gconfd (root-5502): Exiting
Jan 23 23:22:24 m0nk3ym4n-laptop gconfd (root-5565): starting (version 2.16.0), pid 5565 user 'root'
Jan 23 23:22:24 m0nk3ym4n-laptop gconfd (root-5565): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 23 23:22:24 m0nk3ym4n-laptop gconfd (root-5565): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jan 23 23:22:24 m0nk3ym4n-laptop gconfd (root-5565): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 23 23:22:24 m0nk3ym4n-laptop gconfd (root-5565): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 23 23:22:24 m0nk3ym4n-laptop gconfd (root-5565): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 23 23:22:54 m0nk3ym4n-laptop gconfd (root-5565): GConf server is not in use, shutting down.
Jan 23 23:22:54 m0nk3ym4n-laptop gconfd (root-5565): Exiting
Jan 23 23:38:12 m0nk3ym4n-laptop -- MARK --
Jan 23 23:44:14 m0nk3ym4n-laptop gconfd (root-6386): starting (version 2.16.0), pid 6386 user 'root'
Jan 23 23:44:14 m0nk3ym4n-laptop gconfd (root-6386): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 23 23:44:14 m0nk3ym4n-laptop gconfd (root-6386): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jan 23 23:44:14 m0nk3ym4n-laptop gconfd (root-6386): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 23 23:44:14 m0nk3ym4n-laptop gconfd (root-6386): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 23 23:44:14 m0nk3ym4n-laptop gconfd (root-6386): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 23 23:46:14 m0nk3ym4n-laptop gconfd (root-6386): GConf server is not in use, shutting down.
Jan 23 23:46:14 m0nk3ym4n-laptop gconfd (root-6386): Exiting
Jan 23 23:53:26 m0nk3ym4n-laptop kernel: [17181773.352000] usb 5-6: new high speed USB device using ehci_hcd and address 7
Jan 23 23:53:26 m0nk3ym4n-laptop kernel: [17181773.484000] usb 5-6: configuration #1 chosen from 2 choices
Jan 23 23:53:26 m0nk3ym4n-laptop kernel: [17181773.484000] scsi3 : SCSI emulation for USB Mass Storage devices
Jan 23 23:53:31 m0nk3ym4n-laptop kernel: [17181778.488000]   Vendor: Apple     Model: iPod              Rev: 1.62
Jan 23 23:53:31 m0nk3ym4n-laptop kernel: [17181778.488000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan 23 23:53:31 m0nk3ym4n-laptop kernel: [17181778.492000] SCSI device sdc: 58605119 512-byte hdwr sectors (30006 MB)
Jan 23 23:53:31 m0nk3ym4n-laptop kernel: [17181778.492000] sdc: Write Protect is off
Jan 23 23:53:31 m0nk3ym4n-laptop kernel: [17181778.492000] SCSI device sdc: 58605119 512-byte hdwr sectors (30006 MB)
Jan 23 23:53:31 m0nk3ym4n-laptop kernel: [17181778.496000] sdc: Write Protect is off
Jan 23 23:53:31 m0nk3ym4n-laptop kernel: [17181778.496000]  sdc: sdc1 sdc2
Jan 23 23:53:31 m0nk3ym4n-laptop kernel: [17181778.508000] sd 3:0:0:0: Attached scsi removable disk sdc
Jan 23 23:53:31 m0nk3ym4n-laptop kernel: [17181778.508000] sd 3:0:0:0: Attached scsi generic sg3 type 0
Jan 23 23:59:45 m0nk3ym4n-laptop gconfd (root-7332): starting (version 2.16.0), pid 7332 user 'root'
Jan 23 23:59:45 m0nk3ym4n-laptop gconfd (root-7332): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 23 23:59:45 m0nk3ym4n-laptop gconfd (root-7332): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jan 23 23:59:45 m0nk3ym4n-laptop gconfd (root-7332): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 23 23:59:45 m0nk3ym4n-laptop gconfd (root-7332): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 23 23:59:45 m0nk3ym4n-laptop gconfd (root-7332): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4


I have no idea why but it seemed like all of a sudden when it's booting Ubuntu it has the cool little screen with the orange bar but then that goes away to a black screen with the blinking cursor at the top left then it gives me a RNG error message and that there was a hw_random failure or something and does a fsck. I have already blacklisted the hw_random module but it won't go away. What do I do?!

---

### Post by M0nk3yM4n on 2007-01-24
[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

Snap, found you can disable it by reading here....

going to reboot and see what happens now...

---

