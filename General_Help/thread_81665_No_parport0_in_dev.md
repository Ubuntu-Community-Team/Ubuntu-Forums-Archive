---
title: "No parport0 in /dev"
date: 2005-10-24
forum: General Help
---

### Post by jiez on 2005-10-24
I'm using Ubuntu on Dell Latitude D610. From dmesg, it seems the kernel detects parport correctly. (The dmesg log is below.) However, there is no parport0 in /dev. Is it a bug? How can I bring parport0 back?

Thanks.

00:00:01.0 to 64
[4294669.483000] assign_interrupt_mode Found MSI capability
[4294669.483000] Allocate Port Service[pcie00]
[4294669.483000] Allocate Port Service[pcie03]
[4294669.483000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294669.483000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294669.483000] assign_interrupt_mode Found MSI capability
[4294669.483000] Allocate Port Service[pcie00]
[4294669.483000] Allocate Port Service[pcie02]
[4294669.483000] Allocate Port Service[pcie03]
[4294669.483000] isapnp: Scanning for PnP cards...
[4294669.837000] isapnp: No Plug & Play device found
[4294669.853000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294669.856000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.857000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.857000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.857000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.859000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.859000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 17
[4294669.859000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[4294669.859000] io scheduler noop registered
[4294669.859000] io scheduler anticipatory registered
[4294669.859000] io scheduler deadline registered
[4294669.859000] io scheduler cfq registered
[4294669.859000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.860000] EISA: Probing bus 0 at eisa.0
[4294669.860000] Cannot allocate resource for EISA slot 1
[4294669.860000] EISA: Detected 0 cards.
[4294669.860000] NET: Registered protocol family 2
[4294669.869000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294669.869000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294669.869000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.869000] TCP: Hash tables configured (established 32768 bind 32768)
[4294669.869000] NET: Registered protocol family 8
[4294669.869000] NET: Registered protocol family 20
[4294669.869000] ACPI wakeup devices: 
[4294669.869000]  LID PBTN PCI0 USB0 USB1 USB2 USB4 USB3 MODM PCIE  NIC 
[4294669.869000] ACPI: (supports S0 S3 S4 S4bios S5)
[4294669.869000] Freeing unused kernel memory: 224k freed
[4294669.876000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294669.880000] vga16fb: initializing
[4294669.880000] vga16fb: mapped to 0xc00a0000
[4294669.941000] Console: switching to colour frame buffer device 80x30
[4294669.941000] fb0: VGA16 VGA frame buffer device
[4294671.085000] Capability LSM initialized
[4294671.094000] NET: Registered protocol family 1
[4294671.107000] SCSI subsystem initialized
[4294671.108000] libata version 1.11 loaded.
[4294671.109000] ahci version 1.00
[4294671.109000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[4294671.109000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[4294671.109000] ahci: probe of 0000:00:1f.2 failed with error -12
[4294671.110000] ata_piix version 1.03
[4294671.110000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[4294671.110000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294671.110000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xBFA0 irq 14
[4294671.264000] ata1: dev 0 cfg 49:0f00 82:746b 83:7fe8 84:4023 85:f469 86:3c48 87:4023 88:203f
[4294671.264000] ata1: dev 0 ATA, max UDMA/100, 117210240 sectors: lba48
[4294671.264000] ata1(0): applying bridge limits
[4294671.264000] ata1: dev 0 configured for UDMA/100
[4294671.264000] scsi0 : ata_piix
[4294671.264000]   Vendor: ATA       Model: HTS548060M9AT00   Rev: MGBO
[4294671.264000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294671.265000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xBFA8 irq 15
[4294671.570000] ata2: dev 0 cfg 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[4294671.570000] ata2: dev 0 ATAPI, max UDMA/33
[4294671.570000] ata2: dev 0 configured for UDMA/33
[4294671.570000] scsi1 : ata_piix
[4294671.571000]   Vendor: PHILIPS   Model: CDRW/DVD CDD5263  Rev: UD91
[4294671.571000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[4294671.582000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.582000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.582000] ACPI: bus type ide registered
[4294671.582000] ide0: I/O resource 0x1F0-0x1F7 not free.
[4294671.582000] ide0: ports already in use, skipping probe
[4294671.582000] ide1: I/O resource 0x170-0x177 not free.
[4294671.582000] ide1: ports already in use, skipping probe
[4294671.582000] Probing IDE interface ide2...
[4294672.095000] Probing IDE interface ide3...
[4294672.607000] Probing IDE interface ide4...
[4294673.119000] Probing IDE interface ide5...
[4294673.634000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[4294673.634000] SCSI device sda: drive cache: write back
[4294673.634000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[4294673.634000] SCSI device sda: drive cache: write back
[4294673.634000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 > p4
[4294673.690000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294673.834000] Attempting manual resume
[4294673.847000] swsusp: Suspend partition has wrong signature?
[4294673.875000] usbcore: registered new driver usbfs
[4294673.875000] usbcore: registered new driver hub
[4294673.876000] USB Universal Host Controller Interface driver v2.2
[4294673.876000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294673.876000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294673.876000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294673.938000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294673.938000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[4294673.938000] hub 1-0:1.0: USB hub found
[4294673.938000] hub 1-0:1.0: 2 ports detected
[4294673.941000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[4294673.941000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294673.941000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294674.003000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294674.003000] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[4294674.003000] hub 2-0:1.0: USB hub found
[4294674.003000] hub 2-0:1.0: 2 ports detected
[4294674.006000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294674.006000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294674.006000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294674.068000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294674.068000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[4294674.068000] hub 3-0:1.0: USB hub found
[4294674.068000] hub 3-0:1.0: 2 ports detected
[4294674.071000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[4294674.071000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294674.071000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294674.133000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294674.133000] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[4294674.133000] hub 4-0:1.0: USB hub found
[4294674.133000] hub 4-0:1.0: 2 ports detected
[4294674.163000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
[4294674.163000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294674.163000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294674.163000] ehci_hcd 0000:00:1d.7: debug port 1
[4294674.163000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294674.163000] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[4294674.167000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294674.167000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294674.167000] hub 5-0:1.0: USB hub found
[4294674.167000] hub 5-0:1.0: 8 ports detected
[4294674.242000] tg3.c:v3.31 (June 8, 2005)
[4294674.242000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294674.242000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[4294674.248000] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCIX:100MHz:32-bit) 10/100/1000BaseT Ethernet 00:11:43:4e:2d:cb
[4294674.248000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[4294674.248000] eth0: dma_rwctrl[76180000]
[4294674.802000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[4294676.302000] usbcore: registered new driver hiddev
[4294676.317000] input: USB HID v1.00 Mouse [413c:3010] on usb-0000:00:1d.3-1
[4294676.317000] usbcore: registered new driver usbhid
[4294676.317000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294676.662000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[4294676.662000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294676.666000] ACPI: Thermal Zone [THM] (50 C)
[4294676.898000] Attempting manual resume
[4294676.898000] swsusp: Suspend partition has wrong signature?
[4294676.911000] kjournald starting.  Commit interval 5 seconds
[4294676.911000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.063000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294680.589000] Adding 971892k swap on /dev/sda5.  Priority:-1 extents:1
[4294680.851000] EXT3 FS on sda4, internal journal
[4294687.210000] mice: PS/2 mouse device common for all mice
[4294687.756000] input: PS/2 Mouse on isa0060/serio1
[4294687.758000] input: AlpsPS/2 ALPS GlidePoint on isa0060/serio1
[4294688.321000] ts: Compaq touchscreen protocol output
[4294689.618000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294691.230000] kjournald starting.  Commit interval 5 seconds
[4294691.230000] EXT3 FS on sda6, internal journal
[4294691.230000] EXT3-fs: mounted filesystem with ordered data mode.
[4294691.237000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294691.296000] NTFS volume version 3.1.
[4294691.297000] kjournald starting.  Commit interval 5 seconds
[4294691.297000] EXT3 FS on sda2, internal journal
[4294691.297000] EXT3-fs: mounted filesystem with ordered data mode.
[4294692.741000] Linux agpgart interface v0.101 (c) Dave Jones
[4294692.747000] agpgart: Detected an Intel 915GM Chipset.
[4294692.777000] agpgart: AGP aperture is 256M @ 0x0
[4294692.840000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294692.843000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294692.843000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294692.913000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294692.913000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294693.164000] hw_random: cannot enable RNG, aborting
[4294693.307000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
[4294693.307000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294694.116000] intel8x0_measure_ac97_clock: measured 49491 usecs
[4294694.116000] intel8x0: clocking to 48000
[4294694.841000] Linux Kernel Card Services
[4294694.841000]   options:  [pci] [cardbus] [pm]
[4294694.850000] PCI: Enabling device 0000:03:01.0 (0000 -> 0002)
[4294694.850000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294694.850000] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0182]
[4294694.850000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294694.850000] Yenta: Routing CardBus interrupts to PCI
[4294694.850000] Yenta TI: socket 0000:03:01.0, mfunc 0x01111122, devctl 0x64
[4294695.071000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 19
[4294695.071000] Socket status: 30000006
[4294695.176000] ieee80211_crypt: registered algorithm 'NULL'
[4294695.179000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294695.179000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294695.186000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294695.186000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294695.189000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294695.189000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[4294695.776000] ipw2200: Radio Frequency Kill Switch is On:
[4294695.776000] Kill switch must be turned off for wireless networking to work.
[4294697.254000] Real Time Clock Driver v1.12
[4294697.299000] input: PC Speaker
[4294697.433000] parport: PnPBIOS parport detected.
[4294697.434000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294697.944000] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[4294697.944000] Uniform CD-ROM driver Revision: 3.20
[4294697.944000] Attached scsi CD-ROM sr0 at scsi1, channel 0, id 0, lun 0
[4294697.956000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
[4294697.957000] Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  type 5
[4294698.322000] NET: Registered protocol family 17
[4294700.260000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[4294700.260000] tg3: eth0: Flow control is on for TX and on for RX.
[4294706.656000] NET: Registered protocol family 10
[4294706.656000] Disabled Privacy Extensions on device c02eb280(lo)
[4294706.656000] IPv6 over IPv4 tunneling driver
[4294711.864000] ACPI: AC Adapter [AC] (on-line)
[4294712.189000] ACPI: Battery Slot [BAT0] (battery present)
[4294712.189000] ACPI: Battery Slot [BAT1] (battery absent)
[4294712.206000] ACPI: Lid Switch [LID]
[4294712.206000] ACPI: Power Button (CM) [PBTN]
[4294712.206000] ACPI: Sleep Button (CM) [SBTN]
[4294712.295000] ibm_acpi: ec object not found
[4294712.395000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294712.395000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294712.395000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[4294717.111000] eth0: no IPv6 routers present
[4294717.433000] lp0: using parport0 (interrupt-driven).
[4294719.720000] apm: BIOS not found.
[4294720.270000] cs: IO port probe 0x100-0x4ff: excluding 0x370-0x37f 0x3f0-0x3ff
[4294720.272000] cs: IO port probe 0xc00-0xcf7: clean.
[4294720.273000] cs: IO port probe 0xa00-0xaff: clean.
[4294720.685000] Bluetooth: Core ver 2.7
[4294720.685000] NET: Registered protocol family 31
[4294720.685000] Bluetooth: HCI device and connection manager initialized
[4294720.685000] Bluetooth: HCI socket layer initialized
[4294720.710000] Bluetooth: L2CAP ver 2.7
[4294720.710000] Bluetooth: L2CAP socket layer initialized
[4294720.788000] Bluetooth: RFCOMM ver 1.5
[4294720.788000] Bluetooth: RFCOMM socket layer initialized
[4294720.788000] Bluetooth: RFCOMM TTY layer initialized
[4294722.988000] atkbd.c: Unknown key pressed (translated set 2, code 0x86 on isa0060/serio0).
[4294722.988000] atkbd.c: Use 'setkeycodes e006 <keycode>' to make it known.
[4294723.175000] atkbd.c: Unknown key pressed (translated set 2, code 0x86 on isa0060/serio0).
[4294723.175000] atkbd.c: Use 'setkeycodes e006 <keycode>' to make it known.
[4294723.330000] atkbd.c: Unknown key pressed (translated set 2, code 0x86 on isa0060/serio0).
[4294723.330000] atkbd.c: Use 'setkeycodes e006 <keycode>' to make it known.

---

