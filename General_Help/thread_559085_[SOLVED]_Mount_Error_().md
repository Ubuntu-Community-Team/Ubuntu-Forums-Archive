---
title: "[SOLVED] Mount Error (?)"
date: 2007-09-24
forum: General Help
---

### Post by Rabidmonkey1 on 2007-09-24
Hi everyone!

I am having some trouble and need some help, and will be very grateful to whomever can help me.

It seems I am having some kind of mount error on dev/sda.  I run Ubuntu Studio, and what happens to me is that Icons and such start disappearing, programs stop responding, files become inaccessible and then finally the system stops responding, the terminal takes over the screen and I see something about "Rejecting dead I/O Device"...  which means I have to restart, and then...sometimes the computer fails to recognize that the SATA drive is even attached any more.

Anyways, this problem seemed to occur after the first File System Check.  Don't know if that provides any clues...

I'm going to attempt to get back into Ubuntu and get into the system logs and see if I can post them because right now, I'm accessing the forums on my backup Windows machine...:(

Again, any help would be much appreciated.  Thanks!

-Bob

---

### Post by jamesjtucker on 2007-09-24
Sounds like it could be dying hardware?

Check your bios settings and see if you can switch the sata mode to compatible from whatever it is currently. 

and check /var/log/kern.log for messages that might help!

---

### Post by ddrichardson on 2007-09-24
We need to see the logs - but it seems that something is about to go the way of elvis.

---

### Post by Rabidmonkey1 on 2007-09-25
Hi everyone, thanks for the quick replies.

Here is where I'm at:

A simple unplug-replug of the Sata drives makes the BIOS recognize them again...don't ask my why, but it works haha.  

(FYI - dual booting here from two sepearte HD's.  Linux w/ Grub on the primary, Windows on another - and never the twain shall meet).  Both the hard drives are relatively new 500 gb Western Digitals - I had to previously send in two because of manufacturing errors, and these new ones came back clean and fine, and I made sure to run them through a full slew of diagnostics.

In GRUB I have several Kernal Options, because for whatever reason, Ubuntu Studio doesn't get rid of the older Kernal selections - so I have Generic and Low Latency option for the current Kernal and the past three iterations or os for a total of some 7 or 8 different options.  

I usually use the Low Latency version of the most current kernal, but since I was having problems with it crashing, I decided to boot up an older version, and here we are.

I'm pouring through all these system logs, and I'm having trouble finding anything specific.  It seems like none of the errors get recorded and written to the HD because, well, it unmounts...

So, unless there is maybe something I should be looking for that I'm missing, I'm not sure what to post...

Here is the Kern.log from one session...it looks like it just drops off the map at the end... (sorry for the extreme length...)

```
Sep 24 16:56:47 ubuntustudio kernel: Inspecting /boot/System.map-2.6.20-16-lowlatency
Sep 24 16:56:47 ubuntustudio kernel: Loaded 25002 symbols from /boot/System.map-2.6.20-16-lowlatency.
Sep 24 16:56:47 ubuntustudio kernel: Symbols match kernel version 2.6.20.
Sep 24 16:56:47 ubuntustudio kernel: No module symbols loaded - kernel modules not enabled. 
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Linux version 2.6.20-16-lowlatency (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP PREEMPT Fri Aug 31 00:58:46 UTC 2007 (Ubuntu Unofficial)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] sanitize start
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] sanitize end
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 00000000cfef0000 end: 00000000cfff0000 type: 1
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 00000000cfff0000 size: 0000000000003000 end: 00000000cfff3000 type: 4
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 00000000cfff3000 size: 000000000000d000 end: 00000000d0000000 type: 3
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 0000000100000000 size: 0000000020000000 end: 0000000120000000 type: 1
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfff0000 (usable)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000cfff3000 (ACPI NVS)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]  BIOS-e820: 00000000cfff3000 - 00000000d0000000 (ACPI data)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Warning only 4GB will be used.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Use a PAE enabled kernel.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] 3200MB HIGHMEM available.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] 896MB LOWMEM available.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] found SMP MP-table at 000f3d40
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Zone PFN ranges:
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]   DMA             0 ->     4096
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]   Normal       4096 ->   229376
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]   HighMem    229376 ->  1048576
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]     0:        0 ->  1048576
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] On node 0 totalpages: 1048576
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]   HighMem zone: 6400 pages used for memmap
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] DMI 2.2 present.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f7e40
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0xcfff3040
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0xcfff30c0
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0xcfff90c0
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0xcfff9300
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0xcfff9000
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Processor #0 15:11 APIC version 16
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Processor #1 15:11 APIC version 16
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: IRQ14 used by override.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] ACPI: IRQ15 used by override.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Allocating PCI resources starting at d1000000 (gap: d0000000:10000000)
Sep 24 16:56:47 ubuntustudio kernel: [    0.000000] Detected 2210.278 MHz processor.
Sep 24 16:56:47 ubuntustudio kernel: [   22.736328] Built 1 zonelists.  Total pages: 1040384
Sep 24 16:56:47 ubuntustudio kernel: [   22.736331] Kernel command line: root=UUID=73ebee5f-2466-425e-a939-04d97c696465 ro quiet splash
Sep 24 16:56:47 ubuntustudio kernel: [   22.736444] mapped APIC to ffffd000 (fee00000)
Sep 24 16:56:47 ubuntustudio kernel: [   22.736447] mapped IOAPIC to ffffc000 (fec00000)
Sep 24 16:56:47 ubuntustudio kernel: [   22.736449] Enabling fast FPU save and restore... done.
Sep 24 16:56:47 ubuntustudio kernel: [   22.736451] Enabling unmasked SIMD FPU exception support... done.
Sep 24 16:56:47 ubuntustudio kernel: [   22.736457] Initializing CPU#0
Sep 24 16:56:47 ubuntustudio kernel: [   22.736509] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep 24 16:56:47 ubuntustudio kernel: [   22.736581] spurious 8259A interrupt: IRQ7.
Sep 24 16:56:47 ubuntustudio kernel: [   22.737990] Console: colour VGA+ 80x25
Sep 24 16:56:47 ubuntustudio kernel: [   22.738276] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 24 16:56:47 ubuntustudio kernel: [   22.738610] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 24 16:56:47 ubuntustudio kernel: [   22.865604] Memory: 3362264k/4194304k available (2019k kernel code, 44288k reserved, 902k data, 328k init, 2490304k highmem)
Sep 24 16:56:47 ubuntustudio kernel: [   22.865612] virtual kernel memory layout:
Sep 24 16:56:47 ubuntustudio kernel: [   22.865613]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Sep 24 16:56:47 ubuntustudio kernel: [   22.865614]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 24 16:56:47 ubuntustudio kernel: [   22.865615]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep 24 16:56:47 ubuntustudio kernel: [   22.865617]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep 24 16:56:47 ubuntustudio kernel: [   22.865618]       .init : 0xc03e1000 - 0xc0433000   ( 328 kB)
Sep 24 16:56:47 ubuntustudio kernel: [   22.865619]       .data : 0xc02f8dd5 - 0xc03da6d4   ( 902 kB)
Sep 24 16:56:47 ubuntustudio kernel: [   22.865620]       .text : 0xc0100000 - 0xc02f8dd5   (2019 kB)
Sep 24 16:56:47 ubuntustudio kernel: [   22.865622] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep 24 16:56:47 ubuntustudio kernel: [   22.925358] Calibrating delay using timer specific routine.. 4421.73 BogoMIPS (lpj=2210866)
Sep 24 16:56:47 ubuntustudio kernel: [   22.925397] Security Framework v1.0.0 initialized
Sep 24 16:56:47 ubuntustudio kernel: [   22.925404] SELinux:  Disabled at boot.
Sep 24 16:56:47 ubuntustudio kernel: [   22.925418] Mount-cache hash table entries: 512
Sep 24 16:56:47 ubuntustudio kernel: [   22.925527] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
Sep 24 16:56:47 ubuntustudio kernel: [   22.925534] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 24 16:56:47 ubuntustudio kernel: [   22.925536] CPU: L2 Cache: 512K (64 bytes/line)
Sep 24 16:56:47 ubuntustudio kernel: [   22.925539] CPU 0(2) -> Core 0
Sep 24 16:56:47 ubuntustudio kernel: [   22.925540] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
Sep 24 16:56:47 ubuntustudio kernel: [   22.925549] Compat vDSO mapped to ffffe000.
Sep 24 16:56:47 ubuntustudio kernel: [   22.925552] Remapping vsyscall page to ffffe000
Sep 24 16:56:47 ubuntustudio kernel: [   22.925560] Checking 'hlt' instruction... OK.
Sep 24 16:56:47 ubuntustudio kernel: [   22.929450] SMP alternatives: switching to UP code
Sep 24 16:56:47 ubuntustudio kernel: [   22.929694] Early unpacking initramfs... done
Sep 24 16:56:47 ubuntustudio kernel: [   23.179432] ACPI: Core revision 20060707
Sep 24 16:56:47 ubuntustudio kernel: [   23.181841] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Sep 24 16:56:47 ubuntustudio kernel: [   23.185428] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
Sep 24 16:56:47 ubuntustudio kernel: [   23.185447] SMP alternatives: switching to SMP code
Sep 24 16:56:47 ubuntustudio kernel: [   23.185497] Booting processor 1/1 eip 3000
Sep 24 16:56:47 ubuntustudio kernel: [   23.196095] Initializing CPU#1
Sep 24 16:56:47 ubuntustudio kernel: [   23.256434] Calibrating delay using timer specific routine.. 4419.74 BogoMIPS (lpj=2209873)
Sep 24 16:56:47 ubuntustudio kernel: [   23.256440] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
Sep 24 16:56:47 ubuntustudio kernel: [   23.256445] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 24 16:56:47 ubuntustudio kernel: [   23.256447] CPU: L2 Cache: 512K (64 bytes/line)
Sep 24 16:56:47 ubuntustudio kernel: [   23.256450] CPU 1(2) -> Core 1
Sep 24 16:56:47 ubuntustudio kernel: [   23.256451] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
Sep 24 16:56:47 ubuntustudio kernel: [   23.256201] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
Sep 24 16:56:47 ubuntustudio kernel: [   23.256214] Total of 2 processors activated (8841.47 BogoMIPS).
Sep 24 16:56:47 ubuntustudio kernel: [   23.256353] ENABLING IO-APIC IRQs
Sep 24 16:56:47 ubuntustudio kernel: [   23.256546] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Sep 24 16:56:47 ubuntustudio kernel: [   23.368000] checking TSC synchronization across 2 CPUs: 
Sep 24 16:56:47 ubuntustudio kernel: [    0.000001] CPU#0 had -174 usecs TSC skew, fixed it up.
Sep 24 16:56:47 ubuntustudio kernel: [    0.000003] CPU#1 had 174 usecs TSC skew, fixed it up.
Sep 24 16:56:47 ubuntustudio kernel: [    0.001002] Brought up 2 CPUs
Sep 24 16:56:47 ubuntustudio kernel: [    0.065142] migration_cost=196
Sep 24 16:56:47 ubuntustudio kernel: [    0.065353] Booting paravirtualized kernel on bare hardware
Sep 24 16:56:47 ubuntustudio kernel: [    0.065430] Time: 16:56:31  Date: 08/24/107
Sep 24 16:56:47 ubuntustudio kernel: [    0.065458] NET: Registered protocol family 16
Sep 24 16:56:47 ubuntustudio kernel: [    0.065531] EISA bus registered
Sep 24 16:56:47 ubuntustudio kernel: [    0.065534] ACPI: bus type pci registered
Sep 24 16:56:47 ubuntustudio kernel: [    0.070251] PCI: PCI BIOS revision 3.00 entry at 0xfa8b0, last bus=5
Sep 24 16:56:47 ubuntustudio kernel: [    0.070253] PCI: Using configuration type 1
Sep 24 16:56:47 ubuntustudio kernel: [    0.070255] Setting up standard PCI resources
Sep 24 16:56:47 ubuntustudio kernel: [    0.078921] ACPI: Interpreter enabled
Sep 24 16:56:47 ubuntustudio kernel: [    0.078925] ACPI: Using IOAPIC for interrupt routing
Sep 24 16:56:47 ubuntustudio kernel: [    0.079357] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 24 16:56:47 ubuntustudio kernel: [    0.079360] PCI: Probing PCI hardware (bus 00)
Sep 24 16:56:47 ubuntustudio kernel: [    0.081354] PCI: Transparent bridge - 0000:00:09.0
Sep 24 16:56:47 ubuntustudio kernel: [    0.081547] Boot video device is 0000:05:00.0
Sep 24 16:56:47 ubuntustudio kernel: [    0.081602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep 24 16:56:47 ubuntustudio kernel: [    0.139620] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Sep 24 16:56:47 ubuntustudio kernel: [    0.141236] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.141512] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.141785] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Sep 24 16:56:47 ubuntustudio kernel: [    0.142062] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Sep 24 16:56:47 ubuntustudio kernel: [    0.142333] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.142604] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Sep 24 16:56:47 ubuntustudio kernel: [    0.142881] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.143152] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Sep 24 16:56:47 ubuntustudio kernel: [    0.143420] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.143692] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.143968] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Sep 24 16:56:47 ubuntustudio kernel: [    0.144239] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Sep 24 16:56:47 ubuntustudio kernel: [    0.144515] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.144793] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Sep 24 16:56:47 ubuntustudio kernel: [    0.145079] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Sep 24 16:56:47 ubuntustudio kernel: [    0.145358] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.145666] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.145970] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.146269] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.146566] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.146797] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.147116] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.147428] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.147741] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.148056] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.148366] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.148676] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.148991] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.149301] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.149618] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.149942] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.150261] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:56:47 ubuntustudio kernel: [    0.153220] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep 24 16:56:47 ubuntustudio kernel: [    0.153228] pnp: PnP ACPI init
Sep 24 16:56:47 ubuntustudio kernel: [    0.159091] pnp: PnP ACPI: found 15 devices
Sep 24 16:56:47 ubuntustudio kernel: [    0.159094] PnPBIOS: Disabled by ACPI PNP
Sep 24 16:56:47 ubuntustudio kernel: [    0.159141] PCI: Using ACPI for IRQ routing
Sep 24 16:56:47 ubuntustudio kernel: [    0.159144] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep 24 16:56:47 ubuntustudio kernel: [    0.216313] NET: Registered protocol family 8
Sep 24 16:56:47 ubuntustudio kernel: [    0.216314] NET: Registered protocol family 20
Sep 24 16:56:47 ubuntustudio kernel: [    0.216604] pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
Sep 24 16:56:47 ubuntustudio kernel: [    0.216607] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
Sep 24 16:56:47 ubuntustudio kernel: [    0.216610] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
Sep 24 16:56:47 ubuntustudio kernel: [    0.216612] pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
Sep 24 16:56:47 ubuntustudio kernel: [    0.216614] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
Sep 24 16:56:47 ubuntustudio kernel: [    0.216616] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
Sep 24 16:56:47 ubuntustudio kernel: [    0.216852] PCI: Bridge: 0000:00:09.0
Sep 24 16:56:47 ubuntustudio kernel: [    0.216854]   IO window: a000-afff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216857]   MEM window: fde00000-fdefffff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216860]   PREFETCH window: fdf00000-fdffffff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216862] PCI: Bridge: 0000:00:0b.0
Sep 24 16:56:47 ubuntustudio kernel: [    0.216864]   IO window: 9000-9fff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216866]   MEM window: fdd00000-fddfffff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216869]   PREFETCH window: fdc00000-fdcfffff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216871] PCI: Bridge: 0000:00:0c.0
Sep 24 16:56:47 ubuntustudio kernel: [    0.216873]   IO window: 8000-8fff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216875]   MEM window: fdb00000-fdbfffff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216878]   PREFETCH window: fda00000-fdafffff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216880] PCI: Bridge: 0000:00:0d.0
Sep 24 16:56:47 ubuntustudio kernel: [    0.216882]   IO window: 7000-7fff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216884]   MEM window: fd900000-fd9fffff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216887]   PREFETCH window: fd800000-fd8fffff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216891] PCI: Bridge: 0000:00:0e.0
Sep 24 16:56:47 ubuntustudio kernel: [    0.216893]   IO window: 6000-6fff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216895]   MEM window: fa000000-fcffffff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216898]   PREFETCH window: d0000000-dfffffff
Sep 24 16:56:47 ubuntustudio kernel: [    0.216904] PCI: Setting latency timer of device 0000:00:09.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    0.216911] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    0.216916] PCI: Setting latency timer of device 0000:00:0c.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    0.216922] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    0.216927] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    0.216960] NET: Registered protocol family 2
Sep 24 16:56:47 ubuntustudio kernel: [    0.227855] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 24 16:56:47 ubuntustudio kernel: [    0.227982] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Sep 24 16:56:47 ubuntustudio kernel: [    0.228922] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
Sep 24 16:56:47 ubuntustudio kernel: [    0.229399] TCP: Hash tables configured (established 131072 bind 65536)
Sep 24 16:56:47 ubuntustudio kernel: [    0.229402] TCP reno registered
Sep 24 16:56:47 ubuntustudio kernel: [    0.231908] checking if image is initramfs... it is
Sep 24 16:56:47 ubuntustudio kernel: [    0.722572] Freeing initrd memory: 6881k freed
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] audit: initializing netlink socket (disabled)
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] audit(1190652991.530:1): initialized
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] highmem bounce pool size: 64 pages
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] VFS: Disk quotas dquot_6.5.1
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] io scheduler noop registered
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] io scheduler anticipatory registered
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] io scheduler deadline registered
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] io scheduler cfq registered (default)
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
Sep 24 16:56:47 ubuntustudio kernel: [    1.235000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] assign_interrupt_mode Found MSI capability
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] Allocate Port Service[0000:00:0b.0:pcie00]
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] assign_interrupt_mode Found MSI capability
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] Allocate Port Service[0000:00:0c.0:pcie00]
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] assign_interrupt_mode Found MSI capability
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] Allocate Port Service[0000:00:0d.0:pcie00]
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] assign_interrupt_mode Found MSI capability
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] Allocate Port Service[0000:00:0e.0:pcie00]
Sep 24 16:56:47 ubuntustudio kernel: [    1.236000] isapnp: Scanning for PnP cards...
Sep 24 16:56:47 ubuntustudio kernel: [    1.591000] isapnp: No Plug & Play device found
Sep 24 16:56:47 ubuntustudio kernel: [    1.611000] Real Time Clock Driver v1.12ac
Sep 24 16:56:47 ubuntustudio kernel: [    1.611000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep 24 16:56:47 ubuntustudio kernel: [    1.611000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 24 16:56:47 ubuntustudio kernel: [    1.611000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep 24 16:56:47 ubuntustudio kernel: [    1.611000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 24 16:56:47 ubuntustudio kernel: [    1.611000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep 24 16:56:47 ubuntustudio kernel: [    1.611000] mice: PS/2 mouse device common for all mice
Sep 24 16:56:47 ubuntustudio kernel: [    1.612000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep 24 16:56:47 ubuntustudio kernel: [    1.612000] input: Macintosh mouse button emulation as /class/input/input0
Sep 24 16:56:47 ubuntustudio kernel: [    1.612000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep 24 16:56:47 ubuntustudio kernel: [    1.612000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep 24 16:56:47 ubuntustudio kernel: [    1.612000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep 24 16:56:47 ubuntustudio kernel: [    1.615000] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 24 16:56:47 ubuntustudio kernel: [    1.615000] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 24 16:56:47 ubuntustudio kernel: [    1.615000] EISA: Probing bus 0 at eisa.0
Sep 24 16:56:47 ubuntustudio kernel: [    1.615000] Cannot allocate resource for EISA slot 1
Sep 24 16:56:47 ubuntustudio kernel: [    1.615000] Cannot allocate resource for EISA slot 6
Sep 24 16:56:47 ubuntustudio kernel: [    1.615000] Cannot allocate resource for EISA slot 7
Sep 24 16:56:47 ubuntustudio kernel: [    1.615000] Cannot allocate resource for EISA slot 8
Sep 24 16:56:47 ubuntustudio kernel: [    1.615000] EISA: Detected 0 cards.
Sep 24 16:56:47 ubuntustudio kernel: [    1.634000] input: AT Translated Set 2 keyboard as /class/input/input1
Sep 24 16:56:47 ubuntustudio kernel: [    1.645000] TCP cubic registered
Sep 24 16:56:47 ubuntustudio kernel: [    1.645000] NET: Registered protocol family 1
Sep 24 16:56:47 ubuntustudio kernel: [    1.645000] Starting balanced_irq
Sep 24 16:56:47 ubuntustudio kernel: [    1.645000] Using IPI No-Shortcut mode
Sep 24 16:56:47 ubuntustudio kernel: [    1.645000] ACPI: (supports S0 S1 S4 S5)
Sep 24 16:56:47 ubuntustudio kernel: [    1.645000]   Magic number: 7:410:945
Sep 24 16:56:47 ubuntustudio kernel: [    1.645000]   hash matches device ttya0
Sep 24 16:56:47 ubuntustudio kernel: [    1.645000]   hash matches device tty2
Sep 24 16:56:47 ubuntustudio kernel: [    1.645000] Freeing unused kernel memory: 328k freed
Sep 24 16:56:47 ubuntustudio kernel: [    1.646000] Time: acpi_pm clocksource has been installed.
Sep 24 16:56:47 ubuntustudio kernel: [    2.499000] Capability LSM initialized
Sep 24 16:56:47 ubuntustudio kernel: [    2.532000] ACPI: Fan [FAN] (on)
Sep 24 16:56:47 ubuntustudio kernel: [    2.537000] ACPI: Thermal Zone [THRM] (40 C)
Sep 24 16:56:47 ubuntustudio kernel: [    2.868000] usbcore: registered new interface driver usbfs
Sep 24 16:56:47 ubuntustudio kernel: [    2.868000] usbcore: registered new interface driver hub
Sep 24 16:56:47 ubuntustudio kernel: [    2.868000] usbcore: registered new device driver usb
Sep 24 16:56:47 ubuntustudio kernel: [    2.869000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 24 16:56:47 ubuntustudio kernel: [    2.869000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Sep 24 16:56:47 ubuntustudio kernel: [    2.869000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
Sep 24 16:56:47 ubuntustudio kernel: [    2.869000] PCI: Setting latency timer of device 0000:00:02.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    2.869000] ohci_hcd 0000:00:02.0: OHCI Host Controller
Sep 24 16:56:47 ubuntustudio kernel: [    2.870000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Sep 24 16:56:47 ubuntustudio kernel: [    2.870000] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfe02f000
Sep 24 16:56:47 ubuntustudio kernel: [    2.874000] SCSI subsystem initialized
Sep 24 16:56:47 ubuntustudio kernel: [    2.878000] libata version 2.20 loaded.
Sep 24 16:56:47 ubuntustudio kernel: [    2.913000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
Sep 24 16:56:47 ubuntustudio kernel: [    2.929000] usb usb1: configuration #1 chosen from 1 choice
Sep 24 16:56:47 ubuntustudio kernel: [    2.929000] hub 1-0:1.0: USB hub found
Sep 24 16:56:47 ubuntustudio kernel: [    2.929000] hub 1-0:1.0: 10 ports detected
Sep 24 16:56:47 ubuntustudio kernel: [    2.938000] ieee1394: Initialized config rom entry `ip1394'
Sep 24 16:56:47 ubuntustudio kernel: [    2.964000] Floppy drive(s): fd0 is 1.44M
Sep 24 16:56:47 ubuntustudio kernel: [    2.990000] FDC 0 is a post-1991 82077
Sep 24 16:56:47 ubuntustudio kernel: [    3.031000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Sep 24 16:56:47 ubuntustudio kernel: [    3.031000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 17
Sep 24 16:56:47 ubuntustudio kernel: [    3.031000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    3.031000] forcedeth: using HIGHDMA
Sep 24 16:56:47 ubuntustudio kernel: [    3.544000] eth0: forcedeth.c: subsystem: 010de:cb84 bound to 0000:00:0a.0
Sep 24 16:56:47 ubuntustudio kernel: [    3.545000] sata_nv 0000:00:07.0: version 3.3
Sep 24 16:56:47 ubuntustudio kernel: [    3.545000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Sep 24 16:56:47 ubuntustudio kernel: [    3.545000] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
Sep 24 16:56:47 ubuntustudio kernel: [    3.546000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
Sep 24 16:56:47 ubuntustudio kernel: [    3.546000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 19
Sep 24 16:56:47 ubuntustudio kernel: [    3.546000] sata_nv 0000:00:07.0: Using ADMA mode
Sep 24 16:56:47 ubuntustudio kernel: [    3.546000] PCI: Setting latency timer of device 0000:00:07.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    3.546000] ata1: SATA max UDMA/133 cmd 0xf88ba480 ctl 0xf88ba4a0 bmdma 0x0001cc00 irq 19
Sep 24 16:56:47 ubuntustudio kernel: [    3.546000] ata2: SATA max UDMA/133 cmd 0xf88ba580 ctl 0xf88ba5a0 bmdma 0x0001cc08 irq 19
Sep 24 16:56:47 ubuntustudio kernel: [    3.546000] scsi0 : sata_nv
Sep 24 16:56:47 ubuntustudio kernel: [    3.598000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Sep 24 16:56:47 ubuntustudio kernel: [    4.000000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 24 16:56:47 ubuntustudio kernel: [    4.018000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 24 16:56:47 ubuntustudio kernel: [    4.018000] ata1.00: ATA-7: WDC WD5000KS-00MNB0, 07.02E07, max UDMA/133
Sep 24 16:56:47 ubuntustudio kernel: [    4.018000] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Sep 24 16:56:47 ubuntustudio kernel: [    4.021000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 24 16:56:47 ubuntustudio kernel: [    4.021000] ata1.00: configured for UDMA/133
Sep 24 16:56:47 ubuntustudio kernel: [    4.021000] scsi1 : sata_nv
Sep 24 16:56:47 ubuntustudio kernel: [    4.476000] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 24 16:56:47 ubuntustudio kernel: [    4.505000] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 24 16:56:47 ubuntustudio kernel: [    4.505000] ata2.00: ATA-7: WDC WD5000KS-00MNB0, 07.02E07, max UDMA/133
Sep 24 16:56:47 ubuntustudio kernel: [    4.505000] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Sep 24 16:56:47 ubuntustudio kernel: [    4.509000] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 24 16:56:47 ubuntustudio kernel: [    4.509000] ata2.00: configured for UDMA/133
Sep 24 16:56:47 ubuntustudio kernel: [    4.510000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000KS-00M 07.0 PQ: 0 ANSI: 5
Sep 24 16:56:47 ubuntustudio kernel: [    4.510000] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
Sep 24 16:56:47 ubuntustudio kernel: [    4.510000] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000KS-00M 07.0 PQ: 0 ANSI: 5
Sep 24 16:56:47 ubuntustudio kernel: [    4.510000] ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
Sep 24 16:56:47 ubuntustudio kernel: [    4.511000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
Sep 24 16:56:47 ubuntustudio kernel: [    4.511000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
Sep 24 16:56:47 ubuntustudio kernel: [    4.511000] sata_nv 0000:00:08.0: Using ADMA mode
Sep 24 16:56:47 ubuntustudio kernel: [    4.511000] PCI: Setting latency timer of device 0000:00:08.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    4.511000] ata3: SATA max UDMA/133 cmd 0xf8918480 ctl 0xf89184a0 bmdma 0x0001b800 irq 20
Sep 24 16:56:47 ubuntustudio kernel: [    4.511000] ata4: SATA max UDMA/133 cmd 0xf8918580 ctl 0xf89185a0 bmdma 0x0001b808 irq 20
Sep 24 16:56:47 ubuntustudio kernel: [    4.511000] scsi2 : sata_nv
Sep 24 16:56:47 ubuntustudio kernel: [    4.814000] ata3: SATA link down (SStatus 0 SControl 300)
Sep 24 16:56:47 ubuntustudio kernel: [    4.814000] scsi3 : sata_nv
Sep 24 16:56:47 ubuntustudio kernel: [    4.861000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106000000479b]
Sep 24 16:56:47 ubuntustudio kernel: [    5.117000] ata4: SATA link down (SStatus 0 SControl 300)
Sep 24 16:56:47 ubuntustudio kernel: [    5.120000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
Sep 24 16:56:47 ubuntustudio kernel: [    5.120000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
Sep 24 16:56:47 ubuntustudio kernel: [    5.120000] PCI: Setting latency timer of device 0000:00:02.1 to 64
Sep 24 16:56:47 ubuntustudio kernel: [    5.120000] ehci_hcd 0000:00:02.1: EHCI Host Controller
Sep 24 16:56:47 ubuntustudio kernel: [    5.120000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Sep 24 16:56:47 ubuntustudio kernel: [    5.120000] ehci_hcd 0000:00:02.1: debug port 1
Sep 24 16:56:47 ubuntustudio kernel: [    5.120000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
Sep 24 16:56:47 ubuntustudio kernel: [    5.120000] ehci_hcd 0000:00:02.1: irq 16, io mem 0xfeb00000
Sep 24 16:56:47 ubuntustudio kernel: [    5.120000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep 24 16:56:47 ubuntustudio kernel: [    5.122000] usb usb2: configuration #1 chosen from 1 choice
Sep 24 16:56:47 ubuntustudio kernel: [    5.122000] hub 2-0:1.0: USB hub found
Sep 24 16:56:47 ubuntustudio kernel: [    5.122000] hub 2-0:1.0: 10 ports detected
Sep 24 16:56:47 ubuntustudio kernel: [    5.227000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
Sep 24 16:56:47 ubuntustudio kernel: [    5.227000] NFORCE-CK804: chipset revision 162
Sep 24 16:56:47 ubuntustudio kernel: [    5.227000] NFORCE-CK804: not 100%% native mode: will probe irqs later
Sep 24 16:56:47 ubuntustudio kernel: [    5.227000] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
Sep 24 16:56:47 ubuntustudio kernel: [    5.227000]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
Sep 24 16:56:47 ubuntustudio kernel: [    5.227000]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
Sep 24 16:56:47 ubuntustudio kernel: [    5.227000] Probing IDE interface ide0...
Sep 24 16:56:47 ubuntustudio kernel: [    5.242000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
Sep 24 16:56:47 ubuntustudio kernel: [    5.242000] sda: Write Protect is off
Sep 24 16:56:47 ubuntustudio kernel: [    5.242000] sda: Mode Sense: 00 3a 00 00
Sep 24 16:56:47 ubuntustudio kernel: [    5.242000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 16:56:47 ubuntustudio kernel: [    5.242000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
Sep 24 16:56:47 ubuntustudio kernel: [    5.242000] sda: Write Protect is off
Sep 24 16:56:47 ubuntustudio kernel: [    5.242000] sda: Mode Sense: 00 3a 00 00
Sep 24 16:56:47 ubuntustudio kernel: [    5.242000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 16:56:47 ubuntustudio kernel: [    5.242000]  sda: sda1 sda2 < sda5 >
Sep 24 16:56:47 ubuntustudio kernel: [    5.270000] sd 0:0:0:0: Attached scsi disk sda
Sep 24 16:56:47 ubuntustudio kernel: [    5.270000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 24 16:56:47 ubuntustudio kernel: [    5.270000] sdb: Write Protect is off
Sep 24 16:56:47 ubuntustudio kernel: [    5.270000] sdb: Mode Sense: 00 3a 00 00
Sep 24 16:56:47 ubuntustudio kernel: [    5.270000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 16:56:47 ubuntustudio kernel: [    5.270000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 24 16:56:47 ubuntustudio kernel: [    5.270000] sdb: Write Protect is off
Sep 24 16:56:47 ubuntustudio kernel: [    5.270000] sdb: Mode Sense: 00 3a 00 00
Sep 24 16:56:47 ubuntustudio kernel: [    5.270000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 16:56:47 ubuntustudio kernel: [    5.270000]  sdb: sdb1
Sep 24 16:56:47 ubuntustudio kernel: [    5.279000] sd 1:0:0:0: Attached scsi disk sdb
Sep 24 16:56:47 ubuntustudio kernel: [    5.282000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 24 16:56:47 ubuntustudio kernel: [    5.282000] sd 1:0:0:0: Attached scsi generic sg1 type 0
Sep 24 16:56:47 ubuntustudio kernel: [    5.409000] Attempting manual resume
Sep 24 16:56:47 ubuntustudio kernel: [    5.409000] swsusp: Resume From Partition 8:5
Sep 24 16:56:47 ubuntustudio kernel: [    5.409000] PM: Checking swsusp image.
Sep 24 16:56:47 ubuntustudio kernel: [    5.409000] PM: Resume from disk failed.
Sep 24 16:56:47 ubuntustudio kernel: [    5.422000] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep 24 16:56:47 ubuntustudio kernel: [    5.422000] EXT3-fs: write access will be enabled during recovery.
Sep 24 16:56:47 ubuntustudio kernel: [    6.154000] hdb: BENQ DVD DD DW1650, ATAPI CD/DVD-ROM drive
Sep 24 16:56:47 ubuntustudio kernel: [    6.206000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep 24 16:56:47 ubuntustudio kernel: [    6.208000] Probing IDE interface ide1...
Sep 24 16:56:47 ubuntustudio kernel: [    6.735000] hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Sep 24 16:56:47 ubuntustudio kernel: [    6.735000] Uniform CD-ROM driver Revision: 3.20
Sep 24 16:56:47 ubuntustudio kernel: [    7.143000] kjournald starting.  Commit interval 5 seconds
Sep 24 16:56:47 ubuntustudio kernel: [    7.143000] EXT3-fs: recovery complete.
Sep 24 16:56:47 ubuntustudio kernel: [    7.143000] EXT3-fs: mounted filesystem with ordered data mode.
Sep 24 16:56:47 ubuntustudio kernel: [   16.313000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0xf800
Sep 24 16:56:47 ubuntustudio kernel: [   16.313000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0xf400
Sep 24 16:56:47 ubuntustudio kernel: [   16.314000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 24 16:56:47 ubuntustudio kernel: [   16.316000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 24 16:56:47 ubuntustudio kernel: [   16.434000] input: PC Speaker as /class/input/input2
Sep 24 16:56:47 ubuntustudio kernel: [   16.634000] Linux agpgart interface v0.102 (c) Dave Jones
Sep 24 16:56:47 ubuntustudio kernel: [   16.648000] parport: PnPBIOS parport detected.
Sep 24 16:56:47 ubuntustudio kernel: [   16.648000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Sep 24 16:56:47 ubuntustudio kernel: [   16.714000] nvidia: module license 'NVIDIA' taints kernel.
Sep 24 16:56:47 ubuntustudio kernel: [   16.886000] NET: Registered protocol family 17
Sep 24 16:56:47 ubuntustudio kernel: [   16.924000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Sep 24 16:56:47 ubuntustudio kernel: [   16.924000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 21
Sep 24 16:56:47 ubuntustudio kernel: [   16.926000] Audigy2 value: Special config.
Sep 24 16:56:47 ubuntustudio kernel: [   16.996000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
Sep 24 16:56:47 ubuntustudio kernel: [   16.996000] PCI: Setting latency timer of device 0000:05:00.0 to 64
Sep 24 16:56:47 ubuntustudio kernel: [   16.996000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Sep 24 16:56:47 ubuntustudio kernel: [   17.254000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Sep 24 16:56:47 ubuntustudio kernel: [   17.383000] lp0: using parport0 (interrupt-driven).
Sep 24 16:56:47 ubuntustudio kernel: [   17.419000] fuse init (API version 7.8)
Sep 24 16:56:47 ubuntustudio kernel: [   17.453000] Adding 9871900k swap on /dev/disk/by-uuid/3333fb11-dc05-474a-9fc3-d0633ddc7221.  Priority:-1 extents:1 across:9871900k
Sep 24 16:56:47 ubuntustudio kernel: [   17.640000] EXT3 FS on sda1, internal journal
Sep 24 16:56:47 ubuntustudio kernel: [   17.775000] NET: Registered protocol family 10
Sep 24 16:56:47 ubuntustudio kernel: [   17.775000] lo: Disabled Privacy Extensions
Sep 24 16:56:47 ubuntustudio kernel: [   18.135000] input: Power Button (FF) as /class/input/input4
Sep 24 16:56:47 ubuntustudio kernel: [   18.135000] ACPI: Power Button (FF) [PWRF]
Sep 24 16:56:47 ubuntustudio kernel: [   18.135000] input: Power Button (CM) as /class/input/input5
Sep 24 16:56:47 ubuntustudio kernel: [   18.135000] ACPI: Power Button (CM) [PWRB]
Sep 24 16:56:47 ubuntustudio kernel: [   18.180000] Using specific hotkey driver
Sep 24 16:56:47 ubuntustudio kernel: [   18.214000] No dock devices found.
Sep 24 16:56:47 ubuntustudio kernel: [   18.241000] ibm_acpi: ec object not found
Sep 24 16:56:47 ubuntustudio kernel: [   18.304000] pcc_acpi: loading...
Sep 24 16:56:47 ubuntustudio kernel: [   18.441000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (version 2.00.00)
Sep 24 16:56:47 ubuntustudio kernel: [   18.441000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
Sep 24 16:56:47 ubuntustudio kernel: [   18.441000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
Sep 24 16:56:47 ubuntustudio kernel: [   18.441000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
Sep 24 16:56:47 ubuntustudio kernel: [   18.441000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Sep 24 16:56:53 ubuntustudio kernel: [   24.341000] ppdev: user-space parallel port driver
Sep 24 16:56:53 ubuntustudio kernel: [   24.943000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Sep 24 16:56:53 ubuntustudio kernel: [   24.943000] apm: disabled - APM is not SMP safe.
Sep 24 16:56:53 ubuntustudio kernel: [   25.055000] Bluetooth: Core ver 2.11
Sep 24 16:56:53 ubuntustudio kernel: [   25.055000] NET: Registered protocol family 31
Sep 24 16:56:53 ubuntustudio kernel: [   25.055000] Bluetooth: HCI device and connection manager initialized
Sep 24 16:56:53 ubuntustudio kernel: [   25.055000] Bluetooth: HCI socket layer initialized
Sep 24 16:56:53 ubuntustudio kernel: [   25.069000] Bluetooth: L2CAP ver 2.8
Sep 24 16:56:53 ubuntustudio kernel: [   25.069000] Bluetooth: L2CAP socket layer initialized
Sep 24 16:56:54 ubuntustudio kernel: [   25.144000] Bluetooth: RFCOMM socket layer initialized
Sep 24 16:56:54 ubuntustudio kernel: [   25.144000] Bluetooth: RFCOMM TTY layer initialized
Sep 24 16:56:54 ubuntustudio kernel: [   25.144000] Bluetooth: RFCOMM ver 1.8
Sep 24 16:57:07 ubuntustudio kernel: [   38.256000] eth0: no IPv6 routers present
Sep 24 16:58:49 ubuntustudio kernel: Inspecting /boot/System.map-2.6.20-16-lowlatency
Sep 24 16:58:49 ubuntustudio kernel: Loaded 25002 symbols from /boot/System.map-2.6.20-16-lowlatency.
Sep 24 16:58:49 ubuntustudio kernel: Symbols match kernel version 2.6.20.
Sep 24 16:58:49 ubuntustudio kernel: No module symbols loaded - kernel modules not enabled. 
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Linux version 2.6.20-16-lowlatency (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP PREEMPT Fri Aug 31 00:58:46 UTC 2007 (Ubuntu Unofficial)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] sanitize start
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] sanitize end
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 00000000cfef0000 end: 00000000cfff0000 type: 1
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 00000000cfff0000 size: 0000000000003000 end: 00000000cfff3000 type: 4
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 00000000cfff3000 size: 000000000000d000 end: 00000000d0000000 type: 3
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() start: 0000000100000000 size: 0000000020000000 end: 0000000120000000 type: 1
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfff0000 (usable)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000cfff3000 (ACPI NVS)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]  BIOS-e820: 00000000cfff3000 - 00000000d0000000 (ACPI data)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Warning only 4GB will be used.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Use a PAE enabled kernel.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] 3200MB HIGHMEM available.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] 896MB LOWMEM available.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] found SMP MP-table at 000f3d40
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Zone PFN ranges:
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]   DMA             0 ->     4096
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]   Normal       4096 ->   229376
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]   HighMem    229376 ->  1048576
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]     0:        0 ->  1048576
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] On node 0 totalpages: 1048576
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]   HighMem zone: 6400 pages used for memmap
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] DMI 2.2 present.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f7e40
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0xcfff3040
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0xcfff30c0
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0xcfff90c0
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0xcfff9300
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0xcfff9000
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Processor #0 15:11 APIC version 16
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Processor #1 15:11 APIC version 16
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: IRQ14 used by override.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] ACPI: IRQ15 used by override.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Allocating PCI resources starting at d1000000 (gap: d0000000:10000000)
Sep 24 16:58:49 ubuntustudio kernel: [    0.000000] Detected 2210.243 MHz processor.
Sep 24 16:58:49 ubuntustudio kernel: [   22.438549] Built 1 zonelists.  Total pages: 1040384
Sep 24 16:58:49 ubuntustudio kernel: [   22.438551] Kernel command line: root=UUID=73ebee5f-2466-425e-a939-04d97c696465 ro quiet splash
Sep 24 16:58:49 ubuntustudio kernel: [   22.438665] mapped APIC to ffffd000 (fee00000)
Sep 24 16:58:49 ubuntustudio kernel: [   22.438667] mapped IOAPIC to ffffc000 (fec00000)
Sep 24 16:58:49 ubuntustudio kernel: [   22.438669] Enabling fast FPU save and restore... done.
Sep 24 16:58:49 ubuntustudio kernel: [   22.438671] Enabling unmasked SIMD FPU exception support... done.
Sep 24 16:58:49 ubuntustudio kernel: [   22.438677] Initializing CPU#0
Sep 24 16:58:49 ubuntustudio kernel: [   22.438729] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep 24 16:58:49 ubuntustudio kernel: [   22.438801] spurious 8259A interrupt: IRQ7.
Sep 24 16:58:49 ubuntustudio kernel: [   22.440205] Console: colour VGA+ 80x25
Sep 24 16:58:49 ubuntustudio kernel: [   22.440490] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 24 16:58:49 ubuntustudio kernel: [   22.440824] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 24 16:58:49 ubuntustudio kernel: [   22.567861] Memory: 3362264k/4194304k available (2019k kernel code, 44288k reserved, 902k data, 328k init, 2490304k highmem)
Sep 24 16:58:49 ubuntustudio kernel: [   22.567870] virtual kernel memory layout:
Sep 24 16:58:49 ubuntustudio kernel: [   22.567871]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Sep 24 16:58:49 ubuntustudio kernel: [   22.567872]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 24 16:58:49 ubuntustudio kernel: [   22.567873]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep 24 16:58:49 ubuntustudio kernel: [   22.567874]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep 24 16:58:49 ubuntustudio kernel: [   22.567875]       .init : 0xc03e1000 - 0xc0433000   ( 328 kB)
Sep 24 16:58:49 ubuntustudio kernel: [   22.567876]       .data : 0xc02f8dd5 - 0xc03da6d4   ( 902 kB)
Sep 24 16:58:49 ubuntustudio kernel: [   22.567877]       .text : 0xc0100000 - 0xc02f8dd5   (2019 kB)
Sep 24 16:58:49 ubuntustudio kernel: [   22.567880] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep 24 16:58:49 ubuntustudio kernel: [   22.627579] Calibrating delay using timer specific routine.. 4421.71 BogoMIPS (lpj=2210858)
Sep 24 16:58:49 ubuntustudio kernel: [   22.627618] Security Framework v1.0.0 initialized
Sep 24 16:58:49 ubuntustudio kernel: [   22.627624] SELinux:  Disabled at boot.
Sep 24 16:58:49 ubuntustudio kernel: [   22.627639] Mount-cache hash table entries: 512
Sep 24 16:58:49 ubuntustudio kernel: [   22.627747] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
Sep 24 16:58:49 ubuntustudio kernel: [   22.627755] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 24 16:58:49 ubuntustudio kernel: [   22.627757] CPU: L2 Cache: 512K (64 bytes/line)
Sep 24 16:58:49 ubuntustudio kernel: [   22.627760] CPU 0(2) -> Core 0
Sep 24 16:58:49 ubuntustudio kernel: [   22.627761] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
Sep 24 16:58:49 ubuntustudio kernel: [   22.627770] Compat vDSO mapped to ffffe000.
Sep 24 16:58:49 ubuntustudio kernel: [   22.627773] Remapping vsyscall page to ffffe000
Sep 24 16:58:49 ubuntustudio kernel: [   22.627781] Checking 'hlt' instruction... OK.
Sep 24 16:58:49 ubuntustudio kernel: [   22.631670] SMP alternatives: switching to UP code
Sep 24 16:58:49 ubuntustudio kernel: [   22.631915] Early unpacking initramfs... done
Sep 24 16:58:49 ubuntustudio kernel: [   22.881653] ACPI: Core revision 20060707
Sep 24 16:58:49 ubuntustudio kernel: [   22.884063] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Sep 24 16:58:49 ubuntustudio kernel: [   22.887649] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
Sep 24 16:58:49 ubuntustudio kernel: [   22.887668] SMP alternatives: switching to SMP code
Sep 24 16:58:49 ubuntustudio kernel: [   22.887719] Booting processor 1/1 eip 3000
Sep 24 16:58:49 ubuntustudio kernel: [   22.898254] Initializing CPU#1
Sep 24 16:58:49 ubuntustudio kernel: [   22.958592] Calibrating delay using timer specific routine.. 4419.73 BogoMIPS (lpj=2209868)
Sep 24 16:58:49 ubuntustudio kernel: [   22.958597] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
Sep 24 16:58:49 ubuntustudio kernel: [   22.958603] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep 24 16:58:49 ubuntustudio kernel: [   22.958605] CPU: L2 Cache: 512K (64 bytes/line)
Sep 24 16:58:49 ubuntustudio kernel: [   22.958607] CPU 1(2) -> Core 1
Sep 24 16:58:49 ubuntustudio kernel: [   22.958608] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
Sep 24 16:58:49 ubuntustudio kernel: [   22.958423] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
Sep 24 16:58:49 ubuntustudio kernel: [   22.958436] Total of 2 processors activated (8841.45 BogoMIPS).
Sep 24 16:58:49 ubuntustudio kernel: [   22.958575] ENABLING IO-APIC IRQs
Sep 24 16:58:49 ubuntustudio kernel: [   22.958768] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Sep 24 16:58:49 ubuntustudio kernel: [   23.070222] checking TSC synchronization across 2 CPUs: 
Sep 24 16:58:49 ubuntustudio kernel: [    0.000001] CPU#0 had -143 usecs TSC skew, fixed it up.
Sep 24 16:58:49 ubuntustudio kernel: [    0.000003] CPU#1 had 143 usecs TSC skew, fixed it up.
Sep 24 16:58:49 ubuntustudio kernel: [    0.001003] Brought up 2 CPUs
Sep 24 16:58:49 ubuntustudio kernel: [    0.065097] migration_cost=195
Sep 24 16:58:49 ubuntustudio kernel: [    0.065308] Booting paravirtualized kernel on bare hardware
Sep 24 16:58:49 ubuntustudio kernel: [    0.065385] Time: 16:58:32  Date: 08/24/107
Sep 24 16:58:49 ubuntustudio kernel: [    0.065413] NET: Registered protocol family 16
Sep 24 16:58:49 ubuntustudio kernel: [    0.065486] EISA bus registered
Sep 24 16:58:49 ubuntustudio kernel: [    0.065489] ACPI: bus type pci registered
Sep 24 16:58:49 ubuntustudio kernel: [    0.070210] PCI: PCI BIOS revision 3.00 entry at 0xfa8b0, last bus=5
Sep 24 16:58:49 ubuntustudio kernel: [    0.070212] PCI: Using configuration type 1
Sep 24 16:58:49 ubuntustudio kernel: [    0.070213] Setting up standard PCI resources
Sep 24 16:58:49 ubuntustudio kernel: [    0.078873] ACPI: Interpreter enabled
Sep 24 16:58:49 ubuntustudio kernel: [    0.078875] ACPI: Using IOAPIC for interrupt routing
Sep 24 16:58:49 ubuntustudio kernel: [    0.079324] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 24 16:58:49 ubuntustudio kernel: [    0.079327] PCI: Probing PCI hardware (bus 00)
Sep 24 16:58:49 ubuntustudio kernel: [    0.081333] PCI: Transparent bridge - 0000:00:09.0
Sep 24 16:58:49 ubuntustudio kernel: [    0.081526] Boot video device is 0000:05:00.0
Sep 24 16:58:49 ubuntustudio kernel: [    0.081580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep 24 16:58:49 ubuntustudio kernel: [    0.139598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Sep 24 16:58:49 ubuntustudio kernel: [    0.141211] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.141483] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.141756] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Sep 24 16:58:49 ubuntustudio kernel: [    0.142033] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Sep 24 16:58:49 ubuntustudio kernel: [    0.142302] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.142576] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Sep 24 16:58:49 ubuntustudio kernel: [    0.142847] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.143123] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Sep 24 16:58:49 ubuntustudio kernel: [    0.143391] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.143661] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.143935] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Sep 24 16:58:49 ubuntustudio kernel: [    0.144205] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Sep 24 16:58:49 ubuntustudio kernel: [    0.144476] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.144754] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Sep 24 16:58:49 ubuntustudio kernel: [    0.145040] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Sep 24 16:58:49 ubuntustudio kernel: [    0.145320] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.145631] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.145935] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.146234] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.146531] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.146762] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.147080] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.147392] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.147702] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.148015] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.148325] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.148634] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.148952] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.149261] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.149578] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.149902] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.150220] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
Sep 24 16:58:49 ubuntustudio kernel: [    0.153171] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep 24 16:58:49 ubuntustudio kernel: [    0.153180] pnp: PnP ACPI init
Sep 24 16:58:49 ubuntustudio kernel: [    0.159039] pnp: PnP ACPI: found 15 devices
Sep 24 16:58:49 ubuntustudio kernel: [    0.159042] PnPBIOS: Disabled by ACPI PNP
Sep 24 16:58:49 ubuntustudio kernel: [    0.159089] PCI: Using ACPI for IRQ routing
Sep 24 16:58:49 ubuntustudio kernel: [    0.159092] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep 24 16:58:49 ubuntustudio kernel: [    0.216158] NET: Registered protocol family 8
Sep 24 16:58:49 ubuntustudio kernel: [    0.216159] NET: Registered protocol family 20
Sep 24 16:58:49 ubuntustudio kernel: [    0.216447] pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
Sep 24 16:58:49 ubuntustudio kernel: [    0.216450] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
Sep 24 16:58:49 ubuntustudio kernel: [    0.216452] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
Sep 24 16:58:49 ubuntustudio kernel: [    0.216455] pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
Sep 24 16:58:49 ubuntustudio kernel: [    0.216457] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
Sep 24 16:58:49 ubuntustudio kernel: [    0.216459] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
Sep 24 16:58:49 ubuntustudio kernel: [    0.216692] PCI: Bridge: 0000:00:09.0
Sep 24 16:58:49 ubuntustudio kernel: [    0.216694]   IO window: a000-afff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216697]   MEM window: fde00000-fdefffff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216700]   PREFETCH window: fdf00000-fdffffff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216702] PCI: Bridge: 0000:00:0b.0
Sep 24 16:58:49 ubuntustudio kernel: [    0.216704]   IO window: 9000-9fff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216706]   MEM window: fdd00000-fddfffff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216709]   PREFETCH window: fdc00000-fdcfffff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216711] PCI: Bridge: 0000:00:0c.0
Sep 24 16:58:49 ubuntustudio kernel: [    0.216713]   IO window: 8000-8fff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216715]   MEM window: fdb00000-fdbfffff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216718]   PREFETCH window: fda00000-fdafffff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216720] PCI: Bridge: 0000:00:0d.0
Sep 24 16:58:49 ubuntustudio kernel: [    0.216722]   IO window: 7000-7fff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216724]   MEM window: fd900000-fd9fffff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216727]   PREFETCH window: fd800000-fd8fffff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216731] PCI: Bridge: 0000:00:0e.0
Sep 24 16:58:49 ubuntustudio kernel: [    0.216733]   IO window: 6000-6fff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216735]   MEM window: fa000000-fcffffff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216738]   PREFETCH window: d0000000-dfffffff
Sep 24 16:58:49 ubuntustudio kernel: [    0.216744] PCI: Setting latency timer of device 0000:00:09.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    0.216751] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    0.216756] PCI: Setting latency timer of device 0000:00:0c.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    0.216761] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    0.216767] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    0.216799] NET: Registered protocol family 2
Sep 24 16:58:49 ubuntustudio kernel: [    0.226854] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 24 16:58:49 ubuntustudio kernel: [    0.226977] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Sep 24 16:58:49 ubuntustudio kernel: [    0.227912] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
Sep 24 16:58:49 ubuntustudio kernel: [    0.228388] TCP: Hash tables configured (established 131072 bind 65536)
Sep 24 16:58:49 ubuntustudio kernel: [    0.228391] TCP reno registered
Sep 24 16:58:49 ubuntustudio kernel: [    0.230912] checking if image is initramfs... it is
Sep 24 16:58:49 ubuntustudio kernel: [    0.721394] Freeing initrd memory: 6881k freed
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] audit: initializing netlink socket (disabled)
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] audit(1190653113.513:1): initialized
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] highmem bounce pool size: 64 pages
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] VFS: Disk quotas dquot_6.5.1
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] io scheduler noop registered
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] io scheduler anticipatory registered
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] io scheduler deadline registered
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] io scheduler cfq registered (default)
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] assign_interrupt_mode Found MSI capability
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] Allocate Port Service[0000:00:0b.0:pcie00]
Sep 24 16:58:49 ubuntustudio kernel: [    1.218000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    1.219000] assign_interrupt_mode Found MSI capability
Sep 24 16:58:49 ubuntustudio kernel: [    1.219000] Allocate Port Service[0000:00:0c.0:pcie00]
Sep 24 16:58:49 ubuntustudio kernel: [    1.219000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    1.219000] assign_interrupt_mode Found MSI capability
Sep 24 16:58:49 ubuntustudio kernel: [    1.219000] Allocate Port Service[0000:00:0d.0:pcie00]
Sep 24 16:58:49 ubuntustudio kernel: [    1.219000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    1.219000] assign_interrupt_mode Found MSI capability
Sep 24 16:58:49 ubuntustudio kernel: [    1.219000] Allocate Port Service[0000:00:0e.0:pcie00]
Sep 24 16:58:49 ubuntustudio kernel: [    1.219000] isapnp: Scanning for PnP cards...
Sep 24 16:58:49 ubuntustudio kernel: [    1.574000] isapnp: No Plug & Play device found
Sep 24 16:58:49 ubuntustudio kernel: [    1.593000] Real Time Clock Driver v1.12ac
Sep 24 16:58:49 ubuntustudio kernel: [    1.593000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep 24 16:58:49 ubuntustudio kernel: [    1.593000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 24 16:58:49 ubuntustudio kernel: [    1.593000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep 24 16:58:49 ubuntustudio kernel: [    1.593000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 24 16:58:49 ubuntustudio kernel: [    1.594000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep 24 16:58:49 ubuntustudio kernel: [    1.594000] mice: PS/2 mouse device common for all mice
Sep 24 16:58:49 ubuntustudio kernel: [    1.594000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep 24 16:58:49 ubuntustudio kernel: [    1.594000] input: Macintosh mouse button emulation as /class/input/input0
Sep 24 16:58:49 ubuntustudio kernel: [    1.594000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep 24 16:58:49 ubuntustudio kernel: [    1.594000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep 24 16:58:49 ubuntustudio kernel: [    1.595000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep 24 16:58:49 ubuntustudio kernel: [    1.597000] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 24 16:58:49 ubuntustudio kernel: [    1.597000] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 24 16:58:49 ubuntustudio kernel: [    1.597000] EISA: Probing bus 0 at eisa.0
Sep 24 16:58:49 ubuntustudio kernel: [    1.597000] Cannot allocate resource for EISA slot 1
Sep 24 16:58:49 ubuntustudio kernel: [    1.597000] Cannot allocate resource for EISA slot 6
Sep 24 16:58:49 ubuntustudio kernel: [    1.597000] Cannot allocate resource for EISA slot 7
Sep 24 16:58:49 ubuntustudio kernel: [    1.597000] Cannot allocate resource for EISA slot 8
Sep 24 16:58:49 ubuntustudio kernel: [    1.597000] EISA: Detected 0 cards.
Sep 24 16:58:49 ubuntustudio kernel: [    1.617000] input: AT Translated Set 2 keyboard as /class/input/input1
Sep 24 16:58:49 ubuntustudio kernel: [    1.627000] TCP cubic registered
Sep 24 16:58:49 ubuntustudio kernel: [    1.627000] NET: Registered protocol family 1
Sep 24 16:58:49 ubuntustudio kernel: [    1.627000] Starting balanced_irq
Sep 24 16:58:49 ubuntustudio kernel: [    1.627000] Using IPI No-Shortcut mode
Sep 24 16:58:49 ubuntustudio kernel: [    1.627000] ACPI: (supports S0 S1 S4 S5)
Sep 24 16:58:49 ubuntustudio kernel: [    1.627000]   Magic number: 7:960:995
Sep 24 16:58:49 ubuntustudio kernel: [    1.627000]   hash matches device ttyd8
Sep 24 16:58:49 ubuntustudio kernel: [    1.627000]   hash matches device ttyab
Sep 24 16:58:49 ubuntustudio kernel: [    1.628000] Time: acpi_pm clocksource has been installed.
Sep 24 16:58:49 ubuntustudio kernel: [    1.628000] Freeing unused kernel memory: 328k freed
Sep 24 16:58:49 ubuntustudio kernel: [    2.823000] Capability LSM initialized
Sep 24 16:58:49 ubuntustudio kernel: [    2.856000] ACPI: Fan [FAN] (on)
Sep 24 16:58:49 ubuntustudio kernel: [    2.860000] ACPI: Thermal Zone [THRM] (40 C)
Sep 24 16:58:49 ubuntustudio kernel: [    3.231000] usbcore: registered new interface driver usbfs
Sep 24 16:58:49 ubuntustudio kernel: [    3.231000] usbcore: registered new interface driver hub
Sep 24 16:58:49 ubuntustudio kernel: [    3.231000] usbcore: registered new device driver usb
Sep 24 16:58:49 ubuntustudio kernel: [    3.231000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 24 16:58:49 ubuntustudio kernel: [    3.232000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Sep 24 16:58:49 ubuntustudio kernel: [    3.232000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
Sep 24 16:58:49 ubuntustudio kernel: [    3.232000] PCI: Setting latency timer of device 0000:00:02.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    3.232000] ohci_hcd 0000:00:02.0: OHCI Host Controller
Sep 24 16:58:49 ubuntustudio kernel: [    3.232000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Sep 24 16:58:49 ubuntustudio kernel: [    3.232000] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfe02f000
Sep 24 16:58:49 ubuntustudio kernel: [    3.258000] ieee1394: Initialized config rom entry `ip1394'
Sep 24 16:58:49 ubuntustudio kernel: [    3.290000] usb usb1: configuration #1 chosen from 1 choice
Sep 24 16:58:49 ubuntustudio kernel: [    3.290000] hub 1-0:1.0: USB hub found
Sep 24 16:58:49 ubuntustudio kernel: [    3.290000] hub 1-0:1.0: 10 ports detected
Sep 24 16:58:49 ubuntustudio kernel: [    3.293000] SCSI subsystem initialized
Sep 24 16:58:49 ubuntustudio kernel: [    3.297000] libata version 2.20 loaded.
Sep 24 16:58:49 ubuntustudio kernel: [    3.306000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
Sep 24 16:58:49 ubuntustudio kernel: [    3.325000] Floppy drive(s): fd0 is 1.44M
Sep 24 16:58:49 ubuntustudio kernel: [    3.340000] FDC 0 is a post-1991 82077
Sep 24 16:58:49 ubuntustudio kernel: [    3.392000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Sep 24 16:58:49 ubuntustudio kernel: [    3.392000] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 17
Sep 24 16:58:49 ubuntustudio kernel: [    3.445000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Sep 24 16:58:49 ubuntustudio kernel: [    3.451000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Sep 24 16:58:49 ubuntustudio kernel: [    3.451000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 18
Sep 24 16:58:49 ubuntustudio kernel: [    3.451000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    3.451000] forcedeth: using HIGHDMA
Sep 24 16:58:49 ubuntustudio kernel: [    3.963000] eth0: forcedeth.c: subsystem: 010de:cb84 bound to 0000:00:0a.0
Sep 24 16:58:49 ubuntustudio kernel: [    3.964000] sata_nv 0000:00:07.0: version 3.3
Sep 24 16:58:49 ubuntustudio kernel: [    3.964000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
Sep 24 16:58:49 ubuntustudio kernel: [    3.964000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 19
Sep 24 16:58:49 ubuntustudio kernel: [    3.964000] sata_nv 0000:00:07.0: Using ADMA mode
Sep 24 16:58:49 ubuntustudio kernel: [    3.964000] PCI: Setting latency timer of device 0000:00:07.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    3.964000] ata1: SATA max UDMA/133 cmd 0xf886c480 ctl 0xf886c4a0 bmdma 0x0001cc00 irq 19
Sep 24 16:58:49 ubuntustudio kernel: [    3.964000] ata2: SATA max UDMA/133 cmd 0xf886c580 ctl 0xf886c5a0 bmdma 0x0001cc08 irq 19
Sep 24 16:58:49 ubuntustudio kernel: [    3.964000] scsi0 : sata_nv
Sep 24 16:58:49 ubuntustudio kernel: [    4.418000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 24 16:58:49 ubuntustudio kernel: [    4.434000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 24 16:58:49 ubuntustudio kernel: [    4.434000] ata1.00: ATA-7: WDC WD5000KS-00MNB0, 07.02E07, max UDMA/133
Sep 24 16:58:49 ubuntustudio kernel: [    4.434000] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Sep 24 16:58:49 ubuntustudio kernel: [    4.437000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 24 16:58:49 ubuntustudio kernel: [    4.437000] ata1.00: configured for UDMA/133
Sep 24 16:58:49 ubuntustudio kernel: [    4.437000] scsi1 : sata_nv
Sep 24 16:58:49 ubuntustudio kernel: [    4.707000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106000000479b]
Sep 24 16:58:49 ubuntustudio kernel: [    4.892000] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 24 16:58:49 ubuntustudio kernel: [    4.929000] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 24 16:58:49 ubuntustudio kernel: [    4.929000] ata2.00: ATA-7: WDC WD5000KS-00MNB0, 07.02E07, max UDMA/133
Sep 24 16:58:49 ubuntustudio kernel: [    4.929000] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Sep 24 16:58:49 ubuntustudio kernel: [    4.932000] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 24 16:58:49 ubuntustudio kernel: [    4.932000] ata2.00: configured for UDMA/133
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000KS-00M 07.0 PQ: 0 ANSI: 5
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000KS-00M 07.0 PQ: 0 ANSI: 5
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] sata_nv 0000:00:08.0: Using ADMA mode
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] PCI: Setting latency timer of device 0000:00:08.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] ata3: SATA max UDMA/133 cmd 0xf899e480 ctl 0xf899e4a0 bmdma 0x0001b800 irq 20
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] ata4: SATA max UDMA/133 cmd 0xf899e580 ctl 0xf899e5a0 bmdma 0x0001b808 irq 20
Sep 24 16:58:49 ubuntustudio kernel: [    4.933000] scsi2 : sata_nv
Sep 24 16:58:49 ubuntustudio kernel: [    5.237000] ata3: SATA link down (SStatus 0 SControl 300)
Sep 24 16:58:49 ubuntustudio kernel: [    5.237000] scsi3 : sata_nv
Sep 24 16:58:49 ubuntustudio kernel: [    5.540000] ata4: SATA link down (SStatus 0 SControl 300)
Sep 24 16:58:49 ubuntustudio kernel: [    5.542000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
Sep 24 16:58:49 ubuntustudio kernel: [    5.542000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
Sep 24 16:58:49 ubuntustudio kernel: [    5.542000] PCI: Setting latency timer of device 0000:00:02.1 to 64
Sep 24 16:58:49 ubuntustudio kernel: [    5.542000] ehci_hcd 0000:00:02.1: EHCI Host Controller
Sep 24 16:58:49 ubuntustudio kernel: [    5.542000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Sep 24 16:58:49 ubuntustudio kernel: [    5.542000] ehci_hcd 0000:00:02.1: debug port 1
Sep 24 16:58:49 ubuntustudio kernel: [    5.542000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
Sep 24 16:58:49 ubuntustudio kernel: [    5.542000] ehci_hcd 0000:00:02.1: irq 16, io mem 0xfeb00000
Sep 24 16:58:49 ubuntustudio kernel: [    5.542000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep 24 16:58:49 ubuntustudio kernel: [    5.543000] usb usb2: configuration #1 chosen from 1 choice
Sep 24 16:58:49 ubuntustudio kernel: [    5.543000] hub 2-0:1.0: USB hub found
Sep 24 16:58:49 ubuntustudio kernel: [    5.543000] hub 2-0:1.0: 10 ports detected
Sep 24 16:58:49 ubuntustudio kernel: [    5.648000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
Sep 24 16:58:49 ubuntustudio kernel: [    5.648000] NFORCE-CK804: chipset revision 162
Sep 24 16:58:49 ubuntustudio kernel: [    5.648000] NFORCE-CK804: not 100%% native mode: will probe irqs later
Sep 24 16:58:49 ubuntustudio kernel: [    5.648000] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
Sep 24 16:58:49 ubuntustudio kernel: [    5.648000]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
Sep 24 16:58:49 ubuntustudio kernel: [    5.648000]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
Sep 24 16:58:49 ubuntustudio kernel: [    5.648000] Probing IDE interface ide0...
Sep 24 16:58:49 ubuntustudio kernel: [    5.661000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
Sep 24 16:58:49 ubuntustudio kernel: [    5.661000] sda: Write Protect is off
Sep 24 16:58:49 ubuntustudio kernel: [    5.661000] sda: Mode Sense: 00 3a 00 00
Sep 24 16:58:49 ubuntustudio kernel: [    5.661000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 16:58:49 ubuntustudio kernel: [    5.661000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
Sep 24 16:58:49 ubuntustudio kernel: [    5.661000] sda: Write Protect is off
Sep 24 16:58:49 ubuntustudio kernel: [    5.661000] sda: Mode Sense: 00 3a 00 00
Sep 24 16:58:49 ubuntustudio kernel: [    5.661000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 16:58:49 ubuntustudio kernel: [    5.661000]  sda: sda1 sda2 < sda5 >
Sep 24 16:58:49 ubuntustudio kernel: [    5.686000] sd 0:0:0:0: Attached scsi disk sda
Sep 24 16:58:49 ubuntustudio kernel: [    5.687000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 24 16:58:49 ubuntustudio kernel: [    5.687000] sdb: Write Protect is off
Sep 24 16:58:49 ubuntustudio kernel: [    5.687000] sdb: Mode Sense: 00 3a 00 00
Sep 24 16:58:49 ubuntustudio kernel: [    5.687000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 16:58:49 ubuntustudio kernel: [    5.687000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 24 16:58:49 ubuntustudio kernel: [    5.687000] sdb: Write Protect is off
Sep 24 16:58:49 ubuntustudio kernel: [    5.687000] sdb: Mode Sense: 00 3a 00 00
Sep 24 16:58:49 ubuntustudio kernel: [    5.687000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 16:58:49 ubuntustudio kernel: [    5.687000]  sdb: sdb1
Sep 24 16:58:49 ubuntustudio kernel: [    5.694000] sd 1:0:0:0: Attached scsi disk sdb
Sep 24 16:58:49 ubuntustudio kernel: [    5.699000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 24 16:58:49 ubuntustudio kernel: [    5.699000] sd 1:0:0:0: Attached scsi generic sg1 type 0
Sep 24 16:58:49 ubuntustudio kernel: [    5.874000] Attempting manual resume
Sep 24 16:58:49 ubuntustudio kernel: [    5.874000] swsusp: Resume From Partition 8:5
Sep 24 16:58:49 ubuntustudio kernel: [    5.874000] PM: Checking swsusp image.
Sep 24 16:58:49 ubuntustudio kernel: [    5.875000] PM: Resume from disk failed.
Sep 24 16:58:49 ubuntustudio kernel: [    5.915000] kjournald starting.  Commit interval 5 seconds
Sep 24 16:58:49 ubuntustudio kernel: [    5.915000] EXT3-fs: mounted filesystem with ordered data mode.
Sep 24 16:58:49 ubuntustudio kernel: [    6.575000] hdb: BENQ DVD DD DW1650, ATAPI CD/DVD-ROM drive
Sep 24 16:58:49 ubuntustudio kernel: [    6.627000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep 24 16:58:49 ubuntustudio kernel: [    6.629000] Probing IDE interface ide1...
Sep 24 16:58:49 ubuntustudio kernel: [   14.724000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 24 16:58:49 ubuntustudio kernel: [   14.726000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 24 16:58:49 ubuntustudio kernel: [   14.792000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0xf800
Sep 24 16:58:49 ubuntustudio kernel: [   14.792000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0xf400
Sep 24 16:58:49 ubuntustudio kernel: [   14.832000] input: PC Speaker as /class/input/input2
Sep 24 16:58:49 ubuntustudio kernel: [   14.909000] parport: PnPBIOS parport detected.
Sep 24 16:58:49 ubuntustudio kernel: [   14.909000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Sep 24 16:58:49 ubuntustudio kernel: [   14.994000] hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Sep 24 16:58:49 ubuntustudio kernel: [   14.994000] Uniform CD-ROM driver Revision: 3.20
Sep 24 16:58:49 ubuntustudio kernel: [   14.998000] Linux agpgart interface v0.102 (c) Dave Jones
Sep 24 16:58:49 ubuntustudio kernel: [   15.071000] nvidia: module license 'NVIDIA' taints kernel.
Sep 24 16:58:49 ubuntustudio kernel: [   15.171000] NET: Registered protocol family 17
Sep 24 16:58:49 ubuntustudio kernel: [   15.274000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Sep 24 16:58:49 ubuntustudio kernel: [   15.274000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 21
Sep 24 16:58:49 ubuntustudio kernel: [   15.276000] Audigy2 value: Special config.
Sep 24 16:58:49 ubuntustudio kernel: [   15.348000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 17
Sep 24 16:58:49 ubuntustudio kernel: [   15.348000] PCI: Setting latency timer of device 0000:05:00.0 to 64
Sep 24 16:58:49 ubuntustudio kernel: [   15.349000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Sep 24 16:58:49 ubuntustudio kernel: [   15.507000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Sep 24 16:58:49 ubuntustudio kernel: [   15.679000] lp0: using parport0 (interrupt-driven).
Sep 24 16:58:49 ubuntustudio kernel: [   15.719000] fuse init (API version 7.8)
Sep 24 16:58:49 ubuntustudio kernel: [   15.755000] Adding 9871900k swap on /dev/disk/by-uuid/3333fb11-dc05-474a-9fc3-d0633ddc7221.  Priority:-1 extents:1 across:9871900k
Sep 24 16:58:49 ubuntustudio kernel: [   15.945000] EXT3 FS on sda1, internal journal
Sep 24 16:58:49 ubuntustudio kernel: [   16.119000] NET: Registered protocol family 10
Sep 24 16:58:49 ubuntustudio kernel: [   16.119000] lo: Disabled Privacy Extensions
Sep 24 16:58:49 ubuntustudio kernel: [   16.637000] input: Power Button (FF) as /class/input/input4
Sep 24 16:58:49 ubuntustudio kernel: [   16.637000] ACPI: Power Button (FF) [PWRF]
Sep 24 16:58:49 ubuntustudio kernel: [   16.637000] input: Power Button (CM) as /class/input/input5
Sep 24 16:58:49 ubuntustudio kernel: [   16.637000] ACPI: Power Button (CM) [PWRB]
Sep 24 16:58:49 ubuntustudio kernel: [   16.679000] Using specific hotkey driver
Sep 24 16:58:49 ubuntustudio kernel: [   16.712000] No dock devices found.
Sep 24 16:58:49 ubuntustudio kernel: [   16.735000] ibm_acpi: ec object not found
Sep 24 16:58:49 ubuntustudio kernel: [   16.796000] pcc_acpi: loading...
Sep 24 16:58:49 ubuntustudio kernel: [   16.974000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (version 2.00.00)
Sep 24 16:58:49 ubuntustudio kernel: [   16.974000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
Sep 24 16:58:49 ubuntustudio kernel: [   16.974000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
Sep 24 16:58:49 ubuntustudio kernel: [   16.974000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
Sep 24 16:58:49 ubuntustudio kernel: [   16.974000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Sep 24 16:58:54 ubuntustudio kernel: [   23.082000] ppdev: user-space parallel port driver
Sep 24 16:58:55 ubuntustudio kernel: [   23.810000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Sep 24 16:58:55 ubuntustudio kernel: [   23.810000] apm: disabled - APM is not SMP safe.
Sep 24 16:58:55 ubuntustudio kernel: [   23.958000] Bluetooth: Core ver 2.11
Sep 24 16:58:55 ubuntustudio kernel: [   23.958000] NET: Registered protocol family 31
Sep 24 16:58:55 ubuntustudio kernel: [   23.958000] Bluetooth: HCI device and connection manager initialized
Sep 24 16:58:55 ubuntustudio kernel: [   23.958000] Bluetooth: HCI socket layer initialized
Sep 24 16:58:55 ubuntustudio kernel: [   23.972000] Bluetooth: L2CAP ver 2.8
Sep 24 16:58:55 ubuntustudio kernel: [   23.972000] Bluetooth: L2CAP socket layer initialized
Sep 24 16:58:55 ubuntustudio kernel: [   24.045000] Bluetooth: RFCOMM socket layer initialized
Sep 24 16:58:55 ubuntustudio kernel: [   24.045000] Bluetooth: RFCOMM TTY layer initialized
Sep 24 16:58:55 ubuntustudio kernel: [   24.045000] Bluetooth: RFCOMM ver 1.8
Sep 24 16:59:10 ubuntustudio kernel: [   38.657000] eth0: no IPv6 routers present
```

Sorry again for the length of that - But that's where the session ends.  I think it might have something to do with an obscure ACPI setting, but again, not entirely sure...

Any insight to the problem will be much appreciated.  

JamesJTucker, you mentioned something about changing the BIOS settings to compatible... I'm not familiar with that particular setting, though am by no means scared of navigating the BIOS at all haha - what should I be looking for?

Again, thanks for everyone's help.  It is GREATLY appreciated and you are fantastic members of the Ubuntu community.  

One last thing - if it comes down to it, I can take my home folder and simply import it into a new installation to keep all my settings and such, right?  

Thanks again!
-Bob

---

### Post by ddrichardson on 2007-09-25
The BIOS setting mentioned tends to affect drives not being detected at boot, especially with respect to installation - not knowing your BIOS it will have an option that says "SATA Mode", best set to "Compatability", check that first.

Yes you can import your home folder.

---

### Post by gwi on 2007-09-26
I am having the same kind of problems. I am getting messages like these (taken from handwritten notes while watching the messages appear during boot):
```
ata2: softreset failed, port not ready
ata2: softreset failed (timeout)
ata2.00: exception Emask 0x0 sAct 0x3C SErr 0x0 action 0x2 frozen
ata2.00: exception Emask 0x0 sAct 0x47 SErr 0x0 action 0x2 frozen
ata2: hardreset failed (PHY debouncing failed)
ata2.00: exception Emask 0x0 sAct 0x0 SErr 0x40d0000 action 0x2 frozen
irq_stat 0x00060002 failed to transmit command FIS
scsi 3:0:0:0: rejecting I/O to dead device
```
Above messages are not necessarily in the order they appeared in (as I said: handtaken notes while watching the screen). Some are there one time, some are repeated dozens of times.

Trying to solve the problem I tried:[LIST]
[*]three different motherboards (Asus A8N, Abit KN9, Asus M2N32);
[*]three different processors (Athlon64 3200+, Opteron165, AthlonX2 4800+);
[*]three different chipsets (nForce4, nForce570, nForce590);
[*]four different SATA controlers (in the chipsets mentioned above, and a SiI3124);
[*]two different SATA harddisks (Seagate Barracuda 7200.9, Western Digital WD5000AAKS);
[*]several cables and ports on the controllers.
[/LIST]
So far after every reinstall the system runs stable, but after a few weeks the problems start, at a rapidly increasing frequency. I use my computer for a few hours almost every day, and shutdown after use.

I have one SATA harddisk and one ATAPI DVDRW drive, so no raid, no SCSI, no ATA.
Right now, the system freezes before I can login, so forget about collecting logs.

Would be nice to see this problem solved. I is really starting to piss me off (and thinking "how would Vista do?"). The last four months I've spent more time trying to get my system running, than doing real work on it.

---

### Post by ddrichardson on 2007-09-26
gwi, are you using a low latency kernel too?

---

### Post by gwi on 2007-09-26
No, I am using the 2.6.20-16-generic kernel.

---

### Post by Rabidmonkey1 on 2007-09-26
The generic kernel still works fine for me though gwi's problem sounds very similar to mine...

---

### Post by ddrichardson on 2007-09-26
rabidmonkey, there are lines in kernel log setting the sata latency to 64 - is there only a problem with the generic kernel?

---

### Post by Rabidmonkey1 on 2007-09-27
The generic kernel is working for me at the moment.  It's the low latency that seems to be the problem.

---

### Post by SeanTater on 2007-09-27
If your hard disk is failing, you might confirm that by doing:

```
sudo apt-get install smartmontools
sudo smartctl -s on /dev/sda
sudo smartctl -a /dev/sda
sudo smartctl -H /dev/sda

```

If your drive does not support SMART, then that will give you a bunch of nothing, otherwise, it will tell you if it thinks your hard drive will die within 24 hours.

---

### Post by gwi on 2007-09-27
In my case I don't think it is the harddisk that is failing. I had the problem with two different drives (Seagate Barracuda 7200.9, Western Digital WD5000AAKS). I even used two WD5000AAKS drives (had the first one replaced under guarantee after a few weeks, just to make sure).

I never new of a SATA latency setting. Can I change the value via a config file?

---

### Post by ddrichardson on 2007-09-27
I don't know if you can change it, most likely it's set in the sata module. Just seems a coincidence that you're experiencing an issue with the low latency kernel and with the sata having a message regarding latency. It may be worth registering this as a bug with launchpad.

---

### Post by Rabidmonkey1 on 2007-09-29
GWI that is so odd, I've had trouble with the exact same WD drives - I had to return two of them before!

---

### Post by gwi on 2007-10-08
@Rabidmonkey1: I also had the problem with a Seagate Barracuda 7200.9, so I hope it is not drive related.

@ddrichardson: After the problems reoccurred, I switched the harddisk back from the SiI controller to the nForce. So far the system has been stable.

If it happens again after the upgrade to Gutsy, I'll post a bugreport.

---

### Post by Rabidmonkey1 on 2007-10-10
Thanks everyone for your help.  I've been doing some talking with people and it actually looks like my power supply was the culprit here - something with a weak 12 v line I think.  I went out and bought a 680 watt and returned the Hd's to western digital - hopefully the new power supply won't interfere with them any more.  Thanks again for everyone's help.

---

