---
title: "New kernel boot stalls with nvidia driver installation.. ?"
date: 2015-06-11
forum: General Help
---

### Post by einstein**-7 on 2015-06-11
Anyone have a suggestion for finding the cause of a boot simply stalling ? I've looked in all the normal system log files and also enabled bootlogd and can't seem to find the source of the problem!  I recently updated the kernel to 3.13.0-53 and it booted fine, however after installing the nvidia drivers from nvidia's site the boot gets to the last line or so and simply stops with no fails in the list of processes.
It does boot perfectly from the recovery menu for that kernel version ! weird..  Also nomodeset and forcing rw mounting of the filesystem from the NON recovery grub line gets nothing.
Today Ubuntu released the 3.13.0.54 kernel and I upgraded to that and same exact problem.  Buttt... now the 53 kernel works fine !??! I even removed the graphic driver and reinstalled it for the 53 version and still works perfectly....
The only error I have ever got a glimpse of is once when booting from the recovery menu I saw a "" unable to verify nvidia driver etc "" or some such just before the greeter login popped up. 

NOTE: I did find a lot of threads about similar boot / nvidia issues but none of them is relevant as they usually involve some kind of user permission or display manager configuration problems and generate errors in multiple log files none of which is true in my case ,, just empty logs...

Any ideas about tracking this down would be appreciated!

---

### Post by QDR06VV9 on 2015-06-11
When it comes to installing Video Drivers **it is Always best to stay with what comes in the package managers**(synaptic or software centre) for the Very Reason you are posting your thread.
See this [http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)
And for How to install [http://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers/61433#61433](http://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers/61433#61433)
kernel updates or upgrades will break your Driver installing from the Nvidia Site
Read the whole page.
Regards

---

### Post by einstein**-7 on 2015-06-12
Did a little more research on log files to be sure i didn't miss something and here is the log below for "dmesg".

The section below is the only section with nvidia specific errors that i could see, any ideas?
Also the Xorg.0.log just showed at the end of the log that the graphic cards were unloaded and server was terminated with an EE status but no errors in xserver itself. 

```
 7.141596] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.143343] mei_me 0000:00:16.0: irq 91 for MSI/MSI-X
[    7.147889] [drm] Initialized drm 1.1.0 20060810
[    7.149969] lp: driver loaded but no devices found
[    7.150247] nvidia: module license 'NVIDIA' taints kernel.
[    7.150249] Disabling lock debugging due to kernel taint
[    7.152613] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    7.158198] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    7.158443] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[    7.158477] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[    7.158921] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[    7.158985] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:02:00.0 on minor 1
[    7.158996] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.72  Tue May  5 22:03:13 PDT 2015

```

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-53-generic (buildd@phianna) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 (Ubuntu 3.13.0-53.89-generic 3.13.11-ckt19)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-53-generic root=UUID=454a85dd-7c27-44c5-90bc-94bf06412f1b rw vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bbf5ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bbf60000-0x00000000bc39dfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bc39e000-0x00000000bc4abfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bc4ac000-0x00000000bc6ccfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bc6cd000-0x00000000bd718fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bd719000-0x00000000bd719fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bd71a000-0x00000000bd79ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bd7a0000-0x00000000bdbdafff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bdbdb000-0x00000000bdff3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bdff4000-0x00000000bdffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000083fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: System manufacturer System Product Name/SABERTOOTH X79, BIOS 4801 07/25/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x840000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask 3FF800000000 write-back
[    0.000000]   1 base 000800000000 mask 3FFFC0000000 write-back
[    0.000000]   2 base 0000BF000000 mask 3FFFFF000000 uncachable
[    0.000000]   3 base 0000C0000000 mask 3FFFC0000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 32GB, type WB
[    0.000000] reg 1, base: 32GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3056MB, range: 16MB, type UC
[    0.000000] reg 3, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 32752M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3056MB, range: 16MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 16GB, type WB
[    0.000000] reg 6, base: 32GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xbf000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbe000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd900-0x000fd90f] mapped at [ffff8800000fd900]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x83fe00000-0x83fffffff]
[    0.000000]  [mem 0x83fe00000-0x83fffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x83c000000-0x83fdfffff]
[    0.000000]  [mem 0x83c000000-0x83fdfffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x800000000-0x83bffffff]
[    0.000000]  [mem 0x800000000-0x83bffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbbf5ffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0xbbdfffff] page 2M
[    0.000000]  [mem 0xbbe00000-0xbbf5ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbd719000-0xbd719fff]
[    0.000000]  [mem 0xbd719000-0xbd719fff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbd7a0000-0xbdbdafff]
[    0.000000]  [mem 0xbd7a0000-0xbd7fffff] page 4k
[    0.000000]  [mem 0xbd800000-0xbd9fffff] page 2M
[    0.000000]  [mem 0xbda00000-0xbdbdafff] page 4k
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbdff4000-0xbdffffff]
[    0.000000]  [mem 0xbdff4000-0xbdffffff] page 4k
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100000000-0x7ffffffff]
[    0.000000]  [mem 0x100000000-0x7ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x34a74000-0x36531fff]
[    0.000000] ACPI: RSDP 00000000000f0490 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000bc3d4070 000054 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000bc3de230 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000bc3d4158 00A0D7 (v02 ALASKA    A M I 00000016 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bc6c4080 000040
[    0.000000] ACPI: APIC 00000000bc3de340 0000C8 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000bc3de408 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000bc3de450 00003C (v01 ALASKA OEMMCFG. 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bc3de490 000038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000bc3de520 0CD128 (v02  INTEL    CpuPm 00004000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000083fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x83fffffff]
[    0.000000]   NODE_DATA [mem 0x83fff9000-0x83fffdfff]
[    0.000000]  [ffffea0000000000-ffffea0020ffffff] PMD -> [ffff88081f600000-ffff88083f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x83fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xbbf5ffff]
[    0.000000]   node   0: [mem 0xbd719000-0xbd719fff]
[    0.000000]   node   0: [mem 0xbd7a0000-0xbdbdafff]
[    0.000000]   node   0: [mem 0xbdff4000-0xbdffffff]
[    0.000000]   node   0: [mem 0x100000000-0x83fffffff]
[    0.000000] On node 0 totalpages: 8373061
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11983 pages used for memmap
[    0.000000]   DMA32 zone: 766888 pages, LIFO batch:31
[    0.000000]   Normal zone: 118784 pages used for memmap
[    0.000000]   Normal zone: 7602176 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec01000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 2, version 32, address 0xfec01000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbbf60000-0xbc39dfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbc39e000-0xbc4abfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbc4ac000-0xbc6ccfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbc6cd000-0xbd718fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbd71a000-0xbd79ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbdbdb000-0xbdff3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbe000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xbe000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88083fc00000 s81536 r8192 d20864 u262144
[    0.000000] pcpu-alloc: s81536 r8192 d20864 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 8242209
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-53-generic root=UUID=454a85dd-7c27-44c5-90bc-94bf06412f1b rw vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 32856992K/33492244K available (7391K kernel code, 1146K rwdata, 3408K rodata, 1336K init, 1448K bss, 635252K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:1152 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 134217728 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3806.803 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 7613.60 BogoMIPS (lpj=15227212)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000023] Security Framework initialized
[    0.000036] AppArmor: AppArmor initialized
[    0.000038] Yama: becoming mindful.
[    0.001402] Dentry cache hash table entries: 4194304 (order: 13, 33554432 bytes)
[    0.005583] Inode-cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.007382] Mount-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.007408] Mountpoint-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.007606] Initializing cgroup subsys memory
[    0.007610] Initializing cgroup subsys devices
[    0.007612] Initializing cgroup subsys freezer
[    0.007614] Initializing cgroup subsys blkio
[    0.007615] Initializing cgroup subsys perf_event
[    0.007617] Initializing cgroup subsys hugetlb
[    0.007633] CPU: Physical Processor ID: 0
[    0.007634] CPU: Processor Core ID: 0
[    0.007639] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.007639] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.007642] mce: CPU supports 16 MCE banks
[    0.007659] CPU0: Thermal monitoring enabled (TM1)
[    0.007672] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.007672] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.007672] tlb_flushall_shift: 5
[    0.007761] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.008750] ACPI: Core revision 20131115
[    0.025252] ACPI: All ACPI Tables successfully acquired
[    0.308797] ftrace: allocating 28577 entries in 112 pages
[    0.318901] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.358587] smpboot: CPU0: Intel(R) Core(TM) i7-3820 CPU @ 3.60GHz (fam: 06, model: 2d, stepping: 07)
[    0.358592] TSC deadline timer enabled
[    0.358598] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, full-width counters, Intel PMU driver.
[    0.358603] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.358606] ... version:                3
[    0.358607] ... bit width:              48
[    0.358608] ... generic registers:      4
[    0.358609] ... value mask:             0000ffffffffffff
[    0.358610] ... max period:             0000ffffffffffff
[    0.358611] ... fixed-purpose events:   3
[    0.358612] ... event mask:             000000070000000f
[    0.359648] x86: Booting SMP configuration:
[    0.372846] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.359650] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.452064] x86: Booted up 1 node, 8 CPUs
[    0.452069] smpboot: Total of 8 processors activated (60908.84 BogoMIPS)
[    0.458772] devtmpfs: initialized
[    0.461326] EVM: security.selinux
[    0.461327] EVM: security.SMACK64
[    0.461328] EVM: security.ima
[    0.461329] EVM: security.capability
[    0.461355] PM: Registering ACPI NVS region [mem 0xbc4ac000-0xbc6ccfff] (2232320 bytes)
[    0.461376] PM: Registering ACPI NVS region [mem 0xbd71a000-0xbd79ffff] (548864 bytes)
[    0.461942] pinctrl core: initialized pinctrl subsystem
[    0.461981] regulator-dummy: no parameters
[    0.462007] RTC time: 11:49:21, date: 06/11/15
[    0.462031] NET: Registered protocol family 16
[    0.462093] cpuidle: using governor ladder
[    0.462095] cpuidle: using governor menu
[    0.462115] ACPI: bus type PCI registered
[    0.462117] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.462152] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.462155] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.477035] PCI: Using configuration type 1 for base access
[    0.477746] bio: create slab <bio-0> at 0
[    0.477899] ACPI: Added _OSI(Module Device)
[    0.477901] ACPI: Added _OSI(Processor Device)
[    0.477902] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.477904] ACPI: Added _OSI(Processor Aggregator Device)
[    0.487020] ACPI: Executed 1 blocks of module-level executable AML code
[    0.560224] ACPI: Interpreter enabled
[    0.560231] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.560235] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.560243] ACPI: (supports S0 S3 S4 S5)
[    0.560245] ACPI: Using IOAPIC for interrupt routing
[    0.560264] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.560395] ACPI: No dock devices found.
[    0.565888] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.565893] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.565982] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME AER]
[    0.566064] acpi PNP0A08:00: _OSC: OS now controls [PCIeCapability]
[    0.566287] PCI host bridge to bus 0000:00
[    0.566290] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.566292] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
[    0.566293] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
[    0.566295] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
[    0.566296] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.566298] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.566300] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.566301] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xffffffff]
[    0.566312] pci 0000:00:00.0: [8086:3c00] type 00 class 0x060000
[    0.566356] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    0.566408] pci 0000:00:01.0: [8086:3c02] type 01 class 0x060400
[    0.566459] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.566496] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.566522] pci 0000:00:02.0: [8086:3c04] type 01 class 0x060400
[    0.566572] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.566608] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.566634] pci 0000:00:03.0: [8086:3c08] type 01 class 0x060400
[    0.566685] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.566720] pci 0000:00:03.0: System wakeup disabled by ACPI
[    0.566742] pci 0000:00:05.0: [8086:3c28] type 00 class 0x088000
[    0.566823] pci 0000:00:05.2: [8086:3c2a] type 00 class 0x088000
[    0.566901] pci 0000:00:05.4: [8086:3c2c] type 00 class 0x080020
[    0.566911] pci 0000:00:05.4: reg 0x10: [mem 0xf912a000-0xf912afff]
[    0.566999] pci 0000:00:11.0: [8086:1d3e] type 01 class 0x060400
[    0.567075] pci 0000:00:11.0: PME# supported from D0 D3hot D3cold
[    0.567136] pci 0000:00:16.0: [8086:1d3a] type 00 class 0x078000
[    0.567156] pci 0000:00:16.0: reg 0x10: [mem 0xf9129000-0xf912900f 64bit]
[    0.567221] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.567276] pci 0000:00:19.0: [8086:1503] type 00 class 0x020000
[    0.567291] pci 0000:00:19.0: reg 0x10: [mem 0xf9100000-0xf911ffff]
[    0.567297] pci 0000:00:19.0: reg 0x14: [mem 0xf9128000-0xf9128fff]
[    0.567304] pci 0000:00:19.0: reg 0x18: [io  0xf040-0xf05f]
[    0.567356] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.567387] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.567410] pci 0000:00:1a.0: [8086:1d2d] type 00 class 0x0c0320
[    0.567428] pci 0000:00:1a.0: reg 0x10: [mem 0xf9127000-0xf91273ff]
[    0.567505] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.567538] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.567560] pci 0000:00:1b.0: [8086:1d20] type 00 class 0x040300
[    0.567572] pci 0000:00:1b.0: reg 0x10: [mem 0xf9120000-0xf9123fff 64bit]
[    0.567628] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.567677] pci 0000:00:1c.0: [8086:1d10] type 01 class 0x060400
[    0.567743] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.567777] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.567798] pci 0000:00:1c.1: [8086:1d12] type 01 class 0x060400
[    0.567864] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.567899] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.567918] pci 0000:00:1c.2: [8086:1d14] type 01 class 0x060400
[    0.567985] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.568019] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.568039] pci 0000:00:1c.3: [8086:1d16] type 01 class 0x060400
[    0.568105] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.568140] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.568160] pci 0000:00:1c.4: [8086:1d18] type 01 class 0x060400
[    0.568226] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.568261] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.568280] pci 0000:00:1c.5: [8086:1d1a] type 01 class 0x060400
[    0.568347] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.568381] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.568405] pci 0000:00:1d.0: [8086:1d26] type 00 class 0x0c0320
[    0.568423] pci 0000:00:1d.0: reg 0x10: [mem 0xf9126000-0xf91263ff]
[    0.568500] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.568533] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.568550] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.568615] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.568636] pci 0000:00:1f.0: [8086:1d41] type 00 class 0x060100
[    0.568775] pci 0000:00:1f.2: [8086:1d02] type 00 class 0x010601
[    0.568789] pci 0000:00:1f.2: reg 0x10: [io  0xf090-0xf097]
[    0.568795] pci 0000:00:1f.2: reg 0x14: [io  0xf080-0xf083]
[    0.568801] pci 0000:00:1f.2: reg 0x18: [io  0xf070-0xf077]
[    0.568807] pci 0000:00:1f.2: reg 0x1c: [io  0xf060-0xf063]
[    0.568813] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.568819] pci 0000:00:1f.2: reg 0x24: [mem 0xf9125000-0xf91257ff]
[    0.568855] pci 0000:00:1f.2: PME# supported from D3hot
[    0.568900] pci 0000:00:1f.3: [8086:1d22] type 00 class 0x0c0500
[    0.568912] pci 0000:00:1f.3: reg 0x10: [mem 0xf9124000-0xf91240ff 64bit]
[    0.568929] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.569011] pci 0000:00:01.0: PCI bridge to [bus 03]
[    0.569056] pci 0000:01:00.0: [10de:1080] type 00 class 0x030000
[    0.569062] pci 0000:01:00.0: reg 0x10: [mem 0xfa000000-0xfaffffff]
[    0.569069] pci 0000:01:00.0: reg 0x14: [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.569075] pci 0000:01:00.0: reg 0x1c: [mem 0xd8000000-0xd9ffffff 64bit pref]
[    0.569080] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.569085] pci 0000:01:00.0: reg 0x30: [mem 0xfb000000-0xfb07ffff pref]
[    0.569132] pci 0000:01:00.1: [10de:0e09] type 00 class 0x040300
[    0.569139] pci 0000:01:00.1: reg 0x10: [mem 0xfb080000-0xfb083fff]
[    0.574664] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.574672] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.574687] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfb0fffff]
[    0.574691] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.574730] pci 0000:02:00.0: [10de:1080] type 00 class 0x030000
[    0.574736] pci 0000:02:00.0: reg 0x10: [mem 0xf8000000-0xf8ffffff]
[    0.574742] pci 0000:02:00.0: reg 0x14: [mem 0xc0000000-0xc7ffffff 64bit pref]
[    0.574748] pci 0000:02:00.0: reg 0x1c: [mem 0xc8000000-0xc9ffffff 64bit pref]
[    0.574751] pci 0000:02:00.0: reg 0x24: [io  0xd000-0xd07f]
[    0.574755] pci 0000:02:00.0: reg 0x30: [mem 0xf9000000-0xf907ffff pref]
[    0.574807] pci 0000:02:00.1: [10de:0e09] type 00 class 0x040300
[    0.574813] pci 0000:02:00.1: reg 0x10: [mem 0xf9080000-0xf9083fff]
[    0.582667] pci 0000:00:03.0: PCI bridge to [bus 02]
[    0.582675] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    0.582680] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xf90fffff]
[    0.582696] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xc9ffffff 64bit pref]
[    0.582741] pci 0000:00:11.0: PCI bridge to [bus 04]
[    0.582791] pci 0000:00:1c.0: PCI bridge to [bus 05]
[    0.582863] pci 0000:06:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.582890] pci 0000:06:00.0: reg 0x10: [mem 0xfb600000-0xfb607fff 64bit]
[    0.583027] pci 0000:06:00.0: PME# supported from D3hot D3cold
[    0.590677] pci 0000:00:1c.1: PCI bridge to [bus 06]
[    0.590697] pci 0000:00:1c.1:   bridge window [mem 0xfb600000-0xfb6fffff]
[    0.590768] pci 0000:07:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.590795] pci 0000:07:00.0: reg 0x10: [mem 0xfb500000-0xfb507fff 64bit]
[    0.590932] pci 0000:07:00.0: PME# supported from D3hot D3cold
[    0.598682] pci 0000:00:1c.2: PCI bridge to [bus 07]
[    0.598704] pci 0000:00:1c.2:   bridge window [mem 0xfb500000-0xfb5fffff]
[    0.598774] pci 0000:08:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.598801] pci 0000:08:00.0: reg 0x10: [mem 0xfb400000-0xfb407fff 64bit]
[    0.598938] pci 0000:08:00.0: PME# supported from D3hot D3cold
[    0.606686] pci 0000:00:1c.3: PCI bridge to [bus 08]
[    0.606708] pci 0000:00:1c.3:   bridge window [mem 0xfb400000-0xfb4fffff]
[    0.606772] pci 0000:09:00.0: [1b21:0612] type 00 class 0x010601
[    0.606789] pci 0000:09:00.0: reg 0x10: [io  0xc050-0xc057]
[    0.606801] pci 0000:09:00.0: reg 0x14: [io  0xc040-0xc043]
[    0.606813] pci 0000:09:00.0: reg 0x18: [io  0xc030-0xc037]
[    0.606825] pci 0000:09:00.0: reg 0x1c: [io  0xc020-0xc023]
[    0.606837] pci 0000:09:00.0: reg 0x20: [io  0xc000-0xc01f]
[    0.606849] pci 0000:09:00.0: reg 0x24: [mem 0xfb300000-0xfb3001ff]
[    0.614690] pci 0000:00:1c.4: PCI bridge to [bus 09]
[    0.614699] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.614714] pci 0000:00:1c.4:   bridge window [mem 0xfb300000-0xfb3fffff]
[    0.614778] pci 0000:0a:00.0: [1106:3403] type 00 class 0x0c0010
[    0.614803] pci 0000:0a:00.0: reg 0x10: [mem 0xfb200000-0xfb2007ff 64bit]
[    0.614816] pci 0000:0a:00.0: reg 0x18: [io  0xb000-0xb0ff]
[    0.614924] pci 0000:0a:00.0: supports D2
[    0.614925] pci 0000:0a:00.0: PME# supported from D2 D3hot D3cold
[    0.622698] pci 0000:00:1c.5: PCI bridge to [bus 0a]
[    0.622717] pci 0000:00:1c.5:   bridge window [io  0xb000-0xbfff]
[    0.622720] pci 0000:00:1c.5:   bridge window [mem 0xfb200000-0xfb2fffff]
[    0.622778] pci 0000:00:1e.0: PCI bridge to [bus 0b] (subtractive decode)
[    0.622786] pci 0000:00:1e.0:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.622787] pci 0000:00:1e.0:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.622788] pci 0000:00:1e.0:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.622789] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.622790] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.622791] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.622792] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.623085] ACPI: PCI Root Bridge [UNC0] (domain 0000 [bus ff])
[    0.623088] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.623102] acpi PNP0A03:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.623129] PCI host bridge to bus 0000:ff
[    0.623131] pci_bus 0000:ff: root bus resource [bus ff]
[    0.623138] pci 0000:ff:08.0: [8086:3c80] type 00 class 0x088000
[    0.623169] pci 0000:ff:08.3: [8086:3c83] type 00 class 0x088000
[    0.623206] pci 0000:ff:08.4: [8086:3c84] type 00 class 0x088000
[    0.623248] pci 0000:ff:09.0: [8086:3c90] type 00 class 0x088000
[    0.623278] pci 0000:ff:09.3: [8086:3c93] type 00 class 0x088000
[    0.623315] pci 0000:ff:09.4: [8086:3c94] type 00 class 0x088000
[    0.623356] pci 0000:ff:0a.0: [8086:3cc0] type 00 class 0x088000
[    0.623380] pci 0000:ff:0a.1: [8086:3cc1] type 00 class 0x088000
[    0.623404] pci 0000:ff:0a.2: [8086:3cc2] type 00 class 0x088000
[    0.623427] pci 0000:ff:0a.3: [8086:3cd0] type 00 class 0x088000
[    0.623453] pci 0000:ff:0b.0: [8086:3ce0] type 00 class 0x088000
[    0.623475] pci 0000:ff:0b.3: [8086:3ce3] type 00 class 0x088000
[    0.623499] pci 0000:ff:0c.0: [8086:3ce8] type 00 class 0x088000
[    0.623521] pci 0000:ff:0c.1: [8086:3ce8] type 00 class 0x088000
[    0.623544] pci 0000:ff:0c.6: [8086:3cf4] type 00 class 0x088000
[    0.623566] pci 0000:ff:0c.7: [8086:3cf6] type 00 class 0x088000
[    0.623588] pci 0000:ff:0d.0: [8086:3ce8] type 00 class 0x088000
[    0.623612] pci 0000:ff:0d.1: [8086:3ce8] type 00 class 0x088000
[    0.623635] pci 0000:ff:0d.6: [8086:3cf5] type 00 class 0x088000
[    0.623658] pci 0000:ff:0e.0: [8086:3ca0] type 00 class 0x088000
[    0.623682] pci 0000:ff:0e.1: [8086:3c46] type 00 class 0x110100
[    0.623712] pci 0000:ff:0f.0: [8086:3ca8] type 00 class 0x088000
[    0.623743] pci 0000:ff:0f.1: [8086:3c71] type 00 class 0x088000
[    0.623774] pci 0000:ff:0f.2: [8086:3caa] type 00 class 0x088000
[    0.623805] pci 0000:ff:0f.3: [8086:3cab] type 00 class 0x088000
[    0.623836] pci 0000:ff:0f.4: [8086:3cac] type 00 class 0x088000
[    0.623867] pci 0000:ff:0f.5: [8086:3cad] type 00 class 0x088000
[    0.623897] pci 0000:ff:0f.6: [8086:3cae] type 00 class 0x088000
[    0.623924] pci 0000:ff:10.0: [8086:3cb0] type 00 class 0x088000
[    0.623956] pci 0000:ff:10.1: [8086:3cb1] type 00 class 0x088000
[    0.623988] pci 0000:ff:10.2: [8086:3cb2] type 00 class 0x088000
[    0.624019] pci 0000:ff:10.3: [8086:3cb3] type 00 class 0x088000
[    0.624050] pci 0000:ff:10.4: [8086:3cb4] type 00 class 0x088000
[    0.624082] pci 0000:ff:10.5: [8086:3cb5] type 00 class 0x088000
[    0.624114] pci 0000:ff:10.6: [8086:3cb6] type 00 class 0x088000
[    0.624145] pci 0000:ff:10.7: [8086:3cb7] type 00 class 0x088000
[    0.624176] pci 0000:ff:11.0: [8086:3cb8] type 00 class 0x088000
[    0.624205] pci 0000:ff:13.0: [8086:3ce4] type 00 class 0x088000
[    0.624227] pci 0000:ff:13.1: [8086:3c43] type 00 class 0x110100
[    0.624250] pci 0000:ff:13.4: [8086:3ce6] type 00 class 0x110100
[    0.624273] pci 0000:ff:13.5: [8086:3c44] type 00 class 0x110100
[    0.624297] pci 0000:ff:13.6: [8086:3c45] type 00 class 0x088000
[    0.624364] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.624397] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.624429] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 *15)
[    0.624461] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 *14 15)
[    0.624492] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.624524] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.624557] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.624589] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.626654] ACPI: Enabled 2 GPEs in block 00 to 3F
[    0.626659] ACPI: \_SB_.PCI0: notify handler is installed
[    0.626682] ACPI: \_SB_.UNC0: notify handler is installed
[    0.626742] Found 2 acpi root devices
[    0.626755] ACPI : EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    0.626823] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.626826] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.626829] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
[    0.626834] vgaarb: loaded
[    0.626835] vgaarb: bridge control possible 0000:02:00.0
[    0.626836] vgaarb: bridge control possible 0000:01:00.0
[    0.626929] SCSI subsystem initialized
[    0.626971] libata version 3.00 loaded.
[    0.626981] ACPI: bus type USB registered
[    0.626993] usbcore: registered new interface driver usbfs
[    0.626999] usbcore: registered new interface driver hub
[    0.627013] usbcore: registered new device driver usb
[    0.627078] PCI: Using ACPI for IRQ routing
[    0.632320] PCI: pci_cache_line_size set to 64 bytes
[    0.632413] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
[    0.632414] e820: reserve RAM buffer [mem 0xbbf60000-0xbbffffff]
[    0.632415] e820: reserve RAM buffer [mem 0xbd71a000-0xbfffffff]
[    0.632416] e820: reserve RAM buffer [mem 0xbdbdb000-0xbfffffff]
[    0.632416] e820: reserve RAM buffer [mem 0xbe000000-0xbfffffff]
[    0.632471] NetLabel: Initializing
[    0.632472] NetLabel:  domain hash size = 128
[    0.632473] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.632483] NetLabel:  unlabeled traffic allowed by default
[    0.632517] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.632521] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.634551] Switched to clocksource hpet
[    0.637319] AppArmor: AppArmor Filesystem Enabled
[    0.637331] pnp: PnP ACPI init
[    0.637337] ACPI: bus type PNP registered
[    0.637400] system 00:00: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.637402] system 00:00: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.637404] system 00:00: [mem 0xfe000000-0xfeafffff] has been reserved
[    0.637406] system 00:00: [mem 0xfeb00000-0xfebfffff] has been reserved
[    0.637408] system 00:00: [mem 0xfed00400-0xfed3ffff] could not be reserved
[    0.637410] system 00:00: [mem 0xfed45000-0xfedfffff] has been reserved
[    0.637411] system 00:00: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.637414] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.637479] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.637482] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.637488] pnp 00:02: [dma 4]
[    0.637496] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.637514] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.637523] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.637560] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.637562] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.637576] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.637693] pnp 00:07: [dma 0 disabled]
[    0.637721] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.637835] system 00:08: [io  0x0400-0x0453] could not be reserved
[    0.637837] system 00:08: [io  0x0458-0x047f] has been reserved
[    0.637839] system 00:08: [io  0x1180-0x119f] has been reserved
[    0.637841] system 00:08: [io  0x0500-0x057f] has been reserved
[    0.637843] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.637845] system 00:08: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.637847] system 00:08: [mem 0xff000000-0xffffffff] has been reserved
[    0.637849] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.637886] system 00:09: [io  0x0454-0x0457] has been reserved
[    0.637889] system 00:09: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.637953] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.638087] pnp: PnP ACPI: found 11 devices
[    0.638089] ACPI: bus type PNP unregistered
[    0.643746] pci 0000:00:01.0: PCI bridge to [bus 03]
[    0.643754] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.643756] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.643760] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfb0fffff]
[    0.643763] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.643768] pci 0000:00:03.0: PCI bridge to [bus 02]
[    0.643770] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    0.643774] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xf90fffff]
[    0.643777] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xc9ffffff 64bit pref]
[    0.643781] pci 0000:00:11.0: PCI bridge to [bus 04]
[    0.643792] pci 0000:00:1c.0: PCI bridge to [bus 05]
[    0.643801] pci 0000:00:1c.1: PCI bridge to [bus 06]
[    0.643806] pci 0000:00:1c.1:   bridge window [mem 0xfb600000-0xfb6fffff]
[    0.643812] pci 0000:00:1c.2: PCI bridge to [bus 07]
[    0.643817] pci 0000:00:1c.2:   bridge window [mem 0xfb500000-0xfb5fffff]
[    0.643823] pci 0000:00:1c.3: PCI bridge to [bus 08]
[    0.643827] pci 0000:00:1c.3:   bridge window [mem 0xfb400000-0xfb4fffff]
[    0.643834] pci 0000:00:1c.4: PCI bridge to [bus 09]
[    0.643837] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.643841] pci 0000:00:1c.4:   bridge window [mem 0xfb300000-0xfb3fffff]
[    0.643848] pci 0000:00:1c.5: PCI bridge to [bus 0a]
[    0.643850] pci 0000:00:1c.5:   bridge window [io  0xb000-0xbfff]
[    0.643854] pci 0000:00:1c.5:   bridge window [mem 0xfb200000-0xfb2fffff]
[    0.643861] pci 0000:00:1e.0: PCI bridge to [bus 0b]
[    0.643870] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.643871] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.643872] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.643873] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.643874] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.643875] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.643876] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
[    0.643877] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.643878] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfb0fffff]
[    0.643879] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.643880] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.643881] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xf90fffff]
[    0.643882] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc9ffffff 64bit pref]
[    0.643883] pci_bus 0000:06: resource 1 [mem 0xfb600000-0xfb6fffff]
[    0.643885] pci_bus 0000:07: resource 1 [mem 0xfb500000-0xfb5fffff]
[    0.643886] pci_bus 0000:08: resource 1 [mem 0xfb400000-0xfb4fffff]
[    0.643887] pci_bus 0000:09: resource 0 [io  0xc000-0xcfff]
[    0.643888] pci_bus 0000:09: resource 1 [mem 0xfb300000-0xfb3fffff]
[    0.643889] pci_bus 0000:0a: resource 0 [io  0xb000-0xbfff]
[    0.643890] pci_bus 0000:0a: resource 1 [mem 0xfb200000-0xfb2fffff]
[    0.643891] pci_bus 0000:0b: resource 4 [io  0x0000-0x03af]
[    0.643892] pci_bus 0000:0b: resource 5 [io  0x03e0-0x0cf7]
[    0.643893] pci_bus 0000:0b: resource 6 [io  0x03b0-0x03df]
[    0.643894] pci_bus 0000:0b: resource 7 [io  0x0d00-0xffff]
[    0.643895] pci_bus 0000:0b: resource 8 [mem 0x000a0000-0x000bffff]
[    0.643896] pci_bus 0000:0b: resource 9 [mem 0x000c0000-0x000dffff]
[    0.643897] pci_bus 0000:0b: resource 10 [mem 0xc0000000-0xffffffff]
[    0.643916] NET: Registered protocol family 2
[    0.644109] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.644392] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.644480] TCP: Hash tables configured (established 262144 bind 65536)
[    0.644495] TCP: reno registered
[    0.644519] UDP hash table entries: 16384 (order: 7, 524288 bytes)
[    0.644596] UDP-Lite hash table entries: 16384 (order: 7, 524288 bytes)
[    0.644681] NET: Registered protocol family 1
[    0.682642] pci 0000:01:00.0: Video device with shadowed ROM
[    0.682979] PCI: CLS 64 bytes, default 64
[    0.683014] Trying to unpack rootfs image as initramfs...
[    0.960836] Freeing initrd memory: 27384K (ffff880034a74000 - ffff880036532000)
[    0.960844] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.960846] software IO TLB [mem 0xb7f60000-0xbbf60000] (64MB) mapped at [ffff8800b7f60000-ffff8800bbf5ffff]
[    0.961177] microcode: CPU0 sig=0x206d7, pf=0x4, revision=0x705
[    0.961181] microcode: CPU1 sig=0x206d7, pf=0x4, revision=0x705
[    0.961187] microcode: CPU2 sig=0x206d7, pf=0x4, revision=0x705
[    0.961193] microcode: CPU3 sig=0x206d7, pf=0x4, revision=0x705
[    0.961199] microcode: CPU4 sig=0x206d7, pf=0x4, revision=0x705
[    0.961204] microcode: CPU5 sig=0x206d7, pf=0x4, revision=0x705
[    0.961210] microcode: CPU6 sig=0x206d7, pf=0x4, revision=0x705
[    0.961215] microcode: CPU7 sig=0x206d7, pf=0x4, revision=0x705
[    0.961252] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.961255] Scanning for low memory corruption every 60 seconds
[    0.961413] Initialise system trusted keyring
[    0.961443] audit: initializing netlink socket (disabled)
[    0.961455] type=2000 audit(1434023360.668:1): initialized
[    0.978365] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.979339] zbud: loaded
[    0.979431] VFS: Disk quotas dquot_6.5.2
[    0.979455] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.979670] fuse init (API version 7.22)
[    0.979709] msgmni has been set to 32768
[    0.979737] Key type big_key registered
[    0.980031] Key type asymmetric registered
[    0.980033] Asymmetric key parser 'x509' registered
[    0.980049] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.980080] io scheduler noop registered
[    0.980081] io scheduler deadline registered (default)
[    0.980093] io scheduler cfq registered
[    0.980799] ioapic: probe of 0000:00:05.4 failed with error -22
[    0.980805] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.980813] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.980839] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    0.980841] vesafb: scrolling: redraw
[    0.980842] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.986592] vesafb: framebuffer at 0xd9000000, mapped to 0xffffc90013700000, using 5120k, total 5120k
[    0.990315] Console: switching to colour frame buffer device 160x64
[    0.993991] fb0: VESA VGA frame buffer device
[    0.994022] intel_idle: MWAIT substates: 0x21120
[    0.994023] intel_idle: v0.4 model 0x2D
[    0.994024] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.994131] ipmi message handler version 39.2
[    0.994196] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.994233] ACPI: Power Button [PWRB]
[    0.994268] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.994300] ACPI: Power Button [PWRF]
[    0.999643] GHES: HEST is not enabled!
[    0.999723] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.020131] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.020912] Linux agpgart interface v0.103
[    1.021578] brd: module loaded
[    1.021899] loop: module loaded
[    1.022118] libphy: Fixed MDIO Bus: probed
[    1.022177] tun: Universal TUN/TAP device driver, 1.6
[    1.022198] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.022244] PPP generic driver version 2.4.2
[    1.022283] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.022312] ehci-pci: EHCI PCI platform driver
[    1.022419] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.022444] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.022485] ehci-pci 0000:00:1a.0: debug port 2
[    1.026410] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.026421] ehci-pci 0000:00:1a.0: irq 23, io mem 0xf9127000
[    1.034574] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.034623] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.034652] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.034683] usb usb1: Product: EHCI Host Controller
[    1.034703] usb usb1: Manufacturer: Linux 3.13.0-53-generic ehci_hcd
[    1.034730] usb usb1: SerialNumber: 0000:00:1a.0
[    1.034833] hub 1-0:1.0: USB hub found
[    1.034852] hub 1-0:1.0: 2 ports detected
[    1.034984] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.035010] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.035050] ehci-pci 0000:00:1d.0: debug port 2
[    1.038952] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.038957] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf9126000
[    1.050572] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.050617] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.050646] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.050677] usb usb2: Product: EHCI Host Controller
[    1.050697] usb usb2: Manufacturer: Linux 3.13.0-53-generic ehci_hcd
[    1.051866] usb usb2: SerialNumber: 0000:00:1d.0
[    1.053109] hub 2-0:1.0: USB hub found
[    1.054264] hub 2-0:1.0: 2 ports detected
[    1.055466] ehci-platform: EHCI generic platform driver
[    1.056619] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.057771] ohci-pci: OHCI PCI platform driver
[    1.058926] ohci-platform: OHCI generic platform driver
[    1.060079] uhci_hcd: USB Universal Host Controller Interface driver
[    1.061297] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.062469] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 3
[    1.175550] xhci_hcd 0000:06:00.0: irq 64 for MSI/MSI-X
[    1.175554] xhci_hcd 0000:06:00.0: irq 65 for MSI/MSI-X
[    1.175557] xhci_hcd 0000:06:00.0: irq 66 for MSI/MSI-X
[    1.175560] xhci_hcd 0000:06:00.0: irq 67 for MSI/MSI-X
[    1.175563] xhci_hcd 0000:06:00.0: irq 68 for MSI/MSI-X
[    1.175566] xhci_hcd 0000:06:00.0: irq 69 for MSI/MSI-X
[    1.175569] xhci_hcd 0000:06:00.0: irq 70 for MSI/MSI-X
[    1.175572] xhci_hcd 0000:06:00.0: irq 71 for MSI/MSI-X
[    1.175676] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.176859] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.178034] usb usb3: Product: xHCI Host Controller
[    1.179213] usb usb3: Manufacturer: Linux 3.13.0-53-generic xhci_hcd
[    1.180399] usb usb3: SerialNumber: 0000:06:00.0
[    1.181655] hub 3-0:1.0: USB hub found
[    1.182843] hub 3-0:1.0: 2 ports detected
[    1.184055] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.185224] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 4
[    1.186433] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.187614] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.188795] usb usb4: Product: xHCI Host Controller
[    1.189966] usb usb4: Manufacturer: Linux 3.13.0-53-generic xhci_hcd
[    1.191138] usb usb4: SerialNumber: 0000:06:00.0
[    1.192362] hub 4-0:1.0: USB hub found
[    1.193514] hub 4-0:1.0: 2 ports detected
[    1.202629] xhci_hcd 0000:07:00.0: xHCI Host Controller
[    1.203767] xhci_hcd 0000:07:00.0: new USB bus registered, assigned bus number 5
[    1.264289] xhci_hcd 0000:07:00.0: irq 72 for MSI/MSI-X
[    1.264292] xhci_hcd 0000:07:00.0: irq 73 for MSI/MSI-X
[    1.264295] xhci_hcd 0000:07:00.0: irq 74 for MSI/MSI-X
[    1.264298] xhci_hcd 0000:07:00.0: irq 75 for MSI/MSI-X
[    1.264302] xhci_hcd 0000:07:00.0: irq 76 for MSI/MSI-X
[    1.264304] xhci_hcd 0000:07:00.0: irq 77 for MSI/MSI-X
[    1.264307] xhci_hcd 0000:07:00.0: irq 78 for MSI/MSI-X
[    1.264310] xhci_hcd 0000:07:00.0: irq 79 for MSI/MSI-X
[    1.264411] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    1.265541] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.266666] usb usb5: Product: xHCI Host Controller
[    1.267788] usb usb5: Manufacturer: Linux 3.13.0-53-generic xhci_hcd
[    1.268916] usb usb5: SerialNumber: 0000:07:00.0
[    1.270130] hub 5-0:1.0: USB hub found
[    1.271241] hub 5-0:1.0: 2 ports detected
[    1.272382] xhci_hcd 0000:07:00.0: xHCI Host Controller
[    1.273490] xhci_hcd 0000:07:00.0: new USB bus registered, assigned bus number 6
[    1.274647] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[    1.275776] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.276904] usb usb6: Product: xHCI Host Controller
[    1.278023] usb usb6: Manufacturer: Linux 3.13.0-53-generic xhci_hcd
[    1.279149] usb usb6: SerialNumber: 0000:07:00.0
[    1.280364] hub 6-0:1.0: USB hub found
[    1.281481] hub 6-0:1.0: 2 ports detected
[    1.286635] xhci_hcd 0000:08:00.0: xHCI Host Controller
[    1.287745] xhci_hcd 0000:08:00.0: new USB bus registered, assigned bus number 7
[    1.346624] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.348270] xhci_hcd 0000:08:00.0: irq 80 for MSI/MSI-X
[    1.348274] xhci_hcd 0000:08:00.0: irq 81 for MSI/MSI-X
[    1.348277] xhci_hcd 0000:08:00.0: irq 82 for MSI/MSI-X
[    1.348280] xhci_hcd 0000:08:00.0: irq 83 for MSI/MSI-X
[    1.348283] xhci_hcd 0000:08:00.0: irq 84 for MSI/MSI-X
[    1.348286] xhci_hcd 0000:08:00.0: irq 85 for MSI/MSI-X
[    1.348288] xhci_hcd 0000:08:00.0: irq 86 for MSI/MSI-X
[    1.348291] xhci_hcd 0000:08:00.0: irq 87 for MSI/MSI-X
[    1.348397] usb usb7: New USB device found, idVendor=1d6b, idProduct=0002
[    1.349532] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.350674] usb usb7: Product: xHCI Host Controller
[    1.351800] usb usb7: Manufacturer: Linux 3.13.0-53-generic xhci_hcd
[    1.352935] usb usb7: SerialNumber: 0000:08:00.0
[    1.354161] hub 7-0:1.0: USB hub found
[    1.355297] hub 7-0:1.0: 2 ports detected
[    1.356471] xhci_hcd 0000:08:00.0: xHCI Host Controller
[    1.357604] xhci_hcd 0000:08:00.0: new USB bus registered, assigned bus number 8
[    1.358780] usb usb8: New USB device found, idVendor=1d6b, idProduct=0003
[    1.359927] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.361083] usb usb8: Product: xHCI Host Controller
[    1.362240] usb usb8: Manufacturer: Linux 3.13.0-53-generic xhci_hcd
[    1.363401] usb usb8: SerialNumber: 0000:08:00.0
[    1.364641] hub 8-0:1.0: USB hub found
[    1.365791] hub 8-0:1.0: 2 ports detected
[    1.374663] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.378715] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.379870] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.381177] mousedev: PS/2 mouse device common for all mice
[    1.382556] rtc_cmos 00:03: RTC can wake from S4
[    1.383858] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.385029] rtc_cmos 00:03: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.386223] device-mapper: uevent: version 1.0.3
[    1.387442] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.388617] ledtrig-cpu: registered to indicate activity on CPUs
[    1.389851] TCP: cubic registered
[    1.391053] NET: Registered protocol family 10
[    1.392297] NET: Registered protocol family 17
[    1.393454] Key type dns_resolver registered
[    1.394818] Loading compiled-in X.509 certificates
[    1.396528] Loaded X.509 cert 'Magrathea: Glacier signing key: 9aac900abd0220fb93c8be10f20d6973dab829f5'
[    1.397709] registered taskstats version 1
[    1.400680] Key type trusted registered
[    1.404876] Key type encrypted registered
[    1.406043] AppArmor: AppArmor sha1 policy hashing enabled
[    1.407212] IMA: No TPM chip found, activating TPM-bypass!
[    1.408818] regulator-dummy: disabling
[    1.410084]   Magic number: 3:778:832
[    1.411344] rtc_cmos 00:03: setting system clock to 2015-06-11 11:49:22 UTC (1434023362)
[    1.413364] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.414545] EDD information not available.
[    1.415752] PM: Hibernation image not present or could not be loaded.
[    1.416685] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.417895] Write protecting the kernel read-only data: 12288k
[    1.420427] Freeing unused kernel memory: 788K (ffff88000173b000 - ffff880001800000)
[    1.422743] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.433692] systemd-udevd[145]: starting version 204
[    1.440624] wmi: Mapper loaded
[    1.443187] pps_core: LinuxPPS API ver. 1 registered
[    1.444403] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.446605] PTP clock support registered
[    1.450198] ahci 0000:00:1f.2: version 3.0
[    1.450326] ahci 0000:00:1f.2: irq 88 for MSI/MSI-X
[    1.451812] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    1.453115] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    1.463054] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x29 impl SATA mode
[    1.464338] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.479047] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.479061] scsi0 : ahci
[    1.479163] scsi1 : ahci
[    1.479248] scsi2 : ahci
[    1.479338] scsi3 : ahci
[    1.479438] scsi4 : ahci
[    1.479527] scsi5 : ahci
[    1.479555] ata1: SATA max UDMA/133 abar m2048@0xf9125000 port 0xf9125100 irq 88
[    1.479555] ata2: DUMMY
[    1.479556] ata3: DUMMY
[    1.479558] ata4: SATA max UDMA/133 abar m2048@0xf9125000 port 0xf9125280 irq 88
[    1.479559] ata5: DUMMY
[    1.479560] ata6: SATA max UDMA/133 abar m2048@0xf9125000 port 0xf9125380 irq 88
[    1.479663] ahci 0000:09:00.0: irq 89 for MSI/MSI-X
[    1.479696] ahci 0000:09:00.0: SSS flag set, parallel bus scan disabled
[    1.479751] ahci 0000:09:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.479752] ahci 0000:09:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc 
[    1.479762] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.479787] e1000e 0000:00:19.0: irq 90 for MSI/MSI-X
[    1.479951] scsi6 : ahci
[    1.480001] scsi7 : ahci
[    1.480030] ata7: SATA max UDMA/133 abar m512@0xfb300000 port 0xfb300100 irq 89
[    1.480033] ata8: SATA max UDMA/133 abar m512@0xfb300000 port 0xfb300180 irq 89
[    1.504677] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.506149] hub 1-1:1.0: USB hub found
[    1.507499] hub 1-1:1.0: 6 ports detected
[    1.514665] firewire_ohci 0000:0a:00.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    1.618610] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.747550] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.748830] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 74:d0:2b:2b:cf:43
[    1.750118] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.751030] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.751031] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.751284] hub 2-1:1.0: USB hub found
[    1.751405] hub 2-1:1.0: 8 ports detected
[    1.756534] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    1.798619] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.799917] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.801207] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.802510] ata1.00: ATA-9: SanDisk SDSSDHII240G, X31200RL, max UDMA/133
[    1.803792] ata1.00: 468862128 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.803841] ata7: SATA link down (SStatus 0 SControl 300)
[    1.806325] ata6.00: ATAPI: TSSTcorp CDDVDW TS-H663C, UO00, max UDMA/100
[    1.807591] ata4.00: ATA-8: WDC WD5002AALX-00J37A0, 15.01H15, max UDMA/133
[    1.808863] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.811390] ata4.00: configured for UDMA/133
[    1.812705] ata1.00: configured for UDMA/133
[    1.814094] scsi 0:0:0:0: Direct-Access     ATA      SanDisk SDSSDHII X312 PQ: 0 ANSI: 5
[    1.815478] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/223 GiB)
[    1.815505] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.815698] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5002AALX-0 15.0 PQ: 0 ANSI: 5
[    1.815775] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.815787] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.815804] sd 3:0:0:0: [sdb] Write Protect is off
[    1.815805] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.815813] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.824363] sd 0:0:0:0: [sda] Write Protect is off
[    1.825619] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.825628] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.827280]  sda: sda1 sda2
[    1.828752] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.853043]  sdb: sdb1 sdb2 < sdb5 >
[    1.854581] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.958638] tsc: Refined TSC clocksource calibration: 3806.814 MHz
[    1.975431] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
[    1.991212] usb 4-1: Parent hub missing LPM exit latency info.  Power management will be impacted.
[    1.993451] usb 4-1: New USB device found, idVendor=13fe, idProduct=5200
[    1.994722] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.995975] usb 4-1: Product: USB DISK 3.0
[    1.997216] usb 4-1: Manufacturer:         
[    1.998461] usb 4-1: SerialNumber: 070B329A8681CA10
[    2.002487] usb-storage 4-1:1.0: USB Mass Storage device detected
[    2.003904] scsi8 : usb-storage 4-1:1.0
[    2.005223] usbcore: registered new interface driver usb-storage
[    2.014697] firewire_core 0000:0a:00.0: created device fw0: GUID 001e8c000063d1b5, S400
[    2.070644] usb 1-1.2: new full-speed USB device number 3 using ehci-pci
[    2.165894] usb 1-1.2: New USB device found, idVendor=046d, idProduct=c52b
[    2.167242] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.168580] usb 1-1.2: Product: USB Receiver
[    2.169906] usb 1-1.2: Manufacturer: Logitech
[    2.173835] hidraw: raw HID events driver (C) Jiri Kosina
[    2.180284] usbcore: registered new interface driver usbhid
[    2.181591] usbhid: USB HID core driver
[    2.185074] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.2/input2
[    2.188850] input: Logitech Unifying Device. Wireless PID:101b as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:046D:C52B.0003/input/input5
[    2.190305] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101b] on usb-0000:00:1a.0-1.2:1
[    2.191862] input: Logitech Unifying Device. Wireless PID:200a as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:046D:C52B.0003/input/input6
[    2.193482] logitech-djdevice 0003:046D:C52B.0005: input,hidraw2: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:200a] on usb-0000:00:1a.0-1.2:2
[    2.242832] usb 2-1.5: new full-speed USB device number 3 using ehci-pci
[    2.340283] usb 2-1.5: New USB device found, idVendor=056a, idProduct=0017
[    2.341824] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.343332] usb 2-1.5: Product: CTE-450
[    2.344804] usb 2-1.5: Manufacturer: Wacom Co.,Ltd.
[    2.418831] usb 2-1.6: new high-speed USB device number 4 using ehci-pci
[    2.528343] usb 2-1.6: New USB device found, idVendor=148f, idProduct=2070
[    2.529819] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.531294] usb 2-1.6: Product: 802.11 g WLAN
[    2.532757] usb 2-1.6: Manufacturer: Ralink
[    2.534209] usb 2-1.6: SerialNumber: 1.0
[    2.605097] ata6.00: configured for UDMA/100
[    2.958779] Switched to clocksource tsc
[    3.003111] scsi 8:0:0:0: Direct-Access              USB DISK 3.0     PMAP PQ: 0 ANSI: 6
[    3.004770] sd 8:0:0:0: Attached scsi generic sg2 type 0
[    3.005006] sd 8:0:0:0: [sdc] 123535360 512-byte logical blocks: (63.2 GB/58.9 GiB)
[    3.005965] sd 8:0:0:0: [sdc] Write Protect is off
[    3.005967] sd 8:0:0:0: [sdc] Mode Sense: 45 00 00 00
[    3.006939] sd 8:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.012136]  sdc: sdc1 sdc2 < sdc5 >
[    3.016528] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[    3.406960] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H663C  UO00 PQ: 0 ANSI: 5
[    3.412336] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.413847] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.415421] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    3.415457] sr 5:0:0:0: Attached scsi generic sg3 type 5
[    3.734709] ata8: SATA link down (SStatus 0 SControl 300)
[    6.466870] random: nonblocking pool is initialized
[    6.558744] raid6: sse2x1   10894 MB/s
[    6.626745] raid6: sse2x2   13471 MB/s
[    6.694746] raid6: sse2x4   15533 MB/s
[    6.694760] raid6: using algorithm sse2x4 (15533 MB/s)
[    6.694781] raid6: using ssse3x2 recovery algorithm
[    6.695513] xor: automatically using best checksumming function:
[    6.734748]    avx       : 30707.000 MB/sec
[    6.742587] bio: create slab <bio-1> at 1
[    6.742712] Btrfs loaded
[    6.854818] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    7.057299] Adding 9869308k swap on /dev/sdb5.  Priority:-1 extents:1 across:9869308k FS
[    7.099782] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.125409] systemd-udevd[445]: starting version 204
[    7.141596] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.143343] mei_me 0000:00:16.0: irq 91 for MSI/MSI-X
[    7.147889] [drm] Initialized drm 1.1.0 20060810
[    7.149969] lp: driver loaded but no devices found
[    7.150247] nvidia: module license 'NVIDIA' taints kernel.
[    7.150249] Disabling lock debugging due to kernel taint
[    7.152613] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    7.158198] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    7.158443] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[    7.158477] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[    7.158921] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[    7.158985] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:02:00.0 on minor 1
[    7.158996] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.72  Tue May  5 22:03:13 PDT 2015
[    7.161212] ppdev: user-space parallel port driver
[    7.174424] snd_hda_intel 0000:00:1b.0: irq 92 for MSI/MSI-X
[    7.185242] SKU: Nid=0x1d sku_cfg=0x4005e601
[    7.185244] SKU: port_connectivity=0x1
[    7.185244] SKU: enable_pcbeep=0x0
[    7.185245] SKU: check_sum=0x00000005
[    7.185246] SKU: customization=0x000000e6
[    7.185246] SKU: external_amp=0x0
[    7.185247] SKU: platform_type=0x0
[    7.185247] SKU: swap=0x0
[    7.185248] SKU: override=0x1
[    7.185700] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[    7.185702]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    7.185703]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    7.185704]    mono: mono_out=0x0
[    7.185704]    dig-out=0x11/0x1e
[    7.185705]    inputs:
[    7.185706]      Front Mic=0x19
[    7.185707]      Rear Mic=0x18
[    7.185708]      Line=0x1a
[    7.185708] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
[    7.185709] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0892
[    7.196070] EDAC MC: Ver: 3.0.0
[    7.197538] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:3ca0
[    7.197546] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:3ca0
[    7.197548] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:3ca8
[    7.197552] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:3ca8
[    7.197554] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:3c71
[    7.197557] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:3c71
[    7.197559] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:3caa
[    7.197563] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:3caa
[    7.197565] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:3cab
[    7.197569] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:3cab
[    7.197570] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:3cac
[    7.197574] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:3cac
[    7.197576] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:3cad
[    7.197580] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:3cad
[    7.197581] EDAC sbridge: Seeking for: dev 11.0 PCI ID 8086:3cb8
[    7.197585] EDAC sbridge: Seeking for: dev 11.0 PCI ID 8086:3cb8
[    7.197587] EDAC sbridge: Seeking for: dev 0c.6 PCI ID 8086:3cf4
[    7.197590] EDAC sbridge: Seeking for: dev 0c.6 PCI ID 8086:3cf4
[    7.197592] EDAC sbridge: Seeking for: dev 0c.7 PCI ID 8086:3cf6
[    7.197595] EDAC sbridge: Seeking for: dev 0c.7 PCI ID 8086:3cf6
[    7.197597] EDAC sbridge: Seeking for: dev 0d.6 PCI ID 8086:3cf5
[    7.197600] EDAC sbridge: Seeking for: dev 0d.6 PCI ID 8086:3cf5
[    7.197603] EDAC sbridge: ECC is disabled. Aborting
[    7.197625] EDAC sbridge: Couldn't find mci handler
[    7.197808] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    7.197855] input: HDA Intel PCH Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    7.197902] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    7.197939] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    7.197984] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    7.198167] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    7.198832] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    7.198907] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    7.199204] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20131115/utaddress-251)
[    7.199211] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.199218] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20131115/utaddress-251)
[    7.199222] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.199223] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    7.199240] hda_intel: Disabling MSI
[    7.199246] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    7.199286] hda-intel 0000:01:00.1: Disabling 64bit DMA
[    7.203038] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[    7.215535] input: Wacom BambooFun 4x5 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input15
[    7.224827] usbcore: registered new interface driver wacom
[    7.226459] cfg80211: Calling CRDA to update world regulatory domain
[    7.241156] device-mapper: multipath: version 1.6.0 loaded
[    7.273743] type=1400 audit(1434048568.355:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=620 comm="apparmor_parser"
[    7.273747] type=1400 audit(1434048568.355:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=620 comm="apparmor_parser"
[    7.274008] type=1400 audit(1434048568.355:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=620 comm="apparmor_parser"
[    7.275204] type=1400 audit(1434048568.359:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=653 comm="apparmor_parser"
[    7.275207] type=1400 audit(1434048568.359:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=653 comm="apparmor_parser"
[    7.275209] type=1400 audit(1434048568.359:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=653 comm="apparmor_parser"
[    7.275463] type=1400 audit(1434048568.359:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=653 comm="apparmor_parser"
[    7.275467] type=1400 audit(1434048568.359:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=653 comm="apparmor_parser"
[    7.275611] type=1400 audit(1434048568.359:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=653 comm="apparmor_parser"
[    7.285170] Bluetooth: Core ver 2.17
[    7.285180] NET: Registered protocol family 31
[    7.285181] Bluetooth: HCI device and connection manager initialized
[    7.285186] Bluetooth: HCI socket layer initialized
[    7.285187] Bluetooth: L2CAP socket layer initialized
[    7.285190] Bluetooth: SCO socket layer initialized
[    7.285654] asus_wmi: ASUS WMI generic driver loaded
[    7.286942] asus_wmi: Initialization: 0x0
[    7.286964] asus_wmi: BIOS WMI version: 0.9
[    7.287002] asus_wmi: SFUN value: 0x0
[    7.287275] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input16
[    7.287847] Bluetooth: RFCOMM TTY layer initialized
[    7.287853] Bluetooth: RFCOMM socket layer initialized
[    7.287856] Bluetooth: RFCOMM ver 1.11
[    7.287949] asus_wmi: Disabling ACPI video driver
[    7.291306] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.291308] Bluetooth: BNEP filters: protocol multicast
[    7.291312] Bluetooth: BNEP socket layer initialized
[    7.314813] usb 2-1.6: reset high-speed USB device number 4 using ehci-pci
[    7.315652] init: cups main process (667) killed by HUP signal
[    7.315661] init: cups main process ended, respawning
[    7.325528] cfg80211: World regulatory domain updated:
[    7.325535] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.325537] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.325543] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.325544] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.325560] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.325561] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.368311] init: failsafe main process (757) killed by TERM signal
[    7.389792] intel_rapl: domain dram energy ctr 0:0 not working, skip
[    7.417689] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[    7.421703] type=1400 audit(1434048568.503:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=934 comm="apparmor_parser"
[    7.446943] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0006 detected
[    7.449230] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    7.449461] usbcore: registered new interface driver rt2800usb
[    7.670901] e1000e 0000:00:19.0: irq 90 for MSI/MSI-X
```

---

### Post by grahammechanical on 2015-06-12
> It does boot perfectly from the recovery menu for that kernel version ! weird..

Not weird. Recovery mode does not use the proprietary video driver.

> after installing the nvidia drivers from nvidia's site

Make sure that the latest drivers from the web site still support your video adapter whatever it is. I cannot use the latest Nvidia drivers as they no longer support my Nvidia GT220. In fact Additional Drivers will not offer me the latest Nvidia drivers. I use what is called a legacy driver and I am running kernel 3.19.

Regards.

---

### Post by efflandt on 2015-06-12
What video card/chip do you have (from lspci)? As mentioned it is best to use Ubuntu packages for video drivers to make sure that everything is compatible and updates properly (at least usually). If you need newer drivers than are in the normal repositories there are other repositories with newer drivers. For example I have a relatively new card with the new Maxwell chip, which did NOT work with **nvidia-current** in 14.04, but worked with **nvidia-331-updates**. Although, I am now running **nvidia-352** from xorg-edgers ppa:```
efflandt@XPS-8100-1404:~$ uname -a
Linux XPS-8100-1404 3.13.0-54-generic #91-Ubuntu SMP Tue May 26 19:15:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

efflandt@XPS-8100-1404:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-352                                            352.09-0ubuntu0~xedgers14.04.2                         amd64        NVIDIA binary driver - version 352.09
ii  nvidia-opencl-icd-352                                 352.09-0ubuntu0~xedgers14.04.2                         amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       352.09-0ubuntu0~xedgers14.04.1                         amd64        Tool for configuring the NVIDIA graphics driver
```

---

### Post by einstein**-7 on 2015-06-13
> **grahammechanical said:**
> Not weird. Recovery mode does not use the proprietary video driver.


? How can this be true when the system booted from recovery mode runs the nvidia settings program which also shows that the driver is in use and the xscreens configured ? ?  Also other drivers is impossible since i have stripped the system of any other graphical drivers..

---

### Post by einstein**-7 on 2015-06-13
> **efflandt said:**
> What video card/chip do you have (from lspci)? As mentioned it is best to use Ubuntu packages for video drivers to make sure that everything is compatible and updates properly (at least usually). If you need newer drivers than are in the normal repositories there are other repositories with newer drivers. For example I have a relatively new card with the new Maxwell chip, which did NOT work with **nvidia-current** in 14.04, but worked with **nvidia-331-updates**. Although, I am now running **nvidia-352** from xorg-edgers ppa:```
efflandt@XPS-8100-1404:~$ uname -a
Linux XPS-8100-1404 3.13.0-54-generic #91-Ubuntu SMP Tue May 26 19:15:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

efflandt@XPS-8100-1404:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-352                                            352.09-0ubuntu0~xedgers14.04.2                         amd64        NVIDIA binary driver - version 352.09
ii  nvidia-opencl-icd-352                                 352.09-0ubuntu0~xedgers14.04.2                         amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       352.09-0ubuntu0~xedgers14.04.1                         amd64        Tool for configuring the NVIDIA graphics driver
```

I have used the xorg-edgers ppa in the past and it did work ok but then I ran into problems later with the xorg and ubuntu main conflicting dependencies on some packages I needed and had a hell of a time fixing that little fiasco! lol  
Contrary to popular opinion I have found the opposite to be true when working with nvidia drivers and have never gotten a fully working or repeatable result with the nvidia packages from any ppa due to the flaws of various methods of installation and fixes/maybes etc. and so on ....  I have found that simply stripping the system of all video related drivers and using the installer works every time. Until now that is , and the system I'm having problems on is a clone of the system I'm currently typing on -- this one updated and after installing the drivers works fine as usual but the clone has these weird issues?

---

### Post by einstein**-7 on 2015-06-13
Anyone know how to manually fix this error below about the missing key/signature?

```
[    7.150247] nvidia: module license 'NVIDIA' taints kernel.
[    7.150249] Disabling lock debugging due to kernel taint
[    7.152613] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
```

---

### Post by Holger_Gehrke on 2015-06-13
Except for the second message, these messages merely call your attention to a legal problem: the NVIDIA-module is not GPL-licensed, so the kernel as a whole is not GPL-compliant anymore. The second message only means that you need access to the source of the kernel and all modules to do debugging, and since the source code for the NVIDIA module is not available ... 
The signature would be added by the kernel-developers if they had access to the source; they don't, so they can't ...

---

### Post by einstein**-7 on 2015-06-13
> **Holger_Gehrke said:**
> Except for the second message, these messages merely call your attention to a legal problem: the NVIDIA-module is not GPL-licensed, so the kernel as a whole is not GPL-compliant anymore. The second message only means that you need access to the source of the kernel and all modules to do debugging, and since the source code for the NVIDIA module is not available ... 
The signature would be added by the kernel-developers if they had access to the source; they don't, so they can't ...

OK! thanks, 

I also just found this the the x-0-greeter.log.. Is this error about an asyncronis read error maybe something that needs to be set up in the fstab options for this ssd drive since the original drive was and hdd and this system is a clone? 

```
[+0.00s] DEBUG: unity-greeter.vala:496: Starting unity-greeter 14.04.11 UID=112 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:499: Setting cursor
[+0.00s] DEBUG: unity-greeter.vala:513: Loading command line options
[+0.00s] DEBUG: unity-greeter.vala:541: Setting GTK+ settings
[+0.03s] DEBUG: unity-greeter.vala:564: Creating Unity Greeter
[+0.03s] DEBUG: unity-greeter.vala:57: Creating background surface
[+0.03s] DEBUG: Connecting to display manager...
[+0.03s] DEBUG: Wrote 18 bytes to daemon
[+0.03s] DEBUG: Read 8 bytes from daemon
[+0.03s] DEBUG: Read 150 bytes from daemon
[+0.03s] DEBUG: Connected version=1.10.5 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true show-remote-login=true
[+0.05s] DEBUG: menubar.vala:336: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.06s] DEBUG: menubar.vala:368: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.06s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.06s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.06s] DEBUG: user-list.vala:1030: Adding/updating user crush (crush)
[+0.06s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.06s] DEBUG: user-list.vala:1012: Adding guest account entry
[+0.09s] DEBUG: Loaded session /usr/share/xsessions/XBMC.desktop (XBMC, This session will start XBMC Media Center)
[+0.09s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.09s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0.09s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock.desktop (Cairo-Dock (GNOME), This session logs you into GNOME with Cairo-Dock)
[+0.09s] DEBUG: Starting authentication for user crush...
[+0.09s] DEBUG: Wrote 21 bytes to daemon
[+0.09s] DEBUG: main-window.vala:185: Screen is 2560x1080 pixels
[+0.09s] DEBUG: main-window.vala:193: Monitor 0 is 2560x1080 pixels at 0,0
[+0.09s] DEBUG: unity-greeter.vala:567: Showing greeter
[+0.09s] DEBUG: unity-greeter.vala:252: Showing main window
[+0.09s] DEBUG: background.vala:483: Regenerating backgrounds
[+0.09s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 2560x1080
[+0.09s] DEBUG: unity-greeter.vala:610: Starting main loop
[+0.09s] DEBUG: Read 8 bytes from daemon
[+0.10s] DEBUG: Read 35 bytes from daemon
[+0.10s] DEBUG: Prompt user with 1 message(s)
[+0.10s] DEBUG: settings-daemon.vala:75: Acquired org.gnome.SessionManager
[+0.10s] DEBUG: settings-daemon.vala:102: Acquired org.gnome.ScreenSaver
[+0.10s] DEBUG: settings-daemon.vala:159: All bus names acquired, starting unity-settings-daemon
[+0.11s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/Beach_by_Renato_Giordanelli.jpg at 2560x1080
[+0.12s] DEBUG: Connected to Application Indicator Service.
[+0.12s] DEBUG: unity-greeter.vala:235: starting system-ready sound
[+0.16s] DEBUG: background.vala:121: Render of background /usr/share/backgrounds/Beach_by_Renato_Giordanelli.jpg complete
[+0.17s] DEBUG: menubar.vala:538: Adding indicator object 0xe1c9d0 at position 0
[+0.18s] DEBUG: menubar.vala:538: Adding indicator object 0xe1c710 at position 0
[+0.18s] DEBUG: Request current apps
[+0.19s] DEBUG: menubar.vala:538: Adding indicator object 0xe1c450 at position 2
[+0.20s] DEBUG: menubar.vala:538: Adding indicator object 0xe1cf50 at position 2
[+0.20s] DEBUG: background.vala:121: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+0.25s] DEBUG: Building new application entry: :1.17  with icon: nm-stage03-connecting01 at position 0
[+0.25s] DEBUG: menubar.vala:538: Adding indicator object 0x10a7d60 at position 4

** (unity-settings-daemon:1408): WARNING **: Unable to register client: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such method 'RegisterClient'
[+0.79s] CRITICAL: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
[+0.79s] CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
[+0.79s] CRITICAL: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
[+0.79s] CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
[+0.79s] CRITICAL: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
[+0.79s] CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
[+4.23s] DEBUG: Providing response to display manager
[+4.23s] DEBUG: Wrote 26 bytes to daemon
[+4.24s] DEBUG: Read 8 bytes from daemon
[+4.24s] DEBUG: Read 17 bytes from daemon
[+4.24s] DEBUG: Authentication complete for user crush with return code 0
[+4.24s] DEBUG: Starting session ubuntu
[+4.24s] DEBUG: Wrote 18 bytes to daemon
[+4.24s] DEBUG: Read 8 bytes from daemon
[+4.24s] DEBUG: Read 4 bytes from daemon
[+4.24s] DEBUG: unity-greeter.vala:605: Got a SIGTERM
[+4.24s] DEBUG: unity-greeter.vala:613: Cleaning up
[+4.24s] DEBUG: unity-greeter.vala:621: Upstart exited with return value 0
[+4.24s] DEBUG: unity-greeter.vala:633: AT-SPI exited with return value 0
[+4.24s] DEBUG: unity-greeter.vala:639: Exiting

** (unity-settings-daemon:1408): WARNING **: Name taken or bus went away - shutting down
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
nm-applet-Message: PID 1393 (we are 1393) sent signal 15, shutting down...

(nm-applet:1393): libappindicator-WARNING **: Unable to send signal for NewStatus: The connection is closed
init: indicator-bluetooth main process (1397) killed by TERM signal
init: indicator-power main process (1399) killed by TERM signal
init: indicator-session main process (1410) killed by TERM signal
init: indicator-application main process (1418) killed by TERM signal
init: indicator-datetime main process (1405) killed by TERM signal

(nm-applet:1393): GLib-CRITICAL **: Source ID 89 was not found when attempting to remove it

(unity-settings-daemon:1408): dconf-WARNING **: failed to commit changes to dconf: The connection is closed
g_dbus_connection_real_closed: Remote peer vanished with error: Error receiving message: Connection reset by peer (g-io-error-quark, 0). Exiting. 
```

---

### Post by einstein**-7 on 2015-06-16
BUMP! 
I only get this greeter error with failed boots .. Anyone?!?!

---

### Post by einstein**-7 on 2015-06-17
Just re cloned the system and same problems , however I was able to get it to boot with either noacpi or nolacpi the latter which works a little better but still wondering why I'm having to bypass the acpi daemon when the exact same host machine I cloned from works fine with acpi??

---

### Post by einstein**-7 on 2015-06-18
NOTICE!
After two weeks of war the problem is finally fixed.  It is indeed a timing error of some sort when the filesystem drive is reading asynchronously and loads the nvidia driver module before the acpi module which means that the nvidia module looking for the acpi can't find it and gets dropped off the BUS literally..  
Maybe this is caused by the SSD since I've never had this problem on HDD's before and also never installed linux on an SSD either.
This thread [http://askubuntu.com/questions/235760/unity-does-not-appear-after-installing-proprietary-nvidia-drivers-gpu-has-falle](http://askubuntu.com/questions/235760/unity-does-not-appear-after-installing-proprietary-nvidia-drivers-gpu-has-falle) explains the problem better and offers 3 solutions no.1 worked for me. 
Also this one.. [http://www.cyberciti.biz/faq/debian-ubuntu-rhel-fedora-linux-nvidia-nvrm-gpu-fallen-off-bus/](http://www.cyberciti.biz/faq/debian-ubuntu-rhel-fedora-linux-nvidia-nvrm-gpu-fallen-off-bus/)

NOTE!  For others trying to partially clone linux systems such as only the filesystem partition and not the swap etc.. or simply creating a duplicate system on a new drive make sure to copy the NEW UUID for the NEW SWAP partition into your /etc/fstab file as well as the filesystem one.. None of the cloning guides/threads mention this and unless your dropping the old drive and doing a full system clone with all partitions this can cause major problems with the swap partition mounting other drives and failing etc..

---

