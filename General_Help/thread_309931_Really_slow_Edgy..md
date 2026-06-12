---
title: "Really slow Edgy."
date: 2006-11-30
forum: General Help
---

### Post by Eddy Dean on 2006-11-30
Hello,

I have been using Ubuntu for several months now and I pretty much know my way around now. One thing that just kept bugging me was that it was slow. Really slow.
I did some tests, and I got the following results:
Booting to login screen: 67 seconds
Loading FireFox: 13 seconds (!!!)
Logging in and loading desktop: 77 seconds.

I thought this 1,67GHz PC could do better, so I installed Windows on dual-boot. Booting up was just over half a minute, and FireFox would load in less then 3 seconds.

I started googling about a solution and did all "speed up Linux" tutorials. DMA is enabled, I installed XFCE. I removed unneccesary files. I installed the newest driver of my graphics card. Nothing of this really helped.

My system specs:
AMD Athlon XP 1600+
GeForce4 MX420
512MB SD RAM
80GB Seagate HD, 7200RPM

Is that really not enough to make Ubuntu run smoothly?

I'd like to know if anyone else has these problems, and what they did about it.


Thanks in advance,
Eddy Dean

---

### Post by xopher on 2006-11-30
Perhaps you still have some files left behind that are slowing you down. You could for instance try resetting the firefox settings completely. ```
 mv ~/.mozilla .mozilla-backup 
```

And have a look at BUM (Boot up manager), with it you can disable unneeded boot processes easily. Eg. why start CUPS if you don't have a printer?

Hope this helps - that system should be more than adequate to run Ubuntu IMO, and with xfce it should be blazing fast.

---

### Post by Eddy Dean on 2006-11-30
Well, thanks for your help, but it's not just firefox that's slow. Opening a terminal window takes 16 seconds, loading Amarok takes 75 seconds.

I refuse to believe that this really is the best I can get from Linux. I reinstalled Ubuntu several times and the problem is always the same.

I tested my install CD for errors but it seemed all fine.

The kernel version I'm using is 2.6.17-10-386, which should be the newest kernel for i386 architecture.

The speed increase I get by XFCE is almost non-existant, I barely notice it.


Greetz,
Arno

---

### Post by reclusivemonkey on 2006-11-30
> **Eddy Dean said:**
> Well, thanks for your help, but it's not just firefox that's slow. Opening a terminal window takes 16 seconds, loading Amarok takes 75 seconds.

I refuse to believe that this really is the best I can get from Linux. I reinstalled Ubuntu several times and the problem is always the same.

I tested my install CD for errors but it seemed all fine.

The kernel version I'm using is 2.6.17-10-386, which should be the newest kernel for i386 architecture.

The speed increase I get by XFCE is almost non-existant, I barely notice it.


Ouch. Something isn't right. I have an AthlonXP 1700 (overclocked to 2100) and 512Mb DDR with a 7200 rpm HD and NVIDIA FX5200 so I have a very similar spec to you. Gnome-Terminal opens almost instantaneously, I haven't measured boot time as I rarely turn my PC off and Firefox loads in about 3/4 seconds. It could be your SD ram, but that shouldn't really be that much slower. Is something eating your RAM??? Have you taken a look at top to see what is going on with your processes. From the spec you have told me things really shouldn't be running that slow. Do you have beryl installed?

---

### Post by wesley_of_course on 2006-11-30
I have a very similar problem also. After looking in /var/log/message I noticed low memory was 767MB available but 0MB HIGHMEM available ! What up with that ?  It takes firfox,Thunderbird ,Rythum Box or just about anything forever to load . How to enable HIGHMEM ?  Here's the log , can't burn cd's either , DMA ? Hope this helps and is in the right forum , Thanks in advance !

   Nov 26 09:48:01 Ratdog syslogd 1.4.1#17ubuntu7: restart.
Nov 26 10:08:01 Ratdog -- MARK --
Nov 26 10:23:21 Ratdog gconfd (wesley-4899): Exiting
Nov 26 10:23:22 Ratdog gconfd (wesley-6816): starting (version 2.14.0), pid 6816 user 'wesley'
Nov 26 10:23:22 Ratdog gconfd (wesley-6816): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov 26 10:23:22 Ratdog gconfd (wesley-6816): Resolved address "xml:readwrite:/home/wesley/.gconf" to a writable configuration source at position 1
Nov 26 10:23:22 Ratdog gconfd (wesley-6816): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 26 10:23:22 Ratdog gconfd (wesley-6816): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov 26 10:23:22 Ratdog gconfd (wesley-6816): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov 26 10:23:23 Ratdog shutdown[4388]: shutting down for system halt
Nov 26 10:23:26 Ratdog kernel: [17182341.164000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov 26 10:23:26 Ratdog kernel: [17182341.164000] apm: disabled on user request.
Nov 26 10:23:33 Ratdog kernel: Kernel logging (proc) stopped.
Nov 26 10:23:33 Ratdog kernel: Kernel log daemon terminating.
Nov 26 10:23:34 Ratdog exiting on signal 15
Nov 26 18:25:17 Ratdog syslogd 1.4.1#17ubuntu7: restart.
Nov 26 18:25:17 Ratdog kernel: Inspecting /boot/System.map-2.6.15-27-386
Nov 26 18:25:17 Ratdog kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Nov 26 18:25:17 Ratdog kernel: Symbols match kernel version 2.6.15.
Nov 26 18:25:17 Ratdog kernel: No module symbols loaded - kernel modules not enabled. 
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] BIOS-provided physical RAM map:
Nov 26 18:25:17 Ratdog kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] 0MB HIGHMEM available.
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] 767MB LOWMEM available.
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] found SMP MP-table at 000f5bc0
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] DMI 2.2 present.
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x408
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Processor #0 15:1 APIC version 20
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Built 1 zonelists
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Kernel command line: root=/dev/hdb3 ro quiet splash
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Initializing CPU#0
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Detected 1615.262 MHz processor.
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Using pmtmr for high-res timesource
Nov 26 18:25:17 Ratdog kernel: [17179569.184000] Console: colour VGA+ 80x25
Nov 26 18:25:17 Ratdog kernel: [17179573.380000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 26 18:25:17 Ratdog kernel: [17179573.380000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 26 18:25:17 Ratdog kernel: [17179573.420000] Memory: 768820k/786368k available (1976k kernel code, 16888k reserved, 606k data, 288k init, 0k highmem)
Nov 26 18:25:17 Ratdog kernel: [17179573.420000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] Calibrating delay using timer specific routine.. 3233.80 BogoMIPS (lpj=6467600)
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] Security Framework v1.0.0 initialized
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] SELinux:  Disabled at boot.
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] Mount-cache hash table entries: 512
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] CPU: L2 cache: 256K
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] mtrr: v2.0 (20020519)
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] CPU: Intel(R) Pentium(R) 4 CPU 1.60GHz stepping 02
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] Enabling fast FPU save and restore... done.
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] Enabling unmasked SIMD FPU exception support... done.
Nov 26 18:25:17 Ratdog kernel: [17179573.500000] Checking 'hlt' instruction... OK.
Nov 26 18:25:17 Ratdog kernel: [17179573.516000] checking if image is initramfs... it is
Nov 26 18:25:17 Ratdog kernel: [17179574.408000] Freeing initrd memory: 6617k freed
Nov 26 18:25:17 Ratdog kernel: [17179574.436000] ACPI: Looking for DSDT ... not found!
Nov 26 18:25:17 Ratdog kernel: [17179574.560000] ENABLING IO-APIC IRQs
Nov 26 18:25:17 Ratdog kernel: [17179574.560000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 26 18:25:17 Ratdog kernel: [17179574.704000] NET: Registered protocol family 16
Nov 26 18:25:17 Ratdog kernel: [17179574.704000] EISA bus registered
Nov 26 18:25:17 Ratdog kernel: [17179574.704000] ACPI: bus type pci registered
Nov 26 18:25:17 Ratdog kernel: [17179574.716000] PCI: PCI BIOS revision 2.10 entry at 0xfb0d0, last bus=2
Nov 26 18:25:17 Ratdog kernel: [17179574.716000] PCI: Using configuration type 1
Nov 26 18:25:17 Ratdog kernel: [17179574.716000] ACPI: Subsystem revision 20051216
Nov 26 18:25:17 Ratdog kernel: [17179574.728000] ACPI: Interpreter enabled
Nov 26 18:25:17 Ratdog kernel: [17179574.728000] ACPI: Using IOAPIC for interrupt routing
Nov 26 18:25:17 Ratdog kernel: [17179574.728000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 26 18:25:17 Ratdog kernel: [17179574.732000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Nov 26 18:25:17 Ratdog kernel: [17179574.732000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
Nov 26 18:25:17 Ratdog kernel: [17179574.732000] PCI: Transparent bridge - 0000:00:1e.0
Nov 26 18:25:17 Ratdog kernel: [17179574.760000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 26 18:25:17 Ratdog kernel: [17179574.760000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 26 18:25:17 Ratdog kernel: [17179574.764000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 26 18:25:17 Ratdog kernel: [17179574.764000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 26 18:25:17 Ratdog kernel: [17179574.764000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 26 18:25:17 Ratdog kernel: [17179574.764000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 26 18:25:17 Ratdog kernel: [17179574.764000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 26 18:25:17 Ratdog kernel: [17179574.764000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 26 18:25:17 Ratdog kernel: [17179574.768000] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 26 18:25:17 Ratdog kernel: [17179574.768000] pnp: PnP ACPI init
Nov 26 18:25:17 Ratdog kernel: [17179574.776000] pnp: PnP ACPI: found 12 devices
Nov 26 18:25:17 Ratdog kernel: [17179574.776000] PnPBIOS: Disabled by ACPI PNP
Nov 26 18:25:17 Ratdog kernel: [17179574.776000] PCI: Using ACPI for IRQ routing
Nov 26 18:25:17 Ratdog kernel: [17179574.776000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] PCI: Bridge: 0000:00:01.0
Nov 26 18:25:17 Ratdog kernel: [17179574.796000]   IO window: disabled.
Nov 26 18:25:17 Ratdog kernel: [17179574.796000]   MEM window: ec000000-edffffff
Nov 26 18:25:17 Ratdog kernel: [17179574.796000]   PREFETCH window: e0000000-e7ffffff
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] PCI: Bridge: 0000:00:1e.0
Nov 26 18:25:17 Ratdog kernel: [17179574.796000]   IO window: c000-cfff
Nov 26 18:25:17 Ratdog kernel: [17179574.796000]   MEM window: ee000000-efffffff
Nov 26 18:25:17 Ratdog kernel: [17179574.796000]   PREFETCH window: 40000000-400fffff
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] audit: initializing netlink socket (disabled)
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] audit(1164565489.796:1): initialized
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] VFS: Disk quotas dquot_6.5.1
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] Initializing Cryptographic API
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] io scheduler noop registered
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] io scheduler anticipatory registered
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] io scheduler deadline registered
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] io scheduler cfq registered
Nov 26 18:25:17 Ratdog kernel: [17179574.796000] isapnp: Scanning for PnP cards...
Nov 26 18:25:17 Ratdog kernel: [17179575.152000] isapnp: No Plug & Play device found
Nov 26 18:25:17 Ratdog kernel: [17179575.180000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov 26 18:25:17 Ratdog kernel: [17179575.184000] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 26 18:25:17 Ratdog kernel: [17179575.184000] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 26 18:25:17 Ratdog kernel: [17179575.184000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Nov 26 18:25:17 Ratdog kernel: [17179575.184000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 26 18:25:17 Ratdog kernel: [17179575.184000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 26 18:25:17 Ratdog kernel: [17179575.188000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 26 18:25:17 Ratdog kernel: [17179575.188000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 26 18:25:17 Ratdog kernel: [17179575.188000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 26 18:25:17 Ratdog kernel: [17179575.188000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 26 18:25:17 Ratdog kernel: [17179575.188000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 26 18:25:17 Ratdog kernel: [17179575.188000] mice: PS/2 mouse device common for all mice
Nov 26 18:25:17 Ratdog kernel: [17179575.192000] EISA: Probing bus 0 at eisa.0
Nov 26 18:25:17 Ratdog kernel: [17179575.192000] EISA: Detected 0 cards.
Nov 26 18:25:17 Ratdog kernel: [17179575.192000] NET: Registered protocol family 2
Nov 26 18:25:17 Ratdog kernel: [17179575.216000] input: AT Translated Set 2 keyboard as /class/input/input0
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] TCP: Hash tables configured (established 131072 bind 65536)
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] TCP reno registered
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] TCP bic registered
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] NET: Registered protocol family 1
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] NET: Registered protocol family 8
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] NET: Registered protocol family 20
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] Using IPI Shortcut mode
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] ACPI wakeup devices: 
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] SLPB PCI0 HUB0 USB0 USB1 MODM UAR1 UAR2 
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] ACPI: (supports S0 S1 S5)
Nov 26 18:25:17 Ratdog kernel: [17179575.228000] Freeing unused kernel memory: 288k freed
Nov 26 18:25:17 Ratdog kernel: [17179575.316000] vga16fb: mapped to 0xc00a0000
Nov 26 18:25:17 Ratdog kernel: [17179575.468000] Console: switching to colour frame buffer device 80x25
Nov 26 18:25:17 Ratdog kernel: [17179575.468000] fb0: VGA16 VGA frame buffer device
Nov 26 18:25:17 Ratdog kernel: [17179576.612000] Capability LSM initialized
Nov 26 18:25:17 Ratdog kernel: [17179576.672000] ACPI: Fan [FAN] (on)
Nov 26 18:25:17 Ratdog kernel: [17179576.680000] ACPI: Processor [CPU0] (supports 2 throttling states)
Nov 26 18:25:17 Ratdog kernel: [17179576.680000] ACPI: Thermal Zone [THRM] (20 C)
Nov 26 18:25:17 Ratdog kernel: [17179577.840000] ICH2: IDE controller at PCI slot 0000:00:1f.1
Nov 26 18:25:17 Ratdog kernel: [17179577.840000] ICH2: chipset revision 18
Nov 26 18:25:17 Ratdog kernel: [17179577.840000] ICH2: not 100%% native mode: will probe irqs later
Nov 26 18:25:17 Ratdog kernel: [17179577.840000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Nov 26 18:25:17 Ratdog kernel: [17179577.840000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Nov 26 18:25:17 Ratdog kernel: [17179578.128000] hda: WDC WD800BB-00CAA1, ATA DISK drive
Nov 26 18:25:17 Ratdog kernel: [17179578.408000] hdb: Maxtor 6B200P0, ATA DISK drive
Nov 26 18:25:17 Ratdog kernel: [17179578.464000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov 26 18:25:17 Ratdog kernel: [17179579.240000] hdc: MSI CD-RW MS-8348, ATAPI CD/DVD-ROM drive
Nov 26 18:25:17 Ratdog kernel: [17179580.024000] hdd: 56X CD-ROM, ATAPI CD/DVD-ROM drive
Nov 26 18:25:17 Ratdog kernel: [17179580.080000] ide1 at 0x170-0x177,0x376 on irq 15
Nov 26 18:25:17 Ratdog kernel: [17179580.092000] hda: max request size: 128KiB
Nov 26 18:25:17 Ratdog kernel: [17179580.116000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
Nov 26 18:25:17 Ratdog kernel: [17179580.116000] hda: cache flushes not supported
Nov 26 18:25:17 Ratdog kernel: [17179580.116000]  hda: hda1
Nov 26 18:25:17 Ratdog kernel: [17179580.136000] hdb: max request size: 1024KiB
Nov 26 18:25:17 Ratdog kernel: [17179580.136000] hdb: 398297088 sectors (203928 MB) w/8192KiB Cache, CHS=24792/255/63, UDMA(33)
Nov 26 18:25:17 Ratdog kernel: [17179580.140000] hdb: cache flushes supported
Nov 26 18:25:17 Ratdog kernel: [17179580.140000]  hdb: hdb1 hdb2 < hdb5 hdb6 hdb7 > hdb3
Nov 26 18:25:17 Ratdog kernel: [17179580.200000] hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Nov 26 18:25:17 Ratdog kernel: [17179580.200000] Uniform CD-ROM driver Revision: 3.20
Nov 26 18:25:17 Ratdog kernel: [17179580.204000] hdd: ATAPI 52X CD-ROM drive, 128kB Cache, UDMA(33)
Nov 26 18:25:17 Ratdog kernel: [17179580.820000] usbcore: registered new driver usbfs
Nov 26 18:25:17 Ratdog kernel: [17179580.820000] usbcore: registered new driver hub
Nov 26 18:25:17 Ratdog kernel: [17179580.824000] USB Universal Host Controller Interface driver v2.3
Nov 26 18:25:17 Ratdog kernel: [17179580.824000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 169
Nov 26 18:25:17 Ratdog kernel: [17179580.824000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
Nov 26 18:25:17 Ratdog kernel: [17179580.824000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
Nov 26 18:25:17 Ratdog kernel: [17179580.824000] uhci_hcd 0000:00:1f.2: irq 169, io base 0x0000d000
Nov 26 18:25:17 Ratdog kernel: [17179580.824000] hub 1-0:1.0: USB hub found
Nov 26 18:25:17 Ratdog kernel: [17179580.824000] hub 1-0:1.0: 2 ports detected
Nov 26 18:25:17 Ratdog kernel: [17179580.928000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 177
Nov 26 18:25:17 Ratdog kernel: [17179580.928000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
Nov 26 18:25:17 Ratdog kernel: [17179580.928000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
Nov 26 18:25:17 Ratdog kernel: [17179580.928000] uhci_hcd 0000:00:1f.4: irq 177, io base 0x0000d800
Nov 26 18:25:17 Ratdog kernel: [17179580.928000] hub 2-0:1.0: USB hub found
Nov 26 18:25:17 Ratdog kernel: [17179580.928000] hub 2-0:1.0: 2 ports detected
Nov 26 18:25:17 Ratdog kernel: [17179581.164000] Attempting manual resume
Nov 26 18:25:17 Ratdog kernel: [17179581.188000] kjournald starting.  Commit interval 5 seconds
Nov 26 18:25:17 Ratdog kernel: [17179581.188000] EXT3-fs: mounted filesystem with ordered data mode.
Nov 26 18:25:17 Ratdog kernel: [17179592.484000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 26 18:25:17 Ratdog kernel: [17179592.492000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 26 18:25:17 Ratdog kernel: [17179592.952000] input: PC Speaker as /class/input/input1
Nov 26 18:25:17 Ratdog kernel: [17179592.956000] Linux agpgart interface v0.101 (c) Dave Jones
Nov 26 18:25:17 Ratdog kernel: [17179592.964000] agpgart: Detected an Intel i845 Chipset.
Nov 26 18:25:17 Ratdog kernel: [17179592.968000] agpgart: AGP aperture is 64M @ 0xe8000000
Nov 26 18:25:17 Ratdog kernel: [17179593.200000] nvidia: module license 'NVIDIA' taints kernel.
Nov 26 18:25:17 Ratdog kernel: [17179593.212000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
Nov 26 18:25:17 Ratdog kernel: [17179593.212000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Nov 26 18:25:17 Ratdog kernel: [17179593.228000] gameport: EMU10K1 is pci0000:02:03.1/gameport0, io 0xc800, speed 917kHz
Nov 26 18:25:17 Ratdog kernel: [17179593.236000] Linux Tulip driver version 1.1.13 (December 15, 2004)
Nov 26 18:25:17 Ratdog kernel: [17179593.236000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 193
Nov 26 18:25:17 Ratdog kernel: [17179593.236000] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
Nov 26 18:25:17 Ratdog kernel: [17179593.244000] eth0: ADMtek Comet rev 17 at 0001c000, 00:04:5A:88:DA:92, IRQ 193.
Nov 26 18:25:17 Ratdog kernel: [17179593.252000] Real Time Clock Driver v1.12
Nov 26 18:25:17 Ratdog kernel: [17179593.672000] input: ImExPS/2 Logitech Wheel Mouse as /class/input/input2
Nov 26 18:25:17 Ratdog kernel: [17179594.064000] parport: PnPBIOS parport detected.
Nov 26 18:25:17 Ratdog kernel: [17179594.064000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Nov 26 18:25:17 Ratdog kernel: [17179594.096000] FDC 0 is a post-1991 82077
Nov 26 18:25:17 Ratdog kernel: [17179594.288000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 22 (level, low) -> IRQ 201
Nov 26 18:25:17 Ratdog kernel: [17179594.916000] ts: Compaq touchscreen protocol output
Nov 26 18:25:17 Ratdog kernel: [17179595.696000] NET: Registered protocol family 17
Nov 26 18:25:17 Ratdog kernel: [17179595.896000] lp0: using parport0 (interrupt-driven).
Nov 26 18:25:17 Ratdog kernel: [17179595.996000] Adding 2273156k swap on /dev/hdb7.  Priority:-1 extents:1 across:2273156k
Nov 26 18:25:17 Ratdog kernel: [17179596.172000] EXT3 FS on hdb3, internal journal
Nov 26 18:25:17 Ratdog kernel: [17179596.444000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Nov 26 18:25:17 Ratdog kernel: [17179596.444000] md: bitmap version 4.39
Nov 26 18:25:17 Ratdog kernel: [17179597.560000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
Nov 26 18:25:17 Ratdog kernel: [17179597.592000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Nov 26 18:25:17 Ratdog kernel: [17179597.960000] cdrom: open failed.
Nov 26 18:25:17 Ratdog kernel: [17179598.624000] cdrom: open failed.
Nov 26 18:25:17 Ratdog kernel: [17179598.628000] cdrom: open failed.
Nov 26 18:25:17 Ratdog kernel: [17179598.928000] NET: Registered protocol family 10
Nov 26 18:25:17 Ratdog kernel: [17179598.928000] lo: Disabled Privacy Extensions
Nov 26 18:25:17 Ratdog kernel: [17179598.928000] IPv6 over IPv4 tunneling driver
Nov 26 18:25:17 Ratdog kernel: [17179605.812000] ACPI: Power Button (FF) [PWRF]
Nov 26 18:25:17 Ratdog kernel: [17179605.812000] ACPI: Power Button (CM) [PWRB]
Nov 26 18:25:17 Ratdog kernel: [17179605.812000] ACPI: Sleep Button (CM) [SLPB]
Nov 26 18:25:17 Ratdog kernel: [17179606.032000] pcc_acpi: loading...
Nov 26 18:25:20 Ratdog hpiod: 0.9.7 accepting connections at 37423... 
Nov 26 18:25:22 Ratdog kernel: [17179612.492000] ppdev: user-space parallel port driver
Nov 26 18:25:22 Ratdog kernel: [17179612.756000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov 26 18:25:22 Ratdog kernel: [17179612.756000] apm: overridden by ACPI.
Nov 26 18:25:28 Ratdog kernel: [17179617.972000] Bluetooth: Core ver 2.8
Nov 26 18:25:28 Ratdog kernel: [17179617.972000] NET: Registered protocol family 31
Nov 26 18:25:28 Ratdog kernel: [17179617.972000] Bluetooth: HCI device and connection manager initialized
Nov 26 18:25:28 Ratdog kernel: [17179617.972000] Bluetooth: HCI socket layer initialized
Nov 26 18:25:28 Ratdog kernel: [17179617.992000] Bluetooth: L2CAP ver 2.8
Nov 26 18:25:28 Ratdog kernel: [17179617.992000] Bluetooth: L2CAP socket layer initialized
Nov 26 18:25:28 Ratdog kernel: [17179618.016000] Bluetooth: RFCOMM socket layer initialized
Nov 26 18:25:28 Ratdog kernel: [17179618.016000] Bluetooth: RFCOMM TTY layer initialized
Nov 26 18:25:28 Ratdog kernel: [17179618.016000] Bluetooth: RFCOMM ver 1.7
Nov 26 18:25:40 Ratdog gconfd (wesley-4893): starting (version 2.14.0), pid 4893 user 'wesley'
Nov 26 18:25:41 Ratdog gconfd (wesley-4893): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov 26 18:25:41 Ratdog gconfd (wesley-4893): Resolved address "xml:readwrite:/home/wesley/.gconf" to a writable configuration source at position 1
Nov 26 18:25:41 Ratdog gconfd (wesley-4893): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 26 18:25:41 Ratdog gconfd (wesley-4893): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov 26 18:25:41 Ratdog gconfd (wesley-4893): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov 26 18:25:45 Ratdog gconfd (wesley-4893): Resolved address "xml:readwrite:/home/wesley/.gconf" to a writable configuration source at position 0
Nov 26 18:45:17 Ratdog -- MARK --
Nov 26 19:00:27 Ratdog gconfd (wesley-4893): Exiting
Nov 26 19:00:27 Ratdog gconfd (wesley-5927): starting (version 2.14.0), pid 5927 user 'wesley'
Nov 26 19:00:27 Ratdog gconfd (wesley-5927): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov 26 19:00:27 Ratdog gconfd (wesley-5927): Resolved address "xml:readwrite:/home/wesley/.gconf" to a writable configuration source at position 1
Nov 26 19:00:27 Ratdog gconfd (wesley-5927): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 26 19:00:27 Ratdog gconfd (wesley-5927): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov 26 19:00:27 Ratdog gconfd (wesley-5927): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov 26 19:00:29 Ratdog shutdown[4386]: shutting down for system halt
Nov 26 19:00:31 Ratdog kernel: [17181721.688000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov 26 19:00:31 Ratdog kernel: [17181721.688000] apm: disabled on user request.
Nov 26 19:00:39 Ratdog kernel: Kernel logging (proc) stopped.
Nov 26 19:00:39 Ratdog kernel: Kernel log daemon terminating.
Nov 26 19:00:40 Ratdog exiting on signal 15
Nov 26 22:21:22 Ratdog syslogd 1.4.1#17ubuntu7: restart.
Nov 26 22:21:22 Ratdog kernel: Inspecting /boot/System.map-2.6.15-27-386
Nov 26 22:21:22 Ratdog kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Nov 26 22:21:22 Ratdog kernel: Symbols match kernel version 2.6.15.
Nov 26 22:21:22 Ratdog kernel: No module symbols loaded - kernel modules not enabled. 
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] BIOS-provided physical RAM map:
Nov 26 22:21:22 Ratdog kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] 0MB HIGHMEM available.
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] 767MB LOWMEM available.
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] found SMP MP-table at 000f5bc0
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] DMI 2.2 present.
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x408
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Processor #0 15:1 APIC version 20
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Built 1 zonelists
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Kernel command line: root=/dev/hdb3 ro quiet splash
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Initializing CPU#0
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Detected 1615.269 MHz processor.
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Using pmtmr for high-res timesource
Nov 26 22:21:22 Ratdog kernel: [17179569.184000] Console: colour VGA+ 80x25
Nov 26 22:21:22 Ratdog kernel: [17179572.816000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 26 22:21:22 Ratdog kernel: [17179572.820000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 26 22:21:22 Ratdog kernel: [17179572.856000] Memory: 768820k/786368k available (1976k kernel code, 16888k reserved, 606k data, 288k init, 0k highmem)
Nov 26 22:21:22 Ratdog kernel: [17179572.856000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] Calibrating delay using timer specific routine.. 3233.76 BogoMIPS (lpj=6467524)
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] Security Framework v1.0.0 initialized
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] SELinux:  Disabled at boot.
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] Mount-cache hash table entries: 512
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] CPU: L2 cache: 256K
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] mtrr: v2.0 (20020519)
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] CPU: Intel(R) Pentium(R) 4 CPU 1.60GHz stepping 02
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] Enabling fast FPU save and restore... done.
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] Enabling unmasked SIMD FPU exception support... done.
Nov 26 22:21:22 Ratdog kernel: [17179572.936000] Checking 'hlt' instruction... OK.
Nov 26 22:21:22 Ratdog kernel: [17179572.952000] checking if image is initramfs... it is
Nov 26 22:21:22 Ratdog kernel: [17179573.844000] Freeing initrd memory: 6617k freed
Nov 26 22:21:22 Ratdog kernel: [17179573.868000] ACPI: Looking for DSDT ... not found!
Nov 26 22:21:22 Ratdog kernel: [17179573.984000] ENABLING IO-APIC IRQs
Nov 26 22:21:22 Ratdog kernel: [17179573.988000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 26 22:21:22 Ratdog kernel: [17179574.128000] NET: Registered protocol family 16
Nov 26 22:21:22 Ratdog kernel: [17179574.128000] EISA bus registered
Nov 26 22:21:22 Ratdog kernel: [17179574.128000] ACPI: bus type pci registered
Nov 26 22:21:22 Ratdog kernel: [17179574.140000] PCI: PCI BIOS revision 2.10 entry at 0xfb0d0, last bus=2
Nov 26 22:21:22 Ratdog kernel: [17179574.140000] PCI: Using configuration type 1
Nov 26 22:21:22 Ratdog kernel: [17179574.140000] ACPI: Subsystem revision 20051216
Nov 26 22:21:22 Ratdog kernel: [17179574.152000] ACPI: Interpreter enabled
Nov 26 22:21:22 Ratdog kernel: [17179574.152000] ACPI: Using IOAPIC for interrupt routing
Nov 26 22:21:22 Ratdog kernel: [17179574.152000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 26 22:21:22 Ratdog kernel: [17179574.156000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Nov 26 22:21:22 Ratdog kernel: [17179574.156000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
Nov 26 22:21:22 Ratdog kernel: [17179574.156000] PCI: Transparent bridge - 0000:00:1e.0
Nov 26 22:21:22 Ratdog kernel: [17179574.184000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 26 22:21:22 Ratdog kernel: [17179574.184000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 26 22:21:22 Ratdog kernel: [17179574.184000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 26 22:21:22 Ratdog kernel: [17179574.188000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 26 22:21:22 Ratdog kernel: [17179574.188000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 26 22:21:22 Ratdog kernel: [17179574.188000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 26 22:21:22 Ratdog kernel: [17179574.188000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 26 22:21:22 Ratdog kernel: [17179574.188000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 26 22:21:22 Ratdog kernel: [17179574.192000] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 26 22:21:22 Ratdog kernel: [17179574.192000] pnp: PnP ACPI init
Nov 26 22:21:22 Ratdog kernel: [17179574.200000] pnp: PnP ACPI: found 12 devices
Nov 26 22:21:22 Ratdog kernel: [17179574.200000] PnPBIOS: Disabled by ACPI PNP
Nov 26 22:21:22 Ratdog kernel: [17179574.200000] PCI: Using ACPI for IRQ routing
Nov 26 22:21:22 Ratdog kernel: [17179574.200000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 26 22:21:22 Ratdog kernel: [17179574.220000] PCI: Bridge: 0000:00:01.0
Nov 26 22:21:22 Ratdog kernel: [17179574.220000]   IO window: disabled.
Nov 26 22:21:22 Ratdog kernel: [17179574.220000]   MEM window: ec000000-edffffff
Nov 26 22:21:22 Ratdog kernel: [17179574.220000]   PREFETCH window: e0000000-e7ffffff
Nov 26 22:21:22 Ratdog kernel: [17179574.220000] PCI:

---

### Post by coolclassic on 2006-11-30
Check dma settings

hdparm  /dev/hda

---

### Post by wesley_of_course on 2006-11-30
/dev/hdb:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 24792/255/63, sectors = 398297088, start = 0
](*,)

---

### Post by Eddy Dean on 2006-12-01
/dev/hdb:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156301488, start = 0

/dev/hdb:
 Timing buffered disk reads:  118 MB in  3.03 seconds =  38.96 MB/sec

That's hdb, the 80GB HD linux is installed on. It is the "slave" HD.

Hope this helps a bit...
Eddy Dean

---

### Post by coolclassic on 2006-12-01
wesley_of_course you may benefit by adjusting your settings have a look here for info.

[http://linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html)

---

### Post by coolclassic on 2006-12-01
wesley_of_course-run top and see what processes are running, is there any programme/process hogging ram or cpu time?

---

### Post by Eddy Dean on 2006-12-01
Well, the problem remains. I don't really care about this boot time, but having to wait 15 seconds to load a terminal screen really scares me.
Do note that ALL programs take a while to load, there isn't a single program that just loads instantly, except command-line programs.

Greetz,
Eddy Dean

---

### Post by coolclassic on 2006-12-01
If the problems remain-what have you done to try and solve problem.  

By posting the results from top might give some indication what is wrong if not then it rules other problems out.

Are you using the nvidia drivers?

---

### Post by wesley_of_course on 2006-12-01
Non that I could see ?

---

### Post by wesley_of_course on 2006-12-01
[http://linuxdevcenter.com/pub/a/linu...29/hdparm.html](http://linuxdevcenter.com/pub/a/linu...29/hdparm.html)

Great site and it worked but , how to save ?  couldn't find file /etc/rc.d/
/dev/hdb:
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 24792/255/63, sectors = 398297088, start = 0

/dev/hdb:
 Timing cached reads:   872 MB in  2.00 seconds = 435.97 MB/sec
 Timing buffered disk reads:   76 MB in  3.07 seconds =  24.74 MB/sec

   But like I said to save and | or how ?  And where ? Thanks

     /dev/hda/  is Windows 2000

---

### Post by Eddy Dean on 2006-12-02
Okay then, some more data

```

top - 09:27:54 up 13 min,  2 users,  load average: 0.14, 0.26, 0.17
Tasks:  96 total,   1 running,  94 sleeping,   0 stopped,   1 zombie
Cpu(s):  9.3%us,  0.8%sy,  0.0%ni, 89.3%id,  0.0%wa,  0.0%hi,  0.6%si,  0.0%st
Mem:    516056k total,   508900k used,     7156k free,    77120k buffers
Swap:  1510068k total,        0k used,  1510068k free,   253536k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                           
 4891 arno      15   0 92508  14m 9184 S  4.7  2.9   0:01.25 gnome-terminal                                                                    
 4118 root      15   0 40424  27m 7172 S  3.1  5.4   0:22.08 Xorg                                                                              
 4841 arno      15   0  137m  42m  26m S  2.1  8.5   0:10.88 amarokapp                                                                         
 4576 arno      15   0 14948 7128 5240 S  0.1  1.4   0:00.35 xfce4-systemloa                                                                   
 4914 root      16   0  2248 1132  844 R  0.1  0.2   0:00.04 top                                                                               
    1 root      16   0  1632  536  448 S  0.0  0.1   0:01.18 init                                                                              
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                                       
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                        
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0                                                                          
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper                                                                           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                                                           
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0                                                                         
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                            
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                      
   79 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                           
  112 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                           
  113 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                           
  114 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                           
  115 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                             
 1798 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                             
 1878 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kjournald                                                                         
 1950 root      15   0  1600  548  468 S  0.0  0.1   0:00.02 logd                                                                              
 2098 root      13  -4  2612 1040  360 S  0.0  0.2   0:00.50 udevd                                                                             
 2855 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 shpchpd                                                                           
 2924 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                         
 3022 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd                                                                        
 3728 root      16   0  1596  504  432 S  0.0  0.1   0:00.00 getty                                                                             
 3729 root      16   0  1596  504  432 S  0.0  0.1   0:00.00 getty                                                                             
 3730 root      16   0  1596  504  432 S  0.0  0.1   0:00.00 getty                                                                             
 3731 root      16   0  1600  508  432 S  0.0  0.1   0:00.00 getty                                                                             
 3732 root      16   0  1596  500  432 S  0.0  0.1   0:00.00 getty                                                                             
 3733 root      16   0  1596  504  432 S  0.0  0.1   0:00.00 getty                                                                             
 3924 root      16   0  2204 1156  640 S  0.0  0.2   0:00.00 acpid                                                                             
 4032 root      16   0  1720  508  420 S  0.0  0.1   0:00.01 dd                                                                                
 4034 klog      16   0  2396 1276  384 S  0.0  0.2   0:00.06 klogd                                                                             
 4106 root      15   0 11880 1788 1268 S  0.0  0.3   0:00.00 gdm                                                                               
 4107 root      15   0 12236 2636 2044 S  0.0  0.5   0:00.02 gdm                                                                               
 4135 messageb  16   0  2172  840  636 S  0.0  0.2   0:00.01 dbus-daemon                                                                       
 4150 haldaemo  15   0  7084 5544 1640 S  0.0  1.1   0:02.33 hald                                                                              
 4151 root      20   0  2908 1040  880 S  0.0  0.2   0:00.01 hald-runner                                                                       
 4172 haldaemo  21   0  2024  808  692 S  0.0  0.2   0:00.00 hald-addon-acpi                                                                   
 4174 haldaemo  15   0  2024  808  692 S  0.0  0.2   0:00.01 hald-addon-keyb 
```

And hdparm:
```
/dev/hdb:
 Timing cached reads:   672 MB in  2.01 seconds = 334.17 MB/sec
 Timing buffered disk reads:   90 MB in  3.03 seconds =  29.72 MB/sec

/dev/hdb:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156301488, start = 0

```

Kernel: 2.6.17-10-386
Window manager: XFCE4

Another thing I notice is that if I load an application nothing happens for ~10 seconds, and then the CPU usage goes up and the program loads rather fast.

Hope this helped... Another thing I get is that if XFCE boots it says it can not find arno-desktop in /etc/hosts (or something like that), and that I might have to add it manually.


Greetz,
Eddy Dean

---

### Post by reclusivemonkey on 2006-12-02
> **Eddy Dean said:**
> 
Hope this helped... Another thing I get is that if XFCE boots it says it can not find arno-desktop in /etc/hosts (or something like that), and that I might have to add it manually.


Post /etc/hosts please and did you name your machine arno-desktop when you installed?

---

### Post by Eddy Dean on 2006-12-02
```
127.0.0.1 localhost
127.0.1.1 arno-desktop.MSHOME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

MSHOME is the network I'm connected to (Yup, my other PC is windows...)

Thanks for all replies so far,
Eddy Dean

---

### Post by wesley_of_course on 2006-12-02
Back again , I had forgot to include Top :
4516 root      15   0  105m  19m 8912 S  1.0  2.6   0:42.89 Xorg
 5325 wesley    15   0 73152  15m 9760 S  1.0  2.0   0:02.94 gnome-terminal 5345 wesley    16   0  2196 1104  864 R  0.3  0.1   0:00.23 top
    1 root      16   0  1568  532  460 S  0.0  0.1   0:01.49 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    6 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    7 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.11 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  113 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  114 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  116 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  115 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  704 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod

](*,)

---

### Post by reclusivemonkey on 2006-12-03
> **Eddy Dean said:**
> ```
127.0.0.1 localhost
127.0.1.1 arno-desktop.MSHOME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

MSHOME is the network I'm connected to (Yup, my other PC is windows...)

Thanks for all replies so far,
Eddy Dean

You should change this

```

127.0.1.1 arno-desktop.MSHOME

```

to your ip address of the machine. If you have a home network, you should specify ip addresses for all of your machines. Something like 192.168.1.* (where * is any number between 2-253). Keep arno-desktop, but lose the MSHOME for now. Are you using SAMBA by any chance?

---

### Post by Eddy Dean on 2006-12-04
I switched to Fedora to test if the problem was the same here. On gnome it is, but KDE seems to be a lot faster.
I will stick with Fedora for a while I think, but I'm still orienting and learning. I really enjoyed my time with Ubuntu, and wouldn't have switched if the speed was a bit more reasonable. On Fedora I can load FireFox within 2 seconds, and that's good enough for me.
Thanks a million for all the great help you gave me,

Greetz,
Eddy Dean

---

### Post by LucidTaZ on 2006-12-04
I'm having the same problem since today. Programs take 10-20 seconds to load.

What I did the last days:
I installed and used VMWare. Without problems I must add. Everything worked perfectly.

-2 days later-

I messed around with the wireless essids. Connected to various hotspots in my university and in the bus. Everything was still fast.

After a reboot the problem started and I can't get it away. I already tried disabling networking but no success...

Oh I played a lot of Geweled too, but I don't think that's the problem cause I always play it. :P

I didn't install software or used anything else than listen above.

My system: Acer Aspire 3613 WLMi laptop. 1 gig RAM, 1.5GHz cpu. Ubuntu 6.10 Edgy Eft. Intel videocard. Broadcom wireless card.

---

### Post by LucidTaZ on 2006-12-05
I discovered that the problem disappears when I pull the network cable out of my pc, and when I try to connect to an unexisting wifi network. Simply disabling wifi doesn't work. :|

Anyone that has an idea?

---

### Post by finferflu on 2006-12-06
Actually I've made some changes with hdparm, it looks slightly lighter, but still, firefox takes **17 seconds** to start up! It's *ridicolous*!! I've got a Pentium IV, 2.6 GHz and 512 Mb RAM, I expect it to be faster! And I've just switched to KDE from GNOME, since KDE is way faster...

---

### Post by Eddy Dean on 2006-12-11
Well, I'm back with ubuntu again, I somehow managed to kill my X server in fedora and was unable to repair it. I think I made a too big step going from Ubuntu to Fedora ;)

Anyway, Now I'm in a really, really fresh install of Dapper (Nothing new installed, but I did update).

And I think I'm onto something:
arno@arno-desktop:~$ uname -m
i686
arno@arno-desktop:~$ uname -r
2.6.15-27-386

The kernel is 386 while my PC is 686... I'm not really sure what these "numbers" (I believe they're called an "Arch"?) mean, but I remember that Fedora installed 586 and it was a lot faster; but fluxbox used some 386 components and was considerably slower then KDE!

I hope this info helps a bit. The "top" command displays nothing weird, and the harddisks are configured correctly.


Thanks in advance,
Arno


PS: Should I create an new thread for this or change the thread name? It's not really about Edgy anymore...

---

### Post by finferflu on 2006-12-11
well, with Edgy the kernel is just "generic", I'm not expert in kernel at all, but this is the output for the commands you have used:

```
$ uname -m
i686
$ uname -r
2.6.17-10-generic

```

---

