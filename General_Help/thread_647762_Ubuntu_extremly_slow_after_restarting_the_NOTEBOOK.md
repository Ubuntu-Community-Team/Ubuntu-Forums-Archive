---
title: "Ubuntu extremly slow after restarting the NOTEBOOK"
date: 2007-12-22
forum: General Help
---

### Post by xx6xx on 2007-12-22
[I][I]Hi all, 
this is my problem:
I have been using Ubuntu 7.10 for few weeks on my notebook Asus A8JP ( Core2Duo 2ghz, ATI X1700) and suddenly, after restarting it got extremly slow... full of lags ... no fluency at all :( Visuall Effects got disabled, can´t schwitch them on ... There are small small display errors ( "sound icon" on top panel is unrecognizable for example ... )

I have no idea how did it happen, I haven´t done any changes, no packages installed lately.   Perhapse I did hibernate my notebook before it got slow, but I am not sure  [/I][/I]

Any ideas how to get my previous, excellent looking and working OS... ?? :confused:

THX for help

---

### Post by cmnorton on 2007-12-22
I'd get stuff out of your logs and post them. /var/log/syslog and /var/log/messages, and perhaps the output of dmesg. Is this notebook still sluggish after a cold power up?

---

### Post by xx6xx on 2007-12-26
> **cmnorton said:**
> Is this notebook still sluggish after a cold power up?
Yeah, it's one BIG LAAAAAAG while using ubuntu ... wit some small graphic errors...


Ok, here are my logs 

[SIZE="5"]**_ /var/log/syslog_**[/SIZE]
```
Dec 26 18:38:33 xx6xx-laptop syslogd 1.4.1#21ubuntu3: restart.
Dec 26 18:38:33 xx6xx-laptop anacron[6108]: Job `cron.daily' terminated
Dec 26 18:38:33 xx6xx-laptop anacron[6108]: Normal exit (1 job run)
```


 and**_[SIZE="5"] /var/log/messages[/SIZE]_**

```
Dec 23 17:51:39 xx6xx-laptop syslogd 1.4.1#21ubuntu3: restart.
Dec 23 18:21:20 xx6xx-laptop -- MARK --
Dec 23 18:41:20 xx6xx-laptop -- MARK --
Dec 23 18:45:45 xx6xx-laptop exiting on signal 15
Dec 24 00:47:05 xx6xx-laptop syslogd 1.4.1#21ubuntu3: restart.
Dec 24 00:47:05 xx6xx-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Dec 24 00:47:05 xx6xx-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Dec 24 00:47:05 xx6xx-laptop kernel: Symbols match kernel version 2.6.22.
Dec 24 00:47:05 xx6xx-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 000000003ffce000 - 0000000040000000 (ACPI NVS)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] 127MB HIGHMEM available.
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] 896MB LOWMEM available.
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] found SMP MP-table at 000ff780
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Zone PFN ranges:
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]   DMA             0 ->     4096
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]   HighMem    229376 ->   262080
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000]     0:        0 ->   262080
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] DMI 2.3 present.
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7C40 checksum 0
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: RSDP 000F7C40, 0014 (r0 ACPIAM)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: RSDT 3FFC0000, 003C (r1 A M I  OEMRSDT   8000610 MSFT       97)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: FACP 3FFC0200, 0084 (r2 A M I  OEMFACP   8000610 MSFT       97)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: DSDT 3FFC0460, 837F (r1  A8J00 A8J00005        5 INTL  2002026)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: FACS 3FFCE000, 0040
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: APIC 3FFC0390, 005C (r1 A M I  OEMAPIC   8000610 MSFT       97)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: MCFG 3FFC03F0, 003C (r1 A M I  OEMMCFG   8000610 MSFT       97)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: BOOT 3FFC0430, 0028 (r1 A M I  OEMBOOT   8000610 MSFT       97)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: OEMB 3FFCE040, 0046 (r1 A M I  AMI_OEM   8000610 MSFT       97)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: TCPA 3FFC87E0, 0032 (r1 A M I  TBLOEMID        1 MSFT       97)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 260033
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Kernel command line: root=UUID=b0303344-8d15-4766-a216-b901194d5dc0 ro quiet splash
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Initializing CPU#0
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 24 00:47:05 xx6xx-laptop kernel: [    0.000000] Detected 1995.102 MHz processor.
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.507313] Console: colour VGA+ 80x25
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.507568] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.507831] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.530958] Memory: 1027712k/1048320k available (2015k kernel code, 19964k reserved, 916k data, 364k init, 130816k highmem)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.530965] virtual kernel memory layout:
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.530966]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.530967]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.530968]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.530969]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.530970]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.530971]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.530972]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.530974] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.531002] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.610988] Calibrating delay using timer specific routine.. 3994.61 BogoMIPS (lpj=7989222)
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611007] Security Framework v1.0.0 initialized
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611012] SELinux:  Disabled at boot.
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611023] Mount-cache hash table entries: 512
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611127] monitor/mwait feature present.
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611128] using mwait in idle threads.
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611132] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611134] CPU: L2 cache: 4096K
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611136] CPU: Physical Processor ID: 0
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611137] CPU: Processor Core ID: 0
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611147] Compat vDSO mapped to ffffe000.
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.611157] Checking 'hlt' instruction... OK.
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.627064] SMP alternatives: switching to UP code
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.627410] Early unpacking initramfs... done
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.903495] ACPI: Core revision 20070126
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.903544] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.919168] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.919183] SMP alternatives: switching to SMP code
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.919252] Booting processor 1/1 eip 3000
Dec 24 00:47:05 xx6xx-laptop kernel: [   29.929646] Initializing CPU#1
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.006789] Calibrating delay using timer specific routine.. 3990.32 BogoMIPS (lpj=7980643)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.006799] monitor/mwait feature present.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.006802] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.006803] CPU: L2 cache: 4096K
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.006805] CPU: Physical Processor ID: 0
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.006806] CPU: Processor Core ID: 1
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.007473] CPU1: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.007494] Total of 2 processors activated (7984.93 BogoMIPS).
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.007687] ENABLING IO-APIC IRQs
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.007883] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.154812] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.174816] Brought up 2 CPUs
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.406356] migration_cost=52
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.406476] Booting paravirtualized kernel on bare hardware
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.406561] Time:  0:46:46  Date: 11/24/107
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.406578] NET: Registered protocol family 16
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.406656] EISA bus registered
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.406660] ACPI: bus type pci registered
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.406829] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.406830] PCI: Using configuration type 1
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.406832] Setting up standard PCI resources
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.411179] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.484087] ACPI: Interpreter enabled
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.484089] ACPI: (supports S0 S1 S3 S4 S5)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.484109] ACPI: Using IOAPIC for interrupt routing
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.492569] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.492694] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.493384] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.493388] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.494656] PCI: Transparent bridge - 0000:00:1e.0
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.506445] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.506616] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.506762] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.506912] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.507057] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.507202] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.507347] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.507491] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 7 10 11 12 14 15)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.507653] ACPI: Power Resource [GFAN] (off)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.507658] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.507666] pnp: PnP ACPI init
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.507674] ACPI: bus type pnp registered
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.510686] pnp: PnP ACPI: found 16 devices
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.510689] ACPI: ACPI bus type pnp unregistered
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.510692] PnPBIOS: Disabled by ACPI PNP
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.510754] PCI: Using ACPI for IRQ routing
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.510756] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530100] NET: Registered protocol family 8
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530102] NET: Registered protocol family 20
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530156] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530165] pnp: 00:09: ioport range 0xa00-0xa0f has been reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530169] pnp: 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530171] pnp: 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530174] pnp: 00:0a: iomem range 0xfed45000-0xfed89fff has been reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530180] pnp: 00:0b: iomem range 0xffb80000-0xffbfffff could not be reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530183] pnp: 00:0b: iomem range 0xfff80000-0xffffffff could not be reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530187] pnp: 00:0c: iomem range 0xffc00000-0xfff7ffff could not be reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530191] pnp: 00:0d: ioport range 0x400-0x41f has been reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530194] pnp: 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530196] pnp: 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530199] pnp: 00:0d: iomem range 0xfec10000-0xfec17fff has been reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530201] pnp: 00:0d: iomem range 0xfec18000-0xfec1ffff has been reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530205] pnp: 00:0e: iomem range 0xe0000000-0xe3ffffff has been reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530210] pnp: 00:0f: iomem range 0x0-0x9ffff could not be reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530212] pnp: 00:0f: iomem range 0xc0000-0xcffff could not be reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530214] pnp: 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530217] pnp: 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.530544] Time: tsc clocksource has been installed.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560490] PCI: Bridge: 0000:00:01.0
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560492]   IO window: 9000-bfff
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560496]   MEM window: fdf00000-fdffffff
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560499]   PREFETCH window: bdf00000-ddefffff
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560502] PCI: Bridge: 0000:00:1c.0
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560503]   IO window: disabled.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560509]   MEM window: fe000000-fe0fffff
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560513]   PREFETCH window: disabled.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560519] PCI: Bridge: 0000:00:1c.2
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560521]   IO window: c000-cfff
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560527]   MEM window: fe100000-fe1fffff
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560531]   PREFETCH window: disabled.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560537] PCI: Bridge: 0000:00:1c.3
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560538]   IO window: disabled.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560543]   MEM window: disabled.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560547]   PREFETCH window: disabled.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560553] PCI: Bridge: 0000:00:1e.0
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560554]   IO window: disabled.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560560]   MEM window: fea00000-feafffff
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560564]   PREFETCH window: disabled.
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560579] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560605] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560634] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 17
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560662] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.560691] NET: Registered protocol family 2
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.598614] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.598667] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.599259] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.599457] TCP: Hash tables configured (established 131072 bind 65536)
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.599459] TCP reno registered
Dec 24 00:47:05 xx6xx-laptop kernel: [   30.610692] checking if image is initramfs... it is
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.062288] Switched to high resolution mode on CPU 0
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.062356] Switched to high resolution mode on CPU 1
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.153426] Freeing initrd memory: 7057k freed
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.153551] Simple Boot Flag at 0x52 set to 0x1
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.153974] audit: initializing netlink socket (disabled)
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.153987] audit(1198457206.300:1): initialized
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.154064] highmem bounce pool size: 64 pages
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.155777] VFS: Disk quotas dquot_6.5.1
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.155815] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.155893] io scheduler noop registered
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.155895] io scheduler anticipatory registered
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.155897] io scheduler deadline registered
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.155907] io scheduler cfq registered (default)
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.156117] assign_interrupt_mode Found MSI capability
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.156249] assign_interrupt_mode Found MSI capability
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.156428] assign_interrupt_mode Found MSI capability
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.156608] assign_interrupt_mode Found MSI capability
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.156792] isapnp: Scanning for PnP cards...
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.510521] isapnp: No Plug & Play device found
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.528869] Real Time Clock Driver v1.12ac
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.528982] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.529161] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.530068] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.530183] input: Macintosh mouse button emulation as /class/input/input0
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.530258] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.533531] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.534669] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.534674] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.534677] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.534680] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.534682] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.534787] mice: PS/2 mouse device common for all mice
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.534896] EISA: Probing bus 0 at eisa.0
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.534934] EISA: Detected 0 cards.
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.535079] TCP cubic registered
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.535091] NET: Registered protocol family 1
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.535110] Using IPI No-Shortcut mode
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.535266]   Magic number: 3:74:760
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.535515] Freeing unused kernel memory: 364k freed
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.612506] input: AT Translated Set 2 keyboard as /class/input/input1
Dec 24 00:47:05 xx6xx-laptop kernel: [   31.797832] input: AT Translated Set 2 keyboard as /class/input/input2
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.703756] AppArmor: AppArmor initialized<5>audit(1198457207.800:2):  type=1505 info="AppArmor initialized" pid=1249
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.713979] fuse init (API version 7.8)
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.720625] Failure registering capabilities with primary security module.
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.960299] ACPI: Transitioning device [FN00] to D3
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.960302] ACPI: Transitioning device [FN00] to D3
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.960304] ACPI: Fan [FN00] (off)
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.973258] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  83, should be 6E [20070126]
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.973266] ACPI: SSDT 3FFC8820, 0CC3 (r1    AMI   CPU1PM        1 INTL 20051117)
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.997162] ACPI: CPU0 (power states: C1[C1] C2[C2])
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.997166] ACPI: Processor [CPU1] (supports 8 throttling states)
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.997214] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  3B, should be 01 [20070126]
Dec 24 00:47:05 xx6xx-laptop kernel: [   32.997219] ACPI: SSDT 3FFC94F0, 04A4 (r1    AMI   CPU2PM        1 INTL 20051117)
Dec 24 00:47:05 xx6xx-laptop kernel: [   33.013148] ACPI: CPU1 (power states: C1[C1] C2[C2])
Dec 24 00:47:05 xx6xx-laptop kernel: [   33.013152] ACPI: Processor [CPU2] (supports 8 throttling states)
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.324000] Marking TSC unstable due to: possible TSC halt in C2.
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.328000] Time: acpi_pm clocksource has been installed.
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.332000] ACPI: Thermal Zone [THRM] (47 C)
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.736000] usbcore: registered new interface driver usbfs
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.736000] usbcore: registered new interface driver hub
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.736000] usbcore: registered new device driver usb
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.740000] USB Universal Host Controller Interface driver v3.0
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.740000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.740000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.740000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.740000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ec00
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.740000] usb usb1: configuration #1 chosen from 1 choice
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.740000] hub 1-0:1.0: USB hub found
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.740000] hub 1-0:1.0: 2 ports detected
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.844000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.844000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.844000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.844000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e880
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.844000] usb usb2: configuration #1 chosen from 1 choice
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.844000] hub 2-0:1.0: USB hub found
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.844000] hub 2-0:1.0: 2 ports detected
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.880000] SCSI subsystem initialized
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.952000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 20 (level, low) -> IRQ 20
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.952000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.952000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.952000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e800
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.952000] usb usb3: configuration #1 chosen from 1 choice
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.952000] hub 3-0:1.0: USB hub found
Dec 24 00:47:05 xx6xx-laptop kernel: [    3.952000] hub 3-0:1.0: 2 ports detected
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.060000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 22 (level, low) -> IRQ 21
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.060000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.060000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.060000] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000e480
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.060000] usb usb4: configuration #1 chosen from 1 choice
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.060000] hub 4-0:1.0: USB hub found
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.060000] hub 4-0:1.0: 2 ports detected
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.168000] r8169 Gigabit Ethernet driver 2.2LK loaded
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.168000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 17
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.168000] eth0: RTL8168b/8111b at 0xf887c000, 00:18:f3:5f:34:1c, XID 38000000 IRQ 17
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.168000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.168000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.168000] scsi0 : ata_piix
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.168000] scsi1 : ata_piix
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.168000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.168000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.196000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.344000] ata1.00: ATA-7: FUJITSU MHV2120BH PL, 00000029, max UDMA/100
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.344000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.360000] ata1.00: configured for UDMA/100
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.444000] usb 2-1: configuration #1 chosen from 1 choice
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.688000] usb 2-2: new full speed USB device using uhci_hcd and address 3
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.692000] ata2.01: ATAPI: MATSHITADVD-RAM UJ-850S, 1.21, max UDMA/33
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.852000] usb 2-2: configuration #1 chosen from 1 choice
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.872000] ata2.01: configured for UDMA/33
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.872000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120B 0000 PQ: 0 ANSI: 5
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.872000] scsi 1:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.21 PQ: 0 ANSI: 5
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.876000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.876000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.876000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.876000] ehci_hcd 0000:00:1d.7: debug port 1
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.876000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.880000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.880000] usb usb5: configuration #1 chosen from 1 choice
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.880000] hub 5-0:1.0: USB hub found
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.880000] hub 5-0:1.0: 8 ports detected
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.884000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.884000] sd 0:0:0:0: [sda] Write Protect is off
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.884000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.884000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.884000] sd 0:0:0:0: [sda] Write Protect is off
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.884000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 24 00:47:05 xx6xx-laptop kernel: [    4.884000]  sda: sda1 sda2 < sda5 sda6<6>ACPI: PCI Interrupt 0000:06:00.0[B] -> GSI 17 (level, low) -> IRQ 22
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.000000]  sda7 sda8 >
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.012000] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.016000] usb 2-1: USB disconnect, address 2
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.040000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.048000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.048000] Uniform CD-ROM driver Revision: 3.20
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.052000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.052000] sr 1:0:1:0: Attached scsi generic sg1 type 5
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.144000] usb 2-2: USB disconnect, address 3
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.496000] Attempting manual resume
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.540000] kjournald starting.  Commit interval 5 seconds
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.540000] EXT3-fs: mounted filesystem with ordered data mode.
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.752000] usb 5-4: new high speed USB device using ehci_hcd and address 3
Dec 24 00:47:05 xx6xx-laptop kernel: [    5.892000] usb 5-4: configuration #1 chosen from 1 choice
Dec 24 00:47:05 xx6xx-laptop kernel: [    6.316000] usb 2-1: new full speed USB device using uhci_hcd and address 4
Dec 24 00:47:05 xx6xx-laptop kernel: [    6.560000] usb 2-1: configuration #1 chosen from 1 choice
Dec 24 00:47:05 xx6xx-laptop kernel: [    6.804000] usb 3-2: new low speed USB device using uhci_hcd and address 2
Dec 24 00:47:05 xx6xx-laptop kernel: [    6.976000] usb 3-2: configuration #1 chosen from 1 choice
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.296000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.300000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.448000] iTCO_vendor_support: vendor-support=0
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.448000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.472000] Linux agpgart interface v0.102 (c) Dave Jones
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.676000] NET: Registered protocol family 23
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.740000] Bluetooth: Core ver 2.11
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.740000] NET: Registered protocol family 31
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.740000] Bluetooth: HCI device and connection manager initialized
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.740000] Bluetooth: HCI socket layer initialized
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.784000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.784000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.888000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.888000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.888000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.904000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.904000] Bluetooth: HCI USB driver ver 2.9
Dec 24 00:47:05 xx6xx-laptop kernel: [   12.912000] usbcore: registered new interface driver hci_usb
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.048000] sdhci: Secure Digital Host Controller Interface driver
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.048000] sdhci: Copyright(c) Pierre Ossman
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.048000] sdhci: SDHCI controller found at 0000:06:00.1 [1180:0822] (rev 19)
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.048000] ACPI: PCI Interrupt 0000:06:00.1[B] -> GSI 17 (level, low) -> IRQ 22
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.048000] mmc0: SDHCI at 0xfeaff400 irq 22 DMA
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.060000] Linux video capture interface: v2.00
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.084000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04713/0x200000
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.116000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.120000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.124000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.124000] input: PC Speaker as /class/input/input4
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.124000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.124000] found SMC SuperIO Chip (devid=0x7a rev=01 base=0x002e): LPC47N227
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.124000] smsc_superio_flat(): fir: 0x6f8, sir: 0x2f8, dma: 15, irq: 3, mode: 0x0e
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.124000] smsc_ircc_present: can't get sir_base of 0x2f8
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.336000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 23
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.340000] usbcore: registered new interface driver gspca
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.340000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.340000] usbcore: registered new interface driver hiddev
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.356000] input: A4Tech PS/2+USB Mouse as /class/input/input5
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.356000] input: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1d.2-2
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.356000] usbcore: registered new interface driver usbhid
Dec 24 00:47:05 xx6xx-laptop kernel: [   13.356000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Dec 24 00:47:05 xx6xx-laptop kernel: [   14.392000] lp: driver loaded but no devices found
Dec 24 00:47:05 xx6xx-laptop kernel: [   14.472000] Adding 999912k swap on /dev/sda7.  Priority:-1 extents:1 across:999912k
Dec 24 00:47:05 xx6xx-laptop kernel: [   14.848000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 24 00:47:05 xx6xx-laptop kernel: [   15.428000] EXT3 FS on sda6, internal journal
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.300000] ACPI: Battery Slot [BAT0] (battery present)
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.456000] input: Power Button (FF) as /class/input/input6
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.456000] ACPI: Power Button (FF) [PWRF]
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.484000] input: Lid Switch as /class/input/input7
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.484000] ACPI: Lid Switch [LID]
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.484000] input: Power Button (CM) as /class/input/input8
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.484000] ACPI: Power Button (CM) [PWRB]
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.484000] input: Sleep Button (CM) as /class/input/input9
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.484000] ACPI: Sleep Button (CM) [SLPB]
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.548000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.556000] No dock devices found.
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.772000] Asus Laptop ACPI Extras version 0.30
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.772000]   unsupported model A8JP, trying default values
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.772000]   send /proc/acpi/dsdt to the developers
Dec 24 00:47:05 xx6xx-laptop kernel: [   18.796000] ACPI: AC Adapter [AC0] (on-line)
Dec 24 00:47:06 xx6xx-laptop kernel: [   20.240000] r8169: eth0: link down
Dec 24 00:47:06 xx6xx-laptop kernel: [   20.572000] NET: Registered protocol family 10
Dec 24 00:47:06 xx6xx-laptop kernel: [   20.572000] lo: Disabled Privacy Extensions
Dec 24 00:47:06 xx6xx-laptop kernel: [   20.572000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 24 00:47:06 xx6xx-laptop kernel: [   20.572000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 24 00:47:07 xx6xx-laptop kernel: [   20.988000] ppdev: user-space parallel port driver
Dec 24 00:47:07 xx6xx-laptop kernel: [   21.368000] audit(1198453627.108:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5229 profile="/usr/sbin/cupsd"
Dec 24 00:47:07 xx6xx-laptop kernel: [   21.416000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 24 00:47:07 xx6xx-laptop kernel: [   21.416000] apm: disabled - APM is not SMP safe.
Dec 24 00:47:07 xx6xx-laptop kernel: [   21.968000] Failure registering capabilities with primary security module.
Dec 24 00:47:07 xx6xx-laptop dhcdbd: Started up.
Dec 24 00:47:07 xx6xx-laptop kernel: [   22.160000] Bluetooth: L2CAP ver 2.8
Dec 24 00:47:07 xx6xx-laptop kernel: [   22.160000] Bluetooth: L2CAP socket layer initialized
Dec 24 00:47:08 xx6xx-laptop kernel: [   22.256000] Bluetooth: RFCOMM socket layer initialized
Dec 24 00:47:08 xx6xx-laptop kernel: [   22.256000] Bluetooth: RFCOMM TTY layer initialized
Dec 24 00:47:08 xx6xx-laptop kernel: [   22.256000] Bluetooth: RFCOMM ver 1.8
Dec 24 00:47:19 xx6xx-laptop kernel: [   34.072000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Dec 24 00:47:19 xx6xx-laptop kernel: [   34.076000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
Dec 24 00:47:19 xx6xx-laptop kernel: [   34.076000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
Dec 24 00:47:19 xx6xx-laptop kernel: [   34.120000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 24 00:47:22 xx6xx-laptop kernel: [   36.272000] mtrr: no more MTRRs available
Dec 24 00:47:22 xx6xx-laptop last message repeated 3 times
Dec 24 00:47:42 xx6xx-laptop exiting on signal 15
Dec 24 16:04:49 xx6xx-laptop syslogd 1.4.1#21ubuntu3: restart.
Dec 24 16:04:49 xx6xx-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Dec 24 16:04:49 xx6xx-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Dec 24 16:04:49 xx6xx-laptop kernel: Symbols match kernel version 2.6.22.
Dec 24 16:04:49 xx6xx-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 000000003ffce000 - 0000000040000000 (ACPI NVS)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] 127MB HIGHMEM available.
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] 896MB LOWMEM available.
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] found SMP MP-table at 000ff780
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Zone PFN ranges:
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]   DMA             0 ->     4096
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]   HighMem    229376 ->   262080
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000]     0:        0 ->   262080
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] DMI 2.3 present.
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7C40 checksum 0
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: RSDP 000F7C40, 0014 (r0 ACPIAM)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: RSDT 3FFC0000, 003C (r1 A M I  OEMRSDT   8000610 MSFT       97)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: FACP 3FFC0200, 0084 (r2 A M I  OEMFACP   8000610 MSFT       97)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: DSDT 3FFC0460, 837F (r1  A8J00 A8J00005        5 INTL  2002026)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: FACS 3FFCE000, 0040
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: APIC 3FFC0390, 005C (r1 A M I  OEMAPIC   8000610 MSFT       97)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: MCFG 3FFC03F0, 003C (r1 A M I  OEMMCFG   8000610 MSFT       97)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: BOOT 3FFC0430, 0028 (r1 A M I  OEMBOOT   8000610 MSFT       97)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: OEMB 3FFCE040, 0046 (r1 A M I  AMI_OEM   8000610 MSFT       97)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: TCPA 3FFC87E0, 0032 (r1 A M I  TBLOEMID        1 MSFT       97)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 260033
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Kernel command line: root=UUID=b0303344-8d15-4766-a216-b901194d5dc0 ro quiet splash
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Initializing CPU#0
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 24 16:04:49 xx6xx-laptop kernel: [    0.000000] Detected 1995.236 MHz processor.
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.280061] Console: colour VGA+ 80x25
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.280371] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.280798] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324719] Memory: 1027712k/1048320k available (2015k kernel code, 19964k reserved, 916k data, 364k init, 130816k highmem)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324733] virtual kernel memory layout:
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324735]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324737]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324739]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324741]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324743]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324745]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324747]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324752] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.324798] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.404789] Calibrating delay using timer specific routine.. 3995.55 BogoMIPS (lpj=7991115)
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.404821] Security Framework v1.0.0 initialized
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.404827] SELinux:  Disabled at boot.
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.404845] Mount-cache hash table entries: 512
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.405017] monitor/mwait feature present.
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.405020] using mwait in idle threads.
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.405026] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.405030] CPU: L2 cache: 4096K
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.405034] CPU: Physical Processor ID: 0
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.405037] CPU: Processor Core ID: 0
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.405054] Compat vDSO mapped to ffffe000.
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.405071] Checking 'hlt' instruction... OK.
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.420928] SMP alternatives: switching to UP code
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.421540] Early unpacking initramfs... done
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.967994] ACPI: Core revision 20070126
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.968078] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.987440] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.987463] SMP alternatives: switching to SMP code
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.987550] Booting processor 1/1 eip 3000
Dec 24 16:04:49 xx6xx-laptop kernel: [   30.998317] Initializing CPU#1
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.076454] Calibrating delay using timer specific routine.. 3990.31 BogoMIPS (lpj=7980633)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.076472] monitor/mwait feature present.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.076476] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.076479] CPU: L2 cache: 4096K
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.076482] CPU: Physical Processor ID: 0
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.076485] CPU: Processor Core ID: 1
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.077750] CPU1: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.077783] Total of 2 processors activated (7985.87 BogoMIPS).
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.077986] ENABLING IO-APIC IRQs
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.078210] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.224521] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.244537] Brought up 2 CPUs
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.604189] migration_cost=76
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.604379] Booting paravirtualized kernel on bare hardware
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.604482] Time: 16:04:25  Date: 11/24/107
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.604509] NET: Registered protocol family 16
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.604626] EISA bus registered
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.604632] ACPI: bus type pci registered
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.604846] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.604850] PCI: Using configuration type 1
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.604852] Setting up standard PCI resources
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.613251] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.690419] ACPI: Interpreter enabled
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.690424] ACPI: (supports S0 S1 S3 S4 S5)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.690462] ACPI: Using IOAPIC for interrupt routing
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.707253] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.707497] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.708452] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.708459] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.710083] PCI: Transparent bridge - 0000:00:1e.0
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.733620] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.733910] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.734196] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.734491] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.734775] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.735059] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.735344] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.735627] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 7 10 11 12 14 15)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.735947] ACPI: Power Resource [GFAN] (off)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.735957] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.735971] pnp: PnP ACPI init
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.735988] ACPI: bus type pnp registered
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.741857] pnp: PnP ACPI: found 16 devices
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.741861] ACPI: ACPI bus type pnp unregistered
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.741867] PnPBIOS: Disabled by ACPI PNP
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.741940] PCI: Using ACPI for IRQ routing
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.741945] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764820] NET: Registered protocol family 8
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764823] NET: Registered protocol family 20
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764909] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764925] pnp: 00:09: ioport range 0xa00-0xa0f has been reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764933] pnp: 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764938] pnp: 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764943] pnp: 00:0a: iomem range 0xfed45000-0xfed89fff has been reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764952] pnp: 00:0b: iomem range 0xffb80000-0xffbfffff could not be reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764957] pnp: 00:0b: iomem range 0xfff80000-0xffffffff could not be reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764966] pnp: 00:0c: iomem range 0xffc00000-0xfff7ffff could not be reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764974] pnp: 00:0d: ioport range 0x400-0x41f has been reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764979] pnp: 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764984] pnp: 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764989] pnp: 00:0d: iomem range 0xfec10000-0xfec17fff has been reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.764994] pnp: 00:0d: iomem range 0xfec18000-0xfec1ffff has been reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.765002] pnp: 00:0e: iomem range 0xe0000000-0xe3ffffff has been reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.765011] pnp: 00:0f: iomem range 0x0-0x9ffff could not be reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.765016] pnp: 00:0f: iomem range 0xc0000-0xcffff could not be reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.765021] pnp: 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.765026] pnp: 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.768137] Time: tsc clocksource has been installed.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795522] PCI: Bridge: 0000:00:01.0
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795526]   IO window: 9000-bfff
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795533]   MEM window: fdf00000-fdffffff
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795538]   PREFETCH window: bdf00000-ddefffff
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795544] PCI: Bridge: 0000:00:1c.0
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795546]   IO window: disabled.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795555]   MEM window: fe000000-fe0fffff
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795561]   PREFETCH window: disabled.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795569] PCI: Bridge: 0000:00:1c.2
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795573]   IO window: c000-cfff
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795582]   MEM window: fe100000-fe1fffff
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795588]   PREFETCH window: disabled.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795595] PCI: Bridge: 0000:00:1c.3
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795598]   IO window: disabled.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795605]   MEM window: disabled.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795611]   PREFETCH window: disabled.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795619] PCI: Bridge: 0000:00:1e.0
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795622]   IO window: disabled.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795630]   MEM window: fea00000-feafffff
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795636]   PREFETCH window: disabled.
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795659] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795697] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795737] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 17
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795777] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.795822] NET: Registered protocol family 2
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.832140] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.832209] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.833163] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.833500] TCP: Hash tables configured (established 131072 bind 65536)
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.833504] TCP reno registered
Dec 24 16:04:49 xx6xx-laptop kernel: [   31.844298] checking if image is initramfs...<6>Switched to high resolution mode on CPU 1
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.295882] Switched to high resolution mode on CPU 0
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.364027]  it is
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.921247] Freeing initrd memory: 7057k freed
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.921397] Simple Boot Flag at 0x52 set to 0x1
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.922119] audit: initializing netlink socket (disabled)
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.922142] audit(1198512266.248:1): initialized
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.922299] highmem bounce pool size: 64 pages
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.925365] VFS: Disk quotas dquot_6.5.1
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.925442] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.925573] io scheduler noop registered
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.925576] io scheduler anticipatory registered
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.925579] io scheduler deadline registered
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.925601] io scheduler cfq registered (default)
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.925911] assign_interrupt_mode Found MSI capability
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.926113] assign_interrupt_mode Found MSI capability
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.926377] assign_interrupt_mode Found MSI capability
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.926644] assign_interrupt_mode Found MSI capability
Dec 24 16:04:49 xx6xx-laptop kernel: [   32.926930] isapnp: Scanning for PnP cards...
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.280929] isapnp: No Plug & Play device found
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.314079] Real Time Clock Driver v1.12ac
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.314259] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.314499] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.316120] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.316434] input: Macintosh mouse button emulation as /class/input/input0
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.316566] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.320088] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.321261] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.321267] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.321272] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.321276] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.321280] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.321550] mice: PS/2 mouse device common for all mice
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.321837] EISA: Probing bus 0 at eisa.0
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.321887] EISA: Detected 0 cards.
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.321994] TCP cubic registered
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.322010] NET: Registered protocol family 1
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.322039] Using IPI No-Shortcut mode
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.322273]   Magic number: 3:52:86
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.322579] Freeing unused kernel memory: 364k freed
Dec 24 16:04:49 xx6xx-laptop kernel: [   33.411661] input: AT Translated Set 2 keyboard as /class/input/input1
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.654371] AppArmor: AppArmor initialized<5>audit(1198512267.748:2):  type=1505 info="AppArmor initialized" pid=1247
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.671444] fuse init (API version 7.8)
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.685204] Failure registering capabilities with primary security module.
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.816813] ACPI: Transitioning device [FN00] to D3
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.816818] ACPI: Transitioning device [FN00] to D3
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.816823] ACPI: Fan [FN00] (off)
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.838756] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  83, should be 6E [20070126]
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.838771] ACPI: SSDT 3FFC8820, 0CC3 (r1    AMI   CPU1PM        1 INTL 20051117)
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.839443] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.839450] ACPI: Processor [CPU1] (supports 8 throttling states)
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.839531] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  3B, should be 01 [20070126]
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.839540] ACPI: SSDT 3FFC94F0, 04A4 (r1    AMI   CPU2PM        1 INTL 20051117)
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.862596] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec 24 16:04:49 xx6xx-laptop kernel: [   34.862606] ACPI: Processor [CPU2] (supports 8 throttling states)
Dec 24 16:04:49 xx6xx-laptop kernel: [    4.380000] Marking TSC unstable due to: possible TSC halt in C2.
Dec 24 16:04:49 xx6xx-laptop kernel: [    4.384000] Time: acpi_pm clocksource has been installed.
Dec 24 16:04:49 xx6xx-laptop kernel: [    4.388000] ACPI: Thermal Zone [THRM] (30 C)
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] usbcore: registered new interface driver usbfs
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] usbcore: registered new interface driver hub
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] usbcore: registered new device driver usb
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] USB Universal Host Controller Interface driver v3.0
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ec00
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] usb usb1: configuration #1 chosen from 1 choice
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] hub 1-0:1.0: USB hub found
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.188000] hub 1-0:1.0: 2 ports detected
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.292000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.292000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.292000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.292000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e880
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.292000] usb usb2: configuration #1 chosen from 1 choice
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.292000] hub 2-0:1.0: USB hub found
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.292000] hub 2-0:1.0: 2 ports detected
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.320000] SCSI subsystem initialized
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.396000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 20 (level, low) -> IRQ 20
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.396000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.396000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.396000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e800
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.396000] usb usb3: configuration #1 chosen from 1 choice
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.396000] hub 3-0:1.0: USB hub found
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.396000] hub 3-0:1.0: 2 ports detected
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.500000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 22 (level, low) -> IRQ 21
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.500000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.500000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.500000] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000e480
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.500000] usb usb4: configuration #1 chosen from 1 choice
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.500000] hub 4-0:1.0: USB hub found
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.500000] hub 4-0:1.0: 2 ports detected
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.536000] usb 1-1: new low speed USB device using uhci_hcd and address 2
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.608000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.608000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.608000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.608000] ehci_hcd 0000:00:1d.7: debug port 1
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.608000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.656000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.656000] usb usb5: configuration #1 chosen from 1 choice
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.656000] hub 5-0:1.0: USB hub found
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.656000] hub 5-0:1.0: 8 ports detected
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.764000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.764000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.764000] scsi0 : ata_piix
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.764000] scsi1 : ata_piix
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.764000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.764000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.928000] ata1.00: ATA-7: FUJITSU MHV2120BH PL, 00000029, max UDMA/100
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.928000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 24 16:04:49 xx6xx-laptop kernel: [    5.944000] ata1.00: configured for UDMA/100
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.288000] ata2.01: ATAPI: MATSHITADVD-RAM UJ-850S, 1.21, max UDMA/33
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.460000] ata2.01: configured for UDMA/33
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.460000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120B 0000 PQ: 0 ANSI: 5
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.460000] scsi 1:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.21 PQ: 0 ANSI: 5
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.460000] r8169 Gigabit Ethernet driver 2.2LK loaded
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.460000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 17
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.464000] eth0: RTL8168b/8111b at 0xf8860000, 00:18:f3:5f:34:1c, XID 38000000 IRQ 17
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.464000] ACPI: PCI Interrupt 0000:06:00.0[B] -> GSI 17 (level, low) -> IRQ 22
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.516000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.540000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.540000] sd 0:0:0:0: [sda] Write Protect is off
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.540000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.540000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.540000] sd 0:0:0:0: [sda] Write Protect is off
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.540000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.540000]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.668000] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.676000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.676000] sr 1:0:1:0: Attached scsi generic sg1 type 5
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.680000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 24 16:04:49 xx6xx-laptop kernel: [    6.680000] Uniform CD-ROM driver Revision: 3.20
Dec 24 16:04:49 xx6xx-laptop kernel: [    7.080000] usb 5-4: new high speed USB device using ehci_hcd and address 4
Dec 24 16:04:49 xx6xx-laptop kernel: [    7.236000] usb 5-4: configuration #1 chosen from 1 choice
Dec 24 16:04:49 xx6xx-laptop kernel: [    7.300000] Attempting manual resume
Dec 24 16:04:49 xx6xx-laptop kernel: [    7.348000] kjournald starting.  Commit interval 5 seconds
Dec 24 16:04:49 xx6xx-laptop kernel: [    7.348000] EXT3-fs: mounted filesystem with ordered data mode.
Dec 24 16:04:49 xx6xx-laptop kernel: [    7.480000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Dec 24 16:04:49 xx6xx-laptop kernel: [    7.740000] usb 2-1: configuration #1 chosen from 1 choice
Dec 24 16:04:49 xx6xx-laptop kernel: [    7.996000] usb 1-1: new low speed USB device using uhci_hcd and address 4
Dec 24 16:04:49 xx6xx-laptop kernel: [    8.184000] usb 1-1: configuration #1 chosen from 1 choice
Dec 24 16:04:49 xx6xx-laptop kernel: [   14.840000] Linux agpgart interface v0.102 (c) Dave Jones
Dec 24 16:04:49 xx6xx-laptop kernel: [   14.884000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 24 16:04:49 xx6xx-laptop kernel: [   14.888000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.172000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.172000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.220000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.220000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.220000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.228000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.336000] iTCO_vendor_support: vendor-support=0
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.336000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.336000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.336000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.840000] Bluetooth: Core ver 2.11
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.840000] NET: Registered protocol family 31
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.840000] Bluetooth: HCI device and connection manager initialized
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.840000] Bluetooth: HCI socket layer initialized
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.948000] sdhci: Secure Digital Host Controller Interface driver
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.948000] sdhci: Copyright(c) Pierre Ossman
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.984000] Bluetooth: HCI USB driver ver 2.9
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.988000] usbcore: registered new interface driver hci_usb
Dec 24 16:04:49 xx6xx-laptop kernel: [   15.992000] usbcore: registered new interface driver hiddev
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.008000] input: A4Tech PS/2+USB Mouse as /class/input/input2
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.008000] input: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1d.0-1
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.008000] usbcore: registered new interface driver usbhid
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.008000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.404000] input: PC Speaker as /class/input/input3
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.504000] Linux video capture interface: v2.00
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.560000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.784000] usbcore: registered new interface driver gspca
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.784000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.820000] sdhci: SDHCI controller found at 0000:06:00.1 [1180:0822] (rev 19)
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.820000] ACPI: PCI Interrupt 0000:06:00.1[B] -> GSI 17 (level, low) -> IRQ 22
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.820000] mmc0: SDHCI at 0xfeaff400 irq 22 DMA
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.820000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 23
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.860000] NET: Registered protocol family 23
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.948000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04713/0x200000
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.984000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.988000] found SMC SuperIO Chip (devid=0x7a rev=01 base=0x002e): LPC47N227
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.988000] smsc_superio_flat(): fir: 0x6f8, sir: 0x2f8, dma: 15, irq: 3, mode: 0x0e
Dec 24 16:04:49 xx6xx-laptop kernel: [   16.988000] smsc_ircc_present: can't get sir_base of 0x2f8
Dec 24 16:04:49 xx6xx-laptop kernel: [   18.344000] lp: driver loaded but no devices found
Dec 24 16:04:49 xx6xx-laptop kernel: [   18.644000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 24 16:04:49 xx6xx-laptop kernel: [   18.792000] Adding 999912k swap on /dev/sda7.  Priority:-1 extents:1 across:999912k
Dec 24 16:04:49 xx6xx-laptop kernel: [   19.312000] EXT3 FS on sda6, internal journal
Dec 24 16:04:49 xx6xx-laptop kernel: [   22.912000] ACPI: Battery Slot [BAT0] (battery present)
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.120000] input: Power Button (FF) as /class/input/input5
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.120000] ACPI: Power Button (FF) [PWRF]
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.120000] input: Lid Switch as /class/input/input6
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.120000] ACPI: Lid Switch [LID]
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.120000] input: Power Button (CM) as /class/input/input7
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.120000] ACPI: Power Button (CM) [PWRB]
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.120000] input: Sleep Button (CM) as /class/input/input8
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.120000] ACPI: Sleep Button (CM) [SLPB]
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.300000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.340000] No dock devices found.
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.660000] Asus Laptop ACPI Extras version 0.30
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.660000]   unsupported model A8JP, trying default values
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.660000]   send /proc/acpi/dsdt to the developers
Dec 24 16:04:49 xx6xx-laptop kernel: [   23.704000] ACPI: AC Adapter [AC0] (off-line)
Dec 24 16:04:50 xx6xx-laptop kernel: [   25.508000] r8169: eth0: link down
Dec 24 16:04:50 xx6xx-laptop kernel: [   25.852000] NET: Registered protocol family 10
Dec 24 16:04:50 xx6xx-laptop kernel: [   25.852000] lo: Disabled Privacy Extensions
Dec 24 16:04:50 xx6xx-laptop kernel: [   25.852000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 24 16:04:50 xx6xx-laptop kernel: [   25.852000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 24 16:04:51 xx6xx-laptop kernel: [   26.272000] ppdev: user-space parallel port driver
Dec 24 16:04:51 xx6xx-laptop kernel: [   26.472000] audit(1198508691.265:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5187 profile="/usr/sbin/cupsd"
Dec 24 16:04:51 xx6xx-laptop kernel: [   26.504000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 24 16:04:51 xx6xx-laptop kernel: [   26.504000] apm: disabled - APM is not SMP safe.
Dec 24 16:04:51 xx6xx-laptop kernel: [   26.948000] Failure registering capabilities with primary security module.
Dec 24 16:04:52 xx6xx-laptop dhcdbd: Started up.
Dec 24 16:04:52 xx6xx-laptop kernel: [   27.212000] Bluetooth: L2CAP ver 2.8
Dec 24 16:04:52 xx6xx-laptop kernel: [   27.212000] Bluetooth: L2CAP socket layer initialized
Dec 24 16:04:52 xx6xx-laptop kernel: [   27.312000] Bluetooth: RFCOMM socket layer initialized
Dec 24 16:04:52 xx6xx-laptop kernel: [   27.312000] Bluetooth: RFCOMM TTY layer initialized
Dec 24 16:04:52 xx6xx-laptop kernel: [   27.312000] Bluetooth: RFCOMM ver 1.8
Dec 24 16:05:03 xx6xx-laptop kernel: [   39.112000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Dec 24 16:05:04 xx6xx-laptop kernel: [   39.116000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
Dec 24 16:05:04 xx6xx-laptop kernel: [   39.116000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
Dec 24 16:05:04 xx6xx-laptop kernel: [   39.164000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 24 16:05:06 xx6xx-laptop kernel: [   41.372000] mtrr: no more MTRRs available
Dec 24 16:05:06 xx6xx-laptop kernel: [   41.372000] mtrr: no more MTRRs available
Dec 24 16:05:06 xx6xx-laptop kernel: [   41.376000] mtrr: no more MTRRs available
Dec 24 16:05:06 xx6xx-laptop kernel: [   41.376000] mtrr: no more MTRRs available
Dec 24 16:05:07 xx6xx-laptop kernel: [   42.272000] Clocksource tsc unstable (delta = -268787400 ns)
Dec 24 16:07:05 xx6xx-laptop exiting on signal 15
Dec 26 18:30:52 xx6xx-laptop syslogd 1.4.1#21ubuntu3: restart.
Dec 26 18:30:52 xx6xx-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Dec 26 18:30:52 xx6xx-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Dec 26 18:30:52 xx6xx-laptop kernel: Symbols match kernel version 2.6.22.
Dec 26 18:30:52 xx6xx-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 000000003ffce000 - 0000000040000000 (ACPI NVS)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] 127MB HIGHMEM available.
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] 896MB LOWMEM available.
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] found SMP MP-table at 000ff780
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Zone PFN ranges:
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]   DMA             0 ->     4096
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]   HighMem    229376 ->   262080
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000]     0:        0 ->   262080
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] DMI 2.3 present.
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7C40 checksum 0
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: RSDP 000F7C40, 0014 (r0 ACPIAM)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: RSDT 3FFC0000, 003C (r1 A M I  OEMRSDT   8000610 MSFT       97)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: FACP 3FFC0200, 0084 (r2 A M I  OEMFACP   8000610 MSFT       97)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: DSDT 3FFC0460, 837F (r1  A8J00 A8J00005        5 INTL  2002026)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: FACS 3FFCE000, 0040
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: APIC 3FFC0390, 005C (r1 A M I  OEMAPIC   8000610 MSFT       97)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: MCFG 3FFC03F0, 003C (r1 A M I  OEMMCFG   8000610 MSFT       97)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: BOOT 3FFC0430, 0028 (r1 A M I  OEMBOOT   8000610 MSFT       97)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: OEMB 3FFCE040, 0046 (r1 A M I  AMI_OEM   8000610 MSFT       97)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: TCPA 3FFC87E0, 0032 (r1 A M I  TBLOEMID        1 MSFT       97)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 260033
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Kernel command line: root=UUID=b0303344-8d15-4766-a216-b901194d5dc0 ro quiet splash
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Initializing CPU#0
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 26 18:30:52 xx6xx-laptop kernel: [    0.000000] Detected 1995.131 MHz processor.
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.549754] Console: colour VGA+ 80x25
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.550066] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.550497] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592624] Memory: 1027712k/1048320k available (2015k kernel code, 19964k reserved, 916k data, 364k init, 130816k highmem)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592639] virtual kernel memory layout:
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592640]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592642]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592644]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592646]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592648]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592650]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592652]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592657] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.592704] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672696] Calibrating delay using timer specific routine.. 3995.47 BogoMIPS (lpj=7990950)
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672726] Security Framework v1.0.0 initialized
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672733] SELinux:  Disabled at boot.
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672752] Mount-cache hash table entries: 512
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672924] monitor/mwait feature present.
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672927] using mwait in idle threads.
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672933] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672937] CPU: L2 cache: 4096K
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672941] CPU: Physical Processor ID: 0
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672944] CPU: Processor Core ID: 0
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672960] Compat vDSO mapped to ffffe000.
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.672978] Checking 'hlt' instruction... OK.
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.688834] SMP alternatives: switching to UP code
Dec 26 18:30:52 xx6xx-laptop kernel: [   36.689447] Early unpacking initramfs... done
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.236754] ACPI: Core revision 20070126
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.236840] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.255885] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.255908] SMP alternatives: switching to SMP code
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.255996] Booting processor 1/1 eip 3000
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.266762] Initializing CPU#1
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.344360] Calibrating delay using timer specific routine.. 3990.36 BogoMIPS (lpj=7980734)
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.344378] monitor/mwait feature present.
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.344383] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.344386] CPU: L2 cache: 4096K
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.344389] CPU: Physical Processor ID: 0
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.344392] CPU: Processor Core ID: 1
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.345595] CPU1: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.345628] Total of 2 processors activated (7985.84 BogoMIPS).
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.345829] ENABLING IO-APIC IRQs
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.346052] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.492427] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.512442] Brought up 2 CPUs
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.872163] migration_cost=69
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.872349] Booting paravirtualized kernel on bare hardware
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.872452] Time: 18:30:28  Date: 11/26/107
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.872479] NET: Registered protocol family 16
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.872595] EISA bus registered
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.872602] ACPI: bus type pci registered
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.872816] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.872819] PCI: Using configuration type 1
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.872822] Setting up standard PCI resources
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.881218] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.958367] ACPI: Interpreter enabled
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.958372] ACPI: (supports S0 S1 S3 S4 S5)
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.958410] ACPI: Using IOAPIC for interrupt routing
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.975197] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.975442] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.976398] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.976405] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Dec 26 18:30:52 xx6xx-laptop kernel: [   37.978021] PCI: Transparent bridge - 0000:00:1e.0
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.001520] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.001810] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.002095] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.002391] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.002675] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.002958] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.003242] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.003526] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 7 10 11 12 14 15)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.003847] ACPI: Power Resource [GFAN] (off)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.003856] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.003871] pnp: PnP ACPI init
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.003887] ACPI: bus type pnp registered
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.009752] pnp: PnP ACPI: found 16 devices
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.009756] ACPI: ACPI bus type pnp unregistered
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.009762] PnPBIOS: Disabled by ACPI PNP
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.009835] PCI: Using ACPI for IRQ routing
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.009839] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032704] NET: Registered protocol family 8
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032707] NET: Registered protocol family 20
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032793] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032809] pnp: 00:09: ioport range 0xa00-0xa0f has been reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032817] pnp: 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032822] pnp: 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032827] pnp: 00:0a: iomem range 0xfed45000-0xfed89fff has been reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032836] pnp: 00:0b: iomem range 0xffb80000-0xffbfffff could not be reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032841] pnp: 00:0b: iomem range 0xfff80000-0xffffffff could not be reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032850] pnp: 00:0c: iomem range 0xffc00000-0xfff7ffff could not be reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032857] pnp: 00:0d: ioport range 0x400-0x41f has been reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032862] pnp: 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032868] pnp: 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032873] pnp: 00:0d: iomem range 0xfec10000-0xfec17fff has been reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032877] pnp: 00:0d: iomem range 0xfec18000-0xfec1ffff has been reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032886] pnp: 00:0e: iomem range 0xe0000000-0xe3ffffff has been reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032895] pnp: 00:0f: iomem range 0x0-0x9ffff could not be reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032900] pnp: 00:0f: iomem range 0xc0000-0xcffff could not be reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032904] pnp: 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.032909] pnp: 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.036045] Time: tsc clocksource has been installed.
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063402] PCI: Bridge: 0000:00:01.0
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063406]   IO window: 9000-bfff
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063412]   MEM window: fdf00000-fdffffff
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063418]   PREFETCH window: bdf00000-ddefffff
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063424] PCI: Bridge: 0000:00:1c.0
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063426]   IO window: disabled.
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063435]   MEM window: fe000000-fe0fffff
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063441]   PREFETCH window: disabled.
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063448] PCI: Bridge: 0000:00:1c.2
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063453]   IO window: c000-cfff
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063461]   MEM window: fe100000-fe1fffff
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063467]   PREFETCH window: disabled.
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063475] PCI: Bridge: 0000:00:1c.3
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063477]   IO window: disabled.
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063485]   MEM window: disabled.
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063490]   PREFETCH window: disabled.
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063499] PCI: Bridge: 0000:00:1e.0
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063501]   IO window: disabled.
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063509]   MEM window: fea00000-feafffff
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063515]   PREFETCH window: disabled.
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063538] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063576] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063616] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 17
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063656] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.063700] NET: Registered protocol family 2
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.100047] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.100114] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.101064] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.101399] TCP: Hash tables configured (established 131072 bind 65536)
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.101403] TCP reno registered
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.112202] checking if image is initramfs...<6>Switched to high resolution mode on CPU 1
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.563789] Switched to high resolution mode on CPU 0
Dec 26 18:30:52 xx6xx-laptop kernel: [   38.631951]  it is
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.189196] Freeing initrd memory: 7057k freed
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.189344] Simple Boot Flag at 0x52 set to 0x1
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.190065] audit: initializing netlink socket (disabled)
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.190088] audit(1198693829.248:1): initialized
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.190245] highmem bounce pool size: 64 pages
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.193318] VFS: Disk quotas dquot_6.5.1
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.193394] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.193525] io scheduler noop registered
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.193529] io scheduler anticipatory registered
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.193532] io scheduler deadline registered
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.193553] io scheduler cfq registered (default)
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.193863] assign_interrupt_mode Found MSI capability
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.194065] assign_interrupt_mode Found MSI capability
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.194328] assign_interrupt_mode Found MSI capability
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.194594] assign_interrupt_mode Found MSI capability
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.194880] isapnp: Scanning for PnP cards...
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.548879] isapnp: No Plug & Play device found
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.582020] Real Time Clock Driver v1.12ac
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.582200] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.582439] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.584060] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.584377] input: Macintosh mouse button emulation as /class/input/input0
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.584510] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.587347] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589037] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589044] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589048] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589052] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589056] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589328] mice: PS/2 mouse device common for all mice
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589615] EISA: Probing bus 0 at eisa.0
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589663] EISA: Detected 0 cards.
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589893] TCP cubic registered
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589910] NET: Registered protocol family 1
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.589939] Using IPI No-Shortcut mode
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.590172]   Magic number: 3:379:545
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.590473] Freeing unused kernel memory: 364k freed
Dec 26 18:30:52 xx6xx-laptop kernel: [   39.695388] input: AT Translated Set 2 keyboard as /class/input/input1
Dec 26 18:30:52 xx6xx-laptop kernel: [   40.922631] AppArmor: AppArmor initialized<5>audit(1198693830.748:2):  type=1505 info="AppArmor initialized" pid=1247
Dec 26 18:30:52 xx6xx-laptop kernel: [   40.939210] fuse init (API version 7.8)
Dec 26 18:30:52 xx6xx-laptop kernel: [   40.949008] Failure registering capabilities with primary security module.
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.148379] ACPI: Transitioning device [FN00] to D3
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.148383] ACPI: Transitioning device [FN00] to D3
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.148388] ACPI: Fan [FN00] (off)
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.158445] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  83, should be 6E [20070126]
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.158459] ACPI: SSDT 3FFC8820, 0CC3 (r1    AMI   CPU1PM        1 INTL 20051117)
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.159130] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.159138] ACPI: Processor [CPU1] (supports 8 throttling states)
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.159215] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  3B, should be 01 [20070126]
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.159224] ACPI: SSDT 3FFC94F0, 04A4 (r1    AMI   CPU2PM        1 INTL 20051117)
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.178317] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec 26 18:30:52 xx6xx-laptop kernel: [   41.178327] ACPI: Processor [CPU2] (supports 8 throttling states)
Dec 26 18:30:52 xx6xx-laptop kernel: [    4.428000] Marking TSC unstable due to: possible TSC halt in C2.
Dec 26 18:30:52 xx6xx-laptop kernel: [    4.432000] Time: acpi_pm clocksource has been installed.
Dec 26 18:30:52 xx6xx-laptop kernel: [    4.436000] ACPI: Thermal Zone [THRM] (45 C)
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] usbcore: registered new interface driver usbfs
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] usbcore: registered new interface driver hub
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] usbcore: registered new device driver usb
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] USB Universal Host Controller Interface driver v3.0
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ec00
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] usb usb1: configuration #1 chosen from 1 choice
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] hub 1-0:1.0: USB hub found
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.360000] hub 1-0:1.0: 2 ports detected
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.464000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.464000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.464000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.464000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e880
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.464000] usb usb2: configuration #1 chosen from 1 choice
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.464000] hub 2-0:1.0: USB hub found
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.464000] hub 2-0:1.0: 2 ports detected
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.552000] SCSI subsystem initialized
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.568000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 20 (level, low) -> IRQ 20
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.568000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.568000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.568000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e800
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.568000] usb usb3: configuration #1 chosen from 1 choice
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.568000] hub 3-0:1.0: USB hub found
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.568000] hub 3-0:1.0: 2 ports detected
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.672000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 22 (level, low) -> IRQ 21
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.672000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.672000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.672000] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000e480
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.672000] usb usb4: configuration #1 chosen from 1 choice
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.672000] hub 4-0:1.0: USB hub found
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.672000] hub 4-0:1.0: 2 ports detected
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.704000] usb 1-1: new low speed USB device using uhci_hcd and address 2
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.776000] r8169 Gigabit Ethernet driver 2.2LK loaded
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.776000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 17
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.776000] eth0: RTL8168b/8111b at 0xf88b8000, 00:18:f3:5f:34:1c, XID 38000000 IRQ 17
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.776000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.776000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.776000] scsi0 : ata_piix
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.776000] scsi1 : ata_piix
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.776000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.776000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.876000] usb 1-1: configuration #1 chosen from 1 choice
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.940000] ata1.00: ATA-7: FUJITSU MHV2120BH PL, 00000029, max UDMA/100
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.940000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 26 18:30:52 xx6xx-laptop kernel: [    5.956000] ata1.00: configured for UDMA/100
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.128000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.276000] ata2.01: ATAPI: MATSHITADVD-RAM UJ-850S, 1.21, max UDMA/33
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.364000] usb 2-1: configuration #1 chosen from 1 choice
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.448000] ata2.01: configured for UDMA/33
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.448000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120B 0000 PQ: 0 ANSI: 5
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.448000] scsi 1:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.21 PQ: 0 ANSI: 5
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.448000] ACPI: PCI Interrupt 0000:06:00.0[B] -> GSI 17 (level, low) -> IRQ 22
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.504000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.508000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.508000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.508000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.508000] ehci_hcd 0000:00:1d.7: debug port 1
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.508000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.512000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.512000] usb usb5: configuration #1 chosen from 1 choice
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.512000] hub 5-0:1.0: USB hub found
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.512000] hub 5-0:1.0: 8 ports detected
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.524000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.524000] sd 0:0:0:0: [sda] Write Protect is off
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.524000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.524000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.524000] sd 0:0:0:0: [sda] Write Protect is off
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.524000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.524000]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.648000] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.656000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.656000] Uniform CD-ROM driver Revision: 3.20
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.656000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.656000] sr 1:0:1:0: Attached scsi generic sg1 type 5
Dec 26 18:30:52 xx6xx-laptop kernel: [    6.660000] usb 2-1: USB disconnect, address 2
Dec 26 18:30:52 xx6xx-laptop kernel: [    7.096000] Attempting manual resume
Dec 26 18:30:52 xx6xx-laptop kernel: [    7.152000] kjournald starting.  Commit interval 5 seconds
Dec 26 18:30:52 xx6xx-laptop kernel: [    7.152000] EXT3-fs: mounted filesystem with ordered data mode.
Dec 26 18:30:52 xx6xx-laptop kernel: [    7.452000] usb 5-4: new high speed USB device using ehci_hcd and address 4
Dec 26 18:30:52 xx6xx-laptop kernel: [    7.592000] usb 5-4: configuration #1 chosen from 1 choice
Dec 26 18:30:52 xx6xx-laptop kernel: [    7.592000] usb 1-1: USB disconnect, address 2
Dec 26 18:30:52 xx6xx-laptop kernel: [    7.592000] usbcore: registered new interface driver hiddev
Dec 26 18:30:52 xx6xx-laptop kernel: [    7.832000] usb 1-1: new low speed USB device using uhci_hcd and address 3
Dec 26 18:30:52 xx6xx-laptop kernel: [    8.004000] usb 1-1: configuration #1 chosen from 1 choice
Dec 26 18:30:52 xx6xx-laptop kernel: [    8.256000] usb 2-1: new full speed USB device using uhci_hcd and address 3
Dec 26 18:30:52 xx6xx-laptop kernel: [    8.500000] usb 2-1: configuration #1 chosen from 1 choice
Dec 26 18:30:52 xx6xx-laptop kernel: [    8.516000] input: A4Tech PS/2+USB Mouse as /class/input/input2
Dec 26 18:30:52 xx6xx-laptop kernel: [    8.516000] input: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1d.0-1
Dec 26 18:30:52 xx6xx-laptop kernel: [    8.516000] usbcore: registered new interface driver usbhid
Dec 26 18:30:52 xx6xx-laptop kernel: [    8.516000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Dec 26 18:30:52 xx6xx-laptop kernel: [   15.188000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 26 18:30:52 xx6xx-laptop kernel: [   15.192000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 26 18:30:52 xx6xx-laptop kernel: [   15.348000] iTCO_vendor_support: vendor-support=0
Dec 26 18:30:52 xx6xx-laptop kernel: [   15.348000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Dec 26 18:30:52 xx6xx-laptop kernel: [   15.348000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
Dec 26 18:30:52 xx6xx-laptop kernel: [   15.348000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 26 18:30:52 xx6xx-laptop kernel: [   15.360000] Linux agpgart interface v0.102 (c) Dave Jones
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.260000] input: PC Speaker as /class/input/input3
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.580000] sdhci: Secure Digital Host Controller Interface driver
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.580000] sdhci: Copyright(c) Pierre Ossman
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.580000] sdhci: SDHCI controller found at 0000:06:00.1 [1180:0822] (rev 19)
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.580000] ACPI: PCI Interrupt 0000:06:00.1[B] -> GSI 17 (level, low) -> IRQ 22
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.580000] mmc0: SDHCI at 0xfeaff400 irq 22 DMA
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.592000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04713/0x200000
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.592000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.592000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.628000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.744000] Bluetooth: Core ver 2.11
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.744000] NET: Registered protocol family 31
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.744000] Bluetooth: HCI device and connection manager initialized
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.744000] Bluetooth: HCI socket layer initialized
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.764000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.764000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.764000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.776000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.784000] Linux video capture interface: v2.00
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.836000] NET: Registered protocol family 23
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.888000] Bluetooth: HCI USB driver ver 2.9
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.888000] usbcore: registered new interface driver hci_usb
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.920000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.936000] found SMC SuperIO Chip (devid=0x7a rev=01 base=0x002e): LPC47N227
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.936000] smsc_superio_flat(): fir: 0x6f8, sir: 0x2f8, dma: 15, irq: 3, mode: 0x0e
Dec 26 18:30:52 xx6xx-laptop kernel: [   16.936000] smsc_ircc_present: can't get sir_base of 0x2f8
Dec 26 18:30:52 xx6xx-laptop kernel: [   17.140000] usbcore: registered new interface driver gspca
Dec 26 18:30:52 xx6xx-laptop kernel: [   17.140000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
Dec 26 18:30:52 xx6xx-laptop kernel: [   17.196000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 23
Dec 26 18:30:52 xx6xx-laptop kernel: [   18.784000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Dec 26 18:30:52 xx6xx-laptop kernel: [   18.792000] hda_intel: azx_get_response timeout, switching to polling mode...
Dec 26 18:30:52 xx6xx-laptop kernel: [   18.804000] lp: driver loaded but no devices found
Dec 26 18:30:52 xx6xx-laptop kernel: [   19.012000] Adding 999912k swap on /dev/sda7.  Priority:-1 extents:1 across:999912k
Dec 26 18:30:52 xx6xx-laptop kernel: [   19.664000] EXT3 FS on sda6, internal journal
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.232000] ACPI: Battery Slot [BAT0] (battery present)
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.448000] input: Power Button (FF) as /class/input/input5
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.448000] ACPI: Power Button (FF) [PWRF]
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.492000] input: Lid Switch as /class/input/input6
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.492000] ACPI: Lid Switch [LID]
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.492000] input: Power Button (CM) as /class/input/input7
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.492000] ACPI: Power Button (CM) [PWRB]
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.504000] input: Sleep Button (CM) as /class/input/input8
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.504000] ACPI: Sleep Button (CM) [SLPB]
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.592000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Dec 26 18:30:52 xx6xx-laptop kernel: [   23.628000] No dock devices found.
Dec 26 18:30:52 xx6xx-laptop kernel: [   24.000000] Asus Laptop ACPI Extras version 0.30
Dec 26 18:30:52 xx6xx-laptop kernel: [   24.000000]   unsupported model A8JP, trying default values
Dec 26 18:30:52 xx6xx-laptop kernel: [   24.000000]   send /proc/acpi/dsdt to the developers
Dec 26 18:30:52 xx6xx-laptop kernel: [   24.036000] ACPI: AC Adapter [AC0] (off-line)
Dec 26 18:30:53 xx6xx-laptop kernel: [   26.028000] r8169: eth0: link down
Dec 26 18:30:53 xx6xx-laptop kernel: [   26.196000] NET: Registered protocol family 10
Dec 26 18:30:53 xx6xx-laptop kernel: [   26.196000] lo: Disabled Privacy Extensions
Dec 26 18:30:53 xx6xx-laptop kernel: [   26.196000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 26 18:30:53 xx6xx-laptop kernel: [   26.196000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 26 18:30:54 xx6xx-laptop kernel: [   26.572000] ppdev: user-space parallel port driver
Dec 26 18:30:54 xx6xx-laptop kernel: [   26.820000] audit(1198690254.179:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5204 profile="/usr/sbin/cupsd"
Dec 26 18:30:54 xx6xx-laptop kernel: [   26.884000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 26 18:30:54 xx6xx-laptop kernel: [   26.884000] apm: disabled - APM is not SMP safe.
Dec 26 18:30:55 xx6xx-laptop kernel: [   27.340000] Failure registering capabilities with primary security module.
Dec 26 18:30:55 xx6xx-laptop dhcdbd: Started up.
Dec 26 18:30:55 xx6xx-laptop kernel: [   27.524000] Bluetooth: L2CAP ver 2.8
Dec 26 18:30:55 xx6xx-laptop kernel: [   27.524000] Bluetooth: L2CAP socket layer initialized
Dec 26 18:30:55 xx6xx-laptop kernel: [   27.632000] Bluetooth: RFCOMM socket layer initialized
Dec 26 18:30:55 xx6xx-laptop kernel: [   27.632000] Bluetooth: RFCOMM TTY layer initialized
Dec 26 18:30:55 xx6xx-laptop kernel: [   27.632000] Bluetooth: RFCOMM ver 1.8
Dec 26 18:31:07 xx6xx-laptop kernel: [   39.420000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Dec 26 18:31:07 xx6xx-laptop kernel: [   39.424000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
Dec 26 18:31:07 xx6xx-laptop kernel: [   39.424000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
Dec 26 18:31:07 xx6xx-laptop kernel: [   39.476000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 26 18:31:09 xx6xx-laptop kernel: [   41.652000] mtrr: no more MTRRs available
Dec 26 18:31:09 xx6xx-laptop last message repeated 3 times
Dec 26 18:31:10 xx6xx-laptop kernel: [   42.772000] Clocksource tsc unstable (delta = -449071013 ns)
Dec 26 18:31:30 xx6xx-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Dec 26 18:31:32 xx6xx-laptop kernel: [   65.072000] NET: Registered protocol family 17
Dec 26 18:31:36 xx6xx-laptop kernel: [   69.020000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Dec 26 18:31:46 xx6xx-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Dec 26 18:31:46 xx6xx-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Dec 26 18:31:46 xx6xx-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Dec 26 18:38:33 xx6xx-laptop syslogd 1.4.1#21ubuntu3: restart.
```



 and_**[SIZE="5"] the output of dmesg.[/SIZE]**_

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffce000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262080
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262080
[    0.000000] On node 0 totalpages: 262080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32449 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7C40 checksum 0
[    0.000000] ACPI: RSDP 000F7C40, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFC0000, 003C (r1 A M I  OEMRSDT   8000610 MSFT       97)
[    0.000000] ACPI: FACP 3FFC0200, 0084 (r2 A M I  OEMFACP   8000610 MSFT       97)
[    0.000000] ACPI: DSDT 3FFC0460, 837F (r1  A8J00 A8J00005        5 INTL  2002026)
[    0.000000] ACPI: FACS 3FFCE000, 0040
[    0.000000] ACPI: APIC 3FFC0390, 005C (r1 A M I  OEMAPIC   8000610 MSFT       97)
[    0.000000] ACPI: MCFG 3FFC03F0, 003C (r1 A M I  OEMMCFG   8000610 MSFT       97)
[    0.000000] ACPI: BOOT 3FFC0430, 0028 (r1 A M I  OEMBOOT   8000610 MSFT       97)
[    0.000000] ACPI: OEMB 3FFCE040, 0046 (r1 A M I  AMI_OEM   8000610 MSFT       97)
[    0.000000] ACPI: TCPA 3FFC87E0, 0032 (r1 A M I  TBLOEMID        1 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] Built 1 zonelists.  Total pages: 260033
[    0.000000] Kernel command line: root=UUID=b0303344-8d15-4766-a216-b901194d5dc0 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.131 MHz processor.
[   36.549754] Console: colour VGA+ 80x25
[   36.550066] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   36.550497] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   36.592624] Memory: 1027712k/1048320k available (2015k kernel code, 19964k reserved, 916k data, 364k init, 130816k highmem)
[   36.592639] virtual kernel memory layout:
[   36.592640]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   36.592642]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   36.592644]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   36.592646]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   36.592648]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   36.592650]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   36.592652]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   36.592657] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   36.592704] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   36.672696] Calibrating delay using timer specific routine.. 3995.47 BogoMIPS (lpj=7990950)
[   36.672726] Security Framework v1.0.0 initialized
[   36.672733] SELinux:  Disabled at boot.
[   36.672752] Mount-cache hash table entries: 512
[   36.672911] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   36.672924] monitor/mwait feature present.
[   36.672927] using mwait in idle threads.
[   36.672933] CPU: L1 I cache: 32K, L1 D cache: 32K
[   36.672937] CPU: L2 cache: 4096K
[   36.672941] CPU: Physical Processor ID: 0
[   36.672944] CPU: Processor Core ID: 0
[   36.672947] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   36.672960] Compat vDSO mapped to ffffe000.
[   36.672978] Checking 'hlt' instruction... OK.
[   36.688834] SMP alternatives: switching to UP code
[   36.689447] Early unpacking initramfs... done
[   37.236754] ACPI: Core revision 20070126
[   37.236840] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   37.255885] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[   37.255908] SMP alternatives: switching to SMP code
[   37.255996] Booting processor 1/1 eip 3000
[   37.266762] Initializing CPU#1
[   37.344360] Calibrating delay using timer specific routine.. 3990.36 BogoMIPS (lpj=7980734)
[   37.344370] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   37.344378] monitor/mwait feature present.
[   37.344383] CPU: L1 I cache: 32K, L1 D cache: 32K
[   37.344386] CPU: L2 cache: 4096K
[   37.344389] CPU: Physical Processor ID: 0
[   37.344392] CPU: Processor Core ID: 1
[   37.344395] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   37.345595] CPU1: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[   37.345628] Total of 2 processors activated (7985.84 BogoMIPS).
[   37.345829] ENABLING IO-APIC IRQs
[   37.346052] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   37.492427] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   37.512442] Brought up 2 CPUs
[   37.872163] migration_cost=69
[   37.872349] Booting paravirtualized kernel on bare hardware
[   37.872452] Time: 18:30:28  Date: 11/26/107
[   37.872479] NET: Registered protocol family 16
[   37.872595] EISA bus registered
[   37.872602] ACPI: bus type pci registered
[   37.872816] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[   37.872819] PCI: Using configuration type 1
[   37.872822] Setting up standard PCI resources
[   37.879607] ACPI: EC: Look up EC in DSDT
[   37.881218] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   37.958367] ACPI: Interpreter enabled
[   37.958372] ACPI: (supports S0 S1 S3 S4 S5)
[   37.958410] ACPI: Using IOAPIC for interrupt routing
[   37.975197] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   37.975442] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   37.975472] PCI: Probing PCI hardware (bus 00)
[   37.976398] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   37.976405] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   37.978021] PCI: Transparent bridge - 0000:00:1e.0
[   37.978139] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   37.978436] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   37.978633] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   37.978894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   37.979109] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   37.979323] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   38.001520] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   38.001810] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   38.002095] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   38.002391] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   38.002675] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   38.002958] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   38.003242] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   38.003526] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   38.003847] ACPI: Power Resource [GFAN] (off)
[   38.003856] Linux Plug and Play Support v0.97 (c) Adam Belay
[   38.003871] pnp: PnP ACPI init
[   38.003887] ACPI: bus type pnp registered
[   38.009752] pnp: PnP ACPI: found 16 devices
[   38.009756] ACPI: ACPI bus type pnp unregistered
[   38.009762] PnPBIOS: Disabled by ACPI PNP
[   38.009835] PCI: Using ACPI for IRQ routing
[   38.009839] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   38.009847] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.3
[   38.009920] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
[   38.009990] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.3
[   38.032704] NET: Registered protocol family 8
[   38.032707] NET: Registered protocol family 20
[   38.032793] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   38.032809] pnp: 00:09: ioport range 0xa00-0xa0f has been reserved
[   38.032817] pnp: 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   38.032822] pnp: 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
[   38.032827] pnp: 00:0a: iomem range 0xfed45000-0xfed89fff has been reserved
[   38.032836] pnp: 00:0b: iomem range 0xffb80000-0xffbfffff could not be reserved
[   38.032841] pnp: 00:0b: iomem range 0xfff80000-0xffffffff could not be reserved
[   38.032850] pnp: 00:0c: iomem range 0xffc00000-0xfff7ffff could not be reserved
[   38.032857] pnp: 00:0d: ioport range 0x400-0x41f has been reserved
[   38.032862] pnp: 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[   38.032868] pnp: 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   38.032873] pnp: 00:0d: iomem range 0xfec10000-0xfec17fff has been reserved
[   38.032877] pnp: 00:0d: iomem range 0xfec18000-0xfec1ffff has been reserved
[   38.032886] pnp: 00:0e: iomem range 0xe0000000-0xe3ffffff has been reserved
[   38.032895] pnp: 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   38.032900] pnp: 00:0f: iomem range 0xc0000-0xcffff could not be reserved
[   38.032904] pnp: 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   38.032909] pnp: 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
[   38.036045] Time: tsc clocksource has been installed.
[   38.063402] PCI: Bridge: 0000:00:01.0
[   38.063406]   IO window: 9000-bfff
[   38.063412]   MEM window: fdf00000-fdffffff
[   38.063418]   PREFETCH window: bdf00000-ddefffff
[   38.063424] PCI: Bridge: 0000:00:1c.0
[   38.063426]   IO window: disabled.
[   38.063435]   MEM window: fe000000-fe0fffff
[   38.063441]   PREFETCH window: disabled.
[   38.063448] PCI: Bridge: 0000:00:1c.2
[   38.063453]   IO window: c000-cfff
[   38.063461]   MEM window: fe100000-fe1fffff
[   38.063467]   PREFETCH window: disabled.
[   38.063475] PCI: Bridge: 0000:00:1c.3
[   38.063477]   IO window: disabled.
[   38.063485]   MEM window: disabled.
[   38.063490]   PREFETCH window: disabled.
[   38.063499] PCI: Bridge: 0000:00:1e.0
[   38.063501]   IO window: disabled.
[   38.063509]   MEM window: fea00000-feafffff
[   38.063515]   PREFETCH window: disabled.
[   38.063538] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   38.063546] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   38.063576] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   38.063584] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   38.063616] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 17
[   38.063624] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   38.063656] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[   38.063666] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   38.063684] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   38.063700] NET: Registered protocol family 2
[   38.100047] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   38.100114] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   38.101064] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   38.101399] TCP: Hash tables configured (established 131072 bind 65536)
[   38.101403] TCP reno registered
[   38.112202] checking if image is initramfs...<6>Switched to high resolution mode on CPU 1
[   38.563789] Switched to high resolution mode on CPU 0
[   38.631951]  it is
[   39.189196] Freeing initrd memory: 7057k freed
[   39.189344] Simple Boot Flag at 0x52 set to 0x1
[   39.190065] audit: initializing netlink socket (disabled)
[   39.190088] audit(1198693829.248:1): initialized
[   39.190245] highmem bounce pool size: 64 pages
[   39.193318] VFS: Disk quotas dquot_6.5.1
[   39.193394] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   39.193525] io scheduler noop registered
[   39.193529] io scheduler anticipatory registered
[   39.193532] io scheduler deadline registered
[   39.193553] io scheduler cfq registered (default)
[   39.193676] Boot video device is 0000:01:00.0
[   39.193804] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   39.193863] assign_interrupt_mode Found MSI capability
[   39.193867] Allocate Port Service[0000:00:01.0:pcie00]
[   39.193991] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   39.194065] assign_interrupt_mode Found MSI capability
[   39.194068] Allocate Port Service[0000:00:1c.0:pcie00]
[   39.194118] Allocate Port Service[0000:00:1c.0:pcie02]
[   39.194255] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   39.194328] assign_interrupt_mode Found MSI capability
[   39.194332] Allocate Port Service[0000:00:1c.2:pcie00]
[   39.194381] Allocate Port Service[0000:00:1c.2:pcie02]
[   39.194520] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   39.194594] assign_interrupt_mode Found MSI capability
[   39.194597] Allocate Port Service[0000:00:1c.3:pcie00]
[   39.194646] Allocate Port Service[0000:00:1c.3:pcie02]
[   39.194880] isapnp: Scanning for PnP cards...
[   39.548879] isapnp: No Plug & Play device found
[   39.582020] Real Time Clock Driver v1.12ac
[   39.582200] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   39.582439] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   39.584060] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   39.584377] input: Macintosh mouse button emulation as /class/input/input0
[   39.584510] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   39.587347] i8042.c: Detected active multiplexing controller, rev 1.1.
[   39.589037] serio: i8042 KBD port at 0x60,0x64 irq 1
[   39.589044] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   39.589048] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   39.589052] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   39.589056] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   39.589328] mice: PS/2 mouse device common for all mice
[   39.589615] EISA: Probing bus 0 at eisa.0
[   39.589663] EISA: Detected 0 cards.
[   39.589893] TCP cubic registered
[   39.589910] NET: Registered protocol family 1
[   39.589939] Using IPI No-Shortcut mode
[   39.590172]   Magic number: 3:379:545
[   39.590473] Freeing unused kernel memory: 364k freed
[   39.695388] input: AT Translated Set 2 keyboard as /class/input/input1
[   40.922631] AppArmor: AppArmor initialized<5>audit(1198693830.748:2):  type=1505 info="AppArmor initialized" pid=1247
[   40.939210] fuse init (API version 7.8)
[   40.949008] Failure registering capabilities with primary security module.
[   41.148379] ACPI: Transitioning device [FN00] to D3
[   41.148383] ACPI: Transitioning device [FN00] to D3
[   41.148388] ACPI: Fan [FN00] (off)
[   41.158445] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  83, should be 6E [20070126]
[   41.158459] ACPI: SSDT 3FFC8820, 0CC3 (r1    AMI   CPU1PM        1 INTL 20051117)
[   41.159114] Monitor-Mwait will be used to enter C-1 state
[   41.159119] Monitor-Mwait will be used to enter C-2 state
[   41.159123] Monitor-Mwait will be used to enter C-3 state
[   41.159130] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   41.159138] ACPI: Processor [CPU1] (supports 8 throttling states)
[   41.159215] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  3B, should be 01 [20070126]
[   41.159224] ACPI: SSDT 3FFC94F0, 04A4 (r1    AMI   CPU2PM        1 INTL 20051117)
[   41.178317] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   41.178327] ACPI: Processor [CPU2] (supports 8 throttling states)
[    4.428000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.432000] Time: acpi_pm clocksource has been installed.
[    4.436000] ACPI: Thermal Zone [THRM] (45 C)
[    5.360000] usbcore: registered new interface driver usbfs
[    5.360000] usbcore: registered new interface driver hub
[    5.360000] usbcore: registered new device driver usb
[    5.360000] USB Universal Host Controller Interface driver v3.0
[    5.360000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    5.360000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    5.360000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.360000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    5.360000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ec00
[    5.360000] usb usb1: configuration #1 chosen from 1 choice
[    5.360000] hub 1-0:1.0: USB hub found
[    5.360000] hub 1-0:1.0: 2 ports detected
[    5.464000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[    5.464000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    5.464000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.464000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    5.464000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e880
[    5.464000] usb usb2: configuration #1 chosen from 1 choice
[    5.464000] hub 2-0:1.0: USB hub found
[    5.464000] hub 2-0:1.0: 2 ports detected
[    5.552000] SCSI subsystem initialized
[    5.560000] libata version 2.21 loaded.
[    5.568000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 20 (level, low) -> IRQ 20
[    5.568000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    5.568000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.568000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    5.568000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e800
[    5.568000] usb usb3: configuration #1 chosen from 1 choice
[    5.568000] hub 3-0:1.0: USB hub found
[    5.568000] hub 3-0:1.0: 2 ports detected
[    5.672000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 22 (level, low) -> IRQ 21
[    5.672000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    5.672000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    5.672000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    5.672000] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000e480
[    5.672000] usb usb4: configuration #1 chosen from 1 choice
[    5.672000] hub 4-0:1.0: USB hub found
[    5.672000] hub 4-0:1.0: 2 ports detected
[    5.704000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    5.776000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    5.776000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 17
[    5.776000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    5.776000] eth0: RTL8168b/8111b at 0xf88b8000, 00:18:f3:5f:34:1c, XID 38000000 IRQ 17
[    5.776000] ata_piix 0000:00:1f.2: version 2.11
[    5.776000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    5.776000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[    5.776000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.776000] scsi0 : ata_piix
[    5.776000] scsi1 : ata_piix
[    5.776000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    5.776000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    5.876000] usb 1-1: configuration #1 chosen from 1 choice
[    5.940000] ata1.00: ATA-7: FUJITSU MHV2120BH PL, 00000029, max UDMA/100
[    5.940000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.956000] ata1.00: configured for UDMA/100
[    6.128000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    6.276000] ata2.01: ATAPI: MATSHITADVD-RAM UJ-850S, 1.21, max UDMA/33
[    6.364000] usb 2-1: configuration #1 chosen from 1 choice
[    6.448000] ata2.01: configured for UDMA/33
[    6.448000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120B 0000 PQ: 0 ANSI: 5
[    6.448000] scsi 1:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.21 PQ: 0 ANSI: 5
[    6.448000] ACPI: PCI Interrupt 0000:06:00.0[B] -> GSI 17 (level, low) -> IRQ 22
[    6.504000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    6.508000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    6.508000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    6.508000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.508000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    6.508000] ehci_hcd 0000:00:1d.7: debug port 1
[    6.508000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    6.508000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
[    6.512000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.512000] usb usb5: configuration #1 chosen from 1 choice
[    6.512000] hub 5-0:1.0: USB hub found
[    6.512000] hub 5-0:1.0: 8 ports detected
[    6.524000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.524000] sd 0:0:0:0: [sda] Write Protect is off
[    6.524000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.524000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.524000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.524000] sd 0:0:0:0: [sda] Write Protect is off
[    6.524000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.524000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.524000]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    6.648000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.656000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.656000] Uniform CD-ROM driver Revision: 3.20
[    6.656000] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    6.656000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.656000] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    6.660000] usb 2-1: USB disconnect, address 2
[    7.096000] Attempting manual resume
[    7.096000] swsusp: Resume From Partition 8:7
[    7.096000] PM: Checking swsusp image.
[    7.096000] PM: Resume from disk failed.
[    7.152000] kjournald starting.  Commit interval 5 seconds
[    7.152000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.452000] usb 5-4: new high speed USB device using ehci_hcd and address 4
[    7.592000] usb 5-4: configuration #1 chosen from 1 choice
[    7.592000] usb 1-1: USB disconnect, address 2
[    7.592000] usbcore: registered new interface driver hiddev
[    7.780000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800036aa699]
[    7.832000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[    8.004000] usb 1-1: configuration #1 chosen from 1 choice
[    8.256000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[    8.500000] usb 2-1: configuration #1 chosen from 1 choice
[    8.516000] input: A4Tech PS/2+USB Mouse as /class/input/input2
[    8.516000] input: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1d.0-1
[    8.516000] usbcore: registered new interface driver usbhid
[    8.516000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   15.188000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.192000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.348000] iTCO_vendor_support: vendor-support=0
[   15.348000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   15.348000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   15.348000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.360000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.928000] intel_rng: FWH not detected
[   16.260000] input: PC Speaker as /class/input/input3
[   16.468000] ieee80211_crypt: registered algorithm 'NULL'
[   16.580000] sdhci: Secure Digital Host Controller Interface driver
[   16.580000] sdhci: Copyright(c) Pierre Ossman
[   16.580000] sdhci: SDHCI controller found at 0000:06:00.1 [1180:0822] (rev 19)
[   16.580000] ACPI: PCI Interrupt 0000:06:00.1[B] -> GSI 17 (level, low) -> IRQ 22
[   16.580000] mmc0: SDHCI at 0xfeaff400 irq 22 DMA
[   16.592000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04713/0x200000
[   16.592000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.592000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.628000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   16.744000] Bluetooth: Core ver 2.11
[   16.744000] NET: Registered protocol family 31
[   16.744000] Bluetooth: HCI device and connection manager initialized
[   16.744000] Bluetooth: HCI socket layer initialized
[   16.764000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   16.764000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   16.764000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.764000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   16.776000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.784000] Linux video capture interface: v2.00
[   16.836000] irda_init()
[   16.836000] NET: Registered protocol family 23
[   16.888000] Bluetooth: HCI USB driver ver 2.9
[   16.888000] usbcore: registered new interface driver hci_usb
[   16.920000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
[   16.936000] found SMC SuperIO Chip (devid=0x7a rev=01 base=0x002e): LPC47N227
[   16.936000] smsc_superio_flat(): fir: 0x6f8, sir: 0x2f8, dma: 15, irq: 3, mode: 0x0e
[   16.936000] smsc_ircc_present: can't get sir_base of 0x2f8
[   17.140000] usbcore: registered new interface driver gspca
[   17.140000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   17.196000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 23
[   17.196000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.784000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   18.792000] hda_intel: azx_get_response timeout, switching to polling mode...
[   18.804000] lp: driver loaded but no devices found
[   19.012000] Adding 999912k swap on /dev/sda7.  Priority:-1 extents:1 across:999912k
[   19.664000] EXT3 FS on sda6, internal journal
[   23.232000] ACPI: Battery Slot [BAT0] (battery present)
[   23.448000] input: Power Button (FF) as /class/input/input5
[   23.448000] ACPI: Power Button (FF) [PWRF]
[   23.492000] input: Lid Switch as /class/input/input6
[   23.492000] ACPI: Lid Switch [LID]
[   23.492000] input: Power Button (CM) as /class/input/input7
[   23.492000] ACPI: Power Button (CM) [PWRB]
[   23.504000] input: Sleep Button (CM) as /class/input/input8
[   23.504000] ACPI: Sleep Button (CM) [SLPB]
[   23.592000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   23.628000] No dock devices found.
[   24.000000] Asus Laptop ACPI Extras version 0.30
[   24.000000]   unsupported model A8JP, trying default values
[   24.000000]   send /proc/acpi/dsdt to the developers
[   24.036000] ACPI: AC Adapter [AC0] (off-line)
[   26.028000] r8169: eth0: link down
[   26.196000] NET: Registered protocol family 10
[   26.196000] lo: Disabled Privacy Extensions
[   26.196000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.196000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   26.572000] ppdev: user-space parallel port driver
[   26.820000] audit(1198690254.179:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5204 profile="/usr/sbin/cupsd"
[   26.884000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   26.884000] apm: disabled - APM is not SMP safe.
[   27.340000] Failure registering capabilities with primary security module.
[   27.524000] Bluetooth: L2CAP ver 2.8
[   27.524000] Bluetooth: L2CAP socket layer initialized
[   27.632000] Bluetooth: RFCOMM socket layer initialized
[   27.632000] Bluetooth: RFCOMM TTY layer initialized
[   27.632000] Bluetooth: RFCOMM ver 1.8
[   39.420000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   39.424000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[   39.424000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   39.476000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.644000] [fglrx:firegl_unlock] *ERROR* Process 5512 using kernel context 0
[   41.652000] mtrr: no more MTRRs available
[   41.652000] mtrr: no more MTRRs available
[   41.652000] mtrr: no more MTRRs available
[   41.652000] mtrr: no more MTRRs available
[   42.772000] Clocksource tsc unstable (delta = -449071013 ns)
[   65.072000] NET: Registered protocol family 17
[   68.640000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[   68.748000] ieee80211_crypt: registered algorithm 'WEP'
[   69.020000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   69.036000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[   69.036000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[   69.036000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[   69.036000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[   69.036000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[   69.036000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
[   90.012000] eth1: no IPv6 routers present

```

[COLOR="Red"][SIZE="6"]*HELP PLEASE*[/SIZE][/COLOR]

---

