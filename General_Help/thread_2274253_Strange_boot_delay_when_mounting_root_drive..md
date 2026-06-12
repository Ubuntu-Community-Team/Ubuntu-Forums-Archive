---
title: "Strange boot delay when mounting root drive."
date: 2015-04-19
forum: General Help
---

### Post by kumareshy on 2015-04-19
Hello everybody,
            I've noticed this strange issue during boot time in both ubuntu 14.04 and 14.10. Here's the dmesg log.
```
[    0.567153] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.568115] zpool: loaded
[    0.568118] zbud: loaded
[    0.568229] VFS: Disk quotas dquot_6.5.2
[    0.568254] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.568560] fuse init (API version 7.23)
[    0.568616] msgmni has been set to 7835
[    0.568662] Key type big_key registered
[    0.568967] Key type asymmetric registered
[    0.568969] Asymmetric key parser 'x509' registered
[    0.568992] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.569040] io scheduler noop registered
[    0.569042] io scheduler deadline registered
[    0.569074] io scheduler cfq registered (default)
[    0.569215] pcieport 0000:00:01.0: irq 41 for MSI/MSI-X
[    0.569348] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.569360] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.569393] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.569394] vesafb: scrolling: redraw
[    0.569396] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    0.569406] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90004780000, using 3072k, total 3072k
[    0.600841] Console: switching to colour frame buffer device 128x48
[    0.632594] fb0: VESA VGA frame buffer device
[    0.632879] intel_idle: MWAIT substates: 0x1120
[    0.632881] intel_idle: v0.4 model 0x3A
[    0.632881] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.633125] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.633619] ACPI: Power Button [PWRB]
[    0.633859] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.634302] ACPI: Power Button [PWRF]
[    0.634565] ACPI: Fan [FAN0] (off)
[    0.634784] ACPI: Fan [FAN1] (off)
[    0.635001] ACPI: Fan [FAN2] (off)
[    0.635219] ACPI: Fan [FAN3] (off)
[    0.635435] ACPI: Fan [FAN4] (off)
[    0.646121] thermal LNXTHERM:00: registered as thermal_zone0
[    0.646455] ACPI: Thermal Zone [TZ00] (28 C)
[    0.646843] thermal LNXTHERM:01: registered as thermal_zone1
[    0.647177] ACPI: Thermal Zone [TZ01] (30 C)
[    0.647450] GHES: HEST is not enabled!
[    0.647730] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.668576] 00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.670293] Linux agpgart interface v0.103
[    0.671403] brd: module loaded
[    0.672023] loop: module loaded
[    0.672354] libphy: Fixed MDIO Bus: probed
[    0.672598] tun: Universal TUN/TAP device driver, 1.6
[    0.672895] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.684155] PPP generic driver version 2.4.2
[    0.695338] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.706635] ehci-pci: EHCI PCI platform driver
[    0.717885] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.729246] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.740809] ehci-pci 0000:00:1a.0: debug port 2
[    0.756065] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.756079] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7f28000
[    0.777957] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.789260] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.800784] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.812459] usb usb1: Product: EHCI Host Controller
[    0.824103] usb usb1: Manufacturer: Linux 3.16.0-34-generic ehci_hcd
[    0.835772] usb usb1: SerialNumber: 0000:00:1a.0
[    0.847361] hub 1-0:1.0: USB hub found
[    0.858895] hub 1-0:1.0: 2 ports detected
[    0.870591] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.882316] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.894161] ehci-pci 0000:00:1d.0: debug port 2
[    0.909670] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.909681] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7f27000
[    0.930060] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.941546] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.953201] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.964823] usb usb2: Product: EHCI Host Controller
[    0.976230] usb usb2: Manufacturer: Linux 3.16.0-34-generic ehci_hcd
[    0.987646] usb usb2: SerialNumber: 0000:00:1d.0
[    0.999024] hub 2-0:1.0: USB hub found
[    1.009995] hub 2-0:1.0: 2 ports detected
[    1.020750] ehci-platform: EHCI generic platform driver
[    1.031380] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.041961] ohci-pci: OHCI PCI platform driver
[    1.052580] ohci-platform: OHCI generic platform driver
[    1.063426] uhci_hcd: USB Universal Host Controller Interface driver
[    1.074633] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.089058] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.100760] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.112445] mousedev: PS/2 mouse device common for all mice
[    1.124223] rtc_cmos 00:02: RTC can wake from S4
[    1.135829] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.147662] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.159434] device-mapper: uevent: version 1.0.3
[    1.171099] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.182913] Intel P-state driver initializing.
[    1.194586] Intel pstate controlling: cpu 0
[    1.194636] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.218217] Intel pstate controlling: cpu 1
[    1.230217] Intel pstate controlling: cpu 2
[    1.242017] Intel pstate controlling: cpu 3
[    1.253551] Intel pstate controlling: cpu 4
[    1.263683] Intel pstate controlling: cpu 5
[    1.273530] Intel pstate controlling: cpu 6
[    1.283151] Intel pstate controlling: cpu 7
[    1.292604] Consider also installing thermald for improved thermal control.
[    1.302251] ledtrig-cpu: registered to indicate activity on CPUs
[    1.312008] TCP: cubic registered
[    1.321694] IPv6: Loaded, but administratively disabled, reboot required to enable
[    1.331771] NET: Registered protocol family 17
[    1.334528] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.334529] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.334675] hub 1-1:1.0: USB hub found
[    1.334777] hub 1-1:1.0: 4 ports detected
[    1.381583] Key type dns_resolver registered
[    1.391848] Loading compiled-in X.509 certificates
[    1.402321] Loaded X.509 cert 'Magrathea: Glacier signing key: 720f95eab0ea3a33b3bedee1ee3ae788f51cae26'
[    1.412717] registered taskstats version 1
[    1.424544] Key type trusted registered
[    1.437819] Key type encrypted registered
[    1.446302] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.458703] AppArmor: AppArmor sha1 policy hashing enabled
[    1.469152] ima: No TPM chip found, activating TPM-bypass!
[    1.479596] evm: HMAC attrs: 0x1
[    1.490179]   Magic number: 11:403:378
[    1.500496] rtc_cmos 00:02: setting system clock to 2015-04-19 11:21:21 UTC (1429442481)
[    1.511210] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.521685] EDD information not available.
[    1.532270] PM: Hibernation image not present or could not be loaded.
[    1.532901] Freeing unused kernel memory: 1360K (ffffffff81d2d000 - ffffffff81e81000)
[    1.543719] Write protecting the kernel read-only data: 12288k
[    1.555294] Freeing unused kernel memory: 432K (ffff880001794000 - ffff880001800000)
[    1.567102] Freeing unused kernel memory: 484K (ffff880001b87000 - ffff880001c00000)
[    1.570335] tsc: Refined TSC clocksource calibration: 3392.329 MHz
[    1.606660] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.617756] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.629260] systemd-udevd[146]: starting version 208
[    1.629337] hub 2-1:1.0: USB hub found
[    1.629414] hub 2-1:1.0: 6 ports detected
[    1.663483] random: systemd-udevd urandom read with 8 bits of entropy available
[    1.685978] pps_core: LinuxPPS API ver. 1 registered
[    1.697763] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.702450] usb 1-1.1: new low-speed USB device number 3 using ehci-pci
[    1.721239] ahci 0000:00:1f.2: version 3.0
[    1.721353] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.721959] [drm] Initialized drm 1.1.0 20060810
[    1.721979] PTP clock support registered
[    1.734418] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x30 impl SATA mode
[    1.734419] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.742875] scsi0 : ahci
[    1.743017] scsi1 : ahci
[    1.743106] scsi2 : ahci
[    1.743184] scsi3 : ahci
[    1.743259] scsi4 : ahci
[    1.743331] scsi5 : ahci
[    1.743356] ata1: DUMMY
[    1.743357] ata2: DUMMY
[    1.743357] ata3: DUMMY
[    1.743357] ata4: DUMMY
[    1.743359] ata5: SATA max UDMA/133 abar m2048@0xf7f26000 port 0xf7f26300 irq 42
[    1.743361] ata6: SATA max UDMA/133 abar m2048@0xf7f26000 port 0xf7f26380 irq 42
[    1.798236] usb 1-1.1: New USB device found, idVendor=0461, idProduct=4d22
[    1.798237] usb 1-1.1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    1.798238] usb 1-1.1: Product: USB Optical Mouse
[    1.870528] usb 1-1.2: new low-speed USB device number 4 using ehci-pci
[    1.951725] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    1.962413] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    1.972907] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.979317] usb 1-1.2: New USB device found, idVendor=413c, idProduct=2107
[    1.979318] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.979319] usb 1-1.2: Product: Dell USB Entry Keyboard
[    1.979320] usb 1-1.2: Manufacturer: Dell
[    2.026487] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    2.037495] [drm] radeon kernel modesetting enabled.
[    2.048619] checking generic (e0000000 300000) vs hw (e0000000 10000000)
[    2.048620] fb: switching to radeondrmfb from VESA VGA
[    2.050603] usb 1-1.4: new full-speed USB device number 5 using ehci-pci
[    2.062561] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.063214] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.063216] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.063217] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.063702] ata6.00: ATA-8: ST1000DM003-1CH162, CC46, max UDMA/133
[    2.063703] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.064254] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.064255] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.064256] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.064712] ata6.00: configured for UDMA/133
[    2.066573] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.069783] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.069785] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.069786] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.070795] ata5.00: ATAPI: HL-DT-ST DVDRAM GH24NS95, RN01, max UDMA/133
[    2.072651] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.072652] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.072653] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.074134] ata5.00: configured for UDMA/133
[    2.076409] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS95  RN01 PQ: 0 ANSI: 5
[    2.148147] usb 1-1.4: New USB device found, idVendor=045e, idProduct=028e
[    2.148148] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.148149] usb 1-1.4: Product: Controller
[    2.148149] usb 1-1.4: Manufacturer: ©Microsoft Corporation
[    2.148150] usb 1-1.4: SerialNumber: 0968AE6
[    2.292530] e1000e 0000:00:19.0 eth0: registered PHC clock
[    2.292541] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 70:54:d2:c4:5c:ab
[    2.292542] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.292573] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    2.341855] Console: switching to colour dummy device 80x25
[    2.341933] hidraw: raw HID events driver (C) Jiri Kosina
[    2.342078] [drm] initializing kernel modesetting (PITCAIRN 0x1002:0x6819 0x1458:0x2553).
[    2.342087] [drm] register mmio base: 0xF7E00000
[    2.342088] [drm] register mmio size: 262144
[    2.342130] ATOM BIOS: GV
[    2.342188] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[    2.342190] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[    2.342192] [drm] Detected VRAM RAM=2048M, BAR=256M
[    2.342193] [drm] RAM width 256bits DDR
[    2.342237] [TTM] Zone  kernel: Available graphics memory: 2007040 kiB
[    2.342239] [TTM] Initializing pool allocator
[    2.342243] [TTM] Initializing DMA pool allocator
[    2.342255] [drm] radeon: 2048M of VRAM memory ready
[    2.342256] [drm] radeon: 1024M of GTT memory ready.
[    2.342262] [drm] Loading PITCAIRN Microcode
[    2.342314] [drm] radeon/PITCAIRN_mc2.bin: 31100 bytes
[    2.342334] [drm] Internal thermal controller with fan control
[    2.342366] [drm] probing gen 2 caps for device 8086:151 = 261ad03/e
[    2.349427] usbcore: registered new interface driver usbhid
[    2.349430] usbhid: USB HID core driver
[    2.349496] [drm] radeon: dpm initialized
[    2.349604] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    2.350283] [drm] probing gen 2 caps for device 8086:151 = 261ad03/e
[    2.350288] [drm] PCIE gen 3 link speeds already enabled
[    2.350609] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/0003:0461:4D22.0001/input/input5
[    2.350796] hid-generic 0003:0461:4D22.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.0-1.1/input0
[    2.350890] input: Dell Dell USB Entry Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:413C:2107.0002/input/input6
[    2.350975] hid-generic 0003:413C:2107.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Entry Keyboard] on usb-0000:00:1a.0-1.2/input0
[    2.355005] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.355008] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.355177] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.355292] sr 4:0:0:0: Attached scsi generic sg0 type 5
[    2.355570] scsi 5:0:0:0: Direct-Access     ATA      ST1000DM003-1CH1 CC46 PQ: 0 ANSI: 5
[    2.355836] sd 5:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.355840] sd 5:0:0:0: [sda] 4096-byte physical blocks
[    2.355891] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    2.356050] sd 5:0:0:0: [sda] Write Protect is off
[    2.356052] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.356124] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.358745] usb 2-1-port1: over-current condition
[    2.359937] [drm] PCIE GART of 1024M enabled (table at 0x0000000000276000).
[    2.360042] radeon 0000:01:00.0: WB enabled
[    2.360045] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff880034880c00
[    2.360047] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff880034880c04
[    2.360049] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff880034880c08
[    2.360051] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff880034880c0c
[    2.360053] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff880034880c10
[    2.360667] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90004b35a18
[    2.360670] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.360671] [drm] Driver supports precise vblank timestamp query.
[    2.360672] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    2.360686] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[    2.360692] radeon 0000:01:00.0: radeon: using MSI.
[    2.360716] [drm] radeon: irq initialized.
[    2.401470]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.402199] sd 5:0:0:0: [sda] Attached SCSI disk
[    2.516853] [drm] ring test on 0 succeeded in 4 usecs
[    2.516858] [drm] ring test on 1 succeeded in 1 usecs
[    2.516862] [drm] ring test on 2 succeeded in 1 usecs
[    2.516872] [drm] ring test on 3 succeeded in 6 usecs
[    2.516880] [drm] ring test on 4 succeeded in 5 usecs
[    2.566838] usb 2-1-port2: over-current condition
[    2.702550] Switched to clocksource tsc
[    2.702561] [drm] ring test on 5 succeeded in 2 usecs
[    2.702568] [drm] UVD initialized successfully.
[    2.702787] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.702837] [drm] ib test on ring 1 succeeded in 0 usecs
[    2.702892] [drm] ib test on ring 2 succeeded in 0 usecs
[    2.702944] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.702985] [drm] ib test on ring 4 succeeded in 0 usecs
[    2.853976] [drm] ib test on ring 5 succeeded
[    2.854636] [drm] Radeon Display Connectors
[    2.854638] [drm] Connector 0:
[    2.854639] [drm]   DP-1
[    2.854640] [drm]   HPD4
[    2.854641] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    2.854642] [drm]   Encoders:
[    2.854643] [drm]     DFP1: INTERNAL_UNIPHY2
[    2.854644] [drm] Connector 1:
[    2.854645] [drm]   DP-2
[    2.854646] [drm]   HPD5
[    2.854647] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    2.854648] [drm]   Encoders:
[    2.854649] [drm]     DFP2: INTERNAL_UNIPHY2
[    2.854650] [drm] Connector 2:
[    2.854651] [drm]   HDMI-A-1
[    2.854651] [drm]   HPD1
[    2.854652] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[    2.854654] [drm]   Encoders:
[    2.854654] [drm]     DFP3: INTERNAL_UNIPHY1
[    2.854655] [drm] Connector 3:
[    2.854656] [drm]   DVI-I-1
[    2.854657] [drm]   HPD6
[    2.854658] [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
[    2.854659] [drm]   Encoders:
[    2.854660] [drm]     DFP4: INTERNAL_UNIPHY
[    2.854661] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.902896] [drm] fb mappable at 0xE0478000
[    2.902898] [drm] vram apper at 0xE0000000
[    2.902899] [drm] size 4325376
[    2.902900] [drm] fb depth is 24
[    2.902901] [drm]    pitch is 5632
[    2.902964] fbcon: radeondrmfb (fb0) is primary device
[    2.907002] usb 2-1-port3: over-current condition
[    2.911393] Console: switching to colour frame buffer device 170x48
[    2.912889] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    2.912904] radeon 0000:01:00.0: registered panic notifier
[    2.919002] [drm] Initialized radeon 2.39.0 20080528 for 0000:01:00.0 on minor 0
[    3.115102] usb 2-1-port4: over-current condition
[    4.703885] floppy0: no floppy controllers found
[    4.868740] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    5.269396] random: nonblocking pool is initialized
[   15.877454] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   16.519905] Adding 4194300k swap on /swapfile.  Priority:-1 extents:7 across:6553596k FS
[   16.522747] systemd-udevd[448]: starting version 208
[   16.686853] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.688810] mei_me 0000:00:16.0: irq 45 for MSI/MSI-X
[   16.694746] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
[   16.694752] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.694756] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   16.694758] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.694759] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   16.694762] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.694763] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   16.694765] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.694766] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   16.710109] systemd-udevd[499]: renamed network interface eth0 to eth1
[   16.716260] AVX version of gcm_enc/dec engaged.
[   16.740144] intel_rapl: Found RAPL domain package
[   16.740147] intel_rapl: Found RAPL domain core
[   16.747249] ppdev: user-space parallel port driver
[   16.748420] lp: driver loaded but no devices found
[   16.768644] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   16.768710] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.768712] snd_hda_intel 0000:01:00.1: Force to non-snoop mode
[   16.768770] snd_hda_intel 0000:01:00.1: irq 47 for MSI/MSI-X
[   16.777506] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input7
[   16.777564] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   16.777612] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   16.777652] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   16.777704] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   16.777764] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   16.780441] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   16.780444] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.780446] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   16.780448] sound hdaudioC0D0:    mono: mono_out=0x0
[   16.780449] sound hdaudioC0D0:    dig-out=0x11/0x0
[   16.780451] sound hdaudioC0D0:    inputs:
[   16.780453] sound hdaudioC0D0:      Front Mic=0x19
[   16.780455] sound hdaudioC0D0:      Rear Mic=0x18
[   16.780457] sound hdaudioC0D0:      Line=0x1a
[   16.790556] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   16.790607] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   16.790652] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   16.922121] audit: type=1400 audit(1429422696.911:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=575 comm="apparmor_parser"
[   16.922126] audit: type=1400 audit(1429422696.911:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=575 comm="apparmor_parser"
[   16.922128] audit: type=1400 audit(1429422696.911:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=575 comm="apparmor_parser"
[   16.922134] audit: type=1400 audit(1429422696.911:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=572 comm="apparmor_parser"
[   16.922139] audit: type=1400 audit(1429422696.911:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=572 comm="apparmor_parser"
[   16.922141] audit: type=1400 audit(1429422696.911:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=572 comm="apparmor_parser"
[   18.019412] init: Error while reading from descriptor: Broken pipe
[   18.020385] init: failsafe main process (774) killed by TERM signal
[   18.147716] input: Microsoft X-Box 360 pad as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input16
[   18.147774] usbcore: registered new interface driver xpad
[   18.574571] audit: type=1400 audit(1429422698.563:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=854 comm="apparmor_parser"
[   18.574576] audit: type=1400 audit(1429422698.563:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=854 comm="apparmor_parser"
[   18.575536] audit: type=1400 audit(1429422698.563:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=854 comm="apparmor_parser"
[   18.575540] audit: type=1400 audit(1429422698.563:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=854 comm="apparmor_parser"
[   18.996187] init: cups main process (891) killed by HUP signal
[   18.996194] init: cups main process ended, respawning
[   19.186054] Bluetooth: Core ver 2.19
[   19.186064] NET: Registered protocol family 31
[   19.186065] Bluetooth: HCI device and connection manager initialized
[   19.186070] Bluetooth: HCI socket layer initialized
[   19.186071] Bluetooth: L2CAP socket layer initialized
[   19.186076] Bluetooth: SCO socket layer initialized
[   19.194601] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.194603] Bluetooth: BNEP filters: protocol multicast
[   19.194605] Bluetooth: BNEP socket layer initialized
[   19.214470] Bluetooth: RFCOMM TTY layer initialized
[   19.214475] Bluetooth: RFCOMM socket layer initialized
[   19.214478] Bluetooth: RFCOMM ver 1.11
[   19.702968] floppy0: no floppy controllers found
[   20.187473] init: samba-ad-dc main process (985) terminated with status 1
[   20.253673] systemd-logind[1095]: New seat seat0.
[   20.263543] systemd-logind[1095]: Watching system buttons on /dev/input/event1 (Power Button)
[   20.263579] systemd-logind[1095]: Watching system buttons on /dev/input/event0 (Power Button)
[   20.503943] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   20.607323] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   22.171876] init: gdm main process (1378) killed by TERM signal
[   22.553751] systemd-logind[1095]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   22.553756] systemd-logind[1095]: Failed to start user service: Unknown unit: user@1000.service
[   22.556280] systemd-logind[1095]: New session c1 of user kumaresh.
[   22.556291] systemd-logind[1095]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   24.702343] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   24.702348] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[   27.590408] init: /etc/init/plymouth-upstart-bridge.conf:18: Unknown stanza

```
For some reason, There's a huge delay in the mounting of the Hard drive ( from 5 to 16 seconds ). Is this a bug or is there something wrong with my hard drive ? 
PS: One more thing, at 27 seconds, there's this line 
```
[   27.590408] init: /etc/init/plymouth-upstart-bridge.conf:18: Unknown stanza
```
I've never got this error code until I upgraded from 14.04 to 14.10.

---

### Post by dino99 on 2015-04-19
so edit it to see what is written on that line 18  (/etc/init/plymouth-upstart-bridge.conf:18)

---

