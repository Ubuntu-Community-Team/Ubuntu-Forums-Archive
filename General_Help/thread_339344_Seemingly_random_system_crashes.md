---
title: "Seemingly random system crashes"
date: 2007-01-15
forum: General Help
---

### Post by kombucha on 2007-01-15
Well, at first I thought it was bittorrent clients causing my frequent system crashes, so I stopped using those. I also uninstalled Beryl, because I feel like these crashes started around the same time. And yet, the crashes continue. I can just be surfing the internet and listening to music, and all of a sudden the music will go crazy (loop on one note), the mouse will lock up, and everything freezes, forcing a hard restart.
I know this is an incredibly broad thing to troubleshoot, but I have NO idea what to do. Is there a way I can log everything that's going in, in hopes of identifying the source? This is incredibly frustrating... 
I'd love any ideas, I'm desperate... this is driving me insane and making any work extremely difficult.
The crashes occur maybe once every hour or two, although they are very irregular and I've gone for maybe five or six without a lockup.
Thanks in advance!!!
:(

---

### Post by mlissner on 2007-01-20
I'd suggest posting the result of running dmesg in the terminal. It wouldn't mean much to me, but it might have some clues.

---

### Post by kombucha on 2007-01-20
I have no idea how much to post... here's what's visible in Konsole after I run it:

> [17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version
4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26
UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6140
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 KM266                                 ) @ 0x0
00f7bf0
[17179569.184000] ACPI: RSDT (v001 KM266  AWRDACPI 0x42302e31 AWRD 0x00000000) @
 0x1fff3000
[17179569.184000] ACPI: FADT (v001 KM266  AWRDACPI 0x42302e31 AWRD 0x00000000) @
 0x1fff3040
[17179569.184000] ACPI: MADT (v001 KM266  AWRDACPI 0x42302e31 AWRD 0x00000000) @
 0x1fff7400
[17179569.184000] ACPI: DSDT (v001 KM266  AWRDACPI 0x00001000 MSFT 0x0100000e) @
 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:6 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:d
ec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdc1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1665.601 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.876000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes
)
[17179572.876000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.896000] Memory: 510056k/524224k available (1910k kernel code, 13556k r
eserved, 1069k data, 308k init, 0k highmem)
[17179572.896000] Checking if this processor honours the WP bit even in supervis
or mode... Ok.
[17179572.976000] Calibrating delay using timer specific routine.. 3334.31 BogoM
IPS (lpj=6668637)
[17179572.976000] Security Framework v1.0.0 initialized
[17179572.976000] SELinux:  Disabled at boot.
[17179572.976000] Mount-cache hash table entries: 512
[17179572.976000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000
00000000 00000000 00000000 00000000
[17179572.976000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 0
0000000 00000000 00000000 00000000
[17179572.976000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/li
ne)
[17179572.976000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.976000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 0000042
0 00000000 00000000 00000000
[17179572.976000] Checking 'hlt' instruction... OK.
[17179572.992000] SMP alternatives: switching to UP code
[17179572.992000] Freeing SMP alternatives: 16k freed
[17179572.992000] checking if image is initramfs... it is
[17179573.544000] Freeing initrd memory: 5282k freed
[17179573.544000] ACPI: Core revision 20060707
[17179573.548000] ACPI: Looking for DSDT ... not found!
[17179573.608000] CPU0: AMD Athlon(tm) XP 2000+ stepping 02
[17179573.608000] Total of 1 processors activated (3334.31 BogoMIPS).
[17179573.612000] ENABLING IO-APIC IRQs
[17179573.612000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.756000] Brought up 1 CPUs
[17179573.756000] migration_cost=0
[17179573.756000] NET: Registered protocol family 16
[17179573.756000] EISA bus registered
[17179573.756000] ACPI: bus type pci registered
[17179573.756000] PCI: PCI BIOS revision 2.10 entry at 0xfba00, last bus=1
[17179573.756000] PCI: Using configuration type 1
[17179573.756000] Setting up standard PCI resources
[17179573.772000] ACPI: Interpreter enabled
[17179573.772000] ACPI: Using IOAPIC for interrupt routing
[17179573.772000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.772000] PCI: Probing PCI hardware (bus 00)
[17179573.772000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.776000] PCI quirk: region 4000-407f claimed by vt8235 PM
[17179573.776000] PCI quirk: region 5000-500f claimed by vt8235 SMB
[17179573.776000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179573.776000] Boot video device is 0000:01:00.0
[17179573.776000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.808000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[17179573.808000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
[17179573.808000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[17179573.808000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 6 7 10 11 12)
[17179573.808000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, di
sabled.
[17179573.808000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, di
sabled.
[17179573.808000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, di
sabled.
[17179573.808000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, di
sabled.
[17179573.808000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179573.808000] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[17179573.812000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[17179573.812000] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[17179573.812000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.812000] pnp: PnP ACPI init
[17179573.816000] pnp: PnP ACPI: found 13 devices
[17179573.816000] PnPBIOS: Disabled by ACPI PNP
[17179573.820000] PCI: Using ACPI for IRQ routing
[17179573.820000] PCI: If a device doesn't work, try "pci=routeirq".  If it help
s, post a report
[17179573.848000] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[17179573.848000] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[17179573.848000] PCI: Bridge: 0000:00:01.0
[17179573.848000]   IO window: c000-cfff
[17179573.848000]   MEM window: ec000000-edffffff
[17179573.848000]   PREFETCH window: e0000000-e7ffffff
[17179573.848000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.848000] NET: Registered protocol family 2
[17179573.888000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes
)
[17179573.888000] TCP established hash table entries: 16384 (order: 5, 131072 by
tes)
[17179573.888000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.888000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.888000] TCP reno registered
[17179573.888000] audit: initializing netlink socket (disabled)
[17179573.888000] audit(1169330588.888:1): initialized
[17179573.888000] VFS: Disk quotas dquot_6.5.1
[17179573.888000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.888000] Initializing Cryptographic API
[17179573.888000] io scheduler noop registered
[17179573.888000] io scheduler anticipatory registered
[17179573.888000] io scheduler deadline registered
[17179573.888000] io scheduler cfq registered (default)
[17179573.888000] isapnp: Scanning for PnP cards...
[17179574.244000] isapnp: No Plug & Play device found
[17179574.268000] Real Time Clock Driver v1.12ac
[17179574.268000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ shari
ng enabled
[17179574.272000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.272000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.272000] mice: PS/2 mouse device common for all mice
[17179574.272000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b
locksize
[17179574.272000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.272000] ide: Assuming 33MHz system bus speed for PIO modes; override w
ith idebus=xx
[17179574.272000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64
irq 1,12
[17179574.272000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.272000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.272000] EISA: Probing bus 0 at eisa.0
[17179574.272000] Cannot allocate resource for EISA slot 4
[17179574.272000] Cannot allocate resource for EISA slot 5
[17179574.272000] EISA: Detected 0 cards.
[17179574.272000] TCP bic registered
[17179574.272000] NET: Registered protocol family 1
[17179574.272000] NET: Registered protocol family 8
[17179574.272000] NET: Registered protocol family 20
[17179574.272000] Using IPI No-Shortcut mode
[17179574.272000] ACPI: (supports S0 S1 S3 S4 S5)
[17179574.276000] Freeing unused kernel memory: 308k freed
[17179574.304000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.424000] Capability LSM initialized
[17179575.464000] ACPI: Fan [FAN] (on)
[17179575.468000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.468000] ACPI: Thermal Zone [THRM] (40 C)
[17179576.092000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179576.092000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ
 20
[17179576.092000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179576.092000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (
level, low) -> IRQ 169
[17179576.092000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 9
[17179576.092000] VP_IDE: chipset revision 6
[17179576.092000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.092000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:
00:11.1
[17179576.092000]     ide0: BM-DMA at 0xe400-0xe407, BIOS settings: hda:DMA, hdb
:DMA
[17179576.092000]     ide1: BM-DMA at 0xe408-0xe40f, BIOS settings: hdc:DMA, hdd
:DMA
[17179576.092000] Probing IDE interface ide0...
[17179576.528000] hda: ST340810A, ATA DISK drive
[17179576.824000] hdb: Maxtor 6Y060L0, ATA DISK drive
[17179576.888000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.908000] Probing IDE interface ide1...
[17179577.336000] hdc: WDC WD200EB-00CPF0, ATA DISK drive
[17179577.796000] hdd: HL-DT-STDVD-ROM GDR8161B, ATAPI CD/DVD-ROM drive
[17179577.864000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.900000] hda: max request size: 128KiB
[17179577.924000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16
/63, UDMA(100)
[17179577.924000] hda: cache flushes not supported
[17179577.924000]  hda: hda1 hda2 < hda5 >
[17179577.948000] hdb: max request size: 128KiB
[17179577.948000] hdb: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/1
6/63, UDMA(133)
[17179577.948000] hdb: cache flushes supported
[17179577.948000]  hdb: hdb1
[17179577.956000] hdc: max request size: 128KiB
[17179577.956000] hdc: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16
/63, UDMA(100)
[17179577.956000] hdc: cache flushes not supported
[17179577.956000]  hdc: hdc1 hdc2 < hdc5 >
[17179578.044000] hdd: ATAPI 48X DVD-ROM drive, 256kB Cache, UDMA(33)
[17179578.044000] Uniform CD-ROM driver Revision: 3.20
[17179578.216000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179578.216000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179578.216000] ide: failed opcode was: unknown
[17179578.516000] ieee1394: Initialized config rom entry `ip1394'
[17179578.520000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) ->
IRQ 177
[17179578.604000] usbcore: registered new driver usbfs
[17179578.604000] usbcore: registered new driver hub
[17179578.608000] USB Universal Host Controller Interface driver v3.0
[17179578.620000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[177]  MMIO=[ef10
3000-ef1037ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[17179578.628000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ
 21
[17179578.628000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179578.628000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (
level, low) -> IRQ 185
[17179578.628000] PCI: Via IRQ fixup for 0000:00:10.0, from 255 to 9
[17179578.628000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179578.628000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus nu
mber 1
[17179578.628000] uhci_hcd 0000:00:10.0: irq 185, io base 0x0000d800
[17179578.628000] usb usb1: configuration #1 chosen from 1 choice
[17179578.628000] hub 1-0:1.0: USB hub found
[17179578.628000] hub 1-0:1.0: 2 ports detected
[17179578.736000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKB] -> GSI 21 (
level, low) -> IRQ 185
[17179578.736000] PCI: Via IRQ fixup for 0000:00:10.1, from 255 to 9
[17179578.736000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179578.736000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus nu
mber 2
[17179578.736000] uhci_hcd 0000:00:10.1: irq 185, io base 0x0000dc00
[17179578.736000] usb usb2: configuration #1 chosen from 1 choice
[17179578.736000] hub 2-0:1.0: USB hub found
[17179578.736000] hub 2-0:1.0: 2 ports detected
[17179578.840000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKB] -> GSI 21 (
level, low) -> IRQ 185
[17179578.840000] PCI: Via IRQ fixup for 0000:00:10.2, from 255 to 9
[17179578.840000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179578.840000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus nu
mber 3
[17179578.840000] uhci_hcd 0000:00:10.2: irq 185, io base 0x0000e000
[17179578.840000] usb usb3: configuration #1 chosen from 1 choice
[17179578.840000] hub 3-0:1.0: USB hub found
[17179578.840000] hub 3-0:1.0: 2 ports detected
[17179578.948000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKB] -> GSI 21 (
level, low) -> IRQ 185
[17179578.948000] PCI: Via IRQ fixup for 0000:00:10.3, from 255 to 9
[17179578.948000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179578.948000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus nu
mber 4
[17179578.948000] ehci_hcd 0000:00:10.3: irq 185, io mem 0xef104000
[17179578.948000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 D
ec 2004
[17179578.948000] usb usb4: configuration #1 chosen from 1 choice
[17179578.948000] hub 4-0:1.0: USB hub found
[17179578.948000] hub 4-0:1.0: 6 ports detected
[17179578.996000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179579.104000] Attempting manual resume
[17179579.116000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179579.116000] EXT3-fs: write access will be enabled during recovery.
[17179579.308000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179579.308000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179579.308000] ide: failed opcode was: unknown
[17179579.912000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00051600005469bc
]
[17179580.168000] usb 4-3: new high speed USB device using ehci_hcd and address
3
[17179580.300000] usb 4-3: configuration #1 chosen from 1 choice
[17179580.676000] usbcore: registered new driver libusual
[17179580.688000] SCSI subsystem initialized
[17179580.692000] Initializing USB Mass Storage driver...
[17179580.916000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[17179581.104000] usb 1-1: configuration #1 chosen from 1 choice
[17179581.356000] usb 2-2: new full speed USB device using uhci_hcd and address
2
[17179581.524000] usb 2-2: configuration #1 chosen from 1 choice
[17179581.776000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[17179581.952000] usb 3-1: configuration #1 chosen from 1 choice
[17179581.972000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179581.972000] usb-storage: device found at 3
[17179581.972000] usb-storage: waiting for device to settle before scanning
[17179581.972000] usbcore: registered new driver usb-storage
[17179581.972000] USB Mass Storage support registered.
[17179581.972000] usbcore: registered new driver hiddev
[17179582.000000] input: SAITEK P880 as /class/input/input1
[17179582.000000] input: USB HID v1.00 Joystick [SAITEK P880] on usb-0000:00:10.
2-1
[17179582.000000] usbcore: registered new driver usbhid
[17179582.000000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179585.176000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179585.176000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179585.176000] ide: failed opcode was: unknown
[17179585.176000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179585.176000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179585.176000] ide: failed opcode was: unknown
[17179585.196000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179585.196000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179585.196000] ide: failed opcode was: unknown
[17179585.196000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179585.196000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179585.196000] ide: failed opcode was: unknown
[17179585.212000] hdd: DMA disabled
[17179585.264000] ide1: reset: success
[17179586.972000] usb-storage: device scan complete
[17179586.972000]   Vendor: Seagate   Model: External Drive    Rev:
[17179586.972000]   Type:   Direct-Access                      ANSI SCSI revisio
n: 00
[17179586.984000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179586.984000] sda: Write Protect is off
[17179586.984000] sda: Mode Sense: 27 00 00 00
[17179586.984000] sda: assuming drive cache: write through
[17179586.984000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179586.984000] sda: Write Protect is off
[17179586.984000] sda: Mode Sense: 27 00 00 00
[17179586.984000] sda: assuming drive cache: write through
[17179586.984000]  sda: sda1
[17179587.008000] sd 0:0:0:0: Attached scsi disk sda
[17179587.972000] kjournald starting.  Commit interval 5 seconds
[17179587.972000] EXT3-fs: hdc1: orphan cleanup on readonly fs
[17179587.972000] ext3_orphan_cleanup: deleting unreferenced inode 1671593
[17179587.972000] ext3_orphan_cleanup: deleting unreferenced inode 1671587
[17179587.972000] EXT3-fs: hdc1: 2 orphan inodes deleted
[17179587.972000] EXT3-fs: recovery complete.
[17179587.996000] EXT3-fs: mounted filesystem with ordered data mode.
[17179588.200000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179588.200000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179588.200000] ide: failed opcode was: unknown
[17179588.200000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179588.200000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179588.200000] ide: failed opcode was: unknown
[17179589.068000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179589.068000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179589.068000] ide: failed opcode was: unknown
[17179589.068000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179589.068000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179589.068000] ide: failed opcode was: unknown
[17179589.084000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179589.084000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179589.084000] ide: failed opcode was: unknown
[17179589.088000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179589.088000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179589.088000] ide: failed opcode was: unknown
[17179589.140000] ide1: reset: success
[17179600.284000] irda_init()
[17179600.284000] NET: Registered protocol family 23
[17179600.304000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179600.312000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179600.692000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17179600.692000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17179600.692000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17179600.692000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17179600.724000]
[17179600.724000] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[17179600.724000] Copyright (c) 2004-2005, Andrea Merello
[17179600.724000] rtl8180: Initializing module
[17179600.724000] rtl8180: Wireless extensions version 20
[17179600.724000] rtl8180: Initializing proc filesystem
[17179600.724000] rtl8180: Configuring chip resources
[17179600.724000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) ->
IRQ 193
[17179600.724000] rtl8180: Memory mapped space @ 0xef101000
[17179600.724000] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[17179600.724000] rtl8180: This is a PCI NIC
[17179600.724000] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[17179600.732000] rtl8180: Card MAC address is 00:13:49:54:9d:4e
[17179600.744000] rtl8180: EEPROM version 105
[17179600.748000] rtl8180: Card reports RF frontend Realtek 8225
[17179600.748000] rtl8180: WW:This driver has EXPERIMENTAL support for this chip
set.
[17179600.748000] rtl8180: WW:use it with care and at your own risk and
[17179600.748000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@t
iscali.it
[17179600.748000] rtl8180: Energy threshold: b
[17179600.748000] rtl8180: PAPE from CONFIG2: 6
[17179600.748000] rtl8180: IRQ 193
[17179600.748000] rtl8180: Driver probe completed
[17179600.748000]
[17179600.816000] parport: PnPBIOS parport detected.
[17179600.816000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRIST
ATE,COMPAT,ECP,DMA]
[17179600.880000] input: PC Speaker as /class/input/input2
[17179601.040000] logips2pp: Detected unknown logitech mouse model 1
[17179601.220000] input: PS/2 Logitech Mouse as /class/input/input3
[17179601.404000] Linux agpgart interface v0.101 (c) Dave Jones
[17179601.452000] Floppy drive(s): fd0 is 1.44M
[17179601.468000] FDC 0 is a post-1991 82077
[17179601.504000] 8139too Fast Ethernet driver 0.9.27
[17179601.508000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) ->
IRQ 201
[17179601.508000] eth0: RealTek RTL8139 at 0xe09ac000, 00:40:ca:43:cd:68, IRQ 20
1
[17179601.508000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179601.520000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179601.720000] input: Wacom Graphire4 4x5 as /class/input/input4
[17179601.744000] usbcore: registered new driver wacom
[17179601.744000] drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom
Intuos tablet driver
[17179601.756000] agpgart: Detected VIA PM266/KM266 chipset
[17179601.760000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179602.128000] Bluetooth: Core ver 2.8
[17179602.128000] NET: Registered protocol family 31
[17179602.128000] Bluetooth: HCI device and connection manager initialized
[17179602.128000] Bluetooth: HCI socket layer initialized
[17179602.176000] Bluetooth: HCI USB driver ver 2.9
[17179602.180000] usbcore: registered new driver hci_usb
[17179602.448000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) ->
IRQ 201
[17179602.672000] rtl8180: Bringing up iface
[17179602.880000] rtl8180: Card successfully reset
[17179606.568000] gameport: CS46xx Gameport is pci0000:00:0a.0/gameport0, speed
1529kHz
[17179606.636000] ts: Compaq touchscreen protocol output
[17179606.868000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179607.168000] eth0: link down
[17179607.352000] lp0: using parport0 (interrupt-driven).
[17179607.380000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1
)
[17179607.380000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179607.436000] fuse init (API version 7.6)
[17179607.484000] Adding 835340k swap on /dev/disk/by-uuid/69aa37c5-669b-478e-ad
ba-c838d396e98d.  Priority:-1 extents:1 across:835340k
[17179607.572000] EXT3 FS on hdc1, internal journal
[17179608.224000] NET: Registered protocol family 17
[17179613.024000] ACPI: Power Button (FF) [PWRF]
[17179613.024000] ACPI: Power Button (CM) [PWRB]
[17179613.184000] ibm_acpi: ec object not found
[17179613.240000] pcc_acpi: loading...
[17179614.740000] Linking with ZyXEL
[17179614.756000] Associated successfully
[17179614.756000] Using G rates
[17179615.384000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179615.384000] apm: overridden by ACPI.
[17179615.424000] [drm] Initialized drm 1.0.1 20051102
[17179615.444000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) ->
IRQ 193
[17179615.448000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179616.604000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000
000
[17179616.604000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000                                   000
[17179616.608000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000                                   000
[17179616.608000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179616.608000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179616.608000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179616.904000] [drm] Setting GART location based on new memory map
[17179616.904000] [drm] Loading R200 Microcode
[17179616.904000] [drm] writeback test succeeded in 1 usecs
[17179617.144000] NET: Registered protocol family 10
[17179617.144000] lo: Disabled Privacy Extensions
[17179617.144000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179617.144000] IPv6 over IPv4 tunneling driver
[17179622.340000] Bluetooth: L2CAP ver 2.8
[17179622.340000] Bluetooth: L2CAP socket layer initialized
[17179622.468000] Bluetooth: RFCOMM socket layer initialized
[17179622.468000] Bluetooth: RFCOMM TTY layer initialized
[17179622.468000] Bluetooth: RFCOMM ver 1.7
[17179627.536000] wlan0: no IPv6 routers present
[17179649.692000] FAT: utf8 is not a recommended IO charset for FAT filesystems,                                    filesystem will be case sensitive!


Hope that helps... I don't really understand the timecodes but there was a crash at 10:02 PM.

Also, I just reinstalled Kubuntu two days ago, so I'm surprised this is still happening... hope that helps. If this doesn't stop, I might have to bail on Kubuntu, which I really don't want to do because I don't like any other distro :( but this is hard to work with... three times today already. I've started a list to track programs I was using at the time, the most recent crash was KTorrent, Gaim, Firefox and Amarok, and I know for a fact I've crashed many times without Gaim, KTorrent or Amarok running.

---

### Post by kombucha on 2007-01-21
Well, it just happened after being left alone for about 45 minutes, while Amarok and KTorrent were running, so it clearly isn't Firefox, or any program that I manually run. Is there a way to figure out if it is a specific service? My money might be on wacom-tools.... but I wouldn't use Kubuntu without them.... do I have to uninstall them to test? Is there no other way?

---

### Post by kombucha on 2007-01-21
It seems as though this could be very related to [https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/16873](https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/16873) and/or [https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/30447](https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/30447) , which is very disheartening because many of the issues mentioned there are unresolved. I tried out a few potential solutions, which I have low hopes for, but we'll see. I'm unwilling to use Linux without 3D support, and as such have to use the "ati" driver for my Radeon 9000.

---

### Post by miguelquiros on 2007-01-27
Hello. I think I have the same experience. From time to time, everything freezes in the computer, mouse and keyboard do not respond at all and even the software clock at the upper right corner get stopped.
And the curious thing is that, if you are patient, a few minutes later (from 2 to 10 minutes) the computer gets back to life in the same point it froze and goes on working from that point as if nothings had happened!!! Only the clock appears several minutes delayed (exactly the time the computer was stopped).
I have had a look at all log files in /var/log and but I cannot see anything appearing at the time that the thing happened.
As you say, this happens entirely ramdomly. it is clearly not related with the program that is running at that moment, if some sound is emerging at that moment, the same note keeps repeating while the freeze is on the run. Somethimes, it does not happen for several days, somethings it happens twice or three times a day! It is not reproducible at all: I cannot deduce if is related with the kernel or with some hardware flaw or what ... Below, you can find the output of lspci in order to get a list of the hardware present in my computer, if you compare with your output of lspci, perhaps we can guess what is the hardware piece responsible for the problem.

Also, when the computer starts up I got in the console the message "Cannot allocate resource region 3 of device 0000:00:00.00" a few seconds just before the Ubuntu symbol shows up and the normal start up procedure takes place. I do not know if it is related to the problem (probably not) but I indicate it just in case ...

Best wishes.

Output of lspci:

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a33 (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d3 (rev a1)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by miguelquiros on 2007-01-31
Hello again. As I have found in several other threads that the nvidia Xorg module may cause crashes and freezes, I have changed "nv" by "vesa" in my xorg.conf file in order to use the vesa module instead and a couple of days later the freeze with the same features appeared again. So I think we can eliminate the nv module as the responsible of the problem. 
As the vesa module also worsenes the graphic performance (for example quite slow scrolls in firefox with the mouse wheel), I have switched back to nv module.

---

### Post by AllanP on 2007-02-02
I also have the odd freeze. Usually when I am away, come back to the puter and the screen saver hasn't activated. Everything is locked up and have to hit reset button to reboot. I notice we have one thing in common in our System log: "DriveReady SeekComplete Error". This message is repeated many times before I rebooted. It is not there now.

Regards, Allan

---

### Post by datakid on 2007-02-13
I'm getting random crashes as well - although no freezes.

I've got ubuntu edgy on a brand new dell dimension 9200, and it's mostly when I run firefox, amarok and gaim. When I've got fx loaded, I can't get any sound out of amarok. If I start amarok first, it seems to be fine, but then fx will crash over and over again.

I'm also getting the crashes in epiphany and galeon, although I use those browsers a lot less often.

I've also noticed that the crashes can/will happen when I'm on a flash-based page in firefox (eg youtube). I've got the flashplayer-mozilla installed, as well as the libflash-mozplugin and libflash-swfplayer (do I need all 3, or will one of those suffice)

---

### Post by AllanP on 2007-02-13
Logic in my opinion would say no re the multiple Java but, I'm not the one to ask. I am savvy enough to keep myself out of trouble but, with Java, Flash etc., I just turn the key and hope it starts.
My freezes are very sporatic in fact, I don't think I have had one in over a week. Hopefully updates have corrected what ever was wrong.

Regards, Allan

---

### Post by miguelquiros on 2007-02-28
Hello. I think I have solved my freezes by playing with the cpufreq system. More details in my post at another related thread:

[http://www.ubuntuforums.org/showthread.php?t=352218](http://www.ubuntuforums.org/showthread.php?t=352218)

Good luck!

---

### Post by jonthysell on 2007-11-04
> **kombucha said:**
> [17179600.724000] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[17179600.724000] Copyright (c) 2004-2005, Andrea Merello
[17179600.724000] rtl8180: Initializing module
[17179600.724000] rtl8180: Wireless extensions version 20
[17179600.724000] rtl8180: Initializing proc filesystem
[17179600.724000] rtl8180: Configuring chip resources
[17179600.724000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) ->
IRQ 193
[17179600.724000] rtl8180: Memory mapped space @ 0xef101000
[17179600.724000] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[17179600.724000] rtl8180: This is a PCI NIC
[17179600.724000] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[17179600.732000] rtl8180: Card MAC address is 00:13:49:54:9d:4e
[17179600.744000] rtl8180: EEPROM version 105
[17179600.748000] rtl8180: Card reports RF frontend Realtek 8225
[17179600.748000] rtl8180: WW:This driver has EXPERIMENTAL support for this chip
set.
[17179600.748000] rtl8180: WW:use it with care and at your own risk and
[17179600.748000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@t
iscali.it
[17179600.748000] rtl8180: Energy threshold: b
[17179600.748000] rtl8180: PAPE from CONFIG2: 6
[17179600.748000] rtl8180: IRQ 193
[17179600.748000] rtl8180: Driver probe completed

I'm having the same freezing problem with the Realtek RTL8185 wireless card. Causes random system freezes in both Gutsy and WinXP, especially when transferring large files for continuous periods. Freezes stop when I disable the card.

Also have an ATI x1300 though, so it may be a conflict of the ATI card and the Realtek card.

---

### Post by zippy028 on 2007-11-04
May not be the most user friendly set of instructions but my Ubuntu desktop has been working superbly for about a week now after using an older driver version from Nvidia.

[My Fix]("http://ubuntuforums.org/showthread.php?t=594196&highlight=freezes+resolve")

---

