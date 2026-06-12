---
title: "Sporadic freezing on Ubuntu Restart"
date: 2007-01-08
forum: General Help
---

### Post by Gobboman123 on 2007-01-08
I'm currently running Ubuntu Edgy on my desktop computer.  Just recently I've been having trouble when I go to restart.  The little loadbar will appear and unload down to about 1/4 where it will freeze.  I can sit there 10 minutes without seeing any change... the computer doesn't restart... but then I try it again some other time and it restarts fine.  Both situations have happened even directly after loading (without opening any other programs) when I go to restart to see if it happens again.

1.  Does anybody have experience with this problem?
2.  How can I see a verbose output of what's going on during restart instead of seeing the pretty Ubuntu Logo and loadbar?

](*,)

---

### Post by doobit on 2007-01-08
> **Gobboman123 said:**
> I'm currently running Ubuntu Edgy on my desktop computer.  Just recently I've been having trouble when I go to restart.  The little loadbar will appear and unload down to about 1/4 where it will freeze.  I can sit there 10 minutes without seeing any change... the computer doesn't restart... but then I try it again some other time and it restarts fine.  Both situations have happened even directly after loading (without opening any other programs) when I go to restart to see if it happens again.

1.  Does anybody have experience with this problem?
2.  How can I see a verbose output of what's going on during restart instead of seeing the pretty Ubuntu Logo and loadbar?

](*,)

It may be having trouble loading a driver for some piece of hardware. The next time you are able to get to the desktop (or you can ht Esc when you boot and choose to boot in recover mode to go directly into a terminal) , open a terminal and edit your /boot/grub/menu.lst file with nano or gedit in sudoer mode. Remove the word "quiet" from the linux boot line. that way, the next time you boot up you will be able to see where it's stalling. Also, before you reboot after editing the grub menu.lst, run dmesg in the terminal. That will give you a list of what's being loaded up when you boot. If you can't find anything strange, then copy it and paste here for us to look at it.

---

### Post by glendavee on 2007-01-08
doobit - Sorry to butt in , but I've been having a similar problem with Ubuntu Edgy. Splash screen hangs for about 90 secs before resuming - annoying but not fatal. I edited /boot/grub/menu.lst as you suggested. The delay is at the following lines:
Configuring network interfaces
Reconfiguring network interfaces

I'm using a wireless USB dongle with a driver enabled by ndiswrapper.
For what its worth, here's the output of dmesg :

[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 1020004k/1038880k available (1910k kernel code, 18064k reserved, 1069k data, 308k init, 121376k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 2992.629 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 5990.58 BogoMIPS (lpj=11981172)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.268000] CPU: L2 cache: 2048K
[17179569.268000] CPU: Hyper-Threading is disabled
[17179569.268000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000649d 00000000 00000000
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179569.708000] Freeing initrd memory: 5323k freed
[17179569.708000] ACPI: Core revision 20060707
[17179569.708000] ACPI: Looking for DSDT ... not found!
[17179569.740000] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[17179569.740000] SMP alternatives: switching to SMP code
[17179569.740000] Booting processor 1/1 eip 3000
[17179569.752000] Initializing CPU#1
[17179569.832000] Calibrating delay using timer specific routine.. 5984.98 BogoMIPS (lpj=11969962)
[17179569.832000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179569.832000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179569.832000] monitor/mwait feature present.
[17179569.832000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.832000] CPU: L2 cache: 2048K
[17179569.832000] CPU: Hyper-Threading is disabled
[17179569.832000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000649d 00000000 00000000
[17179569.832000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[17179569.832000] Total of 2 processors activated (11975.56 BogoMIPS).
[17179569.832000] ENABLING IO-APIC IRQs
[17179569.832000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179569.980000] checking TSC synchronization across 2 CPUs: passed.
[17179569.984000] Brought up 2 CPUs
[17179570.060000] migration_cost=4000
[17179570.060000] NET: Registered protocol family 16
[17179570.060000] EISA bus registered
[17179570.060000] ACPI: bus type pci registered
[17179570.060000] PCI: Using MMCONFIG
[17179570.060000] Setting up standard PCI resources
[17179570.088000] ACPI: Interpreter enabled
[17179570.088000] ACPI: Using IOAPIC for interrupt routing
[17179570.092000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.092000] PCI: Probing PCI hardware (bus 00)
[17179570.092000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.112000] Boot video device is 0000:00:02.0
[17179570.112000] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[17179570.112000] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[17179570.112000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.112000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.112000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.680000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179570.688000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[17179570.692000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI3._PRT]
[17179570.728000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179570.732000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179570.732000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[17179570.732000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[17179570.732000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179570.736000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179570.736000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[17179570.736000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
[17179570.736000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.736000] pnp: PnP ACPI init
[17179570.768000] pnp: PnP ACPI: found 8 devices
[17179570.768000] PnPBIOS: Disabled by ACPI PNP
[17179570.768000] PCI: Using ACPI for IRQ routing
[17179570.768000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.780000] pnp: 00:01: ioport range 0x800-0x85f could not be reserved
[17179570.780000] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[17179570.780000] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[17179570.780000] pnp: 00:07: ioport range 0x100-0x1fe has been reserved
[17179570.780000] pnp: 00:07: ioport range 0x200-0x277 has been reserved
[17179570.780000] pnp: 00:07: ioport range 0x280-0x2e7 has been reserved
[17179570.780000] pnp: 00:07: ioport range 0x2e8-0x2ef has been reserved
[17179570.780000] pnp: 00:07: ioport range 0x2f0-0x2f7 has been reserved
[17179570.780000] pnp: 00:07: ioport range 0x2f8-0x2ff has been reserved
[17179570.780000] pnp: 00:07: ioport range 0x300-0x377 has been reserved
[17179570.780000] pnp: 00:07: ioport range 0x380-0x3bb has been reserved
[17179570.784000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.784000] PCI: Bridge: 0000:00:1c.0
[17179570.784000]   IO window: disabled.
[17179570.784000]   MEM window: dfe00000-dfefffff
[17179570.784000]   PREFETCH window: disabled.
[17179570.784000] PCI: Bridge: 0000:00:1c.1
[17179570.784000]   IO window: disabled.
[17179570.784000]   MEM window: dfd00000-dfdfffff
[17179570.784000]   PREFETCH window: disabled.
[17179570.784000] PCI: Bridge: 0000:00:1e.0
[17179570.784000]   IO window: d000-dfff
[17179570.784000]   MEM window: dfc00000-dfcfffff
[17179570.784000]   PREFETCH window: disabled.
[17179570.784000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.784000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.784000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179570.784000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.784000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.784000] NET: Registered protocol family 2
[17179570.832000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.832000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179570.832000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.832000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.832000] TCP reno registered
[17179570.832000] Simple Boot Flag at 0x7a set to 0x1
[17179570.832000] audit: initializing netlink socket (disabled)
[17179570.832000] audit(1168288803.832:1): initialized
[17179570.832000] highmem bounce pool size: 64 pages
[17179570.832000] VFS: Disk quotas dquot_6.5.1
[17179570.832000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.832000] Initializing Cryptographic API
[17179570.832000] io scheduler noop registered
[17179570.832000] io scheduler anticipatory registered
[17179570.832000] io scheduler deadline registered
[17179570.832000] io scheduler cfq registered (default)
[17179570.848000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.848000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.848000] assign_interrupt_mode Found MSI capability
[17179570.848000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179570.848000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179570.848000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179570.848000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179570.848000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.848000] assign_interrupt_mode Found MSI capability
[17179570.848000] Allocate Port Service[0000:00:1c.1:pcie00]
[17179570.848000] Allocate Port Service[0000:00:1c.1:pcie03]
[17179570.848000] isapnp: Scanning for PnP cards...
[17179571.200000] isapnp: No Plug & Play device found
[17179571.228000] Real Time Clock Driver v1.12ac
[17179571.228000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.228000] mice: PS/2 mouse device common for all mice
[17179571.228000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.228000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.228000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.228000] PNP: No PS/2 controller found. Probing ports directly.
[17179571.748000] i8042.c: Can't read CTR while initializing i8042.
[17179571.748000] EISA: Probing bus 0 at eisa.0
[17179571.748000] Cannot allocate resource for EISA slot 2
[17179571.748000] Cannot allocate resource for EISA slot 5
[17179571.748000] Cannot allocate resource for EISA slot 6
[17179571.748000] EISA: Detected 0 cards.
[17179571.748000] TCP bic registered
[17179571.748000] NET: Registered protocol family 1
[17179571.748000] NET: Registered protocol family 8
[17179571.752000] NET: Registered protocol family 20
[17179571.752000] Starting balanced_irq
[17179571.752000] Using IPI No-Shortcut mode
[17179571.752000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.752000] Freeing unused kernel memory: 308k freed
[17179572.828000] Capability LSM initialized
[17179573.260000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179573.260000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.260000] ICH6: chipset revision 4
[17179573.260000] ICH6: not 100% native mode: will probe irqs later
[17179573.260000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179573.260000] Probing IDE interface ide0...
[17179573.996000] hda: PHILIPS DVD+/-RW DVD8701, ATAPI CD/DVD-ROM drive
[17179574.668000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.680000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.680000] Uniform CD-ROM driver Revision: 3.20
[17179574.772000] SCSI subsystem initialized
[17179574.772000] libata version 1.20 loaded.
[17179574.776000] ahci 0000:00:1f.2: version 1.2
[17179574.776000] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 209
[17179579.012000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179579.012000] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl IDE mode
[17179579.012000] ahci 0000:00:1f.2: flags: 64bit ncq pm led slum part 
[17179579.012000] ata1: SATA max UDMA/133 cmd 0xF883AD00 ctl 0x0 bmdma 0x0 irq 209
[17179579.012000] ata2: SATA max UDMA/133 cmd 0xF883AD80 ctl 0x0 bmdma 0x0 irq 209
[17179579.012000] ata3: SATA max UDMA/133 cmd 0xF883AE00 ctl 0x0 bmdma 0x0 irq 209
[17179579.012000] ata4: SATA max UDMA/133 cmd 0xF883AE80 ctl 0x0 bmdma 0x0 irq 209
[17179579.388000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179579.388000] ata1: dev 0 cfg 49:2f00 82:346b 83:7701 84:4003 85:3469 86:3401 87:4003 88:207f
[17179579.388000] ata1: dev 0 ATA-7, max UDMA/133, 312500000 sectors: LBA48
[17179579.388000] ata1: dev 0 configured for UDMA/133
[17179579.388000] scsi0 : ahci
[17179579.592000] ata2: SATA link down (SStatus 0)
[17179579.592000] scsi1 : ahci
[17179579.968000] ata3: SATA link up 1.5 Gbps (SStatus 113)
[17179579.968000] ata3: dev 0 cfg 49:2f00 82:746b 83:7f01 84:4023 85:7469 86:bc01 87:4023 88:20ff
[17179579.968000] ata3: dev 0 ATA-7, max UDMA7, 488397168 sectors: LBA48
[17179580.000000] ata3: dev 0 configured for UDMA/133
[17179580.000000] scsi2 : ahci
[17179580.204000] ata4: SATA link down (SStatus 0)
[17179580.204000] scsi3 : ahci
[17179580.204000]   Vendor: ATA       Model: ST3160828AS       Rev: 8.03
[17179580.204000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179580.204000]   Vendor: ATA       Model: SAMSUNG SP2504C   Rev: VT10
[17179580.204000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179580.212000] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[17179580.212000] sda: Write Protect is off
[17179580.212000] sda: Mode Sense: 00 3a 00 00
[17179580.212000] SCSI device sda: drive cache: write back
[17179580.212000] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[17179580.212000] sda: Write Protect is off
[17179580.216000] sda: Mode Sense: 00 3a 00 00
[17179580.216000] SCSI device sda: drive cache: write back
[17179580.216000]  sda: sda1 sda2 sda3
[17179580.236000] sd 0:0:0:0: Attached scsi disk sda
[17179580.236000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[17179580.236000] sdb: Write Protect is off
[17179580.236000] sdb: Mode Sense: 00 3a 00 00
[17179580.236000] SCSI device sdb: drive cache: write back
[17179580.236000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[17179580.236000] sdb: Write Protect is off
[17179580.236000] sdb: Mode Sense: 00 3a 00 00
[17179580.236000] SCSI device sdb: drive cache: write back
[17179580.236000]  sdb: sdb1 sdb2 < sdb5 >
[17179580.264000] sd 2:0:0:0: Attached scsi disk sdb
[17179580.540000] Probing IDE interface ide1...
[17179580.600000] usbcore: registered new driver usbfs
[17179580.600000] usbcore: registered new driver hub
[17179580.604000] USB Universal Host Controller Interface driver v3.0
[17179580.604000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 217
[17179580.604000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179580.604000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179580.604000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179580.604000] uhci_hcd 0000:00:1d.0: irq 217, io base 0x0000ff80
[17179580.604000] usb usb1: configuration #1 chosen from 1 choice
[17179580.604000] hub 1-0:1.0: USB hub found
[17179580.604000] hub 1-0:1.0: 2 ports detected
[17179580.616000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179580.708000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 225
[17179580.708000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179580.708000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179580.708000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179580.708000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x0000ff60
[17179580.708000] usb usb2: configuration #1 chosen from 1 choice
[17179580.708000] hub 2-0:1.0: USB hub found
[17179580.708000] hub 2-0:1.0: 2 ports detected
[17179580.812000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 233
[17179580.812000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179580.812000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179580.812000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179580.812000] uhci_hcd 0000:00:1d.2: irq 233, io base 0x0000ff40
[17179580.812000] usb usb3: configuration #1 chosen from 1 choice
[17179580.812000] hub 3-0:1.0: USB hub found
[17179580.812000] hub 3-0:1.0: 2 ports detected
[17179580.916000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 50
[17179580.916000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179580.916000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179580.916000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179580.916000] uhci_hcd 0000:00:1d.3: irq 50, io base 0x0000ff20
[17179580.916000] usb usb4: configuration #1 chosen from 1 choice
[17179580.916000] hub 4-0:1.0: USB hub found
[17179580.916000] hub 4-0:1.0: 2 ports detected
[17179580.948000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179581.020000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179581.020000] ohci_hcd 0000:03:01.0: OHCI Host Controller
[17179581.020000] ohci_hcd 0000:03:01.0: new USB bus registered, assigned bus number 5
[17179581.020000] ohci_hcd 0000:03:01.0: irq 177, io mem 0xdfced000
[17179581.020000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 217
[17179581.020000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179581.020000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179581.020000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 6
[17179581.020000] ehci_hcd 0000:00:1d.7: debug port 1
[17179581.020000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179581.020000] ehci_hcd 0000:00:1d.7: irq 217, io mem 0xffa80800
[17179581.024000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179581.024000] usb usb6: configuration #1 chosen from 1 choice
[17179581.024000] hub 6-0:1.0: USB hub found
[17179581.024000] hub 6-0:1.0: 8 ports detected
[17179581.128000] usb usb5: configuration #1 chosen from 1 choice
[17179581.128000] hub 5-0:1.0: USB hub found
[17179581.128000] hub 5-0:1.0: 3 ports detected
[17179581.232000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 233
[17179581.232000] ohci_hcd 0000:03:01.1: OHCI Host Controller
[17179581.232000] ohci_hcd 0000:03:01.1: new USB bus registered, assigned bus number 7
[17179581.232000] ohci_hcd 0000:03:01.1: irq 233, io mem 0xdfcee000
[17179581.316000] usb usb7: configuration #1 chosen from 1 choice
[17179581.316000] hub 7-0:1.0: USB hub found
[17179581.316000] hub 7-0:1.0: 2 ports detected
[17179581.420000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 19 (level, low) -> IRQ 58
[17179581.420000] ehci_hcd 0000:03:01.2: EHCI Host Controller
[17179581.420000] ehci_hcd 0000:03:01.2: new USB bus registered, assigned bus number 8
[17179581.444000] ehci_hcd 0000:03:01.2: irq 58, io mem 0xdfcecf00
[17179581.444000] ehci_hcd 0000:03:01.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179581.444000] usb usb8: configuration #1 chosen from 1 choice
[17179581.444000] hub 8-0:1.0: USB hub found
[17179581.444000] hub 8-0:1.0: 5 ports detected
[17179581.480000] usb 1-1: device not accepting address 2, error -71
[17179581.644000] Attempting manual resume
[17179581.680000] kjournald starting.  Commit interval 5 seconds
[17179581.680000] EXT3-fs: mounted filesystem with ordered data mode.
[17179582.784000] usb 6-3: new high speed USB device using ehci_hcd and address 4
[17179583.168000] usb 6-3: configuration #1 chosen from 1 choice
[17179583.776000] usb 6-7: new high speed USB device using ehci_hcd and address 7
[17179583.984000] usb 6-7: configuration #1 chosen from 1 choice
[17179584.536000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179584.712000] usb 1-1: configuration #1 chosen from 1 choice
[17179584.956000] usb 1-2: new low speed USB device using uhci_hcd and address 5
[17179585.136000] usb 1-2: configuration #1 chosen from 1 choice
[17179585.392000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179585.580000] usb 2-2: configuration #1 chosen from 1 choice
[17179585.824000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[17179586.256000] usb 3-2: configuration #1 chosen from 1 choice
[17179586.260000] ohci_hcd 0000:03:01.0: wakeup
[17179586.644000] usb 5-3: new full speed USB device using ohci_hcd and address 2
[17179586.868000] usb 5-3: configuration #1 chosen from 1 choice
[17179588.596000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.596000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.796000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.836000] input: PC Speaker as /class/input/input0
[17179588.840000] agpgart: Detected an Intel 915G Chipset.
[17179588.840000] agpgart: Detected 7932K stolen memory.
[17179588.856000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179588.916000] hw_random: RNG not detected
[17179589.212000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.212000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179589.248000] usbcore: registered new driver hiddev
[17179589.264000] input: Dell Dell USB Mouse as /class/input/input1
[17179589.264000] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.0-1
[17179589.280000] input: Dell Dell USB Keyboard as /class/input/input2
[17179589.280000] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-2
[17179589.280000] usbcore: registered new driver usbhid
[17179589.280000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.448000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179589.448000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179589.572000] usbcore: registered new driver libusual
[17179589.664000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179589.664000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[17179589.684000] ts: Compaq touchscreen protocol output
[17179589.696000] ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 20 (level, low) -> IRQ 209
[17179589.724000] e100: eth0: e100_probe: addr 0xdfcef000, irq 209, MAC addr 00:13:20:AC:74:FA
[17179589.724000] Initializing USB Mass Storage driver...
[17179589.724000] scsi4 : SCSI emulation for USB Mass Storage devices
[17179589.724000] usb-storage: device found at 7
[17179589.724000] usb-storage: waiting for device to settle before scanning
[17179589.724000] usbcore: registered new driver usb-storage
[17179589.724000] USB Mass Storage support registered.
[17179589.784000] Bluetooth: Core ver 2.8
[17179589.784000] NET: Registered protocol family 31
[17179589.784000] Bluetooth: HCI device and connection manager initialized
[17179589.784000] Bluetooth: HCI socket layer initialized
[17179589.852000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x413C pid 0x5008
[17179589.852000] usbcore: registered new driver usblp
[17179589.852000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179589.872000] Bluetooth: HCI USB driver ver 2.9
[17179589.872000] usbcore: registered new driver hci_usb
[17179590.208000] lp: driver loaded but no devices found
[17179590.232000] ndiswrapper version 1.31 loaded (preempt=no,smp=yes)
[17179590.400000] usb 6-3: reset high speed USB device using ehci_hcd and address 4
[17179590.608000] ndiswrapper: driver rt73 (Belkin Corporation,11/24/2005, 1.00.02.0000) loaded
[17179591.148000] NET: Registered protocol family 17
[17179591.452000] wlan0: ethernet device 00:17:3f:4a:6e:5f using NDIS driver: rt73, version: 0x0, NDIS version: 0x500, vendor: 'Belkin Wireless G Plus MIMO USB ', 050D:905B.F.conf
[17179591.452000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179591.456000] usbcore: registered new driver ndiswrapper
[17179591.500000] Adding 3004112k swap on /dev/sdb5.  Priority:-1 extents:1 across:3004112k
[17179591.572000] EXT3 FS on sdb1, internal journal
[17179591.820000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179591.848000] NTFS volume version 3.1.
[17179594.732000] usb-storage: device scan complete
[17179594.736000]   Vendor: TEAC      Model: USB   HS-CF Card  Rev: 4.00
[17179594.736000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.736000]   Vendor: TEAC      Model: USB   HS-xD/SM    Rev: 4.00
[17179594.740000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.740000]   Vendor: TEAC      Model: USB   HS-MS Card  Rev: 4.00
[17179594.744000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.744000]   Vendor: TEAC      Model: USB   HS-SD Card  Rev: 4.00
[17179594.744000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.756000] sd 4:0:0:0: Attached scsi removable disk sdc
[17179594.756000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[17179594.772000] sd 4:0:0:1: Attached scsi removable disk sdd
[17179594.772000] sd 4:0:0:1: Attached scsi generic sg3 type 0
[17179594.784000] sd 4:0:0:2: Attached scsi removable disk sde
[17179594.784000] sd 4:0:0:2: Attached scsi generic sg4 type 0
[17179594.840000] sd 4:0:0:3: Attached scsi removable disk sdf
[17179594.840000] sd 4:0:0:3: Attached scsi generic sg5 type 0
[17179669.204000] NET: Registered protocol family 10
[17179669.204000] lo: Disabled Privacy Extensions
[17179669.204000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179669.204000] IPv6 over IPv4 tunneling driver
[17179670.520000] ACPI: Power Button (FF) [PWRF]
[17179670.520000] ACPI: Power Button (CM) [VBTN]
[17179670.704000] ibm_acpi: ec object not found
[17179670.740000] pcc_acpi: loading...
[17179671.812000] Symbol usb_register_driver is being used by a non-GPL module, which will not be allowed in the future
[17179671.812000] Please see the file Documentation/feature-removal-schedule.txt in the kernel source tree for more details.
[17179671.812000] Symbol usb_deregister is being used by a non-GPL module, which will not be allowed in the future
[17179671.812000] Please see the file Documentation/feature-removal-schedule.txt in the kernel source tree for more details.
[17179671.932000] driverloader: stack=8192/60/0 REGPARM SMP
[17179671.932000] usbcore: registered new driver driverloader
[17179673.456000] [drm] Initialized drm 1.0.1 20051102
[17179673.460000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179673.460000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179673.908000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179673.908000] apm: disabled - APM is not SMP safe.
[17179678.008000] ip_tables: (C) 2000-2006 Netfilter Core Team
[17179678.092000] Netfilter messages via NETLINK v0.30.
[17179678.096000] ip_conntrack version 2.4 (8116 buckets, 64928 max) - 224 bytes per conntrack
[17179678.784000] Bluetooth: L2CAP ver 2.8
[17179678.784000] Bluetooth: L2CAP socket layer initialized
[17179678.808000] Bluetooth: RFCOMM socket layer initialized
[17179678.808000] Bluetooth: RFCOMM TTY layer initialized
[17179678.808000] Bluetooth: RFCOMM ver 1.7
[17179679.568000] wlan0: no IPv6 routers present
david@david-desktop:~$ 

Any suggestions on how to sort this out?

---

### Post by doobit on 2007-01-08
@glendavee
I'm not surprised it hanges a little on Ndiswrapper because you are fooling the OS into loading a driver that wasn't designed for it. That takes a little processing power and time. However, you may also (possibly) be having a little port conflict as a result of that, so open a terminal and type sudo ifconfig eth0 down
enter and reboot to see it it made a difference. (make sure you have set up to save your session settings)

---

### Post by glendavee on 2007-01-08
doobit. Tried it - made no difference. I guess I'll just have to live with the slow boot for now
Thanks for the suggestion

---

### Post by doobit on 2007-01-08
Your USB hub is causing a problem too, I noticed. Just for the heck of it, unplug the hub and reboot. Then plug the hub back in.  If I were you I'd use a PS2 adapter for your keyboard and mouse unless they use special functions that only the USB can provide.

---

### Post by Gobboman123 on 2007-01-09
After recompiling the kernel module things seem to be okay.

---

### Post by Gobboman123 on 2007-01-10
The help on this forum is always great.  Thanks to everyone for being so amazing.  Beginners and Geeks rejoice, there will always be someone around to help you.

---

