---
title: "Ipod 4GB know vfat or RAID detected?"
date: 2007-01-31
forum: General Help
---

### Post by onlybui on 2007-01-31
Ok I tried installing a bug fix problem is that I'm not too sure if my ipod is being dectected as a Raid. I followed this link here [https://launchpad.net/ubuntu/+source/hal/+bug/66068](https://launchpad.net/ubuntu/+source/hal/+bug/66068)
and did this all
"So, as a christmas present, I prepared precompiled .debs which can be found at [http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/](http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/). In the README, there's information provided how to install them."

```
dmesg |tail
[ 1254.506751] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1314.433183] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1374.358623] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1434.281088] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1494.203150] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1554.129858] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1614.054957] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1673.976932] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1683.457370] FAT: count of clusters too big (246935)
[ 1683.457376] VFS: Can't find a valid FAT filesystem on dev sdc.

```

```
dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ff00000 (usable)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 261888
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32512 pages, LIFO batch:7
[17179569.184000] DMI 2.4 present.
[17179569.184000] ACPI: Unable to locate RSDP
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] Found and enabled local APIC!
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1791.160 MHz processor.
[   30.711817] Using tsc for high-res timesource
[   30.713309] Console: colour VGA+ 80x25
[   30.713728] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   30.714106] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   30.733097] Memory: 1028684k/1047552k available (1910k kernel code, 18096k reserved, 1069k data, 308k init, 130048k highmem)
[   30.733100] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.811606] Calibrating delay using timer specific routine.. 3588.90 BogoMIPS (lpj=7177808)
[   30.811643] Security Framework v1.0.0 initialized
[   30.811649] SELinux:  Disabled at boot.
[   30.811663] Mount-cache hash table entries: 512
[   30.811783] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   30.811789] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   30.811796] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   30.811799] CPU: L2 Cache: 512K (64 bytes/line)
[   30.811801] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   30.811816] Checking 'hlt' instruction... OK.
[   30.827666] SMP alternatives: switching to UP code
[   30.827809] Freeing SMP alternatives: 16k freed
[   30.827930] checking if image is initramfs... it is
[   31.321112] Freeing initrd memory: 5327k freed
[   31.321117] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[   31.321122] SMP motherboard not detected.
[   31.426830] Brought up 1 CPUs
[   31.426843] migration_cost=0
[   31.427062] NET: Registered protocol family 16
[   31.427085] EISA bus registered
[   31.443406] PCI: PCI BIOS revision 3.00 entry at 0xfa4b0, last bus=2
[   31.443412] PCI: Using configuration type 1
[   31.443414] Setting up standard PCI resources
[   31.445443] ACPI: Interpreter disabled.
[   31.445446] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.445452] pnp: PnP ACPI: disabled
[   31.445455] PnPBIOS: Scanning system for PnP BIOS support...
[   31.445650] PnPBIOS: Found PnP BIOS installation structure at 0xc00fafd0
[   31.445656] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb000, dseg 0xf0000
[   31.446299] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   31.446330] PCI: Probing PCI hardware
[   31.446333] PCI: Probing PCI hardware (bus 00)
[   31.447039] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[   31.447266] Boot video device is 0000:01:00.0
[   31.448061] PCI: Transparent bridge - 0000:00:14.4
[   31.448991] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   31.512029] pnp: 00:0b: ioport range 0x800-0x87f has been reserved
[   31.512180] PCI: Bridge: 0000:00:02.0
[   31.512183]   IO window: e000-efff
[   31.512186]   MEM window: fa000000-fcffffff
[   31.512189]   PREFETCH window: d0000000-dfffffff
[   31.512193] PCI: Bridge: 0000:00:14.4
[   31.512196]   IO window: d000-dfff
[   31.512203]   MEM window: fde00000-fdefffff
[   31.512208]   PREFETCH window: fdd00000-fddfffff
[   31.512221] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.512247] NET: Registered protocol family 2
[   31.542682] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.542830] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   31.543718] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.544126] TCP: Hash tables configured (established 131072 bind 65536)
[   31.544129] TCP reno registered
[   31.544599] audit: initializing netlink socket (disabled)
[   31.544607] audit(1170274899.916:1): initialized
[   31.544661] highmem bounce pool size: 64 pages
[   31.544725] VFS: Disk quotas dquot_6.5.1
[   31.544742] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   31.544795] Initializing Cryptographic API
[   31.544799] io scheduler noop registered
[   31.544806] io scheduler anticipatory registered
[   31.544812] io scheduler deadline registered
[   31.544828] io scheduler cfq registered (default)
[   31.544981] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.544984] pcie_portdrv_probe->Dev[5a34:1002] has invalid IRQ. Check vendor BIOS
[   31.545005] assign_interrupt_mode Found MSI capability
[   31.545044] Allocate Port Service[0000:00:02.0:pcie00]
[   31.545133] isapnp: Scanning for PnP cards...
[   31.899755] isapnp: No Plug & Play device found
[   31.917203] Real Time Clock Driver v1.12ac
[   31.917253] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.917399] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.917934] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.918092] mice: PS/2 mouse device common for all mice
[   31.918511] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.918658] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.918662] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.918900] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   31.918903] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   32.465181] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.465833] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.467055] EISA: Probing bus 0 at eisa.0
[   32.467097] EISA: Detected 0 cards.
[   32.467283] TCP bic registered
[   32.467293] NET: Registered protocol family 1
[   32.467298] NET: Registered protocol family 8
[   32.467300] NET: Registered protocol family 20
[   32.467320] Using IPI No-Shortcut mode
[   32.467547] Freeing unused kernel memory: 308k freed
[   32.911269] input: AT Translated Set 2 keyboard as /class/input/input0
[   33.974140] Capability LSM initialized
[   34.418175] SCSI subsystem initialized
[   34.420964] libata version 1.20 loaded.
[   34.422809] sata_sil 0000:00:11.0: version 0.9
[   34.422881] ata1: SATA max UDMA/100 cmd 0xF8828080 ctl 0xF882808A bmdma 0xF8828000 irq 11
[   34.422898] ata2: SATA max UDMA/100 cmd 0xF88280C0 ctl 0xF88280CA bmdma 0xF8828008 irq 11
[   34.630402] ata1: SATA link down (SStatus 0)
[   34.640409] scsi0 : sata_sil
[   34.846108] ata2: SATA link down (SStatus 0)
[   34.856107] scsi1 : sata_sil
[   34.856272] ata3: SATA max UDMA/100 cmd 0xF882A080 ctl 0xF882A08A bmdma 0xF882A000 irq 10
[   34.856289] ata4: SATA max UDMA/100 cmd 0xF882A0C0 ctl 0xF882A0CA bmdma 0xF882A008 irq 10
[   35.221619] ata3: SATA link up 1.5 Gbps (SStatus 113)
[   35.234060] ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3468 86:3c01 87:4003 88:407f
[   35.234064] ata3: dev 0 ATA-6, max UDMA/133, 312581808 sectors: LBA48
[   35.246046] ata3: dev 0 configured for UDMA/100
[   35.246051] scsi2 : sata_sil
[   35.613084] ata4: SATA link up 1.5 Gbps (SStatus 113)
[   35.625523] ata4: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3468 86:3c01 87:4023 88:407f
[   35.625527] ata4: dev 0 ATA-7, max UDMA/133, 586072368 sectors: LBA48
[   35.637506] ata4: dev 0 configured for UDMA/100
[   35.637511] scsi3 : sata_sil
[   35.638137]   Vendor: ATA       Model: ST3160827AS       Rev: 3.42
[   35.638146]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   35.641106]   Vendor: ATA       Model: ST3300622AS       Rev: 3.AA
[   35.641116]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   35.650538] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   35.650550] sda: Write Protect is off
[   35.650552] sda: Mode Sense: 00 3a 00 00
[   35.650564] SCSI device sda: drive cache: write back
[   35.650610] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   35.650617] sda: Write Protect is off
[   35.650619] sda: Mode Sense: 00 3a 00 00
[   35.650630] SCSI device sda: drive cache: write back
[   35.650632]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[   35.703735] sd 2:0:0:0: Attached scsi disk sda
[   35.707545] SCSI device sdb: 586072368 512-byte hdwr sectors (300069 MB)
[   35.707567] sdb: Write Protect is off
[   35.707569] sdb: Mode Sense: 00 3a 00 00
[   35.709009] SCSI device sdb: drive cache: write back
[   35.713019] SCSI device sdb: 586072368 512-byte hdwr sectors (300069 MB)
[   35.716939] sdb: Write Protect is off
[   35.716943] sdb: Mode Sense: 00 3a 00 00
[   35.717746] SCSI device sdb: drive cache: write back
[   35.717750]  sdb: sdb1 < sdb5 >
[   35.732606] sd 3:0:0:0: Attached scsi disk sdb
[   36.053087] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   36.053112] ATIIXP: chipset revision 0
[   36.053114] ATIIXP: not 100% native mode: will probe irqs later
[   36.053123]     ide0: BM-DMA at 0xf300-0xf307, BIOS settings: hda:pio, hdb:pio
[   36.053137]     ide1: BM-DMA at 0xf308-0xf30f, BIOS settings: hdc:pio, hdd:pio
[   36.053145] Probing IDE interface ide0...
[   36.623671] Probing IDE interface ide1...
[   37.363105] hdc: TOSHIBA DVD-ROM SD-M1502, ATAPI CD/DVD-ROM drive
[   38.150026] hdd: BENQ DVD DD DW1620, ATAPI CD/DVD-ROM drive
[   38.210563] ide1 at 0x170-0x177,0x376 on irq 15
[   38.222949] hdc: ATAPI 48X DVD-ROM drive, 128kB Cache, UDMA(33)
[   38.222957] Uniform CD-ROM driver Revision: 3.20
[   38.231291] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   38.342138] Probing IDE interface ide0...
[   38.374578] usbcore: registered new driver usbfs
[   38.374596] usbcore: registered new driver hub
[   38.375160] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   38.375200] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   38.375320] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   39.028891] spurious 8259A interrupt: IRQ7.
[   39.028910] ohci_hcd 0000:00:13.0: irq 10, io mem 0xfe02d000
[   39.070359] ieee1394: Initialized config rom entry `ip1394'
[   39.094570] usb usb1: configuration #1 chosen from 1 choice
[   39.094670] hub 1-0:1.0: USB hub found
[   39.094683] hub 1-0:1.0: 4 ports detected
[   39.200323] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   39.200423] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   39.232311] ohci_hcd 0000:00:13.1: irq 10, io mem 0xfe02c000
[   39.296128] usb usb2: configuration #1 chosen from 1 choice
[   39.296238] hub 2-0:1.0: USB hub found
[   39.296249] hub 2-0:1.0: 4 ports detected
[   39.411917] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   39.411959] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   39.412030] ehci_hcd 0000:00:13.2: irq 10, io mem 0xfe02b000
[   39.412042] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   39.412128] usb usb3: configuration #1 chosen from 1 choice
[   39.412149] hub 3-0:1.0: USB hub found
[   39.412155] hub 3-0:1.0: 8 ports detected
[   39.582715] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fdefe000-fdefe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   39.638031] Attempting manual resume
[   39.656245] kjournald starting.  Commit interval 5 seconds
[   39.656256] EXT3-fs: mounted filesystem with ordered data mode.
[   40.466427] usb 3-4: new high speed USB device using ehci_hcd and address 4
[   40.612456] usb 3-4: configuration #1 chosen from 2 choices
[   40.612731] ohci_hcd 0000:00:13.0: wakeup
[   40.866006] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00009f1ae1]
[   40.997695] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   41.197496] usb 1-1: configuration #1 chosen from 1 choice
[   41.505010] usb 1-2: new low speed USB device using ohci_hcd and address 4
[   41.714748] usb 1-2: configuration #1 chosen from 1 choice
[   47.252338] Linux agpgart interface v0.101 (c) Dave Jones
[   47.267025] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.286809] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.294876] gameport: EMU10K1 is pci0000:02:00.1/gameport0, io 0xde00, speed 501kHz
[   48.316413] input: PC Speaker as /class/input/input1
[   48.400206] Floppy drive(s): fd0 is 1.44M
[   48.423743] FDC 0 is a post-1991 82077
[   48.443406] Linux video capture interface: v1.00
[   48.608406] 8139too Fast Ethernet driver 0.9.27
[   48.609133] eth0: RealTek RTL8139 at 0xf8a28000, 00:11:09:16:05:28, IRQ 5
[   48.609136] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   48.615223] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   48.671529] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   48.676990] parport: PnPBIOS parport detected.
[   48.677036] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   48.835923] usbcore: registered new driver hiddev
[   48.846793] input: Logitech USB Receiver as /class/input/input2
[   48.846827] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-1
[   48.856769] input: Logitech USB Receiver as /class/input/input3
[   48.856845] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-1
[   48.865745] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   48.865775] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   48.867295] input: Microsoft Microsoft IntelliMouse&#65533; Optical as /class/input/input4
[   48.867341] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse&#65533; Optical] on usb-0000:00:13.0-2
[   48.867352] usbcore: registered new driver usbhid
[   48.867355] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   48.895125] ts: Compaq touchscreen protocol output
[   49.007269] nvidia: module license 'NVIDIA' taints kernel.
[   49.260220] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   49.260432] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006
[   49.273425] bttv: driver version 0.9.16 loaded
[   49.273429] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   49.273484] bttv: Bt8xx card found (0).
[   49.273523] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 11, latency: 64, mmio: 0xfddff000
[   49.273542] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[   49.273546] bttv0: using: Twinhan DST + clones [card=113,autodetected]
[   49.273562] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   49.273600] bttv0: using tuner=4
[   49.310480] usbcore: registered new driver libusual
[   49.379261] bttv0: add subdevice "dvb0"
[   49.395868] bt878: AUDIO driver version 0.0.0 loaded
[   49.395901] bt878: Bt878 AUDIO function found (0).
[   49.395933] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
[   49.395943] bt878(0): Bt878 (rev 17) at 02:01.1, irq: 11, latency: 64, memory: 0xfddfe000
[   49.401500] Initializing USB Mass Storage driver...
[   49.401827] scsi4 : SCSI emulation for USB Mass Storage devices
[   49.401901] usbcore: registered new driver usb-storage
[   49.401904] USB Mass Storage support registered.
[   49.401907] usb-storage: device found at 4
[   49.401909] usb-storage: waiting for device to settle before scanning
[   49.730678] NET: Registered protocol family 17
[   50.011216] lp0: using parport0 (interrupt-driven).
[   50.026147] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   50.026151] ieee1394: sbp2: Try serialize_io=0 for better performance
[   50.057854] Adding 1992052k swap on /dev/disk/by-uuid/7692ef48-791d-486b-88a5-1b19afe79e59.  Priority:-1 extents:1 across:1992052k
[   50.198478] EXT3 FS on sda2, internal journal
[   50.465041] kjournald starting.  Commit interval 5 seconds
[   50.472928] EXT3 FS on sda6, internal journal
[   50.472933] EXT3-fs: mounted filesystem with ordered data mode.
[   50.486532] kjournald starting.  Commit interval 5 seconds
[   50.496943] EXT3 FS on sda5, internal journal
[   50.496947] EXT3-fs: mounted filesystem with ordered data mode.
[   50.504869] kjournald starting.  Commit interval 5 seconds
[   50.516918] EXT3 FS on sdb5, internal journal
[   50.516922] EXT3-fs: mounted filesystem with ordered data mode.
[   50.581983] NTFS driver 2.1.27 [Flags: R/O MODULE].
[   50.632492] NTFS volume version 3.1.
[   53.657733] NET: Registered protocol family 10
[   53.657815] lo: Disabled Privacy Extensions
[   53.657943] IPv6 over IPv4 tunneling driver
[   54.395683] usb-storage: device scan complete
[   54.399410]   Vendor: Apple     Model: iPod              Rev: 1.62
[   54.399418]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   54.415376] SCSI device sdc: 1982464 2048-byte hdwr sectors (4060 MB)
[   54.416918] sdc: Write Protect is off
[   54.416923] sdc: Mode Sense: 68 00 00 08
[   54.416926] sdc: assuming drive cache: write through
[   54.418999] SCSI device sdc: 1982464 2048-byte hdwr sectors (4060 MB)
[   54.419872] sdc: Write Protect is off
[   54.419875] sdc: Mode Sense: 68 00 00 08
[   54.419876] sdc: assuming drive cache: write through
[   54.419879]  sdc: sdc1 sdc2
[   54.422526] sd 4:0:0:0: Attached scsi removable disk sdc
[   54.422565] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   56.343868] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   56.358230] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   59.026492] apm: BIOS not found.
[   64.305849] eth0: no IPv6 routers present
[   64.386715] ip_tables: (C) 2000-2006 Netfilter Core Team
[   64.469298] Netfilter messages via NETLINK v0.30.
[   64.477197] ip_conntrack version 2.4 (8184 buckets, 65472 max) - 224 bytes per conntrack
[   65.596801] Bluetooth: Core ver 2.8
[   65.596806] NET: Registered protocol family 31
[   65.596808] Bluetooth: HCI device and connection manager initialized
[   65.596821] Bluetooth: HCI socket layer initialized
[   65.631442] Bluetooth: L2CAP ver 2.8
[   65.631446] Bluetooth: L2CAP socket layer initialized
[   65.657626] Bluetooth: RFCOMM socket layer initialized
[   65.657639] Bluetooth: RFCOMM TTY layer initialized
[   65.657641] Bluetooth: RFCOMM ver 1.7
[  115.922736] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  116.620100] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.67.250 LEN=197 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=32772 DPT=16680 LEN=177 
[  135.189550] Inbound IN=eth0 OUT= MAC=00:11:09:16:05:28:00:0f:66:91:3c:1e:08:00 SRC=71.111.174.85 DST=192.168.1.102 LEN=595 TOS=0x00 PREC=0x00 TTL=114 ID=34933 DF PROTO=TCP SPT=6881 DPT=45443 WINDOW=16532 RES=0x00 ACK PSH URGP=0 
[  140.021334] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=11979 PROTO=UDP SPT=2549 DPT=1900 LEN=140 
[  140.021449] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=11980 PROTO=UDP SPT=2549 DPT=1900 LEN=141 
[  141.518576] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=12065 PROTO=UDP SPT=2549 DPT=1900 LEN=140 
[  141.518605] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=12066 PROTO=UDP SPT=2549 DPT=1900 LEN=141 
[  175.845847] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  211.314399] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=17669 PROTO=UDP SPT=2568 DPT=1900 LEN=140 
[  211.314448] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=17670 PROTO=UDP SPT=2568 DPT=1900 LEN=141 
[  212.812289] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=17792 PROTO=UDP SPT=2568 DPT=1900 LEN=140 
[  212.812317] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=17793 PROTO=UDP SPT=2568 DPT=1900 LEN=141 
[  235.775822] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  295.702346] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  355.627948] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  415.551907] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  475.476186] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  535.402197] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  583.467764] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=50029 PROTO=UDP SPT=2636 DPT=1900 LEN=140 
[  583.467831] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=50030 PROTO=UDP SPT=2636 DPT=1900 LEN=141 
[  584.965141] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=50151 PROTO=UDP SPT=2636 DPT=1900 LEN=140 
[  584.965170] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=50152 PROTO=UDP SPT=2636 DPT=1900 LEN=141 
[  595.324656] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  631.659469] FAT: count of clusters too big (246935)
[  631.659475] VFS: Can't find a valid FAT filesystem on dev sdc.
[  655.246181] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  701.581367] Inbound IN=eth0 OUT= MAC=00:11:09:16:05:28:00:0f:66:91:3c:1e:08:00 SRC=89.243.53.218 DST=192.168.1.102 LEN=1400 TOS=0x00 PREC=0x00 TTL=111 ID=54485 DF PROTO=TCP SPT=36028 DPT=53454 WINDOW=64980 RES=0x00 ACK URGP=0 
[  715.172407] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  775.094251] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  835.016380] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  892.019433] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=10835 PROTO=UDP SPT=2747 DPT=1900 LEN=140 
[  892.019463] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=10836 PROTO=UDP SPT=2747 DPT=1900 LEN=141 
[  893.516645] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=10996 PROTO=UDP SPT=2747 DPT=1900 LEN=140 
[  893.516673] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=10997 PROTO=UDP SPT=2747 DPT=1900 LEN=141 
[  894.942497] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[  954.877570] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1014.802618] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1074.653514] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=25513 PROTO=UDP SPT=2838 DPT=1900 LEN=140 
[ 1074.653584] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=25514 PROTO=UDP SPT=2838 DPT=1900 LEN=141 
[ 1074.731899] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1076.150924] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=25643 PROTO=UDP SPT=2838 DPT=1900 LEN=140 
[ 1076.150953] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=161 TOS=0x00 PREC=0x00 TTL=1 ID=25644 PROTO=UDP SPT=2838 DPT=1900 LEN=141 
[ 1128.500005] FAT: count of clusters too big (246935)
[ 1128.500010] VFS: Can't find a valid FAT filesystem on dev sdc.
[ 1134.658740] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1181.308862] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:50:8d:97:ba:b8:08:00 SRC=192.168.1.101 DST=239.255.255.250 LEN=128 TOS=0x00 PREC=0x00 TTL=1 ID=35795 PROTO=UDP SPT=1035 DPT=1900 LEN=108 
[ 1194.584637] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1254.506751] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1314.433183] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1374.358623] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1434.281088] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1494.203150] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1554.129858] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1614.054957] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1673.976932] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1683.457370] FAT: count of clusters too big (246935)
[ 1683.457376] VFS: Can't find a valid FAT filesystem on dev sdc.
[ 1733.898952] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[ 1793.825028] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.102 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
```

Windows detects it as FAT32 and I get this when I try to mount it
sudo mount -t vfat /dev/sdc /media/ipod
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by onlybui on 2007-01-31
Sorry it looked like that fixed the problem running , just had to reboot.... {RESLOVED}

---

