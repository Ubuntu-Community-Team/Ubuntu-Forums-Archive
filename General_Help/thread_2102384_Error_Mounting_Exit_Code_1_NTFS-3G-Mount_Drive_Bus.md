---
title: "Error Mounting Exit Code 1 NTFS-3G-Mount Drive Busy"
date: 2013-01-07
forum: General Help
---

### Post by resevil83 on 2013-01-07
I am trying to help out a friend with an odd issue. He has two external hard drives he was using as storage on a I-Mac. He had several terabytes of information on each drive, then one day the drives didn't show up on his mac. I believe he may have switched the drives from one mac to another which may have caused an issue.

So I took the drives to my house to try and access them to back up the data onto a new external hard drive. I wanted to harness the power of Linux to get the data back. I burned a copy of Knoppix 7.0.5 to a cd and tried to see the drives. I only had one of them plugged in and saw two seperate "raid" devices. I saw my internal drives and could access those fine. The error code when I tried to click on the raid drives was something along the lines of "Error Mounting Exit Code 1 NTFS-3G-Mount Drive Busy" There was more to it than that, but not much. 

Basically, any help would be much appreciated. I did some diving into this a bit, but I'm not comfortable in Linux yet. I think I may have found the problem but would like some guidance. In this thread "Patsissons" ended up stripping the raid information from the metadata. Even though he gives the commands, I do not know how to input these into the terminal in knoppix to get it to work. Also I do not know how to target these commands at the external device and not my internal drives. I don't want to mess those up! :)

Before I jump into that, because it may not be the problem, I will try and provide some information that I found in a debugging wikipedia for ubuntu devices. I will input that data in my next post.

---

### Post by resevil83 on 2013-01-07
ID_WWN=0x5000c5003f6c77c9
ID_WWN_WITH_EXTENSION=0x5000c5003f6c77c9
MAJOR=8
MINOR=50
SEQNUM=2952
SUBSYSTEM=block
UDEV_LOG=3
UDISKS_PRESENTATION_NOPOLICY=0
USEC_INITIALIZED=2441988304

UDEV  [2442.038288] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd1 (block)
ACTION=add
DEVLINKS=/dev/disk/by-id/ata-ST3000DM001-9YN166_Z1F0D3D7-part1 /dev/disk/by-id/scsi-SSeagate_GoFlex_Desk_Mac_NA0PGY4H-part1 /dev/disk/by-id/wwn-0x5000c5003f6c77c9-part1 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1
DEVNAME=/dev/sdd1
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd1
DEVTYPE=partition
ID_ATA=^C





DEVICES.TXT
brw-rw---- 1 root disk   8,   0 Jan  7 00:21 /dev/sda
brw-rw---- 1 root disk   8,   1 Jan  7 00:21 /dev/sda1
brw-rw---- 1 root disk   8,  10 Jan  7 00:20 /dev/sda10
brw-rw---- 1 root disk   8,  11 Jan  7 00:20 /dev/sda11
brw-rw---- 1 root disk   8,  12 Jan  7 00:20 /dev/sda12
brw-rw---- 1 root disk   8,  13 Jan  7 00:20 /dev/sda13
brw-rw---- 1 root disk   8,  14 Jan  7 00:20 /dev/sda14
brw-rw---- 1 root disk   8,  15 Jan  7 00:20 /dev/sda15
brw-rw---- 1 root fuse   8,   2 Jan  7 00:24 /dev/sda2
brw-rw---- 1 root fuse   8,   3 Jan  7 00:24 /dev/sda3
brw-rw---- 1 root disk   8,   4 Jan  7 00:20 /dev/sda4
brw-rw---- 1 root disk   8,   5 Jan  7 00:20 /dev/sda5
brw-rw---- 1 root disk   8,   6 Jan  7 00:20 /dev/sda6
brw-rw---- 1 root disk   8,   7 Jan  7 00:20 /dev/sda7
brw-rw---- 1 root disk   8,   8 Jan  7 00:20 /dev/sda8
brw-rw---- 1 root disk   8,   9 Jan  7 00:20 /dev/sda9
brw-rw---- 1 root disk   8,  16 Jan  7 00:21 /dev/sdb
brw-rw---T 1 root fuse   8,  17 Jan  7 00:40 /dev/sdb1
brw-rw---- 1 root disk   8,  26 Jan  7 00:20 /dev/sdb10
brw-rw---- 1 root disk   8,  27 Jan  7 00:20 /dev/sdb11
brw-rw---- 1 root disk   8,  28 Jan  7 00:20 /dev/sdb12
brw-rw---- 1 root disk   8,  29 Jan  7 00:20 /dev/sdb13
brw-rw---- 1 root disk   8,  30 Jan  7 00:20 /dev/sdb14
brw-rw---- 1 root disk   8,  31 Jan  7 00:20 /dev/sdb15
brw-rw---- 1 root disk   8,  18 Jan  7 00:20 /dev/sdb2
brw-rw---- 1 root disk   8,  19 Jan  7 00:20 /dev/sdb3
brw-rw---- 1 root disk   8,  20 Jan  7 00:20 /dev/sdb4
brw-rw---- 1 root disk   8,  21 Jan  7 00:20 /dev/sdb5
brw-rw---- 1 root disk   8,  22 Jan  7 00:20 /dev/sdb6
brw-rw---- 1 root disk   8,  23 Jan  7 00:20 /dev/sdb7
brw-rw---- 1 root disk   8,  24 Jan  7 00:20 /dev/sdb8
brw-rw---- 1 root disk   8,  25 Jan  7 00:20 /dev/sdb9
brw-rw---- 1 root disk   8,  32 Jan  7 00:21 /dev/sdc
brw-rw---T 1 root fuse   8,  33 Jan  7 00:25 /dev/sdc1
brw-rw---- 1 root disk   8,  42 Jan  7 00:20 /dev/sdc10
brw-rw---- 1 root disk   8,  43 Jan  7 00:20 /dev/sdc11
brw-rw---- 1 root disk   8,  44 Jan  7 00:20 /dev/sdc12
brw-rw---- 1 root disk   8,  45 Jan  7 00:20 /dev/sdc13
brw-rw---- 1 root disk   8,  46 Jan  7 00:20 /dev/sdc14
brw-rw---- 1 root disk   8,  47 Jan  7 00:20 /dev/sdc15
brw-rw---- 1 root disk   8,  34 Jan  7 00:20 /dev/sdc2
brw-rw---- 1 root disk   8,  35 Jan  7 00:20 /dev/sdc3
brw-rw---- 1 root disk   8,  36 Jan  7 00:20 /dev/sdc4
brw-rw---- 1 root disk   8,  37 Jan  7 00:20 /dev/sdc5
brw-rw---- 1 root disk   8,  38 Jan  7 00:20 /dev/sdc6
brw-rw---- 1 root disk   8,  39 Jan  7 00:20 /dev/sdc7
brw-rw---- 1 root disk   8,  40 Jan  7 00:20 /dev/sdc8
brw-rw---- 1 root disk   8,  41 Jan  7 00:20 /dev/sdc9
brw-rw---T 1 root floppy 8,  48 Jan  7 01:00 /dev/sdd
brw-rw---T 1 root floppy 8,  49 Jan  7 01:00 /dev/sdd1
brw-rw---- 1 root disk   8,  58 Jan  7 00:20 /dev/sdd10
brw-rw---- 1 root disk   8,  59 Jan  7 00:20 /dev/sdd11
brw-rw---- 1 root disk   8,  60 Jan  7 00:20 /dev/sdd12
brw-rw---- 1 root disk   8,  61 Jan  7 00:20 /dev/sdd13
brw-rw---- 1 root disk   8,  62 Jan  7 00:20 /dev/sdd14
brw-rw---- 1 root disk   8,  63 Jan  7 00:20 /dev/sdd15
brw-rw---T 1 root floppy 8,  50 Jan  7 01:00 /dev/sdd2
brw-rw---- 1 root disk   8,  51 Jan  7 00:20 /dev/sdd3
brw-rw---- 1 root disk   8,  52 Jan  7 00:20 /dev/sdd4
brw-rw---- 1 root disk   8,  53 Jan  7 00:20 /dev/sdd5
brw-rw---- 1 root disk   8,  54 Jan  7 00:20 /dev/sdd6
brw-rw---- 1 root disk   8,  55 Jan  7 00:20 /dev/sdd7
brw-rw---- 1 root disk   8,  56 Jan  7 00:20 /dev/sdd8
brw-rw---- 1 root disk   8,  57 Jan  7 00:20 /dev/sdd9
brw-rw---- 1 root disk   8,  64 Jan  7 00:20 /dev/sde
brw-rw---- 1 root disk   8,  65 Jan  7 00:20 /dev/sde1
brw-rw---- 1 root disk   8,  74 Jan  7 00:20 /dev/sde10
brw-rw---- 1 root disk   8,  75 Jan  7 00:20 /dev/sde11
brw-rw---- 1 root disk   8,  76 Jan  7 00:20 /dev/sde12
brw-rw---- 1 root disk   8,  77 Jan  7 00:20 /dev/sde13
brw-rw---- 1 root disk   8,  78 Jan  7 00:20 /dev/sde14
brw-rw---- 1 root disk   8,  79 Jan  7 00:20 /dev/sde15
brw-rw---- 1 root disk   8,  66 Jan  7 00:20 /dev/sde2
brw-rw---- 1 root disk   8,  67 Jan  7 00:20 /dev/sde3
brw-rw---- 1 root disk   8,  68 Jan  7 00:20 /dev/sde4
brw-rw---- 1 root disk   8,  69 Jan  7 00:20 /dev/sde5
brw-rw---- 1 root disk   8,  70 Jan  7 00:20 /dev/sde6
brw-rw---- 1 root disk   8,  71 Jan  7 00:20 /dev/sde7
brw-rw---- 1 root disk   8,  72 Jan  7 00:20 /dev/sde8
brw-rw---- 1 root disk   8,  73 Jan  7 00:20 /dev/sde9
brw-rw---- 1 root disk   8,  80 Jan  7 00:20 /dev/sdf
brw-rw---- 1 root disk   8,  81 Jan  7 00:20 /dev/sdf1
brw-rw---- 1 root disk   8,  90 Jan  7 00:20 /dev/sdf10
brw-rw---- 1 root disk   8,  91 Jan  7 00:20 /dev/sdf11
brw-rw---- 1 root disk   8,  92 Jan  7 00:20 /dev/sdf12
brw-rw---- 1 root disk   8,  93 Jan  7 00:20 /dev/sdf13
brw-rw---- 1 root disk   8,  94 Jan  7 00:20 /dev/sdf14
brw-rw---- 1 root disk   8,  95 Jan  7 00:20 /dev/sdf15
brw-rw---- 1 root disk   8,  82 Jan  7 00:20 /dev/sdf2
brw-rw---- 1 root disk   8,  83 Jan  7 00:20 /dev/sdf3
brw-rw---- 1 root disk   8,  84 Jan  7 00:20 /dev/sdf4
brw-rw---- 1 root disk   8,  85 Jan  7 00:20 /dev/sdf5
brw-rw---- 1 root disk   8,  86 Jan  7 00:20 /dev/sdf6
brw-rw---- 1 root disk   8,  87 Jan  7 00:20 /dev/sdf7
brw-rw---- 1 root disk   8,  88 Jan  7 00:20 /dev/sdf8
brw-rw---- 1 root disk   8,  89 Jan  7 00:20 /dev/sdf9
brw-rw---- 1 root disk   8,  96 Jan  7 00:20 /dev/sdg
brw-rw---- 1 root disk   8,  97 Jan  7 00:20 /dev/sdg1
brw-rw---- 1 root disk   8, 106 Jan  7 00:20 /dev/sdg10
brw-rw---- 1 root disk   8, 107 Jan  7 00:20 /dev/sdg11
brw-rw---- 1 root disk   8, 108 Jan  7 00:20 /dev/sdg12
brw-rw---- 1 root disk   8, 109 Jan  7 00:20 /dev/sdg13
brw-rw---- 1 root disk   8, 110 Jan  7 00:20 /dev/sdg14
brw-rw---- 1 root disk   8, 111 Jan  7 00:20 /dev/sdg15
brw-rw---- 1 root disk   8,  98 Jan  7 00:20 /dev/sdg2
brw-rw---- 1 root disk   8,  99 Jan  7 00:20 /dev/sdg3
brw-rw---- 1 root disk   8, 100 Jan  7 00:20 /dev/sdg4
brw-rw---- 1 root disk   8, 101 Jan  7 00:20 /dev/sdg5
brw-rw---- 1 root disk   8, 102 Jan  7 00:20 /dev/sdg6
brw-rw---- 1 root disk   8, 103 Jan  7 00:20 /dev/sdg7
brw-rw---- 1 root disk   8, 104 Jan  7 00:20 /dev/sdg8
brw-rw---- 1 root disk   8, 105 Jan  7 00:20 /dev/sdg9
brw-rw---- 1 root disk   8, 112 Jan  7 00:20 /dev/sdh
brw-rw---- 1 root disk   8, 113 Jan  7 00:20 /dev/sdh1
brw-rw---- 1 root disk   8, 122 Jan  7 00:20 /dev/sdh10
brw-rw---- 1 root disk   8, 123 Jan  7 00:20 /dev/sdh11
brw-rw---- 1 root disk   8, 124 Jan  7 00:20 /dev/sdh12
brw-rw---- 1 root disk   8, 125 Jan  7 00:20 /dev/sdh13
brw-rw---- 1 root disk   8, 126 Jan  7 00:20 /dev/sdh14
brw-rw---- 1 root disk   8, 127 Jan  7 00:20 /dev/sdh15
brw-rw---- 1 root disk   8, 114 Jan  7 00:20 /dev/sdh2
brw-rw---- 1 root disk   8, 115 Jan  7 00:20 /dev/sdh3
brw-rw---- 1 root disk   8, 116 Jan  7 00:20 /dev/sdh4
brw-rw---- 1 root disk   8, 117 Jan  7 00:20 /dev/sdh5
brw-rw---- 1 root disk   8, 118 Jan  7 00:20 /dev/sdh6
brw-rw---- 1 root disk   8, 119 Jan  7 00:20 /dev/sdh7
brw-rw---- 1 root disk   8, 120 Jan  7 00:20 /dev/sdh8
brw-rw---- 1 root disk   8, 121 Jan  7 00:20 /dev/sdh9


DMESG.TXT
[    2.780670] ALSA device list:
[    2.780673]   No soundcards found.
[    2.780747] Freeing unused kernel memory: 588k freed
[    2.780964] Write protecting the kernel text: 6180k
[    2.781012] Write protecting the kernel read-only data: 2136k
[    3.063352] usb 1-3: new high-speed USB device number 2 using ehci_hcd
[    3.193112] usb 1-3: New USB device found, idVendor=0bda, idProduct=8187
[    3.193118] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.193122] usb 1-3: Product: RTL8187_Wireless
[    3.193126] usb 1-3: Manufacturer: Manufacturer_Realtek_RTL8187_
[    3.193130] usb 1-3: SerialNumber: 0015AF0F2FCE
[    3.243458] firewire_core 0000:05:03.0: created device fw0: GUID 0011d800014d68fb, S400
[    3.300016] usb 2-5: new high-speed USB device number 2 using ehci_hcd
[    4.033326] FAT-fs (sr0): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[    5.180142] ISO 9660 Extensions: Microsoft Joliet Level 3
[    5.319872] ISO 9660 Extensions: RRIP_1991A
[    6.271406] cloop: losetup_file: 15549 blocks, 131072 bytes/block, largest block is 131098 bytes.
[    6.790533] ISO 9660 Extensions: RRIP_1991A
[    6.792159] aufs test_add:264:busybox[1848]: uid/gid/perm /KNOPPIX 0/0/0755, 0/0/01777
[   18.406684] usb 2-5: device descriptor read/64, error -110
[   26.391013] [drm] radeon kernel modesetting enabled.
[   26.391215] [drm] initializing kernel modesetting (CEDAR 0x1002:0x68F9 0x1043:0x03C2).
[   26.391238] [drm] register mmio base: 0xFE8C0000
[   26.391239] [drm] register mmio size: 131072
[   26.391445] ATOM BIOS: 68F9.12.20.0.46.AS01
[   26.391521] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   26.391524] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   26.394658] [drm] Detected VRAM RAM=512M, BAR=256M
[   26.394662] [drm] RAM width 64bits DDR
[   26.394731] [TTM] Zone  kernel: Available graphics memory: 435964 kiB
[   26.394733] [TTM] Zone highmem: Available graphics memory: 1684992 kiB
[   26.394735] [TTM] Initializing pool allocator
[   26.394759] [drm] radeon: 512M of VRAM memory ready
[   26.394760] [drm] radeon: 512M of GTT memory ready.
[   26.394779] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   26.394780] [drm] Driver supports precise vblank timestamp query.
[   26.394823] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   26.394834] radeon 0000:01:00.0: radeon: using MSI.
[   26.394857] [drm] radeon: irq initialized.
[   26.394861] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   26.395185] [drm] probing gen 2 caps for device 8086:29c1 = 1/0
[   26.395225] [drm] Loading CEDAR Microcode
[   26.579973] ACPI Warning: 0x00000400-0x0000041f SystemIO conflicts with Region \SMRG 1 (20120711/utaddress-251)
[   26.579980] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   26.969216] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   26.969255] r8169 0000:05:04.0: (unregistered net_device): not PCI Express
[   26.969484] r8169 0000:05:04.0: eth0: RTL8169sc/8110sc at 0xf8346c00, 00:1b:fc:63:30:75, XID 18000000 IRQ 16
[   26.969488] r8169 0000:05:04.0: eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
[   27.120125] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   27.313595] sky2: driver version 1.30
[   27.313643] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 3
[   27.313729] sky2 0000:02:00.0: irq 46 for MSI/MSI-X
[   27.313959] sky2 0000:02:00.0: eth1: addr 00:1b:fc:63:34:ee
[   27.396880] gpio_ich: GPIO from 195 to 255 on gpio_ich
[   29.142654] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   29.142756] radeon 0000:01:00.0: WB enabled
[   29.142760] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xff8a0c00
[   29.159037] [drm] ring test on 0 succeeded in 1 usecs
[   29.159170] [drm] ib test on ring 0 succeeded in 0 usecs
[   29.159550] [drm] Radeon Display Connectors
[   29.159552] [drm] Connector 0:
[   29.159554] [drm]   HDMI-A-1
[   29.159555] [drm]   HPD1
[   29.159557] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   29.159559] [drm]   Encoders:
[   29.159560] [drm]     DFP1: INTERNAL_UNIPHY1
[   29.159561] [drm] Connector 1:
[   29.159563] [drm]   DVI-I-1
[   29.159564] [drm]   HPD4
[   29.159566] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[   29.159567] [drm]   Encoders:
[   29.159569] [drm]     DFP2: INTERNAL_UNIPHY
[   29.159570] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   29.159572] [drm] Connector 2:
[   29.159573] [drm]   VGA-1
[   29.159575] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   29.159576] [drm]   Encoders:
[   29.159578] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   29.159618] [drm] Internal thermal controller without fan control
[   29.159671] [drm] radeon: power management initialized
[   29.213629] [drm] fb mappable at 0xD0142000
[   29.213633] [drm] vram apper at 0xD0000000
[   29.213635] [drm] size 7299072
[   29.213637] [drm] fb depth is 24
[   29.213639] [drm]    pitch is 6912
[   29.213696] fbcon: radeondrmfb (fb0) is primary device
[   29.439322] Console: switching to colour frame buffer device 210x65
[   29.448158] fb0: radeondrmfb frame buffer device
[   29.448160] drm: registered panic notifier
[   29.448164] [drm] Initialized radeon 2.24.0 20080528 for 0000:01:00.0 on minor 0
[   29.448249] snd_hda_intel 0000:01:00.1: irq 47 for MSI/MSI-X
[   33.616683] usb 2-5: device descriptor read/64, error -110
[   33.826682] usb 2-5: new high-speed USB device number 3 using ehci_hcd
[   45.439001] Adding 2527484k swap on /dev/zram0.  Priority:0 extents:1 across:2527484k SS
[   48.933353] usb 2-5: device descriptor read/64, error -110
[   49.387937] Floppy drive(s): fd0 is 1.44M
[   49.403679] FDC 0 is a post-1991 82077
[   54.283809] Serial: 8250/16550 driver, 4 ports, IRQ sharing disabled
[   54.292005] cfg80211: Calling CRDA to update world regulatory domain
[   54.304393] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   55.753219] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   57.896079] coretemp coretemp.0: Using relative temperature scale!
[   57.896111] coretemp coretemp.0: Using relative temperature scale!
[   57.896147] coretemp coretemp.0: Using relative temperature scale!
[   57.896174] coretemp coretemp.0: Using relative temperature scale!
[   60.331145] ieee80211 phy0: Selected rate control algorithm 'pid'
[   60.331292] ieee80211 phy0: hwaddr 00:15:af:0f:2f:ce, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   60.342144] rtl8187: Customer ID is 0x00
[   60.342191] Registered led device: rtl8187-phy0::radio
[   60.342209] Registered led device: rtl8187-phy0::tx
[   60.342228] Registered led device: rtl8187-phy0::rx
[   60.342628] rtl8187: wireless switch is on
[   60.342670] usbcore: registered new interface driver rtl8187
[   64.143346] usb 2-5: device descriptor read/64, error -110
[   64.353346] usb 2-5: new high-speed USB device number 4 using ehci_hcd
[   65.946679] r8169 0000:05:04.0: Refused to change power state, currently in D0
[   66.159055] cfg80211: World regulatory domain updated:
[   66.159059] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   66.159061] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   66.159063] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   66.159065] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   66.159067] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   66.159069] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   69.370168] usb 2-5: device descriptor read/8, error -110
[   69.850683] sky2 0000:02:00.0: eth1: enabling interface
[   69.864182] r8169 0000:05:04.0: eth0: link down
[   69.864187] r8169 0000:05:04.0: eth0: link down
[   74.486795] usb 2-5: device descriptor read/8, error -110
[   74.696678] usb 2-5: new high-speed USB device number 5 using ehci_hcd
[   79.713428] usb 2-5: device descriptor read/8, error -110
[   84.830053] usb 2-5: device descriptor read/8, error -110
[   84.933347] hub 2-0:1.0: unable to enumerate USB device on port 5
[   85.473340] usb 8-1: new full-speed USB device number 2 using uhci_hcd
[  100.633352] usb 8-1: device descriptor read/64, error -110
[  111.264298] lp: driver loaded but no devices found
[  111.268316] ppdev: user-space parallel port driver
[  112.310497] NET: Registered protocol family 10
[  112.310764] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  112.310803] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  112.310843] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  115.843340] usb 8-1: device descriptor read/64, error -110
[  116.053338] usb 8-1: new full-speed USB device number 3 using uhci_hcd
[  131.160003] usb 8-1: device descriptor read/64, error -110
[  146.370008] usb 8-1: device descriptor read/64, error -110
[  146.580000] usb 8-1: new full-speed USB device number 4 using uhci_hcd
[  151.598684] usb 8-1: device descriptor read/8, error -110
[  156.714731] usb 8-1: device descriptor read/8, error -110
[  156.923332] usb 8-1: new full-speed USB device number 5 using uhci_hcd
[  161.941727] usb 8-1: device descriptor read/8, error -110
[  167.057726] usb 8-1: device descriptor read/8, error -110
[  167.160005] hub 8-0:1.0: unable to enumerate USB device on port 1
[  167.386665] usb 8-2: new low-speed USB device number 6 using uhci_hcd
[  167.554729] usb 8-2: New USB device found, idVendor=046d, idProduct=c517
[  167.554735] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  167.554739] usb 8-2: Product: USB Receiver
[  167.554743] usb 8-2: Manufacturer: Logitech
[  167.572106] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input2
[  167.572202] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2/input0
[  167.606785] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[  167.607696] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.1/input/input3
[  167.607842] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2/input1
[  471.547439] wlan0: authenticate with 00:02:6f:e7:72:12
[  471.641575] wlan0: send auth to 00:02:6f:e7:72:12 (try 1/3)
[  471.643333] wlan0: authenticated
[  471.643523] rtl8187 1-3:1.0: wlan0: disabling HT as WMM/QoS is not supported
[  471.693303] wlan0: associate with 00:02:6f:e7:72:12 (try 1/3)
[  471.695457] wlan0: RX AssocResp from 00:02:6f:e7:72:12 (capab=0xc31 status=0 aid=4)
[  471.695947] wlan0: associated
[  471.695976] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  476.427566] wlan0: deauthenticating from 00:02:6f:e7:72:12 by local choice (reason=3)
[  476.547362] cfg80211: Calling CRDA to update world regulatory domain
[  476.553711] cfg80211: World regulatory domain updated:
[  476.553715] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  476.553719] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  476.553722] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  476.553725] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  476.553728] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  476.553731] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  480.967358] wlan0: authenticate with 00:02:6f:e7:72:12
[  481.061583] wlan0: send auth to 00:02:6f:e7:72:12 (try 1/3)
[  481.063455] wlan0: authenticated
[  481.063691] rtl8187 1-3:1.0: wlan0: disabling HT as WMM/QoS is not supported
[  481.113299] wlan0: associate with 00:02:6f:e7:72:12 (try 1/3)
[  481.115456] wlan0: RX AssocResp from 00:02:6f:e7:72:12 (capab=0xc31 status=0 aid=4)
[  481.115950] wlan0: associated
[ 2430.309777] usb 2-5: new high-speed USB device number 7 using ehci_hcd
[ 2430.434141] usb 2-5: New USB device found, idVendor=0bc2, idProduct=6095
[ 2430.434147] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2430.434151] usb 2-5: Product: GoFlex Desk Mac
[ 2430.434155] usb 2-5: Manufacturer: Seagate
[ 2430.434159] usb 2-5: SerialNumber: NA0PGY4H
[ 2430.434567] scsi13 : usb-storage 2-5:1.0
[ 2436.517683] scsi 13:0:0:0: Direct-Access     Seagate  GoFlex Desk Mac  0129 PQ: 0 ANSI: 6
[ 2436.517938] sd 13:0:0:0: Attached scsi generic sg4 type 0
[ 2441.604538] sd 13:0:0:0: [sdd] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[ 2441.605403] sd 13:0:0:0: [sdd] Write Protect is off
[ 2441.605408] sd 13:0:0:0: [sdd] Mode Sense: 5f 00 10 08
[ 2441.606277] sd 13:0:0:0: [sdd] Write cache: enabled, read cache: enabled, supports DPO and FUA
[ 2441.607159] sd 13:0:0:0: [sdd] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[ 2441.669457]  sdd: sdd1 sdd2
[ 2441.670411] sd 13:0:0:0: [sdd] 732566645 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[ 2441.671909] sd 13:0:0:0: [sdd] Attached SCSI disk


LSHAL.TXT

Dumping 155 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/computer'
  info.addons = {'hald-addon-cpufreq', 'hald-addon-acpi'} (string list)
  info.callouts.add = {'hal-storage-cleanup-all-mountpoints'} (string list)
  info.capabilities = {'cpufreq_control'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq'} (string list)
  info.product = 'Computer'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = {'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = {'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = {'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = {'i', 'i', '', '', '', 'b'} (string list)
  org.freedesktop.Hal.version = '0.5.14'  (string)
  org.freedesktop.Hal.version.major = 0  (0x0)  (int)
  org.freedesktop.Hal.version.micro = 14  (0xe)  (int)
  org.freedesktop.Hal.version.minor = 5  (0x5)  (int)
  power_management.acpi.linux.version = '20120711'  (string)
  power_management.can_hibernate = true  (bool)
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = true  (bool)
  power_management.is_powersave_set = false  (bool)
  power_management.quirk.dpms_on = true  (bool)
  power_management.quirk.dpms_suspend = true  (bool)
  power_management.quirk.vbe_post = true  (bool)
  power_management.quirk.vbemode_restore = true  (bool)
  power_management.quirk.vbestate_restore = true  (bool)
  power_management.quirk.vga_mode_3 = true  (bool)
  power_management.type = 'acpi'  (string)
  system.board.product = 'P5K Deluxe'  (string)
  system.board.serial = 'MS1C75B5F300191'  (string)
  system.board.vendor = 'ASUSTeK Computer INC.'  (string)
  system.board.version = 'Rev 1.xx'  (string)
  system.chassis.manufacturer = 'Chassis Manufacture'  (string)
  system.chassis.type = 'Desktop'  (string)
  system.firmware.release_date = '06/15/2007'  (string)
  system.firmware.vendor = 'American Megatrends Inc.'  (string)
  system.firmware.version = '0404'  (string)
  system.formfactor = 'desktop'  (string)
  system.hardware.primary_video.product = 26873  (0x68f9)  (int)
  system.hardware.primary_video.vendor = 4098  (0x1002)  (int)
  system.hardware.product = 'P5K Deluxe'  (string)
  system.hardware.serial = 'System Serial Number'  (string)
  system.hardware.uuid = 'A0880011-D800-014D-68FB-001BFC633075'  (string)
  system.hardware.vendor = 'System manufacturer'  (string)
  system.hardware.version = 'System Version'  (string)
  system.kernel.machine = 'i686'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '3.6.11'  (string)
  system.kernel.version.major = 3  (0x3)  (int)
  system.kernel.version.micro = 11  (0xb)  (int)
  system.kernel.version.minor = 6  (0x6)  (int)

udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  alsa.device_file = '/dev/snd/timer'  (string)
  alsa.type = 'timer'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Timer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'  (string)
  linux.device_file = '/dev/snd/timer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/timer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'  (string)
  linux.device_file = '/dev/sequencer2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer2'  (string)
  oss.device_file = '/dev/sequencer2'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'  (string)
  linux.device_file = '/dev/sequencer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer'  (string)
  oss.device_file = '/dev/sequencer'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  alsa.device_file = '/dev/snd/seq'  (string)
  alsa.type = 'sequencer'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'  (string)
  linux.device_file = '/dev/snd/seq'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/seq'  (string)

udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  info.capabilities = {'net', 'net.loopback'} (string list)
  info.category = 'net.loopback'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Loopback device Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_computer_loopback'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/lo'  (string)
  net.address = '00:00:00:00:00:00'  (string)
  net.arp_proto_hw_id = 772  (0x304)  (int)
  net.interface = 'lo'  (string)
  net.linux.ifindex = 1  (0x1)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_drm__null__ttm'
  info.capabilities = {'drm'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.subsystem = 'drm'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_drm__null__ttm'  (string)
  linux.device_file = ''  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/virtual/drm/ttm'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'  (string)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Power Button'  (string)
  linux.device_file = '/dev/input/event0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event1'  (string)
  input.product = 'Power Button'  (string)
  linux.device_file = '/dev/input/event1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'System Board'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0e'  (string)
  pnp.description = 'System Board'  (string)
  pnp.id = 'PNP0c01'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_2'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0d'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  info.linux.driver = 'i8042 kbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0c'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.id = 'PNP0303'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0b'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (PNP0103)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  pnp.id = 'PNP0103'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PC standard floppy disk controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:06'  (string)
  pnp.description = 'PC standard floppy disk controller'  (string)
  pnp.id = 'PNP0700'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.description = 'Math Coprocessor'  (string)
  pnp.id = 'PNP0c04'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)
  pnp.description = 'AT-style speaker sound'  (string)
  pnp.id = 'PNP0800'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  info.linux.driver = 'rtc_cmos'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT Real-Time Clock'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:03'  (string)
  pnp.description = 'AT Real-Time Clock'  (string)
  pnp.id = 'PNP0b00'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT DMA Controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02'  (string)
  pnp.description = 'AT DMA Controller'  (string)
  pnp.id = 'PNP0200'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'System Board'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:01'  (string)
  pnp.description = 'System Board'  (string)
  pnp.id = 'PNP0c01'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (PNP0a08)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:00'  (string)
  pnp.id = 'PNP0a08'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  info.linux.driver = 'serial8250'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250'  (string)
  platform.id = 'serial8250'  (string)

udi = '/org/freedesktop/Hal/devices/platform_regulatory_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (regulatory.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_regulatory_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/regulatory.0'  (string)
  platform.id = 'regulatory.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_reg_dummy'
  info.linux.driver = 'reg-dummy'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (reg-dummy)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_reg_dummy'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/reg-dummy'  (string)
  platform.id = 'reg-dummy'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr'  (string)
  platform.id = 'pcspkr'  (string)

udi = '/org/freedesktop/Hal/devices/platform_microcode'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (microcode)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_microcode'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/microcode'  (string)
  platform.id = 'microcode'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042'
  info.linux.driver = 'i8042'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'  (string)
  serio.description = 'i8042 KBD port'  (string)
  serio.id = 'serio0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_floppy_0'
  info.linux.driver = 'floppy'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (floppy.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_floppy_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/floppy.0'  (string)
  platform.id = 'floppy.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_coretemp_0'
  info.linux.driver = 'coretemp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (coretemp.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_coretemp_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/coretemp.0'  (string)
  platform.id = 'coretemp.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_alarmtimer'
  info.linux.driver = 'alarmtimer'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (alarmtimer)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_alarmtimer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/alarmtimer'  (string)
  platform.id = 'alarmtimer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2926'
  info.linux.driver = 'ata_piix'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) 2 port SATA Controller [IDE mode]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2926'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 133  (0x85)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5'  (string)
  pci.product = '82801I (ICH9 Family) 2 port SATA Controller [IDE mode]'  (string)
  pci.product_id = 10534  (0x2926)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2926'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/ata6/host5/scsi_host/host5'  (string)
  scsi_host.host = 5  (0x5)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2926'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/ata5/host4'  (string)
  scsi_host.host = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/ata5/host4/scsi_host/host4'  (string)
  scsi_host.host = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/ata5/host4/target4:0:0/4:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 4  (0x4)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'HDS725050KLA360'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_HDS725050KLA360_KRVN67ZAH1GEGF'
  block.device = '/dev/sda'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_HDS725050KLA360_KRVN67ZAH1GEGF'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host_scsi_device_lun0'  (string)
  info.product = 'HDS725050KLA360'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_HDS725050KLA360_KRVN67ZAH1GEGF'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/ata5/host4/target4:0:0/4:0:0:0/block/sda'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = 'K2AOABA5'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'HDS725050KLA360'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 500107862016  (0x7470c06000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'HDS725050KLA360_KRVN67ZAH1GEGF'  (string)
  storage.size = 500107862016  (0x7470c06000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_002A2ECE2A2EC090'
  block.device = '/dev/sda3'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 3  (0x3)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_HDS725050KLA360_KRVN67ZAH1GEGF'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_HDS725050KLA360_KRVN67ZAH1GEGF'  (string)
  info.product = 'NoRaid'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_002A2ECE2A2EC090'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/ata5/host4/target4:0:0/4:0:0:0/block/sda/sda3'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = 'NoRaid'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detach', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = '/media/sda3'  (string)
  volume.num_blocks = 771858432  (0x2e01a000)  (uint64)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 3  (0x3)  (int)
  volume.partition.start = 104915271680  (0x186d700000)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 395191517184  (0x5c03400000)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '002A2ECE2A2EC090'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_07D6_0512'
  block.device = '/dev/sda1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_HDS725050KLA360_KRVN67ZAH1GEGF'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_HDS725050KLA360_KRVN67ZAH1GEGF'  (string)
  info.product = 'DellUtility'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_07D6_0512'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/ata5/host4/target4:0:0/4:0:0:0/block/sda/sda1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'vfat'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = 'FAT16'  (string)
  volume.ignore = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = 'DellUtility'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'shortname=', 'codepage=', 'iocharset=', 'umask=', 'dmask=', 'fmask=', 'uid=', 'flush'} (string list)
  volume.mount_point = ''  (string)
  volume.num_blocks = 112392  (0x1b708)  (uint64)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.size = 57544704  (0x36e1000)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '07D6-0512'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_86B6319CB6318DA5'
  block.device = '/dev/sda2'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 2  (0x2)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_HDS725050KLA360_KRVN67ZAH1GEGF'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_HDS725050KLA360_KRVN67ZAH1GEGF'  (string)
  info.product = 'Volume (ntfs)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_86B6319CB6318DA5'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/ata5/host4/target4:0:0/4:0:0:0/block/sda/sda2'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detach', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = '/media/sda2'  (string)
  volume.num_blocks = 204800000  (0xc350000)  (uint64)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.partition.start = 57671680  (0x3700000)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 104857600000  (0x186a000000)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '86B6319CB6318DA5'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2926_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/ata5/host4/target4:0:0/4:0:0:0/scsi_generic/sg1'  (string)
  scsi_generic.device = '/dev/sg1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2930'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) SMBus Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2930'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 5  (0x5)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'  (string)
  pci.product = '82801I (ICH9 Family) SMBus Controller'  (string)
  pci.product_id = 10544  (0x2930)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2920'
  info.linux.driver = 'ata_piix'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2920'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 143  (0x8f)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'  (string)
  pci.product = '82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]'  (string)
  pci.product_id = 10528  (0x2920)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2920'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/scsi_host/host3'  (string)
  scsi_host.host = 3  (0x3)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2920'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/ata3/host2'  (string)
  scsi_host.host = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/scsi_host/host2'  (string)
  scsi_host.host = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:1/2:0:1:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 2  (0x2)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'DRW-24B1ST   a'  (string)
  scsi.target = 1  (0x1)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'ASUS'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_ASUS_DRW_24B1ST_a_ABD0CL289552'
  block.device = '/dev/sr0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_ASUS_DRW_24B1ST_a_ABD0CL289552'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_scsi_device_lun0'  (string)
  info.product = 'DRW-24B1ST   a'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_ASUS_DRW_24B1ST_a_ABD0CL289552'  (string)
  info.vendor = 'ASUS'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:1/2:0:1:0/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdrdl = true  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = false  (bool)
  storage.cdrom.mrw_w = false  (bool)
  storage.cdrom.read_speed = 8468  (0x2114)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 8468  (0x2114)  (int)
  storage.cdrom.write_speeds = {'8468', '7057', '5645', '4234', '2823'} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = '1.04'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'DRW-24B1ST   a'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 731115520  (0x2b93f000)  (uint64)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.serial = 'ASUS_DRW-24B1ST_a_ABD0CL289552'  (string)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'ASUS'  (string)

udi = '/org/freedesktop/Hal/devices/volume_label_KNOPPIX'
  block.device = '/dev/sr0'  (string)
  block.is_volume = true  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_ASUS_DRW_24B1ST_a_ABD0CL289552'  (string)
  info.capabilities = {'volume.disc', 'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_ASUS_DRW_24B1ST_a_ABD0CL289552'  (string)
  info.product = 'KNOPPIX'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_label_KNOPPIX'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:1/2:0:1:0/block/sr0/fakevolume'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 2048  (0x800)  (int)
  volume.disc.capacity = 735051776  (0x2bd00000)  (uint64)
  volume.disc.has_audio = false  (bool)
  volume.disc.has_data = true  (bool)
  volume.disc.is_appendable = false  (bool)
  volume.disc.is_blank = false  (bool)
  volume.disc.is_blurayvideo = false  (bool)
  volume.disc.is_rewritable = false  (bool)
  volume.disc.is_svcd = false  (bool)
  volume.disc.is_vcd = false  (bool)
  volume.disc.is_videodvd = false  (bool)
  volume.disc.type = 'cd_r'  (string)
  volume.fstype = 'iso9660'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = true  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = true  (bool)
  volume.is_partition = false  (bool)
  volume.label = 'KNOPPIX'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'uid=', 'mode=', 'iocharset='} (string list)
  volume.mount_point = '/mnt-system'  (string)
  volume.num_blocks = 1427960  (0x15c9f8)  (uint64)
  volume.size = 731115520  (0x2b93f000)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:1/2:0:1:0/scsi_generic/sg0'  (string)
  scsi_generic.device = '/dev/sg0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2916'
  info.linux.driver = 'lpc_ich'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801IR (ICH9R) LPC Interface Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2916'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'  (string)
  pci.product = '82801IR (ICH9R) LPC Interface Controller'  (string)
  pci.product_id = 10518  (0x2916)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/platform_iTCO_wdt'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2916'  (string)
  info.product = 'Platform Device (iTCO_wdt)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_iTCO_wdt'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0/iTCO_wdt'  (string)
  platform.id = 'iTCO_wdt'  (string)

udi = '/org/freedesktop/Hal/devices/platform_gpio_ich'
  info.linux.driver = 'gpio_ich'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2916'  (string)
  info.product = 'Platform Device (gpio_ich)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_gpio_ich'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0/gpio_ich'  (string)
  platform.id = 'gpio_ich'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_244e'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801 PCI Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_244e'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'  (string)
  pci.product = '82801 PCI Bridge'  (string)
  pci.product_id = 9294  (0x244e)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_10ec_8167'
  info.linux.driver = 'r8169'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_244e'  (string)
  info.product = 'RTL-8110SC/8169SC Gigabit Ethernet'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_10ec_8167'  (string)
  info.vendor = 'Realtek Semiconductor Co., Ltd.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:04.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:04.0'  (string)
  pci.product = 'RTL-8110SC/8169SC Gigabit Ethernet'  (string)
  pci.product_id = 33127  (0x8167)  (int)
  pci.subsys_product_id = 33293  (0x820d)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Realtek Semiconductor Co., Ltd.'  (string)
  pci.vendor_id = 4332  (0x10ec)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_1b_fc_63_30_75'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_10ec_8167'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_1b_fc_63_30_75'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:04.0/net/eth0'  (string)
  net.80203.mac_address = 120198475893  (0x1bfc633075)  (uint64)
  net.address = '00:1b:fc:63:30:75'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth0'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_10ec_8167'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/pci_11c1_5811'
  info.linux.driver = 'firewire_ohci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_244e'  (string)
  info.product = 'FW322/323 [TrueFire] 1394a Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_11c1_5811'  (string)
  info.vendor = 'LSI Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:03.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:03.0'  (string)
  pci.product = 'FW322/323 [TrueFire] 1394a Controller'  (string)
  pci.product_id = 22545  (0x5811)  (int)
  pci.subsys_product = 'IEEE 1394a Firewire Controller'  (string)
  pci.subsys_product_id = 33428  (0x8294)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'LSI Corporation'  (string)
  pci.vendor_id = 4545  (0x11c1)  (int)

udi = '/org/freedesktop/Hal/devices/ieee1394_guid11d800014d68fb'
  ieee1394.device = '/dev/fw0'  (string)
  ieee1394.guid = 5022569137531131  (0x11d800014d68fb)  (uint64)
  ieee1394.product = 'Juju'  (string)
  ieee1394.product_id = 1  (0x1)  (int)
  ieee1394.vendor = 'Linux Firewire'  (string)
  ieee1394.vendor_id = 13634846  (0xd00d1e)  (int)
  info.capabilities = {'ieee1394'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_11c1_5811'  (string)
  info.subsystem = 'ieee1394'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ieee1394_guid11d800014d68fb'  (string)
  linux.device_file = '/dev/fw0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'firewire'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:03.0/fw0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_105a_3570'
  info.linux.driver = 'sata_promise'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_244e'  (string)
  info.product = 'PDC20771 [FastTrak TX2300]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_105a_3570'  (string)
  info.vendor = 'Promise Technology, Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0'  (string)
  pci.product = 'PDC20771 [FastTrak TX2300]'  (string)
  pci.product_id = 13680  (0x3570)  (int)
  pci.subsys_product_id = 13680  (0x3570)  (int)
  pci.subsys_vendor = 'Promise Technology, Inc.'  (string)
  pci.subsys_vendor_id = 4186  (0x105a)  (int)
  pci.vendor = 'Promise Technology, Inc.'  (string)
  pci.vendor_id = 4186  (0x105a)  (int)

udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_1'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata9/host8/scsi_host/host8'  (string)
  scsi_host.host = 8  (0x8)  (int)

udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata8/host7'  (string)
  scsi_host.host = 7  (0x7)  (int)

udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata8/host7/scsi_host/host7'  (string)
  scsi_host.host = 7  (0x7)  (int)

udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata8/host7/target7:0:0/7:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 7  (0x7)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'ST3750640AS'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_ST3750640AS_3QD0R7NL'
  block.device = '/dev/sdc'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 32  (0x20)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_ST3750640AS_3QD0R7NL'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'ST3750640AS'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_ST3750640AS_3QD0R7NL'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata8/host7/target7:0:0/7:0:0:0/block/sdc'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = '3.AAJ'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'ST3750640AS'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 750156374016  (0xaea8cde000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'ST3750640AS_3QD0R7NL'  (string)
  storage.size = 750156374016  (0xaea8cde000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_2A44B5A544B573E3_0'
  block.device = '/dev/sdc1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 33  (0x21)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_ST3750640AS_3QD0R7NL'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_ST3750640AS_3QD0R7NL'  (string)
  info.product = 'Data RAID'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_2A44B5A544B573E3_0'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata8/host7/target7:0:0/7:0:0:0/block/sdc/sdc1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.1.00'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = 'Data RAID'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detach', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = ''  (string)
  volume.num_blocks = 1465012224  (0x57525000)  (uint64)
  volume.partition.media_size = 750156374016  (0xaea8cde000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 1048576  (0x100000)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 750086258688  (0xaea4a00000)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '2A44B5A544B573E3'  (string)

udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_0_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata8/host7/target7:0:0/7:0:0:0/scsi_generic/sg3'  (string)
  scsi_generic.device = '/dev/sg3'  (string)

udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata7/host6'  (string)
  scsi_host.host = 6  (0x6)  (int)

udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata7/host6/scsi_host/host6'  (string)
  scsi_host.host = 6  (0x6)  (int)

udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata7/host6/target6:0:0/6:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 6  (0x6)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'ST3750640AS'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_ST3750640AS_3QD0T5CQ'
  block.device = '/dev/sdb'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 16  (0x10)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_ST3750640AS_3QD0T5CQ'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_scsi_device_lun0'  (string)
  info.product = 'ST3750640AS'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_ST3750640AS_3QD0T5CQ'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata7/host6/target6:0:0/6:0:0:0/block/sdb'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = '3.AAJ'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'ST3750640AS'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 750156374016  (0xaea8cde000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'ST3750640AS_3QD0T5CQ'  (string)
  storage.size = 750156374016  (0xaea8cde000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_2A44B5A544B573E3'
  block.device = '/dev/sdb1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 17  (0x11)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_ST3750640AS_3QD0T5CQ'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_ST3750640AS_3QD0T5CQ'  (string)
  info.product = 'Data RAID'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_2A44B5A544B573E3'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata7/host6/target6:0:0/6:0:0:0/block/sdb/sdb1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.1.00'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = 'Data RAID'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detach', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = ''  (string)
  volume.num_blocks = 1465012224  (0x57525000)  (uint64)
  volume.partition.media_size = 750156374016  (0xaea8cde000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 1048576  (0x100000)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 750086258688  (0xaea4a00000)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '2A44B5A544B573E3'  (string)

udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_105a_3570_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/ata7/host6/target6:0:0/6:0:0:0/scsi_generic/sg2'  (string)
  scsi_generic.device = '/dev/sg2'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293a'
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) USB2 EHCI Controller #1'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293a'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'  (string)
  pci.product = '82801I (ICH9 Family) USB2 EHCI Controller #1'  (string)
  pci.product_id = 10554  (0x293a)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293a'  (string)
  info.product = '2.0 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/002/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 774  (0x306)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 6  (0x6)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.serial = '0000:00:1d.7'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'  (string)
  info.product = 'GoFlex Desk Mac'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H'  (string)
  info.vendor = 'Seagate RSS LLC'  (string)
  linux.device_file = '/dev/bus/usb/002/007'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 297  (0x129)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 7  (0x7)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5'  (string)
  usb_device.max_power = 2  (0x2)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'GoFlex Desk Mac'  (string)
  usb_device.product_id = 24725  (0x6095)  (int)
  usb_device.serial = 'NA0PGY4H'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Seagate RSS LLC'  (string)
  usb_device.vendor_id = 3010  (0xbc2)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0'
  info.linux.driver = 'usb-storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H'  (string)
  info.product = 'USB Mass Storage Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 297  (0x129)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 8  (0x8)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 80  (0x50)  (int)
  usb.interface.subclass = 6  (0x6)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 7  (0x7)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0'  (string)
  usb.max_power = 2  (0x2)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Mass Storage Interface'  (string)
  usb.product_id = 24725  (0x6095)  (int)
  usb.serial = 'NA0PGY4H'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Seagate RSS LLC'  (string)
  usb.vendor_id = 3010  (0xbc2)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13'  (string)
  scsi_host.host = 13  (0xd)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/scsi_host/host13'  (string)
  scsi_host.host = 13  (0xd)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 13  (0xd)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'GoFlex Desk Mac'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'Seagate'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_ST3000DM001_9YN166_Z1F0D3D7'
  block.device = '/dev/sdd'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 48  (0x30)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_ST3000DM001_9YN166_Z1F0D3D7'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host_scsi_device_lun0'  (string)
  info.product = 'GoFlex Desk Mac'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_ST3000DM001_9YN166_Z1F0D3D7'  (string)
  info.vendor = 'Seagate'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'usb'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = 'CC9D'  (string)
  storage.hotpluggable = true  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'GoFlex Desk Mac'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 3000592977920  (0x2baa1475000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'ST3000DM001-9YN166_Z1F0D3D7'  (string)
  storage.size = 3000592977920  (0x2baa1475000)  (uint64)
  storage.vendor = 'Seagate'  (string)

udi = '/org/freedesktop/Hal/devices/volume_part1_size_209715200'
  block.device = '/dev/sdd1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 49  (0x31)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_ST3000DM001_9YN166_Z1F0D3D7'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_ST3000DM001_9YN166_Z1F0D3D7'  (string)
  info.product = 'Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_part1_size_209715200'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd1'  (string)
  volume.block_size = 4096  (0x1000)  (int)
  volume.fstype = ''  (string)
  volume.fsusage = ''  (string)
  volume.fsversion = ''  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 409600  (0x64000)  (uint64)
  volume.partition.media_size = 3000592977920  (0x2baa1475000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 24576  (0x6000)  (uint64)
  volume.size = 209715200  (0xc800000)  (uint64)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_d31f14b3_b2c4_387b_a0df_2313542f0bd9'
  block.device = '/dev/sdd2'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 50  (0x32)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_ST3000DM001_9YN166_Z1F0D3D7'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_ST3000DM001_9YN166_Z1F0D3D7'  (string)
  info.product = 'Volume (hfsplus)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_d31f14b3_b2c4_387b_a0df_2313542f0bd9'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd2'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 4096  (0x1000)  (int)
  volume.fstype = 'hfsplus'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'force'} (string list)
  volume.mount_point = ''  (string)
  volume.num_blocks = 5859861328  (0x15d466350)  (uint64)
  volume.partition.media_size = 3000592977920  (0x2baa1475000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.partition.start = 209739776  (0xc806000)  (uint64)
  volume.size = 3000248999936  (0x2ba8cc6a000)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'd31f14b3-b2c4-387b-a0df-2313542f0bd9'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc2_6095_NA0PGY4H_if0_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_generic/sg4'  (string)
  scsi_generic.device = '/dev/sg4'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 774  (0x306)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 6  (0x6)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 2  (0x2)  (int)
  usb.serial = '0000:00:1d.7'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_2936'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) USB UHCI Controller #3'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2936'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2'  (string)
  pci.product = '82801I (ICH9 Family) USB UHCI Controller #3'  (string)
  pci.product_id = 10550  (0x2936)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2936'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/008/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8'  (string)
  usb_device.bus_number = 8  (0x8)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 774  (0x306)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.2'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'LX710 Cordless Desktop Laser'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial'  (string)
  info.vendor = 'Logitech, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/008/006'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2'  (string)
  usb_device.bus_number = 8  (0x8)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 14352  (0x3810)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 6  (0x6)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2'  (string)
  usb_device.max_power = 98  (0x62)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 2  (0x2)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'LX710 Cordless Desktop Laser'  (string)
  usb_device.product_id = 50455  (0xc517)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Logitech, Inc.'  (string)
  usb_device.vendor_id = 1133  (0x46d)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if1'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.1'  (string)
  usb.bus_number = 8  (0x8)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 14352  (0x3810)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 1  (0x1)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 6  (0x6)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.1'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 50455  (0xc517)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Logitech, Inc.'  (string)
  usb.vendor_id = 1133  (0x46d)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if1_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'input.keys', 'input.mouse', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if1'  (string)
  info.product = 'Logitech USB Receiver'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if1'  (string)
  input.product = 'Logitech USB Receiver'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.1/input/input3/event3'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0'  (string)
  usb.bus_number = 8  (0x8)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 14352  (0x3810)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 1  (0x1)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 6  (0x6)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 50455  (0xc517)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Logitech, Inc.'  (string)
  usb.vendor_id = 1133  (0x46d)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if0_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if0'  (string)
  info.product = 'Logitech USB Receiver'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event2'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c517_noserial_if0'  (string)
  input.product = 'Logitech USB Receiver'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input2/event2'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0'  (string)
  usb.bus_number = 8  (0x8)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 774  (0x306)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.2'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_2935'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) USB UHCI Controller #2'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2935'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1'  (string)
  pci.product = '82801I (ICH9 Family) USB UHCI Controller #2'  (string)
  pci.product_id = 10549  (0x2935)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2935'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/007/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7'  (string)
  usb_device.bus_number = 7  (0x7)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 774  (0x306)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0'  (string)
  usb.bus_number = 7  (0x7)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 774  (0x306)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_2934'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) USB UHCI Controller #1'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2934'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'  (string)
  pci.product = '82801I (ICH9 Family) USB UHCI Controller #1'  (string)
  pci.product_id = 10548  (0x2934)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2934'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/006/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb6'  (string)
  usb_device.bus_number = 6  (0x6)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 774  (0x306)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb6'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0'  (string)
  usb.bus_number = 6  (0x6)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 774  (0x306)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_294a'
  info.linux.driver = 'pcieport'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) PCI Express Port 6'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_294a'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.5'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.5'  (string)
  pci.product = '82801I (ICH9 Family) PCI Express Port 6'  (string)
  pci.product_id = 10570  (0x294a)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_11ab_4364'
  info.linux.driver = 'sky2'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_294a'  (string)
  info.product = '88E8056 PCI-E Gigabit Ethernet Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_11ab_4364'  (string)
  info.vendor = 'Marvell Technology Group Ltd.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0'  (string)
  pci.product = '88E8056 PCI-E Gigabit Ethernet Controller'  (string)
  pci.product_id = 17252  (0x4364)  (int)
  pci.subsys_product_id = 33272  (0x81f8)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Marvell Technology Group Ltd.'  (string)
  pci.vendor_id = 4523  (0x11ab)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_1b_fc_63_34_ee'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_11ab_4364'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_1b_fc_63_34_ee'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth1'  (string)
  net.80203.mac_address = 120198477038  (0x1bfc6334ee)  (uint64)
  net.address = '00:1b:fc:63:34:ee'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth1'  (string)
  net.linux.ifindex = 3  (0x3)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_11ab_4364'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/pci_8086_2948'
  info.linux.driver = 'pcieport'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) PCI Express Port 5'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2948'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4'  (string)
  pci.product = '82801I (ICH9 Family) PCI Express Port 5'  (string)
  pci.product_id = 10568  (0x2948)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_197b_2363_0'
  info.linux.driver = 'pata_jmicron'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2948'  (string)
  info.product = 'JMB363 SATA/IDE Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_197b_2363_0'  (string)
  info.vendor = 'JMicron Technology Corp.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.1'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 133  (0x85)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.1'  (string)
  pci.product = 'JMB363 SATA/IDE Controller'  (string)
  pci.product_id = 9059  (0x2363)  (int)
  pci.subsys_product_id = 33359  (0x824f)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'JMicron Technology Corp.'  (string)
  pci.vendor_id = 6523  (0x197b)  (int)

udi = '/org/freedesktop/Hal/devices/pci_197b_2363_0_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_197b_2363_0'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_197b_2363_0_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.1/ata11/host10/scsi_host/host10'  (string)
  scsi_host.host = 10  (0xa)  (int)

udi = '/org/freedesktop/Hal/devices/pci_197b_2363_0_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_197b_2363_0'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_197b_2363_0_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.1/ata10/host9/scsi_host/host9'  (string)
  scsi_host.host = 9  (0x9)  (int)

udi = '/org/freedesktop/Hal/devices/pci_197b_2363'
  info.linux.driver = 'ahci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2948'  (string)
  info.product = 'JMB363 SATA/IDE Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_197b_2363'  (string)
  info.vendor = 'JMicron Technology Corp.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 6  (0x6)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0'  (string)
  pci.product = 'JMB363 SATA/IDE Controller'  (string)
  pci.product_id = 9059  (0x2363)  (int)
  pci.subsys_product_id = 33359  (0x824f)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'JMicron Technology Corp.'  (string)
  pci.vendor_id = 6523  (0x197b)  (int)

udi = '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_197b_2363'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/ata2/host1/scsi_host/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_197b_2363'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/ata1/host0/scsi_host/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2940'
  info.linux.driver = 'pcieport'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) PCI Express Port 1'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2940'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'  (string)
  pci.product = '82801I (ICH9 Family) PCI Express Port 1'  (string)
  pci.product_id = 10560  (0x2940)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e'
  info.linux.driver = 'snd_hda_intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) HD Audio Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'  (string)
  pci.product = '82801I (ICH9 Family) HD Audio Controller'  (string)
  pci.product_id = 10558  (0x293e)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293e'  (string)
  info.product = 'HDA Intel Sound Card'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0'  (string)
  sound.card = 0  (0x0)  (int)
  sound.card_id = 'HDA Intel'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_8086_293e'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 1  (0x1)  (int)
  alsa.device_file = '/dev/snd/pcmC0D1p'  (string)
  alsa.device_id = 'AD198x Digital'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'playback'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  info.product = 'AD198x Digital ALSA Playback Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_1'  (string)
  linux.device_file = '/dev/snd/pcmC0D1p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D1p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_capture_1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 1  (0x1)  (int)
  alsa.device_file = '/dev/snd/pcmC0D1c'  (string)
  alsa.device_id = 'AD198x Digital'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  info.product = 'AD198x Digital ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_capture_1'  (string)
  linux.device_file = '/dev/snd/pcmC0D1c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D1c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0p'  (string)
  alsa.device_id = 'AD198x Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'playback'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  info.product = 'AD198x Analog ALSA Playback Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_capture_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0c'  (string)
  alsa.device_id = 'AD198x Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  info.product = 'AD198x Analog ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_capture_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_oss_mixer__1'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  info.product = 'AD198x Analog OSS Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_oss_mixer__1'  (string)
  linux.device_file = '/dev/mixer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device_file = '/dev/mixer'  (string)
  oss.device_id = 'AD198x Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  oss.type = 'mixer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_oss_pcm_0_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  info.product = 'AD198x Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_oss_pcm_0_0'  (string)
  linux.device_file = '/dev/dsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/dsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/dsp'  (string)
  oss.device_id = 'AD198x Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_control__1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device_file = '/dev/snd/controlC0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  alsa.type = 'control'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  info.product = 'HDA Intel ALSA Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_oss_pcm_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  info.product = 'AD198x Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_oss_pcm_0'  (string)
  linux.device_file = '/dev/audio'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/audio'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/audio'  (string)
  oss.device_id = 'AD198x Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_oss_pcm_1'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  info.product = 'AD198x Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_oss_pcm_1'  (string)
  linux.device_file = '/dev/adsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/adsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 1  (0x1)  (int)
  oss.device_file = '/dev/adsp'  (string)
  oss.device_id = 'AD198x Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_293c'
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) USB2 EHCI Controller #2'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_293c'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7'  (string)
  pci.product = '82801I (ICH9 Family) USB2 EHCI Controller #2'  (string)
  pci.product_id = 10556  (0x293c)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_7'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_293c'  (string)
  info.product = '2.0 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_7'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/001/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 774  (0x306)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 6  (0x6)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.serial = '0000:00:1a.7'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_7'  (string)
  info.product = 'RTL8187 Wireless Adapter'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE'  (string)
  info.vendor = 'Realtek Semiconductor Corp.'  (string)
  linux.device_file = '/dev/bus/usb/001/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration = 'Wireless Network Card'  (string)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 256  (0x100)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3'  (string)
  usb_device.max_power = 500  (0x1f4)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'RTL8187 Wireless Adapter'  (string)
  usb_device.product_id = 33159  (0x8187)  (int)
  usb_device.serial = '0015AF0F2FCE'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Realtek Semiconductor Corp.'  (string)
  usb_device.vendor_id = 3034  (0xbda)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/leds_rtl8187_phy0_tx'
  info.addons.singleton = {'hald-addon-leds'} (string list)
  info.capabilities = {'leds', 'keyboard_backlight'} (string list)
  info.category = 'leds'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Leds'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE'  (string)
  info.subsystem = 'leds'  (string)
  info.udi = '/org/freedesktop/Hal/devices/leds_rtl8187_phy0_tx'  (string)
  keyboard_backlight.num_levels = 256  (0x100)  (int)
  leds.device_name = 'rtl8187-phy0'  (string)
  leds.function = 'tx'  (string)
  leds.num_levels = 256  (0x100)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'leds'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/leds/rtl8187-phy0::tx'  (string)

udi = '/org/freedesktop/Hal/devices/leds_rtl8187_phy0_rx'
  info.addons.singleton = {'hald-addon-leds'} (string list)
  info.capabilities = {'leds', 'keyboard_backlight'} (string list)
  info.category = 'leds'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Leds'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE'  (string)
  info.subsystem = 'leds'  (string)
  info.udi = '/org/freedesktop/Hal/devices/leds_rtl8187_phy0_rx'  (string)
  keyboard_backlight.num_levels = 256  (0x100)  (int)
  leds.device_name = 'rtl8187-phy0'  (string)
  leds.function = 'rx'  (string)
  leds.num_levels = 256  (0x100)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'leds'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/leds/rtl8187-phy0::rx'  (string)

udi = '/org/freedesktop/Hal/devices/leds_rtl8187_phy0_radio'
  info.addons.singleton = {'hald-addon-leds'} (string list)
  info.capabilities = {'leds', 'keyboard_backlight'} (string list)
  info.category = 'leds'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Leds'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE'  (string)
  info.subsystem = 'leds'  (string)
  info.udi = '/org/freedesktop/Hal/devices/leds_rtl8187_phy0_radio'  (string)
  keyboard_backlight.num_levels = 256  (0x100)  (int)
  leds.device_name = 'rtl8187-phy0'  (string)
  leds.function = 'radio'  (string)
  leds.num_levels = 256  (0x100)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'leds'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/leds/rtl8187-phy0::radio'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE_if0'
  info.linux.driver = 'rtl8187'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE'  (string)
  info.product = 'USB Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration = 'Wireless Network Card'  (string)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 0  (0x0)  (int)
  usb.interface.description = 'Bulk-IN,Bulk-OUT,Bulk-OUT'  (string)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0'  (string)
  usb.max_power = 500  (0x1f4)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Interface'  (string)
  usb.product_id = 33159  (0x8187)  (int)
  usb.serial = '0015AF0F2FCE'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Realtek Semiconductor Corp.'  (string)
  usb.vendor_id = 3034  (0xbda)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/net_00_15_af_0f_2f_ce'
  info.capabilities = {'net', 'net.80211'} (string list)
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE_if0'  (string)
  info.product = 'WLAN Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_15_af_0f_2f_ce'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/net/wlan0'  (string)
  net.80211.mac_address = 93131321294  (0x15af0f2fce)  (uint64)
  net.address = '00:15:af:0f:2f:ce'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'wlan0'  (string)
  net.linux.ifindex = 4  (0x4)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE_if0'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE_if0_rfkill_phy0_wlan'
  info.addons.singleton = {'hald-addon-rfkill-killswitch'} (string list)
  info.capabilities = {'killswitch'} (string list)
  info.category = 'killswitch'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.KillSwitch'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE_if0'  (string)
  info.product = 'phy0 wlan Killswitch'  (string)
  info.subsystem = 'rfkill'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bda_8187_0015AF0F2FCE_if0_rfkill_phy0_wlan'  (string)
  killswitch.access_method = 'rfkill'  (string)
  killswitch.name = 'phy0'  (string)
  killswitch.state = 1  (0x1)  (int)
  killswitch.type = 'wlan'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'rfkill'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/ieee80211/phy0/rfkill0'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_7_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_7'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_7_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 774  (0x306)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 6  (0x6)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 2  (0x2)  (int)
  usb.serial = '0000:00:1a.7'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_2939'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) USB UHCI Controller #6'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2939'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.2'  (string)
  pci.product = '82801I (ICH9 Family) USB UHCI Controller #6'  (string)
  pci.product_id = 10553  (0x2939)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_2'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2939'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_2'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/005/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.2/usb5'  (string)
  usb_device.bus_number = 5  (0x5)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 774  (0x306)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.2/usb5'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1a.2'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_2_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0'  (string)
  usb.bus_number = 5  (0x5)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 774  (0x306)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1a.2'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_2938'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) USB UHCI Controller #5'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2938'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1'  (string)
  pci.product = '82801I (ICH9 Family) USB UHCI Controller #5'  (string)
  pci.product_id = 10552  (0x2938)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_1'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2938'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_1'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/004/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1/usb4'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 774  (0x306)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1/usb4'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1a.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_1_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 774  (0x306)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1a.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_2937'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801I (ICH9 Family) USB UHCI Controller #4'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2937'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0'  (string)
  pci.product = '82801I (ICH9 Family) USB UHCI Controller #4'  (string)
  pci.product_id = 10551  (0x2937)  (int)
  pci.subsys_product_id = 33399  (0x8277)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_0'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2937'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_0'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/003/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb3'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 774  (0x306)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb3'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1a.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1a_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 774  (0x306)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1a.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_29c1'
  info.linux.driver = 'pcieport'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82G33/G31/P35/P31 Express PCI Express Root Port'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_29c1'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'  (string)
  pci.product = '82G33/G31/P35/P31 Express PCI Express Root Port'  (string)
  pci.product_id = 10689  (0x29c1)  (int)
  pci.subsys_product_id = 33429  (0x8295)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_aa68'
  info.linux.driver = 'snd_hda_intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_29c1'  (string)
  info.product = 'Cedar HDMI Audio [Radeon HD 5400/6300 Series]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_aa68'  (string)
  info.vendor = 'Advanced Micro Devices [AMD] nee ATI'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.1'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.1'  (string)
  pci.product = 'Cedar HDMI Audio [Radeon HD 5400/6300 Series]'  (string)
  pci.product_id = 43624  (0xaa68)  (int)
  pci.subsys_product_id = 43624  (0xaa68)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD] nee ATI'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_aa68_sound_card_1'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_aa68'  (string)
  info.product = 'HD-Audio Generic Sound Card'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_aa68_sound_card_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1'  (string)
  sound.card = 1  (0x1)  (int)
  sound.card_id = 'HD-Audio Generic'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_1002_aa68'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_aa68_sound_card_1_oss_mixer__1'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_aa68_sound_card_1'  (string)
  info.product = 'HD-Audio Generic OSS Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_aa68_sound_card_1_oss_mixer__1'  (string)
  linux.device_file = '/dev/mixer1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/mixer1'  (string)
  oss.card = 1  (0x1)  (int)
  oss.card_id = 'HD-Audio Generic'  (string)
  oss.device_file = '/dev/mixer1'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_aa68_sound_card_1'  (string)
  oss.type = 'mixer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_aa68_sound_card_1_alsa_control__1'
  alsa.card = 1  (0x1)  (int)
  alsa.card_id = 'HD-Audio Generic'  (string)
  alsa.device_file = '/dev/snd/controlC1'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_aa68_sound_card_1'  (string)
  alsa.type = 'control'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_aa68_sound_card_1'  (string)
  info.product = 'HD-Audio Generic ALSA Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_aa68_sound_card_1_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/controlC1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_68f9'
  info.linux.driver = 'radeon'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_29c1'  (string)
  info.product = 'Cedar PRO [Radeon HD 5450]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_68f9'  (string)
  info.vendor = 'Advanced Micro Devices [AMD] nee ATI'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0'  (string)
  pci.product = 'Cedar PRO [Radeon HD 5450]'  (string)
  pci.product_id = 26873  (0x68f9)  (int)
  pci.subsys_product_id = 962  (0x3c2)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD] nee ATI'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__controlD64'
  info.capabilities = {'drm'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_68f9'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.subsystem = 'drm'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__controlD64'  (string)
  info.vendor = 'Advanced Micro Devices [AMD] nee ATI'  (string)
  linux.device_file = '/dev/dri/controlD64'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/controlD64'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0'
  info.capabilities = {'drm'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_68f9'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.subsystem = 'drm'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0'  (string)
  info.vendor = 'Advanced Micro Devices [AMD] nee ATI'  (string)
  linux.device_file = '/dev/dri/card0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0_drm__null__card0_VGA_1'
  info.capabilities = {'drm'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.subsystem = 'drm'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0_drm__null__card0_VGA_1'  (string)
  info.vendor = 'Advanced Micro Devices [AMD] nee ATI'  (string)
  linux.device_file = ''  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0/card0-VGA-1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0_drm__null__card0_HDMI_A_1'
  info.capabilities = {'drm'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.subsystem = 'drm'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0_drm__null__card0_HDMI_A_1'  (string)
  info.vendor = 'Advanced Micro Devices [AMD] nee ATI'  (string)
  linux.device_file = ''  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0/card0-HDMI-A-1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0_drm__null__card0_DVI_I_1'
  info.capabilities = {'drm'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.subsystem = 'drm'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_68f9_drm__null__card0_drm__null__card0_DVI_I_1'  (string)
  info.vendor = 'Advanced Micro Devices [AMD] nee ATI'  (string)
  linux.device_file = ''  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0/card0-DVI-I-1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_29c0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82G33/G31/P35/P31 Express DRAM Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_29c0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.product = '82G33/G31/P35/P31 Express DRAM Controller'  (string)
  pci.product_id = 10688  (0x29c0)  (int)
  pci.subsys_product_id = 33429  (0x8295)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)


Dumped 155 device(s) from the Global Device List.
------------------------------------------------




UDEV.LOG
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[2430.434324] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5 (usb)
ACTION=add
BUSNUM=002
DEVNAME=bus/usb/002/007
DEVNUM=007
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5
DEVTYPE=usb_device
MAJOR=189
MINOR=134
PRODUCT=bc2/6095/129
SEQNUM=2939
SUBSYSTEM=usb
TYPE=0/0/0
UDEV_LOG=3

KERNEL[2430.434510] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0
DEVTYPE=usb_interface
INTERFACE=8/6/80
MODALIAS=usb:v0BC2p6095d0129dc00dsc00dp00ic08isc06ip50in00
PRODUCT=bc2/6095/129
SEQNUM=2940
SUBSYSTEM=usb
TYPE=0/0/0
UDEV_LOG=3

KERNEL[2430.434743] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13 (scsi)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13
DEVTYPE=scsi_host
SEQNUM=2941
SUBSYSTEM=scsi
UDEV_LOG=3

KERNEL[2430.434767] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/scsi_host/host13 (scsi_host)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/scsi_host/host13
SEQNUM=2942
SUBSYSTEM=scsi_host
UDEV_LOG=3

UDEV  [2430.435484] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5 (usb)
ACTION=add
BUSNUM=002
DEVNAME=/dev/bus/usb/002/007
DEVNUM=007
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5
DEVTYPE=usb_device
ID_BUS=usb
ID_MODEL=GoFlex_Desk_Mac
ID_MODEL_ENC=GoFlex\x20Desk\x20Mac\x20
ID_MODEL_ID=6095
ID_REVISION=0129
ID_SERIAL=Seagate_GoFlex_Desk_Mac_NA0PGY4H
ID_SERIAL_SHORT=NA0PGY4H
ID_USB_INTERFACES=:080650:
ID_VENDOR=Seagate
ID_VENDOR_ENC=Seagate\x20
ID_VENDOR_ID=0bc2
MAJOR=189
MINOR=134
PRODUCT=bc2/6095/129
SEQNUM=2939
SUBSYSTEM=usb
TYPE=0/0/0
UDEV_LOG=3
USEC_INITIALIZED=2430435322

UDEV  [2430.438876] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0
DEVTYPE=usb_interface
INTERFACE=8/6/80
MODALIAS=usb:v0BC2p6095d0129dc00dsc00dp00ic08isc06ip50in00
PRODUCT=bc2/6095/129
SEQNUM=2940
SUBSYSTEM=usb
TYPE=0/0/0
UDEV_LOG=3
USEC_INITIALIZED=2430436195

UDEV  [2430.439302] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13 (scsi)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13
DEVTYPE=scsi_host
SEQNUM=2941
SUBSYSTEM=scsi
UDEV_LOG=3
USEC_INITIALIZED=2430439241

UDEV  [2430.439840] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/scsi_host/host13 (scsi_host)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/scsi_host/host13
SEQNUM=2942
SUBSYSTEM=scsi_host
UDEV_LOG=3
USEC_INITIALIZED=2430439743

KERNEL[2436.517765] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0 (scsi)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0
DEVTYPE=scsi_target
SEQNUM=2943
SUBSYSTEM=scsi
UDEV_LOG=3

KERNEL[2436.518503] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0 (scsi)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0
DEVTYPE=scsi_device
MODALIAS=scsi:t-0x00
SEQNUM=2944
SUBSYSTEM=scsi
UDEV_LOG=3

UDEV  [2436.518529] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0 (scsi)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0
DEVTYPE=scsi_target
SEQNUM=2943
SUBSYSTEM=scsi
UDEV_LOG=3
USEC_INITIALIZED=2436518399

KERNEL[2436.518550] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_disk/13:0:0:0 (scsi_disk)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_disk/13:0:0:0
SEQNUM=2945
SUBSYSTEM=scsi_disk
UDEV_LOG=3

KERNEL[2436.518570] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_device/13:0:0:0 (scsi_device)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_device/13:0:0:0
SEQNUM=2946
SUBSYSTEM=scsi_device
UDEV_LOG=3

KERNEL[2436.518605] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_generic/sg4 (scsi_generic)
ACTION=add
DEVNAME=sg4
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_generic/sg4
MAJOR=21
MINOR=4
SEQNUM=2947
SUBSYSTEM=scsi_generic
UDEV_LOG=3

KERNEL[2436.518632] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/bsg/13:0:0:0 (bsg)
ACTION=add
DEVNAME=bsg/13:0:0:0
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/bsg/13:0:0:0
MAJOR=253
MINOR=4
SEQNUM=2948
SUBSYSTEM=bsg
UDEV_LOG=3

UDEV  [2436.522149] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0 (scsi)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0
DEVTYPE=scsi_device
MODALIAS=scsi:t-0x00
SEQNUM=2944
SUBSYSTEM=scsi
UDEV_LOG=3
USEC_INITIALIZED=2436518915

UDEV  [2436.522818] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_device/13:0:0:0 (scsi_device)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_device/13:0:0:0
SEQNUM=2946
SUBSYSTEM=scsi_device
UDEV_LOG=3
USEC_INITIALIZED=2436522718

UDEV  [2436.523688] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_disk/13:0:0:0 (scsi_disk)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_disk/13:0:0:0
SEQNUM=2945
SUBSYSTEM=scsi_disk
UDEV_LOG=3
USEC_INITIALIZED=2436523569

UDEV  [2436.524153] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/bsg/13:0:0:0 (bsg)
ACTION=add
DEVNAME=/dev/bsg/13:0:0:0
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/bsg/13:0:0:0
MAJOR=253
MINOR=4
SEQNUM=2948
SUBSYSTEM=bsg
UDEV_LOG=3
USEC_INITIALIZED=2436517998

UDEV  [2436.524212] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_generic/sg4 (scsi_generic)
ACTION=add
DEVNAME=/dev/sg4
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/scsi_generic/sg4
MAJOR=21
MINOR=4
SEQNUM=2947
SUBSYSTEM=scsi_generic
UDEV_LOG=3
USEC_INITIALIZED=2436517952

KERNEL[2441.606461] add      /devices/virtual/bdi/8:48 (bdi)
ACTION=add
DEVPATH=/devices/virtual/bdi/8:48
SEQNUM=2949
SUBSYSTEM=bdi
UDEV_LOG=3

UDEV  [2441.606831] add      /devices/virtual/bdi/8:48 (bdi)
ACTION=add
DEVPATH=/devices/virtual/bdi/8:48
SEQNUM=2949
SUBSYSTEM=bdi
UDEV_LOG=3
USEC_INITIALIZED=2441606705

KERNEL[2441.669569] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd (block)
ACTION=add
DEVNAME=sdd
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd
DEVTYPE=disk
MAJOR=8
MINOR=48
SEQNUM=2950
SUBSYSTEM=block
UDEV_LOG=3

KERNEL[2441.669589] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd1 (block)
ACTION=add
DEVNAME=sdd1
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd1
DEVTYPE=partition
MAJOR=8
MINOR=49
SEQNUM=2951
SUBSYSTEM=block
UDEV_LOG=3

KERNEL[2441.669607] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd2 (block)
ACTION=add
DEVNAME=sdd2
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd2
DEVTYPE=partition
MAJOR=8
MINOR=50
SEQNUM=2952
SUBSYSTEM=block
UDEV_LOG=3

UDEV  [2441.781908] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd (block)
ACTION=add
DEVLINKS=/dev/disk/by-id/ata-ST3000DM001-9YN166_Z1F0D3D7 /dev/disk/by-id/scsi-SSeagate_GoFlex_Desk_Mac_NA0PGY4H /dev/disk/by-id/wwn-0x5000c5003f6c77c9 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0
DEVNAME=/dev/sdd
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd
DEVTYPE=disk
ID_ATA=1
ID_ATA_DOWNLOAD_MICROCODE=1
ID_ATA_FEATURE_SET_APM=1
ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=128
ID_ATA_FEATURE_SET_APM_ENABLED=1
ID_ATA_FEATURE_SET_HPA=1
ID_ATA_FEATURE_SET_HPA_ENABLED=1
ID_ATA_FEATURE_SET_PM=1
ID_ATA_FEATURE_SET_PM_ENABLED=1
ID_ATA_FEATURE_SET_SECURITY=1
ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=330
ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=330
ID_ATA_FEATURE_SET_SMART=1
ID_ATA_FEATURE_SET_SMART_ENABLED=1
ID_ATA_ROTATION_RATE_RPM=7200
ID_ATA_SATA=1
ID_ATA_SATA_SIGNAL_RATE_GEN1=1
ID_ATA_SATA_SIGNAL_RATE_GEN2=1
ID_ATA_WRITE_CACHE=1
ID_ATA_WRITE_CACHE_ENABLED=1
ID_BUS=ata
ID_MODEL=ST3000DM001-9YN166
ID_MODEL_ENC=ST3000DM001-9YN166\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
ID_PART_TABLE_TYPE=gpt
ID_PATH=pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0
ID_PATH_TAG=pci-0000_00_1d_7-usb-0_5_1_0-scsi-0_0_0_0
ID_REVISION=CC9D
ID_SCSI_COMPAT=SSeagate_GoFlex_Desk_Mac_NA0PGY4H
ID_SERIAL=ST3000DM001-9YN166_Z1F0D3D7
ID_SERIAL_SHORT=Z1F0D3D7
ID_TYPE=disk
ID_WWN=0x5000c5003f6c77c9
ID_WWN_WITH_EXTENSION=0x5000c5003f6c77c9
MAJOR=8
MINOR=48
SEQNUM=2950
SUBSYSTEM=block
UDEV_LOG=3
UDISKS_ATA_SMART_IS_AVAILABLE=1
UDISKS_PRESENTATION_NOPOLICY=0
USEC_INITIALIZED=2441759125

UDEV  [2442.012155] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd2 (block)
ACTION=add
DEVLINKS=/dev/disk/by-id/ata-ST3000DM001-9YN166_Z1F0D3D7-part2 /dev/disk/by-id/scsi-SSeagate_GoFlex_Desk_Mac_NA0PGY4H-part2 /dev/disk/by-id/wwn-0x5000c5003f6c77c9-part2 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part2 /dev/disk/by-uuid/d31f14b3-b2c4-387b-a0df-2313542f0bd9
DEVNAME=/dev/sdd2
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd2
DEVTYPE=partition
ID_ATA=1
ID_ATA_DOWNLOAD_MICROCODE=1
ID_ATA_FEATURE_SET_APM=1
ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=128
ID_ATA_FEATURE_SET_APM_ENABLED=1
ID_ATA_FEATURE_SET_HPA=1
ID_ATA_FEATURE_SET_HPA_ENABLED=1
ID_ATA_FEATURE_SET_PM=1
ID_ATA_FEATURE_SET_PM_ENABLED=1
ID_ATA_FEATURE_SET_SECURITY=1
ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=330
ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=330
ID_ATA_FEATURE_SET_SMART=1
ID_ATA_FEATURE_SET_SMART_ENABLED=1
ID_ATA_ROTATION_RATE_RPM=7200
ID_ATA_SATA=1
ID_ATA_SATA_SIGNAL_RATE_GEN1=1
ID_ATA_SATA_SIGNAL_RATE_GEN2=1
ID_ATA_WRITE_CACHE=1
ID_ATA_WRITE_CACHE_ENABLED=1
ID_BUS=ata
ID_FS_TYPE=hfsplus
ID_FS_USAGE=filesystem
ID_FS_UUID=d31f14b3-b2c4-387b-a0df-2313542f0bd9
ID_FS_UUID_ENC=d31f14b3-b2c4-387b-a0df-2313542f0bd9
ID_MODEL=ST3000DM001-9YN166
ID_MODEL_ENC=ST3000DM001-9YN166\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
ID_PART_ENTRY_DISK=8:48
ID_PART_ENTRY_NAME=Untitled
ID_PART_ENTRY_NUMBER=2
ID_PART_ENTRY_OFFSET=409648
ID_PART_ENTRY_SCHEME=gpt
ID_PART_ENTRY_SIZE=5859861328
ID_PART_ENTRY_TYPE=48465300-0000-11aa-aa11-00306543ecac
ID_PART_ENTRY_UUID=b9f2bcc7-3ad2-4383-ac01-d895ac05c9d2
ID_PART_TABLE_TYPE=gpt
ID_PATH=pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0
ID_PATH_TAG=pci-0000_00_1d_7-usb-0_5_1_0-scsi-0_0_0_0
ID_REVISION=CC9D
ID_SCSI_COMPAT=SSeagate_GoFlex_Desk_Mac_NA0PGY4H
ID_SERIAL=ST3000DM001-9YN166_Z1F0D3D7
ID_SERIAL_SHORT=Z1F0D3D7
ID_TYPE=disk
ID_WWN=0x5000c5003f6c77c9
ID_WWN_WITH_EXTENSION=0x5000c5003f6c77c9
MAJOR=8
MINOR=50
SEQNUM=2952
SUBSYSTEM=block
UDEV_LOG=3
UDISKS_PRESENTATION_NOPOLICY=0
USEC_INITIALIZED=2441988304

UDEV  [2442.038288] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd1 (block)
ACTION=add
DEVLINKS=/dev/disk/by-id/ata-ST3000DM001-9YN166_Z1F0D3D7-part1 /dev/disk/by-id/scsi-SSeagate_GoFlex_Desk_Mac_NA0PGY4H-part1 /dev/disk/by-id/wwn-0x5000c5003f6c77c9-part1 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1
DEVNAME=/dev/sdd1
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/host13/target13:0:0/13:0:0:0/block/sdd/sdd1
DEVTYPE=partition
ID_ATA=




CK-LIST-SESSIONS
Session1:
        unix-user = '1000'
        realname = 'Knoppix User'
        seat = 'Seat1'
        session-type = ''
        active = TRUE
        x11-display = ''
        x11-display-device = ''
        display-device = '/dev/tty5'
        remote-host-name = ''
        is-local = TRUE
        on-since = '2013-01-07T00:21:20.802524Z'
        login-session-id = ''
        idle-since-hint = '2013-01-07T00:21:50.720558Z'
Session2:
        unix-user = '1000'
        realname = 'Knoppix User'
        seat = 'Seat2'
        session-type = ''
        active = FALSE
        x11-display = ':0'
        x11-display-device = '/dev/tty5'
        display-device = ''
        remote-host-name = ''
        is-local = FALSE
        on-since = '2013-01-07T00:21:39.374626Z'
        login-session-id = ''

ID HALDAEMON
uid=104(haldaemon) gid=110(haldaemon) groups=110(haldaemon)

UNAME-A
Linux Microknoppix 3.6.11 #12 SMP PREEMPT Thu Dec 20 04:04:10 CET 2012 i686 GNU/Linux

---

