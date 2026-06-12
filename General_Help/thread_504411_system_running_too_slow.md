---
title: "system running too slow"
date: 2007-07-19
forum: General Help
---

### Post by varun_shrivastava on 2007-07-19
hi
i have Ubuntu 6.10 edgy installed on my system
but its running too slow, i don't know why?
And also it takes a hell lot of time to boot up.
when i click on an icon it takes 15 to 20 secs to start the application.

Can some one please help?

My system configuration:
Intel Pentium D processor
1 GB RAM
2GB swap 

thanks

---

### Post by anubhavrocks on 2007-07-19
what is the output of dmesg?Kindly give more info if you need others to help you.

---

### Post by varun_shrivastava on 2007-07-19
actually i don't know what kind of information is helpful

here's the output of dmesg
```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003e7b1d00 (usable)
[17179569.184000]  BIOS-e820: 000000003e7b1d00 - 000000003e7b3d00 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003e7b3d00 - 000000003f000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fed40000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed45000 - 0000000100000000 (reserved)
[17179569.184000] 103MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f9bf0
[17179569.184000] On node 0 totalpages: 255921
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 26545 pages, LIFO batch:7
[17179569.184000] DMI 2.4 present.
[17179569.184000] Intel MultiProcessor Specification v1.4
[17179569.184000]     Virtual Wire compatibility mode.
[17179569.184000] OEM ID: COMPAQ   Product ID:              APIC at: 0xFEE00000
[17179569.184000] Processor #0 15:6 APIC version 16
[17179569.184000] Processor #1 15:6 APIC version 16
[17179569.184000] MP table busid value (32) for bustype PCI     is too large, max. supported is 31
[17179569.184000] MP table busid value (255) for bustype ISA     is too large, max. supported is 31
[17179569.184000] I/O APIC #1 Version 17 at 0xFEC00000.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Processors: 2
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3f000000:b5000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash nmi-watchdog=0 noapic acpi=off hda=noprobe
[17179569.184000] ide_setup: hda=noprobe
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3392.216 MHz processor.
[   12.080903] Using tsc for high-res timesource
[   12.082374] Console: colour VGA+ 80x25
[   12.082650] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.082943] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.099336] Memory: 1004828k/1023684k available (1910k kernel code, 18176k reserved, 1070k data, 308k init, 106180k highmem)
[   12.099340] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.176562] Calibrating delay using timer specific routine.. 6793.74 BogoMIPS (lpj=13587498)
[   12.176592] Security Framework v1.0.0 initialized
[   12.176596] SELinux:  Disabled at boot.
[   12.176610] Mount-cache hash table entries: 512
[   12.176717] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001
[   12.176727] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001
[   12.176734] monitor/mwait feature present.
[   12.176735] using mwait in idle threads.
[   12.176741] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   12.176743] CPU: L2 cache: 2048K
[   12.176745] CPU: Hyper-Threading is disabled
[   12.176747] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000e49d 00000000 00000001
[   12.176765] Checking 'hlt' instruction... OK.
[   12.192589] SMP alternatives: switching to UP code
[   12.192790] checking if image is initramfs... it is
[   12.586113] Freeing initrd memory: 5564k freed
[   12.586118] CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 05
[   12.586129] SMP alternatives: switching to SMP code
[   12.586307] Booting processor 1/1 eip 3000
[   12.596830] Initializing CPU#1
[   12.675047] Calibrating delay using timer specific routine.. 6783.58 BogoMIPS (lpj=13567166)
[   12.675055] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001
[   12.675062] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001
[   12.675066] monitor/mwait feature present.
[   12.675071] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   12.675073] CPU: L2 cache: 2048K
[   12.675074] CPU: Hyper-Threading is disabled
[   12.675076] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000e49d 00000000 00000001
[   12.675478] CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 05
[   12.675507] Total of 2 processors activated (13577.33 BogoMIPS).
[   12.782730] checking TSC synchronization across 2 CPUs: passed.
[    0.003992] Brought up 2 CPUs
[    0.249437] migration_cost=925
[    0.249679] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.249744] NET: Registered protocol family 16
[    0.249770] EISA bus registered
[    0.250744] PCI: PCI BIOS revision 3.00 entry at 0xeb048, last bus=32
[    0.250750] PCI: Using configuration type 1
[    0.250751] Setting up standard PCI resources
[    0.250997] ACPI: Interpreter disabled.
[    0.251000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.251007] pnp: PnP ACPI: disabled
[    0.251010] PnPBIOS: Scanning system for PnP BIOS support...
[    0.251016] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7e40
[    0.251018] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x7c3d, dseg 0xf0000
[    0.251022] PnPBIOS: dev_node_info: function not supported on this system
[    0.251065] PnPBIOS: Unable to get node info.  Aborting.
[    0.251136] PCI: Probing PCI hardware
[    0.251139] PCI: Probing PCI hardware (bus 00)
[    0.251258] Boot video device is 0000:00:02.0
[    0.251991] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[    0.252160] PCI: Transparent bridge - 0000:00:1e.0
[    0.253628] PCI: Discovered primary peer bus 01 [IRQ]
[    0.253695] PCI: Discovered primary peer bus 3f [IRQ]
[    0.253700] PCI: Using IRQ router PIIX/ICH [8086/2814] at 0000:00:1f.0
[    0.659309] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.659312] PCI: Bridge: 0000:00:1c.0
[    0.659314]   IO window: disabled.
[    0.659318]   MEM window: disabled.
[    0.659322]   PREFETCH window: disabled.
[    0.659326] PCI: Bridge: 0000:00:1e.0
[    0.659327]   IO window: disabled.
[    0.659332]   MEM window: disabled.
[    0.659335]   PREFETCH window: disabled.
[    0.659358] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.659370] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.659396] NET: Registered protocol family 2
[    0.698775] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.698883] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.699480] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.699778] TCP: Hash tables configured (established 131072 bind 65536)
[    0.699780] TCP reno registered
[    0.700880] audit: initializing netlink socket (disabled)
[    0.700896] audit(1184835751.204:1): initialized
[    0.701024] highmem bounce pool size: 64 pages
[    0.701135] VFS: Disk quotas dquot_6.5.1
[    0.701160] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.701236] Initializing Cryptographic API
[    0.701240] io scheduler noop registered
[    0.701256] io scheduler anticipatory registered
[    0.701272] io scheduler deadline registered
[    0.701309] io scheduler cfq registered (default)
[    0.701697] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.701703] pcie_portdrv_probe->Dev[283f:8086] has invalid IRQ. Check vendor BIOS
[    0.701750] assign_interrupt_mode Found MSI capability
[    0.701814] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.701879] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.702028] isapnp: Scanning for PnP cards...
[    1.052571] isapnp: No Plug & Play device found
[    1.083606] Real Time Clock Driver v1.12ac
[    1.083686] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.083815] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.084339] mice: PS/2 mouse device common for all mice
[    1.085107] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.085255] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.085259] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.085523] PNP: No PS/2 controller found. Probing ports directly.
[    1.092458] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.095157] EISA: Probing bus 0 at eisa.0
[    1.095164] Cannot allocate resource for EISA slot 1
[    1.095191] EISA: Detected 0 cards.
[    1.095269] TCP bic registered
[    1.095291] NET: Registered protocol family 1
[    1.095296] NET: Registered protocol family 8
[    1.095298] NET: Registered protocol family 20
[    1.095329] Starting balanced_irq
[    1.095339] Using IPI No-Shortcut mode
[    1.095504] Freeing unused kernel memory: 308k freed
[    1.115286] input: AT Translated Set 2 keyboard as /class/input/input0
[    2.157663] Capability LSM initialized
[    2.546488] SCSI subsystem initialized
[    2.548833] libata version 1.20 loaded.
[    2.549780] ata_piix 0000:00:1f.2: version 1.05
[    2.549803] PCI: Found IRQ 5 for device 0000:00:1f.2
[    2.549831] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    2.549865] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x10E0 irq 14
[    2.714448] ata1: dev 0 cfg 49:2f00 82:706b 83:7c01 84:4023 85:7069 86:3c01 87:4023 88:203f
[    2.714451] ata1: dev 0 ATA-7, max UDMA/100, 312581808 sectors: LBA48
[    2.722445] ata1: dev 0 configured for UDMA/100
[    2.722447] scsi0 : ata_piix
[    2.722551]   Vendor: ATA       Model: WDC WD1600JS-60M  Rev: 10.0
[    2.722565]   Type:   Direct-Access                      ANSI SCSI revision: 05
[    2.722621] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x10E8 irq 15
[    3.057454] ata2: dev 0 cfg 49:0f00 82:0210 83:4011 84:4000 85:0000 86:0001 87:4000 88:203f
[    3.057457] ata2: dev 0 ATAPI, max UDMA/100
[    3.212862] ata2: PIO error
[    3.212882] ata2: dev 1 failed to IDENTIFY (I/O error)
[    3.392462] ata2: dev 0 configured for UDMA/100
[    3.392464] scsi1 : ata_piix
[    3.393123]   Vendor: LITE-ON   Model: DVD SHD-16S1S     Rev: EQS8
[    3.393142]   Type:   CD-ROM                             ANSI SCSI revision: 05
[    3.402617] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    3.402631] sda: Write Protect is off
[    3.402634] sda: Mode Sense: 00 3a 00 00
[    3.402652] SCSI device sda: drive cache: write back
[    3.402699] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    3.402709] sda: Write Protect is off
[    3.402711] sda: Mode Sense: 00 3a 00 00
[    3.402728] SCSI device sda: drive cache: write back
[    3.402731]  sda: sda1 sda2 sda3 sda4
[    3.423973] sd 0:0:0:0: Attached scsi disk sda
[    3.464858] sr0: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[    3.464863] Uniform CD-ROM driver Revision: 3.20
[    3.464920] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.844420] ide0: I/O resource 0x1F0-0x1F7 not free.
[    3.844424] ide0: ports already in use, skipping probe
[    3.844427] ide1: I/O resource 0x170-0x177 not free.
[    3.844429] ide1: ports already in use, skipping probe
[    3.844431] Probing IDE interface ide2...
[    3.871382] usbcore: registered new driver usbfs
[    3.871791] usbcore: registered new driver hub
[    3.873309] USB Universal Host Controller Interface driver v3.0
[    3.873739] PCI: Found IRQ 11 for device 0000:00:1a.0
[    3.873755] PCI: Sharing IRQ 11 with 0000:00:1d.0
[    3.873760] PCI: Sharing IRQ 11 with 0000:00:1d.7
[    3.873772] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    3.873775] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.873947] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.873971] uhci_hcd 0000:00:1a.0: irq 11, io base 0x00001020
[    3.874577] usb usb1: configuration #1 chosen from 1 choice
[    3.874679] hub 1-0:1.0: USB hub found
[    3.874687] hub 1-0:1.0: 2 ports detected
[    3.978022] PCI: Found IRQ 5 for device 0000:00:1a.1
[    3.978037] PCI: Sharing IRQ 5 with 0000:00:1b.0
[    3.978045] PCI: Sharing IRQ 5 with 0000:00:1d.1
[    3.978063] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    3.978067] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.978088] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.978110] uhci_hcd 0000:00:1a.1: irq 5, io base 0x00001040
[    3.978170] usb usb2: configuration #1 chosen from 1 choice
[    3.978189] hub 2-0:1.0: USB hub found
[    3.978195] hub 2-0:1.0: 2 ports detected
[    4.081807] PCI: Found IRQ 11 for device 0000:00:1d.0
[    4.081815] PCI: Sharing IRQ 11 with 0000:00:1a.0
[    4.081826] PCI: Sharing IRQ 11 with 0000:00:1d.7
[    4.081835] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.081838] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.081938] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    4.081959] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001060
[    4.082095] usb usb3: configuration #1 chosen from 1 choice
[    4.082195] hub 3-0:1.0: USB hub found
[    4.082202] hub 3-0:1.0: 2 ports detected
[    4.185478] PCI: Found IRQ 5 for device 0000:00:1d.1
[    4.185487] PCI: Sharing IRQ 5 with 0000:00:1a.1
[    4.185492] PCI: Sharing IRQ 5 with 0000:00:1b.0
[    4.185506] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.185509] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.185605] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    4.185625] uhci_hcd 0000:00:1d.1: irq 5, io base 0x00001080
[    4.185764] usb usb4: configuration #1 chosen from 1 choice
[    4.185863] hub 4-0:1.0: USB hub found
[    4.185870] hub 4-0:1.0: 2 ports detected
[    4.296761] PCI: Found IRQ 10 for device 0000:00:1a.7
[    4.296795] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    4.296799] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.296825] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 5
[    4.296855] ehci_hcd 0000:00:1a.7: debug port 1
[    4.296861] PCI: cache line size of 128 is not supported by device 0000:00:1a.7
[    4.296869] ehci_hcd 0000:00:1a.7: irq 10, io mem 0xf0525000
[    4.300727] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.300780] usb usb5: configuration #1 chosen from 1 choice
[    4.300801] hub 5-0:1.0: USB hub found
[    4.300808] hub 5-0:1.0: 4 ports detected
[    4.320941] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.404773] PCI: Found IRQ 11 for device 0000:00:1d.7
[    4.404784] PCI: Sharing IRQ 11 with 0000:00:1a.0
[    4.404794] PCI: Sharing IRQ 11 with 0000:00:1d.0
[    4.404828] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.404832] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.404856] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 6
[    4.404883] ehci_hcd 0000:00:1d.7: debug port 1
[    4.404889] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    4.404896] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf0525400
[    4.406305] Probing IDE interface ide3...
[    4.408761] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.408808] usb usb6: configuration #1 chosen from 1 choice
[    4.408829] hub 6-0:1.0: USB hub found
[    4.408836] hub 6-0:1.0: 4 ports detected
[    4.829056] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    4.968651] Probing IDE interface ide4...
[    5.001044] usb 2-1: configuration #1 chosen from 1 choice
[    5.010068] usbcore: registered new driver hiddev
[    5.025964] input: USB Optical Mouse as /class/input/input1
[    5.025982] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.1-1
[    5.025989] usbcore: registered new driver usbhid
[    5.025992] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.531072] Probing IDE interface ide5...
[    6.104371] Attempting manual resume
[    6.127830] kjournald starting.  Commit interval 5 seconds
[    6.127838] EXT3-fs: mounted filesystem with ordered data mode.
[   12.720220] Linux agpgart interface v0.101 (c) Dave Jones
[   12.729574] agpgart: Detected an Intel 965Q Chipset.
[   12.730799] agpgart: Detected 7676K stolen memory.
[   12.744863] agpgart: AGP aperture is 256M @ 0xe0000000
[   12.798142] hw_random hardware driver 1.0.0 loaded
[   12.922544] ts: Compaq touchscreen protocol output
[   12.950844] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.954003] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.964810] Intel(R) PRO/1000 Network Driver - version 7.1.9-k4
[   12.964813] Copyright (c) 1999-2006 Intel Corporation.
[   12.964855] PCI: Found IRQ 10 for device 0000:00:19.0
[   12.964883] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   12.997925] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x4) 00:18:fe:62:dd:f4
[   13.097432] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   13.097500] PCI: Found IRQ 5 for device 0000:00:1b.0
[   13.097512] PCI: Sharing IRQ 5 with 0000:00:1a.1
[   13.097521] PCI: Sharing IRQ 5 with 0000:00:1d.1
[   13.097543] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   13.164168] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.165175] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.464165] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   13.827334] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE]
[   13.828126] parport0: irq 7 detected
[   13.925008] lp0: using parport0 (polling).
[   13.993573] Adding 2048276k swap on /dev/disk/by-uuid/f3053225-1f17-4a23-8b1f-8c3f5129cf6f.  Priority:-1 extents:1 across:2048276k
[   14.061793] EXT3 FS on sda1, internal journal
[   14.323371] kjournald starting.  Commit interval 5 seconds
[   14.331987] EXT3 FS on sda3, internal journal
[   14.331993] EXT3-fs: mounted filesystem with ordered data mode.
[   14.349444] kjournald starting.  Commit interval 5 seconds
[   14.359946] EXT3 FS on sda4, internal journal
[   14.359951] EXT3-fs: mounted filesystem with ordered data mode.
[   14.692057] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   14.692061] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   15.664230] NET: Registered protocol family 17
[   28.337504] [drm] Initialized drm 1.0.1 20051102
[   28.345122] PCI: Found IRQ 5 for device 0000:00:02.0
[   28.345129] PCI: Sharing IRQ 5 with 0000:00:03.0
[   28.345334] [drm] Initialized i915 1.5.0 20060119 on minor 0
[   28.874417] NET: Registered protocol family 10
[   28.874499] lo: Disabled Privacy Extensions
[   28.874725] IPv6 over IPv4 tunneling driver
[   38.929431] eth0: no IPv6 routers present
[   48.629347] apm: BIOS not found.
[   50.569864] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   50.651851] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   50.652185] NFSD: starting 90-second grace period
[  224.916018] fusion: no version for "struct_module" found: kernel tainted.

```

---

### Post by davidsrsb on 2007-07-19
Pentium D dual core with a Compaq laptop motherboard?
That does not sound right.
What is the real spec of your PC?

---

### Post by varun_shrivastava on 2007-07-19
> **davidsrsb said:**
> Pentium D dual core with a Compaq laptop motherboard?

How did you found that?

But these is the real output of dmesg command. I haven't edited that
My computer is from HP Compaq
whose info can be found at:
[http://h10010.www1.hp.com/wwpc/in/en/sm/WF06a/1090261-1139371-1139371-1139371-12798980-12799032.html]("http://h10010.www1.hp.com/wwpc/in/en/sm/WF06a/1090261-1139371-1139371-1139371-12798980-12799032.html")

---

### Post by davidsrsb on 2007-07-19
[   12.675478] CPU1: Intel(R) Pentium(R) D CPU 3.40GHz stepping 05
[   12.675507] Total of 2 processors activated (13577.33 BogoMIPS).
and
[    0.249679] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
Maybe 6.10 is too old for your system hardware and you need Feisty 7.04. Your PC SHOULD be fast with 1GB of ram as well so slow running probably means bad chipset support
As I asked before, what is the spec, especially the motherboard type.

---

### Post by varun_shrivastava on 2007-07-19
here is some more info
$ lspci -v 
```
00:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f0400000 (32-bit, non-prefetchable) [size=1M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1100 [size=8]
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

00:03.0 Communication controller: Intel Corporation HECI Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f0525900 (64-bit, non-prefetchable) [size=16]
        Capabilities: [50] Power Management version 3
        Capabilities: [8c] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

00:19.0 Ethernet controller: Intel Corporation Unknown device 104a (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2800
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f0500000 (32-bit, non-prefetchable) [size=128K]
        Memory at f0524000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1000 [size=32]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

00:1a.0 USB Controller: Intel Corporation USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1020 [size=32]

00:1a.1 USB Controller: Intel Corporation USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1040 [size=32]

00:1a.7 USB Controller: Intel Corporation USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at f0525000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation HD Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f0520000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=20, subordinate=20, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1060 [size=32]

00:1d.1 USB Controller: Intel Corporation USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1080 [size=32]

00:1d.7 USB Controller: Intel Corporation USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at f0525400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        Capabilities: [50] #0d [0000]

00:1f.0 ISA bridge: Intel Corporation LPC Interface Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation SATA Controller 1 IDE (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 2801
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 5
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 10e0 [size=16]
        I/O ports at 10f0 [size=16]
        Capabilities: [70] Power Management version 3

```

$ cat /etc/X11/xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "HP 7540"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "HP 7540"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by anubhavrocks on 2007-07-19
Have to tried putting in Feisty?

---

### Post by varun_shrivastava on 2007-07-19
> **anubhavrocks said:**
> Have to tried putting in Feisty?
No i haven't tried

But my system used to work fine few days back, suddenly one morning i found it slow

---

### Post by Ayuthia on 2007-07-19
I have an HP dv6338se and I have been running with noapic but not with acpi=off.  Does your laptop need that one?  I am not for sure if that is what is doing it or not.

---

### Post by varun_shrivastava on 2007-07-19
> **thanos12 said:**
> format your hard disk please!!
[IMG]http://s4.bitefight.gr/c.php?uid=15792[/IMG]
[IMG]http://s3.bitefight.gr/c.php?uid=16467[/IMG]

formating is not the only solution like pressing restart button when system hangs

---

### Post by varun_shrivastava on 2007-07-19
> **Ayuthia said:**
> I have an HP dv6338se and I have been running with noapic but not with acpi=off.  Does your laptop need that one?  I am not for sure if that is what is doing it or not.

how to make that change?

---

### Post by Ayuthia on 2007-07-19
You should be able to access that information in /boot/grub/menu.lst.  It will require root access (sudo).

---

### Post by varun_shrivastava on 2007-07-19
> **Ayuthia said:**
> You should be able to access that information in /boot/grub/menu.lst.  It will require root access (sudo).

here's my file 
```
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash nmi-watchdog=0 noapic acpi=off hda=noprobe
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

```

should i remove that word but my system used to work with that settings few days back. i never changed these settings

---

### Post by Ayuthia on 2007-07-19
I am just trying to remember how acpi=off affects the system.  I thought that I tried it before and I cannot remember if it slowed things down or not.  For some reason I ended up taking it out, but I cannot remember why.

The other thing is that you have an Intel chip and I have an AMD so there might be a reason to have it for you.  You can always try it out and if it does not work, put it back in.

Another thing to look at is the temperature of your laptop to see if it is running too hot.  You might also look at what processes are running when things slow down.  Maybe something is taking up the CPU.

---

### Post by davidsrsb on 2007-07-19
00:03.0 Communication controller: Intel Corporation HECI Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2801
 and
00:19.0 Ethernet controller: Intel Corporation Unknown device 104a (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2800
 Unrecognized chips means that your problem is due to unexpected interrupts and loads of software timeouts. You really must reinstall with Feisty. Why do you want to install a distribution that hit feature freeze almost one year ago?

---

### Post by varun_shrivastava on 2007-07-20
> **davidsrsb said:**
> 00:03.0 Communication controller: Intel Corporation HECI Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2801
 and
00:19.0 Ethernet controller: Intel Corporation Unknown device 104a (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2800
 Unrecognized chips means that your problem is due to unexpected interrupts and loads of software timeouts. You really must reinstall with Feisty. Why do you want to install a distribution that hit feature freeze almost one year ago?

Can i upgrade through internet?

---

### Post by davidsrsb on 2007-07-20
You can, but...
I never try to update an unstable machine, preferring to do a clean install. Backup anything in home to a usb key  first.

---

### Post by varun_shrivastava on 2007-07-20
> **davidsrsb said:**
> You can, but...
I never try to update an unstable machine, preferring to do a clean install. Backup anything in home to a usb key  first.

i should clean install as running update manager shows no upgrades available

---

### Post by anubhavrocks on 2007-07-20
use this command to upgrade

```
gksu "update-manager -c"
```

---

### Post by varun_shrivastava on 2007-07-20
> **anubhavrocks said:**
> use this command to upgrade

```
gksu "update-manager -c"
```

now it showed 7.04 upgrade available but with following lines displayed on terminal

gksu "update-manager -c"
```
warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

---

### Post by anubhavrocks on 2007-07-20
Just go ahead and click the new release.

---

