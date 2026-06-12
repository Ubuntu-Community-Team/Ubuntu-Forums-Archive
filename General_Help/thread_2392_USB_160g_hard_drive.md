---
title: "USB 160g hard drive"
date: 2004-10-27
forum: General Help
---

### Post by jcscar on 2004-10-27
I am a complete newbie to linux and a step by step solution to mounting my usb ntfs hard drive. I have read some thread about mounting ntfs but they are over my head. The other person always started out knowing more then me.  Please help.

---

### Post by jdong on 2004-10-27
[http://www.ubuntuforums.org/showthread.php?t=1886](http://www.ubuntuforums.org/showthread.php?t=1886)

Have you seen that thread? Are you having trouble following those instructions? Tell us what's confusing you, and hopefully we can clear it up!

---

### Post by jcscar on 2004-10-27
```
/dev/hda1  /mnt/win  ntfs  nls=iso8859-1,ro,umask=0  0  0
``` 
/dev/hda1  Would I change this to /dev/sda0 ??


/mnt/win    this puts it in the mnt/win directory I believe


nls=iso8859-1,ro,umask=0  0  0 What is all of this

---

### Post by FLeiXiuS on 2004-10-27
**Thread has been moved to General Support.**

---

### Post by jdong on 2004-10-27
No, change it to sda1. All partitions start numbering from 1.

you are correct: /mnt/win puts it in the /mnt/win folder.

the other stuff: nls sets default language. ro specifies to mount "read only" (the default NTFS drivers are incapable of writing to NTFS). umask=0 means "let all users access this folder", as opposed to "let root access this folder".


0 0 means "don't run a fsck (aka scandisk) after improper unmount"

---

### Post by jcscar on 2004-10-27
Alright I have it entered just like what I typed above but with sda1.. but it keeps telling me I don't have the directory.. How do I create a directory in root terminal?

---

### Post by jcscar on 2004-10-27
alright for now, I just changed it to mount in the /mnt directory.. but now I am coming up with the error "special device /dev/sda1 does not exist".

---

### Post by FLeiXiuS on 2004-10-27
[QUOTE=jcscar]alright for now, I just changed it to mount in the /mnt directory.. but now I am coming up with the error "special device /dev/sda1 does not exist".[/QUOTE]

Looks like linux didn't recognize your USB device.  Try running
```

modprobe usb-storage

```

After this,
```

lsmod

```

Please include the above in the next post.

---

### Post by mungkok on 2004-10-28
just use /dev/sda

---

### Post by jdong on 2004-10-28
It's very suspicious that HAL along with hotplug wouldn't load a USB drive.

Unplug and replug the drive, then post the output of **dmesg**. (The last 10 lines or so would suffice)

---

### Post by jcscar on 2004-10-28
```
root@mashed:/home/jcscar # modprobe usb-storage
root@mashed:/home/jcscar # lsmod
Module                  Size  Used by
jfs                   157632  0
xfs                   500184  0
reiserfs              207600  0
hfs                    41860  0
hfsplus                54532  0
isofs                  33976  0
udf                    79876  0
vfat                   13312  0
fat                    41792  1 vfat
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
3c59x                  36776  0
ohci1394               32004  0
usblp                  12032  0
shpchp                 87276  0
pciehp                 83948  0
pci_hotplug            30640  2 shpchp,pciehp
snd_intel8x0           33068  3
snd_ac97_codec         59268  1 snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
ehci_hcd               27780  0
usb_storage            59200  0
ohci_hcd               19460  0
usbcore               104292  6 usblp,ehci_hcd,usb_storage,ohci_hcd
nvidia_agp              7580  1
agpgart                31784  2 nvidia_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
ntfs                   88660  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
nvidia               4821428  12
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  0
mousedev               10124  1
psmouse                17800  0
sr_mod                 15780  0
cdrom                  35872  2 ide_cd,sr_mod
sd_mod                 20480  0
scsi_mod              115148  4 usb_storage,sbp2,sr_mod,sd_mod
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
ide_disk               16768  3
amd74xx                13340  1
ide_core              125272  5 usb_storage,ide_cd,ide_generic,ide_disk,amd74xx
unix                   25904  697
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb
root@mashed:/home/jcscar #
root@mashed:/home/jcscar #
root@mashed:/home/jcscar # dmesg
el, high) -> IRQ 169
ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 22 (level, high) -> IRQ 177
ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 21 (level, high) -> IRQ 185
ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 20 (level, high) -> IRQ 193
ACPI: PCI Interrupt Link [APCI] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:05.0[A] -> GSI 22 (level, high) -> IRQ 177
ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 21 (level, high) -> IRQ 185
ACPI: PCI Interrupt Link [APCM] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:0d.0[A] -> GSI 20 (level, high) -> IRQ 193
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
ACPI: PCI interrupt 0000:01:0b.0[A] -> GSI 19 (level, high) -> IRQ 201
ACPI: PCI Interrupt Link [AP3C] enabled at IRQ 22
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 22 (level, high) -> IRQ 177
ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 19 (level, high) -> IRQ 201
number of MP IRQ sources: 15.
number of IO-APIC #2 registers: 24.
testing the IO APIC.......................
IO APIC #2......
.... register #00: 02000000
.......    : physical APIC id: 02
.......    : Delivery Type: 0
.......    : LTS          : 0
.... register #01: 00170011
.......     : max redirection entries: 0017
.......     : PRQ implemented: 0
.......     : IO APIC version: 0011
.... register #02: 00000000
.......     : arbitration: 00
.... IRQ redirection table:
 NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:
 00 000 00  1    0    0   0   0    0    0    00
 01 001 01  0    0    0   0   0    1    1    39
 02 000 00  1    0    0   0   0    0    0    00
 03 001 01  0    0    0   0   0    1    1    41
 04 001 01  0    0    0   0   0    1    1    49
 05 001 01  0    0    0   0   0    1    1    51
 06 001 01  0    0    0   0   0    1    1    59
 07 001 01  1    0    0   0   0    1    1    61
 08 001 01  0    0    0   0   0    1    1    69
 09 001 01  0    1    0   0   0    1    1    71
 0a 001 01  0    0    0   0   0    1    1    79
 0b 001 01  0    0    0   0   0    1    1    81
 0c 001 01  0    0    0   0   0    1    1    89
 0d 001 01  0    0    0   0   0    1    1    91
 0e 001 01  0    0    0   0   0    1    1    99
 0f 001 01  0    0    0   0   0    1    1    A1
 10 000 00  1    0    0   0   0    0    0    00
 11 000 00  1    0    0   0   0    0    0    00
 12 000 00  1    0    0   0   0    0    0    00
 13 001 01  1    1    0   0   0    1    1    C9
 14 001 01  1    1    0   0   0    1    1    C1
 15 001 01  1    1    0   0   0    1    1    B9
 16 001 01  1    1    0   0   0    1    1    B1
 17 001 01  1    1    0   0   0    1    1    A9
Using vector-based indexing
IRQ to pin mappings:
IRQ0 -> 0:2
IRQ1 -> 0:1
IRQ3 -> 0:3
IRQ4 -> 0:4
IRQ5 -> 0:5
IRQ6 -> 0:6
IRQ7 -> 0:7
IRQ8 -> 0:8
IRQ9 -> 0:9
IRQ10 -> 0:10
IRQ11 -> 0:11
IRQ12 -> 0:12
IRQ13 -> 0:13
IRQ14 -> 0:14
IRQ15 -> 0:15
IRQ201 -> 0:19
IRQ193 -> 0:20
IRQ185 -> 0:21
IRQ177 -> 0:22
IRQ169 -> 0:23
.................................... done.
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 4
Cannot allocate resource for EISA slot 5
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
ACPI: (supports S0 S3 S4 S5)
ACPI wakeup devices:
HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4116 blocks [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 204k freed
vesafb: probe of vesafb0 failed with error -6
ACPI: Processor [CPU0] (supports C1)
ACPI: Thermal Zone [THRM] (36 C)
ACPI: Fan [FAN] (on)
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
hda: Maxtor 5T040H4, ATA DISK drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: Host Protected Area detected.
        current capacity is 78125000 sectors (40000 MB)
        native  capacity is 80043264 sectors (40982 MB)
hda: 78125000 sectors (40000 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
hdc: DVD-RW IDE1004, ATAPI CD/DVD-ROM drive
hdd: IOMEGA ZIP 250 ATAPI, ATAPI FLOPPY drive
ide1 at 0x170-0x177,0x376 on irq 15
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 499928k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
SCSI subsystem initialized
input: PS2++ Logitech Wheel Mouse on isa0060/serio1
mice: PS/2 mouse device common for all mice
hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
ts: Compaq touchscreen protocol output
ieee1394: Initialized config rom entry `ip1394'
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 19 (level, high) -> IRQ 201
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-6111  Tue Jul 27 07:55:38 PDT 2004
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
NTFS driver 2.1.15 [Flags: R/O MODULE].
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.8.1-3-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected NVIDIA nForce2 chipset
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: AGP aperture is 128M @ 0xe0000000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 22 (level, high) -> IRQ 177
ohci_hcd 0000:00:02.0: nVidia Corporation nForce2 USB Controller
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 177, pci mem f89b2000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 21 (level, high) -> IRQ 185
ohci_hcd 0000:00:02.1: nVidia Corporation nForce2 USB Controller (#2)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ohci_hcd 0000:00:02.1: irq 185, pci mem f89b4000
ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
usb 1-3: new full speed USB device using address 2
usb 2-2: new full speed USB device using address 2
hub 2-2:1.0: USB hub found
hub 2-2:1.0: 4 ports detected
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usb 2-2.2: new full speed USB device using address 3
  Vendor: SPRING    Model: MultiCard Slot A  Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
  Vendor: SPRING    Model: MultiCard Slot D  Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sdb at scsi0, channel 0, id 0, lun 1
  Vendor: SPRING    Model: MultiCard Slot S  Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sdc at scsi0, channel 0, id 0, lun 2
  Vendor: SPRING    Model: MultiCard Slot M  Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sdd at scsi0, channel 0, id 0, lun 3
USB Mass Storage device found at 2
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 20 (level, high) -> IRQ 193
ehci_hcd 0000:00:02.2: nVidia Corporation nForce2 USB Controller
PCI: Setting latency timer of device 0000:00:02.2 to 64
ehci_hcd 0000:00:02.2: irq 193, pci mem f89b9000
ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
PCI: cache line size of 64 is not supported by device 0000:00:02.2
ehci_hcd 0000:00:02.2: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
hub 2-2:1.0: cannot reset port 3 (err = -110)
hub 2-2:1.0: cannot reset port 3 (err = -110)
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 6 ports detected
hub 2-2:1.0: cannot reset port 3 (err = -110)
hub 2-2:1.0: cannot reset port 3 (err = -110)
hub 2-2:1.0: cannot reset port 3 (err = -110)
hub 2-2:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
hub 2-2:1.0: cannot disable port 3 (err = -110)
hub 2-2:1.0: cannot reset port 3 (err = -110)
hub 2-2:1.0: cannot reset port 3 (err = -110)
hub 2-2:1.0: cannot reset port 3 (err = -110)
hub 2-2:1.0: cannot reset port 3 (err = -110)
hub 2-2:1.0: cannot reset port 3 (err = -110)
hub 2-2:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
hub 2-2:1.0: cannot disable port 3 (err = -110)
hub 2-2:1.0: cannot disable port 3 (err = -110)
usb 2-2: USB disconnect, address 2
usb 2-2.2: USB disconnect, address 3
usb 1-3: USB disconnect, address 2
ohci_hcd 0000:00:02.1: wakeup
ohci_hcd 0000:00:02.0: wakeup
ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 21 (level, high) -> IRQ 185
PCI: Setting latency timer of device 0000:00:06.0 to 64
usb 2-2: new full speed USB device using address 6
hub 2-2:1.0: USB hub found
hub 2-2:1.0: 4 ports detected
intel8x0_measure_ac97_clock: measured 123762 usecs
intel8x0: clocking to 48000
usb 1-3: new full speed USB device using address 3
scsi1 : SCSI emulation for USB Mass Storage devices
  Vendor: SPRING    Model: MultiCard Slot A  Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
  Vendor: SPRING    Model: MultiCard Slot D  Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sdb at scsi1, channel 0, id 0, lun 1
  Vendor: SPRING    Model: MultiCard Slot S  Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sdc at scsi1, channel 0, id 0, lun 2
  Vendor: SPRING    Model: MultiCard Slot M  Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sdd at scsi1, channel 0, id 0, lun 3
USB Mass Storage device found at 3
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: PCI Express Hot Plug Controller Driver version: 0.4
usb 2-2.2: new full speed USB device using address 7
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
usb 2-2.3: new full speed USB device using address 8
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 8 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1204
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:00:0d.0[A] -> GSI 20 (level, high) -> IRQ 193
PCI: Setting latency timer of device 0000:00:0d.0 to 64
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[193]  MMIO=[ed084000-ed0847ff]  Max Packet=[2048]
ACPI: PCI interrupt 0000:01:0b.0[A] -> GSI 19 (level, high) -> IRQ 201
3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
0000:01:0b.0: 3Com PCI 3c905 Boomerang 100baseTx at 0x9000. Vers LK1.1.19
eth0: Dropping NETIF_F_SG since no checksum feature.
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 22 (level, high) -> IRQ 177
0000:02:01.0: 3Com PCI 3c920 Tornado at 0xa000. Vers LK1.1.19
ohci1394: fw-host0: SelfID received outside of bus reset sequence
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040ca0701037b0c]
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02cc0c0(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
eth1: no IPv6 routers present
usb 3-6: new high speed USB device using address 4
scsi2 : SCSI emulation for USB Mass Storage devices
  Vendor: Maxtor 6  Model: Y160P0            Rev:  0 0
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sde: 320173056 512-byte hdwr sectors (163929 MB)
sde: assuming drive cache: write through
 /dev/scsi/host2/bus0/target0/lun0: p1
Attached scsi disk sde at scsi2, channel 0, id 0, lun 0
USB Mass Storage device found at 4
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sde1.
udf: registering filesystem
UDF-fs: No partition found (1)
Unable to identify CD-ROM format.
HFS+-fs: unable to find HFS+ superblock
VFS: Can't find a HFS filesystem on dev sde1.
VFS: Can't find ext3 filesystem on dev sde1.
VFS: Can't find ext2 filesystem on dev sde1.
ReiserFS: sde1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sde1
SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
SGI XFS Quota Management subsystem
XFS: bad magic number
XFS: SB validate failed
root@mashed:/home/jcscar #
```

* Edited by a mod: [/b] Put long snips in code blocks, please.*

---

### Post by FLeiXiuS on 2004-10-30
Have you tried a standard mount command just to see if it would work this way?

mount -t vfat /dev/sda /path/to/mount

Perhaps this will do it for you.

---

### Post by nightmaresc on 2004-10-30
I am actually having the same exact problem.  I've tried the things you have all mentioned.  I'll post my results here too:

```
root@ubuntu:/home/david # modprobe usb-storage
root@ubuntu:/home/david # lsmod
Module                  Size  Used by
vfat                   13312  0
fat                    41792  1 vfat
radeon                115236  2
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
8139too                23936  0
8139cp                 19072  0
mii                     4864  2 8139too,8139cp
crc32                   4608  2 8139too,8139cp
ohci1394               32004  0
snd_intel8x0           33068  3
snd_ac97_codec         59268  1 snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
ata_piix                7940  0
libata                 36356  1 ata_piix
ehci_hcd               27780  0
usb_storage            59200  0
uhci_hcd               29328  0
usbcore               104292  5 ehci_hcd,usb_storage,uhci_hcd
shpchp                 87276  0
pciehp                 83948  0
pci_hotplug            30640  2 shpchp,pciehp
intel_agp              20512  0
intel_mch_agp          10000  1
agpgart                31784  3 intel_agp,intel_mch_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  0
mousedev               10124  1
psmouse                17800  0
sr_mod                 15780  0
cdrom                  35872  2 ide_cd,sr_mod
sd_mod                 20480  0
scsi_mod              115148  5 libata,usb_storage,sbp2,sr_mod,sd_mod
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   25904  690
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

```

> mount -t vfat /dev/sda /path/to/mount
I tried that too but got this:

Mount: no medium found.


Thanks for any help.

Edit:  Forgot to mention that the Live CD version automounted it and detected it perfectly.

---

### Post by nightmaresc on 2004-10-31
Here's the part that probably matters in dmesg:

```

usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 169, io base 0000e000
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 177
uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 177, io base 0000e400
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 185, io base 0000e800
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 169
uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 169, io base 0000ec00
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 2-1: new low speed USB device using address 2
usb 4-1: new full speed USB device using address 2
usbcore: registered new driver hiddev
Initializing USB Mass Storage driver...
hiddev96: USB HID v1.10 Device [APC Back-UPS ES 500 FW:801.e5.D USB FW:e5] on usb-0000:00:1d.1-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
scsi0 : SCSI emulation for USB Mass Storage devices
  Vendor: Generic   Model: USB SD Reader     Rev: 1.00
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
  Vendor: Generic   Model: USB CF Reader     Rev: 1.01
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sdb at scsi0, channel 0, id 0, lun 1
  Vendor: Generic   Model: USB SM Reader     Rev: 1.02
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sdc at scsi0, channel 0, id 0, lun 2
  Vendor: Generic   Model: USB MS Reader     Rev: 1.03
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sdd at scsi0, channel 0, id 0, lun 3
USB Mass Storage device found at 2
usbcore: registered new driver usb-storage
USB Mass Storage support registered.

```

I am also receiving the "nobiospnp" error at boot and in dmesg, if that has anything to do with it.

Any suggestions?

---

### Post by jdong on 2004-10-31
[QUOTE=FLeiXiuS]Have you tried a standard mount command just to see if it would work this way?

mount -t vfat /dev/sda /path/to/mount

Perhaps this will do it for you.[/QUOTE]

No, you have to use ** /dev/sda1**, not /dev/sda. sda is the entire drive, and you're not gonna get that mounted!

---

### Post by nightmaresc on 2004-10-31
root@ubuntu:/home/david # mount -t vfat /dev/sda1 /mnt/external
mount: special device /dev/sda1 does not exist

Didn't work :(

---

### Post by jcscar on 2004-10-31
root@mashed:/home/jcscar # mount -t ntfs /dev/sda1 /mnt/storage

resulted in an Error Displaying Folder "You do not have the permissions necessary to view the contents of "storage".

---

### Post by FLeiXiuS on 2004-10-31
[QUOTE=jdong]No, you have to use ** /dev/sda1**, not /dev/sda. sda is the entire drive, and you're not gonna get that mounted![/QUOTE]


I meant /dev/sda1 (sorry)

---

### Post by 6bit on 2004-10-31
this is what i get my 120g usb harde won't work.

dmesg

usb 3-4: USB disconnect, address 9
usb 3-4: new high speed USB device using address 10
scsi4 : SCSI emulation for USB Mass Storage devices
  Vendor: USB 2.0   Model: Storage Device    Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sdc: 234441648 512-byte hdwr sectors (120034 MB)
sdc: assuming drive cache: write through
 /dev/scsi/host4/bus0/target0/lun0: p1
Attached scsi disk sdc at scsi4, channel 0, id 0, lun 0
USB Mass Storage device found at 10
usb 3-2: string descriptor 0 read error: -32
usb 3-2: string descriptor 0 read error: -32
usb 3-2: string descriptor 0 read error: -32
usb 3-2: string descriptor 0 read error: -32
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sdc1.
UDF-fs: No partition found (1)
Unable to identify CD-ROM format.
HFS+-fs: unable to find HFS+ superblock
VFS: Can't find a HFS filesystem on dev sdc1.
VFS: Can't find ext3 filesystem on dev sdc1.
VFS: Can't find ext2 filesystem on dev sdc1.
ReiserFS: sdc1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdc1
XFS: bad magic number
XFS: SB validate failed

---

### Post by FLeiXiuS on 2004-10-31
You may beable to try to REFORMAT your thumb drive.  
```

mkfs.vfat /dev/sda1

```

I guarentee thats what the problem is.  I'ts not recognizing the data format.  I had this same problem when I bought mine yesterday.  After formatting it, then mounting it with the correct fs, it worked perfectly.  Just my 2 cents it may be otherwise for you.

---

### Post by jdong on 2004-10-31
In case there's people reading this who lack common sense, **the mkfs command reformats. ALL DATA WILL BE LOST ON SPECIFIED PARTITION**.

OMG I can't tell you how many times I was trying to format a floppy and mindlessly fed /dev/hda1 instead of /dev/fd0 into the command...  ](*,)  ](*,)

---

### Post by FLeiXiuS on 2004-11-01
[QUOTE=jdong]In case there's people reading this who lack common sense, **the mkfs command reformats. ALL DATA WILL BE LOST ON SPECIFIED PARTITION**.

OMG I can't tell you how many times I was trying to format a floppy and mindlessly fed /dev/hda1 instead of /dev/fd0 into the command...  ](*,)  ](*,)[/QUOTE]


You wouldn't believe how many times I would be in /home/ and think im in /home/fleixius/

then I would cd rm -Rf ../

and then well what do you know...  ../ would be the / directory.  

There you have it laddies and gents, even the moderators make the most common mistakes. :roll:

---

### Post by 6bit on 2004-11-01
[QUOTE=FLeiXiuS]You may beable to try to REFORMAT your thumb drive.  
```

mkfs.vfat /dev/sda1

```

I guarentee thats what the problem is.  I'ts not recognizing the data format.  I had this same problem when I bought mine yesterday.  After formatting it, then mounting it with the correct fs, it worked perfectly.  Just my 2 cents it may be otherwise for you.[/QUOTE]

my external drive is now formatted as an NTFS but that means I can't write to it and I want to be able to writ to it so i want to format it as an FAT32 

if I try this i get the message:
Attempting to create a too large file system

---

### Post by FLeiXiuS on 2004-11-01
[QUOTE=6bit]my external drive is now formatted as an NTFS but that means I can't write to it and I want to be able to writ to it so i want to format it as an FAT32 

if I try this i get the message:
Attempting to create a too large file system[/QUOTE]

You have to tell the fs to be 32 bit as opposed to the default 16/8 bit.

To do so,
```

mkfs.vfat -F 32 /dev/device/here

```

---

