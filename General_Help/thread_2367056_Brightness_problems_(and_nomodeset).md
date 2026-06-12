---
title: "Brightness problems (and nomodeset?)"
date: 2017-07-25
forum: General Help
---

### Post by chrisk0 on 2017-07-25
Have Xubuntu Zapus running pretty well on my Dell Inspiron 3000 laptop now. The main problem now is that I have no control over the screen brightness, which seems to be set at a low level compared to the max brightness on Windows.

Laptop has an Intel graphics card, and I have run the Intel graphics driver update tool successfully.

I've installed brightness-controller and brightness-controller-simple from repository, and when I run them as administrator, I get messages like:
[INDENT]xrandr: Failed to get size of gamma for output default
xrandr: Gamma size is 0.[/INDENT]

And when I move the sliders there's no apparent change in screen brightness.

I've seen some indications that this might be because I put nomodeset in my grub, in place of quiet splash. When I try to go back to booting under quiet splash, all I get is a black screen, and I'm not completely clear how to troubleshoot that.

Thank you in advance for any assistance.

---

### Post by efflandt on 2017-07-25
Did or do the normal keyboard brightness settings work originally (which uses ACPI)? Or do BIOS/UEFI settings work?

But the only Dell laptop I have is 10 years old with legacy ATI X1300 graphics.

---

### Post by BenginM on 2017-07-26
Salutations!
The newest kernels have moved the video mode setting into the   kernel. So all the programming of the hardware specific clock rates   and registers on the video card happen in the kernel rather than in   the X driver when the X server starts.. This makes it possible to have   high resolution nice looking splash (boot) screens and flicker free   transitions from boot splash to login screen. Unfortunately, on some   cards this doesn't work properly and you end up with a black screen.   Adding the nomodeset parameter instructs the kernel to not load video   drivers and use BIOS modes instead until X is loaded. (nomodeset - tells the kernel to not start video drivers until the system is up and running.)!>

nomodeset is a temporary  solution/workaround until fixing the graphic card, either by installing a  driver or upgrading to a newer version. It can cause  several problems depending on Kernel version, hardware. Many free drivers have removed support for non-kernel mode setting, so in those  cases when you use nomodeset you will end up falling back to the very  basic VESA un-accelerated driver.  This is very much a performance and  feature hit. Radeon and Intel Graphics has removed User Mode Setting" (what nomodeset forces the computer to use) 

## So..
 lets look into your situation ..So you had to set the nomodeset in the first place because ..! 

Please paste the outputs of these command in a ```
 tag like so .. 

[PHP]
[CODE]

$ lspci | grep VGA
$ ls /sys/class/backlight
$ dmesg


```
[/PHP]

to let us look at the logs which might help to indicate the cause of the black screen without nomodeset ...thanks.

---

### Post by BenginM on 2017-07-26
Well, looking on the web .. some users had the same issue with no control over brightness.. and updating the BIOS solved this!

---

### Post by chrisk0 on 2017-07-29
Hey! Thanks everybody, and sorry I didn't notice the replies sooner... *futzes with subscription notification settings*

The original brightness hotkeys of Fn-F11 and Fn-F12 still work when I'm in the BIOS menu, but stop once I get to the Xubuntu login menu.

I've already updated the BIOS to v2.0.1, the latest update to this model from about a month ago. (That was while I was still trying to figure out how to boot from the liveUSB using UEFI)

Here's the output from the suggested commands:
```

chris@bali-blue:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 21)
chris@bali-blue:~$ ls /sys/class/backlight
chris@bali-blue:~$ dmesg
[    0.000000] Linux version 4.10.0-28-generic (buildd@lgw01-11) (gcc version 6.3.0 20170406 (Ubuntu 6.3.0-12ubuntu2) ) #32-Ubuntu SMP Fri Jun 30 05:32:18 UTC 2017 (Ubuntu 4.10.0-28.32-generic 4.10.17)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-28-generic.efi.signed root=UUID=e34fc988-8001-49b4-986a-03d795ad2156 ro nomodeset
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000003efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000003f000-0x000000000003ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000000040000-0x000000000009ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001effffff] usable
[    0.000000] BIOS-e820: [mem 0x000000001f000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x000000007a5eafff] usable
[    0.000000] BIOS-e820: [mem 0x000000007a5eb000-0x000000007a66afff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007a66b000-0x000000007a67cfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007a67d000-0x000000007b54bfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007b54c000-0x000000007b911fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007b912000-0x000000007b968fff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007b969000-0x000000007bffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fea00000-0x00000000feafffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed03000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed06000-0x00000000fed06fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed09fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1cfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fedbffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff980000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ESRT=0x7b90e298  ACPI=0x7a66e000  ACPI 2.0=0x7a66e000  SMBIOS=0xf05e0  MPS=0xfc910 
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: Dell Inc. Inspiron 11-3162/0J71G2, BIOS 2.0.1 05/05/2017
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07C800000 mask FFF800000 uncachable
[    0.000000]   2 base 07D000000 mask FFF000000 uncachable
[    0.000000]   3 base 07E000000 mask FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] total RAM covered: 1992M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] found SMP MP-table at [mem 0x000fcaa0-0x000fcaaf] mapped at [ffff934d800fcaa0]
[    0.000000] esrt: Reserving ESRT space from 0x000000007b90e298 to 0x000000007b90e2d0.
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff934d80097000] 97000 size 24576
[    0.000000] BRK [0x6f429000, 0x6f429fff] PGTABLE
[    0.000000] BRK [0x6f42a000, 0x6f42afff] PGTABLE
[    0.000000] BRK [0x6f42b000, 0x6f42bfff] PGTABLE
[    0.000000] BRK [0x6f42c000, 0x6f42cfff] PGTABLE
[    0.000000] BRK [0x6f42d000, 0x6f42dfff] PGTABLE
[    0.000000] BRK [0x6f42e000, 0x6f42efff] PGTABLE
[    0.000000] BRK [0x6f42f000, 0x6f42ffff] PGTABLE
[    0.000000] RAMDISK: [mem 0x32cc5000-0x35659fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000007A66E000 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 0x000000007A66E0A0 0000BC (v01 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x000000007A678950 00010C (v05 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 128/32 (20160930/tbfadt-603)
[    0.000000] ACPI: DSDT 0x000000007A66E1E8 00A764 (v02 DELL   WN09     01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x000000007B549E80 000040
[    0.000000] ACPI: APIC 0x000000007A678A60 000068 (v03 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x000000007A678AC8 000044 (v01 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x000000007A678B10 00009C (v01 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x000000007A678BB0 00003C (v01 DELL   WN09     01072009 MSFT 00000097)
[    0.000000] ACPI: BOOT 0x000000007A678BF0 000028 (v01 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: SLIC 0x000000007A678C18 000176 (v01 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: HPET 0x000000007A678D90 000038 (v01 DELL   WN09     01072009 AMI. 00000000)
[    0.000000] ACPI: SSDT 0x000000007A678DC8 000763 (v01 PmRef  CpuPm    00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 0x000000007A679530 000290 (v01 PmRef  Cpu0Tst  00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 0x000000007A6797C0 00017A (v01 PmRef  ApTst    00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 0x000000007A679940 000042 (v01 DELL   WN09     00000000      00000000)
[    0.000000] ACPI: MSDM 0x000000007A679988 000055 (v03 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: LPIT 0x000000007A6799E0 000104 (v01 DELL   WN09     00000005 MSFT 0100000D)
[    0.000000] ACPI: BGRT 0x000000007A679AE8 000038 (v01 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: TPM2 0x000000007A679B20 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
[    0.000000] ACPI: CSRT 0x000000007A679B58 00014C (v00 INTEL  LANFORDC 00000005 MSFT 0100000D)
[    0.000000] ACPI: SSDT 0x000000007A679CA8 000544 (v01 CpuDpf CpuDptf  00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 0x000000007A67A1F0 002230 (v01 DptfTb DptfTab  00001000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007bffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x7a22d000-0x7a257fff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x000000007bffffff]
[    0.000000]   Normal   empty
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000003efff]
[    0.000000]   node   0: [mem 0x0000000000040000-0x000000000009ffff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000001effffff]
[    0.000000]   node   0: [mem 0x0000000020200000-0x000000007a5eafff]
[    0.000000]   node   0: [mem 0x000000007b969000-0x000000007bffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000007bffffff]
[    0.000000] On node 0 totalpages: 498208
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 26 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7872 pages used for memmap
[    0.000000]   DMA32 zone: 494210 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics memory at 0x000000007ce00000-0x000000007edfffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-114
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0003f000-0x0003ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x1f000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7a5eb000-0x7a66afff]
[    0.000000] PM: Registered nosave memory: [mem 0x7a66b000-0x7a67cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7a67d000-0x7b54bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7b54c000-0x7b911fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7b912000-0x7b968fff]
[    0.000000] e820: [mem 0x7ee00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:8192 nr_cpumask_bits:2 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] percpu: Embedded 36 pages/cpu @ffff934dfa000000 s107992 r8192 d31272 u1048576
[    0.000000] pcpu-alloc: s107992 r8192 d31272 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 490246
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-28-generic.efi.signed root=UUID=e34fc988-8001-49b4-986a-03d795ad2156 ro nomodeset
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1798608K/1992832K available (9083K kernel code, 1666K rwdata, 3816K rodata, 2232K init, 2364K bss, 194224K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=2.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=2
[    0.000000] NR_IRQS:524544 nr_irqs:512 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Detected 1600.000 MHz processor
[    0.000043] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.00 BogoMIPS (lpj=6400000)
[    0.000062] pid_max: default: 32768 minimum: 301
[    0.000106] ACPI: Core revision 20160930
[    0.021953] ACPI: 6 ACPI AML tables successfully acquired and loaded
[    0.023148] Security Framework initialized
[    0.023161] Yama: becoming mindful.
[    0.023204] AppArmor: AppArmor initialized
[    0.023561] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.024780] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.025345] Mount-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.025369] Mountpoint-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.025947] CPU: Physical Processor ID: 0
[    0.025960] CPU: Processor Core ID: 0
[    0.025972] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.025981] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.026002] mce: CPU supports 6 MCE banks
[    0.026026] process: using mwait in idle threads
[    0.026041] Last level iTLB entries: 4KB 48, 2MB 0, 4MB 0
[    0.026052] Last level dTLB entries: 4KB 256, 2MB 16, 4MB 16, 1GB 0
[    0.026413] Freeing SMP alternatives memory: 32K
[    0.038554] ftrace: allocating 34179 entries in 134 pages
[    0.071571] smpboot: Max logical packages: 1
[    0.073281] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.112991] TSC deadline timer enabled
[    0.112997] smpboot: CPU0: Intel(R) Celeron(R) CPU  N3050  @ 1.60GHz (family: 0x6, model: 0x4c, stepping: 0x3)
[    0.113197] Performance Events: PEBS fmt2+, 8-deep LBR, Silvermont events, 8-deep LBR, full-width counters, Intel PMU driver.
[    0.113237] ... version:                3
[    0.113245] ... bit width:              40
[    0.113252] ... generic registers:      2
[    0.113260] ... value mask:             000000ffffffffff
[    0.113268] ... max period:             0000007fffffffff
[    0.113276] ... fixed-purpose events:   3
[    0.113283] ... event mask:             0000000700000003
[    0.115233] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.115300] smp: Bringing up secondary CPUs ...
[    0.115628] x86: Booting SMP configuration:
[    0.115641] .... node  #0, CPUs:      #1
[    0.115890] smp: Brought up 1 node, 2 CPUs
[    0.115907] smpboot: Total of 2 processors activated (6400.00 BogoMIPS)
[    0.117116] devtmpfs: initialized
[    0.117297] x86/mm: Memory block size: 128MB
[    0.125266] evm: security.selinux
[    0.125276] evm: security.SMACK64
[    0.125283] evm: security.SMACK64EXEC
[    0.125290] evm: security.SMACK64TRANSMUTE
[    0.125299] evm: security.SMACK64MMAP
[    0.125306] evm: security.ima
[    0.125314] evm: security.capability
[    0.125453] PM: Registering ACPI NVS region [mem 0x0003f000-0x0003ffff] (4096 bytes)
[    0.125469] PM: Registering ACPI NVS region [mem 0x7a67d000-0x7b54bfff] (15527936 bytes)
[    0.126256] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.126285] futex hash table entries: 512 (order: 3, 32768 bytes)
[    0.126400] pinctrl core: initialized pinctrl subsystem
[    0.126701] RTC time: 12:56:11, date: 07/29/17
[    0.127000] NET: Registered protocol family 16
[    0.137071] cpuidle: using governor ladder
[    0.149085] cpuidle: using governor menu
[    0.149098] PCCT header not found.
[    0.149165] Simple Boot Flag at 0x47 set to 0x1
[    0.149199] ACPI: bus type PCI registered
[    0.149210] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.149373] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.149392] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.149439] PCI: Using configuration type 1 for base access
[    0.149461] dmi type 0xB1 record - unknown flag
[    0.161487] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.162217] ACPI: Added _OSI(Module Device)
[    0.162231] ACPI: Added _OSI(Processor Device)
[    0.162239] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.162247] ACPI: Added _OSI(Processor Aggregator Device)
[    0.171976] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.189688] ACPI: Dynamic OEM Table Load:
[    0.189713] ACPI: SSDT 0xFFFF934DF1A29800 00056E (v01 PmRef  Cpu0Ist  00003000 INTL 20061109)
[    0.190262] ACPI: Dynamic OEM Table Load:
[    0.190281] ACPI: SSDT 0xFFFF934DF1AC5000 0003A5 (v01 PmRef  Cpu0Cst  00003001 INTL 20061109)
[    0.191306] ACPI: Dynamic OEM Table Load:
[    0.191327] ACPI: SSDT 0xFFFF934DF1AED600 00015F (v01 PmRef  ApIst    00003000 INTL 20061109)
[    0.191796] ACPI: Dynamic OEM Table Load:
[    0.191814] ACPI: SSDT 0xFFFF934DF1ADF0C0 00008D (v01 PmRef  ApCst    00003000 INTL 20061109)
[    0.193282] ACPI: Interpreter enabled
[    0.193348] ACPI: (supports S0 S3 S4 S5)
[    0.193357] ACPI: Using IOAPIC for interrupt routing
[    0.193450] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.196802] ACPI: Power Resource [ID3C] (off)
[    0.197829] ACPI: Power Resource [USBC] (on)
[    0.230786] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.230813] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.231392] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.232361] PCI host bridge to bus 0000:00
[    0.232376] pci_bus 0000:00: root bus resource [io  0x0070-0x0077]
[    0.232388] pci_bus 0000:00: root bus resource [io  0x0000-0x006f window]
[    0.232398] pci_bus 0000:00: root bus resource [io  0x0078-0x0cf7 window]
[    0.232409] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.232419] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.232433] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
[    0.232448] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000fffff window]
[    0.232462] pci_bus 0000:00: root bus resource [mem 0x80000000-0xdfffffff window]
[    0.232477] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.232501] pci 0000:00:00.0: [8086:2280] type 00 class 0x060000
[    0.232807] pci 0000:00:02.0: [8086:22b1] type 00 class 0x030000
[    0.232833] pci 0000:00:02.0: reg 0x10: [mem 0x90000000-0x90ffffff 64bit]
[    0.232847] pci 0000:00:02.0: reg 0x18: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.232858] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.233160] pci 0000:00:0b.0: [8086:22dc] type 00 class 0x118000
[    0.233184] pci 0000:00:0b.0: reg 0x10: [mem 0x9131e000-0x9131efff 64bit]
[    0.233540] pci 0000:00:14.0: [8086:22b5] type 00 class 0x0c0330
[    0.233570] pci 0000:00:14.0: reg 0x10: [mem 0x91300000-0x9130ffff 64bit]
[    0.233677] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.233855] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.233978] pci 0000:00:1a.0: [8086:2298] type 00 class 0x108000
[    0.234003] pci 0000:00:1a.0: reg 0x10: [mem 0x91100000-0x911fffff]
[    0.234016] pci 0000:00:1a.0: reg 0x14: [mem 0x91000000-0x910fffff]
[    0.234115] pci 0000:00:1a.0: PME# supported from D0 D3hot
[    0.234391] pci 0000:00:1b.0: [8086:2284] type 00 class 0x040300
[    0.234425] pci 0000:00:1b.0: reg 0x10: [mem 0x91310000-0x91313fff 64bit]
[    0.234542] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.234696] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.234975] pci 0000:00:1c.0: [8086:22c8] type 01 class 0x060400
[    0.236504] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.236895] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.237019] pci 0000:00:1f.0: [8086:229c] type 00 class 0x060100
[    0.237384] pci 0000:00:1f.3: [8086:2292] type 00 class 0x0c0500
[    0.237458] pci 0000:00:1f.3: reg 0x10: [mem 0x91318000-0x9131801f]
[    0.237578] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.238714] pci 0000:01:00.0: [8086:08b3] type 00 class 0x028000
[    0.238887] pci 0000:01:00.0: reg 0x10: [mem 0x91200000-0x91201fff 64bit]
[    0.239200] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.239373] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.249562] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.249661] pci 0000:00:1c.0:   bridge window [mem 0x91200000-0x912fffff]
[    0.358217] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.358396] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.358567] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.358734] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.358908] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.359076] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.359240] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.359410] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.370745] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.371615] SCSI subsystem initialized
[    0.371767] libata version 3.00 loaded.
[    0.371856] pci 0000:00:02.0: vgaarb: setting as boot VGA device
[    0.371869] pci 0000:00:02.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.371889] pci 0000:00:02.0: vgaarb: bridge control possible
[    0.371897] vgaarb: loaded
[    0.371956] ACPI: bus type USB registered
[    0.372017] usbcore: registered new interface driver usbfs
[    0.372047] usbcore: registered new interface driver hub
[    0.372089] usbcore: registered new device driver usb
[    0.372318] Registered efivars operations
[    0.377077] PCI: Using ACPI for IRQ routing
[    0.388197] PCI: pci_cache_line_size set to 64 bytes
[    0.388372] e820: reserve RAM buffer [mem 0x0003f000-0x0003ffff]
[    0.388376] e820: reserve RAM buffer [mem 0x1f000000-0x1fffffff]
[    0.388378] e820: reserve RAM buffer [mem 0x7a5eb000-0x7bffffff]
[    0.388632] NetLabel: Initializing
[    0.388644] NetLabel:  domain hash size = 128
[    0.388653] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    0.388710] NetLabel:  unlabeled traffic allowed by default
[    0.388951] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.388967] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.391025] clocksource: Switched to clocksource hpet
[    0.412039] VFS: Disk quotas dquot_6.6.0
[    0.412098] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.412363] AppArmor: AppArmor Filesystem Enabled
[    0.412518] pnp: PnP ACPI init
[    0.412680] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.413215] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.413228] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.413239] system 00:01: [io  0x0500-0x05fe] has been reserved
[    0.413256] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.413363] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.413483] pnp 00:03: Plug and Play ACPI device, IDs DLL0725 PNP0f13 (active)
[    0.413604] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.413625] system 00:04: [mem 0xfe900000-0xfe902fff] has been reserved
[    0.413641] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.415089] system 00:05: [mem 0x9131c000-0x9131cfff] has been reserved
[    0.415105] system 00:05: [mem 0x9131b000-0x9131bfff] has been reserved
[    0.415116] system 00:05: [mem 0x91319000-0x91319fff] has been reserved
[    0.415133] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.415260] system 00:06: [mem 0xe0000000-0xefffffff] has been reserved
[    0.415273] system 00:06: [mem 0xfea00000-0xfeafffff] has been reserved
[    0.415286] system 00:06: [mem 0xfed01000-0xfed01fff] has been reserved
[    0.415296] system 00:06: [mem 0xfed03000-0xfed03fff] has been reserved
[    0.415307] system 00:06: [mem 0xfed06000-0xfed06fff] has been reserved
[    0.415318] system 00:06: [mem 0xfed08000-0xfed09fff] has been reserved
[    0.415330] system 00:06: [mem 0xfed80000-0xfedbffff] could not be reserved
[    0.415341] system 00:06: [mem 0xfed1c000-0xfed1cfff] has been reserved
[    0.415352] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.415366] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.423688] pnp: PnP ACPI: found 7 devices
[    0.434227] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.434407] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.434488] pci 0000:00:1c.0:   bridge window [mem 0x91200000-0x912fffff]
[    0.434634] pci_bus 0000:00: resource 4 [io  0x0070-0x0077]
[    0.434638] pci_bus 0000:00: resource 5 [io  0x0000-0x006f window]
[    0.434642] pci_bus 0000:00: resource 6 [io  0x0078-0x0cf7 window]
[    0.434646] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff window]
[    0.434649] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff window]
[    0.434652] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff window]
[    0.434655] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000fffff window]
[    0.434659] pci_bus 0000:00: resource 11 [mem 0x80000000-0xdfffffff window]
[    0.434664] pci_bus 0000:01: resource 1 [mem 0x91200000-0x912fffff]
[    0.434899] NET: Registered protocol family 2
[    0.435391] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.435498] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.435605] TCP: Hash tables configured (established 16384 bind 16384)
[    0.435689] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.435722] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.435832] NET: Registered protocol family 1
[    0.435892] pci 0000:00:02.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    0.437436] PCI: CLS 64 bytes, default 64
[    0.437582] Unpacking initramfs...
[    1.831979] Freeing initrd memory: 42580K
[    1.832141] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x171024fa93b, max_idle_ns: 440795253189 ns
[    1.832191] clocksource: Switched to clocksource tsc
[    1.832306] Scanning for low memory corruption every 60 seconds
[    1.833122] audit: initializing netlink subsys (disabled)
[    1.833233] audit: type=2000 audit(1501332972.793:1): initialized
[    1.833960] Initialise system trusted keyrings
[    1.834137] workingset: timestamp_bits=36 max_order=19 bucket_order=0
[    1.838623] zbud: loaded
[    1.839943] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    1.840548] fuse init (API version 7.26)
[    1.843773] Key type asymmetric registered
[    1.843787] Asymmetric key parser 'x509' registered
[    1.843905] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 248)
[    1.843978] io scheduler noop registered
[    1.843988] io scheduler deadline registered
[    1.844017] io scheduler cfq registered (default)
[    1.846140] pcieport 0000:00:1c.0: Signaling PME with IRQ 170
[    1.846321] efifb: probing for efifb
[    1.846359] efifb: framebuffer at 0x80000000, using 4160k, total 4160k
[    1.846369] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    1.846377] efifb: scrolling: redraw
[    1.846386] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.854819] Console: switching to colour frame buffer device 170x48
[    1.863001] fb0: EFI VGA frame buffer device
[    1.863102] intel_idle: MWAIT substates: 0x33000020
[    1.863105] intel_idle: v0.4.1 model 0x4C
[    1.863334] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.863646] ACPI: AC Adapter [AC] (off-line)
[    1.866281] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.866394] ACPI: Lid Switch [LID0]
[    1.866547] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.866657] ACPI: Power Button [PWRB]
[    1.866804] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    1.866914] ACPI: Sleep Button [SLPB]
[    1.867104] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.867202] ACPI: Power Button [PWRF]
[    1.904183] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[    1.904552] thermal LNXTHERM:00: registered as thermal_zone0
[    1.904627] ACPI: Thermal Zone [THM] (32 C)
[    1.905686] GHES: HEST is not enabled!
[    1.906002] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.928247] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.952428] ACPI: Battery Slot [BAT0] (battery present)
[    1.952839] Linux agpgart interface v0.103
[    1.962018] loop: module loaded
[    1.962626] libphy: Fixed MDIO Bus: probed
[    1.962683] tun: Universal TUN/TAP device driver, 1.6
[    1.962750] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.962911] PPP generic driver version 2.4.2
[    1.965947] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.968892] ehci-pci: EHCI PCI platform driver
[    1.971785] ehci-platform: EHCI generic platform driver
[    1.974657] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.977519] ohci-pci: OHCI PCI platform driver
[    1.980389] ohci-platform: OHCI generic platform driver
[    1.983241] uhci_hcd: USB Universal Host Controller Interface driver
[    1.986477] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.989320] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    1.993344] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x01509810
[    1.996224] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.996438] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.999340] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.002237] usb usb1: Product: xHCI Host Controller
[    2.005109] usb usb1: Manufacturer: Linux 4.10.0-28-generic xhci-hcd
[    2.007978] usb usb1: SerialNumber: 0000:00:14.0
[    2.011169] hub 1-0:1.0: USB hub found
[    2.014054] hub 1-0:1.0: 7 ports detected
[    2.019912] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.022781] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    2.025883] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    2.028796] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.031700] usb usb2: Product: xHCI Host Controller
[    2.034583] usb usb2: Manufacturer: Linux 4.10.0-28-generic xhci-hcd
[    2.037494] usb usb2: SerialNumber: 0000:00:14.0
[    2.040661] hub 2-0:1.0: USB hub found
[    2.043543] hub 2-0:1.0: 6 ports detected
[    2.049179] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.056880] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.059753] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.062889] mousedev: PS/2 mouse device common for all mice
[    2.066138] rtc_cmos 00:00: RTC can wake from S4
[    2.069129] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
[    2.071891] rtc_cmos 00:00: alarms up to one day, y3k, 242 bytes nvram, hpet irqs
[    2.074619] i2c /dev entries driver
[    2.077411] device-mapper: uevent: version 1.0.3
[    2.080196] device-mapper: ioctl: 4.35.0-ioctl (2016-06-23) initialised: dm-devel@redhat.com
[    2.082779] intel_pstate: Intel P-state driver initializing
[    2.085684] ledtrig-cpu: registered to indicate activity on CPUs
[    2.087663] EFI Variables Facility v0.08 2004-May-17
[    2.095091] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.099245] NET: Registered protocol family 10
[    2.114964] Segment Routing with IPv6
[    2.117156] NET: Registered protocol family 17
[    2.119113] Key type dns_resolver registered
[    2.122365] microcode: sig=0x406c3, pf=0x1, revision=0x35e
[    2.124426] microcode: Microcode Update Driver: v2.2.
[    2.124679] registered taskstats version 1
[    2.128693] Loading compiled-in X.509 certificates
[    2.139946] Loaded X.509 cert 'Build time autogenerated kernel key: e9026736a679ce48fa6d373f1c17a210f04dee61'
[    2.141995] zswap: loaded using pool lzo/zbud
[    2.169902] Key type big_key registered
[    2.172058] Key type trusted registered
[    2.179760] Key type encrypted registered
[    2.181890] AppArmor: AppArmor sha1 policy hashing enabled
[    2.183836] ima: No TPM chip found, activating TPM-bypass! (rc=-19)
[    2.185823] evm: HMAC attrs: 0x1
[    2.188342]   Magic number: 9:349:937
[    2.190276] misc lightnvm: hash matches
[    2.192212] platform PNP0103:00: hash matches
[    2.194116] acpi PNP0103:00: hash matches
[    2.196232] rtc_cmos 00:00: setting system clock to 2017-07-29 12:56:13 UTC (1501332973)
[    2.198622] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.200567] EDD information not available.
[    2.202601] PM: Hibernation image not present or could not be loaded.
[    2.207043] Freeing unused kernel memory: 2232K
[    2.208979] Write protecting the kernel read-only data: 14336k
[    2.212250] Freeing unused kernel memory: 1140K
[    2.215917] Freeing unused kernel memory: 280K
[    2.234878] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    2.275205] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.276331] random: udevadm: uninitialized urandom read (16 bytes read)
[    2.276414] random: udevadm: uninitialized urandom read (16 bytes read)
[    2.279898] random: udevadm: uninitialized urandom read (16 bytes read)
[    2.280063] random: udevadm: uninitialized urandom read (16 bytes read)
[    2.280103] random: udevadm: uninitialized urandom read (16 bytes read)
[    2.280281] random: udevadm: uninitialized urandom read (16 bytes read)
[    2.281083] random: udevadm: uninitialized urandom read (16 bytes read)
[    2.281223] random: udevadm: uninitialized urandom read (16 bytes read)
[    2.281367] random: udevadm: uninitialized urandom read (16 bytes read)
[    2.355048] usb 1-3: new full-speed USB device number 2 using xhci_hcd
[    2.369904] FUJITSU Extended Socket Network Device Driver - version 1.2 - Copyright (c) 2015 FUJITSU LIMITED
[    2.378161] sdhci: Secure Digital Host Controller Interface driver
[    2.379953] sdhci: Copyright(c) Pierre Ossman
[    2.385217] hidraw: raw HID events driver (C) Jiri Kosina
[    2.401496] wmi: Mapper loaded
[    2.405846] mmc0: SDHCI controller on ACPI [80860F14:00] using ADMA
[    2.415281] [drm] Initialized
[    2.508738] usb 1-3: New USB device found, idVendor=8087, idProduct=07dc
[    2.512632] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.583827] mmc0: new HS200 MMC card at address 0001
[    2.591295] mmcblk0: mmc0:0001 DF4032 29.1 GiB 
[    2.593845] mmcblk0boot0: mmc0:0001 DF4032 partition 1 4.00 MiB
[    2.596557] mmcblk0boot1: mmc0:0001 DF4032 partition 2 4.00 MiB
[    2.598875] mmcblk0rpmb: mmc0:0001 DF4032 partition 3 4.00 MiB
[    2.606575]  mmcblk0: p1 p2
[    2.635036] usb 1-5: new high-speed USB device number 3 using xhci_hcd
[    2.639673] random: fast init done
[    2.789765] usb 1-5: New USB device found, idVendor=1bcf, idProduct=2c00
[    2.791772] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.793462] usb 1-5: Product: Integrated Webcam
[    2.795142] usb 1-5: Manufacturer: SY20160217210842
[    2.922431] EXT4-fs (mmcblk0p2): mounted filesystem with ordered data mode. Opts: (null)
[    3.146871] psmouse serio1: synaptics: queried max coordinates: x [..5676], y [..4768]
[    3.179120] psmouse serio1: synaptics: queried min coordinates: x [1266..], y [1082..]
[    3.237503] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.2, id: 0x1e2a1, caps: 0xf00123/0x840300/0x12e800/0x0, board id: 3207, fw id: 2085213
[    3.245447] ip_tables: (C) 2000-2006 Netfilter Core Team
[    3.270626] systemd[1]: systemd 232 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD +IDN)
[    3.275341] systemd[1]: Detected architecture x86-64.
[    3.282585] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    3.288724] systemd[1]: Set hostname to <bali-blue>.
[    3.473327] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    3.478600] systemd[1]: Listening on Journal Socket.
[    3.483553] systemd[1]: Listening on fsck to fsckd communication Socket.
[    3.488759] systemd[1]: Created slice User and Session Slice.
[    3.493761] systemd[1]: Listening on udev Kernel Socket.
[    3.498726] systemd[1]: Listening on Syslog Socket.
[    3.503648] systemd[1]: Reached target Remote File Systems.
[    3.622538] lp: driver loaded but no devices found
[    3.633371] ppdev: user-space parallel port driver
[    3.822440] EXT4-fs (mmcblk0p2): re-mounted. Opts: errors=remount-ro
[    3.889973] systemd-journald[223]: Received request to flush runtime journal from PID 1
[    4.084347] Adding 1392256k swap on /swapfile.  Priority:-1 extents:5 across:1425024k SSFS
[    4.246352] input: DELL Wireless hotkeys as /devices/virtual/input/input7
[    4.459118] proc_thermal 0000:00:0b.0: enabling device (0000 -> 0002)
[    4.461759] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[    4.461861] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[    4.473303] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.579962] media: Linux media interface: v0.10
[    4.600979] Intel(R) Wireless WiFi driver for Linux
[    4.600982] Copyright(c) 2003- 2015 Intel Corporation
[    4.601102] iwlwifi 0000:01:00.0: enabling device (0000 -> 0002)
[    4.621803] Bluetooth: Core ver 2.22
[    4.621841] NET: Registered protocol family 31
[    4.621843] Bluetooth: HCI device and connection manager initialized
[    4.621850] Bluetooth: HCI socket layer initialized
[    4.621855] Bluetooth: L2CAP socket layer initialized
[    4.621866] Bluetooth: SCO socket layer initialized
[    4.624719] Linux video capture interface: v2.00
[    4.628974] iwlwifi 0000:01:00.0: loaded firmware version 17.459231.0 op_mode iwlmvm
[    4.698800] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    4.700980] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    4.701369] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    4.722040] uvcvideo: Found UVC 1.00 device Integrated Webcam (1bcf:2c00)
[    4.726962] usbcore: registered new interface driver btusb
[    4.730940] uvcvideo 1-5:1.0: Entity type for entity Extension 4 was not initialized!
[    4.730946] uvcvideo 1-5:1.0: Entity type for entity Extension 3 was not initialized!
[    4.730949] uvcvideo 1-5:1.0: Entity type for entity Processing 2 was not initialized!
[    4.730952] uvcvideo 1-5:1.0: Entity type for entity Camera 1 was not initialized!
[    4.732814] input: Integrated Webcam as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input8
[    4.732951] usbcore: registered new interface driver uvcvideo
[    4.732952] USB Video Class driver (1.1.1)
[    4.742580] Bluetooth: hci0: read Intel version: 3707100100012d0d00
[    4.751487] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.1.2d.d.bseq
[    4.808397] SSE version of gcm_enc/dec engaged.
[    4.819750] snd_hda_intel 0000:00:1b.0: failed to add i915 component master (-19)
[    4.874521] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.916448] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC3234: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    4.916453] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.916456] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    4.916458] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    4.916459] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    4.916463] snd_hda_codec_realtek hdaudioC0D0:      Headset Mic=0x19
[    4.916465] snd_hda_codec_realtek hdaudioC0D0:      Headphone Mic=0x1a
[    4.916467] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    4.934579] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    4.951598] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    5.003778] snd_hda_codec_hdmi hdaudioC0D2: No i915 binding for Intel HDMI/DP codec
[    5.004290] snd_hda_codec_hdmi hdaudioC0D2: No i915 binding for Intel HDMI/DP codec
[    5.018215] input: HDA Intel PCH Headphone Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    5.018346] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    5.095740] dell_laptop: Keyboard brightness level control not supported
[    5.236738] intel_rapl: Found RAPL domain package
[    5.236741] intel_rapl: Found RAPL domain core
[    5.387788] audit: type=1400 audit(1501332976.688:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=550 comm="apparmor_parser"
[    5.387793] audit: type=1400 audit(1501332976.688:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=550 comm="apparmor_parser"
[    5.392626] audit: type=1400 audit(1501332976.692:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=551 comm="apparmor_parser"
[    5.392630] audit: type=1400 audit(1501332976.692:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=551 comm="apparmor_parser"
[    5.392632] audit: type=1400 audit(1501332976.692:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=551 comm="apparmor_parser"
[    5.392633] audit: type=1400 audit(1501332976.692:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=551 comm="apparmor_parser"
[    5.413575] audit: type=1400 audit(1501332976.712:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=557 comm="apparmor_parser"
[    5.413579] audit: type=1400 audit(1501332976.712:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=557 comm="apparmor_parser"
[    5.418838] audit: type=1400 audit(1501332976.716:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=560 comm="apparmor_parser"
[    5.462322] dell_wmi: Detected Dell WMI interface version 1
[    5.462467] input: Dell WMI hotkeys as /devices/virtual/input/input11
[    5.526166] hid-rmi 0018:06CB:7D47.0001: Scanning PDT...
[    5.528525] hid-rmi 0018:06CB:7D47.0001: Found F34 on page 0x00
[    5.533043] hid-rmi 0018:06CB:7D47.0001: Found F01 on page 0x00
[    5.535705] hid-rmi 0018:06CB:7D47.0001: Found F11 on page 0x00
[    5.541442] hid-rmi 0018:06CB:7D47.0001: Found F30 on page 0x01
[    5.543770] hid-rmi 0018:06CB:7D47.0001: Found F54 on page 0x01
[    5.549116] hid-rmi 0018:06CB:7D47.0001: rmi_scan_pdt: Done with PDT scan.
[    5.613533] hid-rmi 0018:06CB:7D47.0001: rmi_populate_f11: size in mm: 97 x 52
[    5.638899] hid-rmi 0018:06CB:7D47.0001: firmware id: 2085213
[    5.639085] input: DLL0725:01 06CB:7D47 as /devices/pci0000:00/808622C1:00/i2c-0/i2c-DLL0725:01/0018:06CB:7D47.0001/input/input12
[    5.639885] hid-rmi 0018:06CB:7D47.0001: input,hidraw0: I2C HID v1.00 Mouse [DLL0725:01 06CB:7D47] on i2c-DLL0725:01
[    5.900922] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    6.630423] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.630427] Bluetooth: BNEP filters: protocol multicast
[    6.630438] Bluetooth: BNEP socket layer initialized
[    7.140116] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    7.142363] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.142728] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.264928] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.265345] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.282081] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    7.294275] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.294618] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.417196] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.417529] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.434363] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    7.583069] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   23.861696] random: crng init done
[   24.098297] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   25.779194] dell_laptop: Keyboard brightness level control not supported
[   27.388163] wlp1s0: authenticate with c0:56:27:c4:33:6d
[   27.398020] wlp1s0: send auth to c0:56:27:c4:33:6d (try 1/3)
[   27.401736] wlp1s0: authenticated
[   27.407025] wlp1s0: associate with c0:56:27:c4:33:6d (try 1/3)
[   27.408927] wlp1s0: RX AssocResp from c0:56:27:c4:33:6d (capab=0x911 status=0 aid=2)
[   27.410467] wlp1s0: associated
[   27.410558] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[   27.472113] wlp1s0: Limiting TX power to 20 (20 - 0) dBm as advertised by c0:56:27:c4:33:6d
chris@bali-blue:~$ 

```

---

### Post by BenginM on 2017-07-29
Hiya chrisk0 , you're still booting with nomodeset ..
0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-28-generic.efi.signed root=UUID=e34fc988-8001-49b4-986a-03d795ad2156 ro nomodeset
[    0.000000] KERNEL supported cpus:

boot without it , and i don't think the machine having issue booting with the Intel Integrated Graphics .. or is it!

---

### Post by chrisk0 on 2017-07-29
Hey!

I just tried removing nomodeset from the grub options and booting like that--no go. I see a quick rush of text after a few seconds, and then a black screen, no way to get it to respond that I could see, other than forcing a power-down and booting again.

---

### Post by yoshii on 2017-07-29
You might need to try some of the kernel options related to BIOS incompatibility with Linux.  
I forget what they are called, but on some systems, the hardware expects signals from Microsoft Windows, and without it, some things don't work.  
However, Linux has some tricks that can be used to tell the system to "look like" Microsoft Windows in the firmware then it gets the functions back again.  
Sorry I can't be more specific.  I don't have my Linux system in front of me at the moment.

---

### Post by BenginM on 2017-07-29
> **chrisk0 said:**
> Hey!

I just tried removing nomodeset from the grub options and booting like that--no go. I see a quick rush of text after a few seconds, and then a black screen, no way to get it to respond that I could see, other than forcing a power-down and booting again.

Ok,well glad you've test it , because now that tell us the machine unable to boot with the Intel driver for some reason , and the only way to reach the desktop is setting nomodeset which falls back to the Vesa driver , and in the process disables the functionality of the function hotkeys combination for brightness .. SO we need to get the Intel Graphics uses the Intel driver .. that's should be the proper fix, at lest to my knowledge .. hopefully others will chime in ..!

whilst the machine boots with nomodeset , run $ [B]lspci -knn , that should tell you the kernel driver in use for the Intel graphic .

or better yet , run $ inxi -G , if inxi is not present ... sudo apt install inxi

I suppose sudo lshw -C video , should detail the exact Intel graphic model ..

looking at the dell laptop specs , it's CPU is an Intel Pentium N3540 .. i wonder if the system boots to the desktop fine with the Intel integrated graphic[/B][B] prior to 17.,04 Zapus , 16.04 or the new development release 17.10 .. do you care to test a livecd/usb of 16.04 and 17.10 ..!
[/B]
Usually intel's GPUs are well supported with no issues ..

Also, you've installed Xubuntu 64-bit, Right!

---

### Post by BenginM on 2017-07-29
Looking through the output of dmesg above among few others bits , i noticed this :

dell_laptop: Keyboard brightness level control not supported

am not sure if the cause is nomodeset , or if it's an upstream bug ..

Edit: just came across this :

[https://askubuntu.com/questions/803640/system-freezes-completely-with-intel-bay-trail](https://askubuntu.com/questions/803640/system-freezes-completely-with-intel-bay-trail)

---

### Post by chrisk0 on 2017-07-30
> **BenginM said:**
> 
whilst the machine boots with nomodeset , run $ [B]lspci -knn , that should tell you the kernel driver in use for the Intel graphic .

or better yet , run $ inxi -G , if inxi is not present ... sudo apt install inxi

I suppose sudo lshw -C video , should detail the exact Intel graphic model ..


Thank you! Looks like it's a "Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller"....
```

chris@bali-blue:~$ inxi -G
Graphics:  Card: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
           Display Server: X.Org 1.19.3 drivers: vesa (unloaded: modesetting,fbdev)
           Resolution: 1368x768@0.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 4.0, 128 bits)
           GLX Version: 3.0 Mesa 17.0.3
chris@bali-blue:~$ sudo lshw -C video
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:90000000-90ffffff memory:80000000-8fffffff ioport:f000(size=64) memory:c0000-dffff
chris@bali-blue:~$ lspci -knn
00:00.0 Host bridge [0600]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register [8086:2280] (rev 21)
	Subsystem: Dell Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register [1028:0725]
	Kernel driver in use: iosf_mbi_pci
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller [8086:22b1] (rev 21)
	DeviceName:  Onboard IGD
	Subsystem: Dell Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller [1028:0725]
	Kernel modules: i915
00:0b.0 Signal processing controller [1180]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller [8086:22dc] (rev 21)
	Subsystem: Dell Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller [1028:0725]
	Kernel driver in use: proc_thermal
	Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller [8086:22b5] (rev 21)
	Subsystem: Dell Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller [1028:0725]
	Kernel driver in use: xhci_hcd
00:1a.0 Encryption controller [1080]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine [8086:2298] (rev 21)
	Subsystem: Dell Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine [1028:0725]
	Kernel driver in use: mei_txe
	Kernel modules: mei_txe
00:1b.0 Audio device [0403]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller [8086:2284] (rev 21)
	Subsystem: Dell Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller [1028:0725]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 [8086:22c8] (rev 21)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU [8086:229c] (rev 21)
	Subsystem: Dell Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU [1028:0725]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.3 SMBus [0c05]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx SMBus Controller [8086:2292] (rev 21)
	Subsystem: Dell Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx SMBus Controller [1028:0725]
	Kernel modules: i2c_i801
01:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8470]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

```

Further updates to come!

---

### Post by BenginM on 2017-07-30
```


Kernel driver in use: iosf_mbi_pci
00:02.0 VGA  compatible controller [0300]: Intel Corporation Atom/Celeron/Pentium  Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller  [8086:22b1] (rev 21)
    DeviceName:  Onboard IGD
    Subsystem: Dell Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller [1028:0725]
    Kernel modules: i915

```


VendorId: 8086
Chipset ID: 22b1

Then if we follow [this link]("https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units")  you will find out your chipset in the Eighth generation table which is  HD Graphics 400  ... to be exact! which is supposedly supported under  GNU/Linux and it looks like it has been supported since kernel 3.9 

when you run: sudo lshw -C cpu

you should see the exact CPU ..

##

```


[SIZE=2]**Loading**

The Intel kernel module should load fine automatically on system boot. 
If it does not happen, then: 


[LIST]
[*] Make sure you do **not** have nomodeset or vga= as a [[COLOR=#0077bb]kernel parameter[/COLOR]]("https://wiki.archlinux.org/index.php/Kernel_parameter"), since Intel requires kernel mode-setting. 
[*]  Also, check that you have not disabled Intel by using any modprobe  blacklisting within /etc/modprobe.d/ or /usr/lib/modprobe.d/. 
[*] 
[/LIST]
[/SIZE]
```

source: [https://wiki.archlinux.org/index.php/intel_graphics](https://wiki.archlinux.org/index.php/intel_graphics)

I want you to try something , boot without nomodeset or any other parameter , when the screen goes black .. switch to a virtual console by pressing Ctrl+Alt+F3 , you have consoles from F2 to F6 , F7 is desktop session with X running , now login with your username and passd , run the following commands :

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install --reinstall xserver-xorg-video-intel

after that , cd to /etc/modprobe.d $ cd /etc/modprobe.d , and cat the files in there to make sure the intel i915 kernel driver is not blacklisted ,
for example, in my system..
sary@tru:/etc/modprobe.d$ ls -l
total 16
-rw-r--r-- 1 root root 154 Nov 30  2016 amd64-microcode-blacklist.conf
-rw-r--r-- 1 root root 127 Feb  7 18:27 dkms.conf
-rw-r--r-- 1 root root 154 Nov 10  2016 intel-microcode-blacklist.conf
-rw-r--r-- 1 root root 379 Jul 28  2016 mdadm.conf
sary@tru:/etc/modprobe.d$ cat intel-microcode-blacklist.conf
# The microcode module attempts to apply a microcode update when
# it autoloads.  This is not always safe, so we block it by default.
blacklist microcode
 
if you see a line with : blacklist i915 in one of these files ,remove that line, or place a # at the begining of the line.

now , maybe it's a good idea to add i915 to /etc/modules , as we don't know yet as to why it's not loaded therefore you get a black screen for some reason..

so , got back to the /etc directory cd .. , and open the file with nano : sudo nano /etc/modules , type i915 in a separate line there , save by pressing Ctrl+x, select Yes , then hit enter.

 Now reboot without nomodeset , sudo reboot

Do you still get stuck in a black screen..! if yes then we need to have a look at some logs..

---

### Post by BenginM on 2017-07-31
excuse me , this was a duplicated post!

---

### Post by chrisk0 on 2017-07-31
Okay... I'm not getting the console when I press control-alt-F3 at the black screen, just more black. I do get the console login by pressing control-alt-F3 at the X login after booting with nomodeset.

---

### Post by BenginM on 2017-08-06
Intels GPU needs KMS enabled , and bootin' with nomodeset disable is it , and the brightness control.

---

### Post by chrisk0 on 2017-08-07
Thank you.

I have reverted this device to Windows 10 home.

---

### Post by DaBzzz on 2017-08-12
Well, that's one way to deal with it :(

Kernel 4.10.0-28 also kinda-sorta broke the brightness control on my Lenovo Thinkpad T400 with integrated sh!tty Intel graphics,

```
inxi -G
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller
           Display Server: X.Org 1.19.3 driver: intel Resolution: 1440x900@60.00hz
           GLX Renderer: Mesa DRI Mobile Intel GM45 Express GLX Version: 2.1 Mesa 17.0.7
```


```
sudo lshw -C video
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:32 memory:f4400000-f47fffff memory:d0000000-dfffffff ioport:1800(size=8) memory:c0000-dffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f4200000-f42fffff
```
Brightness adjust (+) now has some overly fancy ramping effect instead of the usual hard stepping between the 16 brightness modes. However, turning the brightness down causes flicker and in a maximum of 4 steps completely turns off the backlight. Ramping back up doesn't work, one needs to close the lid and re-open it. Sometimes that also happens with the lock screen, where the screen is set to slowly auto-dim to the lowest value. It's not locked, but you can't really see much as the backlight is off.

So...4.10.0-28 is bogus and needs to be avoided on older Intel machines apparently.

---

