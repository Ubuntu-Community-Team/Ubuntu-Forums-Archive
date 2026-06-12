---
title: "After install some packages booting slow"
date: 2015-07-24
forum: General Help
---

### Post by kenik123 on 2015-07-24
Hi,
I install some packages
```
aptitude aptitude-common beanstalkd bison byobu chrpath cloud-guest-utils cloud-init cmake cmake-data cryptsetup debconf-utils distro-info 
distro-info-data dkms eatmydata fonts-ubuntu-font-family-console gawk git-core gyp hardening-wrapper juju juju-core landscape-client landscape-common libaio-dev 
libbison-dev:amd64 libboost-iostreams1.54.0:amd64 libc-ares-dev:amd64 libc-ares2:amd64 libcwidget3 libdumbnet1 libept1.4.12:amd64 libffi-dev:amd64 libjs-node-uuid  
libmemcached11:amd64:amd64 libncurses5-dev:amd64 libnss-myhostname:amd64 libonig2 libossp-uuid16 libpq5 libqdbm14 libreadline-dev:amd64 libreadline6-dev:amd64 
libsqlite3-dev:amd64 libtcl8.5:amd64 libtinfo-dev:amd64 libv8-3.14-dev libyaml-dev:amd64 linux-headers-virtual linux-virtual node-abbrev node-ansi node-archy node-async 
node-block-stream node-combined-stream node-cookie-jar node-delayed-stream node-forever-agent node-form-data node-fstream node-fstream-ignore node-github-url-from-git     
node-glob node-graceful-fs node-gyp node-inherits node-ini node-json-stringify-safe     node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp node-mute-stream 
node-node-uuid node-nopt node-normalize-package-data    node-npmlog node-once node-osenv node-qs node-read node-read-package-json node-request node-retry node-rimraf 
node-semver node-sha node-sigmund node-slide node-tar node-tunnel-agent node-which nodejs nodejs-dev npm     open-vm-tools openssh-server openssh-sftp-server overlayroot 
php5 php5-cgi php5-fpm php5-intl php5-memcached php5-pgsql php5-sqlite pollinate postgresql postgresql-9.3 postgresql-client postgresql-client-9.3 postgresql-client-common 
postgresql-common postgresql-contrib postgresql-contrib-9.3 python-apport python-cheetah python-configobj python-json-pointer python-jsonpatch python-keyring python-launchpadlib 
python-lazr.restfulclient     python-lazr.uri python-oauth python-prettytable python-problem-report python-secretstorage python-simplejson python-twisted-names python-wadllib 
python-yaml python3-newt run-one screen  ssh-import-id tasksel tasksel-data tcl8.5 tmux update-motd vim vim-runtime w3m zerofree   

```

**Until this my computer start slow **

bootchart:
[https://drive.google.com/file/d/0BwbG-9oHMHNFcU5OX1dETmhrVzA/view?usp=sharing](https://drive.google.com/file/d/0BwbG-9oHMHNFcU5OX1dETmhrVzA/view?usp=sharing)

dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-57-generic (buildd@brownie) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #95-Ubuntu SMP Fri Jun 19 09:28:15 UTC 2015 (Ubuntu 3.13.0-57.95-generic 3.13.11-ckt21)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-57-generic root=UUID=69cade7e-b04c-4c7a-8c4a-55a901936d90 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000009b63efff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b63f000-0x000000009b6befff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009b6bf000-0x000000009b7befff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009b7bf000-0x000000009b7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009b7ff000-0x000000009b7fffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b800000-0x000000009fffffff] reserved
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
[    0.000000] BIOS-e820: [mem 0x0000000200000000-0x000000025bffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion G72 NoteBook PC     /1439, BIOS F.47 02/15/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x25c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FE0000000 write-back
[    0.000000]   3 base 09C000000 mask FFC000000 uncachable
[    0.000000]   4 base 09B800000 mask FFF800000 uncachable
[    0.000000]   5 base 100000000 mask F00000000 write-back
[    0.000000]   6 base 200000000 mask F80000000 write-back
[    0.000000]   7 base 25C000000 mask FFC000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x9b800 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x25be00000-0x25bffffff]
[    0.000000]  [mem 0x25be00000-0x25bffffff] page 2M
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x258000000-0x25bdfffff]
[    0.000000]  [mem 0x258000000-0x25bdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x257ffffff]
[    0.000000]  [mem 0x200000000-0x257ffffff] page 2M
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x9b63efff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x9b5fffff] page 2M
[    0.000000]  [mem 0x9b600000-0x9b63efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9b7ff000-0x9b7fffff]
[    0.000000]  [mem 0x9b7ff000-0x9b7fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1fbffffff]
[    0.000000]  [mem 0x100000000-0x1fbffffff] page 2M
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35b46000-0x36d9afff]
[    0.000000] ACPI: RSDP 00000000000fe020 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 000000009b7fe120 000074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 000000009b7fc000 0000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 000000009b7ed000 00B80E (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 000000009b75e000 000040
[    0.000000] ACPI: ASF! 000000009b7fd000 0000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 000000009b7fb000 000038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 000000009b7fa000 00008C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 000000009b7f9000 00003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 000000009b7ec000 000176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 000000009b7e8000 000028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 000000009b7e5000 000034 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: WDAT 000000009b7e4000 000224 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 000000009b7e3000 0009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000025bffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x25bffffff]
[    0.000000]   NODE_DATA [mem 0x25bff5000-0x25bff9fff]
[    0.000000]  [ffffea0000000000-ffffea00097fffff] PMD -> [ffff880253600000-ffff88025b5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x25bffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x9b63efff]
[    0.000000]   node   0: [mem 0x9b7ff000-0x9b7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x1fbffffff]
[    0.000000]   node   0: [mem 0x200000000-0x25bffffff]
[    0.000000] On node 0 totalpages: 2045404
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9881 pages used for memmap
[    0.000000]   DMA32 zone: 632384 pages, LIFO batch:31
[    0.000000]   Normal zone: 22272 pages used for memmap
[    0.000000]   Normal zone: 1409024 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
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
[    0.000000] smpboot: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b63f000-0x9b6befff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b6bf000-0x9b7befff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b7bf000-0x9b7fefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b800000-0x9fffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xa0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1afff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1b000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x1fc000000-0x1ffffffff]
[    0.000000] e820: [mem 0xa0000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88025bc00000 s81536 r8192 d20864 u262144
[    0.000000] pcpu-alloc: s81536 r8192 d20864 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2013166
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-57-generic root=UUID=69cade7e-b04c-4c7a-8c4a-55a901936d90 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7948188K/8181616K available (7392K kernel code, 1146K rwdata, 3408K rodata, 1336K init, 1448K bss, 233428K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1999.836 MHz processor
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.67 BogoMIPS (lpj=7999344)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000043] Security Framework initialized
[    0.000068] AppArmor: AppArmor initialized
[    0.000070] Yama: becoming mindful.
[    0.000812] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002886] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003808] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003824] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.004103] Initializing cgroup subsys memory
[    0.004110] Initializing cgroup subsys devices
[    0.004112] Initializing cgroup subsys freezer
[    0.004114] Initializing cgroup subsys blkio
[    0.004116] Initializing cgroup subsys perf_event
[    0.004119] Initializing cgroup subsys hugetlb
[    0.004143] CPU: Physical Processor ID: 0
[    0.004145] CPU: Processor Core ID: 0
[    0.004151] mce: CPU supports 9 MCE banks
[    0.004161] CPU0: Thermal monitoring handled by SMI
[    0.004169] process: using mwait in idle threads
[    0.004173] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.004173] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.004173] tlb_flushall_shift: 6
[    0.004294] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.005835] ACPI: Core revision 20131115
[    0.016555] ACPI: All ACPI Tables successfully acquired
[    0.052622] ftrace: allocating 28585 entries in 112 pages
[    0.070934] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.110618] smpboot: CPU0: Intel(R) Pentium(R) CPU        P6100  @ 2.00GHz (fam: 06, model: 25, stepping: 05)
[    0.215571] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.215578] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.215581] ... version:                3
[    0.215582] ... bit width:              48
[    0.215583] ... generic registers:      4
[    0.215585] ... value mask:             0000ffffffffffff
[    0.215586] ... max period:             000000007fffffff
[    0.215587] ... fixed-purpose events:   3
[    0.215588] ... event mask:             000000070000000f
[    0.217728] x86: Booting SMP configuration:
[    0.228784] CPU1: Thermal monitoring handled by SMI
[    0.217730] .... node  #0, CPUs:      #1
[    0.230905] x86: Booted up 1 node, 2 CPUs
[    0.230910] smpboot: Total of 2 processors activated (7999.34 BogoMIPS)
[    0.231065] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.232414] devtmpfs: initialized
[    0.236923] EVM: security.selinux
[    0.236925] EVM: security.SMACK64
[    0.236926] EVM: security.ima
[    0.236927] EVM: security.capability
[    0.236987] PM: Registering ACPI NVS region [mem 0x9b6bf000-0x9b7befff] (1048576 bytes)
[    0.238131] pinctrl core: initialized pinctrl subsystem
[    0.238216] regulator-dummy: no parameters
[    0.238251] RTC time: 20:30:44, date: 07/23/15
[    0.238295] NET: Registered protocol family 16
[    0.238429] cpuidle: using governor ladder
[    0.238431] cpuidle: using governor menu
[    0.238475] ACPI: bus type PCI registered
[    0.238478] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.238557] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.238560] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.248444] PCI: Using configuration type 1 for base access
[    0.249496] bio: create slab <bio-0> at 0
[    0.249658] ACPI: Added _OSI(Module Device)
[    0.249660] ACPI: Added _OSI(Processor Device)
[    0.249662] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.249664] ACPI: Added _OSI(Processor Aggregator Device)
[    0.253403] ACPI: Executed 1 blocks of module-level executable AML code
[    0.259621] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.260152] ACPI: SSDT 000000009b691c18 00036C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.260608] ACPI: Dynamic OEM Table Load:
[    0.260611] ACPI: SSDT           (null) 00036C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.260803] ACPI: SSDT 000000009b68f018 000891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.261237] ACPI: Dynamic OEM Table Load:
[    0.261239] ACPI: SSDT           (null) 000891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.267915] ACPI: SSDT 000000009b690a98 000303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.268420] ACPI: Dynamic OEM Table Load:
[    0.268423] ACPI: SSDT           (null) 000303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.271743] ACPI: SSDT 000000009b68ed98 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.272207] ACPI: Dynamic OEM Table Load:
[    0.272210] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.711425] ACPI: Interpreter enabled
[    0.711437] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.711445] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.711471] ACPI: (supports S0 S3 S4 S5)
[    0.711473] ACPI: Using IOAPIC for interrupt routing
[    0.711512] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.711658] ACPI: No dock devices found.
[    0.800783] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    0.800791] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.800832] \_SB_.PCI0:_OSC invalid UUID
[    0.800833] _OSC request data:1 1f 0 
[    0.800838] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.801698] PCI host bridge to bus 0000:00
[    0.801702] pci_bus 0000:00: root bus resource [bus 00-7e]
[    0.801705] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.801707] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.801709] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.801711] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xfeafffff]
[    0.801721] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.801742] DMAR: Disabling batched IOTLB flush on Ironlake
[    0.801818] pci 0000:00:02.0: [8086:0046] type 00 class 0x030000
[    0.801831] pci 0000:00:02.0: reg 0x10: [mem 0xb0000000-0xb03fffff 64bit]
[    0.801838] pci 0000:00:02.0: reg 0x18: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.801844] pci 0000:00:02.0: reg 0x20: [io  0x3050-0x3057]
[    0.801965] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.801995] pci 0000:00:16.0: reg 0x10: [mem 0xb4404000-0xb440400f 64bit]
[    0.802094] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.802192] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.802218] pci 0000:00:1a.0: reg 0x10: [mem 0xb440a000-0xb440a3ff]
[    0.802332] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.802408] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.802454] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.802477] pci 0000:00:1b.0: reg 0x10: [mem 0xb4400000-0xb4403fff 64bit]
[    0.802578] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.802632] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.802670] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.802773] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.802828] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.802875] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400
[    0.802979] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.803034] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.803083] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.803109] pci 0000:00:1d.0: reg 0x10: [mem 0xb4409000-0xb44093ff]
[    0.803224] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.803297] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.803336] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.803452] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.803491] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100
[    0.803676] pci 0000:00:1f.2: [8086:3b29] type 00 class 0x010601
[    0.803705] pci 0000:00:1f.2: reg 0x10: [io  0x3048-0x304f]
[    0.803717] pci 0000:00:1f.2: reg 0x14: [io  0x305c-0x305f]
[    0.803729] pci 0000:00:1f.2: reg 0x18: [io  0x3040-0x3047]
[    0.803740] pci 0000:00:1f.2: reg 0x1c: [io  0x3058-0x305b]
[    0.803752] pci 0000:00:1f.2: reg 0x20: [io  0x3020-0x303f]
[    0.803764] pci 0000:00:1f.2: reg 0x24: [mem 0xb4408000-0xb44087ff]
[    0.803833] pci 0000:00:1f.2: PME# supported from D3hot
[    0.803912] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.803935] pci 0000:00:1f.3: reg 0x10: [mem 0xb4406000-0xb44060ff 64bit]
[    0.803966] pci 0000:00:1f.3: reg 0x20: [io  0x3000-0x301f]
[    0.804487] pci 0000:02:00.0: [10ec:8136] type 00 class 0x020000
[    0.804748] pci 0000:02:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.804863] pci 0000:02:00.0: reg 0x18: [mem 0xb0410000-0xb0410fff 64bit pref]
[    0.804911] pci 0000:02:00.0: reg 0x20: [mem 0xb0400000-0xb040ffff 64bit pref]
[    0.804958] pci 0000:02:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.805229] pci 0000:02:00.0: supports D1 D2
[    0.805231] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.807531] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.807688] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.807693] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.807698] pci 0000:00:1c.0:   bridge window [mem 0xb3400000-0xb43fffff]
[    0.807706] pci 0000:00:1c.0:   bridge window [mem 0xb0400000-0xb13fffff 64bit pref]
[    0.807865] pci 0000:03:00.0: [14e4:4727] type 00 class 0x028000
[    0.807910] pci 0000:03:00.0: reg 0x10: [mem 0xb2400000-0xb2403fff 64bit]
[    0.808148] pci 0000:03:00.0: supports D1 D2
[    0.808202] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.818921] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.818930] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.818939] pci 0000:00:1c.2:   bridge window [mem 0xb2400000-0xb33fffff]
[    0.818954] pci 0000:00:1c.2:   bridge window [mem 0xb1400000-0xb23fffff 64bit pref]
[    0.819043] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.819057] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.819059] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.819061] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.819063] pci 0000:00:1e.0:   bridge window [mem 0xa0000000-0xfeafffff] (subtractive decode)
[    0.819515] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.819578] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.819642] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.819703] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.819763] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.819824] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.819884] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.819944] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.847650] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 7f])
[    0.847655] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.847660] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.847738] PCI host bridge to bus 0000:7f
[    0.847741] pci_bus 0000:7f: root bus resource [bus 7f]
[    0.847747] pci 0000:7f:00.0: [8086:2c62] type 00 class 0x060000
[    0.847793] pci 0000:7f:00.1: [8086:2d01] type 00 class 0x060000
[    0.847841] pci 0000:7f:02.0: [8086:2d10] type 00 class 0x060000
[    0.847883] pci 0000:7f:02.1: [8086:2d11] type 00 class 0x060000
[    0.847925] pci 0000:7f:02.2: [8086:2d12] type 00 class 0x060000
[    0.847972] pci 0000:7f:02.3: [8086:2d13] type 00 class 0x060000
[    0.848394] ACPI: Enabled 7 GPEs in block 00 to 3F
[    0.848402] ACPI: \_SB_.PCI0: notify handler is installed
[    0.848446] ACPI: \_SB_.CPBG: notify handler is installed
[    0.848461] Found 2 acpi root devices
[    0.848511] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.848612] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.848614] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.848618] vgaarb: loaded
[    0.848619] vgaarb: bridge control possible 0000:00:02.0
[    0.848806] SCSI subsystem initialized
[    0.848872] libata version 3.00 loaded.
[    0.848897] ACPI: bus type USB registered
[    0.848914] usbcore: registered new interface driver usbfs
[    0.848922] usbcore: registered new interface driver hub
[    0.848950] usbcore: registered new device driver usb
[    0.849061] PCI: Using ACPI for IRQ routing
[    0.853992] PCI: pci_cache_line_size set to 64 bytes
[    0.854080] e820: reserve RAM buffer [mem 0x0009d000-0x0009ffff]
[    0.854082] e820: reserve RAM buffer [mem 0x9b63f000-0x9bffffff]
[    0.854084] e820: reserve RAM buffer [mem 0x9b800000-0x9bffffff]
[    0.854186] NetLabel: Initializing
[    0.854188] NetLabel:  domain hash size = 128
[    0.854189] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.854205] NetLabel:  unlabeled traffic allowed by default
[    0.854287] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.854293] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.856333] Switched to clocksource hpet
[    0.861891] AppArmor: AppArmor Filesystem Enabled
[    0.861929] pnp: PnP ACPI init
[    0.861946] ACPI: bus type PNP registered
[    0.862041] pnp 00:00: [dma 4]
[    0.862070] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.862097] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.862245] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.862286] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.862311] pnp 00:04: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.2 BAR 13 [io  0x1000-0x1fff]
[    0.862356] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.862358] system 00:04: [io  0x0800-0x080f] has been reserved
[    0.862360] system 00:04: [io  0x0810-0x0813] has been reserved
[    0.862363] system 00:04: [io  0xffff] has been reserved
[    0.862365] system 00:04: [io  0x0400-0x047f] could not be reserved
[    0.862368] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.862371] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.862404] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.862441] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.862471] pnp 00:07: Plug and Play ACPI device, IDs SYN1e2c SYN1e00 SYN0002 PNP0f13 (active)
[    0.862835] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.862838] system 00:08: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.862840] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.862843] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.862845] system 00:08: [mem 0xf0000000-0xf1ffffff] has been reserved
[    0.862847] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.862850] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.862852] system 00:08: [mem 0xff000000-0xffffffff] could not be reserved
[    0.862854] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.862857] system 00:08: [mem 0xb4500000-0xb4500fff] has been reserved
[    0.862860] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.885106] pnp: PnP ACPI: found 9 devices
[    0.885108] ACPI: bus type PNP unregistered
[    0.891746] pci 0000:02:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.891788] pci 0000:02:00.0: BAR 6: assigned [mem 0xb0420000-0xb043ffff pref]
[    0.891792] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.891796] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.891802] pci 0000:00:1c.0:   bridge window [mem 0xb3400000-0xb43fffff]
[    0.891807] pci 0000:00:1c.0:   bridge window [mem 0xb0400000-0xb13fffff 64bit pref]
[    0.891815] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.891819] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.891826] pci 0000:00:1c.2:   bridge window [mem 0xb2400000-0xb33fffff]
[    0.891831] pci 0000:00:1c.2:   bridge window [mem 0xb1400000-0xb23fffff 64bit pref]
[    0.891839] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.891855] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.891857] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.891859] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.891861] pci_bus 0000:00: resource 7 [mem 0xa0000000-0xfeafffff]
[    0.891864] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.891866] pci_bus 0000:02: resource 1 [mem 0xb3400000-0xb43fffff]
[    0.891868] pci_bus 0000:02: resource 2 [mem 0xb0400000-0xb13fffff 64bit pref]
[    0.891870] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.891872] pci_bus 0000:03: resource 1 [mem 0xb2400000-0xb33fffff]
[    0.891874] pci_bus 0000:03: resource 2 [mem 0xb1400000-0xb23fffff 64bit pref]
[    0.891876] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.891878] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.891880] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.891883] pci_bus 0000:04: resource 7 [mem 0xa0000000-0xfeafffff]
[    0.891918] NET: Registered protocol family 2
[    0.892198] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.892426] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.892630] TCP: Hash tables configured (established 65536 bind 65536)
[    0.892663] TCP: reno registered
[    0.892676] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.892716] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.892812] NET: Registered protocol family 1
[    0.892828] pci 0000:00:02.0: Video device with shadowed ROM
[    0.893536] PCI: CLS 64 bytes, default 64
[    0.893612] Trying to unpack rootfs image as initramfs...
[    1.284866] Freeing initrd memory: 18772K (ffff880035b46000 - ffff880036d9b000)
[    1.284873] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.284876] software IO TLB [mem 0x9763f000-0x9b63f000] (64MB) mapped at [ffff88009763f000-ffff88009b63efff]
[    1.284936] Simple Boot Flag at 0x44 set to 0x1
[    1.285102] microcode: CPU0 sig=0x20655, pf=0x10, revision=0x2
[    1.285107] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x2
[    1.285169] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.285171] Scanning for low memory corruption every 60 seconds
[    1.285441] Initialise system trusted keyring
[    1.285499] audit: initializing netlink socket (disabled)
[    1.285512] type=2000 audit(1437683445.144:1): initialized
[    1.318382] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.319674] zbud: loaded
[    1.319855] VFS: Disk quotas dquot_6.5.2
[    1.319903] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.320422] fuse init (API version 7.22)
[    1.320502] msgmni has been set to 15560
[    1.320566] Key type big_key registered
[    1.320932] Key type asymmetric registered
[    1.320934] Asymmetric key parser 'x509' registered
[    1.320972] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.321004] io scheduler noop registered
[    1.321006] io scheduler deadline registered (default)
[    1.321033] io scheduler cfq registered
[    1.321482] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.321497] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.321538] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.321540] vesafb: scrolling: redraw
[    1.321542] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.321549] mtrr: no more MTRRs available
[    1.321816] vesafb: framebuffer at 0xa0000000, mapped to 0xffffc90008e80000, using 3072k, total 3072k
[    1.324173] Console: switching to colour frame buffer device 128x48
[    1.326466] fb0: VESA VGA frame buffer device
[    1.326490] intel_idle: MWAIT substates: 0x120
[    1.326492] intel_idle: v0.4 model 0x25
[    1.326494] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.326560] ipmi message handler version 39.2
[    1.327260] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.328290] ACPI: AC Adapter [ADP1] (on-line)
[    1.328444] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.333038] ACPI: Lid Switch [LID0]
[    1.333086] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.333091] ACPI: Power Button [PWRB]
[    1.333132] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.333134] ACPI: Power Button [PWRF]
[    1.347067] thermal LNXTHERM:00: registered as thermal_zone0
[    1.347074] ACPI: Thermal Zone [TSZ0] (0 C)
[    1.347098] GHES: HEST is not enabled!
[    1.347181] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.352017] Linux agpgart interface v0.103
[    1.352080] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.352140] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.352630] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.352829] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[    1.354439] brd: module loaded
[    1.355189] loop: module loaded
[    1.355580] libphy: Fixed MDIO Bus: probed
[    1.355667] tun: Universal TUN/TAP device driver, 1.6
[    1.355668] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.355714] PPP generic driver version 2.4.2
[    1.355756] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.355761] ehci-pci: EHCI PCI platform driver
[    1.355951] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.355959] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.355978] ehci-pci 0000:00:1a.0: debug port 2
[    1.359911] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.359936] ehci-pci 0000:00:1a.0: irq 16, io mem 0xb440a000
[    1.368346] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.368391] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.368393] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.368395] usb usb1: Product: EHCI Host Controller
[    1.368397] usb usb1: Manufacturer: Linux 3.13.0-57-generic ehci_hcd
[    1.368399] usb usb1: SerialNumber: 0000:00:1a.0
[    1.368515] hub 1-0:1.0: USB hub found
[    1.368524] hub 1-0:1.0: 3 ports detected
[    1.368765] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.368823] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.368838] ehci-pci 0000:00:1d.0: debug port 2
[    1.372758] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.372777] ehci-pci 0000:00:1d.0: irq 23, io mem 0xb4409000
[    1.372818] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.372826] ACPI: Battery Slot [BAT0] (battery absent)
[    1.384396] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.384518] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.384524] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.384528] usb usb2: Product: EHCI Host Controller
[    1.384532] usb usb2: Manufacturer: Linux 3.13.0-57-generic ehci_hcd
[    1.384537] usb usb2: SerialNumber: 0000:00:1d.0
[    1.384763] hub 2-0:1.0: USB hub found
[    1.384774] hub 2-0:1.0: 3 ports detected
[    1.384900] ehci-platform: EHCI generic platform driver
[    1.384908] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.384909] ohci-pci: OHCI PCI platform driver
[    1.384922] ohci-platform: OHCI generic platform driver
[    1.384928] uhci_hcd: USB Universal Host Controller Interface driver
[    1.384989] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.393925] i8042: Detected active multiplexing controller, rev 1.1
[    1.395868] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.395873] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.395899] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.395916] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.395935] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.396168] mousedev: PS/2 mouse device common for all mice
[    1.396437] rtc_cmos 00:05: RTC can wake from S4
[    1.396608] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.396643] rtc_cmos 00:05: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.396713] device-mapper: uevent: version 1.0.3
[    1.396793] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.396802] ledtrig-cpu: registered to indicate activity on CPUs
[    1.396910] TCP: cubic registered
[    1.396994] NET: Registered protocol family 10
[    1.397166] NET: Registered protocol family 17
[    1.397179] Key type dns_resolver registered
[    1.397484] Loading compiled-in X.509 certificates
[    1.398738] Loaded X.509 cert 'Magrathea: Glacier signing key: a55b8de68a607adbfa6df96000506950cdaea041'
[    1.398754] registered taskstats version 1
[    1.401297] Key type trusted registered
[    1.403217] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.405279] Key type encrypted registered
[    1.405283] AppArmor: AppArmor sha1 policy hashing enabled
[    1.405286] IMA: No TPM chip found, activating TPM-bypass!
[    1.405630] regulator-dummy: disabling
[    1.405671]   Magic number: 7:335:549
[    1.405692] tty ttyS25: hash matches
[    1.405705] clockevents clockevent0: hash matches
[    1.405730] acpi PNP0C0F:00: hash matches
[    1.405805] rtc_cmos 00:05: setting system clock to 2015-07-23 20:30:45 UTC (1437683445)
[    1.406301] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.406303] EDD information not available.
[    1.406348] PM: Hibernation image not present or could not be loaded.
[    1.407545] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.407549] Write protecting the kernel read-only data: 12288k
[    1.410192] Freeing unused kernel memory: 788K (ffff88000173b000 - ffff880001800000)
[    1.412383] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.436735] systemd-udevd[125]: starting version 204
[    1.489001] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.489015] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.489271] r8169 0000:02:00.0: irq 40 for MSI/MSI-X
[    1.489450] r8169 0000:02:00.0 eth0: RTL8102e at 0xffffc90000c7e000, 98:4b:e1:f0:b1:d7, XID 04e00000 IRQ 40
[    1.490677] ahci 0000:00:1f.2: version 3.0
[    1.490828] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    1.490892] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    1.490896] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    1.491481] scsi0 : ahci
[    1.492465] scsi1 : ahci
[    1.492761] scsi2 : ahci
[    1.493031] scsi3 : ahci
[    1.493080] ata1: SATA max UDMA/133 abar m2048@0xb4408000 port 0xb4408100 irq 41
[    1.493082] ata2: DUMMY
[    1.493083] ata3: DUMMY
[    1.493084] ata4: DUMMY
[    1.680446] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.812429] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.812663] ata1.00: ATA-8: OCZ-ARC100, 1.01, max UDMA/133
[    1.812671] ata1.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.812795] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.812801] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.813202] hub 1-1:1.0: USB hub found
[    1.813386] hub 1-1:1.0: 6 ports detected
[    1.818368] ata1.00: configured for UDMA/133
[    1.818685] scsi 0:0:0:0: Direct-Access     ATA      OCZ-ARC100       1.01 PQ: 0 ANSI: 5
[    1.818934] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.818998] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.819023] sd 0:0:0:0: [sda] Write Protect is off
[    1.819027] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.819057] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.819675]  sda: sda1
[    1.820196] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.924441] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.056786] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    2.056793] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.057256] hub 2-1:1.0: USB hub found
[    2.057389] hub 2-1:1.0: 8 ports detected
[    2.128566] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    2.284403] tsc: Refined TSC clocksource calibration: 1999.999 MHz
[    2.387293] usb 1-1.3: New USB device found, idVendor=5986, idProduct=0149
[    2.387300] usb 1-1.3: New USB device strings: Mfr=3, Product=1, SerialNumber=0
[    2.387304] usb 1-1.3: Product: HP Webcam-101
[    2.387308] usb 1-1.3: Manufacturer: Bison Electronics Inc.
[    2.476565] usb 2-1.1: new full-speed USB device number 3 using ehci-pci
[    2.573296] usb 2-1.1: New USB device found, idVendor=413c, idProduct=2501
[    2.573304] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.573309] usb 2-1.1: Product: Dell KM632 Wireless Keyboard and Mouse
[    2.573314] usb 2-1.1: Manufacturer: Dell
[    2.577772] hidraw: raw HID events driver (C) Jiri Kosina
[    2.585592] usbcore: registered new interface driver usbhid
[    2.585595] usbhid: USB HID core driver
[    2.587554] input: Dell Dell KM632 Wireless Keyboard and Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input12
[    2.588012] hid-generic 0003:413C:2501.0001: input,hidraw0: USB HID v1.11 Keyboard [Dell Dell KM632 Wireless Keyboard and Mouse] on usb-0000:00:1d.0-1.1/input0
[    2.589751] input: Dell Dell KM632 Wireless Keyboard and Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input13
[    2.589865] hid-generic 0003:413C:2501.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Dell Dell KM632 Wireless Keyboard and Mouse] on usb-0000:00:1d.0-1.1/input1
[    2.590222] input: Dell Dell KM632 Wireless Keyboard and Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/input/input14
[    2.590307] hid-generic 0003:413C:2501.0003: input,hidraw2: USB HID v1.11 Mouse [Dell Dell KM632 Wireless Keyboard and Mouse] on usb-0000:00:1d.0-1.1/input2
[    2.644601] usb 2-1.2: new low-speed USB device number 4 using ehci-pci
[    2.742658] usb 2-1.2: New USB device found, idVendor=04b4, idProduct=0060
[    2.742666] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.742671] usb 2-1.2: Product: USB Device
[    2.742676] usb 2-1.2: Manufacturer: Areson
[    2.747038] input: Areson USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input15
[    2.747170] hid-generic 0003:04B4:0060.0004: input,hidraw3: USB HID v1.00 Mouse [Areson USB Device] on usb-0000:00:1d.0-1.2/input0
[    2.750771] hid-generic 0003:04B4:0060.0005: hiddev0,hidraw4: USB HID v1.00 Device [Areson USB Device] on usb-0000:00:1d.0-1.2/input1
[    3.072355] psmouse serio2: synaptics: queried max coordinates: x [..5826], y [..4764]
[    3.140804] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xe40000/0xa0400, board id: 0, fw id: 639092
[    3.184624] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input11
[    3.284518] Switched to clocksource tsc
[    6.867230] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.989221] random: init urandom read with 43 bits of entropy available
[    7.023698] init: plymouth-upstart-bridge main process (185) terminated with status 1
[    7.023713] init: plymouth-upstart-bridge main process ended, respawning
[    7.033321] init: plymouth-upstart-bridge main process (193) terminated with status 1
[    7.033336] init: plymouth-upstart-bridge main process ended, respawning
[    7.039517] init: plymouth-upstart-bridge main process (197) terminated with status 1
[    7.039532] init: plymouth-upstart-bridge main process ended, respawning
[    7.168362] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro
[    7.925840] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.008972] systemd-udevd[417]: starting version 204
[    8.064981] lp: driver loaded but no devices found
[    8.074416] ppdev: user-space parallel port driver
[    8.116206] mei_me 0000:00:16.0: irq 42 for MSI/MSI-X
[    8.144290] [drm] Initialized drm 1.1.0 20060810
[    8.165012] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.170112] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    8.170121] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.170125] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    8.170129] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \_GPE.GPIO 2 (20131115/utaddress-251)
[    8.170132] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.170134] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    8.170137] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_GPE.GPIO 2 (20131115/utaddress-251)
[    8.170140] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.170142] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    8.170145] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_GPE.GPIO 2 (20131115/utaddress-251)
[    8.170148] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.170149] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.174609] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[    8.174650] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[    8.174684] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[    8.174750] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[    8.179688] wmi: Mapper loaded
[    8.185133] [drm] Memory usable by graphics device = 2048M
[    8.185156] checking generic (a0000000 300000) vs hw (a0000000 10000000)
[    8.185159] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[    8.185181] Console: switching to colour dummy device 80x25
[    8.208854] bcma: bus0: Bus registered
[    8.232555] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    8.232570] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    8.232571] [drm] Driver supports precise vblank timestamp query.
[    8.232650] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    8.233425] systemd-udevd[444]: renamed network interface eth0 to eth3
[    8.258083] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.268132] type=1400 audit(1437676252.357:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=473 comm="apparmor_parser"
[    8.268141] type=1400 audit(1437676252.357:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=473 comm="apparmor_parser"
[    8.268146] type=1400 audit(1437676252.357:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=473 comm="apparmor_parser"
[    8.268707] type=1400 audit(1437676252.361:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=473 comm="apparmor_parser"
[    8.268714] type=1400 audit(1437676252.361:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=473 comm="apparmor_parser"
[    8.269021] type=1400 audit(1437676252.361:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=473 comm="apparmor_parser"
[    8.280613] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    8.294581] fbcon: inteldrmfb (fb0) is primary device
[    8.299928] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    8.545759] Linux video capture interface: v2.00
[    8.624356] uvcvideo: Found UVC 1.00 device HP Webcam-101 (5986:0149)
[    8.628749] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input20
[    8.629364] usbcore: registered new interface driver uvcvideo
[    8.629365] USB Video Class driver (1.1.1)
[    8.633447] random: nonblocking pool is initialized
[    8.648014] input: HP WMI hotkeys as /devices/virtual/input/input21
[    8.694489] cfg80211: Calling CRDA to update world regulatory domain
[    8.700985] cfg80211: World regulatory domain updated:
[    8.700986] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.700987] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.700989] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.700990] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.700991] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.700992] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.733200] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[    8.733204] b43: probe of bcma0:0 failed with error -524
[    8.733600] Broadcom 43xx driver loaded [ Features: PNL ]
[    8.752024] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 18
[    8.760015] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    8.760356] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[    8.760376] cfg80211: Calling CRDA for country: US
[    8.769896] cfg80211: Regulatory domain changed to country: US
[    8.769897] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.769899] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.769900] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[    8.769901] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.769902] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.769903] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.769904] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[    8.769905] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[    9.020447] Console: switching to colour frame buffer device 200x56
[    9.024921] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    9.024923] i915 0000:00:02.0: registered panic notifier
[    9.057380] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.072497] acpi device:02: registered as cooling_device3
[    9.072612] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input22
[    9.072785] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.073156] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[    9.110290] SKU: Nid=0x1d sku_cfg=0x40179a2d
[    9.110294] SKU: port_connectivity=0x1
[    9.110295] SKU: enable_pcbeep=0x1
[    9.110296] SKU: check_sum=0x00000007
[    9.110297] SKU: customization=0x0000009a
[    9.110299] SKU: external_amp=0x5
[    9.110300] SKU: platform_type=0x1
[    9.110301] SKU: swap=0x0
[    9.110302] SKU: override=0x1
[    9.110537] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    9.110539]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    9.110540]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    9.110542]    mono: mono_out=0x0
[    9.110543]    inputs:
[    9.110596]      Internal Mic=0x19
[    9.110598]      Mic=0x18
[    9.110599] realtek: No valid SSID, checking pincfg 0x40179a2d for NID 0x1d
[    9.110601] realtek: Enabling init ASM_ID=0x9a2d CODEC_ID=10ec0270
[    9.138518] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input25
[    9.140657] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input24
[    9.141462] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input23
[    9.157888] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[  136.303139] FS-Cache: Loaded
[  136.318345] RPC: Registered named UNIX socket transport module.
[  136.318349] RPC: Registered udp transport module.
[  136.318351] RPC: Registered tcp transport module.
[  136.318352] RPC: Registered tcp NFSv4.1 backchannel transport module.
[  136.356228] FS-Cache: Netfs 'nfs' registered for caching
[  136.400665] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  136.544191] init: failsafe main process (918) killed by TERM signal
[  136.638726] init: samba-ad-dc main process (957) terminated with status 1
[  136.769095] Bluetooth: Core ver 2.17
[  136.769118] NET: Registered protocol family 31
[  136.769120] Bluetooth: HCI device and connection manager initialized
[  136.769132] Bluetooth: HCI socket layer initialized
[  136.769135] Bluetooth: L2CAP socket layer initialized
[  136.769139] Bluetooth: SCO socket layer initialized
[  136.788021] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  136.788026] Bluetooth: BNEP filters: protocol multicast
[  136.788037] Bluetooth: BNEP socket layer initialized
[  136.818945] Bluetooth: RFCOMM TTY layer initialized
[  136.818963] Bluetooth: RFCOMM socket layer initialized
[  136.818970] Bluetooth: RFCOMM ver 1.11
[  136.948283] type=1400 audit(1437676381.037:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1083 comm="apparmor_parser"
[  136.948293] type=1400 audit(1437676381.041:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1083 comm="apparmor_parser"
[  136.948962] type=1400 audit(1437676381.041:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1083 comm="apparmor_parser"
[  137.064505] init: cups main process (1095) killed by HUP signal
[  137.064520] init: cups main process ended, respawning
[  137.105710] type=1400 audit(1437676381.197:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1140 comm="apparmor_parser"
[  137.105721] type=1400 audit(1437676381.197:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1140 comm="apparmor_parser"
[  137.105726] type=1400 audit(1437676381.197:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1140 comm="apparmor_parser"
[  137.106276] type=1400 audit(1437676381.197:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1140 comm="apparmor_parser"
[  137.106281] type=1400 audit(1437676381.197:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1140 comm="apparmor_parser"
[  137.106571] type=1400 audit(1437676381.197:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1140 comm="apparmor_parser"
[  137.128966] type=1400 audit(1437676381.221:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1139 comm="apparmor_parser"
[  137.205488] r8169 0000:02:00.0 eth3: link down
[  137.207346] IPv6: ADDRCONF(NETDEV_UP): eth3: link is not ready
[  137.207871] IPv6: ADDRCONF(NETDEV_UP): eth3: link is not ready
[  137.284793] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  137.284807] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  137.285033] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  137.285572] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


```

Thank You in advance for Help.

---

### Post by v3.xx on 2015-07-24
If this is happening while you are not connected to the internet.

Open /etc/network/interface with your text editor.   And comment (#) out eth0.

To read..
```
#auto eth0
#iface eth0 inet dhcp
```

---

