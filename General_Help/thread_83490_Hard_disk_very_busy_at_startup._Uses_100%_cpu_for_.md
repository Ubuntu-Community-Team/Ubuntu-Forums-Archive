---
title: "Hard disk very busy at startup. Uses 100% cpu for 5 mins."
date: 2005-10-28
forum: General Help
---

### Post by chessmani on 2005-10-28
After I get into desktop, sometimes hard disk seems to be extremely busy and uses 100% cpu and I can't do anything for about 5 minutes.

I think it has something to do with the graphics card (Intel Extreme Graphics 2), but I don't know how to solve the problem.

Here's the dmesg. Hope you can help me.

```
[4294669.870000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294669.870000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.874000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.874000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[4294669.875000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[4294669.875000] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[4294669.875000] ACPI: PCI Interrupt Link [LNKC] (IRQs *11)
[4294669.876000] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[4294669.876000] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[4294669.876000] ACPI: PCI Interrupt Link [LNKF] (IRQs *11)
[4294669.876000] ACPI: PCI Interrupt Link [LNKG] (IRQs 11) *0, disabled.
[4294669.877000] ACPI: PCI Interrupt Link [LNKH] (IRQs *11)
[4294669.877000] burst-mode-ec-10-Aug
[4294669.877000] ACPI: Embedded Controller [H_EC] (gpe 29)
[4294669.882000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.882000] pnp: PnP ACPI init
[4294669.885000] pnp: PnP ACPI: found 7 devices
[4294669.885000] PnPBIOS: Disabled by ACPI PNP
[4294669.885000] PCI: Using ACPI for IRQ routing
[4294669.885000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps
, post a report
[4294669.891000] Simple Boot Flag at 0x36 set to 0x1
[4294669.891000] audit: initializing netlink socket (disabled)
[4294669.891000] audit: initialized
[4294669.891000] VFS: Disk quotas dquot_6.5.1
[4294669.891000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.891000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.891000] devfs: boot_options: 0x0
[4294669.891000] Initializing Cryptographic API
[4294669.891000] isapnp: Scanning for PnP cards...
[4294670.246000] isapnp: No Plug & Play device found
[4294670.262000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PSM1] at 0x60,0x64 i
rq 1,12
[4294670.269000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.269000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.269000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ shari
ng enabled
[4294670.271000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294670.271000] PCI: setting IRQ 5 as level-triggered
[4294670.271000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (le
vel, low) -> IRQ 5
[4294670.271000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294670.271000] io scheduler noop registered
[4294670.271000] io scheduler anticipatory registered
[4294670.271000] io scheduler deadline registered
[4294670.271000] io scheduler cfq registered
[4294670.272000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl
ocksize
[4294670.273000] EISA: Probing bus 0 at eisa.0
[4294670.273000] Cannot allocate resource for EISA slot 1
[4294670.273000] Cannot allocate resource for EISA slot 2
[4294670.273000] Cannot allocate resource for EISA slot 3
[4294670.273000] EISA: Detected 0 cards.
[4294670.273000] NET: Registered protocol family 2
[4294670.283000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294670.283000] TCP established hash table entries: 16384 (order: 5, 131072 byt
es)
[4294670.283000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.283000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.283000] NET: Registered protocol family 8
[4294670.283000] NET: Registered protocol family 20
[4294670.283000] ACPI wakeup devices:
[4294670.283000] BAT0  LAN PS2K PSM1 USB0 USB1 USB7
[4294670.283000] ACPI: (supports S0 S3 S4 S5)
[4294670.283000] Freeing unused kernel memory: 224k freed
[4294670.295000] vga16fb: initializing
[4294670.295000] vga16fb: mapped to 0xc00a0000
[4294670.413000] Console: switching to colour frame buffer device 80x30
[4294670.413000] fb0: VGA16 VGA frame buffer device
[4294670.429000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.514000] Capability LSM initialized
[4294671.522000] NET: Registered protocol family 1
[4294671.533000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.533000] ide: Assuming 33MHz system bus speed for PIO modes; override wi
th idebus=xx
[4294671.533000] ACPI: bus type ide registered
[4294671.537000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294671.537000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294671.538000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294671.538000] PCI: setting IRQ 11 as level-triggered
[4294671.538000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (l
evel, low) -> IRQ 11
[4294671.538000] ICH4: chipset revision 3
[4294671.538000] ICH4: not 100% native mode: will probe irqs later
[4294671.538000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:
pio
[4294671.538000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:
pio
[4294671.538000] Probing IDE interface ide0...
[4294671.802000] hda: ST94019A, ATA DISK drive
[4294672.414000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.414000] Probing IDE interface ide1...
[4294673.086000] hdc: DV-W24EW, ATAPI CD/DVD-ROM drive
[4294673.698000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.698000] Probing IDE interface ide2...
[4294674.211000] Probing IDE interface ide3...
[4294674.723000] Probing IDE interface ide4...
[4294675.235000] Probing IDE interface ide5...
[4294675.749000] hda: max request size: 1024KiB
[4294675.937000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=16383/255
/63, UDMA(100)
[4294675.937000] hda: cache flushes supported
[4294675.937000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 p6 >
[4294676.030000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2193kB Cache
[4294676.030000] Uniform CD-ROM driver Revision: 3.20
[4294676.226000] Attempting manual resume
[4294676.228000] swsusp: Suspend partition has wrong signature?
[4294676.267000] usbcore: registered new driver usbfs
[4294676.267000] usbcore: registered new driver hub
[4294676.268000] USB Universal Host Controller Interface driver v2.2
[4294676.268000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[4294676.268000] PCI: setting IRQ 10 as level-triggered
[4294676.268000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (l
evel, low) -> IRQ 10
[4294676.268000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294676.268000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801DB/DBL/DBM (ICH4/
ICH4-L/ICH4-M) USB UHCI Controller #1
[4294676.330000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus num
ber 1
[4294676.330000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001820
[4294676.330000] hub 1-0:1.0: USB hub found
[4294676.330000] hub 1-0:1.0: 2 ports detected
[4294676.333000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294676.333000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (l
evel, low) -> IRQ 11
[4294676.333000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294676.333000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801DB/DBL/DBM (ICH4/
ICH4-L/ICH4-M) USB UHCI Controller #2
[4294676.395000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus num
ber 2
[4294676.395000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[4294676.395000] hub 2-0:1.0: USB hub found
[4294676.395000] hub 2-0:1.0: 2 ports detected
[4294676.398000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (l
evel, low) -> IRQ 11
[4294676.398000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294676.398000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801DB/DBL/DBM (ICH4/
ICH4-L/ICH4-M) USB UHCI Controller #3
[4294676.460000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus num
ber 3
[4294676.460000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[4294676.460000] hub 3-0:1.0: USB hub found
[4294676.460000] hub 3-0:1.0: 2 ports detected
[4294676.484000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[4294676.484000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (l
evel, low) -> IRQ 11
[4294676.484000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294676.484000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801DB/DBM (ICH4/ICH4
-M) USB2 EHCI Controller
[4294676.484000] ehci_hcd 0000:00:1d.7: debug port 1
[4294676.484000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus num
ber 4
[4294676.484000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[4294676.488000] PCI: cache line size of 32 is not supported by device 0000:00:1
d.7
[4294676.488000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 1
0 Dec 2004
[4294676.488000] hub 4-0:1.0: USB hub found
[4294676.488000] hub 4-0:1.0: 6 ports detected
[4294676.553000] 8139too Fast Ethernet driver 0.9.27
[4294676.553000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (l
evel, low) -> IRQ 10
[4294676.553000] eth0: RealTek RTL8139 at 0x3000, 00:c0:9f:63:49:a5, IRQ 10
[4294676.553000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294676.554000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294676.999000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[4294678.588000] usbcore: registered new driver hiddev
[4294678.606000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on
usb-0000:00:1d.0-2
[4294678.606000] usbcore: registered new driver usbhid
[4294678.606000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294678.834000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294678.835000] ACPI: Thermal Zone [THRM] (32 C)
[4294679.277000] Attempting manual resume
[4294679.278000] swsusp: Suspend partition has wrong signature?
[4294679.285000] ReiserFS: hda3: found reiserfs format "3.6" with standard journ
al
[4294680.042000] ReiserFS: hda3: using ordered data mode
[4294680.056000] ReiserFS: hda3: journal params: device hda3, size 8192, journal
first block 18, max trans len 1024, max batch 900, max commit age 30, max trans
age 30
[4294680.057000] ReiserFS: hda3: checking transaction log (hda3)
[4294680.118000] ReiserFS: hda3: Using r5 hash to sort names
[4294681.872000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294686.327000] Adding 1004020k swap on /dev/hda6.  Priority:-1 extents:1
[4294698.700000] SCSI subsystem initialized
[4294698.734000] mice: PS/2 mouse device common for all mice
[4294698.766000] ieee1394: Initialized config rom entry `ip1394'
[4294698.770000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294698.795000] lp: driver loaded but no devices found
[4294698.831000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294699.299000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x90
4713/0x10008
[4294699.302000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294700.163000] ts: Compaq touchscreen protocol output
[4294701.289000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r
edhat.com
[4294701.913000] cdrom: open failed.
[4294702.925000] cdrom: open failed.
[4294708.345000] ReiserFS: hda5: found reiserfs format "3.6" with standard journ
al
[4294708.789000] ReiserFS: hda5: using ordered data mode
[4294708.808000] ReiserFS: hda5: journal params: device hda5, size 8192, journal
first block 18, max trans len 1024, max batch 900, max commit age 30, max trans
age 30
[4294708.808000] ReiserFS: hda5: checking transaction log (hda5)
[4294708.856000] ReiserFS: hda5: Using r5 hash to sort names
[4294709.007000] NTFS volume version 3.1.
[4294710.365000] Linux agpgart interface v0.101 (c) Dave Jones
[4294710.370000] agpgart: Detected an Intel 855 Chipset.
[4294710.371000] agpgart: Detected 32636K stolen memory.
[4294710.391000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294710.648000] hw_random hardware driver 1.0.0 loaded
[4294710.677000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294710.687000] shpchp: shpc_init : shpc_cap_offset == 0
[4294710.687000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294711.072000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (le
vel, low) -> IRQ 5
[4294711.072000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294711.378000] intel8x0_measure_ac97_clock: measured 49798 usecs
[4294711.378000] intel8x0: clocking to 48000
[4294712.767000] Linux Kernel Card Services
[4294712.767000]   options:  [pci] [cardbus] [pm]
[4294712.776000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[4294712.776000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 11 (l
evel, low) -> IRQ 11
[4294712.776000] Yenta: CardBus bridge found at 0000:02:05.0 [103c:3084]
[4294712.776000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294712.776000] Yenta: Routing CardBus interrupts to PCI
[4294712.776000] Yenta TI: socket 0000:02:05.0, mfunc 0x01111112, devctl 0x64
[4294712.997000] Yenta: ISA IRQ mask 0x00d8, PCI irq 11
[4294712.997000] Socket status: 30000006
[4294713.068000] ieee80211_crypt: registered algorithm 'NULL'
[4294713.071000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294713.071000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@
linux.intel.com>
[4294713.078000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294713.078000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294713.081000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKC] -> GSI 11 (l
evel, low) -> IRQ 11
[4294713.081000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294714.135000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294714.135000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[4294714.135000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKF] -> GSI 11 (l
evel, low) -> IRQ 11
[4294714.186000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[e02050
00-e02057ff]  Max Packet=[2048]
[4294715.443000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00002e30e7]
[4294715.865000] Real Time Clock Driver v1.12
[4294718.997000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294725.504000] NET: Registered protocol family 10
[4294725.504000] Disabled Privacy Extensions on device c02eb280(lo)
[4294725.504000] IPv6 over IPv4 tunneling driver
[4294727.727000] ACPI: AC Adapter [ACAD] (on-line)
[4294727.780000] ACPI: Power Button (FF) [PWRF]
[4294727.780000] ACPI: Lid Switch [LID0]
[4294727.780000] ACPI: Power Button (CM) [PWRB]
[4294727.816000] ibm_acpi: ec object not found
[4294727.853000] ACPI: Battery Slot [BAT0] (battery present)
[4294727.865000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[4294735.785000] eth0: no IPv6 routers present
[4294737.139000] [drm] Initialized drm 1.0.0 20040925
[4294737.143000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (l                                            evel, low) -> IRQ 10
[4294737.147000] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corpora                                            tion 82852/855GM Integrated Graphics Device
[4294737.150000] [drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corpora                                            tion 82852/855GM Integrated Graphics Device (#2)
[4294737.150000] mtrr: base(0xe8020000) is not aligned on a size(0x300000) bound                                            ary
[4294746.512000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294746.512000] apm: overridden by ACPI.
[4294757.264000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294757.266000] cs: IO port probe 0xc00-0xcf7: clean.
[4294757.267000] cs: IO port probe 0xa00-0xaff: clean.
[4294762.922000] Bluetooth: Core ver 2.7
[4294762.923000] NET: Registered protocol family 31
[4294762.923000] Bluetooth: HCI device and connection manager initialized
[4294762.923000] Bluetooth: HCI socket layer initialized
[4294762.964000] Bluetooth: L2CAP ver 2.7
[4294762.964000] Bluetooth: L2CAP socket layer initialized
[4294762.996000] Bluetooth: RFCOMM ver 1.5
[4294762.996000] Bluetooth: RFCOMM socket layer initialized
[4294762.996000] Bluetooth: RFCOMM TTY layer initialized
```

---

### Post by Desintegr on 2005-10-29
I think the problem is updatedb.
updatedb updates the slocate file database. During this updatedb, the harddisk drive is busy and can slow down your system.
If you don't use slodate, you can disable updatedb.

Try to remove &#171; /etc/cron.daily/slocate &#187; file.

If you want to recreate this file, simply reinstall &#171; slocate &#187; package.

---

### Post by chessmani on 2005-10-29
Thx for replying. It has not happened again so far today. I will update this post if it happens again.

---

