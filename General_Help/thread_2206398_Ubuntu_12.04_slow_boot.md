---
title: "Ubuntu 12.04 slow boot"
date: 2014-02-18
forum: General Help
---

### Post by jgf621 on 2014-02-18
I hope I'm doing this in tthe right format.  I am also having slow boot issues with 12.04 64 bit version.  Here is what dmseg tells me.  Obviously, at the bottom, there are some delays but I don't know how to address.

Thanks for any help or advice.

```


"
[    0.210188] SCSI subsystem initialized
[    0.210188] ACPI: bus type ATA registered
[    0.210188] libata version 3.00 loaded.
[    0.210188] ACPI: bus type USB registered
[    0.210188] usbcore: registered new interface driver usbfs
[    0.210188] usbcore: registered new interface driver hub
[    0.210188] usbcore: registered new device driver usb
[    0.210188] PCI: Using ACPI for IRQ routing
[    0.223585] PCI: pci_cache_line_size set to 64 bytes
[    0.223657] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.223661] e820: reserve RAM buffer [mem 0xbfef0000-0xbfffffff]
[    0.223798] NetLabel: Initializing
[    0.223800] NetLabel:  domain hash size = 128
[    0.223801] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.223820] NetLabel:  unlabeled traffic allowed by default
[    0.223846] Switched to clocksource refined-jiffies
[    0.233849] AppArmor: AppArmor Filesystem Enabled
[    0.233914] pnp: PnP ACPI init
[    0.233938] ACPI: bus type PNP registered
[    0.234231] system 00:00: [io  0x0228-0x022f] has been reserved
[    0.234235] system 00:00: [io  0x040b] has been reserved
[    0.234238] system 00:00: [io  0x04d6] has been reserved
[    0.234241] system 00:00: [io  0x0c00-0x0c01] has been reserved
[    0.234243] system 00:00: [io  0x0c14] has been reserved
[    0.234246] system 00:00: [io  0x0c50-0x0c52] has been reserved
[    0.234249] system 00:00: [io  0x0c6c-0x0c6d] has been reserved
[    0.234252] system 00:00: [io  0x0c6f] has been reserved
[    0.234255] system 00:00: [io  0x0cd4-0x0cdf] has been reserved
[    0.234258] system 00:00: [io  0x4000-0x40fe] could not be reserved
[    0.234261] system 00:00: [io  0x4210-0x4217] has been reserved
[    0.234265] system 00:00: [mem 0x00000000-0x00000fff window] could not be reserved
[    0.234270] system 00:00: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.234275] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.234404] pnp 00:01: [dma 4]
[    0.234435] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.234485] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.234519] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.234555] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.234726] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.234729] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.234732] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.235159] pnp 00:06: [dma 3]
[    0.235207] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.235301] pnp 00:07: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.235403] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    0.235406] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.235593] system 00:09: [mem 0x000f0000-0x000f3fff] could not be reserved
[    0.235596] system 00:09: [mem 0x000f4000-0x000f7fff] could not be reserved
[    0.235599] system 00:09: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.235602] system 00:09: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.235605] system 00:09: [mem 0xbff00000-0xbfffffff] could not be reserved
[    0.235609] system 00:09: [mem 0xbfef0000-0xbfefffff] could not be reserved
[    0.235612] system 00:09: [mem 0xffff0000-0xffffffff] has been reserved
[    0.235615] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.235618] system 00:09: [mem 0x00100000-0xbfeeffff] could not be reserved
[    0.235621] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.235625] system 00:09: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.235628] system 00:09: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.235631] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.235644] pnp: PnP ACPI: found 10 devices
[    0.235646] ACPI: bus type PNP unregistered
[    0.242600] Switched to clocksource acpi_pm
[    0.242643] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.242647] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.242651] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.242655] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.242661] pci 0000:00:14.4: PCI bridge to [bus 02]
[    0.242665] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
[    0.242672] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.242678] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.242702] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.242705] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.242708] pci_bus 0000:00: resource 6 [mem 0xc0000000-0xefffffff]
[    0.242710] pci_bus 0000:00: resource 7 [mem 0xf0000000-0xfcffffffff]
[    0.242713] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.242716] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbffffff]
[    0.242719] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.242722] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.242724] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.242727] pci_bus 0000:02: resource 2 [mem 0xfde00000-0xfdefffff pref]
[    0.242730] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.242733] pci_bus 0000:02: resource 5 [mem 0x000a0000-0x000bffff]
[    0.242736] pci_bus 0000:02: resource 6 [mem 0xc0000000-0xefffffff]
[    0.242739] pci_bus 0000:02: resource 7 [mem 0xf0000000-0xfcffffffff]
[    0.242806] NET: Registered protocol family 2
[    0.243058] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.243598] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.243598] TCP: Hash tables configured (established 32768 bind 32768)
[    0.243598] TCP: reno registered
[    0.243598] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.243598] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.243598] NET: Registered protocol family 1
[    0.243598] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.364322] pci 0000:01:00.0: Boot video device
[    0.364333] PCI: CLS 32 bytes, default 64
[    0.364424] Trying to unpack rootfs image as initramfs...
[    0.778016] Freeing initrd memory: 17056K (ffff880035ea0000 - ffff880036f48000)
[    0.778515] Scanning for low memory corruption every 60 seconds
[    0.778862] Initialise module verification
[    0.778923] audit: initializing netlink socket (disabled)
[    0.778943] type=2000 audit(1392669701.775:1): initialized
[    0.812647] bounce pool size: 64 pages
[    0.812670] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.814559] zbud: loaded
[    0.814772] VFS: Disk quotas dquot_6.5.2
[    0.814842] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.815676] fuse init (API version 7.22)
[    0.815815] msgmni has been set to 6012
[    0.816754] Key type asymmetric registered
[    0.816758] Asymmetric key parser 'x509' registered
[    0.816813] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.816874] io scheduler noop registered
[    0.816876] io scheduler deadline registered (default)
[    0.816909] io scheduler cfq registered
[    0.817150] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.817171] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.817355] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.817362] ACPI: Power Button [PWRB]
[    0.817423] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.817426] ACPI: Power Button [PWRF]
[    0.817477] ACPI: Fan [FAN] (on)
[    0.820713] thermal LNXTHERM:00: registered as thermal_zone0
[    0.820716] ACPI: Thermal Zone [THRM] (40 C)
[    0.820749] GHES: HEST is not enabled!
[    0.820874] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.823214] Linux agpgart interface v0.103
[    0.825300] brd: module loaded
[    0.826389] loop: module loaded
[    0.826489] megasas: 06.600.18.00-rc1 Wed. May. 15 17:00:00 PDT 2013
[    0.827030] libphy: Fixed MDIO Bus: probed
[    0.827163] tun: Universal TUN/TAP device driver, 1.6
[    0.827165] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.827241] PPP generic driver version 2.4.2
[    0.827310] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.827312] ehci-pci: EHCI PCI platform driver
[    0.827496] ehci-pci 0000:00:13.2: EHCI Host Controller
[    0.827505] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.827597] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe02c000
[    0.836040] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.836073] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.836076] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.836079] usb usb1: Product: EHCI Host Controller
[    0.836081] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    0.836083] usb usb1: SerialNumber: 0000:00:13.2
[    0.836230] hub 1-0:1.0: USB hub found
[    0.836237] hub 1-0:1.0: 8 ports detected
[    0.836476] ehci-platform: EHCI generic platform driver
[    0.836491] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.836493] ohci-pci: OHCI PCI platform driver
[    0.836612] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    0.836620] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.836640] ohci-pci 0000:00:13.0: irq 19, io mem 0xfe02e000
[    0.896033] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.896036] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.896038] usb usb2: Product: OHCI PCI host controller
[    0.896041] usb usb2: Manufacturer: Linux 3.11.0-15-generic ohci_hcd
[    0.896043] usb usb2: SerialNumber: 0000:00:13.0
[    0.896180] hub 2-0:1.0: USB hub found
[    0.896190] hub 2-0:1.0: 4 ports detected
[    0.896428] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    0.896436] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.896458] ohci-pci 0000:00:13.1: irq 19, io mem 0xfe02d000
[    0.956025] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.956028] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.956031] usb usb3: Product: OHCI PCI host controller
[    0.956033] usb usb3: Manufacturer: Linux 3.11.0-15-generic ohci_hcd
[    0.956036] usb usb3: SerialNumber: 0000:00:13.1
[    0.956157] hub 3-0:1.0: USB hub found
[    0.956166] hub 3-0:1.0: 4 ports detected
[    0.956316] ohci-platform: OHCI generic platform driver
[    0.956326] uhci_hcd: USB Universal Host Controller Interface driver
[    0.956413] i8042: PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    0.956415] i8042: PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.959415] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.959422] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.959638] mousedev: PS/2 mouse device common for all mice
[    0.959851] rtc_cmos 00:02: RTC can wake from S4
[    0.960062] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.960092] rtc_cmos 00:02: alarms up to one month, 242 bytes nvram
[    0.960185] device-mapper: uevent: version 1.0.3
[    0.960278] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.960369] cpuidle: using governor ladder
[    0.960372] cpuidle: using governor menu
[    0.960386] ledtrig-cpu: registered to indicate activity on CPUs
[    0.960504] TCP: cubic registered
[    0.960648] NET: Registered protocol family 10
[    0.960931] NET: Registered protocol family 17
[    0.960944] Key type dns_resolver registered
[    0.961285] PM: Hibernation image not present or could not be loaded.
[    0.961299] Loading module verification certificates
[    0.962479] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: e20ade5b3af83aaa8563f0ef4119a030c4d3ffdb'
[    0.962501] registered taskstats version 1
[    0.966014] Key type trusted registered
[    0.969204] Key type encrypted registered
[    0.972354] AppArmor: AppArmor sha1 policy hashing enabled
[    0.972684]   Magic number: 2:507:700
[    0.972839] rtc_cmos 00:02: setting system clock to 2014-02-17 20:41:42 UTC (1392669702)
[    0.973029] powernow-k8: fid 0xe (2200 MHz), vid 0x8
[    0.973031] powernow-k8: fid 0xc (2000 MHz), vid 0xa
[    0.973033] powernow-k8: fid 0xa (1800 MHz), vid 0xc
[    0.973035] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    0.973071] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2 cpu cores) (version 2.20.00)
[    0.973077] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.973078] EDD information not available.
[    0.975720] Freeing unused kernel memory: 1392K (ffffffff81d0f000 - ffffffff81e6b000)
[    0.975728] Write protecting the kernel read-only data: 12288k
[    0.978533] Freeing unused kernel memory: 672K (ffff880001758000 - ffff880001800000)
[    0.978653] Freeing unused kernel memory: 20K (ffff880001bfb000 - ffff880001c00000)
[    1.008088] udevd[100]: starting version 175
[    1.082665] sata_sil 0000:00:12.0: version 2.4
[    1.083463] scsi0 : sata_sil
[    1.086464] scsi1 : sata_sil
[    1.086648] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 22
[    1.086653] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 22
[    1.148085] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    1.168083] scsi2 : pata_atiixp
[    1.170166] scsi3 : pata_atiixp
[    1.170607] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    1.170611] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    1.176122] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.176180] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.178599] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.180108] 8139too 0000:02:03.0 eth0: RealTek RTL8139 at 0x000000000001dc00, 00:15:f2:a5:3a:75, IRQ 21
[    1.252070] firewire_ohci 0000:02:05.0: added OHCI v1.0 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    1.281323] usb 1-3: New USB device found, idVendor=0d49, idProduct=7310
[    1.281330] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.281333] usb 1-3: Product: OneTouch        
[    1.281336] usb 1-3: Manufacturer: Maxtor  
[    1.281338] usb 1-3: SerialNumber: 2HA44WDS    
[    1.368610] ata4.00: ATAPI: LITE-ON DVDRW SHW-160H6S, CP81, max UDMA/66
[    1.368620] ata4.01: ATAPI: IDE-DVD DROM6216, HD08, max UDMA/100
[    1.400522] ata4.00: configured for UDMA/66
[    1.408091] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.416566] ata1.00: ATA-7: ST3250823AS, 3.03, max UDMA/100
[    1.416569] ata1.00: 488397168 sectors, multi 16: LBA48 
[    1.416801] ata4.01: configured for UDMA/100
[    1.432325] ata1.00: configured for UDMA/100
[    1.432553] scsi 0:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    1.432893] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.432967] sd 0:0:0:0: [sda] Write Protect is off
[    1.432970] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.433001] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.433422] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.450362]  sda: sda1 sda2
[    1.450795] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.752086] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.752172] firewire_core 0000:02:05.0: created device fw0: GUID 0011d800008dd5c4, S400
[    1.760713] ata2.00: ATA-8: ST3500820AS, SD1A, max UDMA/133
[    1.760717] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.776682] ata2.00: configured for UDMA/100
[    1.776884] scsi 1:0:0:0: Direct-Access     ATA      ST3500820AS      SD1A PQ: 0 ANSI: 5
[    1.777175] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.777249] sd 1:0:0:0: [sdb] Write Protect is off
[    1.777252] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.777284] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.777761] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.779050] scsi 3:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-160H6S CP81 PQ: 0 ANSI: 5
[    1.781628] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.781635] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.781900] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.782096] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.783183] scsi 3:0:1:0: CD-ROM            IDE-DVD  DROM6216         HD08 PQ: 0 ANSI: 5
[    1.785537] sr1: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[    1.785794] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    1.786021] sr 3:0:1:0: Attached scsi generic sg3 type 5
[    1.794259]  sdb: sdb1
[    1.794895] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.070160] usb-storage 1-3:1.0: USB Mass Storage device detected
[    2.070278] usb-storage 1-3:1.0: Quirks match for vid 0d49 pid 7310: 8000
[    2.070375] scsi4 : usb-storage 1-3:1.0
[    2.070532] usbcore: registered new interface driver usb-storage
[    2.368034] usb 3-2: new full-speed USB device number 2 using ohci-pci
[    2.588077] usb 3-2: New USB device found, idVendor=04b8, idProduct=0818
[    2.588082] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.588085] usb 3-2: Product: USB MFP
[    2.588087] usb 3-2: Manufacturer: EPSON
[    2.588089] usb 3-2: SerialNumber: L33040508242301090
[    3.068739] scsi 4:0:0:0: Direct-Access     Maxtor   OneTouch         0125 PQ: 0 ANSI: 4
[    3.069149] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    3.070206] sd 4:0:0:0: [sdc] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    3.070963] sd 4:0:0:0: [sdc] Write Protect is off
[    3.070969] sd 4:0:0:0: [sdc] Mode Sense: 2d 08 00 00
[    3.071704] sd 4:0:0:0: [sdc] No Caching mode page found
[    3.071707] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    3.074076] sd 4:0:0:0: [sdc] No Caching mode page found
[    3.074080] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    3.153713]  sdc: sdc1 sdc2 < sdc5 sdc6 >
[    3.156850] sd 4:0:0:0: [sdc] No Caching mode page found
[    3.156858] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    3.156863] sd 4:0:0:0: [sdc] Attached SCSI disk
[    3.168034] usb 2-3: new full-speed USB device number 2 using ohci-pci
[    3.375080] usb 2-3: New USB device found, idVendor=062a, idProduct=3286
[    3.375088] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.375090] usb 2-3: Product: 2.4G Keyboard Mouse
[    3.375093] usb 2-3: Manufacturer: MOSART Semi.
[    3.384877] hidraw: raw HID events driver (C) Jiri Kosina
[    3.396307] usbcore: registered new interface driver usbhid
[    3.396315] usbhid: USB HID core driver
[    3.402071] input: MOSART Semi. 2.4G Keyboard Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-3/2-3:1.0/input/input2
[    3.402289] hid-generic 0003:062A:3286.0001: input,hidraw0: USB HID v1.10 Keyboard [MOSART Semi. 2.4G Keyboard Mouse] on usb-0000:00:13.0-3/input0
[    3.403065] input: MOSART Semi. 2.4G Keyboard Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-3/2-3:1.1/input/input3
[    3.403258] hid-generic 0003:062A:3286.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [MOSART Semi. 2.4G Keyboard Mouse] on usb-0000:00:13.0-3/input1
[    3.680036] usb 2-4: new full-speed USB device number 3 using ohci-pci
[    3.772407] EXT4-fs (sdc5): mounted filesystem with ordered data mode. Opts: (null)
[    3.889094] usb 2-4: New USB device found, idVendor=058f, idProduct=9360
[    3.889101] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.889104] usb 2-4: Product: USB Reader
[    3.889107] usb 2-4: Manufacturer:  
[    3.889109] usb 2-4: SerialNumber: 2004888
[    3.891128] usb-storage 2-4:1.0: USB Mass Storage device detected
[    3.891259] scsi5 : usb-storage 2-4:1.0
[    4.895128] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    4.901102] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    4.907112] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    4.913112] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    4.913394] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    4.913575] sd 5:0:0:1: Attached scsi generic sg6 type 0
[    4.913743] sd 5:0:0:2: Attached scsi generic sg7 type 0
[    4.913907] sd 5:0:0:3: Attached scsi generic sg8 type 0
[    5.003109] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[    5.013103] sd 5:0:0:1: [sde] Attached SCSI removable disk
[    5.023081] sd 5:0:0:2: [sdf] Attached SCSI removable disk
[    5.033107] sd 5:0:0:3: [sdg] Attached SCSI removable disk
[    5.416826] init: ureadahead main process (287) terminated with status 5
[    6.751559] Adding 3142652k swap on /dev/sdc6.  Priority:-1 extents:1 across:3142652k FS
[    7.587357] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.700080] udevd[364]: starting version 175
[    8.937421] lp: driver loaded but no devices found
[    9.228734] parport_pc 00:06: reported by Plug and Play ACPI
[    9.228792] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[    9.320524] lp0: using parport0 (interrupt-driven).
[    9.546046] ppdev: user-space parallel port driver
[   10.014584] MCE: In-kernel MCE decoding enabled.
[   10.150764] EDAC MC: Ver: 3.0.0
[   10.160715] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SM00 1 (20130517/utaddress-251)
[   10.160727] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.346191] AMD64 EDAC driver v3.4.0
[   10.346263] EDAC amd64: DRAM ECC disabled.
[   10.346273] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   10.346273]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   10.346273]  (Note that use of the override may cause unknown side effects.)
[   11.262216] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   12.596163] Did not find alt setting 1 for intf 0, config 1
[   12.744396] nvidia: module license 'NVIDIA' taints kernel.
[   12.744404] Disabling lock debugging due to kernel taint
[   12.748456] type=1400 audit(1392687714.273:2): apparmor="STATUS" operation="profile_load" parent=650 profile="unconfined" name="/sbin/dhclient" pid=685 comm="apparmor_parser"
[   12.748486] type=1400 audit(1392687714.273:3): apparmor="STATUS" operation="profile_load" parent=650 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=685 comm="apparmor_parser"
[   12.748494] type=1400 audit(1392687714.273:4): apparmor="STATUS" operation="profile_load" parent=650 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=685 comm="apparmor_parser"
[   12.749336] type=1400 audit(1392687714.273:5): apparmor="STATUS" operation="profile_replace" parent=650 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=685 comm="apparmor_parser"
[   12.749350] type=1400 audit(1392687714.273:6): apparmor="STATUS" operation="profile_replace" parent=650 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=685 comm="apparmor_parser"
[   12.749756] type=1400 audit(1392687714.273:7): apparmor="STATUS" operation="profile_replace" parent=650 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=685 comm="apparmor_parser"
[   12.752282] type=1400 audit(1392687714.277:8): apparmor="STATUS" operation="profile_replace" parent=652 profile="unconfined" name="/sbin/dhclient" pid=686 comm="apparmor_parser"
[   12.752310] type=1400 audit(1392687714.277:9): apparmor="STATUS" operation="profile_replace" parent=652 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=686 comm="apparmor_parser"
[   12.752316] type=1400 audit(1392687714.277:10): apparmor="STATUS" operation="profile_replace" parent=652 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=686 comm="apparmor_parser"
[   12.753176] type=1400 audit(1392687714.277:11): apparmor="STATUS" operation="profile_replace" parent=652 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=686 comm="apparmor_parser"
[   12.774033] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   12.878347] usblp 3-2:1.1: usblp1: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0818
[   12.878946] usbcore: registered new interface driver usblp
[   13.031430] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.031772] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.39  Wed Nov 27 14:25:00 PST 2013
[   14.203699] EXT4-fs (sdc5): re-mounted. Opts: errors=remount-ro
[   15.004986] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   15.004993] vesafb: scrolling: redraw
[   15.004997] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.005945] vesafb: framebuffer at 0xf9000000, mapped to 0xffffc90010d00000, using 5120k, total 5120k
[   15.006792] Console: switching to colour frame buffer device 160x64
[   15.012378] fb0: VESA VGA frame buffer device
[   17.254784] init: failsafe main process (894) killed by TERM signal
[   19.811862] audit_printk_skb: 6 callbacks suppressed
[   19.811869] type=1400 audit(1392687721.333:14): apparmor="STATUS" operation="profile_replace" parent=954 profile="unconfined" name="/sbin/dhclient" pid=962 comm="apparmor_parser"
[   19.811882] type=1400 audit(1392687721.333:15): apparmor="STATUS" operation="profile_replace" parent=954 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=962 comm="apparmor_parser"
[   19.811888] type=1400 audit(1392687721.333:16): apparmor="STATUS" operation="profile_replace" parent=954 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=962 comm="apparmor_parser"
[   19.812723] type=1400 audit(1392687721.337:17): apparmor="STATUS" operation="profile_replace" parent=954 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=962 comm="apparmor_parser"
[   19.812730] type=1400 audit(1392687721.337:18): apparmor="STATUS" operation="profile_replace" parent=954 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=962 comm="apparmor_parser"
[   19.813124] type=1400 audit(1392687721.337:19): apparmor="STATUS" operation="profile_replace" parent=954 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=962 comm="apparmor_parser"
[   20.058251] type=1400 audit(1392687721.581:20): apparmor="STATUS" operation="profile_load" parent=954 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=961 comm="apparmor_parser"
[   20.058266] type=1400 audit(1392687721.581:21): apparmor="STATUS" operation="profile_load" parent=954 profile="unconfined" name="chromium_browser" pid=961 comm="apparmor_parser"
[   20.058825] type=1400 audit(1392687721.581:22): apparmor="STATUS" operation="profile_replace" parent=954 profile="unconfined" name="chromium_browser" pid=961 comm="apparmor_parser"
[   20.459206] type=1400 audit(1392687721.981:23): apparmor="STATUS" operation="profile_load" parent=954 profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=976 comm="apparmor_parser"
[   21.437047] Bluetooth: Core ver 2.16
[   21.437092] NET: Registered protocol family 31
[   21.437095] Bluetooth: HCI device and connection manager initialized
[   21.437116] Bluetooth: HCI socket layer initialized
[   21.437119] Bluetooth: L2CAP socket layer initialized
[   21.437127] Bluetooth: SCO socket layer initialized
[   21.743317] Bluetooth: RFCOMM TTY layer initialized
[   21.743348] Bluetooth: RFCOMM socket layer initialized
[   21.743350] Bluetooth: RFCOMM ver 1.11
[   21.831579] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.831587] Bluetooth: BNEP filters: protocol multicast
[   21.831610] Bluetooth: BNEP socket layer initialized
[   26.534317] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   52.209629] init: plymouth-stop pre-start process (1681) terminated with status 1
[   75.518838] audit_printk_skb: 135 callbacks suppressed
[   75.518846] type=1400 audit(1392687777.039:69): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1908 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  139.358987] type=1400 audit(1392687840.882:70): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=994 comm="cupsd" pid=994 comm="cupsd" capability=36  capname="block_suspend"
[  282.770400] type=1400 audit(1392687984.292:71): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=994 comm="cupsd" pid=994 comm="cupsd" capability=36  capname="block_suspend"
[  285.396449] usblp1: removed
[  285.451071] usblp 3-2:1.1: usblp1: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0818
[  286.506928] usblp1: removed
[  286.554206] usblp 3-2:1.1: usblp1: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0818
[  345.215380] usblp1: removed
[ 1289.779607] usb 3-2: USB disconnect, device number 2

"
```

---

### Post by oldfred on 2014-02-18
Moved to your own thread.
Please use code tags with long text output. Easy to add with # with advanced editor.

Try with printer unplugged. You have a very long time with that USB port. Not sure if USB port or printer issue.

---

### Post by jgf621 on 2014-02-19
Thanks for advice.

I unplugged printer and time to desktop background appearing was two minutes and five econds.  Here is new dmeseg 

```
subtractive decode)
[    0.208772] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.208840] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.208904] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.208967] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.209031] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.209095] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11)
[    0.209157] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11)
[    0.209220] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.209889] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.209900] ACPI: \_SB_.PCI0: notify handler is installed
[    0.209947] Found 1 acpi root devices
[    0.210087] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.210087] vgaarb: loaded
[    0.210087] vgaarb: bridge control possible 0000:01:00.0
[    0.210087] SCSI subsystem initialized
[    0.210087] ACPI: bus type ATA registered
[    0.210087] libata version 3.00 loaded.
[    0.210087] ACPI: bus type USB registered
[    0.210087] usbcore: registered new interface driver usbfs
[    0.210087] usbcore: registered new interface driver hub
[    0.210087] usbcore: registered new device driver usb
[    0.210087] PCI: Using ACPI for IRQ routing
[    0.223240] PCI: pci_cache_line_size set to 64 bytes
[    0.223310] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.223314] e820: reserve RAM buffer [mem 0xbfef0000-0xbfffffff]
[    0.223455] NetLabel: Initializing
[    0.223456] NetLabel:  domain hash size = 128
[    0.223458] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.223477] NetLabel:  unlabeled traffic allowed by default
[    0.223499] Switched to clocksource refined-jiffies
[    0.234074] AppArmor: AppArmor Filesystem Enabled
[    0.234136] pnp: PnP ACPI init
[    0.234160] ACPI: bus type PNP registered
[    0.234443] system 00:00: [io  0x0228-0x022f] has been reserved
[    0.234453] system 00:00: [io  0x040b] has been reserved
[    0.234456] system 00:00: [io  0x04d6] has been reserved
[    0.234459] system 00:00: [io  0x0c00-0x0c01] has been reserved
[    0.234461] system 00:00: [io  0x0c14] has been reserved
[    0.234464] system 00:00: [io  0x0c50-0x0c52] has been reserved
[    0.234467] system 00:00: [io  0x0c6c-0x0c6d] has been reserved
[    0.234470] system 00:00: [io  0x0c6f] has been reserved
[    0.234473] system 00:00: [io  0x0cd4-0x0cdf] has been reserved
[    0.234477] system 00:00: [io  0x4000-0x40fe] could not be reserved
[    0.234480] system 00:00: [io  0x4210-0x4217] has been reserved
[    0.234483] system 00:00: [mem 0x00000000-0x00000fff window] could not be reserved
[    0.234488] system 00:00: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.234493] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.234624] pnp 00:01: [dma 4]
[    0.234654] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.234703] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.234735] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.234770] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.234936] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.234940] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.234944] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.235374] pnp 00:06: [dma 3]
[    0.235420] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.235512] pnp 00:07: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.235614] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    0.235617] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.235798] system 00:09: [mem 0x000f0000-0x000f3fff] could not be reserved
[    0.235802] system 00:09: [mem 0x000f4000-0x000f7fff] could not be reserved
[    0.235805] system 00:09: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.235808] system 00:09: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.235811] system 00:09: [mem 0xbff00000-0xbfffffff] could not be reserved
[    0.235814] system 00:09: [mem 0xbfef0000-0xbfefffff] could not be reserved
[    0.235818] system 00:09: [mem 0xffff0000-0xffffffff] has been reserved
[    0.235821] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.235824] system 00:09: [mem 0x00100000-0xbfeeffff] could not be reserved
[    0.235827] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.235831] system 00:09: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.235834] system 00:09: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.235837] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.235850] pnp: PnP ACPI: found 10 devices
[    0.235851] ACPI: bus type PNP unregistered
[    0.242818] Switched to clocksource acpi_pm
[    0.242861] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.242866] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.242870] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.242874] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.242880] pci 0000:00:14.4: PCI bridge to [bus 02]
[    0.242884] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
[    0.242892] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.242898] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.242922] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.242925] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.242927] pci_bus 0000:00: resource 6 [mem 0xc0000000-0xefffffff]
[    0.242930] pci_bus 0000:00: resource 7 [mem 0xf0000000-0xfcffffffff]
[    0.242933] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.242936] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbffffff]
[    0.242939] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.242942] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.242945] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.242948] pci_bus 0000:02: resource 2 [mem 0xfde00000-0xfdefffff pref]
[    0.242951] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.242954] pci_bus 0000:02: resource 5 [mem 0x000a0000-0x000bffff]
[    0.242956] pci_bus 0000:02: resource 6 [mem 0xc0000000-0xefffffff]
[    0.242959] pci_bus 0000:02: resource 7 [mem 0xf0000000-0xfcffffffff]
[    0.243027] NET: Registered protocol family 2
[    0.243287] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.243840] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.243840] TCP: Hash tables configured (established 32768 bind 32768)
[    0.243840] TCP: reno registered
[    0.243840] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.243840] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.243840] NET: Registered protocol family 1
[    0.243840] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.364264] pci 0000:01:00.0: Boot video device
[    0.364276] PCI: CLS 32 bytes, default 64
[    0.364370] Trying to unpack rootfs image as initramfs...
[    0.777460] Freeing initrd memory: 17056K (ffff880035ea0000 - ffff880036f48000)
[    0.777961] Scanning for low memory corruption every 60 seconds
[    0.778291] Initialise module verification
[    0.778355] audit: initializing netlink socket (disabled)
[    0.778376] type=2000 audit(1392817944.775:1): initialized
[    0.812115] bounce pool size: 64 pages
[    0.812132] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.814058] zbud: loaded
[    0.814267] VFS: Disk quotas dquot_6.5.2
[    0.814340] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.815224] fuse init (API version 7.22)
[    0.815365] msgmni has been set to 6012
[    0.816299] Key type asymmetric registered
[    0.816304] Asymmetric key parser 'x509' registered
[    0.816363] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.816425] io scheduler noop registered
[    0.816427] io scheduler deadline registered (default)
[    0.816468] io scheduler cfq registered
[    0.816695] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.816716] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.816900] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.816908] ACPI: Power Button [PWRB]
[    0.816965] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.816968] ACPI: Power Button [PWRF]
[    0.817017] ACPI: Fan [FAN] (on)
[    0.820257] thermal LNXTHERM:00: registered as thermal_zone0
[    0.820261] ACPI: Thermal Zone [THRM] (40 C)
[    0.820293] GHES: HEST is not enabled!
[    0.820454] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.822608] Linux agpgart interface v0.103
[    0.824714] brd: module loaded
[    0.825808] loop: module loaded
[    0.825911] megasas: 06.600.18.00-rc1 Wed. May. 15 17:00:00 PDT 2013
[    0.826445] libphy: Fixed MDIO Bus: probed
[    0.826575] tun: Universal TUN/TAP device driver, 1.6
[    0.826577] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.826642] PPP generic driver version 2.4.2
[    0.826719] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.826721] ehci-pci: EHCI PCI platform driver
[    0.826905] ehci-pci 0000:00:13.2: EHCI Host Controller
[    0.826914] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.827000] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe02c000
[    0.836037] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.836072] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.836074] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.836077] usb usb1: Product: EHCI Host Controller
[    0.836079] usb usb1: Manufacturer: Linux 3.11.0-17-generic ehci_hcd
[    0.836082] usb usb1: SerialNumber: 0000:00:13.2
[    0.836251] hub 1-0:1.0: USB hub found
[    0.836263] hub 1-0:1.0: 8 ports detected
[    0.836496] ehci-platform: EHCI generic platform driver
[    0.836517] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.836519] ohci-pci: OHCI PCI platform driver
[    0.836649] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    0.836657] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.836679] ohci-pci 0000:00:13.0: irq 19, io mem 0xfe02e000
[    0.896035] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.896038] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.896040] usb usb2: Product: OHCI PCI host controller
[    0.896043] usb usb2: Manufacturer: Linux 3.11.0-17-generic ohci_hcd
[    0.896045] usb usb2: SerialNumber: 0000:00:13.0
[    0.896172] hub 2-0:1.0: USB hub found
[    0.896181] hub 2-0:1.0: 4 ports detected
[    0.896416] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    0.896424] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.896444] ohci-pci 0000:00:13.1: irq 19, io mem 0xfe02d000
[    0.956025] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.956028] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.956031] usb usb3: Product: OHCI PCI host controller
[    0.956033] usb usb3: Manufacturer: Linux 3.11.0-17-generic ohci_hcd
[    0.956036] usb usb3: SerialNumber: 0000:00:13.1
[    0.956156] hub 3-0:1.0: USB hub found
[    0.956167] hub 3-0:1.0: 4 ports detected
[    0.956307] ohci-platform: OHCI generic platform driver
[    0.956317] uhci_hcd: USB Universal Host Controller Interface driver
[    0.956406] i8042: PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    0.956408] i8042: PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.959205] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.959212] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.959429] mousedev: PS/2 mouse device common for all mice
[    0.959632] rtc_cmos 00:02: RTC can wake from S4
[    0.959824] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.959856] rtc_cmos 00:02: alarms up to one month, 242 bytes nvram
[    0.959952] device-mapper: uevent: version 1.0.3
[    0.960064] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.960160] cpuidle: using governor ladder
[    0.960162] cpuidle: using governor menu
[    0.960177] ledtrig-cpu: registered to indicate activity on CPUs
[    0.960294] TCP: cubic registered
[    0.960441] NET: Registered protocol family 10
[    0.960708] NET: Registered protocol family 17
[    0.960725] Key type dns_resolver registered
[    0.961063] PM: Hibernation image not present or could not be loaded.
[    0.961068] Loading module verification certificates
[    0.962232] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d129e34292be0bf4c53989b44f39fdfb63de7f23'
[    0.962259] registered taskstats version 1
[    0.965823] Key type trusted registered
[    0.969057] Key type encrypted registered
[    0.972221] AppArmor: AppArmor sha1 policy hashing enabled
[    0.972543]   Magic number: 2:121:888
[    0.972696] rtc_cmos 00:02: setting system clock to 2014-02-19 13:52:25 UTC (1392817945)
[    0.972887] powernow-k8: fid 0xe (2200 MHz), vid 0x8
[    0.972889] powernow-k8: fid 0xc (2000 MHz), vid 0xa
[    0.972891] powernow-k8: fid 0xa (1800 MHz), vid 0xc
[    0.972893] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    0.972926] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (2 cpu cores) (version 2.20.00)
[    0.972931] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.972933] EDD information not available.
[    0.975568] Freeing unused kernel memory: 1392K (ffffffff81d10000 - ffffffff81e6c000)
[    0.975576] Write protecting the kernel read-only data: 12288k
[    0.978362] Freeing unused kernel memory: 672K (ffff880001758000 - ffff880001800000)
[    0.978496] Freeing unused kernel memory: 24K (ffff880001bfa000 - ffff880001c00000)
[    1.007684] udevd[100]: starting version 175
[    1.095620] sata_sil 0000:00:12.0: version 2.4
[    1.099157] scsi0 : sata_sil
[    1.102489] scsi1 : sata_sil
[    1.102697] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 22
[    1.102701] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 22
[    1.143193] scsi2 : pata_atiixp
[    1.145657] scsi3 : pata_atiixp
[    1.146131] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    1.146134] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    1.148112] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    1.182161] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.182214] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.184536] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.185923] 8139too 0000:02:03.0 eth0: RealTek RTL8139 at 0x000000000001dc00, 00:15:f2:a5:3a:75, IRQ 21
[    1.260082] firewire_ohci 0000:02:05.0: added OHCI v1.0 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    1.281348] usb 1-3: New USB device found, idVendor=0d49, idProduct=7310
[    1.281354] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.281357] usb 1-3: Product: OneTouch        
[    1.281360] usb 1-3: Manufacturer: Maxtor  
[    1.281362] usb 1-3: SerialNumber: 2HA44WDS    
[    1.344615] ata4.00: ATAPI: LITE-ON DVDRW SHW-160H6S, CP81, max UDMA/66
[    1.344625] ata4.01: ATAPI: IDE-DVD DROM6216, HD08, max UDMA/100
[    1.376526] ata4.00: configured for UDMA/66
[    1.392537] ata4.01: configured for UDMA/100
[    1.420068] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.428330] ata1.00: ATA-7: ST3250823AS, 3.03, max UDMA/100
[    1.428333] ata1.00: 488397168 sectors, multi 16: LBA48 
[    1.444328] ata1.00: configured for UDMA/100
[    1.444556] scsi 0:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    1.444858] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.444932] sd 0:0:0:0: [sda] Write Protect is off
[    1.444936] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.444968] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.445602] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.464437]  sda: sda1 sda2
[    1.464868] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.760176] firewire_core 0000:02:05.0: created device fw0: GUID 0011d800008dd5c4, S400
[    1.764076] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.772834] ata2.00: ATA-8: ST3500820AS, SD1A, max UDMA/133
[    1.772837] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.788720] ata2.00: configured for UDMA/100
[    1.788914] scsi 1:0:0:0: Direct-Access     ATA      ST3500820AS      SD1A PQ: 0 ANSI: 5
[    1.789191] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.789264] sd 1:0:0:0: [sdb] Write Protect is off
[    1.789268] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.789299] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.789677] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.790722] scsi 3:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-160H6S CP81 PQ: 0 ANSI: 5
[    1.793169] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.793177] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.793386] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.793586] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.794779] scsi 3:0:1:0: CD-ROM            IDE-DVD  DROM6216         HD08 PQ: 0 ANSI: 5
[    1.797185] sr1: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[    1.797523] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    1.797624] sr 3:0:1:0: Attached scsi generic sg3 type 5
[    1.801178]  sdb: sdb1
[    1.801678] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.062130] usb-storage 1-3:1.0: USB Mass Storage device detected
[    2.062246] usb-storage 1-3:1.0: Quirks match for vid 0d49 pid 7310: 8000
[    2.062293] scsi4 : usb-storage 1-3:1.0
[    2.062409] usbcore: registered new interface driver usb-storage
[    2.232036] usb 2-3: new full-speed USB device number 2 using ohci-pci
[    2.439061] usb 2-3: New USB device found, idVendor=062a, idProduct=3286
[    2.439065] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.439068] usb 2-3: Product: 2.4G Keyboard Mouse
[    2.439070] usb 2-3: Manufacturer: MOSART Semi.
[    2.447799] hidraw: raw HID events driver (C) Jiri Kosina
[    2.458116] usbcore: registered new interface driver usbhid
[    2.458122] usbhid: USB HID core driver
[    2.462868] input: MOSART Semi. 2.4G Keyboard Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-3/2-3:1.0/input/input2
[    2.463016] hid-generic 0003:062A:3286.0001: input,hidraw0: USB HID v1.10 Keyboard [MOSART Semi. 2.4G Keyboard Mouse] on usb-0000:00:13.0-3/input0
[    2.463718] input: MOSART Semi. 2.4G Keyboard Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-3/2-3:1.1/input/input3
[    2.463891] hid-generic 0003:062A:3286.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [MOSART Semi. 2.4G Keyboard Mouse] on usb-0000:00:13.0-3/input1
[    2.744034] usb 2-4: new full-speed USB device number 3 using ohci-pci
[    2.953062] usb 2-4: New USB device found, idVendor=058f, idProduct=9360
[    2.953065] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.953068] usb 2-4: Product: USB Reader
[    2.953071] usb 2-4: Manufacturer:  
[    2.953073] usb 2-4: SerialNumber: 2004888
[    2.955123] usb-storage 2-4:1.0: USB Mass Storage device detected
[    2.955246] scsi5 : usb-storage 2-4:1.0
[    3.060766] scsi 4:0:0:0: Direct-Access     Maxtor   OneTouch         0125 PQ: 0 ANSI: 4
[    3.061171] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    3.062461] sd 4:0:0:0: [sdc] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    3.063236] sd 4:0:0:0: [sdc] Write Protect is off
[    3.063239] sd 4:0:0:0: [sdc] Mode Sense: 2d 08 00 00
[    3.063980] sd 4:0:0:0: [sdc] No Caching mode page found
[    3.063983] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    3.066353] sd 4:0:0:0: [sdc] No Caching mode page found
[    3.066357] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    3.116492]  sdc: sdc1 sdc2 < sdc5 sdc6 >
[    3.147522] sd 4:0:0:0: [sdc] No Caching mode page found
[    3.147530] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    3.147535] sd 4:0:0:0: [sdc] Attached SCSI disk
[    3.743491] EXT4-fs (sdc5): mounted filesystem with ordered data mode. Opts: (null)
[    3.959103] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    3.965099] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    3.971091] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    3.977090] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    3.977426] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    3.977621] sd 5:0:0:1: Attached scsi generic sg6 type 0
[    3.977786] sd 5:0:0:2: Attached scsi generic sg7 type 0
[    3.977939] sd 5:0:0:3: Attached scsi generic sg8 type 0
[    4.067084] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[    4.077083] sd 5:0:0:1: [sde] Attached SCSI removable disk
[    4.087082] sd 5:0:0:2: [sdf] Attached SCSI removable disk
[    4.097090] sd 5:0:0:3: [sdg] Attached SCSI removable disk
[    5.529495] init: ureadahead main process (293) terminated with status 5
[    6.886883] Adding 3142652k swap on /dev/sdc6.  Priority:-1 extents:1 across:3142652k FS
[    7.819574] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.968669] udevd[367]: starting version 175
[    9.233743] lp: driver loaded but no devices found
[    9.489669] parport_pc 00:06: reported by Plug and Play ACPI
[    9.489729] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[    9.585010] lp0: using parport0 (interrupt-driven).
[    9.879170] ppdev: user-space parallel port driver
[   10.320856] MCE: In-kernel MCE decoding enabled.
[   10.451463] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SM00 1 (20130517/utaddress-251)
[   10.451481] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.486661] EDAC MC: Ver: 3.0.0
[   10.652388] AMD64 EDAC driver v3.4.0
[   10.652455] EDAC amd64: DRAM ECC disabled.
[   10.652462] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   10.652462]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   10.652462]  (Note that use of the override may cause unknown side effects.)
[   11.730083] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   13.291495] nvidia: module license 'NVIDIA' taints kernel.
[   13.291503] Disabling lock debugging due to kernel taint
[   13.314980] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   13.376913] type=1400 audit(1392835957.900:2): apparmor="STATUS" operation="profile_load" parent=655 profile="unconfined" name="/sbin/dhclient" pid=672 comm="apparmor_parser"
[   13.376927] type=1400 audit(1392835957.900:3): apparmor="STATUS" operation="profile_load" parent=655 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=672 comm="apparmor_parser"
[   13.376933] type=1400 audit(1392835957.900:4): apparmor="STATUS" operation="profile_load" parent=655 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=672 comm="apparmor_parser"
[   13.377669] type=1400 audit(1392835957.900:5): apparmor="STATUS" operation="profile_replace" parent=655 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=672 comm="apparmor_parser"
[   13.377678] type=1400 audit(1392835957.900:6): apparmor="STATUS" operation="profile_replace" parent=655 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=672 comm="apparmor_parser"
[   13.378077] type=1400 audit(1392835957.900:7): apparmor="STATUS" operation="profile_replace" parent=655 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=672 comm="apparmor_parser"
[   13.379465] type=1400 audit(1392835957.900:8): apparmor="STATUS" operation="profile_replace" parent=654 profile="unconfined" name="/sbin/dhclient" pid=673 comm="apparmor_parser"
[   13.379478] type=1400 audit(1392835957.900:9): apparmor="STATUS" operation="profile_replace" parent=654 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=673 comm="apparmor_parser"
[   13.379484] type=1400 audit(1392835957.900:10): apparmor="STATUS" operation="profile_replace" parent=654 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=673 comm="apparmor_parser"
[   13.380259] type=1400 audit(1392835957.904:11): apparmor="STATUS" operation="profile_replace" parent=654 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=673 comm="apparmor_parser"
[   13.571880] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.572309] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.39  Wed Nov 27 14:25:00 PST 2013
[   14.239909] EXT4-fs (sdc5): re-mounted. Opts: errors=remount-ro
[   15.019946] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   15.019956] vesafb: scrolling: redraw
[   15.019961] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.020781] vesafb: framebuffer at 0xf9000000, mapped to 0xffffc90010d00000, using 5120k, total 5120k
[   15.021478] Console: switching to colour frame buffer device 160x64
[   15.027019] fb0: VESA VGA frame buffer device
[   17.236471] init: failsafe main process (889) killed by TERM signal
[   20.570180] audit_printk_skb: 6 callbacks suppressed
[   20.570187] type=1400 audit(1392835965.092:14): apparmor="STATUS" operation="profile_replace" parent=959 profile="unconfined" name="/sbin/dhclient" pid=970 comm="apparmor_parser"
[   20.570199] type=1400 audit(1392835965.092:15): apparmor="STATUS" operation="profile_replace" parent=959 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=970 comm="apparmor_parser"
[   20.570205] type=1400 audit(1392835965.092:16): apparmor="STATUS" operation="profile_replace" parent=959 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=970 comm="apparmor_parser"
[   20.570973] type=1400 audit(1392835965.092:17): apparmor="STATUS" operation="profile_replace" parent=959 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=970 comm="apparmor_parser"
[   20.570979] type=1400 audit(1392835965.092:18): apparmor="STATUS" operation="profile_replace" parent=959 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=970 comm="apparmor_parser"
[   20.571391] type=1400 audit(1392835965.092:19): apparmor="STATUS" operation="profile_replace" parent=959 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=970 comm="apparmor_parser"
[   21.186603] type=1400 audit(1392835965.708:20): apparmor="STATUS" operation="profile_load" parent=959 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=969 comm="apparmor_parser"
[   21.186618] type=1400 audit(1392835965.708:21): apparmor="STATUS" operation="profile_load" parent=959 profile="unconfined" name="chromium_browser" pid=969 comm="apparmor_parser"
[   21.187206] type=1400 audit(1392835965.708:22): apparmor="STATUS" operation="profile_replace" parent=959 profile="unconfined" name="chromium_browser" pid=969 comm="apparmor_parser"
[   21.325853] type=1400 audit(1392835965.848:23): apparmor="STATUS" operation="profile_load" parent=978 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=982 comm="apparmor_parser"
[   21.867501] Bluetooth: Core ver 2.16
[   21.867549] NET: Registered protocol family 31
[   21.867551] Bluetooth: HCI device and connection manager initialized
[   21.867570] Bluetooth: HCI socket layer initialized
[   21.867574] Bluetooth: L2CAP socket layer initialized
[   21.867581] Bluetooth: SCO socket layer initialized
[   22.313001] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.313008] Bluetooth: BNEP filters: protocol multicast
[   22.313031] Bluetooth: BNEP socket layer initialized
[   22.362788] Bluetooth: RFCOMM TTY layer initialized
[   22.362813] Bluetooth: RFCOMM socket layer initialized
[   22.362815] Bluetooth: RFCOMM ver 1.11
[   27.619208] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   58.190090] init: plymouth-stop pre-start process (1741) terminated with status 1
[  803.410191] audit_printk_skb: 135 callbacks suppressed
[  803.410204] type=1400 audit(1392836748.498:69): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=995 comm="cupsd" pid=995 comm="cupsd" capability=36  capname="block_suspend"
[  916.786054] type=1400 audit(1392836861.876:70): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=995 comm="cupsd" pid=995 comm="cupsd" capability=36  capname="block_suspend"
```

---

### Post by oldfred on 2014-02-19
Please use code tags.

This is the main part of the delay, few other minor ones.
```
[   27.619208] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   58.190090] init: plymouth-stop pre-start process (1741) terminated with status 1
[  803.410191] audit_printk_skb: 135 callbacks suppressed
[  803.410204] type=1400 audit(1392836748.498:69): apparmor="DENIED"  operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=995  comm="cupsd" pid=995 comm="cupsd" capability=36  capname="block_suspend"
[  916.786054] type=1400 audit(1392836861.876:70): apparmor="DENIED"  operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=995  comm="cupsd" pid=995 comm="cupsd" capability=36  capname="block_suspend"
```

Are you using a USB hub? or are all USB ports USB3? And first issue status1 means plymount had issues?
Still seems to be something related to printing, but I do not know exact errors.

---

### Post by jgf621 on 2014-02-21
I think I figured this out. I have an external USB drive attached.  When I installed Ubuntu, I said to install it alongside Windows XP.  It resized the main drive but everything is on the USB drive.  Trying to reboot with the USB drive unconnected gives me a grub error and stops me cold.

Is there a safe way other than reinstalling 12.04 to fix this?  If I try to re-install with the USB drive un-cnnected, will I risk damaging my XP system?  I don't want to depend on the USB drive going forward.

Thanks,

Joe

---

### Post by oldfred on 2014-02-21
You can run this from your live Installer.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by jgf621 on 2014-02-21
Thank you for help.  I ran boot repair and it has removed grub.  I now can only boot to windows.  I can  see that ubuntu files are still on sdc5 which is the external usb drive.  Hard to fathom how that happened.

I'm guessing I'll have to start over?

Here is text of report.

```
" Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Windows 2000/XP/2003 is installed in the MBR of /dev/sdb.
 => No known boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.4 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    15,711,569    15,711,507   b W95 FAT32
/dev/sda2    *     15,711,570   488,375,999   472,664,430   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   493,342,020   493,341,958   7 NTFS / exFAT / HPFS
/dev/sdc2         493,342,718   625,141,759   131,799,042   5 Extended
/dev/sdc5    *    493,342,720   618,854,399   125,511,680  83 Linux
/dev/sdc6         618,856,448   625,141,759     6,285,312  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2B72-1CC3                              vfat       HP_RECOVERY
/dev/sda2        0424023624022AEE                       ntfs       HP_PAVILION
/dev/sdb1        A03897ED3897C128                       ntfs       2nd Internal Drive
/dev/sdc1        55D123D9E79ABF54                       ntfs       OneTouch 4
/dev/sdc5        61c4608e-26f7-4bb1-8b27-49e7eac1bfe8   ext4       
/dev/sdc6        4e115266-5c46-4700-a515-b9da13f44516   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04.4 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------

=========================== sdc5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set=root 61c4608e-26f7-4bb1-8b27-49e7eac1bfe8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos5)'
  search --no-floppy --fs-uuid --set=root 61c4608e-26f7-4bb1-8b27-49e7eac1bfe8
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
menuentry "Windows XP Media Center Edition (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 0424023624022AEE
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/33_linux_proxy ###
menuentry "Ubuntu, with Linux 3.11.0-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root 61c4608e-26f7-4bb1-8b27-49e7eac1bfe8
    linux    /boot/vmlinuz-3.11.0-17-generic root=UUID=61c4608e-26f7-4bb1-8b27-49e7eac1bfe8 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.0-17-generic
}
menuentry "Ubuntu, with Linux 3.11.0-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root 61c4608e-26f7-4bb1-8b27-49e7eac1bfe8
    echo    'Loading Linux 3.11.0-17-generic ...'
    linux    /boot/vmlinuz-3.11.0-17-generic root=UUID=61c4608e-26f7-4bb1-8b27-49e7eac1bfe8 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.11.0-17-generic
}
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
### END /etc/grub.d/33_linux_proxy ###

### BEGIN /etc/grub.d/34_linux_xen ###
### END /etc/grub.d/34_linux_xen ###

### BEGIN /etc/grub.d/35_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root 61c4608e-26f7-4bb1-8b27-49e7eac1bfe8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set=root 61c4608e-26f7-4bb1-8b27-49e7eac1bfe8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/35_memtest86+ ###

### BEGIN /etc/grub.d/36_os-prober_proxy ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 2B72-1CC3
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/36_os-prober_proxy ###

### BEGIN /etc/grub.d/37_uefi-firmware ###
### END /etc/grub.d/37_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=61c4608e-26f7-4bb1-8b27-49e7eac1bfe8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=4e115266-5c46-4700-a515-b9da13f44516 none            swap    sw              0       0
UUID=0424023624022AEE /mnt/windows ntfs users,defaults 0 0
UUID=A03897ED3897C128 /mnt/windows1 ntfs users,defaults 0 0
UUID=55D123D9E79ABF54 /mnt/windows2 ntfs users,defaults 0 0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 279.507629395 = 300.119031808  boot/grub/grub.cfg                             1
 239.380981445 = 257.033371648  boot/grub/core.img                             1
 235.788707733 = 253.176197120  boot/vmlinuz-3.11.0-15-generic                 1
 237.845703125 = 255.384879104  boot/vmlinuz-3.11.0-17-generic                 2
 237.845703125 = 255.384879104  vmlinuz                                        2
 235.788707733 = 253.176197120  vmlinuz.old                                    1
 236.424468994 = 253.858840576  boot/initrd.img-3.11.0-15-generic              1
 238.518218994 = 256.106987520  boot/initrd.img-3.11.0-17-generic              1
 236.424468994 = 253.858840576  initrd.img.old                                 1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdc

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  07 1f 77 f0 00 00 00 01  |..........w.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 06 cd 67 1d 00 fe  |......?.....g...|
000001d0  ff ff 05 fe ff ff fe cf  67 1d 02 18 db 07 00 00  |........g.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda1

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  0c bd ef 00 d2 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 c3 1c 72 2b 20  20 20 20 20 20 20 20 20  |..)..r+         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc2

00000000  6a f5 14 76 1e f2 ff ba  e5 c3 ee 00 08 d2 24 a4  |j..v..........$.|
00000010  4a 8b 82 24 bf 8e 87 e2  9c 49 7d 5a 62 c1 9f 3c  |J..$.....I}Zb..<|
00000020  7c 5c 0e 9c c7 5a 62 83  94 5e e8 8c 31 e8 63 8b  ||\...Zb..^..1.c.|
00000030  ef 55 47 75 62 13 51 17  55 ee eb be ad cb af 92  |.UGub.Q.U.......|
00000040  92 b3 dc 43 d2 5f a6 5d  df af b3 2e e6 ff ff ec  |...C._.]........|
00000050  61 9b e5 91 1a 6c 10 46  76 35 37 ec 71 d0 95 15  |a....l.Fv57.q...|
00000060  8e 9b cb 06 64 a6 4a 3a  54 79 be e6 6f 77 fd bf  |....d.J:Ty..ow..|
00000070  ff 72 bc b2 e4 64 5c 43  43 e6 14 2a 02 10 c5 d2  |.r...d\CC..*....|
00000080  3b d8 00 00 24 92 4a 25  44 50 97 1f c5 86 30 50  |;...$.J%DP....0P|
00000090  83 ae b1 16 a1 c1 c4 3b  98 e2 c2 de 30 c7 9d 67  |.......;....0..g|
000000a0  23 07 4b 4b 04 92 32 17  77 bc e4 57 74 13 12 21  |#.KK..2.w..Wt..!|
000000b0  10 4b 9d af be f5 ed eb  dc 75 5b ad ec 83 ff 14  |.K.......u[.....|
000000c0  91 cb af 77 71 1b 12 fa  72 12 c3 0b a5 28 58 38  |...wq...r....(X8|
000000d0  39 93 6a 26 99 ab 6d f7  65 9e 56 1e 89 47 5e c1  |9.j&..m.e.V..G^.|
000000e0  3d 8f 06 de dd d6 c4 3a  e9 af fd df ff 7b 17 74  |=......:.....{.t|
000000f0  f0 c1 07 fa 56 88 af 37  a9 87 3b 0a 00 08 d2 aa  |....V..7..;.....|
00000100  83 98 42 06 3f 89 ae 02  84 1d 7e 02 d4 76 a9 dd  |..B.?.....~..v..|
00000110  dd 27 48 97 c6 f1 57 29  be 2e 36 67 b5 60 a6 e6  |.'H...W)..6g.`..|
00000120  31 7b f7 b3 dc 5e db 26  d0 42 8a f8 fa 8f ab a8  |1{...^.&.B......|
00000130  fd ea 6c 4d 2a 7c db d8  e7 ee b3 ac e2 29 8f 7d  |..lM*|.......).}|
00000140  c7 98 a3 6c a4 a2 0d 17  b1 0c 68 76 0a c3 f4 3c  |...l......hv...<|
00000150  79 6c 85 c2 5d 5e ff fa  a0 04 2b f6 6a 00 03 cf  |yl..]^....+.j...|
00000160  57 d6 d1 e5 33 76 7e 6a  ea c9 3c c8 6e ce b5 2f  |W...3v~j..<.n../|
00000170  5d 34 f3 00 1a 00 ae 2b  e6 9e 80 03 59 65 58 f1  |]4.....+....YeX.|
00000180  5a b0 fc ea 20 38 31 11  6b 2b 31 37 7d ee e9 22  |Z... 81.k+17}.."|
00000190  ff 99 92 c3 f8 9b 64 a0  1c d6 b3 78 cd 8f e0 45  |......d....x...E|
000001a0  c0 00 1a 55 50 74 98 ea  66 50 27 07 60 1c d9 e4  |...UPt..fP'.`...|
000001b0  de f3 6a 66 26 b0 32 1b  e3 3d f6 77 47 39 80 fe  |..jf&.2..=.wG9..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 28 7b 07 00 fe  |...........({...|
000001d0  ff ff 05 fe ff ff fc 2d  7b 07 06 ea 5f 00 00 00  |.......-{..._...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-02-21__22h43 ===================
boot-repair version : 3.199~ppa40~precise
boot-sav version : 3.199~ppa40~precise
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 3.199~ppa40~precise
boot-repair is executed in live-session (Ubuntu 12.04.4 LTS, precise, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity

=================== os-prober:
/dev/sda1:Windows NT/2000/XP:Windows:chain
/dev/sda2:Windows XP Media Center Edition:Windows1:chain
/dev/sdc5:Ubuntu 12.04.4 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="HP_RECOVERY" UUID="2B72-1CC3" TYPE="vfat"
/dev/sda2: LABEL="HP_PAVILION" UUID="0424023624022AEE" TYPE="ntfs"
/dev/sdb1: LABEL="2nd Internal Drive" UUID="A03897ED3897C128" TYPE="ntfs"
/dev/sr0: LABEL="Ubuntu 12.04.4 LTS amd64" TYPE="iso9660"
/dev/sdc1: LABEL="OneTouch 4" UUID="55D123D9E79ABF54" TYPE="ntfs"
/dev/sdc5: UUID="61c4608e-26f7-4bb1-8b27-49e7eac1bfe8" TYPE="ext4"
/dev/sdc6: UUID="4e115266-5c46-4700-a515-b9da13f44516" TYPE="swap"


2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sdc5/etc/grub.d/ :
drwxr-xr-x  5 root root     4096 Feb 21 18:32 grub.d
total 72
-rwxr-xr-x 1 root root 7806 Dec  6 10:06 00_header
-rwxr-xr-x 1 root root 5522 Dec  6 09:52 05_debian_theme
-rwxr-xr-x 1 root root  572 Feb 21 18:32 10_linux_proxy
-rwxr-xr-x 1 root root  279 Feb 21 18:32 30_os-prober_proxy
-rwxr-xr-x 1 root root  612 Feb 21 18:32 33_linux_proxy
-rwxr-xr-x 1 root root 6449 Dec  6 10:06 34_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 35_memtest86+
-rwxr-xr-x 1 root root  279 Feb 21 18:32 36_os-prober_proxy
-rwxr-xr-x 1 root root 1388 Dec  6 10:06 37_uefi-firmware
-rwxr-xr-x 1 root root  214 Dec  6 10:06 40_custom
-rwxr-xr-x 1 root root   95 Dec  6 10:06 41_custom
drwxr-xr-x 4 root root 4096 Feb 12 20:15 backup
drwxr-xr-x 2 root root 4096 Feb 12 20:15 bin
drwxr-xr-x 2 root root 4096 Feb 21 18:32 proxifiedScripts
-rw-r--r-- 1 root root  483 Dec  6 10:06 README




=================== sdc5/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    NTLDR,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc1.
sdc5    : sdc,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    customized,    farbios,    /mnt/boot-sav/sdc5.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    63 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA ST3250823AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  8044MB  8044MB  primary  fat32
2      8044MB  250GB   242GB   primary  ntfs         boot


Model: ATA ST3500820AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  500GB  500GB  primary  ntfs


Model: Maxtor OneTouch (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      32.3kB  253GB  253GB   primary   ntfs
2      253GB   320GB  67.5GB  extended
5      253GB   317GB  64.3GB  logical   ext4            boot
6      317GB   320GB  3218MB  logical   linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:250GB:scsi:512:512:msdos:ATA ST3250823AS;
1:32.3kB:8044MB:8044MB:fat32::;
2:8044MB:250GB:242GB:ntfs::boot;

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:ATA ST3500820AS;
1:32.3kB:500GB:500GB:ntfs::;

BYT;
/dev/sdc:320GB:scsi:512:512:msdos:Maxtor OneTouch;
1:32.3kB:253GB:253GB:ntfs::;
2:253GB:320GB:67.5GB:::;
5:253GB:317GB:64.3GB:ext4::boot;
6:317GB:320GB:3218MB:linux-swap(v1)::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc5 on /mnt/boot-sav/sdc5 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc2 sdc5 sdc6 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrom1 cdrw1 char console core cpu cpu_dma_latency disk dri dvd dvd1 dvdrw1 ecryptfs fb0 fd full fuse fw0 hpet input kmsg log lp0 mapper mcelog mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdc sdc1 sdc2 sdc5 sdc6 sdd sde sdf sdg sg0 sg1 sg2 sg3 sg4 sg5 sg6 sg7 sg8 shm snapshot snd sr0 sr1 stderr stdin stdout uhid uinput urandom usb vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  0c bd ef 00 d2 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 c3 1c 72 2b 20  20 20 20 20 20 20 20 20  |..)..r+         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 52 bd ef 00  |........?...R...|
00000020  00 00 00 00 80 00 80 00  6d 49 2c 1c 00 00 00 00  |........mI,.....|
00000030  00 00 0c 00 00 00 00 00  fb 58 1b 00 00 00 00 00  |.........X......|
00000040  f6 00 00 00 01 00 00 00  ee 2a 02 24 36 02 24 04  |.........*.$6.$.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  01 4c 38 3a 00 00 00 00  |.........L8:....|
00000030  00 00 0c 00 00 00 00 00  c0 84 a3 03 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  28 c1 97 38 ed 97 38 a0  |........(..8..8.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  f8 cc 67 1d 00 00 00 00  |..........g.....|
00000030  02 00 00 00 00 00 00 00  30 00 00 00 00 00 00 00  |........0.......|
00000040  f6 00 00 00 01 00 00 00  54 bf 9a e7 d9 23 d1 55  |........T....#.U|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.5G  134M  1.4G   9% /
udev           devtmpfs   1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs      602M  820K  601M   1% /run
/dev/sr0       iso9660    733M  733M     0 100% /cdrom
/dev/loop0     squashfs   689M  689M     0 100% /rofs
tmpfs          tmpfs      1.5G   40K  1.5G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      1.5G   80K  1.5G   1% /run/shm
/dev/sda1      vfat       7.5G  7.1G  488M  94% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    226G  100G  127G  44% /mnt/boot-sav/sda2
/dev/sdb1      fuseblk    466G  148G  319G  32% /mnt/boot-sav/sdb1
/dev/sdc1      fuseblk    236G  176G   60G  75% /mnt/boot-sav/sdc1
/dev/sdc5      ext4        59G  5.2G   51G  10% /mnt/boot-sav/sdc5

=================== fdisk -l:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    15711569     7855753+   b  W95 FAT32
/dev/sda2   *    15711570   488375999   236332215    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7c4a711d

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf0771f07

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   493342020   246670979    7  HPFS/NTFS/exFAT
/dev/sdc2       493342718   625141759    65899521    5  Extended
/dev/sdc5   *   493342720   618854399    62755840   83  Linux
/dev/sdc6       618856448   625141759     3142656   82  Linux swap / Solaris


User choice: Is sdc (320GB) a removable disk? yes
Partition outside the disk detected.
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on the removable disk!

=================== Default settings
Recommended-Repair
This setting would purge (in order to fix customized files) and reinstall the grub2 of sdc5 into the MBR of sdc.
It would also fix access to other systems (other MBRs) for the situations when the removable media is disconnected.
The boot flag would be placed on sdc5.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.
pastebinit  packages needed
User refused to install pastebinit
```

---

### Post by oldfred on 2014-02-21
Better to use pastebin and just provide link. 
And if you are posting long text use code tags. Easy to add with # in advanced editor.

You should install grub to the MBR of sdc.
But do not have boot flag on sdc5, but any primary partition.
Grub does not use boot flag. Windows has to have the boot flag on a primary NTFS/FAT partition.
But a few BIOS will not boot without a boot flag on a primary partition so we still suggest one.

---

