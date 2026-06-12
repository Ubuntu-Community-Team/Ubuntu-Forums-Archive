---
title: "Bad noise with bt878 but good picture"
date: 2014-05-13
forum: General Help
---

### Post by elliotn on 2014-05-13
I have a hauppage bt878 win TV card that worked well with 13.10 but now with 14.04 I get a very uncomfortsble noise even if I put the speaker jack in the tv card output I still get the same noise, picture is very good and clear with TVTime. I need help
here is my lspci | grep bt878
```
elliotn@elliotn-G31-M7-TE:~$ lspci | grep Bt878
04:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
elliotn@elliotn-G31-M7-TE:~$ 

```

and here is my dmesg
```
pci 0000:01:00.1: [1002:aa10] type 00 class 0x040300
pci 0000:01:00.1: reg 0x10: [mem 0xfeaec000-0xfeaeffff 64bit]
pci 0000:01:00.1: supports D1 D2
pci 0000:00:01.0: PCI bridge to [bus 01]
pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
pci 0000:00:1c.0: PCI bridge to [bus 02]
pci 0000:03:00.0: [10ec:8136] type 00 class 0x020000
pci 0000:03:00.0: reg 0x10: [io  0xe800-0xe8ff]
pci 0000:03:00.0: reg 0x18: [mem 0xfdeff000-0xfdefffff 64bit pref]
pci 0000:03:00.0: reg 0x20: [mem 0xfdee0000-0xfdeeffff 64bit pref]
pci 0000:03:00.0: reg 0x30: [mem 0xfebe0000-0xfebfffff pref]
pci 0000:03:00.0: supports D1 D2
pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:1c.1: PCI bridge to [bus 03]
pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
pci 0000:00:1c.1:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
pci 0000:04:02.0: [109e:036e] type 00 class 0x040000
pci 0000:04:02.0: reg 0x10: [mem 0xfdfff000-0xfdffffff pref]
pci 0000:04:02.1: [109e:0878] type 00 class 0x048000
pci 0000:04:02.1: reg 0x10: [mem 0xfdffe000-0xfdffefff pref]
pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
pci 0000:00:1e.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
ACPI: Enabled 3 GPEs in block 00 to 1F
vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
vgaarb: loaded
vgaarb: bridge control possible 0000:01:00.0
ACPI: bus type USB registered
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Using ACPI for IRQ routing
PCI: pci_cache_line_size set to 64 bytes
e820: reserve RAM buffer [mem 0x0009f400-0x0009ffff]
e820: reserve RAM buffer [mem 0xbffb0000-0xbfffffff]
NetLabel: Initializing
NetLabel:  domain hash size = 128
NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
hpet clockevent registered
HPET: 3 timers in total, 0 timers will be used for per-cpu timer
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Switched to clocksource hpet
pnp: PnP ACPI init
ACPI: bus type PNP registered
system 00:00: [mem 0xfed14000-0xfed19fff] has been reserved
system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
pnp 00:01: [dma 4]
pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
pnp 00:05: [dma 0 disabled]
pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
pnp 00:06: [dma 2]
pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
pnp 00:08: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
system 00:09: [io  0x0a00-0x0a0f] has been reserved
system 00:09: [io  0x0a10-0x0a1f] has been reserved
system 00:09: [io  0x0a20-0x0a2f] has been reserved
system 00:09: [io  0x0a30-0x0a3f] has been reserved
system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
system 00:0a: [io  0x04d0-0x04d1] has been reserved
system 00:0a: [io  0x0800-0x087f] could not be reserved
system 00:0a: [io  0x0480-0x04bf] has been reserved
system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
system 00:0a: [mem 0xfed20000-0xfed8ffff] has been reserved
system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:0b: Plug and Play ACPI device, IDs PNP0103 (active)
pnp 00:0c: Plug and Play ACPI device, IDs INT0800 (active)
system 00:0d: [mem 0xffc00000-0xfff7ffff] has been reserved
system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
system 00:0e: [mem 0xfec00000-0xfec00fff] could not be reserved
system 00:0e: [mem 0xfee00000-0xfee00fff] has been reserved
system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
system 00:0f: [mem 0xe0000000-0xefffffff] has been reserved
system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
system 00:10: [mem 0x00000000-0x0009ffff] could not be reserved
system 00:10: [mem 0x000c0000-0x000cffff] could not be reserved
system 00:10: [mem 0x000e0000-0x000fffff] could not be reserved
system 00:10: [mem 0x00100000-0xbfffffff] could not be reserved
system 00:10: Plug and Play ACPI device, IDs PNP0c01 (active)
pnp: PnP ACPI: found 17 devices
ACPI: bus type PNP unregistered
pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
pci 0000:00:1f.0: BAR 13: [io  0x0800-0x087f] has bogus alignment
pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
pci 0000:00:01.0: PCI bridge to [bus 01]
pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
pci 0000:00:1c.0: PCI bridge to [bus 02]
pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff]
pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
pci 0000:00:1c.1: PCI bridge to [bus 03]
pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
pci 0000:00:1c.1:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
pci 0000:00:1e.0: PCI bridge to [bus 04]
pci 0000:00:1e.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
pci_bus 0000:00: resource 9 [mem 0xf0000000-0xffffffff]
pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
pci_bus 0000:02: resource 1 [mem 0xc0000000-0xc01fffff]
pci_bus 0000:02: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
pci_bus 0000:03: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
pci_bus 0000:04: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
pci_bus 0000:04: resource 8 [mem 0xc0000000-0xdfffffff]
pci_bus 0000:04: resource 9 [mem 0xf0000000-0xffffffff]
NET: Registered protocol family 2
TCP established hash table entries: 32768 (order: 6, 262144 bytes)
TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
TCP: Hash tables configured (established 32768 bind 32768)
TCP: reno registered
UDP hash table entries: 2048 (order: 4, 65536 bytes)
UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
NET: Registered protocol family 1
pci 0000:01:00.0: Boot video device
PCI: CLS 32 bytes, default 64
Unpacking initramfs...
Freeing initrd memory: 17692K (ffff880035d62000 - ffff880036ea9000)
microcode: CPU0 sig=0x6f6, pf=0x1, revision=0xcb
microcode: CPU1 sig=0x6f6, pf=0x1, revision=0xcb
microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
futex hash table entries: 1024 (order: 4, 65536 bytes)
audit: initializing netlink subsys (disabled)
audit: type=2000 audit(1399965645.443:1): initialized
bounce pool size: 64 pages
HugeTLB registered 2 MB page size, pre-allocated 0 pages
zbud: loaded
VFS: Disk quotas dquot_6.5.2
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
msgmni has been set to 6025
tsc: Refined TSC clocksource calibration: 2389.240 MHz
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered
io scheduler bfq registered (default)
BFQ I/O-scheduler version: v7r3
pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
pcieport 0000:00:1c.0: enabling device (0104 -> 0107)
pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Switched to clocksource tsc
Linux agpgart interface v0.103
simple-framebuffer simple-framebuffer.0: framebuffer at 0xd0000000, 0x300000 bytes, mapped to 0xffffc90010780000
simple-framebuffer simple-framebuffer.0: format=x8r8g8b8, mode=1024x768x32, linelength=4096
Console: switching to colour frame buffer device 128x48
simple-framebuffer simple-framebuffer.0: fb0: simplefb registered!
intel_idle: does not run on family 6 model 15
GHES: HEST is not enabled!
xenfs: not registering filesystem on non-xen platform
libphy: Fixed MDIO Bus: probed
i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mousedev: PS/2 mouse device common for all mice
ledtrig-cpu: registered to indicate activity on CPUs
hidraw: raw HID events driver (C) Jiri Kosina
TCP: vegas registered
TCP: yeah registered
Key type dns_resolver registered
registered taskstats version 1
regulator-dummy: disabling
Freeing unused kernel memory: 1004K (ffffffff81818000 - ffffffff81913000)
CFS CPU scheduler.
systemd-udevd[80]: starting version 204
input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
uhci_hcd: USB Universal Host Controller Interface driver
uhci_hcd 0000:00:1d.0: UHCI Host Controller
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000cc00
usb usb1: New USB device found, idVendor=1d6b, idProduct=0001
usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb1: Product: UHCI Host Controller
usb usb1: Manufacturer: Linux 3.14-3.dmz.1-liquorix-amd64 uhci_hcd
usb usb1: SerialNumber: 0000:00:1d.0
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
uhci_hcd 0000:00:1d.1: UHCI Host Controller
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c880
usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb2: Product: UHCI Host Controller
usb usb2: Manufacturer: Linux 3.14-3.dmz.1-liquorix-amd64 uhci_hcd
usb usb2: SerialNumber: 0000:00:1d.1
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
uhci_hcd 0000:00:1d.2: UHCI Host Controller
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c800
usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb3: Product: UHCI Host Controller
usb usb3: Manufacturer: Linux 3.14-3.dmz.1-liquorix-amd64 uhci_hcd
usb usb3: SerialNumber: 0000:00:1d.2
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
uhci_hcd 0000:00:1d.3: UHCI Host Controller
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c480
usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb4: Product: UHCI Host Controller
usb usb4: Manufacturer: Linux 3.14-3.dmz.1-liquorix-amd64 uhci_hcd
usb usb4: SerialNumber: 0000:00:1d.3
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
r8169 0000:03:00.0: irq 43 for MSI/MSI-X
r8169 0000:03:00.0 eth0: RTL8102e at 0xffffc90010744000, 00:30:67:6e:6c:d9, XID 04a00000 IRQ 43
Floppy drive(s): fd0 is 1.44M
SCSI subsystem initialized
thermal LNXTHERM:00: registered as thermal_zone0
ACPI: Thermal Zone [THRM] (37 C)
libata version 3.00 loaded.
ata_piix 0000:00:1f.1: version 2.13
scsi0 : ata_piix
scsi1 : ata_piix
ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
scsi2 : ata_piix
scsi3 : ata_piix
ata3: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xb880 irq 19
ata4: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb888 irq 19
FDC 0 is a post-1991 82077
ata4.01: NODEV after polling detection
ata4.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB02, max UDMA/100
ata4.00: configured for UDMA/100
ata3.00: ATA-7: SAMSUNG HD502HI, 1AG01118, max UDMA7
ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata3.00: configured for UDMA/133
ata1.01: HPA detected: current 78163247, native 78165360
ata1.01: ATA-6: ST340014A, 8.54, max UDMA/100
ata1.01: 78163247 sectors, multi 16: LBA48 
ata1.01: limited to UDMA/33 due to 40-wire cable
ata1.01: configured for UDMA/33
scsi 0:0:1:0: Direct-Access     ATA      ST340014A        8.54 PQ: 0 ANSI: 5
scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD502HI  1AG0 PQ: 0 ANSI: 5
sd 0:0:1:0: [sda] 78163247 512-byte logical blocks: (40.0 GB/37.2 GiB)
sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
sd 0:0:1:0: [sda] Write Protect is off
sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
sd 2:0:0:0: [sdb] Write Protect is off
sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB02 PQ: 0 ANSI: 5
 sda: sda1
sd 0:0:1:0: [sda] Attached SCSI disk
 sdb: sdb1 < sdb5 > sdb2 sdb3 sdb4
sd 2:0:0:0: [sdb] Attached SCSI disk
sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
cdrom: Uniform CD-ROM driver Revision: 3.20
sr 3:0:0:0: Attached scsi CD-ROM sr0
random: nonblocking pool is initialized
EXT4-fs (sdb4): mounted filesystem with ordered data mode. Opts: (null)
init: plymouth-upstart-bridge main process (146) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (154) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (156) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (157) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (158) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (159) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (161) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (162) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (166) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (167) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (169) terminated with status 1
init: plymouth-upstart-bridge respawning too fast, stopped
Adding 4299772k swap on /dev/sdb5.  Priority:-1 extents:1 across:4299772k FS
EXT4-fs (sdb4): re-mounted. Opts: errors=remount-ro
systemd-udevd[281]: starting version 204
intel_rng: FWH not detected
IT8712 SuperIO detected.
input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
ACPI: Power Button [PWRB]
input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
ACPI: Power Button [PWRF]
rtc_cmos 00:02: RTC can wake from S4
rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
lp: driver loaded but no devices found
bt87x0: Using board 1, analog, digital (rate 32000 Hz)
snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
snd_hda_intel 0000:01:00.1: irq 45 for MSI/MSI-X
input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input4
ppdev: user-space parallel port driver
input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
leds_ss4200: no LED devices found
gpio_ich: GPIO from 206 to 255 on gpio_ich
[drm] Initialized drm 1.1.0 20060810
media: Linux media interface: v0.10
[drm] radeon kernel modesetting enabled.
checking generic (d0000000 300000) vs hw (d0000000 10000000)
fb: conflicting fb hw usage radeondrmfb vs simple - removing generic driver
Console: switching to colour dummy device 80x25
[drm] initializing kernel modesetting (RV610 0x1002:0x94C3 0x174B:0xE400).
[drm] register mmio base: 0xFEAF0000
[drm] register mmio size: 65536
ATOM BIOS: 11x
radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
[drm] Detected VRAM RAM=256M, BAR=256M
[drm] RAM width 64bits DDR
[TTM] Zone  kernel: Available graphics memory: 1542986 kiB
[TTM] Initializing pool allocator
[TTM] Initializing DMA pool allocator
[drm] radeon: 256M of VRAM memory ready
[drm] radeon: 512M of GTT memory ready.
[drm] Loading RV610 Microcode
Linux video capture interface: v2.00
psmouse serio1: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
bttv: driver version 0.9.19 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0)
bttv: 0: Bt878 (rev 17) at 0000:04:02.0, irq: 17, latency: 64, mmio: 0xfdfff000
bttv: 0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
bttv: 0: using: Hauppauge (bt878) [card=10,autodetected]
bttv: 0: Hauppauge/Voodoo msp34xx: reset line init [5]
tveeprom 0-0050: The eeprom says no radio is present, but the tuner type
tveeprom 0-0050: indicates otherwise. I will assume that radio is present.
tveeprom 0-0050: Hauppauge model 44809, rev E1A5, serial# 9787177
tveeprom 0-0050: tuner model is TCL MPE05-2 (idx 105, type 38)
tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
tveeprom 0-0050: audio processor is None (idx 0)
tveeprom 0-0050: decoder processor is BT878 (idx 14)
tveeprom 0-0050: has radio
bttv: 0: Hauppauge eeprom indicates model#44809
bttv: 0: tuner type=38
[drm] Internal thermal controller with fan control
[drm] radeon: power management initialized
[drm] GART: num cpu pages 131072, num gpu pages 131072
[drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
radeon 0000:01:00.0: WB enabled
radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000010000c00 and cpu addr 0xffff8800ac9a0c00
[drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[drm] Driver supports precise vblank timestamp query.
radeon 0000:01:00.0: irq 46 for MSI/MSI-X
radeon 0000:01:00.0: radeon: using MSI.
[drm] radeon: irq initialized.
[drm] ring test on 0 succeeded in 1 usecs
[drm] ib test on ring 0 succeeded in 0 usecs
[drm] Radeon Display Connectors
[drm] Connector 0:
[drm]   VGA-1
[drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[drm]   Encoders:
[drm]     CRT1: INTERNAL_KLDSCP_DAC1
[drm] Connector 1:
[drm]   DIN-1
[drm]   Encoders:
[drm]     TV1: INTERNAL_KLDSCP_DAC2
[drm] Connector 2:
[drm]   DVI-I-1
[drm]   HPD1
[drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[drm]   Encoders:
[drm]     CRT2: INTERNAL_KLDSCP_DAC2
[drm]     DFP1: INTERNAL_LVTM1
coretemp coretemp.0: Using relative temperature scale!
coretemp coretemp.0: Using relative temperature scale!
bttv: 0: audio absent, no audio device found!
[drm] fb mappable at 0xD0141000
[drm] vram apper at 0xD0000000
[drm] size 3145728
[drm] fb depth is 24
[drm]    pitch is 4096
fbcon: radeondrmfb (fb0) is primary device
tda9887 0-0043: creating new instance
tda9887 0-0043: tda988[5/6/7] found
tuner 0-0043: Tuner 74 found with type(s) Radio TV.
tuner 0-0061: Tuner -1 found with type(s) Radio TV.
tuner-simple 0-0061: creating new instance
tuner-simple 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
bttv: 0: Setting PLL: 28636363 => 35468950 (needs up to 100ms)
Console: switching to colour frame buffer device 128x48
radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
radeon 0000:01:00.0: registered panic notifier
[drm] Initialized radeon 2.37.0 20080528 for 0000:01:00.0 on minor 0
bttv: PLL set ok
bttv: 0: registered device video0
bttv: 0: registered device vbi0
bttv: 0: registered device radio0
init: failsafe main process (614) killed by TERM signal
fuse init (API version 7.22)
psmouse serio1: Failed to enable mouse on isa0060/serio1
input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
NET: Registered protocol family 10
Bluetooth: Core ver 2.18
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP socket layer initialized
Bluetooth: SCO socket layer initialized
init: avahi-cups-reload main process (703) terminated with status 1
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM ver 1.11
Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Bluetooth: BNEP filters: protocol multicast
Bluetooth: BNEP socket layer initialized
r8169 0000:03:00.0 eth0: link down
IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
usb 3-2: new full-speed USB device number 2 using uhci_hcd
usb 3-2: New USB device found, idVendor=04e8, idProduct=685b
usb 3-2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
usb 3-2: Product: Android
usb 3-2: Manufacturer: Android
usb 3-2: SerialNumber: 0019624a54639e
usb-storage 3-2:1.0: USB Mass Storage device detected
scsi4 : usb-storage 3-2:1.0
usbcore: registered new interface driver usb-storage
scsi 4:0:0:0: Direct-Access     Samsung  File-CD Gadget   0000 PQ: 0 ANSI: 2
scsi 4:0:0:1: Direct-Access     Samsung  File-CD Gadget   0000 PQ: 0 ANSI: 2
sd 4:0:0:0: [sdc] Attached SCSI removable disk
sd 4:0:0:1: [sdd] Attached SCSI removable disk
usb 3-2: USB disconnect, device number 2
usb 3-2: new full-speed USB device number 3 using uhci_hcd
usb 3-2: New USB device found, idVendor=04e8, idProduct=6863
usb 3-2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
usb 3-2: Product: Android
usb 3-2: Manufacturer: Android
usb 3-2: SerialNumber: 0019624a54639e
usbcore: registered new interface driver cdc_ether
rndis_host 3-2:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.2-2, RNDIS device, 6a:82:37:2b:13:7f
usbcore: registered new interface driver rndis_host
NET: Registered protocol family 17
elliotn@elliotn-G31-M7-TE:~$ 

```

---

### Post by elliotn on 2014-05-13
Bump anyone

---

