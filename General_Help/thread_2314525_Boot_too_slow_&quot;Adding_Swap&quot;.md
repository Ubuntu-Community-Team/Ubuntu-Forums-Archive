---
title: "Boot too slow &quot;Adding Swap&quot;"
date: 2016-02-21
forum: General Help
---

### Post by Rod_C on 2016-02-21
hi every one, 
i have ubuntu 14.04 on my dell vostro 5740 laptop, with an i3 processor and the booting time is almost 1 minute. 
the adding swap step is taking too long:

**[   20.121651] Adding 8198140k swap on /dev/sda5.  Priority:-1 extents:1 across:8198140k FS**

some ideas to decrease the adding swap time????

here are all dmesg messages:[    0.598067] hw unit of domain dram 2^-14 Joules
```
[    0.598068] hw unit of domain pp1-gpu 2^-14 Joules
[    0.598198] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x17
[    0.598205] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x17
[    0.598215] microcode: CPU2 sig=0x40651, pf=0x40, revision=0x17
[    0.598223] microcode: CPU3 sig=0x40651, pf=0x40, revision=0x17
[    0.598274] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.598320] Scanning for low memory corruption every 60 seconds
[    0.598724] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.598770] audit: initializing netlink subsys (disabled)
[    0.598787] audit: type=2000 audit(1456104323.592:1): initialized
[    0.599175] Initialise system trusted keyring
[    0.599261] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.599263] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.600878] zbud: loaded
[    0.601110] VFS: Disk quotas dquot_6.6.0
[    0.601146] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.601621] fuse init (API version 7.23)
[    0.601761] Key type big_key registered
[    0.602121] Key type asymmetric registered
[    0.602125] Asymmetric key parser 'x509' registered
[    0.602144] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.602181] io scheduler noop registered
[    0.602186] io scheduler deadline registered (default)
[    0.602227] io scheduler cfq registered
[    0.602801] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.602807] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.602838] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    0.602839] vesafb: scrolling: redraw
[    0.602841] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.602852] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90000800000, using 4160k, total 4160k
[    0.712476] Console: switching to colour frame buffer device 170x48
[    0.821716] fb0: VESA VGA frame buffer device
[    0.821737] intel_idle: MWAIT substates: 0x11142120
[    0.821739] intel_idle: v0.4 model 0x45
[    0.821740] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.922438] ACPI: AC Adapter [ADP0] (off-line)
[    0.922529] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.922534] ACPI: Power Button [PWRB]
[    0.922571] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.922574] ACPI: Sleep Button [SLPB]
[    0.922613] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.923002] ACPI: Lid Switch [LID0]
[    0.923057] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.923060] ACPI: Power Button [PWRF]
[    0.923705] thermal LNXTHERM:00: registered as thermal_zone0
[    0.923708] ACPI: Thermal Zone [TZ00] (28 C)
[    0.923900] thermal LNXTHERM:01: registered as thermal_zone1
[    0.923901] ACPI: Thermal Zone [TZ01] (30 C)
[    0.923937] GHES: HEST is not enabled!
[    0.924109] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.927308] Linux agpgart interface v0.103
[    0.929071] ACPI: Battery Slot [BAT0] (battery present)
[    0.930186] brd: module loaded
[    0.931411] loop: module loaded
[    0.931694] libphy: Fixed MDIO Bus: probed
[    0.931699] tun: Universal TUN/TAP device driver, 1.6
[    0.931700] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.931740] PPP generic driver version 2.4.2
[    0.931883] xhci_hcd 0000:00:14.0: can't derive routing for PCI INT A
[    0.931885] xhci_hcd 0000:00:14.0: PCI INT A: no GSI
[    0.931909] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.931916] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.931989] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x0004b810
[    0.931994] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.932083] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.932085] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.932087] usb usb1: Product: xHCI Host Controller
[    0.932089] usb usb1: Manufacturer: Linux 4.3.0-040300-generic xhci-hcd
[    0.932090] usb usb1: SerialNumber: 0000:00:14.0
[    0.932197] hub 1-0:1.0: USB hub found
[    0.932207] hub 1-0:1.0: 9 ports detected
[    0.934181] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.934185] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.934214] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.934216] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.934218] usb usb2: Product: xHCI Host Controller
[    0.934219] usb usb2: Manufacturer: Linux 4.3.0-040300-generic xhci-hcd
[    0.934221] usb usb2: SerialNumber: 0000:00:14.0
[    0.934347] hub 2-0:1.0: USB hub found
[    0.934356] hub 2-0:1.0: 4 ports detected
[    0.935155] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.935162] ehci-pci: EHCI PCI platform driver
[    0.935264] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.935269] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    0.935280] ehci-pci 0000:00:1d.0: debug port 2
[    0.939166] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.939182] ehci-pci 0000:00:1d.0: irq 23, io mem 0xd161d000
[    0.950317] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.950355] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.950357] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.950359] usb usb3: Product: EHCI Host Controller
[    0.950361] usb usb3: Manufacturer: Linux 4.3.0-040300-generic ehci_hcd
[    0.950362] usb usb3: SerialNumber: 0000:00:1d.0
[    0.950579] hub 3-0:1.0: USB hub found
[    0.950586] hub 3-0:1.0: 2 ports detected
[    0.950722] ehci-platform: EHCI generic platform driver
[    0.950735] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.950742] ohci-pci: OHCI PCI platform driver
[    0.950755] ohci-platform: OHCI generic platform driver
[    0.950765] uhci_hcd: USB Universal Host Controller Interface driver
[    0.950827] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.953840] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.953844] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.954019] mousedev: PS/2 mouse device common for all mice
[    0.954219] rtc_cmos 00:01: RTC can wake from S4
[    0.954370] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.954400] rtc_cmos 00:01: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.954411] i2c /dev entries driver
[    0.954475] device-mapper: uevent: version 1.0.3
[    0.954543] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.954567] Intel P-state driver initializing.
[    0.954703] ledtrig-cpu: registered to indicate activity on CPUs
[    0.955456] NET: Registered protocol family 10
[    0.955963] NET: Registered protocol family 17
[    0.956003] Key type dns_resolver registered
[    0.956794] registered taskstats version 1
[    0.956844] Loading compiled-in X.509 certificates
[    0.959135] Loaded X.509 cert 'Build time autogenerated kernel key: 57d62c37587c99cd510d22fbde8cf1ac069cb6f6'
[    0.959185] zswap: loaded using pool lzo/zbud
[    0.962349] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.962914] Key type trusted registered
[    0.965900] Key type encrypted registered
[    0.965908] AppArmor: AppArmor sha1 policy hashing enabled
[    0.965912] ima: No TPM chip found, activating TPM-bypass!
[    0.965939] evm: HMAC attrs: 0x1
[    0.966402]   Magic number: 4:106:408
[    0.966504] rtc_cmos 00:01: setting system clock to 2016-02-22 01:25:24 UTC (1456104324)
[    0.966556] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.966557] EDD information not available.
[    0.966641] PM: Hibernation image not present or could not be loaded.
[    0.966954] Freeing unused kernel memory: 1448K (ffffffff81d3a000 - ffffffff81ea4000)
[    0.966955] Write protecting the kernel read-only data: 12288k
[    0.967310] Freeing unused kernel memory: 276K (ffff8800017bb000 - ffff880001800000)
[    0.967384] Freeing unused kernel memory: 196K (ffff880001bcf000 - ffff880001c00000)
[    0.977887] systemd-udevd[131]: starting version 204
[    1.192752] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.203879] rtsx_pci 0000:02:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 43
[    1.206713] ahci 0000:00:1f.2: version 3.0
[    1.222223] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x2 impl SATA mode
[    1.222230] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
[    1.223029] scsi host0: ahci
[    1.223179] scsi host1: ahci
[    1.223382] scsi host2: ahci
[    1.223689] scsi host3: ahci
[    1.223775] ata1: DUMMY
[    1.223779] ata2: SATA max UDMA/133 abar m2048@0xd161c000 port 0xd161c180 irq 44
[    1.223781] ata3: DUMMY
[    1.223783] ata4: DUMMY
[    1.242263] usb 1-4: new full-speed USB device number 2 using xhci_hcd
[    1.262243] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.371533] usb 1-4: New USB device found, idVendor=138a, idProduct=0011
[    1.371537] usb 1-4: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    1.371539] usb 1-4: SerialNumber: 3fce16ea329c
[    1.394642] usb 3-1: New USB device found, idVendor=8087, idProduct=8000
[    1.394646] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.395049] hub 3-1:1.0: USB hub found
[    1.395251] hub 3-1:1.0: 8 ports detected
[    1.538138] usb 1-5: new high-speed USB device number 3 using xhci_hcd
[    1.542144] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.542911] ata2.00: ATA-9: WDC WD5000LPVX-75V0TT0, 01.01A01, max UDMA/133
[    1.542916] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.543723] ata2.00: configured for UDMA/133
[    1.543948] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000LPVX-7 1A01 PQ: 0 ANSI: 5
[    1.544216] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.544220] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.544239] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.544297] sd 1:0:0:0: [sda] Write Protect is off
[    1.544300] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.544327] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.594119] tsc: Refined TSC clocksource calibration: 1895.612 MHz
[    1.594125] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x36a5f58a5e2, max_idle_ns: 881590593810 ns
[    1.616174]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    1.616650] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.779703] usb 1-5: New USB device found, idVendor=1bcf, idProduct=28b4
[    1.779707] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.779709] usb 1-5: Product: Integrated_Webcam_HD
[    1.779710] usb 1-5: Manufacturer: CN0XFM7M724874C50427A01
[    1.805248] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x361f05)
[    1.820367] psmouse serio1: elantech: Synaptics capabilities query result 0x00, 0x15, 0x0e.
[    1.836138] psmouse serio1: elantech: Elan sample query result 0b, 42, 64
[    1.913424] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input6
[    1.961973] usb 1-7: new full-speed USB device number 4 using xhci_hcd
[    2.091333] usb 1-7: New USB device found, idVendor=8087, idProduct=07dc
[    2.091337] usb 1-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.593926] clocksource: Switched to clocksource tsc
[    7.098969] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    7.886674] random: nonblocking pool is initialized
[   20.121651] Adding 8198140k swap on /dev/sda5.  Priority:-1 extents:1 across:8198140k FS
[   20.448081] systemd-udevd[328]: starting version 204
[   20.992277] wmi: Mapper loaded
[   21.019100] input: DELL Wireless hotkeys as /devices/virtual/input/input7
[   21.071234] lp: driver loaded but no devices found
[   21.104030] ppdev: user-space parallel port driver
[   21.384609] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.537439] [drm] Initialized drm 1.1.0 20060810
[   21.707276] AVX2 version of gcm_enc/dec engaged.
[   21.707280] AES CTR mode by8 optimization enabled
[   21.776342] Intel(R) Wireless WiFi driver for Linux
[   21.776346] Copyright(c) 2003- 2015 Intel Corporation
[   21.776381] Bluetooth: Core ver 2.20
[   21.776402] NET: Registered protocol family 31
[   21.776404] Bluetooth: HCI device and connection manager initialized
[   21.776410] Bluetooth: HCI socket layer initialized
[   21.776414] Bluetooth: L2CAP socket layer initialized
[   21.776421] Bluetooth: SCO socket layer initialized
[   22.017317] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-7260-17.ucode failed with error -2
[   22.040000] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-7260-16.ucode failed with error -2
[   22.063700] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2
[   22.063715] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-7260-14.ucode failed with error -2
[   22.120141] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   22.129160] usbcore: registered new interface driver btusb
[   22.142397] Bluetooth: hci0: read Intel version: 3707100180012d0d00
[   22.198435] [drm] Memory usable by graphics device = 2048M
[   22.198442] checking generic (c0000000 410000) vs hw (c0000000 10000000)
[   22.198444] fb: switching to inteldrmfb from VESA VGA
[   22.198517] Console: switching to colour dummy device 80x25
[   22.198695] [drm] Replacing VGA console driver
[   22.206009] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   22.206011] [drm] Driver supports precise vblank timestamp query.
[   22.206105] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   22.242446] fbcon: inteldrmfb (fb0) is primary device
[   22.244002] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   22.244279] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   22.244375] [drm] Initialized i915 1.6.0 20150731 for 0000:00:02.0 on minor 0
[   22.264942] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   22.283466] audit: type=1400 audit(1456104345.820:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=533 comm="apparmor_parser"
[   22.283470] audit: type=1400 audit(1456104345.820:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=533 comm="apparmor_parser"
[   22.283472] audit: type=1400 audit(1456104345.820:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=533 comm="apparmor_parser"
[   22.283835] audit: type=1400 audit(1456104345.820:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=533 comm="apparmor_parser"
[   22.283838] audit: type=1400 audit(1456104345.820:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=533 comm="apparmor_parser"
[   22.284014] audit: type=1400 audit(1456104345.820:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=533 comm="apparmor_parser"
[   22.375085] media: Linux media interface: v0.10
[   22.378027] intel_rapl: Found RAPL domain package
[   22.378031] intel_rapl: Found RAPL domain core
[   22.378034] intel_rapl: Found RAPL domain uncore
[   22.378038] intel_rapl: Found RAPL domain dram
[   22.384747] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.1.2d.d.bseq
[   22.429703] cfg80211: World regulatory domain updated:
[   22.429705] cfg80211:  DFS Master region: unset
[   22.429705] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   22.429707] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   22.429708] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   22.429709] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   22.429710] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   22.429711] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   22.458268] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   22.613039] iwlwifi 0000:08:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[   22.851125] Linux video capture interface: v2.00
[   22.924684] iwlwifi 0000:08:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[   22.924752] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[   22.924991] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[   23.089446] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC290: line_outs=2 (0x14/0x17/0x0/0x0/0x0) type:speaker
[   23.089447] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   23.089449] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   23.089450] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[   23.089450] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[   23.089452] snd_hda_codec_realtek hdaudioC1D0:      Headset Mic=0x1a
[   23.089453] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x19
[   23.097470] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[   23.110934] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.155894] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   23.254420] uvcvideo: Found UVC 1.00 device Integrated_Webcam_HD (1bcf:28b4)
[   23.263213] input: Integrated_Webcam_HD as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input11
[   23.263334] usbcore: registered new interface driver uvcvideo
[   23.263335] USB Video Class driver (1.1.1)
[   23.282030] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   23.353147] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   23.353166] Console: switching to colour frame buffer device 170x48
[   23.356930] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   23.412488] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input12
[   23.412581] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input13
[   23.412663] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[   23.510983] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   25.208139] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   25.803511] init: failsafe main process (795) killed by TERM signal
[   26.199343] audit: type=1400 audit(1456104349.736:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=867 comm="apparmor_parser"
[   26.199349] audit: type=1400 audit(1456104349.736:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=867 comm="apparmor_parser"
[   26.199721] audit: type=1400 audit(1456104349.736:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=867 comm="apparmor_parser"
[   26.431628] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.431632] Bluetooth: BNEP filters: protocol multicast
[   26.431637] Bluetooth: BNEP socket layer initialized
[   26.515615] audit: type=1400 audit(1456104350.052:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session" pid=914 comm="apparmor_parser"
[   26.592667] Bluetooth: RFCOMM TTY layer initialized
[   26.592676] Bluetooth: RFCOMM socket layer initialized
[   26.592682] Bluetooth: RFCOMM ver 1.11
[   27.015423] init: cups main process (868) killed by HUP signal
[   27.015433] init: cups main process ended, respawning
[   27.335894] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[   27.336132] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[   27.447493] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
[   27.523365] audit_printk_skb: 153 callbacks suppressed
[   27.523369] audit: type=1400 audit(1456104351.060:63): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cups-browsed" pid=1125 comm="apparmor_parser"
[   27.534816] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[   27.535056] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[   27.555703] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.623686] audit: type=1400 audit(1456104351.160:64): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1259 comm="apparmor_parser"
[   28.447647] wlan0: authenticate with 30:91:8f:ea:91:f9
[   28.450770] wlan0: send auth to 30:91:8f:ea:91:f9 (try 1/3)
[   28.649252] wlan0: send auth to 30:91:8f:ea:91:f9 (try 2/3)
[   28.651073] wlan0: authenticated
[   28.652336] wlan0: associate with 30:91:8f:ea:91:f9 (try 1/3)
[   28.656074] wlan0: RX AssocResp from 30:91:8f:ea:91:f9 (capab=0x411 status=0 aid=4)
[   28.658876] wlan0: associated
[   28.658898] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.725245] init: samba-ad-dc main process (1316) terminated with status 1
[   33.865710] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   34.154730] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[   34.160077] vboxdrv: Found 4 processor cores.
[   34.160788] vboxdrv: fAsync=0 offMin=0xf0 offMax=0x10a8
[   34.161448] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   34.161452] vboxdrv: Successfully loaded version 4.3.36_Ubuntu (interface 0x001a000b).
[   34.308542] vboxpci: IOMMU not found (not registered)
[   56.272679] audit: type=1400 audit(1456104379.831:65): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=2325 comm="apparmor_parser"
[   56.272685] audit: type=1400 audit(1456104379.831:66): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=2325 comm="apparmor_parser"
[   56.273059] audit: type=1400 audit(1456104379.831:67): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=2325 comm="apparmor_parser"
```

---

### Post by Bucky Ball on 2016-02-21
Welcome. Please use code tags for terminal output. I have added them to your previous post. Instructions in my signature.

Please open your fstab file with:

```
nano /etc/fstab
```

Post the contents here (code tags, please). 

Then run this:

```
sudo blkid
```

Post that here, please.

---

### Post by Rod_C on 2016-02-22
Thanks Bucky Ball, I can't edit your post.
this is the content of the fstab file

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=5893d1be-b3a8-44a0-ab79-0310fa7e7d60 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f3a45f02-8cf6-4fe1-b6d1-648374a5cd8c none            swap    sw              0       0

```

And the result for blkid command.
```

/dev/sda1: LABEL="DELLUTILITY" UUID="8221-6BF5" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="5450-4444" TYPE="vfat" 
/dev/sda3: UUID="5893d1be-b3a8-44a0-ab79-0310fa7e7d60" TYPE="ext4" 
/dev/sda5: UUID="f3a45f02-8cf6-4fe1-b6d1-648374a5cd8c" TYPE="swap" 

```

---

### Post by QIII on 2016-02-22
By "post that here", he meant "in the thread".

No, you can't edit the posts of other users.  :)

---

### Post by Bucky Ball on 2016-02-23
As QIII said. :)

Hmm. That looks fine. Maybe something to do with encryption, as suggested. Launch Gparted (you can install from repos if not installed already). On sda there should be the /dev/sda5 /swap partition. Right click on it. Does it say swapon or swapoff? If 'off', switch to on and reboot. 

Odd.

---

### Post by Rod_C on 2016-02-23
Bucky, I launched Gparted and the swap partition was already 'ON'. :(

---

### Post by Rod_C on 2016-02-23
I think the Bootchart analisys can be usefull.
The boot gets slow after the 7 sec, When UREADAHEAD process starts running, after that swapon starts.

---

