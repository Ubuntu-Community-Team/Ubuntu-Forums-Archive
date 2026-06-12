---
title: "System locks up"
date: 2007-06-28
forum: General Help
---

### Post by strikeback03 on 2007-06-28
my system has occasionally locked up after several hours of use, never enough to really be a problem though.  Today however it has locked up 3 times, each within 5 minutes of booting.  Everything is locked - no keyboard or mouse, so I can't try to kill X or anything.  How do I find out what is wrong?

---

### Post by invalid on 2007-06-28
There may be some useful information in your system log (/var/log/syslog) around the time of the lockup. I would take a look at this - and you can post it if you would like us to take a loot at it.

---

### Post by strikeback03 on 2007-11-04
Seems under Feisty that most of the lockup problems were related to Firefox, esp. when trying to close it.  I hoped the upgrade to Gutsy would help, but it seems to be worse.  Downloaded the upgrade last night, now the system is completely unstable.  2 kernels were installed, 2.6.20 and 2.6.22.  With 2.6.22 the system successfully boots about 2/3 the time, but usually locks up within a few minutes.  I even booted then left it for a few hrs, it locked up just sitting.  X always fails to start with the 2.6.20 kernel, so that has not been any help.

Here is the syslog from when I let it sit for a few hrs.  When I came home to it the screensaver image was frozen on screen, no response to anything.

```
 Nov  4 09:40:06 Ezekiel syslogd 1.4.1#21ubuntu3: restart.
Nov  4 09:40:06 Ezekiel kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov  4 09:40:06 Ezekiel kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov  4 09:40:06 Ezekiel kernel: Symbols match kernel version 2.6.22.
Nov  4 09:40:06 Ezekiel kernel: No module symbols loaded - kernel modules not enabled. 
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fedf800 (usable)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]  BIOS-e820: 000000007fedf800 - 000000007fee0000 (reserved)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] 1150MB HIGHMEM available.
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] 896MB LOWMEM available.
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] found SMP MP-table at 000f3ba0
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Entering add_active_range(0, 0, 523999) 0 entries of 256 used
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Zone PFN ranges:
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]   DMA             0 ->     4096
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]   Normal       4096 ->   229376
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]   HighMem    229376 ->   523999
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]     0:        0 ->   523999
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] On node 0 totalpages: 523999
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]   HighMem zone: 292322 pages, LIFO batch:31
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] DMI 2.4 present.
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7D10 checksum 0
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: RSDP 000F7D10, 0014 (r0 IntelR)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: DSDT 7FEE3180, 43C0 (r1 INTELR AWRDACPI     1000 MSFT  100000E)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: HPET 7FEE7680, 0038 (r1 IntelR AWRDACPI 42302E31 AWRD       98)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: MCFG 7FEE7700, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: APIC 7FEE7580, 0084 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: SSDT 7FEE7780, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: SSDT 7FEE7C10, 02F1 (r1  PmRef    CpuPm     3000 INTL 20041203)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Nov  4 09:40:06 Ezekiel kernel: [    0.000000]     Virtual Wire compatibility mode.
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Processor #0 6:15 APIC version 17
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Processor #1 6:15 APIC version 17
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] I/O APIC #4 Version 17 at 0xFEC00000.
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Processors: 2
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Built 1 zonelists.  Total pages: 519906
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Kernel command line: root=UUID=a531c6c6-3243-4364-bbaf-50d1452bef42 ro all_generic_ide noapic nolapic quiet splash
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Initializing CPU#0
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov  4 09:40:06 Ezekiel kernel: [    0.000000] Detected 2396.015 MHz processor.
Nov  4 09:40:06 Ezekiel kernel: [   37.980610] Console: colour VGA+ 80x25
Nov  4 09:40:06 Ezekiel kernel: [   37.980773] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov  4 09:40:06 Ezekiel kernel: [   37.980970] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  4 09:40:06 Ezekiel kernel: [   38.045154] Memory: 2066340k/2095996k available (2015k kernel code, 28248k reserved, 916k data, 364k init, 1178492k highmem)
Nov  4 09:40:06 Ezekiel kernel: [   38.045161] virtual kernel memory layout:
Nov  4 09:40:06 Ezekiel kernel: [   38.045161]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Nov  4 09:40:06 Ezekiel kernel: [   38.045162]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov  4 09:40:06 Ezekiel kernel: [   38.045163]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov  4 09:40:06 Ezekiel kernel: [   38.045164]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov  4 09:40:06 Ezekiel kernel: [   38.045165]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Nov  4 09:40:06 Ezekiel kernel: [   38.045166]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Nov  4 09:40:06 Ezekiel kernel: [   38.045166]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Nov  4 09:40:06 Ezekiel kernel: [   38.045168] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov  4 09:40:06 Ezekiel kernel: [   38.045194] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Nov  4 09:40:06 Ezekiel kernel: [   38.125153] Calibrating delay using timer specific routine.. 4795.49 BogoMIPS (lpj=9590994)
Nov  4 09:40:06 Ezekiel kernel: [   38.125171] Security Framework v1.0.0 initialized
Nov  4 09:40:06 Ezekiel kernel: [   38.125174] SELinux:  Disabled at boot.
Nov  4 09:40:06 Ezekiel kernel: [   38.125183] Mount-cache hash table entries: 512
Nov  4 09:40:06 Ezekiel kernel: [   38.125258] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Nov  4 09:40:06 Ezekiel kernel: [   38.125263] monitor/mwait feature present.
Nov  4 09:40:06 Ezekiel kernel: [   38.125264] using mwait in idle threads.
Nov  4 09:40:06 Ezekiel kernel: [   38.125267] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov  4 09:40:06 Ezekiel kernel: [   38.125269] CPU: L2 cache: 4096K
Nov  4 09:40:06 Ezekiel kernel: [   38.125270] CPU: Physical Processor ID: 0
Nov  4 09:40:06 Ezekiel kernel: [   38.125272] CPU: Processor Core ID: 0
Nov  4 09:40:06 Ezekiel kernel: [   38.125273] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Nov  4 09:40:06 Ezekiel kernel: [   38.125279] Compat vDSO mapped to ffffe000.
Nov  4 09:40:06 Ezekiel kernel: [   38.125287] Checking 'hlt' instruction... OK.
Nov  4 09:40:06 Ezekiel kernel: [   38.141227] SMP alternatives: switching to UP code
Nov  4 09:40:06 Ezekiel kernel: [   38.141540] Early unpacking initramfs... done
Nov  4 09:40:06 Ezekiel kernel: [   38.372254] ACPI: Core revision 20070126
Nov  4 09:40:06 Ezekiel kernel: [   38.372283] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov  4 09:40:06 Ezekiel kernel: [   38.373558] ACPI: setting ELCR to 0200 (from 0e20)
Nov  4 09:40:06 Ezekiel kernel: [   38.395243] CPU0: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
Nov  4 09:40:06 Ezekiel kernel: [   38.395256] SMP alternatives: switching to SMP code
Nov  4 09:40:06 Ezekiel kernel: [   38.395305] Booting processor 1/1 eip 3000
Nov  4 09:40:06 Ezekiel kernel: [   38.405566] Initializing CPU#1
Nov  4 09:40:06 Ezekiel kernel: [   38.484838] Calibrating delay using timer specific routine.. 4792.17 BogoMIPS (lpj=9584343)
Nov  4 09:40:06 Ezekiel kernel: [   38.484843] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Nov  4 09:40:06 Ezekiel kernel: [   38.484846] monitor/mwait feature present.
Nov  4 09:40:06 Ezekiel kernel: [   38.484848] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov  4 09:40:06 Ezekiel kernel: [   38.484850] CPU: L2 cache: 4096K
Nov  4 09:40:06 Ezekiel kernel: [   38.484851] CPU: Physical Processor ID: 0
Nov  4 09:40:06 Ezekiel kernel: [   38.484852] CPU: Processor Core ID: 1
Nov  4 09:40:06 Ezekiel kernel: [   38.484853] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Nov  4 09:40:06 Ezekiel kernel: [   38.485428] CPU1: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
Nov  4 09:40:06 Ezekiel kernel: [   38.485442] Total of 2 processors activated (9587.66 BogoMIPS).
Nov  4 09:40:06 Ezekiel kernel: [   38.592822] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov  4 09:40:06 Ezekiel kernel: [   38.612817] Brought up 2 CPUs
Nov  4 09:40:06 Ezekiel kernel: [   38.803993] migration_cost=29
Nov  4 09:40:06 Ezekiel kernel: [   38.804083] Booting paravirtualized kernel on bare hardware
Nov  4 09:40:06 Ezekiel kernel: [   38.804133] Time:  9:39:49  Date: 10/04/107
Nov  4 09:40:06 Ezekiel kernel: [   38.804146] NET: Registered protocol family 16
Nov  4 09:40:06 Ezekiel kernel: [   38.804205] EISA bus registered
Nov  4 09:40:06 Ezekiel kernel: [   38.804209] ACPI: bus type pci registered
Nov  4 09:40:06 Ezekiel kernel: [   38.829747] PCI: PCI BIOS revision 3.00 entry at 0xfa030, last bus=4
Nov  4 09:40:06 Ezekiel kernel: [   38.829749] PCI: Using configuration type 1
Nov  4 09:40:06 Ezekiel kernel: [   38.829751] Setting up standard PCI resources
Nov  4 09:40:06 Ezekiel kernel: [   38.832264] ACPI: EC: Look up EC in DSDT
Nov  4 09:40:06 Ezekiel kernel: [   38.836415] ACPI: Interpreter enabled
Nov  4 09:40:06 Ezekiel kernel: [   38.836419] ACPI: (supports S0 S3 S4 S5)
Nov  4 09:40:06 Ezekiel kernel: [   38.836432] ACPI: Using PIC for interrupt routing
Nov  4 09:40:06 Ezekiel kernel: [   38.840969] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  4 09:40:06 Ezekiel kernel: [   38.840975] PCI: Probing PCI hardware (bus 00)
Nov  4 09:40:06 Ezekiel kernel: [   38.841475] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Nov  4 09:40:06 Ezekiel kernel: [   38.841478] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Nov  4 09:40:06 Ezekiel kernel: [   38.842174] PCI: Transparent bridge - 0000:00:1e.0
Nov  4 09:40:06 Ezekiel kernel: [   38.842217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov  4 09:40:06 Ezekiel kernel: [   38.842383] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Nov  4 09:40:06 Ezekiel kernel: [   38.842448] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
Nov  4 09:40:06 Ezekiel kernel: [   38.842518] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Nov  4 09:40:06 Ezekiel kernel: [   38.853392] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 9 *10 11 12 14 15)
Nov  4 09:40:06 Ezekiel kernel: [   38.853468] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 9 10 11 12 14 15)
Nov  4 09:40:06 Ezekiel kernel: [   38.853542] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *9 10 11 12 14 15)
Nov  4 09:40:06 Ezekiel kernel: [   38.853616] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 9 10 *11 12 14 15)
Nov  4 09:40:06 Ezekiel kernel: [   38.853690] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 9 *10 11 12 14 15)
Nov  4 09:40:06 Ezekiel kernel: [   38.853764] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 9 10 11 12 14 15) *0, disabled.
Nov  4 09:40:06 Ezekiel kernel: [   38.853839] ACPI: PCI Interrupt Link [LNK0] (IRQs 5 9 10 *11 12 14 15)
Nov  4 09:40:06 Ezekiel kernel: [   38.853913] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 9 10 11 12 14 15) *0, disabled.
Nov  4 09:40:06 Ezekiel kernel: [   38.853989] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  4 09:40:06 Ezekiel kernel: [   38.853995] pnp: PnP ACPI init
Nov  4 09:40:06 Ezekiel kernel: [   38.854000] ACPI: bus type pnp registered
Nov  4 09:40:06 Ezekiel kernel: [   38.856411] pnp: PnP ACPI: found 16 devices
Nov  4 09:40:06 Ezekiel kernel: [   38.856413] ACPI: ACPI bus type pnp unregistered
Nov  4 09:40:06 Ezekiel kernel: [   38.856416] PnPBIOS: Disabled by ACPI PNP
Nov  4 09:40:06 Ezekiel kernel: [   38.856447] PCI: Using ACPI for IRQ routing
Nov  4 09:40:06 Ezekiel kernel: [   38.856449] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov  4 09:40:06 Ezekiel kernel: [   38.884193] NET: Registered protocol family 8
Nov  4 09:40:06 Ezekiel kernel: [   38.884194] NET: Registered protocol family 20
Nov  4 09:40:06 Ezekiel kernel: [   38.884249] pnp: 00:0c: ioport range 0x400-0x4bf could not be reserved
Nov  4 09:40:06 Ezekiel kernel: [   38.884253] pnp: 00:0e: iomem range 0xe0000000-0xefffffff could not be reserved
Nov  4 09:40:06 Ezekiel kernel: [   38.884257] pnp: 00:0f: iomem range 0xd3000-0xd3fff has been reserved
Nov  4 09:40:06 Ezekiel kernel: [   38.884259] pnp: 00:0f: iomem range 0xf0000-0xf7fff could not be reserved
Nov  4 09:40:06 Ezekiel kernel: [   38.884261] pnp: 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
Nov  4 09:40:06 Ezekiel kernel: [   38.884263] pnp: 00:0f: iomem range 0xfc000-0xfffff could not be reserved
Nov  4 09:40:06 Ezekiel kernel: [   38.884507] Time: tsc clocksource has been installed.
Nov  4 09:40:06 Ezekiel kernel: [   38.914451] PCI: Bridge: 0000:00:01.0
Nov  4 09:40:06 Ezekiel kernel: [   38.914453]   IO window: 6000-6fff
Nov  4 09:40:06 Ezekiel kernel: [   38.914455]   MEM window: fa000000-fcffffff
Nov  4 09:40:06 Ezekiel kernel: [   38.914458]   PREFETCH window: d0000000-dfffffff
Nov  4 09:40:06 Ezekiel kernel: [   38.914461] PCI: Bridge: 0000:00:1c.0
Nov  4 09:40:06 Ezekiel kernel: [   38.914463]   IO window: 9000-afff
Nov  4 09:40:06 Ezekiel kernel: [   38.914466]   MEM window: fdd00000-fddfffff
Nov  4 09:40:06 Ezekiel kernel: [   38.914469]   PREFETCH window: fda00000-fdafffff
Nov  4 09:40:06 Ezekiel kernel: [   38.914473] PCI: Bridge: 0000:00:1c.1
Nov  4 09:40:06 Ezekiel kernel: [   38.914475]   IO window: 8000-8fff
Nov  4 09:40:06 Ezekiel kernel: [   38.914479]   MEM window: fd900000-fd9fffff
Nov  4 09:40:06 Ezekiel kernel: [   38.914482]   PREFETCH window: fde00000-fdefffff
Nov  4 09:40:06 Ezekiel kernel: [   38.914485] PCI: Bridge: 0000:00:1e.0
Nov  4 09:40:06 Ezekiel kernel: [   38.914487]   IO window: 7000-7fff
Nov  4 09:40:06 Ezekiel kernel: [   38.914491]   MEM window: fdc00000-fdcfffff
Nov  4 09:40:06 Ezekiel kernel: [   38.914494]   PREFETCH window: fdb00000-fdbfffff
Nov  4 09:40:06 Ezekiel kernel: [   38.914593] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   38.914595] PCI: setting IRQ 10 as level-triggered
Nov  4 09:40:06 Ezekiel kernel: [   38.914598] ACPI: PCI Interrupt 0000:00:01.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   38.914603] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   38.914616] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   38.914620] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   38.914716] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Nov  4 09:40:06 Ezekiel kernel: [   38.914718] PCI: setting IRQ 5 as level-triggered
Nov  4 09:40:06 Ezekiel kernel: [   38.914721] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Nov  4 09:40:06 Ezekiel kernel: [   38.914725] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Nov  4 09:40:06 Ezekiel kernel: [   38.914733] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   38.914740] NET: Registered protocol family 2
Nov  4 09:40:06 Ezekiel kernel: [   38.952661] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  4 09:40:06 Ezekiel kernel: [   38.952702] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Nov  4 09:40:06 Ezekiel kernel: [   38.953183] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov  4 09:40:06 Ezekiel kernel: [   38.953330] TCP: Hash tables configured (established 131072 bind 65536)
Nov  4 09:40:06 Ezekiel kernel: [   38.953332] TCP reno registered
Nov  4 09:40:06 Ezekiel kernel: [   38.964813] checking if image is initramfs... it is
Nov  4 09:40:06 Ezekiel kernel: [   39.412386] Switched to high resolution mode on CPU 1
Nov  4 09:40:06 Ezekiel kernel: [   39.416303] Switched to high resolution mode on CPU 0
Nov  4 09:40:06 Ezekiel kernel: [   39.420405] Freeing initrd memory: 7125k freed
Nov  4 09:40:06 Ezekiel kernel: [   39.420791] audit: initializing netlink socket (disabled)
Nov  4 09:40:06 Ezekiel kernel: [   39.420802] audit(1194169189.204:1): initialized
Nov  4 09:40:06 Ezekiel kernel: [   39.420874] highmem bounce pool size: 64 pages
Nov  4 09:40:06 Ezekiel kernel: [   39.422170] VFS: Disk quotas dquot_6.5.1
Nov  4 09:40:06 Ezekiel kernel: [   39.422203] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  4 09:40:06 Ezekiel kernel: [   39.422260] io scheduler noop registered
Nov  4 09:40:06 Ezekiel kernel: [   39.422262] io scheduler anticipatory registered
Nov  4 09:40:06 Ezekiel kernel: [   39.422263] io scheduler deadline registered
Nov  4 09:40:06 Ezekiel kernel: [   39.422272] io scheduler cfq registered (default)
Nov  4 09:40:06 Ezekiel kernel: [   39.422365] Boot video device is 0000:01:00.0
Nov  4 09:40:06 Ezekiel kernel: [   39.422428] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   39.422453] assign_interrupt_mode Found MSI capability
Nov  4 09:40:06 Ezekiel kernel: [   39.422455] Allocate Port Service[0000:00:01.0:pcie00]
Nov  4 09:40:06 Ezekiel kernel: [   39.422512] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   39.422544] assign_interrupt_mode Found MSI capability
Nov  4 09:40:06 Ezekiel kernel: [   39.422545] Allocate Port Service[0000:00:1c.0:pcie00]
Nov  4 09:40:06 Ezekiel kernel: [   39.422568] Allocate Port Service[0000:00:1c.0:pcie02]
Nov  4 09:40:06 Ezekiel kernel: [   39.422627] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Nov  4 09:40:06 Ezekiel kernel: [   39.422659] assign_interrupt_mode Found MSI capability
Nov  4 09:40:06 Ezekiel kernel: [   39.422661] Allocate Port Service[0000:00:1c.1:pcie00]
Nov  4 09:40:06 Ezekiel kernel: [   39.422682] Allocate Port Service[0000:00:1c.1:pcie02]
Nov  4 09:40:06 Ezekiel kernel: [   39.422786] isapnp: Scanning for PnP cards...
Nov  4 09:40:06 Ezekiel kernel: [   39.775309] isapnp: No Plug & Play device found
Nov  4 09:40:06 Ezekiel kernel: [   39.789373] Real Time Clock Driver v1.12ac
Nov  4 09:40:06 Ezekiel kernel: [   39.789447] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov  4 09:40:06 Ezekiel kernel: [   39.789531] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  4 09:40:06 Ezekiel kernel: [   39.789633] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov  4 09:40:06 Ezekiel kernel: [   39.789993] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  4 09:40:06 Ezekiel kernel: [   39.790487] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov  4 09:40:06 Ezekiel kernel: [   39.790628] input: Macintosh mouse button emulation as /class/input/input0
Nov  4 09:40:06 Ezekiel kernel: [   39.790685] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov  4 09:40:06 Ezekiel kernel: [   39.792721] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  4 09:40:06 Ezekiel kernel: [   39.792724] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov  4 09:40:06 Ezekiel kernel: [   39.792827] mice: PS/2 mouse device common for all mice
Nov  4 09:40:06 Ezekiel kernel: [   39.792898] EISA: Probing bus 0 at eisa.0
Nov  4 09:40:06 Ezekiel kernel: [   39.792915] Cannot allocate resource for EISA slot 6
Nov  4 09:40:06 Ezekiel kernel: [   39.792917] Cannot allocate resource for EISA slot 7
Nov  4 09:40:06 Ezekiel kernel: [   39.792918] Cannot allocate resource for EISA slot 8
Nov  4 09:40:06 Ezekiel kernel: [   39.792919] EISA: Detected 0 cards.
Nov  4 09:40:06 Ezekiel kernel: [   39.792972] TCP cubic registered
Nov  4 09:40:06 Ezekiel kernel: [   39.792981] NET: Registered protocol family 1
Nov  4 09:40:06 Ezekiel kernel: [   39.792994] Using IPI No-Shortcut mode
Nov  4 09:40:06 Ezekiel kernel: [   39.793112]   Magic number: 15:415:676
Nov  4 09:40:06 Ezekiel kernel: [   39.793268] Freeing unused kernel memory: 364k freed
Nov  4 09:40:06 Ezekiel kernel: [   39.815652] input: AT Translated Set 2 keyboard as /class/input/input1
Nov  4 09:40:06 Ezekiel kernel: [   39.852799] SCSI subsystem initialized
Nov  4 09:40:06 Ezekiel kernel: [   39.855947] libata version 2.21 loaded.
Nov  4 09:40:06 Ezekiel kernel: [   39.856791] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Nov  4 09:40:06 Ezekiel kernel: [   39.856793] PCI: setting IRQ 11 as level-triggered
Nov  4 09:40:06 Ezekiel kernel: [   39.856797] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Nov  4 09:40:06 Ezekiel kernel: [   39.856816] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Nov  4 09:40:06 Ezekiel kernel: [   39.856846] scsi0 : ata_generic
Nov  4 09:40:06 Ezekiel kernel: [   39.856884] scsi1 : ata_generic
Nov  4 09:40:06 Ezekiel kernel: [   39.856955] ata1: PATA max UDMA/100 cmd 0x0001e800 ctl 0x0001e402 bmdma 0x0001d800 irq 11
Nov  4 09:40:06 Ezekiel kernel: [   39.856958] ata2: PATA max UDMA/100 cmd 0x0001e000 ctl 0x0001dc02 bmdma 0x0001d808 irq 11
Nov  4 09:40:06 Ezekiel kernel: [   40.073501] ata1.00: ata_hpa_resize 1: hpa sectors (586072368) is smaller than sectors (625142448)
Nov  4 09:40:06 Ezekiel kernel: [   40.073506] ata1.00: ATA-7: ST3320620AS, 3.AAD, max UDMA/133
Nov  4 09:40:06 Ezekiel kernel: [   40.073509] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov  4 09:40:06 Ezekiel kernel: [   40.115332] ata1.01: ata_hpa_resize 1: hpa sectors (586072368) is smaller than sectors (625142448)
Nov  4 09:40:06 Ezekiel kernel: [   40.115336] ata1.01: ATA-7: ST3320620AS, 3.AAD, max UDMA/133
Nov  4 09:40:06 Ezekiel kernel: [   40.115342] ata1.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov  4 09:40:06 Ezekiel kernel: [   40.115346] ata1.00: configured for UDMA/100
Nov  4 09:40:06 Ezekiel kernel: [   40.115348] ata1.01: configured for UDMA/100
Nov  4 09:40:06 Ezekiel kernel: [   40.607068] ata2.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L02, max UDMA/100
Nov  4 09:40:06 Ezekiel kernel: [   40.607072] ata2.00: configured for UDMA/100
Nov  4 09:40:06 Ezekiel kernel: [   40.607160] scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
Nov  4 09:40:06 Ezekiel kernel: [   40.607254] scsi 0:0:1:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
Nov  4 09:40:06 Ezekiel kernel: [   40.608449] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L02 PQ: 0 ANSI: 5
Nov  4 09:40:06 Ezekiel kernel: [   40.608535] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Nov  4 09:40:06 Ezekiel kernel: [   40.608557] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Nov  4 09:40:06 Ezekiel kernel: [   40.608580] scsi2 : ata_generic
Nov  4 09:40:06 Ezekiel kernel: [   40.608629] scsi3 : ata_generic
Nov  4 09:40:06 Ezekiel kernel: [   40.608702] ata3: PATA max UDMA/100 cmd 0x0001cc00 ctl 0x0001c802 bmdma 0x0001bc00 irq 11
Nov  4 09:40:06 Ezekiel kernel: [   40.608704] ata4: PATA max UDMA/100 cmd 0x0001c400 ctl 0x0001c002 bmdma 0x0001bc08 irq 11
Nov  4 09:40:06 Ezekiel kernel: [   42.019232] AppArmor: AppArmor initialized<5>audit(1194169191.704:2):  type=1505 info="AppArmor initialized" pid=1261
Nov  4 09:40:06 Ezekiel kernel: [   42.024575] fuse init (API version 7.8)
Nov  4 09:40:06 Ezekiel kernel: [   42.028218] Failure registering capabilities with primary security module.
Nov  4 09:40:06 Ezekiel kernel: [   42.052426] ACPI: Fan [FAN] (on)
Nov  4 09:40:06 Ezekiel kernel: [   42.055840] ACPI: SSDT 7FEE7B80, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
Nov  4 09:40:06 Ezekiel kernel: [   42.055929] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov  4 09:40:06 Ezekiel kernel: [   42.055936] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov  4 09:40:06 Ezekiel kernel: [   42.056670] ACPI: Thermal Zone [THRM] (40 C)
Nov  4 09:40:06 Ezekiel kernel: [   42.328855] usbcore: registered new interface driver usbfs
Nov  4 09:40:06 Ezekiel kernel: [   42.328872] usbcore: registered new interface driver hub
Nov  4 09:40:06 Ezekiel kernel: [   42.328888] usbcore: registered new device driver usb
Nov  4 09:40:06 Ezekiel kernel: [   42.329405] USB Universal Host Controller Interface driver v3.0
Nov  4 09:40:06 Ezekiel kernel: [   42.329444] ACPI: PCI Interrupt 0000:00:1a.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   42.329453] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   42.329456] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Nov  4 09:40:06 Ezekiel kernel: [   42.329543] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Nov  4 09:40:06 Ezekiel kernel: [   42.329565] uhci_hcd 0000:00:1a.0: irq 10, io base 0x0000fc00
Nov  4 09:40:06 Ezekiel kernel: [   42.329639] usb usb1: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   42.329656] hub 1-0:1.0: USB hub found
Nov  4 09:40:06 Ezekiel kernel: [   42.329660] hub 1-0:1.0: 2 ports detected
Nov  4 09:40:06 Ezekiel kernel: [   42.415136] FDC 0 is a post-1991 82077
Nov  4 09:40:06 Ezekiel kernel: [   42.433383] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
Nov  4 09:40:06 Ezekiel kernel: [   42.433386] ACPI: PCI Interrupt 0000:00:1a.1[B] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
Nov  4 09:40:06 Ezekiel kernel: [   42.433395] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Nov  4 09:40:06 Ezekiel kernel: [   42.433398] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Nov  4 09:40:06 Ezekiel kernel: [   42.433415] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Nov  4 09:40:06 Ezekiel kernel: [   42.433436] uhci_hcd 0000:00:1a.1: irq 11, io base 0x0000f800
Nov  4 09:40:06 Ezekiel kernel: [   42.433501] usb usb2: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   42.433518] hub 2-0:1.0: USB hub found
Nov  4 09:40:06 Ezekiel kernel: [   42.433522] hub 2-0:1.0: 2 ports detected
Nov  4 09:40:06 Ezekiel kernel: [   42.537311] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   42.537314] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   42.537323] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   42.537326] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov  4 09:40:06 Ezekiel kernel: [   42.537353] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Nov  4 09:40:06 Ezekiel kernel: [   42.537372] uhci_hcd 0000:00:1d.0: irq 10, io base 0x0000f400
Nov  4 09:40:06 Ezekiel kernel: [   42.537434] usb usb3: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   42.537452] hub 3-0:1.0: USB hub found
Nov  4 09:40:06 Ezekiel kernel: [   42.537456] hub 3-0:1.0: 2 ports detected
Nov  4 09:40:06 Ezekiel kernel: [   42.641060] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Nov  4 09:40:06 Ezekiel kernel: [   42.641068] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Nov  4 09:40:06 Ezekiel kernel: [   42.641072] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov  4 09:40:06 Ezekiel kernel: [   42.641091] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Nov  4 09:40:06 Ezekiel kernel: [   42.641112] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000f000
Nov  4 09:40:06 Ezekiel kernel: [   42.641199] usb usb4: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   42.641226] hub 4-0:1.0: USB hub found
Nov  4 09:40:06 Ezekiel kernel: [   42.641231] hub 4-0:1.0: 2 ports detected
Nov  4 09:40:06 Ezekiel kernel: [   42.672965] usb 1-2: new full speed USB device using uhci_hcd and address 2
Nov  4 09:40:06 Ezekiel kernel: [   42.745121] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
Nov  4 09:40:06 Ezekiel kernel: [   42.745124] PCI: setting IRQ 9 as level-triggered
Nov  4 09:40:06 Ezekiel kernel: [   42.745127] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
Nov  4 09:40:06 Ezekiel kernel: [   42.745135] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Nov  4 09:40:06 Ezekiel kernel: [   42.745148] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov  4 09:40:06 Ezekiel kernel: [   42.745162] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Nov  4 09:40:06 Ezekiel kernel: [   42.745180] uhci_hcd 0000:00:1d.2: irq 9, io base 0x0000ec00
Nov  4 09:40:06 Ezekiel kernel: [   42.745244] usb usb5: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   42.745261] hub 5-0:1.0: USB hub found
Nov  4 09:40:06 Ezekiel kernel: [   42.745265] hub 5-0:1.0: 2 ports detected
Nov  4 09:40:06 Ezekiel kernel: [   42.840198] usb 1-2: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   42.848978] ACPI: PCI Interrupt 0000:00:1a.7[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
Nov  4 09:40:06 Ezekiel kernel: [   42.848988] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Nov  4 09:40:06 Ezekiel kernel: [   42.848992] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Nov  4 09:40:06 Ezekiel kernel: [   42.849013] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Nov  4 09:40:06 Ezekiel kernel: [   42.849038] ehci_hcd 0000:00:1a.7: debug port 1
Nov  4 09:40:06 Ezekiel kernel: [   42.849045] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Nov  4 09:40:06 Ezekiel kernel: [   42.849049] ehci_hcd 0000:00:1a.7: irq 9, io mem 0xfdfff000
Nov  4 09:40:06 Ezekiel kernel: [   42.852923] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  4 09:40:06 Ezekiel kernel: [   42.852981] usb usb6: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   42.852997] hub 6-0:1.0: USB hub found
Nov  4 09:40:06 Ezekiel kernel: [   42.853002] hub 6-0:1.0: 4 ports detected
Nov  4 09:40:06 Ezekiel kernel: [   42.956810] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   42.956822] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Nov  4 09:40:06 Ezekiel kernel: [   42.956826] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov  4 09:40:06 Ezekiel kernel: [   42.956851] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Nov  4 09:40:06 Ezekiel kernel: [   42.956878] ehci_hcd 0000:00:1d.7: debug port 1
Nov  4 09:40:06 Ezekiel kernel: [   42.956884] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Nov  4 09:40:06 Ezekiel kernel: [   42.956890] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xfdffe000
Nov  4 09:40:06 Ezekiel kernel: [   42.960762] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  4 09:40:06 Ezekiel kernel: [   42.960812] usb usb7: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   42.960830] hub 7-0:1.0: USB hub found
Nov  4 09:40:06 Ezekiel kernel: [   42.960834] hub 7-0:1.0: 6 ports detected
Nov  4 09:40:06 Ezekiel kernel: [   43.064798] ahci 0000:02:00.0: version 2.2
Nov  4 09:40:06 Ezekiel kernel: [   43.064817] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   43.352359] usb 1-2: USB disconnect, address 2
Nov  4 09:40:06 Ezekiel kernel: [   43.352535] usbcore: registered new interface driver libusual
Nov  4 09:40:06 Ezekiel kernel: [   43.720006] usb 6-2: new high speed USB device using ehci_hcd and address 2
Nov  4 09:40:06 Ezekiel kernel: [   43.853498] usb 6-2: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   43.857676] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov  4 09:40:06 Ezekiel kernel: [   43.857679] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov  4 09:40:06 Ezekiel kernel: [   43.858727] Initializing USB Mass Storage driver...
Nov  4 09:40:06 Ezekiel kernel: [   44.067685] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Nov  4 09:40:06 Ezekiel kernel: [   44.067690] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Nov  4 09:40:06 Ezekiel kernel: [   44.067697] PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   44.067795] scsi4 : ahci
Nov  4 09:40:06 Ezekiel kernel: [   44.067839] scsi5 : ahci
Nov  4 09:40:06 Ezekiel kernel: [   44.067866] ata5: SATA max UDMA/133 cmd 0xf8908100 ctl 0x00000000 bmdma 0x00000000 irq 10
Nov  4 09:40:06 Ezekiel kernel: [   44.067870] ata6: SATA max UDMA/133 cmd 0xf8908180 ctl 0x00000000 bmdma 0x00000000 irq 10
Nov  4 09:40:06 Ezekiel kernel: [   44.379391] ata5: SATA link down (SStatus 0 SControl 300)
Nov  4 09:40:06 Ezekiel kernel: [   44.459291] usb 7-4: new high speed USB device using ehci_hcd and address 4
Nov  4 09:40:06 Ezekiel kernel: [   44.591536] usb 7-4: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   44.591620] hub 7-4:1.0: USB hub found
Nov  4 09:40:06 Ezekiel kernel: [   44.591719] hub 7-4:1.0: 4 ports detected
Nov  4 09:40:06 Ezekiel kernel: [   44.691077] ata6: SATA link down (SStatus 0 SControl 300)
Nov  4 09:40:06 Ezekiel kernel: [   44.691841] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   44.691844] ACPI: PCI Interrupt 0000:04:01.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   44.691849] PCI: Setting latency timer of device 0000:04:01.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   44.695218] scsi6 : SCSI emulation for USB Mass Storage devices
Nov  4 09:40:06 Ezekiel kernel: [   44.695245] usb-storage: device found at 2
Nov  4 09:40:06 Ezekiel kernel: [   44.695246] usb-storage: waiting for device to settle before scanning
Nov  4 09:40:06 Ezekiel kernel: [   44.695254] usbcore: registered new interface driver usb-storage
Nov  4 09:40:06 Ezekiel kernel: [   44.695255] USB Mass Storage support registered.
Nov  4 09:40:06 Ezekiel kernel: [   44.743312] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Nov  4 09:40:06 Ezekiel kernel: [   44.743320] sd 0:0:0:0: [sda] Write Protect is off
Nov  4 09:40:06 Ezekiel kernel: [   44.743322] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  4 09:40:06 Ezekiel kernel: [   44.743332] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  4 09:40:06 Ezekiel kernel: [   44.743362] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Nov  4 09:40:06 Ezekiel kernel: [   44.743368] sd 0:0:0:0: [sda] Write Protect is off
Nov  4 09:40:06 Ezekiel kernel: [   44.743370] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  4 09:40:06 Ezekiel kernel: [   44.743380] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  4 09:40:06 Ezekiel kernel: [   44.743383]  sda:<6>ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov  4 09:40:06 Ezekiel kernel: [   44.749534] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
Nov  4 09:40:06 Ezekiel kernel: [   44.749541] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Nov  4 09:40:06 Ezekiel kernel: [   44.749569] PCI: Setting latency timer of device 0000:02:00.1 to 64
Nov  4 09:40:06 Ezekiel kernel: [   44.749598] scsi7 : pata_jmicron
Nov  4 09:40:06 Ezekiel kernel: [   44.749630] scsi8 : pata_jmicron
Nov  4 09:40:06 Ezekiel kernel: [   44.749649] ata7: PATA max UDMA/100 cmd 0x0001ac00 ctl 0x0001a802 bmdma 0x00019c00 irq 5
Nov  4 09:40:06 Ezekiel kernel: [   44.749652] ata8: PATA max UDMA/100 cmd 0x0001a400 ctl 0x0001a002 bmdma 0x00019c08 irq 5
Nov  4 09:40:06 Ezekiel kernel: [   44.756683]  sda1 sda2 < sda5 sda6 > sda3 sda4
Nov  4 09:40:06 Ezekiel kernel: [   44.766665] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  4 09:40:06 Ezekiel kernel: [   44.766769] sd 0:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Nov  4 09:40:06 Ezekiel kernel: [   44.766777] sd 0:0:1:0: [sdb] Write Protect is off
Nov  4 09:40:06 Ezekiel kernel: [   44.766778] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Nov  4 09:40:06 Ezekiel kernel: [   44.766789] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  4 09:40:06 Ezekiel kernel: [   44.766814] sd 0:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Nov  4 09:40:06 Ezekiel kernel: [   44.766821] sd 0:0:1:0: [sdb] Write Protect is off
Nov  4 09:40:06 Ezekiel kernel: [   44.766822] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Nov  4 09:40:06 Ezekiel kernel: [   44.766832] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  4 09:40:06 Ezekiel kernel: [   44.766834]  sdb: sdb1
Nov  4 09:40:06 Ezekiel kernel: [   44.782023] sd 0:0:1:0: [sdb] Attached SCSI disk
Nov  4 09:40:06 Ezekiel kernel: [   44.784664] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov  4 09:40:06 Ezekiel kernel: [   44.784677] sd 0:0:1:0: Attached scsi generic sg1 type 0
Nov  4 09:40:06 Ezekiel kernel: [   44.784689] sr 1:0:0:0: Attached scsi generic sg2 type 5
Nov  4 09:40:06 Ezekiel kernel: [   44.801085] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Nov  4 09:40:06 Ezekiel kernel: [   44.801087] Uniform CD-ROM driver Revision: 3.20
Nov  4 09:40:06 Ezekiel kernel: [   44.801205] sr 1:0:0:0: Attached scsi CD-ROM sr0
Nov  4 09:40:06 Ezekiel kernel: [   44.946835] usb 3-1: new low speed USB device using uhci_hcd and address 2
Nov  4 09:40:06 Ezekiel kernel: [   45.125167] usb 3-1: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   45.199449] Attempting manual resume
Nov  4 09:40:06 Ezekiel kernel: [   45.199451] swsusp: Resume From Partition 8:6
Nov  4 09:40:06 Ezekiel kernel: [   45.199452] PM: Checking swsusp image.
Nov  4 09:40:06 Ezekiel kernel: [   45.199603] PM: Resume from disk failed.
Nov  4 09:40:06 Ezekiel kernel: [   45.227550] kjournald starting.  Commit interval 5 seconds
Nov  4 09:40:06 Ezekiel kernel: [   45.227557] EXT3-fs: mounted filesystem with ordered data mode.
Nov  4 09:40:06 Ezekiel kernel: [   45.366440] usb 3-2: new low speed USB device using uhci_hcd and address 3
Nov  4 09:40:06 Ezekiel kernel: [   45.560779] usb 3-2: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   45.762179] usb 7-4.2: new full speed USB device using ehci_hcd and address 5
Nov  4 09:40:06 Ezekiel kernel: [   45.855661] usb 7-4.2: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   45.855866] hub 7-4.2:1.0: USB hub found
Nov  4 09:40:06 Ezekiel kernel: [   45.855967] hub 7-4.2:1.0: 3 ports detected
Nov  4 09:40:06 Ezekiel kernel: [   46.017924] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c2000219f59]
Nov  4 09:40:06 Ezekiel kernel: [   46.157824] usb 7-4.2.2: new full speed USB device using ehci_hcd and address 6
Nov  4 09:40:06 Ezekiel kernel: [   46.256300] usb 7-4.2.2: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   46.453562] usb 7-4.2.3: new full speed USB device using ehci_hcd and address 7
Nov  4 09:40:06 Ezekiel kernel: [   46.553531] usb 7-4.2.3: configuration #1 chosen from 1 choice
Nov  4 09:40:06 Ezekiel kernel: [   46.555111] usbcore: registered new interface driver hiddev
Nov  4 09:40:06 Ezekiel kernel: [   46.573037] input: Logitech USB Receiver as /class/input/input2
Nov  4 09:40:06 Ezekiel kernel: [   46.573051] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
Nov  4 09:40:06 Ezekiel kernel: [   47.022427] hiddev96: USB HID v1.10 Device [APC Back-UPS ES 500 FW:824.B1.D USB FW:B1] on usb-0000:00:1d.0-2
Nov  4 09:40:06 Ezekiel kernel: [   47.025487] input: Logitech Logitech BT Mini-Receiver as /class/input/input3
Nov  4 09:40:06 Ezekiel kernel: [   47.025511] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.7-4.2.2
Nov  4 09:40:06 Ezekiel kernel: [   47.031871] input: Logitech Logitech BT Mini-Receiver as /class/input/input4
Nov  4 09:40:06 Ezekiel kernel: [   47.031948] input,hiddev97: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.7-4.2.3
Nov  4 09:40:06 Ezekiel kernel: [   47.031958] usbcore: registered new interface driver usbhid
Nov  4 09:40:06 Ezekiel kernel: [   47.031961] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Nov  4 09:40:06 Ezekiel kernel: [   49.690498] usb-storage: device scan complete
Nov  4 09:40:06 Ezekiel kernel: [   49.691153] scsi 6:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0
Nov  4 09:40:06 Ezekiel kernel: [   49.693794] scsi 6:0:0:1: Direct-Access     USB2.0   CardReader SM XD 0100 PQ: 0 ANSI: 0
Nov  4 09:40:06 Ezekiel kernel: [   49.694372] scsi 6:0:0:2: Direct-Access     USB2.0   CardReader MS    0100 PQ: 0 ANSI: 0
Nov  4 09:40:06 Ezekiel kernel: [   49.696574] scsi 6:0:0:3: Direct-Access     USB2.0   CardReader SD    0100 PQ: 0 ANSI: 0
Nov  4 09:40:06 Ezekiel kernel: [   49.699643] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Nov  4 09:40:06 Ezekiel kernel: [   49.699679] sd 6:0:0:0: Attached scsi generic sg3 type 0
Nov  4 09:40:06 Ezekiel kernel: [   49.700640] sd 6:0:0:1: [sdd] Attached SCSI removable disk
Nov  4 09:40:06 Ezekiel kernel: [   49.700670] sd 6:0:0:1: Attached scsi generic sg4 type 0
Nov  4 09:40:06 Ezekiel kernel: [   49.701634] sd 6:0:0:2: [sde] Attached SCSI removable disk
Nov  4 09:40:06 Ezekiel kernel: [   49.701668] sd 6:0:0:2: Attached scsi generic sg5 type 0
Nov  4 09:40:06 Ezekiel kernel: [   49.702630] sd 6:0:0:3: [sdf] Attached SCSI removable disk
Nov  4 09:40:06 Ezekiel kernel: [   49.702665] sd 6:0:0:3: Attached scsi generic sg6 type 0
Nov  4 09:40:06 Ezekiel kernel: [   50.535396] Linux agpgart interface v0.102 (c) Dave Jones
Nov  4 09:40:06 Ezekiel kernel: [   50.570932] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  4 09:40:06 Ezekiel kernel: [   50.573306] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  4 09:40:06 Ezekiel kernel: [   50.665702] iTCO_vendor_support: vendor-support=0
Nov  4 09:40:06 Ezekiel kernel: [   50.691775] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Nov  4 09:40:06 Ezekiel kernel: [   50.691838] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0460)
Nov  4 09:40:06 Ezekiel kernel: [   50.691872] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Nov  4 09:40:06 Ezekiel kernel: [   50.923459] input: PC Speaker as /class/input/input5
Nov  4 09:40:06 Ezekiel kernel: [   51.006455] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Nov  4 09:40:06 Ezekiel kernel: [   51.006466] PCI: Setting latency timer of device 0000:03:00.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   51.006484] sky2 0000:03:00.0: v1.18 addr 0xfd9fc000 irq 5 Yukon-EC Ultra (0xb4) rev 2
Nov  4 09:40:06 Ezekiel kernel: [   51.006684] sky2 eth0: addr 00:15:58:78:e2:a2
Nov  4 09:40:06 Ezekiel kernel: [   51.088214] usbcore: registered new interface driver xpad
Nov  4 09:40:06 Ezekiel kernel: [   51.088217] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
Nov  4 09:40:06 Ezekiel kernel: [   51.114262] irda_init()
Nov  4 09:40:06 Ezekiel kernel: [   51.114270] NET: Registered protocol family 23
Nov  4 09:40:06 Ezekiel kernel: [   51.156833] nvidia: module license 'NVIDIA' taints kernel.
Nov  4 09:40:06 Ezekiel kernel: [   51.407314] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov  4 09:40:06 Ezekiel kernel: [   51.407322] PCI: Setting latency timer of device 0000:01:00.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   51.407400] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
Nov  4 09:40:06 Ezekiel kernel: [   51.408992] usbcore: registered new interface driver lmpcm_usb
Nov  4 09:40:06 Ezekiel kernel: [   51.408996] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
Nov  4 09:40:06 Ezekiel kernel: [   51.432796] rtl_ieee80211_crypt: registered algorithm 'NULL'
Nov  4 09:40:06 Ezekiel kernel: [   51.432799] rtl_ieee80211_crypt: registered algorithm 'TKIP'
Nov  4 09:40:06 Ezekiel kernel: [   51.432800] rtl_ieee80211_crypt: registered algorithm 'WEP'
Nov  4 09:40:06 Ezekiel kernel: [   51.432802] rtl_ieee80211_crypt: registered algorithm 'CCMP'
Nov  4 09:40:06 Ezekiel kernel: [   51.435259] 
Nov  4 09:40:06 Ezekiel kernel: [   51.435260] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
Nov  4 09:40:06 Ezekiel kernel: [   51.435262] Copyright (c) 2004-2005, Andrea Merello
Nov  4 09:40:06 Ezekiel kernel: [   51.435263] rtl8180: Initializing module
Nov  4 09:40:06 Ezekiel kernel: [   51.435264] rtl8180: Wireless extensions version 22
Nov  4 09:40:06 Ezekiel kernel: [   51.435265] rtl8180: Initializing proc filesystem
Nov  4 09:40:06 Ezekiel kernel: [   51.435291] rtl8180: Configuring chip resources
Nov  4 09:40:06 Ezekiel kernel: [   51.435305] ACPI: PCI Interrupt 0000:04:04.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
Nov  4 09:40:06 Ezekiel kernel: [   51.435337] rtl8180: Memory mapped space @ 0xfdcfe000 
Nov  4 09:40:06 Ezekiel kernel: [   51.435344] rtl8180: MAC controller is a RTL8185 b/g (V. D)
Nov  4 09:40:06 Ezekiel kernel: [   51.435347] rtl8180: This is a PCI NIC
Nov  4 09:40:06 Ezekiel kernel: [   51.435348] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
Nov  4 09:40:06 Ezekiel kernel: [   51.441454] rtl8180: Card MAC address is 00:0e:2e:6d:6e:3b
Nov  4 09:40:06 Ezekiel kernel: [   51.456686] rtl8180: EEPROM version 105
Nov  4 09:40:06 Ezekiel kernel: [   51.458718] rtl8180: Card reports RF frontend Realtek 8225
Nov  4 09:40:06 Ezekiel kernel: [   51.458719] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
Nov  4 09:40:06 Ezekiel kernel: [   51.458720] rtl8180: WW:use it with care and at your own risk and
Nov  4 09:40:06 Ezekiel kernel: [   51.458722] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
Nov  4 09:40:06 Ezekiel kernel: [   51.458723] rtl8180: Energy threshold: b
Nov  4 09:40:06 Ezekiel kernel: [   51.458725] rtl8180: PAPE from CONFIG2: 6
Nov  4 09:40:06 Ezekiel kernel: [   51.458782] rtl8180: IRQ 9
Nov  4 09:40:06 Ezekiel kernel: [   51.458848] rtl8180: Driver probe completed
Nov  4 09:40:06 Ezekiel kernel: [   51.458848] 
Nov  4 09:40:06 Ezekiel kernel: [   51.488729] rtl8180: Bringing up iface
Nov  4 09:40:06 Ezekiel kernel: [   51.697365] rtl8180: Card successfully reset
Nov  4 09:40:06 Ezekiel kernel: [   52.641759] input: ImPS/2 Generic Wheel Mouse as /class/input/input6
Nov  4 09:40:06 Ezekiel kernel: [   52.644323] parport_pc 00:09: reported by Plug and Play ACPI
Nov  4 09:40:06 Ezekiel kernel: [   52.644365] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Nov  4 09:40:06 Ezekiel kernel: [   52.813581] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 11
Nov  4 09:40:06 Ezekiel kernel: [   52.813584] ACPI: PCI Interrupt 0000:00:1b.0[A] -> Link [LNK0] -> GSI 11 (level, low) -> IRQ 11
Nov  4 09:40:06 Ezekiel kernel: [   52.813595] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Nov  4 09:40:06 Ezekiel kernel: [   53.019257] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Nov  4 09:40:06 Ezekiel kernel: [   53.680650] lp0: using parport0 (interrupt-driven).
Nov  4 09:40:06 Ezekiel kernel: [   53.729743] Adding 4072404k swap on /dev/sda6.  Priority:-1 extents:1 across:4072404k
Nov  4 09:40:06 Ezekiel kernel: [   53.938710] NET: Registered protocol family 17
Nov  4 09:40:06 Ezekiel kernel: [   54.136421] EXT3 FS on sda3, internal journal
Nov  4 09:40:06 Ezekiel kernel: [   54.264214] Linking with default
Nov  4 09:40:06 Ezekiel kernel: [   54.279850] Associated successfully
Nov  4 09:40:06 Ezekiel kernel: [   54.279852] Using G rates
Nov  4 09:40:06 Ezekiel kernel: [   54.636924] kjournald starting.  Commit interval 5 seconds
Nov  4 09:40:06 Ezekiel kernel: [   54.637063] EXT3 FS on sda4, internal journal
Nov  4 09:40:06 Ezekiel kernel: [   54.637068] EXT3-fs: mounted filesystem with ordered data mode.
Nov  4 09:40:06 Ezekiel kernel: [   55.703539] No dock devices found.
Nov  4 09:40:06 Ezekiel kernel: [   55.837075] input: Power Button (FF) as /class/input/input7
Nov  4 09:40:06 Ezekiel kernel: [   55.837170] ACPI: Power Button (FF) [PWRF]
Nov  4 09:40:06 Ezekiel kernel: [   55.837666] input: Power Button (CM) as /class/input/input8
Nov  4 09:40:06 Ezekiel kernel: [   55.837757] ACPI: Power Button (CM) [PWRB]
Nov  4 09:40:06 Ezekiel kernel: [   55.931445] NET: Registered protocol family 10
Nov  4 09:40:06 Ezekiel kernel: [   55.931507] lo: Disabled Privacy Extensions
Nov  4 09:40:06 Ezekiel NetworkManager: <info>  starting... 
Nov  4 09:40:07 Ezekiel ntpdate[5083]: adjust time server 91.189.94.4 offset 0.380641 sec
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.071115] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_29a0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.317280] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_29a1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.319041] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10de_391'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.319686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2834'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.320310] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.320872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.321302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2835'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.321735] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.322146] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.322549] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283a'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.322961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.323361] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.323759] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.324159] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.324558] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_if0_scsi_host'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.325205] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_if0_scsi_host_scsi_device_lun0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.325515] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_if0_scsi_host_scsi_device_lun1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.325821] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_if0_scsi_host_scsi_device_lun2'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.326127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_if0_scsi_host_scsi_device_lun3'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.326433] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.326739] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283f'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.327070] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2361'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.327374] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2361_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.327677] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2841'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.327982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_4364'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.328287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2830'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.328591] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.328894] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.329201] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c50e_noserial_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.329883] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_BB0535039018'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.330737] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_BB0535039018_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.332121] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2831'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.332593] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.332910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.333465] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2832'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.334256] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.334559] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.334859] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2836'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.335166] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.335440] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.335719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_424_2504_noserial'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.335999] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_b02_noserial'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.336627] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c70e_000761455E3C'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.336902] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c70e_000761455E3C_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.337192] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c70a_000761455E3C'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.337470] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c70a_000761455E3C_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.361189] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_b02_noserial_if0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.361475] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.361754] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_244e'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.362017] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3044'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.362279] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10ec_8185'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.362551] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2810'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.362812] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2820'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.363092] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2820_scsi_host'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.363365] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2820_scsi_host_scsi_device_lun0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.363644] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2820_scsi_host_scsi_device_lun0_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.363912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2820_scsi_host_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.364179] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2820_scsi_host_0_scsi_device_lun0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.364446] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283e'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.364714] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2825'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.364987] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284f'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.365256] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.365521] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.365788] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.366053] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.366318] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.366590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.366854] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.367130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a08'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.367378] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.367624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.367869] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.368114] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.368359] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.368603] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0700'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.368846] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.369091] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0510'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.369335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0400'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.369578] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.369821] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.370065] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.370308] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_INT0800'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.370552] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.370796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.371045] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.371290] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c50e_noserial_if0_logicaldev_input'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.371567] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.371887] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.372144] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_58_78_e2_a2'). 
Nov  4 09:40:07 Ezekiel kernel: [   56.983200] sky2 eth0: enabling interface
Nov  4 09:40:07 Ezekiel kernel: [   56.987670] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  4 09:40:07 Ezekiel NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'. 
Nov  4 09:40:07 Ezekiel NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  4 09:40:07 Ezekiel NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  4 09:40:07 Ezekiel NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Nov  4 09:40:07 Ezekiel NetworkManager: <info>  Deactivating device eth0. 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.464529] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0e_2e_6d_6e_3b'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.476155] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2820_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.476472] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2820_scsi_host_scsi_device_lun0_0_scsi_generic'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.476773] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2820_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.477073] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.477372] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.477671] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_if0_scsi_host_scsi_device_lun2_scsi_generic'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.477981] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_if0_scsi_host_scsi_device_lun3_scsi_generic'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.478291] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_pcm_1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.478588] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_pcm_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.478883] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_control__1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.479183] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_pcm_0_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.479478] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_mixer__1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.479774] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_capture_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.480070] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_playback_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.480365] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_playback_1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.480661] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_capture_2'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.480977] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.481272] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.481576] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.481871] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.482165] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.482460] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.482757] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c70e_000761455E3C_if0_logicaldev_input'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.483123] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c70a_000761455E3C_if0_logicaldev_input'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.483421] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.483717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.484013] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.484306] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.484643] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.484946] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.485240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.485534] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c50e_noserial_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.485827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_BB0535039018_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.486212] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.486624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.487103] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.487495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_11b0_6566_606569746801_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.487978] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.488381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_424_2504_noserial_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.488675] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_b02_noserial_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.488977] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c70e_000761455E3C_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.489271] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c70a_000761455E3C_usbraw'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.489564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3320620AS'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.489857] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3A18D43918D3F1BD'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.490148] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_51d_2_BB0535039018_if0_hiddev'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.490441] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.490732] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_a531c6c6_3243_4364_bbaf_50d1452bef42'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.491028] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c50e_noserial'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.524352] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_b5cd1dd6_738d_47d8_bf80_0fee9604dee4'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.607149] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_094C9CAC118AB52B'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.610285] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_c8295546_1578_47c1_8dcc_1859bc894064'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.624407] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3320620AS_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.655137] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_B044F23244F1FAC4'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.664618] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_USB2_0_CardReader_CF_606569746801_0_0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.671308] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_USB2_0_CardReader_SM_XD_606569746801_0_1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.680121] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_USB2_0_CardReader_MS_606569746801_0_2'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.687138] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_USB2_0_CardReader_SD_606569746801_0_3'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.720775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.723187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.723732] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_FAN'). 
Nov  4 09:40:07 Ezekiel NetworkManager: <debug> [1194187207.724014] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDRW_LH_20A1S'). 
Nov  4 09:40:09 Ezekiel kernel: [   59.095178] ppdev: user-space parallel port driver
Nov  4 09:40:09 Ezekiel kernel: [   59.384466] audit(1194187209.761:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5565 profile="/usr/sbin/cupsd"
Nov  4 09:40:09 Ezekiel kernel: [   59.438668] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov  4 09:40:09 Ezekiel kernel: [   59.438671] apm: disabled - APM is not SMP safe.
Nov  4 09:40:09 Ezekiel kernel: [   59.589552] Failure registering capabilities with primary security module.
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: Successfully dropped root privileges.
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: avahi-daemon 0.6.20 starting up.
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: Successfully called chroot().
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: Successfully dropped remaining capabilities.
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: No service file found in /etc/avahi/services.
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: New relevant interface wlan0.IPv4 for mDNS.
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: Network interface enumeration completed.
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: Registering new address record for fe80::20e:2eff:fe6d:6e3b on wlan0.*.
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: Registering new address record for 192.168.0.102 on wlan0.IPv4.
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  4 09:40:10 Ezekiel dhcdbd: Started up.
Nov  4 09:40:10 Ezekiel hcid[5771]: Bluetooth HCI daemon
Nov  4 09:40:10 Ezekiel kernel: [   59.779786] Bluetooth: Core ver 2.11
Nov  4 09:40:10 Ezekiel kernel: [   59.779966] NET: Registered protocol family 31
Nov  4 09:40:10 Ezekiel kernel: [   59.779968] Bluetooth: HCI device and connection manager initialized
Nov  4 09:40:10 Ezekiel kernel: [   59.779970] Bluetooth: HCI socket layer initialized
Nov  4 09:40:10 Ezekiel hcid[5771]: Starting SDP server
Nov  4 09:40:10 Ezekiel kernel: [   59.796706] Bluetooth: L2CAP ver 2.8
Nov  4 09:40:10 Ezekiel kernel: [   59.796709] Bluetooth: L2CAP socket layer initialized
Nov  4 09:40:10 Ezekiel hcid[5771]: Created local server at unix:abstract=/var/run/dbus-R1LOVM9Sni,guid=d1e7ff6959375a1bb0f06e00472dd9ca
Nov  4 09:40:10 Ezekiel kernel: [   59.798788] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
Nov  4 09:40:10 Ezekiel hidd[5789]: Bluetooth HID daemon
Nov  4 09:40:10 Ezekiel input[5788]: Bluetooth Input daemon
Nov  4 09:40:10 Ezekiel input[5788]: Registered input manager path:/org/bluez/input
Nov  4 09:40:10 Ezekiel audio[5791]: Bluetooth Audio daemon
Nov  4 09:40:10 Ezekiel audio[5791]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Nov  4 09:40:10 Ezekiel audio[5791]: Unix socket created: 5
Nov  4 09:40:10 Ezekiel input[5788]: Created input device: /org/bluez/input/keyboard0
Nov  4 09:40:10 Ezekiel input[5788]: Failed to listen on control channel
Nov  4 09:40:10 Ezekiel kernel: [   59.872532] Bluetooth: RFCOMM socket layer initialized
Nov  4 09:40:10 Ezekiel kernel: [   59.872682] Bluetooth: RFCOMM TTY layer initialized
Nov  4 09:40:10 Ezekiel kernel: [   59.872684] Bluetooth: RFCOMM ver 1.8
Nov  4 09:40:10 Ezekiel audio[5791]: add_service_record: got record id 0x10000
Nov  4 09:40:10 Ezekiel audio[5791]: add_service_record: got record id 0x10001
Nov  4 09:40:10 Ezekiel audio[5791]: Registered manager path:/org/bluez/audio
Nov  4 09:40:10 Ezekiel kernel: [   59.959318] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
Nov  4 09:40:10 Ezekiel kernel: [   59.959331]  [<f89a4628>] hid_output_report+0x2a8/0x320 [hid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959372]  [<f89ad4a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959397]  [<f89ad76b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959404]  [<f89adaf1>] usbhid_init_reports+0x71/0xf0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959419]  [<f89afea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959425]  [<f89ad98f>] usbhid_open+0xf/0x20 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959440]  [<f88db6ff>] usb_open+0x8f/0xf0 [usbcore]
Nov  4 09:40:10 Ezekiel kernel: [   59.959466]  [<f88db670>] usb_open+0x0/0xf0 [usbcore]
Nov  4 09:40:10 Ezekiel kernel: [   59.959479]  [chrdev_open+173/400] chrdev_open+0xad/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.959489]  [chrdev_open+0/400] chrdev_open+0x0/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.959491]  [__dentry_open+351/448] __dentry_open+0x15f/0x1c0
Nov  4 09:40:10 Ezekiel kernel: [   59.959512]  [fasync_helper+38/224] fasync_helper+0x26/0xe0
Nov  4 09:40:10 Ezekiel kernel: [   59.959519]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959526]  [do_ioctl+132/192] do_ioctl+0x84/0xc0
Nov  4 09:40:10 Ezekiel kernel: [   59.959533]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959541]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
Nov  4 09:40:10 Ezekiel kernel: [   59.959550]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Nov  4 09:40:10 Ezekiel kernel: [   59.959557]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Nov  4 09:40:10 Ezekiel kernel: [   59.959570]  [clip_ioctl+1280/1296] clip_ioctl+0x500/0x510
Nov  4 09:40:10 Ezekiel kernel: [   59.959582]  =======================
Nov  4 09:40:10 Ezekiel kernel: [   59.959583] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
Nov  4 09:40:10 Ezekiel kernel: [   59.959587]  [<f89a4628>] hid_output_report+0x2a8/0x320 [hid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959616]  [<f89ad4a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959633]  [<f89ad76b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959638]  [<f89adaf1>] usbhid_init_reports+0x71/0xf0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959649]  [<f89afea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959653]  [<f89ad98f>] usbhid_open+0xf/0x20 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959664]  [<f88db6ff>] usb_open+0x8f/0xf0 [usbcore]
Nov  4 09:40:10 Ezekiel kernel: [   59.959675]  [<f88db670>] usb_open+0x0/0xf0 [usbcore]
Nov  4 09:40:10 Ezekiel kernel: [   59.959687]  [chrdev_open+173/400] chrdev_open+0xad/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.959694]  [chrdev_open+0/400] chrdev_open+0x0/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.959696]  [__dentry_open+351/448] __dentry_open+0x15f/0x1c0
Nov  4 09:40:10 Ezekiel kernel: [   59.959713]  [fasync_helper+38/224] fasync_helper+0x26/0xe0
Nov  4 09:40:10 Ezekiel kernel: [   59.959719]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959725]  [do_ioctl+132/192] do_ioctl+0x84/0xc0
Nov  4 09:40:10 Ezekiel kernel: [   59.959731]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959738]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
Nov  4 09:40:10 Ezekiel kernel: [   59.959745]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Nov  4 09:40:10 Ezekiel kernel: [   59.959752]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Nov  4 09:40:10 Ezekiel kernel: [   59.959762]  [clip_ioctl+1280/1296] clip_ioctl+0x500/0x510
Nov  4 09:40:10 Ezekiel kernel: [   59.959772]  =======================
Nov  4 09:40:10 Ezekiel kernel: [   59.959773] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
Nov  4 09:40:10 Ezekiel kernel: [   59.959776]  [<f89a4628>] hid_output_report+0x2a8/0x320 [hid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959800]  [<f89ad4a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959815]  [<f89ad76b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959819]  [<f89adaf1>] usbhid_init_reports+0x71/0xf0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959828]  [<f89afea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959832]  [<f89ad98f>] usbhid_open+0xf/0x20 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959842]  [<f88db6ff>] usb_open+0x8f/0xf0 [usbcore]
Nov  4 09:40:10 Ezekiel kernel: [   59.959853]  [<f88db670>] usb_open+0x0/0xf0 [usbcore]
Nov  4 09:40:10 Ezekiel kernel: [   59.959864]  [chrdev_open+173/400] chrdev_open+0xad/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.959871]  [chrdev_open+0/400] chrdev_open+0x0/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.959874]  [__dentry_open+351/448] __dentry_open+0x15f/0x1c0
Nov  4 09:40:10 Ezekiel kernel: [   59.959890]  [fasync_helper+38/224] fasync_helper+0x26/0xe0
Nov  4 09:40:10 Ezekiel kernel: [   59.959896]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959903]  [do_ioctl+132/192] do_ioctl+0x84/0xc0
Nov  4 09:40:10 Ezekiel kernel: [   59.959908]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.959915]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
Nov  4 09:40:10 Ezekiel kernel: [   59.959923]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Nov  4 09:40:10 Ezekiel kernel: [   59.959929]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Nov  4 09:40:10 Ezekiel kernel: [   59.959940]  [clip_ioctl+1280/1296] clip_ioctl+0x500/0x510
Nov  4 09:40:10 Ezekiel kernel: [   59.959949]  =======================
Nov  4 09:40:10 Ezekiel kernel: [   59.964080] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
Nov  4 09:40:10 Ezekiel kernel: [   59.964085]  [<f89a4628>] hid_output_report+0x2a8/0x320 [hid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964109]  [<f89ad4a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964113]  [process_timeout+0/16] process_timeout+0x0/0x10
Nov  4 09:40:10 Ezekiel kernel: [   59.964118]  [schedule_timeout+71/208] schedule_timeout+0x47/0xd0
Nov  4 09:40:10 Ezekiel kernel: [   59.964123]  [finish_wait+45/112] finish_wait+0x2d/0x70
Nov  4 09:40:10 Ezekiel kernel: [   59.964130]  [<f89ad76b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964134]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Nov  4 09:40:10 Ezekiel kernel: [   59.964143]  [<f89afea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964147]  [<f89ad98f>] usbhid_open+0xf/0x20 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964156]  [<f88db6ff>] usb_open+0x8f/0xf0 [usbcore]
Nov  4 09:40:10 Ezekiel kernel: [   59.964167]  [<f88db670>] usb_open+0x0/0xf0 [usbcore]
Nov  4 09:40:10 Ezekiel kernel: [   59.964179]  [chrdev_open+173/400] chrdev_open+0xad/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.964184]  [chrdev_open+0/400] chrdev_open+0x0/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.964187]  [__dentry_open+351/448] __dentry_open+0x15f/0x1c0
Nov  4 09:40:10 Ezekiel kernel: [   59.964200]  [fasync_helper+38/224] fasync_helper+0x26/0xe0
Nov  4 09:40:10 Ezekiel kernel: [   59.964205]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964211]  [do_ioctl+132/192] do_ioctl+0x84/0xc0
Nov  4 09:40:10 Ezekiel kernel: [   59.964215]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964221]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
Nov  4 09:40:10 Ezekiel kernel: [   59.964227]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Nov  4 09:40:10 Ezekiel kernel: [   59.964233]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Nov  4 09:40:10 Ezekiel kernel: [   59.964241]  [clip_ioctl+1280/1296] clip_ioctl+0x500/0x510
Nov  4 09:40:10 Ezekiel kernel: [   59.964249]  =======================
Nov  4 09:40:10 Ezekiel kernel: [   59.964250] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
Nov  4 09:40:10 Ezekiel kernel: [   59.964253]  [<f89a4628>] hid_output_report+0x2a8/0x320 [hid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964272]  [<f89ad4a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964275]  [process_timeout+0/16] process_timeout+0x0/0x10
Nov  4 09:40:10 Ezekiel kernel: [   59.964279]  [schedule_timeout+71/208] schedule_timeout+0x47/0xd0
Nov  4 09:40:10 Ezekiel kernel: [   59.964283]  [finish_wait+45/112] finish_wait+0x2d/0x70
Nov  4 09:40:10 Ezekiel kernel: [   59.964289]  [<f89ad76b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964293]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Nov  4 09:40:10 Ezekiel kernel: [   59.964301]  [<f89afea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964305]  [<f89ad98f>] usbhid_open+0xf/0x20 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964313]  [<f88db6ff>] usb_open+0x8f/0xf0 [usbcore]
Nov  4 09:40:10 Ezekiel kernel: [   59.964323]  [<f88db670>] usb_open+0x0/0xf0 [usbcore]
Nov  4 09:40:10 Ezekiel kernel: [   59.964334]  [chrdev_open+173/400] chrdev_open+0xad/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.964340]  [chrdev_open+0/400] chrdev_open+0x0/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.964342]  [__dentry_open+351/448] __dentry_open+0x15f/0x1c0
Nov  4 09:40:10 Ezekiel kernel: [   59.964355]  [fasync_helper+38/224] fasync_helper+0x26/0xe0
Nov  4 09:40:10 Ezekiel kernel: [   59.964361]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964366]  [do_ioctl+132/192] do_ioctl+0x84/0xc0
Nov  4 09:40:10 Ezekiel kernel: [   59.964371]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.964377]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
Nov  4 09:40:10 Ezekiel kernel: [   59.964383]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Nov  4 09:40:10 Ezekiel kernel: [   59.964388]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Nov  4 09:40:10 Ezekiel kernel: [   59.964397]  [clip_ioctl+1280/1296] clip_ioctl+0x500/0x510
Nov  4 09:40:10 Ezekiel kernel: [   59.964404]  =======================
Nov  4 09:40:10 Ezekiel kernel: [   59.967675] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
Nov  4 09:40:10 Ezekiel kernel: [   59.967681]  [<f89a4628>] hid_output_report+0x2a8/0x320 [hid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967700]  [<f89ad4a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967703]  [process_timeout+0/16] process_timeout+0x0/0x10
Nov  4 09:40:10 Ezekiel kernel: [   59.967707]  [schedule_timeout+71/208] schedule_timeout+0x47/0xd0
Nov  4 09:40:10 Ezekiel kernel: [   59.967712]  [finish_wait+45/112] finish_wait+0x2d/0x70
Nov  4 09:40:10 Ezekiel kernel: [   59.967718]  [<f89ad76b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967722]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Nov  4 09:40:10 Ezekiel kernel: [   59.967729]  [<f89afea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967738]  [schedule+714/2192] schedule+0x2ca/0x890
Nov  4 09:40:10 Ezekiel kernel: [   59.967743]  [chrdev_open+173/400] chrdev_open+0xad/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.967765]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967770]  [do_ioctl+132/192] do_ioctl+0x84/0xc0
Nov  4 09:40:10 Ezekiel kernel: [   59.967775]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967781]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
Nov  4 09:40:10 Ezekiel kernel: [   59.967787]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Nov  4 09:40:10 Ezekiel kernel: [   59.967792]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Nov  4 09:40:10 Ezekiel kernel: [   59.967801]  [clip_ioctl+1280/1296] clip_ioctl+0x500/0x510
Nov  4 09:40:10 Ezekiel kernel: [   59.967808]  =======================
Nov  4 09:40:10 Ezekiel kernel: [   59.967809] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
Nov  4 09:40:10 Ezekiel kernel: [   59.967813]  [<f89a4628>] hid_output_report+0x2a8/0x320 [hid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967831]  [<f89ad4a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967834]  [process_timeout+0/16] process_timeout+0x0/0x10
Nov  4 09:40:10 Ezekiel kernel: [   59.967838]  [schedule_timeout+71/208] schedule_timeout+0x47/0xd0
Nov  4 09:40:10 Ezekiel kernel: [   59.967842]  [finish_wait+45/112] finish_wait+0x2d/0x70
Nov  4 09:40:10 Ezekiel kernel: [   59.967848]  [<f89ad76b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967852]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Nov  4 09:40:10 Ezekiel kernel: [   59.967859]  [<f89afea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967867]  [schedule+714/2192] schedule+0x2ca/0x890
Nov  4 09:40:10 Ezekiel kernel: [   59.967872]  [chrdev_open+173/400] chrdev_open+0xad/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.967893]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967898]  [do_ioctl+132/192] do_ioctl+0x84/0xc0
Nov  4 09:40:10 Ezekiel kernel: [   59.967903]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967908]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
Nov  4 09:40:10 Ezekiel kernel: [   59.967915]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Nov  4 09:40:10 Ezekiel kernel: [   59.967920]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Nov  4 09:40:10 Ezekiel kernel: [   59.967928]  [clip_ioctl+1280/1296] clip_ioctl+0x500/0x510
Nov  4 09:40:10 Ezekiel kernel: [   59.967935]  =======================
Nov  4 09:40:10 Ezekiel kernel: [   59.967937] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
Nov  4 09:40:10 Ezekiel kernel: [   59.967940]  [<f89a4628>] hid_output_report+0x2a8/0x320 [hid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967958]  [<f89ad4a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967961]  [process_timeout+0/16] process_timeout+0x0/0x10
Nov  4 09:40:10 Ezekiel kernel: [   59.967965]  [schedule_timeout+71/208] schedule_timeout+0x47/0xd0
Nov  4 09:40:10 Ezekiel kernel: [   59.967969]  [finish_wait+45/112] finish_wait+0x2d/0x70
Nov  4 09:40:10 Ezekiel kernel: [   59.967975]  [<f89ad76b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967978]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Nov  4 09:40:10 Ezekiel kernel: [   59.967986]  [<f89afea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.967994]  [schedule+714/2192] schedule+0x2ca/0x890
Nov  4 09:40:10 Ezekiel kernel: [   59.967999]  [chrdev_open+173/400] chrdev_open+0xad/0x190
Nov  4 09:40:10 Ezekiel kernel: [   59.968020]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.968025]  [do_ioctl+132/192] do_ioctl+0x84/0xc0
Nov  4 09:40:10 Ezekiel kernel: [   59.968029]  [<f89afa60>] hiddev_ioctl+0x0/0xb50 [usbhid]
Nov  4 09:40:10 Ezekiel kernel: [   59.968035]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
Nov  4 09:40:10 Ezekiel kernel: [   59.968041]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Nov  4 09:40:10 Ezekiel kernel: [   59.968047]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Nov  4 09:40:10 Ezekiel kernel: [   59.968055]  [clip_ioctl+1280/1296] clip_ioctl+0x500/0x510
Nov  4 09:40:10 Ezekiel kernel: [   59.968062]  =======================
Nov  4 09:40:10 Ezekiel anacron[5817]: Anacron 2.3 started on 2007-11-04
Nov  4 09:40:10 Ezekiel anacron[5817]: Normal exit (0 jobs run)
Nov  4 09:40:10 Ezekiel /usr/sbin/cron[5844]: (CRON) INFO (pidfile fd = 3)
Nov  4 09:40:10 Ezekiel /usr/sbin/cron[5845]: (CRON) STARTUP (fork ok)
Nov  4 09:40:10 Ezekiel /usr/sbin/cron[5845]: (CRON) INFO (Running @reboot jobs)
Nov  4 09:40:10 Ezekiel kernel: [   60.167068] usb 7-4.2.1: new full speed USB device using ehci_hcd and address 8
Nov  4 09:40:10 Ezekiel kernel: [   60.264070] usb 7-4.2.1: configuration #1 chosen from 1 choice
Nov  4 09:40:10 Ezekiel NetworkManager: <debug> [1194187210.664648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_000761455E3C'). 
Nov  4 09:40:10 Ezekiel kernel: [   60.355829] Bluetooth: HCI USB driver ver 2.9
Nov  4 09:40:10 Ezekiel hcid[5771]: HCI dev 0 registered
Nov  4 09:40:10 Ezekiel kernel: [   60.357436] usbcore: registered new interface driver hci_usb
Nov  4 09:40:10 Ezekiel hcid[5771]: HCI dev 0 up
Nov  4 09:40:10 Ezekiel hcid[5771]: Device hci0 has been added
Nov  4 09:40:10 Ezekiel NetworkManager: <debug> [1194187210.770978] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_000761455E3C_if1'). 
Nov  4 09:40:10 Ezekiel NetworkManager: <debug> [1194187210.772112] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_000761455E3C_if0'). 
Nov  4 09:40:10 Ezekiel hcid[5771]: Starting security manager 0
Nov  4 09:40:10 Ezekiel NetworkManager: <debug> [1194187210.781267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_000761455E3C_if2'). 
Nov  4 09:40:10 Ezekiel NetworkManager: <debug> [1194187210.782781] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_000761455E3C_if0_bluetooth_hci'). 
Nov  4 09:40:10 Ezekiel NetworkManager: <debug> [1194187210.798884] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_000761455E3C_if3'). 
Nov  4 09:40:10 Ezekiel hcid[5771]: Device hci0 has been activated
Nov  4 09:40:10 Ezekiel avahi-daemon[5736]: Server startup complete. Host name is Ezekiel.local. Local service cookie is 71014160.
Nov  4 09:40:10 Ezekiel NetworkManager: <debug> [1194187210.820080] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_000761455E3C_usbraw'). 
Nov  4 09:40:16 Ezekiel kernel: [   66.493799] wlan0: no IPv6 routers present
Nov  4 09:40:59 Ezekiel NetworkManager: <debug> [1194187259.789151] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_000761455E3C_if0_bluetooth_hci_bluetooth_hci'). 
Nov  4 09:41:00 Ezekiel hidd[5789]: New HID device 00:07:61:35:D7:80 (Logitech Bluetooth Keyboard)
Nov  4 09:41:00 Ezekiel kernel: [  109.957821] input: Logitech Bluetooth Keyboard as /class/input/input9
Nov  4 09:41:00 Ezekiel NetworkManager: <debug> [1194187260.463203] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_000761455E3C_if0_bluetooth_hci_bluetooth_hci_logicaldev_input'). 
Nov  4 09:41:09 Ezekiel hcid[5771]: Default passkey agent (:1.21, /org/bluez/passkey) registered
Nov  4 09:41:09 Ezekiel hcid[5771]: Default authorization agent (:1.21, /org/bluez/auth) registered
Nov  4 09:41:10 Ezekiel NetworkManager: <info>  Updating allowed wireless network lists. 
Nov  4 09:41:11 Ezekiel NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov  4 09:45:21 Ezekiel kernel: [  371.078354] Associated successfully
Nov  4 09:45:21 Ezekiel kernel: [  371.078358] Using G rates
Nov  4 09:50:15 Ezekiel kernel: [  664.313371] Associated successfully
Nov  4 09:50:15 Ezekiel kernel: [  664.313375] Using G rates
Nov  4 09:55:09 Ezekiel kernel: [  957.548834] Associated successfully
Nov  4 09:55:09 Ezekiel kernel: [  957.548839] Using G rates
Nov  4 10:00:02 Ezekiel kernel: [ 1250.782810] Associated successfully
Nov  4 10:00:02 Ezekiel kernel: [ 1250.782815] Using G rates
Nov  4 10:04:56 Ezekiel kernel: [ 1544.018736] Associated successfully
Nov  4 10:04:56 Ezekiel kernel: [ 1544.018741] Using G rates
Nov  4 10:09:49 Ezekiel kernel: [ 1837.254930] Associated successfully
Nov  4 10:09:49 Ezekiel kernel: [ 1837.254935] Using G rates
Nov  4 12:32:50 Ezekiel syslogd 1.4.1#21ubuntu3: restart.
Nov  4 12:32:50 Ezekiel kernel: Inspecting /boot/System.map-2.6.22-14-generic

```

Any suggestions anyone?

---

### Post by HermanAB on 2007-11-04
These kind of issues are usually indicative of a borderline hardware problem.  I suggest going into the BIOS and reducing the clock speed a little.

---

### Post by strikeback03 on 2007-11-04
it's at stock speed, no overclock at all on this machine.

---

### Post by jonthysell on 2007-11-04
```
Nov  4 09:40:06 Ezekiel kernel: [   51.435260] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
Nov  4 09:40:06 Ezekiel kernel: [   51.435262] Copyright (c) 2004-2005, Andrea Merello
Nov  4 09:40:06 Ezekiel kernel: [   51.435263] rtl8180: Initializing module
Nov  4 09:40:06 Ezekiel kernel: [   51.435264] rtl8180: Wireless extensions version 22
Nov  4 09:40:06 Ezekiel kernel: [   51.435265] rtl8180: Initializing proc filesystem
Nov  4 09:40:06 Ezekiel kernel: [   51.435291] rtl8180: Configuring chip resources
Nov  4 09:40:06 Ezekiel kernel: [   51.435305] ACPI: PCI Interrupt 0000:04:04.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
Nov  4 09:40:06 Ezekiel kernel: [   51.435337] rtl8180: Memory mapped space @ 0xfdcfe000 
Nov  4 09:40:06 Ezekiel kernel: [   51.435344] rtl8180: MAC controller is a RTL8185 b/g (V. D)
Nov  4 09:40:06 Ezekiel kernel: [   51.435347] rtl8180: This is a PCI NIC
Nov  4 09:40:06 Ezekiel kernel: [   51.435348] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
Nov  4 09:40:06 Ezekiel kernel: [   51.441454] rtl8180: Card MAC address is 00:0e:2e:6d:6e:3b
Nov  4 09:40:06 Ezekiel kernel: [   51.456686] rtl8180: EEPROM version 105
Nov  4 09:40:06 Ezekiel kernel: [   51.458718] rtl8180: Card reports RF frontend Realtek 8225
Nov  4 09:40:06 Ezekiel kernel: [   51.458719] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
Nov  4 09:40:06 Ezekiel kernel: [   51.458720] rtl8180: WW:use it with care and at your own risk and
Nov  4 09:40:06 Ezekiel kernel: [   51.458722] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
Nov  4 09:40:06 Ezekiel kernel: [   51.458723] rtl8180: Energy threshold: b
Nov  4 09:40:06 Ezekiel kernel: [   51.458725] rtl8180: PAPE from CONFIG2: 6
Nov  4 09:40:06 Ezekiel kernel: [   51.458782] rtl8180: IRQ 9
Nov  4 09:40:06 Ezekiel kernel: [   51.458848] rtl8180: Driver probe completed
Nov  4 09:40:06 Ezekiel kernel: [   51.458848] 
Nov  4 09:40:06 Ezekiel kernel: [   51.488729] rtl8180: Bringing up iface
Nov  4 09:40:06 Ezekiel kernel: [   51.697365] rtl8180: Card successfully reset
```

Your problem is most likely the wireless card. I have a Realtek RTL8185 as well, and it does the same thing, causes random system freezes. It's a hardware issue, as it happens in both Linux and Windows. 

Found your post while trying to search for a solution for my freezing issue.

---

### Post by strikeback03 on 2007-11-04
Wireless occasionally dies in Windows, but never takes the system with it.  That thing has been a POS though, so should probably replace it.

---

### Post by strikeback03 on 2007-11-05
testing with kernel option maxcpus=1 gives much better stability, so problem might be related to the nvidia driver bug with dual-core.  Or some other dual-core related lack of support.

---

### Post by Aathos on 2007-11-07
That wireless driver has known issues that cause those symptoms when trying to connect to encrypted networks.  You might try blacklisting the native driver and using the windows driver with nidswrapper.

---

### Post by Tuckwoor on 2007-11-08
I am getting the same lockups in gutsy and only thing I can see in syslogs that seems to be around time of crashes is message about wireless networks as said previously:

```
NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```

There is no wireless adaptor in my pc...

---

### Post by FoxOne on 2007-12-12
> **jonthysell said:**
> ```
Nov  4 09:40:06 Ezekiel kernel: [   51.435260] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
Nov  4 09:40:06 Ezekiel kernel: [   51.435262] Copyright (c) 2004-2005, Andrea Merello
Nov  4 09:40:06 Ezekiel kernel: [   51.435263] rtl8180: Initializing module
Nov  4 09:40:06 Ezekiel kernel: [   51.435264] rtl8180: Wireless extensions version 22
Nov  4 09:40:06 Ezekiel kernel: [   51.435265] rtl8180: Initializing proc filesystem
Nov  4 09:40:06 Ezekiel kernel: [   51.435291] rtl8180: Configuring chip resources
Nov  4 09:40:06 Ezekiel kernel: [   51.435305] ACPI: PCI Interrupt 0000:04:04.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
Nov  4 09:40:06 Ezekiel kernel: [   51.435337] rtl8180: Memory mapped space @ 0xfdcfe000 
Nov  4 09:40:06 Ezekiel kernel: [   51.435344] rtl8180: MAC controller is a RTL8185 b/g (V. D)
Nov  4 09:40:06 Ezekiel kernel: [   51.435347] rtl8180: This is a PCI NIC
Nov  4 09:40:06 Ezekiel kernel: [   51.435348] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
Nov  4 09:40:06 Ezekiel kernel: [   51.441454] rtl8180: Card MAC address is 00:0e:2e:6d:6e:3b
Nov  4 09:40:06 Ezekiel kernel: [   51.456686] rtl8180: EEPROM version 105
Nov  4 09:40:06 Ezekiel kernel: [   51.458718] rtl8180: Card reports RF frontend Realtek 8225
Nov  4 09:40:06 Ezekiel kernel: [   51.458719] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
Nov  4 09:40:06 Ezekiel kernel: [   51.458720] rtl8180: WW:use it with care and at your own risk and
Nov  4 09:40:06 Ezekiel kernel: [   51.458722] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
Nov  4 09:40:06 Ezekiel kernel: [   51.458723] rtl8180: Energy threshold: b
Nov  4 09:40:06 Ezekiel kernel: [   51.458725] rtl8180: PAPE from CONFIG2: 6
Nov  4 09:40:06 Ezekiel kernel: [   51.458782] rtl8180: IRQ 9
Nov  4 09:40:06 Ezekiel kernel: [   51.458848] rtl8180: Driver probe completed
Nov  4 09:40:06 Ezekiel kernel: [   51.458848] 
Nov  4 09:40:06 Ezekiel kernel: [   51.488729] rtl8180: Bringing up iface
Nov  4 09:40:06 Ezekiel kernel: [   51.697365] rtl8180: Card successfully reset
```

Your problem is most likely the wireless card. I have a Realtek RTL8185 as well, and it does the same thing, causes random system freezes. It's a hardware issue, as it happens in both Linux and Windows. 

Found your post while trying to search for a solution for my freezing issue.

I have the same issue, but it started before I installed my Netgear WG311 wireless card. So I don't think it's related to a wireless issue. I'd like to know if you get this issue with the card removed

---

### Post by jonthysell on 2008-02-10
> **FoxOne said:**
> I have the same issue, but it started before I installed my Netgear WG311 wireless card. So I don't think it's related to a wireless issue. I'd like to know if you get this issue with the card removed

I've since replaced the card with an external wireless/ethernet bridge, and the problem is gone.

---

