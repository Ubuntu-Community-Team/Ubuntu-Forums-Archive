---
title: "Why is it taking me 5 minutes to boot ubuntu???"
date: 2005-10-31
forum: General Help
---

### Post by docmanny on 2005-10-31
I'm using Breezy now, and Hoary was never quick (about 2:30 from grub to login)

I've tried booting in recovery mode and takes about 2:45 (hotplug went quick)

I tried the initng method, but for some reason Gnome then became painfully slow with opening windows, running javascripts, and everything else.

So this morning, it takes 5:00 from grub to usefulness.

Hangup areas: 
creating initial device nodes
checking root file system
hotplug (I know there's nothing much I can do there)
In the log, several drivers (usb, input) seem to be loaded several times (already loaded message)

And this is not some 486 system, its a P4-3Ghz, with 1G of RAM.

I'll settle for 2:30 minutes to boot, or I'm going abandon ubuntu....

Here's the dmesg:
> [4294669.390000] Freeing initrd memory: 5177k freed
[4294669.391000] ACPI: Looking for DSDT in initrd... not found!
[4294669.428000]  not found!
[4294669.439000] ENABLING IO-APIC IRQs
[4294669.439000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294669.550000] NET: Registered protocol family 16
[4294669.550000] EISA bus registered
[4294669.550000] ACPI: bus type pci registered
[4294669.550000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[4294669.550000] PCI: Using configuration type 1
[4294669.550000] mtrr: v2.0 (20020519)
[4294669.550000] ACPI: Subsystem revision 20050729
[4294669.560000] ACPI: Interpreter enabled
[4294669.560000] ACPI: Using IOAPIC for interrupt routing
[4294669.561000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.561000] PCI: Probing PCI hardware (bus 00)
[4294669.561000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.563000] Boot video device is 0000:00:02.0
[4294669.564000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294669.564000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.575000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.575000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[4294669.583000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294669.583000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294669.584000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294669.584000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[4294669.584000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.584000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.584000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294669.585000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294669.585000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.585000] pnp: PnP ACPI init
[4294669.591000] pnp: PnP ACPI: found 14 devices
[4294669.591000] PnPBIOS: Disabled by ACPI PNP
[4294669.591000] PCI: Using ACPI for IRQ routing
[4294669.591000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.594000] pnp: 00:09: ioport range 0x480-0x487 has been reserved
[4294669.594000] pnp: 00:09: ioport range 0xd00-0xd07 has been reserved
[4294669.595000] audit: initializing netlink socket (disabled)
[4294669.595000] audit: initialized
[4294669.595000] highmem bounce pool size: 64 pages
[4294669.595000] VFS: Disk quotas dquot_6.5.1
[4294669.595000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.595000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.595000] devfs: boot_options: 0x0
[4294669.595000] Initializing Cryptographic API
[4294669.595000] isapnp: Scanning for PnP cards...
[4294669.949000] isapnp: No Plug & Play device found
[4294669.963000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294669.964000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.965000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.965000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.965000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.966000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.967000] io scheduler noop registered
[4294669.967000] io scheduler anticipatory registered
[4294669.967000] io scheduler deadline registered
[4294669.967000] io scheduler cfq registered
[4294669.967000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.967000] EISA: Probing bus 0 at eisa.0
[4294669.967000] EISA: Detected 0 cards.
[4294669.967000] NET: Registered protocol family 2
[4294669.977000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294669.977000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[4294669.977000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.977000] TCP: Hash tables configured (established 131072 bind 65536)
[4294669.977000] NET: Registered protocol family 8
[4294669.977000] NET: Registered protocol family 20
[4294669.978000] ACPI wakeup devices:
[4294669.978000] P0P4 MC97 USB1 USB2 USB3 USB4 EUSB PS2K PS2M UAR1 ILAN
[4294669.978000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.978000] Freeing unused kernel memory: 224k freed
[4294669.999000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.123000] vga16fb: initializing
[4294670.123000] vga16fb: mapped to 0xc00a0000
[4294670.233000] Console: switching to colour frame buffer device 80x30
[4294670.233000] fb0: VGA16 VGA frame buffer device
[4294671.502000] Capability LSM initialized
[4294671.527000] NET: Registered protocol family 1
[4294671.572000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.572000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.572000] ACPI: bus type ide registered
[4294671.588000] SCSI subsystem initialized
[4294671.589000] libata version 1.11 loaded.
[4294671.590000] ata_piix version 1.03
[4294671.590000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[4294671.590000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294671.590000] ata1: SATA max UDMA/133 cmd 0xEFE0 ctl 0xEFAE bmdma 0xEF90 irq 18
[4294671.590000] ata2: SATA max UDMA/133 cmd 0xEFA0 ctl 0xEFAA bmdma 0xEF98 irq 18
[4294671.744000] ata1: dev 0 cfg 49:2f00 82:346b 83:7f61 84:4003 85:3469 86:3c41 87:4003 88:207f
[4294671.744000] ata1: dev 0 ATA, max UDMA/133, 390721968 sectors: lba48
[4294671.745000] ata1: dev 0 configured for UDMA/133
[4294671.745000] scsi0 : ata_piix
[4294671.745000] ata2: SATA port has no device.
[4294671.745000] scsi1 : ata_piix
[4294671.745000]   Vendor: ATA       Model: WDC WD2000JD-22H  Rev: 08.0
[4294671.745000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294671.761000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[4294671.761000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294671.761000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294671.761000] ICH5: chipset revision 2
[4294671.761000] ICH5: not 100% native mode: will probe irqs later
[4294671.761000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[4294671.761000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[4294671.761000] Probing IDE interface ide0...
[4294672.025000] hda: Maxtor 6Y120P0, ATA DISK drive
[4294672.280000] hdb: ST3300831A, ATA DISK drive
[4294672.331000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.331000] Probing IDE interface ide1...
[4294673.003000] hdc: PLEXTOR DVDR PX-708A, ATAPI CD/DVD-ROM drive
[4294673.717000] hdd: TOSHIBA DVD-ROM SD-M1212, ATAPI CD/DVD-ROM drive
[4294673.768000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.768000] Probing IDE interface ide2...
[4294674.281000] Probing IDE interface ide3...
[4294674.793000] Probing IDE interface ide4...
[4294675.305000] Probing IDE interface ide5...
[4294675.826000] hda: max request size: 128KiB
[4294675.836000] hda: 240121728 sectors (122942 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(100)
[4294675.836000] hda: cache flushes supported
[4294675.836000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
[4294675.844000] hdb: max request size: 1024KiB
[4294675.844000] hdb: 586072368 sectors (300069 MB) w/8192KiB Cache, CHS=36481/255/63, UDMA(100)
[4294675.844000] hdb: cache flushes supported
[4294675.844000]  /dev/ide/host0/bus0/target1/lun0: p1
[4294675.868000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294675.868000] Uniform CD-ROM driver Revision: 3.20
[4294675.870000] hdd: ATAPI 32X DVD-ROM drive, 256kB Cache
[4294675.888000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[4294675.888000] SCSI device sda: drive cache: write back
[4294675.888000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[4294675.888000] SCSI device sda: drive cache: write back
[4294675.888000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 p7 p8 >
[4294675.957000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294678.673000] Attempting manual resume
[4294678.689000] swsusp: Suspend partition has wrong signature?
[4294678.723000] usbcore: registered new driver usbfs
[4294678.723000] usbcore: registered new driver hub
[4294678.725000] USB Universal Host Controller Interface driver v2.2
[4294678.725000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294678.725000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294678.725000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
[4294678.787000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294678.787000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ef00
[4294678.787000] hub 1-0:1.0: USB hub found
[4294678.787000] hub 1-0:1.0: 2 ports detected
[4294678.790000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294678.790000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294678.790000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
[4294678.852000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294678.852000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ef20
[4294678.852000] hub 2-0:1.0: USB hub found
[4294678.852000] hub 2-0:1.0: 2 ports detected
[4294678.855000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294678.855000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294678.855000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI #3
[4294678.917000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294678.917000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef40
[4294678.917000] hub 3-0:1.0: USB hub found
[4294678.917000] hub 3-0:1.0: 2 ports detected
[4294678.949000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
[4294678.949000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294678.949000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
[4294678.949000] ehci_hcd 0000:00:1d.7: debug port 1
[4294678.949000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294678.949000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe77bc00
[4294678.953000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294678.953000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294678.953000] hub 4-0:1.0: USB hub found
[4294678.953000] hub 4-0:1.0: 6 ports detected
[4294679.040000] 8139too Fast Ethernet driver 0.9.27
[4294679.040000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294679.040000] eth0: RealTek RTL8139 at 0xd800, 00:11:2f:9f:3e:66, IRQ 22
[4294679.040000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294679.042000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294679.245000] usb 4-4: new high speed USB device using ehci_hcd and address 2[4294679.320000] hub 4-4:1.0: USB hub found
[4294679.321000] hub 4-4:1.0: 4 ports detected
[4294679.561000] usb 4-4.1: new full speed USB device using ehci_hcd and address 3
[4294685.524000] ACPI: CPU0 (power states: C1[C1])
[4294685.980000] Attempting manual resume
[4294685.980000] swsusp: Suspend partition has wrong signature?
[4294685.998000] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[4294686.346000] ReiserFS: sda5: using ordered data mode
[4294686.355000] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294686.356000] ReiserFS: sda5: checking transaction log (sda5)
[4294686.375000] ReiserFS: sda5: Using r5 hash to sort names
[4294689.422000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294745.542000] Adding 1461872k swap on /dev/sda6.  Priority:-1 extents:1
[4294776.502000] parport: PnPBIOS parport detected.
[4294776.502000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294776.611000] lp0: using parport0 (interrupt-driven).
[4294777.189000] mice: PS/2 mouse device common for all mice
[4294777.977000] input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
[4294784.019000] ts: Compaq touchscreen protocol output
[4294799.515000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294801.453000] cdrom: open failed.
[4294801.459000] cdrom: open failed.
[4294809.685000] kjournald starting.  Commit interval 5 seconds
[4294809.685000] EXT3 FS on sda1, internal journal
[4294809.685000] EXT3-fs: mounted filesystem with ordered data mode.
[4294809.725000] ReiserFS: sda7: found reiserfs format "3.6" with standard journal
[4294809.927000] ReiserFS: sda7: using ordered data mode
[4294809.933000] ReiserFS: sda7: journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294809.934000] ReiserFS: sda7: checking transaction log (sda7)
[4294809.943000] ReiserFS: sda7: Using r5 hash to sort names
[4294812.878000] kjournald starting.  Commit interval 5 seconds
[4294812.878000] EXT3 FS on hdb1, internal journal
[4294812.878000] EXT3-fs: mounted filesystem with ordered data mode.
[4294818.510000] Linux agpgart interface v0.101 (c) Dave Jones
[4294818.557000] agpgart: Detected an Intel 865 Chipset.
[4294818.557000] agpgart: Detected 8060K stolen memory.
[4294818.630000] agpgart: AGP aperture is 128M @ 0xf0000000
[4294822.983000] hw_random: RNG not detected
[4294824.464000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294824.511000] shpchp: shpc_init : shpc_cap_offset == 0
[4294824.511000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294837.263000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294837.263000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294837.617000] AC'97 0 analog subsections not ready
[4294837.679000] intel8x0_measure_ac97_clock: measured 49993 usecs
[4294837.679000] intel8x0: clocking to 48000
[4294850.050000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3A11
[4294850.117000] usbcore: registered new driver usblp
[4294850.117000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[4294855.137000] Real Time Clock Driver v1.12
[4294861.730000] input: PC Speaker
[4294865.221000] FDC 0 is a post-1991 82077
[4294881.623000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294882.524000] NET: Registered protocol family 17
[4294886.426000] NET: Registered protocol family 10
[4294886.426000] Disabled Privacy Extensions on device c02eb280(lo)
[4294886.426000] IPv6 over IPv4 tunneling driver
[4294894.797000] ACPI: Power Button (FF) [PWRF]
[4294894.797000] ACPI: Power Button (CM) [PWRB]
[4294896.426000] ibm_acpi: ec object not found
[4294896.855000] eth0: no IPv6 routers present
[4294936.194000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294936.194000] apm: overridden by ACPI.
[4294998.726000] Bluetooth: Core ver 2.7
[4294998.726000] NET: Registered protocol family 31
[4294998.726000] Bluetooth: HCI device and connection manager initialized
[4294998.726000] Bluetooth: HCI socket layer initialized
[4294999.651000] Bluetooth: L2CAP ver 2.7
[4294999.651000] Bluetooth: L2CAP socket layer initialized
[4295000.565000] Bluetooth: RFCOMM ver 1.5
[4295000.565000] Bluetooth: RFCOMM socket layer initialized
[4295000.565000] Bluetooth: RFCOMM TTY layer initialized


---

### Post by matthewv on 2005-10-31
A common cause of long boot up times is the failing of the synchronising clock to ntp.ubuntulinux.com... maybe thats failing?

---

### Post by docmanny on 2005-10-31
The clock gets synced near the end of the process. Should it be moved up?

---

### Post by vassie on 2005-10-31
I took the sync out

```
sudo nano /etc/default/ntpdate
```

Then comment out ntp.ubuntulinux.org

Ben

---

### Post by docmanny on 2005-10-31
But the clock sync part takes like no time. Most of the painfully slow process happens before that. I takes like 4 minute before the clock sync. I use my box for storage, gimp, firefox and open office. Music & video too. Can I get rid of some of the other stuff?

---

### Post by stozka on 2005-12-05
I'm having same situation here, but I do believe that problem lies with DHCP client getting IP. That's very slow. Try to disable network interfaces like Wifi and eth, it should boot up in less than 2 minutes.

---

### Post by hw-tph on 2005-12-05
Disable network interface hotplugging - in my experience can take a very long time. If you still want that sort of functionality, use ifplugd instead. IMHO ifplugd should be included with the base install since it is so useful - the interface up script is run when a cable is plugged in, and if you unplug a cable it is automatically brought down cleanly.


H&#229;kan

---

### Post by Bachstelze on 2005-12-05
Or just press Ctrl+C when you have "Configuring network interfaces" and "Waiting for network interface to come up".

---

### Post by mherring on 2005-12-05
I dont think it is in DHCP---I use 5.10 with a router (DHCP), and it boots up very quickly---less than a minute from the grub menu.
My 5.10 is "virgin"--ie I have done almost no custom configuration yet.  That's  maybe a clue

---

### Post by jalexstark on 2005-12-05
I upgraded from 4.10 (don't jump releases like this, it can go badly wrong).  Maybe because of the glitches that resulted, I have had some DMA disk problems, and perhaps other performance impact.  Bootup is definitely too slow (Thinkpad T20).

---

