---
title: "ubuntu 14.04 boot takes more than 5 minutes"
date: 2014-11-11
forum: General Help
---

### Post by sreekantha on 2014-11-11
Hi,

I upgraded from 12.04 to 14.04 couple of months back. The boot time is more than 5 minutes. Once I get the login screen, takes few more minutes to load the desktop. The desktop has Core i5 with 8GB ram, dual boot with Windows 7 Ultimate.I have attached the dmesg and bootchart. In the dmesg, I have highlighted the lines in red where it is taking too long. 
Could someone pl. help.

Thanks,
Sreekantha.

[ATTACH]257889[/ATTACH]

---

### Post by oldfred on 2014-11-11
I never learned to use boot chart, but any post of it is always too small to review. 
I am running on my laptop and with full Ubuntu and only 1.5GB of RAM and I cannot easily load more than one large  app. So looking at your Office file and using Firefox causes my system to start using swap and gets real slow. Just a text file is all that is required.
My old laptop takes less than a minute to boot, but I use fallback not Unity as old Intel video chip cannot run Unity.

I see loop mounts? Is this a wubi install? 

Post these:
sudo parted -l
sudo fdisk -lu

---

### Post by BBQdave on 2014-11-11
> **sreekantha said:**
> I upgraded from 12.04 to 14.04 couple of months back. The boot time is more than 5 minutes.

If the upgrade had trouble, the most efficient solution may be to back up your data and do a fresh install of 14.04.

I am running Ubuntu Unity 14.04 on a Lenovo Thinkpad T400 (Intel® Core™2 Duo processor with 2GB of RAM) with out trouble. Smooth, responsive system.

That was a fairly big leap (with lots of system changes) from 12.04 to 14.04, though Ubuntu says you can upgrade, I would do a fresh install :)

---

### Post by sreekantha on 2014-11-11
This is a Wubi install.

Attached the dmesg below.

```
[    0.000000]Initializing cgroup subsys cpuset 
[    0.000000]Initializing cgroup subsys cpu 
[    0.000000]Initializing cgroup subsys cpuacct 
[    0.000000] Linuxversion 3.13.0-39-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu4.8.2-19ubuntu1) ) #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014(Ubuntu 3.13.0-39.66-generic 3.13.11.8) 
[    0.000000]Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-genericroot=UUID=2E6C87486C8709B3 loop=/ubuntu/disks/root.disk rw quietsplash vt.handoff=7 
[    0.000000]KERNEL supported cpus: 
[    0.000000]  Intel GenuineIntel 
[    0.000000]   AMDAuthenticAMD 
[    0.000000]  Centaur CentaurHauls 
[    0.000000] e820:BIOS-provided physical RAM map: 
[    0.000000]BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable 
[    0.000000]BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved 
[    0.000000]BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved 
[    0.000000]BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable 
[    0.000000]BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved 
[    0.000000]BIOS-e820: [mem 0x0000000020200000-0x000000003fffffff] usable 
[    0.000000]BIOS-e820: [mem 0x0000000040000000-0x00000000401fffff] reserved 
[    0.000000]BIOS-e820: [mem 0x0000000040200000-0x00000000da858fff] usable 
[    0.000000]BIOS-e820: [mem 0x00000000da859000-0x00000000da8a3fff] ACPI NVS 
[    0.000000]BIOS-e820: [mem 0x00000000da8a4000-0x00000000da8abfff] ACPI data 
[    0.000000]BIOS-e820: [mem 0x00000000da8ac000-0x00000000dabd9fff] reserved 
[    0.000000]BIOS-e820: [mem 0x00000000dabda000-0x00000000dabe7fff] ACPI NVS 
[    0.000000]BIOS-e820: [mem 0x00000000dabe8000-0x00000000dac0ffff] reserved 
[    0.000000]BIOS-e820: [mem 0x00000000dac10000-0x00000000dac52fff] ACPI NVS 
[    0.000000]BIOS-e820: [mem 0x00000000dac53000-0x00000000dae8dfff] reserved 
[    0.000000]BIOS-e820: [mem 0x00000000dae8e000-0x00000000daffffff] usable 
[    0.000000]BIOS-e820: [mem 0x00000000db800000-0x00000000df9fffff] reserved 
[    0.000000]BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved 
[    0.000000]BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved 
[    0.000000]BIOS-e820: [mem 0x0000000100000000-0x000000021f5fffff] usable 
[    0.000000] NX(Execute Disable) protection: active 
[    0.000000]SMBIOS 2.7 present. 
[    0.000000] DMI:                 /DH67CL, BIOS BLH6710H.86A.0146.2011.1222.141512/22/2011 
[    0.000000] e820:update [mem 0x00000000-0x00000fff] usable ==> reserved 
[    0.000000] e820:remove [mem 0x000a0000-0x000fffff] usable 
[    0.000000] NoAGP bridge found 
[    0.000000] e820:last_pfn = 0x21f600 max_arch_pfn = 0x400000000 
[    0.000000] MTRRdefault type: uncachable 
[    0.000000] MTRRfixed ranges enabled: 
[    0.000000]  00000-9FFFF write-back 
[    0.000000]  A0000-BFFFF uncachable 
[    0.000000]  C0000-CFFFF write-protect 
[    0.000000]  D0000-E7FFF uncachable 
[    0.000000]  E8000-FFFFF write-protect 
[    0.000000] MTRRvariable ranges enabled: 
[    0.000000]   0base 000000000 mask E00000000 write-back 
[    0.000000]   1base 200000000 mask FE0000000 write-back 
[    0.000000]   2base 0DB800000 mask FFF800000 uncachable 
[    0.000000]   3base 0DC000000 mask FFC000000 uncachable 
[    0.000000]   4base 0E0000000 mask FE0000000 uncachable 
[    0.000000]   5base 21F600000 mask FFFE00000 uncachable 
[    0.000000]   6base 21F800000 mask FFF800000 uncachable 
[    0.000000]   7disabled 
[    0.000000]   8disabled 
[    0.000000]   9disabled 
[    0.000000] x86PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106 
[    0.000000]original variable MTRRs 
[    0.000000] reg0, base: 0GB, range: 8GB, type WB 
[    0.000000] reg1, base: 8GB, range: 512MB, type WB 
[    0.000000] reg2, base: 3512MB, range: 8MB, type UC 
[    0.000000] reg3, base: 3520MB, range: 64MB, type UC 
[    0.000000] reg4, base: 3584MB, range: 512MB, type UC 
[    0.000000] reg5, base: 8694MB, range: 2MB, type UC 
[    0.000000] reg6, base: 8696MB, range: 8MB, type UC 
[    0.000000] totalRAM covered: 8110M 
[    0.000000] Foundoptimal setting for mtrr clean up 
[    0.000000] gran_size: 64K     chunk_size: 128M     num_reg: 9      lose cover RAM: 0G 
[    0.000000] Newvariable MTRRs 
[    0.000000] reg0, base: 0GB, range: 2GB, type WB 
[    0.000000] reg1, base: 2GB, range: 1GB, type WB 
[    0.000000] reg2, base: 3GB, range: 512MB, type WB 
[    0.000000] reg3, base: 3512MB, range: 8MB, type UC 
[    0.000000] reg4, base: 3520MB, range: 64MB, type UC 
[    0.000000] reg5, base: 4GB, range: 4GB, type WB 
[    0.000000] reg6, base: 8GB, range: 512MB, type WB 
[    0.000000] reg7, base: 8694MB, range: 2MB, type UC 
[    0.000000] reg8, base: 8696MB, range: 8MB, type UC 
[    0.000000] e820:update [mem 0xdb800000-0xffffffff] usable ==> reserved 
[    0.000000] e820:last_pfn = 0xdb000 max_arch_pfn = 0x400000000 
[    0.000000] foundSMP MP-table at [mem 0x000fcea0-0x000fceaf] mapped at[ffff8800000fcea0] 
[    0.000000]Scanning 1 areas for low memory corruption 
[    0.000000] Basememory trampoline at [ffff880000097000] 97000 size 24576 
[    0.000000]init_memory_mapping: [mem 0x00000000-0x000fffff] 
[    0.000000]  [mem0x00000000-0x000fffff] page 4k 
[    0.000000] BRK[0x01fe1000, 0x01fe1fff] PGTABLE 
[    0.000000] BRK[0x01fe2000, 0x01fe2fff] PGTABLE 
[    0.000000] BRK[0x01fe3000, 0x01fe3fff] PGTABLE 
[    0.000000]init_memory_mapping: [mem 0x21f400000-0x21f5fffff] 
[    0.000000]  [mem0x21f400000-0x21f5fffff] page 2M 
[    0.000000] BRK[0x01fe4000, 0x01fe4fff] PGTABLE 
[    0.000000]init_memory_mapping: [mem 0x21c000000-0x21f3fffff] 
[    0.000000]  [mem0x21c000000-0x21f3fffff] page 2M 
[    0.000000]init_memory_mapping: [mem 0x200000000-0x21bffffff] 
[    0.000000]  [mem0x200000000-0x21bffffff] page 2M 
[    0.000000]init_memory_mapping: [mem 0x00100000-0x1fffffff] 
[    0.000000]  [mem0x00100000-0x001fffff] page 4k 
[    0.000000]  [mem0x00200000-0x1fffffff] page 2M 
[    0.000000]init_memory_mapping: [mem 0x20200000-0x3fffffff] 
[    0.000000]  [mem0x20200000-0x3fffffff] page 2M 
[    0.000000]init_memory_mapping: [mem 0x40200000-0xda858fff] 
[    0.000000]  [mem0x40200000-0xda7fffff] page 2M 
[    0.000000]  [mem0xda800000-0xda858fff] page 4k 
[    0.000000] BRK[0x01fe5000, 0x01fe5fff] PGTABLE 
[    0.000000] BRK[0x01fe6000, 0x01fe6fff] PGTABLE 
[    0.000000]init_memory_mapping: [mem 0xdae8e000-0xdaffffff] 
[    0.000000]  [mem0xdae8e000-0xdaffffff] page 4k 
[    0.000000]init_memory_mapping: [mem 0x100000000-0x1ffffffff] 
[    0.000000]  [mem0x100000000-0x1ffffffff] page 2M 
[    0.000000]RAMDISK: [mem 0x35b54000-0x36da1fff] 
[    0.000000] ACPI:RSDP 000000000009dba0 000024 (v02  :NTEL) 
[    0.000000] ACPI:XSDT 00000000da8ab7fc 000054 (v01 HPQOEM SLIC-MPC 01072009 AMI 00010013) 
[    0.000000] ACPI:FACP 00000000da8ab4d0 0000F4 (v04 INTEL  DH67CL   01072009 AMI 00010013) 
[    0.000000] ACPI:DSDT 00000000da8a4140 00738C (v02 INTEL  DH67CL   00000012 INTL20051117) 
[    0.000000] ACPI:FACS 00000000dabdff80 000040 
[    0.000000] ACPI:APIC 00000000da8ab5c8 000072 (v03 INTEL  DH67CL   01072009 AMI 00010013) 
[    0.000000] ACPI:SSDT 00000000da8ab640 000102 (v01 INTEL  DH67CL   00000001 MSFT03000001) 
[    0.000000] ACPI:MCFG 00000000da8ab748 00003C (v01 INTEL  DH67CL   01072009 MSFT00000097) 
[    0.000000] ACPI:HPET 00000000da8ab788 000038 (v01 INTEL  DH67CL   01072009 AMI.00000004) 
[    0.000000] ACPI:SLIC 00000000da8ab850 000176 (v01 HPQOEM SLIC-MPC 00000001 HPQ 00000001) 
[    0.000000] ACPI:Local APIC address 0xfee00000 
[    0.000000] NoNUMA configuration found 
[    0.000000]Faking a node at [mem 0x0000000000000000-0x000000021f5fffff] 
[    0.000000]Initmem setup node 0 [mem 0x00000000-0x21f5fffff] 
[    0.000000]  NODE_DATA [mem 0x21f5f4000-0x21f5f8fff] 
[    0.000000] [ffffea0000000000-ffffea00087fffff] PMD ->[ffff880216c00000-ffff88021ebfffff] on node 0 
[    0.000000] Zoneranges: 
[    0.000000]   DMA     [mem 0x00001000-0x00ffffff] 
[    0.000000]  DMA32    [mem 0x01000000-0xffffffff] 
[    0.000000]  Normal   [mem 0x100000000-0x21f5fffff] 
[    0.000000]Movable zone start for each node 
[    0.000000] Earlymemory node ranges 
[    0.000000]  node   0: [mem 0x00001000-0x0009cfff] 
[    0.000000]  node   0: [mem 0x00100000-0x1fffffff] 
[    0.000000]  node   0: [mem 0x20200000-0x3fffffff] 
[    0.000000]  node   0: [mem 0x40200000-0xda858fff] 
[    0.000000]  node   0: [mem 0xdae8e000-0xdaffffff] 
[    0.000000]  node   0: [mem 0x100000000-0x21f5fffff] 
[    0.000000] Onnode 0 totalpages: 2071399 
[    0.000000]   DMAzone: 64 pages used for memmap 
[    0.000000]   DMAzone: 21 pages reserved 
[    0.000000]   DMAzone: 3996 pages, LIFO batch:0 
[    0.000000]  DMA32 zone: 13912 pages used for memmap 
[    0.000000]  DMA32 zone: 890315 pages, LIFO batch:31 
[    0.000000]  Normal zone: 18392 pages used for memmap 
[    0.000000]  Normal zone: 1177088 pages, LIFO batch:31 
[    0.000000] ACPI:PM-Timer IO Port: 0x408 
[    0.000000] ACPI:Local APIC address 0xfee00000 
[    0.000000] ACPI:LAPIC (acpi_id[0x00] lapic_id[0x00] enabled) 
[    0.000000] ACPI:LAPIC (acpi_id[0x01] lapic_id[0x02] enabled) 
[    0.000000] ACPI:LAPIC (acpi_id[0x02] lapic_id[0x04] enabled) 
[    0.000000] ACPI:LAPIC (acpi_id[0x03] lapic_id[0x06] enabled) 
[    0.000000] ACPI:LAPIC_NMI (acpi_id[0xff] high edge lint[0x1]) 
[    0.000000] ACPI:IOAPIC (id[0x00] address[0xfec00000] gsi_base[0]) 
[    0.000000]IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23 
[    0.000000] ACPI:INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
[    0.000000] ACPI:INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
[    0.000000] ACPI:IRQ0 used by override. 
[    0.000000] ACPI:IRQ2 used by override. 
[    0.000000] ACPI:IRQ9 used by override. 
[    0.000000] UsingACPI (MADT) for SMP configuration information 
[    0.000000] ACPI:HPET id: 0x8086a701 base: 0xfed00000 
[    0.000000]smpboot: Allowing 4 CPUs, 0 hotplug CPUs 
[    0.000000]nr_irqs_gsi: 40 
[    0.000000] PM:Registered nosave memory: [mem 0x0009d000-0x0009dfff] 
[    0.000000] PM:Registered nosave memory: [mem 0x0009e000-0x0009ffff] 
[    0.000000] PM:Registered nosave memory: [mem 0x000a0000-0x000dffff] 
[    0.000000] PM:Registered nosave memory: [mem 0x000e0000-0x000fffff] 
[    0.000000] PM:Registered nosave memory: [mem 0x20000000-0x201fffff] 
[    0.000000] PM:Registered nosave memory: [mem 0x40000000-0x401fffff] 
[    0.000000] PM:Registered nosave memory: [mem 0xda859000-0xda8a3fff] 
[    0.000000] PM:Registered nosave memory: [mem 0xda8a4000-0xda8abfff] 
[    0.000000] PM:Registered nosave memory: [mem 0xda8ac000-0xdabd9fff] 
[    0.000000] PM:Registered nosave memory: [mem 0xdabda000-0xdabe7fff] 
[    0.000000] PM:Registered nosave memory: [mem 0xdabe8000-0xdac0ffff] 
[    0.000000] PM:Registered nosave memory: [mem 0xdac10000-0xdac52fff] 
[    0.000000] PM:Registered nosave memory: [mem 0xdac53000-0xdae8dfff] 
[    0.000000] PM:Registered nosave memory: [mem 0xdb000000-0xdb7fffff] 
[    0.000000] PM:Registered nosave memory: [mem 0xdb800000-0xdf9fffff] 
[    0.000000] PM:Registered nosave memory: [mem 0xdfa00000-0xfed1bfff] 
[    0.000000] PM:Registered nosave memory: [mem 0xfed1c000-0xfed1ffff] 
[    0.000000] PM:Registered nosave memory: [mem 0xfed20000-0xfeffffff] 
[    0.000000] PM:Registered nosave memory: [mem 0xff000000-0xffffffff] 
[    0.000000] e820:[mem 0xdfa00000-0xfed1bfff] available for PCI devices 
[    0.000000]Booting paravirtualized kernel on bare hardware 
[    0.000000]setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4nr_node_ids:1 
[    0.000000]PERCPU: Embedded 29 pages/cpu @ffff88021f200000 s86400 r8192 d24192u524288 
[    0.000000]pcpu-alloc: s86400 r8192 d24192 u524288 alloc=1*2097152 
[    0.000000]pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built1 zonelists in Zone order, mobility grouping on.  Total pages:2039010 
[    0.000000]Policy zone: Normal 
[    0.000000]Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-genericroot=UUID=2E6C87486C8709B3 loop=/ubuntu/disks/root.disk rw quietsplash vt.handoff=7 
[    0.000000] PIDhash table entries: 4096 (order: 3, 32768 bytes) 
[    0.000000]xsave: enabled xstate_bv 0x7, cntxt size 0x340 
[    0.000000]Checking aperture... 
[    0.000000] NoAGP bridge found 
[    0.000000]Calgary: detecting Calgary via BIOS EBDA area 
[    0.000000]Calgary: Unable to locate Rio Grande table in EBDA - bailing! 
[    0.000000]Memory: 8052596K/8285596K available (7375K kernel code, 1144K rwdata,3404K rodata, 1336K init, 1444K bss, 233000K reserved) 
[    0.000000] SLUB:HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1 
[    0.000000]Hierarchical RCU implementation. 
[    0.000000]     RCUdyntick-idle grace-period acceleration is enabled. 
[    0.000000]     RCUrestricting CPUs from NR_CPUS=256 to nr_cpu_ids=4. 
[    0.000000]    Offload RCU callbacks from all CPUs 
[    0.000000]    Offload RCU callbacks from CPUs: 0-3. 
[    0.000000]NR_IRQS:16640 nr_irqs:712 16 
[    0.000000]Console: colour dummy device 80x25 
[    0.000000]console [tty0] enabled 
[    0.000000]allocated 33554432 bytes of page_cgroup 
[    0.000000]please try 'cgroup_disable=memory' option if you don't want memorycgroups 
[    0.000000] hpetclockevent registered 
[    0.000000] tsc:Fast TSC calibration using PIT 
[    0.004000] tsc:Detected 2993.435 MHz processor 
[    0.000001]Calibrating delay loop (skipped), value calculated using timerfrequency.. 5986.87 BogoMIPS (lpj=11973740) 
[    0.000004]pid_max: default: 32768 minimum: 301 
[    0.000023]Security Framework initialized 
[    0.000036]AppArmor: AppArmor initialized 
[    0.000037] Yama:becoming mindful. 
[    0.000472]Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes) 
[    0.002092]Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes) 
[    0.002812]Mount-cache hash table entries: 16384 (order: 5, 131072 bytes) 
[    0.002819]Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes) 
[    0.002975]Initializing cgroup subsys memory 
[    0.002979]Initializing cgroup subsys devices 
[    0.002981]Initializing cgroup subsys freezer 
[    0.002982]Initializing cgroup subsys blkio 
[    0.002983]Initializing cgroup subsys perf_event 
[    0.002985]Initializing cgroup subsys hugetlb 
[    0.003002] CPU:Physical Processor ID: 0 
[    0.003003] CPU:Processor Core ID: 0 
[    0.003008] mce:CPU supports 9 MCE banks 
[    0.003018] CPU0:Thermal monitoring enabled (TM1) 
[    0.003027] Lastlevel iTLB entries: 4KB 512, 2MB 0, 4MB 0 
[    0.003027] Lastlevel dTLB entries: 4KB 512, 2MB 32, 4MB 32 
[    0.003027]tlb_flushall_shift: 2 
[    0.003124]Freeing SMP alternatives memory: 32K (ffffffff81e6e000 -ffffffff81e76000) 
[    0.004053] ACPI:Core revision 20131115 
[    0.005881] ACPI:All ACPI Tables successfully acquired 
[    0.239588]ftrace: allocating 28541 entries in 112 pages 
[    0.250750]..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1 
[    0.290424]smpboot: CPU0: Intel(R) Core(TM) i5-3330 CPU @ 3.00GHz (fam: 06,model: 3a, stepping: 09) 
[    0.290430] TSCdeadline timer enabled 
[    0.290437]Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events,full-width counters, Intel PMU driver. 
[    0.290442] ...version:                3 
[    0.290443] ...bit width:              48 
[    0.290444] ...generic registers:      8 
[    0.290445] ...value mask:             0000ffffffffffff 
[    0.290445] ...max period:             0000ffffffffffff 
[    0.290446] ...fixed-purpose events:   3 
[    0.290447] ...event mask:             00000007000000ff 
[    0.291651] x86:Booting SMP configuration: 
[    0.304726] NMIwatchdog: enabled on all CPUs, permanently consumes one hw-PMUcounter. 
[    0.291652] ....node  #0, CPUs:      #1 #2 #3 
[    0.331139] x86:Booted up 1 node, 4 CPUs 
[    0.331142]smpboot: Total of 4 processors activated (23947.48 BogoMIPS) 
[    0.333999]devtmpfs: initialized 
[    0.336019] EVM:security.selinux 
[    0.336020] EVM:security.SMACK64 
[    0.336021] EVM:security.ima 
[    0.336021] EVM:security.capability 
[    0.336055] PM:Registering ACPI NVS region [mem 0xda859000-0xda8a3fff] (307200bytes) 
[    0.336059] PM:Registering ACPI NVS region [mem 0xdabda000-0xdabe7fff] (57344 bytes)
[    0.336060] PM:Registering ACPI NVS region [mem 0xdac10000-0xdac52fff] (274432bytes) 
[    0.336640]pinctrl core: initialized pinctrl subsystem 
[    0.336684]regulator-dummy: no parameters 
[    0.336712] RTCtime:  3:10:28, date: 11/11/14 
[    0.336735] NET:Registered protocol family 16 
[    0.336811]cpuidle: using governor ladder 
[    0.336812]cpuidle: using governor menu 
[    0.336840] ACPI:bus type PCI registered 
[    0.336841]acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5 
[    0.336881] PCI:MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff](base 0xf8000000) 
[    0.336883] PCI:not using MMCONFIG 
[    0.336884] PCI:Using configuration type 1 for base access 
[    0.337511] bio:create slab <bio-0> at 0 
[    0.337616] ACPI:Added _OSI(Module Device) 
[    0.337617] ACPI:Added _OSI(Processor Device) 
[    0.337618] ACPI:Added _OSI(3.0 _SCP Extensions) 
[    0.337619] ACPI:Added _OSI(Processor Aggregator Device) 
[    0.338979] ACPI:Executed 1 blocks of module-level executable AML code 
[    0.340616] ACPI:SSDT 00000000dabde918 0003E0 (v01    AMI      IST 00000001 MSFT03000001) 
[    0.340809] ACPI:Dynamic OEM Table Load: 
[    0.340810] ACPI:SSDT           (null) 0003E0 (v01    AMI      IST 00000001 MSFT03000001) 
[    0.340833] ACPI:SSDT 00000000dabddd98 000120 (v01    AMI      CST 00000001 MSFT03000001) 
[    0.340990] ACPI:Dynamic OEM Table Load: 
[    0.340992] ACPI:SSDT           (null) 000120 (v01    AMI      CST 00000001 MSFT03000001) 
[    0.341307] ACPI:Interpreter enabled 
[    0.341310] ACPIException: AE_NOT_FOUND, While evaluating Sleep State [\_S1_](20131115/hwxface-580) 
[    0.341313] ACPIException: AE_NOT_FOUND, While evaluating Sleep State [\_S2_](20131115/hwxface-580) 
[    0.341320] ACPI:(supports S0 S3 S4 S5) 
[    0.341321] ACPI:Using IOAPIC for interrupt routing 
[    0.341335] PCI:MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff](base 0xf8000000) 
[    0.341370] PCI:MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboardresources 
[    0.346578] PCI:Using host bridge windows from ACPI; if necessary, use "pci=nocrs"and report a bug 
[    0.346659] ACPI:No dock devices found. 
[    0.346739][Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored 
[    0.350211] ACPI:PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff]) 
[    0.350216] acpiPNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM SegmentsMSI] 
[    0.350339] acpiPNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AERPCIeCapability] 
[    0.350467] acpiPNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f]only partially covers this bridge 
[    0.350599] PCIhost bridge to bus 0000:00 
[    0.350601]pci_bus 0000:00: root bus resource [bus 00-ff] 
[    0.350603]pci_bus 0000:00: root bus resource [io  0x0000-0x03af] 
[    0.350604]pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7] 
[    0.350605]pci_bus 0000:00: root bus resource [io  0x03b0-0x03df] 
[    0.350606]pci_bus 0000:00: root bus resource [io  0x0d00-0xffff] 
[    0.350608]pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff] 
[    0.350609]pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff] 
[    0.350610]pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xffffffff] 
[    0.350616] pci0000:00:00.0: [8086:0150] type 00 class 0x060000 
[    0.350677] pci0000:00:02.0: [8086:0152] type 00 class 0x030000 
[    0.350686] pci0000:00:02.0: reg 0x10: [mem 0xfe000000-0xfe3fffff 64bit] 
[    0.350691] pci0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref] 
[    0.350695] pci0000:00:02.0: reg 0x20: [io  0xf000-0xf03f] 
[    0.350776] pci0000:00:16.0: [8086:1c3a] type 00 class 0x078000 
[    0.350798] pci0000:00:16.0: reg 0x10: [mem 0xfe529000-0xfe52900f 64bit] 
[    0.350871] pci0000:00:16.0: PME# supported from D0 D3hot D3cold 
[    0.350933] pci0000:00:19.0: [8086:1503] type 00 class 0x020000 
[    0.350951] pci0000:00:19.0: reg 0x10: [mem 0xfe500000-0xfe51ffff] 
[    0.350959] pci0000:00:19.0: reg 0x14: [mem 0xfe528000-0xfe528fff] 
[    0.350968] pci0000:00:19.0: reg 0x18: [io  0xf080-0xf09f] 
[    0.351029] pci0000:00:19.0: PME# supported from D0 D3hot D3cold 
[    0.351062] pci0000:00:19.0: System wakeup disabled by ACPI 
[    0.351090] pci0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320 
[    0.351111] pci0000:00:1a.0: reg 0x10: [mem 0xfe527000-0xfe5273ff] 
[    0.351202] pci0000:00:1a.0: PME# supported from D0 D3hot D3cold 
[    0.351236] pci0000:00:1a.0: System wakeup disabled by ACPI 
[    0.351262] pci0000:00:1b.0: [8086:1c20] type 00 class 0x040300 
[    0.351275] pci0000:00:1b.0: reg 0x10: [mem 0xfe520000-0xfe523fff 64bit] 
[    0.351341] pci0000:00:1b.0: PME# supported from D0 D3hot D3cold 
[    0.351395] pci0000:00:1c.0: [8086:1c10] type 01 class 0x060400 
[    0.351470] pci0000:00:1c.0: PME# supported from D0 D3hot D3cold 
[    0.351505] pci0000:00:1c.0: System wakeup disabled by ACPI 
[    0.351530] pci0000:00:1c.3: [8086:1c16] type 01 class 0x060400 
[    0.351606] pci0000:00:1c.3: PME# supported from D0 D3hot D3cold 
[    0.351641] pci0000:00:1c.3: System wakeup disabled by ACPI 
[    0.351671] pci0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320 
[    0.351691] pci0000:00:1d.0: reg 0x10: [mem 0xfe526000-0xfe5263ff] 
[    0.351779] pci0000:00:1d.0: PME# supported from D0 D3hot D3cold 
[    0.351813] pci0000:00:1d.0: System wakeup disabled by ACPI 
[    0.351839] pci0000:00:1f.0: [8086:1c4a] type 00 class 0x060100 
[    0.351987] pci0000:00:1f.2: [8086:1c02] type 00 class 0x010601 
[    0.352005] pci0000:00:1f.2: reg 0x10: [io  0xf0d0-0xf0d7] 
[    0.352013] pci0000:00:1f.2: reg 0x14: [io  0xf0c0-0xf0c3] 
[    0.352021] pci0000:00:1f.2: reg 0x18: [io  0xf0b0-0xf0b7] 
[    0.352029] pci0000:00:1f.2: reg 0x1c: [io  0xf0a0-0xf0a3] 
[    0.352037] pci0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f] 
[    0.352045] pci0000:00:1f.2: reg 0x24: [mem 0xfe525000-0xfe5257ff] 
[    0.352087] pci0000:00:1f.2: PME# supported from D3hot 
[    0.352135] pci0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500 
[    0.352150] pci0000:00:1f.3: reg 0x10: [mem 0xfe524000-0xfe5240ff 64bit] 
[    0.352170] pci0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f] 
[    0.352310] pci0000:01:00.0: [1283:8892] type 01 class 0x060401 
[    0.352478] pci0000:01:00.0: supports D1 D2 
[    0.352479] pci0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.352504] pci0000:01:00.0: System wakeup disabled by ACPI 
[    0.352521] pci0000:00:1c.0: PCI bridge to [bus 01-02] 
[    0.352709] pci0000:01:00.0: PCI bridge to [bus 02] (subtractive decode) 
[    0.352735] pci0000:01:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractivedecode) 
[    0.352736] pci0000:01:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractivedecode) 
[    0.352738] pci0000:01:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractivedecode) 
[    0.352739] pci0000:01:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractivedecode) 
[    0.352822] pci0000:03:00.0: [1033:0194] type 00 class 0x0c0330 
[    0.352848] pci0000:03:00.0: reg 0x10: [mem 0xfe400000-0xfe401fff 64bit] 
[    0.352977] pci0000:03:00.0: PME# supported from D0 D3hot D3cold 
[    0.359154] pci0000:00:1c.3: PCI bridge to [bus 03] 
[    0.359162] pci0000:00:1c.3:   bridge window [mem 0xfe400000-0xfe4fffff] 
[    0.359586] ACPI:PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15) 
[    0.359624] ACPI:PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15) 
[    0.359660] ACPI:PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15) 
[    0.359695] ACPI:PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 10 11 12 14 15) 
[    0.359731] ACPI:PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15) 
[    0.359767] ACPI:PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0 
[    0.359803] ACPI:PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15) 
[    0.359838] ACPI:PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15) 
[    0.359928] ACPI:Enabled 3 GPEs in block 00 to 3F 
[    0.359932] ACPI:\_SB_.PCI0: notify handler is installed 
[    0.359960] Found1 acpi root devices 
[    0.360020]vgaarb: device added:PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none 
[    0.360022]vgaarb: loaded 
[    0.360023]vgaarb: bridge control possible 0000:00:02.0 
[    0.360124] SCSIsubsystem initialized 
[    0.360146]libata version 3.00 loaded. 
[    0.360157] ACPI:bus type USB registered 
[    0.360168]usbcore: registered new interface driver usbfs 
[    0.360173]usbcore: registered new interface driver hub 
[    0.360185]usbcore: registered new device driver usb 
[    0.360246] PCI:Using ACPI for IRQ routing 
[    0.361752] PCI:pci_cache_line_size set to 64 bytes 
[    0.361793] e820:reserve RAM buffer [mem 0x0009d800-0x0009ffff] 
[    0.361794] e820:reserve RAM buffer [mem 0xda859000-0xdbffffff] 
[    0.361796] e820:reserve RAM buffer [mem 0xdb000000-0xdbffffff] 
[    0.361797] e820:reserve RAM buffer [mem 0x21f600000-0x21fffffff] 
[    0.361851]NetLabel: Initializing 
[    0.361852]NetLabel:  domain hash size = 128 
[    0.361852]NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.361862]NetLabel:  unlabeled traffic allowed by default 
[    0.361902]hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0 
[    0.361906]hpet0: 8 comparators, 64-bit 14.318180 MHz counter 
[    0.363932]Switched to clocksource hpet 
[    0.366942]AppArmor: AppArmor Filesystem Enabled 
[    0.366957] pnp:PnP ACPI init 
[    0.366966] ACPI:bus type PNP registered 
[    0.367040]system 00:00: [mem 0xfed10000-0xfed19fff] has been reserved 
[    0.367042]system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved 
[    0.367043]system 00:00: [mem 0xfed90000-0xfed93fff] has been reserved 
[    0.367045]system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved 
[    0.367046]system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved 
[    0.367048]system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active) 
[    0.367137]system 00:01: [io  0x0290-0x029f] has been reserved 
[    0.367139]system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    0.367315] pnp00:02: [dma 4] 
[    0.367326] pnp00:02: Plug and Play ACPI device, IDs PNP0200 (active) 
[    0.367347] pnp00:03: Plug and Play ACPI device, IDs PNP0b00 (active) 
[    0.367360] pnp00:04: Plug and Play ACPI device, IDs PNP0800 (active) 
[    0.367388]system 00:05: [io  0x04d0-0x04d1] has been reserved 
[    0.367390]system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    0.367406] pnp00:06: Plug and Play ACPI device, IDs PNP0c04 (active) 
[    0.367510]system 00:07: [io  0x0400-0x0453] could not be reserved 
[    0.367512]system 00:07: [io  0x0458-0x047f] has been reserved 
[    0.367513]system 00:07: [io  0x1180-0x119f] has been reserved 
[    0.367514]system 00:07: [io  0x0500-0x057f] has been reserved 
[    0.367516]system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved 
[    0.367518]system 00:07: [mem 0xfec00000-0xfecfffff] could not be reserved 
[    0.367519]system 00:07: [mem 0xfed08000-0xfed08fff] has been reserved 
[    0.367521]system 00:07: [mem 0xff000000-0xffffffff] has been reserved 
[    0.367522]system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active) 
[    0.367556]system 00:08: [io  0x0454-0x0457] has been reserved 
[    0.367558]system 00:08: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.367632] pnp00:09: Plug and Play ACPI device, IDs PNP0103 (active) 
[    0.367716] pnp:PnP ACPI: found 10 devices 
[    0.367717] ACPI:bus type PNP unregistered 
[    0.373665] pci0000:01:00.0: PCI bridge to [bus 02] 
[    0.373689] pci0000:00:1c.0: PCI bridge to [bus 01-02] 
[    0.373700] pci0000:00:1c.3: PCI bridge to [bus 03] 
[    0.373705] pci0000:00:1c.3:   bridge window [mem 0xfe400000-0xfe4fffff] 
[    0.373714]pci_bus 0000:00: resource 4 [io  0x0000-0x03af] 
[    0.373715]pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7] 
[    0.373716]pci_bus 0000:00: resource 6 [io  0x03b0-0x03df] 
[    0.373717]pci_bus 0000:00: resource 7 [io  0x0d00-0xffff] 
[    0.373719]pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff] 
[    0.373720]pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff] 
[    0.373721]pci_bus 0000:00: resource 10 [mem 0xdfa00000-0xffffffff] 
[    0.373723]pci_bus 0000:03: resource 1 [mem 0xfe400000-0xfe4fffff] 
[    0.373742] NET:Registered protocol family 2 
[    0.373883] TCPestablished hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.373998] TCPbind hash table entries: 65536 (order: 8, 1048576 bytes) 
[    0.374115] TCP:Hash tables configured (established 65536 bind 65536) 
[    0.374127] TCP:reno registered 
[    0.374136] UDPhash table entries: 4096 (order: 5, 131072 bytes) 
[    0.374158]UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes) 
[    0.374206] NET:Registered protocol family 1 
[    0.374545] pci0000:00:02.0: BIOS left Intel GPU interrupts enabled; disabling 
[    0.374556] pci0000:00:02.0: Boot video device 
[    0.374841] PCI:CLS 64 bytes, default 64 
[    0.374877]Trying to unpack rootfs image as initramfs... 
[    0.604218]Freeing initrd memory: 18744K (ffff880035b54000 - ffff880036da2000) 
[    0.604222]PCI-DMA: Using software bounce buffering for IO (SWIOTLB) 
[    0.604224]software IO TLB [mem 0xd6859000-0xda859000] (64MB) mapped at[ffff8800d6859000-ffff8800da858fff] 
[    0.604409]microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x7 
[    0.604415]microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x7 
[    0.604421]microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x7 
[    0.604427]microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x7 
[    0.604465]microcode: Microcode Update Driver: v2.00<tigran@aivazian.fsnet.co.uk>, Peter Oruba 
[    0.604467]Scanning for low memory corruption every 60 seconds 
[    0.604644]Initialise system trusted keyring 
[    0.604673]audit: initializing netlink socket (disabled) 
[    0.604681]type=2000 audit(1415675427.380:1): initialized 
[    0.625608]HugeTLB registered 2 MB page size, pre-allocated 0 pages 
[    0.626336] zbud:loaded 
[    0.626441] VFS:Disk quotas dquot_6.5.2 
[    0.626468]Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[    0.626737] fuseinit (API version 7.22) 
[    0.626787]msgmni has been set to 15764 
[    0.626819] Keytype big_key registered 
[    0.627178] Keytype asymmetric registered 
[    0.627180]Asymmetric key parser 'x509' registered 
[    0.627209] Blocklayer SCSI generic (bsg) driver version 0.4 loaded (major 252) 
[    0.627238] ioscheduler noop registered 
[    0.627239] ioscheduler deadline registered (default) 
[    0.627255] ioscheduler cfq registered 
[    0.627389]pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X 
[    0.627464]pcieport 0000:00:1c.3: irq 41 for MSI/MSI-X 
[    0.627536]pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt 
[    0.627538] pci0000:01:00.0: Signaling PME through PCIe PME interrupt 
[    0.627542]pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded 
[    0.627557]pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt 
[    0.627559] pci0000:03:00.0: Signaling PME through PCIe PME interrupt 
[    0.627563]pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded 
[    0.627569]pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    0.627578]pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    0.627600]vesafb: mode is 1600x900x32, linelength=6400, pages=0 
[    0.627601]vesafb: scrolling: redraw 
[    0.627602]vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0 
[    0.628068]vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90004e80000,using 5632k, total 5632k 
[    0.712586]Console: switching to colour frame buffer device 200x56 
[    0.796881] fb0:VESA VGA frame buffer device 
[    0.796892]intel_idle: MWAIT substates: 0x1120 
[    0.796893]intel_idle: v0.4 model 0x3A 
[    0.796894]intel_idle: lapic_timer_reliable_states 0xffffffff 
[    0.796954] ipmimessage handler version 39.2 
[    0.796998]input: Power Button as/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0 
[    0.797002] ACPI:Power Button [PWRB] 
[    0.797023]input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1 
[    0.797025] ACPI:Power Button [PWRF] 
[    0.797358] GHES:HEST is not enabled! 
[    0.797417]Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled 
[    0.798365] Linuxagpgart interface v0.103 
[    0.799150] brd:module loaded 
[    0.799545] loop:module loaded 
[    0.799755]libphy: Fixed MDIO Bus: probed 
[    0.799816] tun:Universal TUN/TAP device driver, 1.6 
[    0.799816] tun:(C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    0.799854] PPPgeneric driver version 2.4.2 
[    0.799889]ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.799897]ehci-pci: EHCI PCI platform driver 
[    0.799966]ehci-pci 0000:00:1a.0: EHCI Host Controller 
[    0.799970]ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1 
[    0.799982]ehci-pci 0000:00:1a.0: debug port 2 
[    0.803870]ehci-pci 0000:00:1a.0: cache line size of 64 is not supported 
[    0.803883]ehci-pci 0000:00:1a.0: irq 16, io mem 0xfe527000 
[    0.815804]ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00 
[    0.815840] usbusb1: New USB device found, idVendor=1d6b, idProduct=0002 
[    0.815842] usbusb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    0.815843] usbusb1: Product: EHCI Host Controller 
[    0.815845] usbusb1: Manufacturer: Linux 3.13.0-39-generic ehci_hcd 
[    0.815846] usbusb1: SerialNumber: 0000:00:1a.0 
[    0.815980] hub1-0:1.0: USB hub found 
[    0.815987] hub1-0:1.0: 2 ports detected 
[    0.816108]ehci-pci 0000:00:1d.0: EHCI Host Controller 
[    0.816111]ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2 
[    0.816122]ehci-pci 0000:00:1d.0: debug port 2 
[    0.820007]ehci-pci 0000:00:1d.0: cache line size of 64 is not supported 
[    0.820018]ehci-pci 0000:00:1d.0: irq 23, io mem 0xfe526000 
[    0.831811]ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00 
[    0.831855] usbusb2: New USB device found, idVendor=1d6b, idProduct=0002 
[    0.831857] usbusb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    0.831858] usbusb2: Product: EHCI Host Controller 
[    0.831859] usbusb2: Manufacturer: Linux 3.13.0-39-generic ehci_hcd 
[    0.831861] usbusb2: SerialNumber: 0000:00:1d.0 
[    0.832005] hub2-0:1.0: USB hub found 
[    0.832011] hub2-0:1.0: 2 ports detected 
[    0.832073]ehci-platform: EHCI generic platform driver 
[    0.832079]ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    0.832080]ohci-pci: OHCI PCI platform driver 
[    0.832086]ohci-platform: OHCI generic platform driver 
[    0.832089]uhci_hcd: USB Universal Host Controller Interface driver 
[    0.832142]xhci_hcd 0000:03:00.0: xHCI Host Controller 
[    0.832146]xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3 
[    0.832322]xhci_hcd 0000:03:00.0: irq 42 for MSI/MSI-X 
[    0.832325]xhci_hcd 0000:03:00.0: irq 43 for MSI/MSI-X 
[    0.832329]xhci_hcd 0000:03:00.0: irq 44 for MSI/MSI-X 
[    0.832333]xhci_hcd 0000:03:00.0: irq 45 for MSI/MSI-X 
[    0.832336]xhci_hcd 0000:03:00.0: irq 46 for MSI/MSI-X 
[    0.832445] usbusb3: New USB device found, idVendor=1d6b, idProduct=0002 
[    0.832446] usbusb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    0.832448] usbusb3: Product: xHCI Host Controller 
[    0.832449] usbusb3: Manufacturer: Linux 3.13.0-39-generic xhci_hcd 
[    0.832450] usbusb3: SerialNumber: 0000:03:00.0 
[    0.832571] hub3-0:1.0: USB hub found 
[    0.832581] hub3-0:1.0: 2 ports detected 
[    0.832635]xhci_hcd 0000:03:00.0: xHCI Host Controller 
[    0.832637]xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 4 
[    0.835654] usbusb4: New USB device found, idVendor=1d6b, idProduct=0003 
[    0.835655] usbusb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    0.835656] usbusb4: Product: xHCI Host Controller 
[    0.835658] usbusb4: Manufacturer: Linux 3.13.0-39-generic xhci_hcd 
[    0.835659] usbusb4: SerialNumber: 0000:03:00.0 
[    0.835807] hub4-0:1.0: USB hub found 
[    0.835822] hub4-0:1.0: 2 ports detected 
[    0.843916]i8042: PNP: No PS/2 controller found. Probing ports directly. 
[    0.846214]serio: i8042 KBD port at 0x60,0x64 irq 1 
[    0.846219]serio: i8042 AUX port at 0x60,0x64 irq 12 
[    0.846418]mousedev: PS/2 mouse device common for all mice 
[    0.846679]rtc_cmos 00:03: RTC can wake from S4 
[    0.846847]rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
[    0.846877]rtc_cmos 00:03: alarms up to one month, y3k, 114 bytes nvram, hpetirqs 
[    0.846919]device-mapper: uevent: version 1.0.3 
[    0.846993]device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised:dm-devel@redhat.com 
[    0.846997]ledtrig-cpu: registered to indicate activity on CPUs 
[    0.847063] TCP:cubic registered 
[    0.847115] NET:Registered protocol family 10 
[    0.847225] NET:Registered protocol family 17 
[    0.847230] Keytype dns_resolver registered 
[    0.847469]Loading compiled-in X.509 certificates 
[    0.848158]Loaded X.509 cert 'Magrathea: Glacier signing key:e3c165d0891e3ceeb6dd5c18c7e1993cd24956b0' 
[    0.848167]registered taskstats version 1 
[    0.850106] Keytype trusted registered 
[    0.851653] Keytype encrypted registered 
[    0.853303]AppArmor: AppArmor sha1 policy hashing enabled 
[    0.853306] IMA:No TPM chip found, activating TPM-bypass! 
[    0.853497]regulator-dummy: disabling 
[    0.853628]  Magic number: 6:787:158 
[    0.853647] acpidevice:25: hash matches 
[    0.853723]rtc_cmos 00:03: setting system clock to 2014-11-11 03:10:28 UTC(1415675428) 
[    0.854192] BIOSEDD facility v0.16 2004-Jun-25, 0 devices found 
[    0.854193] EDDinformation not available. 
[    0.854217] PM:Hibernation image not present or could not be loaded. 
[    0.854937]Freeing unused kernel memory: 1336K (ffffffff81d20000 -ffffffff81e6e000) 
[    0.854938] Writeprotecting the kernel read-only data: 12288k 
[    0.856605]Freeing unused kernel memory: 804K (ffff880001737000 -ffff880001800000) 
[    0.857965]Freeing unused kernel memory: 692K (ffff880001b53000 -ffff880001c00000) 
[    0.871273]systemd-udevd[129]: starting version 204 
[    0.882006]pps_core: LinuxPPS API ver. 1 registered 
[    0.882008]pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti<giometti@linux.it> 
[    0.882909] PTPclock support registered 
[    0.884033] ahci0000:00:1f.2: version 3.0 
[    0.884134] ahci0000:00:1f.2: irq 47 for MSI/MSI-X 
[    0.885880]e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k 
[    0.885882]e1000e: Copyright(c) 1999 - 2013 Intel Corporation. 
[    0.899835] ahci0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATAmode 
[    0.899839] ahci0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems sxsapst 
[    0.940172] scsi0: ahci 
[    0.940365] scsi1: ahci 
[    0.940545] scsi2: ahci 
[    0.940741] scsi3: ahci 
[    0.940893] scsi4: ahci 
[    0.941056] scsi5: ahci 
[    0.941117] ata1:SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525100 irq 47 
[    0.941121] ata2:SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525180 irq 47 
[    0.941124] ata3:SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525200 irq 47 
[    0.941126] ata4:SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525280 irq 47 
[    0.941129] ata5:SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525300 irq 47 
[    0.941132] ata6:SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525380 irq 47 
[    0.941363]e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set todynamic conservative mode 
[    0.941384]e1000e 0000:00:19.0: irq 48 for MSI/MSI-X 
[    1.127779] usb1-1: new high-speed USB device number 2 using ehci-pci 
[    1.200235]e1000e 0000:00:19.0 eth0: registered PHC clock 
[    1.200237]e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1)4c:72:b9:4e:ca:28 
[    1.200238]e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection 
[    1.200273]e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF 
[    1.259687] ata5:SATA link down (SStatus 0 SControl 300) 
[    1.259723] ata4:SATA link down (SStatus 0 SControl 300) 
[    1.259740] ata6:SATA link down (SStatus 0 SControl 300) 
[    1.259763] ata3:SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    1.259816] ata2:SATA link down (SStatus 0 SControl 300) 
[    1.260069] usb1-1: New USB device found, idVendor=8087, idProduct=0024 
[    1.260073] usb1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0 
[    1.260338] hub1-1:1.0: USB hub found 
[    1.260403] hub1-1:1.0: 6 ports detected 
[    1.262951]ata3.00: ATAPI: HL-DT-ST DVDRAM GH24NS72, WM01, max UDMA/100 
[    1.267247]ata3.00: configured for UDMA/100 
[    1.267696] ata1:SATA link up 6.0 Gbps (SStatus 133 SControl 300) 
[    1.268997]ata1.00: ATA-8: ST500DM002-1BD142, KC45, max UDMA/133 
[    1.269002]ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32) 
[    1.270525]ata1.00: configured for UDMA/133 
[    1.270703] scsi0:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 KC45 PQ: 0 ANSI:5 
[    1.270820] sd0:0:0:0: Attached scsi generic sg0 type 0 
[    1.270821] sd0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB) 
[    1.270823] sd0:0:0:0: [sda] 4096-byte physical blocks 
[    1.270858] sd0:0:0:0: [sda] Write Protect is off 
[    1.270871] sd0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    1.270894] sd0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn'tsupport DPO or FUA 
[    1.275679] scsi2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS72  WM01 PQ: 0 ANSI:5 
[    1.284190] sr0:scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray 
[    1.284192]cdrom: Uniform CD-ROM driver Revision: 3.20 
[    1.284368] sr2:0:0:0: Attached scsi CD-ROM sr0 
[    1.284435] sr2:0:0:0: Attached scsi generic sg1 type 5 
[    1.288922]  sda:sda1 sda2 sda3 sda4 
[    1.289237] sd0:0:0:0: [sda] Attached SCSI disk 
[    1.371697] usb2-1: new high-speed USB device number 2 using ehci-pci 
[    1.503954] usb2-1: New USB device found, idVendor=8087, idProduct=0024 
[    1.503959] usb2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0 
[    1.504222] hub2-1:1.0: USB hub found 
[    1.504346] hub2-1:1.0: 8 ports detected 
[    1.575697] usb1-1.1: new full-speed USB device number 3 using ehci-pci 
[    1.603570] tsc:Refined TSC clocksource calibration: 2993.200 MHz 
[    1.669291] usb1-1.1: New USB device found, idVendor=041e, idProduct=4036 
[    1.669296] usb1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
[    1.669298] usb1-1.1: Product: WebCam Live!   
[    1.669300] usb1-1.1: Manufacturer: Creative Labs  
[    1.739709] usb1-1.4: new low-speed USB device number 4 using ehci-pci 
[    1.839246] usb1-1.4: New USB device found, idVendor=045e, idProduct=00e3 
[    1.839251] usb1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
[    1.839254] usb1-1.4: Product: Microsoft Wireless OpticalDesktop\xffffffc2\xffffffae\xffffffae 2.20 
[    1.839256] usb1-1.4: Manufacturer: Microsft 
[    1.842591]hidraw: raw HID events driver (C) Jiri Kosina 
[    1.862277]usbcore: registered new interface driver usbhid 
[    1.862289]usbhid: USB HID core driver 
[    1.863619]input: Microsft Microsoft Wireless OpticalDesktop\xffffffc2\xffffffae\xffffffae 2.20 as/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input5
[    1.863706]hid-generic 0003:045E:00E3.0001: input,hidraw0: USB HID v1.11Keyboard [Microsft Microsoft Wireless OpticalDesktop\xffffffc2\xffffffae\xffffffae 2.20] onusb-0000:00:1a.0-1.4/input0 
[    1.870462]input: Microsft Microsoft Wireless OpticalDesktop\xffffffc2\xffffffae\xffffffae 2.20 as/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/input/input6
[    1.870552]hid-generic 0003:045E:00E3.0002: input,hidraw1: USB HID v1.11 Mouse[Microsft Microsoft Wireless OpticalDesktop\xffffffc2\xffffffae\xffffffae 2.20] onusb-0000:00:1a.0-1.4/input1 
[    1.911658] usb1-1.5: new low-speed USB device number 5 using ehci-pci 
[    2.007165] usb1-1.5: New USB device found, idVendor=0461, idProduct=4d81 
[    2.007170] usb1-1.5: New USB device strings: Mfr=0, Product=2, SerialNumber=0 
[    2.007172] usb1-1.5: Product: USB Optical Mouse 
[    2.009678]input: USB Optical Mouse as/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input7
[    2.009846]hid-generic 0003:0461:4D81.0003: input,hidraw2: USB HID v1.11 Mouse[USB Optical Mouse] on usb-0000:00:1a.0-1.5/input0 
[    2.206355]EXT4-fs (loop0): mounting ext3 file system using the ext4 subsystem 
[    2.603422]Switched to clocksource tsc 
[    2.924043]random: nonblocking pool is initialized 
[    3.062944]EXT4-fs (loop0): 12 orphan inodes deleted 
[    3.062946]EXT4-fs (loop0): recovery complete 
[    3.149662]EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts:(null) 
[COLOR=#800000]**[  34.546375] Adding 262140k swap on /host/ubuntu/disks/swap.disk. Priority:-1 extents:1 across:262140k FS **[/COLOR]
[   34.619017] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   34.829183]systemd-udevd[415]: starting version 204 
[   35.381202] lp:driver loaded but no devices found 
[   35.487309]ppdev: user-space parallel port driver 
[   37.052118]type=1400 audit(1415675464.702:2): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=484comm="apparmor_parser" 
[   37.052123]type=1400 audit(1415675464.702:3): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/sbin/cupsd" pid=484 comm="apparmor_parser"
[   37.052442]type=1400 audit(1415675464.706:4): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=484 comm="apparmor_parser"
[   37.146917]Bluetooth: Core ver 2.17 
[   37.146940] NET:Registered protocol family 31 
[   37.146942]Bluetooth: HCI device and connection manager initialized 
[   37.146947]Bluetooth: HCI socket layer initialized 
[   37.146949]Bluetooth: L2CAP socket layer initialized 
[   37.146951]Bluetooth: SCO socket layer initialized 
[   37.149353]Bluetooth: RFCOMM TTY layer initialized 
[   37.149359]Bluetooth: RFCOMM socket layer initialized 
[   37.149362]Bluetooth: RFCOMM ver 1.11 
[   37.191310]Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   37.191313]Bluetooth: BNEP filters: protocol multicast 
[   37.191319]Bluetooth: BNEP socket layer initialized 
[   37.440287] init:cups main process (488) killed by HUP signal 
[   37.440295] init:cups main process ended, respawning 
[   39.030798]mei_me 0000:00:16.0: irq 49 for MSI/MSI-X 
[   39.999061] [drm]Initialized drm 1.1.0 20060810 
[   40.117805]type=1400 audit(1415675467.770:5): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/sbin/dhclient" pid=588 comm="apparmor_parser"
[   40.117809]type=1400 audit(1415675467.770:6): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=588 comm="apparmor_parser" 
[   40.117811]type=1400 audit(1415675467.770:7): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=588comm="apparmor_parser" 
[   40.118109]type=1400 audit(1415675467.770:8): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=588 comm="apparmor_parser" 
[   40.118112]type=1400 audit(1415675467.770:9): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=588comm="apparmor_parser" 
[   40.118266]type=1400 audit(1415675467.770:10): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=588comm="apparmor_parser" 
[   40.120085]type=1400 audit(1415675467.774:11): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/sbin/dhclient" pid=589 comm="apparmor_parser"
[   40.200971] [drm]Memory usable by graphics device = 2048M 
[   40.200975]checking generic (e0000000 580000) vs hw (e0000000 10000000) 
[   40.200976] fb:conflicting fb hw usage inteldrmfb vs VESA VGA - removing genericdriver 
[   40.200999]Console: switching to colour dummy device 80x25 
[   40.243285] i9150000:00:02.0: irq 50 for MSI/MSI-X 
[   40.243294] [drm]Supports vblank timestamp caching Rev 2 (21.10.2013). 
[   40.243295] [drm]Driver supports precise vblank timestamp query. 
[   40.243343]vgaarb: device changed decodes:PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem 
[   40.263382] [drm]Wrong MCH_SSKPD value: 0x1e0e0206 
[   40.263384] [drm]This can cause pipe underruns and display issues. 
[   40.263384] [drm]Please upgrade your BIOS to fix this. 
[   40.335234] [drm]GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin2 
[   40.428515]fbcon: inteldrmfb (fb0) is primary device 
[   40.477096]gpio_ich: GPIO from 180 to 255 on gpio_ich 
[   40.627236]Console: switching to colour frame buffer device 200x56 
[   40.629719] i9150000:00:02.0: fb0: inteldrmfb frame buffer device 
[   40.629720] i9150000:00:02.0: registered panic notifier 
[   40.629741] i915:No ACPI video bus found 
[   40.629819] [drm]Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
[   40.911755] init:failsafe main process (613) killed by TERM signal 
[   41.843643]snd_hda_intel 0000:00:1b.0: irq 51 for MSI/MSI-X 
[   41.973986] SKU:Nid=0x1d sku_cfg=0x4006f601 
[   41.973988] SKU:port_connectivity=0x1 
[   41.973989] SKU:enable_pcbeep=0x0 
[   41.973989] SKU:check_sum=0x00000006 
[   41.973990] SKU:customization=0x000000f6 
[   41.973991] SKU:external_amp=0x0 
[   41.973991] SKU:platform_type=0x0 
[   41.973992] SKU:swap=0x0 
[   41.973993] SKU:override=0x1 
[   41.974419]autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line 
[   41.974420]   speaker_outs=0 (0x0/0x0/0x0/0x0/0x0) 
[   41.974421]   hp_outs=1 (0x1b/0x0/0x0/0x0/0x0) 
[   41.974422]   mono: mono_out=0x0 
[   41.974422]   dig-out=0x11/0x1e 
[   41.974423]   inputs: 
[   41.974424]     Front Mic=0x19 
[   41.974425]     Rear Mic=0x18 
[   41.974426]     Line=0x1a 
[   41.974427]realtek: No valid SSID, checking pincfg 0x4006f601 for NID 0x1d 
[   41.974428]realtek: Enabling init ASM_ID=0xf601 CODEC_ID=10ec0892 
[   42.027070] [drm]Enabling RC6 states: RC6 on, RC6p on, RC6pp off 
[   42.132181]input: HDA Intel PCH HDMI/DP,pcm=3 as/devices/pci0000:00/0000:00:1b.0/sound/card0/input15 
[   42.132266]input: HDA Intel PCH Front Headphone as/devices/pci0000:00/0000:00:1b.0/sound/card0/input14 
[   42.132306]input: HDA Intel PCH Line Out CLFE as/devices/pci0000:00/0000:00:1b.0/sound/card0/input13 
[   42.132342]input: HDA Intel PCH Line Out Surround as/devices/pci0000:00/0000:00:1b.0/sound/card0/input12 
[   42.132375]input: HDA Intel PCH Line Out Front as/devices/pci0000:00/0000:00:1b.0/sound/card0/input11 
[   42.132409]input: HDA Intel PCH Line as/devices/pci0000:00/0000:00:1b.0/sound/card0/input10 
[   42.132443]input: HDA Intel PCH Rear Mic as/devices/pci0000:00/0000:00:1b.0/sound/card0/input9 
[   42.132480]input: HDA Intel PCH Front Mic as/devices/pci0000:00/0000:00:1b.0/sound/card0/input8 
[   42.295629] Linuxvideo capture interface: v2.00 
[   42.418501]gspca_main: v2.14.0 registered 
[   42.628051]gspca_main: gspca_zc3xx-2.14.0 probing 041e:4036 
[   43.578970]input: gspca_zc3xx as/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/input/input16 
[   43.579130]usbcore: registered new interface driver gspca_zc3xx 
[   45.345777]e1000e 0000:00:19.0: irq 48 for MSI/MSI-X 
[   45.449662]e1000e 0000:00:19.0: irq 48 for MSI/MSI-X 
[   45.449752] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   45.449935] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   45.642454]audit_printk_skb: 15 callbacks suppressed 
[   45.642464]type=1400 audit(1415675473.298:17): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/sbin/dhclient" pid=895 comm="apparmor_parser"
[   45.642470]type=1400 audit(1415675473.298:18): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=895 comm="apparmor_parser" 
[   45.642473]type=1400 audit(1415675473.298:19): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=895comm="apparmor_parser" 
[   45.642789]type=1400 audit(1415675473.298:20): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=895 comm="apparmor_parser" 
[   45.642792]type=1400 audit(1415675473.298:21): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=895comm="apparmor_parser" 
[   45.642947]type=1400 audit(1415675473.298:22): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=895comm="apparmor_parser" 
[   45.674389]type=1400 audit(1415675473.330:23): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/telepathy/mission-control-5" pid=898comm="apparmor_parser" 
[   45.674394]type=1400 audit(1415675473.330:24): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/telepathy/telepathy-*" pid=898comm="apparmor_parser" 
[   45.674397]type=1400 audit(1415675473.330:25): apparmor="STATUS"operation="profile_load" profile="unconfined"name="pxgsettings" pid=898 comm="apparmor_parser"
[   45.674400]type=1400 audit(1415675473.330:26): apparmor="STATUS"operation="profile_load" profile="unconfined"name="sanitized_helper" pid=898 comm="apparmor_parser"
[   46.075793] init:Failed to spawn hybrid-gfx main process: unable to execute: No suchfile or directory 
[   46.943078]e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   46.943082]e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO 
[   46.943114] IPv6:ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[   52.595716] init:plymouth-upstart-bridge main process ended, respawning 
[   52.608506] init:plymouth-upstart-bridge main process ended, respawning 
[   67.089817]audit_printk_skb: 123 callbacks suppressed 
[   67.089820]type=1400 audit(1415675494.750:68): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=1770comm="apparmor_parser" 
[   67.089825]type=1400 audit(1415675494.750:69): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=1770 comm="apparmor_parser"
[   67.090125]type=1400 audit(1415675494.750:70): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=1770 comm="apparmor_parser"
[COLOR=#800000]**[1102.449263] type=1400 audit(1415676530.207:71): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=3178comm="apparmor_parser" **[/COLOR]
[ 1102.449270]type=1400 audit(1415676530.207:72): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=3178 comm="apparmor_parser"
[ 1102.449615]type=1400 audit(1415676530.207:73): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=3178 comm="apparmor_parser" 

```

**Output of sudo parted -l**:
Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   105GB  105GB  primary  ntfs
 3      105GB   315GB  210GB  primary  ntfs
 4      315GB   500GB  186GB  primary  ntfs

[B]Output of sudo fdisk -lu:
[/B]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4f3d7ff4


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   204799999   102296576    7  HPFS/NTFS/exFAT
/dev/sda3       204800000   614399999   204800000    7  HPFS/NTFS/exFAT
/dev/sda4       614400000   976771071   181185536    7  HPFS/NTFS/exFAT

---

### Post by hakuna_matata on 2014-11-12
> **sreekantha said:**
> 
```

[    3.062944]EXT4-fs (loop0): 12 orphan inodes deleted  
[    3.062946]EXT4-fs (loop0): recovery complete

```

Are these messages also in the output of dmesg after next booting ?

IMHO it is possible that fsck can't correct a corrupt file system and this causes other problems.

---

### Post by sreekantha on 2014-11-13
Those messages are not there

---

### Post by oldfred on 2014-11-13
That it is slow mounting NTFS is normal, I think. I noticed with my SSD that time increased 25% when I added the mount of my NTFS partition. Before SSD the extra time to mount NTFS was lost in all the other times.

But your main issue is the lines at the end with apparmor and cups.
Do you have printer(s) installed. Do they work or are there issues?
If you remove printer temporarily does it boot a lot quicker?

---

### Post by sreekantha on 2014-11-14
Yes, I do have a canon MP 160 printer/scanner installed. The printer works fine but the scanner does not. I tried removing the printer but did not help

---

### Post by oldfred on 2014-11-14
I have a MP160 also.
When I first got it, I had to down load drivers from some Canon site in Asia. But now drivers generally work.
Both scanner & printer work, but it often locks up on the last page and I have to power cycle it. OFF switch does not even work.

This is my part of log for loading driver. Note times, new UEFI system with SSD. :)

> [    2.474474] Bluetooth: RFCOMM ver 1.11
[    2.481085] type=1400 audit(1415828926.441:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=802 comm="apparmor_parser"
[    2.481089] type=1400 audit(1415828926.441:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=802 comm="apparmor_parser"
[    2.481286] type=1400 audit(1415828926.441:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=802 comm="apparmor_parser"
[    2.496283] init: cups main process (810) killed by HUP signal


---

