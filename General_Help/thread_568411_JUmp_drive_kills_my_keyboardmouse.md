---
title: "JUmp drive kills my keyboard/mouse"
date: 2007-10-05
forum: General Help
---

### Post by tomsyco on 2007-10-05
When i plug in my jump drive (sandisk) my keyboard and mouse (Logitech s510)  stop working. Its some kind of confliction because the dongle for the wireless keyboard/mouse wont even try to reconnect when i hit the connect button

---

### Post by dcstar on 2007-10-06
> **tomsyco said:**
> When i plug in my jump drive (sandisk) my keyboard and mouse (Logitech s510)  stop working. Its some kind of confliction because the dongle for the wireless keyboard/mouse wont even try to reconnect when i hit the connect button

Probably it is overloading the USB bus, in a terminal run:

```
dmesg
```

when you plug things in and check the output.

---

### Post by tomsyco on 2007-10-06
Heres what i got

[   28.108425] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   28.108768] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   28.109178] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   28.109264] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.109278] pnp: PnP ACPI init
[   28.114955] pnp: PnP ACPI: found 15 devices
[   28.115026] PCI: Using ACPI for IRQ routing
[   28.115030] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.115049] PCI: Cannot allocate resource region 0 of device 0000:00:04.0
[   28.115129] NET: Registered protocol family 8
[   28.115131] NET: Registered protocol family 20
[   28.115219] agpgart: Detected AGP bridge 20
[   28.115225] Setting up ULi AGP.
[   28.120235] agpgart: AGP aperture is 128M @ 0xd8000000
[   28.120972] pnp: 00:0d: ioport range 0x290-0x29f has been reserved
[   28.121251] PCI: Bridge: 0000:00:01.0
[   28.121253]   IO window: disabled.
[   28.121257]   MEM window: fc700000-fc7fffff
[   28.121259]   PREFETCH window: disabled.
[   28.121263] PCI: Bridge: 0000:00:02.0
[   28.121264]   IO window: disabled.
[   28.121268]   MEM window: fc800000-fc8fffff
[   28.121270]   PREFETCH window: disabled.
[   28.121273] PCI: Bridge: 0000:00:05.0
[   28.121274]   IO window: disabled.
[   28.121279]   MEM window: fc900000-fe9fffff
[   28.121283]   PREFETCH window: bff00000-cfefffff
[   28.121288] PCI: Bridge: 0000:00:06.0
[   28.121289]   IO window: disabled.
[   28.121294]   MEM window: fea00000-feafffff
[   28.121297]   PREFETCH window: disabled.
[   28.121316] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 29 (level, low) -> IRQ 29
[   28.121321] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.121328] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 34 (level, low) -> IRQ 34
[   28.121332] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   28.121339] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   28.121345] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   28.121425] NET: Registered protocol family 2
[   28.159388] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   28.159488] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[   28.159685] TCP bind hash table entries: 8192 (order: 5, 131072 bytes)
[   28.159788] TCP: Hash tables configured (established 16384 bind 8192)
[   28.159791] TCP reno registered
[   28.171441] checking if image is initramfs... it is
[   28.801763] Freeing initrd memory: 6837k freed
[   28.808871] audit: initializing netlink socket (disabled)
[   28.808889] audit(1191609707.208:1): initialized
[   28.809054] VFS: Disk quotas dquot_6.5.1
[   28.809075] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   28.809134] io scheduler noop registered
[   28.809136] io scheduler anticipatory registered
[   28.809139] io scheduler deadline registered
[   28.809151] io scheduler cfq registered (default)
[   28.870453] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.870476] assign_interrupt_mode Found MSI capability
[   28.870481] Allocate Port Service[0000:00:01.0:pcie00]
[   28.870554] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   28.870576] assign_interrupt_mode Found MSI capability
[   28.870579] Allocate Port Service[0000:00:02.0:pcie00]
[   28.895124] Real Time Clock Driver v1.12ac
[   28.895178] Linux agpgart interface v0.102 (c) Dave Jones
[   28.895181] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.895309] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.895486] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.896020] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.896234] mice: PS/2 mouse device common for all mice
[   28.896773] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.897047] input: Macintosh mouse button emulation as /class/input/input0
[   28.897080] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   28.897085] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.897341] PNP: No PS/2 controller found. Probing ports directly.
[   28.900597] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.900604] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.900717] TCP cubic registered
[   28.900726] NET: Registered protocol family 1
[   28.900893] ACPI: (supports S0 S1 S3 S4 S5)
[   28.900936]   Magic number: 11:441:695
[   28.901085]   hash matches device 0000:00:00.0
[   28.901088] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   28.901183] Freeing unused kernel memory: 304k freed
[   30.114786] Capability LSM initialized
[   30.153088] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   30.748186] SCSI subsystem initialized
[   30.754035] libata version 2.20 loaded.
[   30.757326] ALI15X3: IDE controller at PCI slot 0000:00:12.0
[   30.757343] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 19 (level, low) -> IRQ 19
[   30.757354] ALI15X3: chipset revision 199
[   30.757356] ALI15X3: not 100% native mode: will probe irqs later
[   30.757374]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
[   30.757387]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[   30.757397] Probing IDE interface ide0...
[   30.793617] usbcore: registered new interface driver usbfs
[   30.793648] usbcore: registered new interface driver hub
[   30.793676] usbcore: registered new device driver usb
[   30.794544] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   30.903384] Floppy drive(s): fd0 is 1.44M
[   30.962652] FDC 0 is a post-1991 82077
[   31.087049] hda: WDC WD800JB-00CRA1, ATA DISK drive
[   31.762913] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   31.781911] Probing IDE interface ide1...
[   32.520866] hdc: LITE-ON COMBO LTC-48161H, ATAPI CD/DVD-ROM drive
[   32.860260] ide1 at 0x170-0x177,0x376 on irq 15
[   32.860985] sata_uli 0000:00:12.1: version 1.1
[   32.860997] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 19 (level, low) -> IRQ 19
[   32.861090] ata1: SATA max UDMA/133 cmd 0x000000000001ec00 ctl 0x000000000001e082 bmdma 0x000000000001d880 irq 19
[   32.861121] ata2: SATA max UDMA/133 cmd 0x000000000001e000 ctl 0x000000000001dc02 bmdma 0x000000000001d888 irq 19
[   32.861137] scsi0 : sata_uli
[   32.867778] hda: max request size: 128KiB
[   32.876463] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[   32.876471] hda: cache flushes not supported
[   32.876532]  hda: hda1 hda2 < hda5 >
[   32.908788] hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(44)
[   32.908797] Uniform CD-ROM driver Revision: 3.20
[   33.068508] Attempting manual resume
[   33.068512] swsusp: Resume From Partition 3:5
[   33.068514] PM: Checking swsusp image.
[   33.068676] PM: Resume from disk failed.
[   33.108696] kjournald starting.  Commit interval 5 seconds
[   33.108708] EXT3-fs: mounted filesystem with ordered data mode.
[   33.179679] ata1: SATA link down (SStatus 0 SControl 300)
[   33.179716] scsi1 : sata_uli
[   33.647007] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.655255] ata2.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[   33.655262] ata2.00: ATA-7: ST3400832AS, 3.03, max UDMA/133
[   33.655265] ata2.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   33.667196] ata2.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[   33.667201] ata2.00: configured for UDMA/133
[   33.667714] scsi 1:0:0:0: Direct-Access     ATA      ST3400832AS      3.03 PQ: 0 ANSI: 5
[   33.668374] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 20 (level, low) -> IRQ 20
[   33.668393] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   33.668601] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   33.668623] ohci_hcd 0000:00:13.0: irq 20, io mem 0xfebfd000
[   33.729001] usb usb1: configuration #1 chosen from 1 choice
[   33.729031] hub 1-0:1.0: USB hub found
[   33.729043] hub 1-0:1.0: 3 ports detected
[   33.834857] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 21 (level, low) -> IRQ 21
[   33.834878] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   33.834905] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   33.834926] ohci_hcd 0000:00:13.1: irq 21, io mem 0xfebfc000
[   33.892719] usb usb2: configuration #1 chosen from 1 choice
[   33.892749] hub 2-0:1.0: USB hub found
[   33.892760] hub 2-0:1.0: 3 ports detected
[   33.998563] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 22 (level, low) -> IRQ 22
[   33.998585] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   33.998612] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   33.998633] ohci_hcd 0000:00:13.2: irq 22, io mem 0xfebfb000
[   34.056511] usb usb3: configuration #1 chosen from 1 choice
[   34.056541] hub 3-0:1.0: USB hub found
[   34.056553] hub 3-0:1.0: 3 ports detected
[   34.138218] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   34.162507] ACPI: PCI Interrupt 0000:00:13.3[D] -> GSI 23 (level, low) -> IRQ 23
[   34.162524] ehci_hcd 0000:00:13.3: EHCI Host Controller
[   34.162553] ehci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   34.162590] ehci_hcd 0000:00:13.3: debug port 1
[   34.190154] ehci_hcd 0000:00:13.3: irq 23, io mem 0xfebfe800
[   34.190161] ehci_hcd 0000:00:13.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.190270] usb usb4: configuration #1 chosen from 1 choice
[   34.190299] hub 4-0:1.0: USB hub found
[   34.190309] hub 4-0:1.0: 8 ports detected
[   34.925019] usb 4-5: new high speed USB device using ehci_hcd and address 3
[   35.057869] usb 4-5: configuration #1 chosen from 1 choice
[   37.892516] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   38.114308] usb 1-2: configuration #1 chosen from 1 choice
[   44.714743] ali1535_smbus 0000:00:07.1: ALI1535_smb region uninitialized - upgrade BIOS?
[   44.714749] ali1535_smbus 0000:00:07.1: ALI1535 not detected, module not inserted.
[   44.746849] ali15x3_smbus 0000:00:07.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   44.746855] ali15x3_smbus 0000:00:07.1: ALI15X3 not detected, module not inserted.
[   44.831414] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.833505] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.057567] ali1563: SMBus control = 0403
[   45.057641] ali1563_probe: Returning 0
[   45.183272] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
[   45.183336] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 17 (level, low) -> IRQ 17
[   45.204944] eth0: ULi M5263 at pci0000:00:11.0, 00:13:8f:49:bb:e5, irq 17.
[   45.538947] input: PC Speaker as /class/input/input1
[   45.561318] parport: PnPBIOS parport detected.
[   45.561429] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   45.829368] SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
[   45.832446] sda: Write Protect is off
[   45.832449] sda: Mode Sense: 00 3a 00 00
[   45.836230] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.840445] SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
[   45.840506] sda: Write Protect is off
[   45.840509] sda: Mode Sense: 00 3a 00 00
[   45.841205] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.841216]  sda: sda1 sda2
[   45.859389] sd 1:0:0:0: Attached scsi disk sda
[   46.078487] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   46.200263] irda_init()
[   46.200287] NET: Registered protocol family 23
[   46.216290] usb 4-5: USB disconnect, address 3
[   46.331699] usb 4-5: new high speed USB device using ehci_hcd and address 5
[   46.465991] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[   46.466098] usb 4-5: configuration #1 chosen from 1 choice
[   46.475367] usbcore: registered new interface driver libusual
[   46.475512] usbcore: registered new interface driver hiddev
[   46.494812] Initializing USB Mass Storage driver...
[   46.614462] input: Logitech USB Receiver as /class/input/input2
[   46.614512] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-2
[   46.614901] scsi2 : SCSI emulation for USB Mass Storage devices
[   46.614976] usbcore: registered new interface driver usb-storage
[   46.614980] USB Mass Storage support registered.
[   46.615142] usb-storage: device found at 5
[   46.615144] usb-storage: waiting for device to settle before scanning
[   46.624482] input: Logitech USB Receiver as /class/input/input3
[   46.624621] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2
[   46.624639] usbcore: registered new interface driver usbhid
[   46.624643] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   47.106127] NET: Registered protocol family 17
[   47.382187] usb 1-2: USB disconnect, address 3
[   47.481921] AC'97 1 does not respond - RESET
[   47.482473] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   47.482479] Unable to initialize codec #1
[   47.541833] intel8x0_measure_ac97_clock: measured 58920 usecs
[   47.541836] intel8x0: clocking to 48000
[   47.731178] fuse init (API version 7.8)
[   47.758962] lp0: using parport0 (interrupt-driven).
[   47.816588] Adding 1494004k swap on /dev/disk/by-uuid/59304220-ac78-428f-a2a7-7d2802c09c7e.  Priority:-1 extents:1 across:1494004k
[   47.950275] EXT3 FS on hda1, internal journal
[   48.760325] uli526x: eth0 NIC Link is Up 100 Mbps Full duplex
[   49.209019] NET: Registered protocol family 10
[   49.209134] lo: Disabled Privacy Extensions
[   51.608227] usb-storage: device scan complete
[   51.608712] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[   51.610438] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[   51.611058] sdb: Write Protect is off
[   51.611061] sdb: Mode Sense: 03 00 00 00
[   51.611063] sdb: assuming drive cache: write through
[   51.613180] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[   51.613803] sdb: Write Protect is off
[   51.613805] sdb: Mode Sense: 03 00 00 00
[   51.613807] sdb: assuming drive cache: write through
[   51.613812]  sdb: sdb1
[   51.614876] sd 2:0:0:0: Attached scsi removable disk sdb
[   51.614924] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   54.239600] No dock devices found.
[   54.356720] ibm_acpi: ec object not found
[   54.393798] Using specific hotkey driver
[   54.456590] input: Power Button (FF) as /class/input/input4
[   54.461464] ACPI: Power Button (FF) [PWRF]
[   54.491166] input: Power Button (CM) as /class/input/input5
[   54.495961] ACPI: Power Button (CM) [PWRB]
[   54.674353] pcc_acpi: loading...
[   54.921746] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   54.921789] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   54.921792] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0xa
[   58.388918] ppdev: user-space parallel port driver
[   59.291480] Bluetooth: Core ver 2.11
[   59.291552] NET: Registered protocol family 31
[   59.291554] Bluetooth: HCI device and connection manager initialized
[   59.291558] Bluetooth: HCI socket layer initialized
[   59.317766] Bluetooth: L2CAP ver 2.8
[   59.317771] Bluetooth: L2CAP socket layer initialized
[   59.525505] Bluetooth: RFCOMM socket layer initialized
[   59.525518] Bluetooth: RFCOMM TTY layer initialized
[   59.525520] Bluetooth: RFCOMM ver 1.8
[   67.656045] eth0: no IPv6 routers present
[   70.738031] usb 4-5: USB disconnect, address 5
[   70.740428] scsi 2:0:0:0: rejecting I/O to dead device
[   70.740523] scsi 2:0:0:0: rejecting I/O to dead device
[   70.740599] scsi 2:0:0:0: rejecting I/O to dead device
[   70.740605] scsi 2:0:0:0: rejecting I/O to dead device
[   70.740609] sdb : READ CAPACITY failed.
[   70.740610] sdb : status=0, message=00, host=1, driver=00 
[   70.740612] sdb : sense not available. 
[   70.740616] scsi 2:0:0:0: rejecting I/O to dead device
[   70.740620] sdb: Write Protect is off
[   70.740622] sdb: Mode Sense: 00 00 00 00
[   70.740624] sdb: assuming drive cache: write through
[   70.740633] scsi 2:0:0:0: rejecting I/O to dead device
[   70.740637] scsi 2:0:0:0: rejecting I/O to dead device
[   70.740642] scsi 2:0:0:0: rejecting I/O to dead device
[   70.740646] scsi 2:0:0:0: rejecting I/O to dead device
[   70.740650] sdb : READ CAPACITY failed.
[   70.740651] sdb : status=0, message=00, host=1, driver=00 
[   70.740653] sdb : sense not available. 
[   70.740657] scsi 2:0:0:0: rejecting I/O to dead device
[   70.740660] sdb: Write Protect is off
[   70.740662] sdb: Mode Sense: 00 00 00 00
[   70.740663] sdb: assuming drive cache: write through
[   72.473153] usb 4-6: new high speed USB device using ehci_hcd and address 6
[   72.547380] usb 4-6: configuration #1 chosen from 1 choice
[   72.547522] scsi3 : SCSI emulation for USB Mass Storage devices
[   72.547640] usb-storage: device found at 6
[   72.547642] usb-storage: waiting for device to settle before scanning
[   75.320537] usb-storage: device scan complete
[   75.320860] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[   75.322130] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[   75.322458] sdb: Write Protect is off
[   75.322461] sdb: Mode Sense: 03 00 00 00
[   75.322463] sdb: assuming drive cache: write through
[   75.323843] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[   75.324189] sdb: Write Protect is off
[   75.324192] sdb: Mode Sense: 03 00 00 00
[   75.324193] sdb: assuming drive cache: write through
[   75.324199]  sdb: sdb1
[   75.324739] sd 3:0:0:0: Attached scsi removable disk sdb
[   75.324781] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   80.210253] usb 1-1: new low speed USB device using ohci_hcd and address 4
[   80.329066] usb 1-1: configuration #1 chosen from 1 choice
[   80.334653] input: Logitech USB Receiver as /class/input/input6
[   80.334685] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-1
[   80.340249] input: Logitech USB Receiver as /class/input/input7
[   80.340333] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-1
[   80.923877] usb 1-1: USB disconnect, address 4
[   80.927416] hald-addon-keyb[5448] general protection rip:2b292da2021b rsp:7fff7d766f50 error:0
[   80.927559] hald-addon-keyb[5456] general protection rip:2b774c14221b rsp:7fff5f044820 error:0
[  104.807402] usb 1-2: new low speed USB device using ohci_hcd and address 5
[  104.928435] usb 1-2: configuration #1 chosen from 1 choice
[  104.934021] input: Logitech USB Receiver as /class/input/input8
[  104.934053] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-2
[  104.939613] input: Logitech USB Receiver as /class/input/input9
[  104.939695] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2
[  105.042641] usb 4-6: USB disconnect, address 6
[  105.043593] scsi 3:0:0:0: rejecting I/O to dead device
[  105.043678] scsi 3:0:0:0: rejecting I/O to dead device
[  105.043756] scsi 3:0:0:0: rejecting I/O to dead device
[  105.043761] scsi 3:0:0:0: rejecting I/O to dead device
[  105.043765] sdb : READ CAPACITY failed.
[  105.043766] sdb : status=0, message=00, host=1, driver=00 
[  105.043768] sdb : sense not available. 
[  105.043772] scsi 3:0:0:0: rejecting I/O to dead device
[  105.043776] sdb: Write Protect is off
[  105.043778] sdb: Mode Sense: 00 00 00 00
[  105.043779] sdb: assuming drive cache: write through
[  105.043787] scsi 3:0:0:0: rejecting I/O to dead device
[  105.043791] scsi 3:0:0:0: rejecting I/O to dead device
[  105.043795] scsi 3:0:0:0: rejecting I/O to dead device
[  105.043800] scsi 3:0:0:0: rejecting I/O to dead device
[  105.043804] sdb : READ CAPACITY failed.
[  105.043805] sdb : status=0, message=00, host=1, driver=00 
[  105.043807] sdb : sense not available. 
[  105.043810] scsi 3:0:0:0: rejecting I/O to dead device
[  105.043813] sdb: Write Protect is off
[  105.043815] sdb: Mode Sense: 00 00 00 00
[  105.043817] sdb: assuming drive cache: write through
[  496.117438] usb 1-2: USB disconnect, address 5
[  496.125156] hald-addon-keyb[5497] general protection rip:2ac0f766921b rsp:7fffb3b1e300 error:0
[  496.125304] hald-addon-keyb[5543] general protection rip:2ad73cbad21b rsp:7fff6e5d7db0 error:0
[  496.448033] usb 4-5: new high speed USB device using ehci_hcd and address 10
[  496.521980] usb 4-5: configuration #1 chosen from 1 choice
[  496.522115] scsi4 : SCSI emulation for USB Mass Storage devices
[  496.522242] usb-storage: device found at 10
[  496.522244] usb-storage: waiting for device to settle before scanning
[  499.297352] usb-storage: device scan complete
[  499.297710] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[  499.299203] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[  499.299549] sdb: Write Protect is off
[  499.299551] sdb: Mode Sense: 03 00 00 00
[  499.299554] sdb: assuming drive cache: write through
[  499.300934] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[  499.301281] sdb: Write Protect is off
[  499.301284] sdb: Mode Sense: 03 00 00 00
[  499.301286] sdb: assuming drive cache: write through
[  499.301289]  sdb: sdb1
[  499.301830] sd 4:0:0:0: Attached scsi removable disk sdb
[  499.301875] sd 4:0:0:0: Attached scsi generic sg1 type 0
[  538.966299] usb 4-5: USB disconnect, address 10
[  539.427804] usb 1-2: new low speed USB device using ohci_hcd and address 6
[  539.568786] usb 1-2: configuration #1 chosen from 1 choice
[  539.578827] input: Logitech USB Receiver as /class/input/input10
[  539.578873] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-2
[  539.588870] input: Logitech USB Receiver as /class/input/input11
[  539.588970] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2
[  651.643353] usb 1-2: USB disconnect, address 6
[  651.649588] hald-addon-keyb[6188] general protection rip:2b75942d721b rsp:7fff16eae690 error:0
[  651.649732] hald-addon-keyb[6214] general protection rip:2b7c3f9aa21b rsp:7fff6b7dcfb0 error:0
[  651.871153] usb 4-1: new high speed USB device using ehci_hcd and address 12
[  651.945093] usb 4-1: configuration #1 chosen from 1 choice
[  651.945231] scsi5 : SCSI emulation for USB Mass Storage devices
[  651.945352] usb-storage: device found at 12
[  651.945354] usb-storage: waiting for device to settle before scanning
[  654.718247] usb-storage: device scan complete
[  654.718569] scsi 5:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[  654.719895] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[  654.720239] sdb: Write Protect is off
[  654.720242] sdb: Mode Sense: 03 00 00 00
[  654.720244] sdb: assuming drive cache: write through
[  654.721624] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[  654.721970] sdb: Write Protect is off
[  654.721973] sdb: Mode Sense: 03 00 00 00
[  654.721975] sdb: assuming drive cache: write through
[  654.721978]  sdb: sdb1
[  654.722555] sd 5:0:0:0: Attached scsi removable disk sdb
[  654.722597] sd 5:0:0:0: Attached scsi generic sg1 type 0
[  667.764652] usb 4-1: USB disconnect, address 12
[  667.764949] Buffer I/O error on device sdb1, logical block 495
[  667.764953] lost page write due to I/O error on sdb1
[  668.595365] usb 1-2: new low speed USB device using ohci_hcd and address 7
[  668.817146] usb 1-2: configuration #1 chosen from 1 choice
[  668.827182] input: Logitech USB Receiver as /class/input/input12
[  668.827228] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-2
[  668.837219] input: Logitech USB Receiver as /class/input/input13
[  668.837316] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2
[ 1698.550918] usb 1-1: new low speed USB device using ohci_hcd and address 8
[ 1698.672442] usb 1-1: configuration #1 chosen from 1 choice
[ 1698.680233] input: HID 1241:1166 as /class/input/input14
[ 1698.680293] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:13.0-1
[ 1722.259029] usb 1-2: USB disconnect, address 7
[ 1722.264977] hald-addon-keyb[6446] general protection rip:2b7d3097d21b rsp:7fff7a807ff0 error:0
[ 1722.265122] hald-addon-keyb[6467] general protection rip:2b9a18aff21b rsp:7fff92685e60 error:0
[ 1722.487780] usb 4-5: new high speed USB device using ehci_hcd and address 15
[ 1722.562078] usb 4-5: configuration #1 chosen from 1 choice
[ 1722.562212] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1722.562343] usb-storage: device found at 15
[ 1722.562345] usb-storage: waiting for device to settle before scanning
[ 1725.334676] usb-storage: device scan complete
[ 1725.335001] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[ 1725.336527] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[ 1725.336872] sdb: Write Protect is off
[ 1725.336875] sdb: Mode Sense: 03 00 00 00
[ 1725.336877] sdb: assuming drive cache: write through
[ 1725.338326] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[ 1725.338673] sdb: Write Protect is off
[ 1725.338675] sdb: Mode Sense: 03 00 00 00
[ 1725.338677] sdb: assuming drive cache: write through
[ 1725.338681]  sdb: sdb1
[ 1725.339264] sd 6:0:0:0: Attached scsi removable disk sdb
[ 1725.339305] sd 6:0:0:0: Attached scsi generic sg1 type 0
[ 1734.575291] usb 1-1: USB disconnect, address 8
[ 1736.363006] usb 1-1: new low speed USB device using ohci_hcd and address 9
[ 1736.484028] usb 1-1: configuration #1 chosen from 1 choice
[ 1736.491811] input: HID 1241:1166 as /class/input/input15
[ 1736.491868] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:13.0-1
[ 1744.043885] usb 1-1: USB disconnect, address 9
[ 1748.165033] usb 4-5: USB disconnect, address 15
[ 1748.165259] Buffer I/O error on device sdb1, logical block 495
[ 1748.165263] lost page write due to I/O error on sdb1
[ 1748.457912] usb 1-2: new low speed USB device using ohci_hcd and address 10
[ 1748.603797] usb 1-2: configuration #1 chosen from 1 choice
[ 1748.613833] input: Logitech USB Receiver as /class/input/input16
[ 1748.613878] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-2
[ 1748.623876] input: Logitech USB Receiver as /class/input/input17
[ 1748.623977] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2

---

### Post by dcstar on 2007-10-09
> **tomsyco said:**
> Heres what i got
...................
[ 1698.550918] usb 1-1: new low speed USB device using ohci_hcd and address 8
[ 1698.672442] usb 1-1: configuration #1 chosen from 1 choice
[ 1698.680233] input: HID 1241:1166 as /class/input/input14
[ 1698.680293] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:13.0-1
[ 1722.259029] usb 1-2: USB disconnect, address 7
[ 1722.264977] hald-addon-keyb[6446] general protection rip:2b7d3097d21b rsp:7fff7a807ff0 error:0
[ 1722.265122] hald-addon-keyb[6467] general protection rip:2b9a18aff21b rsp:7fff92685e60 error:0
[ 1722.487780] usb 4-5: new high speed USB device using ehci_hcd and address 15
[ 1722.562078] usb 4-5: configuration #1 chosen from 1 choice
[ 1722.562212] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1722.562343] usb-storage: device found at 15
[ 1722.562345] usb-storage: waiting for device to settle before scanning
[ 1725.334676] usb-storage: device scan complete
[ 1725.335001] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[ 1725.336527] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[ 1725.336872] sdb: Write Protect is off
[ 1725.336875] sdb: Mode Sense: 03 00 00 00
[ 1725.336877] sdb: assuming drive cache: write through
[ 1725.338326] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[ 1725.338673] sdb: Write Protect is off
[ 1725.338675] sdb: Mode Sense: 03 00 00 00
[ 1725.338677] sdb: assuming drive cache: write through
[ 1725.338681]  sdb: sdb1
[ 1725.339264] sd 6:0:0:0: Attached scsi removable disk sdb
[ 1725.339305] sd 6:0:0:0: Attached scsi generic sg1 type 0
[ 1734.575291] usb 1-1: USB disconnect, address 8
[ 1736.363006] usb 1-1: new low speed USB device using ohci_hcd and address 9
[ 1736.484028] usb 1-1: configuration #1 chosen from 1 choice
[ 1736.491811] input: HID 1241:1166 as /class/input/input15
[ 1736.491868] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:13.0-1
[ 1744.043885] usb 1-1: USB disconnect, address 9
**[ 1748.165033] usb 4-5: USB disconnect, address 15**
[B][ 1748.165259] Buffer I/O error on device sdb1, logical block 495
[ 1748.165263] lost page write due to I/O error on sdb1[/B]
[ 1748.457912] usb 1-2: new low speed USB device using ohci_hcd and address 10
[ 1748.603797] usb 1-2: configuration #1 chosen from 1 choice
[ 1748.613833] input: Logitech USB Receiver as /class/input/input16
[ 1748.613878] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-2
[ 1748.623876] input: Logitech USB Receiver as /class/input/input17
[ 1748.623977] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2

There are numerous repeated problems in that list, some of the serious ones I have highlighted.

I can only guess that the mouse and USB drive are both conflicting/overloading the USB system, can you move the mouse to another USB connector?

---

### Post by tomsyco on 2007-10-09
Ive tried my mouse/keyboard is plugged in the rear and the jump drive in the remote ones in the front. Thats the error i noticed just didn't know what to make of it. Thanks for your help I apppreciate you reviewing the error. :)

---

