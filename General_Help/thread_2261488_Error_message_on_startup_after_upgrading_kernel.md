---
title: "Error message on startup after upgrading kernel"
date: 2015-01-19
forum: General Help
---

### Post by harry28 on 2015-01-19
I installed Linux Ubuntu 14.10 on my Acer C720 chromebook a couple of months ago and it has been running fine. Recently the system started to hang and freeze, sometimes it would recover from it and sometimes I would have to force shutdown. I fixed this (I think) by upgrading the kernel from 3.18 to 3.19. However now when it boots up it comes up with: 

```
1.8406921] usb 1-4: language id specifier not provided by device, defaulting to English
```

The system boots fine, however I was wondering what this is about and if there is anyway to remove?. This is the output from dmesg (not sure if this is going to help):

```
[    0.143915] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.143946] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.143995] system 00:04: [io  0x0900-0x09fe] has been reserved
[    0.143998] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.144048] system 00:05: [io  0x0200] has been reserved
[    0.144050] system 00:05: [io  0x0204] has been reserved
[    0.144053] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.144055] system 00:05: [io  0x0880-0x08ff] has been reserved
[    0.144058] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.144104] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.144144] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.144192] pnp 00:08: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    0.144301] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.144428] pnp: PnP ACPI: found 10 devices
[    0.151356] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.151364] pci 0000:00:1c.0:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.151374] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.151377] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.151379] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.151381] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.151383] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.151386] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.151388] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.151390] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.151392] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.151395] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.151397] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.151399] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.151401] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.151403] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.151405] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff]
[    0.151408] pci_bus 0000:00: resource 19 [mem 0x7ea00001-0xfebfffff]
[    0.151410] pci_bus 0000:00: resource 20 [mem 0xfed40000-0xfed44fff]
[    0.151413] pci_bus 0000:01: resource 1 [mem 0xe0400000-0xe04fffff]
[    0.151453] NET: Registered protocol family 2
[    0.151654] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.151706] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.151753] TCP: Hash tables configured (established 16384 bind 16384)
[    0.151778] TCP: reno registered
[    0.151788] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.151800] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.151854] NET: Registered protocol family 1
[    0.151873] pci 0000:00:02.0: Video device with shadowed ROM
[    0.152378] PCI: CLS 64 bytes, default 64
[    0.152446] Trying to unpack rootfs image as initramfs...
[    0.634125] Freeing initrd memory: 18592K (ffff880035ba0000 - ffff880036dc8000)
[    0.634163] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.634167] software IO TLB [mem 0x75800000-0x79800000] (64MB) mapped at [ffff880075800000-ffff8800797fffff]
[    0.634351] RAPL PMU detected, hw unit 2^-14 Joules, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.634424] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x15
[    0.634433] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x15
[    0.634498] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.634538] Scanning for low memory corruption every 60 seconds
[    0.634955] futex hash table entries: 512 (order: 3, 32768 bytes)
[    0.634977] Initialise system trusted keyring
[    0.635010] audit: initializing netlink subsys (disabled)
[    0.635027] audit: type=2000 audit(1421673532.624:1): initialized
[    0.635549] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.637644] zpool: loaded
[    0.637647] zbud: loaded
[    0.637881] VFS: Disk quotas dquot_6.5.2
[    0.637934] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.638551] fuse init (API version 7.23)
[    0.638748] Key type big_key registered
[    0.639190] Key type asymmetric registered
[    0.639195] Asymmetric key parser 'x509' registered
[    0.639250] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.639289] io scheduler noop registered
[    0.639294] io scheduler deadline registered (default)
[    0.639337] io scheduler cfq registered
[    0.639742] aer 0000:00:1c.0:pcie02: service driver aer loaded
[    0.639764] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.639766] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.639771] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.639779] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.639800] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.639842] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    0.639844] vesafb: scrolling: redraw
[    0.639846] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.639869] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90004400000, using 4160k, total 4160k
[    0.643422] Console: switching to colour frame buffer device 170x48
[    0.646807] fb0: VESA VGA frame buffer device
[    0.646831] intel_idle: MWAIT substates: 0x11142120
[    0.646833] intel_idle: v0.4 model 0x45
[    0.646835] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.647094] ACPI: AC Adapter [AC] (off-line)
[    0.647206] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.647235] ACPI: Lid Switch [LID0]
[    0.647285] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.647290] ACPI: Power Button [PWRB]
[    0.647336] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.647339] ACPI: Sleep Button [TPAD]
[    0.647394] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:01/input/input3
[    0.647397] ACPI: Sleep Button [TSCR]
[    0.647457] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[    0.647460] ACPI: Power Button [PWRF]
[    0.648818] thermal LNXTHERM:00: registered as thermal_zone0
[    0.648822] ACPI: Thermal Zone [THRM] (42 C)
[    0.648889] GHES: HEST is not enabled!
[    0.649338] ACPI: Battery Slot [BAT0] (battery present)
[    0.649404] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.651576] Linux agpgart interface v0.103
[    0.651899] tpm_tis 00:08: 1.2 TPM (device-id 0xB, rev-id 16)
[    0.910040] brd: module loaded
[    0.910843] loop: module loaded
[    0.911140] libphy: Fixed MDIO Bus: probed
[    0.911146] tun: Universal TUN/TAP device driver, 1.6
[    0.911147] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.911205] PPP generic driver version 2.4.2
[    0.911479] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.911488] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.911580] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.911670] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.911673] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.911675] usb usb1: Product: xHCI Host Controller
[    0.911677] usb usb1: Manufacturer: Linux 3.19.0-031900rc3-generic xhci-hcd
[    0.911679] usb usb1: SerialNumber: 0000:00:14.0
[    0.911821] hub 1-0:1.0: USB hub found
[    0.911834] hub 1-0:1.0: 8 ports detected
[    0.912132] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.912136] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.912177] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.912179] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.912181] usb usb2: Product: xHCI Host Controller
[    0.912183] usb usb2: Manufacturer: Linux 3.19.0-031900rc3-generic xhci-hcd
[    0.912185] usb usb2: SerialNumber: 0000:00:14.0
[    0.912311] hub 2-0:1.0: USB hub found
[    0.912322] hub 2-0:1.0: 4 ports detected
[    0.912508] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.912517] ehci-pci: EHCI PCI platform driver
[    0.912676] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.912683] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    0.912696] ehci-pci 0000:00:1d.0: debug port 2
[    0.916594] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.916612] ehci-pci 0000:00:1d.0: irq 19, io mem 0xe051f800
[    0.927312] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.927364] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.927367] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.927369] usb usb3: Product: EHCI Host Controller
[    0.927371] usb usb3: Manufacturer: Linux 3.19.0-031900rc3-generic ehci_hcd
[    0.927373] usb usb3: SerialNumber: 0000:00:1d.0
[    0.927540] hub 3-0:1.0: USB hub found
[    0.927547] hub 3-0:1.0: 2 ports detected
[    0.927682] ehci-platform: EHCI generic platform driver
[    0.927698] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.927705] ohci-pci: OHCI PCI platform driver
[    0.927721] ohci-platform: OHCI generic platform driver
[    0.927733] uhci_hcd: USB Universal Host Controller Interface driver
[    0.927816] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.927817] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.928356] i8042: Warning: Keylock active
[    0.928493] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.928676] mousedev: PS/2 mouse device common for all mice
[    0.929087] rtc_cmos 00:03: RTC can wake from S4
[    0.929225] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.929255] rtc_cmos 00:03: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.929369] device-mapper: uevent: version 1.0.3
[    0.929475] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    0.929506] Intel P-state driver initializing.
[    0.929585] ledtrig-cpu: registered to indicate activity on CPUs
[    0.929862] TCP: cubic registered
[    0.930018] NET: Registered protocol family 10
[    0.930370] NET: Registered protocol family 17
[    0.930387] Key type dns_resolver registered
[    0.930849] Loading compiled-in X.509 certificates
[    0.932052] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.932174] Loaded X.509 cert 'Magrathea: Glacier signing key: 896c69cb6b216abcae9d9e5859b461e29bfd3cec'
[    0.932196] registered taskstats version 1
[    0.934722] Key type trusted registered
[    0.938939] Key type encrypted registered
[    0.938951] AppArmor: AppArmor sha1 policy hashing enabled
[    1.223336] usb 1-3: new high-speed USB device number 2 using xhci_hcd
[    1.239340] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.371937] usb 3-1: New USB device found, idVendor=8087, idProduct=8000
[    1.371943] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.372350] hub 3-1:1.0: USB hub found
[    1.372544] hub 3-1:1.0: 8 ports detected
[    1.476462] usb 1-3: New USB device found, idVendor=1bcf, idProduct=2c67
[    1.476467] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.476470] usb 1-3: Product: HD WebCam
[    1.476473] usb 1-3: Manufacturer: NC.21411.02440900356LM0001
[    1.631249] tsc: Refined TSC clocksource calibration: 1396.766 MHz
[    1.711256] usb 1-4: new full-speed USB device number 3 using xhci_hcd
[    1.840692] usb 1-4: language id specifier not provided by device, defaulting to English
[    1.842623] usb 1-4: New USB device found, idVendor=0489, idProduct=e056
[    1.842626] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.955214] usb 1-5: new full-speed USB device number 4 using xhci_hcd
[    2.085462] usb 1-5: New USB device found, idVendor=046d, idProduct=c52f
[    2.085467] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.085470] usb 1-5: Product: USB Receiver
[    2.085473] usb 1-5: Manufacturer: Logitech
[    2.631258] Switched to clocksource tsc
[   53.742674] evm: HMAC attrs: 0x1
[   53.742982]   Magic number: 15:46:332
[   53.743016] tty tty53: hash matches
[   53.743102] rtc_cmos 00:03: setting system clock to 2015-01-19 13:19:46 UTC (1421673586)
[   53.743171] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   53.743172] EDD information not available.
[   53.743269] PM: Hibernation image not present or could not be loaded.
[   53.743682] Freeing unused kernel memory: 1404K (ffffffff81d26000 - ffffffff81e85000)
[   53.743684] Write protecting the kernel read-only data: 12288k
[   53.743986] Freeing unused kernel memory: 152K (ffff8800017da000 - ffff880001800000)
[   53.744101] Freeing unused kernel memory: 252K (ffff880001bc1000 - ffff880001c00000)
[   53.759843] systemd-udevd[106]: starting version 208
[   53.760443] random: systemd-udevd urandom read with 5 bits of entropy available
[   53.788508] sdhci: Secure Digital Host Controller Interface driver
[   53.788512] sdhci: Copyright(c) Pierre Ossman
[   53.802387] hidraw: raw HID events driver (C) Jiri Kosina
[   53.802977] ahci 0000:00:1f.2: version 3.0
[   53.803179] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[   53.809800] usbcore: registered new interface driver usbhid
[   53.809805] usbhid: USB HID core driver
[   53.819485] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x1 impl SATA mode
[   53.819492] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo only pio slum part deso sadm sds apst 
[   53.827506] scsi host0: ahci
[   53.832138] scsi host1: ahci
[   53.832225] ata1: SATA max UDMA/133 abar m2048@0xe051f000 port 0xe051f100 irq 42
[   53.832228] ata2: DUMMY
[   53.836382] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/0003:046D:C52F.0001/input/input6
[   53.836606] hid-generic 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-5/input0
[   53.837523] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.1/0003:046D:C52F.0002/input/input7
[   53.890865] hid-generic 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-5/input1
[   54.150513] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   54.150738] ata1.00: ATA-10: KINGSTON SNS4151S316G, S9FM01.1, max UDMA/100
[   54.150743] ata1.00: 31277232 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[   54.151100] ata1.00: configured for UDMA/100
[   54.151277] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SNS4151 01.1 PQ: 0 ANSI: 5
[   54.151636] sd 0:0:0:0: [sda] 31277232 512-byte logical blocks: (16.0 GB/14.9 GiB)
[   54.151676] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   54.151687] sd 0:0:0:0: [sda] Write Protect is off
[   54.151691] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.151708] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.154089]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12
[   54.154940] sd 0:0:0:0: [sda] Attached SCSI disk
[   54.210204] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   54.373438] init: plymouth-upstart-bridge main process (160) terminated with status 1
[   54.373452] init: plymouth-upstart-bridge main process ended, respawning
[   54.381489] init: ureadahead main process (162) terminated with status 5
[   54.515403] EXT4-fs (sda7): re-mounted. Opts: (null)
[   54.767793] systemd-udevd[313]: starting version 208
[   54.944735] lp: driver loaded but no devices found
[   54.962922] ppdev: user-space parallel port driver
[   55.079899] dw_dmac_pci 0000:00:15.0: Unbalanced pm_runtime_enable!
[   55.080121] dw_dmac_pci 0000:00:15.0: DesignWare DMA Controller, 8 channels
[   55.085200] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   55.092346] [drm] Initialized drm 1.1.0 20060810
[   55.153956] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   55.154182] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   55.291587] Bluetooth: Core ver 2.20
[   55.291640] NET: Registered protocol family 31
[   55.291643] Bluetooth: HCI device and connection manager initialized
[   55.291648] Bluetooth: HCI socket layer initialized
[   55.291652] Bluetooth: L2CAP socket layer initialized
[   55.291660] Bluetooth: SCO socket layer initialized
[   55.302441] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   55.302446] Bluetooth: BNEP filters: protocol multicast
[   55.302452] Bluetooth: BNEP socket layer initialized
[   55.330266] Bluetooth: RFCOMM TTY layer initialized
[   55.330277] Bluetooth: RFCOMM socket layer initialized
[   55.330285] Bluetooth: RFCOMM ver 1.11
[   55.441869] sound hdaudioC1D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   55.441875] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   55.441878] sound hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   55.441880] sound hdaudioC1D0:    mono: mono_out=0x0
[   55.441882] sound hdaudioC1D0:    inputs:
[   55.441885] sound hdaudioC1D0:      Internal Mic=0x1a
[   55.441888] sound hdaudioC1D0:      Mic=0x19
[   55.454083] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
[   55.454213] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[   55.465797] usbcore: registered new interface driver btusb
[   55.557992] usbcore: registered new interface driver ath3k
[   55.558514] media: Linux media interface: v0.10
[   55.583586] Linux video capture interface: v2.00
[   55.598755] cfg80211: Calling CRDA to update world regulatory domain
[   55.600616] [drm] Memory usable by graphics device = 2048M
[   55.600621] checking generic (d0000000 410000) vs hw (d0000000 10000000)
[   55.600624] fb: switching to inteldrmfb from VESA VGA
[   55.600649] Console: switching to colour dummy device 80x25
[   55.600734] [drm] Replacing VGA console driver
[   55.602936] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   55.602940] [drm] Driver supports precise vblank timestamp query.
[   55.603031] [drm] applying backlight present quirk
[   55.603056] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   55.645250] uvcvideo: Found UVC 1.00 device HD WebCam (1bcf:2c67)
[   55.656813] input: HD WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input11
[   55.657000] usbcore: registered new interface driver uvcvideo
[   55.657005] USB Video Class driver (1.1.1)
[   55.720929] ath: phy0: ASPM enabled: 0x43
[   55.720935] ath: EEPROM regdomain: 0x6c
[   55.720936] ath: EEPROM indicates we should expect a direct regpair map
[   55.720939] ath: Country alpha2 being used: 00
[   55.720941] ath: Regpair used: 0x6c
[   55.744354] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
[   55.746526] fbcon: inteldrmfb (fb0) is primary device
[   55.774720] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   55.779669] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input12
[   55.779798] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input13
[   55.779921] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[   55.780220] ieee80211 phy0: Atheros AR9462 Rev:2 mem=0xffffc90004900000, irq=16
[   55.788996] intel_rapl: Found RAPL domain package
[   55.788999] intel_rapl: Found RAPL domain core
[   55.789002] intel_rapl: Found RAPL domain uncore
[   55.789004] intel_rapl: Found RAPL domain dram
[   55.846237] __add_probed_i2c_device failed to register device 1-4a
[   55.863967] platform chromeos_laptop: Driver chromeos_laptop requests probe deferral
[   55.899450] cfg80211: World regulatory domain updated:
[   55.899452] cfg80211:  DFS Master region: unset
[   55.899452] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   55.899455] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   55.899457] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   55.899458] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   55.899459] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   55.899460] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   55.909772] input: Cypress APA Trackpad (cyapa) as /devices/pci0000:00/0000:00:15.1/i2c-0/0-0067/input/input15
[   55.911057] __add_probed_i2c_device failed to register device 1-4a
[   55.911066] platform chromeos_laptop: Driver chromeos_laptop requests probe deferral
[   55.919814] isl29018: module is from the staging directory, the quality is unknown, you have been warned.
[   55.920146] isl29018 1-0044: No cache defaults, reading back from HW
[   55.924664] __add_probed_i2c_device failed to register device 1-4a
[   55.924671] platform chromeos_laptop: Driver chromeos_laptop requests probe deferral
[   56.826122] Console: switching to colour frame buffer device 170x48
[   56.829755] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   56.829757] i915 0000:00:02.0: registered panic notifier
[   57.217263] init: failsafe main process (587) killed by TERM signal
[   57.713582] systemd-logind[763]: New seat seat0.
[   57.714763] systemd-logind[763]: Watching system buttons on /dev/input/event4 (Power Button)
[   57.714838] systemd-logind[763]: Watching system buttons on /dev/input/event8 (Video Bus)
[   57.714905] systemd-logind[763]: Watching system buttons on /dev/input/event1 (Power Button)
[   57.714968] systemd-logind[763]: Watching system buttons on /dev/input/event0 (Lid Switch)
[   57.715029] systemd-logind[763]: Watching system buttons on /dev/input/event2 (Sleep Button)
[   57.715091] systemd-logind[763]: Watching system buttons on /dev/input/event3 (Sleep Button)
[   57.745977] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.108401] random: nonblocking pool is initialized
[   58.850352] init: plymouth-upstart-bridge main process ended, respawning
[   58.859844] init: plymouth-upstart-bridge main process (1154) terminated with status 1
[   58.910394] systemd-logind[763]: Failed to start unit user@111.service: Unknown unit: user@111.service
[   58.910403] systemd-logind[763]: Failed to start user service: Unknown unit: user@111.service
[   58.916113] systemd-logind[763]: New session c1 of user lightdm.
[   58.916140] systemd-logind[763]: Linked /tmp/.X11-unix/X0 to /run/user/111/X11-display.
[   60.168918] init: anacron main process (928) killed by TERM signal
[   61.334234] systemd-logind[763]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   61.334244] systemd-logind[763]: Failed to start user service: Unknown unit: user@1000.service
[   61.341608] systemd-logind[763]: New session c2 of user user.
[   61.341636] systemd-logind[763]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   68.229062] wlan0: authenticate with 08:ea:44:93:88:28
[   68.242356] wlan0: send auth to 08:ea:44:93:88:28 (try 1/3)
[   68.245975] wlan0: authenticated
[   68.252557] wlan0: associate with 08:ea:44:93:88:28 (try 1/3)
[   68.254269] wlan0: RX AssocResp from 08:ea:44:93:88:28 (capab=0x411 status=0 aid=3)
[   68.254351] wlan0: associated
[   68.254375] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   68.254431] cfg80211: Calling CRDA for country: GB
[   68.257333] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by 08:ea:44:93:88:28
[   68.276215] ath: EEPROM regdomain: 0x833a
[   68.276220] ath: EEPROM indicates we should expect a country code
[   68.276222] ath: doing EEPROM country->regdmn map search
[   68.276224] ath: country maps to regdmn code: 0x37
[   68.276226] ath: Country alpha2 being used: GB
[   68.276227] ath: Regpair used: 0x37
[   68.276229] ath: regdomain 0x833a dynamically updated by country IE
[   68.276253] cfg80211: Regulatory domain changed to country: GB
[   68.276254] cfg80211:  DFS Master region: unset
[   68.276256] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   68.276259] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   68.276261] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   68.276264] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
[   68.276266] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
[   68.276268] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[   68.362021] wlan0: deauthenticating from 08:ea:44:93:88:28 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   68.368092] cfg80211: Calling CRDA to update world regulatory domain
[   68.368796] wlan0: authenticate with 08:ea:44:93:88:28
[   68.380893] wlan0: send auth to 08:ea:44:93:88:28 (try 1/3)
[   68.381874] wlan0: authenticated
[   68.382050] cfg80211: World regulatory domain updated:
[   68.382053] cfg80211:  DFS Master region: unset
[   68.382055] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   68.382059] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   68.382061] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   68.382064] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   68.382066] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   68.382068] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   68.384140] wlan0: associate with 08:ea:44:93:88:28 (try 1/3)
[   68.386622] wlan0: RX AssocResp from 08:ea:44:93:88:28 (capab=0x411 status=0 aid=3)
[   68.386721] wlan0: associated
[   68.386915] cfg80211: Calling CRDA for country: GB
[   68.391031] ath: EEPROM regdomain: 0x833a
[   68.391036] ath: EEPROM indicates we should expect a country code
[   68.391038] ath: doing EEPROM country->regdmn map search
[   68.391040] ath: country maps to regdmn code: 0x37
[   68.391042] ath: Country alpha2 being used: GB
[   68.391043] ath: Regpair used: 0x37
[   68.391089] ath: regdomain 0x833a dynamically updated by country IE
[   68.391111] cfg80211: Regulatory domain changed to country: GB
[   68.391113] cfg80211:  DFS Master region: unset
[   68.391115] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   68.391118] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   68.391120] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   68.391123] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
[   68.391125] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
[   68.391127] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[   68.462567] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by 08:ea:44:93:88:28
[   72.282608] chrome[2164]: segfault at 1f8 ip 00007f5fd3a6763f sp 00007fffb78d7df0 error 4 in i965_dri.so[7f5fd3714000+51c000]
[   72.645177] chrome[2251]: segfault at 1f8 ip 00007f5bc2a1863f sp 00007fffa6ad45a0 error 4 in i965_dri.so[7f5bc26c5000+51c000]
[   72.982761] chrome[2274]: segfault at 1f8 ip 00007f6407af863f sp 00007fff4f783820 error 4 in i965_dri.so[7f64077a5000+51c000]
[  306.211136] systemd-hostnamed[2712]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!



```

---

### Post by TheFu on 2015-01-19
i have a C720 too.
* kill any flash running in tabs.
* increase the swap space to 4G.
Doing this has solved the issue for me on 14.04.

---

### Post by harry28 on 2015-01-19
> **TheFu said:**
> i have a C720 too.
* kill any flash running in tabs.
* increase the swap space to 4G.
Doing this has solved the issue for me on 14.04.

Thanks for your reply. Is this for fixing the hang issue? If so I have already fixed it by upgrading the kernel. I was wondering how I can get rid of the usb error message on startup. Thanks anyway

---

### Post by TheFu on 2015-01-19
I'm not seeing any errors in my kernel messages/dmesg, but I only run LTS versions and would much prefer to use "stable" kernel releases, not the development branch. Both of us are on development branches .... odd numbers are dev.

Do you use chrome?

Posting the entire dmesg file will likely distract others. Best to edit it down to only the relevant sections.  IMHO.

---

