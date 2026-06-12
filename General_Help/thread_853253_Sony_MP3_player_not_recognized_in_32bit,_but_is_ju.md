---
title: "Sony MP3 player not recognized in 32bit, but is just fine in 64bit?"
date: 2008-07-08
forum: General Help
---

### Post by Sir Rodness on 2008-07-08
Just a general question not sure who can answer it. I have a sony mp3 walkman that is recognized and usable in 64bit ubuntu 8.04. Recently I switch to 32bit ubuntu because of stronger software base(I'm moving back to 64bit when they catch up a bit more). But the issue is that 32 bit ubuntu doesn't recognize my walkman at all and actually it's only my walkman that can't be recognized. Everything else I plug in is fine.  It knows that some kind of USB device is attached but it won't mount it at all. I figured it would of been the other way around. Any one got some clues? Very strange.

---

### Post by Sir Rodness on 2008-07-17
Out of curiosity I decided to check 7.10 32bit to see if my mp3 player would work. It did, hmmm, so somewhere along the move to 8.04 something small was changed and overlooked. Truth be told I'm moving back to 64bit anyway so if someone could help me out with getting the java game Dynomite to work in 64bit properly I rather go with that fix. Tried a few of the java 32 walk-throughs don't seem to work. Is there a 32bit Java container of some sort. That would be a cool idea to run 32bit java games in the 64bit environment till they work out the kinks.

---

### Post by danwood76 on 2008-07-17
Odd, just a second ago here at work I plugged a Sony MP3 player (the little stick one) into my 32 bit laptop and it worked perfectly.

When you plug the device in run the following command in the terminal and  post the output:
```

dmesg

```
This will display any kernel messages relating to the mounting of your device.

---

### Post by Sir Rodness on 2008-07-21
Thanks for the interest. It was a pretty large dump from that code. I think it cut some of data off the top though. Also when you have a large chunk of code like this to display is there some type of embedded scrolling window that you can put it in. Feel like I'm spamming when pasting like this.

dump

[   24.326612] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   24.326616] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   24.326998] PCI: Transparent bridge - 0000:00:1e.0
[   24.327027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.327532] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   24.428679] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   24.429002] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   24.429319] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   24.429634] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   24.429950] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   24.430277] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   24.430595] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   24.430911] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   24.431181] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.431229] pnp: PnP ACPI init
[   24.431241] ACPI: bus type pnp registered
[   24.454491] pnp: PnP ACPI: found 10 devices
[   24.454495] ACPI: ACPI bus type pnp unregistered
[   24.454501] PnPBIOS: Disabled by ACPI PNP
[   24.454874] PCI: Using ACPI for IRQ routing
[   24.454879] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.474119] NET: Registered protocol family 8
[   24.474122] NET: Registered protocol family 20
[   24.474263] hpet clockevent registered
[   24.474269] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   24.474274] hpet0: 3 64-bit timers, 14318180 Hz
[   24.475320] AppArmor: AppArmor Filesystem Enabled
[   24.478102] Time: tsc clocksource has been installed.
[   24.486160] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   24.486164] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[   24.486167] system 00:00: iomem range 0x1000000-0x3fe6ffff could not be reserved
[   24.486170] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
[   24.486173] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   24.486176] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   24.486179] system 00:00: iomem range 0xfed20000-0xfed8ffff could not be reserved
[   24.486182] system 00:00: iomem range 0xfecf0000-0xfecf0fff could not be reserved
[   24.486185] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[   24.486188] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[   24.486201] system 00:09: ioport range 0x800-0x85f has been reserved
[   24.486204] system 00:09: ioport range 0xc00-0xc7f has been reserved
[   24.486207] system 00:09: ioport range 0x860-0x8ff could not be reserved
[   24.516761] PCI: Bridge: 0000:00:1e.0
[   24.516767]   IO window: d000-dfff
[   24.516773]   MEM window: fc000000-feafffff
[   24.516777]   PREFETCH window: e0000000-efffffff
[   24.516792] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.516807] NET: Registered protocol family 2
[   24.554060] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.554412] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.555071] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.555403] TCP: Hash tables configured (established 131072 bind 65536)
[   24.555408] TCP reno registered
[   24.566143] checking if image is initramfs... it is
[   24.977274] Switched to high resolution mode on CPU 0
[   25.192182] Freeing initrd memory: 7391k freed
[   25.192366] Simple Boot Flag at 0x7a set to 0x1
[   25.193037] audit: initializing netlink socket (disabled)
[   25.193052] audit(1216553784.460:1): initialized
[   25.193230] highmem bounce pool size: 64 pages
[   25.195641] VFS: Disk quotas dquot_6.5.1
[   25.195746] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.195926] io scheduler noop registered
[   25.195930] io scheduler anticipatory registered
[   25.195932] io scheduler deadline registered
[   25.195950] io scheduler cfq registered (default)
[   25.196035] Boot video device is 0000:01:01.0
[   25.196040] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   25.196434] isapnp: Scanning for PnP cards...
[   25.547815] isapnp: No Plug & Play device found
[   25.619616] Real Time Clock Driver v1.12ac
[   25.619730] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.619871] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.621402] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.622521] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.622616] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.622829] PNP: No PS/2 controller found. Probing ports directly.
[   25.625868] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.625874] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.632228] mice: PS/2 mouse device common for all mice
[   25.632406] EISA: Probing bus 0 at eisa.0
[   25.632443] EISA: Detected 0 cards.
[   25.632447] cpuidle: using governor ladder
[   25.632449] cpuidle: using governor menu
[   25.632537] NET: Registered protocol family 1
[   25.632569] Using IPI No-Shortcut mode
[   25.632601] registered taskstats version 1
[   25.632695]   Magic number: 0:256:631
[   25.632753]   hash matches device ptyca
[   25.632816] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.632818] EDD information not available.
[   25.633083] Freeing unused kernel memory: 368k freed
[   25.962073] vesafb: framebuffer at 0xe0000000, mapped to 0xf8880000, using 10240k, total 262144k
[   25.962079] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   25.962081] vesafb: protected mode interface info at c000:d3a0
[   25.962084] vesafb: pmi: set display start = c00cd3d6, set palette = c00cd440
[   25.962086] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[   25.962098] vesafb: scrolling: redraw
[   25.962101] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   25.962284] Console: switching to colour frame buffer device 160x64
[   26.094543] fb0: VESA VGA frame buffer device
[   27.382156] fuse init (API version 7.9)
[   27.407213] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.978251] usbcore: registered new interface driver usbfs
[   27.978281] usbcore: registered new interface driver hub
[   27.987000] usbcore: registered new device driver usb
[   28.001964] USB Universal Host Controller Interface driver v3.0
[   28.002037] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.002050] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   28.002055] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   28.002353] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   28.002388] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[   28.002549] usb usb1: configuration #1 chosen from 1 choice
[   28.002580] hub 1-0:1.0: USB hub found
[   28.002589] hub 1-0:1.0: 2 ports detected
[   28.056090] SCSI subsystem initialized
[   28.103863] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   28.103878] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   28.103883] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   28.103915] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   28.103946] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[   28.104073] usb usb2: configuration #1 chosen from 1 choice
[   28.104105] hub 2-0:1.0: USB hub found
[   28.104113] hub 2-0:1.0: 2 ports detected
[   28.117695] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   28.117699] e100: Copyright(c) 1999-2006 Intel Corporation
[   28.118497] libata version 3.00 loaded.
[   28.207673] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   28.207688] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   28.207693] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   28.207726] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 3
[   28.207753] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[   28.207882] usb usb3: configuration #1 chosen from 1 choice
[   28.207914] hub 3-0:1.0: USB hub found
[   28.207922] hub 3-0:1.0: 2 ports detected
[   28.208038] Floppy drive(s): fd0 is 1.44M
[   28.225628] FDC 0 is a post-1991 82077
[   28.311639] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 18
[   28.311658] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   28.311662] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   28.311704] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   28.315618] ehci_hcd 0000:00:1d.7: debug port 1
[   28.315626] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   28.315639] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80800
[   28.343355] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   28.355341] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.355526] usb usb4: configuration #1 chosen from 1 choice
[   28.355558] hub 4-0:1.0: USB hub found
[   28.355567] hub 4-0:1.0: 8 ports detected
[   28.459375] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 19
[   28.480002] e100: eth0: e100_probe: addr 0xfe9ff000, irq 19, MAC addr 00:16:76:87:ec:b4
[   28.480031] ata_piix 0000:00:1f.1: version 2.12
[   28.480054] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[   28.480095] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.482123] scsi0 : ata_piix
[   28.483737] scsi1 : ata_piix
[   28.483800] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   28.483803] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   28.647222] ata1.00: ATA-6: WDC WD800BB-75JHC0, 06.01C06, max UDMA/100
[   28.647227] ata1.00: 156250000 sectors, multi 8: LBA 
[   28.655131] ata1.00: configured for UDMA/100
[   28.910370] usb 4-2: new high speed USB device using ehci_hcd and address 2
[   29.189264] usb 4-2: configuration #1 chosen from 1 choice
[   29.321938] ata2.00: ATAPI: DVD RW DRU-820A, 1.0b, max UDMA/66
[   29.321968] ata2.01: ATAPI: SONY CD-RW/DVD-ROM CRX310EE, SDK3, max UDMA/33
[   29.321984] ata2.00: limited to UDMA/33 due to 40-wire cable
[   29.425404] usb 4-3: new high speed USB device using ehci_hcd and address 3
[   29.493609] ata2.00: configured for UDMA/33
[   29.559186] usb 4-3: configuration #1 chosen from 1 choice
[   29.681185] ata2.01: configured for UDMA/33
[   29.681342] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BB-75JH 06.0 PQ: 0 ANSI: 5
[   29.683123] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DRU-820A  1.0b PQ: 0 ANSI: 5
[   29.684413] scsi 1:0:1:0: CD-ROM            SONY     CDRWDVD CRX310EE SDK3 PQ: 0 ANSI: 5
[   29.704598] Driver 'sd' needs updating - please use bus_type methods
[   29.704700] sd 0:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
[   29.704718] sd 0:0:0:0: [sda] Write Protect is off
[   29.704721] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.704746] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.704813] sd 0:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
[   29.704828] sd 0:0:0:0: [sda] Write Protect is off
[   29.704831] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.704854] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.704859]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   29.732345]  sda1 sda2 sda3
[   29.749640] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.758157] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.758186] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   29.758209] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   29.765673] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   29.765680] Uniform CD-ROM driver Revision: 3.20
[   29.765746] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.774706] sr1: scsi3-mmc drive: 0x/48x writer cd/rw xa/form2 cdda tray
[   29.774787] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   29.805183] usbcore: registered new interface driver libusual
[   29.815680] Initializing USB Mass Storage driver...
[   29.820339] scsi2 : SCSI emulation for USB Mass Storage devices
[   29.821944] usbcore: registered new interface driver usb-storage
[   29.821951] USB Mass Storage support registered.
[   29.822079] usb-storage: device found at 3
[   29.822083] usb-storage: waiting for device to settle before scanning
[   30.068282] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   30.238061] usb 2-2: configuration #1 chosen from 1 choice
[   30.244000] hub 2-2:1.0: USB hub found
[   30.244957] hub 2-2:1.0: 2 ports detected
[   30.327930] Attempting manual resume
[   30.327936] swsusp: Resume From Partition 8:2
[   30.327937] PM: Checking swsusp image.
[   30.328148] PM: Resume from disk failed.
[   30.356823] kjournald starting.  Commit interval 5 seconds
[   30.356843] EXT3-fs: mounted filesystem with ordered data mode.
[   30.557352] usb 2-2.1: new full speed USB device using uhci_hcd and address 3
[   30.705181] usb 2-2.1: configuration #1 chosen from 1 choice
[   30.912679] usb 2-2.2: new full speed USB device using uhci_hcd and address 4
[   31.096440] usb 2-2.2: configuration #1 chosen from 1 choice
[   34.812176] usb-storage: device scan complete
[   34.847492] scsi 2:0:0:0: Direct-Access     Hitachi  HDT725032VLAT80  V54O PQ: 0 ANSI: 0
[   34.848953] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   34.849826] sd 2:0:0:0: [sdb] Write Protect is off
[   34.849830] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   34.849833] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   34.850823] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   34.851698] sd 2:0:0:0: [sdb] Write Protect is off
[   34.851701] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   34.851703] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   34.851708]  sdb: sdb1
[   34.871914] sd 2:0:0:0: [sdb] Attached SCSI disk
[   34.871966] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   38.519704] input: PC Speaker as /devices/platform/pcspkr/input/input1
[   38.669282] Linux agpgart interface v0.102
[   38.749057] intel_rng: Firmware space is locked read-only. If you can't or
[   38.749061] intel_rng: don't want to disable this in firmware setup, and if
[   38.749062] intel_rng: you are certain that your system has a functional
[   38.749064] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   38.884840] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.940783] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.028613] agpgart: Detected an Intel 865 Chipset.
[   39.028862] agpgart: Detected 892K stolen memory.
[   39.059397] agpgart: AGP aperture is 128M @ 0xd0000000
[   39.375967] iTCO_vendor_support: vendor-support=0
[   39.409294] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   39.409402] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   39.409442] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   39.448008] input: Power Button (FF) as /devices/virtual/input/input2
[   39.459788] ACPI: Power Button (FF) [PWRF]
[   39.459877] input: Power Button (CM) as /devices/virtual/input/input3
[   39.475761] ACPI: Power Button (CM) [VBTN]
[   40.156640] parport_pc 00:08: reported by Plug and Play ACPI
[   40.156694] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   40.242574] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   40.526059] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   40.526087] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   40.949869] nvidia: module license 'NVIDIA' taints kernel.
[   40.954240] intel8x0_measure_ac97_clock: measured 61480 usecs
[   40.954245] intel8x0: clocking to 48000
[   41.740244] Linux video capture interface: v2.00
[   41.836474] usbcore: registered new interface driver snd-usb-audio
[   41.851689] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)
[   41.867402] usbcore: registered new interface driver uvcvideo
[   41.867409] USB Video Class driver (v0.1.0)
[   41.883675] usbcore: registered new interface driver hiddev
[   41.894978] input: Logitech VoIP USB Dual RF Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.1/2-2.1:1.0/input/input4
[   41.919538] input,hidraw0: USB HID v1.11 Keyboard [Logitech VoIP USB Dual RF Receiver] on usb-0000:00:1d.1-2.1
[   41.923405] input: Logitech VoIP USB Dual RF Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.1/2-2.1:1.1/input/input5
[   41.967551] input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech VoIP USB Dual RF Receiver] on usb-0000:00:1d.1-2.1
[   41.967577] usbcore: registered new interface driver usbhid
[   41.967582] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   42.008271] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 22 (level, low) -> IRQ 22
[   42.008499] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   44.097987] lp0: using parport0 (interrupt-driven).
[   44.173742] Adding 2000084k swap on /dev/sda2.  Priority:-1 extents:1 across:2000084k
[   44.748061] EXT3 FS on sda3, internal journal
[   46.109393] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.683289] No dock devices found.
[   48.068543] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   48.068550] apm: overridden by ACPI.
[   48.895183] ppdev: user-space parallel port driver
[   49.081689] audit(1216568208.127:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5026 profile="/usr/sbin/cupsd" namespace="default"
[   52.186328] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   52.186336] vboxdrv: Successfully done.
[   52.186338] vboxdrv: Found 1 processor cores.
[   52.186342] vboxdrv: fAsync=0 u64DiffCores=1.
[   52.186402] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   52.186404] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002).
[   52.479778] tun: Universal TUN/TAP device driver, 1.6
[   52.479784] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   55.962851] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   56.057224] Bluetooth: Core ver 2.11
[   56.057946] NET: Registered protocol family 31
[   56.057952] Bluetooth: HCI device and connection manager initialized
[   56.057957] Bluetooth: HCI socket layer initialized
[   56.086602] Bluetooth: L2CAP ver 2.9
[   56.086608] Bluetooth: L2CAP socket layer initialized
[   56.144563] Bluetooth: RFCOMM socket layer initialized
[   56.144826] Bluetooth: RFCOMM TTY layer initialized
[   56.144832] Bluetooth: RFCOMM ver 1.8
[   58.402800] NET: Registered protocol family 17
[   61.501884] NET: Registered protocol family 10
[   61.502465] lo: Disabled Privacy Extensions
[   72.170244] eth0: no IPv6 routers present
[80351.402040] usb 4-8: new high speed USB device using ehci_hcd and address 5
[80351.535147] usb 4-8: configuration #1 chosen from 1 choice
[80351.573176] scsi3 : SCSI emulation for USB Mass Storage devices
[80351.574399] usb-storage: device found at 5
[80351.574405] usb-storage: waiting for device to settle before scanning
[80356.565171] usb-storage: device scan complete
[80356.566301] scsi 3:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 0 CCS
[80357.583604] ready
[80357.584352] sd 3:0:0:0: [sdc] 899072 2048-byte hardware sectors (1841 MB)
[80357.686790] sd 3:0:0:0: [sdc] Write Protect is off
[80357.686798] sd 3:0:0:0: [sdc] Mode Sense: 00 2a 00 00
[80357.686802] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[80357.689017] sd 3:0:0:0: [sdc] 899072 2048-byte hardware sectors (1841 MB)
[80357.796582] sd 3:0:0:0: [sdc] Write Protect is off
[80357.796591] sd 3:0:0:0: [sdc] Mode Sense: 00 2a 00 00
[80357.796594] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[80357.796602]  sdc: sdc1
[80357.803084]  sdc: p1 exceeds device capacity
[80357.803628] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[80357.803690] sd 3:0:0:0: Attached scsi generic sg4 type 0
[80357.944972] attempt to access beyond end of device
[80357.944983] sdc: rw=0, want=4294967044, limit=3596288
[80357.944987] Buffer I/O error on device sdc1, logical block 1073741760
[80357.944992] attempt to access beyond end of device
[80357.944994] sdc: rw=0, want=4294967048, limit=3596288
[80357.944997] Buffer I/O error on device sdc1, logical block 1073741761
[80357.945001] attempt to access beyond end of device
[80357.945004] sdc: rw=0, want=4294967044, limit=3596288
[80357.945006] Buffer I/O error on device sdc1, logical block 1073741760
[80357.945009] attempt to access beyond end of device
[80357.945011] sdc: rw=0, want=4294967048, limit=3596288
[80357.945013] Buffer I/O error on device sdc1, logical block 1073741761
[80357.945033] attempt to access beyond end of device
[80357.945036] sdc: rw=0, want=4294967276, limit=3596288
[80357.945039] Buffer I/O error on device sdc1, logical block 1073741818
[80357.945042] attempt to access beyond end of device
[80357.945044] sdc: rw=0, want=4294967280, limit=3596288
[80357.945046] Buffer I/O error on device sdc1, logical block 1073741819
[80357.945050] attempt to access beyond end of device
[80357.945052] sdc: rw=0, want=4294967276, limit=3596288
[80357.945054] Buffer I/O error on device sdc1, logical block 1073741818
[80357.945056] attempt to access beyond end of device
[80357.945059] sdc: rw=0, want=4294967280, limit=3596288
[80357.945061] Buffer I/O error on device sdc1, logical block 1073741819
[80357.945132] attempt to access beyond end of device
[80357.945137] sdc: rw=0, want=4294967292, limit=3596288
[80357.945140] Buffer I/O error on device sdc1, logical block 1073741822
[80357.945144] attempt to access beyond end of device
[80357.945146] sdc: rw=0, want=4294967292, limit=3596288
[80357.945149] Buffer I/O error on device sdc1, logical block 1073741822
[80357.945158] attempt to access beyond end of device
[80357.945160] sdc: rw=0, want=4294967292, limit=3596288
[80357.945168] attempt to access beyond end of device
[80357.945170] sdc: rw=0, want=4294967292, limit=3596288
[80357.945177] attempt to access beyond end of device
[80357.945179] sdc: rw=0, want=4294967292, limit=3596288
[80357.945187] attempt to access beyond end of device
[80357.945189] sdc: rw=0, want=4294967292, limit=3596288
[80357.945196] attempt to access beyond end of device
[80357.945198] sdc: rw=0, want=4294967292, limit=3596288
[80357.945207] attempt to access beyond end of device
[80357.945210] sdc: rw=0, want=4294967228, limit=3596288
[80357.945212] attempt to access beyond end of device
[80357.945215] sdc: rw=0, want=4294967232, limit=3596288
[80357.945223] attempt to access beyond end of device
[80357.945226] sdc: rw=0, want=4294967284, limit=3596288
[80357.945229] attempt to access beyond end of device
[80357.945231] sdc: rw=0, want=4294967288, limit=3596288
[80357.945238] attempt to access beyond end of device
[80357.945240] sdc: rw=0, want=4294967292, limit=3596288
[80357.945248] attempt to access beyond end of device
[80357.945250] sdc: rw=0, want=4294967292, limit=3596288
[80765.623869] usb 4-8: USB disconnect, address 5
[80779.617204] usb 4-8: new high speed USB device using ehci_hcd and address 6
[80779.750360] usb 4-8: configuration #1 chosen from 1 choice
[80779.789010] scsi4 : SCSI emulation for USB Mass Storage devices
[80779.790191] usb-storage: device found at 6
[80779.790197] usb-storage: waiting for device to settle before scanning
[80784.780382] usb-storage: device scan complete
[80784.781515] scsi 4:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 0 CCS
[80785.798883] ready
[80785.799952] sd 4:0:0:0: [sdc] 899072 2048-byte hardware sectors (1841 MB)
[80785.902137] sd 4:0:0:0: [sdc] Write Protect is off
[80785.902145] sd 4:0:0:0: [sdc] Mode Sense: 00 2a 00 00
[80785.902148] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[80785.904359] sd 4:0:0:0: [sdc] 899072 2048-byte hardware sectors (1841 MB)
[80786.011921] sd 4:0:0:0: [sdc] Write Protect is off
[80786.011929] sd 4:0:0:0: [sdc] Mode Sense: 00 2a 00 00
[80786.011932] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[80786.011941]  sdc: sdc1
[80786.013805]  sdc: p1 exceeds device capacity
[80786.014355] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[80786.014419] sd 4:0:0:0: Attached scsi generic sg4 type 0
[80786.135728] attempt to access beyond end of device
[80786.135739] sdc: rw=0, want=4294967044, limit=3596288
[80786.135743] printk: 11 messages suppressed.
[80786.135746] Buffer I/O error on device sdc1, logical block 1073741760
[80786.135751] attempt to access beyond end of device
[80786.135753] sdc: rw=0, want=4294967048, limit=3596288
[80786.135756] Buffer I/O error on device sdc1, logical block 1073741761
[80786.135760] attempt to access beyond end of device
[80786.135762] sdc: rw=0, want=4294967044, limit=3596288
[80786.135764] Buffer I/O error on device sdc1, logical block 1073741760
[80786.135767] attempt to access beyond end of device
[80786.135769] sdc: rw=0, want=4294967048, limit=3596288
[80786.135772] Buffer I/O error on device sdc1, logical block 1073741761
[80786.135785] attempt to access beyond end of device
[80786.135788] sdc: rw=0, want=4294967276, limit=3596288
[80786.135790] Buffer I/O error on device sdc1, logical block 1073741818
[80786.135793] attempt to access beyond end of device
[80786.135796] sdc: rw=0, want=4294967280, limit=3596288
[80786.135798] Buffer I/O error on device sdc1, logical block 1073741819
[80786.135801] attempt to access beyond end of device
[80786.135803] sdc: rw=0, want=4294967276, limit=3596288
[80786.135805] Buffer I/O error on device sdc1, logical block 1073741818
[80786.135808] attempt to access beyond end of device
[80786.135810] sdc: rw=0, want=4294967280, limit=3596288
[80786.135812] Buffer I/O error on device sdc1, logical block 1073741819
[80786.135897] attempt to access beyond end of device
[80786.135902] sdc: rw=0, want=4294967292, limit=3596288
[80786.135905] Buffer I/O error on device sdc1, logical block 1073741822
[80786.135909] attempt to access beyond end of device
[80786.135911] sdc: rw=0, want=4294967292, limit=3596288
[80786.135913] Buffer I/O error on device sdc1, logical block 1073741822
[80786.135923] attempt to access beyond end of device
[80786.135925] sdc: rw=0, want=4294967292, limit=3596288
[80786.135933] attempt to access beyond end of device
[80786.135935] sdc: rw=0, want=4294967292, limit=3596288
[80786.135942] attempt to access beyond end of device
[80786.135944] sdc: rw=0, want=4294967292, limit=3596288
[80786.135952] attempt to access beyond end of device
[80786.135954] sdc: rw=0, want=4294967292, limit=3596288
[80786.135961] attempt to access beyond end of device
[80786.135964] sdc: rw=0, want=4294967292, limit=3596288
[80786.135973] attempt to access beyond end of device
[80786.135976] sdc: rw=0, want=4294967228, limit=3596288
[80786.135979] attempt to access beyond end of device
[80786.135981] sdc: rw=0, want=4294967232, limit=3596288
[80786.135989] attempt to access beyond end of device
[80786.135992] sdc: rw=0, want=4294967284, limit=3596288
[80786.135994] attempt to access beyond end of device
[80786.135996] sdc: rw=0, want=4294967288, limit=3596288
[80786.136004] attempt to access beyond end of device
[80786.136007] sdc: rw=0, want=4294967292, limit=3596288
[80786.136014] attempt to access beyond end of device
[80786.136017] sdc: rw=0, want=4294967292, limit=3596288

---

### Post by danwood76 on 2008-07-21
Yeah if you throw it in a set of code tags it will create a scrolling window.
So like [-code-] without the '-' to start and [-/code-] without the '-' to end the code segment. (Or select the text and click the code tage (#))

Right looking at this output I have seen this error before, I'm just gonna have a quick search to see if I can find the other thread.

---

### Post by danwood76 on 2008-07-21
Well I've had a look through previous threads and it looks like the Sony MP3s work very badly on linux based machines.
Some have had luck using pmount to mount their players:
[http://ubuntuforums.org/showpost.php?p=5127989&postcount=10](http://ubuntuforums.org/showpost.php?p=5127989&postcount=10)

The one I tested the other day here worked fine though I only read files from the device and my laptop is 32 bit.
I would just use 64 bit if its working in there, theres no real reason to use 32 bit. (flash support in 64 is a little bad but nspluginwrapper is pretty good for flash ;))

---

### Post by Sir Rodness on 2008-07-24
Thanks for the code scroll information and for the help with my MP3 player. I moved back to 64bit ubuntu a few days ago and I'm much happier.
My flash does work in 64bit, but of course that nasty menus covered by flash problem still remains. However, I'm willing to endure it since I can now put music on my MP3 player again. :)

Again, thanks for taking the time to help out, much appreciated.

---

### Post by DLF44 on 2008-12-07
i have a nwz sony player and have the same problems. it shows ip in"places" but i cant do anything with it.

i tried that code you said to enter and this is waht i got.

```
ls: cannot access /dev/disk/by-label: No such file or directory

```

---

