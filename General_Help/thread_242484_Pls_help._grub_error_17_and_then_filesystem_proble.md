---
title: "Pls help. grub error 17 and then filesystem problems. dmesg in post"
date: 2006-08-23
forum: General Help
---

### Post by theadventuresofanidealist on 2006-08-23
tried some of the grub help in the forum, but nothing helped.
i have very important data on the partition which might have the fiesystem problem. i cant afford to loose it. i have a dual boot windows xp / Xubuntu. dont know what else to do.
here's my dmesg :

ubuntu@ubuntu:~$ dmesg
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4. 0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000002fff0000 - 000000002fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000002fff8000 - 0000000030000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffee0000 - 00000000fff0ffff (reserved)
[17179569.184000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 767MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 196592
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 192496 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x0 00fa310
[17179569.184000] ACPI: RSDT (v001 AMIINT SiS645XX 0x00000010 MSFT 0x0100000b) @  0x2fff0000
[17179569.184000] ACPI: FADT (v002 AMIINT SiS645XX 0x00000011 MSFT 0x0100000b) @  0x2fff0030
[17179569.184000] ACPI: DSDT (v001    SiS      645 0x00001000 MSFT 0x0100000d) @  0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 30000000:c fee0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz preseed/file=/ cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=104 8576 root=/dev/ram rw quiet splash --
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01603000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1992.319 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.488000] Dentry cache hash table entries: 131072 (order: 7, 524288 byte s)
[17179569.492000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.528000] Memory: 768692k/786368k available (1976k kernel code, 17116k r eserved, 606k data, 288k init, 0k highmem)
[17179569.528000] Checking if this processor honours the WP bit even in supervis or mode... Ok.
[17179569.608000] Calibrating delay using timer specific routine.. 3987.73 BogoM IPS (lpj=7975477)
[17179569.608000] Security Framework v1.0.0 initialized
[17179569.608000] SELinux:  Disabled at boot.
[17179569.608000] Mount-cache hash table entries: 512
[17179569.608000] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.608000] CPU: After vendor identify, caps: 3febf9ff 00000000 00000000 0 0000000 00000000 00000000 00000000
[17179569.608000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179569.608000] CPU: L2 cache: 512K
[17179569.608000] CPU: After all inits, caps: 3febf9ff 00000000 00000000 0000008 0 00000000 00000000 00000000
[17179569.608000] mtrr: v2.0 (20020519)
[17179569.608000] CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
[17179569.608000] Enabling fast FPU save and restore... done.
[17179569.608000] Enabling unmasked SIMD FPU exception support... done.
[17179569.608000] Checking 'hlt' instruction... OK.
[17179569.624000] checking if image is initramfs... it is
[17179570.400000] Freeing initrd memory: 6843k freed
[17179570.424000] ACPI: Looking for DSDT ... not found!
[17179570.428000] ACPI: setting ELCR to 0200 (from 1820)
[17179570.428000] NET: Registered protocol family 16
[17179570.428000] EISA bus registered
[17179570.428000] ACPI: bus type pci registered
[17179570.428000] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[17179570.428000] PCI: Using configuration type 1
[17179570.432000] ACPI: Subsystem revision 20051216
[17179570.436000] ACPI: Interpreter enabled
[17179570.436000] ACPI: Using PIC for interrupt routing
[17179570.436000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.436000] PCI: Probing PCI hardware (bus 00)
[17179570.440000] Uncovering SIS961 that hid as a SIS503 (compatible=1)
[17179570.440000] Enabling SiS 96x SMBus.
[17179570.440000] Boot video device is 0000:01:00.0
[17179570.440000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.448000] ACPI: Power Resource [URP1] (off)
[17179570.448000] ACPI: Power Resource [URP2] (off)
[17179570.448000] ACPI: Power Resource [FDDP] (off)
[17179570.448000] ACPI: Power Resource [LPTP] (off)
[17179570.448000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179570.448000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.448000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.448000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179570.448000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179570.448000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179570.448000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.452000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 *12 14 15)
[17179570.452000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.452000] pnp: PnP ACPI init
[17179570.456000] pnp: PnP ACPI: found 11 devices
[17179570.456000] PnPBIOS: Disabled by ACPI PNP
[17179570.456000] PCI: Using ACPI for IRQ routing
[17179570.456000] PCI: If a device doesn't work, try "pci=routeirq".  If it help s, post a report
[17179570.468000] PCI: Bridge: 0000:00:01.0
[17179570.468000]   IO window: disabled.
[17179570.468000]   MEM window: d5e00000-d7efffff
[17179570.468000]   PREFETCH window: c5b00000-d5cfffff
[17179570.468000] audit: initializing netlink socket (disabled)
[17179570.468000] audit(1156375133.468:1): initialized
[17179570.468000] VFS: Disk quotas dquot_6.5.1
[17179570.468000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.468000] Initializing Cryptographic API
[17179570.468000] io scheduler noop registered
[17179570.468000] io scheduler anticipatory registered
[17179570.468000] io scheduler deadline registered
[17179570.468000] io scheduler cfq registered
[17179570.468000] isapnp: Scanning for PnP cards...
[17179570.824000] isapnp: No Plug & Play device found
[17179570.844000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179570.844000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179570.848000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.848000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shar ing enabled
[17179570.848000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.848000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.852000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.852000] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.852000] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024  blocksize
[17179570.852000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.852000] ide: Assuming 33MHz system bus speed for PIO modes; override w ith idebus=xx
[17179570.852000] mice: PS/2 mouse device common for all mice
[17179570.856000] EISA: Probing bus 0 at eisa.0
[17179570.856000] EISA: Detected 0 cards.
[17179570.856000] NET: Registered protocol family 2
[17179570.880000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.892000] IP route cache hash table entries: 32768 (order: 5, 131072 byt es)
[17179570.892000] TCP established hash table entries: 131072 (order: 7, 524288 b ytes)
[17179570.892000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.892000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.892000] TCP reno registered
[17179570.892000] TCP bic registered
[17179570.892000] NET: Registered protocol family 1
[17179570.892000] NET: Registered protocol family 8
[17179570.892000] NET: Registered protocol family 20
[17179570.892000] Using IPI Shortcut mode
[17179570.892000] ACPI wakeup devices:
[17179570.892000] PCI0 PS2K UAR1 UAR2 USB1 USB2  LAN  MDM  AUD SLPB
[17179570.892000] ACPI: (supports S0 S1 S4 S5)
[17179570.892000] Freeing unused kernel memory: 288k freed
[17179570.960000] vga16fb: initializing
[17179570.960000] vga16fb: mapped to 0xc00a0000
[17179571.088000] Console: switching to colour frame buffer device 80x25
[17179571.088000] fb0: VGA16 VGA frame buffer device
[17179572.168000] Capability LSM initialized
[17179573.076000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179573.076000] SIS5513: chipset revision 208
[17179573.076000] SIS5513: not 100% native mode: will probe irqs later
[17179573.076000] SIS5513: SiS 961 MuTIOL IDE UDMA100 controller
[17179573.076000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb :DMA
[17179573.076000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd :DMA
[17179573.076000] Probing IDE interface ide0...
[17179573.364000] hda: ST380021A, ATA DISK drive
[17179574.148000] hdb: HL-DT-ST DVDRAM GSA-4167B, ATAPI CD/DVD-ROM drive
[17179574.204000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.212000] Probing IDE interface ide1...
[17179574.948000] hdc: HL-DT-ST CD-ROM GCR-8520B, ATAPI CD/DVD-ROM drive
[17179575.732000] hdd: CDRW5224, ATAPI CD/DVD-ROM drive
[17179575.788000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.804000] hda: max request size: 128KiB
[17179575.828000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/1 6/63, UDMA(33)
[17179575.828000] hda: cache flushes not supported
[17179575.828000]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 >
[17179575.904000] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.904000] Uniform CD-ROM driver Revision: 3.20
[17179576.332000] hdc: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
[17179576.336000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.728000] usbcore: registered new driver usbfs
[17179576.728000] usbcore: registered new driver hub
[17179576.732000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179576.732000] **** SET: Misaligned resource pointer: dfb35cc2 Type 07 Len 0
[17179576.732000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[17179576.732000] PCI: setting IRQ 11 as level-triggered
[17179576.732000] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKE] -> GSI 11 ( level, low) -> IRQ 11
[17179576.732000] ohci_hcd 0000:00:02.2: OHCI Host Controller
[17179576.732000] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus nu mber 1
[17179576.732000] ohci_hcd 0000:00:02.2: irq 11, io mem 0xdbffe000
[17179576.748000] hub 1-0:1.0: USB hub found
[17179576.748000] hub 1-0:1.0: 3 ports detected
[17179576.852000] **** SET: Misaligned resource pointer: dfb359c2 Type 07 Len 0
[17179576.852000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 12
[17179576.852000] PCI: setting IRQ 12 as level-triggered
[17179576.852000] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 12 ( level, low) -> IRQ 12
[17179576.852000] ohci_hcd 0000:00:02.3: OHCI Host Controller
[17179576.852000] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus nu mber 2
[17179576.852000] ohci_hcd 0000:00:02.3: irq 12, io mem 0xdbfff000
[17179576.868000] hub 2-0:1.0: USB hub found
[17179576.868000] hub 2-0:1.0: 3 ports detected
[17179577.148000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[17179577.376000] usbcore: registered new driver hiddev
[17179577.388000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
[17179577.388000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] o n usb-0000:00:02.3-1
[17179577.388000] usbcore: registered new driver usbhid
[17179577.388000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179577.588000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17179577.588000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17179577.588000] ide: failed opcode was: unknown
[17179577.588000] end_request: I/O error, dev hdb, sector 1338496
[17179577.588000] Buffer I/O error on device hdb, logical block 167312
[17179577.592000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17179577.592000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17179577.592000] ide: failed opcode was: unknown
[17179577.592000] end_request: I/O error, dev hdb, sector 1338496
[17179577.592000] Buffer I/O error on device hdb, logical block 167312
[17179577.596000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17179577.596000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17179577.596000] ide: failed opcode was: unknown
[17179577.596000] end_request: I/O error, dev hdb, sector 1338496
[17179577.596000] Buffer I/O error on device hdb, logical block 167312
[17179577.604000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17179577.604000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17179577.604000] ide: failed opcode was: unknown
[17179577.604000] end_request: I/O error, dev hdb, sector 1338496
[17179577.604000] Buffer I/O error on device hdb, logical block 167312
[17179577.608000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17179577.608000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17179577.608000] ide: failed opcode was: unknown
[17179577.608000] end_request: I/O error, dev hdb, sector 1338496
[17179577.608000] Buffer I/O error on device hdb, logical block 167312
[17179577.616000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17179577.616000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17179577.616000] ide: failed opcode was: unknown
[17179577.616000] end_request: I/O error, dev hdb, sector 1338496
[17179577.616000] Buffer I/O error on device hdb, logical block 167312
[17179578.100000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179578.184000] ISO 9660 Extensions: RRIP_1991A
[17179578.228000] loop: loaded (max 8 devices)
[17179578.248000] Registering unionfs 1.1.2
[17179578.420000] squashfs: version 3.0prerelease (2006/1/24) Phillip Lougher
[17179629.864000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179629.864000] 8139cp: pci dev 0000:00:08.0 (id 10ec:8139 rev 10) is not an 8 139C+ compatible chip
[17179629.864000] 8139cp: Try the "8139too" driver instead.
[17179629.868000] 8139too Fast Ethernet driver 0.9.27
[17179629.868000] **** SET: Misaligned resource pointer: dfd82102 Type 07 Len 0
[17179629.868000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[17179629.868000] PCI: setting IRQ 5 as level-triggered
[17179629.868000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 5 (l evel, low) -> IRQ 5
[17179629.868000] eth0: RealTek RTL8139 at 0xf08acf00, 00:50:fc:c1:6e:71, IRQ 5
[17179629.868000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179642.172000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179643.364000] ts: Compaq touchscreen protocol output
[17179643.556000] NET: Registered protocol family 17
[17179643.732000] input: PC Speaker as /class/input/input2
[17179643.928000] Real Time Clock Driver v1.12
[17179644.328000] Floppy drive(s): fd0 is 1.44M
[17179644.428000] FDC 0 is a post-1991 82077
[17179644.552000] rt61: module license 'unspecified' taints kernel.
[17179644.556000] **** SET: Misaligned resource pointer: eb387e02 Type 07 Len 0
[17179644.556000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179644.556000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 11 ( level, low) -> IRQ 11
[17179644.556000] RT61: Vendor = 0x1814, Product = 0x0401
[17179645.052000] Linux agpgart interface v0.101 (c) Dave Jones
[17179647.680000] **** SET: Misaligned resource pointer: e9c4acc2 Type 07 Len 0
[17179647.680000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[17179647.680000] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKF] -> GSI 11 ( level, low) -> IRQ 11
[17179647.856000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179647.996000] intel8x0_measure_ac97_clock: measured 55821 usecs
[17179647.996000] intel8x0: clocking to 48000
[17179648.276000] NET: Registered protocol family 10
[17179648.276000] lo: Disabled Privacy Extensions
[17179648.276000] IPv6 over IPv4 tunneling driver
[17179648.304000] parport: PnPBIOS parport detected.
[17179648.304000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRIST ATE,COMPAT,ECP,DMA]
[17179648.316000] agpgart: Detected SiS 646 chipset
[17179648.320000] agpgart: AGP aperture is 64M @ 0xdc000000
[17179649.508000] i2c-sis96x version 1.0.0
[17179649.508000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[17179649.696000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179652.148000] Adding 1020088k swap on /dev/hda6.  Priority:-1 extents:1 acro ss:1020088k
[17179652.660000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179652.660000] md: bitmap version 4.39
[17179653.484000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@ redhat.com
[17179654.476000] cdrom: open failed.
[17179654.496000] cdrom: open failed.
[17179657.348000] cdrom: open failed.
[17179657.352000] cdrom: open failed.
[17179658.512000] eth0: no IPv6 routers present
[17179667.360000] ACPI: Power Button (FF) [PWRF]
[17179667.360000] ACPI: Power Button (CM) [PWRB]
[17179667.360000] ACPI: Sleep Button (CM) [SLPB]
[17179667.508000] ibm_acpi: ec object not found
[17179667.552000] pcc_acpi: loading...
[17179700.752000] lp0: using parport0 (interrupt-driven).
[17179700.824000] ppdev: user-space parallel port driver
[17179702.108000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179702.108000] apm: overridden by ACPI.
[17179708.752000] ra0 (WE) : Driver using old /proc/net/wireless support, please  fix driver !
[17179948.088000] end_request: I/O error, dev fd0, sector 0
[17179948.120000] cdrom: open failed.
[17179948.120000] cdrom: open failed.
[17180149.332000] end_request: I/O error, dev fd0, sector 0
[17180149.360000] cdrom: open failed.
[17180149.364000] cdrom: open failed.
[17180219.672000] end_request: I/O error, dev fd0, sector 0
[17180219.692000] cdrom: open failed.
[17180219.692000] cdrom: open failed.
[17180489.828000] cdrom: open failed.
[17180489.832000] cdrom: open failed.
[17180489.832000] cdrom: open failed.
[17180489.836000] cdrom: open failed.
[17180492.576000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17180492.576000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17180492.576000] ide: failed opcode was: unknown
[17180492.576000] end_request: I/O error, dev hdb, sector 1338496
[17180492.576000] Buffer I/O error on device hdb, logical block 334624
[17180492.584000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17180492.584000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17180492.584000] ide: failed opcode was: unknown
[17180492.584000] end_request: I/O error, dev hdb, sector 1338500
[17180492.584000] Buffer I/O error on device hdb, logical block 334625
[17180492.592000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17180492.592000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17180492.592000] ide: failed opcode was: unknown
[17180492.592000] end_request: I/O error, dev hdb, sector 1338496
[17180492.592000] Buffer I/O error on device hdb, logical block 334624
[17180492.596000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17180492.596000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17180492.596000] ide: failed opcode was: unknown
[17180492.596000] end_request: I/O error, dev hdb, sector 1338500
[17180492.596000] Buffer I/O error on device hdb, logical block 334625
[17180818.752000] cdrom: open failed.
[17180818.752000] cdrom: open failed.
[17180818.756000] cdrom: open failed.
[17180818.756000] cdrom: open failed.
[17180821.048000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17180821.048000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17180821.048000] ide: failed opcode was: unknown
[17180821.048000] end_request: I/O error, dev hdb, sector 1338496
[17180821.048000] Buffer I/O error on device hdb, logical block 334624
[17180821.084000] hdb: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17180821.084000] hdb: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17180821.084000] ide: failed opcode was: unknown
[17180821.084000] end_request: I/O error, dev hdb, sector 1338500
[17180821.084000] Buffer I/O error on device hdb, logical block 334625
[17181084.600000] VFS: Can't find ext3 filesystem on dev hda7.
[17181240.028000] ohci_hcd 0000:00:02.2: wakeup
[17181240.412000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[17181245.388000] SCSI subsystem initialized
[17181245.680000] Initializing USB Mass Storage driver...
[17181245.680000] scsi0 : SCSI emulation for USB Mass Storage devices
[17181245.680000] usb-storage: device found at 2
[17181245.680000] usb-storage: waiting for device to settle before scanning
[17181245.680000] usbcore: registered new driver usb-storage
[17181245.680000] USB Mass Storage support registered.
[17181250.688000]   Vendor:           Model: USB DISK 2.0      Rev: 1.15
[17181250.688000]   Type:   Direct-Access                      ANSI SCSI revisio n: 00
[17181250.696000] usb-storage: device scan complete
[17181250.712000] Driver 'sd' needs updating - please use bus_type methods
[17181250.732000] SCSI device sda: 253952 512-byte hdwr sectors (130 MB)
[17181250.740000] sda: Write Protect is off
[17181250.740000] sda: Mode Sense: 03 00 00 00
[17181250.740000] sda: assuming drive cache: write through
[17181250.768000] SCSI device sda: 253952 512-byte hdwr sectors (130 MB)
[17181250.776000] sda: Write Protect is off
[17181250.776000] sda: Mode Sense: 03 00 00 00
[17181250.776000] sda: assuming drive cache: write through
[17181250.776000]  sda: sda1
[17181250.788000] sd 0:0:0:0: Attached scsi removable disk sda
[17181250.800000] sd 0:0:0:0: Attached scsi generic sg0 type 0
ubuntu@ubuntu:~$

PLS Help.

---

