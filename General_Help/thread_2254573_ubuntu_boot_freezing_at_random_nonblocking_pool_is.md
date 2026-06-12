---
title: "ubuntu boot freezing at random: nonblocking pool is initialized"
date: 2014-11-28
forum: General Help
---

### Post by kumsy on 2014-11-28
Hello everybody, :)
This is my first time here posting in the ubuntu forums. I have a small doubt I would like to clarify with you all. I'm currently running Ubuntu 14.04 and I'm having the following issue. The boot suddenly freezes with the message "random: nonblocking pool is initialized" around 4 seconds. The boot speed is at a respectable 19 seconds, which is great for a hard drive, but I would still like to sort out this issue.
```

[    0.459875] microcode: CPU5 sig=0x306a9, pf=0x2, revision=0x15[    0.459881] microcode: CPU6 sig=0x306a9, pf=0x2, revision=0x15
[    0.459888] microcode: CPU7 sig=0x306a9, pf=0x2, revision=0x15
[    0.459928] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.459930] Scanning for low memory corruption every 60 seconds
[    0.460123] Initialise system trusted keyring
[    0.460153] audit: initializing netlink socket (disabled)
[    0.460162] type=2000 audit(1417193383.452:1): initialized
[    0.478660] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.479295] zbud: loaded
[    0.479391] VFS: Disk quotas dquot_6.5.2
[    0.479416] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.479666] fuse init (API version 7.22)
[    0.479724] msgmni has been set to 7835
[    0.479758] Key type big_key registered
[    0.480131] Key type asymmetric registered
[    0.480132] Asymmetric key parser 'x509' registered
[    0.480150] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.480192] io scheduler noop registered
[    0.480194] io scheduler deadline registered (default)
[    0.480207] io scheduler cfq registered
[    0.480336] pcieport 0000:00:01.0: irq 41 for MSI/MSI-X
[    0.480455] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.480464] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.480486] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.480488] vesafb: scrolling: redraw
[    0.480489] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    0.480698] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90004780000, using 3072k, total 3072k
[    0.512100] Console: switching to colour frame buffer device 128x48
[    0.543825] fb0: VESA VGA frame buffer device
[    0.544092] intel_idle: MWAIT substates: 0x1120
[    0.544093] intel_idle: v0.4 model 0x3A
[    0.544094] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.544190] ipmi message handler version 39.2
[    0.544495] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.544979] ACPI: Power Button [PWRB]
[    0.545212] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.545648] ACPI: Power Button [PWRF]
[    0.545900] ACPI: Fan [FAN0] (off)
[    0.546115] ACPI: Fan [FAN1] (off)
[    0.546329] ACPI: Fan [FAN2] (off)
[    0.546544] ACPI: Fan [FAN3] (off)
[    0.546758] ACPI: Fan [FAN4] (off)
[    0.551928] thermal LNXTHERM:00: registered as thermal_zone0
[    0.552262] ACPI: Thermal Zone [TZ00] (28 C)
[    0.552645] thermal LNXTHERM:01: registered as thermal_zone1
[    0.552978] ACPI: Thermal Zone [TZ01] (30 C)
[    0.553243] GHES: HEST is not enabled!
[    0.553512] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.574323] 00:08: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.575664] Linux agpgart interface v0.103
[    0.576683] brd: module loaded
[    0.577250] loop: module loaded
[    0.577644] libphy: Fixed MDIO Bus: probed
[    0.577933] tun: Universal TUN/TAP device driver, 1.6
[    0.589310] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.600835] PPP generic driver version 2.4.2
[    0.612313] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.623924] ehci-pci: EHCI PCI platform driver
[    0.635488] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.647081] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.658752] ehci-pci 0000:00:1a.0: debug port 2
[    0.674110] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.674126] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7f28000
[    0.695793] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.707335] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.719125] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.730976] usb usb1: Product: EHCI Host Controller
[    0.742679] usb usb1: Manufacturer: Linux 3.13.0-39-generic ehci_hcd
[    0.754371] usb usb1: SerialNumber: 0000:00:1a.0
[    0.766077] hub 1-0:1.0: USB hub found
[    0.777684] hub 1-0:1.0: 2 ports detected
[    0.789383] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.801027] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.812748] ehci-pci 0000:00:1d.0: debug port 2
[    0.828143] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.828155] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7f27000
[    0.847863] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.859309] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.870833] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.882235] usb usb2: Product: EHCI Host Controller
[    0.893472] usb usb2: Manufacturer: Linux 3.13.0-39-generic ehci_hcd
[    0.904756] usb usb2: SerialNumber: 0000:00:1d.0
[    0.916095] hub 2-0:1.0: USB hub found
[    0.926940] hub 2-0:1.0: 2 ports detected
[    0.937594] ehci-platform: EHCI generic platform driver
[    0.948110] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.958584] ohci-pci: OHCI PCI platform driver
[    0.969098] ohci-platform: OHCI generic platform driver
[    0.979830] uhci_hcd: USB Universal Host Controller Interface driver
[    0.990919] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.005233] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.016961] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.028665] mousedev: PS/2 mouse device common for all mice
[    1.040460] rtc_cmos 00:05: RTC can wake from S4
[    1.052104] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.064069] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.075864] device-mapper: uevent: version 1.0.3
[    1.087577] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.099391] ledtrig-cpu: registered to indicate activity on CPUs
[    1.111204] TCP: cubic registered
[    1.122892] IPv6: Loaded, but administratively disabled, reboot required to enable
[    1.128038] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.147396] NET: Registered protocol family 17
[    1.159694] Key type dns_resolver registered
[    1.172305] Loading compiled-in X.509 certificates
[    1.185057] Loaded X.509 cert 'Magrathea: Glacier signing key: e3c165d0891e3ceeb6dd5c18c7e1993cd24956b0'
[    1.197649] registered taskstats version 1
[    1.211964] Key type trusted registered
[    1.225855] Key type encrypted registered
[    1.239591] AppArmor: AppArmor sha1 policy hashing enabled
[    1.251896] IMA: No TPM chip found, activating TPM-bypass!
[    1.264453] regulator-dummy: disabling
[    1.272453] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.272454] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.272595] hub 1-1:1.0: USB hub found
[    1.272701] hub 1-1:1.0: 4 ports detected
[    1.326489]   Magic number: 6:620:844
[    1.338614] hub 1-1:1.0: hash matches
[    1.350809] rtc_cmos 00:05: setting system clock to 2014-11-28 16:49:45 UTC (1417193385)
[    1.364374] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.375764] EDD information not available.
[    1.384144] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.398424] PM: Hibernation image not present or could not be loaded.
[    1.399023] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.410714] Write protecting the kernel read-only data: 12288k
[    1.423880] Freeing unused kernel memory: 804K (ffff880001737000 - ffff880001800000)
[    1.437030] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    1.456156] tsc: Refined TSC clocksource calibration: 3392.291 MHz
[    1.480913] systemd-udevd[142]: starting version 204
[    1.502340] pps_core: LinuxPPS API ver. 1 registered
[    1.502341] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.503171] PTP clock support registered
[    1.516570] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.516571] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.516831] hub 2-1:1.0: USB hub found
[    1.516937] hub 2-1:1.0: 6 ports detected
[    1.571239] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    1.571240] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    1.571554] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.571574] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[    1.588345] usb 1-1.1: new low-speed USB device number 3 using ehci-pci
[    1.687261] usb 1-1.1: New USB device found, idVendor=413c, idProduct=2107
[    1.700355] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.713375] usb 1-1.1: Product: Dell USB Entry Keyboard
[    1.726170] usb 1-1.1: Manufacturer: Dell
[    1.741251] hidraw: raw HID events driver (C) Jiri Kosina
[    1.758368] usbcore: registered new interface driver usbhid
[    1.771111] usbhid: USB HID core driver
[    1.784650] input: Dell Dell USB Entry Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input5
[    1.798213] hid-generic 0003:413C:2107.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Entry Keyboard] on usb-0000:00:1a.0-1.1/input0
[    1.808449] usb 1-1.2: new low-speed USB device number 4 using ehci-pci
[    1.829123] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.829133] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 70:54:d2:c4:5c:ab
[    1.829134] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.829163] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    1.829189] ahci 0000:00:1f.2: version 3.0
[    1.829328] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.844363] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x30 impl SATA mode
[    1.844364] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.852796] scsi0 : ahci
[    1.852887] scsi1 : ahci
[    1.852971] scsi2 : ahci
[    1.853056] scsi3 : ahci
[    1.853137] scsi4 : ahci
[    1.853219] scsi5 : ahci
[    1.853256] ata1: DUMMY
[    1.853256] ata2: DUMMY
[    1.853257] ata3: DUMMY
[    1.853257] ata4: DUMMY
[    1.853259] ata5: SATA max UDMA/133 abar m2048@0xf7f26000 port 0xf7f26300 irq 43
[    1.853261] ata6: SATA max UDMA/133 abar m2048@0xf7f26000 port 0xf7f26380 irq 43
[    1.903985] usb 1-1.2: New USB device found, idVendor=0461, idProduct=4d22
[    1.903986] usb 1-1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    1.903987] usb 1-1.2: Product: USB Optical Mouse
[    1.906246] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input6
[    1.906414] hid-generic 0003:0461:4D22.0002: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.0-1.2/input0
[    2.112580] hub 2-1:1.0: over-current condition on port 1
[    2.172504] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.184249] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.195946] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.195951] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.207791] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.220182] ata6.00: ATA-8: ST1000DM003-1CH162, CC46, max UDMA/133
[    2.232146] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.244206] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.244209] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.256400] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.269107] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.269112] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.280996] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.292800] ata5.00: ATAPI: HL-DT-ST DVDRAM GH24NS95, RN01, max UDMA/133
[    2.304865] ata6.00: configured for UDMA/133
[    2.318150] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.318156] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.320683] hub 2-1:1.0: over-current condition on port 2
[    2.341584] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.354732] ata5.00: configured for UDMA/133
[    2.368723] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS95  RN01 PQ: 0 ANSI: 5
[    2.385735] sr0: scsi3-mmc drive: 24x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.398116] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.410290] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.410359] sr 4:0:0:0: Attached scsi generic sg0 type 5
[    2.422412] scsi 5:0:0:0: Direct-Access     ATA      ST1000DM003-1CH1 CC46 PQ: 0 ANSI: 5
[    2.434034] sd 5:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.434068] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    2.457449] sd 5:0:0:0: [sda] 4096-byte physical blocks
[    2.469494] Switched to clocksource tsc
[    2.469514] sd 5:0:0:0: [sda] Write Protect is off
[    2.469515] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.469532] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.505692]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.517725] sd 5:0:0:0: [sda] Attached SCSI disk
[    2.528770] hub 2-1:1.0: over-current condition on port 3
[    2.736896] hub 2-1:1.0: over-current condition on port 4
[    2.820932] usb 2-1.6: new full-speed USB device number 3 using ehci-pci
[    2.930578] usb 2-1.6: New USB device found, idVendor=045e, idProduct=028e
[    2.942741] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.955080] usb 2-1.6: Product: Controller
[    2.967472] usb 2-1.6: Manufacturer: \xffffffc2\xffffffa9\xffffffa9Microsoft Corporation
[    2.980113] usb 2-1.6: SerialNumber: 0968AE6
[    3.355139] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    3.697951] random: nonblocking pool is initialized
[   15.158515] systemd-udevd[328]: starting version 204
[   15.196538] lp: driver loaded but no devices found
[   15.199505] ppdev: user-space parallel port driver
[   15.216083] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[   15.218985] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   15.218990] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.218993] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   15.218996] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.218997] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   15.219000] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.219001] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   15.219003] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.219004] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   15.220822] [drm] Initialized drm 1.1.0 20060810
[   15.248391] [drm] radeon kernel modesetting enabled.
[   15.248425] checking generic (e0000000 300000) vs hw (e0000000 10000000)
[   15.248426] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[   15.248442] Console: switching to colour dummy device 80x25
[   15.249249] [drm] initializing kernel modesetting (PITCAIRN 0x1002:0x6819 0x1458:0x2553).
[   15.249279] [drm] register mmio base: 0xF7E00000
[   15.249281] [drm] register mmio size: 262144
[   15.249361] ATOM BIOS: GV
[   15.249408] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[   15.249410] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[   15.249412] [drm] Detected VRAM RAM=2048M, BAR=256M
[   15.249413] [drm] RAM width 256bits DDR
[   15.249449] [TTM] Zone  kernel: Available graphics memory: 2007272 kiB
[   15.249450] [TTM] Initializing pool allocator
[   15.249454] [TTM] Initializing DMA pool allocator
[   15.249467] [drm] radeon: 2048M of VRAM memory ready
[   15.249468] [drm] radeon: 1024M of GTT memory ready.
[   15.249476] [drm] Loading PITCAIRN Microcode
[   15.266798] systemd-udevd[352]: renamed network interface eth0 to eth1
[   15.276119] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   15.287577] input: Microsoft X-Box 360 pad as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7
[   15.287638] usbcore: registered new interface driver xpad
[   15.289236] SKU: Nid=0x1d sku_cfg=0x4016c629
[   15.289238] SKU: port_connectivity=0x1
[   15.289238] SKU: enable_pcbeep=0x1
[   15.289239] SKU: check_sum=0x00000006
[   15.289239] SKU: customization=0x000000c6
[   15.289240] SKU: external_amp=0x5
[   15.289240] SKU: platform_type=0x0
[   15.289241] SKU: swap=0x0
[   15.289241] SKU: override=0x1
[   15.289521] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   15.289523]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   15.289524]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   15.289524]    mono: mono_out=0x0
[   15.289525]    dig-out=0x11/0x0
[   15.289525]    inputs:
[   15.289527]      Front Mic=0x19
[   15.289527]      Rear Mic=0x18
[   15.289528]      Line=0x1a
[   15.289529] realtek: No valid SSID, checking pincfg 0x4016c629 for NID 0x1d
[   15.289530] realtek: Enabling init ASM_ID=0xc629 CODEC_ID=10ec0892
[   15.299178] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.299228] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   15.299271] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.401792] intel_rapl: domain uncore energy ctr 0:0 not working, skip
[   15.659250] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   15.659427] type=1400 audit(1417173599.800:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=476 comm="apparmor_parser"
[   15.659440] type=1400 audit(1417173599.800:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=476 comm="apparmor_parser"
[   15.659443] type=1400 audit(1417173599.800:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=476 comm="apparmor_parser"
[   15.659485] type=1400 audit(1417173599.800:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=477 comm="apparmor_parser"
[   15.659490] type=1400 audit(1417173599.800:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=477 comm="apparmor_parser"
[   15.659494] type=1400 audit(1417173599.800:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=477 comm="apparmor_parser"
[   15.659712] type=1400 audit(1417173599.800:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=476 comm="apparmor_parser"
[   15.659715] type=1400 audit(1417173599.800:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=476 comm="apparmor_parser"
[   15.659831] type=1400 audit(1417173599.800:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=477 comm="apparmor_parser"
[   15.659834] type=1400 audit(1417173599.800:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=477 comm="apparmor_parser"
[   15.663262] [drm] radeon/PITCAIRN_mc2.bin: 31100 bytes
[   15.703219] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   15.703708] [drm] probing gen 2 caps for device 8086:151 = 261ad03/e
[   15.703711] [drm] PCIE gen 3 link speeds already enabled
[   15.709937] [drm] PCIE GART of 1024M enabled (table at 0x0000000000276000).
[   15.710041] radeon 0000:01:00.0: WB enabled
[   15.710044] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff880118395c00
[   15.710045] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff880118395c04
[   15.710047] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff880118395c08
[   15.710048] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff880118395c0c
[   15.710049] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff880118395c10
[   15.710655] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90004d35a18
[   15.710657] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   15.710658] [drm] Driver supports precise vblank timestamp query.
[   15.710674] radeon 0000:01:00.0: irq 46 for MSI/MSI-X
[   15.710682] radeon 0000:01:00.0: radeon: using MSI.
[   15.710709] [drm] radeon: irq initialized.
[   15.866878] [drm] ring test on 0 succeeded in 4 usecs
[   15.866883] [drm] ring test on 1 succeeded in 1 usecs
[   15.866886] [drm] ring test on 2 succeeded in 1 usecs
[   15.866949] [drm] ring test on 3 succeeded in 2 usecs
[   15.866958] [drm] ring test on 4 succeeded in 1 usecs
[   15.927785] Adding 4194300k swap on /swapfile.  Priority:-1 extents:7 across:6553596k FS
[   15.954448] init: failsafe main process (612) killed by TERM signal
[   16.013812] Bluetooth: Core ver 2.17
[   16.013822] NET: Registered protocol family 31
[   16.013823] Bluetooth: HCI device and connection manager initialized
[   16.013828] Bluetooth: HCI socket layer initialized
[   16.013830] Bluetooth: L2CAP socket layer initialized
[   16.013831] Bluetooth: SCO socket layer initialized
[   16.016805] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.016807] Bluetooth: BNEP filters: protocol multicast
[   16.016813] Bluetooth: BNEP socket layer initialized
[   16.018584] Bluetooth: RFCOMM TTY layer initialized
[   16.018587] Bluetooth: RFCOMM socket layer initialized
[   16.018591] Bluetooth: RFCOMM ver 1.11
[   16.052680] [drm] ring test on 5 succeeded in 2 usecs
[   16.052685] [drm] UVD initialized successfully.
[   16.053859] [drm] Enabling audio 0 support
[   16.053860] [drm] Enabling audio 1 support
[   16.053861] [drm] Enabling audio 2 support
[   16.053862] [drm] Enabling audio 3 support
[   16.053862] [drm] Enabling audio 4 support
[   16.053863] [drm] Enabling audio 5 support
[   16.053927] [drm] ib test on ring 0 succeeded in 0 usecs
[   16.053973] [drm] ib test on ring 1 succeeded in 0 usecs
[   16.054018] [drm] ib test on ring 2 succeeded in 0 usecs
[   16.054061] [drm] ib test on ring 3 succeeded in 0 usecs
[   16.054102] [drm] ib test on ring 4 succeeded in 1 usecs
[   16.115395] init: avahi-cups-reload main process (725) terminated with status 1
[   16.205136] [drm] ib test on ring 5 succeeded
[   16.205470] [drm] Radeon Display Connectors
[   16.205471] [drm] Connector 0:
[   16.205472] [drm]   DP-1
[   16.205472] [drm]   HPD4
[   16.205473] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[   16.205474] [drm]   Encoders:
[   16.205474] [drm]     DFP1: INTERNAL_UNIPHY2
[   16.205475] [drm] Connector 1:
[   16.205475] [drm]   DP-2
[   16.205476] [drm]   HPD5
[   16.205477] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[   16.205477] [drm]   Encoders:
[   16.205478] [drm]     DFP2: INTERNAL_UNIPHY2
[   16.205478] [drm] Connector 2:
[   16.205479] [drm]   HDMI-A-1
[   16.205480] [drm]   HPD1
[   16.205480] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[   16.205481] [drm]   Encoders:
[   16.205481] [drm]     DFP3: INTERNAL_UNIPHY1
[   16.205482] [drm] Connector 3:
[   16.205483] [drm]   DVI-I-1
[   16.205483] [drm]   HPD6
[   16.205484] [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
[   16.205484] [drm]   Encoders:
[   16.205485] [drm]     DFP4: INTERNAL_UNIPHY
[   16.205486] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   16.205539] [drm] Internal thermal controller with fan control
[   16.205564] [drm] probing gen 2 caps for device 8086:151 = 261ad03/e
[   16.667166] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   16.771224] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   17.334670] init: samba-ad-dc main process (804) terminated with status 1
[   17.397974] [drm] radeon: dpm initialized
[   17.443813] [drm] fb mappable at 0xE1480000
[   17.443815] [drm] vram apper at 0xE0000000
[   17.443815] [drm] size 4325376
[   17.443816] [drm] fb depth is 24
[   17.443816] [drm]    pitch is 5632
[   17.443902] fbcon: radeondrmfb (fb0) is primary device
[   18.000257] Console: switching to colour frame buffer device 170x48
[   18.001801] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   18.001803] radeon 0000:01:00.0: registered panic notifier
[   18.001806] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[   18.001934] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   18.001936] hda-intel 0000:01:00.1: Using LPIB position fix
[   18.001937] hda-intel 0000:01:00.1: Force to non-snoop mode
[   18.001970] snd_hda_intel 0000:01:00.1: irq 47 for MSI/MSI-X
[   18.004380] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[   18.007366] HDMI ATI/AMD: no speaker allocation for ELD
[   18.007402] HDMI ATI/AMD: no speaker allocation for ELD
[   18.007438] HDMI ATI/AMD: no speaker allocation for ELD
[   18.007474] HDMI ATI/AMD: no speaker allocation for ELD
[   18.007511] HDMI ATI/AMD: no speaker allocation for ELD
[   18.007549] HDMI ATI/AMD: no speaker allocation for ELD
[   18.007597] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[   18.007652] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[   18.007696] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   18.007738] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   18.007796] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   18.007904] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   19.382510] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   19.382514] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO



```

---

### Post by eduardobcastro on 2015-09-10
Same here:

```
[    2.553152] usb 7-2: Manufacturer: Broadcom Corp
[    3.246746] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.812078] random: nonblocking pool is initialized
[   19.069302] systemd-udevd[352]: starting version 204
[   19.217365] lp: driver loaded but no devices found
[   19.224705] ppdev: user-space parallel port driver
[   19.284294] wmi: Mapper loaded
[   19.308131] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.320202] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
```

The message **IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready** was after **random: nonblocking pool is initialized**. I disabled IPv6 and now I know that IPv6 was not the problem.

---

