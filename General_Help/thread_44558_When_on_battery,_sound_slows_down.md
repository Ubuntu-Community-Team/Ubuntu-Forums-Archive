---
title: "When on battery, sound slows down"
date: 2005-06-26
forum: General Help
---

### Post by SQFreak on 2005-06-26
I'm running Ubuntu Hoary on my Dell Latitude D505, which has an Intel Pentium M processor. Its sound chip is an Intel 82801, which takes module snd_intel8x0.

Whenever the computer is plugged in, the sound works great, but when I unplug it and run the computer on battery, the sound slows down. I don't really know where to look. It's program independent - this happens in XMMS, VLC, MPlayer, Xine, RhythmBox, etc. It's format independent - it happens with MP3, OGG, DivX, MPEG1, MPEG2, etc. I haven't found a place to adjust the processor scaling directly.

Any suggestions?

Output of sudo lspci -v:
```
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: [40] #09 [8105]

0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, fast devsel, latency 0

0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, fast devsel, latency 0

0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at faf80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at c000 [size=8]
        Capabilities: [d0] Power Management version 1

0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, fast devsel, latency 0
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at faf00000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 1

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf80 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf40 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf20 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at faeffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [2080]

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fc000000-fdffffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at d800 [size=256]
        I/O ports at dc40 [size=64]
        Memory at faeff800 (32-bit, non-prefetchable) [size=512]
        Memory at faeff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: Conexant: Unknown device 5422
        Flags: medium devsel, IRQ 5
        I/O ports at d400 [size=256]
        I/O ports at d080 [size=128]
        Capabilities: [50] Power Management version 2

0000:01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 20001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (prog-if 10 [OHCI])
        Subsystem: Dell: Unknown device 0163
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at fcfff800 (32-bit, non-prefetchable) [size=2K]
        Memory at fcff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

0000:01:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Dell: Unknown device 0003
        Flags: bus master, fast devsel, latency 32, IRQ 11
        Memory at fcffc000 (32-bit, non-prefetchable) [size=8K]

0000:01:08.0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 81)
        Subsystem: Dell: Unknown device 2002
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at fcffe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ecc0 [size=64]
        Capabilities: [dc] Power Management version 2


```

Output of lsmod:
```
Module                  Size  Used by
pcmcia                 26576  2
i915                   20864  1
video                  16516  0
e100                   37312  0
ohci1394               36100  0
yenta_socket           23816  1
rsrc_nonstatic         11520  1 yenta_socket
pcmcia_core            52384  3 pcmcia,yenta_socket,rsrc_nonstatic
ub                     19740  0
snd_intel8x0           34496  3
snd_ac97_codec         79352  1 snd_intel8x0
piix                   11140  0 [permanent]
ehci_hcd               33800  0
uhci_hcd               34128  0
joydev                 10240  0
sr_mod                 17828  0
sbp2                   25096  0

```

Output of dmesg:
```
Linux version 2.6.11.12 (root@migordon) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #3 SMP Sat Jun 18 17:03:21 EDT 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
 BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001feaa000 (usable)
 BIOS-e820: 000000001feaa000 - 0000000020000000 (reserved)
 BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
 BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
 BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
510MB LOWMEM available.
On node 0 totalpages: 130730
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 126634 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf00
ACPI: RSDT (v001 DELL    CPi R   0x27d40903 ASL  0x00000061) @ 0x1fef0000
ACPI: FADT (v001 DELL    CPi R   0x27d40903 ASL  0x00000061) @ 0x1fef0400
ACPI: BOOT (v001 DELL    CPi R   0x27d40903 ASL  0x00000061) @ 0x1fef07c0
ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
Allocating PCI resources starting at 20000000 (gap: 20000000:dec10000)
Built 1 zonelists
Kernel command line: root=/dev/hda7 resume2=swap:/dev/hda6 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01440000)
Initializing CPU#0
CPU 0 irqstacks, hard=c0575000 soft=c056d000
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1493.931 MHz processor.
Using tsc for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 512788k/522920k available (3103k kernel code, 9596k reserved, 1157k data, 244k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 2957.31 BogoMIPS (lpj=1478656)
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
CPU: After vendor identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 1024K
CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: setting ELCR to 0200 (from 0800)
CPU0: Intel(R) Pentium(R) M processor 1500MHz stepping 05
per-CPU timeslice cutoff: 2925.69 usecs.
task migration cache decay timeout: 3 msecs.
SMP motherboard not detected.
Local APIC not detected. Using dummy APIC emulation.
Brought up 1 CPUs
CPU0 attaching sched-domain:
 domain 0: span 01
  groups: 01
  domain 1: span 01
   groups: 01
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 14 devices
SCSI subsystem initialized
usbcore: registered new driver usbfs
usbcore: registered new driver hub
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:01: ioport range 0x800-0x805 could not be reserved
pnp: 00:01: ioport range 0x808-0x80f could not be reserved
pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
pnp: 00:02: ioport range 0x806-0x807 has been reserved
pnp: 00:02: ioport range 0x810-0x85f could not be reserved
pnp: 00:02: ioport range 0x860-0x87f has been reserved
pnp: 00:02: ioport range 0x880-0x8bf has been reserved
pnp: 00:02: ioport range 0x8c0-0x8df has been reserved
pnp: 00:07: ioport range 0x900-0x97f has been reserved
pnp: 00:0c: ioport range 0x7b0-0x7bb has been reserved
pnp: 00:0c: ioport range 0x7c0-0x7df has been reserved
pnp: 00:0c: ioport range 0xbb0-0xbbb has been reserved
pnp: 00:0c: ioport range 0xbc0-0xbdf has been reserved
pnp: 00:0c: ioport range 0xfb0-0xfbb has been reserved
pnp: 00:0c: ioport range 0xfc0-0xfdf has been reserved
pnp: 00:0c: ioport range 0x13b0-0x13bb has been reserved
pnp: 00:0c: ioport range 0x13c0-0x13df has been reserved
Simple Boot Flag at 0x79 set to 0x1
Machine check exception polling timer started.
audit: initializing netlink socket (disabled)
audit(1119807805.588:0): initialized
Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
NTFS driver 2.1.22 [Flags: R/O].
Initializing Cryptographic API
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Battery Slot [BAT1] (battery absent)
ACPI: Lid Switch [LID]
ACPI: Power Button (CM) [PBTN]
ACPI: Sleep Button (CM) [SBTN]
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THM] (41 C)
lp: driver loaded but no devices found
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 855 Chipset.
agpgart: Maximum main memory to use for agp memory: 438M
agpgart: Detected 892K stolen memory.
agpgart: AGP aperture is 128M @ 0xf0000000
[drm] Initialized drm 1.0.0 20040925
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 8 ports, IRQ sharing disabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 5 (level, low) -> IRQ 5
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
floppy0: no floppy controllers found
RAMDISK driver initialized: 16 RAM disks of 4096K size 1024 blocksize
loop: loaded (max 8 devices)
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Probing IDE interface ide0...
hda: FUJITSU MHT2060AT PL, ATA DISK drive
Probing IDE interface ide1...
hdc: HL-DT-STCD-RW/DVD-ROM GCC-4243N, ATAPI CD/DVD-ROM drive
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 128KiB
hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=65535/16/63
hda: cache flushes supported
 hda: hda1 hda2 hda3 hda4 < hda5 hda6 hda7 >
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
ide-floppy driver 0.99.newide
libata version 1.10 loaded.
ieee1394: raw1394: /dev/raw1394 device initialized
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
mice: PS/2 mouse device common for all mice
input: AT Translated Set 2 keyboard on isa0060/serio0
ALPS Touchpad (Glidepoint) detected
  Disabling hardware tapping
input: AlpsPS/2 ALPS TouchPad on isa0060/serio1
md: linear personality registered as nr 1
md: raid0 personality registered as nr 2
md: raid1 personality registered as nr 3
md: raid5 personality registered as nr 4
raid5: automatically using best checksumming function: pIII_sse
   pIII_sse  :  3868.000 MB/sec
raid5: using function: pIII_sse (3868.000 MB/sec)
md: multipath personality registered as nr 7
md: faulty personality registered as nr 10
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Advanced Linux Sound Architecture Driver Version 1.0.8 (Thu Jan 13 09:39:32 2005 UTC).
ALSA device list:
  No soundcards found.
oprofile: using timer interrupt.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 32Kbytes
TCP established hash table entries: 16384 (order: 6, 262144 bytes)
TCP bind hash table entries: 16384 (order: 5, 196608 bytes)
TCP: Hash tables configured (established 16384 bind 16384)
ip_conntrack version 2.1 (4085 buckets, 32680 max) - 220 bytes per conntrack
ip_tables: (C) 2000-2002 Netfilter core team
ipt_recent v0.3.1: Stephen Frost <sfrost@snowman.net>.  http://snowman.net/projects/ipt_recent/
arp_tables: (C) 2002 David S. Miller
NET: Registered protocol family 1
NET: Registered protocol family 17
Software Suspend Core.
Software Suspend LZF Compression Driver loading.
Software Suspend Swap Writer loading.
ACPI wakeup devices:
 LID PBTN PCI0 USB0  CH1 USB1 USB2 USB3 MODM PCIE
ACPI: (supports S0 S1 S3 S4 S4bios S5)
md: Autodetecting RAID arrays.
md: autorun ...
md: ... autorun DONE.
Software Suspend 2.1.9: Swapwriter: Signature found.
Software Suspend 2.1.9: Suspending enabled.
EXT3-fs: mounted filesystem with ordered data mode.
VFS: Mounted root (ext3 filesystem) readonly.
Freeing unused kernel memory: 244k freed
kjournald starting.  Commit interval 5 seconds
Adding 1542200k swap on /dev/hda6.  Priority:-1 extents:1
EXT3 FS on hda7, internal journal
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
NTFS volume version 3.1.
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 11, io base 0xbf80
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 11, io base 0xbf40
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 11, io base 0xbf20
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
Losing too many ticks!
TSC cannot be used as a timesource.
Possible reasons for this are:
  You're running with Speedstep,
  You don't have DMA enabled for your hard disk (see hdparm),
  Incorrect TSC synchronization on an SMP system (see dmesg).
Falling back to a sane timesource now.
usb 3-2: new full speed USB device using uhci_hcd and address 2
hub 3-2:1.0: USB hub found
hub 3-2:1.0: 4 ports detected
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 11 (level, low) -> IRQ 11
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 11, pci mem 0xfaeffc00
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
hub 3-2:1.0: hub_port_status failed (err = -71)
hub 3-2:1.0: connect-debounce failed, port 1 disabled
hub 3-2:1.0: cannot disable port 1 (err = -71)
hub 3-2:1.0: hub_port_status failed (err = -71)
hub 3-2:1.0: hub_port_status failed (err = -71)
hub 3-2:1.0: hub_port_status failed (err = -71)
hub 3-2:1.0: hub_port_status failed (err = -71)
hub 3-2:1.0: hub_port_status failed (err = -71)
hub 3-2:1.0: hub_port_status failed (err = -71)
usb 4-6: new high speed USB device using ehci_hcd and address 2
hub 4-6:1.0: USB hub found
hub 4-6:1.0: 4 ports detected
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 11 (level, low) -> IRQ 11
ICH4: chipset revision 1
ICH4: not 100% native mode: will probe irqs later
ICH4: port 0x01f0 already claimed by ide0
ICH4: port 0x0170 already claimed by ide1
ICH4: neither IDE port enabled (BIOS)
usb 3-2: USB disconnect, address 2
usb 4-6.1: new high speed USB device using ehci_hcd and address 3
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 5 (level, low) -> IRQ 5
PCI: Setting latency timer of device 0000:00:1f.5 to 64
ub: sizeof ub_scsi_cmd 64 ub_dev 2504
usb 4-6.3: new low speed USB device using ehci_hcd and address 4
input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.7-6.3
uba: device 3 capacity nsec 585938944 bsize 512
uba: device 3 capacity nsec 585938944 bsize 512
 uba: uba1
usbcore: registered new driver ub
intel8x0_measure_ac97_clock: measured 49943 usecs
intel8x0: clocking to 45972
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Enabling device 0000:01:01.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:01:01.0[A] -> GSI 11 (level, low) -> IRQ 11
Yenta: CardBus bridge found at 0000:01:01.0 [1028:0163]
Yenta: ISA IRQ mask 0x0458, PCI irq 11
Socket status: 30000006
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:01:01.1[B] -> GSI 11 (level, low) -> IRQ 11
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fcfff800-fcffffff]  Max Packet=[2048]
e100: Intel(R) PRO/100 Network Driver, 3.3.6-k2-NAPI
e100: Copyright(c) 1999-2004 Intel Corporation
ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
ACPI: PCI interrupt 0000:01:08.0[A] -> GSI 11 (level, low) -> IRQ 11
e100: eth0: e100_probe: addr 0xfcffe000, irq 11, MAC addr 00:0F:1F:B3:93:D5
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[334fc000210b1ca1]
ibm_acpi: acpi_evalf(DHKC, d, ...) failed: 4097
ibm_acpi: `enable,0xffff' invalid for parameter `hotkey'
toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 11 (level, low) -> IRQ 11
[drm] Initialized i915 1.1.0 20040405 on minor 0: Intel Corp. 82852/855GM Integrated Graphics Device
[drm] Initialized i915 1.1.0 20040405 on minor 1: Intel Corp. 82852/855GM Integrated Graphics Device (#2)
mtrr: base(0xf0020000) is not aligned on a size(0x300000) boundary
cs: IO port probe 0x100-0x4ff: clean.
cs: IO port probe 0x800-0x8ff: clean.
cs: IO port probe 0xc00-0xcff: clean.
cs: IO port probe 0xa00-0xaff: clean.
ibm_acpi: acpi_evalf(DHKC, d, ...) failed: 4097
ibm_acpi: `enable,0xffff' invalid for parameter `hotkey'
toshiba_acpi: Unknown parameter `hotkeys_over_acpi'

```

---

