---
title: "problems with Shutdown  and Evolution"
date: 2006-10-18
forum: General Help
---

### Post by Efhache84 on 2006-10-18
Hello all,

I already asked on the forum ubuntu-Fr, but nobody could bring an answer to me. I hope to have more chance here.
I am on Dapper Ubuntu 6.06.1 LTS (Gnome) **without** compil, beryl or Xgl. On October 12 I made the updates suggested by ubuntu of which here the list (resulting from synaptic - historic)

> Commit Log for Thu Oct 12 22:37:51 2006


Les paquets suivant ont été mis à jour :
cpio (2.6-10) to 2.6-10ubuntu0.2
libmusicbrainz4c2a (2.1.2-2ubuntu3) to 2.1.2-2ubuntu3.1
python2.4 (2.4.3-0ubuntu4) to 2.4.3-0ubuntu6
python2.4-examples (2.4.3-0ubuntu4) to 2.4.3-0ubuntu6
python2.4-gdbm (2.4.3-0ubuntu4) to 2.4.3-0ubuntu6
python2.4-minimal (2.4.3-0ubuntu4) to 2.4.3-0ubuntu6
python2.4-tk (2.4.3-0ubuntu4) to 2.4.3-0ubuntu6
skype (1.2.0.18-2) to 1.3.0.53-0plf6.06

Les paquets suivants ont été installés :
librte1 (0.5.1-0.1)

My problem is as follows:

When I click on the icon “shutdown” nothing occurs. My mouse remains active and the adesklets also (temperature and speed CPU on SYSTEM-MONITOR ). But nothing more. I can nothing any more launch.  I try the keys ctrl+alt+backspace then. There I arrive on an environment text and after a few seconds closing continues. (or sometimes that reboot)

I also have a problem with EVOLUTION. When I close EVOLUTION, if I want to reopen it later, nothing does not do either.

I also installed the game SAVAGE whose procedure of installation was in the planet ubuntu-Fr.

Could somebody help me? Is this a problem with PYTHON? A process which remains blocked? 

Help me please](*,) 

Thanks

Efhache84 (Belgium)

---

### Post by Efhache84 on 2006-10-18
I have also uninstalled the games wormux

> Commit Log for Thu Oct 12 22:55:36 2006


Les paquets suivants ont été complètement supprimés :
wormux
wormux-data

and remove the orphan packet (with deborphan in synaptic)

>  Commit Log for Thu Oct 12 22:56:15 2006


Les paquets suivants ont été complètement supprimés :
libsdl-gfx1.2-4
libsdl-image1.2
libsdl-ttf1.2
libxml++2.6c2a
libttf2

Saturday, octobre 14, I've install and uninstall the software "gajim" 

> ommit Log for Sat Oct 14 16:35:16 2006


Les paquets suivants ont été installés :
gajim (0.10-0ubuntu4)
python-pysqlite2 (2.0.5-1ubuntu1)
python2.4-pysqlite2 (2.0.5-1ubuntu1)

and for the remove of gajim

> Commit Log for Sat Oct 14 16:39:51 2006


Les paquets suivants ont été complètement supprimés :
gajim



If it can help you... to resolve my problem...

---

### Post by Efhache84 on 2006-10-19
Someone can help me?? :-?

---

### Post by metalheart on 2006-10-19
Can you shut down from command prompt?
```
sudo shutdown -h now
```

---

### Post by Efhache84 on 2006-10-20
> **metalheart said:**
> Can you shut down from command prompt?
```
sudo shutdown -h now
```
Like I said, if I click on the shutdown icon, I can't do anithing more. And so I can't open a shell (terminal). And for continuing the shutdown process I must type ctrl+alt+backspace.

But after that, after a restart, I do the command shutdown -h, and it was somes messages, then my prompt appear more times. (+/- 20 times) in a few second...

---

### Post by Efhache84 on 2006-10-20
.

---

### Post by Efhache84 on 2006-10-20
I don't know if that can help you, but here it's the copy of my log journal for the last restart.

```

Oct 20 13:25:50 localhost syslogd 1.4.1#17ubuntu7: restart.
Oct 20 13:25:50 localhost kernel: Inspecting /boot/System.map-2.6.15-27-386
Oct 20 13:25:50 localhost kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Oct 20 13:25:50 localhost kernel: Symbols match kernel version 2.6.15.
Oct 20 13:25:50 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Oct 20 13:25:50 localhost kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
Oct 20 13:25:50 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Oct 20 13:25:50 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 20 13:25:50 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 20 13:25:50 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 20 13:25:50 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
Oct 20 13:25:50 localhost kernel: [17179569.184000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
Oct 20 13:25:50 localhost kernel: [17179569.184000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
Oct 20 13:25:50 localhost kernel: [17179569.184000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
Oct 20 13:25:50 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Oct 20 13:25:50 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 20 13:25:50 localhost kernel: [17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Oct 20 13:25:50 localhost kernel: [17179569.184000] 0MB HIGHMEM available.
Oct 20 13:25:50 localhost kernel: [17179569.184000] 511MB LOWMEM available.
Oct 20 13:25:50 localhost kernel: [17179569.184000] DMI 2.3 present.
Oct 20 13:25:50 localhost kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0xe408
Oct 20 13:25:50 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 20 13:25:50 localhost kernel: [17179569.184000] Processor #0 15:2 APIC version 20
Oct 20 13:25:50 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct 20 13:25:50 localhost kernel: [17179569.184000] Processor #1 15:2 APIC version 20
Oct 20 13:25:50 localhost kernel: [17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
Oct 20 13:25:50 localhost kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 20 13:25:50 localhost kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 20 13:25:50 localhost kernel: [17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 20 13:25:50 localhost kernel: [17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 20 13:25:50 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
Oct 20 13:25:50 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 22 low level)
Oct 20 13:25:50 localhost kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 20 13:25:50 localhost kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Oct 20 13:25:50 localhost kernel: [17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Oct 20 13:25:50 localhost kernel: [17179569.184000] Built 1 zonelists
Oct 20 13:25:50 localhost kernel: [17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
Oct 20 13:25:50 localhost kernel: [17179569.184000] Initializing CPU#0
Oct 20 13:25:50 localhost kernel: [17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
Oct 20 13:25:50 localhost kernel: [17179569.184000] Detected 2400.557 MHz processor.
Oct 20 13:25:50 localhost kernel: [17179569.184000] Using pmtmr for high-res timesource
Oct 20 13:25:50 localhost kernel: [17179569.184000] Console: colour VGA+ 80x25
Oct 20 13:25:50 localhost kernel: [17179573.228000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 20 13:25:50 localhost kernel: [17179573.228000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 20 13:25:50 localhost kernel: [17179573.240000] Memory: 508852k/524208k available (1976k kernel code, 14804k reserved, 606k data, 288k init, 0k highmem)
Oct 20 13:25:50 localhost kernel: [17179573.240000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 20 13:25:50 localhost kernel: [17179573.320000] Calibrating delay using timer specific routine.. 4804.90 BogoMIPS (lpj=9609812)
Oct 20 13:25:50 localhost kernel: [17179573.320000] Security Framework v1.0.0 initialized
Oct 20 13:25:50 localhost kernel: [17179573.320000] SELinux:  Disabled at boot.
Oct 20 13:25:50 localhost kernel: [17179573.320000] Mount-cache hash table entries: 512
Oct 20 13:25:50 localhost kernel: [17179573.320000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Oct 20 13:25:50 localhost kernel: [17179573.320000] CPU: L2 cache: 512K
Oct 20 13:25:50 localhost kernel: [17179573.320000] mtrr: v2.0 (20020519)
Oct 20 13:25:50 localhost kernel: [17179573.320000] CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 05
Oct 20 13:25:50 localhost kernel: [17179573.320000] Enabling fast FPU save and restore... done.
Oct 20 13:25:50 localhost kernel: [17179573.320000] Enabling unmasked SIMD FPU exception support... done.
Oct 20 13:25:50 localhost kernel: [17179573.320000] Checking 'hlt' instruction... OK.
Oct 20 13:25:50 localhost kernel: [17179573.336000] checking if image is initramfs... it is
Oct 20 13:25:50 localhost kernel: [17179573.896000] Freeing initrd memory: 6616k freed
Oct 20 13:25:50 localhost kernel: [17179573.908000] ACPI: Looking for DSDT ... not found!
Oct 20 13:25:50 localhost kernel: [17179573.908000] ENABLING IO-APIC IRQs
Oct 20 13:25:50 localhost kernel: [17179573.912000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 20 13:25:50 localhost kernel: [17179574.052000] NET: Registered protocol family 16
Oct 20 13:25:50 localhost kernel: [17179574.052000] EISA bus registered
Oct 20 13:25:50 localhost kernel: [17179574.052000] ACPI: bus type pci registered
Oct 20 13:25:50 localhost kernel: [17179574.052000] PCI: PCI BIOS revision 2.10 entry at 0xf1e50, last bus=2
Oct 20 13:25:50 localhost kernel: [17179574.052000] PCI: Using configuration type 1
Oct 20 13:25:50 localhost kernel: [17179574.052000] ACPI: Subsystem revision 20051216
Oct 20 13:25:50 localhost kernel: [17179574.056000] ACPI: Interpreter enabled
Oct 20 13:25:50 localhost kernel: [17179574.056000] ACPI: Using IOAPIC for interrupt routing
Oct 20 13:25:50 localhost kernel: [17179574.056000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Oct 20 13:25:50 localhost kernel: [17179574.056000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 20 13:25:50 localhost kernel: [17179574.056000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 20 13:25:50 localhost kernel: [17179574.056000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 20 13:25:50 localhost kernel: [17179574.060000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Oct 20 13:25:50 localhost kernel: [17179574.060000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 20 13:25:50 localhost kernel: [17179574.060000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 20 13:25:50 localhost kernel: [17179574.060000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Oct 20 13:25:50 localhost kernel: [17179574.060000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 20 13:25:50 localhost kernel: [17179574.060000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Oct 20 13:25:50 localhost kernel: [17179574.064000] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
Oct 20 13:25:50 localhost kernel: [17179574.064000] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
Oct 20 13:25:50 localhost kernel: [17179574.064000] PCI: Enabled i801 SMBus device
Oct 20 13:25:50 localhost kernel: [17179574.064000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Oct 20 13:25:50 localhost kernel: [17179574.064000] PCI: Transparent bridge - 0000:00:1e.0
Oct 20 13:25:50 localhost kernel: [17179574.072000] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 20 13:25:50 localhost kernel: [17179574.072000] pnp: PnP ACPI init
Oct 20 13:25:50 localhost kernel: [17179574.080000] pnp: PnP ACPI: found 15 devices
Oct 20 13:25:50 localhost kernel: [17179574.080000] PnPBIOS: Disabled by ACPI PNP
Oct 20 13:25:50 localhost kernel: [17179574.080000] PCI: Using ACPI for IRQ routing
Oct 20 13:25:50 localhost kernel: [17179574.080000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 20 13:25:50 localhost kernel: [17179574.088000] pnp: 00:01: ioport range 0xe400-0xe47f could not be reserved
Oct 20 13:25:50 localhost kernel: [17179574.088000] pnp: 00:01: ioport range 0xe800-0xe81f has been reserved
Oct 20 13:25:50 localhost kernel: [17179574.088000] pnp: 00:01: ioport range 0xec00-0xec3f has been reserved
Oct 20 13:25:50 localhost kernel: [17179574.088000] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
Oct 20 13:25:50 localhost kernel: [17179574.088000] pnp: 00:0e: ioport range 0x3f0-0x3f1 has been reserved
Oct 20 13:25:50 localhost kernel: [17179574.088000] PCI: Bridge: 0000:00:01.0
Oct 20 13:25:50 localhost kernel: [17179574.088000]   IO window: disabled.
Oct 20 13:25:50 localhost kernel: [17179574.088000]   MEM window: ee000000-efdfffff
Oct 20 13:25:50 localhost kernel: [17179574.088000]   PREFETCH window: eff00000-f7ffffff
Oct 20 13:25:50 localhost kernel: [17179574.088000] PCI: Bridge: 0000:00:1e.0
Oct 20 13:25:50 localhost kernel: [17179574.088000]   IO window: disabled.
Oct 20 13:25:50 localhost kernel: [17179574.088000]   MEM window: ed000000-ed7fffff
Oct 20 13:25:50 localhost kernel: [17179574.088000]   PREFETCH window: efe00000-efefffff
Oct 20 13:25:50 localhost kernel: [17179574.088000] Simple Boot Flag at 0x3a set to 0x1
Oct 20 13:25:50 localhost kernel: [17179574.088000] audit: initializing netlink socket (disabled)
Oct 20 13:25:50 localhost kernel: [17179574.088000] audit(1161343531.088:1): initialized
Oct 20 13:25:50 localhost kernel: [17179574.088000] VFS: Disk quotas dquot_6.5.1
Oct 20 13:25:50 localhost kernel: [17179574.088000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 20 13:25:50 localhost kernel: [17179574.088000] Initializing Cryptographic API
Oct 20 13:25:50 localhost kernel: [17179574.088000] io scheduler noop registered
Oct 20 13:25:50 localhost kernel: [17179574.088000] io scheduler anticipatory registered
Oct 20 13:25:50 localhost kernel: [17179574.088000] io scheduler deadline registered
Oct 20 13:25:50 localhost kernel: [17179574.088000] io scheduler cfq registered
Oct 20 13:25:50 localhost kernel: [17179574.088000] isapnp: Scanning for PnP cards...
Oct 20 13:25:50 localhost kernel: [17179574.440000] isapnp: No Plug & Play device found
Oct 20 13:25:50 localhost kernel: [17179574.456000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 20 13:25:50 localhost kernel: [17179574.460000] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 20 13:25:50 localhost kernel: [17179574.460000] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 20 13:25:50 localhost kernel: [17179574.460000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Oct 20 13:25:50 localhost kernel: [17179574.460000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 20 13:25:50 localhost kernel: [17179574.460000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Oct 20 13:25:50 localhost kernel: [17179574.460000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 20 13:25:50 localhost kernel: [17179574.464000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Oct 20 13:25:50 localhost kernel: [17179574.464000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 20 13:25:50 localhost kernel: [17179574.464000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2

```

---

### Post by Efhache84 on 2006-10-20
log journal rest :

```

Oct 20 13:25:50 localhost kernel: [17179574.464000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 20 13:25:50 localhost kernel: [17179574.464000] mice: PS/2 mouse device common for all mice
Oct 20 13:25:50 localhost kernel: [17179574.464000] EISA: Probing bus 0 at eisa.0
Oct 20 13:25:50 localhost kernel: [17179574.464000] EISA: Detected 0 cards.
Oct 20 13:25:50 localhost kernel: [17179574.464000] NET: Registered protocol family 2
Oct 20 13:25:50 localhost kernel: [17179574.484000] input: AT Translated Set 2 keyboard as /class/input/input0
Oct 20 13:25:50 localhost kernel: [17179574.504000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
Oct 20 13:25:50 localhost kernel: [17179574.504000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
Oct 20 13:25:50 localhost kernel: [17179574.504000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
Oct 20 13:25:50 localhost kernel: [17179574.504000] TCP: Hash tables configured (established 32768 bind 32768)
Oct 20 13:25:50 localhost kernel: [17179574.504000] TCP reno registered
Oct 20 13:25:50 localhost kernel: [17179574.504000] TCP bic registered
Oct 20 13:25:50 localhost kernel: [17179574.504000] NET: Registered protocol family 1
Oct 20 13:25:50 localhost kernel: [17179574.504000] NET: Registered protocol family 8
Oct 20 13:25:50 localhost kernel: [17179574.504000] NET: Registered protocol family 20
Oct 20 13:25:50 localhost kernel: [17179574.504000] Using IPI Shortcut mode
Oct 20 13:25:50 localhost kernel: [17179574.504000] ACPI wakeup devices: 
Oct 20 13:25:50 localhost kernel: [17179574.504000] PCI0 PCI1 PCI2 UAR1 USB0 USB1 USB2 US20 AC97 
Oct 20 13:25:50 localhost kernel: [17179574.504000] ACPI: (supports S0 S1 S4 S5)
Oct 20 13:25:50 localhost kernel: [17179574.504000] Freeing unused kernel memory: 288k freed
Oct 20 13:25:50 localhost kernel: [17179574.548000] vga16fb: mapped to 0xc00a0000
Oct 20 13:25:50 localhost kernel: [17179574.696000] Console: switching to colour frame buffer device 80x25
Oct 20 13:25:50 localhost kernel: [17179574.696000] fb0: VGA16 VGA frame buffer device
Oct 20 13:25:50 localhost kernel: [17179575.832000] Capability LSM initialized
Oct 20 13:25:50 localhost kernel: [17179576.420000] ICH4: IDE controller at PCI slot 0000:00:1f.1
Oct 20 13:25:50 localhost kernel: [17179576.420000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
Oct 20 13:25:50 localhost kernel: [17179576.420000] ICH4: chipset revision 2
Oct 20 13:25:50 localhost kernel: [17179576.420000] ICH4: not 100%% native mode: will probe irqs later
Oct 20 13:25:50 localhost kernel: [17179576.420000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Oct 20 13:25:50 localhost kernel: [17179576.420000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Oct 20 13:25:50 localhost kernel: [17179576.708000] hda: Maxtor 6L120P0, ATA DISK drive
Oct 20 13:25:50 localhost kernel: [17179576.988000] hdb: Maxtor 6Y080L0, ATA DISK drive
Oct 20 13:25:50 localhost kernel: [17179577.044000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Oct 20 13:25:50 localhost kernel: [17179577.804000] hdc: CD-RW IDE5232, ATAPI CD/DVD-ROM drive
Oct 20 13:25:50 localhost kernel: [17179578.588000] hdd: DVD-ROM BDV316C, ATAPI CD/DVD-ROM drive
Oct 20 13:25:50 localhost kernel: [17179578.644000] ide1 at 0x170-0x177,0x376 on irq 15
Oct 20 13:25:50 localhost kernel: [17179578.648000] hda: max request size: 128KiB
Oct 20 13:25:50 localhost kernel: [17179578.668000] hda: 240121728 sectors (122942 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
Oct 20 13:25:50 localhost kernel: [17179578.668000] hda: cache flushes supported
Oct 20 13:25:50 localhost kernel: [17179578.668000]  hda: hda1 hda2 < hda5 >
Oct 20 13:25:50 localhost kernel: [17179578.716000] hdb: max request size: 128KiB
Oct 20 13:25:50 localhost kernel: [17179578.716000] hdb: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Oct 20 13:25:50 localhost kernel: [17179578.716000] hdb: cache flushes supported
Oct 20 13:25:50 localhost kernel: [17179578.716000]  hdb: hdb1 hdb2
Oct 20 13:25:50 localhost kernel: [17179578.720000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Oct 20 13:25:50 localhost kernel: [17179578.720000] Uniform CD-ROM driver Revision: 3.20
Oct 20 13:25:50 localhost kernel: [17179578.724000] hdd: ATAPI 1X DVD-ROM drive, 512kB Cache, UDMA(33)
Oct 20 13:25:50 localhost kernel: [17179579.072000] usbcore: registered new driver usbfs
Oct 20 13:25:50 localhost kernel: [17179579.072000] usbcore: registered new driver hub
Oct 20 13:25:50 localhost kernel: [17179579.076000] USB Universal Host Controller Interface driver v2.3
Oct 20 13:25:50 localhost kernel: [17179579.076000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
Oct 20 13:25:50 localhost kernel: [17179579.076000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 20 13:25:50 localhost kernel: [17179579.076000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct 20 13:25:50 localhost kernel: [17179579.076000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x0000d800
Oct 20 13:25:50 localhost kernel: [17179579.076000] hub 1-0:1.0: USB hub found
Oct 20 13:25:50 localhost kernel: [17179579.076000] hub 1-0:1.0: 2 ports detected
Oct 20 13:25:50 localhost kernel: [17179579.180000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
Oct 20 13:25:50 localhost kernel: [17179579.180000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 20 13:25:50 localhost kernel: [17179579.180000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Oct 20 13:25:50 localhost kernel: [17179579.180000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000d400
Oct 20 13:25:50 localhost kernel: [17179579.180000] hub 2-0:1.0: USB hub found
Oct 20 13:25:50 localhost kernel: [17179579.180000] hub 2-0:1.0: 2 ports detected
Oct 20 13:25:50 localhost kernel: [17179579.284000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
Oct 20 13:25:50 localhost kernel: [17179579.284000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 20 13:25:50 localhost kernel: [17179579.284000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Oct 20 13:25:50 localhost kernel: [17179579.284000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x0000d000
Oct 20 13:25:50 localhost kernel: [17179579.284000] hub 3-0:1.0: USB hub found
Oct 20 13:25:50 localhost kernel: [17179579.284000] hub 3-0:1.0: 2 ports detected
Oct 20 13:25:50 localhost kernel: [17179579.388000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
Oct 20 13:25:50 localhost kernel: [17179579.388000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 20 13:25:50 localhost kernel: [17179579.388000] ehci_hcd 0000:00:1d.7: debug port 1
Oct 20 13:25:50 localhost kernel: [17179579.388000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Oct 20 13:25:50 localhost kernel: [17179579.388000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xed800000
Oct 20 13:25:50 localhost kernel: [17179579.392000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 20 13:25:50 localhost kernel: [17179579.392000] hub 4-0:1.0: USB hub found
Oct 20 13:25:50 localhost kernel: [17179579.392000] hub 4-0:1.0: 6 ports detected
Oct 20 13:25:50 localhost kernel: [17179579.420000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Oct 20 13:25:50 localhost kernel: [17179579.592000] Attempting manual resume
Oct 20 13:25:50 localhost kernel: [17179579.612000] kjournald starting.  Commit interval 5 seconds
Oct 20 13:25:50 localhost kernel: [17179579.612000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 20 13:25:50 localhost kernel: [17179580.844000] usb 1-1: new full speed USB device using uhci_hcd and address 3
Oct 20 13:25:50 localhost kernel: [17179581.228000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Oct 20 13:25:50 localhost kernel: [17179581.608000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Oct 20 13:25:50 localhost kernel: [17179581.996000] usb 2-2: new full speed USB device using uhci_hcd and address 3
Oct 20 13:25:50 localhost kernel: [17179588.592000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 20 13:25:50 localhost kernel: [17179588.612000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 20 13:25:50 localhost kernel: [17179588.636000] Linux agpgart interface v0.101 (c) Dave Jones
Oct 20 13:25:50 localhost kernel: [17179588.636000] agpgart: Detected an Intel 845G Chipset.
Oct 20 13:25:50 localhost kernel: [17179588.640000] agpgart: AGP aperture is 64M @ 0xf8000000
Oct 20 13:25:50 localhost kernel: [17179589.084000] nvidia: module license 'NVIDIA' taints kernel.
Oct 20 13:25:50 localhost kernel: [17179589.088000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
Oct 20 13:25:50 localhost kernel: [17179589.088000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
Oct 20 13:25:50 localhost kernel: [17179589.100000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x8104
Oct 20 13:25:50 localhost kernel: [17179589.100000] usbcore: registered new driver usblp
Oct 20 13:25:50 localhost kernel: [17179589.100000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Oct 20 13:25:50 localhost kernel: [17179589.668000] Real Time Clock Driver v1.12
Oct 20 13:25:50 localhost kernel: [17179589.712000] input: PC Speaker as /class/input/input1
Oct 20 13:25:50 localhost kernel: [17179589.744000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
Oct 20 13:25:50 localhost kernel: [17179589.832000] Floppy drive(s): fd0 is 1.44M
Oct 20 13:25:50 localhost kernel: [17179589.852000] FDC 0 is a post-1991 82077
Oct 20 13:25:50 localhost kernel: [17179589.984000] input: PS2++ Logitech MX Mouse as /class/input/input2
Oct 20 13:25:50 localhost kernel: [17179590.008000] SCSI subsystem initialized
Oct 20 13:25:50 localhost kernel: [17179590.020000] Initializing USB Mass Storage driver...
Oct 20 13:25:50 localhost kernel: [17179590.020000] scsi0 : SCSI emulation for USB Mass Storage devices
Oct 20 13:25:50 localhost kernel: [17179590.020000] usbcore: registered new driver usb-storage
Oct 20 13:25:50 localhost kernel: [17179590.020000] USB Mass Storage support registered.
Oct 20 13:25:50 localhost kernel: [17179590.104000] AC'97 0 analog subsections not ready
Oct 20 13:25:50 localhost kernel: [17179590.168000] intel8x0_measure_ac97_clock: measured 52148 usecs
Oct 20 13:25:50 localhost kernel: [17179590.168000] intel8x0: clocking to 48000
Oct 20 13:25:50 localhost kernel: [17179590.228000] hw_random hardware driver 1.0.0 loaded
Oct 20 13:25:50 localhost kernel: [17179590.276000] parport: PnPBIOS parport detected.
Oct 20 13:25:50 localhost kernel: [17179590.276000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Oct 20 13:25:50 localhost kernel: [17179590.288000] Linux video capture interface: v1.00
Oct 20 13:25:50 localhost kernel: [17179590.340000] pwc Philips webcam module version 10.0.7-unofficial loaded.
Oct 20 13:25:50 localhost kernel: [17179590.340000] pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
Oct 20 13:25:50 localhost kernel: [17179590.340000] pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
Oct 20 13:25:50 localhost kernel: [17179590.340000] pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
Oct 20 13:25:50 localhost kernel: [17179590.340000] pwc Trace options: 0x00a1
Oct 20 13:25:50 localhost kernel: [17179590.340000] pwc Logitech QuickCam Zoom (new model) USB webcam detected.
Oct 20 13:25:50 localhost kernel: [17179590.340000] pwc Registered as /dev/video0.
Oct 20 13:25:50 localhost kernel: [17179590.340000] usbcore: registered new driver Philips webcam
Oct 20 13:25:50 localhost kernel: [17179590.448000] ts: Compaq touchscreen protocol output
Oct 20 13:25:50 localhost kernel: [17179590.512000] usbcore: registered new driver snd-usb-audio
Oct 20 13:25:50 localhost kernel: [17179590.640000] tg3.c:v3.47 (Dec 28, 2005)
Oct 20 13:25:50 localhost kernel: [17179590.640000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 217
Oct 20 13:25:50 localhost kernel: [17179590.660000] eth0: Tigon3 [partno(BCM95702A20) rev 1002 PHY(5703)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0c:6e:b6:1d:e8
Oct 20 13:25:50 localhost kernel: [17179590.660000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
Oct 20 13:25:50 localhost kernel: [17179590.660000] eth0: dma_rwctrl[763f0000]
Oct 20 13:25:50 localhost kernel: [17179591.228000] lp0: using parport0 (interrupt-driven).
Oct 20 13:25:50 localhost kernel: [17179591.708000] Adding 1502036k swap on /dev/hda5.  Priority:-1 extents:1 across:1502036k
Oct 20 13:25:50 localhost kernel: [17179591.872000] EXT3 FS on hda1, internal journal
Oct 20 13:25:50 localhost kernel: [17179592.056000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Oct 20 13:25:50 localhost kernel: [17179592.056000] md: bitmap version 4.39
Oct 20 13:25:50 localhost kernel: [17179592.244000] NET: Registered protocol family 17
Oct 20 13:25:50 localhost kernel: [17179592.788000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct 20 13:25:50 localhost kernel: [17179592.788000] tg3: eth0: Flow control is off for TX and off for RX.
Oct 20 13:25:50 localhost kernel: [17179592.992000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
Oct 20 13:25:50 localhost kernel: [17179593.244000] cdrom: open failed.
Oct 20 13:25:50 localhost kernel: [17179593.620000] cdrom: open failed.
Oct 20 13:25:50 localhost kernel: [17179593.624000] cdrom: open failed.
Oct 20 13:25:50 localhost kernel: [17179594.072000] NTFS driver 2.1.25 [Flags: R/O MODULE].
Oct 20 13:25:50 localhost kernel: [17179594.120000] NTFS volume version 3.1.
Oct 20 13:25:50 localhost kernel: [17179595.024000]   Vendor: IOMEGA    Model: ZIP 250           Rev: 31.G
Oct 20 13:25:50 localhost kernel: [17179595.024000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Oct 20 13:25:50 localhost kernel: [17179595.068000] Driver 'sd' needs updating - please use bus_type methods
Oct 20 13:25:50 localhost kernel: [17179595.100000] sd 0:0:0:0: Attached scsi removable disk sda
Oct 20 13:25:50 localhost kernel: [17179595.112000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 20 13:25:50 localhost kernel: [17179595.784000] NET: Registered protocol family 10
Oct 20 13:25:50 localhost kernel: [17179595.784000] lo: Disabled Privacy Extensions
Oct 20 13:25:50 localhost kernel: [17179595.784000] IPv6 over IPv4 tunneling driver
Oct 20 13:25:50 localhost kernel: [17179596.028000] ip_tables: (C) 2000-2002 Netfilter core team
Oct 20 13:25:50 localhost kernel: [17179596.532000] ACPI: Power Button (FF) [PWRF]
Oct 20 13:25:50 localhost kernel: [17179596.532000] ACPI: Power Button (CM) [PWRB]
Oct 20 13:25:50 localhost kernel: [17179596.660000] pcc_acpi: loading...
Oct 20 13:25:53 localhost hpiod: 0.9.7 accepting connections at 35970... 
Oct 20 13:25:54 localhost kernel: [17179601.688000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct 20 13:25:54 localhost kernel: [17179601.688000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct 20 13:25:54 localhost kernel: [17179601.688000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Oct 20 13:25:54 localhost kernel: [17179601.804000] i2c_adapter i2c-1: SMBus Quick command not supported, can't probe for chips
Oct 20 13:25:54 localhost kernel: [17179601.804000] i2c_adapter i2c-2: SMBus Quick command not supported, can't probe for chips
Oct 20 13:25:54 localhost kernel: [17179601.804000] i2c_adapter i2c-3: SMBus Quick command not supported, can't probe for chips
Oct 20 13:25:55 localhost kernel: [17179603.080000] ppdev: user-space parallel port driver
Oct 20 13:25:56 localhost kernel: [17179603.480000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct 20 13:25:56 localhost kernel: [17179603.480000] apm: overridden by ACPI.
Oct 20 13:25:59 localhost kernel: [17179606.700000] Netfilter messages via NETLINK v0.30.
Oct 20 13:25:59 localhost kernel: [17179606.772000] ip_conntrack version 2.4 (4095 buckets, 32760 max) - 232 bytes per conntrack
Oct 20 13:26:01 localhost kernel: [17179608.920000] Bluetooth: Core ver 2.8
Oct 20 13:26:01 localhost kernel: [17179608.920000] NET: Registered protocol family 31
Oct 20 13:26:01 localhost kernel: [17179608.920000] Bluetooth: HCI device and connection manager initialized
Oct 20 13:26:01 localhost kernel: [17179608.920000] Bluetooth: HCI socket layer initialized
Oct 20 13:26:01 localhost kernel: [17179608.944000] Bluetooth: L2CAP ver 2.8
Oct 20 13:26:01 localhost kernel: [17179608.944000] Bluetooth: L2CAP socket layer initialized
Oct 20 13:26:01 localhost kernel: [17179608.948000] Bluetooth: RFCOMM socket layer initialized
Oct 20 13:26:01 localhost kernel: [17179608.948000] Bluetooth: RFCOMM TTY layer initialized
Oct 20 13:26:01 localhost kernel: [17179608.948000] Bluetooth: RFCOMM ver 1.7
Oct 20 13:26:06 localhost gconfd (fhiernaux-5144): démarrage (version 2.14.0), pid 5144 utilisateur « fhiernaux »
Oct 20 13:26:06 localhost gconfd (fhiernaux-5144): Adresse « xml:readonly:/etc/gconf/gconf.xml.mandatory » résolue vers une source de configuration en lecture seule à la position 0
Oct 20 13:26:06 localhost gconfd (fhiernaux-5144): Adresse « xml:readwrite:/home/fhiernaux/.gconf » résolue vers une source de configuration accessible en écriture à la position 1
Oct 20 13:26:06 localhost gconfd (fhiernaux-5144): Adresse « xml:readonly:/etc/gconf/gconf.xml.defaults » résolue vers une source de configuration en lecture seule à la position 2
Oct 20 13:26:06 localhost gconfd (fhiernaux-5144): Adresse « xml:readonly:/var/lib/gconf/debian.defaults » résolue vers une source de configuration en lecture seule à la position 3
Oct 20 13:26:06 localhost gconfd (fhiernaux-5144): Adresse « xml:readonly:/var/lib/gconf/defaults » résolue vers une source de configuration en lecture seule à la position 4
Oct 20 13:26:12 localhost gconfd (fhiernaux-5144): Adresse « xml:readwrite:/home/fhiernaux/.gconf » résolue vers une source de configuration accessible en écriture à la position 0
Oct 20 13:27:12 localhost kernel: [17179679.768000] pwc Failed to restore power to the camera! (-32)
Oct 20 13:27:12 localhost kernel: [17179679.768000] pwc Failed to set LED on/off time.
Oct 20 13:27:32 localhost shutdown[5359]: shutting down for system halt
Oct 20 13:27:33 localhost gconfd (fhiernaux-5144): Réception du signal 15, arrêt correct
Oct 20 13:27:33 localhost gconfd (fhiernaux-5144): Sortie
Oct 20 13:27:33 localhost kernel: [17179700.836000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct 20 13:27:33 localhost kernel: [17179700.836000] apm: disabled on user request.
Oct 20 13:27:40 localhost kernel: Kernel logging (proc) stopped.
Oct 20 13:27:40 localhost kernel: Kernel log daemon terminating.
Oct 20 13:27:40 localhost exiting on signal 15
Oct 20 13:28:45 localhost syslogd 1.4.1#17ubuntu7: restart.
Oct 20 13:28:45 localhost kernel: Inspecting /boot/System.map-2.6.15-27-386
Oct 20 13:28:46 localhost kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Oct 20 13:28:46 localhost kernel: Symbols match kernel version 2.6.15.
Oct 20 13:28:46 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Oct 20 13:28:46 localhost kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
Oct 20 13:28:46 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Oct 20 13:28:46 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 20 13:28:46 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 20 13:28:46 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 20 13:28:46 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
Oct 20 13:28:46 localhost kernel: [17179569.184000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
Oct 20 13:28:46 localhost kernel: [17179569.184000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
Oct 20 13:28:46 localhost kernel: [17179569.184000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
Oct 20 13:28:46 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Oct 20 13:28:46 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 20 13:28:46 localhost kernel: [17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Oct 20 13:28:46 localhost kernel: [17179569.184000] 0MB HIGHMEM available.
Oct 20 13:28:46 localhost kernel: [17179569.184000] 511MB LOWMEM available.
Oct 20 13:28:46 localhost kernel: [17179569.184000] DMI 2.3 present.
Oct 20 13:28:46 localhost kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0xe408
Oct 20 13:28:46 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 20 13:28:46 localhost kernel: [17179569.184000] Processor #0 15:2 APIC version 20
Oct 20 13:28:46 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct 20 13:28:46 localhost kernel: [17179569.184000] Processor #1 15:2 APIC version 20
Oct 20 13:28:46 localhost kernel: [17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
Oct 20 13:28:46 localhost kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 20 13:28:46 localhost kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 20 13:28:46 localhost kernel: [17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 20 13:28:46 localhost kernel: [17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 20 13:28:46 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
Oct 20 13:28:46 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 22 low level)
Oct 20 13:28:46 localhost kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 20 13:28:46 localhost kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Oct 20 13:28:46 localhost kernel: [17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Oct 20 13:28:46 localhost kernel: [17179569.184000] Built 1 zonelists
Oct 20 13:28:46 localhost kernel: [17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
Oct 20 13:28:46 localhost kernel: [17179569.184000] Initializing CPU#0
Oct 20 13:28:46 localhost kernel: [17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
Oct 20 13:28:46 localhost kernel: [17179569.184000] Detected 2400.585 MHz processor.
Oct 20 13:28:46 localhost kernel: [17179569.184000] Using pmtmr for high-res timesource
Oct 20 13:28:46 localhost kernel: [17179569.184000] Console: colour VGA+ 80x25
Oct 20 13:28:46 localhost kernel: [17179571.348000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 20 13:28:46 localhost kernel: [17179571.348000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 20 13:28:46 localhost kernel: [17179571.360000] Memory: 508852k/524208k available (1976k kernel code, 14804k reserved, 606k data, 288k init, 0k highmem)
Oct 20 13:28:46 localhost kernel: [17179571.360000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 20 13:28:46 localhost kernel: [17179571.440000] Calibrating delay using timer specific routine.. 4804.93 BogoMIPS (lpj=9609860)
Oct 20 13:28:46 localhost kernel: [17179571.440000] Security Framework v1.0.0 initialized
Oct 20 13:28:46 localhost kernel: [17179571.440000] SELinux:  Disabled at boot.
Oct 20 13:28:46 localhost kernel: [17179571.440000] Mount-cache hash table entries: 512
Oct 20 13:28:46 localhost kernel: [17179571.440000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Oct 20 13:28:46 localhost kernel: [17179571.440000] CPU: L2 cache: 512K
Oct 20 13:28:46 localhost kernel: [17179571.440000] mtrr: v2.0 (20020519)
Oct 20 13:28:46 localhost kernel: [17179571.440000] CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 05
Oct 20 13:28:46 localhost kernel: [17179571.440000] Enabling fast FPU save and restore... done.
Oct 20 13:28:46 localhost kernel: [17179571.440000] Enabling unmasked SIMD FPU exception support... done.
Oct 20 13:28:46 localhost kernel: [17179571.440000] Checking 'hlt' instruction... OK.
Oct 20 13:28:46 localhost kernel: [17179571.456000] checking if image is initramfs... it is
Oct 20 13:28:46 localhost kernel: [17179572.016000] Freeing initrd memory: 6616k freed
Oct 20 13:28:46 localhost kernel: [17179572.028000] ACPI: Looking for DSDT ... not found!
Oct 20 13:28:46 localhost kernel: [17179572.032000] ENABLING IO-APIC IRQs
Oct 20 13:28:46 localhost kernel: [17179572.032000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 20 13:28:46 localhost kernel: [17179572.176000] NET: Registered protocol family 16
Oct 20 13:28:46 localhost kernel: [17179572.176000] EISA bus registered
Oct 20 13:28:46 localhost kernel: [17179572.176000] ACPI: bus type pci registered
Oct 20 13:28:46 localhost kernel: [17179572.176000] PCI: PCI BIOS revision 2.10 entry at 0xf1e50, last bus=2
Oct 20 13:28:46 localhost kernel: [17179572.176000] PCI: Using configuration type 1
Oct 20 13:28:46 localhost kernel: [17179572.176000] ACPI: Subsystem revision 20051216
Oct 20 13:28:46 localhost kernel: [17179572.180000] ACPI: Interpreter enabled
Oct 20 13:28:46 localhost kernel: [17179572.180000] ACPI: Using IOAPIC for interrupt routing
Oct 20 13:28:46 localhost kernel: [17179572.180000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Oct 20 13:28:46 localhost kernel: [17179572.180000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 20 13:28:46 localhost kernel: [17179572.180000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 20 13:28:46 localhost kernel: [17179572.180000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 20 13:28:46 localhost kernel: [17179572.184000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Oct 20 13:28:46 localhost kernel: [17179572.184000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 20 13:28:46 localhost kernel: [17179572.184000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 20 13:28:46 localhost kernel: [17179572.184000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Oct 20 13:28:46 localhost kernel: [17179572.184000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 20 13:28:46 localhost kernel: [17179572.184000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Oct 20 13:28:46 localhost kernel: [17179572.192000] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
Oct 20 13:28:46 localhost kernel: [17179572.192000] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
Oct 20 13:28:46 localhost kernel: [17179572.192000] PCI: Enabled i801 SMBus device
Oct 20 13:28:46 localhost kernel: [17179572.192000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Oct 20 13:28:46 localhost kernel: [17179572.192000] PCI: Transparent bridge - 0000:00:1e.0
Oct 20 13:28:46 localhost kernel: [17179572.200000] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 20 13:28:46 localhost kernel: [17179572.200000] pnp: PnP ACPI init
Oct 20 13:28:46 localhost kernel: [17179572.204000] pnp: PnP ACPI: found 15 devices
Oct 20 13:28:46 localhost kernel: [17179572.204000] PnPBIOS: Disabled by ACPI PNP
Oct 20 13:28:46 localhost kernel: [17179572.204000] PCI: Using ACPI for IRQ routing
Oct 20 13:28:46 localhost kernel: [17179572.204000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 20 13:28:46 localhost kernel: [17179572.212000] pnp: 00:01: ioport range 0xe400-0xe47f could not be reserved
Oct 20 13:28:46 localhost kernel: [17179572.212000] pnp: 00:01: ioport range 0xe800-0xe81f has been reserved
Oct 20 13:28:46 localhost kernel: [17179572.212000] pnp: 00:01: ioport range 0xec00-0xec3f has been reserved
Oct 20 13:28:46 localhost kernel: [17179572.212000] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
Oct 20 13:28:46 localhost kernel: [17179572.212000] pnp: 00:0e: ioport range 0x3f0-0x3f1 has been reserved
Oct 20 13:28:46 localhost kernel: [17179572.212000] PCI: Bridge: 0000:00:01.0
Oct 20 13:28:46 localhost kernel: [17179572.212000]   IO window: disabled.
Oct 20 13:28:46 localhost kernel: [17179572.212000]   MEM window: ee000000-efdfffff
Oct 20 13:28:46 localhost kernel: [17179572.212000]   PREFETCH window: eff00000-f7ffffff
Oct 20 13:28:46 localhost kernel: [17179572.212000] PCI: Bridge: 0000:00:1e.0
Oct 20 13:28:46 localhost kernel: [17179572.212000]   IO window: disabled.
Oct 20 13:28:46 localhost kernel: [17179572.212000]   MEM window: ed000000-ed7fffff
Oct 20 13:28:46 localhost kernel: [17179572.212000]   PREFETCH window: efe00000-efefffff
Oct 20 13:28:46 localhost kernel: [17179572.212000] Simple Boot Flag at 0x3a set to 0x1
Oct 20 13:28:46 localhost kernel: [17179572.212000] audit: initializing netlink socket (disabled)
Oct 20 13:28:46 localhost kernel: [17179572.212000] audit(1161343704.212:1): initialized
Oct 20 13:28:46 localhost kernel: [17179572.212000] VFS: Disk quotas dquot_6.5.1
Oct 20 13:28:46 localhost kernel: [17179572.212000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 20 13:28:46 localhost kernel: [17179572.212000] Initializing Cryptographic API
Oct 20 13:28:46 localhost kernel: [17179572.212000] io scheduler noop registered
Oct 20 13:28:46 localhost kernel: [17179572.212000] io scheduler anticipatory registered
Oct 20 13:28:46 localhost kernel: [17179572.212000] io scheduler deadline registered
Oct 20 13:28:46 localhost kernel: [17179572.212000] io scheduler cfq registered
Oct 20 13:28:46 localhost kernel: [17179572.212000] isapnp: Scanning for PnP cards...
Oct 20 13:28:46 localhost kernel: [17179572.564000] isapnp: No Plug & Play device found
Oct 20 13:28:46 localhost kernel: [17179572.580000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 20 13:28:46 localhost kernel: [17179572.584000] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 20 13:28:46 localhost kernel: [17179572.584000] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 20 13:28:46 localhost kernel: [17179572.584000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Oct 20 13:28:46 localhost kernel: [17179572.584000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 20 13:28:46 localhost kernel: [17179572.584000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Oct 20 13:28:46 localhost kernel: [17179572.588000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 20 13:28:46 localhost kernel: [17179572.588000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Oct 20 13:28:46 localhost kernel: [17179572.588000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 20 13:28:46 localhost kernel: [17179572.588000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct 20 13:28:46 localhost kernel: [17179572.588000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 20 13:28:46 localhost kernel: [17179572.588000] mice: PS/2 mouse device common for all mice
Oct 20 13:28:46 localhost kernel: [17179572.588000] EISA: Probing bus 0 at eisa.0
Oct 20 13:28:46 localhost kernel: [17179572.588000] EISA: Detected 0 cards.
Oct 20 13:28:46 localhost kernel: [17179572.588000] NET: Registered protocol family 2
Oct 20 13:28:46 localhost kernel: [17179572.608000] input: AT Translated Set 2 keyboard as /class/input/input0
Oct 20 13:28:46 localhost kernel: [17179572.628000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
Oct 20 13:28:46 localhost kernel: [17179572.628000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
Oct 20 13:28:46 localhost kernel: [17179572.628000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
Oct 20 13:28:46 localhost kernel: [17179572.628000] TCP: Hash tables configured (established 32768 bind 32768)
Oct 20 13:28:46 localhost kernel: [17179572.628000] TCP reno registered
Oct 20 13:28:46 localhost kernel: [17179572.628000] TCP bic registered
Oct 20 13:28:46 localhost kernel: [17179572.628000] NET: Registered protocol family 1
Oct 20 13:28:46 localhost kernel: [17179572.628000] NET: Registered protocol family 8
Oct 20 13:28:46 localhost kernel: [17179572.628000] NET: Registered protocol family 20
Oct 20 13:28:46 localhost kernel: [17179572.628000] Using IPI Shortcut mode
Oct 20 13:28:46 localhost kernel: [17179572.628000] ACPI wakeup devices: 
Oct 20 13:28:46 localhost kernel: [17179572.628000] PCI0 PCI1 PCI2 UAR1 USB0 USB1 USB2 US20 AC97 
Oct 20 13:28:46 localhost kernel: [17179572.628000] ACPI: (supports S0 S1 S4 S5)
Oct 20 13:28:46 localhost kernel: [17179572.628000] Freeing unused kernel memory: 288k freed
Oct 20 13:28:46 localhost kernel: [17179572.676000] vga16fb: mapped to 0xc00a0000
Oct 20 13:28:46 localhost kernel: [17179572.824000] Console: switching to colour frame buffer device 80x25
Oct 20 13:28:46 localhost kernel: [17179572.824000] fb0: VGA16 VGA frame buffer device
Oct 20 13:28:46 localhost kernel: [17179573.956000] Capability LSM initialized
Oct 20 13:28:46 localhost kernel: [17179574.544000] ICH4: IDE controller at PCI slot 0000:00:1f.1
Oct 20 13:28:46 localhost kernel: [17179574.544000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
Oct 20 13:28:46 localhost kernel: [17179574.544000] ICH4: chipset revision 2
Oct 20 13:28:46 localhost kernel: [17179574.544000] ICH4: not 100%% native mode: will probe irqs later
Oct 20 13:28:46 localhost kernel: [17179574.544000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Oct 20 13:28:46 localhost kernel: [17179574.544000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA

```

---

### Post by Efhache84 on 2006-10-20
(log journal rest 2 :

```

Oct 20 13:28:46 localhost kernel: [17179574.836000] hda: Maxtor 6L120P0, ATA DISK drive
Oct 20 13:28:46 localhost kernel: [17179575.116000] hdb: Maxtor 6Y080L0, ATA DISK drive
Oct 20 13:28:46 localhost kernel: [17179575.172000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Oct 20 13:28:46 localhost kernel: [17179575.932000] hdc: CD-RW IDE5232, ATAPI CD/DVD-ROM drive
Oct 20 13:28:46 localhost kernel: [17179576.716000] hdd: DVD-ROM BDV316C, ATAPI CD/DVD-ROM drive
Oct 20 13:28:46 localhost kernel: [17179576.772000] ide1 at 0x170-0x177,0x376 on irq 15
Oct 20 13:28:46 localhost kernel: [17179576.776000] hda: max request size: 128KiB
Oct 20 13:28:46 localhost kernel: [17179576.796000] hda: 240121728 sectors (122942 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
Oct 20 13:28:46 localhost kernel: [17179576.796000] hda: cache flushes supported
Oct 20 13:28:46 localhost kernel: [17179576.796000]  hda: hda1 hda2 < hda5 >
Oct 20 13:28:46 localhost kernel: [17179576.828000] hdb: max request size: 128KiB
Oct 20 13:28:46 localhost kernel: [17179576.828000] hdb: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Oct 20 13:28:46 localhost kernel: [17179576.828000] hdb: cache flushes supported
Oct 20 13:28:46 localhost kernel: [17179576.828000]  hdb:<6>hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Oct 20 13:28:46 localhost kernel: [17179576.828000] Uniform CD-ROM driver Revision: 3.20
Oct 20 13:28:46 localhost kernel: [17179576.832000] hdd: ATAPI 1X DVD-ROM drive, 512kB Cache, UDMA(33)
Oct 20 13:28:46 localhost kernel: [17179576.844000]  hdb1 hdb2
Oct 20 13:28:46 localhost kernel: [17179577.164000] usbcore: registered new driver usbfs
Oct 20 13:28:46 localhost kernel: [17179577.164000] usbcore: registered new driver hub
Oct 20 13:28:46 localhost kernel: [17179577.168000] USB Universal Host Controller Interface driver v2.3
Oct 20 13:28:46 localhost kernel: [17179577.168000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
Oct 20 13:28:46 localhost kernel: [17179577.168000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 20 13:28:46 localhost kernel: [17179577.168000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct 20 13:28:46 localhost kernel: [17179577.168000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x0000d800
Oct 20 13:28:46 localhost kernel: [17179577.168000] hub 1-0:1.0: USB hub found
Oct 20 13:28:46 localhost kernel: [17179577.168000] hub 1-0:1.0: 2 ports detected
Oct 20 13:28:46 localhost kernel: [17179577.272000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
Oct 20 13:28:46 localhost kernel: [17179577.272000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 20 13:28:46 localhost kernel: [17179577.272000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Oct 20 13:28:46 localhost kernel: [17179577.272000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000d400
Oct 20 13:28:46 localhost kernel: [17179577.272000] hub 2-0:1.0: USB hub found
Oct 20 13:28:46 localhost kernel: [17179577.272000] hub 2-0:1.0: 2 ports detected
Oct 20 13:28:46 localhost kernel: [17179577.376000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
Oct 20 13:28:46 localhost kernel: [17179577.376000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 20 13:28:46 localhost kernel: [17179577.376000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Oct 20 13:28:46 localhost kernel: [17179577.376000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x0000d000
Oct 20 13:28:46 localhost kernel: [17179577.376000] hub 3-0:1.0: USB hub found
Oct 20 13:28:46 localhost kernel: [17179577.376000] hub 3-0:1.0: 2 ports detected
Oct 20 13:28:46 localhost kernel: [17179577.480000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
Oct 20 13:28:46 localhost kernel: [17179577.480000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 20 13:28:46 localhost kernel: [17179577.480000] ehci_hcd 0000:00:1d.7: debug port 1
Oct 20 13:28:46 localhost kernel: [17179577.480000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Oct 20 13:28:46 localhost kernel: [17179577.480000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xed800000
Oct 20 13:28:46 localhost kernel: [17179577.484000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 20 13:28:46 localhost kernel: [17179577.484000] hub 4-0:1.0: USB hub found
Oct 20 13:28:46 localhost kernel: [17179577.484000] hub 4-0:1.0: 6 ports detected
Oct 20 13:28:46 localhost kernel: [17179577.512000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Oct 20 13:28:46 localhost kernel: [17179577.708000] Attempting manual resume
Oct 20 13:28:46 localhost kernel: [17179577.724000] kjournald starting.  Commit interval 5 seconds
Oct 20 13:28:46 localhost kernel: [17179577.724000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 20 13:28:46 localhost kernel: [17179578.936000] usb 1-1: new full speed USB device using uhci_hcd and address 3
Oct 20 13:28:46 localhost kernel: [17179579.320000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Oct 20 13:28:46 localhost kernel: [17179579.700000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Oct 20 13:28:46 localhost kernel: [17179580.088000] usb 2-2: new full speed USB device using uhci_hcd and address 3
Oct 20 13:28:46 localhost kernel: [17179586.940000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 20 13:28:46 localhost kernel: [17179586.944000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 20 13:28:46 localhost kernel: [17179586.980000] Linux agpgart interface v0.101 (c) Dave Jones
Oct 20 13:28:46 localhost kernel: [17179587.004000] hw_random hardware driver 1.0.0 loaded
Oct 20 13:28:46 localhost kernel: [17179587.016000] agpgart: Detected an Intel 845G Chipset.
Oct 20 13:28:46 localhost kernel: [17179587.020000] agpgart: AGP aperture is 64M @ 0xf8000000
Oct 20 13:28:46 localhost kernel: [17179587.088000] input: PS2++ Logitech MX Mouse as /class/input/input1
Oct 20 13:28:46 localhost kernel: [17179587.416000] Real Time Clock Driver v1.12
Oct 20 13:28:46 localhost kernel: [17179587.440000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
Oct 20 13:28:46 localhost kernel: [17179587.552000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x8104
Oct 20 13:28:46 localhost kernel: [17179587.552000] usbcore: registered new driver usblp
Oct 20 13:28:46 localhost kernel: [17179587.552000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Oct 20 13:28:46 localhost kernel: [17179587.564000] input: PC Speaker as /class/input/input2
Oct 20 13:28:46 localhost kernel: [17179587.612000] Floppy drive(s): fd0 is 1.44M
Oct 20 13:28:46 localhost kernel: [17179587.628000] FDC 0 is a post-1991 82077
Oct 20 13:28:46 localhost kernel: [17179587.800000] AC'97 0 analog subsections not ready
Oct 20 13:28:46 localhost kernel: [17179587.828000] nvidia: module license 'NVIDIA' taints kernel.
Oct 20 13:28:46 localhost kernel: [17179587.840000] Linux video capture interface: v1.00
Oct 20 13:28:46 localhost kernel: [17179587.868000] intel8x0_measure_ac97_clock: measured 55801 usecs
Oct 20 13:28:46 localhost kernel: [17179587.868000] intel8x0: clocking to 48000
Oct 20 13:28:46 localhost kernel: [17179587.868000] tg3.c:v3.47 (Dec 28, 2005)
Oct 20 13:28:46 localhost kernel: [17179587.868000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 217
Oct 20 13:28:46 localhost kernel: [17179587.888000] eth0: Tigon3 [partno(BCM95702A20) rev 1002 PHY(5703)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0c:6e:b6:1d:e8
Oct 20 13:28:46 localhost kernel: [17179587.888000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
Oct 20 13:28:46 localhost kernel: [17179587.888000] eth0: dma_rwctrl[763f0000]
Oct 20 13:28:46 localhost kernel: [17179587.888000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
Oct 20 13:28:46 localhost kernel: [17179587.888000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
Oct 20 13:28:46 localhost kernel: [17179587.972000] SCSI subsystem initialized
Oct 20 13:28:46 localhost kernel: [17179588.100000] parport: PnPBIOS parport detected.
Oct 20 13:28:46 localhost kernel: [17179588.100000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Oct 20 13:28:46 localhost kernel: [17179588.168000] pwc Philips webcam module version 10.0.7-unofficial loaded.
Oct 20 13:28:46 localhost kernel: [17179588.168000] pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
Oct 20 13:28:46 localhost kernel: [17179588.168000] pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
Oct 20 13:28:46 localhost kernel: [17179588.168000] pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
Oct 20 13:28:46 localhost kernel: [17179588.168000] pwc Trace options: 0x00a1
Oct 20 13:28:46 localhost kernel: [17179588.168000] pwc Logitech QuickCam Zoom (new model) USB webcam detected.
Oct 20 13:28:46 localhost kernel: [17179588.168000] pwc Registered as /dev/video0.
Oct 20 13:28:46 localhost kernel: [17179588.168000] usbcore: registered new driver Philips webcam
Oct 20 13:28:46 localhost kernel: [17179588.200000] Initializing USB Mass Storage driver...
Oct 20 13:28:46 localhost kernel: [17179588.200000] scsi0 : SCSI emulation for USB Mass Storage devices
Oct 20 13:28:46 localhost kernel: [17179588.200000] usbcore: registered new driver usb-storage
Oct 20 13:28:46 localhost kernel: [17179588.200000] USB Mass Storage support registered.
Oct 20 13:28:46 localhost kernel: [17179588.252000] usbcore: registered new driver snd-usb-audio
Oct 20 13:28:46 localhost kernel: [17179588.348000] ts: Compaq touchscreen protocol output
Oct 20 13:28:46 localhost kernel: [17179589.800000] lp0: using parport0 (interrupt-driven).
Oct 20 13:28:46 localhost kernel: [17179590.284000] Adding 1502036k swap on /dev/hda5.  Priority:-1 extents:1 across:1502036k
Oct 20 13:28:46 localhost kernel: [17179590.448000] EXT3 FS on hda1, internal journal
Oct 20 13:28:46 localhost kernel: [17179590.636000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Oct 20 13:28:46 localhost kernel: [17179590.636000] md: bitmap version 4.39
Oct 20 13:28:46 localhost kernel: [17179590.840000] NET: Registered protocol family 17
Oct 20 13:28:46 localhost kernel: [17179591.380000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct 20 13:28:46 localhost kernel: [17179591.380000] tg3: eth0: Flow control is off for TX and off for RX.
Oct 20 13:28:46 localhost kernel: [17179591.580000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
Oct 20 13:28:46 localhost kernel: [17179591.840000] cdrom: open failed.
Oct 20 13:28:46 localhost kernel: [17179592.240000] cdrom: open failed.
Oct 20 13:28:46 localhost kernel: [17179592.244000] cdrom: open failed.
Oct 20 13:28:46 localhost kernel: [17179592.776000] NTFS driver 2.1.25 [Flags: R/O MODULE].
Oct 20 13:28:46 localhost kernel: [17179592.824000] NTFS volume version 3.1.
Oct 20 13:28:46 localhost kernel: [17179593.204000]   Vendor: IOMEGA    Model: ZIP 250           Rev: 31.G
Oct 20 13:28:46 localhost kernel: [17179593.204000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Oct 20 13:28:46 localhost kernel: [17179593.300000] Driver 'sd' needs updating - please use bus_type methods
Oct 20 13:28:46 localhost kernel: [17179593.316000] sd 0:0:0:0: Attached scsi removable disk sda
Oct 20 13:28:46 localhost kernel: [17179593.324000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 20 13:28:46 localhost kernel: [17179594.540000] ip_tables: (C) 2000-2002 Netfilter core team
Oct 20 13:28:46 localhost kernel: [17179595.092000] ACPI: Power Button (FF) [PWRF]
Oct 20 13:28:46 localhost kernel: [17179595.092000] ACPI: Power Button (CM) [PWRB]
Oct 20 13:28:46 localhost kernel: [17179595.220000] pcc_acpi: loading...
Oct 20 13:28:48 localhost hpiod: 0.9.7 accepting connections at 44283... 
Oct 20 13:28:48 localhost kernel: [17179599.196000] NET: Registered protocol family 10
Oct 20 13:28:48 localhost kernel: [17179599.196000] lo: Disabled Privacy Extensions
Oct 20 13:28:48 localhost kernel: [17179599.196000] IPv6 over IPv4 tunneling driver
Oct 20 13:28:49 localhost kernel: [17179600.200000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct 20 13:28:49 localhost kernel: [17179600.200000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct 20 13:28:49 localhost kernel: [17179600.204000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Oct 20 13:28:49 localhost kernel: [17179600.320000] i2c_adapter i2c-1: SMBus Quick command not supported, can't probe for chips
Oct 20 13:28:49 localhost kernel: [17179600.320000] i2c_adapter i2c-2: SMBus Quick command not supported, can't probe for chips
Oct 20 13:28:49 localhost kernel: [17179600.320000] i2c_adapter i2c-3: SMBus Quick command not supported, can't probe for chips
Oct 20 13:28:51 localhost kernel: [17179601.376000] ppdev: user-space parallel port driver
Oct 20 13:28:51 localhost kernel: [17179602.040000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct 20 13:28:51 localhost kernel: [17179602.040000] apm: overridden by ACPI.
Oct 20 13:28:55 localhost kernel: [17179605.352000] Netfilter messages via NETLINK v0.30.
Oct 20 13:28:55 localhost kernel: [17179605.428000] ip_conntrack version 2.4 (4095 buckets, 32760 max) - 232 bytes per conntrack
Oct 20 13:28:56 localhost kernel: [17179607.172000] Bluetooth: Core ver 2.8
Oct 20 13:28:56 localhost kernel: [17179607.172000] NET: Registered protocol family 31
Oct 20 13:28:56 localhost kernel: [17179607.172000] Bluetooth: HCI device and connection manager initialized
Oct 20 13:28:56 localhost kernel: [17179607.172000] Bluetooth: HCI socket layer initialized
Oct 20 13:28:56 localhost kernel: [17179607.200000] Bluetooth: L2CAP ver 2.8
Oct 20 13:28:56 localhost kernel: [17179607.200000] Bluetooth: L2CAP socket layer initialized
Oct 20 13:28:56 localhost kernel: [17179607.200000] Bluetooth: RFCOMM socket layer initialized
Oct 20 13:28:56 localhost kernel: [17179607.200000] Bluetooth: RFCOMM TTY layer initialized
Oct 20 13:28:56 localhost kernel: [17179607.200000] Bluetooth: RFCOMM ver 1.7
Oct 20 13:29:00 localhost gconfd (fhiernaux-5145): démarrage (version 2.14.0), pid 5145 utilisateur « fhiernaux »
Oct 20 13:29:00 localhost gconfd (fhiernaux-5145): Adresse « xml:readonly:/etc/gconf/gconf.xml.mandatory » résolue vers une source de configuration en lecture seule à la position 0
Oct 20 13:29:00 localhost gconfd (fhiernaux-5145): Adresse « xml:readwrite:/home/fhiernaux/.gconf » résolue vers une source de configuration accessible en écriture à la position 1
Oct 20 13:29:00 localhost gconfd (fhiernaux-5145): Adresse « xml:readonly:/etc/gconf/gconf.xml.defaults » résolue vers une source de configuration en lecture seule à la position 2
Oct 20 13:29:00 localhost gconfd (fhiernaux-5145): Adresse « xml:readonly:/var/lib/gconf/debian.defaults » résolue vers une source de configuration en lecture seule à la position 3
Oct 20 13:29:00 localhost gconfd (fhiernaux-5145): Adresse « xml:readonly:/var/lib/gconf/defaults » résolue vers une source de configuration en lecture seule à la position 4
Oct 20 13:29:05 localhost gconfd (fhiernaux-5145): Adresse « xml:readwrite:/home/fhiernaux/.gconf » résolue vers une source de configuration accessible en écriture à la position 0
Oct 20 13:29:29 localhost kernel: [17179639.888000] pwc Failed to restore power to the camera! (-32)
Oct 20 13:29:29 localhost kernel: [17179639.888000] pwc Failed to set LED on/off time.
```

---

### Post by metalheart on 2006-10-20
Delete /tmp/gconfd-%USERNAME/lock directory and try to run Evolution again and also if shutdown works.

---

