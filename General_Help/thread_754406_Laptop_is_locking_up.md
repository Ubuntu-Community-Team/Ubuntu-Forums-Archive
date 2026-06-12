---
title: "Laptop is locking up"
date: 2008-04-13
forum: General Help
---

### Post by allspiritseve on 2008-04-13
My laptop has locked up twice in the last half hour... I have pasted below the relevant data from /var/log/messages. I don't know if that's the right place to look, but its the only log I know about. Can anyone figure out what might be the problem, or tell me where I can find more information?

```


Apr 13 18:31:08 spirit-laptop -- MARK --
Apr 13 18:33:05 spirit-laptop kernel: [ 1342.200000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Apr 13 18:33:05 spirit-laptop kernel: [ 1342.200000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Apr 13 18:33:27 spirit-laptop kernel: [ 1364.436000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 13 18:33:41 spirit-laptop kernel: [ 1377.912000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 13 18:34:11 spirit-laptop kernel: [ 1408.112000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 13 18:34:12 spirit-laptop kernel: [ 1409.016000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Apr 13 18:34:12 spirit-laptop kernel: [ 1409.016000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Apr 13 18:34:22 spirit-laptop kernel: [ 1418.604000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 13 18:34:25 spirit-laptop kernel: [ 1422.324000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 13 18:34:31 spirit-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Apr 13 18:34:31 spirit-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Apr 13 18:34:31 spirit-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Apr 13 18:51:08 spirit-laptop -- MARK --
Apr 13 18:52:31 spirit-laptop syslogd 1.4.1#21ubuntu3: restart.

```

Thanks,

Cory

---

### Post by allspiritseve on 2008-04-14
I would really appreciate some help here... my laptop is randomly locking up and I don't know why.

---

### Post by Fixman on 2008-04-14
The last message was 20 minutes from reboot, so I guess that is not the right place to look. Please give us some more information, such as what distro you are using, you quantity or RAM, how mutch time did you have that distro, etc.

---

### Post by allspiritseve on 2008-04-14
I'm using Kubuntu Gutsy on a dell Inspiron 6400 with 1gb RAM, I've been using it for just over a year. The computer is maybe two years old.

Cory

---

### Post by pointone on 2008-04-14
"Locking up" is vague.

Is it just X freezing? Can you hit Ctrl+Alt+Backspace to restart the X server? Does pressing Ctrl+Alt+F# take you to a console? 

Does Ctrl+Alt+Delete still restart the computer, or do you need to power down manually?

Does the magic SysRq key work?

/var/log/syslog or /var/log/kern.log may contain more useful information. If this is an X-related problem, /var/log/Xorg.0.log may be helpful.

---

### Post by allspiritseve on 2008-04-14
CTRL-ALT-Backspace doesn't work, nor does CTRL-ALT-F# or CTRL-ALT-DELETE

What is the magic SysRq?

I'll check on those logs and see if I can find anything.

Cory

---

### Post by Choad on 2008-04-14
go to

system > preferences > appearance 
visual effects > none

well, if they were already set to none, then this won't be the cause, but i have and continue to get occasional random lockups due to compiz. if you disable it and you never get these lockups again, then you know what is to blame at least. as for fixing it... i haven't a clue. it's still pretty fresh code under there, it's not perfect yet by any means.

---

### Post by allspiritseve on 2008-04-22
> **pointone said:**
> /var/log/syslog or /var/log/kern.log may contain more useful information. If this is an X-related problem, /var/log/Xorg.0.log may be helpful.

I looked through these, and I can't find anything except that after I restarted, when it locked up, mysqld said something about recovering from a crash. I don't really know what I'm looking for... I'm posting here the log from when I started up my computer, to when it locked up and I restarted. If I should be posting the log after it starts up, I can do that too... or if I should be looking for something specific, please let me know and I would be happy to dig through the logs again myself. I really just don't know what I'm looking for though.

```

Apr 22 11:16:06 spirit-laptop syslogd 1.4.1#21ubuntu3: restart.
Apr 22 11:16:06 spirit-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Apr 22 11:16:06 spirit-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Apr 22 11:16:06 spirit-laptop kernel: Symbols match kernel version 2.6.22.
Apr 22 11:16:06 spirit-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fed3400 (usable)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]  BIOS-e820: 000000003fed3400 - 0000000040000000 (reserved)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] 126MB HIGHMEM available.
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] 896MB LOWMEM available.
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 261843) 0 entries of 256 used
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Zone PFN ranges:
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]   DMA             0 ->     4096
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]   HighMem    229376 ->   261843
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]     0:        0 ->   261843
Apr 22 11:16:06 spirit-laptop NetworkManager: <info>  starting... 
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] On node 0 totalpages: 261843
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]   HighMem zone: 253 pages used for memmap
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000]   HighMem zone: 32214 pages, LIFO batch:7
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] DMI 2.4 present.
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC370 checksum 0
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: RSDP 000FC370, 0014 (r0 DELL  )
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: RSDT 3FED3B04, 0038 (r1 DELL    M07     27D60414 ASL        61)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: FACP 3FED4800, 0074 (r1 DELL    M07     27D60414 ASL        61)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: DSDT 3FED5400, 3A5B (r1 INT430 SYSFexxx     1001 INTL 20050624)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: FACS 3FEE3C00, 0040
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: APIC 3FED5000, 0068 (r1 DELL    M07     27D60414 ASL        47)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: MCFG 3FED4FC0, 003E (r16 DELL    M07     27D60414 ASL        61)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: BOOT 3FED4BC0, 0028 (r1 DELL    M07     27D60414 ASL        61)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: SSDT 3FED3B3C, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Processor #0 6:14 APIC version 20
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Processor #1 6:14 APIC version 20
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 259798
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Kernel command line: root=UUID=f0574c52-2ef1-4fba-b5eb-44e5ca98cdd5 ro quiet splash
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Initializing CPU#0
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 22 11:16:06 spirit-laptop kernel: [    0.000000] Detected 1829.513 MHz processor.
Apr 22 11:16:06 spirit-laptop kernel: [    5.985888] Console: colour VGA+ 80x25
Apr 22 11:16:06 spirit-laptop kernel: [    5.986301] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 22 11:16:06 spirit-laptop kernel: [    5.987077] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 22 11:16:06 spirit-laptop kernel: [    6.049018] Memory: 1026760k/1047372k available (2015k kernel code, 20000k reserved, 915k data, 364k init, 129868k highmem)
Apr 22 11:16:06 spirit-laptop kernel: [    6.049044] virtual kernel memory layout:
Apr 22 11:16:06 spirit-laptop kernel: [    6.049046]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Apr 22 11:16:06 spirit-laptop kernel: [    6.049048]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 22 11:16:06 spirit-laptop kernel: [    6.049051]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 22 11:16:06 spirit-laptop kernel: [    6.049053]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 22 11:16:06 spirit-laptop kernel: [    6.049055]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Apr 22 11:16:06 spirit-laptop kernel: [    6.049057]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Apr 22 11:16:06 spirit-laptop kernel: [    6.049069]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Apr 22 11:16:06 spirit-laptop kernel: [    6.049075] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 22 11:16:06 spirit-laptop kernel: [    6.049147] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 22 11:16:06 spirit-laptop kernel: [    6.129056] Calibrating delay using timer specific routine.. 3663.03 BogoMIPS (lpj=7326069)
Apr 22 11:16:06 spirit-laptop kernel: [    6.129111] Security Framework v1.0.0 initialized
Apr 22 11:16:06 spirit-laptop kernel: [    6.129120] SELinux:  Disabled at boot.
Apr 22 11:16:06 spirit-laptop kernel: [    6.129152] Mount-cache hash table entries: 512
Apr 22 11:16:06 spirit-laptop kernel: [    6.129401] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
Apr 22 11:16:06 spirit-laptop kernel: [    6.129424] monitor/mwait feature present.
Apr 22 11:16:06 spirit-laptop kernel: [    6.129427] using mwait in idle threads.
Apr 22 11:16:06 spirit-laptop kernel: [    6.129434] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 22 11:16:06 spirit-laptop kernel: [    6.129438] CPU: L2 cache: 2048K
Apr 22 11:16:06 spirit-laptop kernel: [    6.129452] CPU: Physical Processor ID: 0
Apr 22 11:16:06 spirit-laptop kernel: [    6.129455] CPU: Processor Core ID: 0
Apr 22 11:16:06 spirit-laptop kernel: [    6.129458] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
Apr 22 11:16:06 spirit-laptop kernel: [    6.129483] Compat vDSO mapped to ffffe000.
Apr 22 11:16:06 spirit-laptop kernel: [    6.129501] Checking 'hlt' instruction... OK.
Apr 22 11:16:06 spirit-laptop kernel: [    6.145274] SMP alternatives: switching to UP code
Apr 22 11:16:06 spirit-laptop kernel: [    6.146242] Early unpacking initramfs... done
Apr 22 11:16:06 spirit-laptop kernel: [    7.001835] ACPI: Core revision 20070126
Apr 22 11:16:06 spirit-laptop kernel: [    7.001958] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 22 11:16:06 spirit-laptop kernel: [    7.007450] CPU0: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
Apr 22 11:16:06 spirit-laptop kernel: [    7.007485] SMP alternatives: switching to SMP code
Apr 22 11:16:06 spirit-laptop kernel: [    7.007713] Booting processor 1/1 eip 3000
Apr 22 11:16:06 spirit-laptop kernel: [    8.874980] Initializing CPU#1
Apr 22 11:16:06 spirit-laptop kernel: [    8.955469] Calibrating delay using timer specific routine.. 3659.15 BogoMIPS (lpj=7318302)
Apr 22 11:16:06 spirit-laptop kernel: [    8.955480] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
Apr 22 11:16:06 spirit-laptop kernel: [    8.955498] monitor/mwait feature present.
Apr 22 11:16:06 spirit-laptop kernel: [    8.955504] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 22 11:16:06 spirit-laptop kernel: [    8.955507] CPU: L2 cache: 2048K
Apr 22 11:16:06 spirit-laptop kernel: [    8.955511] CPU: Physical Processor ID: 0
Apr 22 11:16:06 spirit-laptop kernel: [    8.955524] CPU: Processor Core ID: 1
Apr 22 11:16:06 spirit-laptop kernel: [    8.955526] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
Apr 22 11:16:06 spirit-laptop kernel: [    7.100464] CPU1: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
Apr 22 11:16:06 spirit-laptop kernel: [    7.100518] Total of 2 processors activated (7322.18 BogoMIPS).
Apr 22 11:16:06 spirit-laptop kernel: [    7.100788] ENABLING IO-APIC IRQs
Apr 22 11:16:06 spirit-laptop kernel: [    7.101076] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 22 11:16:06 spirit-laptop kernel: [    7.247431] checking TSC synchronization [CPU#0 -> CPU#1]:
Apr 22 11:16:06 spirit-laptop kernel: [    7.267418] Measured 3399901879 cycles TSC warp between CPUs, turning off TSC clock.
Apr 22 11:16:06 spirit-laptop kernel: [    1.096000] Marking TSC unstable due to: check_tsc_sync_source failed.
Apr 22 11:16:06 spirit-laptop kernel: [    1.100000] Brought up 2 CPUs
Apr 22 11:16:06 spirit-laptop kernel: [    1.352000] migration_cost=4000
Apr 22 11:16:06 spirit-laptop kernel: [    1.352000] Booting paravirtualized kernel on bare hardware
Apr 22 11:16:06 spirit-laptop kernel: [    1.352000] Time: 11:15:40  Date: 03/22/108
Apr 22 11:16:06 spirit-laptop kernel: [    1.352000] NET: Registered protocol family 16
Apr 22 11:16:06 spirit-laptop kernel: [    1.352000] EISA bus registered
Apr 22 11:16:06 spirit-laptop kernel: [    1.352000] ACPI: bus type pci registered
Apr 22 11:16:06 spirit-laptop kernel: [    1.388000] PCI: PCI BIOS revision 2.10 entry at 0xfb4d6, last bus=13
Apr 22 11:16:06 spirit-laptop kernel: [    1.388000] PCI: Using configuration type 1
Apr 22 11:16:06 spirit-laptop kernel: [    1.388000] Setting up standard PCI resources
Apr 22 11:16:06 spirit-laptop kernel: [    1.404000] ACPI: EC: Look up EC in DSDT
Apr 22 11:16:06 spirit-laptop kernel: [    1.416000] ACPI: Interpreter enabled
Apr 22 11:16:06 spirit-laptop kernel: [    1.416000] ACPI: (supports S0 S3 S4 S5)
Apr 22 11:16:06 spirit-laptop kernel: [    1.416000] ACPI: Using IOAPIC for interrupt routing
Apr 22 11:16:06 spirit-laptop kernel: [    1.452000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 22 11:16:06 spirit-laptop kernel: [    1.452000] PCI: Probing PCI hardware (bus 00)
Apr 22 11:16:06 spirit-laptop kernel: [    1.456000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 22 11:16:06 spirit-laptop kernel: [    1.456000] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Apr 22 11:16:06 spirit-laptop kernel: [    1.456000] PCI: Transparent bridge - 0000:00:1e.0
Apr 22 11:16:06 spirit-laptop kernel: [    1.456000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 22 11:16:06 spirit-laptop kernel: [    1.456000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Apr 22 11:16:06 spirit-laptop kernel: [    1.456000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr 22 11:16:06 spirit-laptop kernel: [    1.460000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 22 11:16:06 spirit-laptop kernel: [    1.460000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr 22 11:16:06 spirit-laptop kernel: [    1.476000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
Apr 22 11:16:06 spirit-laptop kernel: [    1.476000] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
Apr 22 11:16:06 spirit-laptop kernel: [    1.480000] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Apr 22 11:16:06 spirit-laptop kernel: [    1.480000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Apr 22 11:16:06 spirit-laptop kernel: [    1.480000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 22 11:16:06 spirit-laptop kernel: [    1.480000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr 22 11:16:06 spirit-laptop kernel: [    1.480000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 22 11:16:06 spirit-laptop kernel: [    1.480000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Apr 22 11:16:06 spirit-laptop kernel: [    1.480000] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 22 11:16:06 spirit-laptop kernel: [    1.480000] pnp: PnP ACPI init
Apr 22 11:16:06 spirit-laptop kernel: [    1.480000] ACPI: bus type pnp registered
Apr 22 11:16:06 spirit-laptop kernel: [    1.552000] pnp: PnP ACPI: found 11 devices
Apr 22 11:16:06 spirit-laptop kernel: [    1.552000] ACPI: ACPI bus type pnp unregistered
Apr 22 11:16:06 spirit-laptop kernel: [    1.552000] PnPBIOS: Disabled by ACPI PNP
Apr 22 11:16:06 spirit-laptop kernel: [    1.552000] PCI: Using ACPI for IRQ routing
Apr 22 11:16:06 spirit-laptop kernel: [    1.552000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] NET: Registered protocol family 8
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] NET: Registered protocol family 20
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:02: ioport range 0x1000-0x1005 has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:02: ioport range 0x1008-0x100f has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:08: ioport range 0xc80-0xcff could not be reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:08: ioport range 0x910-0x91f has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:08: ioport range 0x920-0x92f has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:08: ioport range 0xcb0-0xcbf has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.624000] pnp: 00:08: ioport range 0x940-0x97f has been reserved
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] PCI: Bridge: 0000:00:01.0
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   IO window: e000-efff
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   MEM window: dfd00000-dfefffff
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   PREFETCH window: c0000000-cfffffff
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] PCI: Bridge: 0000:00:1c.0
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   IO window: disabled.
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   MEM window: dfc00000-dfcfffff
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   PREFETCH window: disabled.
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] PCI: Bridge: 0000:00:1c.3
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   IO window: d000-dfff
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   MEM window: dfa00000-dfbfffff
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   PREFETCH window: d0000000-d01fffff
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] PCI: Bridge: 0000:00:1e.0
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   IO window: disabled.
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   MEM window: df900000-df9fffff
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000]   PREFETCH window: disabled.
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    1.656000] NET: Registered protocol family 2
Apr 22 11:16:06 spirit-laptop kernel: [    1.660000] Time: acpi_pm clocksource has been installed.
Apr 22 11:16:06 spirit-laptop kernel: [    1.660000] Switched to high resolution mode on CPU 0
Apr 22 11:16:06 spirit-laptop kernel: [    1.660000] Switched to high resolution mode on CPU 1
Apr 22 11:16:06 spirit-laptop kernel: [    1.700000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 22 11:16:06 spirit-laptop kernel: [    1.700000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Apr 22 11:16:06 spirit-laptop kernel: [    1.700000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 22 11:16:06 spirit-laptop kernel: [    1.700000] TCP: Hash tables configured (established 131072 bind 65536)
Apr 22 11:16:06 spirit-laptop kernel: [    1.700000] TCP reno registered
Apr 22 11:16:06 spirit-laptop kernel: [    1.716000] checking if image is initramfs... it is
Apr 22 11:16:06 spirit-laptop kernel: [    2.896000] Freeing initrd memory: 7090k freed
Apr 22 11:16:06 spirit-laptop kernel: [    2.896000] Simple Boot Flag at 0x79 set to 0x1
Apr 22 11:16:06 spirit-laptop kernel: [    2.896000] audit: initializing netlink socket (disabled)
Apr 22 11:16:06 spirit-laptop kernel: [    2.896000] audit(1208862941.660:1): initialized
Apr 22 11:16:06 spirit-laptop kernel: [    2.896000] highmem bounce pool size: 64 pages
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] VFS: Disk quotas dquot_6.5.1
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] io scheduler noop registered
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] io scheduler anticipatory registered
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] io scheduler deadline registered
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] io scheduler cfq registered (default)
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] Boot video device is 0000:01:00.0
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] assign_interrupt_mode Found MSI capability
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] Allocate Port Service[0000:00:01.0:pcie00]
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] assign_interrupt_mode Found MSI capability
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] assign_interrupt_mode Found MSI capability
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] Allocate Port Service[0000:00:1c.3:pcie00]
Apr 22 11:16:06 spirit-laptop kernel: [    2.900000] Allocate Port Service[0000:00:1c.3:pcie02]
Apr 22 11:16:06 spirit-laptop kernel: [    2.904000] isapnp: Scanning for PnP cards...
Apr 22 11:16:06 spirit-laptop kernel: [    3.256000] isapnp: No Plug & Play device found
Apr 22 11:16:06 spirit-laptop kernel: [    3.296000] Real Time Clock Driver v1.12ac
Apr 22 11:16:06 spirit-laptop kernel: [    3.296000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 22 11:16:06 spirit-laptop kernel: [    3.296000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 22 11:16:06 spirit-laptop kernel: [    3.296000] input: Macintosh mouse button emulation as /class/input/input0
Apr 22 11:16:06 spirit-laptop kernel: [    3.296000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000] mice: PS/2 mouse device common for all mice
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000] EISA: Probing bus 0 at eisa.0
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000] Cannot allocate resource for EISA slot 1
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000] EISA: Detected 0 cards.
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000] TCP cubic registered
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000] NET: Registered protocol family 1
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000] Using IPI No-Shortcut mode
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000]   Magic number: 4:525:277
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000]   hash matches device ttyy5
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000]   hash matches device tty14
Apr 22 11:16:06 spirit-laptop kernel: [    3.300000] Freeing unused kernel memory: 364k freed
Apr 22 11:16:06 spirit-laptop kernel: [    3.308000] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 22 11:16:06 spirit-laptop kernel: [    4.636000] AppArmor: AppArmor initialized<5>audit(1208862943.160:2):  type=1505 info="AppArmor initialized" pid=1247
Apr 22 11:16:06 spirit-laptop kernel: [    4.648000] fuse init (API version 7.8)
Apr 22 11:16:06 spirit-laptop kernel: [    4.660000] Failure registering capabilities with primary security module.
Apr 22 11:16:06 spirit-laptop kernel: [    4.700000] ACPI: SSDT 3FED41F5, 01AF (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Apr 22 11:16:06 spirit-laptop kernel: [    4.700000] ACPI: SSDT 3FED4018, 0158 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Apr 22 11:16:06 spirit-laptop kernel: [    4.700000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 22 11:16:06 spirit-laptop kernel: [    4.700000] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 22 11:16:06 spirit-laptop kernel: [    4.700000] ACPI: SSDT 3FED43A4, 0090 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Apr 22 11:16:06 spirit-laptop kernel: [    4.700000] ACPI: SSDT 3FED4170, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Apr 22 11:16:06 spirit-laptop kernel: [    4.700000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 22 11:16:06 spirit-laptop kernel: [    4.700000] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 22 11:16:06 spirit-laptop kernel: [    4.708000] ACPI: Thermal Zone [THM] (25 C)
Apr 22 11:16:06 spirit-laptop kernel: [    5.364000] usbcore: registered new interface driver usbfs
Apr 22 11:16:06 spirit-laptop kernel: [    5.364000] usbcore: registered new interface driver hub
Apr 22 11:16:06 spirit-laptop kernel: [    5.364000] usbcore: registered new device driver usb
Apr 22 11:16:06 spirit-laptop kernel: [    5.368000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Apr 22 11:16:06 spirit-laptop kernel: [    5.368000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    5.368000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 22 11:16:06 spirit-laptop kernel: [    5.368000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Apr 22 11:16:06 spirit-laptop kernel: [    5.368000] ehci_hcd 0000:00:1d.7: debug port 1
Apr 22 11:16:06 spirit-laptop kernel: [    5.368000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 22 11:16:06 spirit-laptop kernel: [    5.368000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
Apr 22 11:16:06 spirit-laptop kernel: [    5.372000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 22 11:16:06 spirit-laptop kernel: [    5.372000] usb usb1: configuration #1 chosen from 1 choice
Apr 22 11:16:06 spirit-laptop kernel: [    5.372000] hub 1-0:1.0: USB hub found
Apr 22 11:16:06 spirit-laptop kernel: [    5.372000] hub 1-0:1.0: 8 ports detected
Apr 22 11:16:06 spirit-laptop kernel: [    5.408000] USB Universal Host Controller Interface driver v3.0
Apr 22 11:16:06 spirit-laptop kernel: [    5.428000] SCSI subsystem initialized
Apr 22 11:16:06 spirit-laptop kernel: [    5.436000] libata version 2.21 loaded.
Apr 22 11:16:06 spirit-laptop kernel: [    5.488000] ata_piix 0000:00:1f.2: version 2.11
Apr 22 11:16:06 spirit-laptop kernel: [    5.488000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Apr 22 11:16:06 spirit-laptop kernel: [    5.488000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 19
Apr 22 11:16:06 spirit-laptop kernel: [    5.488000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    5.488000] scsi0 : ata_piix
Apr 22 11:16:06 spirit-laptop kernel: [    5.508000] scsi1 : ata_piix
Apr 22 11:16:06 spirit-laptop kernel: [    5.508000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Apr 22 11:16:06 spirit-laptop kernel: [    5.508000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Apr 22 11:16:06 spirit-laptop kernel: [    5.676000] ata1.00: Host Protected Area detected:
Apr 22 11:16:06 spirit-laptop kernel: [    5.676000] ^Icurrent size: 114270345 sectors
Apr 22 11:16:06 spirit-laptop kernel: [    5.676000] ^Inative size: 117210240 sectors
Apr 22 11:16:06 spirit-laptop kernel: [    5.832000] ata1.00: ATA-7: ST96023AS, 8.02, max UDMA/133
Apr 22 11:16:06 spirit-laptop kernel: [    5.832000] ata1.00: 114270345 sectors, multi 8: LBA48 NCQ (depth 0/32)
Apr 22 11:16:06 spirit-laptop kernel: [    5.848000] ata1.00: Host Protected Area detected:
Apr 22 11:16:06 spirit-laptop kernel: [    5.848000] ^Icurrent size: 114270345 sectors
Apr 22 11:16:06 spirit-laptop kernel: [    5.848000] ^Inative size: 117210240 sectors
Apr 22 11:16:06 spirit-laptop kernel: [    6.004000] ata1.00: configured for UDMA/133
Apr 22 11:16:06 spirit-laptop kernel: [    6.156000] Clocksource tsc unstable (delta = -344140470 ns)
Apr 22 11:16:06 spirit-laptop kernel: [    6.348000] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L532B, DE04, max UDMA/33
Apr 22 11:16:06 spirit-laptop kernel: [    6.584000] ata2.00: configured for UDMA/33
Apr 22 11:16:06 spirit-laptop kernel: [    6.584000] scsi 0:0:0:0: Direct-Access     ATA      ST96023AS        8.02 PQ: 0 ANSI: 5
Apr 22 11:16:06 spirit-laptop kernel: [    6.592000] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L532B DE04 PQ: 0 ANSI: 5
Apr 22 11:16:06 spirit-laptop kernel: [    6.592000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Apr 22 11:16:06 spirit-laptop kernel: [    6.592000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    6.592000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 22 11:16:06 spirit-laptop kernel: [    6.592000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Apr 22 11:16:06 spirit-laptop kernel: [    6.592000] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
Apr 22 11:16:06 spirit-laptop kernel: [    6.592000] usb usb2: configuration #1 chosen from 1 choice
Apr 22 11:16:06 spirit-laptop kernel: [    6.592000] hub 2-0:1.0: USB hub found
Apr 22 11:16:06 spirit-laptop kernel: [    6.592000] hub 2-0:1.0: 2 ports detected
Apr 22 11:16:06 spirit-laptop kernel: [    6.608000] sd 0:0:0:0: [sda] 114270345 512-byte hardware sectors (58506 MB)
Apr 22 11:16:06 spirit-laptop kernel: [    6.608000] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 11:16:06 spirit-laptop kernel: [    6.608000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 11:16:06 spirit-laptop kernel: [    6.608000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 11:16:06 spirit-laptop kernel: [    6.608000] sd 0:0:0:0: [sda] 114270345 512-byte hardware sectors (58506 MB)
Apr 22 11:16:06 spirit-laptop kernel: [    6.608000] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 11:16:06 spirit-laptop kernel: [    6.608000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 11:16:06 spirit-laptop kernel: [    6.608000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 11:16:06 spirit-laptop kernel: [    6.608000]  sda:sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 22 11:16:06 spirit-laptop kernel: [    6.616000] Uniform CD-ROM driver Revision: 3.20
Apr 22 11:16:06 spirit-laptop kernel: [    6.620000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 22 11:16:06 spirit-laptop kernel: [    6.624000]  sda1 sda2 sda3 sda4
Apr 22 11:16:06 spirit-laptop kernel: [    6.624000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 22 11:16:06 spirit-laptop kernel: [    6.624000] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 22 11:16:06 spirit-laptop kernel: [    6.640000] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 22 11:16:06 spirit-laptop kernel: [    6.696000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
Apr 22 11:16:06 spirit-laptop kernel: [    6.696000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    6.696000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 22 11:16:06 spirit-laptop kernel: [    6.696000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Apr 22 11:16:06 spirit-laptop kernel: [    6.696000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000bf60
Apr 22 11:16:06 spirit-laptop kernel: [    6.696000] usb usb3: configuration #1 chosen from 1 choice
Apr 22 11:16:06 spirit-laptop kernel: [    6.696000] hub 3-0:1.0: USB hub found
Apr 22 11:16:06 spirit-laptop kernel: [    6.696000] hub 3-0:1.0: 2 ports detected
Apr 22 11:16:06 spirit-laptop kernel: [    6.808000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
Apr 22 11:16:06 spirit-laptop kernel: [    6.808000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    6.808000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 22 11:16:06 spirit-laptop kernel: [    6.808000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Apr 22 11:16:06 spirit-laptop kernel: [    6.812000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000bf40
Apr 22 11:16:06 spirit-laptop kernel: [    6.812000] usb usb4: configuration #1 chosen from 1 choice
Apr 22 11:16:06 spirit-laptop kernel: [    6.812000] hub 4-0:1.0: USB hub found
Apr 22 11:16:06 spirit-laptop kernel: [    6.812000] hub 4-0:1.0: 2 ports detected
Apr 22 11:16:06 spirit-laptop kernel: [    6.916000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
Apr 22 11:16:06 spirit-laptop kernel: [    6.916000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Apr 22 11:16:06 spirit-laptop kernel: [    6.916000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr 22 11:16:06 spirit-laptop kernel: [    6.916000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Apr 22 11:16:06 spirit-laptop kernel: [    6.916000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000bf20
Apr 22 11:16:06 spirit-laptop kernel: [    6.916000] usb usb5: configuration #1 chosen from 1 choice
Apr 22 11:16:06 spirit-laptop kernel: [    6.916000] hub 5-0:1.0: USB hub found
Apr 22 11:16:06 spirit-laptop kernel: [    6.916000] hub 5-0:1.0: 2 ports detected
Apr 22 11:16:06 spirit-laptop kernel: [    7.020000] b44.c:v1.01 (Jun 16, 2006)
Apr 22 11:16:06 spirit-laptop kernel: [    7.020000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 19
Apr 22 11:16:06 spirit-laptop kernel: [    7.020000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:15:c5:11:56:a8
Apr 22 11:16:06 spirit-laptop kernel: [    7.024000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Apr 22 11:16:06 spirit-laptop kernel: [    7.076000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[df9fd800-df9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 22 11:16:06 spirit-laptop kernel: [    7.164000] kjournald starting.  Commit interval 5 seconds
Apr 22 11:16:06 spirit-laptop kernel: [    7.164000] EXT3-fs: mounted filesystem with ordered data mode.
Apr 22 11:16:06 spirit-laptop kernel: [    8.356000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc00036b3f121]
Apr 22 11:16:06 spirit-laptop kernel: [   18.324000] iTCO_vendor_support: vendor-support=0
Apr 22 11:16:06 spirit-laptop kernel: [   18.336000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Apr 22 11:16:06 spirit-laptop kernel: [   18.336000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Apr 22 11:16:06 spirit-laptop kernel: [   18.336000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 22 11:16:06 spirit-laptop kernel: [   18.428000] intel_rng: FWH not detected
Apr 22 11:16:06 spirit-laptop kernel: [   18.452000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 22 11:16:06 spirit-laptop kernel: [   18.456000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 22 11:16:06 spirit-laptop kernel: [   18.800000] Linux agpgart interface v0.102 (c) Dave Jones
Apr 22 11:16:06 spirit-laptop kernel: [   19.116000] sdhci: Secure Digital Host Controller Interface driver
Apr 22 11:16:06 spirit-laptop kernel: [   19.116000] sdhci: Copyright(c) Pierre Ossman
Apr 22 11:16:06 spirit-laptop kernel: [   19.116000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Apr 22 11:16:06 spirit-laptop kernel: [   19.116000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Apr 22 11:16:06 spirit-laptop kernel: [   19.116000] mmc0: SDHCI at 0xdf9fd400 irq 23 DMA
Apr 22 11:16:06 spirit-laptop kernel: [   19.576000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Apr 22 11:16:06 spirit-laptop kernel: [   19.612000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
Apr 22 11:16:06 spirit-laptop kernel: [   19.652000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
Apr 22 11:16:06 spirit-laptop kernel: [   19.652000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 22 11:16:06 spirit-laptop kernel: [   20.100000] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
Apr 22 11:16:06 spirit-laptop kernel: [   20.188000] hsfhda: no version for "cnxthsf_OsHdaCodecClearEventCallback" found: kernel tainted.
Apr 22 11:16:06 spirit-laptop kernel: [   21.856000] ttySHSF0 at MMIO 0x0 (irq = 1) is a Conexant HSF softmodem (HDA-14f12bfa:14f100c3-1)
Apr 22 11:16:06 spirit-laptop kernel: [   22.624000] lp: driver loaded but no devices found
Apr 22 11:16:06 spirit-laptop kernel: [   22.732000] ndiswrapper version 1.45 loaded (smp=yes)
Apr 22 11:16:06 spirit-laptop kernel: [   22.804000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 22 11:16:06 spirit-laptop kernel: [   22.804000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 22 11:16:06 spirit-laptop kernel: [   22.804000] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 22 11:16:06 spirit-laptop kernel: [   22.816000] ndiswrapper: using IRQ 16
Apr 22 11:16:06 spirit-laptop kernel: [   22.868000] cnxthsf_OsEventWaitTime(f7e4e0c0/HDA CodecUnsolicitedmessage, 40): returning OSEVENT_WAIT_TIMEOUT
Apr 22 11:16:06 spirit-laptop kernel: [   22.912000] cnxthsf_OsEventWaitTime(f7e4e0c0/HDA CodecUnsolicitedmessage, 40): returning OSEVENT_WAIT_TIMEOUT
Apr 22 11:16:06 spirit-laptop kernel: [   22.956000] cnxthsf_OsEventWaitTime(f7e4e0c0/HDA CodecUnsolicitedmessage, 40): returning OSEVENT_WAIT_TIMEOUT
Apr 22 11:16:06 spirit-laptop kernel: [   23.192000] wlan0: ethernet device 00:16:ce:3a:f4:5b using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4312.5.conf
Apr 22 11:16:06 spirit-laptop kernel: [   23.192000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 22 11:16:06 spirit-laptop kernel: [   23.192000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 22 11:16:06 spirit-laptop kernel: [   23.196000] usbcore: registered new interface driver ndiswrapper
Apr 22 11:16:06 spirit-laptop kernel: [   23.336000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Apr 22 11:16:06 spirit-laptop kernel: [   23.336000] vboxdrv: Successfully done.
Apr 22 11:16:06 spirit-laptop kernel: [   23.400000] Adding 2096472k swap on /dev/sda3.  Priority:-1 extents:1 across:2096472k
Apr 22 11:16:06 spirit-laptop kernel: [   23.724000] EXT3 FS on sda2, internal journal
Apr 22 11:16:06 spirit-laptop kernel: [   24.420000] kjournald starting.  Commit interval 5 seconds
Apr 22 11:16:06 spirit-laptop kernel: [   24.420000] EXT3 FS on sda4, internal journal
Apr 22 11:16:06 spirit-laptop kernel: [   24.420000] EXT3-fs: mounted filesystem with ordered data mode.
Apr 22 11:16:06 spirit-laptop kernel: [   25.912000] ACPI: AC Adapter [AC] (off-line)
Apr 22 11:16:06 spirit-laptop kernel: [   26.008000] ACPI: Battery Slot [BAT0] (battery present)
Apr 22 11:16:06 spirit-laptop kernel: [   26.040000] No dock devices found.
Apr 22 11:16:06 spirit-laptop kernel: [   26.084000] input: Lid Switch as /class/input/input3
Apr 22 11:16:06 spirit-laptop kernel: [   26.084000] ACPI: Lid Switch [LID]
Apr 22 11:16:06 spirit-laptop kernel: [   26.084000] input: Power Button (CM) as /class/input/input4
Apr 22 11:16:06 spirit-laptop kernel: [   26.084000] ACPI: Power Button (CM) [PBTN]
Apr 22 11:16:06 spirit-laptop kernel: [   26.084000] input: Sleep Button (CM) as /class/input/input5
Apr 22 11:16:06 spirit-laptop kernel: [   26.084000] ACPI: Sleep Button (CM) [SBTN]
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.075695] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.275722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.346820] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.347554] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a1'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.348158] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_7145'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.349356] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.350952] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.351399] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4312'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.351807] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.352235] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.353097] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.353509] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.353911] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.354313] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.354715] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.355115] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.355538] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.355942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.356351] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.356766] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.357625] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.358048] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.358469] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.397917] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.398376] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.398788] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.399258] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.399719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.400177] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.401694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.403068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.403532] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.403927] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.404320] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.404713] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.405105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.405494] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.405887] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.406274] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.406662] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.407050] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.407470] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.407888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.408278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.408678] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.409069] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.409457] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.409846] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.410232] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.410632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.411019] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.411433] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.411833] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.412219] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.412605] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.412992] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.413378] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.413766] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.414153] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.414540] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.414925] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.415310] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_c5_11_56_a8'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Apr 22 11:16:07 spirit-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 22 11:16:07 spirit-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 22 11:16:07 spirit-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr 22 11:16:07 spirit-laptop NetworkManager: <info>  Deactivating device eth0. 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.496648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ce_3a_f4_5b'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'ndiswrapper'. 
Apr 22 11:16:07 spirit-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 22 11:16:07 spirit-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 22 11:16:07 spirit-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr 22 11:16:07 spirit-laptop NetworkManager: <info>  Deactivating device eth1. 
Apr 22 11:16:07 spirit-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Invalid argument 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.586501] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.587012] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.587562] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_1'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.587965] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.588365] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.588765] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.589163] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.589562] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.589960] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.590359] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_1'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.590843] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_6'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.591240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_6'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.591672] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.592151] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.592548] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.592997] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.593436] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.593852] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.594251] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.594661] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.595058] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.595565] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.595962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.596359] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.596775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST96023AS_3MG01AFV'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.597172] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_A8080B8E080B5AA8'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.597567] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_f0574c52_2ef1_4fba_b5eb_44e5ca98cdd5'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.597962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_0be6ff40_2ccf_4202_bbb0_81bda64a66f9'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.608062] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_21bc092c_4396_4c69_8b73_a6b29316acd7'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.723253] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.753801] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.754242] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.754620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Apr 22 11:16:07 spirit-laptop NetworkManager: <debug> [1208877367.755081] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_TS_L532B'). 
Apr 22 11:16:08 spirit-laptop kernel: [   29.124000] Failure registering capabilities with primary security module.
Apr 22 11:16:08 spirit-laptop avahi-daemon[5097]: Found user 'avahi' (UID 104) and group 'avahi' (GID 108).
Apr 22 11:16:08 spirit-laptop avahi-daemon[5097]: Successfully dropped root privileges.
Apr 22 11:16:08 spirit-laptop avahi-daemon[5097]: avahi-daemon 0.6.20 starting up.
Apr 22 11:16:08 spirit-laptop avahi-daemon[5097]: Successfully called chroot().
Apr 22 11:16:08 spirit-laptop avahi-daemon[5097]: Successfully dropped remaining capabilities.
Apr 22 11:16:08 spirit-laptop avahi-daemon[5097]: No service file found in /etc/avahi/services.
Apr 22 11:16:08 spirit-laptop avahi-daemon[5097]: Network interface enumeration completed.
Apr 22 11:16:08 spirit-laptop avahi-daemon[5097]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 22 11:16:08 spirit-laptop avahi-daemon[5097]: Server startup complete. Host name is spirit-laptop.local. Local service cookie is 434168634.
Apr 22 11:16:09 spirit-laptop kernel: [   30.196000] ppdev: user-space parallel port driver
Apr 22 11:16:09 spirit-laptop kernel: [   30.432000] audit(1208877369.673:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5140 profile="/usr/sbin/cupsd"
Apr 22 11:16:10 spirit-laptop kernel: [   31.100000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
Apr 22 11:16:10 spirit-laptop kernel: [   31.100000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
Apr 22 11:16:10 spirit-laptop kernel: [   31.132000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 22 11:16:10 spirit-laptop mysqld_safe[5233]: started
Apr 22 11:16:11 spirit-laptop mysqld[5236]: 080422 11:16:11  InnoDB: Started; log sequence number 0 43665
Apr 22 11:16:11 spirit-laptop mysqld[5236]: 080422 11:16:11 [Note] /usr/sbin/mysqld: ready for connections.
Apr 22 11:16:11 spirit-laptop mysqld[5236]: Version: '5.0.45-Debian_1ubuntu3.3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
Apr 22 11:16:11 spirit-laptop /etc/mysql/debian-start[5271]: Upgrading MySQL tables if necessary.
Apr 22 11:16:12 spirit-laptop kernel: [   32.704000] apm: BIOS not found.
Apr 22 11:16:12 spirit-laptop /etc/mysql/debian-start[5277]: Looking for 'mysql' in: /usr/bin/mysql
Apr 22 11:16:12 spirit-laptop /etc/mysql/debian-start[5277]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Apr 22 11:16:12 spirit-laptop /etc/mysql/debian-start[5277]: This installation of MySQL is already upgraded to 5.0.45, use --force if you still need to run mysql_upgrade
Apr 22 11:16:12 spirit-laptop /etc/mysql/debian-start[5318]: Checking for insecure root accounts.
Apr 22 11:16:12 spirit-laptop /etc/mysql/debian-start[5322]: Checking for crashed MySQL tables.
Apr 22 11:16:14 spirit-laptop kernel: [   34.860000] [fglrx] total      GART = 130023424
Apr 22 11:16:14 spirit-laptop kernel: [   34.860000] [fglrx] free       GART = 114032640
Apr 22 11:16:14 spirit-laptop kernel: [   34.860000] [fglrx] max single GART = 114032640
Apr 22 11:16:14 spirit-laptop kernel: [   34.860000] [fglrx] total      LFB  = 134086656
Apr 22 11:16:14 spirit-laptop kernel: [   34.860000] [fglrx] free       LFB  = 110088192
Apr 22 11:16:14 spirit-laptop kernel: [   34.860000] [fglrx] max single LFB  = 110088192
Apr 22 11:16:14 spirit-laptop kernel: [   34.860000] [fglrx] total      Inv  = 0
Apr 22 11:16:14 spirit-laptop kernel: [   34.860000] [fglrx] free       Inv  = 0
Apr 22 11:16:14 spirit-laptop kernel: [   34.860000] [fglrx] max single Inv  = 0
Apr 22 11:16:14 spirit-laptop kernel: [   34.860000] [fglrx] total      TIM  = 0
Apr 22 11:16:14 spirit-laptop xinetd[5448]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Apr 22 11:16:14 spirit-laptop xinetd[5448]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Apr 22 11:16:14 spirit-laptop xinetd[5448]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Apr 22 11:16:14 spirit-laptop xinetd[5448]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Apr 22 11:16:14 spirit-laptop xinetd[5448]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Apr 22 11:16:15 spirit-laptop xinetd[5448]: Reading included configuration file: /etc/xinetd.d/vmware-authd [file=/etc/xinetd.d/vmware-authd] [line=28]
Apr 22 11:16:15 spirit-laptop xinetd[5448]: removing chargen
Apr 22 11:16:15 spirit-laptop xinetd[5448]: removing chargen
Apr 22 11:16:15 spirit-laptop xinetd[5448]: removing daytime
Apr 22 11:16:15 spirit-laptop xinetd[5448]: removing daytime
Apr 22 11:16:15 spirit-laptop xinetd[5448]: removing discard
Apr 22 11:16:15 spirit-laptop xinetd[5448]: removing discard
Apr 22 11:16:15 spirit-laptop xinetd[5448]: removing echo
Apr 22 11:16:15 spirit-laptop xinetd[5448]: removing echo
Apr 22 11:16:15 spirit-laptop xinetd[5448]: removing time
Apr 22 11:16:15 spirit-laptop xinetd[5448]: removing time
Apr 22 11:16:15 spirit-laptop xinetd[5448]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Apr 22 11:16:15 spirit-laptop xinetd[5448]: Started working: 1 available service
Apr 22 11:16:15 spirit-laptop dhcdbd: Started up.
Apr 22 11:16:15 spirit-laptop hcid[5544]: Bluetooth HCI daemon
Apr 22 11:16:15 spirit-laptop kernel: [   35.920000] Bluetooth: Core ver 2.11
Apr 22 11:16:15 spirit-laptop kernel: [   35.920000] NET: Registered protocol family 31
Apr 22 11:16:15 spirit-laptop kernel: [   35.920000] Bluetooth: HCI device and connection manager initialized
Apr 22 11:16:15 spirit-laptop kernel: [   35.920000] Bluetooth: HCI socket layer initialized
Apr 22 11:16:15 spirit-laptop hcid[5544]: Starting SDP server
Apr 22 11:16:15 spirit-laptop kernel: [   35.988000] Bluetooth: L2CAP ver 2.8
Apr 22 11:16:15 spirit-laptop kernel: [   35.988000] Bluetooth: L2CAP socket layer initialized
Apr 22 11:16:15 spirit-laptop hcid[5544]: Created local server at unix:abstract=/var/run/dbus-kLlwqIOz9r,guid=1f9c18c79b2c28b3518be800480e013f
Apr 22 11:16:15 spirit-laptop input[5561]: Bluetooth Input daemon
Apr 22 11:16:15 spirit-laptop input[5561]: Registered input manager path:/org/bluez/input
Apr 22 11:16:15 spirit-laptop kernel: [   36.168000] Bluetooth: RFCOMM socket layer initialized
Apr 22 11:16:15 spirit-laptop kernel: [   36.168000] Bluetooth: RFCOMM TTY layer initialized
Apr 22 11:16:15 spirit-laptop kernel: [   36.168000] Bluetooth: RFCOMM ver 1.8
Apr 22 11:16:15 spirit-laptop audio[5562]: Bluetooth Audio daemon
Apr 22 11:16:15 spirit-laptop audio[5562]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Apr 22 11:16:15 spirit-laptop audio[5562]: Unix socket created: 5
Apr 22 11:16:15 spirit-laptop audio[5562]: add_service_record: got record id 0x10000
Apr 22 11:16:15 spirit-laptop audio[5562]: add_service_record: got record id 0x10001
Apr 22 11:16:15 spirit-laptop audio[5562]: Registered manager path:/org/bluez/audio
Apr 22 11:16:15 spirit-laptop /usr/sbin/cron[5617]: (CRON) INFO (pidfile fd = 3)
Apr 22 11:16:15 spirit-laptop /usr/sbin/cron[5618]: (CRON) STARTUP (fork ok)
Apr 22 11:16:15 spirit-laptop /usr/sbin/cron[5618]: (*system*) WRONG SYMLINK OWNER (/etc/crontab)
Apr 22 11:16:15 spirit-laptop /usr/sbin/cron[5618]: (*system*anacron) WRONG SYMLINK OWNER (/etc/cron.d/anacron)
Apr 22 11:16:15 spirit-laptop /usr/sbin/cron[5618]: (*system*php5) WRONG SYMLINK OWNER (/etc/cron.d/php5)
Apr 22 11:16:15 spirit-laptop /usr/sbin/cron[5618]: (CRON) INFO (Running @reboot jobs)
Apr 22 11:17:09 spirit-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr 22 11:17:10 spirit-laptop kernel: [   90.732000] cnxthsf_OsEventWaitTime(f7e4e0c0/HDA CodecUnsolicitedmessage, 40): returning OSEVENT_WAIT_TIMEOUT
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Apr 22 11:17:11 spirit-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Will activate connection 'eth1/ResNet'. 
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Activation (eth1) started... 
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'ResNet' is unencrypted, no key needed. 
Apr 22 11:17:11 spirit-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Apr 22 11:17:11 spirit-laptop last message repeated 15 times
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Apr 22 11:17:12 spirit-laptop kernel: [   92.992000] NET: Registered protocol family 17
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: response was '0' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 5265734e6574' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 22 11:17:12 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 22 11:17:16 spirit-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'ResNet'. 
Apr 22 11:17:16 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 22 11:17:16 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Apr 22 11:17:17 spirit-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Apr 22 11:17:17 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Apr 22 11:17:17 spirit-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Apr 22 11:17:17 spirit-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Apr 22 11:17:18 spirit-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Apr 22 11:17:20 spirit-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Apr 22 11:17:20 spirit-laptop dhclient: DHCPNAK from 1.1.1.1
Apr 22 11:17:20 spirit-laptop avahi-autoipd(eth1)[6005]: Found user 'avahi-autoipd' (UID 108) and group 'avahi-autoipd' (GID 116).
Apr 22 11:17:20 spirit-laptop avahi-autoipd(eth1)[6005]: Successfully called chroot().
Apr 22 11:17:20 spirit-laptop avahi-autoipd(eth1)[6005]: Successfully dropped root privileges.
Apr 22 11:17:20 spirit-laptop avahi-autoipd(eth1)[6005]: fopen() failed: Permission denied
Apr 22 11:17:20 spirit-laptop avahi-autoipd(eth1)[6005]: Starting with address 169.254.7.248
Apr 22 11:17:26 spirit-laptop avahi-autoipd(eth1)[6005]: Callout BIND, address 169.254.7.248 on interface eth1
Apr 22 11:17:26 spirit-laptop avahi-daemon[5097]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.7.248.
Apr 22 11:17:26 spirit-laptop avahi-daemon[5097]: New relevant interface eth1.IPv4 for mDNS.
Apr 22 11:17:26 spirit-laptop avahi-daemon[5097]: Registering new address record for 169.254.7.248 on eth1.IPv4.
Apr 22 11:17:30 spirit-laptop avahi-autoipd(eth1)[6005]: Successfully claimed IP address 169.254.7.248
Apr 22 11:17:30 spirit-laptop avahi-autoipd(eth1)[6005]: fopen() failed: Permission denied
Apr 22 11:17:30 spirit-laptop NetworkManager: <info>  DHCP daemon state is now 10 (unknown) for interface eth1 
Apr 22 11:17:30 spirit-laptop avahi-autoipd(eth1)[6005]: Got SIGTERM, quitting.
Apr 22 11:17:30 spirit-laptop avahi-autoipd(eth1)[6005]: Callout STOP, address 169.254.7.248 on interface eth1
Apr 22 11:17:30 spirit-laptop avahi-daemon[5097]: Withdrawing address record for 169.254.7.248 on eth1.
Apr 22 11:17:30 spirit-laptop avahi-daemon[5097]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.7.248.
Apr 22 11:17:30 spirit-laptop avahi-daemon[5097]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 22 11:17:30 spirit-laptop avahi-autoipd(eth1)[6006]: client: RTNETLINK answers: No such process
Apr 22 11:17:31 spirit-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Apr 22 11:17:31 spirit-laptop dhclient: DHCPOFFER from 1.1.1.1
Apr 22 11:17:31 spirit-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Apr 22 11:17:31 spirit-laptop dhclient: DHCPACK from 1.1.1.1
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Joining mDNS multicast group on interface eth1.IPv4 with address 146.113.68.169.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: New relevant interface eth1.IPv4 for mDNS.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Registering new address record for 146.113.68.169 on eth1.IPv4.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Withdrawing address record for 146.113.68.169 on eth1.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Leaving mDNS multicast group on interface eth1.IPv4 with address 146.113.68.169.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Joining mDNS multicast group on interface eth1.IPv4 with address 146.113.68.169.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: New relevant interface eth1.IPv4 for mDNS.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Registering new address record for 146.113.68.169 on eth1.IPv4.
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Apr 22 11:17:31 spirit-laptop dhclient: bound to 146.113.68.169 -- renewal in 291166 seconds.
Apr 22 11:17:31 spirit-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Apr 22 11:17:31 spirit-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Apr 22 11:17:31 spirit-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>    address 146.113.68.169 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>    netmask 255.255.240.0 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>    broadcast 146.113.79.255 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>    gateway 146.113.64.1 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>    nameserver 146.113.64.100 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>    nameserver 146.113.16.120 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>    domain name 'knet.kzoo.edu' 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Apr 22 11:17:31 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Withdrawing address record for 146.113.68.169 on eth1.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Leaving mDNS multicast group on interface eth1.IPv4 with address 146.113.68.169.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Joining mDNS multicast group on interface eth1.IPv4 with address 146.113.68.169.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: New relevant interface eth1.IPv4 for mDNS.
Apr 22 11:17:31 spirit-laptop avahi-daemon[5097]: Registering new address record for 146.113.68.169 on eth1.IPv4.
Apr 22 11:17:32 spirit-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr 22 11:17:32 spirit-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr 22 11:17:32 spirit-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Apr 22 11:17:32 spirit-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Apr 22 11:17:32 spirit-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 22 11:18:45 spirit-laptop kernel: [  185.856000] NET: Registered protocol family 10
Apr 22 11:18:45 spirit-laptop kernel: [  185.856000] lo: Disabled Privacy Extensions
Apr 22 11:18:45 spirit-laptop kernel: [  185.856000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 22 11:18:46 spirit-laptop avahi-daemon[5097]: Registering new address record for fe80::216:ceff:fe3a:f45b on eth1.*.
Apr 22 11:18:55 spirit-laptop kernel: [  195.912000] eth1: no IPv6 routers present
Apr 22 11:23:39 spirit-laptop NetworkManager: <debug> [1208877819.295603] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0B:85:57:2A:E7 to 00:0B:85:57:2A:47 on wireless network 'ResNet' 
Apr 22 11:29:59 spirit-laptop syslogd 1.4.1#21ubuntu3: restart.


```

---

