---
title: "[ubuntu] 14.04 not recognizing e-reader from usb"
date: 2014-05-15
forum: General Help
---

### Post by dobriensd on 2014-05-15
I am new here, and on an Ubuntu rig that I installed from an Acer C720 Chromebook, and my mouse is on one of the usb ports and I tried to stick a usb flash drive in another one and it recognized it but when I place my e-reader in either one it registers neither in Ubuntu or in Calibre for that matter.  I can't access it either way.  My e-reader is a nook HD.  Not sure if anyone has seen this before but thought I would throw it out there, because I can't install new books from my machine any longer this way.  It's very frustrating.

---

### Post by pretty_whistle on 2014-05-15
I had a similar issue with connecting my phone.  Connecting it to the usb port closest to the back of the computer solved it (I dont know why).

Hope this helps.

---

### Post by dobriensd on 2014-05-16
> **pretty_whistle said:**
> I had a similar issue with connecting my phone.  Connecting it to the usb port closest to the back of the computer solved it (I dont know why).

Hope this helps.

No unfortunately Ubuntu does not recognize the nook when plugged in at all.  Has anyone else seen this problem?  And if so, where can I get drivers?

---

### Post by Luke M on 2014-05-16
After connecting the device, open a terminal and type "dmesg". There should be some USB related messages at the end (new device found etc), maybe that will give a clue.

---

### Post by dobriensd on 2014-05-17
I don't know what it means but perhaps it does give a clue:

[    0.126342] pci 0000:00:1c.0:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.126582] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11, disabled.
[    0.126650] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10, disabled.
[    0.126710] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11, disabled.
[    0.126769] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15), disabled.
[    0.126827] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.126886] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.126944] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.127001] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.127603] ACPI: \_SB_.PCI0: notify handler is installed
[    0.127664] Found 1 acpi root devices
[    0.127711] ACPI : EC: GPE = 0x24, I/O: command/status = 0x66, data = 0x62
[    0.127831] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.127836] vgaarb: loaded
[    0.127838] vgaarb: bridge control possible 0000:00:02.0
[    0.128042] SCSI subsystem initialized
[    0.128097] libata version 3.00 loaded.
[    0.128125] ACPI: bus type USB registered
[    0.128146] usbcore: registered new interface driver usbfs
[    0.128160] usbcore: registered new interface driver hub
[    0.128194] usbcore: registered new device driver usb
[    0.128311] PCI: Using ACPI for IRQ routing
[    0.129968] PCI: pci_cache_line_size set to 64 bytes
[    0.130024] e820: reserve RAM buffer [mem 0x0009e400-0x0009ffff]
[    0.130027] e820: reserve RAM buffer [mem 0x7bf7a000-0x7bffffff]
[    0.130029] e820: reserve RAM buffer [mem 0x100600000-0x103ffffff]
[    0.130125] NetLabel: Initializing
[    0.130128] NetLabel:  domain hash size = 128
[    0.130129] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.130145] NetLabel:  unlabeled traffic allowed by default
[    0.130211] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.130219] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.132264] Switched to clocksource hpet
[    0.138864] AppArmor: AppArmor Filesystem Enabled
[    0.138892] pnp: PnP ACPI init
[    0.138913] ACPI: bus type PNP registered
[    0.138982] pnp 00:00: Plug and Play ACPI device, IDs PNP0c0e (active)
[    0.139021] pnp 00:01: Plug and Play ACPI device, IDs PNP0c0e (active)
[    0.139097] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.139100] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.139103] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.139106] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.139109] system 00:02: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.139111] system 00:02: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.139114] system 00:02: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.139117] system 00:02: [mem 0xfed45000-0xfed8ffff] could not be reserved
[    0.139120] system 00:02: [mem 0x00f00000-0x00ffffff] has been reserved
[    0.139124] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139330] pnp 00:03: [dma 4]
[    0.139352] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.139380] pnp 00:04: Plug and Play ACPI device, IDs INT0800 (active)
[    0.139487] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.139491] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.139528] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.139601] system 00:07: [io  0x1000-0x10fe] could not be reserved
[    0.139605] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139633] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.139680] system 00:09: [io  0x0900-0x09fe] has been reserved
[    0.139684] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139725] system 00:0a: [io  0x0200] has been reserved
[    0.139727] system 00:0a: [io  0x0204] has been reserved
[    0.139730] system 00:0a: [io  0x0800-0x087f] has been reserved
[    0.139732] system 00:0a: [io  0x0880-0x08ff] has been reserved
[    0.139736] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139774] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.139811] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.139857] pnp 00:0d: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    0.139960] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.140088] pnp: PnP ACPI: found 15 devices
[    0.140090] ACPI: bus type PNP unregistered
[    0.146607] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.146615] pci 0000:00:1c.0:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.146626] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.146628] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.146631] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.146633] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.146636] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.146638] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.146640] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.146643] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.146645] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.146647] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.146650] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.146652] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.146654] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.146657] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.146659] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff]
[    0.146662] pci_bus 0000:00: resource 19 [mem 0x7ea00001-0xfebfffff]
[    0.146664] pci_bus 0000:00: resource 20 [mem 0xfed40000-0xfed44fff]
[    0.146667] pci_bus 0000:01: resource 1 [mem 0xe0400000-0xe04fffff]
[    0.146703] NET: Registered protocol family 2
[    0.146889] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.146946] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.146994] TCP: Hash tables configured (established 16384 bind 16384)
[    0.147018] TCP: reno registered
[    0.147026] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.147040] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.147101] NET: Registered protocol family 1
[    0.147115] pci 0000:00:02.0: Boot video device
[    0.147620] PCI: CLS 64 bytes, default 64
[    0.147691] Trying to unpack rootfs image as initramfs...
[    0.609036] Freeing initrd memory: 18652K (ffff880035b82000 - ffff880036db9000)
[    0.609042] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.609046] software IO TLB [mem 0x75800000-0x79800000] (64MB) mapped at [ffff880075800000-ffff8800797fffff]
[    0.609228] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x15
[    0.609237] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x15
[    0.609286] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.609288] Scanning for low memory corruption every 60 seconds
[    0.609571] Initialise system trusted keyring
[    0.609629] audit: initializing netlink socket (disabled)
[    0.609640] type=2000 audit(1400303395.604:1): initialized
[    0.650768] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.652269] VFS: Disk quotas dquot_6.5.2
[    0.652320] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.652830] fuse init (API version 7.22)
[    0.652921] msgmni has been set to 3746
[    0.652987] Key type big_key registered
[    0.653373] Key type asymmetric registered
[    0.653376] Asymmetric key parser 'x509' registered
[    0.653410] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.653443] io scheduler noop registered
[    0.653445] io scheduler deadline registered (default)
[    0.653472] io scheduler cfq registered
[    0.653713] pcieport 0000:00:1c.0: irq 56 for MSI/MSI-X
[    0.653826] aer 0000:00:1c.0:pcie02: service driver aer loaded
[    0.653842] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.653844] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.653849] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.653863] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.653879] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.653926] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    0.653928] vesafb: scrolling: redraw
[    0.653930] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.654486] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90004400000, using 4160k, total 4160k
[    0.658031] Console: switching to colour frame buffer device 170x48
[    0.661648] fb0: VESA VGA frame buffer device
[    0.661676] intel_idle: MWAIT substates: 0x11142120
[    0.661678] intel_idle: v0.4 model 0x45
[    0.661680] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.661780] ipmi message handler version 39.2
[    0.661870] ACPI: AC Adapter [AC] (off-line)
[    0.661953] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.661982] ACPI: Lid Switch [LID0]
[    0.662019] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.662024] ACPI: Power Button [PWRB]
[    0.662057] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.662061] ACPI: Sleep Button [TPAD]
[    0.662094] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:01/input/input3
[    0.662097] ACPI: Sleep Button [TSCR]
[    0.662146] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[    0.662149] ACPI: Power Button [PWRF]
[    0.662211] ACPI: Fan [TDP0] (off)
[    0.662243] ACPI: Fan [TDP1] (on)
[    0.663052] thermal LNXTHERM:00: registered as thermal_zone0
[    0.663056] ACPI: Thermal Zone [THRM] (42 C)
[    0.663085] GHES: HEST is not enabled!
[    0.663180] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.663567] ACPI: Battery Slot [BAT0] (battery present)
[    0.664620] Linux agpgart interface v0.103
[    0.664741] tpm_tis 00:0d: 1.2 TPM (device-id 0xB, rev-id 16)
[    0.934478] brd: module loaded
[    0.935211] loop: module loaded
[    0.935625] libphy: Fixed MDIO Bus: probed
[    0.935725] tun: Universal TUN/TAP device driver, 1.6
[    0.935727] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.935777] PPP generic driver version 2.4.2
[    0.935821] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.935827] ehci-pci: EHCI PCI platform driver
[    0.936010] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.936017] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    0.936032] ehci-pci 0000:00:1d.0: debug port 2
[    0.939940] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.939966] ehci-pci 0000:00:1d.0: irq 19, io mem 0xe051f800
[    0.948141] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.948193] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.948196] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.948198] usb usb1: Product: EHCI Host Controller
[    0.948201] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    0.948203] usb usb1: SerialNumber: 0000:00:1d.0
[    0.948359] hub 1-0:1.0: USB hub found
[    0.948368] hub 1-0:1.0: 2 ports detected
[    0.948486] ehci-platform: EHCI generic platform driver
[    0.948496] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.948498] ohci-pci: OHCI PCI platform driver
[    0.948508] ohci-platform: OHCI generic platform driver
[    0.948515] uhci_hcd: USB Universal Host Controller Interface driver
[    0.948680] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.948686] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.948774] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.948798] xhci_hcd 0000:00:14.0: irq 57 for MSI/MSI-X
[    0.948871] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.948874] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.948876] usb usb2: Product: xHCI Host Controller
[    0.948878] usb usb2: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    0.948880] usb usb2: SerialNumber: 0000:00:14.0
[    0.949012] hub 2-0:1.0: USB hub found
[    0.949025] hub 2-0:1.0: 8 ports detected
[    0.949298] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.949303] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.949351] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    0.949353] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.949355] usb usb3: Product: xHCI Host Controller
[    0.949358] usb usb3: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    0.949360] usb usb3: SerialNumber: 0000:00:14.0
[    0.949484] hub 3-0:1.0: USB hub found
[    0.949493] hub 3-0:1.0: 4 ports detected
[    0.956299] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.956302] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.956839] i8042: Warning: Keylock active
[    0.956977] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.957306] mousedev: PS/2 mouse device common for all mice
[    0.958031] rtc_cmos 00:08: RTC can wake from S4
[    0.958208] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.958240] rtc_cmos 00:08: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.958330] device-mapper: uevent: version 1.0.3
[    0.958428] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.958436] ledtrig-cpu: registered to indicate activity on CPUs
[    0.958565] TCP: cubic registered
[    0.958683] NET: Registered protocol family 10
[    0.958901] NET: Registered protocol family 17
[    0.958910] Key type dns_resolver registered
[    0.959197] Loading compiled-in X.509 certificates
[    0.960441] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.960569] Loaded X.509 cert 'Magrathea: Glacier signing key: 69b0d0a79b85d90621706e8d06604d730b359fc0'
[    0.960583] registered taskstats version 1
[    0.963568] Key type trusted registered
[    0.966148] Key type encrypted registered
[    0.968807] AppArmor: AppArmor sha1 policy hashing enabled
[    1.260191] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.392496] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.392501] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.392764] hub 1-1:1.0: USB hub found
[    1.392853] hub 1-1:1.0: 8 ports detected
[    1.560142] usb 2-3: new high-speed USB device number 2 using xhci_hcd
[    1.608089] tsc: Refined TSC clocksource calibration: 1396.766 MHz
[    1.644155] usb 2-3: New USB device found, idVendor=1bcf, idProduct=2c67
[    1.644160] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.644163] usb 2-3: Product: HD WebCam
[    1.644165] usb 2-3: Manufacturer: SunplusIT Inc
[    1.880082] usb 2-4: new full-speed USB device number 3 using xhci_hcd
[    1.897667] usb 2-4: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[    1.899542] usb 2-4: New USB device found, idVendor=0489, idProduct=e056
[    1.899545] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.011978] usb 2-5: new full-speed USB device number 4 using xhci_hcd
[    2.031302] usb 2-5: New USB device found, idVendor=04f2, idProduct=0976
[    2.031307] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.031310] usb 2-5: Product: Wireless Device
[    2.031312] usb 2-5: Manufacturer: Chicony
[    2.031470] usb 2-5: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.031476] usb 2-5: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.608102] Switched to clocksource tsc
[   53.775691] regulator-dummy: disabling
[   53.775752]   Magic number: 14:414:163
[   53.775859] rtc_cmos 00:08: setting system clock to 2014-05-17 05:10:49 UTC (1400303449)
[   53.776225] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   53.776228] EDD information not available.
[   53.776269] PM: Hibernation image not present or could not be loaded.
[   53.777441] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[   53.777444] Write protecting the kernel read-only data: 12288k
[   53.780689] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[   53.783156] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[   53.802139] systemd-udevd[100]: starting version 204
[   53.844207] hidraw: raw HID events driver (C) Jiri Kosina
[   53.851625] ahci 0000:00:1f.2: version 3.0
[   53.851808] ahci 0000:00:1f.2: irq 58 for MSI/MSI-X
[   53.851833] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[   53.863021] usbcore: registered new interface driver usbhid
[   53.863025] usbhid: USB HID core driver
[   53.868130] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x1 impl SATA mode
[   53.868137] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo only pio slum part deso sadm sds apst 
[   53.870334] scsi0 : ahci
[   53.871307] scsi1 : ahci
[   53.871377] ata1: SATA max UDMA/133 abar m2048@0xe051f000 port 0xe051f100 irq 58
[   53.871380] ata2: DUMMY
[   53.891729] input: Chicony Wireless Device as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input6
[   53.891836] hid-generic 0003:04F2:0976.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony Wireless Device] on usb-0000:00:14.0-5/input0
[   53.893720] input: Chicony Wireless Device as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.1/input/input7
[   53.894043] hid-generic 0003:04F2:0976.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Chicony Wireless Device] on usb-0000:00:14.0-5/input1
[   53.894212] input: Chicony Wireless Device as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.2/input/input8
[   53.894296] hid-generic 0003:04F2:0976.0003: input,hidraw2: USB HID v1.11 Mouse [Chicony Wireless Device] on usb-0000:00:14.0-5/input2
[   54.191342] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   54.191526] ata1.00: ATA-10: KINGSTON SNS4151S316G, S9FM01.1, max UDMA/100
[   54.191531] ata1.00: 31277232 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[   54.191944] ata1.00: configured for UDMA/100
[   54.192136] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SNS4151 S9FM PQ: 0 ANSI: 5
[   54.192339] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   54.192369] sd 0:0:0:0: [sda] 31277232 512-byte logical blocks: (16.0 GB/14.9 GiB)
[   54.192436] sd 0:0:0:0: [sda] Write Protect is off
[   54.192439] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.192458] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.194441]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12
[   54.195213] sd 0:0:0:0: [sda] Attached SCSI disk
[   54.237321] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   54.333895] random: init urandom read with 41 bits of entropy available
[   54.366445] init: plymouth-upstart-bridge main process (152) terminated with status 1
[   54.366462] init: plymouth-upstart-bridge main process ended, respawning
[   54.378762] init: plymouth-upstart-bridge main process (162) terminated with status 1
[   54.378779] init: plymouth-upstart-bridge main process ended, respawning
[   54.387167] init: plymouth-upstart-bridge main process (165) terminated with status 1
[   54.387184] init: plymouth-upstart-bridge main process ended, respawning
[   54.813917] systemd-udevd[271]: starting version 204
[   54.876647] EXT4-fs (sda7): re-mounted. Opts: (null)
[   54.908298] lp: driver loaded but no devices found
[   54.928650] ppdev: user-space parallel port driver
[   54.984747] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   54.984980] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   55.015435] [drm] Initialized drm 1.1.0 20060810
[   55.039800] [drm] Memory usable by graphics device = 2048M
[   55.039806] checking generic (d0000000 410000) vs hw (d0000000 10000000)
[   55.039809] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   55.039830] Console: switching to colour dummy device 80x25
[   55.083076] i915 0000:00:02.0: irq 59 for MSI/MSI-X
[   55.083091] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   55.083093] [drm] Driver supports precise vblank timestamp query.
[   55.083308] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   55.215541] Linux video capture interface: v2.00
[   55.222651] Bluetooth: Core ver 2.17
[   55.228328] NET: Registered protocol family 31
[   55.228333] Bluetooth: HCI device and connection manager initialized
[   55.228343] Bluetooth: HCI socket layer initialized
[   55.228346] Bluetooth: L2CAP socket layer initialized
[   55.228353] Bluetooth: SCO socket layer initialized
[   55.346842] cfg80211: Calling CRDA to update world regulatory domain
[   55.356137] usbcore: registered new interface driver btusb
[   55.357930] fbcon: inteldrmfb (fb0) is primary device
[   55.389738] uvcvideo: Found UVC 1.00 device HD WebCam (1bcf:2c67)
[   55.395207] random: nonblocking pool is initialized
[   55.408803] input: HD WebCam as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.0/input/input10
[   55.413205] usbcore: registered new interface driver uvcvideo
[   55.413206] USB Video Class driver (1.1.1)
[   55.454997] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   55.454998] Bluetooth: BNEP filters: protocol multicast
[   55.455007] Bluetooth: BNEP socket layer initialized
[   55.458639] usb 2-4: USB disconnect, device number 3
[   55.458878] usbcore: registered new interface driver ath3k
[   55.487793] Bluetooth: RFCOMM TTY layer initialized
[   55.487803] Bluetooth: RFCOMM socket layer initialized
[   55.487808] Bluetooth: RFCOMM ver 1.11
[   55.534772] ath: phy0: ASPM enabled: 0x43
[   55.534775] ath: EEPROM regdomain: 0x6c
[   55.534775] ath: EEPROM indicates we should expect a direct regpair map
[   55.534777] ath: Country alpha2 being used: 00
[   55.534778] ath: Regpair used: 0x6c
[   55.554602] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   55.555210] ieee80211 phy0: Atheros AR9462 Rev:2 mem=0xffffc90004580000, irq=16
[   55.731083] usb 2-4: new full-speed USB device number 5 using xhci_hcd
[   55.741370] intel_rapl: domain uncore energy ctr 10101:10101 not working, skip
[   55.748795] usb 2-4: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[   55.750673] usb 2-4: New USB device found, idVendor=0489, idProduct=e056
[   55.750675] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   55.837102] device-mapper: multipath: version 1.6.0 loaded
[   56.426295] cfg80211: World regulatory domain updated:
[   56.426296] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   56.426298] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   56.426299] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   56.426300] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   56.426301] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   56.426302] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   56.811011] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   56.962875] Console: switching to colour frame buffer device 170x48
[   56.966636] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   56.966638] i915 0000:00:02.0: registered panic notifier
[   56.966658] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   56.967259] snd_hda_intel 0000:00:1b.0: irq 60 for MSI/MSI-X
[   57.010123] i915_bdw: exports duplicate symbol i915_release_power_well (owned by i915)
[   57.017219] SKU: Nid=0x0 sku_cfg=0x00000283
[   57.017223] SKU: port_connectivity=0x0
[   57.017224] SKU: enable_pcbeep=0x1
[   57.017226] SKU: check_sum=0x00000000
[   57.017228] SKU: customization=0x00000000
[   57.017229] SKU: external_amp=0x0
[   57.017230] SKU: platform_type=0x0
[   57.017232] SKU: swap=0x1
[   57.017233] SKU: override=0x1
[   57.017444] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   57.017447]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   57.017449]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   57.017450]    mono: mono_out=0x0
[   57.017451]    inputs:
[   57.017453]      Internal Mic=0x1a
[   57.017455]      Mic=0x19
[   57.017457] realtek: Enabling init ASM_ID=0x0283 CODEC_ID=10ec0283
[   57.025022] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[   57.025181] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[   57.031548] HDA driver get symbol successfully from i915 module
[   57.038902] snd_hda_intel 0000:00:03.0: irq 61 for MSI/MSI-X
[   57.065452] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input15
[   57.065594] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[   57.065703] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input13
[   57.149772] init: cups main process (558) killed by HUP signal
[   57.149790] init: cups main process ended, respawning
[   57.375073] init: failsafe main process (599) killed by TERM signal
[   57.933511] init: plymouth-upstart-bridge main process ended, respawning
[   58.095546] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.096163] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.258047] init: udev-fallback-graphics main process (927) terminated with status 1
[   58.525156] init: plymouth-splash main process (996) terminated with status 1
[   59.558560] init: plymouth-stop pre-start process (1202) terminated with status 1
[   59.643639] init: anacron main process (760) killed by TERM signal
[   65.098185] wlan0: authenticate with 0a:a1:51:9f:0d:9a
[   65.153534] wlan0: send auth to 0a:a1:51:9f:0d:9a (try 1/3)
[   65.155541] wlan0: authenticated
[   65.157571] wlan0: associate with 0a:a1:51:9f:0d:9a (try 1/3)
[   65.161870] wlan0: RX AssocResp from 0a:a1:51:9f:0d:9a (capab=0x411 status=0 aid=1)
[   65.161921] wlan0: associated
[   65.161932] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   65.478500] wlan0: deauthenticating from 0a:a1:51:9f:0d:9a by local choice (reason=2)
[   65.491512] cfg80211: Calling CRDA to update world regulatory domain
[   65.498471] cfg80211: World regulatory domain updated:
[   65.498476] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   65.498479] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.498482] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.498484] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   65.498486] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.498488] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.505747] wlan0: authenticate with 0a:a1:51:9f:0d:9a
[   65.595143] wlan0: send auth to 0a:a1:51:9f:0d:9a (try 1/3)
[   65.596991] wlan0: authenticated
[   65.609393] wlan0: associate with 0a:a1:51:9f:0d:9a (try 1/3)
[   65.613671] wlan0: RX AssocResp from 0a:a1:51:9f:0d:9a (capab=0x411 status=0 aid=1)
[   65.613719] wlan0: associated
[  383.538144] traps: compiz[1839] trap int3 ip:7f9234fd4c13 sp:7fff31cd4990 error:0

---

### Post by Luke M on 2014-05-17
You ran dmesg immediately after plugging in the USB device? There's nothing there at all.

Oh, wait...maybe it's affected by how you boot linux. I don't use the "quiet" option (default with ubuntu), maybe that is suppressing the info in your case.

If you don't mind, edit /etc/default/grub to remove "quiet" option, and then run
sudo update-grub

reboot, and see if you get more info from dmesg.

---

### Post by dobriensd on 2014-05-17
Out of curiosity, does this show anything different?

[    0.119935] pci 0000:00:1f.6: reg 0x10: [mem 0xe051e000-0xe051efff 64bit]
[    0.120200] pci 0000:01:00.0: [168c:0034] type 00 class 0x028000
[    0.120226] pci 0000:01:00.0: reg 0x10: [mem 0xe0400000-0xe047ffff 64bit]
[    0.120287] pci 0000:01:00.0: reg 0x30: [mem 0xe0480000-0xe048ffff pref]
[    0.120347] pci 0000:01:00.0: supports D1 D2
[    0.120349] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.126959] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.126966] pci 0000:00:1c.0:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.127206] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11, disabled.
[    0.127273] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10, disabled.
[    0.127334] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11, disabled.
[    0.127393] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15), disabled.
[    0.127452] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.127510] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.127568] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.127626] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.128228] ACPI: \_SB_.PCI0: notify handler is installed
[    0.128289] Found 1 acpi root devices
[    0.128336] ACPI : EC: GPE = 0x24, I/O: command/status = 0x66, data = 0x62
[    0.128455] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.128460] vgaarb: loaded
[    0.128462] vgaarb: bridge control possible 0000:00:02.0
[    0.128666] SCSI subsystem initialized
[    0.128721] libata version 3.00 loaded.
[    0.128750] ACPI: bus type USB registered
[    0.128771] usbcore: registered new interface driver usbfs
[    0.128785] usbcore: registered new interface driver hub
[    0.128819] usbcore: registered new device driver usb
[    0.128938] PCI: Using ACPI for IRQ routing
[    0.130597] PCI: pci_cache_line_size set to 64 bytes
[    0.130653] e820: reserve RAM buffer [mem 0x0009e400-0x0009ffff]
[    0.130656] e820: reserve RAM buffer [mem 0x7bf7a000-0x7bffffff]
[    0.130658] e820: reserve RAM buffer [mem 0x100600000-0x103ffffff]
[    0.130754] NetLabel: Initializing
[    0.130756] NetLabel:  domain hash size = 128
[    0.130757] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.130774] NetLabel:  unlabeled traffic allowed by default
[    0.130840] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.130848] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.132892] Switched to clocksource hpet
[    0.139493] AppArmor: AppArmor Filesystem Enabled
[    0.139520] pnp: PnP ACPI init
[    0.139541] ACPI: bus type PNP registered
[    0.139607] pnp 00:00: Plug and Play ACPI device, IDs PNP0c0e (active)
[    0.139648] pnp 00:01: Plug and Play ACPI device, IDs PNP0c0e (active)
[    0.139727] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.139731] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.139734] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.139736] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.139740] system 00:02: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.139742] system 00:02: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.139745] system 00:02: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.139748] system 00:02: [mem 0xfed45000-0xfed8ffff] could not be reserved
[    0.139751] system 00:02: [mem 0x00f00000-0x00ffffff] has been reserved
[    0.139755] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139960] pnp 00:03: [dma 4]
[    0.139983] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.140011] pnp 00:04: Plug and Play ACPI device, IDs INT0800 (active)
[    0.140117] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.140121] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.140158] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.140231] system 00:07: [io  0x1000-0x10fe] could not be reserved
[    0.140235] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.140263] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.140310] system 00:09: [io  0x0900-0x09fe] has been reserved
[    0.140313] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.140354] system 00:0a: [io  0x0200] has been reserved
[    0.140357] system 00:0a: [io  0x0204] has been reserved
[    0.140359] system 00:0a: [io  0x0800-0x087f] has been reserved
[    0.140362] system 00:0a: [io  0x0880-0x08ff] has been reserved
[    0.140365] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.140403] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.140441] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.140487] pnp 00:0d: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    0.140589] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.140718] pnp: PnP ACPI: found 15 devices
[    0.140719] ACPI: bus type PNP unregistered
[    0.147238] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.147246] pci 0000:00:1c.0:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.147257] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.147260] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.147262] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.147265] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.147267] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.147269] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.147271] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.147274] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.147276] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.147278] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.147281] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.147283] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.147285] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.147287] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.147290] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff]
[    0.147292] pci_bus 0000:00: resource 19 [mem 0x7ea00001-0xfebfffff]
[    0.147294] pci_bus 0000:00: resource 20 [mem 0xfed40000-0xfed44fff]
[    0.147297] pci_bus 0000:01: resource 1 [mem 0xe0400000-0xe04fffff]
[    0.147334] NET: Registered protocol family 2
[    0.147522] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.147579] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.147627] TCP: Hash tables configured (established 16384 bind 16384)
[    0.147650] TCP: reno registered
[    0.147658] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.147672] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.147731] NET: Registered protocol family 1
[    0.147746] pci 0000:00:02.0: Boot video device
[    0.148250] PCI: CLS 64 bytes, default 64
[    0.148321] Trying to unpack rootfs image as initramfs...
[    0.609762] Freeing initrd memory: 18652K (ffff880035b82000 - ffff880036db9000)
[    0.609767] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.609771] software IO TLB [mem 0x75800000-0x79800000] (64MB) mapped at [ffff880075800000-ffff8800797fffff]
[    0.609955] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x15
[    0.609963] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x15
[    0.610013] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.610015] Scanning for low memory corruption every 60 seconds
[    0.610300] Initialise system trusted keyring
[    0.610355] audit: initializing netlink socket (disabled)
[    0.610366] type=2000 audit(1400307645.604:1): initialized
[    0.651519] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.653014] VFS: Disk quotas dquot_6.5.2
[    0.653064] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.653571] fuse init (API version 7.22)
[    0.653662] msgmni has been set to 3746
[    0.653728] Key type big_key registered
[    0.654113] Key type asymmetric registered
[    0.654116] Asymmetric key parser 'x509' registered
[    0.654154] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.654185] io scheduler noop registered
[    0.654187] io scheduler deadline registered (default)
[    0.654214] io scheduler cfq registered
[    0.654457] pcieport 0000:00:1c.0: irq 56 for MSI/MSI-X
[    0.654570] aer 0000:00:1c.0:pcie02: service driver aer loaded
[    0.654586] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.654589] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.654593] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.654608] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.654625] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.654670] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    0.654671] vesafb: scrolling: redraw
[    0.654674] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.655229] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90004400000, using 4160k, total 4160k
[    0.659104] Console: switching to colour frame buffer device 170x48
[    0.663072] fb0: VESA VGA frame buffer device
[    0.663101] intel_idle: MWAIT substates: 0x11142120
[    0.663103] intel_idle: v0.4 model 0x45
[    0.663105] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.663204] ipmi message handler version 39.2
[    0.663295] ACPI: AC Adapter [AC] (on-line)
[    0.663375] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.663404] ACPI: Lid Switch [LID0]
[    0.663441] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.663446] ACPI: Power Button [PWRB]
[    0.663480] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.663483] ACPI: Sleep Button [TPAD]
[    0.663516] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:01/input/input3
[    0.663520] ACPI: Sleep Button [TSCR]
[    0.663569] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[    0.663572] ACPI: Power Button [PWRF]
[    0.663633] ACPI: Fan [TDP0] (off)
[    0.663666] ACPI: Fan [TDP1] (on)
[    0.664476] thermal LNXTHERM:00: registered as thermal_zone0
[    0.664479] ACPI: Thermal Zone [THRM] (46 C)
[    0.664509] GHES: HEST is not enabled!
[    0.664599] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.665037] ACPI: Battery Slot [BAT0] (battery present)
[    0.666027] Linux agpgart interface v0.103
[    0.666149] tpm_tis 00:0d: 1.2 TPM (device-id 0xB, rev-id 16)
[    0.923212] brd: module loaded
[    0.923895] loop: module loaded
[    0.924316] libphy: Fixed MDIO Bus: probed
[    0.924418] tun: Universal TUN/TAP device driver, 1.6
[    0.924419] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.924464] PPP generic driver version 2.4.2
[    0.924507] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.924511] ehci-pci: EHCI PCI platform driver
[    0.924690] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.924697] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    0.924712] ehci-pci 0000:00:1d.0: debug port 2
[    0.928620] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.928639] ehci-pci 0000:00:1d.0: irq 19, io mem 0xe051f800
[    0.936773] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.936834] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.936837] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.936839] usb usb1: Product: EHCI Host Controller
[    0.936842] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    0.936844] usb usb1: SerialNumber: 0000:00:1d.0
[    0.937003] hub 1-0:1.0: USB hub found
[    0.937011] hub 1-0:1.0: 2 ports detected
[    0.937128] ehci-platform: EHCI generic platform driver
[    0.937138] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.937140] ohci-pci: OHCI PCI platform driver
[    0.937152] ohci-platform: OHCI generic platform driver
[    0.937159] uhci_hcd: USB Universal Host Controller Interface driver
[    0.937320] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.937326] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.937420] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.937443] xhci_hcd 0000:00:14.0: irq 57 for MSI/MSI-X
[    0.937516] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.937519] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.937521] usb usb2: Product: xHCI Host Controller
[    0.937523] usb usb2: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    0.937525] usb usb2: SerialNumber: 0000:00:14.0
[    0.937660] hub 2-0:1.0: USB hub found
[    0.937674] hub 2-0:1.0: 8 ports detected
[    0.937951] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.937955] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.938001] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    0.938003] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.938005] usb usb3: Product: xHCI Host Controller
[    0.938008] usb usb3: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    0.938010] usb usb3: SerialNumber: 0000:00:14.0
[    0.938132] hub 3-0:1.0: USB hub found
[    0.938142] hub 3-0:1.0: 4 ports detected
[    0.944994] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.944998] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.945486] i8042: Warning: Keylock active
[    0.945628] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.945904] mousedev: PS/2 mouse device common for all mice
[    0.946640] rtc_cmos 00:08: RTC can wake from S4
[    0.946876] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.946908] rtc_cmos 00:08: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.946987] device-mapper: uevent: version 1.0.3
[    0.947091] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.947098] ledtrig-cpu: registered to indicate activity on CPUs
[    0.947229] TCP: cubic registered
[    0.947344] NET: Registered protocol family 10
[    0.947560] NET: Registered protocol family 17
[    0.947571] Key type dns_resolver registered
[    0.947858] Loading compiled-in X.509 certificates
[    0.949103] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.949231] Loaded X.509 cert 'Magrathea: Glacier signing key: 69b0d0a79b85d90621706e8d06604d730b359fc0'
[    0.949245] registered taskstats version 1
[    0.952247] Key type trusted registered
[    0.954806] Key type encrypted registered
[    0.957469] AppArmor: AppArmor sha1 policy hashing enabled
[    1.248825] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.381170] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.381175] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.381418] hub 1-1:1.0: USB hub found
[    1.381527] hub 1-1:1.0: 8 ports detected
[    1.548775] usb 2-3: new high-speed USB device number 2 using xhci_hcd
[    1.608719] tsc: Refined TSC clocksource calibration: 1396.766 MHz
[    1.632901] usb 2-3: New USB device found, idVendor=1bcf, idProduct=2c67
[    1.632907] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.632910] usb 2-3: Product: HD WebCam
[    1.632912] usb 2-3: Manufacturer: SunplusIT Inc
[    1.868694] usb 2-4: new full-speed USB device number 3 using xhci_hcd
[    1.886298] usb 2-4: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[    1.888161] usb 2-4: New USB device found, idVendor=0489, idProduct=e056
[    1.888164] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.000611] usb 2-5: new full-speed USB device number 4 using xhci_hcd
[    2.019921] usb 2-5: New USB device found, idVendor=04f2, idProduct=0976
[    2.019926] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.019929] usb 2-5: Product: Wireless Device
[    2.019932] usb 2-5: Manufacturer: Chicony
[    2.020089] usb 2-5: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.020095] usb 2-5: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.608760] Switched to clocksource tsc
[   53.776337] regulator-dummy: disabling
[   53.776397]   Magic number: 14:176:317
[   53.776429] tty tty42: hash matches
[   53.776455] reg-dummy reg-dummy: hash matches
[   53.776507] rtc_cmos 00:08: setting system clock to 2014-05-17 06:21:38 UTC (1400307698)
[   53.776710] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   53.776712] EDD information not available.
[   53.776752] PM: Hibernation image not present or could not be loaded.
[   53.777899] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[   53.777901] Write protecting the kernel read-only data: 12288k
[   53.781137] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[   53.783612] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[   53.802581] systemd-udevd[100]: starting version 204
[   53.849227] hidraw: raw HID events driver (C) Jiri Kosina
[   53.856716] ahci 0000:00:1f.2: version 3.0
[   53.856906] ahci 0000:00:1f.2: irq 58 for MSI/MSI-X
[   53.856930] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[   53.856947] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x1 impl SATA mode
[   53.856951] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo only pio slum part deso sadm sds apst 
[   53.859975] scsi0 : ahci
[   53.861068] scsi1 : ahci
[   53.861122] ata1: SATA max UDMA/133 abar m2048@0xe051f000 port 0xe051f100 irq 58
[   53.861125] ata2: DUMMY
[   53.863824] usbcore: registered new interface driver usbhid
[   53.863828] usbhid: USB HID core driver
[   53.899101] input: Chicony Wireless Device as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input6
[   53.899188] hid-generic 0003:04F2:0976.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony Wireless Device] on usb-0000:00:14.0-5/input0
[   53.900786] input: Chicony Wireless Device as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.1/input/input7
[   53.901015] hid-generic 0003:04F2:0976.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Chicony Wireless Device] on usb-0000:00:14.0-5/input1
[   53.901196] input: Chicony Wireless Device as /devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.2/input/input8
[   53.901320] hid-generic 0003:04F2:0976.0003: input,hidraw2: USB HID v1.11 Mouse [Chicony Wireless Device] on usb-0000:00:14.0-5/input2
[   54.179972] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   54.180197] ata1.00: ATA-10: KINGSTON SNS4151S316G, S9FM01.1, max UDMA/100
[   54.180202] ata1.00: 31277232 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[   54.180575] ata1.00: configured for UDMA/100
[   54.180772] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SNS4151 S9FM PQ: 0 ANSI: 5
[   54.180976] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   54.180982] sd 0:0:0:0: [sda] 31277232 512-byte logical blocks: (16.0 GB/14.9 GiB)
[   54.181065] sd 0:0:0:0: [sda] Write Protect is off
[   54.181068] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.181088] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.182762]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12
[   54.183965] sd 0:0:0:0: [sda] Attached SCSI disk
[   54.225943] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   54.323172] random: init urandom read with 40 bits of entropy available
[   54.356584] init: plymouth-upstart-bridge main process (152) terminated with status 1
[   54.356601] init: plymouth-upstart-bridge main process ended, respawning
[   54.367231] init: plymouth-upstart-bridge main process (162) terminated with status 1
[   54.367248] init: plymouth-upstart-bridge main process ended, respawning
[   54.375910] init: plymouth-upstart-bridge main process (165) terminated with status 1
[   54.375926] init: plymouth-upstart-bridge main process ended, respawning
[   54.774324] systemd-udevd[270]: starting version 204
[   54.859999] lp: driver loaded but no devices found
[   54.866381] ppdev: user-space parallel port driver
[   54.925137] Bluetooth: Core ver 2.17
[   54.925161] NET: Registered protocol family 31
[   54.925163] Bluetooth: HCI device and connection manager initialized
[   54.925172] Bluetooth: HCI socket layer initialized
[   54.925175] Bluetooth: L2CAP socket layer initialized
[   54.925180] Bluetooth: SCO socket layer initialized
[   54.928797] EXT4-fs (sda7): re-mounted. Opts: (null)
[   54.952845] [drm] Initialized drm 1.1.0 20060810
[   54.966113] usbcore: registered new interface driver btusb
[   54.978752] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   54.985163] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   55.001260] cfg80211: Calling CRDA to update world regulatory domain
[   55.073634] [drm] Memory usable by graphics device = 2048M
[   55.073641] checking generic (d0000000 410000) vs hw (d0000000 10000000)
[   55.073643] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   55.073666] Console: switching to colour dummy device 80x25
[   55.086632] ath: phy0: ASPM enabled: 0x43
[   55.086638] ath: EEPROM regdomain: 0x6c
[   55.086640] ath: EEPROM indicates we should expect a direct regpair map
[   55.086643] ath: Country alpha2 being used: 00
[   55.086644] ath: Regpair used: 0x6c
[   55.097803] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   55.098206] ieee80211 phy0: Atheros AR9462 Rev:2 mem=0xffffc90004400000, irq=16
[   55.125683] i915 0000:00:02.0: irq 59 for MSI/MSI-X
[   55.125696] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   55.125698] [drm] Driver supports precise vblank timestamp query.
[   55.125795] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   55.141565] usb 2-4: USB disconnect, device number 3
[   55.147693] usbcore: registered new interface driver ath3k
[   55.148242] Linux video capture interface: v2.00
[   55.176915] uvcvideo: Found UVC 1.00 device HD WebCam (1bcf:2c67)
[   55.194451] input: HD WebCam as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.0/input/input10
[   55.194575] usbcore: registered new interface driver uvcvideo
[   55.194578] USB Video Class driver (1.1.1)
[   55.350353] random: nonblocking pool is initialized
[   55.419733] usb 2-4: new full-speed USB device number 5 using xhci_hcd
[   55.437981] usb 2-4: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[   55.443455] usb 2-4: New USB device found, idVendor=0489, idProduct=e056
[   55.443463] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   55.457157] fbcon: inteldrmfb (fb0) is primary device
[   55.800852] device-mapper: multipath: version 1.6.0 loaded
[   55.837370] Bluetooth: RFCOMM TTY layer initialized
[   55.837379] Bluetooth: RFCOMM socket layer initialized
[   55.837384] Bluetooth: RFCOMM ver 1.11
[   55.910006] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   55.910007] Bluetooth: BNEP filters: protocol multicast
[   55.910015] Bluetooth: BNEP socket layer initialized
[   56.442768] cfg80211: World regulatory domain updated:
[   56.442769] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   56.442772] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   56.442773] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   56.442774] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   56.442775] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   56.442776] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   56.811578] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   57.047491] Console: switching to colour frame buffer device 170x48
[   57.051604] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   57.051605] i915 0000:00:02.0: registered panic notifier
[   57.051623] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   57.052201] snd_hda_intel 0000:00:1b.0: irq 60 for MSI/MSI-X
[   57.116302] i915_bdw: exports duplicate symbol i915_release_power_well (owned by i915)
[   57.131826] HDA driver get symbol successfully from i915 module
[   57.132037] SKU: Nid=0x0 sku_cfg=0x00000283
[   57.132040] SKU: port_connectivity=0x0
[   57.132041] SKU: enable_pcbeep=0x1
[   57.132043] SKU: check_sum=0x00000000
[   57.132044] SKU: customization=0x00000000
[   57.132046] SKU: external_amp=0x0
[   57.132047] SKU: platform_type=0x0
[   57.132048] SKU: swap=0x1
[   57.132050] SKU: override=0x1
[   57.132440] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   57.132443]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   57.132445]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   57.132446]    mono: mono_out=0x0
[   57.132447]    inputs:
[   57.132450]      Internal Mic=0x1a
[   57.132452]      Mic=0x19
[   57.132454] realtek: Enabling init ASM_ID=0x0283 CODEC_ID=10ec0283
[   57.139459] snd_hda_intel 0000:00:03.0: irq 61 for MSI/MSI-X
[   57.166495] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[   57.166931] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[   57.187482] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input15
[   57.187651] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[   57.187767] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input13
[   57.360209] init: failsafe main process (640) killed by TERM signal
[   57.781195] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.785045] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.055000] init: plymouth-upstart-bridge main process ended, respawning
[   58.346338] init: plymouth-splash main process (968) terminated with status 1
[   59.649161] init: plymouth-stop pre-start process (1284) terminated with status 1
[   64.762609] wlan0: authenticate with 1c:c6:3c:1d:69:ae
[   64.843338] wlan0: send auth to 1c:c6:3c:1d:69:ae (try 1/3)
[   64.845492] wlan0: authenticated
[   64.846244] wlan0: associate with 1c:c6:3c:1d:69:ae (try 1/3)
[   64.849741] wlan0: RX AssocResp from 1c:c6:3c:1d:69:ae (capab=0x411 status=0 aid=9)
[   64.849789] wlan0: associated
[   64.849819] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   65.299957] wlan0: deauthenticating from 1c:c6:3c:1d:69:ae by local choice (reason=2)
[   65.318119] cfg80211: Calling CRDA to update world regulatory domain
[   65.318211] wlan0: authenticate with 1c:c6:3c:1d:69:ae
[   65.450118] wlan0: send auth to 1c:c6:3c:1d:69:ae (try 1/3)
[   65.450782] cfg80211: World regulatory domain updated:
[   65.450787] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   65.450790] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.450792] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.450794] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   65.450796] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.450798] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.452384] wlan0: authenticated
[   65.458294] wlan0: associate with 1c:c6:3c:1d:69:ae (try 1/3)
[   65.461874] wlan0: RX AssocResp from 1c:c6:3c:1d:69:ae (capab=0x411 status=0 aid=9)
[   65.461921] wlan0: associated


I tried turning the device on first, although the usb should recognize it as a 16GB drive either way I thought maybe this would make a difference.

---

### Post by Luke M on 2014-05-17
Also, run lsusb and see if the device is there.

---

### Post by dobriensd on 2014-05-17
Here is the lsusb dump:

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04f2:0976 Chicony Electronics Co., Ltd 
Bus 002 Device 005: ID 0489:e056 Foxconn / Hon Hai 
Bus 002 Device 002: ID 1bcf:2c67 Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

