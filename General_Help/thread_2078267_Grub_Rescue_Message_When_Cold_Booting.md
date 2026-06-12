---
title: "Grub Rescue Message When Cold Booting"
date: 2012-10-30
forum: General Help
---

### Post by coljohnhannibalsmith on 2012-10-30
Hello,

I have a dual boot system with Windows 7 & Ubuntu 12.04.  I also have Grub Customizer installed, so that I have a splash screen on bootup.

About 50% of the time when cold booting, I get a Grub Rescue message.  Usually, I only have to reboot again to clear the message and enter the dual boot menu; however, this indicates to me that there may be more trouble ahead, like the system failing to boot at all.

Any help appreciated, Hannibal

---

### Post by oldfred on 2012-10-30
Intermittent issues are difficult to resolve.

Do you have any external devices that may be borderline in powering up?

Have you looked in log files to see if there are issues. Even when it works it may be loading, failing and reloading a driver and only sometimes not ever working. Logs can be long, but look for outright errors, long times between tasks, or repeated tries at loading.

You can use log file viewer. Files are in /var/log, I usually look at dmesg first.

---

### Post by coljohnhannibalsmith on 2012-10-30
oldfred,

Thank you for your reply.  I appologize that I don't know what to look for, so I've included the contents of dmsg below:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-32-generic (buildd@batsu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 (Ubuntu 3.2.0-32.51-generic 3.2.30)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic root=UUID=fa270bbd-8cc6-4454-baad-dcb320870a7d ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
[    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
[    0.000000]  BIOS-e820: 0000000040005000 - 00000000aaabf000 (usable)
[    0.000000]  BIOS-e820: 00000000aaabf000 - 00000000aaebf000 (reserved)
[    0.000000]  BIOS-e820: 00000000aaebf000 - 00000000aafbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000aafbf000 - 00000000aafff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000aafff000 - 00000000ab000000 (usable)
[    0.000000]  BIOS-e820: 00000000ab000000 - 00000000afa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000024f600000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: Dell Inc. Inspiron 5520/04G65K, BIOS A07 05/17/2012
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x24f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0AB000000 mask FFF000000 uncachable
[    0.000000]   3 base 0AC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0B0000000 mask FF0000000 uncachable
[    0.000000]   5 base 0FFA00000 mask FFFE00000 write-protect
[    0.000000]   6 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   7 base 100000000 mask F00000000 write-back
[    0.000000]   8 base 200000000 mask FC0000000 write-back
[    0.000000]   9 base 240000000 mask FF0000000 write-back
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xab000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fe1b0] fe1b0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000ab000000
[    0.000000]  0000000000 - 00ab000000 page 2M
[    0.000000] kernel direct mapping tables up to ab000000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000024f600000
[    0.000000]  0100000000 - 024f600000 page 2M
[    0.000000] kernel direct mapping tables up to 24f600000 @ aaab4000-aaabf000
[    0.000000] RAMDISK: 36478000 - 37234000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000aaffe210 0008C (v01 DELL    CL09    00000001      01000013)
[    0.000000] ACPI: FACP 00000000aaffa000 0010C (v05 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 268 to 244 (20110623/tbfadt-288)
[    0.000000] ACPI: DSDT 00000000aafed000 09033 (v01 DELL    CL09    00000000 ASL  00040000)
[    0.000000] ACPI: FACS 00000000aafb9000 00040
[    0.000000] ACPI: SLIC 00000000aaffd000 00176 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: UEFI 00000000aaffc000 00236 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASF! 00000000aaffb000 000A5 (v32 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: HPET 00000000aaff9000 00038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: APIC 00000000aaff8000 0008C (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MCFG 00000000aaff7000 0003C (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 00000000aafec000 006FE (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000aafea000 00028 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASPT 00000000aafe5000 00034 (v07 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: FPDT 00000000aafe3000 00044 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 00000000aafe2000 00860 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000aafe1000 00A92 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000024f600000
[    0.000000] Initmem setup node 0 0000000000000000-000000024f600000
[    0.000000]   NODE_DATA [000000024f5fb000 - 000000024f5fffff]
[    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246c00000-ffff88024ebfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0024f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040004
[    0.000000]     0: 0x00040005 -> 0x000aaabf
[    0.000000]     0: 0x000aafff -> 0x000ab000
[    0.000000]     0: 0x00100000 -> 0x0024f600
[    0.000000] On node 0 totalpages: 2072140
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 678143 pages, LIFO batch:31
[    0.000000]   Normal zone: 21464 pages used for memmap
[    0.000000]   Normal zone: 1352232 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 00000000aaabf000 - 00000000aaebf000
[    0.000000] PM: Registered nosave memory: 00000000aaebf000 - 00000000aafbf000
[    0.000000] PM: Registered nosave memory: 00000000aafbf000 - 00000000aafff000
[    0.000000] PM: Registered nosave memory: 00000000ab000000 - 00000000afa00000
[    0.000000] PM: Registered nosave memory: 00000000afa00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb80000
[    0.000000] PM: Registered nosave memory: 00000000ffb80000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at afa00000 (gap: afa00000:30600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88024f200000 s83136 r8192 d23360 u262144
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2034287
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic root=UUID=fa270bbd-8cc6-4454-baad-dcb320870a7d ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8060620k/9689088k available (6560k kernel code, 1400528k absent, 227940k reserved, 6639k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2095.231 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4190.46 BogoMIPS (lpj=8380924)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000030] Security Framework initialized
[    0.000043] AppArmor: AppArmor initialized
[    0.000044] Yama: becoming mindful.
[    0.000620] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002901] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003915] Mount-cache hash table entries: 256
[    0.004019] Initializing cgroup subsys cpuacct
[    0.004023] Initializing cgroup subsys memory
[    0.004030] Initializing cgroup subsys devices
[    0.004032] Initializing cgroup subsys freezer
[    0.004034] Initializing cgroup subsys blkio
[    0.004039] Initializing cgroup subsys perf_event
[    0.004067] CPU: Physical Processor ID: 0
[    0.004068] CPU: Processor Core ID: 0
[    0.004073] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.004075] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.004510] mce: CPU supports 9 MCE banks
[    0.004525] CPU0: Thermal monitoring enabled (TM1)
[    0.004535] using mwait in idle threads.
[    0.006774] ACPI: Core revision 20110623
[    0.025060] ftrace: allocating 27014 entries in 106 pages
[    0.034795] x2apic not enabled, IRQ remapping init failed
[    0.035218] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074844] CPU0: Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz stepping 09
[    0.180096] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.180102] ... version:                3
[    0.180103] ... bit width:              48
[    0.180104] ... generic registers:      4
[    0.180106] ... value mask:             0000ffffffffffff
[    0.180107] ... max period:             000000007fffffff
[    0.180108] ... fixed-purpose events:   3
[    0.180109] ... event mask:             000000070000000f
[    0.180251] NMI watchdog enabled, takes one hw-pmu counter.
[    0.180323] Booting Node   0, Processors  #1
[    0.180326] smpboot cpu 1: start_ip = 98000
[    0.288504] NMI watchdog enabled, takes one hw-pmu counter.
[    0.288589]  #2
[    0.288591] smpboot cpu 2: start_ip = 98000
[    0.396328] NMI watchdog enabled, takes one hw-pmu counter.
[    0.396402]  #3
[    0.396403] smpboot cpu 3: start_ip = 98000
[    0.504140] NMI watchdog enabled, takes one hw-pmu counter.
[    0.504213]  #4
[    0.504214] smpboot cpu 4: start_ip = 98000
[    0.611951] NMI watchdog enabled, takes one hw-pmu counter.
[    0.612034]  #5
[    0.612036] smpboot cpu 5: start_ip = 98000
[    0.719771] NMI watchdog enabled, takes one hw-pmu counter.
[    0.719847]  #6
[    0.719848] smpboot cpu 6: start_ip = 98000
[    0.827687] NMI watchdog enabled, takes one hw-pmu counter.
[    0.827759]  #7 Ok.
[    0.827761] smpboot cpu 7: start_ip = 98000
[    0.935497] NMI watchdog enabled, takes one hw-pmu counter.
[    0.935526] Brought up 8 CPUs
[    0.935528] Total of 8 processors activated (33522.53 BogoMIPS).
[    0.944130] devtmpfs: initialized
[    0.944976] EVM: security.selinux
[    0.944977] EVM: security.SMACK64
[    0.944978] EVM: security.capability
[    0.945000] PM: Registering ACPI NVS region at aaebf000 (1048576 bytes)
[    0.945777] print_constraints: dummy: 
[    0.945807] RTC time: 11:40:37, date: 10/30/12
[    0.945838] NET: Registered protocol family 16
[    0.945931] Trying to unpack rootfs image as initramfs...
[    0.945934] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.945936] ACPI: bus type pci registered
[    0.946005] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.946009] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.999615] PCI: Using configuration type 1 for base access
[    0.999623] dmi type 0xB1 record - unknown flag
[    1.000525] bio: create slab <bio-0> at 0
[    1.000600] ACPI: Added _OSI(Module Device)
[    1.000602] ACPI: Added _OSI(Processor Device)
[    1.000604] ACPI: Added _OSI(3.0 _SCP Extensions)
[    1.000607] ACPI: Added _OSI(Processor Aggregator Device)
[    1.002051] ACPI: EC: Look up EC in DSDT
[    1.003496] ACPI: Executed 1 blocks of module-level executable AML code
[    1.027284] ACPI: SSDT 00000000aadf9018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    1.027658] ACPI: Dynamic OEM Table Load:
[    1.027661] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    1.062975] ACPI: SSDT 00000000aadfaa98 00303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    1.063373] ACPI: Dynamic OEM Table Load:
[    1.063376] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    1.078807] ACPI: SSDT 00000000aadf8d98 00119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    1.079172] ACPI: Dynamic OEM Table Load:
[    1.079174] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    1.115910] ACPI: Interpreter enabled
[    1.115914] ACPI: (supports S0 S3 S4 S5)
[    1.115938] ACPI: Using IOAPIC for interrupt routing
[    1.200864] Freeing initrd memory: 14064k freed
[    1.247884] ACPI: Power Resource [FN00] (off)
[    1.247958] ACPI: Power Resource [FN01] (off)
[    1.248028] ACPI: Power Resource [FN02] (off)
[    1.248099] ACPI: Power Resource [FN03] (off)
[    1.248170] ACPI: Power Resource [FN04] (off)
[    1.248477] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.248643] ACPI: No dock devices found.
[    1.248645] HEST: Table not found.
[    1.248648] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.248965] \_SB_.PCI0:_OSC invalid UUID
[    1.248966] _OSC request data:1 8 1f 
[    1.248970] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.249483] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.249485] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.249488] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.249491] pci_root PNP0A08:00: host bridge window [mem 0xafa00000-0xfeafffff]
[    1.249502] pci 0000:00:00.0: [8086:0154] type 0 class 0x000600
[    1.249541] pci 0000:00:02.0: [8086:0166] type 0 class 0x000300
[    1.249553] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
[    1.249559] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.249564] pci 0000:00:02.0: reg 20: [io  0x3000-0x303f]
[    1.249620] pci 0000:00:14.0: [8086:1e31] type 0 class 0x000c03
[    1.249644] pci 0000:00:14.0: reg 10: [mem 0xc0600000-0xc060ffff 64bit]
[    1.249719] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    1.249725] pci 0000:00:14.0: PME# disabled
[    1.249748] pci 0000:00:16.0: [8086:1e3a] type 0 class 0x000780
[    1.249774] pci 0000:00:16.0: reg 10: [mem 0xc0614000-0xc061400f 64bit]
[    1.249854] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.249859] pci 0000:00:16.0: PME# disabled
[    1.249894] pci 0000:00:1a.0: [8086:1e2d] type 0 class 0x000c03
[    1.250218] pci 0000:00:1a.0: reg 10: [mem 0xc0619000-0xc06193ff]
[    1.252043] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.252048] pci 0000:00:1a.0: PME# disabled
[    1.252077] pci 0000:00:1b.0: [8086:1e20] type 0 class 0x000403
[    1.252093] pci 0000:00:1b.0: reg 10: [mem 0xc0610000-0xc0613fff 64bit]
[    1.252166] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.252170] pci 0000:00:1b.0: PME# disabled
[    1.252193] pci 0000:00:1c.0: [8086:1e10] type 1 class 0x000604
[    1.252277] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.252281] pci 0000:00:1c.0: PME# disabled
[    1.252306] pci 0000:00:1c.1: [8086:1e12] type 1 class 0x000604
[    1.252389] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.252394] pci 0000:00:1c.1: PME# disabled
[    1.252429] pci 0000:00:1d.0: [8086:1e26] type 0 class 0x000c03
[    1.252740] pci 0000:00:1d.0: reg 10: [mem 0xc0618000-0xc06183ff]
[    1.254571] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.254575] pci 0000:00:1d.0: PME# disabled
[    1.254601] pci 0000:00:1f.0: [8086:1e57] type 0 class 0x000601
[    1.254730] pci 0000:00:1f.2: [8086:1e03] type 0 class 0x000106
[    1.254750] pci 0000:00:1f.2: reg 10: [io  0x3088-0x308f]
[    1.254759] pci 0000:00:1f.2: reg 14: [io  0x3094-0x3097]
[    1.254768] pci 0000:00:1f.2: reg 18: [io  0x3080-0x3087]
[    1.254777] pci 0000:00:1f.2: reg 1c: [io  0x3090-0x3093]
[    1.254786] pci 0000:00:1f.2: reg 20: [io  0x3060-0x307f]
[    1.254795] pci 0000:00:1f.2: reg 24: [mem 0xc0617000-0xc06177ff]
[    1.254843] pci 0000:00:1f.2: PME# supported from D3hot
[    1.254848] pci 0000:00:1f.2: PME# disabled
[    1.254867] pci 0000:00:1f.3: [8086:1e22] type 0 class 0x000c05
[    1.254883] pci 0000:00:1f.3: reg 10: [mem 0xc0615000-0xc06150ff 64bit]
[    1.254906] pci 0000:00:1f.3: reg 20: [io  0x3040-0x305f]
[    1.255068] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
[    1.255138] pci 0000:01:00.0: reg 10: [io  0x2000-0x20ff]
[    1.255262] pci 0000:01:00.0: reg 18: [mem 0xc0404000-0xc0404fff 64bit pref]
[    1.255338] pci 0000:01:00.0: reg 20: [mem 0xc0400000-0xc0403fff 64bit pref]
[    1.255673] pci 0000:01:00.0: supports D1 D2
[    1.255675] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.255690] pci 0000:01:00.0: PME# disabled
[    1.262498] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.262502] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.262511] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
[    1.262622] pci 0000:02:00.0: [8086:0887] type 0 class 0x000280
[    1.262669] pci 0000:02:00.0: reg 10: [mem 0xc0500000-0xc0501fff 64bit]
[    1.262902] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.262911] pci 0000:02:00.0: PME# disabled
[    1.270496] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.270503] pci 0000:00:1c.1:   bridge window [mem 0xc0500000-0xc05fffff]
[    1.270524] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.270638] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.270666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.270752] \_SB_.PCI0:_OSC invalid UUID
[    1.270753] _OSC request data:1 1f 1f 
[    1.270757]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.270797] \_SB_.PCI0:_OSC invalid UUID
[    1.270798] _OSC request data:1 0 1d 
[    1.270802]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.270803] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.272773] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.272818] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    1.272859] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.272902] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.272944] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.272985] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.273030] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.273072] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    1.273167] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.273173] vgaarb: loaded
[    1.273174] vgaarb: bridge control possible 0000:00:02.0
[    1.273260] i2c-core: driver [aat2870] using legacy suspend method
[    1.273261] i2c-core: driver [aat2870] using legacy resume method
[    1.273317] SCSI subsystem initialized
[    1.273356] libata version 3.00 loaded.
[    1.273394] usbcore: registered new interface driver usbfs
[    1.273403] usbcore: registered new interface driver hub
[    1.273420] usbcore: registered new device driver usb
[    1.273494] PCI: Using ACPI for IRQ routing
[    1.280337] PCI: pci_cache_line_size set to 64 bytes
[    1.280450] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    1.280452] reserve RAM buffer: 0000000040004000 - 0000000043ffffff 
[    1.280454] reserve RAM buffer: 00000000aaabf000 - 00000000abffffff 
[    1.280456] reserve RAM buffer: 00000000ab000000 - 00000000abffffff 
[    1.280458] reserve RAM buffer: 000000024f600000 - 000000024fffffff 
[    1.280541] NetLabel: Initializing
[    1.280543] NetLabel:  domain hash size = 128
[    1.280544] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.280553] NetLabel:  unlabeled traffic allowed by default
[    1.280593] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.280598] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.282612] Switching to clocksource hpet
[    1.287920] AppArmor: AppArmor Filesystem Enabled
[    1.287936] pnp: PnP ACPI init
[    1.287948] ACPI: bus type pnp registered
[    1.288225] pnp 00:00: [bus 00-fe]
[    1.288228] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.288230] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.288232] pnp 00:00: [io  0x0d00-0xffff window]
[    1.288234] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.288236] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.288238] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.288240] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.288241] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.288243] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.288245] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.288248] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.288250] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.288252] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.288254] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.288256] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.288257] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.288259] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.288261] pnp 00:00: [mem 0xafa00000-0xfeafffff window]
[    1.288263] pnp 00:00: [mem 0x00010000-0x0001ffff window]
[    1.288313] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.288326] pnp 00:01: [io  0x0000-0x001f]
[    1.288327] pnp 00:01: [io  0x0081-0x0091]
[    1.288329] pnp 00:01: [io  0x0093-0x009f]
[    1.288330] pnp 00:01: [io  0x00c0-0x00df]
[    1.288333] pnp 00:01: [dma 4]
[    1.288353] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.288361] pnp 00:02: [mem 0xff010000-0xffffffff]
[    1.288379] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.288444] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.288465] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.288473] pnp 00:04: [io  0x00f0]
[    1.288482] pnp 00:04: [irq 13]
[    1.288500] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.288510] pnp 00:05: [io  0x002e-0x002f]
[    1.288511] pnp 00:05: [io  0x004e-0x004f]
[    1.288513] pnp 00:05: [io  0x0061]
[    1.288514] pnp 00:05: [io  0x0063]
[    1.288516] pnp 00:05: [io  0x0065]
[    1.288517] pnp 00:05: [io  0x0067]
[    1.288519] pnp 00:05: [io  0x0070]
[    1.288520] pnp 00:05: [io  0x0080]
[    1.288521] pnp 00:05: [io  0x0092]
[    1.288523] pnp 00:05: [io  0x00b2-0x00b3]
[    1.288524] pnp 00:05: [io  0x0680-0x069f]
[    1.288526] pnp 00:05: [io  0x1000-0x100f]
[    1.288528] pnp 00:05: [io  0xffff]
[    1.288529] pnp 00:05: [io  0xffff]
[    1.288531] pnp 00:05: [io  0x0400-0x0453]
[    1.288532] pnp 00:05: [io  0x0458-0x047f]
[    1.288534] pnp 00:05: [io  0x0500-0x057f]
[    1.288535] pnp 00:05: [io  0x164e-0x164f]
[    1.288537] pnp 00:05: [io  0xfd60-0xfd63]
[    1.288572] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.288574] system 00:05: [io  0x1000-0x100f] has been reserved
[    1.288576] system 00:05: [io  0xffff] has been reserved
[    1.288579] system 00:05: [io  0xffff] has been reserved
[    1.288581] system 00:05: [io  0x0400-0x0453] has been reserved
[    1.288583] system 00:05: [io  0x0458-0x047f] has been reserved
[    1.288586] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.288588] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.288591] system 00:05: [io  0xfd60-0xfd63] has been reserved
[    1.288593] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.288601] pnp 00:06: [io  0x0070-0x0077]
[    1.288606] pnp 00:06: [irq 8]
[    1.288626] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.288649] pnp 00:07: [io  0x0454-0x0457]
[    1.288677] system 00:07: [io  0x0454-0x0457] has been reserved
[    1.288680] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.288694] pnp 00:08: [io  0x0060]
[    1.288695] pnp 00:08: [io  0x0064]
[    1.288702] pnp 00:08: [irq 1]
[    1.288723] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.288738] pnp 00:09: [irq 12]
[    1.288759] pnp 00:09: Plug and Play ACPI device, IDs DLL0569 PNP0f13 (active)
[    1.346583] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.346585] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
[    1.346587] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    1.346589] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    1.346590] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    1.346592] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.346594] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
[    1.346595] pnp 00:0a: [mem 0xff000000-0xff000fff]
[    1.346597] pnp 00:0a: [mem 0xff010000-0xffffffff]
[    1.346599] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.346601] pnp 00:0a: [mem 0xafa00000-0xafa00fff]
[    1.346635] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.346638] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.346640] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.346642] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.346645] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    1.346647] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.346649] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.346651] system 00:0a: [mem 0xff000000-0xff000fff] has been reserved
[    1.346654] system 00:0a: [mem 0xff010000-0xffffffff] could not be reserved
[    1.346656] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.346658] system 00:0a: [mem 0xafa00000-0xafa00fff] has been reserved
[    1.346661] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.346891] pnp 00:0b: [mem 0x20000000-0x201fffff]
[    1.346893] pnp 00:0b: [mem 0x40004000-0x40004fff]
[    1.346938] system 00:0b: [mem 0x20000000-0x201fffff] has been reserved
[    1.346941] system 00:0b: [mem 0x40004000-0x40004fff] has been reserved
[    1.346943] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.346968] pnp: PnP ACPI: found 12 devices
[    1.346969] ACPI: ACPI bus type pnp unregistered
[    1.353310] PCI: max bus depth: 1 pci_try_num: 2
[    1.353335] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.353339] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.353347] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
[    1.353355] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    1.353360] pci 0000:00:1c.1:   bridge window [mem 0xc0500000-0xc05fffff]
[    1.353382] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.353387] pci 0000:00:1c.0: setting latency timer to 64
[    1.353400] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.353405] pci 0000:00:1c.1: setting latency timer to 64
[    1.353410] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.353412] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.353414] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.353416] pci_bus 0000:00: resource 7 [mem 0xafa00000-0xfeafffff]
[    1.353418] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    1.353420] pci_bus 0000:01: resource 2 [mem 0xc0400000-0xc04fffff 64bit pref]
[    1.353423] pci_bus 0000:02: resource 1 [mem 0xc0500000-0xc05fffff]
[    1.353450] NET: Registered protocol family 2
[    1.353613] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.354310] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.355444] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.355565] TCP: Hash tables configured (established 524288 bind 65536)
[    1.355567] TCP reno registered
[    1.355581] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.355612] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.355694] NET: Registered protocol family 1
[    1.355706] pci 0000:00:02.0: Boot video device
[    1.355723] pci 0000:00:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.356963] pci 0000:00:14.0: PCI INT A disabled
[    1.356976] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.370473] pci 0000:00:1a.0: PCI INT A disabled
[    1.370494] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.386443] pci 0000:00:1d.0: PCI INT A disabled
[    1.386485] PCI: CLS 64 bytes, default 64
[    1.386487] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.386489] Placing 64MB software IO TLB between ffff8800a6ab4000 - ffff8800aaab4000
[    1.386491] software IO TLB at phys 0xa6ab4000 - 0xaaab4000
[    1.386507] Simple Boot Flag at 0x44 set to 0x1
[    1.387089] audit: initializing netlink socket (disabled)
[    1.387096] type=2000 audit(1351597237.152:1): initialized
[    1.411969] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.413806] VFS: Disk quotas dquot_6.5.2
[    1.413848] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.414253] fuse init (API version 7.17)
[    1.414328] msgmni has been set to 15770
[    1.414656] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.414682] io scheduler noop registered
[    1.414684] io scheduler deadline registered
[    1.414709] io scheduler cfq registered (default)
[    1.414879] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.414897] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.414940] intel_idle: MWAIT substates: 0x21120
[    1.414941] intel_idle: does not run on family 6 model 58
[    1.414981] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.415021] ACPI: AC Adapter [ACAD] (on-line)
[    1.415112] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0C:00/input/input0
[    1.415116] ACPI: Power Button [PWRB]
[    1.415158] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.415180] ACPI: Lid Switch [LID0]
[    1.415215] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.415218] ACPI: Power Button [PWRF]
[    1.415272] ACPI: Fan [FAN0] (off)
[    1.415299] ACPI: Fan [FAN1] (off)
[    1.415324] ACPI: Fan [FAN2] (off)
[    1.415350] ACPI: Fan [FAN3] (off)
[    1.415375] ACPI: Fan [FAN4] (off)
[    1.478575] Monitor-Mwait will be used to enter C-1 state
[    1.478602] Monitor-Mwait will be used to enter C-2 state
[    1.478613] ACPI: acpi_idle registered with cpuidle
[    1.574395] thermal LNXTHERM:00: registered as thermal_zone0
[    1.574398] ACPI: Thermal Zone [TZ00] (28 C)
[    1.574566] thermal LNXTHERM:01: registered as thermal_zone1
[    1.574568] ACPI: Thermal Zone [TZ01] (30 C)
[    1.574586] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.574593] ACPI: Battery Slot [BAT1] (battery present)
[    1.574618] ERST: Table is not found!
[    1.574619] GHES: HEST is not enabled!
[    1.574682] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.602580] Linux agpgart interface v0.103
[    1.602647] agpgart-intel 0000:00:00.0: Intel Ivybridge Chipset
[    1.602781] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.604292] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.604401] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[    1.605576] brd: module loaded
[    1.606196] loop: module loaded
[    1.606301] ahci 0000:00:1f.2: version 3.0
[    1.606322] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.606367] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.622102] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.622106] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.622112] ahci 0000:00:1f.2: setting latency timer to 64
[    1.630462] scsi0 : ahci
[    1.630530] scsi1 : ahci
[    1.630592] scsi2 : ahci
[    1.630646] scsi3 : ahci
[    1.630699] scsi4 : ahci
[    1.630754] scsi5 : ahci
[    1.630830] ata1: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617100 irq 40
[    1.630832] ata2: DUMMY
[    1.630835] ata3: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617200 irq 40
[    1.630837] ata4: DUMMY
[    1.630838] ata5: DUMMY
[    1.630839] ata6: DUMMY
[    1.631130] Fixed MDIO Bus: probed
[    1.631146] tun: Universal TUN/TAP device driver, 1.6
[    1.631147] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.631191] PPP generic driver version 2.4.2
[    1.631275] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.631289] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.631304] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.631308] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.631343] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.631369] ehci_hcd 0000:00:1a.0: debug port 2
[    1.635246] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.635260] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc0619000
[    1.650045] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.650150] hub 1-0:1.0: USB hub found
[    1.650154] hub 1-0:1.0: 2 ports detected
[    1.650205] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.650219] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.650222] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.650262] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.650283] ehci_hcd 0000:00:1d.0: debug port 2
[    1.654169] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.654182] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xc0618000
[    1.670002] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.670104] hub 2-0:1.0: USB hub found
[    1.670107] hub 2-0:1.0: 2 ports detected
[    1.670154] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.670164] uhci_hcd: USB Universal Host Controller Interface driver
[    1.670190] xhci_hcd 0000:00:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.670217] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.670220] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.670258] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.670345] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.670357] xhci_hcd 0000:00:14.0: irq 21, io mem 0xc0600000
[    1.670405] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    1.670505] xHCI xhci_add_endpoint called for root hub
[    1.670507] xHCI xhci_check_bandwidth called for root hub
[    1.670532] hub 3-0:1.0: USB hub found
[    1.670539] hub 3-0:1.0: 4 ports detected
[    1.670587] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.670623] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.670689] xHCI xhci_add_endpoint called for root hub
[    1.670691] xHCI xhci_check_bandwidth called for root hub
[    1.670709] hub 4-0:1.0: USB hub found
[    1.670716] hub 4-0:1.0: 4 ports detected
[    1.710003] usbcore: registered new interface driver libusual
[    1.710035] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.732131] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.732137] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.732246] mousedev: PS/2 mouse device common for all mice
[    1.734573] rtc_cmos 00:06: RTC can wake from S4
[    1.734675] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.734703] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.734766] device-mapper: uevent: version 1.0.3
[    1.734822] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.734946] cpuidle: using governor ladder
[    1.735131] cpuidle: using governor menu
[    1.735133] EFI Variables Facility v0.08 2004-May-17
[    1.735298] TCP cubic registered
[    1.735379] NET: Registered protocol family 10
[    1.735726] NET: Registered protocol family 17
[    1.735730] Registering the dns_resolver key type
[    1.735854] PM: Hibernation image not present or could not be loaded.
[    1.735863] registered taskstats version 1
[    1.742918]   Magic number: 0:578:682
[    1.743024] rtc_cmos 00:06: setting system clock to 2012-10-30 11:40:38 UTC (1351597238)
[    1.744193] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.744195] EDD information not available.
[    1.755647] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.773959] ACPI: Battery Slot [BAT1] (battery present)
[    1.949632] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.949669] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.952851] ata3.00: ATAPI: PLDS DVD+/-RW DS-8A8SH, KD11, max UDMA/100
[    1.953900] ata3.00: configured for UDMA/100
[    1.956033] ata1.00: ATA-8: ST1000LM024 HN-M101MBB, 2AR20002, max UDMA/133
[    1.956039] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.961623] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.962464] ata1.00: configured for UDMA/133
[    1.962675] scsi 0:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 2AR2 PQ: 0 ANSI: 5
[    1.962789] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.962800] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.962839] sd 0:0:0:0: [sda] Write Protect is off
[    1.962841] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.962852] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.967309] scsi 2:0:0:0: CD-ROM            PLDS     DVD+-RW DS-8A8SH KD11 PQ: 0 ANSI: 5
[    1.977046] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.977052] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.977235] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.977341] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.032092]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.033011] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.034155] Freeing unused kernel memory: 924k freed
[    2.034234] Write protecting the kernel read-only data: 12288k
[    2.037850] Freeing unused kernel memory: 1612k freed
[    2.040630] Freeing unused kernel memory: 1200k freed
[    2.053324] udevd[140]: starting version 175
[    2.060979] xor: automatically using best checksumming function: generic_sse
[    2.077244] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.077265] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.077300] r8169 0000:01:00.0: setting latency timer to 64
[    2.077371] r8169 0000:01:00.0: irq 42 for MSI/MSI-X
[    2.077393]    generic_sse: 11731.000 MB/sec
[    2.077396] xor: using function: generic_sse (11731.000 MB/sec)
[    2.077790] r8169 0000:01:00.0: eth0: RTL8105e at 0xffffc90000c3c000, d4:be:d9:44:03:ce, XID 00c00000 IRQ 42
[    2.077851] device-mapper: dm-raid45: initialized v0.2594b
[    2.094052] hub 1-1:1.0: USB hub found
[    2.094127] hub 1-1:1.0: 6 ports detected
[    2.205267] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.337687] hub 2-1:1.0: USB hub found
[    2.337764] hub 2-1:1.0: 8 ports detected
[    2.384953] Refined TSC clocksource calibration: 2095.240 MHz.
[    2.384960] Switching to clocksource tsc
[    2.409066] usb 1-1.3: new high-speed USB device number 3 using ehci_hcd
[    2.572849] usb 1-1.5: new high-speed USB device number 4 using ehci_hcd
[    2.824461] usb 2-1.5: new full-speed USB device number 3 using ehci_hcd
[    3.906971] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    9.357575] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.846221] udevd[411]: starting version 175
[   10.229200] Adding 8287228k swap on /dev/sda6.  Priority:-1 extents:1 across:8287228k 
[   11.809587] lp: driver loaded but no devices found
[   12.190505] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   12.246502] wmi: Mapper loaded
[   13.045801] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.085709] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   13.085940] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.085947] mei 0000:00:16.0: setting latency timer to 64
[   13.085998] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   13.667307] cfg80211: Calling CRDA to update world regulatory domain
[   13.730334] input: Dell WMI hotkeys as /devices/virtual/input/input4
[   13.754634] device-mapper: multipath: version 1.3.0 loaded
[   13.848286] [drm] Initialized drm 1.1.0 20060810
[   14.051637] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   14.080321] psmouse serio1: elantech: Synaptics capabilities query result 0x79, 0x17, 0x0c.
[   14.117699] Bluetooth: Core ver 2.16
[   14.117712] NET: Registered protocol family 31
[   14.117714] Bluetooth: HCI device and connection manager initialized
[   14.117716] Bluetooth: HCI socket layer initialized
[   14.117718] Bluetooth: L2CAP socket layer initialized
[   14.117723] Bluetooth: SCO socket layer initialized
[   14.243362] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input5
[   14.730937] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.730941] i915 0000:00:02.0: setting latency timer to 64
[   14.778292] mtrr: type mismatch for b0000000,10000000 old: write-back new: write-combining
[   14.778294] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   14.778521] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   14.778524] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.778525] [drm] Driver supports precise vblank timestamp query.
[   14.778886] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.999497] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.999499] Copyright(c) 2003-2011 Intel Corporation
[   14.999551] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.999580] iwlwifi 0000:02:00.0: setting latency timer to 64
[   14.999596] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   14.999597] iwlwifi 0000:02:00.0: pci_resource_base = ffffc90000c7c000
[   14.999599] iwlwifi 0000:02:00.0: HW Revision ID = 0xC4
[   14.999727] iwlwifi 0000:02:00.0: irq 45 for MSI/MSI-X
[   14.999782] iwlwifi 0000:02:00.0: Detected 2000 Series 2x2 BGN/BT, REV=0xC8
[   14.999887] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   15.018372] iwlwifi 0000:02:00.0: device EEPROM VER=0x81c, CALIB=0x6
[   15.018373] iwlwifi 0000:02:00.0: Device SKU: 0X150
[   15.018374] iwlwifi 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   15.018395] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   15.037170] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   15.037403] usbcore: registered new interface driver btusb
[   15.353352] fbcon: inteldrmfb (fb0) is primary device
[   15.353423] Console: switching to colour frame buffer device 170x48
[   15.353439] fb0: inteldrmfb frame buffer device
[   15.353440] drm: registered panic notifier
[   15.382508] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[   15.382605] acpi device:31: registered as cooling_device13
[   15.382746] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   15.382786] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.382825] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.612846] Linux video capture interface: v2.00
[   16.872850] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   16.873322] Initializing rts5139 USB card reader driver...
[   16.876201] scsi6 : SCSI emulation for RTS5139 USB card reader
[   16.876338] usbcore: registered new interface driver rts5139
[   16.876340] Realtek rts5139 USB card reader support registered.
[   16.876363] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   16.876948] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   16.878008] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   17.155680] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1
[   17.155861] Registered led device: phy0-led
[   17.155881] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   17.385807] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   17.385809] cfg80211: World regulatory domain updated:
[   17.385810] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.385812] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.385814] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.385815] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.385816] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.385818] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.584004] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_E4HD (0c45:644a)
[   17.609790] input: Laptop_Integrated_Webcam_E4HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input7
[   17.609838] usbcore: registered new interface driver uvcvideo
[   17.609840] USB Video Class driver (1.1.1)
[   18.056976] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.167843] type=1400 audit(1351615256.950:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=712 comm="apparmor_parser"
[   20.167866] type=1400 audit(1351615256.950:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=676 comm="apparmor_parser"
[   20.167877] type=1400 audit(1351615256.950:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=837 comm="apparmor_parser"
[   20.168157] type=1400 audit(1351615256.950:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=837 comm="apparmor_parser"
[   20.168163] type=1400 audit(1351615256.950:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=676 comm="apparmor_parser"
[   20.168171] type=1400 audit(1351615256.950:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=712 comm="apparmor_parser"
[   20.168315] type=1400 audit(1351615256.950:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=837 comm="apparmor_parser"
[   20.168323] type=1400 audit(1351615256.950:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=676 comm="apparmor_parser"
[   20.168364] type=1400 audit(1351615256.950:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=712 comm="apparmor_parser"
[   21.753813] RPC: Registered named UNIX socket transport module.
[   21.753816] RPC: Registered udp transport module.
[   21.753817] RPC: Registered tcp transport module.
[   21.753818] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   21.775090] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.775146] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   21.775168] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   22.292438] FS-Cache: Loaded
[   23.423095] hda_codec: CX20590: BIOS auto-probing.
[   23.642080] FS-Cache: Netfs 'nfs' registered for caching
[   25.033027] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   25.033093] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   25.033168] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   25.033236] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   25.097960] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
[   32.271169] ppdev: user-space parallel port driver
[   32.570716] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.570718] Bluetooth: BNEP filters: protocol multicast
[   32.672840] Bluetooth: RFCOMM TTY layer initialized
[   32.672844] Bluetooth: RFCOMM socket layer initialized
[   32.672846] Bluetooth: RFCOMM ver 1.11
[   33.012397] init: failsafe main process (896) killed by TERM signal
[   33.664847] type=1400 audit(1351615270.466:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1050 comm="apparmor_parser"
[   33.665140] type=1400 audit(1351615270.466:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1050 comm="apparmor_parser"
[   36.952783] type=1400 audit(1351615273.758:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1120 comm="apparmor_parser"
[   36.953070] type=1400 audit(1351615273.758:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1120 comm="apparmor_parser"
[   36.953230] type=1400 audit(1351615273.758:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1120 comm="apparmor_parser"
[   36.953947] type=1400 audit(1351615273.762:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1124 comm="apparmor_parser"
[   36.954279] type=1400 audit(1351615273.762:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1124 comm="apparmor_parser"
[   37.179521] type=1400 audit(1351615273.986:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1119 comm="apparmor_parser"
[   37.192597] type=1400 audit(1351615273.998:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1127 comm="apparmor_parser"
[   37.254659] type=1400 audit(1351615274.062:20): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1125 comm="apparmor_parser"
[   38.346290] r8169 0000:01:00.0: eth0: link down
[   38.346714] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.346907] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.348211] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   38.355765] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   38.619323] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   38.626900] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   38.709646] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.710294] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.149601] audit_printk_skb: 6 callbacks suppressed
[   39.149604] type=1400 audit(1351615275.958:23): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1121 comm="apparmor_parser"
[   39.152602] type=1400 audit(1351615275.962:24): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=1121 comm="apparmor_parser"
[   39.153183] type=1400 audit(1351615275.962:25): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=1121 comm="apparmor_parser"
[   39.153693] type=1400 audit(1351615275.962:26): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1121 comm="apparmor_parser"
[   39.155523] type=1400 audit(1351615275.966:27): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=1121 comm="apparmor_parser"
[   39.156056] type=1400 audit(1351615275.966:28): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//sanitized_helper" pid=1121 comm="apparmor_parser"
[   39.156414] type=1400 audit(1351615275.966:29): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1121 comm="apparmor_parser"
[   39.157639] type=1400 audit(1351615275.966:30): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer//sanitized_helper" pid=1121 comm="apparmor_parser"
[   40.479621] type=1400 audit(1351615277.290:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1205 comm="apparmor_parser"
[   41.811506] wlan0: authenticate with 84:1b:5e:01:5d:fe (try 1)
[   41.818220] wlan0: authenticated
[   41.824995] wlan0: associate with 84:1b:5e:01:5d:fe (try 1)
[   41.828637] wlan0: RX AssocResp from 84:1b:5e:01:5d:fe (capab=0x411 status=0 aid=1)
[   41.828642] wlan0: associated
[   41.831801] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

### Post by oldfred on 2012-10-30
Please use code tags on long data. You highlight like you want to copy and click on the # in the edit panel above your message.

I see this but have no idea if related.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709677](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709677)

I think there was a entire thread on Sandy Bridge issues, but I did not save the link.

Some tweaks, but I would only experiment with this type one at a time to see what works or not.
[https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

---

### Post by COMECON on 2012-10-30
Have you tried installing GRUB again?
```
$ sudo grub-install /dev/sdX && sudo update-grub
```
Replace sdX with the MBR, /dev/sda for me.

---

