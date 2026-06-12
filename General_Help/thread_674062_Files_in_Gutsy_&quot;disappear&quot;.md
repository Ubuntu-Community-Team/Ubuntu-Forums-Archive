---
title: "Files in Gutsy &quot;disappear&quot;"
date: 2008-01-21
forum: General Help
---

### Post by Holonet on 2008-01-21
Sorry about the post description, I couldn't sum this up.

Anyway, I notice this most often when I've got my music folder open and am listening to mp3s (happens whether I use vlc or totem...though totem crashes if I try to seek too much...pff).  So I'll be listening one at a time, double-clicking whatever song...and everything will be fine for a while...sometimes for a few hours, others, it screws up within 15 minutes or so.  What happens is I'll try to click on another song, and low and behold, all of a sudden nothing happens.  The little music note icon turns to a blank white, and it doesn't play.  Then if I try to close and re-open the folder, or any folder, it says it's not accessible...or something like that.  Seems like a bug, but anyone know what's up with this?

I should also note this has happened to me while simply browsing files and not playing music...it's just that's most of the time when it happens.

---

### Post by cdenley on 2008-01-21
Could it be a hardware problem? You might want to check dmesg for any disk read errors.

---

### Post by Holonet on 2008-01-21
I suppose it's possible.  I have one 250 GB hard drive partitioned with a Windows installation as well, and as I become less dependent on Windows, I've moved stuff off that partition onto the Linux partition, and resized/moved to make the LInux one larger a few times.  However, I don't see why that would cause a problem.  gparted always checks for errors in the filesystem, and chkdsk has run over the ntfs.

Also, my apologies, I implied this, but didn't explicitly state it...if I reboot, it goes back to working, but no telling when it'll screw up again.

I'll set some time aside and run SpinRite on it and see if I get any problems.

---

### Post by cdenley on 2008-01-21
What is the output of the dmesg command after you experience the problem?

---

### Post by yeluapyeroc on 2008-01-21
I have the same problem. Happens once per day. When it happens i can't do anything but turn off the computer. The mouse still works, but nothing else will open or move. It fixes when i reset though

---

### Post by Holonet on 2008-01-22
Here is the dmesg output after it happens, as requested:

[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] Command line: root=UUID=17112d50-e492-4405-bb55-f1f5fc3bb289 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6630 checksum 0
[    0.000000] ACPI: RSDP 000F6630, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FFF3000, 0034 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 7FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 7FFF30C0, 42D0 (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: SSDT 7FFF7440, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: MCFG 7FFF7680, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: APIC 7FFF73C0, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524272
[    0.000000] On node 0 totalpages: 524175
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7111 pages used for memmap
[    0.000000]   DMA32 zone: 513065 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:50000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515883
[    0.000000] Kernel command line: root=UUID=17112d50-e492-4405-bb55-f1f5fc3bb289 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   26.091251] time.c: Detected 2211.336 MHz processor.
[   26.092400] Console: colour VGA+ 80x25
[   26.092415] Checking aperture...
[   26.092418] CPU 0: aperture @ 94b4000000 size 32 MB
[   26.092420] Aperture too small (32 MB)
[   26.097076] No AGP bridge found
[   26.112958] Memory: 2056132k/2097088k available (2274k kernel code, 40568k reserved, 1181k data, 296k init)
[   26.113001] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   26.189240] Calibrating delay using timer specific routine.. 4425.39 BogoMIPS (lpj=8850780)
[   26.189269] Security Framework v1.0.0 initialized
[   26.189275] SELinux:  Disabled at boot.
[   26.189416] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   26.190447] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.190934] Mount-cache hash table entries: 256
[   26.191052] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.191054] CPU: L2 Cache: 512K (64 bytes/line)
[   26.191057] CPU 0/0 -> Node 0
[   26.191059] CPU: Physical Processor ID: 0
[   26.191060] CPU: Processor Core ID: 0
[   26.191078] SMP alternatives: switching to UP code
[   26.191299] Early unpacking initramfs... done
[   26.453918] ACPI: Core revision 20070126
[   26.453967] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.497396] Using local APIC timer interrupts.
[   26.542613] result 12564412
[   26.542615] Detected 12.564 MHz APIC timer.
[   26.545270] SMP alternatives: switching to SMP code
[   26.545375] Booting processor 1/2 APIC 0x1
[   26.555902] Initializing CPU#1
[   26.633665] Calibrating delay using timer specific routine.. 4423.05 BogoMIPS (lpj=8846108)
[   26.633671] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.633673] CPU: L2 Cache: 512K (64 bytes/line)
[   26.633676] CPU 1/1 -> Node 0
[   26.633678] CPU: Physical Processor ID: 0
[   26.633679] CPU: Processor Core ID: 1
[   26.633752] AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   26.637210] Brought up 2 CPUs
[   27.326353] migration_cost=176
[   27.326063] NET: Registered protocol family 16
[   27.326142] ACPI: bus type pci registered
[   27.326147] PCI: Using configuration type 1
[   27.327085] ACPI: EC: Look up EC in DSDT
[   27.331583] ACPI: Interpreter enabled
[   27.331586] ACPI: (supports S0 S1 S4 S5)
[   27.331600] ACPI: Using IOAPIC for interrupt routing
[   27.338584] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.338590] PCI: Probing PCI hardware (bus 00)
[   27.338995] PCI: Transparent bridge - 0000:00:09.0
[   27.339233] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.339473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   27.376521] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   27.376650] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.376779] ACPI: PCI Interrupt Link [LNK3] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   27.376907] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   27.377033] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.377164] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   27.377291] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.377419] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   27.377546] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.377673] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.377801] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   27.377929] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   27.378056] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.378191] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   27.378324] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   27.378457] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.378604] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   27.378744] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   27.378884] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   27.379024] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   27.379115] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   27.379267] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   27.379413] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   27.379558] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   27.379703] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   27.379849] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   27.379994] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   27.380139] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   27.380284] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   27.380436] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   27.380587] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   27.380737] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   27.380822] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.380833] pnp: PnP ACPI init
[   27.380844] ACPI: bus type pnp registered
[   27.384120] pnp: PnP ACPI: found 14 devices
[   27.384122] ACPI: ACPI bus type pnp unregistered
[   27.384179] PCI: Using ACPI for IRQ routing
[   27.384182] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.384252] NET: Registered protocol family 8
[   27.384254] NET: Registered protocol family 20
[   27.384362] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   27.384364] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   27.384367] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   27.384370] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   27.384373] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   27.384375] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   27.384384] pnp: 00:0c: iomem range 0xd0000000-0xdfffffff could not be reserved
[   27.384389] pnp: 00:0d: iomem range 0xd1800-0xd3fff has been reserved
[   27.384391] pnp: 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[   27.384394] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   27.384396] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   27.384669] PCI: Bridge: 0000:00:09.0
[   27.384672]   IO window: 9000-9fff
[   27.384675]   MEM window: f3000000-f30fffff
[   27.384677]   PREFETCH window: disabled.
[   27.384679] PCI: Bridge: 0000:00:0b.0
[   27.384681]   IO window: 6000-6fff
[   27.384683]   MEM window: disabled.
[   27.384685]   PREFETCH window: disabled.
[   27.384687] PCI: Bridge: 0000:00:0c.0
[   27.384688]   IO window: 8000-8fff
[   27.384690]   MEM window: disabled.
[   27.384692]   PREFETCH window: disabled.
[   27.384694] PCI: Bridge: 0000:00:0d.0
[   27.384696]   IO window: 7000-7fff
[   27.384698]   MEM window: disabled.
[   27.384699]   PREFETCH window: disabled.
[   27.384703] PCI: Bridge: 0000:00:0e.0
[   27.384705]   IO window: a000-afff
[   27.384708]   MEM window: f0000000-f2ffffff
[   27.384710]   PREFETCH window: e0000000-efffffff
[   27.384717] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   27.384724] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   27.384728] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   27.384733] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   27.384738] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   27.384785] NET: Registered protocol family 2
[   27.385600] Time: acpi_pm clocksource has been installed.
[   27.429143] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   27.429833] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   27.432563] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   27.433049] TCP: Hash tables configured (established 262144 bind 65536)
[   27.433053] TCP reno registered
[   27.445185] checking if image is initramfs... it is
[   27.966012] Freeing initrd memory: 7200k freed
[   27.970540] audit: initializing netlink socket (disabled)
[   27.970555] audit(1200982134.840:1): initialized
[   27.972391] VFS: Disk quotas dquot_6.5.1
[   27.972438] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   27.972526] io scheduler noop registered
[   27.972528] io scheduler anticipatory registered
[   27.972529] io scheduler deadline registered
[   27.972613] io scheduler cfq registered (default)
[   27.973186] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   27.973195] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   27.973200] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   27.973207] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   27.973211] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   27.973218] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   27.973222] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   27.973228] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   27.973236] Boot video device is 0000:05:00.0
[   27.973359] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   27.973375] assign_interrupt_mode Found MSI capability
[   27.973378] Allocate Port Service[0000:00:0b.0:pcie00]
[   27.973435] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   27.973449] assign_interrupt_mode Found MSI capability
[   27.973451] Allocate Port Service[0000:00:0c.0:pcie00]
[   27.973507] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   27.973522] assign_interrupt_mode Found MSI capability
[   27.973524] Allocate Port Service[0000:00:0d.0:pcie00]
[   27.973573] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   27.973588] assign_interrupt_mode Found MSI capability
[   27.973590] Allocate Port Service[0000:00:0e.0:pcie00]
[   27.994716] Real Time Clock Driver v1.12ac
[   27.994805] Linux agpgart interface v0.102 (c) Dave Jones
[   27.994807] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.994887] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.995426] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.996043] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.996159] input: Macintosh mouse button emulation as /class/input/input0
[   27.996229] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   27.996515] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.996520] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.996619] mice: PS/2 mouse device common for all mice
[   27.996739] TCP cubic registered
[   27.996792] NET: Registered protocol family 1
[   27.996987] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   27.996995] Freeing unused kernel memory: 296k freed
[   28.029003] input: AT Translated Set 2 keyboard as /class/input/input1
[   29.162928] AppArmor: AppArmor initialized<5>audit(1200982136.032:2):  type=1505 info="AppArmor initialized" pid=1256
[   29.169112] fuse init (API version 7.8)
[   29.173497] Failure registering capabilities with primary security module.
[   29.685161] usbcore: registered new interface driver usbfs
[   29.685188] usbcore: registered new interface driver hub
[   29.685212] usbcore: registered new device driver usb
[   29.686372] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   29.686381] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 23
[   29.686518] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   29.686525] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   29.686672] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   29.686697] ehci_hcd 0000:00:02.1: debug port 1
[   29.686700] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   29.686710] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfeb00000
[   29.686715] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.686809] usb usb1: configuration #1 chosen from 1 choice
[   29.686831] hub 1-0:1.0: USB hub found
[   29.686837] hub 1-0:1.0: 10 ports detected
[   29.690418] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   29.699951] SCSI subsystem initialized
[   29.704400] libata version 2.21 loaded.
[   29.721672] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   29.748546] Floppy drive(s): fd0 is 1.44M
[   29.781387] FDC 0 is a post-1991 82077
[   29.784190] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.784196] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.794245] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   29.794257] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 22
[   29.794416] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.794423] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   29.794481] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   29.794500] ohci_hcd 0000:00:02.0: irq 22, io mem 0xf3101000
[   29.855294] usb usb2: configuration #1 chosen from 1 choice
[   29.855324] hub 2-0:1.0: USB hub found
[   29.855332] hub 2-0:1.0: 10 ports detected
[   29.963132] sata_nv 0000:00:07.0: version 3.4
[   29.963477] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   29.963485] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   29.963490] sata_nv 0000:00:07.0: Using ADMA mode
[   29.963693] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   29.963865] scsi0 : sata_nv
[   29.963911] scsi1 : sata_nv
[   29.963982] ata1: SATA max UDMA/133 cmd 0xffffc20000aa6480 ctl 0xffffc20000aa64a0 bmdma 0x000000000001c400 irq 21
[   29.963987] ata2: SATA max UDMA/133 cmd 0xffffc20000aa6580 ctl 0xffffc20000aa65a0 bmdma 0x000000000001c408 irq 21
[   30.277114] ata1: SATA link down (SStatus 0 SControl 300)
[   30.589064] ata2: SATA link down (SStatus 0 SControl 300)
[   30.589412] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   30.589419] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
[   30.589424] sata_nv 0000:00:08.0: Using ADMA mode
[   30.589594] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   30.589681] scsi2 : sata_nv
[   30.589743] scsi3 : sata_nv
[   30.589815] ata3: SATA max UDMA/133 cmd 0xffffc20000aa8480 ctl 0xffffc20000aa84a0 bmdma 0x000000000001d800 irq 20
[   30.589820] ata4: SATA max UDMA/133 cmd 0xffffc20000aa8580 ctl 0xffffc20000aa85a0 bmdma 0x000000000001d808 irq 20
[   31.060994] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   31.070032] ata3.00: Host Protected Area detected:
[   31.070033]  current size: 490232639 sectors
[   31.070034]  native size: 490234752 sectors
[   31.081099] ata3.00: native size increased to 490234752 sectors
[   31.081104] ata3.00: ATA-7: Maxtor 6V250F0, VA111900, max UDMA/133
[   31.081107] ata3.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   31.098044] ata3.00: configured for UDMA/133
[   31.412933] ata4: SATA link down (SStatus 0 SControl 300)
[   31.413027] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6V250F0   VA11 PQ: 0 ANSI: 5
[   31.413033] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   31.413493] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   31.413497] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   31.413503] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   31.413512] forcedeth: using HIGHDMA
[   31.420123] sd 2:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[   31.420136] sd 2:0:0:0: [sda] Write Protect is off
[   31.420138] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.420150] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.420196] sd 2:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[   31.420203] sd 2:0:0:0: [sda] Write Protect is off
[   31.420205] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.420215] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.420219]  sda: sda1 sda2 sda3 < sda5 >
[   31.456073] sd 2:0:0:0: [sda] Attached SCSI disk
[   31.459868] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   31.654989] Attempting manual resume
[   31.654993] swsusp: Resume From Partition 8:5
[   31.654995] PM: Checking swsusp image.
[   31.655124] PM: Resume from disk failed.
[   31.668701] EXT3-fs: INFO: recovery required on readonly filesystem.
[   31.668705] EXT3-fs: write access will be enabled during recovery.
[   31.937105] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:0a.0
[   31.937481] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   31.937489] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   31.987657] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f3004000-f30047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   31.987369] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   31.987388] NFORCE-CK804: chipset revision 242
[   31.987390] NFORCE-CK804: not 100% native mode: will probe irqs later
[   31.987395] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   31.987403]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   31.987412]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   31.987418] Probing IDE interface ide0...
[   32.724311] hda: BENQ DVD DD DW1650, ATAPI CD/DVD-ROM drive
[   33.061153] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   33.063839] Probing IDE interface ide1...
[   33.260744] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0016e60000b603b0]
[   33.639666] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   33.639674] Uniform CD-ROM driver Revision: 3.20
[   35.815099] kjournald starting.  Commit interval 5 seconds
[   35.815116] EXT3-fs: recovery complete.
[   35.822016] EXT3-fs: mounted filesystem with ordered data mode.
[   44.940478] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   44.940510] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   45.053333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.077621] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.171539] input: PC Speaker as /class/input/input2
[   45.294871] ISDN subsystem Rev: 1.1.2.3/1.1.2.3/1.1.2.2/1.1.2.3/1.1.2.2/1.1.2.2 loaded
[   45.321720] nvidia: module license 'NVIDIA' taints kernel.
[   45.575895] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   45.575904] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   45.576063] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   45.618789] HiSax: Linux Driver for passive ISDN cards
[   45.618793] HiSax: Version 3.5 (module)
[   45.618795] HiSax: Layer1 Revision 2.46.2.5
[   45.618797] HiSax: Layer2 Revision 2.30.2.4
[   45.618798] HiSax: TeiMgr Revision 2.20.2.3
[   45.618800] HiSax: Layer3 Revision 2.22.2.3
[   45.618801] HiSax: LinkLayer Revision 2.59.2.4
[   45.853282] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   45.853293] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   45.853314] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   46.154953] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   46.157703] parport_pc 00:09: reported by Plug and Play ACPI
[   46.157742] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   47.121347] lp0: using parport0 (interrupt-driven).
[   47.194002] Adding 393552k swap on /dev/sda5.  Priority:-1 extents:1 across:393552k
[   47.423745] EXT3 FS on sda2, internal journal
[   48.412310] No dock devices found.
[   48.425327] input: Power Button (FF) as /class/input/input4
[   48.425349] ACPI: Power Button (FF) [PWRF]
[   48.425388] input: Power Button (CM) as /class/input/input5
[   48.425400] ACPI: Power Button (CM) [PWRB]
[   48.787855] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (version 2.00.00)
[   48.787432] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xa
[   48.787437] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xc
[   48.787439] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xe
[   48.787441] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   49.482679] ppdev: user-space parallel port driver
[   49.737362] audit(1201000156.704:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4887 profile="/usr/sbin/cupsd"
[   49.881523] Failure registering capabilities with primary security module.
[   52.269354] NET: Registered protocol family 17
[   54.572640] NET: Registered protocol family 10
[   54.572718] lo: Disabled Privacy Extensions
[   59.624592] eth0: no IPv6 routers present
[ 1032.453406] eth0: link down.
[ 1034.087129] eth0: link up.
[ 1034.088692] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1045.252155] eth0: no IPv6 routers present

---

### Post by cdenley on 2008-01-22
yeluapyeroc:
That sounds like a problem with compiz-fusion. Try disabling desktop effects.

Holonet:
> should also note this has happened to me while simply browsing files and not playing music
Do you mean it happens while browsing files with nautilus, or with totem/vlc? With no disk errors in dmesg, it sounds like a software problem. Can you try a livecd to check if the same problem exists?

---

### Post by Holonet on 2008-01-22
Sorry, I did mean in nautilus.  When it happens, every file I click on switches its icon to a blank white box, and it's like it's not there.  If I try to browse a folder, it gives me that not accessible error.

I highly suspect it's a software problem, but I don't have a clue how to track it down.  I could try the LiveCD, but I seriously doubt it would surface.  Plus, the time that happened in order to allow me to get the dmesg bit, it was on for hours as it was.

At first I suspected totem, just because it plain sucks haha...that is, it crashes when I seek often...But anyway, I completely removed that, and set vlc as a default to open everything.  Since vlc is well-established as a good player and I haven't heard of it causing any problems, I was suspicious of an ubuntu bug...but I just don't know.

From the sound of it, I don't think yeluapyeroc has a different problem, or at least is very similar.  Sometimes when this happens, in addition, I can't open any programs or even press the button in the corner that brings up the shut down/restart menu.  That doesn't happen as often, and if it did, I'm not sure if I could even get a terminal up to run dmesg.

---

### Post by Holonet on 2008-02-14
Not to revive dead threads needlessly, but I thought this was worth posting.  I feel a bit thick for not trying this before...but anyhoo...

When this problem occurs, if I open the system monitor and end nautilus, then go back into my music folder, the problem is fixed.  I'm finding this stability a little too reminiscent of Windows...just like having to shut down explorer, and I've had Ubuntu crash significantly more than XP.

---

### Post by paul928 on 2008-02-15
Also "killall nautilus" from a terminal works. I've been having the same problem on 2 different computers since I upgraded to Gutsy on one and a fresh install on the other. Just loaded Gutsy on a new computer, hope it doesn't have the same problem with Nautilus crashing.

---

### Post by paul928 on 2008-02-16
Well, it started on my new install also. I think I fixed the problem by going back from the rt 32 bit kernel to the generic kernel. Of course, now that brings me back to audio problems.......

---

