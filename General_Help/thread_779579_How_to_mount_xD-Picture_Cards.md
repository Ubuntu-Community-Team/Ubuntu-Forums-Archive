---
title: "How to mount xD-Picture Cards?"
date: 2008-05-02
forum: General Help
---

### Post by Th3Professor on 2008-05-02
How do you mount 'em?

Thanks!

---

### Post by Th3Professor on 2008-05-03
[SIZE=1]bump[/SIZE]

---

### Post by Th3Professor on 2008-05-05
[bump]

I could clarify... actually, I'll be a little more generic... where in /dev could I possibly find the device that I'd use for mounting one of those picture cards (the card that saves photos on a digital camera)?

Thanks!

EDIT:
Update... dmesg | tail -n 20 has the "xD" card listed:
```
[188648.720960] tifm_core: SmartMedia/xD card detected in socket 0:0
[188648.904889] tifm0 : demand removing card from socket 0:0
[188649.595371] tifm_core: SmartMedia/xD card detected in socket 0:0
[188649.595457] tifm0 : demand removing card from socket 0:0
[188649.662241] tifm_core: SmartMedia/xD card detected in socket 0:0
```(It's listed multiple times possibly because I have inserted the card into the laptop and removed it more than once in testing it out.)

EDIT 2:
The fdisk list doesn't show the card.
(sudo fdisk -l)
I've installed "ivman" to try automounting media, though it isn't working.
(sudo /etc/init.d/ivman start)
I've also tried modprobe, also no luck.
(sudo modprobe tifm_sd)

---

### Post by zeller on 2008-05-13
Bump. I am having the same problem and need this resolved asap for work related issues. I am even getting the same dmesg as op only my socket is 0:2 instead of 0:0. All else is same.

Can anyone help please!?

---

### Post by Th3Professor on 2008-05-15
bump

---

### Post by fyo on 2008-05-15
Could you give the output for:

```
$ lspci
```

and

```
$ pccardctl status
```

---

### Post by Th3Professor on 2008-05-15
> **fyo said:**
> Could you give the output for:

```
$ lspci
```and

```
$ pccardctl status
```

Sure thing...

lspci:```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

There's the:
```

0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
``` in that lspci list.

pccardctl status (with and without a card in the slot)```

Socket 0:
  no card

```

---

### Post by fyo on 2008-05-15
OK, for that card reader others have expressed success with the following combo:

```
sudo modprobe tifm_7xx1
sudo modprobe tifm_core
sudo modprobe tifm_sd
```

where the last one is the same you tried earlier... They're all part of the same driver collection (for the TI PCIxx12 controller), so you probably need them all.

---

### Post by Th3Professor on 2008-05-15
> **fyo said:**
> OK, for that card reader others have expressed success with the following combo:

```
sudo modprobe tifm_7xx1
sudo modprobe tifm_core
sudo modprobe tifm_sd
```where the last one is the same you tried earlier... They're all part of the same driver collection (for the TI PCIxx12 controller), so you probably need them all.

Thanks for the info... I went ahead and tried it.

After doing the modprobe (w/ sudo) on all 3 of those I put the card in and...

...nothing happened.

I checked the "computer" window (shows CD/DVD and Filesystem folders) and there was nothing there.

Is there a specific device in /dev that I need to mount?

(I did another "pccardctl status" after the modprobes and re-inserting the card and it came up with "Socket 0: no card.")

The odd thing is, dmesg shows the card:
$ dmesg | grep xD
```

[36165.972062] tifm_core: SmartMedia/xD card detected in socket 0:0

```
After I removed the card, a fresh dmesg showed it removed:
```

[36535.581301] tifm0 : demand removing card from socket 0:0

```

---

### Post by autocrosser on 2008-05-16
I use a Olympus with the xD card format & I bought a Dazzle card reader a couple of years ago--It works very well & mounts the cards as xx.x MB Media. 

[http://reviews.cnet.com/flash-memory-adapters/dazzle-hi-speed-memory/4505-8898_7-30477792.html](http://reviews.cnet.com/flash-memory-adapters/dazzle-hi-speed-memory/4505-8898_7-30477792.html)

The CircuitCity reviews are very negative, but I've used mine for several years without a problem--I think this is one that works better in Linux :)

---

### Post by fyo on 2008-05-16
> **Th3Professor said:**
> The odd thing is, dmesg shows the card:


OK, so now at least the card reader appears to be working correctly with your system...

Usually, Ubuntu will drop an icon on the desktop if the card is automounted, but you can check in /media/ to be sure (that would be the logical place to have it mounted).

The easiest thing is probably just to see what device file pops up in /dev/ when you insert the card. Otherwise you should be able to deduce the information from dmesg (but not the line you provided - try looking at more lines than just greping for xD).

A good candidate would be /dev/mmcblk0 for the card and /dev/mmcblk0p1 for the first partition (and there would usually only be one).

---

### Post by Th3Professor on 2008-05-16
> **fyo said:**
> OK, so now at least the card reader appears to be working correctly with your system...

Usually, Ubuntu will drop an icon on the desktop if the card is automounted, but you can check in /media/ to be sure (that would be the logical place to have it mounted).

The easiest thing is probably just to see what device file pops up in /dev/ when you insert the card. Otherwise you should be able to deduce the information from dmesg (but not the line you provided - try looking at more lines than just greping for xD).

A good candidate would be /dev/mmcblk0 for the card and /dev/mmcblk0p1 for the first partition (and there would usually only be one).

No icon on desktop. Nothing in /media other than cdrom and cdrom0.

There's no change in /dev before and after inserting the card.

I'll include the big dmesg below... though I'm not sure what else to look or what to do with what would come up anyway.

I checked for /dev/mmcblk0 and /dev/mmcblk0p1 (and did a "find" for anything with characters similar to those) though nothing of the sort was in /dev.

There is, however, a /dev/dri/card0 though was unable to mount, doubt that's it.

Here's dmesg:
```

[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6e3000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 2166MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7190
[    0.000000] Entering add_active_range(0, 0, 784080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   784080
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   784080
[    0.000000] On node 0 totalpages: 784080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4333 pages used for memmap
[    0.000000]   HighMem zone: 550371 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7110 checksum 0
[    0.000000] ACPI: RSDP 000F7110, 0024 (r2 TOSCPL)
[    0.000000] ACPI: XSDT BF6D7A75, 009C (r1 TOSCPL TOSCPL00  6040000  LTP        0)
[    0.000000] ACPI: FACP BF6DFB60, 00F4 (r3 TOSCPL CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT BF6D8E1A, 6CD2 (r2 TOSCPL CRESTLNE  6040000 INTL 20060608)
[    0.000000] ACPI: FACS BF6E2FC0, 0040
[    0.000000] ACPI: APIC BF6DFC54, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET BF6DFCBC, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG BF6DFCF4, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA BF6DFD30, 0032 (r1 Intel  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TMOR BF6DFD62, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: SLIC BF6DFD88, 0176 (r1 TOSCPL TOSCPL00  6040000 LOHR        0)
[    0.000000] ACPI: OSFR BF6DFEFE, 0072 (r1 TOSHIB A+2nd ID  6040000 TASM  4010000)
[    0.000000] ACPI: APIC BF6DFF70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT BF6DFFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT BF6D8B6D, 02AD (r1 SataRe SataAhci     1000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6D8ACA, 00A3 (r1 BrtRef  DD01BRT     1000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6D809D, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6D7FF7, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6D7B11, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777955
[    0.000000] Kernel command line: root=UUID=80eda5e4-babf-4ef5-8ee7-bfac7f0c4620 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1828.797 MHz processor.
[   33.863026] Console: colour VGA+ 80x25
[   33.863029] console [tty0] enabled
[   33.863314] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   33.863600] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   34.017161] Memory: 3097892k/3136320k available (2157k kernel code, 37188k reserved, 998k data, 364k init, 2218816k highmem)
[   34.017168] virtual kernel memory layout:
[   34.017169]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   34.017170]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   34.017171]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   34.017172]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   34.017173]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   34.017174]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   34.017175]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   34.017178] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   34.017216] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   34.017359] hpet clockevent registered
[   34.097230] Calibrating delay using timer specific routine.. 3661.72 BogoMIPS (lpj=7323459)
[   34.097252] Security Framework initialized
[   34.097258] SELinux:  Disabled at boot.
[   34.097271] AppArmor: AppArmor initialized
[   34.097275] Failure registering capabilities with primary security module.
[   34.097283] Mount-cache hash table entries: 512
[   34.097401] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   34.097409] monitor/mwait feature present.
[   34.097410] using mwait in idle threads.
[   34.097414] CPU: L1 I cache: 32K, L1 D cache: 32K
[   34.097416] CPU: L2 cache: 2048K
[   34.097419] CPU: Physical Processor ID: 0
[   34.097420] CPU: Processor Core ID: 0
[   34.097422] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   34.097430] Compat vDSO mapped to ffffe000.
[   34.097442] Checking 'hlt' instruction... OK.
[   34.113557] SMP alternatives: switching to UP code
[   34.115062] Early unpacking initramfs... done
[   34.443223] ACPI: Core revision 20070126
[   34.443266] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   34.508459] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[   34.508474] SMP alternatives: switching to SMP code
[   34.509135] Booting processor 1/1 eip 3000
[   34.519340] Initializing CPU#1
[   34.596376] Calibrating delay using timer specific routine.. 3657.48 BogoMIPS (lpj=7314975)
[   34.596383] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   34.596387] monitor/mwait feature present.
[   34.596390] CPU: L1 I cache: 32K, L1 D cache: 32K
[   34.596392] CPU: L2 cache: 2048K
[   34.596394] CPU: Physical Processor ID: 0
[   34.596395] CPU: Processor Core ID: 1
[   34.596396] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   34.596864] CPU1: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[   34.596884] Total of 2 processors activated (7319.21 BogoMIPS).
[   34.597074] ENABLING IO-APIC IRQs
[   34.597265] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   34.744228] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   34.764209] Brought up 2 CPUs
[   34.764231] CPU0 attaching sched-domain:
[   34.764233]  domain 0: span 03
[   34.764235]   groups: 01 02
[   34.764238] CPU1 attaching sched-domain:
[   34.764239]  domain 0: span 03
[   34.764241]   groups: 02 01
[   34.764433] net_namespace: 64 bytes
[   34.764440] Booting paravirtualized kernel on bare hardware
[   34.764887] Time: 16:26:36  Date: 05/15/08
[   34.764912] NET: Registered protocol family 16
[   34.765079] EISA bus registered
[   34.765083] ACPI: bus type pci registered
[   34.765484] PCI: PCI BIOS revision 3.00 entry at 0xfde01, last bus=13
[   34.765486] PCI: Using configuration type 1
[   34.765487] Setting up standard PCI resources
[   34.767922] ACPI: EC: Look up EC in DSDT
[   34.775184] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   34.775680] ACPI: Interpreter enabled
[   34.775683] ACPI: (supports S0 S3 S4 S5)
[   34.775696] ACPI: Using IOAPIC for interrupt routing
[   34.782509] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   34.820715] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   34.820718] ACPI: EC: driver started in interrupt mode
[   34.820752] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   34.821852] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   34.821856] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   34.823395] PCI: Transparent bridge - 0000:00:1e.0
[   34.823499] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   34.823849] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   34.823973] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   34.824097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   34.824224] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   34.824347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[   34.824485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   34.837102] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   34.837204] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   34.837303] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   34.837401] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   34.837500] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   34.837598] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   34.837696] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   34.837794] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   34.837940] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.837966] pnp: PnP ACPI init
[   34.837973] ACPI: bus type pnp registered
[   34.860247] pnp: PnP ACPI: found 10 devices
[   34.860249] ACPI: ACPI bus type pnp unregistered
[   34.860252] PnPBIOS: Disabled by ACPI PNP
[   34.860436] PCI: Using ACPI for IRQ routing
[   34.860438] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   35.011684] NET: Registered protocol family 8
[   35.011686] NET: Registered protocol family 20
[   35.011715] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   35.011719] hpet0: 3 64-bit timers, 14318180 Hz
[   35.012752] AppArmor: AppArmor Filesystem Enabled
[   35.015671] Time: tsc clocksource has been installed.
[   35.015678] Switched to high resolution mode on CPU 0
[   35.015777] Switched to high resolution mode on CPU 1
[   35.031628] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   35.031631] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   35.031634] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   35.031636] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   35.031639] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   35.031641] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   35.031644] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   35.031646] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   35.031654] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   35.031660] system 00:06: ioport range 0x680-0x69f has been reserved
[   35.031662] system 00:06: ioport range 0x800-0x80f has been reserved
[   35.031664] system 00:06: ioport range 0x1000-0x107f has been reserved
[   35.031667] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   35.031669] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[   35.031672] system 00:06: ioport range 0xff00-0xff7f has been reserved
[   35.062014] PCI: Bridge: 0000:00:1c.0
[   35.062018]   IO window: 2000-2fff
[   35.062024]   MEM window: f0000000-f3ffffff
[   35.062029]   PREFETCH window: ce000000-cfffffff
[   35.062035] PCI: Bridge: 0000:00:1c.1
[   35.062039]   IO window: 3000-3fff
[   35.062045]   MEM window: f4000000-f7ffffff
[   35.062049]   PREFETCH window: cc000000-cdffffff
[   35.062055] PCI: Bridge: 0000:00:1c.2
[   35.062058]   IO window: 4000-4fff
[   35.062064]   MEM window: f8000000-fbffffff
[   35.062069]   PREFETCH window: ca000000-cbffffff
[   35.062075] PCI: Bridge: 0000:00:1c.3
[   35.062078]   IO window: 5000-5fff
[   35.062084]   MEM window: c4000000-c7ffffff
[   35.062088]   PREFETCH window: c8000000-c9ffffff
[   35.062094] PCI: Bridge: 0000:00:1c.4
[   35.062096]   IO window: disabled.
[   35.062101]   MEM window: disabled.
[   35.062106]   PREFETCH window: disabled.
[   35.062114] PCI: Failed to allocate mem resource #9:4000000@0 for 0000:0c:04.0
[   35.062117] PCI: Failed to allocate mem resource #10:4000000@0 for 0000:0c:04.0
[   35.062120] PCI: Bus 13, cardbus bridge: 0000:0c:04.0
[   35.062122]   IO window: 00001400-000014ff
[   35.062127]   IO window: 00006000-000060ff
[   35.062132] PCI: Bridge: 0000:00:1e.0
[   35.062133]   IO window: disabled.
[   35.062139]   MEM window: fc200000-fc2fffff
[   35.062143]   PREFETCH window: disabled.
[   35.062174] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   35.062182] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   35.062207] ACPI: PCI Interrupt 0000:00:1c.1[b] -> GSI 16 (level, low) -> IRQ 17
[   35.062213] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   35.062239] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   35.062245] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   35.062269] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   35.062275] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   35.062300] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 16
[   35.062305] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   35.062320] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   35.062338] ACPI: PCI Interrupt 0000:0c:04.0[A] -> GSI 16 (level, low) -> IRQ 17
[   35.062352] NET: Registered protocol family 2
[   35.099537] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   35.099743] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   35.100139] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   35.100347] TCP: Hash tables configured (established 131072 bind 65536)
[   35.100349] TCP reno registered
[   35.111580] checking if image is initramfs... it is
[   35.755886] Freeing initrd memory: 7687k freed
[   35.756027] Simple Boot Flag at 0x36 set to 0x1
[   35.756587] audit: initializing netlink socket (disabled)
[   35.756600] audit(1210868796.561:1): initialized
[   35.756821] highmem bounce pool size: 64 pages
[   35.758571] VFS: Disk quotas dquot_6.5.1
[   35.758638] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   35.758756] io scheduler noop registered
[   35.758758] io scheduler anticipatory registered
[   35.758760] io scheduler deadline registered
[   35.758770] io scheduler cfq registered (default)
[   35.758781] Boot video device is 0000:00:02.0
[   35.759009] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   35.759073] assign_interrupt_mode Found MSI capability
[   35.759126] Allocate Port Service[0000:00:1c.0:pcie00]
[   35.759154] Allocate Port Service[0000:00:1c.0:pcie02]
[   35.759255] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   35.759317] assign_interrupt_mode Found MSI capability
[   35.759366] Allocate Port Service[0000:00:1c.1:pcie00]
[   35.759396] Allocate Port Service[0000:00:1c.1:pcie02]
[   35.759497] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   35.759559] assign_interrupt_mode Found MSI capability
[   35.759609] Allocate Port Service[0000:00:1c.2:pcie00]
[   35.759636] Allocate Port Service[0000:00:1c.2:pcie02]
[   35.759736] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   35.759798] assign_interrupt_mode Found MSI capability
[   35.759847] Allocate Port Service[0000:00:1c.3:pcie00]
[   35.759876] Allocate Port Service[0000:00:1c.3:pcie02]
[   35.759987] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   35.760049] assign_interrupt_mode Found MSI capability
[   35.760098] Allocate Port Service[0000:00:1c.4:pcie00]
[   35.760132] Allocate Port Service[0000:00:1c.4:pcie02]
[   35.760369] isapnp: Scanning for PnP cards...
[   36.114214] isapnp: No Plug & Play device found
[   36.136540] Real Time Clock Driver v1.12ac
[   36.136756] hpet_resources: 0xfed00000 is busy
[   36.136785] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   36.137829] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   36.137892] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   36.137977] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   36.171931] serio: i8042 KBD port at 0x60,0x64 irq 1
[   36.171934] serio: i8042 AUX port at 0x60,0x64 irq 12
[   36.194681] mice: PS/2 mouse device common for all mice
[   36.194778] EISA: Probing bus 0 at eisa.0
[   36.194784] Cannot allocate resource for EISA slot 1
[   36.194787] Cannot allocate resource for EISA slot 2
[   36.194789] Cannot allocate resource for EISA slot 3
[   36.194790] Cannot allocate resource for EISA slot 4
[   36.194792] Cannot allocate resource for EISA slot 5
[   36.194794] Cannot allocate resource for EISA slot 6
[   36.194804] EISA: Detected 0 cards.
[   36.194807] cpuidle: using governor ladder
[   36.194808] cpuidle: using governor menu
[   36.194883] NET: Registered protocol family 1
[   36.194907] Using IPI No-Shortcut mode
[   36.194933] registered taskstats version 1
[   36.195047]   Magic number: 8:192:439
[   36.195107]   hash matches device 0000:00:1c.0
[   36.195117] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   36.195119] EDD information not available.
[   36.195308] Freeing unused kernel memory: 364k freed
[   36.215930] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   37.396598] fuse init (API version 7.9)
[   37.413822] ACPI: SSDT BF6D880C, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   37.414041] ACPI: SSDT BF6D82FC, 048B (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   37.415825] Monitor-Mwait will be used to enter C-1 state
[   37.415828] Monitor-Mwait will be used to enter C-2 state
[   37.415830] Monitor-Mwait will be used to enter C-3 state
[   37.415944] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   37.415949] ACPI: Processor [CPU0] (supports 8 throttling states)
[   37.416166] ACPI: SSDT BF6D8A02, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   37.416369] ACPI: SSDT BF6D8787, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   37.417320] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   37.417325] ACPI: Processor [CPU1] (supports 8 throttling states)
[   37.539666] usbcore: registered new interface driver usbfs
[   37.539692] usbcore: registered new interface driver hub
[   37.540100] usbcore: registered new device driver usb
[   37.541139] USB Universal Host Controller Interface driver v3.0
[   37.541181] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
[   37.541193] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   37.541197] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   37.541407] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   37.541443] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001820
[   37.541565] usb usb1: configuration #1 chosen from 1 choice
[   37.541587] hub 1-0:1.0: USB hub found
[   37.541591] hub 1-0:1.0: 2 ports detected
[   37.643233] ACPI: PCI Interrupt 0000:00:1a.1[b] -> GSI 21 (level, low) -> IRQ 20
[   37.643245] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   37.643249] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   37.643271] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   37.643305] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00001840
[   37.643410] usb usb2: configuration #1 chosen from 1 choice
[   37.643430] hub 2-0:1.0: USB hub found
[   37.643434] hub 2-0:1.0: 2 ports detected
[   37.747056] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[   37.747068] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   37.747073] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   37.747093] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   37.747127] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00001860
[   37.747233] usb usb3: configuration #1 chosen from 1 choice
[   37.747254] hub 3-0:1.0: USB hub found
[   37.747259] hub 3-0:1.0: 2 ports detected
[   37.850898] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 19
[   37.850911] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   37.850915] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   37.850939] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   37.850974] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[   37.851079] usb usb4: configuration #1 chosen from 1 choice
[   37.851100] hub 4-0:1.0: USB hub found
[   37.851105] hub 4-0:1.0: 2 ports detected
[   37.889542] SCSI subsystem initialized
[   37.916070] libata version 3.00 loaded.
[   37.954713] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   37.954725] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   37.954730] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   37.954753] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   37.954787] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[   37.954898] usb usb5: configuration #1 chosen from 1 choice
[   37.954920] hub 5-0:1.0: USB hub found
[   37.954925] hub 5-0:1.0: 2 ports detected
[   37.990559] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   38.058611] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   38.058627] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   38.058631] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   38.058654] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   38.062554] ehci_hcd 0000:00:1a.7: debug port 1
[   38.062560] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   38.062566] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc504800
[   38.119332] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   38.119439] usb usb6: configuration #1 chosen from 1 choice
[   38.119462] hub 6-0:1.0: USB hub found
[   38.119468] hub 6-0:1.0: 4 ports detected
[   38.223259] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[   38.223275] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   38.223279] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   38.223301] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   38.227203] ehci_hcd 0000:00:1d.7: debug port 1
[   38.227209] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   38.227215] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xfc504c00
[   38.243119] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   38.243214] usb usb7: configuration #1 chosen from 1 choice
[   38.243235] hub 7-0:1.0: USB hub found
[   38.243240] hub 7-0:1.0: 6 ports detected
[   38.346274] ACPI: PCI Interrupt 0000:0c:04.1[b] -> GSI 17 (level, low) -> IRQ 16
[   38.396029] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fc206000-fc2067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   38.396146] r8169 Gigabit Ethernet driver 2.2LK loaded
[   38.396178] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   38.396198] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   38.397439] ata_piix 0000:00:1f.1: version 2.12
[   38.397453] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
[   38.397485] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   38.397554] scsi0 : ata_piix
[   38.398533] scsi1 : ata_piix
[   38.399083] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   38.399086] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   38.513668] usb 2-1: device not accepting address 2, error -71
[   38.689362] Clocksource tsc unstable (delta = -5917459732 ns)
[   38.693465] Time: hpet clocksource has been installed.
[   38.695005] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T20F, ET02, max UDMA/33
[   38.703034] usb 6-3: new high speed USB device using ehci_hcd and address 2
[   38.783254] ata1.00: configured for UDMA/33
[   38.848893] usb 6-3: configuration #1 chosen from 1 choice
[   38.953530] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20F  ET02 PQ: 0 ANSI: 5
[   38.953858] ahci 0000:00:1f.2: version 3.0
[   38.953885] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 19
[   39.031650] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f83ad413a80]
[   39.057154] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   39.057161] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   39.057170] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   39.057434] scsi2 : ahci
[   39.057632] scsi3 : ahci
[   39.057769] scsi4 : ahci
[   39.057850] ata3: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 217
[   39.057854] ata4: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 217
[   39.057857] ata5: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504200 irq 217
[   39.090238] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   39.404347] ata3.00: ATA-7: TOSHIBA MK1637GSX, DL030M, max UDMA/100
[   39.404353] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   39.405359] ata3.00: configured for UDMA/100
[   39.425187] ata4: SATA link down (SStatus 0 SControl 300)
[   39.442869] ata5: SATA link down (SStatus 0 SControl 300)
[   39.443104] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL03 PQ: 0 ANSI: 5
[   39.456785] Driver 'sd' needs updating - please use bus_type methods
[   39.458123] Driver 'sr' needs updating - please use bus_type methods
[   39.461472] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   39.461493] sd 2:0:0:0: [sda] Write Protect is off
[   39.461497] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   39.461526] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.461598] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   39.461607] sd 2:0:0:0: [sda] Write Protect is off
[   39.461609] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   39.461624] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.461627]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   39.474908] Uniform CD-ROM driver Revision: 3.20
[   39.474979] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   39.512052]  sda1 sda2 sda3
[   39.542368] sd 2:0:0:0: [sda] Attached SCSI disk
[   39.546880] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   39.546900] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   39.744853] Attempting manual resume
[   39.744855] swsusp: Resume From Partition 8:3
[   39.744857] PM: Checking swsusp image.
[   39.745138] PM: Resume from disk failed.
[   39.805024] kjournald starting.  Commit interval 5 seconds
[   39.805054] EXT3-fs: mounted filesystem with ordered data mode.
[   47.156811] Linux agpgart interface v0.102
[   47.209346] agpgart: Detected an Intel 965GM Chipset.
[   47.210291] agpgart: Detected 7676K stolen memory.
[   47.223382] agpgart: AGP aperture is 256M @ 0xd0000000
[   47.344870] input: Power Button (FF) as /devices/virtual/input/input2
[   47.363394] ACPI: Power Button (FF) [PWRF]
[   47.363478] input: Lid Switch as /devices/virtual/input/input3
[   47.363544] ACPI: Lid Switch [LID0]
[   47.363601] input: Power Button (CM) as /devices/virtual/input/input4
[   47.395330] ACPI: Power Button (CM) [PWRB]
[   47.499201] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.532273] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.609996] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input5
[   47.634923] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   47.640525] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
[   47.666848] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   47.707452] ACPI: AC Adapter [ACAD] (on-line)
[   48.110221] ACPI: Battery Slot [BAT1] (battery present)
[   48.309829] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   48.309859] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   48.343437] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   48.401596] Linux video capture interface: v2.00
[   48.478501] iTCO_vendor_support: vendor-support=0
[   48.530477] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   48.532446] usbcore: registered new interface driver uvcvideo
[   48.532450] USB Video Class driver (v0.1.0)
[   48.607284] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   48.607366] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   48.607377] iTCO_wdt: No card detected
[   48.719962] ACPI: PCI Interrupt 0000:0c:04.2[C] -> GSI 18 (level, low) -> IRQ 18
[   48.765999] sdhci: Secure Digital Host Controller Interface driver
[   48.766003] sdhci: Copyright(c) Pierre Ossman
[   48.766046] sdhci: SDHCI controller found at 0000:0c:04.3 [104c:803c] (rev 0)
[   48.766069] ACPI: PCI Interrupt 0000:0c:04.3[C] -> GSI 18 (level, low) -> IRQ 18
[   48.766131] mmc0: SDHCI at 0xfc206800 irq 18 DMA
[   48.832853] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   48.832857] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   48.833008] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   48.833023] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   48.833050] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   48.971063] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   49.745077] input: PS/2 Mouse as /devices/virtual/input/input8
[   49.830442] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   50.110667] Yenta: CardBus bridge found at 0000:0c:04.0 [1179:ff00]
[   50.110698] PCI: Bus 13, cardbus bridge: 0000:0c:04.0
[   50.110700]   IO window: 00001400-000014ff
[   50.110705]   IO window: 00006000-000060ff
[   50.110710]   PREFETCH window: c2400000-c27fffff
[   50.110716]   MEM window: c2800000-c2bfffff
[   50.110724] Yenta: Enabling burst memory read transactions
[   50.110729] Yenta: Using CSCINT to route CSC interrupts to PCI
[   50.110731] Yenta: Routing CardBus interrupts to PCI
[   50.110737] Yenta TI: socket 0000:0c:04.0, mfunc 0x10a01b22, devctl 0x64
[   50.184814] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   50.185976] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   50.317763] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   50.317768] Socket status: 30000006
[   50.317770] Yenta: Raising subordinate bus# of parent bus (#0c) from #0d to #10
[   50.317775] pcmcia: parent PCI bridge Memory window: 0xfc200000 - 0xfc2fffff
[   50.468653] cs: IO port probe 0x100-0x3af: clean.
[   50.470780] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   50.471680] cs: IO port probe 0x820-0x8ff: clean.
[   50.472413] cs: IO port probe 0xc00-0xcf7: clean.
[   50.473325] cs: IO port probe 0xa00-0xaff: clean.
[   50.585845] lp: driver loaded but no devices found
[   50.706246] Adding 2008116k swap on /dev/sda3.  Priority:-1 extents:1 across:2008116k
[   51.029400] EXT3 FS on sda1, internal journal
[   51.655271] kjournald starting.  Commit interval 5 seconds
[   51.655625] EXT3 FS on sda2, internal journal
[   51.655632] EXT3-fs: mounted filesystem with ordered data mode.
[   52.283701] ip_tables: (C) 2000-2006 Netfilter Core Team
[   52.696140] No dock devices found.
[   53.875011] apm: BIOS not found.
[   54.022155] ppdev: user-space parallel port driver
[   54.180649] audit(1210868824.226:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5235 profile="/usr/sbin/cupsd" namespace="default"
[   55.360322] r8169: eth0: link up
[   55.360336] r8169: eth0: link up
[   55.369298] Bluetooth: Core ver 2.11
[   55.369932] NET: Registered protocol family 31
[   55.369937] Bluetooth: HCI device and connection manager initialized
[   55.369943] Bluetooth: HCI socket layer initialized
[   55.397505] Bluetooth: L2CAP ver 2.9
[   55.397511] Bluetooth: L2CAP socket layer initialized
[   55.507257] Bluetooth: RFCOMM socket layer initialized
[   55.507268] Bluetooth: RFCOMM TTY layer initialized
[   55.507270] Bluetooth: RFCOMM ver 1.8
[   56.952742] NET: Registered protocol family 17
[   57.249242] [drm] Initialized drm 1.1.0 20060810
[   57.258004] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   57.258018] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   57.258110] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   58.767978] NET: Registered protocol family 10
[   58.768391] lo: Disabled Privacy Extensions
[   58.771232] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   67.856497] eth0: no IPv6 routers present
[   86.352319] CPU0 attaching NULL sched-domain.
[   86.352325] CPU1 attaching NULL sched-domain.
[   86.369132] CPU0 attaching sched-domain:
[   86.369139]  domain 0: span 03
[   86.369142]   groups: 01 02
[   86.369148] CPU1 attaching sched-domain:
[   86.369151]  domain 0: span 03
[   86.369154]   groups: 02 01
[ 7616.930980] tifm_core: SmartMedia/xD card detected in socket 0:0
[ 8412.631769] tifm0 : demand removing card from socket 0:0
[ 8997.677684] UDF-fs: No VRS found
[ 8997.688054] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 8997.689282] ISOFS: changing to secondary root
[36165.972062] tifm_core: SmartMedia/xD card detected in socket 0:0
[36535.581301] tifm0 : demand removing card from socket 0:0
[48217.444009] r8169: eth0: link down
[48218.895303] r8169: eth0: link up
[48218.898785] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[48234.876487] eth0: no IPv6 routers present
[82503.479875] tifm_core: SmartMedia/xD card detected in socket 0:0

```

---

### Post by BandD on 2008-05-16
I have the same problem with my Sony Memory Stick Pro card reader.  Same thing, dmesg reconized the tifm event, but the system fails to actually do anything with the card.  

I tried openeing up Gparted just to see if it would show up there, no luck.

my lspci is:

```
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
```

dmesg output is:

```
[  229.707496] tifm_core: MemoryStick card detected in socket 0:1
[  229.877891] tifm0 : demand removing card from socket 0:1
```

and pccardctl status is:

```
Socket 0:
  no card
```

It seems to me that it is a mounting issue.  Is a bash script we can write or something to force the reader to mount when the tifm event is detected?  That seems to be what's missing...

---

### Post by BandD on 2008-05-17
After some poking around, I came across this info on the [tifm driver wiki]("http://openfacts.berlios.de/index-en.phtml?title=TI%20FlashMedia%20xx12%2Fxx21%20driver"):

> Version 0.6 of the driver is included with stock 2.6.19 release of the linux kernel. Version 0.8 is available in two subversions for 2.6.20 and 2.6.21 kernels and should be used as a replacement for the shipped (and quite unfortunately, buggy) one. It is merged into main kernel, as of version 2.6.22.

Get them here: [http://developer.berlios.de/project/showfiles.php?group_id=5510](http://developer.berlios.de/project/showfiles.php?group_id=5510).

Alternatively, you may consider looking at project's SVN: (alpha quality - [http://svn.berlios.de/wsvn/tifmxx/trunk/driver/?rev=0&sc=0](http://svn.berlios.de/wsvn/tifmxx/trunk/driver/?rev=0&sc=0)).

Driver is implemented using several modules:

    * tifm_core - serves as "bus" driver for the adapters and cards
    * tifm_7xx1 - "host" adapter for the pci device in question
    * tifm_sd - driver for MMC/SD cards (registers itself as mmc_host under kernel's mmc subsystem) 

Currently in development:

    * tifm_ms - driver for MemoryStick cards (beta). This driver is not very useful without higher level MemoryStick protocol drivers. These are found in the same svn repository. Their current status:
          o memstick - card identification driver (beta)
          o ms_block - legacy MemoryStick storage support (alpha)
          o mspro_block - MemoryStick Pro storage support (beta, has some problems) 

Early stages of development:

    * tifm_xd - driver for xD/SmartMedia cards 

Such complications are needed, because adapter's internal architecture appears to support all types of cards (SD, MS, XD) on every available socket (though external wiring is probably more limited). 

I also read on [this site]("http://www.thinkwiki.org/wiki/Tifm") that there are some known bugs in the implementation of this driver in the 2.6.24 kernel.  So perhaps these are the problems we are experincing...

---

### Post by Cresho on 2008-05-17
I use a silverstone cardreader.  It has all the cards but for some odd reason, cannt find the xd slot so I bought a xd to cf card adaptor and mount it in the silverstone cardreader.  It mounts flawlessly and I unmount it with the taskbar icon or in my computer in nautilus.  it's flawless.

---

### Post by BandD on 2008-05-17
I am now able to mount my Memory Stick Pro after using a patch found in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557")

I don't know that it will work with xD cards.  It seems that the development for xD cards is still in very early development.

---

### Post by Th3Professor on 2008-05-18
According to what's mentioned above (in a previous reply here), it looks like we won't (at least easily) get any xD cards to work for the time being, or so says that wiki page:

"Early stages of development:

    * tifm_xd - driver for xD/SmartMedia cards"

So perhaps when "they" finish developing tifm_xd we'll be able to use the xD card.

EDIT:

Okay, one of the links provided above shows this process, I haven't tried it yet (not sure about the svn step)...
```
svn co -r155 [http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/](http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/)
cd driver/
wget [http://www.tu-chemnitz.de/~sweh/tifm_ms.patch]("http://www.tu-chemnitz.de/%7Esweh/tifm_ms.patch")
patch -p0 < tifm_ms.patch
make
sudo make install Output from dmesg after patch:
[ 3267.243300] tifm_ms tifm_ms0:0: executing TPC b008, 6c17
[ 3267.243311] tifm_ms tifm_ms0:0: data event: fifo_status 8, host_status 4020, flags 0
[ 3267.243314] tifm_ms tifm_ms0:0: fifo data transfer, 8, 0
[ 3267.243325] tifm_ms tifm_ms0:0: fifo data transfer, 0 remaining
[ 3267.243342] tifm_ms tifm_ms0:0: host event: host_status 1020, flags 2
[ 3267.243350] tifm_ms tifm_ms0:0: TPC complete
[ 3267.243357] tifm_ms tifm_ms0:0: executing TPC e001, 6c17......
...........
```

---

### Post by Th3Professor on 2008-05-19
Has anybody had any luck with the steps I copied/pasted in my previous reply?

---

### Post by BandD on 2008-05-20
I had success with Memery Sitck Pro cards, I don't have any xD cards so I can't vouch for that.  But those are the steps I followed to get the MS Pro cards to work.  You can get the driver (still in alpha stage) from the same location as the svn step.

---

### Post by Th3Professor on 2008-05-21
svn doesn't come default with ubuntu, does it?

So would those steps work after installing the svn command?

---

### Post by BandD on 2008-05-22
Yeah when I fist tried to code an error message popped-up saying that I had to install the svn program--I can't remember the name of the program now.  But I just apt-get install-ed it and then tried the patch code again and it worked fine.

---

### Post by Th3Professor on 2008-05-22
I did the svn, etc. stuff, though afterwards, after inserting the card there's still nothing... should I try manually mounting it? Not sure where in /dev it'd be. There's not a /dev/mmcblk*(etc.)

I have the same output from lspci, dmesg, pccardctl, etc. as previously posted.

---

### Post by xr0ckstar on 2008-12-08
> **BandD said:**
> I am now able to mount my Memory Stick Pro after using a patch found in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557")

I don't know that it will work with xD cards.  It seems that the development for xD cards is still in very early development.

I tried this method and I got stuck on the 'Make'  this is my terminal errors


xr0ckstar@Lapbuntu:~$ svn co -r155 [http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/](http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/)
Checked out revision 155.
xr0ckstar@Lapbuntu:~$ cd driver/
xr0ckstar@Lapbuntu:~/driver$ wget [http://www.sw83.de/misc/tifm_ms.patch](http://www.sw83.de/misc/tifm_ms.patch)
--19:59:06--  [http://www.sw83.de/misc/tifm_ms.patch](http://www.sw83.de/misc/tifm_ms.patch)
           => `tifm_ms.patch'
Resolving [www.sw83.de](www.sw83.de)... 209.85.171.121
Connecting to [www.sw83.de|209.85.171.121|:80](www.sw83.de|209.85.171.121|:80)... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://files.sw83.de/misc/tifm_ms.patch](http://files.sw83.de/misc/tifm_ms.patch) [following]
--19:59:06--  [http://files.sw83.de/misc/tifm_ms.patch](http://files.sw83.de/misc/tifm_ms.patch)
           => `tifm_ms.patch'
Resolving files.sw83.de... 213.187.85.131
Connecting to files.sw83.de|213.187.85.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,652 (2.6K) [text/x-diff]

100%[====================================>] 2,652         10.24K/s             

19:59:07 (10.22 KB/s) - `tifm_ms.patch' saved [2652/2652]

xr0ckstar@Lapbuntu:~/driver$ patch -p0 < tifm_ms.patch
patching file tifm_ms.c
patching file mspro_block.c
patching file Makefile
xr0ckstar@Lapbuntu:~/driver$ make
echo /home/xr0ckstar/driver
/home/xr0ckstar/driver
make -C /lib/modules/2.6.24-22-rt/build M=/home/xr0ckstar/driver
make: *** /lib/modules/2.6.24-22-rt/build: No such file or directory.  Stop.
make: *** [all] Error 2
xr0ckstar@Lapbuntu:~/driver$ sudo make install
mkdir -p /lib/modules/2.6.24-22-rt
install -c -m 644 tifm_ms.ko memstick.ko mspro_block.ko /lib/modules/2.6.24-22-rt/kernel/drivers/misc/
install: cannot stat `tifm_ms.ko': No such file or directory
install: cannot stat `memstick.ko': No such file or directory
install: cannot stat `mspro_block.ko': No such file or directory
make: *** [install] Error 1

---

### Post by commbba on 2009-03-29
```
sudo modprobe tifm_7xx1
sudo modprobe tifm_core
sudo modprobe tifm_sd
```

I bought an external card reader for reading xd-picture cards and had the same problem,till I entered the above lines.I reentered the xd card and recognized it.An memory stick I'm having recognized it right out of the box.

Thank you for your help.

---

### Post by commbba on 2009-03-30
Unfortunately my luck didn't last long.I have 2 xd-picture cards,an 512 mb and an 2GB.Both recognized by the system but the 2GB card,every time I'm trying to open any data from it unmount it.I've tried to copy-paste the files,same result.I can have the folders open for long time but every time I'm trying to reach a photo,unmounts the volume.With the 512mb that is not happening.I've already copied the photos on the 512mb card.

Lol.I tested the 2GB card with a 32mb memory stick also in the card reader and managed to open and copy the files from the 2GB xd card.Sometimes Linux makes me mad.What conflicts with the 2GB xd card alone and not with the memory stick aside?

---

