---
title: "SD Card Will Not Mount"
date: 2007-01-27
forum: General Help
---

### Post by Iorchova on 2007-01-27
Hello, I am using Ubuntu 6.10 Edgy Eft, and when I insert my Sandisk 1 Gigabyte SD Card(For Wii) it is not read. This kind of puzzles me, as when I was relying off of a 6.06 Dapper Drake Live CD(Hard Drive had died) the SD card worked fine. It is not ready by Ubuntu, nor is the blue "Confirmation" light on the SD Card reader lit up. It is an internal reader, not attached by USB. Can someone tell me what's wrong?

---

### Post by dcstar on 2007-01-27
> **Iorchova said:**
> Hello, I am using Ubuntu 6.10 Edgy Eft, and when I insert my Sandisk 1 Gigabyte SD Card(For Wii) it is not read. This kind of puzzles me, as when I was relying off of a 6.06 Dapper Drake Live CD(Hard Drive had died) the SD card worked fine. It is not ready by Ubuntu, nor is the blue "Confirmation" light on the SD Card reader lit up. It is an internal reader, not attached by USB. Can someone tell me what's wrong?

In a terminal, run: ```
dmesg
``` when you plug it in and post the output here.

Also check - using System-Administration-System Manager - that **gnome-volume-manager** is running.

---

### Post by fragos on 2007-01-27
Are we talking about a laptop?  Desktop readers attach to an internal USB plug.  Some laptops use a proprietary interface instead of USB to read SD cards and it may not be supported.

---

### Post by travs.cd on 2007-01-27
this worked for me, not 1 hour ago..

```
Open a Terminal. Applications -> Accessories -> Terminal

Loading the drivers from terminal type:

sudo modprobe tifm_sd

Now to insert a SD media card and it should auto mount.

If all went well you can now edit the the /etc/modules file so you can load the drivers for the card reader on boot up

From terminal type:

sudo gedit /etc/modules

Add the drivers to the modules file

tifm_sd

save the file 
```

---

### Post by fragos on 2007-01-27
What hardware are you running with tifm_sd?

---

### Post by Iorchova on 2007-01-27
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bfd0000 (usable)
[17179569.184000]  BIOS-e820: 000000001bfd0000 - 000000001bfdf000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001bfdf000 - 000000001c000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 447MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 114640
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110544 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9d30
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x06000327 MSFT 0x00000097) @ 0x1bfd0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x06000327 MSFT 0x00000097) @ 0x1bfd0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x06000327 MSFT 0x00000097) @ 0x1bfd0390
[17179569.184000] ACPI: OEMB (v001 A M I  OEMBIOS  0x06000327 MSFT 0x00000097) @ 0x1bfdf040
[17179569.184000] ACPI: DSDT (v001  A7N8X A7N8X000 0x00000000 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e2c00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 2079.788 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.776000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.776000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.788000] Memory: 444648k/458560k available (1910k kernel code, 13388k reserved, 1069k data, 308k init, 0k highmem)
[17179571.788000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.868000] Calibrating delay using timer specific routine.. 4163.94 BogoMIPS (lpj=8327882)
[17179571.868000] Security Framework v1.0.0 initialized
[17179571.868000] SELinux:  Disabled at boot.
[17179571.868000] Mount-cache hash table entries: 512
[17179571.868000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179571.868000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179571.868000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179571.868000] CPU: L2 Cache: 512K (64 bytes/line)
[17179571.868000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179571.868000] Checking 'hlt' instruction... OK.
[17179571.884000] SMP alternatives: switching to UP code
[17179571.884000] Freeing SMP alternatives: 16k freed
[17179571.884000] checking if image is initramfs... it is
[17179572.336000] Freeing initrd memory: 5623k freed
[17179572.336000] ACPI: Core revision 20060707
[17179572.336000] ACPI: Looking for DSDT ... not found!
[17179572.336000] CPU0: AMD Athlon(tm) XP  2800+ stepping 00
[17179572.336000] Total of 1 processors activated (4163.94 BogoMIPS).
[17179572.340000] ENABLING IO-APIC IRQs
[17179572.340000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179572.480000] Brought up 1 CPUs
[17179572.480000] migration_cost=0
[17179572.480000] NET: Registered protocol family 16
[17179572.480000] EISA bus registered
[17179572.480000] ACPI: bus type pci registered
[17179572.480000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[17179572.480000] PCI: Using configuration type 1
[17179572.480000] Setting up standard PCI resources
[17179572.488000] ACPI: Interpreter enabled
[17179572.488000] ACPI: Using IOAPIC for interrupt routing
[17179572.488000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.488000] PCI: Probing PCI hardware (bus 00)
[17179572.492000] PCI: nForce2 C1 Halt Disconnect fixup
[17179572.492000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:09.0
[17179572.492000] Boot video device is 0000:02:00.0
[17179572.492000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[17179572.504000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179572.508000] ACPI: PCI Interrupt Link [LNKA] (IRQs 16) *0, disabled.
[17179572.508000] ACPI: PCI Interrupt Link [LNKB] (IRQs 18) *0, disabled.
[17179572.508000] ACPI: PCI Interrupt Link [LNKC] (IRQs 18) *0, disabled.
[17179572.508000] ACPI: PCI Interrupt Link [LNKD] (IRQs 19) *11
[17179572.508000] ACPI: PCI Interrupt Link [LNKE] (IRQs 16) *11
[17179572.508000] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *5
[17179572.508000] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *5
[17179572.508000] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *5
[17179572.512000] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *3
[17179572.512000] ACPI: PCI Interrupt Link [LAPU] (IRQs 20 21 22) *0, disabled.
[17179572.512000] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *11
[17179572.512000] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *11
[17179572.512000] ACPI: PCI Interrupt Link [LKSM] (IRQs 23) *10
[17179572.512000] ACPI: PCI Interrupt Link [LFWR] (IRQs 20 21 22) *11
[17179572.512000] ACPI: PCI Interrupt Link [LETH] (IRQs 20 21 22) *0, disabled.
[17179572.512000] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22) *14
[17179572.512000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.512000] pnp: PnP ACPI init
[17179572.516000] pnp: PnP ACPI: found 14 devices
[17179572.516000] PnPBIOS: Disabled by ACPI PNP
[17179572.516000] PCI: Using ACPI for IRQ routing
[17179572.516000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.532000] pnp: 00:0b: ioport range 0x480-0x4ff has been reserved
[17179572.532000] PCI: Bridge: 0000:00:08.0
[17179572.532000]   IO window: d000-dfff
[17179572.532000]   MEM window: fb700000-fb8fffff
[17179572.532000]   PREFETCH window: disabled.
[17179572.532000] PCI: Bridge: 0000:00:1e.0
[17179572.532000]   IO window: disabled.
[17179572.532000]   MEM window: fb900000-fdafffff
[17179572.532000]   PREFETCH window: eb400000-f35fffff
[17179572.532000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179572.532000] NET: Registered protocol family 2
[17179572.568000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.568000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179572.568000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179572.568000] TCP: Hash tables configured (established 16384 bind 8192)
[17179572.568000] TCP reno registered
[17179572.568000] audit: initializing netlink socket (disabled)
[17179572.568000] audit(1169925874.568:1): initialized
[17179572.568000] VFS: Disk quotas dquot_6.5.1
[17179572.568000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.568000] Initializing Cryptographic API
[17179572.568000] io scheduler noop registered
[17179572.568000] io scheduler anticipatory registered
[17179572.568000] io scheduler deadline registered
[17179572.568000] io scheduler cfq registered (default)
[17179572.568000] isapnp: Scanning for PnP cards...
[17179572.928000] isapnp: No Plug & Play device found
[17179572.948000] Real Time Clock Driver v1.12ac
[17179572.948000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.948000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.948000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.948000] mice: PS/2 mouse device common for all mice
[17179572.948000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.948000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.948000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.948000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f12:PS2M] at 0x60,0x64 irq 1,12
[17179572.952000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.952000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.952000] EISA: Probing bus 0 at eisa.0
[17179572.952000] Cannot allocate resource for EISA slot 4
[17179572.952000] EISA: Detected 0 cards.
[17179572.952000] TCP bic registered
[17179572.952000] NET: Registered protocol family 1
[17179572.952000] NET: Registered protocol family 8
[17179572.952000] NET: Registered protocol family 20
[17179572.952000] Using IPI No-Shortcut mode
[17179572.952000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.952000] Freeing unused kernel memory: 308k freed
[17179572.984000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.024000] Capability LSM initialized
[17179574.344000] SCSI subsystem initialized
[17179574.348000] libata version 1.20 loaded.
[17179574.352000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179574.352000] NFORCE2: chipset revision 162
[17179574.352000] NFORCE2: not 100% native mode: will probe irqs later
[17179574.352000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[17179574.352000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[17179574.352000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179574.352000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[17179574.352000] Probing IDE interface ide0...
[17179574.644000] hda: WDC AC14300R, ATA DISK drive
[17179575.328000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.368000] Probing IDE interface ide1...
[17179576.104000] hdc: DVD RW DRU-820A, ATAPI CD/DVD-ROM drive
[17179576.888000] hdd: FX48++W, ATAPI CD/DVD-ROM drive
[17179576.944000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.952000] hda: max request size: 128KiB
[17179576.952000] hda: 8421840 sectors (4311 MB) w/512KiB Cache, CHS=8912/15/63
[17179576.952000] hda: cache flushes not supported
[17179576.952000]  hda: hda1 hda2 < hda5 >
[17179577.016000] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.016000] Uniform CD-ROM driver Revision: 3.20
[17179577.020000] hdd: ATAPI 48X CD-ROM drive, 128kB Cache, UDMA(33)
[17179577.348000] usbcore: registered new driver usbfs
[17179577.348000] usbcore: registered new driver hub
[17179577.348000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.352000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[17179577.352000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 22 (level, high) -> IRQ 177
[17179577.352000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179577.352000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179577.352000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179577.352000] ohci_hcd 0000:00:02.0: irq 177, io mem 0xfe900000
[17179577.372000] ieee1394: Initialized config rom entry `ip1394'
[17179577.408000] usb usb1: configuration #1 chosen from 1 choice
[17179577.408000] hub 1-0:1.0: USB hub found
[17179577.408000] hub 1-0:1.0: 3 ports detected
[17179577.512000] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 21
[17179577.512000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS1] -> GSI 21 (level, high) -> IRQ 185
[17179577.512000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179577.512000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179577.512000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179577.512000] ohci_hcd 0000:00:02.1: irq 185, io mem 0xfea00000
[17179577.568000] usb usb2: configuration #1 chosen from 1 choice
[17179577.568000] hub 2-0:1.0: USB hub found
[17179577.568000] hub 2-0:1.0: 3 ports detected
[17179577.688000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[17179577.688000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUS2] -> GSI 20 (level, high) -> IRQ 193
[17179577.688000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179577.688000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179577.688000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179577.688000] ehci_hcd 0000:00:02.2: debug port 1
[17179577.688000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179577.688000] ehci_hcd 0000:00:02.2: irq 193, io mem 0xfeb00000
[17179577.688000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.688000] usb usb3: configuration #1 chosen from 1 choice
[17179577.688000] hub 3-0:1.0: USB hub found
[17179577.688000] hub 3-0:1.0: 6 ports detected
[17179577.792000] ACPI: PCI Interrupt Link [LFWR] enabled at IRQ 22
[17179577.792000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LFWR] -> GSI 22 (level, high) -> IRQ 177
[17179577.792000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179577.844000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[fe500000-fe5007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179577.900000] Attempting manual resume
[17179577.932000] kjournald starting.  Commit interval 5 seconds
[17179577.932000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.180000] usb 3-2: new high speed USB device using ehci_hcd and address 2
[17179578.516000] usb 3-2: configuration #1 chosen from 1 choice
[17179578.956000] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[17179579.228000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0028c62600e01800]
[17179594.488000] Floppy drive(s): fd0 is 1.44M
[17179594.508000] FDC 0 is a post-1991 82077
[17179594.520000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179594.520000] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 21
[17179594.520000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LKLN] -> GSI 21 (level, high) -> IRQ 185
[17179594.520000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179594.568000] input: PC Speaker as /class/input/input1
[17179594.700000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.848000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179595.040000] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
[17179595.040000] agpgart: Detected NVIDIA nForce2 chipset
[17179595.044000] agpgart: AGP aperture is 64M @ 0xf4000000
[17179595.044000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.044000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4300
[17179595.044000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4340
[17179595.236000] parport: PnPBIOS parport detected.
[17179595.236000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179595.536000] eth0: no link during initialization.
[17179595.764000] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 20
[17179595.764000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LAUI] -> GSI 20 (level, high) -> IRQ 193
[17179595.764000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179595.860000] logips2pp: Detected unknown logitech mouse model 56
[17179596.080000] intel8x0_measure_ac97_clock: measured 52772 usecs
[17179596.080000] intel8x0: clocking to 47495
[17179596.128000] eth0: link up.
[17179596.192000] lp0: using parport0 (interrupt-driven).
[17179596.216000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179596.216000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179596.240000] Adding 208804k swap on /dev/disk/by-uuid/11858531-a45e-4a59-b4cf-d1793705fb84.  Priority:-1 extents:1 across:208804k
[17179596.324000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[17179596.344000] EXT3 FS on hda1, internal journal
[17179596.344000] ts: Compaq touchscreen protocol output
[17179596.612000] NET: Registered protocol family 17
[17179602.236000] ACPI: Power Button (FF) [PWRF]
[17179602.236000] ACPI: Power Button (CM) [PWRB]
[17179602.360000] ibm_acpi: ec object not found
[17179602.388000] pcc_acpi: loading...
[17179605.756000] NET: Registered protocol family 10
[17179605.756000] lo: Disabled Privacy Extensions
[17179605.756000] IPv6 over IPv4 tunneling driver
[17179605.964000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179605.964000] apm: overridden by ACPI.
[17179609.668000] Bluetooth: Core ver 2.8
[17179609.668000] NET: Registered protocol family 31
[17179609.668000] Bluetooth: HCI device and connection manager initialized
[17179609.668000] Bluetooth: HCI socket layer initialized
[17179609.704000] Bluetooth: L2CAP ver 2.8
[17179609.704000] Bluetooth: L2CAP socket layer initialized
[17179609.728000] Bluetooth: RFCOMM socket layer initialized
[17179609.728000] Bluetooth: RFCOMM TTY layer initialized
[17179609.728000] Bluetooth: RFCOMM ver 1.7
[17179616.324000] eth0: no IPv6 routers present
[17181206.548000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17181206.716000] ISO 9660 Extensions: RRIP_1991A
[17182657.496000] eth0: link down.
[17184409.592000] eth0: link up.

---

### Post by Iorchova on 2007-01-27
> **travs.cd said:**
> this worked for me, not 1 hour ago..

```
Open a Terminal. Applications -> Accessories -> Terminal

Loading the drivers from terminal type:

sudo modprobe tifm_sd

Now to insert a SD media card and it should auto mount.

If all went well you can now edit the the /etc/modules file so you can load the drivers for the card reader on boot up

From terminal type:

sudo gedit /etc/modules

Add the drivers to the modules file

tifm_sd

save the file 
```

That didn't work...

---

### Post by Iorchova on 2007-01-27
> **fragos said:**
> Are we talking about a laptop?  Desktop readers attach to an internal USB plug.  Some laptops use a proprietary interface instead of USB to read SD cards and it may not be supported.

It's a Desktop.

---

### Post by Metacarpal on 2007-01-29
> **travs.cd said:**
> this worked for me, not 1 hour ago..

```
Open a Terminal. Applications -> Accessories -> Terminal

Loading the drivers from terminal type:

sudo modprobe tifm_sd

Now to insert a SD media card and it should auto mount.

If all went well you can now edit the the /etc/modules file so you can load the drivers for the card reader on boot up

From terminal type:

sudo gedit /etc/modules

Add the drivers to the modules file

tifm_sd

save the file 
```

You just fixed my laptop's built-in SD card reader problem.  THANKS!

(and now for the obligatory system information to help the next guy's search...)

Toshiba Tecra A5 notebook

---

