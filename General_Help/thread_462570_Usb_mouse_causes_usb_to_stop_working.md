---
title: "Usb mouse causes usb to stop working"
date: 2007-06-02
forum: General Help
---

### Post by daveo5887 on 2007-06-02
I have tried this in both edgy and feisty.
I am running a thinkpad r52 laptop.
Pentium M 1.7 ghz
ATI Radeon mobility x300, tried using proprietary drivers and open source

Whenever using any usb mouse, it stops working after some amount of time, anywhere between 1 and 30 minutes usually. After this no usb device works. I've looked through similar posts, but none provide anything that fixes the problem. I've tried using the acpi=force irqpoll and all possible combinations of that. Here is my dmesg.

```

[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri May 18 23:39:08 UTC 2007 (Ubuntu 2.6.17-11.38-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fee0000 - 000000003fef5000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003fef5000 - 000000003ff00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 126MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 261856
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32480 pages, LIFO batch:7
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v002 IBM                                   ) @ 0x000f6bf0
[17179569.184000] ACPI: XSDT (v001 IBM    TP-76    0x00001180  LTP 0x00000000) @ 0x3fee7009
[17179569.184000] ACPI: FADT (v003 IBM    TP-76    0x00001180 IBM  0x00000001) @ 0x3fee7100
[17179569.184000] ACPI: SSDT (v001 IBM    TP-76    0x00001180 MSFT 0x0100000e) @ 0x3fee72b4
[17179569.184000] ACPI: ECDT (v001 IBM    TP-76    0x00001180 IBM  0x00000001) @ 0x3fef4dd8
[17179569.184000] ACPI: TCPA (v001 IBM    TP-76    0x00001180 PTL  0x00000001) @ 0x3fef4e2a
[17179569.184000] ACPI: MADT (v001 IBM    TP-76    0x00001180 IBM  0x00000001) @ 0x3fef4e5c
[17179569.184000] ACPI: MCFG (v001 IBM    TP-76    0x00001180 IBM  0x00000001) @ 0x3fef4eb6
[17179569.184000] ACPI: BOOT (v001 IBM    TP-76    0x00001180  LTP 0x00000001) @ 0x3fef4fd8
[17179569.184000] ACPI: DSDT (v001 IBM    TP-76    0x00001180 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1729.368 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.088000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.088000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.116000] Memory: 1028564k/1047424k available (1911k kernel code, 18104k reserved, 1073k data, 308k init, 129920k highmem)
[17179572.116000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.196000] Calibrating delay using timer specific routine.. 3463.24 BogoMIPS (lpj=6926499)
[17179572.196000] Security Framework v1.0.0 initialized
[17179572.196000] SELinux:  Disabled at boot.
[17179572.196000] Mount-cache hash table entries: 512
[17179572.196000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179572.196000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179572.196000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.196000] CPU: L2 cache: 2048K
[17179572.196000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000180 00000000 00000000
[17179572.196000] Checking 'hlt' instruction... OK.
[17179572.212000] SMP alternatives: switching to UP code
[17179572.212000] Freeing SMP alternatives: 16k freed
[17179572.212000] checking if image is initramfs... it is
[17179572.724000] Freeing initrd memory: 5326k freed
[17179572.724000] ACPI: Core revision 20060707
[17179572.724000] ACPI: Looking for DSDT ... not found!
[17179572.744000] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[17179572.744000] Total of 1 processors activated (3463.24 BogoMIPS).
[17179572.744000] ENABLING IO-APIC IRQs
[17179572.744000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.888000] Brought up 1 CPUs
[17179572.888000] migration_cost=0
[17179572.888000] NET: Registered protocol family 16
[17179572.888000] EISA bus registered
[17179572.888000] ACPI: bus type pci registered
[17179572.888000] PCI: Using MMCONFIG
[17179572.888000] Setting up standard PCI resources
[17179572.888000] ACPI: Found ECDT
[17179572.900000] ACPI: Interpreter enabled
[17179572.900000] ACPI: Using IOAPIC for interrupt routing
[17179572.900000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.900000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.900000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.900000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.900000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.904000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.904000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.904000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[17179572.904000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.904000] PCI: Probing PCI hardware (bus 00)
[17179572.908000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179572.908000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[17179572.908000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179572.908000] Boot video device is 0000:01:00.0
[17179572.908000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.908000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.912000] ACPI: Embedded Controller [EC] (gpe 28) interrupt mode.
[17179572.912000] ACPI: Power Resource [PUBS] (on)
[17179572.916000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179572.916000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[17179572.916000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[17179572.916000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179572.916000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.916000] pnp: PnP ACPI init
[17179572.924000] pnp: PnP ACPI: found 14 devices
[17179572.924000] PnPBIOS: Disabled by ACPI PNP
[17179572.924000] PCI: Using ACPI for IRQ routing
[17179572.924000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.924000] PCI: Bridge: 0000:00:01.0
[17179572.924000]   IO window: 3000-3fff
[17179572.924000]   MEM window: a8100000-a81fffff
[17179572.924000]   PREFETCH window: c0000000-c7ffffff
[17179572.924000] PCI: Bridge: 0000:00:1c.0
[17179572.924000]   IO window: disabled.
[17179572.924000]   MEM window: a8200000-a82fffff
[17179572.924000]   PREFETCH window: disabled.
[17179572.924000] PCI: Bridge: 0000:00:1c.2
[17179572.924000]   IO window: 4000-4fff
[17179572.924000]   MEM window: a8300000-a83fffff
[17179572.924000]   PREFETCH window: c8000000-c80fffff
[17179572.924000] PCI: Bus 5, cardbus bridge: 0000:04:00.0
[17179572.924000]   IO window: 00005000-000050ff
[17179572.924000]   IO window: 00005400-000054ff
[17179572.924000]   PREFETCH window: d0000000-d1ffffff
[17179572.924000]   MEM window: aa000000-abffffff
[17179572.924000] PCI: Bridge: 0000:00:1e.0
[17179572.924000]   IO window: 5000-8fff
[17179572.924000]   MEM window: a8400000-b7ffffff
[17179572.924000]   PREFETCH window: d0000000-d7ffffff
[17179572.924000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.924000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.924000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179572.924000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179572.924000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 185
[17179572.924000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179572.924000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.924000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.924000] NET: Registered protocol family 2
[17179572.964000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.964000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179572.964000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179572.964000] TCP: Hash tables configured (established 131072 bind 65536)
[17179572.964000] TCP reno registered
[17179572.964000] Simple Boot Flag at 0x35 set to 0x1
[17179572.964000] audit: initializing netlink socket (disabled)
[17179572.964000] audit(1180830514.964:1): initialized
[17179572.964000] highmem bounce pool size: 64 pages
[17179572.964000] VFS: Disk quotas dquot_6.5.1
[17179572.964000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.964000] Initializing Cryptographic API
[17179572.964000] io scheduler noop registered
[17179572.964000] io scheduler anticipatory registered
[17179572.964000] io scheduler deadline registered
[17179572.964000] io scheduler cfq registered (default)
[17179572.964000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.964000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.964000] assign_interrupt_mode Found MSI capability
[17179572.964000] Allocate Port Service[0000:00:01.0:pcie00]
[17179572.964000] Allocate Port Service[0000:00:01.0:pcie03]
[17179572.964000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179572.964000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179572.964000] assign_interrupt_mode Found MSI capability
[17179572.964000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179572.964000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179572.964000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179572.964000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 185
[17179572.964000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179572.964000] assign_interrupt_mode Found MSI capability
[17179572.964000] Allocate Port Service[0000:00:1c.2:pcie00]
[17179572.964000] Allocate Port Service[0000:00:1c.2:pcie02]
[17179572.964000] Allocate Port Service[0000:00:1c.2:pcie03]
[17179572.964000] isapnp: Scanning for PnP cards...
[17179573.320000] isapnp: No Plug & Play device found
[17179573.344000] Real Time Clock Driver v1.12ac
[17179573.344000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.344000] pnp: Device 00:0a activated.
[17179573.344000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[17179573.344000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 23 (level, low) -> IRQ 225
[17179573.344000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[17179573.344000] mice: PS/2 mouse device common for all mice
[17179573.344000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.344000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.344000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.344000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179573.356000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.356000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.356000] EISA: Probing bus 0 at eisa.0
[17179573.356000] Cannot allocate resource for EISA slot 1
[17179573.356000] Cannot allocate resource for EISA slot 2
[17179573.356000] Cannot allocate resource for EISA slot 3
[17179573.356000] Cannot allocate resource for EISA slot 4
[17179573.356000] Cannot allocate resource for EISA slot 5
[17179573.356000] Cannot allocate resource for EISA slot 6
[17179573.356000] Cannot allocate resource for EISA slot 7
[17179573.356000] Cannot allocate resource for EISA slot 8
[17179573.356000] EISA: Detected 0 cards.
[17179573.356000] TCP bic registered
[17179573.356000] NET: Registered protocol family 1
[17179573.356000] NET: Registered protocol family 8
[17179573.356000] NET: Registered protocol family 20
[17179573.356000] Using IPI No-Shortcut mode
[17179573.356000] ACPI: (supports S0 S3 S4 S5)
[17179573.356000] Freeing unused kernel memory: 308k freed
[17179573.416000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.528000] Capability LSM initialized
[17179574.556000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179574.556000] ACPI: Processor [CPU] (supports 8 throttling states)
[17179574.560000] ACPI: Thermal Zone [THM0] (64 C)
[17179574.840000] SCSI subsystem initialized
[17179574.840000] libata version 1.20 loaded.
[17179574.844000] ahci 0000:00:1f.2: version 1.2
[17179574.844000] ahci: probe of 0000:00:1f.2 failed with error -12
[17179574.844000] ata_piix 0000:00:1f.2: version 1.05
[17179574.844000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179574.844000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x18C0 irq 14
[17179575.024000] ata1: dev 0 cfg 49:2b00 82:346b 83:5b29 84:4003 85:3469 86:1a09 87:4003 88:203f
[17179575.024000] ata1: dev 0 ATA-6, max UDMA/100, 117210240 sectors: LBA
[17179575.024000] ata1(0): applying bridge limits
[17179575.048000] ata1: dev 0 configured for UDMA/100
[17179575.048000] scsi0 : ata_piix
[17179575.048000]   Vendor: ATA       Model: FUJITSU MHT2060A  Rev: 8431
[17179575.048000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179575.048000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x18C8 irq 15
[17179575.368000] ata2: dev 0 cfg 49:0f00 82:4210 83:4000 84:0000 85:0000 86:0000 87:0000 88:0407
[17179575.368000] ata2: dev 0 ATAPI, max UDMA/33
[17179575.532000] ata2: dev 0 configured for UDMA/33
[17179575.532000] scsi1 : ata_piix
[17179575.532000]   Vendor: TEAC      Model: DW-225            Rev: 2.2A
[17179575.532000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179575.552000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179575.552000] sda: Write Protect is off
[17179575.552000] sda: Mode Sense: 00 3a 00 00
[17179575.552000] SCSI device sda: drive cache: write back
[17179575.552000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179575.552000] sda: Write Protect is off
[17179575.552000] sda: Mode Sense: 00 3a 00 00
[17179575.552000] SCSI device sda: drive cache: write back
[17179575.552000]  sda: sda1 sda2 < sda5 >
[17179575.612000] sd 0:0:0:0: Attached scsi disk sda
[17179575.788000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179575.788000] ide0: ports already in use, skipping probe
[17179575.788000] ide1: I/O resource 0x170-0x177 not free.
[17179575.788000] ide1: ports already in use, skipping probe
[17179575.824000] usbcore: registered new driver usbfs
[17179575.824000] usbcore: registered new driver hub
[17179575.824000] USB Universal Host Controller Interface driver v3.0
[17179575.824000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179575.824000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179575.824000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179575.828000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179575.828000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x00001800
[17179575.828000] usb usb1: configuration #1 chosen from 1 choice
[17179575.828000] hub 1-0:1.0: USB hub found
[17179575.828000] hub 1-0:1.0: 2 ports detected
[17179575.880000] ieee1394: Initialized config rom entry `ip1394'
[17179575.932000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 233
[17179575.932000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.932000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.932000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179575.932000] uhci_hcd 0000:00:1d.1: irq 233, io base 0x00001820
[17179575.932000] usb usb2: configuration #1 chosen from 1 choice
[17179575.932000] hub 2-0:1.0: USB hub found
[17179575.932000] hub 2-0:1.0: 2 ports detected
[17179576.036000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 50
[17179576.036000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.036000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.036000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179576.036000] uhci_hcd 0000:00:1d.2: irq 50, io base 0x00001840
[17179576.036000] usb usb3: configuration #1 chosen from 1 choice
[17179576.036000] hub 3-0:1.0: USB hub found
[17179576.036000] hub 3-0:1.0: 2 ports detected
[17179576.140000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 58
[17179576.140000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179576.140000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179576.140000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179576.140000] uhci_hcd 0000:00:1d.3: irq 58, io base 0x00001860
[17179576.140000] usb usb4: configuration #1 chosen from 1 choice
[17179576.140000] hub 4-0:1.0: USB hub found
[17179576.140000] hub 4-0:1.0: 2 ports detected
[17179576.252000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 58
[17179576.252000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179576.252000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179576.252000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179576.252000] ehci_hcd 0000:00:1d.7: debug port 1
[17179576.252000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179576.252000] ehci_hcd 0000:00:1d.7: irq 58, io mem 0xa8000000
[17179576.256000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.256000] usb usb5: configuration #1 chosen from 1 choice
[17179576.256000] hub 5-0:1.0: USB hub found
[17179576.256000] hub 5-0:1.0: 8 ports detected
[17179576.360000] ACPI: PCI Interrupt 0000:04:00.1[B] -> GSI 17 (level, low) -> IRQ 233
[17179576.412000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[233]  MMIO=[b1000000-b10007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179576.468000] Attempting manual resume
[17179576.508000] kjournald starting.  Commit interval 5 seconds
[17179576.508000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.692000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae4053840116d]
[17179589.588000] input: PC Speaker as /class/input/input1
[17179589.612000] parport: PnPBIOS parport detected.
[17179589.612000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[17179589.656000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.780000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.820000] hw_random: RNG not detected
[17179590.120000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.136000] agpgart: Detected an Intel 915GM Chipset.
[17179590.152000] agpgart: AGP aperture is 256M @ 0x0
[17179590.216000] Floppy drive(s): fd0 is 1.44M
[17179590.232000] FDC 0 is a National Semiconductor PC87306
[17179590.424000] irda_init()
[17179590.424000] NET: Registered protocol family 23
[17179590.680000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179590.680000] Yenta: CardBus bridge found at 0000:04:00.0 [1014:0532]
[17179590.744000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179590.744000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[17179590.752000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[17179590.752000] Uniform CD-ROM driver Revision: 3.20
[17179590.752000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179590.820000] Yenta: ISA IRQ mask 0x0c38, PCI irq 169
[17179590.820000] Socket status: 30000006
[17179590.820000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x8fff
[17179590.820000] cs: IO port probe 0x5000-0x8fff: clean.
[17179590.824000] pcmcia: parent PCI bridge Memory window: 0xa8400000 - 0xb7ffffff
[17179590.824000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd7ffffff
[17179590.828000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 22 (level, low) -> IRQ 185
[17179590.828000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179590.852000] ieee80211_crypt: registered algorithm 'NULL'
[17179590.860000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179590.860000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179590.908000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179590.908000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179590.908000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179591.144000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[17179591.144000] serio: Synaptics pass-through port at isa0060/serio1/input0
[17179591.188000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179591.192000] pnp: Device 00:0c activated.
[17179591.192000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[17179591.192000] nsc-ircc, chip->init
[17179591.192000] nsc-ircc, Found chip at base=0x02e
[17179591.192000] nsc-ircc, driver loaded (Dag Brattli)
[17179591.192000] IrDA: Registered device irda0
[17179591.192000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[17179591.220000] cs: IO port probe 0x100-0x3af: excluding 0x370-0x377
[17179591.220000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[17179591.220000] cs: IO port probe 0x820-0x8ff: clean.
[17179591.220000] cs: IO port probe 0xc00-0xcf7: clean.
[17179591.224000] cs: IO port probe 0xa00-0xaff: clean.
[17179591.256000] ts: Compaq touchscreen protocol output
[17179591.648000] intel8x0_measure_ac97_clock: measured 55475 usecs
[17179591.648000] intel8x0: clocking to 48000
[17179591.648000] tg3.c:v3.59.1 (August 25, 2006)
[17179591.648000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179591.648000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179591.684000] eth0: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:0a:e4:c2:03:b9
[17179591.684000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[17179591.684000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[17179591.684000] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 21 (level, low) -> IRQ 66
[17179591.684000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[17179591.992000] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[17179592.288000] lp0: using parport0 (interrupt-driven).
[17179592.348000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179592.348000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179592.364000] NET: Registered protocol family 17
[17179592.372000] Adding 2409708k swap on /dev/disk/by-uuid/225fcb06-b013-485d-a393-2160e6b11427.  Priority:-1 extents:1 across:2409708k
[17179592.512000] EXT3 FS on sda1, internal journal
[17179597.124000] ieee80211_crypt: registered algorithm 'TKIP'
[17179622.572000] ACPI: AC Adapter [AC] (on-line)
[17179622.616000] ACPI: Battery Slot [BAT0] (battery present)
[17179622.632000] ACPI: Power Button (FF) [PWRF]
[17179622.632000] ACPI: Lid Switch [LID]
[17179622.632000] ACPI: Sleep Button (CM) [SLPB]
[17179622.664000] ACPI: ACPI Dock Station Driver 
[17179622.772000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179622.772000] ibm_acpi: http://ibm-acpi.sf.net/
[17179622.792000] pcc_acpi: loading...
[17179622.888000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179625.432000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179625.436000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[17179625.436000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179625.472000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179627.908000] IBM machine detected. Enabling interrupts during APM calls.
[17179627.908000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179627.908000] apm: overridden by ACPI.
[17179628.140000] mtrr: no more MTRRs available
[17179628.140000] mtrr: no more MTRRs available
[17179628.140000] mtrr: no more MTRRs available
[17179632.424000] Non-volatile memory driver v1.2
[17179632.520000] input: /usr/sbin/thinkpad-keys as /class/input/input3
[17179632.720000] Bluetooth: Core ver 2.8
[17179632.720000] NET: Registered protocol family 31
[17179632.720000] Bluetooth: HCI device and connection manager initialized
[17179632.720000] Bluetooth: HCI socket layer initialized
[17179632.744000] Bluetooth: L2CAP ver 2.8
[17179632.744000] Bluetooth: L2CAP socket layer initialized
[17179632.748000] Bluetooth: RFCOMM socket layer initialized
[17179632.748000] Bluetooth: RFCOMM TTY layer initialized
[17179632.748000] Bluetooth: RFCOMM ver 1.7
[17179996.968000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[17179997.144000] usb 2-2: configuration #1 chosen from 1 choice
[17179997.364000] usbcore: registered new driver hiddev
[17179997.384000] input: Logitech Logitech USB Optical Mouse as /class/input/input4
[17179997.384000] input: USB HID v1.11 Mouse [Logitech Logitech USB Optical Mouse] on usb-0000:00:1d.1-2
[17179997.384000] usbcore: registered new driver usbhid
[17179997.384000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17180023.144000] uhci_hcd 0000:00:1d.1: host controller process error, something bad happened!
[17180023.144000] uhci_hcd 0000:00:1d.1: host controller halted, very bad!
[17180023.144000] uhci_hcd 0000:00:1d.1: HC died; cleaning up
[17180023.144000] usb 2-2: USB disconnect, address 2

```

Thanks for any help.

---

### Post by skyhopper88 on 2007-06-03
I have the same problem, but don't know if the mouse is the initial cause and I haven't found a working solution yet.

---

### Post by honukele on 2007-06-07
Same problem with Toshiba Satellite M45-S169 and Memorex Scroll Wheel Mouse.  I have found that the scroll wheel seems to trigger the disconnect and loss of all USB services, especially when using Firefox.  No solution yet.

---

### Post by honukele on 2007-06-24
Solution: 1. uninstall Feisty 2. Install Dapper

BTW: I tried Mandriva 2007 and had the same problem.

No problem with Ubuntu Dapper.

Aloha,

Honukele

---

