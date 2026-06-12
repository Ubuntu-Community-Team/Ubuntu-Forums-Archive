---
title: "Slow Boot Times 13.10 (includes Bootchart)"
date: 2013-12-04
forum: General Help
---

### Post by adamzendarski on 2013-12-04
Hi,

I have recently installed Ubuntu Gnome 13.10 and a lot of packages that I like to install after installing Ubuntu.

For some reason after installing my favorite packages, my boot is taking over 30 seconds ON A SANDISK EXTREME SSD.

My original boot prior to installing the packages I installed was 2 seconds.

I installed many packages and wouldn't prefer to test them all in process of elimination.

Anyway, **I have attached a bootchart**.

It's been a while since I used Ubuntu and I forgot how to read bootcharts.

**If anyone could please help me figure out what might be causing my long boot times, I would really appreciate it.**

Thanks ahead of time!

Sincerely,

Adam


[ATTACH=CONFIG]248337[/ATTACH]

---

### Post by oldfred on 2013-12-04
I never understood boot charts but I do look at boot logs and see what is taking more time.

In 12.04 is  a log file viewer or just look at /var/log/dmesg

I have an old slow SSD and dmesg says it takes 10 sec. But my BIOS and grub take 15 or so, so my boot time is about 25 sec which is pretty good for a mostly 6 year old system.

```
[    3.782104] usbhid: USB HID core driver
[    5.610650] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts: (null)
[    7.481304] Adding 3076412k swap on /dev/sdc11.  Priority:-1 extents:1 across:3076412k 

```

I see with my system the mounting is the slowest part of my boot. Almost 2 sec each.

---

### Post by Slim Odds on 2013-12-04
That bootchart is too small to read in any detail.....

I agree with oldfred, look at the boot log to see if anything unusual stands out.

---

### Post by adamzendarski on 2013-12-04
Hi,

Here is my /var/log/dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-14-generic (buildd@allspice) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 (Ubuntu 3.11.0-14.21-generic 3.11.7)
[    0.000000] Command line: BOOT_IMAGE=/@/boot/vmlinuz-3.11.0-14-generic root=UUID=1e55f019-8d6a-4d39-8b26-f8d5cc8a1597 ro rootflags=subvol=@ crashkernel=384M-2G:64M,2G-:128M acpi_backlight=vendor dell_laptop.backlight=0 pcie_aspm=force i915.i915_enable_rc6=1 drm.vblankoffdelay=1 i915.semaphores=1 vt.handoff=7 quiet splash elevator=deadline acpi_osi=linux vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000b18a8fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b18a9000-0x00000000b2ca9fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b2caa000-0x00000000b4877fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b4878000-0x00000000b4ac0fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b4ac1000-0x00000000b6c8efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b6c8f000-0x00000000b6d2cfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b6d2d000-0x00000000b6d3bfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b6d3c000-0x00000000b6dfafff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b6dfb000-0x00000000b6dfcfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b6dfd000-0x00000000b6dfefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b6dff000-0x00000000b6e01fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b6e02000-0x00000000b6e09fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b6e0a000-0x00000000b6e1afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b6e1b000-0x00000000b6f17fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b6f18000-0x00000000b6f1bfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b6f1c000-0x00000000b6f1efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b6f1f000-0x00000000b6f9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b6f9f000-0x00000000b6ffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000b6fff000-0x00000000b6ffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b7000000-0x00000000bf9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed08fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffd80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023fdfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Dell Inc.          Dell System XPS 15Z/00WW5M, BIOS A12 09/07/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x23fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   4 base 0B7000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask F00000000 write-back
[    0.000000]   6 base 200000000 mask FC0000000 write-back
[    0.000000]   7 base 23FE00000 mask FFFE00000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xb7000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd1000, 0x01fd1fff] PGTABLE
[    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23fc00000-0x23fdfffff]
[    0.000000]  [mem 0x23fc00000-0x23fdfffff] page 2M
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23c000000-0x23fbfffff]
[    0.000000]  [mem 0x23c000000-0x23fbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x23bffffff]
[    0.000000]  [mem 0x200000000-0x23bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xb18a8fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xb17fffff] page 2M
[    0.000000]  [mem 0xb1800000-0xb18a8fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xb2caa000-0xb4877fff]
[    0.000000]  [mem 0xb2caa000-0xb2dfffff] page 4k
[    0.000000]  [mem 0xb2e00000-0xb47fffff] page 2M
[    0.000000]  [mem 0xb4800000-0xb4877fff] page 4k
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xb4ac1000-0xb6c8efff]
[    0.000000]  [mem 0xb4ac1000-0xb4bfffff] page 4k
[    0.000000]  [mem 0xb4c00000-0xb6bfffff] page 2M
[    0.000000]  [mem 0xb6c00000-0xb6c8efff] page 4k
[    0.000000] init_memory_mapping: [mem 0xb6fff000-0xb6ffffff]
[    0.000000]  [mem 0xb6fff000-0xb6ffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x35e64000-0x36f29fff]
[    0.000000] Reserving 128MB of memory at 720MB for crashkernel (System RAM: 8019MB)
[    0.000000] ACPI: RSDP 00000000000f00e0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000b6ffe120 000A4 (v01 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: FACP 00000000b6ff0000 000F4 (v03 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: DSDT 00000000b6ff3000 08A57 (v02 DELL    SNB-CPT 00000000 INTL 20061109)
[    0.000000] ACPI: FACS 00000000b6f40000 00040
[    0.000000] ACPI: SLIC 00000000b6ffd000 00176 (v01 DELL    QA09    00000002 LOHR 00000001)
[    0.000000] ACPI: SSDT 00000000b6ffc000 00166 (v01 DELL   PtidDevc 00001000 INTL 20061109)
[    0.000000] ACPI: ASF! 00000000b6ff2000 000A5 (v32 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: HPET 00000000b6fef000 00038 (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: APIC 00000000b6fee000 00098 (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: MCFG 00000000b6fed000 0003C (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: SSDT 00000000b6fec000 00B3B (v01 NvORef NvOptTbl 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000b6feb000 00846 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000b6fea000 00996 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000b6fe9000 002DA (v01  PmRef  Cpu0Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000b6fe8000 0035D (v01  PmRef    ApTst 00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 00000000b6fe7000 0003E (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000b6fe6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: DMAR 00000000b6fe5000 000E8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: UEFI 00000000b6fe4000 0022E (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023fdfffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23fdfffff]
[    0.000000]   NODE_DATA [mem 0x23fdf1000-0x23fdf5fff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237600000-ffff88023f3fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23fdfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xb18a8fff]
[    0.000000]   node   0: [mem 0xb2caa000-0xb4877fff]
[    0.000000]   node   0: [mem 0xb4ac1000-0xb6c8efff]
[    0.000000]   node   0: [mem 0xb6fff000-0xb6ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x23fdfffff]
[    0.000000] On node 0 totalpages: 2053090
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 156 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11546 pages used for memmap
[    0.000000]   DMA32 zone: 738886 pages, LIFO batch:31
[    0.000000]   Normal zone: 20472 pages used for memmap
[    0.000000]   Normal zone: 1310208 pages, LIFO batch:31
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
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xb18a9000-0xb2ca9fff]
[    0.000000] PM: Registered nosave memory: [mem 0xb4878000-0xb4ac0fff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6c8f000-0xb6d2cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6d2d000-0xb6d3bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6d3c000-0xb6dfafff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6dfb000-0xb6dfcfff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6dfd000-0xb6dfefff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6dff000-0xb6e01fff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6e02000-0xb6e09fff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6e0a000-0xb6e1afff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6e1b000-0xb6f17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6f18000-0xb6f1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6f1c000-0xb6f1efff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6f1f000-0xb6f9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xb6f9f000-0xb6ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xb7000000-0xbf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfa00000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed07fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed08000-0xfed08fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed09000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffd7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffd80000-0xffffffff]
[    0.000000] e820: [mem 0xbfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88023fa00000 s86720 r8192 d23872 u262144
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2020852
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/@/boot/vmlinuz-3.11.0-14-generic root=UUID=1e55f019-8d6a-4d39-8b26-f8d5cc8a1597 ro rootflags=subvol=@ crashkernel=384M-2G:64M,2G-:128M acpi_backlight=vendor dell_laptop.backlight=0 pcie_aspm=force i915.i915_enable_rc6=1 drm.vblankoffdelay=1 i915.semaphores=1 vt.handoff=7 quiet splash elevator=deadline acpi_osi=linux vt.handoff=7
[    0.000000] PCIe ASPM is forcibly enabled
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7850928K/8212360K available (7143K kernel code, 1082K rwdata, 3260K rodata, 1364K init, 1420K bss, 361432K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33030144 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2793.724 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5587.44 BogoMIPS (lpj=11174896)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000024] Security Framework initialized
[    0.000038] AppArmor: AppArmor initialized
[    0.000039] Yama: becoming mindful.
[    0.000475] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001889] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002491] Mount-cache hash table entries: 256
[    0.002636] Initializing cgroup subsys memory
[    0.002643] Initializing cgroup subsys devices
[    0.002644] Initializing cgroup subsys freezer
[    0.002645] Initializing cgroup subsys blkio
[    0.002647] Initializing cgroup subsys perf_event
[    0.002648] Initializing cgroup subsys hugetlb
[    0.002666] CPU: Physical Processor ID: 0
[    0.002666] CPU: Processor Core ID: 0
[    0.002671] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002671] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002673] mce: CPU supports 7 MCE banks
[    0.002680] CPU0: Thermal monitoring handled by SMI
[    0.002689] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.002689] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.002689] tlb_flushall_shift: 5
[    0.002786] Freeing SMP alternatives memory: 28K (ffffffff81e65000 - ffffffff81e6c000)
[    0.005052] ACPI: Core revision 20130517
[    0.010228] ACPI: All ACPI Tables successfully acquired
[    0.060588] ftrace: allocating 27804 entries in 109 pages
[    0.072602] dmar: Host address width 36
[    0.072605] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.072610] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.072611] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.072615] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.072617] dmar: RMRR base: 0x000000b6e1d000 end: 0x000000b6e33fff
[    0.072618] dmar: RMRR base: 0x000000b7800000 end: 0x000000bf9fffff
[    0.072688] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.072689] HPET id 0 under DRHD base 0xfed91000
[    0.072690] HPET id 0 under DRHD base 0xfed91000
[    0.072691] HPET id 0 under DRHD base 0xfed91000
[    0.072692] HPET id 0 under DRHD base 0xfed91000
[    0.072692] HPET id 0 under DRHD base 0xfed91000
[    0.072693] HPET id 0 under DRHD base 0xfed91000
[    0.072694] HPET id 0 under DRHD base 0xfed91000
[    0.072695] HPET id 0 under DRHD base 0xfed91000
[    0.072853] Enabled IRQ remapping in x2apic mode
[    0.072854] Enabling x2apic
[    0.072855] Enabled x2apic
[    0.072860] Switched APIC routing to cluster x2apic.
[    0.073312] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.113047] smpboot: CPU0: Intel(R) Core(TM) i7-2640M CPU @ 2.80GHz (fam: 06, model: 2a, stepping: 07)
[    0.113055] TSC deadline timer enabled
[    0.113064] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, full-width counters, Intel PMU driver.
[    0.113070] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.113072] ... version:                3
[    0.113073] ... bit width:              48
[    0.113073] ... generic registers:      4
[    0.113074] ... value mask:             0000ffffffffffff
[    0.113075] ... max period:             0000ffffffffffff
[    0.113076] ... fixed-purpose events:   3
[    0.113077] ... event mask:             000000070000000f
[    0.125344] CPU1: Thermal monitoring handled by SMI
[    0.127513] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.138547] CPU2: Thermal monitoring handled by SMI
[    0.151673] CPU3: Thermal monitoring handled by SMI
[    0.114381] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.153783] Brought up 4 CPUs
[    0.153786] smpboot: Total of 4 processors activated (22349.79 BogoMIPS)
[    0.157157] devtmpfs: initialized
[    0.158093] EVM: security.selinux
[    0.158094] EVM: security.SMACK64
[    0.158095] EVM: security.capability
[    0.158174] PM: Registering ACPI NVS region [mem 0xb6d2d000-0xb6d3bfff] (61440 bytes)
[    0.158177] PM: Registering ACPI NVS region [mem 0xb6dfb000-0xb6dfcfff] (8192 bytes)
[    0.158178] PM: Registering ACPI NVS region [mem 0xb6dff000-0xb6e01fff] (12288 bytes)
[    0.158179] PM: Registering ACPI NVS region [mem 0xb6e0a000-0xb6e1afff] (69632 bytes)
[    0.158181] PM: Registering ACPI NVS region [mem 0xb6f18000-0xb6f1bfff] (16384 bytes)
[    0.158182] PM: Registering ACPI NVS region [mem 0xb6f1f000-0xb6f9efff] (524288 bytes)
[    0.158866] regulator-dummy: no parameters
[    0.158896] RTC time: 17:00:51, date: 12/04/13
[    0.158925] NET: Registered protocol family 16
[    0.159110] ACPI: bus type PCI registered
[    0.159112] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.159163] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.159165] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.165586] PCI: Using configuration type 1 for base access
[    0.165773] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.165774] mtrr: probably your BIOS does not setup all CPUs.
[    0.165774] mtrr: corrected configuration.
[    0.166348] bio: create slab <bio-0> at 0
[    0.166466] ACPI: Added _OSI(Module Device)
[    0.166468] ACPI: Added _OSI(Processor Device)
[    0.166469] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.166470] ACPI: Added _OSI(Processor Aggregator Device)
[    0.166471] ACPI: Added _OSI(linux)
[    0.167677] ACPI: EC: Look up EC in DSDT
[    0.168856] ACPI: Executed 1 blocks of module-level executable AML code
[    0.173892] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.174981] ACPI: SSDT 00000000b6e06718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.175289] ACPI: Dynamic OEM Table Load:
[    0.175292] ACPI: SSDT           (null) 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.181262] ACPI: SSDT 00000000b6e07a98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.181595] ACPI: Dynamic OEM Table Load:
[    0.181597] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.185130] ACPI: SSDT 00000000b6e05d98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.185432] ACPI: Dynamic OEM Table Load:
[    0.185433] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.191185] ACPI: Interpreter enabled
[    0.191191] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.191195] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.191206] ACPI: (supports S0 S3 S4 S5)
[    0.191207] ACPI: Using IOAPIC for interrupt routing
[    0.191227] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.191312] ACPI: No dock devices found.
[    0.196550] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.196578] \_SB_.PCI0:_OSC invalid UUID
[    0.196580] _OSC request data:1 8 0 
[    0.196605] \_SB_.PCI0:_OSC invalid UUID
[    0.196606] _OSC request data:1 1f 0 
[    0.196609] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.196611] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.197090] PCI host bridge to bus 0000:00
[    0.197092] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.197094] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.197096] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.197097] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.197098] pci_bus 0000:00: root bus resource [mem 0xbfa00000-0xfeafffff]
[    0.197100] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff]
[    0.197107] pci 0000:00:00.0: [8086:0104] type 00 class 0x060000
[    0.197170] pci 0000:00:01.0: [8086:0101] type 01 class 0x060400
[    0.197198] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.197224] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.197252] pci 0000:00:02.0: [8086:0126] type 00 class 0x030000
[    0.197262] pci 0000:00:02.0: reg 0x10: [mem 0xf3400000-0xf37fffff 64bit]
[    0.197267] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.197271] pci 0000:00:02.0: reg 0x20: [io  0x4000-0x403f]
[    0.197350] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.197373] pci 0000:00:16.0: reg 0x10: [mem 0xf3c05000-0xf3c0500f 64bit]
[    0.197448] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.197511] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.197532] pci 0000:00:1a.0: reg 0x10: [mem 0xf3c0a000-0xf3c0a3ff]
[    0.197620] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.197664] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.197695] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.197710] pci 0000:00:1b.0: reg 0x10: [mem 0xf3c00000-0xf3c03fff 64bit]
[    0.197776] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.197808] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.197834] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.197915] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.197949] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.197976] pci 0000:00:1c.1: [8086:1c12] type 01 class 0x060400
[    0.198051] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.198085] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.198113] pci 0000:00:1c.3: [8086:1c16] type 01 class 0x060400
[    0.198189] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.198223] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.198248] pci 0000:00:1c.4: [8086:1c18] type 01 class 0x060400
[    0.198325] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.198358] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.198383] pci 0000:00:1c.5: [8086:1c1a] type 01 class 0x060400
[    0.198460] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.198494] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.198524] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.198545] pci 0000:00:1d.0: reg 0x10: [mem 0xf3c09000-0xf3c093ff]
[    0.198633] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.198675] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.198703] pci 0000:00:1f.0: [8086:1c4b] type 00 class 0x060100
[    0.198854] pci 0000:00:1f.2: [8086:1c03] type 00 class 0x010601
[    0.198872] pci 0000:00:1f.2: reg 0x10: [io  0x4088-0x408f]
[    0.198880] pci 0000:00:1f.2: reg 0x14: [io  0x4094-0x4097]
[    0.198888] pci 0000:00:1f.2: reg 0x18: [io  0x4080-0x4087]
[    0.198895] pci 0000:00:1f.2: reg 0x1c: [io  0x4090-0x4093]
[    0.198903] pci 0000:00:1f.2: reg 0x20: [io  0x4060-0x407f]
[    0.198911] pci 0000:00:1f.2: reg 0x24: [mem 0xf3c08000-0xf3c087ff]
[    0.198955] pci 0000:00:1f.2: PME# supported from D3hot
[    0.199004] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.199019] pci 0000:00:1f.3: reg 0x10: [mem 0xf3c04000-0xf3c040ff 64bit]
[    0.199039] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf]
[    0.199133] pci 0000:01:00.0: [10de:0df5] type 00 class 0x030000
[    0.199141] pci 0000:01:00.0: reg 0x10: [mem 0xf2000000-0xf2ffffff]
[    0.199149] pci 0000:01:00.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.199157] pci 0000:01:00.0: reg 0x1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.199162] pci 0000:01:00.0: reg 0x24: [io  0x3000-0x307f]
[    0.199168] pci 0000:01:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
[    0.199208] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.205902] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.205911] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.205918] pci 0000:00:01.0:   bridge window [mem 0xf2000000-0xf30fffff]
[    0.205927] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.206005] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.206228] pci 0000:03:00.0: [8086:0091] type 00 class 0x028000
[    0.206375] pci 0000:03:00.0: reg 0x10: [mem 0xf3b00000-0xf3b01fff 64bit]
[    0.207081] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.207224] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.214030] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.214036] pci 0000:00:1c.1:   bridge window [mem 0xf3b00000-0xf3bfffff]
[    0.214122] pci 0000:04:00.0: [1033:0194] type 00 class 0x0c0330
[    0.214148] pci 0000:04:00.0: reg 0x10: [mem 0xf3a00000-0xf3a01fff 64bit]
[    0.214280] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.214313] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.221945] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.221960] pci 0000:00:1c.3:   bridge window [mem 0xf3a00000-0xf3afffff]
[    0.222070] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    0.222076] pci 0000:00:1c.4:   bridge window [mem 0xf3900000-0xf39fffff]
[    0.222158] pci 0000:06:00.0: [1969:1083] type 00 class 0x020000
[    0.222186] pci 0000:06:00.0: reg 0x10: [mem 0xf3800000-0xf383ffff 64bit]
[    0.222201] pci 0000:06:00.0: reg 0x18: [io  0x2000-0x207f]
[    0.222327] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.222358] pci 0000:06:00.0: System wakeup disabled by ACPI
[    0.229965] pci 0000:00:1c.5: PCI bridge to [bus 06]
[    0.229976] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.229985] pci 0000:00:1c.5:   bridge window [mem 0xf3800000-0xf38fffff]
[    0.230414] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.230460] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *9
[    0.230505] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *9
[    0.230549] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.230593] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.230637] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.230682] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.230726] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.230902] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.230909] ACPI: \_SB_.PCI0: notify handler is installed
[    0.230945] Found 1 acpi root devices
[    0.230986] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.231056] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.231060] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.231061] vgaarb: loaded
[    0.231062] vgaarb: bridge control possible 0000:01:00.0
[    0.231062] vgaarb: no bridge control possible 0000:00:02.0
[    0.231178] SCSI subsystem initialized
[    0.231180] ACPI: bus type ATA registered
[    0.231221] libata version 3.00 loaded.
[    0.231233] ACPI: bus type USB registered
[    0.231243] usbcore: registered new interface driver usbfs
[    0.231249] usbcore: registered new interface driver hub
[    0.231267] usbcore: registered new device driver usb
[    0.231348] PCI: Using ACPI for IRQ routing
[    0.232784] PCI: pci_cache_line_size set to 64 bytes
[    0.232881] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.232882] e820: reserve RAM buffer [mem 0xb18a9000-0xb3ffffff]
[    0.232883] e820: reserve RAM buffer [mem 0xb4878000-0xb7ffffff]
[    0.232886] e820: reserve RAM buffer [mem 0xb6c8f000-0xb7ffffff]
[    0.232887] e820: reserve RAM buffer [mem 0xb7000000-0xb7ffffff]
[    0.232889] e820: reserve RAM buffer [mem 0x23fe00000-0x23fffffff]
[    0.232953] NetLabel: Initializing
[    0.232954] NetLabel:  domain hash size = 128
[    0.232955] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.232962] NetLabel:  unlabeled traffic allowed by default
[    0.233045] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.233050] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.236078] Switched to clocksource hpet
[    0.239810] AppArmor: AppArmor Filesystem Enabled
[    0.239833] pnp: PnP ACPI init
[    0.239843] ACPI: bus type PNP registered
[    0.239874] pnp 00:00: [dma 4]
[    0.239892] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.239973] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.240002] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.240038] system 00:03: [io  0x0680-0x069f] has been reserved
[    0.240040] system 00:03: [io  0x1000-0x1003] has been reserved
[    0.240041] system 00:03: [io  0x1004-0x1013] has been reserved
[    0.240043] system 00:03: [io  0xffff] has been reserved
[    0.240045] system 00:03: [io  0x0400-0x0453] could not be reserved
[    0.240046] system 00:03: [io  0x0458-0x047f] has been reserved
[    0.240048] system 00:03: [io  0x0500-0x057f] has been reserved
[    0.240049] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.240052] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.240073] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.240121] system 00:05: [io  0x0454-0x0457] has been reserved
[    0.240124] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.240171] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.240209] pnp 00:07: Plug and Play ACPI device, IDs DLL0446 PNP0f13 (active)
[    0.240298] pnp 00:08: disabling [mem 0xfffff000-0xffffffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0xfff80000-0xffffffff pref]
[    0.240312] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.240314] system 00:08: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.240316] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.240317] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.240319] system 00:08: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.240320] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.240322] system 00:08: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.240324] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.240326] system 00:08: [mem 0xff000000-0xffffffff] could not be reserved
[    0.240327] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.240329] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.240431] pnp 00:09: Plug and Play ACPI device, IDs SMO8800 (active)
[    0.240526] pnp: PnP ACPI: found 10 devices
[    0.240527] ACPI: bus type PNP unregistered
[    0.246508] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.246555] pci 0000:01:00.0: BAR 6: assigned [mem 0xf3000000-0xf307ffff pref]
[    0.246557] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.246559] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.246561] pci 0000:00:01.0:   bridge window [mem 0xf2000000-0xf30fffff]
[    0.246564] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.246567] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.246578] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.246583] pci 0000:00:1c.1:   bridge window [mem 0xf3b00000-0xf3bfffff]
[    0.246591] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.246596] pci 0000:00:1c.3:   bridge window [mem 0xf3a00000-0xf3afffff]
[    0.246604] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    0.246609] pci 0000:00:1c.4:   bridge window [mem 0xf3900000-0xf39fffff]
[    0.246617] pci 0000:00:1c.5: PCI bridge to [bus 06]
[    0.246620] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.246625] pci 0000:00:1c.5:   bridge window [mem 0xf3800000-0xf38fffff]
[    0.246897] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.246899] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.246900] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.246902] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfeafffff]
[    0.246903] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    0.246905] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.246906] pci_bus 0000:01: resource 1 [mem 0xf2000000-0xf30fffff]
[    0.246908] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.246909] pci_bus 0000:03: resource 1 [mem 0xf3b00000-0xf3bfffff]
[    0.246911] pci_bus 0000:04: resource 1 [mem 0xf3a00000-0xf3afffff]
[    0.246912] pci_bus 0000:05: resource 1 [mem 0xf3900000-0xf39fffff]
[    0.246914] pci_bus 0000:06: resource 0 [io  0x2000-0x2fff]
[    0.246915] pci_bus 0000:06: resource 1 [mem 0xf3800000-0xf38fffff]
[    0.246937] NET: Registered protocol family 2
[    0.247101] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.247272] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.247387] TCP: Hash tables configured (established 65536 bind 65536)
[    0.247405] TCP: reno registered
[    0.247415] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.247440] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.247505] NET: Registered protocol family 1
[    0.247516] pci 0000:00:02.0: Boot video device
[    0.247853] PCI: CLS 64 bytes, default 64
[    0.247892] Trying to unpack rootfs image as initramfs...
[    0.484345] Freeing initrd memory: 17176K (ffff880035e64000 - ffff880036f2a000)
[    0.485305] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.485308] software IO TLB [mem 0xad8a9000-0xb18a9000] (64MB) mapped at [ffff8800ad8a9000-ffff8800b18a8fff]
[    0.485494] Scanning for low memory corruption every 60 seconds
[    0.485696] Initialise module verification
[    0.485727] audit: initializing netlink socket (disabled)
[    0.485739] type=2000 audit(1386176451.440:1): initialized
[    0.507486] bounce pool size: 64 pages
[    0.507493] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.508448] zbud: loaded
[    0.508555] VFS: Disk quotas dquot_6.5.2
[    0.508586] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.508926] fuse init (API version 7.22)
[    0.508980] msgmni has been set to 15367
[    0.509418] Key type asymmetric registered
[    0.509420] Asymmetric key parser 'x509' registered
[    0.509441] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.509477] io scheduler noop registered
[    0.509478] io scheduler deadline registered (default)
[    0.509495] io scheduler cfq registered
[    0.509564] pcieport 0000:00:01.0: irq 42 for MSI/MSI-X
[    0.509784] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.509794] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.509834] intel_idle: MWAIT substates: 0x21120
[    0.509835] intel_idle: v0.4 model 0x2A
[    0.509836] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.708686] ACPI: AC Adapter [ADP0] (on-line)
[    0.708740] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.708744] ACPI: Power Button [PWRB]
[    0.708766] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.708768] ACPI: Sleep Button [SLPB]
[    0.708790] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.709300] ACPI: Lid Switch [LID0]
[    0.709328] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.709330] ACPI: Power Button [PWRF]
[    0.709374] ACPI: Requesting acpi_cpufreq
[    0.710884] thermal LNXTHERM:00: registered as thermal_zone0
[    0.710886] ACPI: Thermal Zone [TZ00] (68 C)
[    0.711045] thermal LNXTHERM:01: registered as thermal_zone1
[    0.711047] ACPI: Thermal Zone [TZ01] (68 C)
[    0.711073] GHES: HEST is not enabled!
[    0.711145] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.716649] Linux agpgart interface v0.103
[    0.717683] brd: module loaded
[    0.718154] loop: module loaded
[    0.718382] libphy: Fixed MDIO Bus: probed
[    0.718437] tun: Universal TUN/TAP device driver, 1.6
[    0.718438] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.718466] PPP generic driver version 2.4.2
[    0.718493] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.718494] ehci-pci: EHCI PCI platform driver
[    0.718568] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.718576] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.718580] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.718594] ehci-pci 0000:00:1a.0: debug port 2
[    0.722490] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.722507] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf3c0a000
[    0.725231] ACPI: Battery Slot [BAT0] (battery present)
[    0.732709] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.732725] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.732726] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.732728] usb usb1: Product: EHCI Host Controller
[    0.732730] usb usb1: Manufacturer: Linux 3.11.0-14-generic ehci_hcd
[    0.732731] usb usb1: SerialNumber: 0000:00:1a.0
[    0.732804] hub 1-0:1.0: USB hub found
[    0.732807] hub 1-0:1.0: 2 ports detected
[    0.732921] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.732926] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.732930] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.732941] ehci-pci 0000:00:1d.0: debug port 2
[    0.736849] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.736864] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf3c09000
[    0.748726] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.748739] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.748741] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.748742] usb usb2: Product: EHCI Host Controller
[    0.748744] usb usb2: Manufacturer: Linux 3.11.0-14-generic ehci_hcd
[    0.748745] usb usb2: SerialNumber: 0000:00:1d.0
[    0.748814] hub 2-0:1.0: USB hub found
[    0.748816] hub 2-0:1.0: 2 ports detected
[    0.748870] ehci-platform: EHCI generic platform driver
[    0.748875] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.748876] ohci-platform: OHCI generic platform driver
[    0.748880] uhci_hcd: USB Universal Host Controller Interface driver
[    0.748930] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    0.748935] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    0.749116] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
[    0.749122] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
[    0.749127] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
[    0.749133] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
[    0.749137] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
[    0.749255] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.749256] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.749258] usb usb3: Product: xHCI Host Controller
[    0.749259] usb usb3: Manufacturer: Linux 3.11.0-14-generic xhci_hcd
[    0.749261] usb usb3: SerialNumber: 0000:04:00.0
[    0.749305] xHCI xhci_add_endpoint called for root hub
[    0.749307] xHCI xhci_check_bandwidth called for root hub
[    0.749321] hub 3-0:1.0: USB hub found
[    0.749327] hub 3-0:1.0: 2 ports detected
[    0.749373] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    0.749376] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    0.752528] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.752530] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.752531] usb usb4: Product: xHCI Host Controller
[    0.752533] usb usb4: Manufacturer: Linux 3.11.0-14-generic xhci_hcd
[    0.752534] usb usb4: SerialNumber: 0000:04:00.0
[    0.752581] xHCI xhci_add_endpoint called for root hub
[    0.752582] xHCI xhci_check_bandwidth called for root hub
[    0.752595] hub 4-0:1.0: USB hub found
[    0.752601] hub 4-0:1.0: 2 ports detected
[    0.756772] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.761759] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.761763] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.761846] mousedev: PS/2 mouse device common for all mice
[    0.762033] rtc_cmos 00:04: RTC can wake from S4
[    0.762142] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.762169] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.762211] device-mapper: uevent: version 1.0.3
[    0.762253] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.762323] cpuidle: using governor ladder
[    0.762405] cpuidle: using governor menu
[    0.762412] ledtrig-cpu: registered to indicate activity on CPUs
[    0.762473] TCP: cubic registered
[    0.762533] NET: Registered protocol family 10
[    0.762679] NET: Registered protocol family 17
[    0.762689] Key type dns_resolver registered
[    0.762899] PM: Hibernation image not present or could not be loaded.
[    0.762902] Loading module verification certificates
[    0.763671] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 4f57df1a3429640d83ffde722907e1377213486f'
[    0.763680] registered taskstats version 1
[    0.765508] Key type trusted registered
[    0.767052] Key type encrypted registered
[    0.767513] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.768697] AppArmor: AppArmor sha1 policy hashing enabled
[    0.769127]   Magic number: 9:102:36
[    0.769134] bdi 7:1: hash matches
[    0.769137] misc loop-control: hash matches
[    0.769235] rtc_cmos 00:04: setting system clock to 2013-12-04 17:00:51 UTC (1386176451)
[    0.769701] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.769702] EDD information not available.
[    0.770390] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    0.770391] Write protecting the kernel read-only data: 12288k
[    0.772135] Freeing unused kernel memory: 1036K (ffff8800016fd000 - ffff880001800000)
[    0.773386] Freeing unused kernel memory: 836K (ffff880001b2f000 - ffff880001c00000)
[    0.786338] systemd-udevd[141]: starting version 204
[    0.893567] microcode: module verification failed: signature and/or required key missing - tainting kernel
[    0.893777] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x25
[    0.893803] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x25
[    0.894253] microcode: CPU0 updated to revision 0x29, date = 2013-06-12
[    0.894259] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x25
[    0.894271] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x25
[    0.894509] microcode: CPU1 updated to revision 0x29, date = 2013-06-12
[    0.894517] microcode: CPU2 sig=0x206a7, pf=0x10, revision=0x25
[    0.894533] microcode: CPU2 sig=0x206a7, pf=0x10, revision=0x25
[    0.894773] microcode: CPU2 updated to revision 0x29, date = 2013-06-12
[    0.894780] microcode: CPU3 sig=0x206a7, pf=0x10, revision=0x25
[    0.894793] microcode: CPU3 sig=0x206a7, pf=0x10, revision=0x25
[    0.895040] microcode: CPU3 updated to revision 0x29, date = 2013-06-12
[    0.895042] perf_event_intel: PEBS enabled due to microcode update
[    0.895088] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.997314] ahci 0000:00:1f.2: version 3.0
[    0.997439] ahci 0000:00:1f.2: irq 48 for MSI/MSI-X
[    0.997469] ahci: SSS flag set, parallel bus scan disabled
[    1.013113] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl SATA mode
[    1.013119] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.013126] ahci 0000:00:1f.2: setting latency timer to 64
[    1.021476] scsi0 : ahci
[    1.021547] scsi1 : ahci
[    1.021616] scsi2 : ahci
[    1.021676] scsi3 : ahci
[    1.021749] scsi4 : ahci
[    1.021808] scsi5 : ahci
[    1.021852] ata1: SATA max UDMA/133 abar m2048@0xf3c08000 port 0xf3c08100 irq 48
[    1.021854] ata2: DUMMY
[    1.021855] ata3: DUMMY
[    1.021856] ata4: DUMMY
[    1.021858] ata5: SATA max UDMA/133 abar m2048@0xf3c08000 port 0xf3c08300 irq 48
[    1.021859] ata6: DUMMY
[    1.030398] atl1c 0000:06:00.0: version 1.0.1.1-NAPI
[    1.045129] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.177872] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.177876] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.178360] hub 1-1:1.0: USB hub found
[    1.178553] hub 1-1:1.0: 6 ports detected
[    1.289507] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.341569] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.353069] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.353902] ata1.00: ATA-8: SanDisk SDSSDX240GG25, R211, max UDMA/133
[    1.353912] ata1.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.363108] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.363936] ata1.00: configured for UDMA/133
[    1.369779] scsi 0:0:0:0: Direct-Access     ATA      SanDisk SDSSDX24 R211 PQ: 0 ANSI: 5
[    1.369913] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/223 GiB)
[    1.369921] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.369972] sd 0:0:0:0: [sda] Write Protect is off
[    1.369975] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.369991] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.370833]  sda: sda1 < sda5 > sda2 sda3
[    1.371466] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.422168] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.422171] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.422489] hub 2-1:1.0: USB hub found
[    1.422575] hub 2-1:1.0: 8 ports detected
[    1.485731] tsc: Refined TSC clocksource calibration: 2793.653 MHz
[    1.493971] usb 1-1.4: new high-speed USB device number 3 using ehci-pci
[    1.642979] usb 1-1.4: New USB device found, idVendor=0c45, idProduct=642a
[    1.642997] usb 1-1.4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.642999] usb 1-1.4: Product: Laptop_Integrated_Webcam_2HDM
[    1.643000] usb 1-1.4: Manufacturer: CN0XRCWG72487168S2CVA00
[    1.690006] ata5: SATA link down (SStatus 0 SControl 300)
[    1.718030] usb 2-1.5: new full-speed USB device number 3 using ehci-pci
[    1.786008] raid6: sse2x1    8969 MB/s
[    1.814398] usb 2-1.5: New USB device found, idVendor=8086, idProduct=0189
[    1.814401] usb 2-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.854089] raid6: sse2x2   11153 MB/s
[    1.922178] raid6: sse2x4   13040 MB/s
[    1.922180] raid6: using algorithm sse2x4 (13040 MB/s)
[    1.922181] raid6: using ssse3x2 recovery algorithm
[    1.922552] xor: automatically using best checksumming function:
[    1.962222]    avx       : 25504.000 MB/sec
[    1.964594] bio: create slab <bio-1> at 1
[    1.964738] Btrfs loaded
[    1.967629] device fsid 1e55f019-8d6a-4d39-8b26-f8d5cc8a1597 devid 1 transid 27108 /dev/sda2
[    1.972401] device fsid 1e55f019-8d6a-4d39-8b26-f8d5cc8a1597 devid 1 transid 27108 /dev/disk/by-uuid/1e55f019-8d6a-4d39-8b26-f8d5cc8a1597
[    1.972737] btrfs: disk space caching is enabled
[    2.036975] Btrfs detected SSD devices, enabling SSD mode
[    2.486951] Switched to clocksource tsc
[    4.305791] Adding 4882428k swap on /dev/sda3.  Priority:-1 extents:1 across:4882428k SSFS
[    4.312312] btrfs: use lzo compression
[    4.312315] btrfs: turning off barriers
[    4.312318] btrfs: use ssd allocation scheme
[    4.312319] btrfs: use spread ssd allocation scheme
[    4.312320] btrfs: disk space caching is enabled
[    4.312469] BTRFS debug (device sda2): unlinked 6 orphans
[    4.313621] BTRFS debug (device sda2): unlinked 10 orphans
[    4.313623] BTRFS debug (device sda2): truncated 5 orphans
[    4.340420] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.362457] systemd-udevd[403]: starting version 204
[    4.363195] device fsid 1e55f019-8d6a-4d39-8b26-f8d5cc8a1597 devid 1 transid 27111 /dev/sda2
[    4.378990] lp: driver loaded but no devices found
[    4.605710] Bluetooth: Core ver 2.16
[    4.605728] NET: Registered protocol family 31
[    4.605730] Bluetooth: HCI device and connection manager initialized
[    4.605737] Bluetooth: HCI socket layer initialized
[    4.605739] Bluetooth: L2CAP socket layer initialized
[    4.605745] Bluetooth: SCO socket layer initialized
[    4.612244] wmi: Mapper loaded
[    4.621741] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.621744] Bluetooth: BNEP filters: protocol multicast
[    4.621752] Bluetooth: BNEP socket layer initialized
[    4.624956] [drm] Initialized drm 1.1.0 20060810
[    4.625552] Bluetooth: RFCOMM TTY layer initialized
[    4.625562] Bluetooth: RFCOMM socket layer initialized
[    4.625564] Bluetooth: RFCOMM ver 1.11
[    4.630389] nvidia: module license 'NVIDIA' taints kernel.
[    4.630393] Disabling lock debugging due to kernel taint
[    4.656700] mei_me 0000:00:16.0: setting latency timer to 64
[    4.656741] mei_me 0000:00:16.0: irq 49 for MSI/MSI-X
[    4.658331] cfg80211: Calling CRDA to update world regulatory domain
[    4.672649] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    4.672652] Copyright(c) 2003-2013 Intel Corporation
[    4.672914] iwlwifi 0000:03:00.0: irq 50 for MSI/MSI-X
[    4.677375] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    4.684946] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[    4.685005] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    4.686168] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[    4.686176] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  319.60  Wed Sep 25 14:28:26 PDT 2013
[    4.689011] ppdev: user-space parallel port driver
[    4.706589] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    4.706593] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    4.706595] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    4.706597] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[    4.706599] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[    4.706841] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    4.720089] type=1400 audit(1386176455.439:2): apparmor="STATUS" operation="profile_load" parent=553 profile="unconfined" name="/sbin/dhclient" pid=554 comm="apparmor_parser"
[    4.720097] type=1400 audit(1386176455.439:3): apparmor="STATUS" operation="profile_load" parent=553 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=554 comm="apparmor_parser"
[    4.720103] type=1400 audit(1386176455.439:4): apparmor="STATUS" operation="profile_load" parent=553 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=554 comm="apparmor_parser"
[    4.720636] type=1400 audit(1386176455.439:5): apparmor="STATUS" operation="profile_replace" parent=553 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=554 comm="apparmor_parser"
[    4.720644] type=1400 audit(1386176455.439:6): apparmor="STATUS" operation="profile_replace" parent=553 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=554 comm="apparmor_parser"
[    4.720931] type=1400 audit(1386176455.439:7): apparmor="STATUS" operation="profile_replace" parent=553 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=554 comm="apparmor_parser"
[    4.732007] init: avahi-cups-reload main process (528) terminated with status 1
[    4.752579] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.757735] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[    4.757742] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.757746] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIN 1 (20130517/utaddress-251)
[    4.757749] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 2 (20130517/utaddress-251)
[    4.757753] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 3 (20130517/utaddress-251)
[    4.757756] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.757758] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIN 1 (20130517/utaddress-251)
[    4.757760] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 2 (20130517/utaddress-251)
[    4.757763] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 3 (20130517/utaddress-251)
[    4.757766] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.757767] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIN 1 (20130517/utaddress-251)
[    4.757770] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 2 (20130517/utaddress-251)
[    4.757773] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 3 (20130517/utaddress-251)
[    4.757776] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.757777] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    4.760876] type=1400 audit(1386176455.479:8): apparmor="STATUS" operation="profile_load" parent=547 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=592 comm="apparmor_parser"
[    4.760881] type=1400 audit(1386176455.479:9): apparmor="STATUS" operation="profile_load" parent=547 profile="unconfined" name="/usr/sbin/cupsd" pid=592 comm="apparmor_parser"
[    4.761360] type=1400 audit(1386176455.479:10): apparmor="STATUS" operation="profile_replace" parent=547 profile="unconfined" name="/usr/sbin/cupsd" pid=592 comm="apparmor_parser"
[    4.763551] [drm] Memory usable by graphics device = 2048M
[    4.763558] i915 0000:00:02.0: setting latency timer to 64
[    4.803060] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    4.804202] dell_laptop: unknown parameter 'backlight' ignored
[    4.831287] i915 0000:00:02.0: irq 51 for MSI/MSI-X
[    4.831296] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.831297] [drm] Driver supports precise vblank timestamp query.
[    4.831313] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[    4.831381] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[    4.831428] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[    4.831452] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[    4.874190] [drm] Wrong MCH_SSKPD value: 0x16040307
[    4.874193] [drm] This can cause pipe underruns and display issues.
[    4.874195] [drm] Please upgrade your BIOS to fix this.
[    4.885792] input: Dell WMI hotkeys as /devices/virtual/input/input5
[    4.896210] cfg80211: World regulatory domain updated:
[    4.896214] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.896217] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.896218] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.896220] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.896222] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.896224] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.946317] init: failsafe main process (628) killed by TERM signal
[    4.973965] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    4.997208] fbcon: inteldrmfb (fb0) is primary device
[    5.001653] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[    5.002853] device fsid 1e55f019-8d6a-4d39-8b26-f8d5cc8a1597 devid 1 transid 27111 /dev/sda2
[    5.024297] device fsid 1e55f019-8d6a-4d39-8b26-f8d5cc8a1597 devid 1 transid 27111 /dev/sda2
[    5.133947] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    5.140605] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    5.411055] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    5.417733] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    5.496001] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.497414] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.502382] atl1c 0000:06:00.0: irq 52 for MSI/MSI-X
[    5.520030] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.523076] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.775052] Console: switching to colour frame buffer device 240x67
[    5.780691] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    5.780693] i915 0000:00:02.0: registered panic notifier
[    5.780888] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    5.780918] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    5.780974] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/LNXVIDEO:00/input/input7
[    5.820198] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    5.820263] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[    5.820545] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[    5.820683] snd_hda_intel 0000:00:1b.0: irq 53 for MSI/MSI-X
[    5.837524] SKU: Nid=0x1d sku_cfg=0x40179a2d
[    5.837528] SKU: port_connectivity=0x1
[    5.837529] SKU: enable_pcbeep=0x1
[    5.837530] SKU: check_sum=0x00000007
[    5.837531] SKU: customization=0x0000009a
[    5.837532] SKU: external_amp=0x5
[    5.837533] SKU: platform_type=0x1
[    5.837534] SKU: swap=0x0
[    5.837535] SKU: override=0x1
[    5.838128] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    5.838130]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.838131]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    5.838131]    mono: mono_out=0x0
[    5.838132]    inputs:
[    5.838133]      Mic=0x18
[    5.838134]      Internal Mic=0x12
[    5.838135] realtek: No valid SSID, checking pincfg 0x40179a2d for NID 0x1d
[    5.838136] realtek: Enabling init ASM_ID=0x9a2d CODEC_ID=10ec0269
[    5.869806] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    5.870191] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    5.870488] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11

```

Sincerely,

Adam

---

### Post by oldfred on 2013-12-04
Changed quote to code tags. please use code tags.

That says 5.87 sec and the only with a gap at all is the mounting of swap.

---

### Post by adamzendarski on 2013-12-22
Hi,

After really looking at my bootchart and looking through my logs files, I found the handoff to XORG takes about 30 SECONDS.

The following are files I have uploaded, relevant to the situation:
**Dmesg Log File:** [http://www.adamsassets.com/ubuntu/dmesg.txt](http://www.adamsassets.com/ubuntu/dmesg.txt)
**Xorg Log File:** [http://www.adamsassets.com/ubuntu/Xorg.0.log.txt](http://www.adamsassets.com/ubuntu/Xorg.0.log.txt)
**Bootchart Image:** [http://www.adamsassets.com/ubuntu/x-x-saucy-20131222-1.png](http://www.adamsassets.com/ubuntu/x-x-saucy-20131222-1.png) **(Don't forget to ZOOM for a larger view!)**

Notice how the handoff to XORG takes about 30 SECONDS to start. The difference between the "dmesg.txt" log file and the "Xorg.0.log.txt" is 25 seconds! Why is it taking so long for XORG to start?
Looking at the bootchart, there's not too much is going on between about 9 seconds and 30 seconds.
I believe the problem is the handoff to XORG.

**What can I do to resolve the problem?**

Thank you for any help you can offer.

Sincerely,

Adam

---

### Post by oldfred on 2013-12-22
Looking at this you seem to have a lot of boot options that are video related.
>  [    29.279] Kernel command line: [EMAIL="BOOT_IMAGE=/@/boot/vmlinuz-3.11.0"]BOOT_IMAGE=/@/boot/vmlinuz-3.11.0[/EMAIL]-14-generic root=UUID=1e55f019-8d6a-4d39-8b26-f8d5cc8a1597 ro rootflags=subvol=@ crashkernel=384M-2G:64M,2G-:128M acpi_backlight=vendor dell_laptop.backlight=0 pcie_aspm=force i915.i915_enable_rc6=1 drm.vblankoffdelay=1 i915.semaphores=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 vt.handoff=7 quiet splash elevator=deadline acpi_osi=linux



I have seen users (or suggested same) for most of those but never all of those at once. Do some perhaps conflict?

---

### Post by adamzendarski on 2013-12-23
Nope, I've tried it with only *acpi_backlight=vendor dell_laptop.backlight=0 quiet splash* and no luck.

---

### Post by oldfred on 2013-12-23
What computer is this and what video card/chip do you have?
Version of Intel chip does seem to make a difference, but I do not know what works for each version.

---

### Post by adamzendarski on 2013-12-23
Dell XPS 15z with Nvidia GeForce GT 525m & Intel HD Graphics 3000.

---

### Post by oldfred on 2013-12-23
Some other Dell models. They seem to be similar across models with just the added options or screen size differences.

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
      
 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

Someone posted that all of sputnik is in 13.10

 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

dual video usually needs bumblebee.
      
 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

### Post by adamzendarski on 2013-12-24
Here is an outline of some slow things during boot and shutdown when removing *quiet splash* from the grub config:

```

--------- SHUTDOWN ATTEMPT #1
START 0:00

Applying power save settings...done.
* Starting TiMidity++ ALSA midi emulation...
* Stopping System V runlevel compatibility
* Starting
* Starting Mount network filesystems
* Stopping Mount network filesystems
* Starting startpar bridge for notification of upstart job start/stop
* Stopping startpar bridge for notification of upstart job start/stop
Applying power save settings...done.lation... ###### SLOW ###### 0:03 0:09 (5 Seconds)
...
* Stopping domain name service bind9 ###### SLOW ###### 0:11 0:17 (6 Seconds)
waiting for pid 1689 to die
...
ModemManager[873]: <info> ModemManager is shut down

* Deactivating swap...
* Unmounting weak filesystems... ###### SLOW ###### 0:22 0:42 (20 Seconds)

END 0:39
--------- SHUTDOWN ATTEMPT #1

--------- BOOT AAA
START 0:00

Starting domain name service... bind9
...
Applying power save settings...done.
* Starting TiMidity++ ALSA midi emulation...
* Stopping System V runlevel compatibility
* Starting
* Stopping cold plug devices
* Stopping log initial device creation
* Starting save udev log and update rules
* Stopping save udev log and update rules ###### SLOW ###### 0:07 0:12 (5 Seconds)
* Starting Mount network filesystems
* Starting startpar bridge for notification of upstart job start/stop
* Stopping startpar bridge for notification of upstart job start/stop
* Stopping Mount network filesystems ###### SLOW ###### 0:13 0:30 (17 Seconds)

END 0:31
--------- BOOT ATTEMPT #1



--------- SHUTDOWN ATTEMPT #2
START 0:00

waiting for pid 1728 to die
* Stopping domain name service bind9
...
ModemManager[894]: <info> ModemManager is shut down

* Deactivating swap...
* Unmounting weak filesystems... ###### SLOW ###### 0:27 0:47 (20 Seconds)

END 0:48
--------- SHUTDOWN ATTEMPT #2


--------- BOOT ATTEMPT #2
START 0:00


Starting domain name service... bind9
...
Applying power save settings...done.
* Starting TiMidity++ ALSA midi emulation...
* Stopping System V runlevel compatibility
* Starting ###### SLOW ###### 0:05 0:11 (6 Seconds)
* Stopping cold plug devices
* Stopping log initial device creation
* Starting save udev log and update rules
* Stopping save udev log and update rules
* Starting Mount network filesystems
* Starting startpar bridge for notification of upstart job start/stop
* Stopping startpar bridge for notification of upstart job start/stop
* Stopping Mount network filesystems ###### SLOW ###### 0:12 0:29 (17 Seconds)

END 0:30
--------- BOOT ATTEMPT #2

```

---

### Post by adamzendarski on 2013-12-24
And I do have Bumblebee.

---

### Post by adamzendarski on 2013-12-24
Also, I think it's worth noting that when I originally installed Ubuntu,  my laptop booted Ubuntu in 2 or 3 seconds, and shutdown was instant.

After  I installed Ubuntu, a couple boots later, I used a script that I wrote  to bulk install all kinds of packages from Launchpad at once, but as I  can imagine, it is only one package out of the few hundred I have  installed via my script.

I guess I'm just looking for the problem  without having to reinstall Ubuntu and nitpick through all of the  packages. Although, I will if I have to.

As shown in post #12, the biggest problem in both boots and shutdowns (found by removing *quiet spash* from grub.conf) is when the systems attempts the following:

```

**SLOW DURING BOOT:**

* Stopping Mount network filesystems ###### SLOW ###### (17 Seconds)
* Stopping save udev log and update rules ###### SLOW ###### (5 Seconds)
* Stopping startpar bridge for notification of upstart job start/stop ###### SOMETIMES SLOW ###### (Sometimes takes 7 seconds)

-----------------

**SLOW DURING SHUTDOWN:**

* Unmounting weak filesystems... ###### SLOW ###### (20 Seconds)
* Stopping domain name service bind9 ###### SLOW ###### (6 Seconds)

```

---

### Post by oldfred on 2013-12-24
What network systems are you mounting.

I have found mounting NTFS partitions on my system slow boot a lot. I still have a NTFS from when I dual booted with XP, but need to convert all that data to ext4 partition since I do not use XP now.
Sometimes a chkdsk or full e2fsck on a partition can help.

---

### Post by adamzendarski on 2013-12-25
My entire SSD is dedicated to Ubuntu with a BTRFS file system.

No separate partition, HDD, SSD, or USB was connected at the time of boot.

---

### Post by oldfred on 2013-12-25
I do not know about btrfs.

 BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)
Linux 3.11 File-System Performance: EXT4, Btrfs, XFS, F2FS
[http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1)
EXT4 Still Leads Over Btrfs File-System On Linux 3.8
[http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1)
[http://www.phoronix.com/scan.php?page=news_item&px=MTM1MTE](http://www.phoronix.com/scan.php?page=news_item&px=MTM1MTE)

---

### Post by adamzendarski on 2013-12-26
I've been using BTRFS since 11.10.

I've only had trouble with BTRFS once during something like Ubuntu 12.04 or 12.10 and it was related to the kernel at the time. Since then, I have had an extremely positive experience with BTRFS and I have watched the quick and miraculous turnaround of such a great file system.

There are a couple things I nitpicked about (and still do) as far as EXT4 goes. in my opinion, EXT4 is better as an eHDD or USB file system.

I know the boot problem isn't the result of BTRFS, because when I originally installed the current version of Ubuntu onto my laptop (with the SSD), the boot time was literally 3 seconds, to go from cold boot to the desktop (using auto login).

I am almost certain that there is a package I've installed after the original installation that caused the problem. The problem for me is that there are well over 250 packages I bulk installed in one session.

Either way, I accidentally dd'd my installation of Ubuntu with if=/dev/zero while trying to get USB performance stats with iostat, so I have no choice but to reinstall now.

After I'm done reinstalling, I will split up the script I created that installs all of my 250+ favorite packages at once and try to reboot multiple times between multiple sets of package installation so I can narrow down the package that caused the problem.

Thank you @oldfred for the time, hard work, and effort you have offered. The profound support is what keeps Ubuntu going.

I will update this thread when I'm done with the reinstall and have found the source of my problems.

Sincerely,

Adam

---

### Post by nyny83 on 2014-01-03
I'm having the same kind of problems. The booting seems fast and my login screen appears pretty quick (<10 sec, seems ok to me) but after I login I have a black screen with only a mouse cursor on it. When I switch to console 1 I see some messages about starting and stopping startpar bridge. After about 30 seconds my disk starts rattling and my X appears (after switching to console 7 ofc). 

My laptop: 
Dell L702x with Intel HD3000 and Nvidia G550M video cards and bumblebee. 

The thing most of us seem to have in common is that we all use bumblebee. Therefore I think it's safe to say the problem is in bumblebee.

---

### Post by adamzendarski on 2014-01-15
Problem packages finally found. After hundreds of boots, shutdowns, package installations, and removals, after 3 sets of install and removal of sbackup and 3 reboots in between installations and removals of sbackup, I can confirm and conclude that **the packages that have caused my boot problem are sbackup and sbackup-gtk**.

**Sbackup and sbackup-gtk cause my the loading of xorg, gdm, and gnome-shell to be delayed by 25 seconds.**

The solution is simple, remove sbackup and sbackup-gtk.

---

