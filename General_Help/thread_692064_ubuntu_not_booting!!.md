---
title: "ubuntu not booting!!"
date: 2008-02-09
forum: General Help
---

### Post by ilwa7esh on 2008-02-09
Hi, yesterday everything was working properly. Today when i started my computer Ubuntu halted for a little then it started showing me text like if you were booting on recovery mode. It would then halt (on getting manual drives) so i press ctrl alt del, and it continues on booting and then it halts again ( for very long times) I press ctrl alt del so it said it rebooting but then it halts again and the only thing i can do is switch pc off. I then tried to boot on recovery line and it was taking much longer time than usual ( i boot on recovery before) but it reached command line ( I didnt know what to do cuz am still new to linux) so i typed reboot, it made the first steps of rebooting but then halted again and stopped  responding so  also had to switch it off. Can anyone plz help me and tell me what happened and what should I do?

---

### Post by ilwa7esh on 2008-02-09
bump :(

---

### Post by SpaceTeddy on 2008-02-09
if you can still bool into the ubuntu (even if it takes forever), please post the boot logs. you can get them by opening a terminal and typing

> dmesg

if that is too much to copy, redirect the ouput to a file in your homedir (boot.log in this case) with

> dmesg > ~/boot.log

---

### Post by ilwa7esh on 2008-02-09
This is boot.log attached. Please note its is from booting in recovery mode since i cant log into ubutnu in normal mode. Recovery mode is not working properly (boots very slow and doesnt reboot) so i hope this log is helpful
Thanx
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Thu Jan 31 23:33:13 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
[    0.000000] Command line: root=UUID=2b8ae7b2-aa76-4f76-a7fc-1d6a54509e3e ro single
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff80000 (usable)
[    0.000000]  BIOS-e820: 000000007ff80000 - 000000007ff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff8e000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524160) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FBCC0 checksum 0
[    0.000000] ACPI: RSDP 000FBCC0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FF80000, 003C (r1 A_M_I_ OEMRSDT  12000711 MSFT       97)
[    0.000000] ACPI: FACP 7FF80200, 0084 (r2 A_M_I_ OEMFACP  12000711 MSFT       97)
[    0.000000] ACPI: DSDT 7FF805C0, 90B7 (r1  A0753 A0753001        1 INTL 20060113)
[    0.000000] ACPI: FACS 7FF8E000, 0040
[    0.000000] ACPI: APIC 7FF80390, 006C (r1 A_M_I_ OEMAPIC  12000711 MSFT       97)
[    0.000000] ACPI: MCFG 7FF80400, 003C (r1 A_M_I_ OEMMCFG  12000711 MSFT       97)
[    0.000000] ACPI: OEMB 7FF8E040, 0081 (r1 A_M_I_ AMI_OEM  12000711 MSFT       97)
[    0.000000] ACPI: HPET 7FF89680, 0038 (r1 A_M_I_ OEMHPET  12000711 MSFT       97)
[    0.000000] ACPI: OSFR 7FF896C0, 00B0 (r1 A_M_I_ OEMOSFR  12000711 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ff80000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524160) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ff80000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524160
[    0.000000] On node 0 totalpages: 524063
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7110 pages used for memmap
[    0.000000]   DMA32 zone: 512954 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515772
[    0.000000] Kernel command line: root=UUID=2b8ae7b2-aa76-4f76-a7fc-1d6a54509e3e ro single
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   13.362025] time.c: Detected 2671.600 MHz processor.
[   13.362564] Console: colour VGA+ 80x25
[   13.364129] Checking aperture...
[   13.364160] Calgary: detecting Calgary via BIOS EBDA area
[   13.364162] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   13.379936] Memory: 2055608k/2096640k available (2274k kernel code, 40644k reserved, 1181k data, 296k init)
[   13.380002] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   13.456523] Calibrating delay using timer specific routine.. 5346.72 BogoMIPS (lpj=10693440)
[   13.456597] Security Framework v1.0.0 initialized
[   13.456628] SELinux:  Disabled at boot.
[   13.456790] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   13.457755] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.458231] Mount-cache hash table entries: 256
[   13.458354] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.458405] CPU: L2 cache: 4096K
[   13.458432] CPU 0/0 -> Node 0
[   13.458458] using mwait in idle threads.
[   13.458484] CPU: Physical Processor ID: 0
[   13.458511] CPU: Processor Core ID: 0
[   13.458540] CPU0: Thermal monitoring enabled (TM2)
[   13.458573] SMP alternatives: switching to UP code
[   13.458781] Early unpacking initramfs... done
[   13.705653] ACPI: Core revision 20070126
[   13.705717] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.806483] Using local APIC timer interrupts.
[   13.843913] result 20871873
[   13.843939] Detected 20.871 MHz APIC timer.
[   13.844266] SMP alternatives: switching to SMP code
[   13.844347] Booting processor 1/2 APIC 0x1
[   13.854725] Initializing CPU#1
[   13.932161] Calibrating delay using timer specific routine.. 5343.38 BogoMIPS (lpj=10686773)
[   13.932166] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.932167] CPU: L2 cache: 4096K
[   13.932169] CPU 1/1 -> Node 0
[   13.932170] CPU: Physical Processor ID: 0
[   13.932171] CPU: Processor Core ID: 1
[   13.932175] CPU1: Thermal monitoring enabled (TM2)
[   13.932551] Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[   13.932606] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   13.956154] Brought up 2 CPUs
[   14.002029] migration_cost=9
[   14.002227] NET: Registered protocol family 16
[   14.002311] ACPI: bus type pci registered
[   14.002340] PCI: Using configuration type 1
[   14.004489] ACPI: EC: Look up EC in DSDT
[   14.009871] ACPI: Interpreter enabled
[   14.009898] ACPI: (supports S0 S1 S3 S4 S5)
[   14.010066] ACPI: Using IOAPIC for interrupt routing
[   14.016120] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.016155] PCI: Probing PCI hardware (bus 00)
[   14.017321] PCI: Transparent bridge - 0000:00:1e.0
[   14.017393] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.017504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   14.017565] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   14.017661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   14.017725] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   14.017797] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   14.029979] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   14.030350] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   14.030718] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   14.031086] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[   14.031455] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   14.031870] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   14.032256] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   14.032625] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   14.032978] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.033010] pnp: PnP ACPI init
[   14.033040] ACPI: bus type pnp registered
[   14.035096] pnp: PnP ACPI: found 15 devices
[   14.035123] ACPI: ACPI bus type pnp unregistered
[   14.035183] PCI: Using ACPI for IRQ routing
[   14.035210] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.035308] NET: Registered protocol family 8
[   14.035335] NET: Registered protocol family 20
[   14.035372] PCI-GART: No AMD northbridge found.
[   14.035401] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   14.035537] hpet0: 4 64-bit timers, 14318180 Hz
[   14.036611] pnp: 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   14.036642] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[   14.036671] pnp: 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   14.036699] pnp: 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   14.036727] pnp: 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[   14.036754] pnp: 00:08: iomem range 0xffa00000-0xffafffff has been reserved
[   14.036784] pnp: 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   14.036812] pnp: 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   14.036844] pnp: 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[   14.036873] pnp: 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   14.036901] pnp: 00:0e: iomem range 0xc0000-0xcffff has been reserved
[   14.036929] pnp: 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   14.036957] pnp: 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[   14.037162] PCI: Bridge: 0000:00:01.0
[   14.037189]   IO window: c000-cfff
[   14.037217]   MEM window: fe800000-fe8fffff
[   14.037244]   PREFETCH window: d0000000-dfffffff
[   14.037272] PCI: Bridge: 0000:00:1c.0
[   14.037298]   IO window: disabled.
[   14.037326]   MEM window: disabled.
[   14.037353]   PREFETCH window: fdf00000-fdffffff
[   14.037382] PCI: Bridge: 0000:00:1c.4
[   14.037409]   IO window: d000-dfff
[   14.037438]   MEM window: fea00000-feafffff
[   14.037465]   PREFETCH window: disabled.
[   14.037493] PCI: Bridge: 0000:00:1c.5
[   14.037519]   IO window: disabled.
[   14.037548]   MEM window: fe900000-fe9fffff
[   14.037575]   PREFETCH window: disabled.
[   14.037603] PCI: Bridge: 0000:00:1e.0
[   14.037630]   IO window: e000-efff
[   14.037659]   MEM window: feb00000-febfffff
[   14.037686]   PREFETCH window: disabled.
[   14.037721] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.037775] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.037787] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.037841] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.037852] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   14.037906] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   14.037917] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   14.037971] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   14.037978] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.037985] NET: Registered protocol family 2
[   14.040080] Time: tsc clocksource has been installed.
[   14.080214] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   14.080691] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   14.082783] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   14.083296] TCP: Hash tables configured (established 262144 bind 65536)
[   14.083324] TCP reno registered
[   14.096307] checking if image is initramfs... it is
[   14.584488] Freeing initrd memory: 7207k freed
[   14.586768] audit: initializing netlink socket (disabled)
[   14.586809] audit(1202574971.124:1): initialized
[   14.588504] VFS: Disk quotas dquot_6.5.1
[   14.588561] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   14.588643] io scheduler noop registered
[   14.588670] io scheduler anticipatory registered
[   14.588697] io scheduler deadline registered
[   14.588781] io scheduler cfq registered (default)
[   14.591622] Boot video device is 0000:01:00.0
[   14.591716] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.591737] assign_interrupt_mode Found MSI capability
[   14.591767] Allocate Port Service[0000:00:01.0:pcie00]
[   14.591822] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.591850] assign_interrupt_mode Found MSI capability
[   14.591877] Allocate Port Service[0000:00:1c.0:pcie00]
[   14.591899] Allocate Port Service[0000:00:1c.0:pcie02]
[   14.591950] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   14.591978] assign_interrupt_mode Found MSI capability
[   14.592005] Allocate Port Service[0000:00:1c.4:pcie00]
[   14.592023] Allocate Port Service[0000:00:1c.4:pcie02]
[   14.592076] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   14.592104] assign_interrupt_mode Found MSI capability
[   14.592131] Allocate Port Service[0000:00:1c.5:pcie00]
[   14.592150] Allocate Port Service[0000:00:1c.5:pcie02]
[   14.604826] Real Time Clock Driver v1.12ac
[   14.604975] hpet_resources: 0xfed00000 is busy
[   14.605005] Linux agpgart interface v0.102 (c) Dave Jones
[   14.605032] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.605140] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   14.605525] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   14.605947] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.606055] input: Macintosh mouse button emulation as /class/input/input0
[   14.606126] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   14.606154] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   14.608423] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.608452] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.608578] mice: PS/2 mouse device common for all mice
[   14.608686] TCP cubic registered
[   14.608753] NET: Registered protocol family 1
[   14.608910] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   14.608945] Freeing unused kernel memory: 296k freed
[   14.700663] AppArmor: AppArmor initialized<5>audit(1202574971.240:2):  type=1505 info="AppArmor initialized" pid=1236
[   14.703776] fuse init (API version 7.8)
[   14.706195] Failure registering capabilities with primary security module.
[   14.728381] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  C4, should be BB [20070126]
[   14.728460] ACPI: SSDT 7FF8E0D0, 01D2 (r1    AMI   CPU1PM        1 INTL 20060113)
[   14.728795] ACPI: SSDT 7FF8E2B0, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[   14.729007] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   14.729088] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   14.983178] usbcore: registered new interface driver usbfs
[   14.983222] usbcore: registered new interface driver hub
[   14.987601] usbcore: registered new device driver usb
[   14.988062] USB Universal Host Controller Interface driver v3.0
[   14.988153] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.988212] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   14.988214] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   14.988333] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   14.988384] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[   14.988477] usb usb1: configuration #1 chosen from 1 choice
[   14.988520] hub 1-0:1.0: USB hub found
[   14.988549] hub 1-0:1.0: 2 ports detected
[   15.013893] SCSI subsystem initialized
[   15.037252] libata version 2.21 loaded.
[   15.064348] Floppy drive(s): fd0 is 1.44M
[   15.083191] FDC 0 is a post-1991 82077
[   15.091712] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   15.091777] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   15.091780] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   15.091825] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   15.091883] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[   15.091970] usb usb2: configuration #1 chosen from 1 choice
[   15.092011] hub 2-0:1.0: USB hub found
[   15.092040] hub 2-0:1.0: 2 ports detected
[   15.196081] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   15.196142] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   15.196145] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   15.196188] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   15.196242] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[   15.196323] usb usb3: configuration #1 chosen from 1 choice
[   15.196363] hub 3-0:1.0: USB hub found
[   15.196391] hub 3-0:1.0: 2 ports detected
[   15.300536] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   15.300596] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   15.300599] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   15.300641] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   15.300696] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[   15.300776] usb usb4: configuration #1 chosen from 1 choice
[   15.300817] hub 4-0:1.0: USB hub found
[   15.300845] hub 4-0:1.0: 2 ports detected
[   15.332613] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   15.405014] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   15.405074] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   15.405077] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   15.405121] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   15.405176] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[   15.405255] usb usb5: configuration #1 chosen from 1 choice
[   15.405297] hub 5-0:1.0: USB hub found
[   15.405325] hub 5-0:1.0: 2 ports detected
[   15.509587] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   15.509647] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   15.509650] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   15.509694] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   15.509748] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[   15.509828] usb usb6: configuration #1 chosen from 1 choice
[   15.509868] hub 6-0:1.0: USB hub found
[   15.509896] hub 6-0:1.0: 2 ports detected
[   15.512085] usb 1-1: configuration #1 chosen from 1 choice
[   15.614197] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   15.614965] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   15.614969] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   15.615038] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   15.615096] ehci_hcd 0000:00:1a.7: debug port 1
[   15.615125] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   15.615131] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe7ffc00
[   15.619028] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.619129] usb usb7: configuration #1 chosen from 1 choice
[   15.619174] hub 7-0:1.0: USB hub found
[   15.619204] hub 7-0:1.0: 6 ports detected
[   15.726457] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   15.727266] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   15.727271] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   15.727332] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   15.727386] ehci_hcd 0000:00:1d.7: debug port 1
[   15.727415] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   15.727421] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe7ff800
[   15.731335] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.731428] usb usb8: configuration #1 chosen from 1 choice
[   15.731472] hub 8-0:1.0: USB hub found
[   15.731501] hub 8-0:1.0: 6 ports detected
[   15.758465] usb 1-1: USB disconnect, address 2
[   15.838696] ACPI: PCI Interrupt 0000:05:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.891832] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   15.896911] ahci 0000:03:00.0: version 2.2
[   15.896931] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.625232] usb 8-5: new high speed USB device using ehci_hcd and address 2
[   16.898060] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   16.898095] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   16.898132] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   16.898432] scsi0 : ahci
[   16.898588] scsi1 : ahci
[   16.898735] ata1: SATA max UDMA/133 cmd 0xffffc20000ac0100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 16
[   16.898769] ata2: SATA max UDMA/133 cmd 0xffffc20000ac0180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 16
[   17.015456] usb 8-5: configuration #1 chosen from 1 choice
[   17.016075] usbcore: registered new interface driver hiddev
[   17.167069] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000164d15f]
[   17.211197] ata1: SATA link down (SStatus 0 SControl 300)
[   17.255384] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   17.434637] usb 1-1: configuration #1 chosen from 1 choice
[   17.524740] ata2: SATA link down (SStatus 0 SControl 300)
[   17.525355] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   17.525388] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 17 (level, low) -> IRQ 17
[   17.525467] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   17.525498] scsi2 : pata_jmicron
[   17.525549] scsi3 : pata_jmicron
[   17.525636] ata3: PATA max UDMA/100 cmd 0x000000000001dc00 ctl 0x000000000001d882 bmdma 0x000000000001d400 irq 17
[   17.525669] ata4: PATA max UDMA/100 cmd 0x000000000001d800 ctl 0x000000000001d482 bmdma 0x000000000001d408 irq 17
[   17.697219] usb 1-2: new low speed USB device using uhci_hcd and address 4
[   17.846069] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB00, max UDMA/66
[   17.875299] usb 1-2: configuration #1 chosen from 1 choice
[   17.907525] input: MLK Trust Mouse 15206 as /class/input/input1
[   17.907585] input,hiddev96: USB HID v1.10 Mouse [MLK Trust Mouse 15206] on usb-0000:00:1a.0-1
[   17.926371] input: KYE 4D device Ergomedia as /class/input/input2
[   17.926402] input: USB HID v1.10 Keyboard [KYE 4D device Ergomedia] on usb-0000:00:1a.0-2
[   17.953464] input: KYE 4D device Ergomedia as /class/input/input3
[   17.953503] input: USB HID v1.10 Mouse [KYE 4D device Ergomedia] on usb-0000:00:1a.0-2
[   17.953581] usbcore: registered new interface driver usbhid
[   17.953609] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   18.018925] ata3.00: configured for UDMA/66
[   18.187130] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202J  SB00 PQ: 0 ANSI: 5
[   18.188945] ata_piix 0000:00:1f.2: version 2.11
[   18.188949] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   18.189107] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 22 (level, low) -> IRQ 22
[   18.189177] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.189197] scsi4 : ata_piix
[   18.189247] scsi5 : ata_piix
[   18.189336] ata5: SATA max UDMA/133 cmd 0x000000000001a000 ctl 0x0000000000019c02 bmdma 0x0000000000019480 irq 22
[   18.189369] ata6: SATA max UDMA/133 cmd 0x0000000000019880 ctl 0x0000000000019802 bmdma 0x0000000000019488 irq 22
[   18.198704] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   18.198739] Uniform CD-ROM driver Revision: 3.20
[   18.198904] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   18.201265] sr 2:0:0:0: Attached scsi generic sg0 type 5
[   18.356235] ata5.00: ATA-7: Hitachi HDT725032VLA360, V54OA7EA, max UDMA/133
[   18.356268] ata5.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   18.372323] ata5.00: configured for UDMA/133
[   18.539227] scsi 4:0:0:0: Direct-Access     ATA      Hitachi HDT72503 V54O PQ: 0 ANSI: 5
[   18.539293] scsi 4:0:0:0: Attached scsi generic sg1 type 0
[   18.539337] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   18.539488] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 22 (level, low) -> IRQ 22
[   18.539558] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   18.539575] scsi6 : ata_piix
[   18.539623] scsi7 : ata_piix
[   18.539712] ata7: SATA max UDMA/133 cmd 0x000000000001b000 ctl 0x000000000001ac02 bmdma 0x000000000001a480 irq 22
[   18.539744] ata8: SATA max UDMA/133 cmd 0x000000000001a880 ctl 0x000000000001a802 bmdma 0x000000000001a488 irq 22
[   18.871710] sd 4:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   18.871747] sd 4:0:0:0: [sda] Write Protect is off
[   18.871775] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.871784] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.871840] sd 4:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   18.871872] sd 4:0:0:0: [sda] Write Protect is off
[   18.871899] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.871909] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.871942]  sda: sda1 sda2 < sda5 > sda3
[   18.904002] sd 4:0:0:0: [sda] Attached SCSI disk
[   19.071263] Attempting manual resume
[   19.071290] swsusp: Resume From Partition 8:5
[   19.071291] PM: Checking swsusp image.
[   19.071402] PM: Resume from disk failed.
[   19.099018] kjournald starting.  Commit interval 5 seconds
[   19.099057] EXT3-fs: mounted filesystem with ordered data mode.
[   25.294653] rtusb init ====>
[   25.294703] idVendor = 0x50d, idProduct = 0x905b 
[   85.248517] rt73: Failed to request_firmware. Check your firmware file location
[   85.248553] rt73: probe of 8-5:1.0 failed with error -2
[   85.248590] usbcore: registered new interface driver rt73
[   85.332207] ip_tables: (C) 2000-2006 Netfilter Core Team
[   85.343644] Netfilter messages via NETLINK v0.30.
[   85.353752] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   85.375414] Unable to handle kernel NULL pointer dereference at 0000000000000000 RIP: 
[   85.375440]  [<0000000000000000>]
[   85.375518] PGD 78539067 PUD 77b27067 PMD 0 
[   85.375611] Oops: 0010 [1] SMP 
[   85.375681] CPU 0 
[   85.375728] Modules linked in: iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nfnetlink iptable_mangle iptable_filter ip_tables x_tables rt73 ext3 jbd mbcache sd_mod sg sr_mod cdrom ata_piix usbhid hid floppy pata_jmicron ahci ohci1394 ieee1394 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
[   85.376602] Pid: 3027, comm: ifconfig Not tainted 2.6.22-14-generic #1
[   85.376629] RIP: 0010:[<0000000000000000>]  [<0000000000000000>]
[   85.376679] RSP: 0018:ffff810075d47e20  EFLAGS: 00010296
[   85.376706] RAX: ffffffff8045f900 RBX: ffff81007c830000 RCX: 0000000000000000
[   85.376734] RDX: ffff810075d47ed0 RSI: ffff81007c830000 RDI: ffff81007c830000
[   85.376762] RBP: ffff81007bd5f420 R08: 00000000ffffffff R09: 0000000000000000
[   85.376789] R10: 00000000fffffffe R11: 0000000000000001 R12: 0000000000000143
[   85.376817] R13: ffff810075d47ed0 R14: 0000000000000400 R15: ffff810077d74d00
[   85.376846] FS:  00002ba19217a6e0(0000) GS:ffffffff80560000(0000) knlGS:0000000000000000
[   85.376876] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   85.376904] CR2: 0000000000000000 CR3: 00000000788f9000 CR4: 00000000000006e0
[   85.376932] Process ifconfig (pid: 3027, threadinfo ffff810075d46000, task ffff81007be16dc0)
[   85.376963] Stack:  ffffffff803b6e9c 0000000000000000 0000000000000000 0000000000000000
[   85.377103]  0000000000000000 0000000000000000 0000000000000000 0000000000000000
[   85.377220]  0000000000000000 0000000000000000 0000000000000000 0000000000000000
[   85.377312] Call Trace:
[   85.377366]  [<ffffffff803b6e9c>] dev_seq_show+0x1c/0x110
[   85.377396]  [<ffffffff802b7155>] seq_read+0x215/0x2e0
[   85.377425]  [<ffffffff80299b12>] vfs_read+0xe2/0x190
[   85.377453]  [<ffffffff8029a003>] sys_read+0x53/0x90
[   85.377482]  [<ffffffff80209e8e>] system_call+0x7e/0x83
[   85.377510] 
[   85.377535] 
[   85.377535] Code:  Bad RIP value.
[   85.377629] RIP  [<0000000000000000>]
[   85.377677]  RSP <ffff810075d47e20>
[   85.377703] CR2: 0000000000000000
[   85.379711] Unable to handle kernel NULL pointer dereference at 0000000000000000 RIP: 
[   85.379739]  [<0000000000000000>]
[   85.379818] PGD 77a9b067 PUD 78f64067 PMD 0 
[   85.379912] Oops: 0010 [2] SMP 
[   85.379982] CPU 1 
[   85.380030] Modules linked in: iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nfnetlink iptable_mangle iptable_filter ip_tables x_tables rt73 ext3 jbd mbcache sd_mod sg sr_mod cdrom ata_piix usbhid hid floppy pata_jmicron ahci ohci1394 ieee1394 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
[   85.380904] Pid: 3032, comm: ifconfig Not tainted 2.6.22-14-generic #1
[   85.380931] RIP: 0010:[<0000000000000000>]  [<0000000000000000>]
[   85.380981] RSP: 0018:ffff810077f03e20  EFLAGS: 00010296
[   85.381008] RAX: ffffffff8045f900 RBX: ffff81007c830000 RCX: 0000000000000000
[   85.381036] RDX: ffff810077f03ed0 RSI: ffff81007c830000 RDI: ffff81007c830000
[   85.381064] RBP: ffff81007c94e7e0 R08: 00000000ffffffff R09: 0000000000000000
[   85.381092] R10: 00000000fffffffe R11: 0000000000000001 R12: 0000000000000143
[   85.381120] R13: ffff810077f03ed0 R14: 0000000000000400 R15: ffff81007cbc0000
[   85.381148] FS:  00002ac05462e6e0(0000) GS:ffff81000103d280(0000) knlGS:0000000000000000
[   85.381179] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   85.381207] CR2: 0000000000000000 CR3: 00000000784c8000 CR4: 00000000000006e0
[   85.381235] Process ifconfig (pid: 3032, threadinfo ffff810077f02000, task ffff810037f20000)
[   85.381265] Stack:  ffffffff803b6e9c 0000000000000000 0000000000000000 0000000000000000
[   85.381405]  0000000000000000 0000000000000000 0000000000000000 0000000000000000
[   85.381522]  0000000000000000 0000000000000000 0000000000000000 0000000000000000
[   85.381615] Call Trace:
[   85.381667]  [<ffffffff803b6e9c>] dev_seq_show+0x1c/0x110
[   85.381697]  [<ffffffff802b7155>] seq_read+0x215/0x2e0
[   85.381726]  [<ffffffff80299b12>] vfs_read+0xe2/0x190
[   85.381754]  [<ffffffff8029a003>] sys_read+0x53/0x90
[   85.381782]  [<ffffffff80209e8e>] system_call+0x7e/0x83
[   85.381810] 
[   85.381835] 
[   85.381836] Code:  Bad RIP value.
[   85.381929] RIP  [<0000000000000000>]
[   85.381978]  RSP <ffff810077f03e20>
[   85.382004] CR2: 0000000000000000
[   85.383203] Unable to handle kernel NULL pointer dereference at 0000000000000000 RIP: 
[   85.383228]  [<0000000000000000>]
[   85.383305] PGD 78f67067 PUD 77e9a067 PMD 0 
[   85.383397] Oops: 0010 [3] SMP 
[   85.383466] CPU 0 
[   85.383513] Modules linked in: iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nfnetlink iptable_mangle iptable_filter ip_tables x_tables rt73 ext3 jbd mbcache sd_mod sg sr_mod cdrom ata_piix usbhid hid floppy pata_jmicron ahci ohci1394 ieee1394 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
[   85.384736] Pid: 3036, comm: ifconfig Not tainted 2.6.22-14-generic #1
[   85.384763] RIP: 0010:[<0000000000000000>]  [<0000000000000000>]
[   85.384813] RSP: 0018:ffff810077b33e20  EFLAGS: 00010296
[   85.384840] RAX: ffffffff8045f900 RBX: ffff81007c830000 RCX: 0000000000000000
[   85.384868] RDX: ffff810077b33ed0 RSI: ffff81007c830000 RDI: ffff81007c830000
[   85.384896] RBP: ffff81007bd5f420 R08: 00000000ffffffff R09: 0000000000000000
[   85.384924] R10: 00000000fffffffe R11: 0000000000000001 R12: 0000000000000143
[   85.384952] R13: ffff810077b33ed0 R14: 0000000000000400 R15: ffff81007bd7b400
[   85.384980] FS:  00002ab50e1056e0(0000) GS:ffffffff80560000(0000) knlGS:0000000000000000
[   85.385011] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   85.385038] CR2: 0000000000000000 CR3: 00000000788db000 CR4: 00000000000006e0
[   85.385066] Process ifconfig (pid: 3036, threadinfo ffff810077b32000, task ffff810037b3cdc0)
[   85.385098] Stack:  ffffffff803b6e9c 0000000000000000 0000000000000000 0000000000000000
[   85.385237]  0000000000000000 0000000000000000 0000000000000000 0000000000000000
[   85.385354]  0000000000000000 0000000000000000 0000000000000000 0000000000000000
[   85.385447] Call Trace:
[   85.385498]  [<ffffffff803b6e9c>] dev_seq_show+0x1c/0x110
[   85.385528]  [<ffffffff802b7155>] seq_read+0x215/0x2e0
[   85.385556]  [<ffffffff80299b12>] vfs_read+0xe2/0x190
[   85.385584]  [<ffffffff8029a003>] sys_read+0x53/0x90
[   85.385612]  [<ffffffff80209e8e>] system_call+0x7e/0x83
[   85.385640] 
[   85.385665] 
[   85.385666] Code:  Bad RIP value.
[   85.385759] RIP  [<0000000000000000>]
[   85.385807]  RSP <ffff810077b33e20>
[   85.385833] CR2: 0000000000000000
[   85.499910] Unable to handle kernel NULL pointer dereference at 0000000000000000 RIP: 
[   85.499941]  [<ffffffff80326ca0>] strcmp+0x0/0x30
[   85.500021] PGD 793be067 PUD 78f6b067 PMD 0 
[   85.500114] Oops: 0000 [4] SMP 
[   85.500183] CPU 1 
[   85.500231] Modules linked in: iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nfnetlink iptable_mangle iptable_filter ip_tables x_tables rt73 ext3 jbd mbcache sd_mod sg sr_mod cdrom ata_piix usbhid hid floppy pata_jmicron ahci ohci1394 ieee1394 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
[   85.501107] Pid: 3086, comm: udevtrigger Not tainted 2.6.22-14-generic #1
[   85.501135] RIP: 0010:[<ffffffff80326ca0>]  [<ffffffff80326ca0>] strcmp+0x0/0x30
[   85.501189] RSP: 0018:ffff8100779c3bf0  EFLAGS: 00010246
[   85.501216] RAX: 0000000000000000 RBX: ffff810078dee120 RCX: ffff810078e71880
[   85.501244] RDX: 0000000000000073 RSI: ffff810077d7eb3c RDI: 0000000000000000
[   85.501271] RBP: ffff810078dee160 R08: 0000000000000001 R09: 0000000000000000
[   85.501299] R10: 000000000000000d R11: 0000000000000005 R12: ffff810077d7ea90
[   85.501327] R13: ffff8100779c3ca8 R14: ffff8100779c3cb8 R15: ffff81007ce796a8
[   85.501356] FS:  00002ad9be81cdb0(0000) GS:ffff81000103d280(0000) knlGS:0000000000000000
[   85.501387] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   85.501414] CR2: 0000000000000000 CR3: 00000000786dd000 CR4: 00000000000006e0
[   85.501442] Process udevtrigger (pid: 3086, threadinfo ffff8100779c2000, task ffff81007bc30000)
[   85.501473] Stack:  ffffffff802e8f7e ffff810077d7ea90 ffff810078e71820 ffff8100779c3e48
[   85.501613]  ffff8100779c3ca8 ffff8100779c3cb8 ffffffff802a1927 ffff8100779c3c88
[   85.501731]  ffff81007ca6ef00 ffff81007ce79760 ffff8100780da01b ffff8100779c3ca8
[   85.501825] Call Trace:
[   85.501877]  [<ffffffff802e8f7e>] sysfs_lookup+0x6e/0x240
[   85.501906]  [<ffffffff802a1927>] do_lookup+0x1b7/0x210
[   85.501934]  [<ffffffff802a3f41>] __link_path_walk+0x891/0xed0
[   85.501964]  [<ffffffff802a45da>] link_path_walk+0x5a/0xf0
[   85.501993]  [<ffffffff8023accb>] current_fs_time+0x3b/0x40
[   85.502021]  [<ffffffff802e8de2>] sysfs_readdir+0xc2/0x1d0
[   85.502049]  [<ffffffff802a73d0>] filldir+0x0/0xf0
[   85.502077]  [<ffffffff802b0038>] touch_atime+0x98/0x160
[   85.502105]  [<ffffffff802a48bc>] do_path_lookup+0xbc/0x230
[   85.502133]  [<ffffffff802a3195>] getname+0xf5/0x220
[   85.502161]  [<ffffffff802a54fb>] __user_walk_fd+0x4b/0x80
[   85.502189]  [<ffffffff8029cbaf>] vfs_stat_fd+0x2f/0x80
[   85.502217]  [<ffffffff8023accb>] current_fs_time+0x3b/0x40
[   85.502245]  [<ffffffff802e8de2>] sysfs_readdir+0xc2/0x1d0
[   85.502273]  [<ffffffff802a73d0>] filldir+0x0/0xf0
[   85.502300]  [<ffffffff802b0038>] touch_atime+0x98/0x160
[   85.502328]  [<ffffffff8029cdf7>] sys_newstat+0x27/0x50
[   85.502356]  [<ffffffff802a756d>] vfs_readdir+0xad/0xe0
[   85.502384]  [<ffffffff802a788f>] sys_getdents+0xdf/0xf0
[   85.502412]  [<ffffffff80209e8e>] system_call+0x7e/0x83
[   85.502440] 
[   85.502465] 
[   85.502465] Code: 0f b6 17 89 d0 2a 06 48 83 c6 01 84 c0 75 11 84 d2 74 0d 48 
[   85.502975] RIP  [<ffffffff80326ca0>] strcmp+0x0/0x30
[   85.503025]  RSP <ffff8100779c3bf0>
[   85.503051] CR2: 0000000000000000
[   86.156559] lp: driver loaded but no devices found
[   86.303111] coretemp coretemp.0: Using undocumented features, absolute temperature might be wrong!
[   86.303173] coretemp coretemp.1: Using undocumented features, absolute temperature might be wrong!
[   86.369268] Adding 6040400k swap on /dev/sda5.  Priority:-1 extents:1 across:6040400k
[   86.629830] EXT3 FS on sda1, internal journal
[   87.084493] kjournald starting.  Commit interval 5 seconds
[   87.084687] EXT3 FS on sda3, internal journal
[   87.084691] EXT3-fs: mounted filesystem with ordered data mode.
```

---

### Post by SpaceTeddy on 2008-02-09
ok... i can't really see much, and compared to my own computer and a vm this looks kind of normal to me... except the huge timegap right after mounting the file system.
i am nor really sure if this is a harddrive problem there some usb thing choking - but that is a wait of 60 seconds...

try disconnection all usb devices, or even disabling all usb in the bios... and see how it behaves then. also, if you still have an install cd, how does booting this one react. is it slow there too ? 

on an off chance that it is your acpi, which does throw erros, but not many,
try to normally boot the linux, but with slightly different parameters... 
when in grub, select the normal boot option in the grub menu and instead if pressing enter press e. this should give you a menu of the grub boot options. select the kernel line (should look like this :
*/boot/vmlinuz-2.6.22-14-generic root=UUID=67397eb5-badc-4989-bb6d-a94f98666f69 ro quiet spash*) and press e once more. That should kick you into edit mode. delete the delete the quiet and splash, Then, at the end add *ACPI=off*. press enter to finish editing. when back at the selection menu with all the grub setting (which should now include your modified kernel line), press b for booting.

i don't know if this will work, but if it acctually gets you as far as a blank screen (after giving you heaps of debug messages), press ctrl+alt+F1. there should be a console there you can log into...

i hope i am not telling you stuff you have already tried :)

---

### Post by ilwa7esh on 2008-02-09
Ok i will try this, I am running from the live cd and its  booting normally so its not a hardware issue i guess. I get back with what happened and thank you for ur help

---

### Post by ilwa7esh on 2008-02-09
ok that didnt work so i reinstalled ubuntu, its working now and am happy that all my settings and files are still the same :D (good thing i partitioned my drive)
but thank you for your help and time

---

