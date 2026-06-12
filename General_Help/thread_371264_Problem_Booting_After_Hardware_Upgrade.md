---
title: "Problem Booting After Hardware Upgrade"
date: 2007-02-26
forum: General Help
---

### Post by bbjonz on 2007-02-26
Hi Everyone,

I upgraded my old (AMD 1gz 384MB RAM) PC on which I run Ubuntu server (6.06--Dapper).  I added another hard drive and a PCI USB 2.0 card.  After partitioning the drive and making the appropriate changes to fstab, I rebooted but got just a blinking cursor after the mem check screen.  I booted from the Ubuntu server iso disk and then told it to boot from the first hard drive.  It booted just fine.  I don't see anything crazy in the dmesg output but I could be wrong.  Seems to me that adding the drive and the partitions goofed something up in the boot kernel.  My guess is it's a simple fix but I don't know what to look for where.  Any help would be appreciated.

Joe

fstab table:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1    #root
/dev/hda5       none            swap    sw              0       1
/dev/hda3       /home           auto    defaults        0       1               #user home
/dev/hdb1      /mnt/intstorage/music auto       defaults        0       1       #Seagate music storage
/dev/hdb2      /mnt/intstorage/images auto      defaults        0       1       #Seagate image storage
/dev/sda1       /mnt/extstorage/music auto defaults     0       1               #External music storage
/dev/sda2       /mnt/extstorage/images auto defaults     0       1              #External image storage
/dev/sda3       /mnt/extstorage/misc auto defaults     0       1                #External backups
/dev/sdb2       /media/ipod     vfat    rw,user         0       0               #ipod 
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0              #since removed floppy drive


dmesg output (not sure where to start but here it is):

[42949389.440000] Linux agpgart interface v0.101 (c) Dave Jones
[42949389.440000] agpgart: Detected AMD 761 chipset
[42949389.460000] agpgart: AGP aperture is 128M @ 0xd0000000
[42949389.470000] parport_pc: VIA 686A/8231 detected
[42949389.470000] parport_pc: probing current configuration
[42949389.470000] parport_pc: Current parallel port base: 0x378
[42949389.480000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[42949389.560000] parport_pc: VIA parallel port: io=0x378, irq=7
[42949389.980000] gameport: EMU10K1 is pci0000:00:09.1/gameport0, io 0xe000, speed 764kHz
[42949390.030000] **** SET: Misaligned resource pointer: d7245aa2 Type 07 Len 0
[42949390.030000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[42949390.030000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[42949390.230000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[42949390.240000] shpchp: HPC vendor_id 1022 device_id 700f ss_vid 0 ss_did 0
[42949390.240000] shpchp: shpc_init: cannot reserve MMIO region
[42949390.240000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[42949390.290000] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
[42949390.290000]   [http://www.scyld.com/network/ne2k-pci.html](http://www.scyld.com/network/ne2k-pci.html)
[42949390.290000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[42949390.290000] eth0: RealTek RTL-8029 found at 0xec00, IRQ 11, 00:30:84:30:CE:E8.
[42949390.620000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
[42949390.620000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[42949390.900000] input: PC Speaker as /class/input/input2
[42949391.060000] Floppy drive(s): fd0 is 1.44M
[42949391.080000] FDC 0 is a post-1991 82077
[42949392.080000] SCSI subsystem initialized
[42949392.110000] Initializing USB Mass Storage driver...
[42949392.120000] scsi0 : SCSI emulation for USB Mass Storage devices
[42949392.120000] usbcore: registered new driver usb-storage
[42949392.120000] USB Mass Storage support registered.
[42949392.120000] usb-storage: device found at 2
[42949392.120000] usb-storage: waiting for device to settle before scanning
[42949392.700000] lp0: using parport0 (interrupt-driven).
[42949392.760000] NET: Registered protocol family 10
[42949392.760000] lo: Disabled Privacy Extensions
[42949392.760000] IPv6 over IPv4 tunneling driver
[42949392.910000] Adding 1124508k swap on /dev/hda5.  Priority:-1 extents:1 across:1124508k
[42949392.990000] EXT3 FS on hda1, internal journal
[42949393.290000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[42949393.290000] md: bitmap version 4.39
[42949393.900000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[42949394.190000] cdrom: open failed.
[42949395.070000] cdrom: open failed.
[42949395.930000] kjournald starting.  Commit interval 5 seconds
[42949395.930000] EXT3 FS on hda3, internal journal
[42949395.930000] EXT3-fs: mounted filesystem with ordered data mode.
[42949395.980000] kjournald starting.  Commit interval 5 seconds
[42949395.980000] EXT3 FS on hdb1, internal journal
[42949395.980000] EXT3-fs: mounted filesystem with ordered data mode.
[42949396.010000] kjournald starting.  Commit interval 5 seconds
[42949396.020000] EXT3 FS on hdb2, internal journal
[42949396.020000] EXT3-fs: mounted filesystem with ordered data mode.
[42949397.120000]   Vendor: Initio    Model: WD2500JB-00GVC0   Rev: 1.05
[42949397.120000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[42949397.120000] usb-storage: device scan complete
[42949397.180000] Driver 'sd' needs updating - please use bus_type methods
[42949397.180000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[42949397.180000] sda: assuming drive cache: write through
[42949397.200000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[42949397.200000] sda: assuming drive cache: write through
[42949397.210000]  sda: sda1 sda2 sda3
[42949397.230000] sd 0:0:0:0: Attached scsi disk sda
[42949397.240000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[42949399.100000] ip_tables: (C) 2000-2002 Netfilter core team
[42949399.240000] Netfilter messages via NETLINK v0.30.
[42949399.250000] ip_conntrack version 2.4 (3071 buckets, 24568 max) - 232 bytes per conntrack
[42949402.770000] eth0: no IPv6 routers present

---

### Post by bbjonz on 2007-02-26
Just to update, I decided to upgrade to Edgy server via apt-get.  Installation was without incident but the computer still won't boot without first going the iso CD.  Strange.  The first entry in my grub config file is:

title           Ubuntu, kernel 2.6.17-11-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-server root=UUID=fc58dd52-46fb-47ca-a60b-d093c7fbc361 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-server
savedefault
boot


It should work, right?  But still doesn't.

---

### Post by pwayboy on 2007-03-05
Same problem here with Ubuntu 6.10-Edgy trying to boot from a SCSI drive on an Adaptec 29160 controller.  After the "Boot from CD" message in the BIOS, it just sits there.

I was able to boot from the iso disk with the option "boot from hard drive."  Booted just fine except for screen resolution was reduced to 800x600 (from 1280x1024).

I've been using linux for only a few days, so I'm more of a n00b than you.  Guess I'll hit the forums till I can figure it out!

---

### Post by pwayboy on 2007-03-06
OK, fixed it.  Hmm, that was easy!  I forgot to mention I have a spare ATA hard drive (hd1) in my system.  I inadvertently chose GRUB to install its boot header to hd1 instead of to SCSI at hd0.  Every time, it tried to boot to the ATA drive at hd1 instead of to hd0 (SCSI).

This command fixed my problem:
sudo grub-install hd0

As for the screen resolution issue, I tried to edit XORG.CONF as suggested in several forum posts.  I hosed the whole system with a XORG error, and I don't have time to fix.  Oh, well.  Time to reinstall.

---

