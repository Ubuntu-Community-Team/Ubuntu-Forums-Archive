---
title: "Uninstall left Wubi partition"
date: 2008-07-06
forum: General Help
---

### Post by bagpiper on 2008-07-06
Hi all, 

First of all what a great app Wubi is. I had no problems installing in a few machines, but I found something I wanted to share with you.

I'm running WinXP SP3. I ran Wubi 8.04.1 and the setup worked OK until it booted and a message informing of "cannot find root resources" (or something like that). I then booted to WinXP and uninstalled Wubi, but it looks like the 15 GB that I defined when setting up Wubi are now "embedded" in the WinXP system and I don't have a way of deleting it. 

Any ideas on how to completely reset my Wubi install? 

BTW, I ran chkdsk /r on the Windows partition, looked at the size of the directory structure and I still could not find those 15 GB.

Thanks!

Additional note: 

After reading how to uninstall Wubi manually I was able to restart Wubi, and the actual message I was referring to above is "No root file system is defined. Please correct this from  the partition menu". Tks.

---

### Post by ago on 2008-07-07
See if you have some hidden files named found0000 in C:\ or C:\ubuntu

---

### Post by bagpiper on 2008-07-07
Thanks,

I have not found any of those files on the Windows side.

Actually I read a bit more on the forums and I was able to generate a log below. Not sure what exactly the issue is...

Appreciate any tips :)

```

Jul  7 07:09:10 ubuntu syslogd 1.5.0#1ubuntu1: restart.
Jul  7 07:09:10 ubuntu kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul  7 07:09:11 ubuntu kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Jul  7 07:09:11 ubuntu kernel: Symbols match kernel version 2.6.24.
Jul  7 07:09:11 ubuntu kernel: Loaded 20346 symbols from 99 modules.
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  7 07:09:11 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Jul  7 07:09:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul  7 07:09:11 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fe74000 (usable)
Jul  7 07:09:11 ubuntu kernel: [    0.000000]  BIOS-e820: 000000002fe74000 - 000000002fe76000 (ACPI NVS)
Jul  7 07:09:11 ubuntu kernel: [    0.000000]  BIOS-e820: 000000002fe76000 - 000000002fe97000 (ACPI data)
Jul  7 07:09:11 ubuntu kernel: [    0.000000]  BIOS-e820: 000000002fe97000 - 000000002ff00000 (reserved)
Jul  7 07:09:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul  7 07:09:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Jul  7 07:09:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
Jul  7 07:09:11 ubuntu kernel: [    0.000000] 766MB LOWMEM available.
Jul  7 07:09:11 ubuntu kernel: [    0.000000] found SMP MP-table at 000fe710
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 196212) 0 entries of 256 used
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Zone PFN ranges:
Jul  7 07:09:11 ubuntu kernel: [    0.000000]   DMA             0 ->     4096
Jul  7 07:09:11 ubuntu kernel: [    0.000000]   Normal       4096 ->   196212
Jul  7 07:09:11 ubuntu kernel: [    0.000000]   HighMem    196212 ->   196212
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Jul  7 07:09:11 ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul  7 07:09:11 ubuntu kernel: [    0.000000]     0:        0 ->   196212
Jul  7 07:09:11 ubuntu kernel: [    0.000000] On node 0 totalpages: 196212
Jul  7 07:09:11 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul  7 07:09:11 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul  7 07:09:11 ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Jul  7 07:09:11 ubuntu kernel: [    0.000000]   Normal zone: 1500 pages used for memmap
Jul  7 07:09:11 ubuntu kernel: [    0.000000]   Normal zone: 190616 pages, LIFO batch:31
Jul  7 07:09:11 ubuntu kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Jul  7 07:09:11 ubuntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Jul  7 07:09:11 ubuntu kernel: [    0.000000] DMI 2.3 present.
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FEB80 checksum 0
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: RSDP 000FEB80, 0014 (r0 DELL  )
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: RSDT 000FD2EA, 0034 (r1 DELL    2400           7 ASL        61)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: FACP 000FD31E, 0074 (r1 DELL    2400           7 ASL        61)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: DSDT FFFCBE22, 2404 (r1   DELL    dt_ex     1000 MSFT  100000D)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: FACS 2FE74000, 0040
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: SSDT FFFCE226, 00A7 (r1   DELL    st_ex     1000 MSFT  100000D)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: APIC 000FD392, 006C (r1 DELL    2400           7 ASL        61)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: BOOT 000FD3FE, 0028 (r1 DELL    2400           7 ASL        61)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Processor #0 15:2 APIC version 20
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul  7 07:09:11 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul  7 07:09:11 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2ff00000:ced00000)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul  7 07:09:11 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194680
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Kernel command line: debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.04.1-desktop-i386.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
Jul  7 07:09:11 ubuntu kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Initializing CPU#0
Jul  7 07:09:11 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jul  7 07:09:11 ubuntu kernel: [    0.000000] Detected 2193.580 MHz processor.
Jul  7 07:09:11 ubuntu kernel: [   23.080614] Console: colour VGA+ 80x25
Jul  7 07:09:11 ubuntu kernel: [   23.080620] console [tty0] enabled
Jul  7 07:09:11 ubuntu kernel: [   23.084992] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul  7 07:09:11 ubuntu kernel: [   23.086029] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  7 07:09:11 ubuntu kernel: [   23.106042] Memory: 765444k/784848k available (2177k kernel code, 18752k reserved, 1006k data, 368k init, 0k highmem)
Jul  7 07:09:11 ubuntu kernel: [   23.106121] virtual kernel memory layout:
Jul  7 07:09:11 ubuntu kernel: [   23.106122]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Jul  7 07:09:11 ubuntu kernel: [   23.106124]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul  7 07:09:11 ubuntu kernel: [   23.106125]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
Jul  7 07:09:11 ubuntu kernel: [   23.106126]     lowmem  : 0xc0000000 - 0xefe74000   ( 766 MB)
Jul  7 07:09:11 ubuntu kernel: [   23.106127]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Jul  7 07:09:11 ubuntu kernel: [   23.106129]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
Jul  7 07:09:11 ubuntu kernel: [   23.106130]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
Jul  7 07:09:11 ubuntu kernel: [   23.106516] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul  7 07:09:11 ubuntu kernel: [   23.106658] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Jul  7 07:09:11 ubuntu kernel: [   23.186605] Calibrating delay using timer specific routine.. 4391.56 BogoMIPS (lpj=8783130)
Jul  7 07:09:11 ubuntu kernel: [   23.186729] Security Framework initialized
Jul  7 07:09:11 ubuntu kernel: [   23.186784] SELinux:  Disabled at boot.
Jul  7 07:09:11 ubuntu kernel: [   23.186847] AppArmor: AppArmor initialized
Jul  7 07:09:11 ubuntu kernel: [   23.186900] Failure registering capabilities with primary security module.
Jul  7 07:09:11 ubuntu kernel: [   23.186959] Mount-cache hash table entries: 512
Jul  7 07:09:11 ubuntu kernel: [   23.187171] Initializing cgroup subsys ns
Jul  7 07:09:11 ubuntu kernel: [   23.187223] Initializing cgroup subsys cpuacct
Jul  7 07:09:11 ubuntu kernel: [   23.187284] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
Jul  7 07:09:11 ubuntu kernel: [   23.187661] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jul  7 07:09:11 ubuntu kernel: [   23.187745] CPU: L2 cache: 512K
Jul  7 07:09:11 ubuntu kernel: [   23.187794] CPU: Hyper-Threading is disabled
Jul  7 07:09:11 ubuntu kernel: [   23.187842] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
Jul  7 07:09:11 ubuntu kernel: [   23.188217] Compat vDSO mapped to ffffe000.
Jul  7 07:09:11 ubuntu kernel: [   23.188280] Checking 'hlt' instruction... OK.
Jul  7 07:09:11 ubuntu kernel: [   23.203099] SMP alternatives: switching to UP code
Jul  7 07:09:11 ubuntu kernel: [   23.205135] Freeing SMP alternatives: 11k freed
Jul  7 07:09:11 ubuntu kernel: [   23.205365] Early unpacking initramfs... done
Jul  7 07:09:11 ubuntu kernel: [   23.610437] ACPI: Core revision 20070126
Jul  7 07:09:11 ubuntu kernel: [   23.622511] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul  7 07:09:11 ubuntu kernel: [   23.646517] CPU0: Intel(R) Pentium(R) 4 CPU 2.20GHz stepping 09
Jul  7 07:09:11 ubuntu kernel: [   23.646684] Total of 1 processors activated (4391.56 BogoMIPS).
Jul  7 07:09:11 ubuntu kernel: [   23.646881] ENABLING IO-APIC IRQs
Jul  7 07:09:11 ubuntu kernel: [   23.647127] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul  7 07:09:11 ubuntu kernel: [   23.793637] Brought up 1 CPUs
Jul  7 07:09:11 ubuntu kernel: [   23.793715] CPU0 attaching sched-domain:
Jul  7 07:09:11 ubuntu kernel: [   23.793765]  domain 0: span 01
Jul  7 07:09:11 ubuntu kernel: [   23.793845]   groups: 01
Jul  7 07:09:11 ubuntu kernel: [   23.794207] net_namespace: 64 bytes
Jul  7 07:09:11 ubuntu kernel: [   23.794269] Booting paravirtualized kernel on bare hardware
Jul  7 07:09:11 ubuntu kernel: [   23.794996] Time:  7:08:27  Date: 07/07/08
Jul  7 07:09:11 ubuntu kernel: [   23.795078] NET: Registered protocol family 16
Jul  7 07:09:11 ubuntu kernel: [   23.795418] EISA bus registered
Jul  7 07:09:11 ubuntu kernel: [   23.795493] ACPI: bus type pci registered
Jul  7 07:09:11 ubuntu kernel: [   23.796711] PCI: PCI BIOS revision 2.10 entry at 0xfbc7f, last bus=1
Jul  7 07:09:11 ubuntu kernel: [   23.796763] PCI: Using configuration type 1
Jul  7 07:09:11 ubuntu kernel: [   23.796831] Setting up standard PCI resources
Jul  7 07:09:11 ubuntu kernel: [   23.806425] ACPI: EC: Look up EC in DSDT
Jul  7 07:09:11 ubuntu kernel: [   23.832385] ACPI: Interpreter enabled
Jul  7 07:09:11 ubuntu kernel: [   23.832437] ACPI: (supports S0 S1 S3 S4 S5)
Jul  7 07:09:11 ubuntu kernel: [   23.832669] ACPI: Using IOAPIC for interrupt routing
Jul  7 07:09:11 ubuntu kernel: [   23.869414] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul  7 07:09:11 ubuntu kernel: [   23.870029] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jul  7 07:09:11 ubuntu kernel: [   23.870031] * this clock source is slow. If you are sure your timer does not have
Jul  7 07:09:11 ubuntu kernel: [   23.870033] * this bug, please use "acpi_pm_good" to disable the workaround
Jul  7 07:09:11 ubuntu kernel: [   23.870252] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Jul  7 07:09:11 ubuntu kernel: [   23.870305] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Jul  7 07:09:11 ubuntu kernel: [   23.870746] PCI: Transparent bridge - 0000:00:1e.0
Jul  7 07:09:11 ubuntu kernel: [   23.870820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul  7 07:09:11 ubuntu kernel: [   23.871405] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Jul  7 07:09:11 ubuntu kernel: [   24.035121] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Jul  7 07:09:11 ubuntu kernel: [   24.035899] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
Jul  7 07:09:11 ubuntu kernel: [   24.036670] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Jul  7 07:09:11 ubuntu kernel: [   24.037448] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Jul  7 07:09:11 ubuntu kernel: [   24.038217] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Jul  7 07:09:11 ubuntu kernel: [   24.039061] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Jul  7 07:09:11 ubuntu kernel: [   24.039907] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Jul  7 07:09:11 ubuntu kernel: [   24.040757] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Jul  7 07:09:11 ubuntu kernel: [   24.041463] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul  7 07:09:11 ubuntu kernel: [   24.041556] pnp: PnP ACPI init
Jul  7 07:09:11 ubuntu kernel: [   24.041613] ACPI: bus type pnp registered
Jul  7 07:09:11 ubuntu kernel: [   24.065741] pnp: PnP ACPI: found 12 devices
Jul  7 07:09:11 ubuntu kernel: [   24.065795] ACPI: ACPI bus type pnp unregistered
Jul  7 07:09:11 ubuntu kernel: [   24.065847] PnPBIOS: Disabled by ACPI PNP
Jul  7 07:09:11 ubuntu kernel: [   24.066212] PCI: Using ACPI for IRQ routing
Jul  7 07:09:11 ubuntu kernel: [   24.066263] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul  7 07:09:11 ubuntu kernel: [   24.081106] NET: Registered protocol family 8
Jul  7 07:09:11 ubuntu kernel: [   24.081156] NET: Registered protocol family 20
Jul  7 07:09:11 ubuntu kernel: [   24.081304] AppArmor: AppArmor Filesystem Enabled
Jul  7 07:09:11 ubuntu kernel: [   24.085079] Time: tsc clocksource has been installed.
Jul  7 07:09:11 ubuntu kernel: [   24.093120] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093173] system 00:00: iomem range 0x100000-0xffffff could not be reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093226] system 00:00: iomem range 0x1000000-0x2fe73fff could not be reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093287] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093340] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093402] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093463] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093516] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093576] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093651] system 00:0b: ioport range 0x800-0x85f has been reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093703] system 00:0b: ioport range 0xc00-0xc7f has been reserved
Jul  7 07:09:11 ubuntu kernel: [   24.093755] system 00:0b: ioport range 0x860-0x8ff could not be reserved
Jul  7 07:09:11 ubuntu kernel: [   24.124347] PCI: Bridge: 0000:00:1e.0
Jul  7 07:09:11 ubuntu kernel: [   24.124396]   IO window: disabled.
Jul  7 07:09:11 ubuntu kernel: [   24.124448]   MEM window: fe900000-feafffff
Jul  7 07:09:11 ubuntu kernel: [   24.125369]   PREFETCH window: disabled.
Jul  7 07:09:11 ubuntu kernel: [   24.125432] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Jul  7 07:09:11 ubuntu kernel: [   24.125497] NET: Registered protocol family 2
Jul  7 07:09:11 ubuntu kernel: [   24.165061] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  7 07:09:11 ubuntu kernel: [   24.165618] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul  7 07:09:11 ubuntu kernel: [   24.167108] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul  7 07:09:11 ubuntu kernel: [   24.168074] TCP: Hash tables configured (established 131072 bind 65536)
Jul  7 07:09:11 ubuntu kernel: [   24.168136] TCP reno registered
Jul  7 07:09:11 ubuntu kernel: [   24.177210] checking if image is initramfs... it is
Jul  7 07:09:11 ubuntu kernel: [   24.624172] Switched to high resolution mode on CPU 0
Jul  7 07:09:11 ubuntu kernel: [   24.975604] Freeing initrd memory: 7667k freed
Jul  7 07:09:11 ubuntu kernel: [   24.975945] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
Jul  7 07:09:11 ubuntu kernel: [   24.975997] Simple Boot Flag at 0x7a set to 0x1
Jul  7 07:09:11 ubuntu kernel: [   24.976617] audit: initializing netlink socket (disabled)
Jul  7 07:09:11 ubuntu kernel: [   24.976688] audit(1215414508.768:1): initialized
Jul  7 07:09:11 ubuntu kernel: [   24.979542] VFS: Disk quotas dquot_6.5.1
Jul  7 07:09:11 ubuntu kernel: [   24.979706] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  7 07:09:11 ubuntu kernel: [   24.979953] io scheduler noop registered
Jul  7 07:09:11 ubuntu kernel: [   24.980003] io scheduler anticipatory registered
Jul  7 07:09:11 ubuntu kernel: [   24.980052] io scheduler deadline registered
Jul  7 07:09:11 ubuntu kernel: [   24.980113] io scheduler cfq registered (default)
Jul  7 07:09:11 ubuntu kernel: [   24.980179] Boot video device is 0000:00:02.0
Jul  7 07:09:11 ubuntu kernel: [   24.980647] isapnp: Scanning for PnP cards...
Jul  7 07:09:11 ubuntu kernel: [   25.334426] isapnp: No Plug & Play device found
Jul  7 07:09:11 ubuntu kernel: [   25.380342] Real Time Clock Driver v1.12ac
Jul  7 07:09:11 ubuntu kernel: [   25.380525] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul  7 07:09:11 ubuntu kernel: [   25.380728] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul  7 07:09:11 ubuntu kernel: [   25.381859] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul  7 07:09:11 ubuntu kernel: [   25.382997] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul  7 07:09:11 ubuntu kernel: [   25.383164] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul  7 07:09:11 ubuntu kernel: [   25.383375] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Jul  7 07:09:11 ubuntu kernel: [   25.386356] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  7 07:09:11 ubuntu kernel: [   25.386410] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul  7 07:09:11 ubuntu kernel: [   25.390888] mice: PS/2 mouse device common for all mice
Jul  7 07:09:11 ubuntu kernel: [   25.391100] EISA: Probing bus 0 at eisa.0
Jul  7 07:09:11 ubuntu kernel: [   25.391186] EISA: Detected 0 cards.
Jul  7 07:09:11 ubuntu kernel: [   25.391235] cpuidle: using governor ladder
Jul  7 07:09:11 ubuntu kernel: [   25.391282] cpuidle: using governor menu
Jul  7 07:09:11 ubuntu kernel: [   25.391456] NET: Registered protocol family 1
Jul  7 07:09:11 ubuntu kernel: [   25.391542] Using IPI No-Shortcut mode
Jul  7 07:09:11 ubuntu kernel: [   25.391631] registered taskstats version 1
Jul  7 07:09:11 ubuntu kernel: [   25.391793]   Magic number: 0:336:116
Jul  7 07:09:11 ubuntu kernel: [   25.391976] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  7 07:09:11 ubuntu kernel: [   25.392026] EDD information not available.
Jul  7 07:09:11 ubuntu kernel: [   25.392625] Freeing unused kernel memory: 368k freed
Jul  7 07:09:11 ubuntu kernel: [   25.426673] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul  7 07:09:11 ubuntu kernel: [   25.679659] fuse init (API version 7.9)
Jul  7 07:09:11 ubuntu kernel: [   25.713154] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul  7 07:09:11 ubuntu kernel: [   26.421325] usbcore: registered new interface driver usbfs
Jul  7 07:09:11 ubuntu kernel: [   26.421414] usbcore: registered new interface driver hub
Jul  7 07:09:11 ubuntu kernel: [   26.448896] usbcore: registered new device driver usb
Jul  7 07:09:11 ubuntu kernel: [   26.498027] SCSI subsystem initialized
Jul  7 07:09:11 ubuntu kernel: [   26.512228] USB Universal Host Controller Interface driver v3.0
Jul  7 07:09:11 ubuntu kernel: [   26.512382] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  7 07:09:11 ubuntu kernel: [   26.512488] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Jul  7 07:09:11 ubuntu kernel: [   26.512541] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul  7 07:09:11 ubuntu kernel: [   26.513014] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jul  7 07:09:11 ubuntu kernel: [   26.513115] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
Jul  7 07:09:11 ubuntu kernel: [   26.513369] usb usb1: configuration #1 chosen from 1 choice
Jul  7 07:09:11 ubuntu kernel: [   26.513450] hub 1-0:1.0: USB hub found
Jul  7 07:09:11 ubuntu kernel: [   26.513503] hub 1-0:1.0: 2 ports detected
Jul  7 07:09:11 ubuntu kernel: [   26.592316] libata version 3.00 loaded.
Jul  7 07:09:11 ubuntu kernel: [   26.616686] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Jul  7 07:09:11 ubuntu kernel: [   26.616801] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Jul  7 07:09:11 ubuntu kernel: [   26.616855] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul  7 07:09:11 ubuntu kernel: [   26.616936] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jul  7 07:09:11 ubuntu kernel: [   26.617028] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
Jul  7 07:09:11 ubuntu kernel: [   26.617237] usb usb2: configuration #1 chosen from 1 choice
Jul  7 07:09:11 ubuntu kernel: [   26.617320] hub 2-0:1.0: USB hub found
Jul  7 07:09:11 ubuntu kernel: [   26.617374] hub 2-0:1.0: 2 ports detected
Jul  7 07:09:11 ubuntu kernel: [   26.697453] Floppy drive(s): fd0 is 1.44M
Jul  7 07:09:11 ubuntu kernel: [   26.714454] FDC 0 is a post-1991 82077
Jul  7 07:09:11 ubuntu kernel: [   26.720466] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul  7 07:09:11 ubuntu kernel: [   26.720582] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Jul  7 07:09:11 ubuntu kernel: [   26.720636] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul  7 07:09:11 ubuntu kernel: [   26.720716] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jul  7 07:09:11 ubuntu kernel: [   26.720806] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
Jul  7 07:09:11 ubuntu kernel: [   26.721008] usb usb3: configuration #1 chosen from 1 choice
Jul  7 07:09:11 ubuntu kernel: [   26.721090] hub 3-0:1.0: USB hub found
Jul  7 07:09:11 ubuntu kernel: [   26.721143] hub 3-0:1.0: 2 ports detected
Jul  7 07:09:11 ubuntu kernel: [   26.824482] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Jul  7 07:09:11 ubuntu kernel: [   26.824601] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Jul  7 07:09:11 ubuntu kernel: [   26.824654] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul  7 07:09:11 ubuntu kernel: [   26.824741] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jul  7 07:09:11 ubuntu kernel: [   26.828714] ehci_hcd 0000:00:1d.7: debug port 1
Jul  7 07:09:11 ubuntu kernel: [   26.828769] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Jul  7 07:09:11 ubuntu kernel: [   26.828840] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80800
Jul  7 07:09:11 ubuntu kernel: [   26.844101] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul  7 07:09:11 ubuntu kernel: [   26.844350] usb usb4: configuration #1 chosen from 1 choice
Jul  7 07:09:11 ubuntu kernel: [   26.844432] hub 4-0:1.0: USB hub found
Jul  7 07:09:11 ubuntu kernel: [   26.844488] hub 4-0:1.0: 6 ports detected
Jul  7 07:09:11 ubuntu kernel: [   26.948291] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  7 07:09:11 ubuntu kernel: [   26.967893] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
Jul  7 07:09:11 ubuntu kernel: [   26.967960] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
Jul  7 07:09:11 ubuntu kernel: [   26.968025] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
Jul  7 07:09:11 ubuntu kernel: [   26.968082] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
Jul  7 07:09:11 ubuntu kernel: [   27.007884] ssb: Sonics Silicon Backplane found on PCI device 0000:01:04.0
Jul  7 07:09:11 ubuntu kernel: [   27.013382] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Jul  7 07:09:11 ubuntu kernel: [   27.013547] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Jul  7 07:09:11 ubuntu kernel: [   27.013612] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Jul  7 07:09:11 ubuntu kernel: [   27.018930] ata_piix 0000:00:1f.1: version 2.12
Jul  7 07:09:11 ubuntu kernel: [   27.019010] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Jul  7 07:09:11 ubuntu kernel: [   27.019171] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Jul  7 07:09:11 ubuntu kernel: [   27.022461] scsi0 : ata_piix
Jul  7 07:09:11 ubuntu kernel: [   27.024886] scsi1 : ata_piix
Jul  7 07:09:11 ubuntu kernel: [   27.025008] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jul  7 07:09:11 ubuntu kernel: [   27.025062] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jul  7 07:09:11 ubuntu kernel: [   27.188711] ata1.00: ATA-5: WDC WD1000BB-00CAA1, 17.07W17, max UDMA/100
Jul  7 07:09:11 ubuntu kernel: [   27.188772] ata1.00: 195371568 sectors, multi 8: LBA 
Jul  7 07:09:11 ubuntu kernel: [   27.204659] ata1.00: configured for UDMA/100
Jul  7 07:09:11 ubuntu kernel: [   27.678998] ata2.00: ATAPI: SAMSUNG DVD-ROM SD-616T, F310, max UDMA/33
Jul  7 07:09:11 ubuntu kernel: [   27.679090] ata2.01: ATAPI: SAMSUNG CD-R/RW SW-248F, R602, max UDMA/33
Jul  7 07:09:11 ubuntu kernel: [   27.842614] ata2.00: configured for UDMA/33
Jul  7 07:09:11 ubuntu kernel: [   28.014272] ata2.01: configured for UDMA/33
Jul  7 07:09:11 ubuntu kernel: [   28.014492] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1000BB-00C 17.0 PQ: 0 ANSI: 5
Jul  7 07:09:11 ubuntu kernel: [   28.015086] scsi 1:0:0:0: CD-ROM            SAMSUNG  DVD-ROM SD-616T  F310 PQ: 0 ANSI: 5
Jul  7 07:09:11 ubuntu kernel: [   28.016755] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-R/RW SW-248F  R602 PQ: 0 ANSI: 5
Jul  7 07:09:11 ubuntu kernel: [   28.017104] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 17 (level, low) -> IRQ 20
Jul  7 07:09:11 ubuntu kernel: [   28.029537] Driver 'sd' needs updating - please use bus_type methods
Jul  7 07:09:11 ubuntu kernel: [   28.029724] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Jul  7 07:09:11 ubuntu kernel: [   28.029794] sd 0:0:0:0: [sda] Write Protect is off
Jul  7 07:09:11 ubuntu kernel: [   28.029844] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul  7 07:09:11 ubuntu kernel: [   28.029939] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  7 07:09:11 ubuntu kernel: [   28.030070] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Jul  7 07:09:11 ubuntu kernel: [   28.030136] sd 0:0:0:0: [sda] Write Protect is off
Jul  7 07:09:11 ubuntu kernel: [   28.030185] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul  7 07:09:11 ubuntu kernel: [   28.030258] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  7 07:09:11 ubuntu kernel: [   28.030323]  sda:<6>ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
Jul  7 07:09:11 ubuntu kernel: [   28.034055] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
Jul  7 07:09:11 ubuntu kernel: [   28.034113] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
Jul  7 07:09:11 ubuntu kernel: [   28.040968] Driver 'sr' needs updating - please use bus_type methods
Jul  7 07:09:11 ubuntu kernel: [   28.044075]  sda1
Jul  7 07:09:11 ubuntu kernel: [   28.044164]  sda: p1 exceeds device capacity
Jul  7 07:09:11 ubuntu kernel: [   28.044310] sd 0:0:0:0: [sda] Attached SCSI disk
Jul  7 07:09:11 ubuntu kernel: [   28.052649] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
Jul  7 07:09:11 ubuntu kernel: [   28.052711] Uniform CD-ROM driver Revision: 3.20
Jul  7 07:09:11 ubuntu kernel: [   28.052839] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul  7 07:09:11 ubuntu kernel: [   28.053356] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  7 07:09:11 ubuntu kernel: [   28.053431] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul  7 07:09:11 ubuntu kernel: [   28.053526] sr 1:0:1:0: Attached scsi generic sg2 type 5
Jul  7 07:09:11 ubuntu kernel: [   28.061465] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Jul  7 07:09:11 ubuntu kernel: [   28.061607] sr 1:0:1:0: Attached scsi CD-ROM sr1
Jul  7 07:09:11 ubuntu kernel: [   28.077965] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
Jul  7 07:09:11 ubuntu kernel: [   28.078059] b44.c:v2.0
Jul  7 07:09:11 ubuntu kernel: [   28.098280] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0b:db:bd:eb:7b
Jul  7 07:09:11 ubuntu kernel: [   28.244495] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.244558] sda: rw=0, want=390716737, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.244609] Buffer I/O error on device sda1, logical block 195358336
Jul  7 07:09:11 ubuntu kernel: [   28.244661] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.244711] sda: rw=0, want=390716739, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.244761] Buffer I/O error on device sda1, logical block 195358337
Jul  7 07:09:11 ubuntu kernel: [   28.245726] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.245776] sda: rw=0, want=390716741, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.245827] Buffer I/O error on device sda1, logical block 195358338
Jul  7 07:09:11 ubuntu kernel: [   28.245878] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.245926] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.245976] Buffer I/O error on device sda1, logical block 195358339
Jul  7 07:09:11 ubuntu kernel: [   28.246028] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.246077] sda: rw=0, want=390716737, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.246127] Buffer I/O error on device sda1, logical block 195358336
Jul  7 07:09:11 ubuntu kernel: [   28.246178] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.246227] sda: rw=0, want=390716739, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.246276] Buffer I/O error on device sda1, logical block 195358337
Jul  7 07:09:11 ubuntu kernel: [   28.246327] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.246376] sda: rw=0, want=390716741, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.246426] Buffer I/O error on device sda1, logical block 195358338
Jul  7 07:09:11 ubuntu kernel: [   28.246477] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.246526] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.246576] Buffer I/O error on device sda1, logical block 195358339
Jul  7 07:09:11 ubuntu kernel: [   28.246638] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.246689] sda: rw=0, want=390716849, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.246739] Buffer I/O error on device sda1, logical block 195358392
Jul  7 07:09:11 ubuntu kernel: [   28.246790] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.246840] sda: rw=0, want=390716851, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.246889] Buffer I/O error on device sda1, logical block 195358393
Jul  7 07:09:11 ubuntu kernel: [   28.246940] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.246989] sda: rw=0, want=390716853, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.247039] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.247087] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.247138] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.247187] sda: rw=0, want=390716849, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.247237] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.247287] sda: rw=0, want=390716851, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.247336] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.247385] sda: rw=0, want=390716853, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.247434] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.247483] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.247725] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.247781] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.247852] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.247902] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.247960] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.248011] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.248067] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.248117] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.248173] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.248222] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.248279] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.248329] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.248385] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.248435] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.248494] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.248545] sda: rw=0, want=390716801, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.248595] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.248644] sda: rw=0, want=390716803, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.248694] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.248743] sda: rw=0, want=390716805, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.248793] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.248842] sda: rw=0, want=390716807, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.248898] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.248949] sda: rw=0, want=390716849, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.248999] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.249048] sda: rw=0, want=390716851, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.249097] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.249146] sda: rw=0, want=390716853, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.249196] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.249244] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.249301] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.249351] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.249407] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.249456] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.327552] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
Jul  7 07:09:11 ubuntu kernel: [   28.330970] SGI XFS Quota Management subsystem
Jul  7 07:09:11 ubuntu kernel: [   28.340704] JFS: nTxBlock = 6045, nTxLock = 48360
Jul  7 07:09:11 ubuntu kernel: [   28.401108] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.401171] sda: rw=0, want=390716737, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.401223] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.401292] sda: rw=0, want=390716739, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.401343] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.401392] sda: rw=0, want=390716741, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.401442] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.401491] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.401542] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.401591] sda: rw=0, want=390716737, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.401641] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.401690] sda: rw=0, want=390716739, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.401740] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.401789] sda: rw=0, want=390716741, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.401838] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.401887] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.401947] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.401997] sda: rw=0, want=390716849, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.402047] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.402097] sda: rw=0, want=390716851, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.402147] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.402196] sda: rw=0, want=390716853, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.402246] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.402295] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.402345] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.402394] sda: rw=0, want=390716849, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.402443] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.402492] sda: rw=0, want=390716851, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.402543] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.402591] sda: rw=0, want=390716853, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.402642] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.402690] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.402934] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.402991] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.403061] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.403112] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.403171] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.403221] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.403278] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.403328] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.403384] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.403434] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.403490] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.403539] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.403596] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.403646] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.403704] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.403754] sda: rw=0, want=390716801, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.403804] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.403853] sda: rw=0, want=390716803, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.403904] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.403953] sda: rw=0, want=390716805, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.404003] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.404052] sda: rw=0, want=390716807, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.404108] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.404159] sda: rw=0, want=390716849, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.404209] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.404259] sda: rw=0, want=390716851, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.404308] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.404357] sda: rw=0, want=390716853, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.404407] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.404456] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.404512] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.404562] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.404618] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.404668] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.413989] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.414052] sda: rw=0, want=390716737, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.414103] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.414153] sda: rw=0, want=390716739, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.414203] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.414252] sda: rw=0, want=390716741, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.414302] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.414351] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.414402] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.414452] sda: rw=0, want=390716737, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.414502] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.414551] sda: rw=0, want=390716739, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.414602] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.414651] sda: rw=0, want=390716741, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.414701] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.414750] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.414810] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.414861] sda: rw=0, want=390716849, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.414911] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.414960] sda: rw=0, want=390716851, limit=195371568

Jul  7 07:09:11 ubuntu kernel: [   28.415010] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.415059] sda: rw=0, want=390716853, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.415109] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.415158] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.415208] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.415257] sda: rw=0, want=390716849, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.415306] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.415356] sda: rw=0, want=390716851, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.415405] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.415455] sda: rw=0, want=390716853, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.415504] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.415553] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.415797] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.415853] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.415924] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.415973] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.416033] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.416084] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.416140] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.416190] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.417142] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.417191] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.417276] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.417327] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.417384] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.417433] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.417493] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.417544] sda: rw=0, want=390716801, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.417594] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.417644] sda: rw=0, want=390716803, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.417693] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.417742] sda: rw=0, want=390716805, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.417792] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.417841] sda: rw=0, want=390716807, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.417898] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.417948] sda: rw=0, want=390716849, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.417998] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.418046] sda: rw=0, want=390716851, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.418097] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.418146] sda: rw=0, want=390716853, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.418196] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.418245] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.418301] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.418351] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.418408] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.418458] sda: rw=0, want=390716865, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.969089] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.969153] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.969206] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.969255] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.969315] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.969365] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.969415] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.969464] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.969584] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.969635] sda: rw=0, want=390716807, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.969685] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.969734] sda: rw=0, want=390716807, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   28.969791] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   28.969841] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   29.072560] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   29.072623] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   29.072684] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   29.072734] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   29.072845] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   29.072896] sda: rw=0, want=390716807, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   29.072952] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   29.073002] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   29.139635] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   29.139697] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   29.139757] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   29.139807] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   29.139953] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   29.140004] sda: rw=0, want=390716807, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   29.140060] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   29.140111] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   29.164999] loop: module loaded
Jul  7 07:09:11 ubuntu kernel: [   29.254892] ISO 9660 Extensions: Microsoft Joliet Level 3
Jul  7 07:09:11 ubuntu kernel: [   29.266679] ISO 9660 Extensions: RRIP_1991A
Jul  7 07:09:11 ubuntu kernel: [   29.282877] Registering unionfs 1.4
Jul  7 07:09:11 ubuntu kernel: [   29.282935] unionfs: debugging is not enabled
Jul  7 07:09:11 ubuntu kernel: [   29.320879] squashfs: version 3.3 (2007/10/31) Phillip Lougher
Jul  7 07:09:11 ubuntu kernel: [   42.310924] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   42.310987] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   42.311038] printk: 104 messages suppressed.
Jul  7 07:09:11 ubuntu kernel: [   42.311087] Buffer I/O error on device sda1, logical block 48839584
Jul  7 07:09:11 ubuntu kernel: [   42.311148] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   42.311199] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   42.311249] Buffer I/O error on device sda1, logical block 48839598
Jul  7 07:09:11 ubuntu kernel: [   42.311360] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   42.311411] sda: rw=0, want=390716807, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   42.311466] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   42.311516] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   55.363459] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   55.363528] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   55.363578] printk: 2 messages suppressed.
Jul  7 07:09:11 ubuntu kernel: [   55.363627] Buffer I/O error on device sda1, logical block 48839584
Jul  7 07:09:11 ubuntu kernel: [   55.363687] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   55.363737] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   55.363788] Buffer I/O error on device sda1, logical block 48839598
Jul  7 07:09:11 ubuntu kernel: [   55.363908] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   55.363959] sda: rw=0, want=390716807, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   55.364009] Buffer I/O error on device sda1, logical block 48839592
Jul  7 07:09:11 ubuntu kernel: [   55.364066] attempt to access beyond end of device
Jul  7 07:09:11 ubuntu kernel: [   55.364116] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:11 ubuntu kernel: [   56.217073] Linux agpgart interface v0.102
Jul  7 07:09:11 ubuntu kernel: [   56.370811] agpgart: Detected an Intel 830M Chipset.
Jul  7 07:09:11 ubuntu kernel: [   56.371010] agpgart: Detected 892K stolen memory.
Jul  7 07:09:11 ubuntu kernel: [   56.447033] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  7 07:09:11 ubuntu kernel: [   56.470612] agpgart: AGP aperture is 128M @ 0xe8000000
Jul  7 07:09:11 ubuntu kernel: [   56.534547] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Jul  7 07:09:11 ubuntu kernel: [   56.598268] iTCO_vendor_support: vendor-support=0
Jul  7 07:09:11 ubuntu kernel: [   56.646225] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Jul  7 07:09:11 ubuntu kernel: [   56.646474] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)
Jul  7 07:09:11 ubuntu kernel: [   56.646585] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jul  7 07:09:11 ubuntu kernel: [   56.726168] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  7 07:09:11 ubuntu kernel: [   57.049430] intel_rng: FWH not detected
Jul  7 07:09:11 ubuntu kernel: [   57.210227] input: Power Button (FF) as /devices/virtual/input/input2
Jul  7 07:09:11 ubuntu kernel: [   57.221121] ACPI: Power Button (FF) [PWRF]
Jul  7 07:09:11 ubuntu kernel: [   57.221360] input: Power Button (CM) as /devices/virtual/input/input3
Jul  7 07:09:11 ubuntu kernel: [   57.237077] ACPI: Power Button (CM) [VBTN]
Jul  7 07:09:11 ubuntu kernel: [   58.678992] input: PC Speaker as /devices/platform/pcspkr/input/input4
Jul  7 07:09:11 ubuntu kernel: [   59.120798] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
Jul  7 07:09:11 ubuntu kernel: [   59.120935] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Jul  7 07:09:11 ubuntu kernel: [   59.540901] intel8x0_measure_ac97_clock: measured 54868 usecs
Jul  7 07:09:11 ubuntu kernel: [   59.540960] intel8x0: clocking to 48000
Jul  7 07:09:11 ubuntu kernel: [   60.106773] b43-phy0: Broadcom 4318 WLAN found
Jul  7 07:09:11 ubuntu kernel: [   60.147801] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
Jul  7 07:09:11 ubuntu kernel: [   60.147915] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
Jul  7 07:09:11 ubuntu kernel: [   60.192295] phy0: Selected rate control algorithm 'simple'
Jul  7 07:09:11 ubuntu kernel: [   60.663382] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input5
Jul  7 07:09:11 ubuntu kernel: [   60.696068] parport_pc 00:0a: reported by Plug and Play ACPI
Jul  7 07:09:11 ubuntu kernel: [   60.696179] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Jul  7 07:09:11 ubuntu kernel: [   60.698296] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jul  7 07:09:11 ubuntu kernel: [   63.401752] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  7 07:09:11 ubuntu kernel: [   65.892451] No dock devices found.
Jul  7 07:09:11 ubuntu NetworkManager: <info>  starting... 
Jul  7 07:09:11 ubuntu avahi-daemon[8054]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jul  7 07:09:11 ubuntu avahi-daemon[8054]: Successfully dropped root privileges.
Jul  7 07:09:11 ubuntu avahi-daemon[8054]: avahi-daemon 0.6.22 starting up.
Jul  7 07:09:11 ubuntu avahi-daemon[8054]: Successfully called chroot().
Jul  7 07:09:11 ubuntu avahi-daemon[8054]: Successfully dropped remaining capabilities.
Jul  7 07:09:11 ubuntu avahi-daemon[8055]: chroot.c: open() failed: No such file or directory
Jul  7 07:09:11 ubuntu avahi-daemon[8054]: Failed to open /etc/resolv.conf: Invalid argument
Jul  7 07:09:11 ubuntu avahi-daemon[8054]: No service file found in /etc/avahi/services.
Jul  7 07:09:11 ubuntu avahi-daemon[8054]: Network interface enumeration completed.
Jul  7 07:09:11 ubuntu avahi-daemon[8054]: Registering HINFO record with values 'I686'/'LINUX'.
Jul  7 07:09:11 ubuntu avahi-daemon[8054]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1957523640.
Jul  7 07:09:11 ubuntu kernel: [   67.612155] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul  7 07:09:11 ubuntu kernel: [   67.612164] apm: overridden by ACPI.
Jul  7 07:09:11 ubuntu kernel: [   67.707947] lp0: using parport0 (interrupt-driven).
Jul  7 07:09:11 ubuntu kernel: [   67.740376] ppdev: user-space parallel port driver
Jul  7 07:09:12 ubuntu dhcdbd: Started up.
Jul  7 07:09:13 ubuntu kernel: [   69.288297] attempt to access beyond end of device
Jul  7 07:09:13 ubuntu kernel: [   69.288309] sda: rw=0, want=390716743, limit=195371568
Jul  7 07:09:13 ubuntu kernel: [   69.288313] printk: 1 messages suppressed.
Jul  7 07:09:13 ubuntu kernel: [   69.288316] Buffer I/O error on device sda1, logical block 48839584
Jul  7 07:09:13 ubuntu kernel: [   69.289120] attempt to access beyond end of device
Jul  7 07:09:13 ubuntu kernel: [   69.289126] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:13 ubuntu kernel: [   69.289129] Buffer I/O error on device sda1, logical block 48839598
Jul  7 07:09:13 ubuntu kernel: [   69.289735] attempt to access beyond end of device
Jul  7 07:09:13 ubuntu kernel: [   69.289741] sda: rw=0, want=390716807, limit=195371568
Jul  7 07:09:13 ubuntu kernel: [   69.289744] Buffer I/O error on device sda1, logical block 48839592
Jul  7 07:09:13 ubuntu kernel: [   69.290291] attempt to access beyond end of device
Jul  7 07:09:13 ubuntu kernel: [   69.290296] sda: rw=0, want=390716855, limit=195371568
Jul  7 07:09:13 ubuntu NetworkManager: <info>  eth0: Device is fully-supported using driver '(null)'. 
Jul  7 07:09:13 ubuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul  7 07:09:13 ubuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul  7 07:09:13 ubuntu NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jul  7 07:09:13 ubuntu NetworkManager: <info>  Deactivating device eth0. 
Jul  7 07:09:13 ubuntu kernel: [   69.420471] input: b43-phy0 as /devices/virtual/input/input6
Jul  7 07:09:13 ubuntu kernel: [   69.519931] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
Jul  7 07:09:13 ubuntu kernel: [   69.520038] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
Jul  7 07:09:13 ubuntu firmware_helper[8346]: main: error loading '/lib/firmware/b43/ucode5.fw' for device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.0/ssb0:0/firmware/ssb0:0' with driver '(unknown)'
Jul  7 07:09:13 ubuntu hcid[8353]: Bluetooth HCI daemon
Jul  7 07:09:13 ubuntu kernel: [   69.625917] Bluetooth: Core ver 2.11
Jul  7 07:09:13 ubuntu kernel: [   69.626921] NET: Registered protocol family 31
Jul  7 07:09:13 ubuntu kernel: [   69.626928] Bluetooth: HCI device and connection manager initialized
Jul  7 07:09:13 ubuntu kernel: [   69.626934] Bluetooth: HCI socket layer initialized
Jul  7 07:09:13 ubuntu hcid[8353]: Starting SDP server
Jul  7 07:09:13 ubuntu kernel: [   69.681563] Bluetooth: L2CAP ver 2.9
Jul  7 07:09:13 ubuntu kernel: [   69.681570] Bluetooth: L2CAP socket layer initialized
Jul  7 07:09:13 ubuntu hcid[8353]: Created local server at unix:abstract=/var/run/dbus-9hL83YdS9X,guid=65f994b81fc0519546368f1b4871c119
Jul  7 07:09:13 ubuntu audio[8369]: Bluetooth Audio daemon
Jul  7 07:09:13 ubuntu audio[8369]: Unix socket created: 5
Jul  7 07:09:13 ubuntu audio[8369]: audio.conf: Key file does not have key 'Enable'
Jul  7 07:09:13 ubuntu audio[8369]: audio.conf: Key file does not have key 'Disable'
Jul  7 07:09:13 ubuntu kernel: [   69.729910] Bluetooth: RFCOMM socket layer initialized
Jul  7 07:09:13 ubuntu kernel: [   69.730225] Bluetooth: RFCOMM TTY layer initialized
Jul  7 07:09:13 ubuntu kernel: [   69.730231] Bluetooth: RFCOMM ver 1.8
Jul  7 07:09:13 ubuntu input[8374]: Bluetooth Input daemon
Jul  7 07:09:13 ubuntu audio[8369]: add_service_record: got record id 0x10000
Jul  7 07:09:13 ubuntu audio[8369]: audio.conf: Key file does not have key 'Disable'
Jul  7 07:09:13 ubuntu audio[8369]: audio.conf: Key file does not have group 'A2DP'
Jul  7 07:09:13 ubuntu last message repeated 3 times
Jul  7 07:09:13 ubuntu audio[8369]: SEP 0x806d248 registered: type:0 codec:0 seid:1
Jul  7 07:09:13 ubuntu audio[8369]: add_service_record: got record id 0x10001
Jul  7 07:09:13 ubuntu audio[8369]: add_service_record: got record id 0x10002
Jul  7 07:09:13 ubuntu audio[8369]: add_service_record: got record id 0x10003
Jul  7 07:09:13 ubuntu audio[8369]: Registered manager path:/org/bluez/audio
Jul  7 07:09:13 ubuntu input[8374]: Registered input manager path:/org/bluez/input
Jul  7 07:09:14 ubuntu kernel: [   70.250094] NET: Registered protocol family 10
Jul  7 07:09:14 ubuntu kernel: [   70.250788] lo: Disabled Privacy Extensions
Jul  7 07:09:14 ubuntu kernel: [   70.252485] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  7 07:09:15 ubuntu NetworkManager: <info>  wlan0: Device is fully-supported using driver '(null)'. 
Jul  7 07:09:15 ubuntu NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Jul  7 07:09:15 ubuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul  7 07:09:15 ubuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul  7 07:09:15 ubuntu NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Jul  7 07:09:15 ubuntu NetworkManager: <info>  Deactivating device wlan0. 
Jul  7 07:09:16 ubuntu kernel: [   72.059697] [drm] Initialized drm 1.1.0 20060810
Jul  7 07:09:16 ubuntu kernel: [   72.066774] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  7 07:09:16 ubuntu kernel: [   72.066788] PCI: Setting latency timer of device 0000:00:02.0 to 64
Jul  7 07:09:16 ubuntu kernel: [   72.067439] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul  7 07:09:16 ubuntu kernel: [   72.284321] input: b43-phy0 as /devices/virtual/input/input7
Jul  7 07:09:16 ubuntu firmware_helper[8449]: main: error loading '/lib/firmware/b43/ucode5.fw' for device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.0/ssb0:0/firmware/ssb0:0' with driver '(unknown)'
Jul  7 07:09:16 ubuntu kernel: [   72.348324] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
Jul  7 07:09:16 ubuntu kernel: [   72.348336] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
Jul  7 07:09:17 ubuntu kernel: [   72.936793] b44: eth0: Link is up at 10 Mbps, half duplex.
Jul  7 07:09:17 ubuntu kernel: [   72.936800] b44: eth0: Flow control is off for TX and off for RX.
Jul  7 07:09:17 ubuntu kernel: [   72.940428] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul  7 07:09:17 ubuntu NetworkManager: <debug> [1215414557.881578] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD_R/RW_SW_248F'). 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jul  7 07:09:17 ubuntu NetworkManager: <debug> [1215414557.883495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Jul  7 07:09:17 ubuntu NetworkManager: <debug> [1215414557.884414] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jul  7 07:09:17 ubuntu NetworkManager: <debug> [1215414557.885284] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2562_drm_i915_card0'). 
Jul  7 07:09:17 ubuntu NetworkManager: <debug> [1215414557.886221] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Jul  7 07:09:17 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Activation (eth0) started... 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jul  7 07:09:17 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jul  7 07:09:18 ubuntu avahi-daemon[8054]: Registering new address record for fe80::20b:dbff:febd:eb7b on eth0.*.
Jul  7 07:09:18 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 
Jul  7 07:09:18 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Jul  7 07:09:18 ubuntu dhclient: wmaster0: unknown hardware address type 801
Jul  7 07:09:18 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jul  7 07:09:18 ubuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Jul  7 07:09:20 ubuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Jul  7 07:09:20 ubuntu dhclient: wmaster0: unknown hardware address type 801
Jul  7 07:09:20 ubuntu kernel: [   76.033964] NET: Registered protocol family 17
Jul  7 07:09:20 ubuntu ubiquity[8498]: Ubiquity 1.8.12
Jul  7 07:09:21 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul  7 07:09:24 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jul  7 07:09:27 ubuntu kernel: [   83.102247] eth0: no IPv6 routers present
Jul  7 07:09:28 ubuntu ubiquity[8498]: log-output -t ubiquity laptop-detect
Jul  7 07:09:29 ubuntu ubiquity[8498]: log-output -t ubiquity fontconfig-voodoo --auto --force --quiet
Jul  7 07:09:31 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jul  7 07:09:33 ubuntu kernel: [   89.371041] input: b43-phy0 as /devices/virtual/input/input8
Jul  7 07:09:33 ubuntu kernel: [   89.437377] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
Jul  7 07:09:33 ubuntu kernel: [   89.437390] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
Jul  7 07:09:33 ubuntu firmware_helper[8576]: main: error loading '/lib/firmware/b43/ucode5.fw' for device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.0/ssb0:0/firmware/ssb0:0' with driver '(unknown)'
Jul  7 07:09:33 ubuntu NetworkManager: <debug> [1215414573.813941] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_4'). 
Jul  7 07:09:33 ubuntu dhclient: DHCPOFFER of 192.168.1.4 from 192.168.1.1
Jul  7 07:09:33 ubuntu dhclient: DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
Jul  7 07:09:33 ubuntu ubiquity[8498]: switched to page stepLanguage
Jul  7 07:09:34 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
Jul  7 07:09:34 ubuntu localechooser: info: Set languagechooser/language-name = 'English'
Jul  7 07:09:34 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'US'
Jul  7 07:09:34 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jul  7 07:09:34 ubuntu localechooser: info: LANGNAME=English
Jul  7 07:09:34 ubuntu localechooser: info: line=English;0;en;US;en_US.UTF-8;UTF-8;;kbd=lat0-sun16(utf8)
Jul  7 07:09:34 ubuntu localechooser: info: Set debian-installer/language = 'en'
Jul  7 07:09:34 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jul  7 07:09:34 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Jul  7 07:09:34 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jul  7 07:09:34 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'kbd=lat0-sun16(utf8)'
Jul  7 07:09:34 ubuntu localechooser: info: Set debconf/language = 'en'
Jul  7 07:09:34 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jul  7 07:09:34 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jul  7 07:09:35 ubuntu ubiquity[8498]: debconffilter_done: Language (current: Language)
Jul  7 07:09:35 ubuntu ubiquity[8498]: Step_before = stepLanguage
Jul  7 07:09:35 ubuntu dhclient: DHCPACK of 192.168.1.4 from 192.168.1.1
Jul  7 07:09:35 ubuntu avahi-daemon[8054]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.4.
Jul  7 07:09:35 ubuntu avahi-daemon[8054]: New relevant interface eth0.IPv4 for mDNS.
Jul  7 07:09:35 ubuntu avahi-daemon[8054]: Registering new address record for 192.168.1.4 on eth0.IPv4.
Jul  7 07:09:35 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 
Jul  7 07:09:35 ubuntu NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Jul  7 07:09:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jul  7 07:09:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Jul  7 07:09:35 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul  7 07:09:35 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul  7 07:09:35 ubuntu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jul  7 07:09:35 ubuntu NetworkManager: <info>    address 192.168.1.4 
Jul  7 07:09:35 ubuntu NetworkManager: <info>    netmask 255.255.255.0 
Jul  7 07:09:35 ubuntu NetworkManager: <info>    broadcast 192.168.1.255 
Jul  7 07:09:35 ubuntu NetworkManager: <info>    gateway 192.168.1.1 
Jul  7 07:09:35 ubuntu NetworkManager: <info>    nameserver 192.168.1.1 
Jul  7 07:09:35 ubuntu NetworkManager: <info>    hostname 'ubuntu' 
Jul  7 07:09:35 ubuntu NetworkManager: <info>    domain name 'home' 
Jul  7 07:09:35 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul  7 07:09:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jul  7 07:09:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jul  7 07:09:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jul  7 07:09:35 ubuntu avahi-daemon[8054]: Withdrawing address record for 192.168.1.4 on eth0.
Jul  7 07:09:35 ubuntu avahi-daemon[8054]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.4.
Jul  7 07:09:35 ubuntu dhclient: bound to 192.168.1.4 -- renewal in 37290 seconds.
Jul  7 07:09:35 ubuntu avahi-daemon[8054]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul  7 07:09:35 ubuntu avahi-daemon[8054]: Withdrawing address record for fe80::20b:dbff:febd:eb7b on eth0.
Jul  7 07:09:35 ubuntu avahi-daemon[8054]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.4.
Jul  7 07:09:35 ubuntu avahi-daemon[8054]: New relevant interface eth0.IPv4 for mDNS.
Jul  7 07:09:35 ubuntu avahi-daemon[8054]: Registering new address record for 192.168.1.4 on eth0.IPv4.
Jul  7 07:09:36 ubuntu NetworkManager: <info>  Clearing nscd hosts cache. 
Jul  7 07:09:36 ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jul  7 07:09:36 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jul  7 07:09:36 ubuntu NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Jul  7 07:09:36 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jul  7 07:09:37 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
Jul  7 07:09:37 ubuntu localechooser: info: Set languagechooser/language-name-fb = 'English'
Jul  7 07:09:37 ubuntu ntpdate[8728]: step time server 91.189.94.4 offset 14397.822827 sec
Jul  7 11:09:35 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'US'
Jul  7 11:09:35 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jul  7 11:09:35 ubuntu localechooser: info: Set debconf/language = ''
Jul  7 11:09:35 ubuntu localechooser: info: Set countrychooser/country-name = 'United States'
Jul  7 11:09:35 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jul  7 11:09:35 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jul  7 11:09:35 ubuntu kernel: [   93.525821] input: b43-phy0 as /devices/virtual/input/input9
Jul  7 11:09:35 ubuntu kernel: [   93.593856] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
Jul  7 11:09:35 ubuntu kernel: [   93.593869] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
Jul  7 11:09:35 ubuntu firmware_helper[8816]: main: error loading '/lib/firmware/b43/ucode5.fw' for device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.0/ssb0:0/firmware/ssb0:0' with driver '(unknown)'
Jul  7 11:09:35 ubuntu NetworkManager: <debug> [1215428975.788745] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'). 
Jul  7 11:09:35 ubuntu avahi-daemon[8054]: Registering new address record for fe80::20b:dbff:febd:eb7b on eth0.*.
Jul  7 11:09:36 ubuntu ubiquity[8498]: debconffilter_done: Timezone (current: Timezone)
Jul  7 11:09:36 ubuntu ubiquity[8498]: Step_before = stepLanguage
Jul  7 11:09:37 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down 
Jul  7 11:09:38 ubuntu ubiquity[8498]: log-output -t ubiquity setxkbmap -model pc105 -layout us
Jul  7 11:09:39 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Jul  7 11:09:39 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Jul  7 11:09:39 ubuntu ubiquity[8498]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Jul  7 11:09:39 ubuntu ubiquity[8498]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
Jul  7 11:09:39 ubuntu ubiquity[8498]: Step_before = stepLanguage
Jul  7 11:09:42 ubuntu kernel: [  100.119450] end_request: I/O error, dev fd0, sector 0
Jul  7 11:09:42 ubuntu kernel: [  100.143403] end_request: I/O error, dev fd0, sector 0
Jul  7 11:09:42 ubuntu partman-auto-loop: Error: Partition number 1 not found in /var/lib/partman/devices/=dev=sda
Jul  7 11:09:44 ubuntu kernel: [  102.906390] eth0: no IPv6 routers present



```

---

### Post by ago on 2008-07-07
I would suggest a clean installation

---

