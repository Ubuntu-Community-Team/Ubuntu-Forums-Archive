---
title: "Mounting Error"
date: 2007-03-22
forum: General Help
---

### Post by dustin0 on 2007-03-22
Im trying to mount my HD so i can  get some files off  of  it  but it wont let me.


Fdisk-l:
Disk /dev/hda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         676     5429938+  82  Linux swap
/dev/hda2             677        1339     5325547+  82  Linux swap
/dev/hda3            1340       19452   145492672+  83  Linux


Error #1:

mount: can't find /dev/hda3 in /etc/fstab or /etc/mtab


Error #2:

root@slax:~# sudo mount -t ext3 /dev/hda3 /mnt/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Dmesg  prints out:
Linux version 2.6.16 (root@slax) (gcc version 3.4.6) #95 Wed May 17 10:16:21 GMT 2006
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
0MB HIGHMEM available.
512MB LOWMEM available.
On node 0 totalpages: 131072
  DMA zone: 4096 pages, LIFO batch:0
  DMA32 zone: 0 pages, LIFO batch:0
  Normal zone: 126976 pages, LIFO batch:31
  HighMem zone: 0 pages, LIFO batch:0
DMI 2.1 present.
ACPI: Unable to locate RSDP
Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Built 1 zonelists
Kernel command line: vga=769 changes=slaxsave.dat max_loop=255 initrd=boot/initrd.gz init=linuxrc load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=4444 root=/dev/ram0 rw BOOT_IMAGE=boot/vmlinuz
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 65536 bytes)
Detected 1002.413 MHz processor.
Using tsc for high-res timesource
Console: colour dummy device 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 511260k/524288k available (4166k kernel code, 12504k reserved, 1287k data, 488k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 2007.08 BogoMIPS (lpj=4014179)
Security Framework v1.0.0 initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 256K
CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU: Intel Pentium III (Coppermine) stepping 06
Checking 'hlt' instruction... OK.
checking if image is initramfs...it isn't (no cpio magic); looks like an initrd
Freeing initrd memory: 1315k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfdb81, last bus=1
PCI: Using configuration type 1
ACPI: Subsystem revision 20060127
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
SCSI subsystem initialized
usbcore: registered new driver usbfs
usbcore: registered new driver hub
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI quirk: region 0400-043f claimed by PIIX4 ACPI
PCI quirk: region 0440-044f claimed by PIIX4 SMB
PIIX4 devres B PIO at 0290-0297
Boot video device is 0000:01:00.0
PCI: Bridge: 0000:00:01.0
  IO window: d000-dfff
  MEM window: fca00000-feafffff
  PREFETCH window: f2800000-f48fffff
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
NTFS driver 2.1.26 [Flags: R/O].
JFS: nTxBlock = 4005, nTxLock = 32044
SGI XFS with ACLs, security attributes, large block numbers, no debug enabled
SGI XFS Quota Management subsystem
Initializing Cryptographic API
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
Limiting direct PCI/PCI transfers.
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
vesafb: framebuffer at 0xf3000000, mapped to 0xe0a80000, using 600k, total 16384k
vesafb: mode is 640x480x8, linelength=640, pages=50
vesafb: protected mode interface info at c000:043c
vesafb: scrolling: redraw
vesafb: Pseudocolor: size=8:8:8:8, shift=0:0:0:0
Console: switching to colour frame buffer device 80x30
fb0: VESA VGA frame buffer device
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Real Time Clock Driver v1.12ac
PNP: No PS/2 controller found. Probing ports directly.
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
RAMDISK driver initialized: 16 RAM disks of 4444K size 1024 blocksize
loop: loaded (max 255 devices)
Compaq SMART2 Driver (v 2.6.0)
HP CISS Driver (v 2.6.10)
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PIIX4: IDE controller at PCI slot 0000:00:07.1
PIIX4: chipset revision 1
PIIX4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: WDC WD1600JB-75GVC0, ATA DISK drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdc: TOSHIBA DVD-ROM SD-R1312, ATAPI CD/DVD-ROM drive
hdd: CD-RW 48X24, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 512KiB
hda: 312500000 sectors (160000 MB) w/8192KiB Cache, CHS=19452/255/63, UDMA(33)
hda: cache flushes supported
 hda: hda1 hda2 hda3
hdc: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
ide-floppy driver 0.99.newide
Loading Adaptec I2O RAID: Version 2.4 Build 5go
Detecting Adaptec I2O RAID controllers...
Adaptec aacraid driver (1.1-4 May  4 2006 18:40:51)
scsi: <fdomain> Detection failed (no card)
sym53c416.c: Version 1.0.0-ac
qlogicfas: no cards were found, please specify I/O address and IRQ using iobase= and irq= optionsEmulex LightPulse Fibre Channel SCSI driver 8.1.1
Copyright(c) 2004-2005 Emulex.  All rights reserved.
Failed initialization of WD-7000 SCSI card!
megaraid cmm: 2.20.2.6 (Release Date: Mon Mar 7 00:01:03 EST 2005)
megaraid: 2.20.4.7 (Release Date: Mon Nov 14 12:27:22 EST 2005)
megasas: 00.00.02.04 Fri Feb 03 14:31:44 PST 2006
GDT-HA: Storage RAID Controller Driver. Version: 3.04
GDT-HA: Found 0 PCI Storage RAID Controllers
3ware Storage Controller device driver for Linux v1.26.02.001.
3ware 9000 Storage Controller device driver for Linux v2.26.02.007.
nsp32: loading...
ipr: IBM Power RAID SCSI Device Driver version: 2.1.2 (February 8, 2006)
libata version 1.20 loaded.
I2O subsystem v1.325
i2o: max drivers = 8
I2O Configuration OSM v1.323
I2O Bus Adapter OSM v1.317
I2O Block Device OSM v1.325
I2O SCSI Peripheral OSM v1.316
I2O ProcFS OSM v1.316
Fusion MPT base driver 3.03.07
Copyright (c) 1999-2005 LSI Logic Corporation
Fusion MPT SPI Host driver 3.03.07
Fusion MPT FC Host driver 3.03.07
Fusion MPT SAS Host driver 3.03.07
usbmon: debugfs is not available
usbcore: registered new driver hiddev
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
mice: PS/2 mouse device common for all mice
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 7, 524288 bytes)
TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
TCP bic registered
Initializing IPsec netlink socket
NET: Registered protocol family 1
NET: Registered protocol family 17
Using IPI Shortcut mode
RAMDISK: Compressed image found at block 0
EXT2-fs warning: checktime reached, running e2fsck is recommended
VFS: Mounted root (ext2 filesystem).
Freeing unused kernel memory: 488k freed
input: AT Translated Set 2 keyboard as /class/input/input0
squashfs: version 3.0 (2006/03/15) Phillip Lougher
Registering unionfs 20060423-1600
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
UDF-fs: No partition found (1)
XFS: bad magic number
XFS: SB validate failed
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
UDF-fs: No VRS found
XFS: bad magic number
XFS: SB validate failed
UDF-fs: No partition found (1)
XFS: bad magic number
XFS: SB validate failed
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
Adding 5325536k swap on /dev/hda2.  Priority:-1 extents:1 across:5325536k
Linux agpgart interface v0.101 (c) Dave Jones
fuse init (API version 7.6)
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
Intel ISA PCIC probe: not found.
Databook TCIC-2 PCMCIA probe: not found.
8139too Fast Ethernet driver 0.9.27
eth0: RealTek RTL8139 at 0xe400, 00:0e:2e:99:7d:54, IRQ 5
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
ehci_hcd 0000:00:0d.2: EHCI Host Controller
ehci_hcd 0000:00:0d.2: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:0d.2: irq 10, io mem 0xfebfff00
ehci_hcd 0000:00:0d.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 5 ports detected
usb 1-2: new high speed USB device using ehci_hcd and address 2
usb 1-2: configuration #1 chosen from 1 choice
hub 1-2:1.0: USB hub found
hub 1-2:1.0: 4 ports detected
usb 1-3: new high speed USB device using ehci_hcd and address 3
usb 1-3: configuration #1 chosen from 1 choice
hub 1-3:1.0: USB hub found
hub 1-3:1.0: 4 ports detected
ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd 0000:00:0d.0: OHCI Host Controller
ohci_hcd 0000:00:0d.0: new USB bus registered, assigned bus number 2
ohci_hcd 0000:00:0d.0: irq 5, io mem 0xfebfd000
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ohci_hcd 0000:00:0d.1: OHCI Host Controller
ohci_hcd 0000:00:0d.1: new USB bus registered, assigned bus number 3
ohci_hcd 0000:00:0d.1: irq 9, io mem 0xfebfe000
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 3-2: new low speed USB device using ohci_hcd and address 2
usb 3-2: configuration #1 chosen from 1 choice
input: HID 1241:1166 as /class/input/input1
input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:0d.1-2
piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
USB Universal Host Controller Interface driver v2.3
PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
PCI: No IRQ known for interrupt pin D of device 0000:00:07.2. Please try using pci=biosirq.
uhci_hcd 0000:00:07.2: Found HC with no IRQ.  Check BIOS/PCI 0000:00:07.2 setup!
uhci_hcd 0000:00:07.2: init 0000:00:07.2 fail, -19
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
agpgart: Detected an Intel 440BX Chipset.
agpgart: AGP aperture is 64M @ 0xf8000000
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present
VFS: Can't find ext3 filesystem on dev hda3.


So can anybody help me please

- Dustin

---

### Post by kidders on 2007-03-22
Hi there,

Ordinarily, the messages you posted mean...

> **dustin0 said:**
> mount: can't find /dev/hda3 in /etc/fstab or /etc/mtabYou forgot to specify a mount point, and your system couldn't guess one for you.

> **dustin0 said:**
> mount: wrong fs type, bad option, bad superblock...The filesystem you're mounting isn't an Ext3 one. (The relevant part of your dmesg, that this error asks you to look at, is the last line.)

It looks to me as though there are three broad possibilities:

[LIST]
[*]Your filesystem _is_ in fact an Ext3 one, but it's too badly damaged for your system to recognise it.
[*]The partition /dev/hda3 isn't formatted.
[*]The filesystem is ReiserFS, XFS, JFS, HFS, FAT.....
[/LIST]

I hope that's of some help.

---

