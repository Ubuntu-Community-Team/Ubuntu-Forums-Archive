---
title: "Slow boot time (Dual-Boot Windows 8.1 Alongside Ubuntu)"
date: 2016-03-15
forum: General Help
---

### Post by Simon_Thriault on 2016-03-15
Hey Guys, 

My boot time is quite long with Ubuntu, I would say it is about 90 seconds, while it is quite fast for Windows (a few seconds)
What could be the problem? Here is the result from the "dmesg" command: 

```
[    0.518011] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.518020] pci 0000:00:1c.0:   bridge window [mem 0xd1400000-0xd14fffff 64bit pref]
[    0.518028] pci 0000:00:1c.2: PCI bridge to [bus 08]
[    0.518034] pci 0000:00:1c.2:   bridge window [mem 0xd1600000-0xd16fffff]
[    0.518045] pci 0000:00:1c.3: PCI bridge to [bus 09]
[    0.518052] pci 0000:00:1c.3:   bridge window [mem 0xd1500000-0xd15fffff]
[    0.518064] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.518066] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.518068] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.518071] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
[    0.518073] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
[    0.518075] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
[    0.518077] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
[    0.518079] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
[    0.518081] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
[    0.518083] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
[    0.518086] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
[    0.518088] pci_bus 0000:00: resource 15 [mem 0x9fa00000-0xfeafffff window]
[    0.518090] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.518092] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xd0ffffff]
[    0.518094] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xbfffffff 64bit pref]
[    0.518097] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
[    0.518099] pci_bus 0000:07: resource 2 [mem 0xd1400000-0xd14fffff 64bit pref]
[    0.518101] pci_bus 0000:08: resource 1 [mem 0xd1600000-0xd16fffff]
[    0.518103] pci_bus 0000:09: resource 1 [mem 0xd1500000-0xd15fffff]
[    0.518144] NET: Registered protocol family 2
[    0.518350] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.518541] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.518722] TCP: Hash tables configured (established 65536 bind 65536)
[    0.518762] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.518797] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.518871] NET: Registered protocol family 1
[    0.518887] pci 0000:00:02.0: Video device with shadowed ROM
[    0.550952] PCI: CLS 64 bytes, default 64
[    0.551011] Trying to unpack rootfs image as initramfs...
[    0.952052] Freeing initrd memory: 19584K (ffff8800359b0000 - ffff880036cd0000)
[    0.952109] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.952112] software IO TLB [mem 0x8f1c0000-0x931c0000] (64MB) mapped at [ffff88008f1c0000-ffff8800931bffff]
[    0.952189] RAPL PMU detected, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    0.952191] hw unit of domain pp0-core 2^-16 Joules
[    0.952192] hw unit of domain package 2^-16 Joules
[    0.952194] hw unit of domain pp1-gpu 2^-16 Joules
[    0.952328] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15
[    0.952337] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x15
[    0.952350] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x15
[    0.952360] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x15
[    0.952427] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.952527] Scanning for low memory corruption every 60 seconds
[    0.952952] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.952985] Initialise system trusted keyring
[    0.953009] audit: initializing netlink subsys (disabled)
[    0.953026] audit: type=2000 audit(1458005300.916:1): initialized
[    0.953469] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.955241] zpool: loaded
[    0.955244] zbud: loaded
[    0.955484] VFS: Disk quotas dquot_6.6.0
[    0.955525] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.956066] fuse init (API version 7.23)
[    0.956229] Key type big_key registered
[    0.956640] Key type asymmetric registered
[    0.956644] Asymmetric key parser 'x509' registered
[    0.956663] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.956711] io scheduler noop registered
[    0.956716] io scheduler deadline registered (default)
[    0.956754] io scheduler cfq registered
[    0.957404] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.957412] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.957449] efifb: probing for efifb
[    0.957463] efifb: framebuffer at 0xc0000000, mapped to 0xffffc90001000000, using 5632k, total 5632k
[    0.957464] efifb: mode is 1600x900x32, linelength=6400, pages=1
[    0.957465] efifb: scrolling: redraw
[    0.957467] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.957586] Console: switching to colour frame buffer device 200x56
[    0.957612] fb0: EFI VGA frame buffer device
[    0.957623] intel_idle: MWAIT substates: 0x21120
[    0.957624] intel_idle: v0.4 model 0x3A
[    0.957626] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.957878] ACPI: AC Adapter [ACAD] (on-line)
[    0.957953] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0
[    0.957958] ACPI: Power Button [PWRB]
[    0.958010] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.958032] ACPI: Lid Switch [LID0]
[    0.958074] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.958077] ACPI: Power Button [PWRF]
[    0.958407] GHES: HEST is not enabled!
[    0.958540] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.195379] ACPI: Battery Slot [BAT1] (battery present)
[    1.195607] Linux agpgart interface v0.103
[    1.198521] brd: module loaded
[    1.199657] loop: module loaded
[    1.199901] libphy: Fixed MDIO Bus: probed
[    1.199907] tun: Universal TUN/TAP device driver, 1.6
[    1.199908] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.199966] PPP generic driver version 2.4.2
[    1.200185] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.200194] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    1.201281] xhci_hcd 0000:00:14.0: hcc params 0x20007181 hci version 0x100 quirks 0x0000b930
[    1.201290] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.201386] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.201388] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.201390] usb usb1: Product: xHCI Host Controller
[    1.201392] usb usb1: Manufacturer: Linux 4.2.0-27-generic xhci-hcd
[    1.201394] usb usb1: SerialNumber: 0000:00:14.0
[    1.201538] hub 1-0:1.0: USB hub found
[    1.201549] hub 1-0:1.0: 4 ports detected
[    1.201930] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.201934] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.201972] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    1.201974] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.201976] usb usb2: Product: xHCI Host Controller
[    1.201977] usb usb2: Manufacturer: Linux 4.2.0-27-generic xhci-hcd
[    1.201979] usb usb2: SerialNumber: 0000:00:14.0
[    1.202108] hub 2-0:1.0: USB hub found
[    1.202119] hub 2-0:1.0: 4 ports detected
[    1.202493] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.202500] ehci-pci: EHCI PCI platform driver
[    1.202610] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.202616] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.202629] ehci-pci 0000:00:1a.0: debug port 2
[    1.206529] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.206544] ehci-pci 0000:00:1a.0: irq 16, io mem 0xd1719000
[    1.215357] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.215401] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.215404] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.215406] usb usb3: Product: EHCI Host Controller
[    1.215407] usb usb3: Manufacturer: Linux 4.2.0-27-generic ehci_hcd
[    1.215409] usb usb3: SerialNumber: 0000:00:1a.0
[    1.215572] hub 3-0:1.0: USB hub found
[    1.215580] hub 3-0:1.0: 2 ports detected
[    1.215787] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.215795] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    1.215808] ehci-pci 0000:00:1d.0: debug port 2
[    1.219727] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.219741] ehci-pci 0000:00:1d.0: irq 23, io mem 0xd1718000
[    1.231392] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.231436] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    1.231438] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.231440] usb usb4: Product: EHCI Host Controller
[    1.231442] usb usb4: Manufacturer: Linux 4.2.0-27-generic ehci_hcd
[    1.231444] usb usb4: SerialNumber: 0000:00:1d.0
[    1.231611] hub 4-0:1.0: USB hub found
[    1.231618] hub 4-0:1.0: 2 ports detected
[    1.231726] ehci-platform: EHCI generic platform driver
[    1.231738] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.231744] ohci-pci: OHCI PCI platform driver
[    1.231759] ohci-platform: OHCI generic platform driver
[    1.231771] uhci_hcd: USB Universal Host Controller Interface driver
[    1.231833] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.251356] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.251362] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.251658] mousedev: PS/2 mouse device common for all mice
[    1.252006] rtc_cmos 00:01: RTC can wake from S4
[    1.252144] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.252177] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.252189] i2c /dev entries driver
[    1.252277] device-mapper: uevent: version 1.0.3
[    1.252363] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    1.252378] Intel P-state driver initializing.
[    1.252522] ledtrig-cpu: registered to indicate activity on CPUs
[    1.252533] EFI Variables Facility v0.08 2004-May-17
[    1.268523] PCCT header not found.
[    1.268718] NET: Registered protocol family 10
[    1.268896] NET: Registered protocol family 17
[    1.268906] Key type dns_resolver registered
[    1.269323] Loading compiled-in X.509 certificates
[    1.270040] Loaded X.509 cert 'Build time autogenerated kernel key: 736e2f9ea1b4728a15ac169b1869267e1128d6e8'
[    1.270056] registered taskstats version 1
[    1.270074] zswap: loading zswap
[    1.270076] zswap: using zbud pool
[    1.270079] zswap: using lzo compressor
[    1.274102] Key type trusted registered
[    1.277411] Key type encrypted registered
[    1.277418] AppArmor: AppArmor sha1 policy hashing enabled
[    1.277421] ima: No TPM chip found, activating TPM-bypass!
[    1.277442] evm: HMAC attrs: 0x1
[    1.277832]   Magic number: 8:137:458
[    1.277940] rtc_cmos 00:01: setting system clock to 2016-03-15 01:28:21 UTC (1458005301)
[    1.277993] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.277994] EDD information not available.
[    1.278082] PM: Hibernation image not present or could not be loaded.
[    1.278346] Freeing unused kernel memory: 1468K (ffffffff81d38000 - ffffffff81ea7000)
[    1.278347] Write protecting the kernel read-only data: 12288k
[    1.278532] Freeing unused kernel memory: 240K (ffff8800027c4000 - ffff880002800000)
[    1.278605] Freeing unused kernel memory: 280K (ffff880002bba000 - ffff880002c00000)
[    1.281815] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.288594] systemd-udevd[118]: starting version 204
[    1.310350] sdhci: Secure Digital Host Controller Interface driver
[    1.310352] sdhci: Copyright(c) Pierre Ossman
[    1.311115] rtsx_pci 0000:09:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 28
[    1.311559] sdhci-pci 0000:09:00.1: SDHCI controller found [10ec:5209] (rev 1)
[    1.311635] sdhci-pci 0000:09:00.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.311643] sdhci-pci 0000:09:00.1: No vmmc regulator found
[    1.311644] sdhci-pci 0000:09:00.1: No vqmmc regulator found
[    1.311651] sdhci-pci 0000:09:00.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.311758] sdhci-pci 0000:09:00.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.312315] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.312324] r8169 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.312777] mmc0: SDHCI controller on PCI [0000:09:00.1] using DMA
[    1.312871] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000ea2000, d4:be:d9:3e:05:47, XID 0c900880 IRQ 29
[    1.312873] r8169 0000:07:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.316515] ahci 0000:00:1f.2: version 3.0
[    1.316665] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.316691] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3 impl RAID mode
[    1.316695] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst 
[    1.324019] scsi host0: ahci
[    1.324119] scsi host1: ahci
[    1.324224] scsi host2: ahci
[    1.324310] scsi host3: ahci
[    1.324401] scsi host4: ahci
[    1.324487] scsi host5: ahci
[    1.324527] ata1: SATA max UDMA/133 abar m2048@0xd1717000 port 0xd1717100 irq 30
[    1.324530] ata2: SATA max UDMA/133 abar m2048@0xd1717000 port 0xd1717180 irq 30
[    1.324531] ata3: DUMMY
[    1.324532] ata4: DUMMY
[    1.324532] ata5: DUMMY
[    1.324533] ata6: DUMMY
[    1.527667] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.543670] usb 4-1: new high-speed USB device number 2 using ehci-pci
[    1.643799] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.644771] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.645120] ata1.00: ATA-8: Hitachi HTS545050A7E380, GG2OA7A0, max UDMA/133
[    1.645129] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.646197] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.646487] ata1.00: configured for UDMA/133
[    1.646656] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54505 A7A0 PQ: 0 ANSI: 5
[    1.646921] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.646923] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.646939] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.647006] sd 0:0:0:0: [sda] Write Protect is off
[    1.647010] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.647040] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.660132] usb 3-1: New USB device found, idVendor=8087, idProduct=0024
[    1.660140] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.660400] hub 3-1:1.0: USB hub found
[    1.660485] hub 3-1:1.0: 6 ports detected
[    1.676200] usb 4-1: New USB device found, idVendor=8087, idProduct=0024
[    1.676202] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.676542] hub 4-1:1.0: USB hub found
[    1.676693] hub 4-1:1.0: 8 ports detected
[    1.710514] GPT:Primary header thinks Alt. header is not at the end of the disk.
[    1.710517] GPT:976769057 != 976773167
[    1.710517] GPT:Alternate GPT header not at the end of the disk.
[    1.710518] GPT:976769057 != 976773167
[    1.710519] GPT: Use GNU Parted to correct GPT errors.
[    1.710529]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
[    1.711318] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.931968] usb 3-1.5: new high-speed USB device number 3 using ehci-pci
[    1.948014] usb 4-1.5: new full-speed USB device number 3 using ehci-pci
[    1.952032] tsc: Refined TSC clocksource calibration: 2394.561 MHz
[    1.952035] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x22842564e28, max_idle_ns: 440795246705 ns
[    1.964043] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.964710] ata2.00: ATA-8: SAMSUNG SSD PM830 mSATA 32GB, CXM12D1Q, max UDMA/133
[    1.964712] ata2.00: 62533296 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.965085] ata2.00: configured for UDMA/133
[    1.965220] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SSD PM83 2D1Q PQ: 0 ANSI: 5
[    1.965397] sd 1:0:0:0: [sdb] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    1.965419] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.965494] sd 1:0:0:0: [sdb] Write Protect is off
[    1.965498] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.965534] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.966434] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.044995] usb 4-1.5: New USB device found, idVendor=8087, idProduct=07da
[    2.045004] usb 4-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.317558] usb 3-1.5: New USB device found, idVendor=1bcf, idProduct=2899
[    2.317561] usb 3-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.317562] usb 3-1.5: Product: Laptop_Integrated_Webcam_1.3M
[    2.317564] usb 3-1.5: Manufacturer: CN01RH717248726BF6WGA00
[    2.498718] psmouse serio1: synaptics: queried max coordinates: x [..5678], y [..4680]
[    2.558731] psmouse serio1: synaptics: queried min coordinates: x [1264..], y [1174..]
[    2.681320] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x126c00/0x0, board id: 2080, fw id: 1114765
[    2.751529] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    2.952987] clocksource: Switched to clocksource tsc
[    3.193408] random: nonblocking pool is initialized
[    3.574539] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   10.412169] Adding 11718652k swap on /dev/sda8.  Priority:-1 extents:1 across:11718652k FS
[   10.547267] systemd-udevd[397]: starting version 204
[   10.708502] lp: driver loaded but no devices found
[   10.712459] ppdev: user-space parallel port driver
[   10.765110] wmi: Mapper loaded
[   10.765903] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.775305] [drm] Initialized drm 1.1.0 20060810
[   10.794663] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20150619/utaddress-254)
[   10.794670] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.794675] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB_.PCI0.PEG0.PEGP.GPIO) (20150619/utaddress-254)
[   10.794679] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   10.794683] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.794685] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB_.PCI0.PEG0.PEGP.GPIO) (20150619/utaddress-254)
[   10.794689] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   10.794693] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.794694] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB_.PCI0.PEG0.PEGP.GPIO) (20150619/utaddress-254)
[   10.794698] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   10.794702] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.794704] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   10.798892] Intel(R) Wireless WiFi driver for Linux
[   10.798895] Copyright(c) 2003- 2015 Intel Corporation
[   10.799085] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[   10.803924] [drm] Memory usable by graphics device = 2048M
[   10.803929] checking generic (c0000000 580000) vs hw (c0000000 10000000)
[   10.803931] fb: switching to inteldrmfb from EFI VGA
[   10.803978] Console: switching to colour dummy device 80x25
[   10.804060] [drm] Replacing VGA console driver
[   10.811608] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   10.811611] [drm] Driver supports precise vblank timestamp query.
[   10.811728] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.823667] Bluetooth: Core ver 2.20
[   10.823702] NET: Registered protocol family 31
[   10.823704] Bluetooth: HCI device and connection manager initialized
[   10.823708] Bluetooth: HCI socket layer initialized
[   10.823711] Bluetooth: L2CAP socket layer initialized
[   10.823717] Bluetooth: SCO socket layer initialized
[   10.826063] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   10.826082] ACPI: \_SB_.PCI0.GFX0: failed to evaluate _DSM
[   10.826114] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   10.826169] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   10.826327] pci 0000:01:00.0: optimus capabilities: enabled, status dynamic power, 
[   10.826329] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG0.PEGP handle
[   10.826368] nouveau 0000:01:00.0: enabling device (0006 -> 0007)
[   10.832002] usbcore: registered new interface driver btusb
[   10.848203] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   10.849956] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   10.850225] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   10.850401] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   10.850464] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:38/LNXVIDEO:00/input/input6
[   10.852055] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.852168] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   10.852232] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[   10.852386] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x0d7000a2
[   10.852388] nouveau  [  DEVICE][0000:01:00.0] Chipset: GF117 (NVD7)
[   10.852389] nouveau  [  DEVICE][0000:01:00.0] Family : NVC0
[   10.854776] audit: type=1400 audit(1458014311.063:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=450 comm="apparmor_parser"
[   10.854785] audit: type=1400 audit(1458014311.063:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=450 comm="apparmor_parser"
[   10.854791] audit: type=1400 audit(1458014311.063:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=450 comm="apparmor_parser"
[   10.854869] device-mapper: multipath: version 1.9.0 loaded
[   10.855238] audit: type=1400 audit(1458014311.063:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=450 comm="apparmor_parser"
[   10.855243] audit: type=1400 audit(1458014311.063:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=450 comm="apparmor_parser"
[   10.855467] audit: type=1400 audit(1458014311.063:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=450 comm="apparmor_parser"
[   10.865179] AVX version of gcm_enc/dec engaged.
[   10.865182] AES CTR mode by8 optimization enabled
[   10.915607] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[   10.934526] fbcon: inteldrmfb (fb0) is primary device
[   10.934609] Console: switching to colour frame buffer device 200x56
[   10.934637] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.934639] i915 0000:00:02.0: registered panic notifier
[   10.936329] nouveau  [   VBIOS][0000:01:00.0] using image from ACPI
[   10.936434] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[   10.936438] nouveau  [   VBIOS][0000:01:00.0] version 75.17.46.00.05
[   10.936718] nouveau  [   VBIOS][0000:01:00.0] running init tables
[   11.025173] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
[   11.025224] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR5
[   11.025227] nouveau  [     PFB][0000:01:00.0] RAM size: 1024 MiB
[   11.025229] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
[   11.043925] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.046774] intel_rapl: Found RAPL domain package
[   11.046778] intel_rapl: Found RAPL domain core
[   11.046780] intel_rapl: Found RAPL domain uncore
[   11.048560] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   11.070851] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[   11.070872] nouveau  [  PTHERM][0000:01:00.0] internal sensor: no
[   11.070930] nouveau  [     CLK][0000:01:00.0] 07: core 270 MHz memory 405 MHz 
[   11.070939] nouveau  [     CLK][0000:01:00.0] 0a: core 625 MHz memory 800 MHz 
[   11.070947] nouveau  [     CLK][0000:01:00.0] 0f: core 625 MHz memory 2000 MHz 
[   11.071103] nouveau  [     CLK][0000:01:00.0] --: core 270 MHz memory 135 MHz 
[   11.076982] vga_switcheroo: enabled
[   11.077080] [TTM] Zone  kernel: Available graphics memory: 4025248 kiB
[   11.077083] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   11.077084] [TTM] Initializing pool allocator
[   11.077092] [TTM] Initializing DMA pool allocator
[   11.077106] nouveau  [     DRM] VRAM: 1024 MiB
[   11.077108] nouveau  [     DRM] GART: 1048576 MiB
[   11.077112] nouveau W[     DRM] Pointer to TMDS table invalid
[   11.077114] nouveau  [     DRM] DCB version 4.0
[   11.077116] nouveau W[     DRM] Pointer to flat panel table invalid
[   11.078972] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC3260: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   11.078976] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   11.078979] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   11.078981] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   11.078983] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   11.078986] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[   11.078988] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[   11.095683] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   11.095808] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   11.096190] nouveau  [     DRM] MM: using COPY0 for buffer copies
[   11.096198] [drm] Initialized nouveau 1.2.2 20120801 for 0000:01:00.0 on minor 1
[   11.096481] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.096858] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   11.152060] cfg80211: World regulatory domain updated:
[   11.152063] cfg80211:  DFS Master region: unset
[   11.152065] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   11.152067] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   11.152068] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   11.152069] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   11.152070] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   11.152072] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   11.174316] iwlwifi 0000:08:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   11.187904] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   11.187907] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   11.187909] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   11.187912] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
[   11.188016] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[   11.206959] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.325067] media: Linux media interface: v0.10
[   11.328714] Linux video capture interface: v2.00
[   11.335117] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (1bcf:2899)
[   11.416298] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.5/3-1.5:1.0/input/input13
[   11.416520] usbcore: registered new interface driver uvcvideo
[   11.416523] USB Video Class driver (1.1.1)
[   15.020880] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   15.496821] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   16.100126] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   16.100189] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[   16.100193] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   16.461730] init: failsafe main process (832) killed by TERM signal
[   16.745134] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.745138] Bluetooth: BNEP filters: protocol multicast
[   16.745143] Bluetooth: BNEP socket layer initialized
[   16.750394] Bluetooth: RFCOMM TTY layer initialized
[   16.750400] Bluetooth: RFCOMM socket layer initialized
[   16.750405] Bluetooth: RFCOMM ver 1.11
[   16.876033] audit: type=1400 audit(1458014317.079:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=986 comm="apparmor_parser"
[   16.876039] audit: type=1400 audit(1458014317.079:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=986 comm="apparmor_parser"
[   16.876346] audit: type=1400 audit(1458014317.079:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=986 comm="apparmor_parser"
[   16.882235] audit: type=1400 audit(1458014317.087:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=997 comm="apparmor_parser"
[   16.882247] audit: type=1400 audit(1458014317.087:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=997 comm="apparmor_parser"
[   16.882253] audit: type=1400 audit(1458014317.087:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=997 comm="apparmor_parser"
[   16.882724] audit: type=1400 audit(1458014317.087:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=997 comm="apparmor_parser"
[   16.882731] audit: type=1400 audit(1458014317.087:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=997 comm="apparmor_parser"
[   16.882974] audit: type=1400 audit(1458014317.087:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=997 comm="apparmor_parser"
[   16.883191] audit: type=1400 audit(1458014317.087:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=996 comm="apparmor_parser"
[   17.179806] init: cups main process (987) killed by HUP signal
[   17.179816] init: cups main process ended, respawning
[   18.692355] r8169 0000:07:00.0 eth0: link down
[   18.692403] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.694173] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[   18.701015] iwlwifi 0000:08:00.0: Radio type=0x2-0x1-0x0
[   18.984952] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[   18.991803] iwlwifi 0000:08:00.0: Radio type=0x2-0x1-0x0
[   19.074340] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.794829] init: plymouth-upstart-bridge main process ended, respawning
[   20.799586] init: plymouth-upstart-bridge main process (1311) terminated with status 1
[   20.799602] init: plymouth-upstart-bridge main process ended, respawning
[   22.224594] wlan0: authenticate with 44:e9:dd:4c:bf:22
[   22.228086] wlan0: send auth to 44:e9:dd:4c:bf:22 (try 1/3)
[   22.238775] wlan0: authenticated
[   22.241273] wlan0: associate with 44:e9:dd:4c:bf:22 (try 1/3)
[   22.249540] wlan0: RX AssocResp from 44:e9:dd:4c:bf:22 (capab=0x431 status=0 aid=4)
[   22.277364] wlan0: associated
[   22.277405] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.279288] cfg80211: Regulatory domain changed to country: CA
[   22.279292] cfg80211:  DFS Master region: unset
[   22.279293] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   22.279295] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm), (N/A)
[   22.279296] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm), (N/A)
[   22.279297] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   22.279299] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   22.279300] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm), (N/A)
[   25.876337] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   25.876400] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[   25.876404] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   46.998254] audit_printk_skb: 132 callbacks suppressed
[   46.998257] audit: type=1400 audit(1458014347.172:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2325 comm="apparmor_parser"
[   46.998263] audit: type=1400 audit(1458014347.172:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2325 comm="apparmor_parser"
[   46.998593] audit: type=1400 audit(1458014347.172:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2325 comm="apparmor_parser"
[   66.129946] systemd-hostnamed[2394]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  128.717451] systemd-timedated[2480]: /etc/localtime should be a symbolic link to a timezone data file in /usr/share/zoneinfo/.
[  152.335416] systemd-timedated[2480]: Changed timezone to 'America/Montreal'.
[  619.157962] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[  619.180114] JFS: nTxBlock = 8192, nTxLock = 65536
[  619.201665] ntfs: driver 2.1.32 [Flags: R/O MODULE].
[  619.228852] QNX4 filesystem 0.2.3 registered.
[  619.322308] raid6: sse2x1   gen()  7693 MB/s
[  619.390399] raid6: sse2x1   xor()  6538 MB/s
[  619.458494] raid6: sse2x2   gen() 10157 MB/s
[  619.526582] raid6: sse2x2   xor()  7230 MB/s
[  619.594676] raid6: sse2x4   gen() 11769 MB/s
[  619.662767] raid6: sse2x4   xor()  8480 MB/s
[  619.662769] raid6: using algorithm sse2x4 gen() 11769 MB/s
[  619.662770] raid6: .... xor() 8480 MB/s, rmw enabled
[  619.662771] raid6: using ssse3x2 recovery algorithm
[  619.666533] xor: automatically using best checksumming function:
[  619.702820]    avx       : 22116.000 MB/sec
[  619.785878] Btrfs loaded
```

Thanks a lot!

---

### Post by ajgreeny on 2016-03-15
```
66.129946] systemd-hostnamed[2394]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  128.717451] systemd-timedated[2480]: /etc/localtime should be a symbolic link to a timezone data file in /usr/share/zoneinfo/.
```
This seems to be the point where the longest delay occurs;  have you tried installing **nss-myhostname** as is suggested? It looks as if in Ubuntu the package is **libnss-myhostname**, so try that.

---

### Post by oldfred on 2016-03-15
The issues that need review are all the one's with large time differences.

What version of Ubuntu?
And I see USB video as if you have camera, but also RAID and loading multiple drivers for various formats, as if a server. How is system configured?

---

### Post by jeremy31 on 2016-03-15
Could it be that Windows is using a hybrid shutdown is causing issues?

---

### Post by Simon_Thriault on 2016-03-15
[@ajgreeny:]("http://ubuntuforums.org/member.php?u=27747") I installed libnss-myhostname and there seems to be no major improvement.

[@oldfred: ]("http://ubuntuforums.org/member.php?u=852711")I'm using Ubuntu 14.04 LTS and I installed Ubuntu on the same disk as Windows, it is not used as a server.

[@jeremy31:]("http://ubuntuforums.org/member.php?u=1924242")[COLOR=#000000] What do you mean by hybrid shutdown?[/COLOR]

---

### Post by oldfred on 2016-03-15
Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

What brand/model system?

Post this, from live installer's terminal or if you can boot from Ubuntu.

sudo parted -l

---

