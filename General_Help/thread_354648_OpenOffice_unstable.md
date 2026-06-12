---
title: "OpenOffice unstable"
date: 2007-02-06
forum: General Help
---

### Post by aweller on 2007-02-06
I have been using OpenOffice 2.0.4 from the Ubuntu repositories, and then 2.1 from the instructions here: [http://ubuntuforums.org/showthread.php?t=324872](http://ubuntuforums.org/showthread.php?t=324872)

It is really starting to drive me crazy that OpenOffice is so unstable. It just keeps crashing. I keep having to reboot no end of times, losing work in the process...

Is anyone else out there having a nightmare with OpenOffice? If so, have you solved it? How?

I would think that OpenOffice stability is vital for a GNU/Linux operating system like Ubuntu...

Thanks, Andy

---

### Post by gwpritch on 2007-02-06
I have been using openoffice for years with no stability problems what-so-ever.
Did you experience this with both versions or just when you upgraded? What system are you running it on? Are you running anything else at the same time? You say you are having to reboot...so is the whole system crashing or just oo. The more details of you problem the better.

---

### Post by aweller on 2007-02-06
I am running OpenOffice from an Edgy i386 installation. I have tried with only OpenOffice running, and with several other things (Firefox, etc).

Yep, I have been having issues with both versions, hence the update. (I prefer to install things from the repositories if possible.)

Thanks, Andy

---

### Post by Arup on 2007-02-06
Been a OO user in Windows, SuSE and now with Ubuntu Edgy, have written 100+ pages of journals, no issues here whatsoever.

---

### Post by gwpritch on 2007-02-06
How about your hardware setup...processor ram etc. oo is pretty heavy duty, although I've run it on an old laptop with 300MHz and 128 Meg Ram before. Sluggish but still pretty stable. Is this a total system lockup you are experiencing?

---

### Post by aweller on 2007-02-06
Yeh Arup, it's similar with me. I've been using OOo for ~5 years with little problems, apart from now. It's a total system lock-down with me. It has, however, been running for the last hour or so (a record) without a problem. It's been a most unproductive day... Anyway, here's a dmesg output for those that understand such things:

[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f6f0000 (usable)
[17179569.184000]  BIOS-e820: 000000001f6f0000 - 000000001f6fa000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001f6fa000 - 000000001f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 502MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6540
[17179569.184000] On node 0 totalpages: 128752
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 124656 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f65d0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x060400d0  LTP 0x00000000) @ 0x1f6f4d1f
[17179569.184000] ACPI: FADT (v001 IBM    THINKCEN 0x060400d0 PTL  0x00000001) @ 0x1f6f9e57
[17179569.184000] ACPI: TCPA (v001 IBM    THINKCEN 0x060400d0 PTL  0x00000001) @ 0x1f6f9ecb
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x060400d0  LTP 0x00000000) @ 0x1f6f9efd
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x060400d0  LTP 0x00000001) @ 0x1f6f9f65
[17179569.184000] ACPI: MCFG (v001 PTLTD         MCFG   0x060400d0  LTP 0x00000000) @ 0x1f6f9f8d
[17179569.184000] ACPI: SSDT (v001 PTLTD  ACPIHT   0x060400d0  LTP 0x00000001) @ 0x1f6f9fc9
[17179569.184000] ACPI: DSDT (v001    IBM THINKCEN 0x060400d0 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=012a2f40-8fe1-4cff-8f16-380cd9fbfd74 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 2993.010 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.788000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.788000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.796000] Memory: 500584k/515008k available (1910k kernel code, 13864k reserved, 1069k data, 308k init, 0k highmem)
[17179571.796000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.876000] Calibrating delay using timer specific routine.. 5992.79 BogoMIPS (lpj=11985587)
[17179571.876000] Security Framework v1.0.0 initialized
[17179571.876000] SELinux:  Disabled at boot.
[17179571.876000] Mount-cache hash table entries: 512
[17179571.876000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179571.876000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179571.876000] monitor/mwait feature present.
[17179571.876000] using mwait in idle threads.
[17179571.876000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179571.876000] CPU: L2 cache: 1024K
[17179571.876000] CPU: Hyper-Threading is disabled
[17179571.876000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000180 0000441d 00000000 00000000
[17179571.876000] Checking 'hlt' instruction... OK.
[17179571.892000] SMP alternatives: switching to UP code
[17179571.892000] checking if image is initramfs... it is
[17179572.336000] Freeing initrd memory: 5622k freed
[17179572.336000] ACPI: Core revision 20060707
[17179572.336000] ACPI: Looking for DSDT ... not found!
[17179572.344000] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[17179572.344000] SMP alternatives: switching to SMP code
[17179572.344000] Booting processor 1/1 eip 3000
[17179572.352000] Initializing CPU#1
[17179572.432000] Calibrating delay using timer specific routine.. 5985.11 BogoMIPS (lpj=11970234)
[17179572.432000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179572.432000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179572.432000] monitor/mwait feature present.
[17179572.432000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179572.432000] CPU: L2 cache: 1024K
[17179572.432000] CPU: Hyper-Threading is disabled
[17179572.432000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000180 0000441d 00000000 00000000
[17179572.432000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[17179572.432000] Total of 2 processors activated (11977.91 BogoMIPS).
[17179572.432000] ENABLING IO-APIC IRQs
[17179572.432000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.576000] checking TSC synchronization across 2 CPUs: passed.
[17179572.580000] Brought up 2 CPUs
[17179572.736000] migration_cost=4000
[17179572.736000] NET: Registered protocol family 16
[17179572.736000] EISA bus registered
[17179572.736000] ACPI: bus type pci registered
[17179572.736000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179572.736000] PCI: Not using MMCONFIG.
[17179572.736000] PCI: PCI BIOS revision 2.10 entry at 0xfd95d, last bus=10
[17179572.736000] PCI: Using configuration type 1
[17179572.736000] Setting up standard PCI resources
[17179572.756000] ACPI: Interpreter enabled
[17179572.756000] ACPI: Using IOAPIC for interrupt routing
[17179572.756000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.756000] PCI: Probing PCI hardware (bus 00)
[17179572.760000] Boot video device is 0000:00:02.0
[17179572.760000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179572.760000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[17179572.760000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179572.760000] PCI: Unable to handle 64-bit address for device 0000:02:00.0
[17179572.760000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.760000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.828000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[17179572.836000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[17179572.836000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179572.840000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11 12 14 15)
[17179572.840000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179572.840000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[17179572.840000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[17179572.840000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179572.840000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179572.840000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179572.844000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.844000] pnp: PnP ACPI init
[17179572.848000] pnp: PnP ACPI: found 13 devices
[17179572.848000] PnPBIOS: Disabled by ACPI PNP
[17179572.848000] PCI: Using ACPI for IRQ routing
[17179572.848000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.864000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179572.864000] PCI: Bridge: 0000:00:1c.0
[17179572.864000]   IO window: disabled.
[17179572.864000]   MEM window: d0000000-d00fffff
[17179572.864000]   PREFETCH window: disabled.
[17179572.864000] PCI: Bridge: 0000:00:1e.0
[17179572.864000]   IO window: disabled.
[17179572.864000]   MEM window: d0100000-d01fffff
[17179572.864000]   PREFETCH window: disabled.
[17179572.864000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179572.864000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179572.864000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.864000] NET: Registered protocol family 2
[17179572.904000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.904000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179572.904000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179572.904000] TCP: Hash tables configured (established 16384 bind 8192)
[17179572.904000] TCP reno registered
[17179572.904000] Simple Boot Flag at 0x35 set to 0x1
[17179572.904000] audit: initializing netlink socket (disabled)
[17179572.904000] audit(1170775530.904:1): initialized
[17179572.904000] VFS: Disk quotas dquot_6.5.1
[17179572.904000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.904000] Initializing Cryptographic API
[17179572.904000] io scheduler noop registered
[17179572.904000] io scheduler anticipatory registered
[17179572.904000] io scheduler deadline registered
[17179572.904000] io scheduler cfq registered (default)
[17179572.904000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179572.904000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179572.904000] assign_interrupt_mode Found MSI capability
[17179572.904000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179572.904000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179572.904000] isapnp: Scanning for PnP cards...
[17179573.256000] isapnp: No Plug & Play device found
[17179573.280000] Real Time Clock Driver v1.12ac
[17179573.280000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.280000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.284000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.284000] mice: PS/2 mouse device common for all mice
[17179573.284000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.284000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.284000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.284000] PNP: PS/2 Controller [PNP0303:KBC] at 0x60,0x64 irq 1
[17179573.284000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179573.284000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.284000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.292000] EISA: Probing bus 0 at eisa.0
[17179573.292000] Cannot allocate resource for EISA slot 1
[17179573.292000] Cannot allocate resource for EISA slot 3
[17179573.292000] EISA: Detected 0 cards.
[17179573.292000] TCP bic registered
[17179573.292000] NET: Registered protocol family 1
[17179573.292000] NET: Registered protocol family 8
[17179573.292000] NET: Registered protocol family 20
[17179573.292000] Starting balanced_irq
[17179573.292000] Using IPI No-Shortcut mode
[17179573.292000] ACPI: (supports S0 S1 S3 S4 S5)
[17179573.296000] Freeing unused kernel memory: 308k freed
[17179573.320000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.372000] Capability LSM initialized
[17179574.404000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179574.404000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179574.404000] ACPI: Thermal Zone [THM0] (60 C)
[17179574.756000] SCSI subsystem initialized
[17179574.760000] libata version 1.20 loaded.
[17179574.760000] ata_piix 0000:00:1f.2: version 1.05
[17179574.760000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 193
[17179574.760000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179574.760000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x34D0 irq 14
[17179574.924000] ata1: dev 0 cfg 49:2f00 82:346b 83:5b01 84:4003 85:3469 86:1901 87:4003 88:207f
[17179574.924000] ata1: dev 0 ATA-6, max UDMA/133, 156312576 sectors: LBA
[17179574.932000] ata1: dev 0 configured for UDMA/133
[17179574.932000] scsi0 : ata_piix
[17179574.932000]   Vendor: ATA       Model: WDC WD800JD-08JN  Rev: 06.0
[17179574.932000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179574.932000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x34D8 irq 15
[17179575.252000] ata2: dev 0 cfg 49:0b00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[17179575.252000] ata2: dev 0 ATAPI, max UDMA/33
[17179575.436000] ata2: dev 1 cfg 49:0f00 82:4210 83:4010 84:4000 85:0000 86:0000 87:4000 88:0407
[17179575.436000] ata2: dev 1 ATAPI, max UDMA/33
[17179575.436000] ata2(1): applying bridge limits
[17179575.600000] ata2: dev 0 configured for UDMA/33
[17179575.780000] ata2: dev 1 configured for UDMA/33
[17179575.780000] scsi1 : ata_piix
[17179575.780000]   Vendor: _NEC      Model: DVD_RW ND-3540A   Rev: 1.01
[17179575.780000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179575.780000]   Vendor: HL-DT-ST  Model: RW/DVD GCC-4482B  Rev: 1.00
[17179575.780000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179575.796000] SCSI device sda: 156312576 512-byte hdwr sectors (80032 MB)
[17179575.796000] sda: Write Protect is off
[17179575.796000] sda: Mode Sense: 00 3a 00 00
[17179575.800000] SCSI device sda: drive cache: write back
[17179575.804000] SCSI device sda: 156312576 512-byte hdwr sectors (80032 MB)
[17179575.808000] sda: Write Protect is off
[17179575.808000] sda: Mode Sense: 00 3a 00 00
[17179575.808000] SCSI device sda: drive cache: write back
[17179575.808000]  sda: sda1 sda2
[17179575.820000] sd 0:0:0:0: Attached scsi disk sda
[17179576.076000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179576.076000] ide0: ports already in use, skipping probe
[17179576.076000] ide1: I/O resource 0x170-0x177 not free.
[17179576.076000] ide1: ports already in use, skipping probe
[17179576.092000] usbcore: registered new driver usbfs
[17179576.092000] usbcore: registered new driver hub
[17179576.096000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 201
[17179576.096000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179576.096000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179576.096000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[17179576.096000] ehci_hcd 0000:00:1d.7: debug port 1
[17179576.096000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179576.096000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xd04c0000
[17179576.100000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.100000] usb usb1: configuration #1 chosen from 1 choice
[17179576.100000] hub 1-0:1.0: USB hub found
[17179576.100000] hub 1-0:1.0: 6 ports detected
[17179576.100000] USB Universal Host Controller Interface driver v3.0
[17179576.144000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179576.204000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> <6>ACPI: PCI Interrupt 0000:0a:00.2[C] -> GSI 23 (level, low) -> IRQ 201
[17179576.204000] GSI 18 (level, low) -> IRQ 209
[17179576.204000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.204000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.204000] ehci_hcd 0000:0a:00.2: EHCI Host Controller
[17179576.204000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[17179576.204000] ehci_hcd 0000:0a:00.2: new USB bus registered, assigned bus number 3
[17179576.204000] uhci_hcd 0000:00:1d.0: irq 201, io base 0x00003440
[17179576.204000] usb usb2: configuration #1 chosen from 1 choice
[17179576.204000] hub 2-0:1.0: USB hub found
[17179576.204000] hub 2-0:1.0: 2 ports detected
[17179576.228000] ehci_hcd 0000:0a:00.2: irq 209, io mem 0xd0104000
[17179576.228000] ehci_hcd 0000:0a:00.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.308000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179576.308000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179576.308000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179576.308000] usb usb3: configuration #1 chosen from 1 choice
[17179576.308000] hub 3-0:1.0: USB hub found
[17179576.308000] hub 3-0:1.0: 5 ports detected
[17179576.412000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[17179576.412000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x00003460
[17179576.412000] usb usb4: configuration #1 chosen from 1 choice
[17179576.412000] hub 4-0:1.0: USB hub found
[17179576.412000] hub 4-0:1.0: 2 ports detected
[17179576.516000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[17179576.516000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.516000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.516000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[17179576.516000] uhci_hcd 0000:00:1d.2: irq 209, io base 0x00003480
[17179576.516000] usb usb5: configuration #1 chosen from 1 choice
[17179576.516000] hub 5-0:1.0: USB hub found
[17179576.516000] hub 5-0:1.0: 2 ports detected
[17179576.620000] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 20 (level, low) -> IRQ 217
[17179576.620000] ohci_hcd 0000:0a:00.0: OHCI Host Controller
[17179576.620000] ohci_hcd 0000:0a:00.0: new USB bus registered, assigned bus number 6
[17179576.620000] ohci_hcd 0000:0a:00.0: irq 217, io mem 0xd0100000
[17179576.628000] usb 1-4: new high speed USB device using ehci_hcd and address 3
[17179576.704000] usb usb6: configuration #1 chosen from 1 choice
[17179576.704000] hub 6-0:1.0: USB hub found
[17179576.704000] hub 6-0:1.0: 3 ports detected
[17179576.764000] usb 1-4: configuration #1 chosen from 1 choice
[17179576.808000] ACPI: PCI Interrupt 0000:0a:00.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179576.808000] ohci_hcd 0000:0a:00.1: OHCI Host Controller
[17179576.808000] ohci_hcd 0000:0a:00.1: new USB bus registered, assigned bus number 7
[17179576.808000] ohci_hcd 0000:0a:00.1: irq 193, io mem 0xd0101000
[17179576.896000] usb usb7: configuration #1 chosen from 1 choice
[17179576.896000] hub 7-0:1.0: USB hub found
[17179576.896000] hub 7-0:1.0: 2 ports detected
[17179577.004000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[17179577.160000] usb 4-1: configuration #1 chosen from 1 choice
[17179577.292000] usbcore: registered new driver libusual
[17179577.292000] usbcore: registered new driver hiddev
[17179577.296000] Initializing USB Mass Storage driver...
[17179577.296000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179577.296000] usb-storage: device found at 3
[17179577.296000] usb-storage: waiting for device to settle before scanning
[17179577.308000] input: HID 04b3:310b as /class/input/input1
[17179577.308000] input: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:1d.1-1
[17179577.308000] usbcore: registered new driver usbhid
[17179577.308000] usbcore: registered new driver usb-storage
[17179577.308000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179577.308000] USB Mass Storage support registered.
[17179582.296000] usb-storage: device scan complete
[17179582.296000]   Vendor: WDC WD40  Model: 0UE-00HCT0        Rev: 0000
[17179582.296000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179582.300000] SCSI device sdb: 78140160 512-byte hdwr sectors (40008 MB)
[17179582.300000] sdb: Write Protect is off
[17179582.300000] sdb: Mode Sense: 27 00 00 00
[17179582.300000] sdb: assuming drive cache: write through
[17179582.300000] SCSI device sdb: 78140160 512-byte hdwr sectors (40008 MB)
[17179582.300000] sdb: Write Protect is off
[17179582.300000] sdb: Mode Sense: 27 00 00 00
[17179582.300000] sdb: assuming drive cache: write through
[17179582.300000]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 >
[17179582.400000] sd 2:0:0:0: Attached scsi disk sdb
[17179582.776000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179582.776000] EXT3-fs: write access will be enabled during recovery.
[17179585.248000] kjournald starting.  Commit interval 5 seconds
[17179585.248000] EXT3-fs: sdb1: orphan cleanup on readonly fs
[17179585.248000] ext3_orphan_cleanup: deleting unreferenced inode 16257
[17179585.248000] ext3_orphan_cleanup: deleting unreferenced inode 16259
[17179585.248000] ext3_orphan_cleanup: deleting unreferenced inode 16258
[17179585.248000] ext3_orphan_cleanup: deleting unreferenced inode 16233
[17179585.248000] ext3_orphan_cleanup: deleting unreferenced inode 16232
[17179585.248000] ext3_orphan_cleanup: deleting unreferenced inode 16231
[17179585.248000] EXT3-fs: sdb1: 6 orphan inodes deleted
[17179585.248000] EXT3-fs: recovery complete.
[17179585.276000] EXT3-fs: mounted filesystem with ordered data mode.
[17179594.792000] Floppy drive(s): fd0 is 1.44M
[17179594.812000] FDC 0 is a post-1991 82077
[17179594.860000] hw_random: RNG not detected
[17179594.892000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179594.944000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179594.976000] Linux agpgart interface v0.101 (c) Dave Jones
[17179595.000000] agpgart: Detected an Intel 915G Chipset.
[17179595.000000] agpgart: Detected 7932K stolen memory.
[17179595.016000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179595.040000] pnp: Device 00:08 disabled.
[17179595.040000] parport_pc: probe of 00:08 failed with error -22
[17179595.208000] input: PC Speaker as /class/input/input2
[17179595.508000] tg3.c:v3.59.1 (August 25, 2006)
[17179595.508000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 225
[17179595.508000] tg3: Cannot find proper PCI device base address, aborting.
[17179595.508000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17179596.172000] ACPI: PCI Interrupt 0000:0a:01.0[A] -> GSI 19 (level, low) -> IRQ 193
[17179596.172000] rt2500 1.1.0 BETA4 2006/06/18 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[17179596.240000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179596.240000]  1:0:0:0: Attached scsi generic sg1 type 5
[17179596.240000]  1:0:1:0: Attached scsi generic sg2 type 5
[17179596.240000] sd 2:0:0:0: Attached scsi generic sg3 type 0
[17179596.352000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[17179596.352000] rt2500 EEPROM:  9  9  9  9  9  9  9  9  9  9  9  9  9  9  dBm Maximum
[17179596.376000] ts: Compaq touchscreen protocol output
[17179596.396000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 169
[17179596.396000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179596.396000] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[17179596.396000] Uniform CD-ROM driver Revision: 3.20
[17179596.396000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179596.536000] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[17179596.536000] sr 1:0:1:0: Attached scsi CD-ROM sr1
[17179596.716000] intel8x0_measure_ac97_clock: measured 55843 usecs
[17179596.716000] intel8x0: clocking to 48000
[17179597.036000] lp: driver loaded but no devices found
[17179597.108000] ieee1394: Initialized config rom entry `ip1394'
[17179597.112000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179597.112000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179597.316000] EXT3 FS on sdb1, internal journal
[17179597.412000] NET: Registered protocol family 17
[17179603.236000] NET: Registered protocol family 10
[17179603.236000] lo: Disabled Privacy Extensions
[17179603.236000] IPv6 over IPv4 tunneling driver
[17179608.860000] kjournald starting.  Commit interval 5 seconds
[17179608.868000] EXT3 FS on sdb6, internal journal
[17179608.868000] EXT3-fs: mounted filesystem with ordered data mode.
[17179609.852000] ACPI: Power Button (FF) [PWRF]
[17179609.852000] ACPI: Power Button (CM) [PWRB]
[17179609.996000] ibm_acpi: ec object not found
[17179610.040000] pcc_acpi: loading...
[17179613.368000] ra0: no IPv6 routers present
[17179613.384000] [drm] Initialized drm 1.0.1 20051102
[17179613.396000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 225
[17179613.396000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179614.216000] IBM machine detected. Enabling interrupts during APM calls.
[17179614.216000] apm: BIOS not found.
[17179618.124000] Non-volatile memory driver v1.2
[17179618.140000] input: /usr/sbin/thinkpad-keys as /class/input/input3
[17179620.624000] Bluetooth: Core ver 2.8
[17179620.624000] NET: Registered protocol family 31
[17179620.624000] Bluetooth: HCI device and connection manager initialized
[17179620.624000] Bluetooth: HCI socket layer initialized
[17179620.684000] Bluetooth: L2CAP ver 2.8
[17179620.684000] Bluetooth: L2CAP socket layer initialized
[17179620.764000] Bluetooth: RFCOMM socket layer initialized
[17179620.764000] Bluetooth: RFCOMM TTY layer initialized
[17179620.764000] Bluetooth: RFCOMM ver 1.7
[17179640.264000] kjournald starting.  Commit interval 5 seconds
[17179640.264000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17179640.404000] EXT3 FS on sdb2, internal journal
[17179640.404000] EXT3-fs: recovery complete.
[17179640.592000] EXT3-fs: mounted filesystem with ordered data mode.
[17183593.748000] usb 1-1: new high speed USB device using ehci_hcd and address 4
[17183593.880000] usb 1-1: configuration #1 chosen from 1 choice
[17183593.880000] scsi3 : SCSI emulation for USB Mass Storage devices
[17183593.880000] usb-storage: device found at 4
[17183593.880000] usb-storage: waiting for device to settle before scanning
[17183598.880000] usb-storage: device scan complete
[17183598.880000]   Vendor: WDC       Model: WD2500JB-00REA0   Rev: 20.0
[17183598.880000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17183598.884000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[17183598.884000] sdc: Write Protect is off
[17183598.884000] sdc: Mode Sense: 53 00 00 08
[17183598.884000] sdc: assuming drive cache: write through
[17183598.884000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[17183598.884000] sdc: Write Protect is off
[17183598.884000] sdc: Mode Sense: 53 00 00 08
[17183598.884000] sdc: assuming drive cache: write through
[17183598.884000]  sdc: sdc1 sdc2
[17183598.892000] sd 3:0:0:0: Attached scsi disk sdc
[17183598.892000] sd 3:0:0:0: Attached scsi generic sg4 type 0
[17183600.016000] kjournald starting.  Commit interval 5 seconds
[17183600.016000] EXT3 FS on sdc1, internal journal
[17183600.016000] EXT3-fs: recovery complete.
[17183600.016000] EXT3-fs: mounted filesystem with ordered data mode.
[17183600.220000] kjournald starting.  Commit interval 5 seconds
[17183600.220000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17183600.220000] EXT3 FS on sdc2, internal journal
[17183600.220000] EXT3-fs: recovery complete.
[17183600.220000] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by aweller on 2007-02-06
Crashed again... It seems as though it may an Impress thing. No problems if I run just Writer - as soon as I open an Impress presentation - bang - it crashes. This time though only OOo crashed. The PC is still running.

Cheers, Andy

---

### Post by gwpritch on 2007-02-06
Have you had any lockups that didn't involve openoffice? Did this coincide with a kernel upgrade by any chance? There have been quite a few reports on this forum of lockups that seem to be related to the -generic kernel. I have been having some myself, although they seem to centre around vmware which is also pretty resource intensive. 
There doesn't seem to have been any concrete answer as to why this is happening. Some folks have found relief by switching to the i386 kernel.

---

### Post by aweller on 2007-02-06
It always seem to be an OOo thing, I think...

---

