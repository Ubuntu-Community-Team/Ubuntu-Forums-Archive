---
title: "Since when is Hibernation not working ?"
date: 2013-06-13
forum: General Help
---

### Post by checoimg on 2013-06-13
Hi everyone!

I filed a bug to the Kernel Bug tracker and I have to find where did hibernation stopped working. I can't remember when it started but with a little help I can test Ubuntu in Virtualbox to confirm where it happened.

Thank you for your time.

---

### Post by checoimg on 2013-06-13
I will start by testing 9.10 and 10.04.

---

### Post by sandyd on 2013-06-13
Hibernation is disabled by default. See [https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

---

### Post by checoimg on 2013-06-13
> **sandyd said:**
> Hibernation is disabled by default. See [https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

But I believe that in 8.04 it was there. I think I used hibernation.

---

### Post by sandyd on 2013-06-13
> **checoimg said:**
> But I believe that in 8.04 it was there. I think I used hibernation.

it was disabled in a later release, and has been disabled since

---

### Post by slickymaster on 2013-06-13
I think it was in the release of 12.04 that Hibernate was disabled by default, because it could cause problems on some system configurations.

---

### Post by checoimg on 2013-06-13
I'm downloading 11.10 for testing.

---

### Post by checoimg on 2013-06-13
> **slickymaster said:**
> I think it was in the release of 12.04 that Hibernate was disabled by default, because it could cause problems on some system configurations.

I'll get there soon.

---

### Post by Toz on 2013-06-13
> **checoimg said:**
> I'm downloading 11.10 for testing.

11.10 is no longer supported. 

Are you having a [problem with hibernation]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume") or are you looking to [re-enable the hibernate option]("https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html")?

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by checoimg on 2013-06-13
> **Toz said:**
> 11.10 is no longer supported. 

Are you having a [problem with hibernation]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume") or are you looking to [re-enable the hibernate option]("https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html")?

Is not working.

---

### Post by checoimg on 2013-06-13
> **ahallubuntu said:**
> Hibernation is NOT disabled by default in 12.04 (and probably the later versions).

What is true is that Hibernation is removed from the shutdown menu(s).  It's easy to add it back (google it).

Every installation of 12.04 can hibernate in this way, from the command line, whether it's is in the shutdown menu or not:

```
sudo pm-hibernate
```

Whether hibernation WORKS on your system is a completely different issue.  In my experience with Ubuntu, for many releases, hibernation has always been hit or miss.  If your hardware happens to work with it, good for you, but otherwise, you can try to fix it but it may not be easy or possible.  This is probably why it has been removed from the shutdown menu(s).

I managed to get hibernation working on my netbook, but it doesn't always resume properly; maybe 1/4 times, resume from hibernation fails and simply reboots.  Suspend works reliably.

So what if I try another Ubuntu version on this very same machine ? I really think it's a kernel problem not a hardware problem but I could be wrong but just to be sure I will install all versions that worked on Virtualbox and try it with the same machine.

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by checoimg on 2013-06-13
> **ahallubuntu said:**
> Hibernating in Virtualbox is not at all the same as hibernating on native hardware.  I can assure you that hibernation works on some machines very reliably in Ubuntu 12.04 but not on others, depending on the hardware.

What exactly is your goal here?  If you wish to try to get hibernation working on a specific machine, post more details about your problem

So hibernation is still working but not in all hardware.

---

### Post by checoimg on 2013-06-13
Wow this is long.

dmesg output : 
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-25-generic (buildd@roseapple) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 (Ubuntu 3.8.0-25.37-generic 3.8.13)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=e7ed069c-57a8-487e-b47e-f99f2510682f ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000b3674fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b3675000-0x00000000b36befff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b36bf000-0x00000000b374bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b374c000-0x00000000b37befff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b37bf000-0x00000000b37e2fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b37e3000-0x00000000b37fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000b37ff000-0x00000000b37fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b3800000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1b000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001fbffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000001fc000000-0x00000001ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000200000000-0x000000023bffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Acer Aspire 5820T/ZR7B, BIOS V1.19 09/08/2010
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x23c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   4 base 0B4000000 mask FFC000000 uncachable
[    0.000000]   5 base 0B3800000 mask FFF800000 uncachable
[    0.000000]   6 base 100000000 mask F00000000 write-back
[    0.000000]   7 base 200000000 mask FC0000000 write-back
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xb3800 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xb37fffff]
[    0.000000]  [mem 0x00000000-0xb37fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xb37fffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1fbffffff]
[    0.000000]  [mem 0x100000000-0x1fbffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x1fbffffff @ [mem 0xb37de000-0xb37e2fff]
[    0.000000] init_memory_mapping: [mem 0x200000000-0x23bffffff]
[    0.000000]  [mem 0x200000000-0x23bffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x23bffffff @ [mem 0x1fbffe000-0x1fbffffff]
[    0.000000] RAMDISK: [mem 0x36120000-0x37087fff]
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 00000000b37fe120 00074 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 00000000b37fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: DSDT 00000000b37ed000 0BE53 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: FACS 00000000b375f000 00040
[    0.000000] ACPI: ASF! 00000000b37fd000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: HPET 00000000b37fb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 00000000b37fa000 0008C (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 00000000b37f9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 00000000b37ec000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 00000000b37e9000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: ASPT 00000000b37e5000 00034 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: WDAT 00000000b37e4000 00224 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SSDT 00000000b37e3000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023bffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23bffffff]
[    0.000000]   NODE_DATA [mem 0x23bffb000-0x23bffffff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880233800000-ffff88023b5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23bffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xb3674fff]
[    0.000000]   node   0: [mem 0xb36bf000-0xb374bfff]
[    0.000000]   node   0: [mem 0xb37bf000-0xb37e2fff]
[    0.000000]   node   0: [mem 0xb37ff000-0xb37fffff]
[    0.000000]   node   0: [mem 0x100000000-0x1fbffffff]
[    0.000000]   node   0: [mem 0x200000000-0x23bffffff]
[    0.000000] On node 0 totalpages: 2012852
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3911 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11421 pages used for memmap
[    0.000000]   DMA32 zone: 719498 pages, LIFO batch:31
[    0.000000]   Normal zone: 20224 pages used for memmap
[    0.000000]   Normal zone: 1257728 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000b3675000 - 00000000b36bf000
[    0.000000] PM: Registered nosave memory: 00000000b374c000 - 00000000b37bf000
[    0.000000] PM: Registered nosave memory: 00000000b37e3000 - 00000000b37ff000
[    0.000000] PM: Registered nosave memory: 00000000b3800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1b000
[    0.000000] PM: Registered nosave memory: 00000000fed1b000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 00000001fc000000 - 0000000200000000
[    0.000000] e820: [mem 0xc0000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88023bc00000 s85056 r8192 d21440 u262144
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1981137
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=e7ed069c-57a8-487e-b47e-f99f2510682f ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7823816k/9371648k available (7008k kernel code, 1320240k absent, 227592k reserved, 6234k data, 996k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33030144 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2659.768 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5319.53 BogoMIPS (lpj=10639072)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000028] Security Framework initialized
[    0.000041] AppArmor: AppArmor initialized
[    0.000042] Yama: becoming mindful.
[    0.000525] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002347] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003157] Mount-cache hash table entries: 256
[    0.003355] Initializing cgroup subsys cpuacct
[    0.003358] Initializing cgroup subsys memory
[    0.003364] Initializing cgroup subsys devices
[    0.003366] Initializing cgroup subsys freezer
[    0.003367] Initializing cgroup subsys blkio
[    0.003369] Initializing cgroup subsys perf_event
[    0.003371] Initializing cgroup subsys hugetlb
[    0.003392] CPU: Physical Processor ID: 0
[    0.003393] CPU: Processor Core ID: 0
[    0.003398] mce: CPU supports 9 MCE banks
[    0.003409] CPU0: Thermal monitoring enabled (TM1)
[    0.003415] process: using mwait in idle threads
[    0.003419] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.003419] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.003419] tlb_flushall_shift: 6
[    0.003545] Freeing SMP alternatives: 24k freed
[    0.005486] ACPI: Core revision 20121018
[    0.033454] ftrace: allocating 26695 entries in 105 pages
[    0.046203] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.085786] smpboot: CPU0: Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz (fam: 06, model: 25, stepping: 05)
[    0.190870] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.190876] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.190878] ... version:                3
[    0.190878] ... bit width:              48
[    0.190879] ... generic registers:      4
[    0.190880] ... value mask:             0000ffffffffffff
[    0.190881] ... max period:             000000007fffffff
[    0.190882] ... fixed-purpose events:   3
[    0.190883] ... event mask:             000000070000000f
[    0.204985] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.191761] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.231417] Brought up 4 CPUs
[    0.231422] smpboot: Total of 4 processors activated (21278.14 BogoMIPS)
[    0.233917] devtmpfs: initialized
[    0.234966] EVM: security.selinux
[    0.234968] EVM: security.SMACK64
[    0.234969] EVM: security.capability
[    0.235013] PM: Registering ACPI NVS region [mem 0xb374c000-0xb37befff] (471040 bytes)
[    0.235781] regulator-dummy: no parameters
[    0.235823] NET: Registered protocol family 16
[    0.235950] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.235952] ACPI: bus type pci registered
[    0.236015] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.236017] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.245365] PCI: Using configuration type 1 for base access
[    0.246102] bio: create slab <bio-0> at 0
[    0.246178] ACPI: Added _OSI(Module Device)
[    0.246179] ACPI: Added _OSI(Processor Device)
[    0.246180] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.246181] ACPI: Added _OSI(Processor Aggregator Device)
[    0.247740] ACPI: EC: Look up EC in DSDT
[    0.249266] ACPI: Executed 1 blocks of module-level executable AML code
[    0.251711] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.252151] ACPI: SSDT 00000000b3691a18 00474 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.252528] ACPI: Dynamic OEM Table Load:
[    0.252530] ACPI: SSDT           (null) 00474 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.252669] ACPI: SSDT 00000000b368f018 008E0 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.253032] ACPI: Dynamic OEM Table Load:
[    0.253034] ACPI: SSDT           (null) 008E0 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.258387] ACPI: SSDT 00000000b3690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.258802] ACPI: Dynamic OEM Table Load:
[    0.258804] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.258925] ACPI: SSDT 00000000b368ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.259311] ACPI: Dynamic OEM Table Load:
[    0.259312] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.259859] ACPI: Interpreter enabled
[    0.259863] ACPI: (supports S0 S3 S4 S5)
[    0.259885] ACPI: Using IOAPIC for interrupt routing
[    0.262899] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.263001] ACPI: No dock devices found.
[    0.263004] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.263259] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    0.263261] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.263382] \_SB_.PCI0:_OSC invalid UUID
[    0.263383] _OSC request data:1 8 0 
[    0.263832] PCI host bridge to bus 0000:00
[    0.263836] pci_bus 0000:00: root bus resource [bus 00-7e]
[    0.263837] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.263839] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.263840] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.263842] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfeafffff]
[    0.263850] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.263867] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.263887] pci 0000:00:02.0: [8086:0046] type 00 class 0x030000
[    0.263896] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd03fffff 64bit]
[    0.263902] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.263906] pci 0000:00:02.0: reg 20: [io  0x3050-0x3057]
[    0.263966] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.263993] pci 0000:00:16.0: reg 10: [mem 0xd4406100-0xd440610f 64bit]
[    0.264082] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.264125] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.264524] pci 0000:00:1a.0: reg 10: [mem 0xd4405c00-0xd4405fff]
[    0.266831] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.266864] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.266883] pci 0000:00:1b.0: reg 10: [mem 0xd4400000-0xd4403fff 64bit]
[    0.266979] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.267008] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.267106] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.267141] pci 0000:00:1c.5: [8086:3b4c] type 01 class 0x060400
[    0.267238] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.267276] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.267671] pci 0000:00:1d.0: reg 10: [mem 0xd4405800-0xd4405bff]
[    0.269977] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.270003] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.270089] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100
[    0.270217] pci 0000:00:1f.2: [8086:3b29] type 00 class 0x010601
[    0.270243] pci 0000:00:1f.2: reg 10: [io  0x3048-0x304f]
[    0.270254] pci 0000:00:1f.2: reg 14: [io  0x305c-0x305f]
[    0.270264] pci 0000:00:1f.2: reg 18: [io  0x3040-0x3047]
[    0.270275] pci 0000:00:1f.2: reg 1c: [io  0x3058-0x305b]
[    0.270285] pci 0000:00:1f.2: reg 20: [io  0x3020-0x303f]
[    0.270296] pci 0000:00:1f.2: reg 24: [mem 0xd4405000-0xd44057ff]
[    0.270361] pci 0000:00:1f.2: PME# supported from D3hot
[    0.270385] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.270405] pci 0000:00:1f.3: reg 10: [mem 0xd4406000-0xd44060ff 64bit]
[    0.270434] pci 0000:00:1f.3: reg 20: [io  0x3000-0x301f]
[    0.270482] pci 0000:00:1f.6: [8086:3b32] type 00 class 0x118000
[    0.270508] pci 0000:00:1f.6: reg 10: [mem 0xd4404000-0xd4404fff 64bit]
[    0.270683] pci 0000:01:00.0: [1969:1073] type 00 class 0x020000
[    0.270711] pci 0000:01:00.0: reg 10: [mem 0xd3400000-0xd343ffff 64bit]
[    0.270728] pci 0000:01:00.0: reg 18: [io  0x2000-0x207f]
[    0.270864] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.282054] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.282062] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.282069] pci 0000:00:1c.0:   bridge window [mem 0xd3400000-0xd43fffff]
[    0.282080] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.282175] pci 0000:02:00.0: [168c:002e] type 00 class 0x028000
[    0.282196] pci 0000:02:00.0: reg 10: [mem 0xd2400000-0xd240ffff 64bit]
[    0.282298] pci 0000:02:00.0: supports D1
[    0.282300] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.290029] pci 0000:00:1c.5: PCI bridge to [bus 02]
[    0.290036] pci 0000:00:1c.5:   bridge window [io  0x1000-0x1fff]
[    0.290044] pci 0000:00:1c.5:   bridge window [mem 0xd2400000-0xd33fffff]
[    0.290054] pci 0000:00:1c.5:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.290152] pci 0000:00:1e.0: PCI bridge to [bus 03] (subtractive decode)
[    0.290164] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.290166] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.290168] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.290169] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
[    0.290199] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.290249] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.290321] \_SB_.PCI0:_OSC invalid UUID
[    0.290322] _OSC request data:1 1f 0 
[    0.290325]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.290326]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.290792] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 7f])
[    0.290837] PCI host bridge to bus 0000:7f
[    0.290839] pci_bus 0000:7f: root bus resource [bus 7f]
[    0.290844] pci 0000:7f:00.0: [8086:2c62] type 00 class 0x060000
[    0.290860] pci 0000:7f:00.1: [8086:2d01] type 00 class 0x060000
[    0.290878] pci 0000:7f:02.0: [8086:2d10] type 00 class 0x060000
[    0.290893] pci 0000:7f:02.1: [8086:2d11] type 00 class 0x060000
[    0.290907] pci 0000:7f:02.2: [8086:2d12] type 00 class 0x060000
[    0.290922] pci 0000:7f:02.3: [8086:2d13] type 00 class 0x060000
[    0.290949]  pci0000:7f: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.290950]  pci0000:7f: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.291066] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.291101] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.291134] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.291167] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.291200] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.291233] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.291270] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.291304] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.291390] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.291393] vgaarb: loaded
[    0.291394] vgaarb: bridge control possible 0000:00:02.0
[    0.291534] SCSI subsystem initialized
[    0.291536] ACPI: bus type scsi registered
[    0.291583] libata version 3.00 loaded.
[    0.291596] ACPI: bus type usb registered
[    0.291611] usbcore: registered new interface driver usbfs
[    0.291617] usbcore: registered new interface driver hub
[    0.291634] usbcore: registered new device driver usb
[    0.291705] PCI: Using ACPI for IRQ routing
[    0.296537] PCI: pci_cache_line_size set to 64 bytes
[    0.296592] e820: reserve RAM buffer [mem 0x0009d000-0x0009ffff]
[    0.296594] e820: reserve RAM buffer [mem 0xb3675000-0xb3ffffff]
[    0.296596] e820: reserve RAM buffer [mem 0xb374c000-0xb3ffffff]
[    0.296597] e820: reserve RAM buffer [mem 0xb37e3000-0xb3ffffff]
[    0.296598] e820: reserve RAM buffer [mem 0xb3800000-0xb3ffffff]
[    0.296675] NetLabel: Initializing
[    0.296677] NetLabel:  domain hash size = 128
[    0.296678] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.296686] NetLabel:  unlabeled traffic allowed by default
[    0.296740] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.296744] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.298755] Switching to clocksource hpet
[    0.303209] AppArmor: AppArmor Filesystem Enabled
[    0.303240] pnp: PnP ACPI init
[    0.303255] ACPI: bus type pnp registered
[    0.303349] pnp 00:00: [dma 4]
[    0.303374] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.303391] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.303489] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.303520] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.303541] pnp 00:04: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.5 BAR 13 [io  0x1000-0x1fff]
[    0.303569] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.303570] system 00:04: [io  0x0800-0x080f] has been reserved
[    0.303572] system 00:04: [io  0xffff] has been reserved
[    0.303574] system 00:04: [io  0xffff] has been reserved
[    0.303575] system 00:04: [io  0x0400-0x047f] has been reserved
[    0.303577] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.303580] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.303601] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.303624] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.303646] pnp 00:07: Plug and Play ACPI device, IDs SYN1b20 SYN1b00 SYN0002 PNP0f13 (active)
[    0.303919] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.303922] system 00:08: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.303923] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.303925] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.303927] system 00:08: [mem 0xf0000000-0xf1ffffff] has been reserved
[    0.303928] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.303930] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.303932] system 00:08: [mem 0xff000000-0xffffffff] could not be reserved
[    0.303934] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.303935] system 00:08: [mem 0xd4500000-0xd4500fff] has been reserved
[    0.303938] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.304034] pnp: PnP ACPI: found 9 devices
[    0.304035] ACPI: ACPI bus type pnp unregistered
[    0.310205] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.310210] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.310216] pci 0000:00:1c.0:   bridge window [mem 0xd3400000-0xd43fffff]
[    0.310220] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.310228] pci 0000:00:1c.5: PCI bridge to [bus 02]
[    0.310231] pci 0000:00:1c.5:   bridge window [io  0x1000-0x1fff]
[    0.310236] pci 0000:00:1c.5:   bridge window [mem 0xd2400000-0xd33fffff]
[    0.310241] pci 0000:00:1c.5:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.310248] pci 0000:00:1e.0: PCI bridge to [bus 03]
[    0.310290] pci 0000:00:1e.0: setting latency timer to 64
[    0.310295] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.310296] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.310298] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.310299] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfeafffff]
[    0.310301] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.310303] pci_bus 0000:01: resource 1 [mem 0xd3400000-0xd43fffff]
[    0.310304] pci_bus 0000:01: resource 2 [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.310306] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.310307] pci_bus 0000:02: resource 1 [mem 0xd2400000-0xd33fffff]
[    0.310309] pci_bus 0000:02: resource 2 [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.310311] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.310312] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.310314] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.310315] pci_bus 0000:03: resource 7 [mem 0xc0000000-0xfeafffff]
[    0.310346] NET: Registered protocol family 2
[    0.310500] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.310753] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.310945] TCP: Hash tables configured (established 65536 bind 65536)
[    0.310978] TCP: reno registered
[    0.310990] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.311024] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.311113] NET: Registered protocol family 1
[    0.311128] pci 0000:00:02.0: Boot video device
[    0.342733] PCI: CLS 64 bytes, default 64
[    0.342798] Trying to unpack rootfs image as initramfs...
[    0.563723] Freeing initrd memory: 15776k freed
[    0.567121] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.567128] software IO TLB [mem 0xaf675000-0xb3675000] (64MB) mapped at [ffff8800af675000-ffff8800b3674fff]
[    0.567171] Simple Boot Flag at 0x44 set to 0x1
[    0.567578] Initialise module verification
[    0.567618] audit: initializing netlink socket (disabled)
[    0.567635] type=2000 audit(1371144334.448:1): initialized
[    0.590327] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.591613] VFS: Disk quotas dquot_6.5.2
[    0.591648] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.592033] fuse init (API version 7.20)
[    0.592095] msgmni has been set to 15311
[    0.592517] Key type asymmetric registered
[    0.592520] Asymmetric key parser 'x509' registered
[    0.592546] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.592578] io scheduler noop registered
[    0.592580] io scheduler deadline registered (default)
[    0.592584] io scheduler cfq registered
[    0.592765] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.592776] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.592807] intel_idle: MWAIT substates: 0x1120
[    0.592808] intel_idle: v0.4 model 0x25
[    0.592809] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.989217] ACPI: AC Adapter [ACAD] (on-line)
[    0.989366] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0C:00/input/input0
[    0.989370] ACPI: Power Button [PWRB]
[    0.989397] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0D:00/input/input1
[    0.989417] ACPI: Lid Switch [LID0]
[    0.989442] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0E:00/input/input2
[    0.989444] ACPI: Sleep Button [SLPB]
[    0.989468] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.989470] ACPI: Power Button [PWRF]
[    0.989529] ACPI: Requesting acpi_cpufreq
[    0.992935] thermal LNXTHERM:00: registered as thermal_zone0
[    0.992938] ACPI: Thermal Zone [THRM] (54 C)
[    0.992960] GHES: HEST is not enabled!
[    0.993074] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.993700] [Firmware Bug]: battery: (dis)charge rate invalid.
[    0.993723] ACPI: Battery Slot [BAT1] (battery present)
[    0.994516] Linux agpgart interface v0.103
[    0.994562] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    0.994626] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.995297] agpgart-intel 0000:00:00.0: detected 131072K stolen memory
[    0.995455] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.996469] brd: module loaded
[    0.996987] loop: module loaded
[    0.997311] libphy: Fixed MDIO Bus: probed
[    0.997352] tun: Universal TUN/TAP device driver, 1.6
[    0.997353] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.997389] PPP generic driver version 2.4.2
[    0.997440] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.997442] ehci-pci: EHCI PCI platform driver
[    0.997482] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.997486] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.997491] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.997507] ehci-pci 0000:00:1a.0: debug port 2
[    1.001416] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.001435] ehci-pci 0000:00:1a.0: irq 16, io mem 0xd4405c00
[    1.013003] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.013033] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.013037] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.013041] usb usb1: Product: EHCI Host Controller
[    1.013044] usb usb1: Manufacturer: Linux 3.8.0-25-generic ehci_hcd
[    1.013047] usb usb1: SerialNumber: 0000:00:1a.0
[    1.013180] hub 1-0:1.0: USB hub found
[    1.013185] hub 1-0:1.0: 3 ports detected
[    1.013273] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.013277] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.013281] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.013295] ehci-pci 0000:00:1d.0: debug port 2
[    1.017204] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.017218] ehci-pci 0000:00:1d.0: irq 23, io mem 0xd4405800
[    1.028962] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.028998] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.029002] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.029006] usb usb2: Product: EHCI Host Controller
[    1.029009] usb usb2: Manufacturer: Linux 3.8.0-25-generic ehci_hcd
[    1.029012] usb usb2: SerialNumber: 0000:00:1d.0
[    1.029130] hub 2-0:1.0: USB hub found
[    1.029136] hub 2-0:1.0: 3 ports detected
[    1.029219] ehci-platform: EHCI generic platform driver
[    1.029225] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.029234] uhci_hcd: USB Universal Host Controller Interface driver
[    1.029279] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.035174] i8042: Detected active multiplexing controller, rev 1.1
[    1.038808] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.038812] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.038831] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.038845] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.038856] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.038962] mousedev: PS/2 mouse device common for all mice
[    1.039153] rtc_cmos 00:05: RTC can wake from S4
[    1.039284] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.039316] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.039379] device-mapper: uevent: version 1.0.3
[    1.039435] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [email]dm-devel@redhat.com[/email]
[    1.039484] cpuidle: using governor ladder
[    1.039540] cpuidle: using governor menu
[    1.039545] ledtrig-cpu: registered to indicate activity on CPUs
[    1.039546] EFI Variables Facility v0.08 2004-May-17
[    1.039734] ashmem: initialized
[    1.039854] TCP: cubic registered
[    1.039922] NET: Registered protocol family 10
[    1.040090] NET: Registered protocol family 17
[    1.040110] Key type dns_resolver registered
[    1.040528] Loading module verification certificates
[    1.042463] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: dbae232d36ad7257df58e2fefc4fab11a387ce7c'
[    1.042493] registered taskstats version 1
[    1.046635] Key type trusted registered
[    1.049820] Key type encrypted registered
[    1.053666] rtc_cmos 00:05: setting system clock to 2013-06-13 17:25:35 UTC (1371144335)
[    1.054961] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.054962] EDD information not available.
[    1.056152] Freeing unused kernel memory: 996k freed
[    1.056319] Write protecting the kernel read-only data: 12288k
[    1.058969] Freeing unused kernel memory: 1172k freed
[    1.059334] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.061463] Freeing unused kernel memory: 1080k freed
[    1.076229] udevd[107]: starting version 175
[    1.107493] Disabling lock debugging due to kernel taint
[    1.108130] ahci 0000:00:1f.2: version 3.0
[    1.108201] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.108236] ahci: SSS flag set, parallel bus scan disabled
[    1.108284] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.108287] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems apst 
[    1.108292] ahci 0000:00:1f.2: setting latency timer to 64
[    1.113662] scsi0 : ahci
[    1.113964] scsi1 : ahci
[    1.114467] scsi2 : ahci
[    1.115254] scsi3 : ahci
[    1.115309] ata1: SATA max UDMA/133 abar m2048@0xd4405000 port 0xd4405100 irq 40
[    1.115314] ata2: SATA max UDMA/133 abar m2048@0xd4405000 port 0xd4405180 irq 40
[    1.115316] ata3: DUMMY
[    1.115317] ata4: DUMMY
[    1.129215] atl1c 0000:01:00.0: version 1.0.1.1-NAPI
[    1.324362] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.432038] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.433303] ata1.00: ATA-8: Hitachi HTS545050B9A300, PB4OC60F, max UDMA/133
[    1.433309] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.434761] ata1.00: configured for UDMA/133
[    1.435157] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54505 PB4O PQ: 0 ANSI: 5
[    1.435407] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.435438] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.435534] sd 0:0:0:0: [sda] Write Protect is off
[    1.435537] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.435574] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.456732] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.456737] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.457390] hub 1-1:1.0: USB hub found
[    1.457471] hub 1-1:1.0: 6 ports detected
[    1.500284]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.501541] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.563727] tsc: Refined TSC clocksource calibration: 2660.000 MHz
[    1.563734] Switching to clocksource tsc
[    1.567710] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.699824] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    1.699829] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.700047] hub 2-1:1.0: USB hub found
[    1.700175] hub 2-1:1.0: 8 ports detected
[    1.751226] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.754908] ata2.00: ATAPI: HL-DT-ST DVDRAM GU10N, AP04, max UDMA/133
[    1.759713] ata2.00: configured for UDMA/133
[    1.771375] usb 1-1.1: new high-speed USB device number 3 using ehci-pci
[    1.871578] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GU10N     AP04 PQ: 0 ANSI: 5
[    1.969376] usb 1-1.1: New USB device found, idVendor=0402, idProduct=9665
[    1.969381] usb 1-1.1: New USB device strings: Mfr=3, Product=1, SerialNumber=0
[    1.969385] usb 1-1.1: Product: 1.3M WebCam
[    1.969388] usb 1-1.1: Manufacturer: XPAAE0NMP
[    1.981264] sr0: scsi3-mmc drive: 62x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.981269] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.981485] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.981557] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.054682] usb 1-1.5: new high-speed USB device number 4 using ehci-pci
[    2.147607] usb 1-1.5: New USB device found, idVendor=058f, idProduct=6366
[    2.147611] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.147614] usb 1-1.5: Product: Mass Storage Device
[    2.147616] usb 1-1.5: Manufacturer: Generic
[    2.147618] usb 1-1.5: SerialNumber: 058F63666433
[    2.149938] Initializing USB Mass Storage driver...
[    2.150035] scsi4 : usb-storage 1-1.5:1.0
[    2.150110] usbcore: registered new interface driver usb-storage
[    2.150112] USB Mass Storage support registered.
[    3.272432] scsi 4:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[    3.273338] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    4.002916] sd 4:0:0:0: [sdb] 7744512 512-byte logical blocks: (3.96 GB/3.69 GiB)
[    4.004095] sd 4:0:0:0: [sdb] Write Protect is off
[    4.004102] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    4.005160] sd 4:0:0:0: [sdb] No Caching mode page present
[    4.005166] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    4.009389] sd 4:0:0:0: [sdb] No Caching mode page present
[    4.009394] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    4.011272]  sdb: sdb1
[    4.015000] sd 4:0:0:0: [sdb] No Caching mode page present
[    4.015011] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    4.015017] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.852989] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   35.627645] Adding 8000508k swap on /dev/sda6.  Priority:-1 extents:1 across:8000508k 
[   35.782366] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.805883] udevd[380]: starting version 175
[   36.085099] microcode: CPU0 sig=0x20655, pf=0x10, revision=0x2
[   36.087262] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   36.087327] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[   36.088895] lp: driver loaded but no devices found
[   36.096613] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   36.096872] mei 0000:00:16.0: setting latency timer to 64
[   36.096953] mei 0000:00:16.0: irq 41 for MSI/MSI-X
[   36.106001] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   36.106009] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.106014] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   36.106018] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \_SB_.PCI0.LPCB.EC0_.GPBD 2 (20121018/utaddress-251)
[   36.106021] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.106022] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   36.106026] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.LPCB.EC0_.GPBD 2 (20121018/utaddress-251)
[   36.106028] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.106030] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   36.106033] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.LPCB.EC0_.GPBD 2 (20121018/utaddress-251)
[   36.106036] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.106037] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   36.106672] [drm] Initialized drm 1.1.0 20060810
[   36.113374] cfg80211: Calling CRDA to update world regulatory domain
[   36.127050] i915 0000:00:02.0: setting latency timer to 64
[   36.147547] wmi: Mapper loaded
[   36.165023] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[   36.165038] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   36.165039] [drm] Driver supports precise vblank timestamp query.
[   36.165088] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   36.223216] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x2
[   36.231068] acer_wmi: Acer Laptop ACPI-WMI Extras
[   36.231087] acer_wmi: Function bitmap for Communication Button: 0x1
[   36.232068] acer_wmi: Brightness must be controlled by acpi video driver
[   36.233705] microcode: CPU2 sig=0x20655, pf=0x10, revision=0x2
[   36.235145] Linux video capture interface: v2.00
[   36.238705] input: Acer WMI hotkeys as /devices/virtual/input/input5
[   36.239668] input: Acer BMA150 accelerometer as /devices/virtual/input/input6
[   36.245655] microcode: CPU3 sig=0x20655, pf=0x10, revision=0x2
[   36.245856] ath: phy0: ASPM enabled: 0x42
[   36.245861] ath: EEPROM regdomain: 0x65
[   36.245863] ath: EEPROM indicates we should expect a direct regpair map
[   36.245866] ath: Country alpha2 being used: 00
[   36.245868] ath: Regpair used: 0x65
[   36.251281] uvcvideo: Found UVC 1.00 device 1.3M WebCam (0402:9665)
[   36.252072] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   36.254743] input: 1.3M WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input7
[   36.255266] usbcore: registered new interface driver uvcvideo
[   36.255269] USB Video Class driver (1.1.1)
[   36.261520] type=1400 audit(1371158770.792:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=579 comm="apparmor_parser"
[   36.261971] type=1400 audit(1371158770.792:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=579 comm="apparmor_parser"
[   36.262228] type=1400 audit(1371158770.792:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=579 comm="apparmor_parser"
[   36.267760] type=1400 audit(1371158770.796:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=578 comm="apparmor_parser"
[   36.268320] type=1400 audit(1371158770.796:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=578 comm="apparmor_parser"
[   36.268523] type=1400 audit(1371158770.796:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=578 comm="apparmor_parser"
[   36.271479] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   36.272146] ieee80211 phy0: Atheros AR9287 Rev:2 mem=0xffffc90008ee0000, irq=17
[   36.286752] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   36.336655] cfg80211: World regulatory domain updated:
[   36.336659] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   36.336660] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.336662] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   36.336663] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   36.336664] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.336665] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.390150] fbcon: inteldrmfb (fb0) is primary device
[   36.983161] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa44000/0xa0000, board id: 3655, fw id: 554713
[   37.030535] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8
[   37.074777] Console: switching to colour frame buffer device 170x48
[   37.077381] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   37.077383] i915 0000:00:02.0: registered panic notifier
[   37.078242] acpi device:01: registered as cooling_device4
[   37.078368] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   37.078413] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   37.078656] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   37.094587] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   37.094705] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   37.109022] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   37.109134] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   37.119200] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   37.905726] init: failsafe main process (979) killed by TERM signal
[   38.235953] Bluetooth: Core ver 2.16
[   38.235977] NET: Registered protocol family 31
[   38.235978] Bluetooth: HCI device and connection manager initialized
[   38.235988] Bluetooth: HCI socket layer initialized
[   38.235991] Bluetooth: L2CAP socket layer initialized
[   38.235997] Bluetooth: SCO socket layer initialized
[   38.239786] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.239790] Bluetooth: BNEP filters: protocol multicast
[   38.239801] Bluetooth: BNEP socket layer initialized
[   38.241232] Bluetooth: RFCOMM TTY layer initialized
[   38.241242] Bluetooth: RFCOMM socket layer initialized
[   38.241243] Bluetooth: RFCOMM ver 1.11
[   38.693346] init: avahi-cups-reload main process (1040) terminated with status 1
[   38.785130] ppdev: user-space parallel port driver
[   38.914381] type=1400 audit(1371158773.452:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1057 comm="apparmor_parser"
[   38.915257] type=1400 audit(1371158773.452:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1057 comm="apparmor_parser"
[   39.238987] atl1c 0000:01:00.0: irq 44 for MSI/MSI-X
[   39.254810] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.260393] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.286614] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.291245] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.190521] type=1400 audit(1371158774.728:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1102 comm="apparmor_parser"
[   40.190871] type=1400 audit(1371158774.732:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1102 comm="apparmor_parser"
[   41.157314] wlan0: authenticate with cc:7d:37:8e:d7:16
[   41.164879] wlan0: send auth to cc:7d:37:8e:d7:16 (try 1/3)
[   41.171070] wlan0: authenticated
[   41.171339] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   41.172418] wlan0: associate with cc:7d:37:8e:d7:16 (try 1/3)
[   41.180291] wlan0: RX AssocResp from cc:7d:37:8e:d7:16 (capab=0x411 status=0 aid=3)
[   41.180402] wlan0: associated
[   41.180419] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   41.284221] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   43.009734] vboxdrv: Found 4 processor cores.
[   43.009891] vboxdrv: fAsync=0 offMin=0xf0 offMax=0x1b21
[   43.009970] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   43.009971] vboxdrv: Successfully loaded version 4.2.10_Ubuntu (interface 0x001a0004).
[   43.031004] vboxpci: IOMMU not found (not registered)
[   43.806873] init: plymouth-stop pre-start process (1762) terminated with status 1
[   45.755435] init: winbind main process (2889) terminated with status 127
[   45.755479] init: winbind main process ended, respawning
[   45.759589] init: winbind main process (2894) terminated with status 127
[   45.759616] init: winbind main process ended, respawning
[   45.764117] init: winbind main process (2896) terminated with status 127
[   45.764140] init: winbind main process ended, respawning
[   45.768478] init: winbind main process (2898) terminated with status 127
[   45.768503] init: winbind main process ended, respawning
[   45.772258] init: winbind main process (2900) terminated with status 127
[   45.772280] init: winbind main process ended, respawning
[   45.775941] init: winbind main process (2902) terminated with status 127
[   45.775970] init: winbind main process ended, respawning
[   45.779265] init: winbind main process (2904) terminated with status 127
[   45.779296] init: winbind main process ended, respawning
[   45.782557] init: winbind main process (2906) terminated with status 127
[   45.782579] init: winbind main process ended, respawning
[   45.785932] init: winbind main process (2908) terminated with status 127
[   45.785964] init: winbind main process ended, respawning
[   45.789883] init: winbind main process (2910) terminated with status 127
[   45.789905] init: winbind main process ended, respawning
[   45.793915] init: winbind main process (2912) terminated with status 127
[   45.793934] init: winbind respawning too fast, stopped
[   49.011476] ISO 9660 Extensions: Microsoft Joliet Level 3
[   49.017862] ISO 9660 Extensions: RRIP_1991A
[   83.766004] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   83.766020] sr 1:0:0:0: CDB: 
[   83.766025] Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[   83.766052] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[   83.766052]          res 40/00:02:00:00:02/00:00:00:00:00/00 Emask 0x4 (timeout)
[   83.766060] ata2.00: status: { DRDY }
[   83.766071] ata2: hard resetting link
[   84.084959] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   84.094461] ata2.00: configured for UDMA/133
[   84.112892] ata2: EH complete
```

---

### Post by checoimg on 2013-06-13
cat /proc/cmdline

output :

BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=e7ed069c-57a8-487e-b47e-f99f2510682f ro quiet splash vt.handoff=7

cat /etc/initramfs-tools/conf.d/resume

output :

RESUME=UUID=77f1b17d-a5a5-47a6-882c-7afa627e4d62

---

