---
title: "Ubuntu 12.04.4 very slow boot, error in dmesg"
date: 2014-06-23
forum: General Help
---

### Post by handsaway on 2014-06-23
Hi,
my installation of ubuntu 12.04 takes 1min22 to boot and I see several errors in the dmesg output. I need help understanding how to correct these, so I posted the errors below. Any ideas?
I also attached the corresponding bootchart in case it helps. I must confess I don't know how to interpret it.

My specs are:
Ubuntu 12.04.4, i686
 Lenovo ThinkPad T420,
 CPU Intel Core i5-2520M 2.5GHz,
 Memory 7.8 GB.

The first large gap in dmesg is:
```
[    3.685487] acpi device:00: registered as cooling_device4
[    3.685588] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    3.685645] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    3.685684] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.764516] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    4.764519] EXT4-fs (sda5): write access will be enabled during recovery
[    6.164577] EXT4-fs (sda5): recovery complete
[    6.168063] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   20.236057] Adding 8601596k swap on /dev/sda6.  Priority:-1 extents:1 across:8601596k 
[   20.705189] udevd[592]: starting version 175
[   20.733503] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.809096] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   20.987461] lp: driver loaded but no devices found
```
Is it the EXT4 recovery or a process starting at 20 (e.g. adding swap, or ADDRCONF) that takes time?
What can make a recovery necessary?

And here is an odd segment in the dmesg:
```
[   36.310455] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.310456] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.310458] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   37.153207] init: plymouth-stop pre-start process (2787) terminated with status 1
[   40.891538] eth0: no IPv6 routers present
[   45.109066] [drm] Changing LVDS panel from (-hsync, +vsync) to (-hsync, -vsync)
[   46.683943] wlan0: no IPv6 routers present
[   47.649398] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a0d0000, was 1a000000
[   52.762780] FIREWALL: IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:8e70:5aff:fe98:9a20 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=87 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=47 
[   53.667438] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:21:cc:c6:bc:1e:08:00 SRC=9.162.33.86 DST=255.255.255.255 LEN=382 TOS=0x08 PREC=0x40 TTL=128 ID=25792 PROTO=UDP SPT=17500 DPT=17500 LEN=362 
[   70.637612] usb 1-1.4: new full-speed USB device number 5 using ehci_hcd
[   74.125249] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=255.255.255.255 LEN=192 TOS=0x00 PREC=0x00 TTL=64 ID=35972 DF PROTO=UDP SPT=17500 DPT=17500 LEN=172 
[   93.781633] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=12824 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 

```
Here, I don't know what is happening. I know the LVDS panel is related to an external monitor. I tried booting without being plugged, but boot time does not change.

And here is the complete dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-64-generic-pae (buildd@tipua) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #97-Ubuntu SMP Wed Jun 4 22:22:15 UTC 2014 (Ubuntu 3.2.0-64.97-generic-pae 3.2.59)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000da99f000 (usable)
[    0.000000]  BIOS-e820: 00000000da99f000 - 00000000dae9f000 (reserved)
[    0.000000]  BIOS-e820: 00000000dae9f000 - 00000000daf9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000daf9f000 - 00000000dafff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dafff000 - 00000000db000000 (usable)
[    0.000000]  BIOS-e820: 00000000db000000 - 00000000dfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed08000 - 00000000fed09000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd20000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000021e600000 (usable)
[    0.000000]  BIOS-e820: 000000021e600000 - 000000021e800000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: LENOVO 4180AG8/4180AG8, BIOS 83ET67WW (1.37 ) 11/28/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x21e600 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0C0000000 mask FE0000000 write-back
[    0.000000]   4 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   5 base 0DB000000 mask FFF000000 uncachable
[    0.000000]   6 base 100000000 mask F00000000 write-back
[    0.000000]   7 base 200000000 mask FE0000000 write-back
[    0.000000]   8 base 21F000000 mask FFF000000 uncachable
[    0.000000]   9 base 21E800000 mask FFF800000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffa000-2000000
[    0.000000] RAMDISK: 35912000 - 36c81000
[    0.000000] ACPI: RSDP 000f00e0 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT daffe120 000AC (v01 LENOVO TP-83    00001370 PTEC 00000002)
[    0.000000] ACPI: FACP dafe8000 000F4 (v04 LENOVO TP-83    00001370 PTL  00000002)
[    0.000000] ACPI: DSDT dafeb000 0E40B (v01 LENOVO TP-83    00001370 INTL 20061109)
[    0.000000] ACPI: FACS daf2d000 00040
[    0.000000] ACPI: SLIC daffd000 00176 (v01 LENOVO TP-83    00001370 PTEC 00000001)
[    0.000000] ACPI: SSDT daffc000 00249 (v01 LENOVO TP-SSDT2 00000200 INTL 20061109)
[    0.000000] ACPI: SSDT daffb000 00033 (v01 LENOVO TP-SSDT1 00000100 INTL 20061109)
[    0.000000] ACPI: SSDT daffa000 00797 (v01 LENOVO SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: HPET dafe7000 00038 (v01 LENOVO TP-83    00001370 PTL  00000002)
[    0.000000] ACPI: APIC dafe6000 00098 (v01 LENOVO TP-83    00001370 PTL  00000002)
[    0.000000] ACPI: MCFG dafe5000 0003C (v01 LENOVO TP-83    00001370 PTL  00000002)
[    0.000000] ACPI: ECDT dafe4000 00052 (v01 LENOVO TP-83    00001370 PTL  00000002)
[    0.000000] ACPI: ASF! dafea000 000A5 (v32 LENOVO TP-83    00001370 PTL  00000002)
[    0.000000] ACPI: TCPA dafe3000 00032 (v02    PTL   LENOVO 06040000 LNVO 00000001)
[    0.000000] ACPI: SSDT dafe2000 00A27 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT dafe1000 00996 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: DMAR dafe0000 000E8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: UEFI dafdf000 0003E (v01 LENOVO TP-83    00001370 PTL  00000002)
[    0.000000] ACPI: UEFI dafde000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI dafdd000 00292 (v01 LENOVO TP-83    00001370 PTL  00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 7786MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0021e600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000da99f
[    0.000000]     0: 0x000dafff -> 0x000db000
[    0.000000]     0: 0x00100000 -> 0x0021e600
[    0.000000] On node 0 totalpages: 2067245
[    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f1542200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 221990 pages, LIFO batch:31
[    0.000000]   HighMem zone: 15573 pages used for memmap
[    0.000000]   HighMem zone: 1823949 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] Allocating PCI resources starting at dfa00000 (gap: dfa00000:18600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7b7a000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 [0] 6 [0] 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2049888
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-64-generic-pae root=UUID=dfe1130a-a0e6-4e37-9eae-6cb360ce9a40 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 35544832 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0021e600)
[    0.000000] Memory: 8132636k/8886272k available (5848k kernel code, 136344k reserved, 2860k data, 744k init, 7358088k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1882000 - 0xc193c000   ( 744 kB)
[    0.000000]       .data : 0xc15b63bc - 0xc18813c0   (2860 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b63bc   (5848 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2491.879 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 4983.75 BogoMIPS (lpj=9967516)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000025] Security Framework initialized
[    0.000037] AppArmor: AppArmor initialized
[    0.000038] Yama: becoming mindful.
[    0.000078] Mount-cache hash table entries: 512
[    0.000178] Initializing cgroup subsys cpuacct
[    0.000183] Initializing cgroup subsys memory
[    0.000190] Initializing cgroup subsys devices
[    0.000191] Initializing cgroup subsys freezer
[    0.000193] Initializing cgroup subsys blkio
[    0.000198] Initializing cgroup subsys perf_event
[    0.000219] Disabled fast string operations
[    0.000221] CPU: Physical Processor ID: 0
[    0.000223] CPU: Processor Core ID: 0
[    0.000227] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000228] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.000231] mce: CPU supports 7 MCE banks
[    0.000241] CPU0: Thermal monitoring enabled (TM1)
[    0.000248] using mwait in idle threads.
[    0.002359] ACPI: Core revision 20110623
[    0.010071] ftrace: allocating 26153 entries in 52 pages
[    0.019130] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.019539] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059133] CPU0: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz stepping 07
[    0.163997] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.164002] PEBS disabled due to CPU errata.
[    0.164005] ... version:                3
[    0.164006] ... bit width:              48
[    0.164007] ... generic registers:      4
[    0.164008] ... value mask:             0000ffffffffffff
[    0.164010] ... max period:             000000007fffffff
[    0.164011] ... fixed-purpose events:   3
[    0.164012] ... event mask:             000000070000000f
[    0.164190] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164264] CPU 1 irqstacks, hard=f7558000 soft=f755a000
[    0.164265] Booting Node   0, Processors  #1
[    0.164267] smpboot cpu 1: start_ip = 99000
[    0.174537] Initializing CPU#1
[    0.251803] Disabled fast string operations
[    0.271828] NMI watchdog enabled, takes one hw-pmu counter.
[    0.271906] CPU 2 irqstacks, hard=f7566000 soft=f7568000
[    0.271908]  #2
[    0.271909] smpboot cpu 2: start_ip = 99000
[    0.282128] Initializing CPU#2
[    0.359553] Disabled fast string operations
[    0.379573] NMI watchdog enabled, takes one hw-pmu counter.
[    0.379647] CPU 3 irqstacks, hard=f759c000 soft=f759e000
[    0.379648]  #3
[    0.379649] smpboot cpu 3: start_ip = 99000
[    0.389868] Initializing CPU#3
[    0.467304] Disabled fast string operations
[    0.487312] NMI watchdog enabled, takes one hw-pmu counter.
[    0.487338] Brought up 4 CPUs
[    0.487340] Total of 4 processors activated (19934.66 BogoMIPS).
[    0.490757] devtmpfs: initialized
[    0.490864] EVM: security.selinux
[    0.490865] EVM: security.SMACK64
[    0.490866] EVM: security.capability
[    0.490889] PM: Registering ACPI NVS region at dae9f000 (1048576 bytes)
[    0.491689] print_constraints: dummy: 
[    0.491720] RTC time: 10:04:48, date: 06/23/14
[    0.491752] NET: Registered protocol family 16
[    0.491833] Trying to unpack rootfs image as initramfs...
[    0.491861] EISA bus registered
[    0.491876] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.491878] ACPI: bus type pci registered
[    0.492110] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.492113] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.492115] PCI: Using MMCONFIG for extended config space
[    0.492116] PCI: Using configuration type 1 for base access
[    0.493248] bio: create slab <bio-0> at 0
[    0.493323] ACPI: Added _OSI(Module Device)
[    0.493325] ACPI: Added _OSI(Processor Device)
[    0.493327] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.493329] ACPI: Added _OSI(Processor Aggregator Device)
[    0.495049] ACPI: EC: EC description table is found, configuring boot EC
[    0.500196] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.587497] ACPI: SSDT dae8c018 008C0 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.587940] ACPI: Dynamic OEM Table Load:
[    0.587943] ACPI: SSDT   (null) 008C0 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.619187] ACPI: SSDT dae8da98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.619667] ACPI: Dynamic OEM Table Load:
[    0.619669] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.650977] ACPI: SSDT dae8bd98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.651418] ACPI: Dynamic OEM Table Load:
[    0.651420] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.675394] ACPI: Interpreter enabled
[    0.675401] ACPI: (supports S0 S3 S4 S5)
[    0.675421] ACPI: Using IOAPIC for interrupt routing
[    0.699151] ACPI: Power Resource [PUBS] (on)
[    0.701912] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.702691] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.702693] HEST: Table not found.
[    0.702697] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.702804] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.702856] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.702859] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.702861] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.702864] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfebfffff]
[    0.702866] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed4bfff]
[    0.702879] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    0.702918] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
[    0.702928] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.702935] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.702940] pci 0000:00:02.0: reg 20: [io  0x5000-0x503f]
[    0.702996] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.703021] pci 0000:00:16.0: reg 10: [mem 0xf2525000-0xf252500f 64bit]
[    0.703100] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.703105] pci 0000:00:16.0: PME# disabled
[    0.703129] pci 0000:00:16.3: [8086:1c3d] type 0 class 0x000700
[    0.703148] pci 0000:00:16.3: reg 10: [io  0x50b0-0x50b7]
[    0.703158] pci 0000:00:16.3: reg 14: [mem 0xf252c000-0xf252cfff]
[    0.703261] pci 0000:00:19.0: [8086:1502] type 0 class 0x000200
[    0.703279] pci 0000:00:19.0: reg 10: [mem 0xf2500000-0xf251ffff]
[    0.703288] pci 0000:00:19.0: reg 14: [mem 0xf252b000-0xf252bfff]
[    0.703297] pci 0000:00:19.0: reg 18: [io  0x5080-0x509f]
[    0.703363] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.703367] pci 0000:00:19.0: PME# disabled
[    0.703393] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.703415] pci 0000:00:1a.0: reg 10: [mem 0xf252a000-0xf252a3ff]
[    0.703510] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.703514] pci 0000:00:1a.0: PME# disabled
[    0.703541] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.703558] pci 0000:00:1b.0: reg 10: [mem 0xf2520000-0xf2523fff 64bit]
[    0.703629] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.703633] pci 0000:00:1b.0: PME# disabled
[    0.703661] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.703792] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.703797] pci 0000:00:1c.0: PME# disabled
[    0.703833] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    0.703962] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.703967] pci 0000:00:1c.1: PME# disabled
[    0.704002] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    0.704133] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.704138] pci 0000:00:1c.3: PME# disabled
[    0.704174] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
[    0.704304] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.704309] pci 0000:00:1c.4: PME# disabled
[    0.704348] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.704370] pci 0000:00:1d.0: reg 10: [mem 0xf2529000-0xf25293ff]
[    0.704463] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.704467] pci 0000:00:1d.0: PME# disabled
[    0.704493] pci 0000:00:1f.0: [8086:1c4f] type 0 class 0x000601
[    0.704623] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    0.704642] pci 0000:00:1f.2: reg 10: [io  0x50a8-0x50af]
[    0.704651] pci 0000:00:1f.2: reg 14: [io  0x50bc-0x50bf]
[    0.704659] pci 0000:00:1f.2: reg 18: [io  0x50a0-0x50a7]
[    0.704668] pci 0000:00:1f.2: reg 1c: [io  0x50b8-0x50bb]
[    0.704676] pci 0000:00:1f.2: reg 20: [io  0x5060-0x507f]
[    0.704685] pci 0000:00:1f.2: reg 24: [mem 0xf2528000-0xf25287ff]
[    0.704731] pci 0000:00:1f.2: PME# supported from D3hot
[    0.704735] pci 0000:00:1f.2: PME# disabled
[    0.704754] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.704771] pci 0000:00:1f.3: reg 10: [mem 0xf2524000-0xf25240ff 64bit]
[    0.704793] pci 0000:00:1f.3: reg 20: [io  0xefa0-0xefbf]
[    0.704892] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.705135] pci 0000:03:00.0: [8086:0085] type 0 class 0x000280
[    0.705284] pci 0000:03:00.0: reg 10: [mem 0xf2400000-0xf2401fff 64bit]
[    0.706004] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.706032] pci 0000:03:00.0: PME# disabled
[    0.710841] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.710850] pci 0000:00:1c.1:   bridge window [mem 0xf2400000-0xf24fffff]
[    0.710930] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    0.710935] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.710940] pci 0000:00:1c.3:   bridge window [mem 0xf1c00000-0xf23fffff]
[    0.710949] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
[    0.711091] pci 0000:0d:00.0: [1180:e823] type 0 class 0x000880
[    0.711110] pci 0000:0d:00.0: MMC controller base frequency changed to 50Mhz.
[    0.711137] pci 0000:0d:00.0: reg 10: [mem 0xf1400000-0xf14000ff]
[    0.711335] pci 0000:0d:00.0: supports D1 D2
[    0.711337] pci 0000:0d:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.711343] pci 0000:0d:00.0: PME# disabled
[    0.718778] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    0.718783] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.718789] pci 0000:00:1c.4:   bridge window [mem 0xf1400000-0xf1bfffff]
[    0.718799] pci 0000:00:1c.4:   bridge window [mem 0xf0c00000-0xf13fffff 64bit pref]
[    0.718832] pci_bus 0000:00: on NUMA node 0
[    0.718837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.718945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.718972] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.718999] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.719027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.719159]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.719308]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.719310] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.721464] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.721522] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.721576] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.721630] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11)
[    0.721682] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11)
[    0.721727] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.721781] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11)
[    0.721834] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11)
[    0.721949] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.721956] vgaarb: loaded
[    0.721957] vgaarb: bridge control possible 0000:00:02.0
[    0.722069] i2c-core: driver [aat2870] using legacy suspend method
[    0.722070] i2c-core: driver [aat2870] using legacy resume method
[    0.722130] SCSI subsystem initialized
[    0.722183] libata version 3.00 loaded.
[    0.722227] usbcore: registered new interface driver usbfs
[    0.722237] usbcore: registered new interface driver hub
[    0.722261] usbcore: registered new device driver usb
[    0.722348] PCI: Using ACPI for IRQ routing
[    0.724110] PCI: pci_cache_line_size set to 64 bytes
[    0.724319] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.724322] reserve RAM buffer: 00000000da99f000 - 00000000dbffffff 
[    0.724324] reserve RAM buffer: 00000000db000000 - 00000000dbffffff 
[    0.724326] reserve RAM buffer: 000000021e600000 - 000000021fffffff 
[    0.724414] NetLabel: Initializing
[    0.724415] NetLabel:  domain hash size = 128
[    0.724416] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.724425] NetLabel:  unlabeled traffic allowed by default
[    0.724483] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.724488] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.726499] Switching to clocksource hpet
[    0.732337] AppArmor: AppArmor Filesystem Enabled
[    0.732359] pnp: PnP ACPI init
[    0.732373] ACPI: bus type pnp registered
[    0.732716] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.732718] pnp 00:00: [mem 0x000c0000-0x000c3fff]
[    0.732720] pnp 00:00: [mem 0x000c4000-0x000c7fff]
[    0.732722] pnp 00:00: [mem 0x000c8000-0x000cbfff]
[    0.732724] pnp 00:00: [mem 0x000cc000-0x000cffff]
[    0.732725] pnp 00:00: [mem 0x000d0000-0x000d3fff]
[    0.732727] pnp 00:00: [mem 0x000d4000-0x000d7fff]
[    0.732729] pnp 00:00: [mem 0x000d8000-0x000dbfff]
[    0.732731] pnp 00:00: [mem 0x000dc000-0x000dffff]
[    0.732732] pnp 00:00: [mem 0x000e0000-0x000e3fff]
[    0.732734] pnp 00:00: [mem 0x000e4000-0x000e7fff]
[    0.732736] pnp 00:00: [mem 0x000e8000-0x000ebfff]
[    0.732737] pnp 00:00: [mem 0x000ec000-0x000effff]
[    0.732739] pnp 00:00: [mem 0x000f0000-0x000fffff]
[    0.732741] pnp 00:00: [mem 0x00100000-0xdf9fffff]
[    0.732743] pnp 00:00: [mem 0xfec00000-0xfed3ffff]
[    0.732744] pnp 00:00: [mem 0xfed4c000-0xffffffff]
[    0.732796] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.732798] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.732800] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.732803] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    0.732805] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    0.732807] system 00:00: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.732809] system 00:00: [mem 0x000d4000-0x000d7fff] has been reserved
[    0.732811] system 00:00: [mem 0x000d8000-0x000dbfff] has been reserved
[    0.732813] system 00:00: [mem 0x000dc000-0x000dffff] has been reserved
[    0.732815] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.732818] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.732820] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.732822] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.732824] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.732827] system 00:00: [mem 0x00100000-0xdf9fffff] could not be reserved
[    0.732829] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.732831] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    0.732835] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.732853] pnp 00:01: [bus 00-fe]
[    0.732855] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.732857] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.732859] pnp 00:01: [io  0x0d00-0xffff window]
[    0.732861] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.732864] pnp 00:01: [mem 0x000c0000-0x000c3fff window]
[    0.732866] pnp 00:01: [mem 0x000c4000-0x000c7fff window]
[    0.732868] pnp 00:01: [mem 0x000c8000-0x000cbfff window]
[    0.732870] pnp 00:01: [mem 0x000cc000-0x000cffff window]
[    0.732871] pnp 00:01: [mem 0x000d0000-0x000d3fff window]
[    0.732873] pnp 00:01: [mem 0x000d4000-0x000d7fff window]
[    0.732875] pnp 00:01: [mem 0x000d8000-0x000dbfff window]
[    0.732877] pnp 00:01: [mem 0x000dc000-0x000dffff window]
[    0.732879] pnp 00:01: [mem 0x000e0000-0x000e3fff window]
[    0.732881] pnp 00:01: [mem 0x000e4000-0x000e7fff window]
[    0.732882] pnp 00:01: [mem 0x000e8000-0x000ebfff window]
[    0.732884] pnp 00:01: [mem 0x000ec000-0x000effff window]
[    0.732886] pnp 00:01: [mem 0xdfa00000-0xfebfffff window]
[    0.732888] pnp 00:01: [mem 0xfed40000-0xfed4bfff window]
[    0.732936] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.732989] pnp 00:02: [io  0x0010-0x001f]
[    0.732991] pnp 00:02: [io  0x0090-0x009f]
[    0.732993] pnp 00:02: [io  0x0024-0x0025]
[    0.732994] pnp 00:02: [io  0x0028-0x0029]
[    0.732996] pnp 00:02: [io  0x002c-0x002d]
[    0.732997] pnp 00:02: [io  0x0030-0x0031]
[    0.732999] pnp 00:02: [io  0x0034-0x0035]
[    0.733000] pnp 00:02: [io  0x0038-0x0039]
[    0.733002] pnp 00:02: [io  0x003c-0x003d]
[    0.733003] pnp 00:02: [io  0x00a4-0x00a5]
[    0.733005] pnp 00:02: [io  0x00a8-0x00a9]
[    0.733007] pnp 00:02: [io  0x00ac-0x00ad]
[    0.733008] pnp 00:02: [io  0x00b0-0x00b5]
[    0.733010] pnp 00:02: [io  0x00b8-0x00b9]
[    0.733011] pnp 00:02: [io  0x00bc-0x00bd]
[    0.733013] pnp 00:02: [io  0x0050-0x0053]
[    0.733014] pnp 00:02: [io  0x0072-0x0077]
[    0.733016] pnp 00:02: [io  0x0400-0x047f]
[    0.733018] pnp 00:02: [io  0x0500-0x057f]
[    0.733019] pnp 00:02: [io  0x0800-0x080f]
[    0.733021] pnp 00:02: [io  0x15e0-0x15ef]
[    0.733022] pnp 00:02: [io  0x1600-0x167f]
[    0.733024] pnp 00:02: [mem 0xf8000000-0xfbffffff]
[    0.733026] pnp 00:02: [mem 0x00000000-0x00000fff]
[    0.733028] pnp 00:02: [mem 0xfed1c000-0xfed1ffff]
[    0.733029] pnp 00:02: [mem 0xfed10000-0xfed13fff]
[    0.733031] pnp 00:02: [mem 0xfed18000-0xfed18fff]
[    0.733033] pnp 00:02: [mem 0xfed19000-0xfed19fff]
[    0.733034] pnp 00:02: [mem 0xfed45000-0xfed4bfff]
[    0.733084] system 00:02: [io  0x0400-0x047f] has been reserved
[    0.733086] system 00:02: [io  0x0500-0x057f] has been reserved
[    0.733088] system 00:02: [io  0x0800-0x080f] has been reserved
[    0.733090] system 00:02: [io  0x15e0-0x15ef] has been reserved
[    0.733092] system 00:02: [io  0x1600-0x167f] has been reserved
[    0.733095] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.733097] system 00:02: [mem 0x00000000-0x00000fff] could not be reserved
[    0.733100] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.733102] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.733104] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.733106] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.733109] system 00:02: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.733111] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.733148] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.733174] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.733182] pnp 00:04: [io  0x0000-0x000f]
[    0.733183] pnp 00:04: [io  0x0080-0x008f]
[    0.733185] pnp 00:04: [io  0x00c0-0x00df]
[    0.733187] pnp 00:04: [dma 4]
[    0.733213] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.733220] pnp 00:05: [io  0x0061]
[    0.733244] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.733251] pnp 00:06: [io  0x00f0]
[    0.733260] pnp 00:06: [irq 13]
[    0.733286] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.733293] pnp 00:07: [io  0x0070-0x0071]
[    0.733299] pnp 00:07: [irq 8]
[    0.733325] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.733332] pnp 00:08: [io  0x0060]
[    0.733333] pnp 00:08: [io  0x0064]
[    0.733338] pnp 00:08: [irq 1]
[    0.733363] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.733373] pnp 00:09: [irq 12]
[    0.733403] pnp 00:09: Plug and Play ACPI device, IDs LEN0015 PNP0f13 (active)
[    0.733431] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.733458] pnp 00:0a: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    0.733802] pnp: PnP ACPI: found 11 devices
[    0.733804] ACPI: ACPI bus type pnp unregistered
[    0.733806] PnPBIOS: Disabled by ACPI PNP
[    0.770565] PCI: max bus depth: 1 pci_try_num: 2
[    0.770626] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.770644] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.770651] pci 0000:00:1c.1:   bridge window [mem 0xf2400000-0xf24fffff]
[    0.770664] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    0.770668] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.770675] pci 0000:00:1c.3:   bridge window [mem 0xf1c00000-0xf23fffff]
[    0.770680] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
[    0.770689] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    0.770693] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.770700] pci 0000:00:1c.4:   bridge window [mem 0xf1400000-0xf1bfffff]
[    0.770705] pci 0000:00:1c.4:   bridge window [mem 0xf0c00000-0xf13fffff 64bit pref]
[    0.770733] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.770745] pci 0000:00:1c.0: setting latency timer to 64
[    0.770756] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.770765] pci 0000:00:1c.1: setting latency timer to 64
[    0.770775] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.770784] pci 0000:00:1c.3: setting latency timer to 64
[    0.770791] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.770800] pci 0000:00:1c.4: setting latency timer to 64
[    0.770804] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.770806] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.770808] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.770810] pci_bus 0000:00: resource 7 [mem 0xdfa00000-0xfebfffff]
[    0.770812] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed4bfff]
[    0.770814] pci_bus 0000:03: resource 1 [mem 0xf2400000-0xf24fffff]
[    0.770816] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
[    0.770818] pci_bus 0000:05: resource 1 [mem 0xf1c00000-0xf23fffff]
[    0.770820] pci_bus 0000:05: resource 2 [mem 0xf0400000-0xf0bfffff 64bit pref]
[    0.770822] pci_bus 0000:0d: resource 0 [io  0x3000-0x3fff]
[    0.770824] pci_bus 0000:0d: resource 1 [mem 0xf1400000-0xf1bfffff]
[    0.770826] pci_bus 0000:0d: resource 2 [mem 0xf0c00000-0xf13fffff 64bit pref]
[    0.770858] NET: Registered protocol family 2
[    0.770916] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.771090] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.771288] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.771383] TCP: Hash tables configured (established 131072 bind 65536)
[    0.771385] TCP reno registered
[    0.771388] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.771392] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.771450] NET: Registered protocol family 1
[    0.771460] pci 0000:00:02.0: Boot video device
[    0.771475] pci 0000:00:1a.0: power state changed by ACPI to D0
[    0.771479] pci 0000:00:1a.0: power state changed by ACPI to D0
[    0.771485] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.771515] pci 0000:00:1a.0: PCI INT A disabled
[    0.771535] pci 0000:00:1d.0: power state changed by ACPI to D0
[    0.771539] pci 0000:00:1d.0: power state changed by ACPI to D0
[    0.771548] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.771565] pci 0000:00:1d.0: PCI INT A disabled
[    0.771645] PCI: CLS 64 bytes, default 64
[    0.771648] DMAR: Host address width 36
[    0.771650] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.771656] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.771658] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.771663] IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.771665] DMAR: RMRR base: 0x000000dacd5000 end: 0x000000dacebfff
[    0.771667] DMAR: RMRR base: 0x000000db800000 end: 0x000000df9fffff
[    0.772142] audit: initializing netlink socket (disabled)
[    0.772149] type=2000 audit(1403517888.616:1): initialized
[    0.791852] highmem bounce pool size: 64 pages
[    0.791857] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.794039] VFS: Disk quotas dquot_6.5.2
[    0.794087] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.794547] fuse init (API version 7.17)
[    0.794630] msgmni has been set to 1512
[    0.794978] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.795006] io scheduler noop registered
[    0.795009] io scheduler deadline registered
[    0.795014] io scheduler cfq registered (default)
[    0.795389] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.795409] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.795462] intel_idle: MWAIT substates: 0x21120
[    0.795464] intel_idle: v0.4 model 0x2A
[    0.795465] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.795717] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.795938] ACPI: AC Adapter [AC] (on-line)
[    0.796059] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.796247] ACPI: Lid Switch [LID]
[    0.796333] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.796337] ACPI: Sleep Button [SLPB]
[    0.796429] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.796432] ACPI: Power Button [PWRF]
[    0.805250] thermal LNXTHERM:00: registered as thermal_zone0
[    0.805252] ACPI: Thermal Zone [THM0] (40 C)
[    0.805270] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.805277] ACPI: Battery Slot [BAT0] (battery present)
[    0.805302] ERST: Table is not found!
[    0.805303] GHES: HEST is not enabled!
[    0.805390] isapnp: Scanning for PnP cards...
[    0.805402] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.817270] ACPI: Battery Slot [BAT0] (battery present)
[    0.856108] Freeing initrd memory: 19900k freed
[    1.158594] isapnp: No Plug & Play device found
[    1.185975] serial 0000:00:16.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.206201] 0000:00:16.3: ttyS4 at I/O 0x50b0 (irq = 19) is a 16550A
[    1.225832] Linux agpgart interface v0.103
[    1.225918] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.225980] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.226858] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.226970] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.228252] brd: module loaded
[    1.228897] loop: module loaded
[    1.229026] ahci 0000:00:1f.2: version 3.0
[    1.229038] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.229084] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.229114] ahci: SSS flag set, parallel bus scan disabled
[    1.241580] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1b impl SATA mode
[    1.241590] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
[    1.241602] ahci 0000:00:1f.2: setting latency timer to 64
[    1.265992] scsi0 : ahci
[    1.266072] scsi1 : ahci
[    1.266134] scsi2 : ahci
[    1.266195] scsi3 : ahci
[    1.266256] scsi4 : ahci
[    1.266315] scsi5 : ahci
[    1.266758] ata1: SATA max UDMA/133 abar m2048@0xf2528000 port 0xf2528100 irq 40
[    1.266761] ata2: SATA max UDMA/133 abar m2048@0xf2528000 port 0xf2528180 irq 40
[    1.266763] ata3: DUMMY
[    1.266766] ata4: SATA max UDMA/133 abar m2048@0xf2528000 port 0xf2528280 irq 40
[    1.266769] ata5: SATA max UDMA/133 abar m2048@0xf2528000 port 0xf2528300 irq 40
[    1.266771] ata6: DUMMY
[    1.267170] Fixed MDIO Bus: probed
[    1.267191] tun: Universal TUN/TAP device driver, 1.6
[    1.267192] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.267244] PPP generic driver version 2.4.2
[    1.267345] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.267357] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.267361] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.267368] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.267385] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.267388] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.267430] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.267454] ehci_hcd 0000:00:1a.0: debug port 2
[    1.271328] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.271342] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf252a000
[    1.285446] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.285630] hub 1-0:1.0: USB hub found
[    1.285633] hub 1-0:1.0: 3 ports detected
[    1.285686] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.285690] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.285696] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.285711] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.285714] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.285754] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.285778] ehci_hcd 0000:00:1d.0: debug port 2
[    1.289656] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.289670] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf2529000
[    1.305402] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.305564] hub 2-0:1.0: USB hub found
[    1.305567] hub 2-0:1.0: 3 ports detected
[    1.305621] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.305632] uhci_hcd: USB Universal Host Controller Interface driver
[    1.305673] usbcore: registered new interface driver libusual
[    1.305712] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.308977] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.308982] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.309107] mousedev: PS/2 mouse device common for all mice
[    1.309262] rtc_cmos 00:07: RTC can wake from S4
[    1.309370] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.309398] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.309446] device-mapper: uevent: version 1.0.3
[    1.309509] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.309525] EISA: Probing bus 0 at eisa.0
[    1.309527] EISA: Cannot allocate resource for mainboard
[    1.309529] Cannot allocate resource for EISA slot 1
[    1.309531] Cannot allocate resource for EISA slot 2
[    1.309533] Cannot allocate resource for EISA slot 3
[    1.309535] Cannot allocate resource for EISA slot 4
[    1.309536] Cannot allocate resource for EISA slot 5
[    1.309538] Cannot allocate resource for EISA slot 6
[    1.309540] Cannot allocate resource for EISA slot 7
[    1.309542] Cannot allocate resource for EISA slot 8
[    1.309543] EISA: Detected 0 cards.
[    1.309551] cpufreq-nforce2: No nForce2 chipset.
[    1.309688] cpuidle: using governor ladder
[    1.309927] cpuidle: using governor menu
[    1.309928] EFI Variables Facility v0.08 2004-May-17
[    1.310091] TCP cubic registered
[    1.310188] NET: Registered protocol family 10
[    1.310546] NET: Registered protocol family 17
[    1.310550] Registering the dns_resolver key type
[    1.310566] Using IPI No-Shortcut mode
[    1.310691] PM: Hibernation image not present or could not be loaded.
[    1.310699] registered taskstats version 1
[    1.312777] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.317199]   Magic number: 2:301:73
[    1.317289] rtc_cmos 00:07: setting system clock to 2014-06-23 10:04:49 UTC (1403517889)
[    1.322303] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.322305] EDD information not available.
[    1.584871] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.586019] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.586032] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.586041] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.587007] ata1.00: ATA-8: HITACHI HTS723232A7A364, EC2ZB70W, max UDMA/100
[    1.587017] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.588834] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.588847] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.588856] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.589817] ata1.00: configured for UDMA/100
[    1.590079] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72323 EC2Z PQ: 0 ANSI: 5
[    1.590233] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.590239] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.590378] sd 0:0:0:0: [sda] Write Protect is off
[    1.590381] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.590513] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.596780] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.666917]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.667862] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.729277] hub 1-1:1.0: USB hub found
[    1.729418] hub 1-1:1.0: 6 ports detected
[    1.768438] Refined TSC clocksource calibration: 2491.905 MHz.
[    1.768451] Switching to clocksource tsc
[    1.840287] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.908124] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.913315] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    1.914985] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    1.914999] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.918859] ata2.00: ATAPI: HL-DT-ST DVDRAM GT50N, LT20, max UDMA/33
[    1.926069] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    1.927644] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    1.927658] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.931578] ata2.00: configured for UDMA/33
[    1.937452] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT50N     LT20 PQ: 0 ANSI: 5
[    1.944158] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.944170] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.944319] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.944413] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.972674] hub 2-1:1.0: USB hub found
[    1.972858] hub 2-1:1.0: 8 ports detected
[    2.043954] usb 1-1.6: new high-speed USB device number 3 using ehci_hcd
[    2.243508] usb 2-1.1: new full-speed USB device number 3 using ehci_hcd
[    2.263312] ata4: SATA link down (SStatus 0 SControl 300)
[    2.411126] usb 2-1.5: new full-speed USB device number 4 using ehci_hcd
[    2.582593] ata5: SATA link down (SStatus 0 SControl 300)
[    2.582849] Freeing unused kernel memory: 744k freed
[    2.583055] Write protecting the kernel text: 5852k
[    2.583094] Write protecting the kernel read-only data: 2388k
[    2.583096] NX-protecting the kernel data: 4388k
[    2.603328] udevd[123]: starting version 175
[    2.628422] usbcore: registered new interface driver usbhid
[    2.628425] usbhid: USB HID core driver
[    2.628709] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.628711] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.628747] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.628761] e1000e 0000:00:19.0: setting latency timer to 64
[    2.628868] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    2.631274] [drm] Initialized drm 1.1.0 20060810
[    2.638194] sdhci: Secure Digital Host Controller Interface driver
[    2.638197] sdhci: Copyright(c) Pierre Ossman
[    2.638891] sdhci-pci 0000:0d:00.0: SDHCI controller found [1180:e823] (rev 5)
[    2.638951] sdhci-pci 0000:0d:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.639066] sdhci-pci 0000:0d:00.0: setting latency timer to 64
[    2.639079] mmc0: no vmmc regulator found
[    2.639147] Registered led device: mmc0::
[    2.640686] mmc0: SDHCI controller on PCI [0000:0d:00.0] using DMA
[    2.645822] wmi: Mapper loaded
[    2.667828] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input2
[    2.669782] input: Logitech Unifying Device. Wireless PID:101b as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:046D:C52B.0003/input/input4
[    2.669891] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101b] on usb-0000:00:1d.0-1.1:1
[    2.672162] input: Logitech Unifying Device. Wireless PID:2008 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:046D:C52B.0003/input/input5
[    2.672289] logitech-djdevice 0003:046D:C52B.0005: input,hidraw2: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:2008] on usb-0000:00:1d.0-1.1:2
[    2.827668] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:21:cc:c6:af:de
[    2.827671] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.827721] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[    2.827765] i915 0000:00:02.0: power state changed by ACPI to D0
[    2.827770] i915 0000:00:02.0: power state changed by ACPI to D0
[    2.827775] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.827780] i915 0000:00:02.0: setting latency timer to 64
[    2.839670] mtrr: no more MTRRs available
[    2.839672] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    2.839920] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    2.839924] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.839925] [drm] Driver supports precise vblank timestamp query.
[    2.839950] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.650470] fbcon: inteldrmfb (fb0) is primary device
[    3.650507] Console: switching to colour frame buffer device 200x56
[    3.650538] fb0: inteldrmfb frame buffer device
[    3.650539] drm: registered panic notifier
[    3.685487] acpi device:00: registered as cooling_device4
[    3.685588] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    3.685645] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    3.685684] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.764516] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    4.764519] EXT4-fs (sda5): write access will be enabled during recovery
[    6.164577] EXT4-fs (sda5): recovery complete
[    6.168063] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   20.236057] Adding 8601596k swap on /dev/sda6.  Priority:-1 extents:1 across:8601596k 
[   20.705189] udevd[592]: starting version 175
[   20.733503] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.809096] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   20.987461] lp: driver loaded but no devices found
[   21.230986] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   21.231344] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.231354] mei 0000:00:16.0: setting latency timer to 64
[   21.231418] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   21.239258] tpm_tis 00:0a: 1.2 TPM (device-id 0x0, rev-id 78)
[   21.247878] Non-volatile memory driver v1.3
[   21.368916] cfg80211: Calling CRDA to update world regulatory domain
[   21.445986] Linux video capture interface: v2.00
[   21.667334] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b221)
[   21.669004] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input7
[   21.669084] usbcore: registered new interface driver uvcvideo
[   21.669086] USB Video Class driver (1.1.1)
[   21.749037] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   21.749039] Copyright(c) 2003-2011 Intel Corporation
[   21.749117] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.749191] iwlwifi 0000:03:00.0: setting latency timer to 64
[   21.749231] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   21.749232] iwlwifi 0000:03:00.0: pci_resource_base = f87b4000
[   21.749234] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[   21.749522] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   21.749633] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   21.749792] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   21.760447] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   21.760449] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   21.760451] iwlwifi 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   21.760480] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   21.890595] cfg80211: World regulatory domain updated:
[   21.890598] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.890600] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.890602] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.890603] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.890605] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.890607] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.117377] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[   22.117751] Registered led device: phy0-led
[   22.117784] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   22.159869] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   22.348920] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000
[   22.348940] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   22.398732] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   22.398789] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   22.398818] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   22.400482] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   22.411237] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   22.411239] thinkpad_acpi: http://ibm-acpi.sf.net/
[   22.411240] thinkpad_acpi: ThinkPad BIOS 83ET67WW (1.37 ), EC unknown
[   22.411242] thinkpad_acpi: Lenovo ThinkPad T420, model 4180AG8
[   22.411518] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   22.411795] thinkpad_acpi: radio switch found; radios are enabled
[   22.411806] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   22.411808] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   22.413124] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
[   22.414656] Registered led device: tpacpi::thinklight
[   22.414683] Registered led device: tpacpi::power
[   22.414700] Registered led device: tpacpi::standby
[   22.414714] Registered led device: tpacpi::thinkvantage
[   22.414718] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   22.415090] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   22.415865] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input9
[   22.843015] type=1400 audit(1403514311.068:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=786 comm="apparmor_parser"
[   22.843054] type=1400 audit(1403514311.068:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=788 comm="apparmor_parser"
[   22.843062] type=1400 audit(1403514311.068:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=902 comm="apparmor_parser"
[   22.843321] type=1400 audit(1403514311.068:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=786 comm="apparmor_parser"
[   22.843480] type=1400 audit(1403514311.068:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=902 comm="apparmor_parser"
[   22.843487] type=1400 audit(1403514311.068:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=788 comm="apparmor_parser"
[   22.843495] type=1400 audit(1403514311.068:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=786 comm="apparmor_parser"
[   22.843720] type=1400 audit(1403514311.068:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=902 comm="apparmor_parser"
[   22.843729] type=1400 audit(1403514311.068:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=788 comm="apparmor_parser"
[   22.928541] usb 1-1.4: new full-speed USB device number 4 using ehci_hcd
[   22.991509] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   22.991549] HDMI status: Codec=3 Pin=6 Presence_Detect=0 ELD_Valid=0
[   22.991589] HDMI status: Codec=3 Pin=7 Presence_Detect=0 ELD_Valid=0
[   22.991651] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   22.991714] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   22.991770] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   23.066423] Bluetooth: Core ver 2.16
[   23.066443] NET: Registered protocol family 31
[   23.066445] Bluetooth: HCI device and connection manager initialized
[   23.066447] Bluetooth: HCI socket layer initialized
[   23.066449] Bluetooth: L2CAP socket layer initialized
[   23.066453] Bluetooth: SCO socket layer initialized
[   23.086840] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   23.087089] usbcore: registered new interface driver btusb
[   23.446472] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   23.678950] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   25.797119] usb 1-1.4: USB disconnect, device number 4
[   25.883759] init: failsafe main process (1061) killed by TERM signal
[   26.608094] type=1400 audit(1403514314.844:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1137 comm="apparmor_parser"
[   26.865664] ppdev: user-space parallel port driver
[   27.043706] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.043709] Bluetooth: BNEP filters: protocol multicast
[   27.155381] Bluetooth: RFCOMM TTY layer initialized
[   27.155386] Bluetooth: RFCOMM socket layer initialized
[   27.155388] Bluetooth: RFCOMM ver 1.11
[   28.220453] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   28.276220] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   28.276412] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.276794] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.278652] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   28.278859] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   28.569078] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   28.569273] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   28.674422] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.674753] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.423590] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   29.680293] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input13
[   29.847464] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   29.847469] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   29.847617] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.428073] [drm] Changing LVDS panel from (-hsync, -vsync) to (-hsync, +vsync)
[   30.511145] symap_custom_dkms_i686: module license 'Proprietary' taints kernel.
[   30.511148] Disabling lock debugging due to kernel taint
[   31.536451] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   31.647573] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a000000, was 12000000
[   32.300219] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.330104] FIREWALL: IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:0221:ccff:fec6:afde DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=411 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=371 
[   32.580701] FIREWALL: IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:0221:ccff:fec6:afde DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=411 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=371 
[   32.580768] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=224.0.0.251 LEN=194 TOS=0x00 PREC=0x00 TTL=255 ID=12814 DF PROTO=UDP SPT=5353 DPT=5353 LEN=174 
[   32.659105] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=224.0.0.251 LEN=307 TOS=0x00 PREC=0x00 TTL=255 ID=12815 DF PROTO=UDP SPT=5353 DPT=5353 LEN=287 
[   32.780483] FIREWALL: IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:0221:ccff:fec6:afde DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=387 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=347 
[   32.780545] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=224.0.0.251 LEN=182 TOS=0x00 PREC=0x00 TTL=255 ID=12816 DF PROTO=UDP SPT=5353 DPT=5353 LEN=162 
[   32.964312] vboxdrv: Found 4 processor cores.
[   32.964457] vboxdrv: fAsync=0 offMin=0x18d offMax=0x161d
[   32.964502] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   32.964503] vboxdrv: Successfully loaded version 4.3.12 (interface 0x001a0007).
[   32.994863] FIREWALL: IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:0221:ccff:fec6:afde DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=87 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=47 
[   33.233168] vboxpci: IOMMU not found (not registered)
[   33.234596] FIREWALL: IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:0221:ccff:fec6:afde DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=240 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=200 
[   33.911938] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=224.0.0.251 LEN=182 TOS=0x00 PREC=0x00 TTL=255 ID=12817 DF PROTO=UDP SPT=5353 DPT=5353 LEN=162 
[   33.937722] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=12818 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 
[   36.291074] wlan0: authenticate with 00:3a:99:be:12:d1 (try 1)
[   36.292653] wlan0: authenticated
[   36.301022] wlan0: associate with 00:3a:99:be:12:d1 (try 1)
[   36.303855] wlan0: RX AssocResp from 00:3a:99:be:12:d1 (capab=0x421 status=0 aid=14)
[   36.303859] wlan0: associated
[   36.307077] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   36.307152] cfg80211: Calling CRDA for country: IE
[   36.310335] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   36.310338] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310340] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   36.310342] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310344] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   36.310345] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310347] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   36.310349] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310350] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   36.310352] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310353] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   36.310355] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310357] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   36.310359] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310360] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   36.310362] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310363] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   36.310365] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310367] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   36.310369] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310370] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   36.310372] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310373] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   36.310375] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310377] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   36.310379] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310380] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   36.310382] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310384] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   36.310385] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310387] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   36.310389] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310390] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   36.310392] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310394] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   36.310396] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310397] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   36.310399] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310400] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   36.310402] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310404] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   36.310405] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   36.310407] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[   36.310409] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310410] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[   36.310412] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310414] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[   36.310415] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310417] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[   36.310419] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310420] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[   36.310422] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310423] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[   36.310425] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310427] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[   36.310428] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310430] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[   36.310432] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310433] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[   36.310435] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310436] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[   36.310438] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310440] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[   36.310442] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[   36.310443] cfg80211: Disabling freq 5745 MHz
[   36.310444] cfg80211: Disabling freq 5765 MHz
[   36.310445] cfg80211: Disabling freq 5785 MHz
[   36.310446] cfg80211: Disabling freq 5805 MHz
[   36.310447] cfg80211: Disabling freq 5825 MHz
[   36.310450] cfg80211: Regulatory domain changed to country: IE
[   36.310452] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   36.310453] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.310455] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.310456] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.310458] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   37.153207] init: plymouth-stop pre-start process (2787) terminated with status 1
[   40.891538] eth0: no IPv6 routers present
[   45.109066] [drm] Changing LVDS panel from (-hsync, +vsync) to (-hsync, -vsync)
[   46.683943] wlan0: no IPv6 routers present
[   47.649398] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a0d0000, was 1a000000
[   52.762780] FIREWALL: IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:8e70:5aff:fe98:9a20 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=87 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=47 
[   53.667438] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:21:cc:c6:bc:1e:08:00 SRC=9.162.33.86 DST=255.255.255.255 LEN=382 TOS=0x08 PREC=0x40 TTL=128 ID=25792 PROTO=UDP SPT=17500 DPT=17500 LEN=362 
[   70.637612] usb 1-1.4: new full-speed USB device number 5 using ehci_hcd
[   74.125249] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=255.255.255.255 LEN=192 TOS=0x00 PREC=0x00 TTL=64 ID=35972 DF PROTO=UDP SPT=17500 DPT=17500 LEN=172 
[   93.781633] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=12824 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 
[   94.832946] FIREWALL: IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:0221:ccff:fec6:afde DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=87 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=47 
[   95.281944] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 000d0000, was 1a0d0000
[  100.633536] FIREWALL: IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:8e70:5aff:fe98:9a20 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=87 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=47 
[  120.913831] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:21:cc:6c:f0:b1:08:00 SRC=9.162.33.72 DST=255.255.255.255 LEN=140 TOS=0x08 PREC=0x40 TTL=128 ID=11242 PROTO=UDP SPT=21327 DPT=21327 LEN=120 
[  134.030936] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=255.255.255.255 LEN=192 TOS=0x00 PREC=0x00 TTL=64 ID=35979 DF PROTO=UDP SPT=17500 DPT=17500 LEN=172 
[  150.302670] FIREWALL: IN=eth0 OUT= MAC=00:21:cc:c6:af:de:0c:d9:96:94:df:40:08:00 SRC=91.189.94.25 DST=9.162.33.64 LEN=40 TOS=0x00 PREC=0x00 TTL=249 ID=42625 PROTO=TCP SPT=80 DPT=38790 WINDOW=15300 RES=0x00 ACK RST URGP=0 
[  157.607548] FIREWALL: IN=eth0 OUT= MAC= SRC=9.162.33.64 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=12826 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 
[  158.657873] FIREWALL: IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:0221:ccff:fec6:afde DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=87 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=47 
[  164.461875] FIREWALL: IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:8e70:5aff:fe98:9a20 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=87 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=47
```

And the corresponding bootchart is here:
[ATTACH]254177[/ATTACH]

I spent hours trying to understand why my boot is so slow. Any idea would be really appreciated.
Please let me know if you need any additional info.

Thank you,
Stéphane

---

### Post by oldfred on 2014-06-23
I do see in my system that the mounting of the file systems is slow. I ran full fsck and it made no difference.

But are you running 32 bit? You say i686?
       uname -a
i386 or i686 = 32-bit
x86_64 = 64-bit

    
While PAE does allow some use of more RAM, each app cannot use more than the 3 or4 GB available and it has to swap in and out the other parts of RAM above the 3.2GB limit.
       Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by handsaway on 2014-06-23
Hi oldfred, 

I'm running 32-bit, PAE enabled:
```
stephane@stephane-ThinkPad-T420:~$ uname -a
Linux stephane-ThinkPad-T420 3.2.0-64-generic-pae #97-Ubuntu SMP Wed Jun 4 22:22:15 UTC 2014 i686 i686 i386 GNU/Linux
```
(I just mentioned "i686" because that is what Ubuntu tweak overview says for "platform").
Do you think that 32-bit PAE is the cause of the slow boot? I remember choosing 32-bit because there was a trade-off with something else involved, but unfortunately I don't remember what.
I'm not eager to reinstall everything, but I'll consider it. Do you have any other suggestions on the slow boot?

PS: I forgot to mention my install is dual boot Win7 and Ubuntu, but I don't think it really matters? The slow boot is during the splash screen.

Thank you for your help!

---

### Post by hockeybum27 on 2014-07-11
This started happening to me as well, after the system updates this past week.  My system info:
Linux MyUbuLaptop 3.2.0-65-generic #99-Ubuntu SMP Fri Jul 4 21:03:29 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

The relevant portion of the dmesg output (as I see it):
[    9.404145] userif-2: sent link up event.
[   10.265979] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a000000, was 12000000
[   18.254825] vmnet8: no IPv6 routers present
[   18.454748] vmnet1: no IPv6 routers present
[   40.773301] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a0d0000, was 1a000000
[   41.432224] [drm] Changing LVDS panel from (-hsync, +vsync) to (-hsync, -vsync)
[ 3728.089125] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 000d0000, was 1a0d0000
[ 5644.242530] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 5648.917782] device eth0 entered promiscuous mode

---

### Post by oldfred on 2014-07-11
handsaway may also have been related to firewall which I know nothing about.

@hockeybum27
Your seems to have issues with whatever gen6_sanitize_pm is, but I know nothing about Virtual installs and what issues those may have.

---

### Post by hockeybum27 on 2014-07-11
Oldfred,
Many thanks for the prompt response!  What do you mean by 'virtual install'?  I do have a dual boot (Grub) - is that what you mean?  That would make sense, since the update that occurred just prior to this starting is - you guessed it - a Grub update!
FMI - newbie question but what is the best way to see a history of updates?
Thanks again!

---

### Post by oldfred on 2014-07-11
@hockeybum27
Generally best to start your own thread unless issue is virtually identical, not generally similar.

You show this message, so I assumed you installed in VirtualBox? I have not used VirtualBox so do not know anything about it.
warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)

There are a lot of log files in /var/log, I think this is the log of installation that you see when you open the details on updates. I usually try to see details and if any error is posted or what is updating to have some idea if issue later.
/var/log/dpkg.log

---

### Post by hockeybum27 on 2014-07-11
Oldfred,

Re: starting a new thread, I understand, and will do; you're right it's just 'generally similar' - FYI this is not a virtual box install, but I have VB installed, so probably a service is starting.   Thanks for your time and patience.

---

