---
title: "Memory Card Reader woes"
date: 2006-08-16
forum: General Help
---

### Post by funnyguyfunnyguy on 2006-08-16
I have a memory card reader in my computer that does not work under Ubuntu 6.06. The card reader does work under Windows XP. When a card is inserted, a little green light goes on next to the slot. If I put the card in at boot the light goes on; however, when Ubuntu is booting it turns off when the Ubuntu boot screen says "mount file systems" the second item at boot. Any ideas? This is one of two things keeping me from switch to Ubuntu full time.

---

### Post by zxee on 2006-08-16
What brand computer is this, was this an add on card reader or OEM?
Post the output from dmesg (typed into a shell/terminal).

---

### Post by funnyguyfunnyguy on 2006-08-17
I built the computer several years ago. It is an add on card reader.

Occasionally (twice) the card reader has functioned properly, but then, a day or so later, it will disappear from the system i.e. Places -> Computer and System -> Administration -> Disks.

Here are the install instructions. Do I need to follow all of them? I thought that Ubuntu 6.06 came with support for usb. Furthermore, since Ubuntu has recognized them in the past, would it be safe to assume that I would not need to re-compile the kernel?

> 
Installation Under Linux
This document was modified from
"http://www.linux-usb.org/USB-guide/book1.html" which was written by Brad Hards.

System Requirement:
kernel versions 2.2.7 and later contain the USB code.

Install Card Reader step by step:

1. Backup Kernel
#cd /usr/src
#cp linux-2.4 linux-2.4.bak
#cp /boot/vmlinuz vmlinuz.bak

2. configure USB into kernel. Use of "make menuconfig" is recommended.
    Under "USB support", you need to select "Support for USB". You also need to
    select either UHCI (Intel PIIX4, VIA, ...) support, UHCI Alternate Driver (JE)
support or OHCI-HCD (Compaq, iMacs, OPTi, SiS, ALi, ...) support. Which one you
select is dependent on what kind of motherboard or adapter you have.
      select "USB Mass Storage support"
      select "Preliminary USB Device Filesystem"
      select "SCSI support"
      select "SCSI disk support"
      select "/proc support"

5. make dep     (advanced user)

4. Append one line into /etc/modules.conf, then reboot Linux
                 options scsi_mod max_scsi_luns=8
      . Rebuild the kernel and the modules (if you configured to build as modules),
    and install the new kernel and the new modules. Reboot the system.
    If you are using modules, you need to load the following modules:
    a. usbcore.o
    b. usb-uhci.o, uhci.o or usb-ohci.o
    c. usb-storage.o
                                            20
                USB2.0                 Card reader Manual
    Inspect the kernel logs. If there isn't anything that could be USB related,
    likely causes are use of the wrong driver (UHCI when you needed OHCI or
    OHCI when you needed UHCI), not physically installing the hardware,
    a BIOS configuration that disables USB or stuffing up the configuration or
    installation of the kernel.
      Use the mount command: mount -t usbdevfs none /proc/bus/usb. Note that the
      'none' keyword is arbitrary.
    If you do not want to have to mount the filesystem each time you reboot the
system,you can add the following to /etc/fstab after the /proc entry.none .
/proc/bus/usb                  usbdevfs          defaults    0     0

5. Edit /etc/fstab
    The exact syntax depends on the Card Reader. The best way is to make suitable
entries in /etc/fstab. The suitable entries for Card Reader would be:
    /dev/sda1         /mnt/sm          auto               noauto,user 0   0
    /dev/sdb1         /mnt/cf           auto              noauto,user 0   0
    /dev/sdc1         /mnt/mmc          auto               noauto,user 0   0
    /dev/sdd1       /mnt/ms              auto              noauto,user 0    0

6 . To check if all flash card has been attached, type the following line at console
mode cat /proc/scsi/scsi
 Linux will response as follows if the flash cards are attached successfully
 [root@localhost root]# cat /proc/scsi/scsi
   Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic Model: USB Storage-SMC Rev: I03A
  Type:     Direct-Access                     ANSI SCSI revision:2
                                                                 0
Host: scsi0 Channel: 00 Id: 00 Lun: 01
  Vendor: Generic Model: USB Storage-CFC Rev: I03A
  Type:     Direct-Access                     ANSI SCSI revision:2
                                                                 0
Host: scsi0 Channel: 00 Id: 00 Lun: 02
  Vendor: Generic Model: USB Storage-MMC Rev: I03A
  Type:     Direct-Access                     ANSI SCSI revision:2
                                                                 0
Host: scsi0 Channel: 00 Id: 00 Lun: 03
                                              21
               USB2.0            Card reader Manual
  Vendor: Generic Model: USB Storage-MSC Rev: I03A
  Type:    Direct-Access                  ANSI SCSI revision:2
                                                             0

7. Create matching mount points in the actual file system:
    mkdir /mnt/sm
    mkdir /mnt/cf
    mkdir /mnt/mmc
    mkdir /mnt/ms

8. Mount Card Reader: Mount the detected flash card to a directory, please type the
following lines, then you can access the content of flash cards from the mapping
directory.
    mount /dev/sda1 /mnt/sm
    mount /dev/sdb1 /mnt/cf
    mount /dev/sdc1 /mnt/mmc
    mount /dev/sdd1 /mnt/ms

Note:
    Note that the above entries assume you have no other SCSI devices.If you do have
other devices, then the USB disk may not be /dev/sda, but could instead be /dev/sdb,
/dev/sdc or some other device.



Thanks for any and all help

---

### Post by funnyguyfunnyguy on 2006-08-17
Here is the dmesg

> [17179572.764000] highmem bounce pool size: 64 pages
[17179572.764000] VFS: Disk quotas dquot_6.5.1
[17179572.764000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.764000] Initializing Cryptographic API
[17179572.764000] io scheduler noop registered
[17179572.764000] io scheduler anticipatory registered
[17179572.764000] io scheduler deadline registered
[17179572.764000] io scheduler cfq registered
[17179572.764000] isapnp: Scanning for PnP cards...
[17179573.124000] isapnp: No Plug & Play device found
[17179573.136000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.140000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.140000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.140000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.140000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.140000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.140000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.140000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.144000] **** SET: Misaligned resource pointer: dfecf222 Type 07 Len 0
[17179573.144000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179573.144000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 177
[17179573.144000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.144000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.144000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.144000] mice: PS/2 mouse device common for all mice
[17179573.144000] EISA: Probing bus 0 at eisa.0
[17179573.144000] Cannot allocate resource for EISA slot 4
[17179573.144000] Cannot allocate resource for EISA slot 5
[17179573.144000] EISA: Detected 0 cards.
[17179573.144000] NET: Registered protocol family 2
[17179573.172000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.184000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.184000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179573.184000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.184000] TCP: Hash tables configured (established 262144 bind 65536)
[17179573.184000] TCP reno registered
[17179573.184000] TCP bic registered
[17179573.184000] NET: Registered protocol family 1
[17179573.184000] NET: Registered protocol family 8
[17179573.184000] NET: Registered protocol family 20
[17179573.184000] Using IPI Shortcut mode
[17179573.184000] ACPI wakeup devices:
[17179573.184000] HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
[17179573.184000] ACPI: (supports S0 S1 S3 S4 S5)
[17179573.184000] Freeing unused kernel memory: 288k freed
[17179573.236000] vga16fb: initializing
[17179573.236000] vga16fb: mapped to 0xc00a0000
[17179573.476000] Console: switching to colour frame buffer device 80x25
[17179573.476000] fb0: VGA16 VGA frame buffer device
[17179574.540000] Capability LSM initialized
[17179575.464000] AEC6280R: IDE controller at PCI slot 0000:01:0a.0
[17179575.464000] **** SET: Misaligned resource pointer: dfe7e1c2 Type 07 Len 0
[17179575.464000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[17179575.464000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 185
[17179575.464000] AEC6280R: chipset revision 7
[17179575.464000] AEC6280R: ROM enabled at 0xdb000000
[17179575.464000] AEC6280R: 100% native mode on irq 185
[17179575.464000]     ide2: BM-DMA at 0xd800-0xd807, BIOS settings: hde:pio, hdf:pio
[17179575.464000]     ide3: BM-DMA at 0xd808-0xd80f, BIOS settings: hdg:pio, hdh:pio
[17179575.464000] Probing IDE interface ide2...
[17179575.980000] hdf: WDC WD1600JB-00GVA0, ATA DISK drive
[17179576.036000] ide2 at 0xc800-0xc807,0xcc02 on irq 185
[17179576.036000] Probing IDE interface ide3...
[17179576.608000] hdf: max request size: 1024KiB
[17179576.616000] hdf: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[17179576.616000] hdf: cache flushes supported
[17179576.616000]  hdf: hdf1 hdf2 hdf3
[17179576.928000] SCSI subsystem initialized
[17179576.928000] ACPI: bus type scsi registered
[17179576.928000] libata version 1.20 loaded.
[17179576.932000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179576.932000] NFORCE2: chipset revision 162
[17179576.932000] NFORCE2: not 100% native mode: will probe irqs later
[17179576.932000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[17179576.932000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[17179576.932000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179576.932000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA

---

### Post by funnyguyfunnyguy on 2006-08-17
more dmesg

> [17179576.932000] Probing IDE interface ide0...
[17179577.220000] hda: Maxtor 6Y060L0, ATA DISK drive
[17179577.500000] hdb: ST380021A, ATA DISK drive
[17179577.556000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.572000] hda: max request size: 128KiB
[17179577.572000] hda: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179577.572000] hda: cache flushes supported
[17179577.572000]  hda: hda1 hda2 hda3
[17179577.600000] hdb: max request size: 128KiB
[17179577.600000] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179577.600000] hdb: cache flushes not supported
[17179577.600000]  hdb: hdb1
[17179577.616000] Probing IDE interface ide1...
[17179578.352000] hdc: TSSTcorpCD/DVDW TS-H552B, ATAPI CD/DVD-ROM drive
[17179579.136000] hdd: LITE-ON LTR-52327S, ATAPI CD/DVD-ROM drive
[17179579.192000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.232000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.232000] Uniform CD-ROM driver Revision: 3.20
[17179579.240000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.692000] usbcore: registered new driver usbfs
[17179579.692000] usbcore: registered new driver hub
[17179579.692000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179579.692000] **** SET: Misaligned resource pointer: dfa41502 Type 07 Len 0
[17179579.692000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179579.692000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 193
[17179579.692000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179579.692000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179579.692000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179579.692000] ohci_hcd 0000:00:02.0: irq 193, io mem 0xdd000000
[17179579.744000] ieee1394: Initialized config rom entry `ip1394'
[17179579.748000] hub 1-0:1.0: USB hub found
[17179579.748000] hub 1-0:1.0: 3 ports detected
[17179579.852000] **** SET: Misaligned resource pointer: dfb50f22 Type 07 Len 0
[17179579.852000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[17179579.852000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 201
[17179579.852000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179579.852000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179579.852000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179579.852000] ohci_hcd 0000:00:02.1: irq 201, io mem 0xdd001000
[17179579.908000] hub 2-0:1.0: USB hub found
[17179579.908000] hub 2-0:1.0: 3 ports detected
[17179580.012000] **** SET: Misaligned resource pointer: dfb50c22 Type 07 Len 0
[17179580.012000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179580.012000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 209
[17179580.012000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179580.012000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179580.012000] ehci_hcd 0000:00:02.2: debug port 1
[17179580.012000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179580.012000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179580.012000] ehci_hcd 0000:00:02.2: irq 209, io mem 0xdd002000
[17179580.012000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.012000] hub 3-0:1.0: USB hub found
[17179580.012000] hub 3-0:1.0: 6 ports detected
[17179580.116000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179580.116000] **** SET: Misaligned resource pointer: dfb50922 Type 07 Len 0
[17179580.116000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179580.116000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 217
[17179580.168000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[217]  MMIO=[dc000000-dc0007ff]  Max Packet=[2048]
[17179580.212000] Probing IDE interface ide3...
[17179580.932000] Attempting manual resume
[17179580.968000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.976000] kjournald starting.  Commit interval 5 seconds
[17179581.084000] usb 3-5: new high speed USB device using ehci_hcd and address 4
[17179581.448000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011066600000724]
[17179581.956000] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179582.068000] usb 3-5: new high speed USB device using ehci_hcd and address 5
[17179582.940000] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179583.052000] usb 3-5: new high speed USB device using ehci_hcd and address 6
[17179583.460000] usb 3-5: device not accepting address 6, error -71
[17179583.572000] usb 3-5: new high speed USB device using ehci_hcd and address 7
[17179583.980000] usb 3-5: device not accepting address 7, error -71
[17179583.980000] ohci_hcd 0000:00:02.1: wakeup
[17179584.364000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[17179584.880000] usb 2-2: new full speed USB device using ohci_hcd and address 3
[17179593.012000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.016000] agpgart: Detected NVIDIA nForce2 chipset
[17179593.020000] agpgart: AGP aperture is 64M @ 0xd4000000
[17179593.352000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179593.352000] **** SET: Misaligned resource pointer: c1a0dca2 Type 07 Len 0
[17179593.352000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[17179593.352000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 193
[17179593.352000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179593.360000] Real Time Clock Driver v1.12
[17179593.368000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.668000] input: PC Speaker as /class/input/input1
[17179593.676000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[17179593.676000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5500
[17179593.812000] parport: PnPBIOS parport detected.
[17179593.812000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179593.876000] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
[17179593.876000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.984000] FDC 0 is a post-1991 82077
[17179594.084000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179594.196000] nvidia: module license 'NVIDIA' taints kernel.
[17179594.204000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 177
[17179594.204000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179594.260000] ts: Compaq touchscreen protocol output
[17179594.780000] eth0: no link during initialization.
[17179594.800000] usbcore: registered new driver snd-usb-audio
[17179595.020000] eth0: link up.
[17179595.832000] NET: Registered protocol family 17
[17179595.996000] lp0: using parport0 (interrupt-driven).
[17179596.032000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179596.032000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179596.032000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179596.116000] Adding 2377612k swap on /dev/hda3.  Priority:-1 extents:1 across:2377612k
[17179596.344000] EXT3 FS on hda2, internal journal
[17179596.528000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179596.528000] md: bitmap version 4.39
[17179597.244000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179597.608000] cdrom: open failed.
[17179598.404000] cdrom: open failed.
[17179598.408000] cdrom: open failed.
[17179598.648000] NET: Registered protocol family 10
[17179598.648000] lo: Disabled Privacy Extensions
[17179598.648000] IPv6 over IPv4 tunneling driver
[17179599.196000] kjournald starting.  Commit interval 5 seconds
[17179599.196000] EXT3 FS on hdf1, internal journal
[17179599.196000] EXT3-fs: mounted filesystem with ordered data mode.
[17179605.088000] ACPI: Power Button (FF) [PWRF]
[17179605.088000] ACPI: Power Button (CM) [PWRB]
[17179605.200000] ibm_acpi: ec object not found
[17179605.232000] pcc_acpi: loading...
[17179609.396000] eth0: no IPv6 routers present
[17179610.544000] ppdev: user-space parallel port driver
[17179610.748000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179610.748000] apm: overridden by ACPI.
[17179614.508000] Bluetooth: Core ver 2.8
[17179614.508000] NET: Registered protocol family 31
[17179614.508000] Bluetooth: HCI device and connection manager initialized
[17179614.508000] Bluetooth: HCI socket layer initialized
[17179614.524000] Bluetooth: L2CAP ver 2.8
[17179614.524000] Bluetooth: L2CAP socket layer initialized
[17179614.592000] Bluetooth: RFCOMM socket layer initialized
[17179614.592000] Bluetooth: RFCOMM TTY layer initialized
[17179614.592000] Bluetooth: RFCOMM ver 1.7


---

### Post by funnyguyfunnyguy on 2006-08-17
The last bit of dmesg

> [17179906.620000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17179906.620000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17179906.752000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17179906.752000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17188586.076000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17188586.076000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17188586.632000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188586.632000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188603.976000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188603.976000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188614.204000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188614.204000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188617.276000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188617.276000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188649.584000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17188649.584000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17188694.520000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188694.520000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188698.088000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188698.088000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188704.088000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188704.088000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188709.596000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17188709.596000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17188712.600000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188712.600000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188718.528000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188718.528000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188727.504000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188727.504000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188741.492000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188741.492000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188755.480000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17188760.948000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17188760.992000] NTFS volume version 3.1.
[17188817.676000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17188817.676000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17188822.300000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188822.300000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188855.004000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188855.004000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188869.476000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188869.476000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188879.644000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17188879.644000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17188904.288000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188904.288000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188915.956000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188915.956000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188935.888000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188935.888000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188939.400000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17188939.400000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17188944.664000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188944.664000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188951.072000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188951.072000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188960.216000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188960.216000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188983.644000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188983.644000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188999.012000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188999.012000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188999.400000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17188999.400000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17189025.916000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189025.916000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189038.184000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189038.184000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189047.504000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189047.504000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189070.220000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17189070.220000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17189077.028000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189077.028000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189083.384000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189083.384000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189091.944000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189091.944000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189118.928000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189118.928000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189135.760000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17189135.760000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17189136.488000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189136.488000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189141.716000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189141.716000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189178.004000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189178.004000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189178.020000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17189178.176000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17189221.844000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17189221.844000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17189228.664000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189228.664000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189247.208000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189247.208000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189300.880000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17189300.880000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17189301.260000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189301.260000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189353.156000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189353.156000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189363.632000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17189363.632000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17189374.624000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189374.624000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189386.988000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189386.988000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189483.904000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17189483.904000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17189486.648000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189486.648000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189544.556000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17189544.556000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17189549.380000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189549.380000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189748.216000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17189748.216000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17189750.244000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189750.244000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189785.156000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189785.156000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17189929.648000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17189929.648000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17189968.620000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17189968.644000] ISOFS: changing to secondary root
[17189975.188000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17189975.188000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190059.936000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190059.936000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190060.684000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190060.684000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190207.428000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190207.428000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190403.852000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190403.852000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190404.200000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190404.200000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190449.472000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190449.472000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190452.648000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190452.648000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190469.012000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190469.012000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190485.432000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190485.432000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190489.712000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190489.712000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190494.052000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190494.052000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190497.772000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190497.772000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190544.648000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190544.648000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190601.604000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190601.604000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190607.092000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190607.092000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190643.804000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190643.804000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190647.232000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190647.232000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190668.764000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190668.764000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190670.764000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190670.764000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190673.916000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190673.916000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190697.356000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190697.356000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190737.984000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190737.984000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190748.936000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190748.936000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190760.304000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190760.304000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190768.360000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190768.360000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190774.552000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190774.552000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190779.964000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190779.964000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190784.276000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190784.276000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190789.400000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190789.400000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190797.956000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190797.956000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190803.888000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190803.888000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190823.596000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190823.596000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190828.748000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190828.748000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190834.184000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190834.184000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190837.876000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190837.876000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190842.212000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190842.212000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190848.264000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190848.264000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190852.868000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190852.868000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190856.680000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190856.680000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190857.860000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190857.860000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190862.528000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190862.528000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190871.108000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190871.108000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190877.152000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190877.152000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190882.720000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190882.720000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190891.144000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190891.144000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190895.336000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190895.336000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190903.828000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190903.828000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190908.196000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190908.196000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190955.144000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17190955.144000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17190977.000000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190977.000000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190981.016000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190981.016000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190984.612000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190984.612000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190987.980000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190987.980000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17190998.656000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17190998.656000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191017.148000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17191017.148000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17191038.812000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191038.812000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191053.548000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191053.548000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191060.728000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191060.728000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191066.248000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191066.248000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191069.892000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191069.892000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191074.592000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191074.592000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191077.112000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17191077.112000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17191080.880000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191080.880000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191084.868000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191084.868000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191088.708000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191088.708000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191093.472000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191093.472000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191097.536000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191097.536000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191102.256000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191102.256000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191112.408000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191112.408000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191116.628000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191116.628000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191120.084000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191120.084000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191137.152000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17191137.152000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17191150.180000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191150.180000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191174.120000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191174.120000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191199.036000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17191199.036000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17191230.756000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191230.756000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17191272.156000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17191272.156000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17191284.592000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17191284.592000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.


---

