---
title: "What is causing lockups? (8.04)"
date: 2008-05-09
forum: General Help
---

### Post by lordgreg on 2008-05-09
hi,

i really don't have any more clue on what to do or where to search, so i've posted new thread here:

- i've updated from 7.10 to 8.04 without any problems at all (the only warning was replacing or leaving the samba config file)

- on first reboot, everything looked perfect. it started to work "out of the box". so i was surprised to be honest.

- after few days of using ubuntu and after few days of successfully installed updates (updates manager), something went wrong.

- daily, i've been having this strange lock-ups of firefox & gnome terminal window. firefox crashes, then i force it to quit (i want to use kill command in terminal), but as soon as i open terminal window, it just locks, so the only thing here to do is CTRL+ALT+F1 to switch to another terminal and do it from there.

- now, even if i login from another screen and kill firefox and terminal processes, that doesn't fix anything. so i switch back to CTRL+ALT+F7. menus work, i can even run update manager at that time and do all updates,

- but what bothers me is, that, i tried to reboot gnome with CTRL+BACKSPACE, which locks up after successful login so

- all i can do after that is reboot. and i mean sudo reboot now. since, this is happening more than once every day, can someone tell me what is causing this and how to fix it?

I have somehow common computer, core 2 duo cpu, asus p5b motherboard, 2gb of ram, 320gb of hdd and geforce 7300GT. oh, the ubuntu is 32bit.

Please help me finding the way out of this problem, it's driving me nuts!

Thank you!


-Gregor

---

### Post by lptr on 2008-05-09
Hi Gregor

what is /var/log/messages telling you?

rob*

---

### Post by lordgreg on 2008-05-09
Hi Rob,

this is today's part of the log:

```
May  9 06:33:13 gpbox -- MARK --
May  9 06:53:13 gpbox -- MARK --
May  9 07:04:48 gpbox pulseaudio[5941]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 07:33:13 gpbox -- MARK --
May  9 07:53:13 gpbox -- MARK --
May  9 07:56:55 gpbox kernel: [90082.949683] nfsd: last server has exited
May  9 07:56:55 gpbox kernel: [90082.949686] nfsd: unexporting all filesystems
May  9 07:56:56 gpbox kernel: [90084.015739] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
May  9 07:56:56 gpbox kernel: [90084.015762] NFSD: starting 90-second grace period
May  9 07:59:15 gpbox kernel: [90222.562426] compiz.real[6032]: segfault at 04320183 eip 08055a80 esp bfc60060 error 4
May  9 07:59:19 gpbox syslogd 1.5.0#1ubuntu1: restart.
May  9 08:01:03 gpbox kernel: [90330.601677] ip6_tables: (C) 2000-2006 Netfilter Core Team
May  9 08:01:04 gpbox kernel: [90331.738232] nfsd: last server has exited
May  9 08:01:04 gpbox kernel: [90331.738235] nfsd: unexporting all filesystems
May  9 08:01:04 gpbox exiting on signal 15
May  9 08:01:54 gpbox syslogd 1.5.0#1ubuntu1: restart.
May  9 08:01:54 gpbox kernel: Inspecting /boot/System.map-2.6.24-17-generic
May  9 08:01:54 gpbox kernel: Loaded 27880 symbols from /boot/System.map-2.6.24-17-generic.
May  9 08:01:54 gpbox kernel: Symbols match kernel version 2.6.24.
May  9 08:01:54 gpbox kernel: Loaded 29716 symbols from 83 modules.
May  9 08:01:54 gpbox kernel: [    0.000000] Initializing cgroup subsys cpuset
May  9 08:01:54 gpbox kernel: [    0.000000] Initializing cgroup subsys cpu
May  9 08:01:54 gpbox kernel: [    0.000000] Linux version 2.6.24-17-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu May 1 14:31:33 UTC 2008 (Ubuntu 2.6.24-17.31-generic)
May  9 08:01:54 gpbox kernel: [    0.000000] BIOS-provided physical RAM map:
May  9 08:01:54 gpbox kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May  9 08:01:54 gpbox kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May  9 08:01:54 gpbox kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
May  9 08:01:54 gpbox kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffa0000 (usable)
May  9 08:01:54 gpbox kernel: [    0.000000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
May  9 08:01:54 gpbox kernel: [    0.000000]  BIOS-e820: 000000007ffae000 - 000000007ffe0000 (ACPI NVS)
May  9 08:01:54 gpbox kernel: [    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
May  9 08:01:54 gpbox kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  9 08:01:54 gpbox kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
May  9 08:01:54 gpbox kernel: [    0.000000] 1151MB HIGHMEM available.
May  9 08:01:54 gpbox kernel: [    0.000000] 896MB LOWMEM available.
May  9 08:01:54 gpbox kernel: [    0.000000] found SMP MP-table at 000ff780
May  9 08:01:54 gpbox kernel: [    0.000000] Zone PFN ranges:
May  9 08:01:54 gpbox kernel: [    0.000000]   DMA             0 ->     4096
May  9 08:01:54 gpbox kernel: [    0.000000]   Normal       4096 ->   229376
May  9 08:01:54 gpbox kernel: [    0.000000]   HighMem    229376 ->   524192
May  9 08:01:54 gpbox kernel: [    0.000000] Movable zone start PFN for each node
May  9 08:01:54 gpbox kernel: [    0.000000] early_node_map[1] active PFN ranges
May  9 08:01:54 gpbox kernel: [    0.000000]     0:        0 ->   524192
May  9 08:01:54 gpbox kernel: [    0.000000] DMI 2.4 present.
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FAE40 checksum 0
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: RSDP 000FAE40, 0014 (r0 ACPIAM)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: RSDT 7FFA0000, 0038 (r1 A M I  OEMRSDT   9000629 MSFT       97)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: FACP 7FFA0200, 0084 (r2 A M I  OEMFACP   9000629 MSFT       97)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: DSDT 7FFA0440, 8926 (r1  A0483 A0483035       35 INTL 20060113)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: FACS 7FFAE000, 0040
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: APIC 7FFA0390, 006C (r1 A M I  OEMAPIC   9000629 MSFT       97)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: MCFG 7FFA0400, 003C (r1 A M I  OEMMCFG   9000629 MSFT       97)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: OEMB 7FFAE040, 007B (r1 A M I  AMI_OEM   9000629 MSFT       97)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: HPET 7FFA8D70, 0038 (r1 A M I  OEMHPET   9000629 MSFT       97)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May  9 08:01:54 gpbox kernel: [    0.000000] Processor #0 6:15 APIC version 20
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
May  9 08:01:54 gpbox kernel: [    0.000000] Processor #1 6:15 APIC version 20
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  9 08:01:54 gpbox kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  9 08:01:54 gpbox kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  9 08:01:54 gpbox kernel: [    0.000000] ACPI: HPET id: 0x8086a202 base: 0xfed00000
May  9 08:01:54 gpbox kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  9 08:01:54 gpbox kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
May  9 08:01:54 gpbox kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May  9 08:01:54 gpbox kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
May  9 08:01:54 gpbox kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
May  9 08:01:54 gpbox kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520097
May  9 08:01:54 gpbox kernel: [    0.000000] Kernel command line: root=UUID=e85b6cd0-93f8-45fc-9c46-9c264d437ced ro quiet splash
May  9 08:01:54 gpbox kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  9 08:01:54 gpbox kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  9 08:01:54 gpbox kernel: [    0.000000] Initializing CPU#0
May  9 08:01:54 gpbox kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  9 08:01:54 gpbox kernel: [    0.000000] Detected 2133.359 MHz processor.
May  9 08:01:54 gpbox kernel: [   19.213841] Console: colour VGA+ 80x25
May  9 08:01:54 gpbox kernel: [   19.213843] console [tty0] enabled
May  9 08:01:54 gpbox kernel: [   19.214014] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  9 08:01:54 gpbox kernel: [   19.214283] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  9 08:01:54 gpbox kernel: [   19.288354] Memory: 2066688k/2096768k available (2176k kernel code, 28808k reserved, 1007k data, 368k init, 1179264k highmem)
May  9 08:01:54 gpbox kernel: [   19.288359] virtual kernel memory layout:
May  9 08:01:54 gpbox kernel: [   19.288360]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May  9 08:01:54 gpbox kernel: [   19.288361]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May  9 08:01:54 gpbox kernel: [   19.288362]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
May  9 08:01:54 gpbox kernel: [   19.288363]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
May  9 08:01:54 gpbox kernel: [   19.288364]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
May  9 08:01:54 gpbox kernel: [   19.288365]       .data : 0xc0320134 - 0xc041bdc4   (1007 kB)
May  9 08:01:54 gpbox kernel: [   19.288365]       .text : 0xc0100000 - 0xc0320134   (2176 kB)
May  9 08:01:54 gpbox kernel: [   19.288368] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May  9 08:01:54 gpbox kernel: [   19.288401] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
May  9 08:01:54 gpbox kernel: [   19.368352] Calibrating delay using timer specific routine.. 4269.80 BogoMIPS (lpj=8539608)
May  9 08:01:54 gpbox kernel: [   19.368368] Security Framework initialized
May  9 08:01:54 gpbox kernel: [   19.368373] SELinux:  Disabled at boot.
May  9 08:01:54 gpbox kernel: [   19.368383] AppArmor: AppArmor initialized
May  9 08:01:54 gpbox kernel: [   19.368387] Failure registering capabilities with primary security module.
May  9 08:01:54 gpbox kernel: [   19.368393] Mount-cache hash table entries: 512
May  9 08:01:54 gpbox kernel: [   19.368489] Initializing cgroup subsys ns
May  9 08:01:54 gpbox kernel: [   19.368492] Initializing cgroup subsys cpuacct
May  9 08:01:54 gpbox kernel: [   19.368506] monitor/mwait feature present.
May  9 08:01:54 gpbox kernel: [   19.368507] using mwait in idle threads.
May  9 08:01:54 gpbox kernel: [   19.368510] CPU: L1 I cache: 32K, L1 D cache: 32K
May  9 08:01:54 gpbox kernel: [   19.368512] CPU: L2 cache: 2048K
May  9 08:01:54 gpbox kernel: [   19.368514] CPU: Physical Processor ID: 0
May  9 08:01:54 gpbox kernel: [   19.368515] CPU: Processor Core ID: 0
May  9 08:01:54 gpbox kernel: [   19.368524] Compat vDSO mapped to ffffe000.
May  9 08:01:54 gpbox kernel: [   19.368534] Checking 'hlt' instruction... OK.
May  9 08:01:54 gpbox kernel: [   19.384687] SMP alternatives: switching to UP code
May  9 08:01:54 gpbox kernel: [   19.385981] Early unpacking initramfs... done
May  9 08:01:54 gpbox kernel: [   19.654726] ACPI: Core revision 20070126
May  9 08:01:54 gpbox kernel: [   19.654767] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May  9 08:01:54 gpbox kernel: [   19.676355] CPU0: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
May  9 08:01:54 gpbox kernel: [   19.676369] SMP alternatives: switching to SMP code
May  9 08:01:54 gpbox kernel: [   19.676947] Booting processor 1/1 eip 3000
May  9 08:01:54 gpbox kernel: [   19.687052] Initializing CPU#1
May  9 08:01:54 gpbox kernel: [   19.767511] Calibrating delay using timer specific routine.. 4266.67 BogoMIPS (lpj=8533356)
May  9 08:01:54 gpbox kernel: [   19.767521] monitor/mwait feature present.
May  9 08:01:54 gpbox kernel: [   19.767523] CPU: L1 I cache: 32K, L1 D cache: 32K
May  9 08:01:54 gpbox kernel: [   19.767525] CPU: L2 cache: 2048K
May  9 08:01:54 gpbox kernel: [   19.767526] CPU: Physical Processor ID: 0
May  9 08:01:54 gpbox kernel: [   19.767527] CPU: Processor Core ID: 1
May  9 08:01:54 gpbox kernel: [   19.767962] CPU1: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
May  9 08:01:54 gpbox kernel: [   19.767978] Total of 2 processors activated (8536.48 BogoMIPS).
May  9 08:01:54 gpbox kernel: [   19.768116] ENABLING IO-APIC IRQs
May  9 08:01:54 gpbox kernel: [   19.768274] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May  9 08:01:54 gpbox kernel: [   19.915285] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
May  9 08:01:54 gpbox kernel: [   19.935256] Brought up 2 CPUs
May  9 08:01:54 gpbox kernel: [   19.935461] net_namespace: 64 bytes
May  9 08:01:54 gpbox kernel: [   19.935469] Booting paravirtualized kernel on bare hardware
May  9 08:01:54 gpbox kernel: [   19.935827] Time:  6:01:34  Date: 05/09/08
May  9 08:01:54 gpbox kernel: [   19.935848] NET: Registered protocol family 16
May  9 08:01:54 gpbox kernel: [   19.936005] EISA bus registered
May  9 08:01:54 gpbox kernel: [   19.936009] ACPI: bus type pci registered
May  9 08:01:54 gpbox kernel: [   19.936176] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
May  9 08:01:54 gpbox kernel: [   19.936178] PCI: Using configuration type 1
May  9 08:01:54 gpbox kernel: [   19.936179] Setting up standard PCI resources
May  9 08:01:54 gpbox kernel: [   19.949413] ACPI: Interpreter enabled
May  9 08:01:54 gpbox kernel: [   19.949415] ACPI: (supports S0 S1 S3 S4 S5)
May  9 08:01:54 gpbox kernel: [   19.949428] ACPI: Using IOAPIC for interrupt routing
May  9 08:01:54 gpbox kernel: [   19.956010] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  9 08:01:54 gpbox kernel: [   19.956603] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
May  9 08:01:54 gpbox kernel: [   19.956607] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
May  9 08:01:54 gpbox kernel: [   19.957405] PCI: Transparent bridge - 0000:00:1e.0
May  9 08:01:54 gpbox kernel: [   19.970377] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
May  9 08:01:54 gpbox kernel: [   19.970483] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
May  9 08:01:54 gpbox kernel: [   19.970586] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
May  9 08:01:54 gpbox kernel: [   19.970690] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
May  9 08:01:54 gpbox kernel: [   19.970793] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
May  9 08:01:54 gpbox kernel: [   19.970897] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
May  9 08:01:54 gpbox kernel: [   19.971000] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
May  9 08:01:54 gpbox kernel: [   19.971103] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
May  9 08:01:54 gpbox kernel: [   19.971213] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  79, should be 70 [20070126]
May  9 08:01:54 gpbox kernel: [   19.971219] Linux Plug and Play Support v0.97 (c) Adam Belay
May  9 08:01:54 gpbox kernel: [   19.971243] pnp: PnP ACPI init
May  9 08:01:54 gpbox kernel: [   19.971249] ACPI: bus type pnp registered
May  9 08:01:54 gpbox kernel: [   19.973842] pnp: PnP ACPI: found 16 devices
May  9 08:01:54 gpbox kernel: [   19.973844] ACPI: ACPI bus type pnp unregistered
May  9 08:01:54 gpbox kernel: [   19.973847] PnPBIOS: Disabled by ACPI PNP
May  9 08:01:54 gpbox kernel: [   19.974030] PCI: Using ACPI for IRQ routing
May  9 08:01:54 gpbox kernel: [   19.974032] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May  9 08:01:54 gpbox kernel: [   20.011143] NET: Registered protocol family 8
May  9 08:01:54 gpbox kernel: [   20.011145] NET: Registered protocol family 20
May  9 08:01:54 gpbox kernel: [   20.011178] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
May  9 08:01:54 gpbox kernel: [   20.011182] hpet0: 3 64-bit timers, 14318180 Hz
May  9 08:01:54 gpbox kernel: [   20.012207] AppArmor: AppArmor Filesystem Enabled
May  9 08:01:54 gpbox kernel: [   20.015148] Time: tsc clocksource has been installed.
May  9 08:01:54 gpbox kernel: [   20.031161] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
May  9 08:01:54 gpbox kernel: [   20.031173] system 00:08: ioport range 0x290-0x297 has been reserved
May  9 08:01:54 gpbox kernel: [   20.031179] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
May  9 08:01:54 gpbox kernel: [   20.031182] system 00:09: ioport range 0x800-0x87f has been reserved
May  9 08:01:54 gpbox kernel: [   20.031185] system 00:09: ioport range 0x480-0x4bf has been reserved
May  9 08:01:54 gpbox kernel: [   20.031188] system 00:09: iomem range 0xffafe000-0xffb0cbff could not be reserved
May  9 08:01:54 gpbox kernel: [   20.031191] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
May  9 08:01:54 gpbox kernel: [   20.031194] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
May  9 08:01:54 gpbox kernel: [   20.031197] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
May  9 08:01:54 gpbox kernel: [   20.031200] system 00:09: iomem range 0xfff00000-0xfffffffe could not be reserved
May  9 08:01:54 gpbox kernel: [   20.031207] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
May  9 08:01:54 gpbox kernel: [   20.031210] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
May  9 08:01:54 gpbox kernel: [   20.031217] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
May  9 08:01:54 gpbox kernel: [   20.031224] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
May  9 08:01:54 gpbox kernel: [   20.031227] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
May  9 08:01:54 gpbox kernel: [   20.031229] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
May  9 08:01:54 gpbox kernel: [   20.031232] system 00:0f: iomem range 0x100000-0x7fffffff could not be reserved
May  9 08:01:54 gpbox kernel: [   20.031235] system 00:0f: iomem range 0x0-0x0 could not be reserved
May  9 08:01:54 gpbox kernel: [   20.061570] PCI: Bridge: 0000:00:01.0
May  9 08:01:54 gpbox kernel: [   20.061572]   IO window: 8000-8fff
May  9 08:01:54 gpbox kernel: [   20.061575]   MEM window: fa700000-fe7fffff
May  9 08:01:54 gpbox kernel: [   20.061577]   PREFETCH window: bfe00000-dfdfffff
May  9 08:01:54 gpbox kernel: [   20.061580] PCI: Bridge: 0000:00:1c.0
May  9 08:01:54 gpbox kernel: [   20.061581]   IO window: disabled.
May  9 08:01:54 gpbox kernel: [   20.061584]   MEM window: disabled.
May  9 08:01:54 gpbox kernel: [   20.061587]   PREFETCH window: dfe00000-dfefffff
May  9 08:01:54 gpbox kernel: [   20.061591] PCI: Bridge: 0000:00:1c.4
May  9 08:01:54 gpbox kernel: [   20.061593]   IO window: a000-afff
May  9 08:01:54 gpbox kernel: [   20.061597]   MEM window: fe900000-fe9fffff
May  9 08:01:54 gpbox kernel: [   20.061599]   PREFETCH window: disabled.
May  9 08:01:54 gpbox kernel: [   20.061603] PCI: Bridge: 0000:00:1c.5
May  9 08:01:54 gpbox kernel: [   20.061605]   IO window: 9000-9fff
May  9 08:01:54 gpbox kernel: [   20.061608]   MEM window: fe800000-fe8fffff
May  9 08:01:54 gpbox kernel: [   20.061611]   PREFETCH window: disabled.
May  9 08:01:54 gpbox kernel: [   20.061615] PCI: Bridge: 0000:00:1e.0
May  9 08:01:54 gpbox kernel: [   20.061617]   IO window: b000-bfff
May  9 08:01:54 gpbox kernel: [   20.061621]   MEM window: fea00000-feafffff
May  9 08:01:54 gpbox kernel: [   20.061624]   PREFETCH window: disabled.
May  9 08:01:54 gpbox kernel: [   20.061636] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
May  9 08:01:54 gpbox kernel: [   20.061654] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
May  9 08:01:54 gpbox kernel: [   20.061672] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
May  9 08:01:54 gpbox kernel: [   20.061690] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
May  9 08:01:54 gpbox kernel: [   20.061710] NET: Registered protocol family 2
May  9 08:01:54 gpbox kernel: [   20.099033] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  9 08:01:54 gpbox kernel: [   20.099252] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  9 08:01:54 gpbox kernel: [   20.099580] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  9 08:01:54 gpbox kernel: [   20.099746] TCP: Hash tables configured (established 131072 bind 65536)
May  9 08:01:54 gpbox kernel: [   20.099748] TCP reno registered
May  9 08:01:54 gpbox kernel: [   20.111075] checking if image is initramfs... it is
May  9 08:01:54 gpbox kernel: [   20.641567] Freeing initrd memory: 7422k freed
May  9 08:01:54 gpbox kernel: [   20.642195] audit: initializing netlink socket (disabled)
May  9 08:01:54 gpbox kernel: [   20.642205] audit(1210312894.213:1): initialized
May  9 08:01:54 gpbox kernel: [   20.642371] highmem bounce pool size: 64 pages
May  9 08:01:54 gpbox kernel: [   20.643967] VFS: Disk quotas dquot_6.5.1
May  9 08:01:54 gpbox kernel: [   20.644026] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  9 08:01:54 gpbox kernel: [   20.644131] io scheduler noop registered
May  9 08:01:54 gpbox kernel: [   20.644133] io scheduler anticipatory registered
May  9 08:01:54 gpbox kernel: [   20.644134] io scheduler deadline registered
May  9 08:01:54 gpbox kernel: [   20.644143] io scheduler cfq registered (default)
May  9 08:01:54 gpbox kernel: [   20.644357] assign_interrupt_mode Found MSI capability
May  9 08:01:54 gpbox kernel: [   20.644476] assign_interrupt_mode Found MSI capability
May  9 08:01:54 gpbox kernel: [   20.644628] assign_interrupt_mode Found MSI capability
May  9 08:01:54 gpbox kernel: [   20.644781] assign_interrupt_mode Found MSI capability
May  9 08:01:54 gpbox kernel: [   20.645030] isapnp: Scanning for PnP cards...
May  9 08:01:54 gpbox kernel: [   20.997375] isapnp: No Plug & Play device found
May  9 08:01:54 gpbox kernel: [   21.017478] Real Time Clock Driver v1.12ac
May  9 08:01:54 gpbox kernel: [   21.017654] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May  9 08:01:54 gpbox kernel: [   21.017758] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  9 08:01:54 gpbox kernel: [   21.018488] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  9 08:01:54 gpbox kernel: [   21.019142] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May  9 08:01:54 gpbox kernel: [   21.019196] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  9 08:01:54 gpbox kernel: [   21.019278] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
May  9 08:01:54 gpbox kernel: [   21.021957] serio: i8042 KBD port at 0x60,0x64 irq 1
May  9 08:01:54 gpbox kernel: [   21.021961] serio: i8042 AUX port at 0x60,0x64 irq 12
May  9 08:01:54 gpbox kernel: [   21.037277] mice: PS/2 mouse device common for all mice
May  9 08:01:54 gpbox kernel: [   21.037367] EISA: Probing bus 0 at eisa.0
May  9 08:01:54 gpbox kernel: [   21.037389] Cannot allocate resource for EISA slot 8
May  9 08:01:54 gpbox kernel: [   21.037391] EISA: Detected 0 cards.
May  9 08:01:54 gpbox kernel: [   21.037393] cpuidle: using governor ladder
May  9 08:01:54 gpbox kernel: [   21.037394] cpuidle: using governor menu
May  9 08:01:54 gpbox kernel: [   21.037456] NET: Registered protocol family 1
May  9 08:01:54 gpbox kernel: [   21.037477] Using IPI No-Shortcut mode
May  9 08:01:54 gpbox kernel: [   21.037499] registered taskstats version 1
May  9 08:01:54 gpbox kernel: [   21.037599]   Magic number: 8:264:13
May  9 08:01:54 gpbox kernel: [   21.037603]   hash matches device ttyca
May  9 08:01:54 gpbox kernel: [   21.037640] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  9 08:01:54 gpbox kernel: [   21.037642] EDD information not available.
May  9 08:01:54 gpbox kernel: [   21.037763] Freeing unused kernel memory: 368k freed
May  9 08:01:54 gpbox kernel: [   21.055040] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  9 08:01:54 gpbox kernel: [   22.207929] fuse init (API version 7.9)
May  9 08:01:54 gpbox kernel: [   22.225062] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  34, should be 3B [20070126]
May  9 08:01:54 gpbox kernel: [   22.225067] ACPI: SSDT 7FFA8DB0, 02E3 (r1    AMI   CPU1PM        1 INTL 20060113)
May  9 08:01:54 gpbox kernel: [   22.225290] ACPI: SSDT 7FFA90A0, 02DA (r1    AMI   CPU2PM        1 INTL 20060113)
May  9 08:01:54 gpbox kernel: [   22.225466] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
May  9 08:01:54 gpbox kernel: [   22.225475] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
May  9 08:01:54 gpbox kernel: [   22.367254] usbcore: registered new interface driver usbfs
May  9 08:01:54 gpbox kernel: [   22.367274] usbcore: registered new interface driver hub
May  9 08:01:54 gpbox kernel: [   22.367936] usbcore: registered new device driver usb
May  9 08:01:54 gpbox kernel: [   22.369079] USB Universal Host Controller Interface driver v3.0
May  9 08:01:54 gpbox kernel: [   22.369118] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
May  9 08:01:54 gpbox kernel: [   22.369130] uhci_hcd 0000:00:1a.0: UHCI Host Controller
May  9 08:01:54 gpbox kernel: [   22.369308] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
May  9 08:01:54 gpbox kernel: [   22.369333] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000dc00
May  9 08:01:54 gpbox kernel: [   22.369441] usb usb1: configuration #1 chosen from 1 choice
May  9 08:01:54 gpbox kernel: [   22.369461] hub 1-0:1.0: USB hub found
May  9 08:01:54 gpbox kernel: [   22.369465] hub 1-0:1.0: 2 ports detected
May  9 08:01:54 gpbox kernel: [   22.469984] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 17
May  9 08:01:54 gpbox kernel: [   22.469997] uhci_hcd 0000:00:1a.1: UHCI Host Controller
May  9 08:01:54 gpbox kernel: [   22.470015] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
May  9 08:01:54 gpbox kernel: [   22.470039] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000e000
May  9 08:01:54 gpbox kernel: [   22.470125] usb usb2: configuration #1 chosen from 1 choice
May  9 08:01:54 gpbox kernel: [   22.470144] hub 2-0:1.0: USB hub found
May  9 08:01:54 gpbox kernel: [   22.470148] hub 2-0:1.0: 2 ports detected
May  9 08:01:54 gpbox kernel: [   22.563415] SCSI subsystem initialized
May  9 08:01:54 gpbox kernel: [   22.573768] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
May  9 08:01:54 gpbox kernel: [   22.573780] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May  9 08:01:54 gpbox kernel: [   22.573799] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
May  9 08:01:54 gpbox kernel: [   22.573822] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000d480
May  9 08:01:54 gpbox kernel: [   22.573913] usb usb3: configuration #1 chosen from 1 choice
May  9 08:01:54 gpbox kernel: [   22.573933] hub 3-0:1.0: USB hub found
May  9 08:01:54 gpbox kernel: [   22.573937] hub 3-0:1.0: 2 ports detected
May  9 08:01:54 gpbox kernel: [   22.645173] Floppy drive(s): fd0 is 1.44M
May  9 08:01:54 gpbox kernel: [   22.665148] FDC 0 is a post-1991 82077
May  9 08:01:54 gpbox kernel: [   22.677567] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
May  9 08:01:54 gpbox kernel: [   22.677580] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May  9 08:01:54 gpbox kernel: [   22.677599] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
May  9 08:01:54 gpbox kernel: [   22.677622] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
May  9 08:01:54 gpbox kernel: [   22.677713] usb usb4: configuration #1 chosen from 1 choice
May  9 08:01:54 gpbox kernel: [   22.677733] hub 4-0:1.0: USB hub found
May  9 08:01:54 gpbox kernel: [   22.677736] hub 4-0:1.0: 2 ports detected
May  9 08:01:54 gpbox kernel: [   22.781328] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
May  9 08:01:54 gpbox kernel: [   22.781341] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May  9 08:01:54 gpbox kernel: [   22.781362] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
May  9 08:01:54 gpbox kernel: [   22.781385] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000d880
May  9 08:01:54 gpbox kernel: [   22.781478] usb usb5: configuration #1 chosen from 1 choice
May  9 08:01:54 gpbox kernel: [   22.781497] hub 5-0:1.0: USB hub found
May  9 08:01:54 gpbox kernel: [   22.781501] hub 5-0:1.0: 2 ports detected
May  9 08:01:54 gpbox kernel: [   22.885216] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
May  9 08:01:54 gpbox kernel: [   22.885231] ehci_hcd 0000:00:1a.7: EHCI Host Controller
May  9 08:01:54 gpbox kernel: [   22.885252] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
May  9 08:01:54 gpbox kernel: [   22.889156] ehci_hcd 0000:00:1a.7: debug port 1
May  9 08:01:54 gpbox kernel: [   22.889165] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfebffc00
May  9 08:01:54 gpbox kernel: [   22.905012] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  9 08:01:54 gpbox kernel: [   22.905100] usb usb6: configuration #1 chosen from 1 choice
May  9 08:01:54 gpbox kernel: [   22.905122] hub 6-0:1.0: USB hub found
May  9 08:01:54 gpbox kernel: [   22.905127] hub 6-0:1.0: 4 ports detected
May  9 08:01:54 gpbox kernel: [   23.008888] ACPI: PCI Interrupt 0000:05:03.0[A] -> GSI 21 (level, low) -> IRQ 21
May  9 08:01:54 gpbox kernel: [   23.058498] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
May  9 08:01:54 gpbox kernel: [   23.059298] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
May  9 08:01:54 gpbox kernel: [   23.059321] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
May  9 08:01:54 gpbox kernel: [   23.059389] scsi0 : ata_piix
May  9 08:01:54 gpbox kernel: [   23.060164] scsi1 : ata_piix
May  9 08:01:54 gpbox kernel: [   23.061392] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 19
May  9 08:01:54 gpbox kernel: [   23.061395] ata2: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 19
May  9 08:01:54 gpbox kernel: [   23.245521] ata1.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
May  9 08:01:54 gpbox kernel: [   23.245526] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/1)
May  9 08:01:54 gpbox kernel: [   23.252607] ata1.00: configured for UDMA/133
May  9 08:01:54 gpbox kernel: [   23.418628] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
May  9 08:01:54 gpbox kernel: [   23.418686] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
May  9 08:01:54 gpbox kernel: [   23.418707] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
May  9 08:01:54 gpbox kernel: [   23.418759] scsi2 : ata_piix
May  9 08:01:54 gpbox kernel: [   23.418792] scsi3 : ata_piix
May  9 08:01:54 gpbox kernel: [   23.419577] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 19
May  9 08:01:54 gpbox kernel: [   23.419579] ata4: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 19
May  9 08:01:54 gpbox kernel: [   23.746567] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 19 (level, low) -> IRQ 19
May  9 08:01:54 gpbox kernel: [   23.746597] skge 1.13 addr 0xfeaf4000 irq 19 chip Yukon-Lite rev 9
May  9 08:01:54 gpbox kernel: [   23.746809] skge eth0: addr 00:18:f3:a2:52:07
May  9 08:01:54 gpbox kernel: [   23.746937] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
May  9 08:01:54 gpbox kernel: [   23.746941] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 17 (level, low) -> IRQ 17
May  9 08:01:54 gpbox kernel: [   23.748801] scsi4 : pata_jmicron
May  9 08:01:54 gpbox kernel: [   23.749750] scsi5 : pata_jmicron
May  9 08:01:54 gpbox kernel: [   23.750265] ata5: PATA max UDMA/100 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 17
May  9 08:01:54 gpbox kernel: [   23.750269] ata6: PATA max UDMA/100 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 17
May  9 08:01:54 gpbox kernel: [   24.067112] ata5.00: ATAPI: Optiarc DVD RW AD-7173A, 1-01, max UDMA/66
May  9 08:01:54 gpbox kernel: [   24.238734] ata5.00: configured for UDMA/66
May  9 08:01:54 gpbox kernel: [   24.406078] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7173A  1-01 PQ: 0 ANSI: 5
May  9 08:01:54 gpbox kernel: [   24.406240] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
May  9 08:01:54 gpbox kernel: [   25.407682] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
May  9 08:01:54 gpbox kernel: [   25.407686] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
May  9 08:01:54 gpbox kernel: [   25.407805] scsi6 : ahci
May  9 08:01:54 gpbox kernel: [   25.407986] scsi7 : ahci
May  9 08:01:54 gpbox kernel: [   25.408034] ata7: SATA max UDMA/133 abar m8192@0xfe9fe000 port 0xfe9fe100 irq 16
May  9 08:01:54 gpbox kernel: [   25.408037] ata8: SATA max UDMA/133 abar m8192@0xfe9fe000 port 0xfe9fe180 irq 16
May  9 08:01:54 gpbox kernel: [   25.728018] ata7: SATA link down (SStatus 0 SControl 300)
May  9 08:01:54 gpbox kernel: [   26.046340] ata8: SATA link down (SStatus 0 SControl 300)
May  9 08:01:54 gpbox kernel: [   26.047573] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
May  9 08:01:54 gpbox kernel: [   26.047585] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May  9 08:01:54 gpbox kernel: [   26.047608] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
May  9 08:01:54 gpbox kernel: [   26.051516] ehci_hcd 0000:00:1d.7: debug port 1
May  9 08:01:54 gpbox kernel: [   26.051526] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfebff800
May  9 08:01:54 gpbox kernel: [   26.070275] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  9 08:01:54 gpbox kernel: [   26.070391] usb usb7: configuration #1 chosen from 1 choice
May  9 08:01:54 gpbox kernel: [   26.070417] hub 7-0:1.0: USB hub found
May  9 08:01:54 gpbox kernel: [   26.070423] hub 7-0:1.0: 6 ports detected
May  9 08:01:54 gpbox kernel: [   26.178422] Driver 'sd' needs updating - please use bus_type methods
May  9 08:01:54 gpbox kernel: [   26.179214] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
May  9 08:01:54 gpbox kernel: [   26.179224] sd 0:0:0:0: [sda] Write Protect is off
May  9 08:01:54 gpbox kernel: [   26.179239] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 08:01:54 gpbox kernel: [   26.179275] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
May  9 08:01:54 gpbox kernel: [   26.179283] sd 0:0:0:0: [sda] Write Protect is off
May  9 08:01:54 gpbox kernel: [   26.179297] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 08:01:54 gpbox kernel: [   26.179300]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May  9 08:01:54 gpbox kernel: [   26.188007]  sda1 sda2 < sda5 >
May  9 08:01:54 gpbox kernel: [   26.215573] sd 0:0:0:0: [sda] Attached SCSI disk
May  9 08:01:54 gpbox kernel: [   26.219350] sd 0:0:0:0: Attached scsi generic sg0 type 0
May  9 08:01:54 gpbox kernel: [   26.219368] sr 4:0:0:0: Attached scsi generic sg1 type 5
May  9 08:01:54 gpbox kernel: [   26.222181] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May  9 08:01:54 gpbox kernel: [   26.222184] Uniform CD-ROM driver Revision: 3.20
May  9 08:01:54 gpbox kernel: [   26.437818] Attempting manual resume
May  9 08:01:54 gpbox kernel: [   26.482148] kjournald starting.  Commit interval 5 seconds
May  9 08:01:54 gpbox kernel: [   26.482154] EXT3-fs: mounted filesystem with ordered data mode.
May  9 08:01:54 gpbox kernel: [   35.121386] input: PC Speaker as /devices/platform/pcspkr/input/input2
May  9 08:01:54 gpbox kernel: [   35.230833] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  9 08:01:54 gpbox kernel: [   35.295637] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  9 08:01:54 gpbox kernel: [   35.335510] Linux agpgart interface v0.102
May  9 08:01:54 gpbox kernel: [   35.419360] iTCO_vendor_support: vendor-support=0
May  9 08:01:54 gpbox kernel: [   35.431336] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
May  9 08:01:54 gpbox kernel: [   35.431397] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0860)
May  9 08:01:54 gpbox kernel: [   35.431429] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
May  9 08:01:54 gpbox kernel: [   35.499285] input: Power Button (FF) as /devices/virtual/input/input3
May  9 08:01:54 gpbox kernel: [   35.563016] ACPI: Power Button (FF) [PWRF]
May  9 08:01:54 gpbox kernel: [   35.563090] input: Power Button (CM) as /devices/virtual/input/input4
May  9 08:01:54 gpbox kernel: [   35.618907] ACPI: Power Button (CM) [PWRB]
May  9 08:01:54 gpbox kernel: [   36.010557] logips2pp: Detected unknown logitech mouse model 90
May  9 08:01:54 gpbox kernel: [   36.062988] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
May  9 08:01:54 gpbox kernel: [   36.063021] sky2 0000:02:00.0: v1.20 addr 0xfe8fc000 irq 17 Yukon-EC Ultra (0xb4) rev 2
May  9 08:01:54 gpbox kernel: [   36.063359] sky2 eth1: addr 00:18:f3:a2:5d:88
May  9 08:01:54 gpbox kernel: [   36.191573] skge eth0: enabling interface
May  9 08:01:54 gpbox kernel: [   36.200865] nvidia: module license 'NVIDIA' taints kernel.
May  9 08:01:54 gpbox kernel: [   36.514759] skge eth0: disabling interface
May  9 08:01:54 gpbox kernel: [   36.516518] skge eth0: enabling interface
May  9 08:01:54 gpbox kernel: [   36.525844] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
May  9 08:01:54 gpbox kernel: [   36.525937] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
May  9 08:01:54 gpbox kernel: [   36.577049] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
May  9 08:01:54 gpbox kernel: [   36.586950] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
May  9 08:01:54 gpbox kernel: [   37.000142] NET: Registered protocol family 10
May  9 08:01:54 gpbox kernel: [   37.000320] lo: Disabled Privacy Extensions
May  9 08:01:54 gpbox kernel: [   37.000613] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  9 08:01:54 gpbox kernel: [   37.202393] lp: driver loaded but no devices found
May  9 08:01:54 gpbox kernel: [   37.281455] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
May  9 08:01:54 gpbox kernel: [   37.814923] EXT3 FS on sda1, internal journal
May  9 08:01:54 gpbox kernel: [   38.163226] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
May  9 08:01:54 gpbox kernel: [   38.164837] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  9 08:01:54 gpbox kernel: [   38.902060] ip_tables: (C) 2000-2006 Netfilter Core Team
May  9 08:01:54 gpbox kernel: [   40.354734] No dock devices found.
May  9 08:01:57 gpbox kernel: [   43.649362] ppdev: user-space parallel port driver
May  9 08:01:57 gpbox kernel: [   43.876707] audit(1210312917.783:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5311 profile="/usr/sbin/cupsd" namespace="default"
May  9 08:01:57 gpbox kernel: [   44.000129] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May  9 08:01:57 gpbox kernel: [   44.000132] apm: disabled - APM is not SMP safe.
May  9 08:01:58 gpbox kernel: [   44.169609] RPC: Registered udp transport module.
May  9 08:01:58 gpbox kernel: [   44.169613] RPC: Registered tcp transport module.
May  9 08:01:58 gpbox kernel: [   44.211968] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
May  9 08:01:58 gpbox kernel: [   44.276795] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
May  9 08:01:58 gpbox kernel: [   44.293389] NFSD: starting 90-second grace period
May  9 08:01:59 gpbox dhcdbd: Started up.
May  9 08:02:00 gpbox kernel: [   46.163363] sky2 eth1: enabling interface
May  9 08:02:00 gpbox kernel: [   46.168570] ADDRCONF(NETDEV_UP): eth1: link is not ready
May  9 08:21:55 gpbox -- MARK --
May  9 08:41:55 gpbox -- MARK --
May  9 08:53:15 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 08:53:41 gpbox last message repeated 6 times
May  9 08:58:24 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:02:14 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:03:25 gpbox last message repeated 12 times
May  9 09:04:22 gpbox last message repeated 2 times
May  9 09:04:56 gpbox last message repeated 4 times
May  9 09:05:55 gpbox last message repeated 2 times
May  9 09:07:19 gpbox last message repeated 5 times
May  9 09:08:35 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:11:57 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:17:19 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:36:58 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:46:33 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:47:47 gpbox last message repeated 3 times
May  9 09:48:36 gpbox last message repeated 3 times
```

Hope you can find anything from this :(

---

### Post by lptr on 2008-05-09
```
May  9 09:08:35 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
```Hello,

this seems you having trouble with pulseaudio.

Anywhere here in forum I read that some folks having problems with pulseaudio, too. If I correctly remember, they switched back using ALSA. 

Hope this is a starting point for you to find some further?

Regards,

rob*

---

### Post by lordgreg on 2008-05-12
hi Rob and thanks for replying,

after 2 days of idling, i logged back into the ubuntu, and same thing happened. Yes, i went to check the log file again and can confirm the problem is somehow causing the audio c file:

```
May  9 08:21:55 gpbox -- MARK --
May  9 08:41:55 gpbox -- MARK --
May  9 08:53:15 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 08:53:41 gpbox last message repeated 6 times
May  9 08:58:24 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:02:14 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:03:25 gpbox last message repeated 12 times
May  9 09:04:22 gpbox last message repeated 2 times
May  9 09:04:56 gpbox last message repeated 4 times
May  9 09:05:55 gpbox last message repeated 2 times
May  9 09:07:19 gpbox last message repeated 5 times
May  9 09:08:35 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:11:57 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:17:19 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:36:58 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:46:33 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:47:47 gpbox last message repeated 3 times
May  9 09:48:36 gpbox last message repeated 3 times
May  9 09:55:12 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:55:55 gpbox last message repeated 6 times
May  9 09:57:35 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 09:58:06 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:00:32 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:01:24 gpbox last message repeated 4 times
May  9 10:02:57 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:03:43 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:05:22 gpbox last message repeated 3 times
May  9 10:05:46 gpbox last message repeated 3 times
May  9 10:09:22 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:10:55 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:11:39 gpbox last message repeated 5 times
May  9 10:12:51 gpbox last message repeated 7 times
May  9 10:13:17 gpbox last message repeated 3 times
May  9 10:14:45 gpbox last message repeated 4 times
May  9 10:15:43 gpbox last message repeated 6 times
May  9 10:16:51 gpbox last message repeated 2 times
May  9 10:17:53 gpbox last message repeated 4 times
May  9 10:18:15 gpbox last message repeated 3 times
May  9 10:21:51 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:22:49 gpbox last message repeated 4 times
May  9 10:23:23 gpbox last message repeated 3 times
May  9 10:25:35 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:26:23 gpbox last message repeated 6 times
May  9 10:28:30 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:29:54 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:30:11 gpbox last message repeated 4 times
May  9 10:31:51 gpbox last message repeated 4 times
May  9 10:32:08 gpbox last message repeated 3 times
May  9 10:34:59 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:39:43 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:41:04 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:41:13 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:45:44 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:45:54 gpbox last message repeated 3 times
May  9 10:48:49 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:50:25 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:50:43 gpbox last message repeated 4 times
May  9 10:52:19 gpbox last message repeated 2 times
May  9 10:55:11 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:56:24 gpbox last message repeated 4 times
May  9 10:57:44 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 10:57:46 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 11:02:56 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 11:05:46 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 11:06:43 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 11:07:37 gpbox last message repeated 2 times
May  9 11:09:28 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 11:10:55 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 11:11:34 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 11:13:13 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 11:41:55 gpbox -- MARK --
May  9 12:01:55 gpbox -- MARK --
May  9 12:21:55 gpbox -- MARK --
May  9 12:35:15 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:38:16 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:38:50 gpbox last message repeated 5 times
May  9 12:40:21 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:41:04 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:42:11 gpbox last message repeated 2 times
May  9 12:42:50 gpbox last message repeated 3 times
May  9 12:44:43 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:45:11 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:46:18 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:49:22 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:50:13 gpbox last message repeated 2 times
May  9 12:52:01 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:52:09 gpbox last message repeated 3 times
May  9 12:54:01 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:57:26 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 12:58:37 gpbox last message repeated 4 times
May  9 12:58:44 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 13:02:29 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 13:03:51 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 13:03:53 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 13:17:00 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 13:17:36 gpbox last message repeated 3 times
May  9 13:23:39 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 13:26:43 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 13:31:43 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 13:32:27 gpbox last message repeated 5 times
May  9 13:33:45 gpbox last message repeated 3 times
May  9 13:34:07 gpbox last message repeated 2 times
May  9 13:35:47 gpbox last message repeated 3 times
May  9 13:39:48 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 13:48:54 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 13:49:10 gpbox last message repeated 3 times
May  9 13:50:46 gpbox last message repeated 5 times
May  9 13:51:27 gpbox last message repeated 3 times
May  9 13:52:10 gpbox last message repeated 2 times
May  9 13:53:51 gpbox last message repeated 10 times
May  9 13:54:52 gpbox last message repeated 7 times
May  9 13:55:50 gpbox last message repeated 10 times
May  9 13:56:54 gpbox last message repeated 11 times
May  9 13:57:54 gpbox last message repeated 10 times
May  9 13:58:03 gpbox pulseaudio[5954]: sink-input.c: Failed to create sink input: too many inputs per sink.
May  9 14:21:55 gpbox -- MARK --
May  9 14:41:55 gpbox -- MARK --
May  9 15:01:55 gpbox -- MARK --
May  9 15:21:55 gpbox -- MARK --
May  9 15:41:55 gpbox -- MARK --
May  9 16:01:55 gpbox -- MARK --
May  9 16:21:55 gpbox -- MARK --
May  9 16:41:55 gpbox -- MARK --
May  9 17:01:55 gpbox -- MARK --
May  9 17:21:55 gpbox -- MARK --
May  9 17:41:55 gpbox -- MARK --
May  9 18:01:55 gpbox -- MARK --
May  9 18:21:55 gpbox -- MARK --
May  9 18:41:55 gpbox -- MARK --
May  9 19:01:55 gpbox -- MARK --
May  9 19:21:55 gpbox -- MARK --
May  9 19:41:55 gpbox -- MARK --
May  9 20:01:55 gpbox -- MARK --
May  9 20:21:55 gpbox -- MARK --
May  9 20:41:55 gpbox -- MARK --
May  9 21:01:55 gpbox -- MARK --
May  9 21:21:55 gpbox -- MARK --
May  9 21:41:55 gpbox -- MARK --
May  9 22:01:55 gpbox -- MARK --
May  9 22:21:55 gpbox -- MARK --
May  9 22:41:55 gpbox -- MARK --
May  9 23:01:55 gpbox -- MARK --
May  9 23:21:55 gpbox -- MARK --
May  9 23:41:55 gpbox -- MARK --
May 10 00:01:55 gpbox -- MARK --
May 10 00:21:55 gpbox -- MARK --
May 10 00:41:55 gpbox -- MARK --
May 10 01:01:55 gpbox -- MARK --
May 10 01:21:55 gpbox -- MARK --
May 10 01:41:55 gpbox -- MARK --
May 10 02:01:55 gpbox -- MARK --
May 10 02:21:55 gpbox -- MARK --
May 10 02:41:55 gpbox -- MARK --
May 10 03:01:55 gpbox -- MARK --
May 10 03:21:55 gpbox -- MARK --
May 10 03:41:55 gpbox -- MARK --
May 10 04:01:55 gpbox -- MARK --
May 10 04:21:55 gpbox -- MARK --
May 10 04:41:55 gpbox -- MARK --
May 10 05:01:55 gpbox -- MARK --
May 10 05:21:55 gpbox -- MARK --
May 10 05:41:55 gpbox -- MARK --
May 10 06:01:55 gpbox -- MARK --
May 10 06:21:55 gpbox -- MARK --
May 10 06:41:55 gpbox -- MARK --
May 10 07:01:55 gpbox -- MARK --
May 10 07:21:55 gpbox -- MARK --
May 10 07:41:55 gpbox -- MARK --
May 10 07:54:42 gpbox syslogd 1.5.0#1ubuntu1: restart.
May 10 08:21:55 gpbox -- MARK --
May 10 08:41:55 gpbox -- MARK --
May 10 09:01:55 gpbox -- MARK --
May 10 09:21:55 gpbox -- MARK --
May 10 09:41:55 gpbox -- MARK --
May 10 10:01:55 gpbox -- MARK --
May 10 10:21:55 gpbox -- MARK --
May 10 10:41:55 gpbox -- MARK --
May 10 11:01:55 gpbox -- MARK --
May 10 11:21:55 gpbox -- MARK --
May 10 11:41:55 gpbox -- MARK --
May 10 12:01:55 gpbox -- MARK --
May 10 12:21:55 gpbox -- MARK --
May 10 12:41:55 gpbox -- MARK --
May 10 13:01:55 gpbox -- MARK --
May 10 13:21:55 gpbox -- MARK --
May 10 13:41:55 gpbox -- MARK --
May 10 14:01:55 gpbox -- MARK --
May 10 14:21:55 gpbox -- MARK --
May 10 14:41:55 gpbox -- MARK --
May 10 15:01:55 gpbox -- MARK --
May 10 15:21:55 gpbox -- MARK --
May 10 15:41:55 gpbox -- MARK --
May 10 16:01:55 gpbox -- MARK --
May 10 16:21:55 gpbox -- MARK --
May 10 16:41:55 gpbox -- MARK --
May 10 17:01:55 gpbox -- MARK --
May 10 17:21:55 gpbox -- MARK --
May 10 17:41:55 gpbox -- MARK --
May 10 18:01:55 gpbox -- MARK --
May 10 18:21:55 gpbox -- MARK --
May 10 18:41:55 gpbox -- MARK --
May 10 19:01:55 gpbox -- MARK --
May 10 19:21:55 gpbox -- MARK --
May 10 19:41:55 gpbox -- MARK --
May 10 20:01:55 gpbox -- MARK --
May 10 20:21:55 gpbox -- MARK --
May 10 20:41:55 gpbox -- MARK --
May 10 21:01:55 gpbox -- MARK --
May 10 21:21:55 gpbox -- MARK --
May 10 21:41:55 gpbox -- MARK --
May 10 22:01:55 gpbox -- MARK --
May 10 22:21:55 gpbox -- MARK --
May 10 22:41:55 gpbox -- MARK --
May 10 23:01:55 gpbox -- MARK --
May 10 23:21:55 gpbox -- MARK --
May 10 23:41:55 gpbox -- MARK --
May 11 00:01:55 gpbox -- MARK --
May 11 00:21:55 gpbox -- MARK --
May 11 00:41:55 gpbox -- MARK --
May 11 01:01:55 gpbox -- MARK --
May 11 01:21:55 gpbox -- MARK --
May 11 01:41:55 gpbox -- MARK --
May 11 02:01:55 gpbox -- MARK --
May 11 02:21:55 gpbox -- MARK --
May 11 02:41:55 gpbox -- MARK --
May 11 03:01:55 gpbox -- MARK --
May 11 03:21:55 gpbox -- MARK --
May 11 03:41:55 gpbox -- MARK --
May 11 04:01:55 gpbox -- MARK --
May 11 04:21:55 gpbox -- MARK --
May 11 04:41:55 gpbox -- MARK --
May 11 05:01:55 gpbox -- MARK --
May 11 05:21:55 gpbox -- MARK --
May 11 05:41:55 gpbox -- MARK --
May 11 06:01:55 gpbox -- MARK --
May 11 06:21:55 gpbox -- MARK --
May 11 06:41:55 gpbox -- MARK --
May 11 07:01:55 gpbox -- MARK --
May 11 07:21:55 gpbox -- MARK --
May 11 07:41:55 gpbox -- MARK --
May 11 08:00:08 gpbox syslogd 1.5.0#1ubuntu1: restart.
May 11 08:21:55 gpbox -- MARK --
May 11 08:41:55 gpbox -- MARK --
May 11 09:01:55 gpbox -- MARK --
May 11 09:21:55 gpbox -- MARK --
May 11 09:41:55 gpbox -- MARK --
May 11 10:01:55 gpbox -- MARK --
May 11 10:21:55 gpbox -- MARK --
May 11 10:41:55 gpbox -- MARK --
May 11 11:01:55 gpbox -- MARK --
May 11 11:21:55 gpbox -- MARK --
May 11 11:41:55 gpbox -- MARK --
May 11 12:01:55 gpbox -- MARK --
May 11 12:21:55 gpbox -- MARK --
May 11 12:41:55 gpbox -- MARK --
May 11 13:01:55 gpbox -- MARK --
May 11 13:21:55 gpbox -- MARK --
May 11 13:41:55 gpbox -- MARK --
May 11 14:01:55 gpbox -- MARK --
May 11 14:21:55 gpbox -- MARK --
May 11 14:41:55 gpbox -- MARK --
May 11 15:01:55 gpbox -- MARK --
May 11 15:21:55 gpbox -- MARK --
May 11 15:41:55 gpbox -- MARK --
May 11 16:01:55 gpbox -- MARK --
May 11 16:21:55 gpbox -- MARK --
May 11 16:41:55 gpbox -- MARK --
May 11 17:01:55 gpbox -- MARK --
May 11 17:21:55 gpbox -- MARK --
May 11 17:41:55 gpbox -- MARK --
May 11 18:01:55 gpbox -- MARK --
May 11 18:21:55 gpbox -- MARK --
May 11 18:41:55 gpbox -- MARK --
May 11 19:01:55 gpbox -- MARK --
May 11 19:21:55 gpbox -- MARK --
May 11 19:41:55 gpbox -- MARK --
May 11 20:01:55 gpbox -- MARK --
May 11 20:21:55 gpbox -- MARK --
May 11 20:41:55 gpbox -- MARK --
May 11 21:01:55 gpbox -- MARK --
May 11 21:21:55 gpbox -- MARK --
May 11 21:41:55 gpbox -- MARK --
May 11 22:01:55 gpbox -- MARK --
May 11 22:21:55 gpbox -- MARK --
May 11 22:41:55 gpbox -- MARK --
May 11 23:01:55 gpbox -- MARK --
May 11 23:21:55 gpbox -- MARK --
May 11 23:41:55 gpbox -- MARK --
May 12 00:01:55 gpbox -- MARK --
May 12 00:21:55 gpbox -- MARK --
May 12 00:41:55 gpbox -- MARK --
May 12 01:01:55 gpbox -- MARK --
May 12 01:21:55 gpbox -- MARK --
May 12 01:41:55 gpbox -- MARK --
May 12 02:01:55 gpbox -- MARK --
May 12 02:21:55 gpbox -- MARK --
May 12 02:41:55 gpbox -- MARK --
May 12 03:01:55 gpbox -- MARK --
May 12 03:21:55 gpbox -- MARK --
May 12 03:41:55 gpbox -- MARK --
May 12 04:01:55 gpbox -- MARK --
May 12 04:21:55 gpbox -- MARK --
May 12 04:41:55 gpbox -- MARK --
May 12 05:01:55 gpbox -- MARK --
May 12 05:21:55 gpbox -- MARK --
May 12 05:41:55 gpbox -- MARK --
May 12 06:01:55 gpbox -- MARK --
May 12 06:21:55 gpbox -- MARK --
May 12 06:41:55 gpbox -- MARK --
```

I'll check the other threads and update this one when i solve it. Thank you for your help :)

---

