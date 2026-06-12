---
title: "VERY slow boot..."
date: 2015-12-25
forum: General Help
---

### Post by BarryD9545 on 2015-12-25
I haven't made any changes recently other than updates as the Software Updater called them out.

I reboot daily at 6:30am, and saw a few days ago that it's taking about 30 minutes (no exaggeration) for the system to restart.

Looking about the forums, I u\would up using gParted to delete and create a new swap drive, but it hasn't made a change to the 30 minutes it's taking to reboot the system.

Any help is appreciated....

---

### Post by Bucky Ball on 2015-12-25
*Thread moved to **General Help**.*

The boot.log is located at /var/log/boot.log. Please reboot the machine and then post the contents of that log file here between code tags, thanks (see last link in my signature).

---

### Post by pqwoerituytrueiwoq on 2015-12-25
did you update [FONT=courier new]/etc/fstab[/FONT] and [FONT=courier new]/etc/initramfs-tools/conf.d/resume[/FONT] with the new UUID (or remove if you got rid of swap)
may as well check [FONT=courier new]/etc/mtab[/FONT] just to be safe
install [bootchart]("apt:bootchart")
a few minutes after you boot you will have a chart in [FONT=courier new]/var/log/bootchart/[/FONT]
if you upload that here it will be scaled down and unreadable (unless you live in the fictional world of CSI)
i suggest uploading it to imgur

---

### Post by BarryD9545 on 2015-12-25
I dunno...kinda new at the deeper aspects.

etc/fstab looks like this

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# / was on /dev/sda1 during installation
UUID=751db636-8f58-406f-839c-55db9682d769 /               ext4    errors=remount-ro 0       1


# swap was on /dev/sda5 during installation
UUID=da1f6541-24d4-4159-b277-bfe4f039cdca none            swap    sw              0       0


#Media Drive
#<File System>          <Mount point>  <type>  <options>                                     <dump>  <pass>
UUID=2A4CF4C74CF48EB7 /media/barry/ ntfs defaults,umask=000,uid=1000,gid=1000,noatime,x-gvfs-show 0 0
```

Also, I noticed the "errors=remount-ro" entry under options in sda1 and I have no idea why that's there.

---

### Post by pqwoerituytrueiwoq on 2015-12-25
open gparted and get the info from your swap partition (right click the swap one), if it is different replace it in those files

 "errors=remount-ro" is a option, it means in the event of a file system error remount the drive as read only, this prevents damage and does not cause a instant crash

does that media drive still exist? if so i would move it to /mnt/media (be sure to create taht folder after changing fstab)

---

### Post by BarryD9545 on 2015-12-26
The boot.log seems to hang when I paste it into the reply, I'm working in that.

The gparted: 
[ATTACH=CONFIG]266394[/ATTACH]
and fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# / was on /dev/sda1 during installation
UUID=751db636-8f58-406f-839c-55db9682d769 /               ext4    errors=remount-ro 0       1


# swap was on /dev/sda5 during installation
UUID=da1f6541-24d4-4159-b277-bfe4f039cdca none            swap    sw              0       0


#Media Drive
#<File System>          <Mount point>  <type>  <options>                                     <dump>  <pass>
UUID=2A4CF4C74CF48EB7 /media/barry/ ntfs defaults,umask=000,uid=1000,gid=1000,noatime,x-gvfs-show 0 0
```

UUID's are different, which is the right one to put where?

---

### Post by pqwoerituytrueiwoq on 2015-12-26
> **BarryD9545 said:**
> and fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# / was on /dev/sda1 during installation
UUID=751db636-8f58-406f-839c-55db9682d769 /               ext4    errors=remount-ro 0       1


# swap was on /dev/sda5 during installation
UUID=da1f6541-24d4-4159-b277-bfe4f039cdca none            swap    sw              0       0


#Media Drive
#<File System>          <Mount point>  <type>  <options>                                     <dump>  <pass>
UUID=2A4CF4C74CF48EB7 /media/barry/ ntfs defaults,umask=000,uid=1000,gid=1000,noatime,x-gvfs-show 0 0
```

UUID's are different, which is the right one to put where?
replace the one in fstab: "da1f6541-24d4-4159-b277-bfe4f039cdca"
also replace it in [FONT=courier new]/etc/initramfs-tools/conf.d/resume[/FONT]

---

### Post by BarryD9545 on 2015-12-26
Replaced the UUID in both files, fstab and resume, and only got about a 10 minute increase, down to about 45 minutes according to the boot.log.

I'm trying to post the boot.log, but it keeps timing out to a server error.  I suppose that 5300+ lines is a bit longer than expected?

---

### Post by pqwoerituytrueiwoq on 2015-12-26
put it in a zip file and try it
there should be a PNG file in [FONT=courier new]/var/log/bootchart[/FONT] that you can upload to imgur.com
also post the output on [FONT=courier new]dmesg[/FONT]

---

### Post by BarryD9545 on 2015-12-26
dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-22-generic (buildd@lcy01-23) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #27-Ubuntu SMP Thu Dec 17 22:57:22 UTC 2015 (Ubuntu 4.2.0-22.27-generic 4.2.6)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Enabled xstate features 0x3, context size is 0x240 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007dd8ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007dd90000-0x000000007dd9dfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007dd9e000-0x000000007dddffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007dde0000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: MSI MS-7592/G41M-P26 (MS-7592), BIOS V26.6 03/02/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7dd90 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07DE00000 mask FFFE00000 uncachable
[    0.000000]   2 base 07E000000 mask FFE000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2014MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2016MB, range: 32MB, type UC
[    0.000000] total RAM covered: 2014M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2014MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2016MB, range: 32MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] initial memory mapped: [mem 0x00000000-0x021fffff]
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20000000-0x377fffff]
[    0.000000]  [mem 0x20000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01cde000, 0x01cdefff] PGTABLE
[    0.000000] BRK [0x01cdf000, 0x01cdffff] PGTABLE
[    0.000000] RAMDISK: [mem 0x34148000-0x3609bfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F99F0 000014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 0x000000007DD90000 000040 (v01 7592MS A7592400 20110302 MSFT 00000097)
[    0.000000] ACPI: FACP 0x000000007DD90200 000084 (v01 7592MS A7592400 20110302 MSFT 00000097)
[    0.000000] ACPI: DSDT 0x000000007DD90440 0062AE (v01 A7592  A7592400 00000400 INTL 20051117)
[    0.000000] ACPI: FACS 0x000000007DD9E000 000040
[    0.000000] ACPI: APIC 0x000000007DD90390 00006C (v01 7592MS A7592400 20110302 MSFT 00000097)
[    0.000000] ACPI: MCFG 0x000000007DD90400 00003C (v01 7592MS OEMMCFG  20110302 MSFT 00000097)
[    0.000000] ACPI: OEMB 0x000000007DD9E040 000072 (v01 7592MS A7592400 20110302 MSFT 00000097)
[    0.000000] ACPI: HPET 0x000000007DD98440 000038 (v01 7592MS OEMHPET  20110302 MSFT 00000097)
[    0.000000] ACPI: GSCI 0x000000007DD9E0C0 002024 (v01 7592MS GMCHSCI  20110302 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x000000007DDA0670 000A7C (v01 DpgPmm CpuPm    00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1121MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   Normal   [mem 0x0000000001000000-0x0000000037bfdfff]
[    0.000000]   HighMem  [mem 0x0000000037bfe000-0x000000007dd8ffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000007dd8ffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000007dd8ffff]
[    0.000000] On node 0 totalpages: 515374
[    0.000000]   DMA zone: 40 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 2190 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 287122 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Reserving Intel graphics stolen memory at 0x7e000000-0x7fffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xfedfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 19 pages/cpu @f678b000 s47116 r0 d30708 u77824
[    0.000000] pcpu-alloc: s47116 r0 d30708 u77824 alloc=19*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 513144
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-22-generic root=UUID=751db636-8f58-406f-839c-55db9682d769 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007dd90)
[    0.000000] Initializing Movable for node 0 (00000000:00000000)
[    0.000000] Memory: 1994420K/2061496K available (7576K kernel code, 742K rwdata, 3020K rodata, 928K init, 796K bss, 67076K reserved, 0K cma-reserved, 1148488K highmem)
[    0.000000] virtual kernel memory layout:
                   fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
                   pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
                   vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
                   lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
                     .init : 0xc1b16000 - 0xc1bfe000   ( 928 kB)
                     .data : 0xc17666f0 - 0xc1b14b00   (3769 kB)
                     .text : 0xc1000000 - 0xc17666f0   (7577 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 32.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=32, nr_cpu_ids=4
[    0.000000] NR_IRQS:2304 nr_irqs:456 16
[    0.000000] CPU 0 irqstacks, hard=f3c36000 soft=f3c38000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3000.133 MHz processor
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 6000.26 BogoMIPS (lpj=12000532)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004019] ACPI: Core revision 20150619
[    0.011780] ACPI: All ACPI Tables successfully acquired
[    0.011795] Security Framework initialized
[    0.011809] AppArmor: AppArmor initialized
[    0.011810] Yama: becoming mindful.
[    0.011846] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.011848] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.012071] Initializing cgroup subsys blkio
[    0.012075] Initializing cgroup subsys memory
[    0.012083] Initializing cgroup subsys devices
[    0.012085] Initializing cgroup subsys freezer
[    0.012088] Initializing cgroup subsys net_cls
[    0.012091] Initializing cgroup subsys perf_event
[    0.012093] Initializing cgroup subsys net_prio
[    0.012095] Initializing cgroup subsys hugetlb
[    0.012114] CPU: Physical Processor ID: 0
[    0.012115] CPU: Processor Core ID: 0
[    0.012120] mce: CPU supports 6 MCE banks
[    0.012126] CPU0: Thermal monitoring enabled (TM2)
[    0.012129] process: using mwait in idle threads
[    0.012136] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.012137] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.012649] Freeing SMP alternatives memory: 28K (c1bfe000 - c1c05000)
[    0.016006] ftrace: allocating 30221 entries in 60 pages
[    0.024098] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024464] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068000] smpboot: CPU0: Intel Pentium(R) Dual-Core  CPU      E5700  @ 3.00GHz (fam: 06, model: 17, stepping: 0a)
[    0.068000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.068000] ... version:                2
[    0.068000] ... bit width:              40
[    0.068000] ... generic registers:      2
[    0.068000] ... value mask:             000000ffffffffff
[    0.068000] ... max period:             000000007fffffff
[    0.068000] ... fixed-purpose events:   3
[    0.068000] ... event mask:             0000000700000003
[    0.068000] CPU 1 irqstacks, hard=f3d76000 soft=f3d78000
[    0.068000] x86: Booting SMP configuration:
[    0.068000] .... node  #0, CPUs:      #1
[    0.008000] Initializing CPU#1
[    0.068038] x86: Booted up 1 node, 2 CPUs
[    0.068041] smpboot: Total of 2 processors activated (12000.53 BogoMIPS)
[    0.069327] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.069386] devtmpfs: initialized
[    0.069386] evm: security.selinux
[    0.069386] evm: security.SMACK64
[    0.069386] evm: security.SMACK64EXEC
[    0.069386] evm: security.SMACK64TRANSMUTE
[    0.069386] evm: security.SMACK64MMAP
[    0.069386] evm: security.ima
[    0.069386] evm: security.capability
[    0.069386] PM: Registering ACPI NVS region [mem 0x7dd9e000-0x7dddffff] (270336 bytes)
[    0.069386] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.069386] pinctrl core: initialized pinctrl subsystem
[    0.069386] RTC time:  2:02:18, date: 12/27/15
[    0.069386] NET: Registered protocol family 16
[    0.069386] EISA bus registered
[    0.080010] cpuidle: using governor ladder
[    0.092006] cpuidle: using governor menu
[    0.092138] ACPI: bus type PCI registered
[    0.092141] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.092209] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.092211] PCI: not using MMCONFIG
[    0.092347] PCI: Using configuration type 1 for base access
[    0.104095] ACPI: Added _OSI(Module Device)
[    0.104097] ACPI: Added _OSI(Processor Device)
[    0.104098] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.104099] ACPI: Added _OSI(Processor Aggregator Device)
[    0.105762] ACPI: Executed 1 blocks of module-level executable AML code
[    0.107580] ACPI: Dynamic OEM Table Load:
[    0.107586] ACPI: SSDT 0x00000000F3DC9800 0002B9 (v01 DpgPmm P001Ist  00000011 INTL 20051117)
[    0.108344] ACPI: Dynamic OEM Table Load:
[    0.108349] ACPI: SSDT 0x00000000F3DC9C00 0002B9 (v01 DpgPmm P002Ist  00000012 INTL 20051117)
[    0.108793] ACPI: Interpreter enabled
[    0.108803] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.108806] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20150619/hwxface-580)
[    0.108815] ACPI: (supports S0 S1 S4 S5)
[    0.108816] ACPI: Using IOAPIC for interrupt routing
[    0.108833] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.109859] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.109861] PCI: Using MMCONFIG for extended config space
[    0.109873] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.115210] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.115215] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.115219] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.115422] PCI host bridge to bus 0000:00
[    0.115425] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.115428] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.115429] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.115431] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.115433] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff window]
[    0.115435] pci_bus 0000:00: root bus resource [mem 0x7de00000-0xdfffffff window]
[    0.115437] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xffffffff window]
[    0.115445] pci 0000:00:00.0: [8086:2e30] type 00 class 0x060000
[    0.115470] DMAR: Forcing write-buffer flush capability
[    0.115471] DMAR: Disabling IOMMU for graphics on this chipset
[    0.115537] pci 0000:00:02.0: [8086:2e32] type 00 class 0x030000
[    0.115552] pci 0000:00:02.0: reg 0x10: [mem 0xfe400000-0xfe7fffff 64bit]
[    0.115559] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.115564] pci 0000:00:02.0: reg 0x20: [io  0xdc00-0xdc07]
[    0.115669] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.115693] pci 0000:00:1b.0: reg 0x10: [mem 0xfeaf8000-0xfeafbfff 64bit]
[    0.115745] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.115819] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.115874] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.115912] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.115956] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.116022] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.116063] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.116106] pci 0000:00:1c.2: [8086:27d4] type 01 class 0x060400
[    0.116161] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.116198] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.116244] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.116282] pci 0000:00:1d.0: reg 0x20: [io  0xd880-0xd89f]
[    0.116344] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.116388] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.116425] pci 0000:00:1d.1: reg 0x20: [io  0xd800-0xd81f]
[    0.116487] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.116530] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.116568] pci 0000:00:1d.2: reg 0x20: [io  0xd480-0xd49f]
[    0.116630] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.116672] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.116710] pci 0000:00:1d.3: reg 0x20: [io  0xd400-0xd41f]
[    0.116770] pci 0000:00:1d.3: System wakeup disabled by ACPI
[    0.116819] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.116843] pci 0000:00:1d.7: reg 0x10: [mem 0xfeaf7c00-0xfeaf7fff]
[    0.116903] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.116939] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.116983] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.117050] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.117096] pci 0000:00:1f.0: [8086:27b8] type 00 class 0x060100
[    0.117176] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0800-0x087f]: address conflict with ACPI CPU throttle [io  0x0810-0x0815]
[    0.117180] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
[    0.117183] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.117186] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0a00 (mask 0017)
[    0.117189] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 00ff)
[    0.117268] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.117281] pci 0000:00:1f.1: reg 0x10: [io  0x0000-0x0007]
[    0.117289] pci 0000:00:1f.1: reg 0x14: [io  0x0000-0x0003]
[    0.117297] pci 0000:00:1f.1: reg 0x18: [io  0x08f0-0x08f7]
[    0.117306] pci 0000:00:1f.1: reg 0x1c: [io  0x08f8-0x08fb]
[    0.117314] pci 0000:00:1f.1: reg 0x20: [io  0xffa0-0xffaf]
[    0.117331] pci 0000:00:1f.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.117333] pci 0000:00:1f.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.117334] pci 0000:00:1f.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.117336] pci 0000:00:1f.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.117406] pci 0000:00:1f.2: [8086:27c0] type 00 class 0x01018f
[    0.117422] pci 0000:00:1f.2: reg 0x10: [io  0xd080-0xd087]
[    0.117429] pci 0000:00:1f.2: reg 0x14: [io  0xd000-0xd003]
[    0.117436] pci 0000:00:1f.2: reg 0x18: [io  0xcc00-0xcc07]
[    0.117443] pci 0000:00:1f.2: reg 0x1c: [io  0xc880-0xc883]
[    0.117450] pci 0000:00:1f.2: reg 0x20: [io  0xc800-0xc80f]
[    0.117476] pci 0000:00:1f.2: PME# supported from D3hot
[    0.117550] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.117598] pci 0000:00:1f.3: reg 0x20: [io  0x0400-0x041f]
[    0.117720] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.117786] pci 0000:02:00.0: [1969:1062] type 00 class 0x020000
[    0.117827] pci 0000:02:00.0: reg 0x10: [mem 0xfebc0000-0xfebfffff 64bit]
[    0.117839] pci 0000:02:00.0: reg 0x18: [io  0xec00-0xec7f]
[    0.117914] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.124027] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.124035] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.124042] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.124132] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.124243] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.124251] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.124253] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.124255] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.124257] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff window] (subtractive decode)
[    0.124259] pci 0000:00:1e.0:   bridge window [mem 0x7de00000-0xdfffffff window] (subtractive decode)
[    0.124263] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xffffffff window] (subtractive decode)
[    0.124283] pci_bus 0000:00: on NUMA node 0
[    0.125007] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.125055] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.125102] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *6 7 10 11 12 14 15)
[    0.125149] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.125196] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.125243] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.125290] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.125337] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 *5 7 10 11 12 14 15)
[    0.125390] ACPI: Enabled 2 GPEs in block 00 to 1F
[    0.125474] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.125474] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.125474] vgaarb: loaded
[    0.125474] vgaarb: bridge control possible 0000:00:02.0
[    0.125474] SCSI subsystem initialized
[    0.125474] libata version 3.00 loaded.
[    0.125474] ACPI: bus type USB registered
[    0.125474] usbcore: registered new interface driver usbfs
[    0.125474] usbcore: registered new interface driver hub
[    0.125474] usbcore: registered new device driver usb
[    0.125474] PCI: Using ACPI for IRQ routing
[    0.131426] PCI: pci_cache_line_size set to 64 bytes
[    0.131463] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.131465] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.131467] e820: reserve RAM buffer [mem 0x7dd90000-0x7fffffff]
[    0.131591] NetLabel: Initializing
[    0.131592] NetLabel:  domain hash size = 128
[    0.131593] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.131604] NetLabel:  unlabeled traffic allowed by default
[    0.131629] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.131629] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.131629] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.133012] clocksource: Switched to clocksource hpet
[    0.140121] AppArmor: AppArmor Filesystem Enabled
[    0.140224] pnp: PnP ACPI init
[    0.140330] system 00:00: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.140332] system 00:00: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.140337] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.140415] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.140597] pnp 00:02: [dma 0 disabled]
[    0.140651] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.140819] pnp 00:03: [dma 0 disabled]
[    0.140883] pnp 00:03: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.141167] pnp 00:04: [dma 0 disabled]
[    0.141258] pnp 00:04: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.141367] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.141369] system 00:05: [io  0x0800-0x087f] could not be reserved
[    0.141371] system 00:05: [io  0x0480-0x04bf] has been reserved
[    0.141374] system 00:05: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.141376] system 00:05: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.141378] system 00:05: [mem 0xffa00000-0xffffffff] could not be reserved
[    0.141381] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.141467] system 00:06: [mem 0xffc00000-0xffefffff] has been reserved
[    0.141471] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.141568] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.141571] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.141574] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.141698] system 00:08: [io  0x0a00-0x0adf] has been reserved
[    0.141701] system 00:08: [io  0x0ae0-0x0aef] has been reserved
[    0.141703] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.141771] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.141774] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.141937] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.141940] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.141942] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.141944] system 00:0a: [mem 0x00100000-0x7ddfffff] could not be reserved
[    0.141947] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.142052] pnp: PnP ACPI: found 11 devices
[    0.142057] PnPBIOS: Disabled by ACPI PNP
[    0.178768] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.178785] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    0.178789] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000 add_align 100000
[    0.178791] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000 add_align 100000
[    0.178799] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000 add_align 100000
[    0.178806] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.178808] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000 add_align 100000
[    0.178811] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000 add_align 100000
[    0.178821] pci 0000:00:1f.0: BAR 13: [io  size 0x0080] has bogus alignment
[    0.178824] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.178826] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.178828] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.178830] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.178833] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.178835] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.178837] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.178839] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.178841] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.178843] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.178845] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.178847] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.178849] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.178851] pci 0000:00:1c.2: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.178858] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.178864] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.178869] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.178871] pci 0000:00:1c.2: BAR 14: assigned [mem 0x80600000-0x807fffff]
[    0.178876] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80800000-0x809fffff 64bit pref]
[    0.178879] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.178882] pci 0000:00:1c.2: BAR 13: assigned [io  0x2000-0x2fff]
[    0.178884] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.178886] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.178891] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.178894] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.178899] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.178901] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.178905] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.178909] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.178914] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.178916] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.178920] pci 0000:00:1c.2:   bridge window [mem 0x80600000-0x807fffff]
[    0.178923] pci 0000:00:1c.2:   bridge window [mem 0x80800000-0x809fffff 64bit pref]
[    0.178928] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.178938] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.178940] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.178941] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.178943] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.178945] pci_bus 0000:00: resource 8 [mem 0x7de00000-0xdfffffff window]
[    0.178947] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xffffffff window]
[    0.178949] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.178950] pci_bus 0000:01: resource 1 [mem 0x80000000-0x801fffff]
[    0.178952] pci_bus 0000:01: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.178954] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.178956] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.178957] pci_bus 0000:02: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.178959] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.178961] pci_bus 0000:03: resource 1 [mem 0x80600000-0x807fffff]
[    0.178963] pci_bus 0000:03: resource 2 [mem 0x80800000-0x809fffff 64bit pref]
[    0.178965] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7 window]
[    0.178966] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff window]
[    0.178968] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.178970] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.178972] pci_bus 0000:04: resource 8 [mem 0x7de00000-0xdfffffff window]
[    0.178974] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xffffffff window]
[    0.179005] NET: Registered protocol family 2
[    0.179200] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.179217] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.179249] TCP: Hash tables configured (established 8192 bind 8192)
[    0.179287] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.179295] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.179342] NET: Registered protocol family 1
[    0.179358] pci 0000:00:02.0: Video device with shadowed ROM
[    0.179932] PCI: CLS 32 bytes, default 64
[    0.179984] Trying to unpack rootfs image as initramfs...
[    0.683261] Freeing initrd memory: 32080K (f4148000 - f609c000)
[    0.683577] microcode: CPU0 sig=0x1067a, pf=0x1, revision=0xa07
[    0.683582] microcode: CPU1 sig=0x1067a, pf=0x1, revision=0xa07
[    0.683661] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.683759] Scanning for low memory corruption every 60 seconds
[    0.684124] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.684171] Initialise system trusted keyring
[    0.684200] audit: initializing netlink subsys (disabled)
[    0.684226] audit: type=2000 audit(1451181738.684:1): initialized
[    0.684534] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.686434] zpool: loaded
[    0.686436] zbud: loaded
[    0.686507] VFS: Disk quotas dquot_6.6.0
[    0.686551] VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.687062] fuse init (API version 7.23)
[    0.687223] Key type big_key registered
[    0.687475] Key type asymmetric registered
[    0.687477] Asymmetric key parser 'x509' registered
[    0.687491] bounce: pool size: 64 pages
[    0.687528] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.687557] io scheduler noop registered
[    0.687560] io scheduler deadline registered (default)
[    0.687596] io scheduler cfq registered
[    0.687700] pcieport 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.687989] pcieport 0000:00:1c.2: enabling device (0104 -> 0107)
[    0.688142] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.688152] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.688186] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.688187] vesafb: scrolling: redraw
[    0.688189] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.688206] vesafb: framebuffer at 0xd0000000, mapped to 0xf8600000, using 3072k, total 3072k
[    0.688308] Console: switching to colour frame buffer device 128x48
[    0.688329] fb0: VESA VGA frame buffer device
[    0.688346] intel_idle: does not run on family 6 model 23
[    0.688428] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.688433] ACPI: Power Button [PWRB]
[    0.688476] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.688479] ACPI: Power Button [PWRF]
[    0.688626] GHES: HEST is not enabled!
[    0.688650] isapnp: Scanning for PnP cards...
[    0.696030] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.716383] 00:02: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.736750] 00:03: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
[    0.738285] Linux agpgart interface v0.103
[    0.738361] agpgart-intel 0000:00:00.0: Intel G41 Chipset
[    0.738377] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.738806] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.738924] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.741307] brd: module loaded
[    0.742312] loop: module loaded
[    0.742481] ata_piix 0000:00:1f.1: version 2.13
[    0.743509] scsi host0: ata_piix
[    0.743592] scsi host1: ata_piix
[    0.743634] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.743636] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.743700] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.744753] scsi host2: ata_piix
[    0.744827] scsi host3: ata_piix
[    0.744871] ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
[    0.744873] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
[    0.744968] libphy: Fixed MDIO Bus: probed
[    0.744970] tun: Universal TUN/TAP device driver, 1.6
[    0.744971] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.745020] PPP generic driver version 2.4.2
[    0.745094] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.745099] ehci-pci: EHCI PCI platform driver
[    0.745187] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.745194] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.745205] ehci-pci 0000:00:1d.7: debug port 1
[    0.749111] ehci-pci 0000:00:1d.7: cache line size of 32 is not supported
[    0.749124] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfeaf7c00
[    0.760012] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.760065] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.760067] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.760071] usb usb1: Product: EHCI Host Controller
[    0.760072] usb usb1: Manufacturer: Linux 4.2.0-22-generic ehci_hcd
[    0.760074] usb usb1: SerialNumber: 0000:00:1d.7
[    0.760217] hub 1-0:1.0: USB hub found
[    0.760227] hub 1-0:1.0: 8 ports detected
[    0.760469] ehci-platform: EHCI generic platform driver
[    0.760481] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.760485] ohci-pci: OHCI PCI platform driver
[    0.760497] ohci-platform: OHCI generic platform driver
[    0.760506] uhci_hcd: USB Universal Host Controller Interface driver
[    0.760572] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.760577] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.760582] uhci_hcd 0000:00:1d.0: detected 2 ports
[    0.760599] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    0.760644] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.760646] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.760648] usb usb2: Product: UHCI Host Controller
[    0.760650] usb usb2: Manufacturer: Linux 4.2.0-22-generic uhci_hcd
[    0.760651] usb usb2: SerialNumber: 0000:00:1d.0
[    0.760752] hub 2-0:1.0: USB hub found
[    0.760758] hub 2-0:1.0: 2 ports detected
[    0.760904] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.760909] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.760914] uhci_hcd 0000:00:1d.1: detected 2 ports
[    0.760930] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.760975] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.760977] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.760979] usb usb3: Product: UHCI Host Controller
[    0.760980] usb usb3: Manufacturer: Linux 4.2.0-22-generic uhci_hcd
[    0.760982] usb usb3: SerialNumber: 0000:00:1d.1
[    0.761083] hub 3-0:1.0: USB hub found
[    0.761089] hub 3-0:1.0: 2 ports detected
[    0.761231] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.761236] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.761241] uhci_hcd 0000:00:1d.2: detected 2 ports
[    0.761262] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    0.761306] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.761308] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.761310] usb usb4: Product: UHCI Host Controller
[    0.761312] usb usb4: Manufacturer: Linux 4.2.0-22-generic uhci_hcd
[    0.761313] usb usb4: SerialNumber: 0000:00:1d.2
[    0.761416] hub 4-0:1.0: USB hub found
[    0.761423] hub 4-0:1.0: 2 ports detected
[    0.761563] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.761568] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.761573] uhci_hcd 0000:00:1d.3: detected 2 ports
[    0.761594] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
[    0.761640] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.761642] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.761643] usb usb5: Product: UHCI Host Controller
[    0.761645] usb usb5: Manufacturer: Linux 4.2.0-22-generic uhci_hcd
[    0.761646] usb usb5: SerialNumber: 0000:00:1d.3
[    0.761743] hub 5-0:1.0: USB hub found
[    0.761751] hub 5-0:1.0: 2 ports detected
[    0.761893] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.762233] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.762237] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.762368] mousedev: PS/2 mouse device common for all mice
[    0.762493] rtc_cmos 00:01: RTC can wake from S4
[    0.762600] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.762621] rtc_cmos 00:01: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.762632] i2c /dev entries driver
[    0.762694] device-mapper: uevent: version 1.0.3
[    0.762761] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.762785] platform eisa.0: Probing EISA bus 0
[    0.762787] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.762789] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.762791] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.762793] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.762794] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.762796] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.762798] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.762799] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.762801] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.762803] platform eisa.0: EISA: Detected 0 cards
[    0.762818] cpufreq-nforce2: No nForce2 chipset.
[    0.762827] ledtrig-cpu: registered to indicate activity on CPUs
[    0.762839] PCCT header not found.
[    0.763080] NET: Registered protocol family 10
[    0.763306] NET: Registered protocol family 17
[    0.763321] Key type dns_resolver registered
[    0.763519] Using IPI No-Shortcut mode
[    0.763646] Loading compiled-in X.509 certificates
[    0.766395] Loaded X.509 cert 'Build time autogenerated kernel key: 8c4ea24b55ccc9a8820b17318bf610192f8689ea'
[    0.766410] registered taskstats version 1
[    0.766427] zswap: loading zswap
[    0.766429] zswap: using zbud pool
[    0.766433] zswap: using lzo compressor
[    0.768528] Key type trusted registered
[    0.771896] Key type encrypted registered
[    0.771903] AppArmor: AppArmor sha1 policy hashing enabled
[    0.771906] ima: No TPM chip found, activating TPM-bypass!
[    0.771930] evm: HMAC attrs: 0x1
[    0.772182]   Magic number: 11:237:6
[    0.772286] rtc_cmos 00:01: setting system clock to 2015-12-27 02:02:18 UTC (1451181738)
[    0.772690] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.772692] EDD information not available.
[    0.772747] PM: Hibernation image not present or could not be loaded.
[    0.915083] ata4.01: NODEV after polling detection
[    0.920267] ata4.00: ATAPI: ATAPI   iHAS124   B, AL0Q, max UDMA/100
[    0.920339] ata3.00: ATA-8: ST3500413AS, JC45, max UDMA/133
[    0.920341] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.920617] ata3.01: ATA-8: ST2000DL003-9VT166, CC32, max UDMA/133
[    0.920619] ata3.01: 3907029168 sectors, multi 16: LBA48 
[    0.936117] ata4.00: configured for UDMA/100
[    0.936484] ata3.00: configured for UDMA/133
[    0.952363] ata3.01: configured for UDMA/133
[    0.998153] isapnp: No Plug & Play device found
[    0.998255] scsi 2:0:0:0: Direct-Access     ATA      ST3500413AS      JC45 PQ: 0 ANSI: 5
[    0.998414] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.998456] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    0.998457] sd 2:0:0:0: [sda] Write Protect is off
[    0.998459] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.998478] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.998544] scsi 2:0:1:0: Direct-Access     ATA      ST2000DL003-9VT1 CC32 PQ: 0 ANSI: 5
[    0.998714] sd 2:0:1:0: Attached scsi generic sg1 type 0
[    1.002105] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS124   B      AL0Q PQ: 0 ANSI: 5
[    1.018055] sd 2:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.020894] sr 3:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.020899] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.021102] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.021161] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.043601]  sda: sda1 sda2 < sda5 >
[    1.043690] sd 2:0:1:0: [sdb] Write Protect is off
[    1.043697] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.043739] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.044217]  sdb: sdb1
[    1.044269] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.044510] sd 2:0:1:0: [sdb] Attached SCSI disk
[    1.044839] Freeing unused kernel memory: 928K (c1b16000 - c1bfe000)
[    1.044885] Write protecting the kernel text: 7580k
[    1.044910] Write protecting the kernel read-only data: 3024k
[    1.044911] NX-protecting the kernel data: 4708k
[    1.062212] random: systemd-udevd urandom read with 20 bits of entropy available
[    1.119060] [drm] Initialized drm 1.1.0 20060810
[    1.148407] atl1c 0000:02:00.0: version 1.0.1.1-NAPI
[    1.177405] [drm] Memory usable by graphics device = 2048M
[    1.177410] checking generic (d0000000 300000) vs hw (d0000000 10000000)
[    1.177412] fb: switching to inteldrmfb from VESA VGA
[    1.177446] Console: switching to colour dummy device 80x25
[    1.177547] [drm] Replacing VGA console driver
[    1.184090] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.184093] [drm] Driver supports precise vblank timestamp query.
[    1.184163] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.187406] i915: No ACPI video bus found
[    1.187454] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    1.220058] usb 2-1: new low-speed USB device number 2 using uhci_hcd
[    1.279330] fbcon: inteldrmfb (fb0) is primary device
[    1.279406] Console: switching to colour frame buffer device 170x48
[    1.279437] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.279439] i915 0000:00:02.0: registered panic notifier
[    1.397071] usb 2-1: New USB device found, idVendor=1d57, idProduct=0001
[    1.397081] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.397089] usb 2-1: Product: 2.4G Mouse
[    1.397093] usb 2-1: Manufacturer: 2.4G KB
[    1.516027] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    1.628023] usb 4-2: new full-speed USB device number 2 using uhci_hcd
[    1.640039] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    1.680020] tsc: Refined TSC clocksource calibration: 2999.963 MHz
[    1.680027] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2b3e2274cba, max_idle_ns: 440795224466 ns
[    1.772048] usb 3-2: New USB device found, idVendor=04d9, idProduct=1503
[    1.772055] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.772059] usb 3-2: Product: USB Keyboard
[    1.772064] usb 3-2: Manufacturer:  
[    1.785113] hidraw: raw HID events driver (C) Jiri Kosina
[    1.791136] usb 4-2: New USB device found, idVendor=05a9, idProduct=0511
[    1.791145] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.793445] random: nonblocking pool is initialized
[    1.800043] usb 2-2: New USB device found, idVendor=0c76, idProduct=160c
[    1.800052] usb 2-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.800060] usb 2-2: Product: USB Speaker
[    1.945565] usbcore: registered new interface driver usbhid
[    1.945569] usbhid: USB HID core driver
[    1.949791] input: 2.4G KB 2.4G Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/0003:1D57:0001.0001/input/input5
[    2.004220] hid-generic 0003:1D57:0001.0001: input,hidraw0: USB HID v1.10 Keyboard [2.4G KB 2.4G Mouse] on usb-0000:00:1d.0-1/input0
[    2.006225] input: USB Speaker as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.2/0003:0C76:160C.0002/input/input6
[    2.060192] hid-generic 0003:0C76:160C.0002: input,hidraw1: USB HID v1.00 Device [USB Speaker] on usb-0000:00:1d.0-2/input2
[    2.060976] input: 2.4G KB 2.4G Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/0003:1D57:0001.0003/input/input7
[    2.116257] hid-generic 0003:1D57:0001.0003: input,hidraw2: USB HID v1.10 Mouse [2.4G KB 2.4G Mouse] on usb-0000:00:1d.0-1/input1
[    2.116641] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/0003:04D9:1503.0004/input/input8
[    2.172199] hid-generic 0003:04D9:1503.0004: input,hidraw3: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.1-2/input0
[    2.184173] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/0003:04D9:1503.0005/input/input9
[    2.240212] hid-generic 0003:04D9:1503.0005: input,hidraw4: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.1-2/input1
[    2.680096] clocksource: Switched to clocksource tsc
[    4.140042] floppy0: no floppy controllers found
[    9.288369] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.309366] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[   10.442667] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[   10.442791] systemd[1]: Detected architecture x86.
[   10.453494] systemd[1]: Set hostname to <BKC-Media>.
[   11.814636] systemd[1]: Reached target Encrypted Volumes.
[   11.814710] systemd[1]: Created slice Root Slice.
[   11.814744] systemd[1]: Listening on Device-mapper event daemon FIFOs.
[   11.814779] systemd[1]: Listening on udev Kernel Socket.
[   11.814817] systemd[1]: Listening on Journal Socket (/dev/log).
[   11.814857] systemd[1]: Listening on Journal Socket.
[   11.814906] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   11.814985] systemd[1]: Listening on Journal Audit Socket.
[   11.815022] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   11.815033] systemd[1]: Reached target Remote File Systems (Pre).
[   11.815066] systemd[1]: Listening on udev Control Socket.
[   11.815154] systemd[1]: Created slice User and Session Slice.
[   11.815288] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   11.815317] systemd[1]: Listening on fsck to fsckd communication Socket.
[   11.815329] systemd[1]: Reached target User and Group Name Lookups.
[   11.815403] systemd[1]: Created slice System Slice.
[   11.816023] systemd[1]: Started Braille Device Support.
[   11.816822] systemd[1]: Mounting Huge Pages File System...
[   11.816953] systemd[1]: Created slice system-getty.slice.
[   11.949699] systemd[1]: Reached target Slices.
[   11.950428] systemd[1]: Starting Uncomplicated firewall...
[   11.951964] systemd[1]: Starting udev Coldplug all Devices...
[   11.952654] systemd[1]: Started Read required files in advance.
[   11.953337] systemd[1]: Starting Setup Virtual Console...
[   12.098035] systemd[1]: Starting Load Kernel Modules...
[   12.098708] systemd[1]: Mounting Debug File System...
[   12.099359] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   12.099934] systemd[1]: Starting Increase datagram queue length...
[   12.101118] systemd[1]: Mounting POSIX Message Queue File System...
[   12.102627] systemd[1]: Started Setup Virtual Console.
[   12.217444] systemd[1]: Started Uncomplicated firewall.
[   12.447346] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   12.448250] systemd[1]: Starting Create Static Device Nodes in /dev...
[   12.526291] systemd[1]: Started udev Coldplug all Devices.
[   12.635053] systemd[1]: Mounted Huge Pages File System.
[   12.635100] systemd[1]: Mounted Debug File System.
[   12.635120] systemd[1]: Mounted POSIX Message Queue File System.
[   12.636073] systemd[1]: Started Increase datagram queue length.
[   12.643395] systemd[1]: Listening on Syslog Socket.
[   12.644078] systemd[1]: Starting Journal Service...
[   12.820436] lp: driver loaded but no devices found
[   12.877271] ppdev: user-space parallel port driver
[   12.907209] parport_pc 00:04: reported by Plug and Play ACPI
[   12.907275] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   13.004204] lp0: using parport0 (interrupt-driven).
[   13.042845] systemd[1]: Started Load Kernel Modules.
[   13.043696] systemd[1]: Starting Apply Kernel Variables...
[   13.044309] systemd[1]: Mounting FUSE Control File System...
[   13.048776] systemd[1]: Mounted FUSE Control File System.
[   13.369230] systemd[1]: Started Journal Service.
[   14.316393] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.560183] systemd-journald[228]: Received request to flush runtime journal from PID 1
[   14.998589] intel_rng: FWH not detected
[   15.005592] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.197917] ACPI Warning: SystemIO range 0x0000000000000828-0x000000000000082F conflicts with OpRegion 0x0000000000000800-0x000000000000084F (\PMRG) (20150619/utaddress-254)
[   15.197925] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.197961] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   15.491665] leds_ss4200: no LED devices found
[   16.072687] gpio_ich: GPIO from 462 to 511 on gpio_ich
[   16.172211] snd_hda_codec_via hdaudioC0D0: autoconfig for VT1708S: line_outs=1 (0x1c/0x0/0x0/0x0/0x0) type:line
[   16.172215] snd_hda_codec_via hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.172218] snd_hda_codec_via hdaudioC0D0:    hp_outs=1 (0x1d/0x0/0x0/0x0/0x0)
[   16.172219] snd_hda_codec_via hdaudioC0D0:    mono: mono_out=0x0
[   16.172221] snd_hda_codec_via hdaudioC0D0:    dig-out=0x20/0x0
[   16.172222] snd_hda_codec_via hdaudioC0D0:    inputs:
[   16.172225] snd_hda_codec_via hdaudioC0D0:      Rear Mic=0x1a
[   16.172227] snd_hda_codec_via hdaudioC0D0:      Front Mic=0x1e
[   16.172228] snd_hda_codec_via hdaudioC0D0:      Line=0x1b
[   16.172230] snd_hda_codec_via hdaudioC0D0:      CD=0x1f
[   16.179117] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.179190] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.179256] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   16.179324] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   16.179390] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   16.541341] usbcore: registered new interface driver snd-usb-audio
[   17.431430] Adding 2058236k swap on /dev/sda5.  Priority:-1 extents:1 across:2058236k FS
[   17.680724] media: Linux media interface: v0.10
[   17.732728] Linux video capture interface: v2.00
[   17.776416] gspca_main: v2.14.0 registered
[   17.819508] gspca_main: ov519-2.14.0 probing 05a9:0511
[   17.972045] floppy0: no floppy controllers found
[   18.214282] input: ov519 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/input/input15
[   18.214497] usbcore: registered new interface driver ov519
[   20.865809] audit: type=1400 audit(1451181758.587:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=554 comm="apparmor_parser"
[   20.865821] audit: type=1400 audit(1451181758.587:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=554 comm="apparmor_parser"
[   20.870539] audit: type=1400 audit(1451181758.591:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=554 comm="apparmor_parser"
[   20.870549] audit: type=1400 audit(1451181758.591:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=554 comm="apparmor_parser"
[   20.870554] audit: type=1400 audit(1451181758.591:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=554 comm="apparmor_parser"
[   20.870558] audit: type=1400 audit(1451181758.591:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=554 comm="apparmor_parser"
[   20.999044] audit: type=1400 audit(1451181758.719:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=554 comm="apparmor_parser"
[   20.999062] audit: type=1400 audit(1451181758.719:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=554 comm="apparmor_parser"
[   20.999068] audit: type=1400 audit(1451181758.719:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=554 comm="apparmor_parser"
[   20.999074] audit: type=1400 audit(1451181758.719:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=554 comm="apparmor_parser"
[   23.193551] cgroup: new mount options do not match the existing superblock, will be ignored
[   31.867266] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.867726] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   37.826618] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[   37.829179] vboxdrv: Found 2 processor cores
[   37.829419] vboxdrv: fAsync=0 offMin=0x20d offMax=0x12b1
[   37.929564] vboxdrv: TSC mode is Synchronous, tentative frequency 2999963190 Hz
[   37.929568] vboxdrv: Successfully loaded version 5.0.10_Ubuntu (interface 0x00240000)
[   37.991550] VBoxNetFlt: Successfully started.
[   38.037282] VBoxNetAdp: Successfully started.
[   38.184762] VBoxPciLinuxInit
[   38.300061] vboxpci: IOMMU not found (not registered)
[   38.605743] Guest personality initialized and is inactive
[   38.605810] VMCI host device registered (name=vmci, major=10, minor=53)
[   38.605811] Initialized host personality
[   38.881694] NET: Registered protocol family 40
[   76.140057] ip_tables: (C) 2000-2006 Netfilter Core Team
[  545.988053] perf interrupt took too long (2503 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 2776.267475] perf interrupt took too long (5002 > 5000), lowering kernel.perf_event_max_sample_rate to 25000

```

boot.log.zip attached

It'll take 45 min to reboot to get the bootchart...

---

### Post by BarryD9545 on 2015-12-27
Over an hour and still waiting...

var/log/bootchart/ doesn't have any file in it at all.

Several attempts, no file in [COLOR=#000000]var/log/bootchart[/COLOR]

---

### Post by QIII on 2015-12-27
What sort of media are you mounting at /media/barry/ and how is it connected to your machine?

---

### Post by BarryD9545 on 2015-12-27
It's an eSATA HDD.

Been attached as is since I built the machine 3 years ago.

---

### Post by pqwoerituytrueiwoq on 2015-12-27
did you install bootchart, you are looking in [FONT=courier new]**/**var/log/bootchart[/FONT] right?
given the very long boot time it may take a while for it to appear in there

from the dmesg output, you can disable ipv6 and save 10 seconds
edit [FONT=Courier New]/etc/default/grub[/FONT]
and do this [https://farm8.staticflickr.com/7286/15982512103_ec5d940e58_b.jpg](https://farm8.staticflickr.com/7286/15982512103_ec5d940e58_b.jpg)
you have some netflix stuff that is taking around 40 seconds, i don't see why you should need some special iptables to use netflix anyway (special routing to bypass country limitations?)
the big issue is
```
[  545.988053] perf interrupt took too long (2503 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 2776.267475] perf interrupt took too long (5002 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
```
im not sure how to fix this but i would guess the easiest way to fix that would be to set kernel.perf_event_max_sample_rate to 25000 well before it has to try to detect it
another way would be to try a new kernel

if it only recently started taking this long try a older kernel [[relevant info]("http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time")] or you can try a new kernel, this makes it newbie easy to do
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

---

### Post by BarryD9545 on 2015-12-27
That's where I'm looking.

Dunno why it's loading NetFlix stuff, it's on a desktop system in Florida (plus I have a slingbox).

10 and 20 seconds here and there doesn't mean anything to me at this point, it's taking 45min to an hour to start.

I'll give the kernel updater a try...

---

### Post by BarryD9545 on 2015-12-27
Kernel Updater didn't wreck anything, and it looks like I'm down to 30 minute boots.

How would I remove the Netflix items that were loading?

---

### Post by pqwoerituytrueiwoq on 2015-12-28
look at your iptable configuration
why you have special iptable configurations i don't know, the only time i ever had a need for that was when i was using the system as a router to share a uplink cause i did not have a router on the network

[http://askubuntu.com/questions/149629/how-do-i-prevent-iptables-from-loading-on-boot](http://askubuntu.com/questions/149629/how-do-i-prevent-iptables-from-loading-on-boot)

post a updated dmesg output, the netflix thing should only save around 1 minute and 10 seconds (but just *maybe* it is causing the bigger issue)
just looked at the boot.log, what video chip are you using? (it appears to be doing the same thing over and over for around 40 minutes)
```
lspci -v |grep -i vga -A10
```

---

### Post by BarryD9545 on 2015-12-29
> **pqwoerituytrueiwoq said:**
> look at your iptable configuration
why you have special iptable configurations i don't know, the only time i ever had a need for that was when i was using the system as a router to share a uplink cause i did not have a router on the network

[http://askubuntu.com/questions/149629/how-do-i-prevent-iptables-from-loading-on-boot](http://askubuntu.com/questions/149629/how-do-i-prevent-iptables-from-loading-on-boot)
I'm good without the iptable, but I didn't see how to remove it in the link you provided.

Am I missing it?
> **pqwoerituytrueiwoq said:**
> post a updated dmesg output, the netflix thing should only save around 1 minute and 10 seconds (but just *maybe* it is causing the bigger issue)
Here's the dmesg output:
```
barry@BKC-Media:~$ dmesg[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.3.3-040303-generic (kernel@tangerine) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #201512150130 SMP Tue Dec 15 06:46:23 UTC 2015
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Enabled xstate features 0x3, context size is 0x240 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007dd8ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007dd90000-0x000000007dd9dfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007dd9e000-0x000000007dddffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007dde0000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: MSI MS-7592/G41M-P26 (MS-7592), BIOS V26.6 03/02/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7dd90 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07DE00000 mask FFFE00000 uncachable
[    0.000000]   2 base 07E000000 mask FFE000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2014MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2016MB, range: 32MB, type UC
[    0.000000] total RAM covered: 2014M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2014MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2016MB, range: 32MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x021fffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20000000-0x377fffff]
[    0.000000]  [mem 0x20000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01d04000, 0x01d04fff] PGTABLE
[    0.000000] BRK [0x01d05000, 0x01d05fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x34148000-0x3609bfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F99F0 000014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 0x000000007DD90000 000040 (v01 7592MS A7592400 20110302 MSFT 00000097)
[    0.000000] ACPI: FACP 0x000000007DD90200 000084 (v01 7592MS A7592400 20110302 MSFT 00000097)
[    0.000000] ACPI: DSDT 0x000000007DD90440 0062AE (v01 A7592  A7592400 00000400 INTL 20051117)
[    0.000000] ACPI: FACS 0x000000007DD9E000 000040
[    0.000000] ACPI: APIC 0x000000007DD90390 00006C (v01 7592MS A7592400 20110302 MSFT 00000097)
[    0.000000] ACPI: MCFG 0x000000007DD90400 00003C (v01 7592MS OEMMCFG  20110302 MSFT 00000097)
[    0.000000] ACPI: OEMB 0x000000007DD9E040 000072 (v01 7592MS A7592400 20110302 MSFT 00000097)
[    0.000000] ACPI: HPET 0x000000007DD98440 000038 (v01 7592MS OEMHPET  20110302 MSFT 00000097)
[    0.000000] ACPI: GSCI 0x000000007DD9E0C0 002024 (v01 7592MS GMCHSCI  20110302 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x000000007DDA0670 000A7C (v01 DpgPmm CpuPm    00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1121MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   Normal   [mem 0x0000000001000000-0x0000000037bfdfff]
[    0.000000]   HighMem  [mem 0x0000000037bfe000-0x000000007dd8ffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000007dd8ffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000007dd8ffff]
[    0.000000] On node 0 totalpages: 515374
[    0.000000]   DMA zone: 40 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 2190 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 287122 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Reserving Intel graphics stolen memory at 0x7e000000-0x7fffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xfedfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 19 pages/cpu @f678b000 s47052 r0 d30772 u77824
[    0.000000] pcpu-alloc: s47052 r0 d30772 u77824 alloc=19*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 513144
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.3.3-040303-generic root=UUID=751db636-8f58-406f-839c-55db9682d769 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007dd90)
[    0.000000] Initializing Movable for node 0 (00000000:00000000)
[    0.000000] Memory: 1994268K/2061496K available (7624K kernel code, 743K rwdata, 3120K rodata, 924K init, 804K bss, 67228K reserved, 0K cma-reserved, 1148488K highmem)
[    0.000000] virtual kernel memory layout:
                   fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
                   pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
                   vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
                   lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
                     .init : 0xc1b3b000 - 0xc1c22000   ( 924 kB)
                     .data : 0xc1772488 - 0xc1b39dc0   (3870 kB)
                     .text : 0xc1000000 - 0xc1772488   (7625 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 32.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=32, nr_cpu_ids=4
[    0.000000] NR_IRQS:2304 nr_irqs:456 16
[    0.000000] CPU 0 irqstacks, hard=f3c38000 soft=f3c3a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 2097152 bytes of page_ext
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2999.988 MHz processor
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.97 BogoMIPS (lpj=11999952)
[    0.004017] pid_max: default: 32768 minimum: 301
[    0.004030] ACPI: Core revision 20150818
[    0.011798] ACPI: 2 ACPI AML tables successfully acquired and loaded
[    0.011817] Security Framework initialized
[    0.011819] Yama: becoming mindful.
[    0.011833] AppArmor: AppArmor initialized
[    0.011868] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.011870] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.012108] Initializing cgroup subsys io
[    0.012114] Initializing cgroup subsys memory
[    0.012123] Initializing cgroup subsys devices
[    0.012126] Initializing cgroup subsys freezer
[    0.012130] Initializing cgroup subsys net_cls
[    0.012132] Initializing cgroup subsys perf_event
[    0.012135] Initializing cgroup subsys net_prio
[    0.012138] Initializing cgroup subsys hugetlb
[    0.012141] Initializing cgroup subsys pids
[    0.012162] CPU: Physical Processor ID: 0
[    0.012164] CPU: Processor Core ID: 0
[    0.012169] mce: CPU supports 6 MCE banks
[    0.012177] CPU0: Thermal monitoring enabled (TM2)
[    0.012180] process: using mwait in idle threads
[    0.012187] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.012189] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.012733] Freeing SMP alternatives memory: 28K (c1c22000 - c1c29000)
[    0.016006] ftrace: allocating 30478 entries in 60 pages
[    0.024107] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024471] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068000] smpboot: CPU0: Intel Pentium(R) Dual-Core  CPU      E5700  @ 3.00GHz (family: 0x6, model: 0x17, stepping: 0xa)
[    0.068000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.068000] ... version:                2
[    0.068000] ... bit width:              40
[    0.068000] ... generic registers:      2
[    0.068000] ... value mask:             000000ffffffffff
[    0.068000] ... max period:             000000007fffffff
[    0.068000] ... fixed-purpose events:   3
[    0.068000] ... event mask:             0000000700000003
[    0.068000] CPU 1 irqstacks, hard=f3f68000 soft=f3f6a000
[    0.068000] x86: Booting SMP configuration:
[    0.068000] .... node  #0, CPUs:      #1
[    0.008000] Initializing CPU#1
[    0.076035] x86: Booted up 1 node, 2 CPUs
[    0.076039] smpboot: Total of 2 processors activated (11999.95 BogoMIPS)
[    0.076184] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.077427] devtmpfs: initialized
[    0.077427] evm: security.selinux
[    0.077427] evm: security.SMACK64
[    0.077427] evm: security.SMACK64EXEC
[    0.077427] evm: security.SMACK64TRANSMUTE
[    0.077427] evm: security.SMACK64MMAP
[    0.077427] evm: security.ima
[    0.077427] evm: security.capability
[    0.077427] PM: Registering ACPI NVS region [mem 0x7dd9e000-0x7dddffff] (270336 bytes)
[    0.077427] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.080012] pinctrl core: initialized pinctrl subsystem
[    0.080012] RTC time: 12:00:36, date: 12/29/15
[    0.080012] NET: Registered protocol family 16
[    0.080012] EISA bus registered
[    0.088009] cpuidle: using governor ladder
[    0.100005] cpuidle: using governor menu
[    0.100012] PCCT header not found.
[    0.100223] ACPI: bus type PCI registered
[    0.100226] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.100289] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.100291] PCI: not using MMCONFIG
[    0.100418] PCI: Using configuration type 1 for base access
[    0.112089] ACPI: Added _OSI(Module Device)
[    0.112091] ACPI: Added _OSI(Processor Device)
[    0.112093] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.112094] ACPI: Added _OSI(Processor Aggregator Device)
[    0.113791] ACPI: Executed 1 blocks of module-level executable AML code
[    0.116006] ACPI: Dynamic OEM Table Load:
[    0.116011] ACPI: SSDT 0x00000000F3469000 0002B9 (v01 DpgPmm P001Ist  00000011 INTL 20051117)
[    0.116411] ACPI: Dynamic OEM Table Load:
[    0.116415] ACPI: SSDT 0x00000000F3469400 0002B9 (v01 DpgPmm P002Ist  00000012 INTL 20051117)
[    0.116883] ACPI: Interpreter enabled
[    0.116893] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150818/hwxface-580)
[    0.116896] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20150818/hwxface-580)
[    0.116905] ACPI: (supports S0 S1 S4 S5)
[    0.116906] ACPI: Using IOAPIC for interrupt routing
[    0.116932] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.118009] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.118010] PCI: Using MMCONFIG for extended config space
[    0.118014] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.123540] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.123546] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.123550] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.123764] PCI host bridge to bus 0000:00
[    0.123766] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.123769] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.123770] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.123772] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.123774] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff window]
[    0.123776] pci_bus 0000:00: root bus resource [mem 0x7de00000-0xdfffffff window]
[    0.123778] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xffffffff window]
[    0.123786] pci 0000:00:00.0: [8086:2e30] type 00 class 0x060000
[    0.123811] DMAR: Forcing write-buffer flush capability
[    0.123812] DMAR: Disabling IOMMU for graphics on this chipset
[    0.123882] pci 0000:00:02.0: [8086:2e32] type 00 class 0x030000
[    0.123897] pci 0000:00:02.0: reg 0x10: [mem 0xfe400000-0xfe7fffff 64bit]
[    0.123904] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.123909] pci 0000:00:02.0: reg 0x20: [io  0xdc00-0xdc07]
[    0.124024] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.124049] pci 0000:00:1b.0: reg 0x10: [mem 0xfeaf8000-0xfeafbfff 64bit]
[    0.124101] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.124180] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.124235] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.124277] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.124321] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.124381] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.124423] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.124467] pci 0000:00:1c.2: [8086:27d4] type 01 class 0x060400
[    0.124521] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.124564] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.124610] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.124648] pci 0000:00:1d.0: reg 0x20: [io  0xd880-0xd89f]
[    0.124715] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.124758] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.124796] pci 0000:00:1d.1: reg 0x20: [io  0xd800-0xd81f]
[    0.124861] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.124905] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.124942] pci 0000:00:1d.2: reg 0x20: [io  0xd480-0xd49f]
[    0.125007] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.125049] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.125087] pci 0000:00:1d.3: reg 0x20: [io  0xd400-0xd41f]
[    0.125154] pci 0000:00:1d.3: System wakeup disabled by ACPI
[    0.125204] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.125227] pci 0000:00:1d.7: reg 0x10: [mem 0xfeaf7c00-0xfeaf7fff]
[    0.125288] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.125327] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.125371] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.125440] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.125486] pci 0000:00:1f.0: [8086:27b8] type 00 class 0x060100
[    0.125566] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0800-0x087f]: address conflict with ACPI CPU throttle [io  0x0810-0x0815]
[    0.125571] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
[    0.125574] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.125577] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0a00 (mask 0017)
[    0.125580] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 00ff)
[    0.125662] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.125676] pci 0000:00:1f.1: reg 0x10: [io  0x0000-0x0007]
[    0.125684] pci 0000:00:1f.1: reg 0x14: [io  0x0000-0x0003]
[    0.125692] pci 0000:00:1f.1: reg 0x18: [io  0x08f0-0x08f7]
[    0.125700] pci 0000:00:1f.1: reg 0x1c: [io  0x08f8-0x08fb]
[    0.125708] pci 0000:00:1f.1: reg 0x20: [io  0xffa0-0xffaf]
[    0.125726] pci 0000:00:1f.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.125727] pci 0000:00:1f.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.125729] pci 0000:00:1f.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.125730] pci 0000:00:1f.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.125804] pci 0000:00:1f.2: [8086:27c0] type 00 class 0x01018f
[    0.125820] pci 0000:00:1f.2: reg 0x10: [io  0xd080-0xd087]
[    0.125828] pci 0000:00:1f.2: reg 0x14: [io  0xd000-0xd003]
[    0.125835] pci 0000:00:1f.2: reg 0x18: [io  0xcc00-0xcc07]
[    0.125842] pci 0000:00:1f.2: reg 0x1c: [io  0xc880-0xc883]
[    0.125849] pci 0000:00:1f.2: reg 0x20: [io  0xc800-0xc80f]
[    0.125874] pci 0000:00:1f.2: PME# supported from D3hot
[    0.125951] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.126000] pci 0000:00:1f.3: reg 0x20: [io  0x0400-0x041f]
[    0.126127] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.126189] pci 0000:02:00.0: [1969:1062] type 00 class 0x020000
[    0.126231] pci 0000:02:00.0: reg 0x10: [mem 0xfebc0000-0xfebfffff 64bit]
[    0.126243] pci 0000:02:00.0: reg 0x18: [io  0xec00-0xec7f]
[    0.126320] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.132027] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.132035] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.132042] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.132138] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.132245] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.132254] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.132256] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.132258] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.132259] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff window] (subtractive decode)
[    0.132261] pci 0000:00:1e.0:   bridge window [mem 0x7de00000-0xdfffffff window] (subtractive decode)
[    0.132263] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xffffffff window] (subtractive decode)
[    0.132281] pci_bus 0000:00: on NUMA node 0
[    0.133049] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.133101] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.133152] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *6 7 10 11 12 14 15)
[    0.133202] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.133253] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.133304] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.133354] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.133405] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 *5 7 10 11 12 14 15)
[    0.133458] ACPI: Enabled 2 GPEs in block 00 to 1F
[    0.133543] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.133543] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.133543] vgaarb: loaded
[    0.133543] vgaarb: bridge control possible 0000:00:02.0
[    0.133543] SCSI subsystem initialized
[    0.133543] libata version 3.00 loaded.
[    0.133543] ACPI: bus type USB registered
[    0.133543] usbcore: registered new interface driver usbfs
[    0.133543] usbcore: registered new interface driver hub
[    0.133543] usbcore: registered new device driver usb
[    0.133543] PCI: Using ACPI for IRQ routing
[    0.139520] PCI: pci_cache_line_size set to 64 bytes
[    0.139559] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.139561] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.139562] e820: reserve RAM buffer [mem 0x7dd90000-0x7fffffff]
[    0.139688] NetLabel: Initializing
[    0.139689] NetLabel:  domain hash size = 128
[    0.139690] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.139701] NetLabel:  unlabeled traffic allowed by default
[    0.139722] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.139722] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.139722] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.141013] clocksource: Switched to clocksource hpet
[    0.148550] AppArmor: AppArmor Filesystem Enabled
[    0.148652] pnp: PnP ACPI init
[    0.148756] system 00:00: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.148758] system 00:00: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.148763] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.148842] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.149033] pnp 00:02: [dma 0 disabled]
[    0.149087] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.149263] pnp 00:03: [dma 0 disabled]
[    0.149332] pnp 00:03: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.149632] pnp 00:04: [dma 0 disabled]
[    0.149726] pnp 00:04: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.149834] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.149837] system 00:05: [io  0x0800-0x087f] could not be reserved
[    0.149839] system 00:05: [io  0x0480-0x04bf] has been reserved
[    0.149841] system 00:05: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.149843] system 00:05: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.149845] system 00:05: [mem 0xffa00000-0xffffffff] could not be reserved
[    0.149848] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.149938] system 00:06: [mem 0xffc00000-0xffefffff] has been reserved
[    0.149942] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.150041] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.150043] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.150046] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.150176] system 00:08: [io  0x0a00-0x0adf] has been reserved
[    0.150179] system 00:08: [io  0x0ae0-0x0aef] has been reserved
[    0.150182] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.150252] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.150255] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.150424] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.150427] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.150429] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.150431] system 00:0a: [mem 0x00100000-0x7ddfffff] could not be reserved
[    0.150434] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.150547] pnp: PnP ACPI: found 11 devices
[    0.150552] PnPBIOS: Disabled by ACPI PNP
[    0.187185] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.187204] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    0.187208] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000 add_align 100000
[    0.187210] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000 add_align 100000
[    0.187218] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000 add_align 100000
[    0.187225] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.187228] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000 add_align 100000
[    0.187230] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000 add_align 100000
[    0.187239] pci 0000:00:1f.0: BAR 13: [io  size 0x0080] has bogus alignment
[    0.187243] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.187245] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.187247] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.187249] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.187251] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.187254] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.187256] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.187258] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.187260] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.187262] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.187264] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.187266] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.187268] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.187270] pci 0000:00:1c.2: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.187277] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.187282] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.187287] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.187290] pci 0000:00:1c.2: BAR 14: assigned [mem 0x80600000-0x807fffff]
[    0.187294] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80800000-0x809fffff 64bit pref]
[    0.187297] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.187300] pci 0000:00:1c.2: BAR 13: assigned [io  0x2000-0x2fff]
[    0.187302] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.187305] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.187310] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.187313] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.187318] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.187320] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.187325] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.187328] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.187333] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.187335] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.187339] pci 0000:00:1c.2:   bridge window [mem 0x80600000-0x807fffff]
[    0.187343] pci 0000:00:1c.2:   bridge window [mem 0x80800000-0x809fffff 64bit pref]
[    0.187348] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.187357] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.187359] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.187361] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.187362] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.187364] pci_bus 0000:00: resource 8 [mem 0x7de00000-0xdfffffff window]
[    0.187366] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xffffffff window]
[    0.187368] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.187370] pci_bus 0000:01: resource 1 [mem 0x80000000-0x801fffff]
[    0.187371] pci_bus 0000:01: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.187373] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.187375] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.187377] pci_bus 0000:02: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.187378] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.187380] pci_bus 0000:03: resource 1 [mem 0x80600000-0x807fffff]
[    0.187382] pci_bus 0000:03: resource 2 [mem 0x80800000-0x809fffff 64bit pref]
[    0.187384] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7 window]
[    0.187386] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff window]
[    0.187387] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.187389] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.187391] pci_bus 0000:04: resource 8 [mem 0x7de00000-0xdfffffff window]
[    0.187393] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xffffffff window]
[    0.187426] NET: Registered protocol family 2
[    0.187625] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.187643] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.187675] TCP: Hash tables configured (established 8192 bind 8192)
[    0.187711] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.187720] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.187762] NET: Registered protocol family 1
[    0.187778] pci 0000:00:02.0: Video device with shadowed ROM
[    0.187898] PCI: CLS 32 bytes, default 64
[    0.187951] Trying to unpack rootfs image as initramfs...
[    0.704370] Freeing initrd memory: 32080K (f4148000 - f609c000)
[    0.704602] microcode: CPU0 sig=0x1067a, pf=0x1, revision=0xa07
[    0.704609] microcode: CPU1 sig=0x1067a, pf=0x1, revision=0xa07
[    0.704699] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.704746] Scanning for low memory corruption every 60 seconds
[    0.705079] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.705139] audit: initializing netlink subsys (disabled)
[    0.705164] audit: type=2000 audit(1451390436.704:1): initialized
[    0.705403] Initialise system trusted keyring
[    0.705506] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.707318] zbud: loaded
[    0.707420] VFS: Disk quotas dquot_6.6.0
[    0.707465] VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.707959] fuse init (API version 7.23)
[    0.708136] Key type big_key registered
[    0.708466] Key type asymmetric registered
[    0.708469] Asymmetric key parser 'x509' registered
[    0.708487] bounce: pool size: 64 pages
[    0.708527] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.708559] io scheduler noop registered
[    0.708562] io scheduler deadline registered (default)
[    0.708596] io scheduler cfq registered
[    0.708808] pcieport 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.709138] pcieport 0000:00:1c.2: enabling device (0104 -> 0107)
[    0.709268] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.709275] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.709311] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.709312] vesafb: scrolling: redraw
[    0.709313] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.709330] vesafb: framebuffer at 0xd0000000, mapped to 0xf8600000, using 3072k, total 3072k
[    0.741104] Console: switching to colour frame buffer device 128x48
[    0.772751] fb0: VESA VGA frame buffer device
[    0.772769] intel_idle: does not run on family 6 model 23
[    0.772853] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.772857] ACPI: Power Button [PWRB]
[    0.772903] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.772905] ACPI: Power Button [PWRF]
[    0.773095] GHES: HEST is not enabled!
[    0.773113] isapnp: Scanning for PnP cards...
[    1.082544] isapnp: No Plug & Play device found
[    1.082647] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.102995] 00:02: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.123364] 00:03: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
[    1.125100] Linux agpgart interface v0.103
[    1.125177] agpgart-intel 0000:00:00.0: Intel G41 Chipset
[    1.125192] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.125621] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.125749] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.128564] brd: module loaded
[    1.129797] loop: module loaded
[    1.130119] ata_piix 0000:00:1f.1: version 2.13
[    1.131059] scsi host0: ata_piix
[    1.131148] scsi host1: ata_piix
[    1.131194] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.131196] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.131271] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.132347] scsi host2: ata_piix
[    1.132426] scsi host3: ata_piix
[    1.132470] ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
[    1.132471] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
[    1.132572] libphy: Fixed MDIO Bus: probed
[    1.132576] tun: Universal TUN/TAP device driver, 1.6
[    1.132577] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.132624] PPP generic driver version 2.4.2
[    1.132708] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.132713] ehci-pci: EHCI PCI platform driver
[    1.132808] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.132815] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.132826] ehci-pci 0000:00:1d.7: debug port 1
[    1.136725] ehci-pci 0000:00:1d.7: cache line size of 32 is not supported
[    1.136737] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfeaf7c00
[    1.148019] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.148143] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.148150] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.148154] usb usb1: Product: EHCI Host Controller
[    1.148161] usb usb1: Manufacturer: Linux 4.3.3-040303-generic ehci_hcd
[    1.148164] usb usb1: SerialNumber: 0000:00:1d.7
[    1.148327] hub 1-0:1.0: USB hub found
[    1.148335] hub 1-0:1.0: 8 ports detected
[    1.148546] ehci-platform: EHCI generic platform driver
[    1.148557] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.148561] ohci-pci: OHCI PCI platform driver
[    1.148573] ohci-platform: OHCI generic platform driver
[    1.148582] uhci_hcd: USB Universal Host Controller Interface driver
[    1.148650] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.148655] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.148662] uhci_hcd 0000:00:1d.0: detected 2 ports
[    1.148679] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    1.148719] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.148721] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.148722] usb usb2: Product: UHCI Host Controller
[    1.148724] usb usb2: Manufacturer: Linux 4.3.3-040303-generic uhci_hcd
[    1.148726] usb usb2: SerialNumber: 0000:00:1d.0
[    1.148828] hub 2-0:1.0: USB hub found
[    1.148834] hub 2-0:1.0: 2 ports detected
[    1.148979] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.148985] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.148990] uhci_hcd 0000:00:1d.1: detected 2 ports
[    1.149007] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    1.149045] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.149047] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.149049] usb usb3: Product: UHCI Host Controller
[    1.149050] usb usb3: Manufacturer: Linux 4.3.3-040303-generic uhci_hcd
[    1.149052] usb usb3: SerialNumber: 0000:00:1d.1
[    1.149153] hub 3-0:1.0: USB hub found
[    1.149159] hub 3-0:1.0: 2 ports detected
[    1.149300] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.149305] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.149310] uhci_hcd 0000:00:1d.2: detected 2 ports
[    1.149331] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    1.149370] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.149372] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.149373] usb usb4: Product: UHCI Host Controller
[    1.149375] usb usb4: Manufacturer: Linux 4.3.3-040303-generic uhci_hcd
[    1.149376] usb usb4: SerialNumber: 0000:00:1d.2
[    1.149476] hub 4-0:1.0: USB hub found
[    1.149482] hub 4-0:1.0: 2 ports detected
[    1.149625] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.149630] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.149635] uhci_hcd 0000:00:1d.3: detected 2 ports
[    1.149656] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
[    1.149697] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.149699] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.149701] usb usb5: Product: UHCI Host Controller
[    1.149703] usb usb5: Manufacturer: Linux 4.3.3-040303-generic uhci_hcd
[    1.149704] usb usb5: SerialNumber: 0000:00:1d.3
[    1.149805] hub 5-0:1.0: USB hub found
[    1.149811] hub 5-0:1.0: 2 ports detected
[    1.149953] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.150293] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.150300] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.150439] mousedev: PS/2 mouse device common for all mice
[    1.150575] rtc_cmos 00:01: RTC can wake from S4
[    1.150686] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.150708] rtc_cmos 00:01: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.150716] i2c /dev entries driver
[    1.150777] device-mapper: uevent: version 1.0.3
[    1.150843] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    1.150868] platform eisa.0: Probing EISA bus 0
[    1.150871] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.150873] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.150875] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.150876] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.150878] platform eisa.0: Cannot allocate resource for EISA slot 4
[    1.150880] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.150881] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.150883] platform eisa.0: Cannot allocate resource for EISA slot 7
[    1.150885] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.150886] platform eisa.0: EISA: Detected 0 cards
[    1.150899] cpufreq-nforce2: No nForce2 chipset.
[    1.150908] ledtrig-cpu: registered to indicate activity on CPUs
[    1.151153] NET: Registered protocol family 10
[    1.151395] NET: Registered protocol family 17
[    1.151405] Key type dns_resolver registered
[    1.151599] Using IPI No-Shortcut mode
[    1.151751] registered taskstats version 1
[    1.151768] Loading compiled-in X.509 certificates
[    1.154538] Loaded X.509 cert 'Build time autogenerated kernel key: 108ee5b98c6dfcc5ccd3a352a52956f4d65c6fab'
[    1.154554] zswap: loaded using pool lzo/zbud
[    1.156806] Key type trusted registered
[    1.160445] Key type encrypted registered
[    1.160454] AppArmor: AppArmor sha1 policy hashing enabled
[    1.160458] ima: No TPM chip found, activating TPM-bypass!
[    1.160483] evm: HMAC attrs: 0x1
[    1.160709]   Magic number: 11:450:27
[    1.160812] rtc_cmos 00:01: setting system clock to 2015-12-29 12:00:37 UTC (1451390437)
[    1.161240] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.161242] EDD information not available.
[    1.161298] PM: Hibernation image not present or could not be loaded.
[    1.294927] ata4.01: NODEV after polling detection
[    1.300269] ata4.00: ATAPI: ATAPI   iHAS124   B, AL0Q, max UDMA/100
[    1.308370] ata3.00: ATA-8: ST3500413AS, JC45, max UDMA/133
[    1.308376] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.308662] ata3.01: ATA-8: ST2000DL003-9VT166, CC32, max UDMA/133
[    1.308666] ata3.01: 3907029168 sectors, multi 16: LBA48 
[    1.316147] ata4.00: configured for UDMA/100
[    1.324370] ata3.00: configured for UDMA/133
[    1.340391] ata3.01: configured for UDMA/133
[    1.340622] scsi 2:0:0:0: Direct-Access     ATA      ST3500413AS      JC45 PQ: 0 ANSI: 5
[    1.340784] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.340822] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.340826] sd 2:0:0:0: [sda] Write Protect is off
[    1.340829] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.340847] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.341011] scsi 2:0:1:0: Direct-Access     ATA      ST2000DL003-9VT1 CC32 PQ: 0 ANSI: 5
[    1.341173] sd 2:0:1:0: Attached scsi generic sg1 type 0
[    1.344680] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS124   B      AL0Q PQ: 0 ANSI: 5
[    1.364892] sr 3:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.364898] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.365099] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.365158] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.378997]  sda: sda1 sda2 < sda5 >
[    1.379017] sd 2:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.379114] sd 2:0:1:0: [sdb] Write Protect is off
[    1.379121] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.379163] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.379409] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.379700]  sdb: sdb1
[    1.379992] sd 2:0:1:0: [sdb] Attached SCSI disk
[    1.380335] Freeing unused kernel memory: 924K (c1b3b000 - c1c22000)
[    1.380383] Write protecting the kernel text: 7628k
[    1.380409] Write protecting the kernel read-only data: 3124k
[    1.380410] NX-protecting the kernel data: 6708k
[    1.399480] random: systemd-udevd urandom read with 21 bits of entropy available
[    1.452058] [drm] Initialized drm 1.1.0 20060810
[    1.457235] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.476603] atl1c 0000:02:00.0: version 1.0.1.1-NAPI
[    1.516186] [drm] Memory usable by graphics device = 2048M
[    1.516191] checking generic (d0000000 300000) vs hw (d0000000 10000000)
[    1.516193] fb: switching to inteldrmfb from VESA VGA
[    1.516221] Console: switching to colour dummy device 80x25
[    1.516301] [drm] Replacing VGA console driver
[    1.522177] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.522182] [drm] Driver supports precise vblank timestamp query.
[    1.522263] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.525572] [drm:intel_opregion_init [i915]] *ERROR* No ACPI video bus found
[    1.525612] [drm] Initialized i915 1.6.0 20150731 for 0000:00:02.0 on minor 0
[    1.588029] usb 2-1: new low-speed USB device number 2 using uhci_hcd
[    1.623282] fbcon: inteldrmfb (fb0) is primary device
[    1.704023] tsc: Refined TSC clocksource calibration: 2999.963 MHz
[    1.704028] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2b3e2274cba, max_idle_ns: 440795224466 ns
[    1.764051] usb 2-1: New USB device found, idVendor=1d57, idProduct=0001
[    1.764058] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.764061] usb 2-1: Product: 2.4G Mouse
[    1.764063] usb 2-1: Manufacturer: 2.4G KB
[    1.790164] Console: switching to colour frame buffer device 170x48
[    1.794078] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.904040] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    2.004022] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    2.016020] usb 4-2: new full-speed USB device number 2 using uhci_hcd
[    2.155463] usb 3-2: New USB device found, idVendor=04d9, idProduct=1503
[    2.155469] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.155473] usb 3-2: Product: USB Keyboard
[    2.155477] usb 3-2: Manufacturer:  
[    2.168148] hidraw: raw HID events driver (C) Jiri Kosina
[    2.179081] usb 4-2: New USB device found, idVendor=05a9, idProduct=0511
[    2.179089] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.327978] usbcore: registered new interface driver usbhid
[    2.327982] usbhid: USB HID core driver
[    2.332506] input: 2.4G KB 2.4G Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/0003:1D57:0001.0001/input/input5
[    2.336138] random: nonblocking pool is initialized
[    2.367054] usb 2-2: New USB device found, idVendor=0c76, idProduct=160c
[    2.367064] usb 2-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.367069] usb 2-2: Product: USB Speaker
[    2.374208] input: USB Speaker as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.2/0003:0C76:160C.0005/input/input6
[    2.388224] hid-generic 0003:1D57:0001.0001: input,hidraw0: USB HID v1.10 Keyboard [2.4G KB 2.4G Mouse] on usb-0000:00:1d.0-1/input0
[    2.388990] input: 2.4G KB 2.4G Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/0003:1D57:0001.0002/input/input7
[    2.444220] hid-generic 0003:0C76:160C.0005: input,hidraw1: USB HID v1.00 Device [USB Speaker] on usb-0000:00:1d.0-2/input2
[    2.500253] hid-generic 0003:1D57:0001.0002: input,hidraw2: USB HID v1.10 Mouse [2.4G KB 2.4G Mouse] on usb-0000:00:1d.0-1/input1
[    2.500654] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/0003:04D9:1503.0003/input/input8
[    2.556211] hid-generic 0003:04D9:1503.0003: input,hidraw3: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.1-2/input0
[    2.569592] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/0003:04D9:1503.0004/input/input9
[    2.624232] hid-generic 0003:04D9:1503.0004: input,hidraw4: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.1-2/input1
[    2.704095] clocksource: Switched to clocksource tsc
[    4.516043] floppy0: no floppy controllers found
[    9.682048] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.726861] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[   10.853040] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[   10.853161] systemd[1]: Detected architecture x86.
[   10.863827] systemd[1]: Set hostname to <BKC-Media>.
[   12.149968] systemd[1]: Created slice Root Slice.
[   12.150025] systemd[1]: Reached target Remote File Systems (Pre).
[   12.150062] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   12.150103] systemd[1]: Listening on udev Control Socket.
[   12.150129] systemd[1]: Listening on udev Kernel Socket.
[   12.150226] systemd[1]: Created slice System Slice.
[   12.150315] systemd[1]: Created slice system-getty.slice.
[   12.150913] systemd[1]: Starting Increase datagram queue length...
[   12.150988] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   12.151072] systemd[1]: Listening on Journal Audit Socket.
[   12.151157] systemd[1]: Created slice User and Session Slice.
[   12.151314] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   12.151368] systemd[1]: Listening on Device-mapper event daemon FIFOs.
[   12.151413] systemd[1]: Listening on Journal Socket (/dev/log).
[   12.151433] systemd[1]: Reached target Slices.
[   12.151478] systemd[1]: Listening on Journal Socket.
[   12.152172] systemd[1]: Started Read required files in advance.
[   12.152963] systemd[1]: Mounting Huge Pages File System...
[   12.153575] systemd[1]: Mounting POSIX Message Queue File System...
[   12.265522] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   12.266152] systemd[1]: Mounting Debug File System...
[   12.266766] systemd[1]: Starting Setup Virtual Console...
[   12.267400] systemd[1]: Starting udev Coldplug all Devices...
[   12.268125] systemd[1]: Started Braille Device Support.
[   12.402618] systemd[1]: Starting Load Kernel Modules...
[   12.402664] systemd[1]: Reached target User and Group Name Lookups.
[   12.402735] systemd[1]: Listening on fsck to fsckd communication Socket.
[   12.403309] systemd[1]: Starting Uncomplicated firewall...
[   12.403334] systemd[1]: Reached target Encrypted Volumes.
[   12.404768] systemd[1]: Started Setup Virtual Console.
[   12.549122] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   12.549947] systemd[1]: Starting Create Static Device Nodes in /dev...
[   12.727735] systemd[1]: Started Uncomplicated firewall.
[   12.796378] systemd[1]: Mounted Huge Pages File System.
[   12.796420] systemd[1]: Mounted Debug File System.
[   12.796439] systemd[1]: Mounted POSIX Message Queue File System.
[   12.796675] systemd[1]: Started Increase datagram queue length.
[   12.797059] systemd[1]: Listening on Syslog Socket.
[   12.797732] systemd[1]: Starting Journal Service...
[   12.816548] systemd[1]: Started udev Coldplug all Devices.
[   13.309025] lp: driver loaded but no devices found
[   13.341911] ppdev: user-space parallel port driver
[   13.401209] parport_pc 00:04: reported by Plug and Play ACPI
[   13.401275] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   13.496220] lp0: using parport0 (interrupt-driven).
[   13.544707] systemd[1]: Started Load Kernel Modules.
[   13.545441] systemd[1]: Starting Apply Kernel Variables...
[   13.546001] systemd[1]: Mounting FUSE Control File System...
[   13.548551] systemd[1]: Mounted FUSE Control File System.
[   13.586098] systemd[1]: Started Journal Service.
[   15.813583] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.138494] systemd-journald[255]: Received request to flush runtime journal from PID 1
[   16.705208] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.761752] intel_rng: FWH not detected
[   16.981893] ACPI Warning: SystemIO range 0x0000000000000828-0x000000000000082F conflicts with OpRegion 0x0000000000000800-0x000000000000084F (\PMRG) (20150818/utaddress-254)
[   16.981902] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.981938] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.150974] leds_ss4200: no LED devices found
[   17.988600] gpio_ich: GPIO from 462 to 511 on gpio_ich
[   18.078378] usbcore: registered new interface driver snd-usb-audio
[   18.154922] snd_hda_codec_via hdaudioC0D0: autoconfig for VT1708S: line_outs=1 (0x1c/0x0/0x0/0x0/0x0) type:line
[   18.154927] snd_hda_codec_via hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.154929] snd_hda_codec_via hdaudioC0D0:    hp_outs=1 (0x1d/0x0/0x0/0x0/0x0)
[   18.154930] snd_hda_codec_via hdaudioC0D0:    mono: mono_out=0x0
[   18.154932] snd_hda_codec_via hdaudioC0D0:    dig-out=0x20/0x0
[   18.154934] snd_hda_codec_via hdaudioC0D0:    inputs:
[   18.154936] snd_hda_codec_via hdaudioC0D0:      Rear Mic=0x1a
[   18.154938] snd_hda_codec_via hdaudioC0D0:      Front Mic=0x1e
[   18.154939] snd_hda_codec_via hdaudioC0D0:      Line=0x1b
[   18.154941] snd_hda_codec_via hdaudioC0D0:      CD=0x1f
[   18.161785] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.161860] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.161926] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.161991] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   18.162057] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   19.402230] media: Linux media interface: v0.10
[   19.474203] Linux video capture interface: v2.00
[   19.508417] gspca_main: v2.14.0 registered
[   19.545198] gspca_main: ov519-2.14.0 probing 05a9:0511
[   19.708043] floppy0: no floppy controllers found
[   19.940212] input: ov519 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/input/input15
[   19.940337] usbcore: registered new interface driver ov519
[   20.003918] Adding 2058236k swap on /dev/sda5.  Priority:-1 extents:1 across:2058236k FS
[   24.211579] audit: type=1400 audit(1451390460.543:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session" pid=569 comm="apparmor_parser"
[   24.211586] audit: type=1400 audit(1451390460.543:3): apparmor="STATUS" operation="profile_load" name="chromium" pid=569 comm="apparmor_parser"
[   24.308916] audit: type=1400 audit(1451390460.643:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=569 comm="apparmor_parser"
[   24.308923] audit: type=1400 audit(1451390460.643:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=569 comm="apparmor_parser"
[   24.308928] audit: type=1400 audit(1451390460.643:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=569 comm="apparmor_parser"
[   24.308932] audit: type=1400 audit(1451390460.643:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=569 comm="apparmor_parser"
[   24.730685] audit: type=1400 audit(1451390461.063:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=569 comm="apparmor_parser"
[   24.730695] audit: type=1400 audit(1451390461.063:9): apparmor="STATUS" operation="profile_load" name="sanitized_helper" pid=569 comm="apparmor_parser"
[   24.730700] audit: type=1400 audit(1451390461.063:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=569 comm="apparmor_parser"
[   24.730704] audit: type=1400 audit(1451390461.063:11): apparmor="STATUS" operation="profile_load" name="sanitized_helper" pid=569 comm="apparmor_parser"
[   26.176407] cgroup: new mount options do not match the existing superblock, will be ignored
[   43.818356] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.820719] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   49.730258] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[   49.733717] vboxdrv: Found 2 processor cores
[   49.735187] vboxdrv: fAsync=0 offMin=0x1ef offMax=0x45ab
[   49.835400] vboxdrv: TSC mode is Synchronous, tentative frequency 2999963160 Hz
[   49.835404] vboxdrv: Successfully loaded version 5.0.10_Ubuntu (interface 0x00240000)
[   49.881884] VBoxNetFlt: Successfully started.
[   49.925089] VBoxNetAdp: Successfully started.
[   49.990409] VBoxPciLinuxInit
[   50.047203] vboxpci: IOMMU not found (not registered)
[   50.538282] Guest personality initialized and is inactive
[   50.538381] VMCI host device registered (name=vmci, major=10, minor=53)
[   50.538383] Initialized host personality
[   50.772810] NET: Registered protocol family 40
[   84.860632] ip_tables: (C) 2000-2006 Netfilter Core Team
[  497.696300] perf interrupt took too long (2510 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 2268.172781] perf interrupt took too long (5041 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
barry@BKC-Media:~$
```
> **pqwoerituytrueiwoq said:**
> just looked at the boot.log, what video chip are you using? (it appears to be doing the same thing over and over for around 40 minutes)
```
lspci -v |grep -i vga -A10
```
Now that you've clued me in for what to look at, I see that it was over 50m on today's reboot.

That might be the magic right there.

Here's the output:
```
barry@BKC-Media:~$ lspci -v |grep -i vga -A1000:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7592
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at dc00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
barry@BKC-Media:~$
```

Thanks.

---

### Post by BarryD9545 on 2015-12-30
Upon viewing the IP table, it looks like this:
```
barry@BKC-Media:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             192.168.1.3          tcp dpt:58051
ACCEPT     tcp  --  anywhere             192.168.1.3          tcp dpt:58050


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
barry@BKC-Media:~$
```

Pretty empty, just an expected entry for a media player that I've been running for quite time.
No a reference to NetFlix...am I looking in the wrong place?

---

### Post by BarryD9545 on 2015-12-30
Here's my latest boot.log:
```
[[32m  OK  [0m] Started Tell Plymouth To Write Out Runtime Data.[[32m  OK  [0m] Started LSB: AppArmor initialization.
         Starting LSB: Raise network interfaces....
[[32m  OK  [0m] Started LSB: Raise network interfaces..
[[32m  OK  [0m] Reached target System Initialization.
[[32m  OK  [0m] Listening on CUPS Scheduler.
[[32m  OK  [0m] Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
         Starting Restore Sound Card State...
[[32m  OK  [0m] Listening on UUID daemon activation socket.
[[32m  OK  [0m] Listening on ACPID Listen Socket.
[[32m  OK  [0m] Listening on D-Bus System Message Bus Socket.
[[32m  OK  [0m] Reached target Sockets.
[[32m  OK  [0m] Started CUPS Scheduler.
[[32m  OK  [0m] Reached target Paths.
[[32m  OK  [0m] Reached target Basic System.
[[32m  OK  [0m] Started Cgroup management daemon.
         Starting Permit User Sessions...
         Starting LSB: Speech Dispatcher...
         Starting LSB: Set the CPU Frequency Scaling governor to "ondemand"...
         Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down....
[[32m  OK  [0m] Started Run anacron jobs.
         Starting Detect the available GPUs and deal with any system changes...
         Starting Thermal Daemon Service...
         Starting System Logging Service...
         Starting Accounts Service...
[[32m  OK  [0m] Started crash report submission daemon.
         Starting LSB: automatic crash report generation...
         Starting Enable support for additional executable binary formats...
         Starting LSB: Start the GNUstep distributed object mapper...
         Starting Network Manager...
         Starting Avahi mDNS/DNS-SD Stack...
[[32m  OK  [0m] Started D-Bus System Message Bus.
[[32m  OK  [0m] Started Thermal Daemon Service.
[[32m  OK  [0m] Started Avahi mDNS/DNS-SD Stack.
[[32m  OK  [0m] Started Network Manager.
[[32m  OK  [0m] Reached target Network.
         Starting Network Manager Wait Online...
         Starting LSB: This services starts and stops the USB Arbitrator....
         Starting Modem Manager...
         Starting LSB: Startup script for the Logitech Media Server...
[[32m  OK  [0m] Started Regular background program processing daemon.
         Starting LSB: Record successful boot for GRUB...
         Starting Login Service...
         Starting LSB: daemon to balance interrupts for SMP systems...
[[32m  OK  [0m] Started CUPS Scheduler.
[[32m  OK  [0m] Reached target Printer.
[[32m  OK  [0m] Started Make remote CUPS printers available locally.
         Starting Console System Startup Logging...
[[32m  OK  [0m] Started Daily Cleanup of Temporary Directories.
[[32m  OK  [0m] Reached target Timers.
[[32m  OK  [0m] Started System Logging Service.
[[32m  OK  [0m] Started Restore Sound Card State.
[[32m  OK  [0m] Started Permit User Sessions.
[[32m  OK  [0m] Started LSB: Speech Dispatcher.
[[32m  OK  [0m] Started LSB: Set the CPU Frequency Scaling governor to "ondemand".
[[32m  OK  [0m] Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down..
[[32m  OK  [0m] Started LSB: automatic crash report generation.
[[32m  OK  [0m] Started LSB: Start the GNUstep distributed object mapper.
[[32m  OK  [0m] Started LSB: Startup script for the Logitech Media Server.
         Mounting Arbitrary Executable File Formats File System...
[[32m  OK  [0m] Mounted Arbitrary Executable File Formats File System.
[[32m  OK  [0m] Started Console System Startup Logging.
[[32m  OK  [0m] Started LSB: daemon to balance interrupts for SMP systems.
[[32m  OK  [0m] Started Login Service.
         Starting Authenticate and Authorize Users to Run Privileged Tasks...
[[32m  OK  [0m] Started Enable support for additional executable binary formats.
[[32m  OK  [0m] Started LSB: Record successful boot for GRUB.
[[32m  OK  [0m] Started Authenticate and Authorize Users to Run Privileged Tasks.
[[32m  OK  [0m] Started Accounts Service.
         Starting WPA supplicant...
         Starting Network Manager Script Dispatcher Service...
[[32m  OK  [0m] Started Network Manager Script Dispatcher Service.
[[32m  OK  [0m] Started Network Manager Wait Online.
         Starting UPnP MediaServer...
[[32m  OK  [0m] Reached target Network is Online.
         Starting LSB: start Samba daemons for the AD DC...
         Starting LSB: Tool to automatically collect and submit kernel crash signatures...
         Starting /etc/rc.local Compatibility...
         Starting LSB: This service starts and stops VMware services...
         Starting LSB: VirtualBox Linux kernel module...
[[32m  OK  [0m] Started BubbleUPnP Server.
         Starting LSB: start Samba NetBIOS nameserver (nmbd)...
         Starting LSB: start DirMngr daemon...
[[32m  OK  [0m] Started /etc/rc.local Compatibility.
         Starting Wait for Plymouth Boot Screen to Quit...
[[32m  OK  [0m] Started LSB: Tool to automatically collect and submit kernel crash signatures.
[[32m  OK  [0m] Started WPA supplicant.
         Starting Manage, Install and Generate Color Profiles...
[[32m  OK  [0m] Started LSB: VirtualBox Linux kernel module.
[[32m  OK  [0m] Started LSB: start DirMngr daemon.
[[32m  OK  [0m] Started Modem Manager.
[[32m  OK  [0m] Started Manage, Install and Generate Color Profiles.
[[32m  OK  [0m] Started LSB: This services starts and stops the USB Arbitrator..
[[1;31mFAILED[0m] Failed to start LSB: This service starts and stops VMware services.
See 'systemctl status vmware.service' for details.
[[0m[31m*     [0m] (1 of 5) A start job is running for Detect the available GPUs and deal with any system changes (37s / no limit)
[K[[32m  OK  [0m] Started UPnP MediaServer.
[[32m  OK  [0m] Started LSB: start Samba daemons for the AD DC.
[[32m  OK  [0m] Started LSB: start Samba NetBIOS nameserver (nmbd).
         Starting LSB: start Samba SMB/CIFS daemon (smbd)...
[[32m  OK  [0m] Started LSB: start Samba SMB/CIFS daemon (smbd).
[[32m  OK  [0m] Started Detect the available GPUs and deal with any system changes.
         Starting Light Display Manager...
```
I found a [thread]("http://askubuntu.com/questions/696625/45-minutes-boot") wherein a user had the same problem as I, with the same line seeming to slow things down:
```
(1 of 5) A start job is running for Detect the available GPUs and deal with any system changes (37s / no limit)
```
Since he said it "spontaneously cleared up" when he removed rm /var/log/syslog; rm /var/log/ufw.log and rm /var/log/auth.* (I didn't have a ufw.log), I figured I'd give it a go.

taa-daa

37s boot.

I'd still like to know how to remove the NetFlix information mentioned earlier in the threads.

I might try the nvidia update app that is also suggested in the forum, after all, what could possibly go wrong?

---

### Post by pqwoerituytrueiwoq on 2015-12-30
why update a nvidia driver? you don't even have a nvida GPU, you have a Intel one
id guess it was [FONT=courier new]rm /var/log/auth.*[/FONT] that made the change, the others jsut freed up a pile of disk space

the ip tables part was in the 1st answer

glad you found a solution :) that would have been driving me crazy

---

### Post by Bucky Ball on 2015-12-30
Good news. Finally. :)

Please see the first link in my signature to help others (as your original problem appears to be solved). This will not close the thread to further discussion.

Good luck.

---

### Post by BarryD9545 on 2015-12-30
I saw that, but I wanted to be sure...

...and I see trouble on the horizon.  I think.

This boot log shows it took almost a minute,  the Plymouth Boot Screen, Samba NetBIOS nameserver, and - as before - Detect the available GPUs and deal with any system changes taking multiple tries.

here's the log:
```

[[32m  OK  [0m] Started Tell Plymouth To Write Out Runtime Data.
[[32m  OK  [0m] Started LSB: AppArmor initialization.
         Starting LSB: Raise network interfaces....
[[32m  OK  [0m] Started LSB: Raise network interfaces..
[[32m  OK  [0m] Reached target System Initialization.
[[32m  OK  [0m] Started Daily Cleanup of Temporary Directories.
[[32m  OK  [0m] Reached target Timers.
         Starting Console System Startup Logging...
         Starting Restore Sound Card State...
[[32m  OK  [0m] Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
[[32m  OK  [0m] Listening on D-Bus System Message Bus Socket.
[[32m  OK  [0m] Listening on CUPS Scheduler.
[[32m  OK  [0m] Started CUPS Scheduler.
[[32m  OK  [0m] Listening on UUID daemon activation socket.
[[32m  OK  [0m] Reached target Paths.
[[32m  OK  [0m] Listening on ACPID Listen Socket.
[[32m  OK  [0m] Reached target Sockets.
[[32m  OK  [0m] Reached target Basic System.
         Starting System Logging Service...
         Starting Detect the available GPUs and deal with any system changes...
         Starting LSB: Speech Dispatcher...
         Starting LSB: automatic crash report generation...
[[32m  OK  [0m] Started crash report submission daemon.
[[32m  OK  [0m] Started Cgroup management daemon.
         Starting Permit User Sessions...
         Starting LSB: Start the GNUstep distributed object mapper...
         Starting LSB: Startup script for the Logitech Media Server...
         Starting Avahi mDNS/DNS-SD Stack...
         Starting Enable support for additional executable binary formats...
         Starting Modem Manager...
         Starting Network Manager...
         Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down....
         Starting LSB: This services starts and stops the USB Arbitrator....
[[32m  OK  [0m] Started Run anacron jobs.
[[32m  OK  [0m] Started Regular background program processing daemon.
         Starting Login Service...
         Starting LSB: daemon to balance interrupts for SMP systems...
         Starting LSB: Set the CPU Frequency Scaling governor to "ondemand"...
         Starting Accounts Service...
         Starting LSB: Record successful boot for GRUB...
[[32m  OK  [0m] Started D-Bus System Message Bus.
[[32m  OK  [0m] Started Avahi mDNS/DNS-SD Stack.
[[32m  OK  [0m] Started Network Manager.
[[32m  OK  [0m] Reached target Network.
         Starting Network Manager Wait Online...
[[32m  OK  [0m] Started CUPS Scheduler.
[[32m  OK  [0m] Started Make remote CUPS printers available locally.
[[32m  OK  [0m] Reached target Printer.
[[32m  OK  [0m] Started System Logging Service.
[[32m  OK  [0m] Started Console System Startup Logging.
[[32m  OK  [0m] Started Restore Sound Card State.
[[32m  OK  [0m] Started LSB: Speech Dispatcher.
[[32m  OK  [0m] Started LSB: automatic crash report generation.
[[32m  OK  [0m] Started Permit User Sessions.
[[32m  OK  [0m] Started LSB: Start the GNUstep distributed object mapper.
[[32m  OK  [0m] Started LSB: Startup script for the Logitech Media Server.
[[32m  OK  [0m] Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down..
[[32m  OK  [0m] Started LSB: daemon to balance interrupts for SMP systems.
[[32m  OK  [0m] Started LSB: Set the CPU Frequency Scaling governor to "ondemand".
[[32m  OK  [0m] Started LSB: Record successful boot for GRUB.
[[32m  OK  [0m] Started Login Service.
         Mounting Arbitrary Executable File Formats File System...
[[32m  OK  [0m] Mounted Arbitrary Executable File Formats File System.
         Starting Authenticate and Authorize Users to Run Privileged Tasks...
[[32m  OK  [0m] Started LSB: This services starts and stops the USB Arbitrator..
[[32m  OK  [0m] Started Enable support for additional executable binary formats.
[[32m  OK  [0m] Started Authenticate and Authorize Users to Run Privileged Tasks.
[[32m  OK  [0m] Started Accounts Service.
         Starting WPA supplicant...
         Starting Network Manager Script Dispatcher Service...
[[32m  OK  [0m] Started Network Manager Script Dispatcher Service.
[[32m  OK  [0m] Started Network Manager Wait Online.
[[32m  OK  [0m] Reached target Network is Online.
         Starting LSB: This service starts and stops VMware services...
         Starting LSB: start DirMngr daemon...
         Starting LSB: start Samba NetBIOS nameserver (nmbd)...
         Starting /etc/rc.local Compatibility...
         Starting LSB: Tool to automatically collect and submit kernel crash signatures...
         Starting LSB: VirtualBox Linux kernel module...
         Starting LSB: start Samba daemons for the AD DC...
[[32m  OK  [0m] Started BubbleUPnP Server.
         Starting UPnP MediaServer...
[[32m  OK  [0m] Started /etc/rc.local Compatibility.
         Starting Wait for Plymouth Boot Screen to Quit...
[[32m  OK  [0m] Started LSB: Tool to automatically collect and submit kernel crash signatures.
         Starting Manage, Install and Generate Color Profiles...
[[32m  OK  [0m] Started WPA supplicant.
[[32m  OK  [0m] Started LSB: VirtualBox Linux kernel module.
[[32m  OK  [0m] Started Modem Manager.
[[32m  OK  [0m] Started LSB: start DirMngr daemon.
[[32m  OK  [0m] Started Manage, Install and Generate Color Profiles.
[[1;31mFAILED[0m] Failed to start LSB: This service starts and stops VMware services.
See 'systemctl status vmware.service' for details.
[[0m[31m*     [0m] (1 of 5) A start job is running for LSB: start Samba daemons for the AD DC (38s / 5min 28s)
[K[[1;31m*[0m[31m*    [0m] (1 of 5) A start job is running for LSB: start Samba daemons for the AD DC (38s / 5min 28s)
[K[[31m*[1;31m*[0m[31m*   [0m] (1 of 5) A start job is running for LSB: start Samba daemons for the AD DC (39s / 5min 28s)
[K[ [31m*[1;31m*[0m[31m*  [0m] (2 of 5) A start job is running for LSB: start Samba NetBIOS nameserver (nmbd) (39s / 5min 28s)
[K[  [31m*[1;31m*[0m[31m* [0m] (2 of 5) A start job is running for LSB: start Samba NetBIOS nameserver (nmbd) (40s / 5min 28s)
[K[   [31m*[1;31m*[0m[31m*[0m] (2 of 5) A start job is running for LSB: start Samba NetBIOS nameserver (nmbd) (40s / 5min 28s)
[K[[32m  OK  [0m] Started UPnP MediaServer.
[    [31m*[1;31m*[0m] (3 of 4) A start job is running for Wait for Plymouth Boot Screen to Quit (46s / no limit)
[K[     [31m*[0m] (3 of 4) A start job is running for Wait for Plymouth Boot Screen to Quit (46s / no limit)
[K[    [31m*[1;31m*[0m] (3 of 4) A start job is running for Wait for Plymouth Boot Screen to Quit (47s / no limit)
[K[[32m  OK  [0m] Started LSB: start Samba daemons for the AD DC.
[[32m  OK  [0m] Started LSB: start Samba NetBIOS nameserver (nmbd).
         Starting LSB: start Samba SMB/CIFS daemon (smbd)...
[[32m  OK  [0m] Started LSB: start Samba SMB/CIFS daemon (smbd).
[   [31m*[1;31m*[0m[31m*[0m] (2 of 2) A start job is running for Detect the available GPUs and deal with any system changes (54s / no limit)
[K[  [31m*[1;31m*[0m[31m* [0m] (2 of 2) A start job is running for Detect the available GPUs and deal with any system changes (54s / no limit)
[K[ [31m*[1;31m*[0m[31m*  [0m] (2 of 2) A start job is running for Detect the available GPUs and deal with any system changes (55s / no limit)
[K[[31m*[1;31m*[0m[31m*   [0m] (1 of 2) A start job is running for Wait for Plymouth Boot Screen to Quit (55s / no limit)
[K[[1;31m*[0m[31m*    [0m] (1 of 2) A start job is running for Wait for Plymouth Boot Screen to Quit (56s / no limit)
[K[[0m[31m*     [0m] (1 of 2) A start job is running for Wait for Plymouth Boot Screen to Quit (56s / no limit)
[K[[32m  OK  [0m] Started Detect the available GPUs and deal with any system changes.
         Starting Light Display Manager...

```

Look like it might be starting to stretch out a bit more each time for some reason...any ideas?

---

### Post by pqwoerituytrueiwoq on 2015-12-31
well this is a dirty solution but why not have [FONT=courier new]/etc/rc.local[/FONT] run [FONT=courier new]rm /var/log/syslog; rm /var/log/ufw.log; rm /var/log/auth.*[/FONT] at boot?

---

