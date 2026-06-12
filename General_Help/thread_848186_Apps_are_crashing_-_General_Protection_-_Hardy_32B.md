---
title: "Apps are crashing - General Protection - Hardy 32Bit"
date: 2008-07-03
forum: General Help
---

### Post by Frazier on 2008-07-03
Hello There,

I've to machines running Ubuntu Hardy Heron, a 64Bit and a 32Bit one, and I'm experiencing random application crashes on the 32Bit one.

The application and time off the incident is random. Just before i wrote this Thread I've got one Gnome-Panel, one Synaptic and one Nautilus crash.
The applications are crashing and reappearing short after.

The errors are listed in kern.log and massages as follows:
(kern.log - **last three entries**)

```
Jul  3 14:30:24 nici kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul  3 14:30:24 nici kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Jul  3 14:30:24 nici kernel: Symbols match kernel version 2.6.24.
Jul  3 14:30:24 nici kernel: Loaded 27139 symbols from 87 modules.
Jul  3 14:30:24 nici kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  3 14:30:24 nici kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  3 14:30:24 nici kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul  3 14:30:24 nici kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  3 14:30:24 nici kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jul  3 14:30:24 nici kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jul  3 14:30:24 nici kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul  3 14:30:24 nici kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
Jul  3 14:30:24 nici kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
Jul  3 14:30:24 nici kernel: [    0.000000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
Jul  3 14:30:24 nici kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jul  3 14:30:24 nici kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul  3 14:30:24 nici kernel: [    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
Jul  3 14:30:24 nici kernel: [    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
Jul  3 14:30:24 nici kernel: [    0.000000] 127MB HIGHMEM available.
Jul  3 14:30:24 nici kernel: [    0.000000] 896MB LOWMEM available.
Jul  3 14:30:24 nici kernel: [    0.000000] found SMP MP-table at 000fbc70
Jul  3 14:30:24 nici kernel: [    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
Jul  3 14:30:24 nici kernel: [    0.000000] Zone PFN ranges:
Jul  3 14:30:24 nici kernel: [    0.000000]   DMA             0 ->     4096
Jul  3 14:30:24 nici kernel: [    0.000000]   Normal       4096 ->   229376
Jul  3 14:30:24 nici kernel: [    0.000000]   HighMem    229376 ->   262128
Jul  3 14:30:24 nici kernel: [    0.000000] Movable zone start PFN for each node
Jul  3 14:30:24 nici kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul  3 14:30:24 nici kernel: [    0.000000]     0:        0 ->   262128
Jul  3 14:30:24 nici kernel: [    0.000000] On node 0 totalpages: 262128
Jul  3 14:30:24 nici kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul  3 14:30:24 nici kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul  3 14:30:24 nici kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Jul  3 14:30:24 nici kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Jul  3 14:30:24 nici kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Jul  3 14:30:24 nici kernel: [    0.000000]   HighMem zone: 255 pages used for memmap
Jul  3 14:30:24 nici kernel: [    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
Jul  3 14:30:24 nici kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Jul  3 14:30:24 nici kernel: [    0.000000] DMI 2.3 present.
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FAA40 checksum 0
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: RSDP 000FAA40, 0014 (r0 AMI   )
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: RSDT 3FFF0000, 002C (r1 AMIINT SiS740XX     1000 MSFT  100000B)
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: FACP 3FFF0030, 0081 (r1 AMIINT SiS740XX       11 MSFT  100000B)
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: DSDT 3FFF0120, 3300 (r1    SiS      746      100 INTL  2002024)
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: FACS 3FFF8000, 0040
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: APIC 3FFF00C0, 005A (r1 AMIINT SiS740XX     1000 MSFT  100000B)
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul  3 14:30:24 nici kernel: [    0.000000] Processor #0 6:10 APIC version 16
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul  3 14:30:24 nici kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul  3 14:30:24 nici kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul  3 14:30:24 nici kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul  3 14:30:24 nici kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  3 14:30:24 nici kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Jul  3 14:30:24 nici kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jul  3 14:30:24 nici kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul  3 14:30:24 nici kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul  3 14:30:24 nici kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260081
Jul  3 14:30:24 nici kernel: [    0.000000] Kernel command line: root=UUID=292ad298-ddc5-4d6f-af69-184a045550d7 ro quiet splash
Jul  3 14:30:24 nici kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Jul  3 14:30:24 nici kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Jul  3 14:30:24 nici kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul  3 14:30:24 nici kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul  3 14:30:24 nici kernel: [    0.000000] Initializing CPU#0
Jul  3 14:30:24 nici kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jul  3 14:30:24 nici kernel: [    0.000000] Detected 1929.141 MHz processor.
Jul  3 14:30:24 nici kernel: [   20.003086] Console: colour VGA+ 80x25
Jul  3 14:30:24 nici kernel: [   20.003090] console [tty0] enabled
Jul  3 14:30:24 nici kernel: [   20.003957] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul  3 14:30:24 nici kernel: [   20.004630] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  3 14:30:24 nici kernel: [   20.044454] Memory: 1027360k/1048512k available (2177k kernel code, 20464k reserved, 1006k data, 368k init, 131008k highmem)
Jul  3 14:30:24 nici kernel: [   20.044464] virtual kernel memory layout:
Jul  3 14:30:24 nici kernel: [   20.044465]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Jul  3 14:30:24 nici kernel: [   20.044466]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul  3 14:30:24 nici kernel: [   20.044467]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jul  3 14:30:24 nici kernel: [   20.044468]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jul  3 14:30:24 nici kernel: [   20.044470]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Jul  3 14:30:24 nici kernel: [   20.044471]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
Jul  3 14:30:24 nici kernel: [   20.044472]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
Jul  3 14:30:24 nici kernel: [   20.044476] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul  3 14:30:24 nici kernel: [   20.044542] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Jul  3 14:30:24 nici kernel: [   20.124445] Calibrating delay using timer specific routine.. 3860.51 BogoMIPS (lpj=7721039)
Jul  3 14:30:24 nici kernel: [   20.124491] Security Framework initialized
Jul  3 14:30:24 nici kernel: [   20.124503] SELinux:  Disabled at boot.
Jul  3 14:30:24 nici kernel: [   20.124532] AppArmor: AppArmor initialized
Jul  3 14:30:24 nici kernel: [   20.124539] Failure registering capabilities with primary security module.
Jul  3 14:30:24 nici kernel: [   20.124551] Mount-cache hash table entries: 512
Jul  3 14:30:24 nici kernel: [   20.124741] Initializing cgroup subsys ns
Jul  3 14:30:24 nici kernel: [   20.124748] Initializing cgroup subsys cpuacct
Jul  3 14:30:24 nici kernel: [   20.124762] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 00000000
Jul  3 14:30:24 nici kernel: [   20.124773] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul  3 14:30:24 nici kernel: [   20.124776] CPU: L2 Cache: 512K (64 bytes/line)
Jul  3 14:30:24 nici kernel: [   20.124780] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000 00000000
Jul  3 14:30:24 nici kernel: [   20.124795] Compat vDSO mapped to ffffe000.
Jul  3 14:30:24 nici kernel: [   20.124815] Checking 'hlt' instruction... OK.
Jul  3 14:30:24 nici kernel: [   20.140746] SMP alternatives: switching to UP code
Jul  3 14:30:24 nici kernel: [   20.142049] Freeing SMP alternatives: 11k freed
Jul  3 14:30:24 nici kernel: [   20.142199] Early unpacking initramfs... done
Jul  3 14:30:24 nici kernel: [   20.490964] ACPI: Core revision 20070126
Jul  3 14:30:24 nici kernel: [   20.491068] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul  3 14:30:24 nici kernel: [   20.492493] CPU0: AMD Athlon(tm) XP 2600+ stepping 00
Jul  3 14:30:24 nici kernel: [   20.492519] Total of 1 processors activated (3860.51 BogoMIPS).
Jul  3 14:30:24 nici kernel: [   20.492639] ENABLING IO-APIC IRQs
Jul  3 14:30:24 nici kernel: [   20.492814] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul  3 14:30:24 nici kernel: [   20.639755] Brought up 1 CPUs
Jul  3 14:30:24 nici kernel: [   20.639789] CPU0 attaching sched-domain:
Jul  3 14:30:24 nici kernel: [   20.639792]  domain 0: span 01
Jul  3 14:30:24 nici kernel: [   20.639794]   groups: 01
Jul  3 14:30:24 nici kernel: [   20.640030] net_namespace: 64 bytes
Jul  3 14:30:24 nici kernel: [   20.640040] Booting paravirtualized kernel on bare hardware
Jul  3 14:30:24 nici kernel: [   20.640528] Time: 14:29:57  Date: 07/03/08
Jul  3 14:30:24 nici kernel: [   20.640566] NET: Registered protocol family 16
Jul  3 14:30:24 nici kernel: [   20.640830] EISA bus registered
Jul  3 14:30:24 nici kernel: [   20.640853] ACPI: bus type pci registered
Jul  3 14:30:24 nici kernel: [   20.642214] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
Jul  3 14:30:24 nici kernel: [   20.642217] PCI: Using configuration type 1
Jul  3 14:30:24 nici kernel: [   20.642228] Setting up standard PCI resources
Jul  3 14:30:24 nici kernel: [   20.644348] ACPI: EC: Look up EC in DSDT
Jul  3 14:30:24 nici kernel: [   20.647290] ACPI: Interpreter enabled
Jul  3 14:30:24 nici kernel: [   20.647294] ACPI: (supports S0 S1 S4 S5)
Jul  3 14:30:24 nici kernel: [   20.647307] ACPI: Using IOAPIC for interrupt routing
Jul  3 14:30:24 nici kernel: [   20.651332] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul  3 14:30:24 nici kernel: [   20.651527] Enabling SiS 96x SMBus.
Jul  3 14:30:24 nici kernel: [   20.652113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul  3 14:30:24 nici kernel: [   20.660171] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jul  3 14:30:24 nici kernel: [   20.660263] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul  3 14:30:24 nici kernel: [   20.660350] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
Jul  3 14:30:24 nici kernel: [   20.660435] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jul  3 14:30:24 nici kernel: [   20.660522] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jul  3 14:30:24 nici kernel: [   20.660609] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 *12 14 15)
Jul  3 14:30:24 nici kernel: [   20.660696] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul  3 14:30:24 nici kernel: [   20.660781] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jul  3 14:30:24 nici kernel: [   20.660882] ACPI: Power Resource [URP1] (off)
Jul  3 14:30:24 nici kernel: [   20.660908] ACPI: Power Resource [URP2] (off)
Jul  3 14:30:24 nici kernel: [   20.660932] ACPI: Power Resource [FDDP] (off)
Jul  3 14:30:24 nici kernel: [   20.660956] ACPI: Power Resource [LPTP] (off)
Jul  3 14:30:24 nici kernel: [   20.661005] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul  3 14:30:24 nici kernel: [   20.661043] pnp: PnP ACPI init
Jul  3 14:30:24 nici kernel: [   20.661050] ACPI: bus type pnp registered
Jul  3 14:30:24 nici kernel: [   20.663254] pnp: PnP ACPI: found 11 devices
Jul  3 14:30:24 nici kernel: [   20.663256] ACPI: ACPI bus type pnp unregistered
Jul  3 14:30:24 nici kernel: [   20.663261] PnPBIOS: Disabled by ACPI PNP
Jul  3 14:30:24 nici kernel: [   20.663549] PCI: Using ACPI for IRQ routing
Jul  3 14:30:24 nici kernel: [   20.663552] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul  3 14:30:24 nici kernel: [   20.675668] NET: Registered protocol family 8
Jul  3 14:30:24 nici kernel: [   20.675670] NET: Registered protocol family 20
Jul  3 14:30:24 nici kernel: [   20.675764] AppArmor: AppArmor Filesystem Enabled
Jul  3 14:30:24 nici kernel: [   20.679627] Time: tsc clocksource has been installed.
Jul  3 14:30:24 nici kernel: [   20.687657] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jul  3 14:30:24 nici kernel: [   20.687660] system 00:01: ioport range 0x295-0x296 has been reserved
Jul  3 14:30:24 nici kernel: [   20.687663] system 00:01: ioport range 0x800-0x87f has been reserved
Jul  3 14:30:24 nici kernel: [   20.687666] system 00:01: ioport range 0x880-0x8ff has been reserved
Jul  3 14:30:24 nici kernel: [   20.687669] system 00:01: ioport range 0xc00-0xc1f has been reserved
Jul  3 14:30:24 nici kernel: [   20.687673] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul  3 14:30:24 nici kernel: [   20.718117] PCI: Bridge: 0000:00:01.0
Jul  3 14:30:24 nici kernel: [   20.718120]   IO window: disabled.
Jul  3 14:30:24 nici kernel: [   20.718127]   MEM window: cbd00000-cfefffff
Jul  3 14:30:24 nici kernel: [   20.718131]   PREFETCH window: aba00000-cbbfffff
Jul  3 14:30:24 nici kernel: [   20.718158] NET: Registered protocol family 2
Jul  3 14:30:24 nici kernel: [   20.755624] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  3 14:30:24 nici kernel: [   20.756073] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul  3 14:30:24 nici kernel: [   20.758352] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul  3 14:30:24 nici kernel: [   20.759565] TCP: Hash tables configured (established 131072 bind 65536)
Jul  3 14:30:24 nici kernel: [   20.759568] TCP reno registered
Jul  3 14:30:24 nici kernel: [   20.771692] checking if image is initramfs... it is
Jul  3 14:30:24 nici kernel: [   21.218835] Switched to high resolution mode on CPU 0
Jul  3 14:30:24 nici kernel: [   21.422901] Freeing initrd memory: 7329k freed
Jul  3 14:30:24 nici kernel: [   21.423775] audit: initializing netlink socket (disabled)
Jul  3 14:30:24 nici kernel: [   21.423797] audit(1215095398.276:1): initialized
Jul  3 14:30:24 nici kernel: [   21.424001] highmem bounce pool size: 64 pages
Jul  3 14:30:24 nici kernel: [   21.426191] VFS: Disk quotas dquot_6.5.1
Jul  3 14:30:24 nici kernel: [   21.426279] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  3 14:30:24 nici kernel: [   21.426438] io scheduler noop registered
Jul  3 14:30:24 nici kernel: [   21.426441] io scheduler anticipatory registered
Jul  3 14:30:24 nici kernel: [   21.426459] io scheduler deadline registered
Jul  3 14:30:24 nici kernel: [   21.426470] io scheduler cfq registered (default)
Jul  3 14:30:24 nici kernel: [   21.426537] Boot video device is 0000:01:00.0
Jul  3 14:30:24 nici kernel: [   21.426864] isapnp: Scanning for PnP cards...
Jul  3 14:30:24 nici kernel: [   21.779927] isapnp: No Plug & Play device found
Jul  3 14:30:24 nici kernel: [   21.812782] Real Time Clock Driver v1.12ac
Jul  3 14:30:24 nici kernel: [   21.812910] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul  3 14:30:24 nici kernel: [   21.813056] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul  3 14:30:24 nici kernel: [   21.813785] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul  3 14:30:24 nici kernel: [   21.814715] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul  3 14:30:24 nici kernel: [   21.814796] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul  3 14:30:24 nici kernel: [   21.814903] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jul  3 14:30:24 nici kernel: [   21.814907] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jul  3 14:30:24 nici kernel: [   21.815021] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  3 14:30:24 nici kernel: [   21.818282] mice: PS/2 mouse device common for all mice
Jul  3 14:30:24 nici kernel: [   21.818418] EISA: Probing bus 0 at eisa.0
Jul  3 14:30:24 nici kernel: [   21.818455] EISA: Detected 0 cards.
Jul  3 14:30:24 nici kernel: [   21.818460] cpuidle: using governor ladder
Jul  3 14:30:24 nici kernel: [   21.818462] cpuidle: using governor menu
Jul  3 14:30:24 nici kernel: [   21.818636] NET: Registered protocol family 1
Jul  3 14:30:24 nici kernel: [   21.818670] Using IPI No-Shortcut mode
Jul  3 14:30:24 nici kernel: [   21.818715] registered taskstats version 1
Jul  3 14:30:24 nici kernel: [   21.818819]   Magic number: 0:640:484
Jul  3 14:30:24 nici kernel: [   21.819073] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  3 14:30:24 nici kernel: [   21.819075] EDD information not available.
Jul  3 14:30:24 nici kernel: [   21.819653] Freeing unused kernel memory: 368k freed
Jul  3 14:30:24 nici kernel: [   21.845816] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul  3 14:30:24 nici kernel: [   23.067546] fuse init (API version 7.9)
Jul  3 14:30:24 nici kernel: [   23.728001] SCSI subsystem initialized
Jul  3 14:30:24 nici kernel: [   23.794805] usbcore: registered new interface driver usbfs
Jul  3 14:30:24 nici kernel: [   23.794838] usbcore: registered new interface driver hub
Jul  3 14:30:24 nici kernel: [   23.812415] libata version 3.00 loaded.
Jul  3 14:30:24 nici kernel: [   23.830459] usbcore: registered new device driver usb
Jul  3 14:30:24 nici kernel: [   23.831275] sis900.c: v1.08.10 Apr. 2 2006
Jul  3 14:30:24 nici kernel: [   23.831352] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
Jul  3 14:30:24 nici kernel: [   23.832372] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
Jul  3 14:30:24 nici kernel: [   23.842577] 0000:00:04.0: Using transceiver found at address 1 as default
Jul  3 14:30:24 nici kernel: [   23.845257] eth0: SiS 900 PCI Fast Ethernet at 0xdc00, IRQ 16, 00:19:66:09:a6:1a
Jul  3 14:30:24 nici kernel: [   23.846603] pata_sis 0000:00:02.5: version 0.5.2
Jul  3 14:30:24 nici kernel: [   23.853145] scsi0 : pata_sis
Jul  3 14:30:24 nici kernel: [   23.854216] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jul  3 14:30:24 nici kernel: [   23.870614] scsi1 : pata_sis
Jul  3 14:30:24 nici kernel: [   23.871304] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jul  3 14:30:24 nici kernel: [   23.871308] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jul  3 14:30:24 nici kernel: [   23.922672] Floppy drive(s): fd0 is 1.44M
Jul  3 14:30:24 nici kernel: [   23.942252] FDC 0 is a post-1991 82077
Jul  3 14:30:24 nici kernel: [   24.058850] ata1.00: ATA-5: IC35L060AVVA07-0, VA3OA52A, max UDMA/100
Jul  3 14:30:24 nici kernel: [   24.058857] ata1.00: 120103200 sectors, multi 16: LBA 
Jul  3 14:30:24 nici kernel: [   24.059158] ata1.01: ATA-6: ExcelStor Technology J680, V32OA60A, max UDMA/100
Jul  3 14:30:24 nici kernel: [   24.059162] ata1.01: 160836480 sectors, multi 16: LBA48 
Jul  3 14:30:24 nici kernel: [   24.082716] ata1.00: configured for UDMA/100
Jul  3 14:30:24 nici kernel: [   24.106741] ata1.01: configured for UDMA/100
Jul  3 14:30:24 nici kernel: [   24.434043] ata2.00: ATA-7: Maxtor 6E040L0, NAR61EA0, max UDMA/133
Jul  3 14:30:24 nici kernel: [   24.434049] ata2.00: 80293248 sectors, multi 16: LBA 
Jul  3 14:30:24 nici kernel: [   24.434069] ata2.01: ATAPI:         DVD+RW RW5240, 1.08, max UDMA/33
Jul  3 14:30:24 nici kernel: [   24.434083] ata2.00: limited to UDMA/33 due to 40-wire cable
Jul  3 14:30:24 nici kernel: [   24.450007] ata2.00: configured for UDMA/33
Jul  3 14:30:24 nici kernel: [   24.621642] ata2.01: configured for UDMA/33
Jul  3 14:30:24 nici kernel: [   24.621807] scsi 0:0:0:0: Direct-Access     ATA      IC35L060AVVA07-0 VA3O PQ: 0 ANSI: 5
Jul  3 14:30:24 nici kernel: [   24.622289] scsi 0:0:1:0: Direct-Access     ATA      ExcelStor Techno V32O PQ: 0 ANSI: 5
Jul  3 14:30:24 nici kernel: [   24.622624] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
Jul  3 14:30:24 nici kernel: [   24.624454] scsi 1:0:1:0: CD-ROM                     DVD+RW RW5240    1.08 PQ: 0 ANSI: 5
Jul  3 14:30:24 nici kernel: [   24.626906] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 17
Jul  3 14:30:24 nici kernel: [   24.626923] ohci_hcd 0000:00:03.0: OHCI Host Controller
Jul  3 14:30:24 nici kernel: [   24.627283] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Jul  3 14:30:24 nici kernel: [   24.627306] ohci_hcd 0000:00:03.0: irq 17, io mem 0xcfffd000
Jul  3 14:30:24 nici kernel: [   24.683466] usb usb1: configuration #1 chosen from 1 choice
Jul  3 14:30:24 nici kernel: [   24.683497] hub 1-0:1.0: USB hub found
Jul  3 14:30:24 nici kernel: [   24.683508] hub 1-0:1.0: 3 ports detected
Jul  3 14:30:24 nici kernel: [   24.785310] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 18
Jul  3 14:30:24 nici kernel: [   24.785333] ohci_hcd 0000:00:03.1: OHCI Host Controller
Jul  3 14:30:24 nici kernel: [   24.785361] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Jul  3 14:30:24 nici kernel: [   24.785383] ohci_hcd 0000:00:03.1: irq 18, io mem 0xcfffe000
Jul  3 14:30:24 nici kernel: [   24.843183] usb usb2: configuration #1 chosen from 1 choice
Jul  3 14:30:24 nici kernel: [   24.843221] hub 2-0:1.0: USB hub found
Jul  3 14:30:24 nici kernel: [   24.843231] hub 2-0:1.0: 3 ports detected
Jul  3 14:30:24 nici kernel: [   24.945407] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 19
Jul  3 14:30:24 nici kernel: [   24.945426] ehci_hcd 0000:00:03.2: EHCI Host Controller
Jul  3 14:30:24 nici kernel: [   24.945464] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Jul  3 14:30:24 nici kernel: [   24.945509] PCI: cache line size of 64 is not supported by device 0000:00:03.2
Jul  3 14:30:24 nici kernel: [   24.945522] ehci_hcd 0000:00:03.2: irq 19, io mem 0xcffff000
Jul  3 14:30:24 nici kernel: [   25.088677] usb 1-1: new full speed USB device using ohci_hcd and address 2
Jul  3 14:30:24 nici kernel: [   25.100653] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul  3 14:30:24 nici kernel: [   25.100823] usb usb3: configuration #1 chosen from 1 choice
Jul  3 14:30:24 nici kernel: [   25.100852] hub 3-0:1.0: USB hub found
Jul  3 14:30:24 nici kernel: [   25.100861] hub 3-0:1.0: 6 ports detected
Jul  3 14:30:24 nici kernel: [   25.220579] Driver 'sd' needs updating - please use bus_type methods
Jul  3 14:30:24 nici kernel: [   25.220706] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
Jul  3 14:30:24 nici kernel: [   25.220724] sd 0:0:0:0: [sda] Write Protect is off
Jul  3 14:30:24 nici kernel: [   25.220727] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul  3 14:30:24 nici kernel: [   25.220748] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  3 14:30:24 nici kernel: [   25.220809] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
Jul  3 14:30:24 nici kernel: [   25.220820] sd 0:0:0:0: [sda] Write Protect is off
Jul  3 14:30:24 nici kernel: [   25.220823] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul  3 14:30:24 nici kernel: [   25.220839] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  3 14:30:24 nici kernel: [   25.220843]  sda: sda1 sda2 sda3
Jul  3 14:30:24 nici kernel: [   25.234587] sd 0:0:0:0: [sda] Attached SCSI disk
Jul  3 14:30:24 nici kernel: [   25.234666] sd 0:0:1:0: [sdb] 160836480 512-byte hardware sectors (82348 MB)
Jul  3 14:30:24 nici kernel: [   25.234684] sd 0:0:1:0: [sdb] Write Protect is off
Jul  3 14:30:24 nici kernel: [   25.234687] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jul  3 14:30:24 nici kernel: [   25.234707] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  3 14:30:24 nici kernel: [   25.234758] sd 0:0:1:0: [sdb] 160836480 512-byte hardware sectors (82348 MB)
Jul  3 14:30:24 nici kernel: [   25.234769] sd 0:0:1:0: [sdb] Write Protect is off
Jul  3 14:30:24 nici kernel: [   25.234772] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jul  3 14:30:24 nici kernel: [   25.234788] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  3 14:30:24 nici kernel: [   25.234792]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
Jul  3 14:30:24 nici kernel: [   25.247795]  sdb1 sdb2 < sdb5 >
Jul  3 14:30:24 nici kernel: [   25.260818] sd 0:0:1:0: [sdb] Attached SCSI disk
Jul  3 14:30:24 nici kernel: [   25.260917] sd 1:0:0:0: [sdc] 80293248 512-byte hardware sectors (41110 MB)
Jul  3 14:30:24 nici kernel: [   25.260935] sd 1:0:0:0: [sdc] Write Protect is off
Jul  3 14:30:24 nici kernel: [   25.260938] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jul  3 14:30:24 nici kernel: [   25.260958] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  3 14:30:24 nici kernel: [   25.261011] sd 1:0:0:0: [sdc] 80293248 512-byte hardware sectors (41110 MB)
Jul  3 14:30:24 nici kernel: [   25.261022] sd 1:0:0:0: [sdc] Write Protect is off
Jul  3 14:30:24 nici kernel: [   25.261025] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jul  3 14:30:24 nici kernel: [   25.261041] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  3 14:30:24 nici kernel: [   25.261046]  sdc:<6>usb 1-1: new full speed USB device using ohci_hcd and address 3
Jul  3 14:30:24 nici kernel: [   27.083413] usb 1-1: configuration #1 chosen from 1 choice
Jul  3 14:30:24 nici kernel: [   27.364570]  sdc1 sdc2 < sdc5 >
Jul  3 14:30:24 nici kernel: [   27.379763] sd 1:0:0:0: [sdc] Attached SCSI disk
Jul  3 14:30:24 nici kernel: [   27.389098] usb 1-2: new full speed USB device using ohci_hcd and address 4
Jul  3 14:30:24 nici kernel: [   27.396610] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  3 14:30:24 nici kernel: [   27.396635] sd 0:0:1:0: Attached scsi generic sg1 type 0
Jul  3 14:30:24 nici kernel: [   27.396658] sd 1:0:0:0: Attached scsi generic sg2 type 0
Jul  3 14:30:24 nici kernel: [   27.396679] sr 1:0:1:0: Attached scsi generic sg3 type 5
Jul  3 14:30:24 nici kernel: [   27.401395] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jul  3 14:30:24 nici kernel: [   27.401404] Uniform CD-ROM driver Revision: 3.20
Jul  3 14:30:24 nici kernel: [   27.401492] sr 1:0:1:0: Attached scsi CD-ROM sr0
Jul  3 14:30:24 nici kernel: [   27.596565] usb 1-2: configuration #1 chosen from 1 choice
Jul  3 14:30:24 nici kernel: [   27.894384] Attempting manual resume
Jul  3 14:30:24 nici kernel: [   27.894390] swsusp: Resume From Partition 8:1
Jul  3 14:30:24 nici kernel: [   27.894392] PM: Checking swsusp image.
Jul  3 14:30:24 nici kernel: [   27.894564] PM: Resume from disk failed.
Jul  3 14:30:24 nici kernel: [   27.900598] usb 2-1: new low speed USB device using ohci_hcd and address 2
Jul  3 14:30:24 nici kernel: [   27.924096] kjournald starting.  Commit interval 5 seconds
Jul  3 14:30:24 nici kernel: [   27.924118] EXT3-fs: mounted filesystem with ordered data mode.
Jul  3 14:30:24 nici kernel: [   28.113711] usb 2-1: configuration #1 chosen from 1 choice
Jul  3 14:30:24 nici kernel: [   28.423431] usb 2-2: new full speed USB device using ohci_hcd and address 3
Jul  3 14:30:24 nici kernel: [   28.647830] usb 2-2: configuration #1 chosen from 1 choice
Jul  3 14:30:24 nici kernel: [   37.110180] Linux agpgart interface v0.102
Jul  3 14:30:24 nici kernel: [   37.441276] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  3 14:30:24 nici kernel: [   37.493247] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  3 14:30:24 nici kernel: [   37.627109] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul  3 14:30:24 nici kernel: [   37.712901] agpgart: Detected SiS chipset - id:1857
Jul  3 14:30:24 nici kernel: [   37.718109] agpgart: AGP aperture is 64M @ 0xd0000000
Jul  3 14:30:24 nici kernel: [   37.807428] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
Jul  3 14:30:24 nici kernel: [   37.932704] input: Power Button (FF) as /devices/virtual/input/input3
Jul  3 14:30:24 nici kernel: [   37.944421] ACPI: Power Button (FF) [PWRF]
Jul  3 14:30:24 nici kernel: [   37.944606] input: Power Button (CM) as /devices/virtual/input/input4
Jul  3 14:30:24 nici kernel: [   37.960376] ACPI: Power Button (CM) [PWRB]
Jul  3 14:30:24 nici kernel: [   38.619506] parport_pc 00:09: reported by Plug and Play ACPI
Jul  3 14:30:24 nici kernel: [   38.619614] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jul  3 14:30:24 nici kernel: [   38.736053] nvidia: module license 'NVIDIA' taints kernel.
Jul  3 14:30:24 nici kernel: [   40.707791] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 20
Jul  3 14:30:24 nici kernel: [   40.725729] gameport: ES1938 is pci0000:00:0a.0/gameport0, io 0xc800, speed 1065kHz
Jul  3 14:30:24 nici kernel: [   40.772272] Linux video capture interface: v2.00
Jul  3 14:30:24 nici kernel: [   40.806975] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
Jul  3 14:30:24 nici kernel: [   40.807553] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
Jul  3 14:30:24 nici kernel: [   40.885676] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
Jul  3 14:30:24 nici kernel: [   40.972338] usbcore: registered new interface driver snd-usb-audio
Jul  3 14:30:24 nici kernel: [   40.974953] usb 1-1: SN9C105 PC Camera Controller detected (vid:pid 0x0C45:0x60FE)
Jul  3 14:30:24 nici kernel: [   41.250511] usb 1-1: OV7630 image sensor detected
Jul  3 14:30:24 nici kernel: [   42.741966] usb 1-1: Initialization succeeded
Jul  3 14:30:24 nici kernel: [   42.742040] usb 1-1: V4L2 device registered as /dev/video0
Jul  3 14:30:24 nici kernel: [   42.742043] usb 1-1: Optional device control through 'sysfs' interface disabled
Jul  3 14:30:24 nici kernel: [   42.742085] usbcore: registered new interface driver sn9c102
Jul  3 14:30:24 nici kernel: [   42.747083] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
Jul  3 14:30:24 nici kernel: [   42.747114] usbcore: registered new interface driver usblp
Jul  3 14:30:24 nici kernel: [   42.747347] usbcore: registered new interface driver hiddev
Jul  3 14:30:24 nici kernel: [   42.752320] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:03.1/usb2/2-1/2-1:1.0/input/input5
Jul  3 14:30:24 nici kernel: [   42.776802] input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:03.1-1
Jul  3 14:30:24 nici kernel: [   42.776830] usbcore: registered new interface driver usbhid
Jul  3 14:30:24 nici kernel: [   42.776836] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jul  3 14:30:24 nici kernel: [   43.880123] lp0: using parport0 (interrupt-driven).
Jul  3 14:30:24 nici kernel: [   43.944307] Adding 1622524k swap on /dev/sda1.  Priority:-1 extents:1 across:1622524k
Jul  3 14:30:24 nici kernel: [   44.509818] EXT3 FS on sda2, internal journal
Jul  3 14:30:24 nici kernel: [   45.254260] kjournald starting.  Commit interval 5 seconds
Jul  3 14:30:24 nici kernel: [   45.254414] EXT3 FS on sda3, internal journal
Jul  3 14:30:24 nici kernel: [   45.254421] EXT3-fs: mounted filesystem with ordered data mode.
Jul  3 14:30:24 nici kernel: [   46.318956] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  3 14:30:24 nici kernel: [   46.788953] No dock devices found.
Jul  3 14:30:25 nici kernel: [   47.918013] apm: BIOS not found.
Jul  3 14:30:25 nici kernel: [   48.032591] ppdev: user-space parallel port driver
Jul  3 14:30:25 nici kernel: [   48.189213] audit(1215088225.425:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4957 profile="/usr/sbin/cupsd" namespace="default"
Jul  3 14:30:28 nici kernel: [   51.014460] Bluetooth: Core ver 2.11
Jul  3 14:30:28 nici kernel: [   51.015423] NET: Registered protocol family 31
Jul  3 14:30:28 nici kernel: [   51.015429] Bluetooth: HCI device and connection manager initialized
Jul  3 14:30:28 nici kernel: [   51.015434] Bluetooth: HCI socket layer initialized
Jul  3 14:30:28 nici kernel: [   51.056719] Bluetooth: L2CAP ver 2.9
Jul  3 14:30:28 nici kernel: [   51.056727] Bluetooth: L2CAP socket layer initialized
Jul  3 14:30:28 nici kernel: [   51.129461] Bluetooth: RFCOMM socket layer initialized
Jul  3 14:30:28 nici kernel: [   51.129488] Bluetooth: RFCOMM TTY layer initialized
Jul  3 14:30:28 nici kernel: [   51.129491] Bluetooth: RFCOMM ver 1.8
Jul  3 14:30:30 nici kernel: [   52.841863] eth0: Media Link On 100mbps full-duplex 
Jul  3 14:30:31 nici kernel: [   54.555051] NET: Registered protocol family 17
Jul  3 14:30:31 nici kernel: [   54.672395] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jul  3 14:30:31 nici kernel: [   54.672808] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul  3 14:30:31 nici kernel: [   54.673795] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul  3 14:30:33 nici kernel: [   56.194231] NET: Registered protocol family 10
Jul  3 14:30:33 nici kernel: [   56.194475] lo: Disabled Privacy Extensions
Jul  3 14:30:44 nici kernel: [   66.359541] eth0: no IPv6 routers present
Jul  3 14:34:39 nici kernel: [  300.619520] gnome-panel[5752] general protection eip:b6f78b32 esp:bf9dcf00 error:0
Jul  3 14:37:49 nici kernel: [  491.066685] synaptic[5903] general protection eip:b75dab32 esp:bfda5570 error:0
Jul  3 14:43:46 nici kernel: [  847.374140] nautilus[5754] general protection eip:b701ab32 esp:bfed2700 error:0
```

Has anyone else experienced such things or can someone tell me if this is a RAM or a kernel issue or anything else?

The machine is a AMD Athlon(tm) XP 2600+ with 2.6.24-19 kernel.

Greetings,
Frazier

---

