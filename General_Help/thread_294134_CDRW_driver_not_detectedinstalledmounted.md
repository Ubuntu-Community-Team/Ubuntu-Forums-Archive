---
title: "CDRW driver not detected/installed/mounted"
date: 2006-11-06
forum: General Help
---

### Post by reynoldlariza on 2006-11-06
I have a CDRW driver... it's ok under WinXP ro, but not in ubuntu.

My Specs...

- AMD Sempron 2200+/256 MB-RAM/64MB-AGP
- HD0 ->  ubuntu drive  (1 partition only) (edge efty dist-upgraded from dapper)
- CDRW ->
- HD1 -> windows xp pro (2 partition)
- HD2 -> data drive (2 partition)

IDE 1:  both HD0 and CDRW are attached.
IDE 2: HD1 and HD2

here's what i get using dmesg:
P.S. sry if it's kind'a long i hope the full msg to be better helpful.

```

dmereynold@rel:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000fff3000 - 0000000010000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f54e0
[17179569.184000] On node 0 totalpages: 65520
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61424 pages, LIFO batch:15
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 VKT400                                ) @ 0x000f7010
[17179569.184000] ACPI: RSDT (v001 VKT400 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3000
[17179569.184000] ACPI: FADT (v001 VKT400 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3040
[17179569.184000] ACPI: MADT (v001 VKT400 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff7980
[17179569.184000] ACPI: DSDT (v001 VKT400 AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 16
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=dcd7c41e-b881-4833-b837-5fa58093864f ro single
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 1494.514 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.120000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.120000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.132000] Memory: 248980k/262080k available (1829k kernel code, 12516k reserved, 1038k data, 288k init, 0k highmem)
[17179572.132000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.212000] Calibrating delay using timer specific routine.. 2991.89 BogoMIPS (lpj=5983787)
[17179572.212000] Security Framework v1.0.0 initialized
[17179572.212000] SELinux:  Disabled at boot.
[17179572.212000] Mount-cache hash table entries: 512
[17179572.212000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179572.212000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179572.212000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.212000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.212000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[17179572.212000] CPU: AMD Sempron(tm)   2200+ stepping 01
[17179572.212000] Checking 'hlt' instruction... OK.
[17179572.228000] SMP alternatives: switching to UP code
[17179572.228000] Freeing SMP alternatives: 0k freed
[17179572.228000] checking if image is initramfs... it is
[17179572.964000] Freeing initrd memory: 6692k freed
[17179572.964000] ACPI: Core revision 20060707
[17179572.968000] ACPI: Looking for DSDT ... not found!
[17179572.972000] ENABLING IO-APIC IRQs
[17179572.972000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.116000] NET: Registered protocol family 16
[17179573.116000] EISA bus registered
[17179573.116000] ACPI: bus type pci registered
[17179573.120000] PCI: PCI BIOS revision 2.10 entry at 0xfb740, last bus=1
[17179573.120000] PCI: Using configuration type 1
[17179573.120000] Setting up standard PCI resources
[17179573.128000] ACPI: Interpreter enabled
[17179573.128000] ACPI: Using IOAPIC for interrupt routing
[17179573.128000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.128000] PCI: Probing PCI hardware (bus 00)
[17179573.132000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.132000] PCI quirk: region 4000-407f claimed by vt8235 PM
[17179573.132000] PCI quirk: region 5000-500f claimed by vt8235 SMB
[17179573.132000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179573.132000] Boot video device is 0000:01:00.0
[17179573.132000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.164000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179573.164000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 10 11 12 14 15)
[17179573.164000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[17179573.164000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[17179573.168000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.168000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.168000] ACPI: PCI Interrupt Link [LNK0] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.168000] ACPI: PCI Interrupt Link [LNK1] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[17179573.176000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.176000] pnp: PnP ACPI init
[17179573.180000] pnp: PnP ACPI: found 13 devices
[17179573.180000] PnPBIOS: Disabled by ACPI PNP
[17179573.180000] PCI: Using ACPI for IRQ routing
[17179573.180000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.208000] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[17179573.208000] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[17179573.208000] PCI: Bridge: 0000:00:01.0
[17179573.208000]   IO window: disabled.
[17179573.208000]   MEM window: e0000000-e1ffffff
[17179573.208000]   PREFETCH window: d8000000-dfffffff
[17179573.208000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.208000] NET: Registered protocol family 2
[17179573.248000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179573.248000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[17179573.248000] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.248000] TCP: Hash tables configured (established 8192 bind 4096)
[17179573.248000] TCP reno registered
[17179573.248000] audit: initializing netlink socket (disabled)
[17179573.248000] audit(1162808166.248:1): initialized
[17179573.248000] VFS: Disk quotas dquot_6.5.1
[17179573.248000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.248000] Initializing Cryptographic API
[17179573.248000] io scheduler noop registered
[17179573.248000] io scheduler anticipatory registered
[17179573.248000] io scheduler deadline registered
[17179573.248000] io scheduler cfq registered (default)
[17179573.248000] isapnp: Scanning for PnP cards...
[17179573.604000] isapnp: No Plug & Play device found
[17179573.628000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.632000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.632000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.632000] mice: PS/2 mouse device common for all mice
[17179573.632000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.632000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.632000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.632000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.632000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.632000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.632000] EISA: Probing bus 0 at eisa.0
[17179573.632000] Cannot allocate resource for EISA slot 4
[17179573.632000] Cannot allocate resource for EISA slot 5
[17179573.632000] EISA: Detected 0 cards.
[17179573.636000] TCP bic registered
[17179573.636000] NET: Registered protocol family 1
[17179573.636000] NET: Registered protocol family 8
[17179573.636000] NET: Registered protocol family 20
[17179573.636000] Using IPI Shortcut mode
[17179573.636000] ACPI: (supports S0 S1 S4 S5)
[17179573.636000] Freeing unused kernel memory: 288k freed
[17179573.656000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.700000] Capability LSM initialized
[17179573.744000] ACPI: Fan [FAN] (on)
[17179573.748000] ACPI: Thermal Zone [THRM] (40 C)
[17179574.348000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179574.348000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[17179574.348000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179574.348000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 169
[17179574.348000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 9
[17179574.348000] VP_IDE: chipset revision 6
[17179574.348000] VP_IDE: not 100% native mode: will probe irqs later
[17179574.348000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179574.348000]     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:DMA
[17179574.348000]     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:DMA
[17179574.348000] Probing IDE interface ide0...
[17179609.148000] ide0: Wait for ready failed before probe !
[17179609.784000] hdb: ST320413A, ATA DISK drive
[17179609.840000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179609.840000] Probing IDE interface ide1...
[17179610.256000] hdc: ExcelStor Technology J840, ATA DISK drive
[17179610.536000] hdd: ExcelStor Technology J240, ATA DISK drive
[17179610.592000] ide1 at 0x170-0x177,0x376 on irq 15
[17179610.616000] hdb: max request size: 128KiB
[17179610.628000] hdb: 39102336 sectors (20020 MB) w/512KiB Cache, CHS=38792/16/63, UDMA(33)
[17179610.628000] hdb: cache flushes not supported
[17179610.628000]  hdb: hdb1 hdb2 < hdb5 >
[17179610.680000] hdc: max request size: 512KiB
[17179610.680000] hdc: 80418240 sectors (41174 MB) w/1719KiB Cache, CHS=16383/255/63, UDMA(133)
[17179610.680000] hdc: cache flushes supported
[17179610.680000]  hdc: hdc1 hdc2 < hdc5 >
[17179610.700000] hdd: max request size: 128KiB
[17179610.700000] hdd: 80418240 sectors (41174 MB) w/1863KiB Cache, CHS=65535/15/63, UDMA(100)
[17179610.704000] hdd: cache flushes supported
[17179610.704000]  hdd:<4>hdd: dma_timer_expiry: dma status == 0x61
[17179640.704000] hdd: DMA timeout error
[17179640.704000] hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
[17179640.704000] ide: failed opcode was: unknown
[17179640.704000]  hdd1 hdd2 <<4>hdd: dma_timer_expiry: dma status == 0x61
[17179670.704000] hdd: DMA timeout error
[17179670.704000] hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
[17179670.704000] ide: failed opcode was: unknown
[17179670.708000]  hdd5<4>hdd: dma_timer_expiry: dma status == 0x61
[17179700.712000] hdd: DMA timeout error
[17179700.712000] hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
[17179700.712000] ide: failed opcode was: unknown
[17179700.716000]  hdd6 >
[17179720.784000] hdd: dma_timer_expiry: dma status == 0x61
[17179730.784000] hdd: DMA timeout error
[17179730.784000] hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
[17179730.784000] ide: failed opcode was: unknown
[17179731.524000] usbcore: registered new driver usbfs
[17179731.524000] usbcore: registered new driver hub
[17179731.524000] USB Universal Host Controller Interface driver v3.0
[17179731.528000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[17179731.528000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179731.528000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179731.528000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 1
[17179731.528000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179731.528000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179731.528000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000d000
[17179731.528000] usb usb1: configuration #1 chosen from 1 choice
[17179731.528000] hub 1-0:1.0: USB hub found
[17179731.528000] hub 1-0:1.0: 2 ports detected
[17179731.632000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179731.632000] PCI: Via IRQ fixup for 0000:00:10.1, from 3 to 1
[17179731.632000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179731.632000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179731.632000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000d400
[17179731.632000] usb usb2: configuration #1 chosen from 1 choice
[17179731.632000] hub 2-0:1.0: USB hub found
[17179731.632000] hub 2-0:1.0: 2 ports detected
[17179731.736000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179731.736000] PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 1
[17179731.736000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179731.736000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179731.736000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000d800
[17179731.736000] usb usb3: configuration #1 chosen from 1 choice
[17179731.736000] hub 3-0:1.0: USB hub found
[17179731.736000] hub 3-0:1.0: 2 ports detected
[17179731.840000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179731.840000] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 1
[17179731.840000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179731.840000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179731.840000] ehci_hcd 0000:00:10.3: irq 177, io mem 0xe2000000
[17179731.844000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179731.844000] usb usb4: configuration #1 chosen from 1 choice
[17179731.844000] hub 4-0:1.0: USB hub found
[17179731.844000] hub 4-0:1.0: 6 ports detected
[17179732.032000] Attempting manual resume
[17179732.124000] kjournald starting.  Commit interval 5 seconds
[17179732.124000] EXT3-fs: mounted filesystem with ordered data mode.
[17179750.872000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179750.888000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179751.084000] Floppy drive(s): fd0 is 1.44M
[17179751.104000] FDC 0 is a post-1991 82077
[17179751.328000] parport: PnPBIOS parport detected.
[17179751.328000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179751.460000] Real Time Clock Driver v1.12ac
[17179751.524000] Linux agpgart interface v0.101 (c) Dave Jones
[17179751.528000] agpgart: Detected VIA KM400/KM400A chipset
[17179751.540000] agpgart: AGP aperture is 128M @ 0xd0000000
[17179751.820000] irda_init()
[17179751.820000] NET: Registered protocol family 23
[17179752.220000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179752.220000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179752.220000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 185
[17179752.220000] PCI: Via IRQ fixup for 0000:00:11.5, from 10 to 9
[17179752.220000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179752.492000] nvidia: module license 'NVIDIA' taints kernel.
[17179752.536000] input: PC Speaker as /class/input/input1
[17179752.736000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179752.736000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179753.088000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179753.088000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[17179753.088000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[17179753.088000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 201
[17179753.088000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 9
[17179753.092000] eth0: VIA Rhine II at 0x1e800, 00:11:5b:33:f2:7d, IRQ 201.
[17179753.092000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179753.160000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179753.428000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179753.508000] ts: Compaq touchscreen protocol output
[17179753.988000] lp0: using parport0 (interrupt-driven).
[17179754.088000] fuse init (API version 7.6)
[17179754.216000] NET: Registered protocol family 10
[17179754.216000] lo: Disabled Privacy Extensions
[17179754.216000] IPv6 over IPv4 tunneling driver
[17179754.304000] Adding 746980k swap on /dev/disk/by-uuid/6d46e7f1-0917-4826-a47d-ffbcfe9e0e6f.  Priority:-1 extents:1 across:746980k
[17179754.656000] EXT3 FS on hdb1, internal journal
[17179754.924000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179754.924000] md: bitmap version 4.39
[17179755.164000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[17179765.112000] eth0: no IPv6 routers present
[17179807.824000] NET: Registered protocol family 17
[17179836.200000] ACPI: Power Button (FF) [PWRF]
[17179836.200000] ACPI: Power Button (CM) [PWRB]
[17179836.200000] ACPI: Sleep Button (CM) [SLPB]
[17179836.344000] ibm_acpi: ec object not found
[17179836.384000] pcc_acpi: loading...
[17179837.100000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179845.040000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179845.040000] agpgart: Device is in legacy mode, falling back to 2.x
[17179845.040000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179845.040000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179850.264000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179850.264000] apm: overridden by ACPI.
[17179870.208000] Bluetooth: Core ver 2.8
[17179870.208000] NET: Registered protocol family 31
[17179870.208000] Bluetooth: HCI device and connection manager initialized
[17179870.208000] Bluetooth: HCI socket layer initialized
[17179870.308000] Bluetooth: L2CAP ver 2.8
[17179870.308000] Bluetooth: L2CAP socket layer initialized
[17179870.476000] Bluetooth: RFCOMM socket layer initialized
[17179870.476000] Bluetooth: RFCOMM TTY layer initialized
[17179870.476000] Bluetooth: RFCOMM ver 1.7


```

Thanks in advance.

---

