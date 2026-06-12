---
title: "Problems with usb mass-storage devices"
date: 2007-02-02
forum: General Help
---

### Post by NorthernPaladin on 2007-02-02
I have a problem with usb. I don`t know what I have done wrong but the problem is that nothing happens when I plug my Creative MuVo tx into usb port, and tried with another usb memory, nothing.
But my usb gamepad works perfectly, so I must have messed something up, just don`t know what. How can I locate the problem, and after that how do I repair the situation. I installed linux about 3-4 weeks ago so I know only little about it. Any help is welcome!
Yesterday everything was going fine, and I don`t have done any major changes after it, just installed CrossOver and Zsnes

---

### Post by MoLE on 2007-02-02
Can you provide some more information?
I assume you have a default Edgy install?
- How did you install Crossover (I'm assuming Crossover Linux here) and Zsnes?

Can you plug in your MuVo and give us the output of "sudo lsusb" and "sudo dmesg"

---

### Post by NorthernPaladin on 2007-02-02
I installed CrossOver from the demo in their website, and I installed zsnes with synaptics, and yes its default edgy


northernpaladin@northernpaladin:~$ sudo lsusb
Password:
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


northernpaladin@northernpaladin:~$ sudo dmesg
[42949372.960000] Linux version 2.6.17-10-server (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:29:32 UTC 2006 (Ubuntu 2.6.17-10.34-server)
[42949372.960000] BIOS-provided physical RAM map:
[42949372.960000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[42949372.960000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[42949372.960000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[42949372.960000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[42949372.960000]  BIOS-e820: 000000001ffd0000 - 000000001ffdf000 (ACPI data)
[42949372.960000]  BIOS-e820: 000000001ffdf000 - 0000000020000000 (ACPI NVS)
[42949372.960000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[42949372.960000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[42949372.960000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[42949372.960000] 0MB HIGHMEM available.
[42949372.960000] 511MB LOWMEM available.
[42949372.960000] On node 0 totalpages: 131024
[42949372.960000]   DMA zone: 4096 pages, LIFO batch:0
[42949372.960000]   Normal zone: 126928 pages, LIFO batch:31
[42949372.960000] DMI 2.3 present.
[42949372.960000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000faa80
[42949372.960000] ACPI: RSDT (v001 A M I  OEMRSDT  0x10000315 MSFT 0x00000097) @ 0x1ffd0000
[42949372.960000] ACPI: FADT (v002 A M I  OEMFACP  0x10000315 MSFT 0x00000097) @ 0x1ffd0200
[42949372.960000] ACPI: MADT (v001 A M I  OEMAPIC  0x10000315 MSFT 0x00000097) @ 0x1ffd0390
[42949372.960000] ACPI: OEMB (v001 A M I  OEMBIOS  0x10000315 MSFT 0x00000097) @ 0x1ffdf040
[42949372.960000] ACPI: DSDT (v001  A7N8X A7N8X000 0x00000000 INTL 0x02002026) @ 0x00000000
[42949372.960000] ACPI: PM-Timer IO Port: 0x4008
[42949372.960000] ACPI: Local APIC address 0xfee00000
[42949372.960000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[42949372.960000] Processor #0 6:10 APIC version 16
[42949372.960000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[42949372.960000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[42949372.960000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[42949372.960000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[42949372.960000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[42949372.960000] ACPI: IRQ9 used by override.
[42949372.960000] ACPI: IRQ14 used by override.
[42949372.960000] ACPI: IRQ15 used by override.
[42949372.960000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[42949372.960000] Using ACPI (MADT) for SMP configuration information
[42949372.960000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[42949372.960000] Built 1 zonelists
[42949372.960000] Kernel command line: root=/dev/hda1 ro quiet splash
[42949372.960000] mapped APIC to ffffd000 (fee00000)
[42949372.960000] mapped IOAPIC to ffffc000 (fec00000)
[42949372.960000] Enabling fast FPU save and restore... done.
[42949372.960000] Enabling unmasked SIMD FPU exception support... done.
[42949372.960000] Initializing CPU#0
[42949372.960000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[42949372.960000] Detected 1913.193 MHz processor.
[42949372.960000] Using pmtmr for high-res timesource
[42949372.960000] Console: colour VGA+ 80x25
[42949374.880000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[42949374.880000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[42949374.890000] Memory: 509928k/524096k available (1903k kernel code, 13616k reserved, 1073k data, 312k init, 0k highmem)
[42949374.890000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[42949375.040000] Calibrating delay using timer specific routine.. 3829.84 BogoMIPS (lpj=19149223)
[42949375.040000] Security Framework v1.0.0 initialized
[42949375.040000] SELinux:  Disabled at boot.
[42949375.040000] Mount-cache hash table entries: 512
[42949375.040000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[42949375.040000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[42949375.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[42949375.040000] CPU: L2 Cache: 512K (64 bytes/line)
[42949375.040000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[42949375.040000] Checking 'hlt' instruction... OK.
[42949375.080000] SMP alternatives: switching to UP code
[42949375.080000] Freeing SMP alternatives: 16k freed
[42949375.080000] checking if image is initramfs... it is
[42949375.550000] Freeing initrd memory: 5336k freed
[42949375.550000] ACPI: Core revision 20060707
[42949375.550000] ACPI: Looking for DSDT ... not found!
[42949375.550000] CPU0: AMD Athlon(tm) XP  2600+ stepping 00
[42949375.550000] Total of 1 processors activated (3829.84 BogoMIPS).
[42949375.550000] ENABLING IO-APIC IRQs
[42949375.550000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[42949375.760000] Brought up 1 CPUs
[42949375.760000] migration_cost=0
[42949375.760000] NET: Registered protocol family 16
[42949375.760000] EISA bus registered
[42949375.760000] ACPI: bus type pci registered
[42949375.760000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[42949375.760000] PCI: Using configuration type 1
[42949375.760000] Setting up standard PCI resources
[42949375.760000] ACPI: Interpreter enabled
[42949375.760000] ACPI: Using IOAPIC for interrupt routing
[42949375.770000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[42949375.770000] PCI: Probing PCI hardware (bus 00)
[42949375.770000] PCI: nForce2 C1 Halt Disconnect fixup
[42949375.770000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:09.0
[42949375.770000] Boot video device is 0000:01:00.0
[42949375.770000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[42949375.780000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[42949375.780000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[42949375.780000] ACPI: PCI Interrupt Link [LNKA] (IRQs 16) *11
[42949375.780000] ACPI: PCI Interrupt Link [LNKB] (IRQs 18) *0, disabled.
[42949375.780000] ACPI: PCI Interrupt Link [LNKC] (IRQs 18) *0, disabled.
[42949375.780000] ACPI: PCI Interrupt Link [LNKD] (IRQs 19) *0, disabled.
[42949375.780000] ACPI: PCI Interrupt Link [LNKE] (IRQs 16) *0, disabled.
[42949375.790000] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *5
[42949375.790000] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *5
[42949375.790000] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *5
[42949375.790000] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *11
[42949375.790000] ACPI: PCI Interrupt Link [LAPU] (IRQs 20 21 22) *0, disabled.
[42949375.790000] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *3
[42949375.790000] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[42949375.790000] ACPI: PCI Interrupt Link [LKSM] (IRQs 23) *11
[42949375.790000] ACPI: PCI Interrupt Link [LFWR] (IRQs 20 21 22) *10
[42949375.790000] ACPI: PCI Interrupt Link [LETH] (IRQs 20 21 22) *0, disabled.
[42949375.790000] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22) *14
[42949375.790000] Linux Plug and Play Support v0.97 (c) Adam Belay
[42949375.790000] pnp: PnP ACPI init
[42949375.790000] pnp: PnP ACPI: found 14 devices
[42949375.790000] PnPBIOS: Disabled by ACPI PNP
[42949375.790000] PCI: Using ACPI for IRQ routing
[42949375.790000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[42949375.810000] pnp: 00:0b: ioport range 0x480-0x4ff has been reserved
[42949375.810000] PCI: Bridge: 0000:00:08.0
[42949375.810000]   IO window: d000-dfff
[42949375.810000]   MEM window: fd900000-fdafffff
[42949375.810000]   PREFETCH window: disabled.
[42949375.810000] PCI: Bridge: 0000:00:1e.0
[42949375.810000]   IO window: disabled.
[42949375.810000]   MEM window: fb700000-fd8fffff
[42949375.810000]   PREFETCH window: eb400000-f35fffff
[42949375.810000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[42949375.810000] NET: Registered protocol family 2
[42949375.890000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[42949375.890000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[42949375.890000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[42949375.890000] TCP: Hash tables configured (established 16384 bind 8192)
[42949375.890000] TCP reno registered
[42949375.890000] audit: initializing netlink socket (disabled)
[42949375.890000] audit(1170354405.890:1): initialized
[42949375.890000] VFS: Disk quotas dquot_6.5.1
[42949375.890000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[42949375.890000] Initializing Cryptographic API
[42949375.890000] io scheduler noop registered
[42949375.890000] io scheduler anticipatory registered
[42949375.890000] io scheduler deadline registered (default)
[42949375.890000] io scheduler cfq registered
[42949375.890000] isapnp: Scanning for PnP cards...
[42949376.240000] isapnp: No Plug & Play device found
[42949376.270000] Real Time Clock Driver v1.12ac
[42949376.270000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[42949376.270000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949376.270000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949376.270000] mice: PS/2 mouse device common for all mice
[42949376.270000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[42949376.270000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[42949376.270000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[42949376.270000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f12:PS2M] at 0x60,0x64 irq 1,12
[42949376.270000] serio: i8042 AUX port at 0x60,0x64 irq 12
[42949376.270000] serio: i8042 KBD port at 0x60,0x64 irq 1
[42949376.270000] EISA: Probing bus 0 at eisa.0
[42949376.270000] Cannot allocate resource for EISA slot 4
[42949376.270000] EISA: Detected 0 cards.
[42949376.270000] TCP bic registered
[42949376.270000] NET: Registered protocol family 1
[42949376.270000] NET: Registered protocol family 8
[42949376.270000] NET: Registered protocol family 20
[42949376.270000] Using IPI No-Shortcut mode
[42949376.270000] ACPI: (supports S0 S1 S3 S4 S5)
[42949376.270000] Freeing unused kernel memory: 312k freed
[42949376.290000] input: AT Translated Set 2 keyboard as /class/input/input0
[42949377.350000] Capability LSM initialized
[42949377.690000] SCSI subsystem initialized
[42949377.700000] libata version 1.20 loaded.
[42949377.700000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[42949377.700000] NFORCE2: chipset revision 162
[42949377.700000] NFORCE2: not 100% native mode: will probe irqs later
[42949377.700000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[42949377.700000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[42949377.700000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[42949377.700000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[42949377.700000] Probing IDE interface ide0...
[42949378.010000] hda: ST380011A, ATA DISK drive
[42949378.730000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[42949378.730000] Probing IDE interface ide1...
[42949379.520000] hdc: IDE-DVD ROM 16x, ATAPI CD/DVD-ROM drive
[42949380.360000] hdd: SAMSUNG CD-R/RW SW-248F, ATAPI CD/DVD-ROM drive
[42949380.420000] ide1 at 0x170-0x177,0x376 on irq 15
[42949380.430000] hda: max request size: 512KiB
[42949380.440000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[42949380.440000] hda: cache flushes supported
[42949380.440000]  hda: hda1 hda2 < hda5 > hda3
[42949380.490000] hdc: ATAPI 40X DVD-ROM drive, 256kB Cache, UDMA(33)
[42949380.490000] Uniform CD-ROM driver Revision: 3.20
[42949380.490000] hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[42949380.880000] usbcore: registered new driver usbfs
[42949380.880000] usbcore: registered new driver hub
[42949380.880000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[42949380.880000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[42949380.880000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 22 (level, high) -> IRQ 177
[42949380.880000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[42949380.880000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[42949380.880000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[42949380.880000] ohci_hcd 0000:00:02.0: irq 177, io mem 0xfe900000
[42949380.920000] ieee1394: Initialized config rom entry `ip1394'
[42949380.940000] usb usb1: configuration #1 chosen from 1 choice
[42949380.940000] hub 1-0:1.0: USB hub found
[42949380.940000] hub 1-0:1.0: 3 ports detected
[42949381.050000] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 21
[42949381.050000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS1] -> GSI 21 (level, high) -> IRQ 185
[42949381.050000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[42949381.050000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[42949381.050000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[42949381.050000] ohci_hcd 0000:00:02.1: irq 185, io mem 0xfea00000
[42949381.110000] usb usb2: configuration #1 chosen from 1 choice
[42949381.110000] hub 2-0:1.0: USB hub found
[42949381.110000] hub 2-0:1.0: 3 ports detected
[42949381.230000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[42949381.230000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUS2] -> GSI 20 (level, high) -> IRQ 193
[42949381.230000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[42949381.230000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[42949381.230000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[42949381.230000] ehci_hcd 0000:00:02.2: debug port 1
[42949381.230000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[42949381.230000] ehci_hcd 0000:00:02.2: irq 193, io mem 0xfeb00000
[42949381.230000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[42949381.230000] usb usb3: configuration #1 chosen from 1 choice
[42949381.230000] hub 3-0:1.0: USB hub found
[42949381.230000] hub 3-0:1.0: 6 ports detected
[42949381.340000] ACPI: PCI Interrupt Link [LFWR] enabled at IRQ 22
[42949381.340000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LFWR] -> GSI 22 (level, high) -> IRQ 177
[42949381.340000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[42949381.390000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[fe500000-fe5007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[42949381.460000] Attempting manual resume
[42949381.470000] EXT3-fs: INFO: recovery required on readonly filesystem.
[42949381.470000] EXT3-fs: write access will be enabled during recovery.
[42949382.510000] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[42949382.830000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00418df500e01800]
[42949385.310000] kjournald starting.  Commit interval 5 seconds
[42949385.310000] EXT3-fs: recovery complete.
[42949385.320000] EXT3-fs: mounted filesystem with ordered data mode.
[42949392.360000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[42949392.360000] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 21
[42949392.360000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LKLN] -> GSI 21 (level, high) -> IRQ 185
[42949392.360000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[42949392.430000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[42949392.890000] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
[42949392.890000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[42949392.900000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4300
[42949392.900000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4340
[42949393.130000] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 20
[42949393.130000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LAUI] -> GSI 20 (level, high) -> IRQ 193
[42949393.130000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[42949393.170000] Linux agpgart interface v0.101 (c) Dave Jones
[42949393.330000] input: PC Speaker as /class/input/input1
[42949393.460000] intel8x0_measure_ac97_clock: measured 58755 usecs
[42949393.460000] intel8x0: clocking to 48000
[42949393.460000] agpgart: Detected NVIDIA nForce2 chipset
[42949393.460000] agpgart: AGP aperture is 64M @ 0xf4000000
[42949393.500000] parport: PnPBIOS parport detected.
[42949393.500000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[42949393.530000] eth0: no link during initialization.
[42949393.680000] Floppy drive(s): fd0 is 1.44M
[42949393.710000] FDC 0 is a post-1991 82077
[42949393.850000] input: PS2++ Logitech MX Mouse as /class/input/input2
[42949394.020000] nvidia: module license 'NVIDIA' taints kernel.
[42949394.060000] eth0: link up.
[42949394.270000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
[42949394.270000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 16 (level, high) -> IRQ 201
[42949394.270000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[42949394.300000] ts: Compaq touchscreen protocol output
[42949394.530000] lp0: using parport0 (interrupt-driven).
[42949394.560000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[42949394.560000] ieee1394: sbp2: Try serialize_io=0 for better performance
[42949394.590000] Adding 1044216k swap on /dev/disk/by-uuid/8018e938-6889-4d64-8047-b0e1f85f337c.  Priority:-1 extents:1 across:1044216k
[42949394.690000] NET: Registered protocol family 17
[42949394.700000] EXT3 FS on hda1, internal journal
[42949396.630000] NET: Registered protocol family 10
[42949396.630000] lo: Disabled Privacy Extensions
[42949396.630000] IPv6 over IPv4 tunneling driver
[42949398.640000] kjournald starting.  Commit interval 5 seconds
[42949398.640000] EXT3 FS on hda5, internal journal
[42949398.640000] EXT3-fs: mounted filesystem with ordered data mode.
[42949403.970000] DLM (built Dec  5 2006 21:44:54) installed
[42949404.010000] GFS2 (built Dec  5 2006 21:45:21) installed
[42949404.020000] Lock_DLM (built Dec  5 2006 21:45:35) installed
[42949406.030000] ACPI: Power Button (FF) [PWRF]
[42949406.030000] ACPI: Power Button (CM) [PWRB]
[42949406.150000] ibm_acpi: ec object not found
[42949406.200000] pcc_acpi: loading...
[42949407.560000] eth0: no IPv6 routers present
[42949408.850000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42949408.850000] apm: overridden by ACPI.
[42949408.960000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[42949408.960000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[42949408.960000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[42949415.910000] Bluetooth: Core ver 2.8
[42949415.910000] NET: Registered protocol family 31
[42949415.910000] Bluetooth: HCI device and connection manager initialized
[42949415.910000] Bluetooth: HCI socket layer initialized
[42949415.930000] Bluetooth: L2CAP ver 2.8
[42949415.930000] Bluetooth: L2CAP socket layer initialized
[42949415.930000] Bluetooth: RFCOMM socket layer initialized
[42949415.930000] Bluetooth: RFCOMM TTY layer initialized
[42949415.930000] Bluetooth: RFCOMM ver 1.7
[42949431.960000] ISO 9660 Extensions: Microsoft Joliet Level 3
[42949432.030000] ISOFS: changing to secondary root
[42949454.370000] usb 3-5: new high speed USB device using ehci_hcd and address 2
[42949454.520000] usb 3-5: configuration #1 chosen from 1 choice
[42949454.620000] usbcore: registered new driver libusual
[42949454.630000] Initializing USB Mass Storage driver...
[42949454.630000] scsi0 : SCSI emulation for USB Mass Storage devices
[42949454.630000] usbcore: registered new driver usb-storage
[42949454.630000] USB Mass Storage support registered.
[42949454.630000] usb-storage: device found at 2
[42949454.630000] usb-storage: waiting for device to settle before scanning
[42949459.630000] usb-storage: device scan complete
[42949459.630000]   Vendor: CREATIVE  Model: NOMAD MuVo TX     Rev: 1223
[42949459.630000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[42949459.680000] SCSI device sda: 493760 2048-byte hdwr sectors (1011 MB)
[42949459.680000] sda: Write Protect is off
[42949459.680000] sda: Mode Sense: 38 00 00 00
[42949459.680000] sda: assuming drive cache: write through
[42949459.680000] SCSI device sda: 493760 2048-byte hdwr sectors (1011 MB)
[42949459.680000] sda: Write Protect is off
[42949459.680000] sda: Mode Sense: 38 00 00 00
[42949459.680000] sda: assuming drive cache: write through
[42949459.680000]  sda: sda1
[42949459.680000] sd 0:0:0:0: Attached scsi removable disk sda
[42949459.740000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[42949459.930000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[42952401.670000] usb 3-5: USB disconnect, address 2
[42959867.140000] ohci_hcd 0000:00:02.1: wakeup
[42959867.600000] usb 2-3: new low speed USB device using ohci_hcd and address 2
[42959867.860000] usb 2-3: configuration #1 chosen from 1 choice
[42959868.980000] usbcore: registered new driver hiddev
[42959869.000000] input: Logitech Logitech Dual Action as /class/input/input3
[42959869.000000] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:02.1-3
[42959869.000000] usbcore: registered new driver usbhid
[42959869.000000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[42961517.030000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42961517.030000] apm: disabled on user request.
[42961654.770000] ibm_acpi: ec object not found
[42961656.300000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[42961656.300000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[42961656.300000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[42961658.030000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42961658.030000] apm: disabled on user request.
[42961960.380000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42961960.380000] apm: disabled on user request.
[42961971.730000] ibm_acpi: ec object not found
[42961972.530000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[42961972.530000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[42961972.530000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[42961972.720000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42961972.720000] apm: disabled on user request.
[42965991.380000] usb 2-3: USB disconnect, address 2
[42965995.100000] ohci_hcd 0000:00:02.1: wakeup
[42965995.550000] usb 2-3: new full speed USB device using ohci_hcd and address 3
[42965995.780000] usb 2-3: configuration #1 chosen from 1 choice
[42965995.780000] scsi1 : SCSI emulation for USB Mass Storage devices
[42965995.780000] usb-storage: device found at 3
[42965995.780000] usb-storage: waiting for device to settle before scanning
[42966000.780000] usb-storage: device scan complete
[42966000.790000]   Vendor: SigmaTel  Model: MSCN              Rev: 0100
[42966000.790000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[42966000.800000] SCSI device sda: 248320 512-byte hdwr sectors (127 MB)
[42966000.800000] sda: Write Protect is off
[42966000.800000] sda: Mode Sense: 38 00 00 00
[42966000.800000] sda: assuming drive cache: write through
[42966000.830000] SCSI device sda: 248320 512-byte hdwr sectors (127 MB)
[42966000.840000] sda: Write Protect is off
[42966000.840000] sda: Mode Sense: 38 00 00 00
[42966000.840000] sda: assuming drive cache: write through
[42966000.840000]  sda: sda1
[42966000.850000] sd 1:0:0:0: Attached scsi removable disk sda
[42966000.850000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[42966051.960000] usb 2-3: USB disconnect, address 3
[42966058.600000] ohci_hcd 0000:00:02.0: wakeup
[42966059.050000] usb 1-3: new full speed USB device using ohci_hcd and address 2
[42966060.680000] usb 1-3: configuration #1 chosen from 1 choice
[42966060.680000] scsi2 : SCSI emulation for USB Mass Storage devices
[42966060.680000] usb-storage: device found at 2
[42966060.680000] usb-storage: waiting for device to settle before scanning
[42966065.680000] usb-storage: device scan complete
[42966065.690000]   Vendor: SigmaTel  Model: MSCN              Rev: 0100
[42966065.690000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[42966065.700000] SCSI device sda: 248320 512-byte hdwr sectors (127 MB)
[42966065.710000] sda: Write Protect is off
[42966065.710000] sda: Mode Sense: 38 00 00 00
[42966065.710000] sda: assuming drive cache: write through
[42966065.730000] SCSI device sda: 248320 512-byte hdwr sectors (127 MB)
[42966065.740000] sda: Write Protect is off
[42966065.740000] sda: Mode Sense: 38 00 00 00
[42966065.740000] sda: assuming drive cache: write through
[42966065.740000]  sda: sda1
[42966065.750000] sd 2:0:0:0: Attached scsi removable disk sda
[42966065.750000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[42966081.460000] usb 1-3: USB disconnect, address 2
[42966094.160000] usb 3-5: new high speed USB device using ehci_hcd and address 6
[42966094.310000] usb 3-5: configuration #1 chosen from 1 choice
[42966094.310000] scsi3 : SCSI emulation for USB Mass Storage devices
[42966094.310000] usb-storage: device found at 6
[42966094.310000] usb-storage: waiting for device to settle before scanning
[42966099.310000] usb-storage: device scan complete
[42966099.310000]   Vendor: CREATIVE  Model: NOMAD MuVo TX     Rev: 1223
[42966099.310000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[42966099.310000] SCSI device sda: 493760 2048-byte hdwr sectors (1011 MB)
[42966099.310000] sda: Write Protect is off
[42966099.310000] sda: Mode Sense: 38 00 00 00
[42966099.310000] sda: assuming drive cache: write through
[42966099.320000] SCSI device sda: 493760 2048-byte hdwr sectors (1011 MB)
[42966099.320000] sda: Write Protect is off
[42966099.320000] sda: Mode Sense: 38 00 00 00
[42966099.320000] sda: assuming drive cache: write through
[42966099.320000]  sda: sda1
[42966099.320000] sd 3:0:0:0: Attached scsi removable disk sda
[42966099.320000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[42969423.320000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42969423.320000] apm: disabled on user request.
[42970282.680000] ibm_acpi: ec object not found
[42970284.320000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[42970284.320000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[42970284.320000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[42970286.120000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42970286.120000] apm: disabled on user request.
[42972550.090000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42972550.090000] apm: disabled on user request.
[42972560.990000] ibm_acpi: ec object not found
[42972562.590000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[42972562.590000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[42972562.590000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[42972564.160000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42972564.160000] apm: disabled on user request.
[42972927.340000] usb 3-5: USB disconnect, address 6
[42972945.310000] ohci_hcd 0000:00:02.1: wakeup
[42972945.760000] usb 2-3: new low speed USB device using ohci_hcd and address 4
[42972946.000000] usb 2-3: configuration #1 chosen from 1 choice
[42972946.020000] input: Logitech Logitech Dual Action as /class/input/input4
[42972946.020000] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:02.1-3
[42975622.760000] usb 2-3: USB disconnect, address 4
[42975627.690000] usb 3-6: new high speed USB device using ehci_hcd and address 8
[42975627.840000] usb 3-6: configuration #1 chosen from 1 choice
[42975627.840000] scsi4 : SCSI emulation for USB Mass Storage devices
[42975627.840000] usb-storage: device found at 8
[42975627.840000] usb-storage: waiting for device to settle before scanning
[42975632.840000] usb-storage: device scan complete
[42975632.840000]   Vendor: CREATIVE  Model: NOMAD MuVo TX     Rev: 1223
[42975632.840000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[42975632.840000] SCSI device sda: 493760 2048-byte hdwr sectors (1011 MB)
[42975632.840000] sda: Write Protect is off
[42975632.840000] sda: Mode Sense: 38 00 00 00
[42975632.840000] sda: assuming drive cache: write through
[42975632.840000] SCSI device sda: 493760 2048-byte hdwr sectors (1011 MB)
[42975632.840000] sda: Write Protect is off
[42975632.840000] sda: Mode Sense: 38 00 00 00
[42975632.840000] sda: assuming drive cache: write through
[42975632.840000]  sda: sda1
[42975632.840000] sd 4:0:0:0: Attached scsi removable disk sda
[42975632.840000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[42977563.200000] usb 3-6: USB disconnect, address 8
[42977567.920000] ohci_hcd 0000:00:02.1: wakeup
[42977568.370000] usb 2-3: new low speed USB device using ohci_hcd and address 5
[42977568.600000] usb 2-3: configuration #1 chosen from 1 choice
[42977568.630000] input: Logitech Logitech Dual Action as /class/input/input5
[42977568.630000] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:02.1-3
[42981799.490000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42981799.490000] apm: disabled on user request.
[42981811.480000] ibm_acpi: ec object not found
[42981813.100000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[42981813.100000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[42981813.100000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[42981815.100000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[42981815.100000] apm: disabled on user request.
[42995352.400000] usb 2-3: USB disconnect, address 5
[42995357.570000] usb 3-6: new high speed USB device using ehci_hcd and address 10
[42995357.730000] usb 3-6: configuration #1 chosen from 1 choice
[42995357.730000] scsi5 : SCSI emulation for USB Mass Storage devices
[42995357.730000] usb-storage: device found at 10
[42995357.730000] usb-storage: waiting for device to settle before scanning
[42995362.740000] usb-storage: device scan complete
[42995362.740000]   Vendor: CREATIVE  Model: NOMAD MuVo TX     Rev: 1223
[42995362.740000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[42995362.740000] SCSI device sda: 493760 2048-byte hdwr sectors (1011 MB)
[42995362.740000] sda: Write Protect is off
[42995362.740000] sda: Mode Sense: 38 00 00 00
[42995362.740000] sda: assuming drive cache: write through
[42995362.740000] SCSI device sda: 493760 2048-byte hdwr sectors (1011 MB)
[42995362.740000] sda: Write Protect is off
[42995362.740000] sda: Mode Sense: 38 00 00 00
[42995362.740000] sda: assuming drive cache: write through
[42995362.740000]  sda: sda1
[42995362.740000] sd 5:0:0:0: Attached scsi removable disk sda
[42995362.740000] sd 5:0:0:0: Attached scsi generic sg0 type 0

---

### Post by NorthernPaladin on 2007-02-09
bump

---

