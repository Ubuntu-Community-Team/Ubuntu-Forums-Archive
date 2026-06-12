---
title: "how to format new hard disks"
date: 2008-03-07
forum: General Help
---

### Post by demiurgen on 2008-03-07
i have just installed a rocketraid 2320 controller card and attached 8 new blank unformatted hard disks to it.
now i need to format them.

how can i do that when they do not show up in gparted, qtparted or hardware information??

is there something physically wrong with the controller card or the disks?

the controller card shows up in hardware information and the driver seems to work.

---

### Post by SpaceTeddy on 2008-03-07
mhm - strange. can you please post the output of the following commands for debugging purposes ?

```
fdisk -l
dmesg
```

thanks

---

### Post by demiurgen on 2008-03-07
/dev/sda1 is conected to my motherboard and holds the os (ubuntu 7.10).
/dev/sdb1 to /dev/sdi1 is connected to my other older controller card.
of those 8 disks i have made a raid 5 volume (/dev/md0)...

after installing the 8 new disks i expected to find /dev/sdj1 /dev/sdk1 etc but found nothing...:confused:

this is what fdisk -l says:```
root@RAMBO:/# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001edc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcec7696d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93d3a6a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93d3a6a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93d3a6aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93d3a6ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93d3a6ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93d3a6ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdi: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00034a7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/md0: 3500.7 GB, 3500736053248 bytes
2 heads, 4 sectors/track, 854671888 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
root@RAMBO:/# 

```and this is what dmesg says:```
[   61.836245] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   61.836335] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   61.836425] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   61.836518] Linux Plug and Play Support v0.97 (c) Adam Belay
[   61.836526] pnp: PnP ACPI init
[   61.836533] ACPI: bus type pnp registered
[   61.839433] pnp: PnP ACPI: found 17 devices
[   61.839434] ACPI: ACPI bus type pnp unregistered
[   61.839439] PnPBIOS: Disabled by ACPI PNP
[   61.839481] PCI: Using ACPI for IRQ routing
[   61.839483] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   61.904361] NET: Registered protocol family 8
[   61.904363] NET: Registered protocol family 20
[   61.904412] pnp: 00:0d: ioport range 0x400-0x4bf has been reserved
[   61.904417] pnp: 00:0e: iomem range 0xc0000000-0xcfffffff could not be reserved
[   61.904421] pnp: 00:0f: iomem range 0xde000-0xdffff has been reserved
[   61.904423] pnp: 00:0f: iomem range 0xf0000-0xf7fff could not be reserved
[   61.904426] pnp: 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
[   61.904428] pnp: 00:0f: iomem range 0xfc000-0xfffff could not be reserved
[   61.907080] Time: tsc clocksource has been installed.
[   61.907088] Switched to high resolution mode on CPU 0
[   61.907157] Switched to high resolution mode on CPU 1
[   61.934629] PCI: Bridge: 0000:00:01.0
[   61.934630]   IO window: disabled.
[   61.934633]   MEM window: f0000000-f2ffffff
[   61.934636]   PREFETCH window: d0000000-dfffffff
[   61.934640] PCI: Bridge: 0000:02:00.0
[   61.934641]   IO window: disabled.
[   61.934645]   MEM window: disabled.
[   61.934649]   PREFETCH window: disabled.
[   61.934654] PCI: Bridge: 0000:02:00.2
[   61.934656]   IO window: b000-bfff
[   61.934661]   MEM window: f3000000-f4ffffff
[   61.934665]   PREFETCH window: disabled.
[   61.934670] PCI: Bridge: 0000:00:1c.0
[   61.934672]   IO window: b000-bfff
[   61.934676]   MEM window: f3000000-f4ffffff
[   61.934679]   PREFETCH window: disabled.
[   61.934684] PCI: Bridge: 0000:00:1c.4
[   61.934686]   IO window: c000-cfff
[   61.934690]   MEM window: f5000000-f5ffffff
[   61.934693]   PREFETCH window: disabled.
[   61.934698] PCI: Bridge: 0000:00:1c.5
[   61.934700]   IO window: d000-dfff
[   61.934704]   MEM window: f6000000-f7ffffff
[   61.934708]   PREFETCH window: 40000000-400fffff
[   61.934712] PCI: Bridge: 0000:00:1e.0
[   61.934713]   IO window: disabled.
[   61.934717]   MEM window: f8000000-f9ffffff
[   61.934721]   PREFETCH window: disabled.
[   61.934733] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   61.934738] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   61.934753] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   61.934757] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   61.934775] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   61.934794] PCI: Setting latency timer of device 0000:02:00.2 to 64
[   61.934809] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   61.934813] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   61.934829] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[   61.934834] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   61.934843] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   61.934852] NET: Registered protocol family 2
[   61.982960] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   61.983018] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   61.983591] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   61.983789] TCP: Hash tables configured (established 131072 bind 65536)
[   61.983792] TCP reno registered
[   61.999074] checking if image is initramfs... it is
[   62.554380] Freeing initrd memory: 7331k freed
[   62.554825] audit: initializing netlink socket (disabled)
[   62.554835] audit(1204886816.260:1): initialized
[   62.554909] highmem bounce pool size: 64 pages
[   62.556381] VFS: Disk quotas dquot_6.5.1
[   62.556418] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   62.556487] io scheduler noop registered
[   62.556489] io scheduler anticipatory registered
[   62.556491] io scheduler deadline registered
[   62.556502] io scheduler cfq registered (default)
[   62.556614] Boot video device is 0000:01:00.0
[   62.556689] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   62.556721] assign_interrupt_mode Found MSI capability
[   62.556723] Allocate Port Service[0000:00:01.0:pcie00]
[   62.556787] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   62.556823] assign_interrupt_mode Found MSI capability
[   62.556825] Allocate Port Service[0000:00:1c.0:pcie00]
[   62.556849] Allocate Port Service[0000:00:1c.0:pcie02]
[   62.556917] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   62.556953] assign_interrupt_mode Found MSI capability
[   62.556955] Allocate Port Service[0000:00:1c.4:pcie00]
[   62.556978] Allocate Port Service[0000:00:1c.4:pcie02]
[   62.557046] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   62.557083] assign_interrupt_mode Found MSI capability
[   62.557084] Allocate Port Service[0000:00:1c.5:pcie00]
[   62.557109] Allocate Port Service[0000:00:1c.5:pcie02]
[   62.557242] isapnp: Scanning for PnP cards...
[   62.909598] isapnp: No Plug & Play device found
[   62.925763] Real Time Clock Driver v1.12ac
[   62.925907] hpet_resources: 0xfed00000 is busy
[   62.925944] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   62.926031] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   62.926143] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   62.926573] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   62.926738] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   62.927307] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   62.927471] input: Macintosh mouse button emulation as /class/input/input0
[   62.927540] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   62.928368] serio: i8042 KBD port at 0x60,0x64 irq 1
[   62.928372] serio: i8042 AUX port at 0x60,0x64 irq 12
[   62.928463] mice: PS/2 mouse device common for all mice
[   62.928538] EISA: Probing bus 0 at eisa.0
[   62.928564] EISA: Detected 0 cards.
[   62.928631] TCP cubic registered
[   62.928642] NET: Registered protocol family 1
[   62.928660] Using IPI No-Shortcut mode
[   62.928802]   Magic number: 0:800:779
[   62.928853]   hash matches device ptyq1
[   62.929024] Freeing unused kernel memory: 364k freed
[   62.953424] input: AT Translated Set 2 keyboard as /class/input/input1
[   64.098329] AppArmor: AppArmor initialized<5>audit(1204886817.760:2):  type=1505 info="AppArmor initialized" pid=1265
[   64.103151] fuse init (API version 7.8)
[   64.106715] Failure registering capabilities with primary security module.
[   64.141580] ACPI: Processor [CPU0] (supports 8 throttling states)
[   64.141594] ACPI: Processor [CPU1] (supports 8 throttling states)
[   64.141602] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   64.141610] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   64.153613] md: linear personality registered for level -1
[   64.157064] md: multipath personality registered for level -4
[   64.160471] md: raid0 personality registered for level 0
[   64.164203] md: raid1 personality registered for level 1
[   64.167459] raid5: automatically using best checksumming function: pIII_sse
[   64.187411]    pIII_sse  :  7363.000 MB/sec
[   64.187413] raid5: using function: pIII_sse (7363.000 MB/sec)
[   64.255370] raid6: int32x1    786 MB/s
[   64.323194] raid6: int32x2    788 MB/s
[   64.391188] raid6: int32x4    588 MB/s
[   64.459006] raid6: int32x8    528 MB/s
[   64.526882] raid6: mmxx1     2542 MB/s
[   64.594760] raid6: mmxx2     2959 MB/s
[   64.662656] raid6: sse1x1    1735 MB/s
[   64.730548] raid6: sse1x2    2274 MB/s
[   64.798434] raid6: sse2x1    3134 MB/s
[   64.866334] raid6: sse2x2    3492 MB/s
[   64.866335] raid6: using algorithm sse2x2 (3492 MB/s)
[   64.866338] md: raid6 personality registered for level 6
[   64.866339] md: raid5 personality registered for level 5
[   64.866341] md: raid4 personality registered for level 4
[   64.884165] md: raid10 personality registered for level 10
[   65.245038] usbcore: registered new interface driver usbfs
[   65.245059] usbcore: registered new interface driver hub
[   65.245078] usbcore: registered new device driver usb
[   65.245788] USB Universal Host Controller Interface driver v3.0
[   65.245850] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   65.245860] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   65.245863] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   65.245993] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   65.246020] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e200
[   65.246115] usb usb1: configuration #1 chosen from 1 choice
[   65.246139] hub 1-0:1.0: USB hub found
[   65.246144] hub 1-0:1.0: 2 ports detected
[   65.286057] SCSI subsystem initialized
[   65.303498] libata version 2.21 loaded.
[   65.328423] Floppy drive(s): fd0 is 1.44M
[   65.349686] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[   65.349697] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   65.349700] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   65.349722] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   65.349747] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000e300
[   65.349822] usb usb2: configuration #1 chosen from 1 choice
[   65.349842] hub 2-0:1.0: USB hub found
[   65.349847] hub 2-0:1.0: 2 ports detected
[   65.369141] FDC 0 is a post-1991 82077
[   65.453539] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 19
[   65.453557] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   65.453560] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   65.453582] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   65.453607] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000e000
[   65.453681] usb usb3: configuration #1 chosen from 1 choice
[   65.453701] hub 3-0:1.0: USB hub found
[   65.453706] hub 3-0:1.0: 2 ports detected
[   65.557342] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   65.557353] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   65.557357] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   65.557391] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   65.557414] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000e400
[   65.557485] usb usb4: configuration #1 chosen from 1 choice
[   65.557505] hub 4-0:1.0: USB hub found
[   65.557509] hub 4-0:1.0: 2 ports detected
[   65.661174] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   65.661184] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   65.661189] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   65.661217] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   65.661245] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000e500
[   65.661316] usb usb5: configuration #1 chosen from 1 choice
[   65.661334] hub 5-0:1.0: USB hub found
[   65.661339] hub 5-0:1.0: 2 ports detected
[   65.765008] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   65.765018] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   65.765022] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   65.765048] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   65.765075] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000e600
[   65.765146] usb usb6: configuration #1 chosen from 1 choice
[   65.765167] hub 6-0:1.0: USB hub found
[   65.765171] hub 6-0:1.0: 2 ports detected
[   65.872129] ata_piix 0000:00:1f.2: version 2.11
[   65.872134] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   65.872154] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[   65.872178] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   65.872235] scsi0 : ata_piix
[   65.872268] scsi1 : ata_piix
[   65.872349] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   65.872352] ata2: SATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   66.077898] ata1.00: Host Protected Area detected:
[   66.077900]  current size: 156299375 sectors
[   66.077902]  native size: 156301488 sectors
[   66.194296] ata1.00: native size increased to 156301488 sectors
[   66.194303] ata1.00: ATA-7: ST380811AS, 3.AAE, max UDMA/133
[   66.194307] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   66.260861] ata1.00: configured for UDMA/133
[   66.735514] ata2.00: ATAPI: Optiarc DVD RW AD-7170S, 1.00, max UDMA/66
[   66.907236] ata2.00: configured for UDMA/66
[   66.907321] scsi 0:0:0:0: Direct-Access     ATA      ST380811AS       3.AA PQ: 0 ANSI: 5
[   66.908290] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7170S  1.00 PQ: 0 ANSI: 5
[   66.908358] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   66.908387] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 21
[   66.908423] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   66.908450] scsi2 : ata_piix
[   66.908479] scsi3 : ata_piix
[   66.908558] ata3: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e902 bmdma 0x0001ec00 irq 21
[   66.908561] ata4: SATA max UDMA/133 cmd 0x0001ea00 ctl 0x0001eb02 bmdma 0x0001ec08 irq 21
[   67.237244] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 19
[   67.237253] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   67.237256] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   67.237280] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   67.237307] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   67.237312] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfa185000
[   67.241196] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   67.241275] usb usb7: configuration #1 chosen from 1 choice
[   67.241297] hub 7-0:1.0: USB hub found
[   67.241305] hub 7-0:1.0: 6 ports detected
[   67.242828] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   67.242838] sd 0:0:0:0: [sda] Write Protect is off
[   67.242840] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   67.242852] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   67.242892] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   67.245808] sd 0:0:0:0: [sda] Write Protect is off
[   67.245811] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   67.246537] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   67.246542]  sda: sda1 sda2 < sda5 >
[   67.294141] sd 0:0:0:0: [sda] Attached SCSI disk
[   67.297530] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   67.297547] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   67.300296] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   67.300299] Uniform CD-ROM driver Revision: 3.20
[   67.300333] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   67.342532] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   67.342544] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   67.342547] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   67.342567] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   67.342593] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   67.342599] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfa184000
[   67.346476] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   67.346541] usb usb8: configuration #1 chosen from 1 choice
[   67.346562] hub 8-0:1.0: USB hub found
[   67.346567] hub 8-0:1.0: 6 ports detected
[   67.450438] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   67.450472] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   67.450509] scsi4 : pata_jmicron
[   67.450544] scsi5 : pata_jmicron
[   67.450624] ata5: PATA max UDMA/100 cmd 0x0001c000 ctl 0x0001c102 bmdma 0x0001c400 irq 16
[   67.450628] ata6: PATA max UDMA/100 cmd 0x0001c200 ctl 0x0001c302 bmdma 0x0001c408 irq 16
[   67.533508] Attempting manual resume
[   67.533511] swsusp: Resume From Partition 8:5
[   67.533513] PM: Checking swsusp image.
[   67.533657] PM: Resume from disk failed.
[   67.571260] kjournald starting.  Commit interval 5 seconds
[   67.571271] EXT3-fs: mounted filesystem with ordered data mode.
[   67.761794] r8169 Gigabit Ethernet driver 2.2LK loaded
[   67.761824] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   67.761845] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   67.762038] eth0: RTL8168b/8111b at 0xf8860000, 00:1a:4d:5c:36:98, XID 38000000 IRQ 17
[   67.763101] sata_mv 0000:07:01.0: version 0.81
[   67.763169] ACPI: PCI Interrupt 0000:07:01.0[A] -> GSI 19 (level, low) -> IRQ 21
[   67.771445] sata_mv 0000:07:01.0: 32 slots 8 ports SCSI mode IRQ via INTx
[   67.771544] scsi6 : sata_mv
[   67.771580] scsi7 : sata_mv
[   67.771605] scsi8 : sata_mv
[   67.771629] scsi9 : sata_mv
[   67.771654] scsi10 : sata_mv
[   67.771678] scsi11 : sata_mv
[   67.771703] scsi12 : sata_mv
[   67.771728] scsi13 : sata_mv
[   67.771748] ata7: SATA max UDMA/133 cmd 0x00000000 ctl 0xf8aa2120 bmdma 0x00000000 irq 21
[   67.771751] ata8: SATA max UDMA/133 cmd 0x00000000 ctl 0xf8aa4120 bmdma 0x00000000 irq 21
[   67.771755] ata9: SATA max UDMA/133 cmd 0x00000000 ctl 0xf8aa6120 bmdma 0x00000000 irq 21
[   67.771758] ata10: SATA max UDMA/133 cmd 0x00000000 ctl 0xf8aa8120 bmdma 0x00000000 irq 21
[   67.771762] ata11: SATA max UDMA/133 cmd 0x00000000 ctl 0xf8ab2120 bmdma 0x00000000 irq 21
[   67.771766] ata12: SATA max UDMA/133 cmd 0x00000000 ctl 0xf8ab4120 bmdma 0x00000000 irq 21
[   67.771769] ata13: SATA max UDMA/133 cmd 0x00000000 ctl 0xf8ab6120 bmdma 0x00000000 irq 21
[   67.771773] ata14: SATA max UDMA/133 cmd 0x00000000 ctl 0xf8ab8120 bmdma 0x00000000 irq 21
[   67.849916] ata7.00: ATA-7: WDC WD5000AAKS-65TMA0, 12.01C01, max UDMA/133
[   67.849919] ata7.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   67.865879] ata7.00: configured for UDMA/133
[   67.953435] ata8.00: ATA-7: ST3500641AS, 3.AAJ, max UDMA/133
[   67.953439] ata8.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   68.025323] ata8.00: configured for UDMA/133
[   68.113181] ata9.00: ATA-7: ST3500641AS, 3.AAJ, max UDMA/133
[   68.113186] ata9.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   68.185066] ata9.00: configured for UDMA/133
[   68.272926] ata10.00: ATA-7: ST3500641AS, 3.AAJ, max UDMA/133
[   68.272931] ata10.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   68.360786] ata10.00: configured for UDMA/133
[   68.448646] ata11.00: ATA-7: ST3500641AS, 3.AAJ, max UDMA/133
[   68.448651] ata11.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   68.536505] ata11.00: configured for UDMA/133
[   68.624363] ata12.00: ATA-7: ST3500641AS, 3.AAJ, max UDMA/133
[   68.624367] ata12.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   68.704244] ata12.00: configured for UDMA/133
[   68.792091] ata13.00: ATA-7: ST3500641AS, 3.AAJ, max UDMA/133
[   68.792095] ata13.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   68.863988] ata13.00: configured for UDMA/133
[   69.407441] ata14.00: ATA-7: WDC WD5000AAKS-65TMA0, 12.01C01, max UDMA/133
[   69.407444] ata14.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   69.423394] ata14.00: configured for UDMA/133
[   69.423465] scsi 6:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-6 12.0 PQ: 0 ANSI: 5
[   69.423515] sd 6:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   69.423524] sd 6:0:0:0: [sdb] Write Protect is off
[   69.423525] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   69.423538] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.423577] sd 6:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   69.423584] sd 6:0:0:0: [sdb] Write Protect is off
[   69.423586] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   69.423598] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.423601]  sdb: sdb1
[   69.433825] sd 6:0:0:0: [sdb] Attached SCSI disk
[   69.433870] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   69.433933] scsi 7:0:0:0: Direct-Access     ATA      ST3500641AS      3.AA PQ: 0 ANSI: 5
[   69.433970] sd 7:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   69.433978] sd 7:0:0:0: [sdc] Write Protect is off
[   69.433979] sd 7:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   69.433991] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.434033] sd 7:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   69.434041] sd 7:0:0:0: [sdc] Write Protect is off
[   69.434042] sd 7:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   69.434054] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.434057]  sdc: sdc1
[   69.450153] sd 7:0:0:0: [sdc] Attached SCSI disk
[   69.450193] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   69.450274] scsi 8:0:0:0: Direct-Access     ATA      ST3500641AS      3.AA PQ: 0 ANSI: 5
[   69.450311] sd 8:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[   69.450319] sd 8:0:0:0: [sdd] Write Protect is off
[   69.450321] sd 8:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   69.450333] sd 8:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.450363] sd 8:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[   69.450370] sd 8:0:0:0: [sdd] Write Protect is off
[   69.450372] sd 8:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   69.450384] sd 8:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.450387]  sdd: sdd1
[   69.467552] sd 8:0:0:0: [sdd] Attached SCSI disk
[   69.467591] sd 8:0:0:0: Attached scsi generic sg4 type 0
[   69.467674] scsi 9:0:0:0: Direct-Access     ATA      ST3500641AS      3.AA PQ: 0 ANSI: 5
[   69.467714] sd 9:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
[   69.467722] sd 9:0:0:0: [sde] Write Protect is off
[   69.467724] sd 9:0:0:0: [sde] Mode Sense: 00 3a 00 00
[   69.467735] sd 9:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.467763] sd 9:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
[   69.467770] sd 9:0:0:0: [sde] Write Protect is off
[   69.467772] sd 9:0:0:0: [sde] Mode Sense: 00 3a 00 00
[   69.467784] sd 9:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.467786]  sde: sde1
[   69.484938] sd 9:0:0:0: [sde] Attached SCSI disk
[   69.484977] sd 9:0:0:0: Attached scsi generic sg5 type 0
[   69.485062] scsi 10:0:0:0: Direct-Access     ATA      ST3500641AS      3.AA PQ: 0 ANSI: 5
[   69.485101] sd 10:0:0:0: [sdf] 976773168 512-byte hardware sectors (500108 MB)
[   69.485108] sd 10:0:0:0: [sdf] Write Protect is off
[   69.485110] sd 10:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[   69.485122] sd 10:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.485150] sd 10:0:0:0: [sdf] 976773168 512-byte hardware sectors (500108 MB)
[   69.485157] sd 10:0:0:0: [sdf] Write Protect is off
[   69.485159] sd 10:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[   69.485171] sd 10:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.485173]  sdf: sdf1
[   69.503576] sd 10:0:0:0: [sdf] Attached SCSI disk
[   69.503615] sd 10:0:0:0: Attached scsi generic sg6 type 0
[   69.503698] scsi 11:0:0:0: Direct-Access     ATA      ST3500641AS      3.AA PQ: 0 ANSI: 5
[   69.503735] sd 11:0:0:0: [sdg] 976773168 512-byte hardware sectors (500108 MB)
[   69.503742] sd 11:0:0:0: [sdg] Write Protect is off
[   69.503744] sd 11:0:0:0: [sdg] Mode Sense: 00 3a 00 00
[   69.503756] sd 11:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.503786] sd 11:0:0:0: [sdg] 976773168 512-byte hardware sectors (500108 MB)
[   69.503793] sd 11:0:0:0: [sdg] Write Protect is off
[   69.503795] sd 11:0:0:0: [sdg] Mode Sense: 00 3a 00 00
[   69.503807] sd 11:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.503809]  sdg: sdg1
[   69.518821] sd 11:0:0:0: [sdg] Attached SCSI disk
[   69.518859] sd 11:0:0:0: Attached scsi generic sg7 type 0
[   69.518947] scsi 12:0:0:0: Direct-Access     ATA      ST3500641AS      3.AA PQ: 0 ANSI: 5
[   69.518986] sd 12:0:0:0: [sdh] 976773168 512-byte hardware sectors (500108 MB)
[   69.518993] sd 12:0:0:0: [sdh] Write Protect is off
[   69.518995] sd 12:0:0:0: [sdh] Mode Sense: 00 3a 00 00
[   69.519007] sd 12:0:0:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.519034] sd 12:0:0:0: [sdh] 976773168 512-byte hardware sectors (500108 MB)
[   69.519042] sd 12:0:0:0: [sdh] Write Protect is off
[   69.519044] sd 12:0:0:0: [sdh] Mode Sense: 00 3a 00 00
[   69.519056] sd 12:0:0:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.519058]  sdh: sdh1
[   69.533443] sd 12:0:0:0: [sdh] Attached SCSI disk
[   69.533481] sd 12:0:0:0: Attached scsi generic sg8 type 0
[   69.533564] scsi 13:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-6 12.0 PQ: 0 ANSI: 5
[   69.533602] sd 13:0:0:0: [sdi] 976773168 512-byte hardware sectors (500108 MB)
[   69.533609] sd 13:0:0:0: [sdi] Write Protect is off
[   69.533611] sd 13:0:0:0: [sdi] Mode Sense: 00 3a 00 00
[   69.533623] sd 13:0:0:0: [sdi] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.533650] sd 13:0:0:0: [sdi] 976773168 512-byte hardware sectors (500108 MB)
[   69.533657] sd 13:0:0:0: [sdi] Write Protect is off
[   69.533659] sd 13:0:0:0: [sdi] Mode Sense: 00 3a 00 00
[   69.533670] sd 13:0:0:0: [sdi] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   69.533673]  sdi: sdi1
[   69.572240] sd 13:0:0:0: [sdi] Attached SCSI disk
[   69.572279] sd 13:0:0:0: Attached scsi generic sg9 type 0
[   69.572345] ACPI: PCI Interrupt 0000:07:07.0[A] -> GSI 23 (level, low) -> IRQ 20
[   69.622034] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f9084000-f90847ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   70.888811] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00cdcd6900001a4d]
[   72.709721] r8169: eth2: link up
[   72.709727] r8169: eth2: link up
[   73.241973] md: md0 stopped.
[   73.295361] md: bind<sdc1>
[   73.295496] md: bind<sdd1>
[   73.295605] md: bind<sde1>
[   73.295732] md: bind<sdf1>
[   73.295857] md: bind<sdg1>
[   73.295997] md: bind<sdh1>
[   73.296168] md: bind<sdi1>
[   73.296328] md: bind<sdb1>
[   73.650261] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   73.660406] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   73.841242] Linux agpgart interface v0.102 (c) Dave Jones
[   73.960517] agpgart: Detected an Intel G33 Chipset.
[   73.961380] agpgart: Detected 7164K stolen memory.
[   73.974112] agpgart: AGP aperture is 256M @ 0xe0000000
[   74.095494] input: PC Speaker as /class/input/input2
[   74.183492] raid5: device sdb1 operational as raid disk 0
[   74.183495] raid5: device sdi1 operational as raid disk 7
[   74.183497] raid5: device sdh1 operational as raid disk 6
[   74.183499] raid5: device sdg1 operational as raid disk 5
[   74.183501] raid5: device sdf1 operational as raid disk 4
[   74.183503] raid5: device sde1 operational as raid disk 3
[   74.183504] raid5: device sdd1 operational as raid disk 2
[   74.183506] raid5: device sdc1 operational as raid disk 1
[   74.183999] raid5: allocated 8368kB for md0
[   74.184001] raid5: raid level 5 set md0 active with 8 out of 8 devices, algorithm 2
[   74.184003] RAID5 conf printout:
[   74.184004]  --- rd:8 wd:8
[   74.184006]  disk 0, o:1, dev:sdb1
[   74.184007]  disk 1, o:1, dev:sdc1
[   74.184009]  disk 2, o:1, dev:sdd1
[   74.184010]  disk 3, o:1, dev:sde1
[   74.184011]  disk 4, o:1, dev:sdf1
[   74.184013]  disk 5, o:1, dev:sdg1
[   74.184014]  disk 6, o:1, dev:sdh1
[   74.184016]  disk 7, o:1, dev:sdi1
[   74.404597] NET: Registered protocol family 10
[   74.404671] lo: Disabled Privacy Extensions
[   74.509977] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   74.639792] parport_pc 00:0a: reported by Plug and Play ACPI
[   74.639836] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   75.061820] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   75.061839] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   75.269671] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   75.549355] lp0: using parport0 (interrupt-driven).
[   75.712897] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   76.109111] EXT3 FS on sda1, internal journal
[   77.392635] kjournald starting.  Commit interval 5 seconds
[   77.442421] EXT3 FS on md0, internal journal
[   77.442428] EXT3-fs: mounted filesystem with ordered data mode.
[   79.785549] input: Power Button (FF) as /class/input/input4
[   79.785565] ACPI: Power Button (FF) [PWRF]
[   79.785597] input: Power Button (CM) as /class/input/input5
[   79.785607] ACPI: Power Button (CM) [PWRB]
[   79.914901] No dock devices found.
[   81.493728] ppdev: user-space parallel port driver
[   81.614011] audit(1204886834.948:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5535 profile="/usr/sbin/cupsd"
[   83.608448] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   83.608452] apm: disabled - APM is not SMP safe.
[   83.957727] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   84.029723] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   84.103797] NFSD: starting 90-second grace period
[   84.614708] eth2: no IPv6 routers present
[   85.469446] Failure registering capabilities with primary security module.
[   85.762976] Bluetooth: Core ver 2.11
[   85.763019] NET: Registered protocol family 31
[   85.763021] Bluetooth: HCI device and connection manager initialized
[   85.763024] Bluetooth: HCI socket layer initialized
[   85.773790] Bluetooth: L2CAP ver 2.8
[   85.773793] Bluetooth: L2CAP socket layer initialized
[   85.825270] Bluetooth: RFCOMM socket layer initialized
[   85.825365] Bluetooth: RFCOMM TTY layer initialized
[   85.825367] Bluetooth: RFCOMM ver 1.8
root@RAMBO:/# 

```

---

### Post by SpaceTeddy on 2008-03-07
either i am blind, or the new controller card did not get detected... i take it you have... 17 disks in that computer now ? one boot (sda), 8 in one raid array(sdb-sdi), and want to create another one with another eight disks to it ?

unforteunatly, i have no idea so far... can you do a lspci please ? to see if the contoller shows up as hardware ?
also, this might be a driver problem - in that case i am less than useless :(

---

### Post by demiurgen on 2008-03-07
maybe i should try putting the controller card in a another machine and install a clean ubuntu... anyway here is what lspci says:```
root@RAMBO:/# lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
02:00.0 PCI bridge: Intel Corporation 41210 [Lanai] Serial to Parallel PCI Bridge (A-Segment Bridge) (rev 09)
02:00.2 PCI bridge: Intel Corporation 41210 [Lanai] Serial to Parallel PCI Bridge (B-Segment Bridge) (rev 09)
04:04.0 SCSI storage controller: HighPoint Technologies, Inc. RocketRAID 2320 SATA-II Controller (rev 09)
05:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:01.0 SCSI storage controller: Marvell Technology Group Ltd. MV88SX5081 8-port SATA I PCI-X Controller (rev 03)
07:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
root@RAMBO:/# 

```
and here are some images that show what comes up in hardware information:

---

### Post by fjgaude on 2008-03-07
We can see the RocketRAID card being recognized by Ubuntu with lspci comand. But do you have driver software to install? You setup the eight-disk array using HighPoint software? How was this done? In Ubuntu? How? Oh, I see... nothing has been done, eh?

---

