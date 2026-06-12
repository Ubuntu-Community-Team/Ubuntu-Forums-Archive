---
title: "Mounting HDD on hoary"
date: 2005-06-07
forum: General Help
---

### Post by fireedo on 2005-06-07
I have 2 harddrive SATA and PATA HDD......and I installed my ubuntu on PATA hdd so everything goes fine and work smooth  :smile:  So this problem show up when I try to make automount my SATA drive (sda5, only this partition I want to mount) on everytime boot up following "ubuntuguide" ways.....
like this :
Q: How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?

   1. Read General Notes
   2. Read How to list partition tables?
   3.

e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows

   4.

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   5. Append the following line at the end of file

/dev/hda1       /media/windows  ntfs    umask=0222      0       0

and I have change to /dev/sda5....

the problem is my /dev/sda5 partition cant automatically load everytime boot up....I always must do this "sudo mount -a" to make my /dev/sda5 mounted........

so anyidea?   please

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=fireedo]I have 2 harddrive SATA and PATA HDD......and I installed my ubuntu on PATA hdd so everything goes fine and work smooth  :smile:  So this problem show up when I try to make automount my SATA drive (sda5, only this partition I want to mount) on everytime boot up following "ubuntuguide" ways.....
like this :
Q: How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?

   1. Read General Notes
   2. Read How to list partition tables?
   3.

e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows

   4.

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   5. Append the following line at the end of file

/dev/hda1       /media/windows  ntfs    umask=0222      0       0

and I have change to /dev/sda5....

the problem is my /dev/sda5 partition cant automatically load everytime boot up....I always must do this "sudo mount -a" to make my /dev/sda5 mounted........

so anyidea?   please[/QUOTE]
 Strange. Any error messages (you can view them by typing "dmesg", or by viewing /var/log/messages. You need to be root)

---

### Post by fireedo on 2005-06-07
[QUOTE=Alexander Kirillov]Strange. Any error messages (you can view them by typing "dmesg", or by viewing /var/log/messages. You need to be root)[/QUOTE]
 hikmah@Ubuntu:~$ dmesg
APCS] (IRQs *23), disabled.
ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 11 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
pnp: 00:00: ioport range 0x4400-0x447f has been reserved
pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
pnp: 00:00: ioport range 0x4200-0x427f has been reserved
pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
pnp: 00:01: ioport range 0x5000-0x503f has been reserved
pnp: 00:01: ioport range 0x5100-0x513f has been reserved
audit: initializing netlink socket (disabled)
audit(1118125047.819:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 4
Cannot allocate resource for EISA slot 5
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Thermal Zone [THRM] (20 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
NFORCE2: IDE controller at PCI slot 0000:00:09.0
NFORCE2: chipset revision 162
NFORCE2: not 100% native mode: will probe irqs later
NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hdb: ST3120026A, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hdb: max request size: 1024KiB
hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
hdb: cache flushes supported
 /dev/ide/host0/bus0/target1/lun0: p1 p2 p3 < p5 p6 >
Probing IDE interface ide1...
hdc: ASUS DVD-E616P2, ATAPI CD/DVD-ROM drive
hdd: ATAPI DVD DUAL 8X4X12, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 1510068k swap on /dev/hdb5.  Priority:-1 extents:1
EXT3 FS on hdb2, internal journal
hdc: ATAPI 48X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb6, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
NTFS driver 2.1.22 [Flags: R/O MODULE].
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected NVIDIA nForce2 chipset
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0xd0000000
i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 22 (level, high) -> IRQ 22
ohci_hcd 0000:00:02.0: nVidia Corporation nForce2 USB Controller
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 22, pci mem 0xdd001000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 21 (level, high) -> IRQ 21
ohci_hcd 0000:00:02.1: nVidia Corporation nForce2 USB Controller (#2)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ohci_hcd 0000:00:02.1: irq 21, pci mem 0xdd002000
ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
usb 1-3: new low speed USB device using ohci_hcd and address 2
ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 20 (level, high) -> IRQ 20
ehci_hcd 0000:00:02.2: nVidia Corporation nForce2 USB Controller
PCI: Setting latency timer of device 0000:00:02.2 to 64
ehci_hcd 0000:00:02.2: irq 20, pci mem 0xdd003000
ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
PCI: cache line size of 64 is not supported by device 0000:00:02.2
ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 6 ports detected
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.30.
ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:04.0[A] -> GSI 22 (level, high) -> IRQ 22
PCI: Setting latency timer of device 0000:00:04.0 to 64
usb 1-3: device not accepting address 2, error -110
eth0: forcedeth.c: subsystem: 0147b:1c06 bound to 0000:00:04.0
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
ohci_hcd 0000:00:02.1: wakeup
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
eth0: no link during initialization.
ohci_hcd 0000:00:02.0: wakeup
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usb 2-1: new full speed USB device using ohci_hcd and address 2
SCSI subsystem initialized
libata version 1.10 loaded.
sata_sil version 0.8
ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
ACPI: PCI interrupt 0000:01:0b.0[A] -> GSI 18 (level, high) -> IRQ 18
ata1: SATA max UDMA/100 cmd 0xE0A0E080 ctl 0xE0A0E08A bmdma 0xE0A0E000 irq 18
ata2: SATA max UDMA/100 cmd 0xE0A0E0C0 ctl 0xE0A0E0CA bmdma 0xE0A0E008 irq 18
drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
usb 2-3: new full speed USB device using ohci_hcd and address 3
ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:207f
ata1: dev 0 ATA, max UDMA/133, 234441648 sectors: lba48
ata1: dev 0 configured for UDMA/100
scsi0 : sata_sil
usbcore: registered new driver usbserial_generic
usbcore: registered new driver usbserial
drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
drivers/usb/serial/usb-serial.c: USB Serial support registered for PL-2303
pl2303 2-1:1.0: PL-2303 converter detected
usb 2-1: PL-2303 converter now attached to ttyUSB0
usbcore: registered new driver pl2303
drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver v0.12
ata2: no device found (phy stat 00000000)
scsi1 : sata_sil
  Vendor: ATA       Model: ST3120827AS       Rev: 3.42
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
usb 1-3: new low speed USB device using ohci_hcd and address 4
snd-usb-audio: probe of 2-3:1.0 failed with error -5
usbcore: registered new driver snd-usb-audio
usb 2-3: USB disconnect, address 3
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [062a:0000] on usb-0000:00:02.0-3
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ts: Compaq touchscreen protocol output
usb 2-3: new full speed USB device using ohci_hcd and address 4
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 19 (level, high) -> IRQ 19
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 122679296
[fglrx] max   LFB = 122679296
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present
CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
PPP BSD Compression module registered
PPP Deflate Compression module registered
NTFS volume version 3.1.
usb 2-2: new full speed USB device using ohci_hcd and address 5
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1056
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '050430_0207', timestamp 2005/04/30 02:08 (11a4)
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 146416
Buffer I/O error on device hdc, logical block 36604
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 146420
Buffer I/O error on device hdc, logical block 36605
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 146416
Buffer I/O error on device hdc, logical block 36604
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 146420
Buffer I/O error on device hdc, logical block 36605
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 146416
Buffer I/O error on device hdc, logical block 36604
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 146416
Buffer I/O error on device hdc, logical block 36604
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 146416
Buffer I/O error on device hdc, logical block 36604
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 146420
Buffer I/O error on device hdc, logical block 36605
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 146416
Buffer I/O error on device hdc, logical block 36604
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 146420
Buffer I/O error on device hdc, logical block 36605
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '041015_2339', timestamp 2004/10/15 23:41 (11a4)
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '050430_0207', timestamp 2005/04/30 02:08 (11a4)
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
hikmah@Ubuntu:~$


this result when I type dmesg.....

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=fireedo]hikmah@Ubuntu:~$ dmesg

scsi1 : sata_sil
  Vendor: ATA       Model: ST3120827AS       Rev: 3.42
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0

this result when I type dmesg.....[/QUOTE]

Seems that the kernel sees your scsi drive just fine (you seem to have some problems with your DVD drive, but this should not be related).

Anything relevant in the system log (you can view it using Applications-System tools-System Log)?

---

### Post by fireedo on 2005-06-07
[QUOTE=Alexander Kirillov]Seems that the kernel sees your scsi drive just fine (you seem to have some problems with your DVD drive, but this should not be related).

Anything relevant in the system log (you can view it using Applications-System tools-System Log)?[/QUOTE]
 nothing relevant on system log.....this maybe related to the kernel ?..... I have no idea.... :(

---

