---
title: "Please help: Numerous - ACPI, WiFi, Adept, sudo / kdesu etc.."
date: 2007-05-30
forum: General Help
---

### Post by Neobuntu on 2007-05-30
#1  Why would XP turn off and Kubuntu not (*anymore* on the desktops)?

My guess is an ACPI kernel conflict. I have, in the past, had success with old releases of Kubuntu (turning all the way off) but not now. I added commands to the boot string as I did then but nothing seems to work. Is the current kernel incompatible or what? Please help.

I just don't like leaving my computers on all the time. Also, assuming I have my important working files saved, what are the pros and cons of just hitting the big power switch. One can't beat that for shut down time saved.  Still, I want to click shutdown...leave, and know that (eventually) it will turn "off" (fan off etc...).

I've done just about everything I can find to speed booting up, (by the way) and I have fair results. 

#2 I've having a frustrating time with Wifi when it is on the fringe. I use "wlassistant" to see a signal bar for my router and to reconnect as it sometimes goes in and out of range. The problem is, after a few tries, the wlassistant CRASHES. Why? is there a better choice? The others I have seen, do not give this control; that I need.

#3 Many times when I exit Adept, I can't use any other means to upgrade due to an Adept running that I clearly closed (unless I reboot). What's up what that? I can't fix it by killing adept either. Strange.

#4 I've learned to use sudo with non-X programs (like nano) and to use kdesu(or gksudo with gnome) with X programs(like gedit). It bugs the heck out of me when sometimes though, the kdesu password popup dialog simply will not come up (again unless rebooted). What's the deal?

I have also noticed this, in the nice Kubuntu "system settings" (and then under network settings) when selecting the sometimes required "Administrator mode". Sometimes, there's just nothing; when you are waiting for a password dialog. Why?

These things are important to the future of, and to those where I have recommended Kubuntu. Thank you.

---

### Post by Neobuntu on 2007-05-30
I'm trying a method to fix hibernation now, also.

At one time (past) I got "suspend2" (with a kernel compile) to go up and down in about 3 seconds. What is the status of such things now?  So, I know it can be done (really fast full hibernation).

---

### Post by Neobuntu on 2007-05-31
Hibernation nor suspend is working so it's back to fixing powering off. HELP!

How do I get this machine to power off. It has before (older Kubuntu). Why not now?

---

### Post by sessine on 2007-05-31
For the shutdown problem, does it work if you shutdown from a terminal?
```
sudo shutdown -h now
```

---

### Post by Neobuntu on 2007-06-01
> acpi=force nor > apm power_off=1...in /etc/modules nor...> sudo shutdown -h now...seems to work. I wish it did not take so much time to test. Thank you (very much) though.

---

### Post by Neobuntu on 2007-06-01
I could really use some help. (Thanks again Sessine).

Actually, I'm shocked. Usually these things have fast fixes and many helpful ubuntu posts.

---

### Post by Neobuntu on 2007-06-02
Anybody?

---

### Post by Neobuntu on 2007-06-04
Motherboard is an ASUS A7S333 .

Could this be the problem?

This is mind numbing because it did work (Completely off; After Kubuntu) with past Kernels/releases. (2.6.18 I think).

Has anyone found a solution?

---

### Post by Neobuntu on 2007-06-08
Nobody?

I'm running the latest Kernel.

So this Asus board is just no longer supported?

---

### Post by dannyboy79 on 2007-06-08
we need to know more about your system. please post the following info.

lspci -v

dmesg

uname -r

And from your profile, Are you using Edgy Kubuntu? What are the boot options you booted with which last? I
Ok wait, what do you mean you trimmed down how long it takes to boot? If you messed within init.d stuff than that's most likely your problem as sudo shutdown -h now has to properly shut everything down thru init and if it trips over itself because you got rid of somethign than there's your reason. Please show me the results of 

ls -la

on every  single /etc/rcX.d/ directory (all the numbers as well as the S one). Example from my machine:
/etc/rc0.d$ ls -la
returns all this:

drwxr-xr-x   2 root root 4096 2007-05-27 22:28 .
drwxr-xr-x 115 root root 4096 2007-06-08 04:11 ..
lrwxrwxrwx   1 root root   13 2007-05-25 21:03 K01gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   17 2007-05-25 21:03 K01usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root   24 2007-05-26 19:20 K16mythtv-backend -> ../init.d/mythtv-backend
lrwxrwxrwx   1 root root   15 2007-05-25 21:03 K19hplip -> ../init.d/hplip
lrwxrwxrwx   1 root root   15 2007-05-27 22:28 K19samba -> ../init.d/samba
lrwxrwxrwx   1 root root   16 2007-05-25 21:03 K20apport -> ../init.d/apport
lrwxrwxrwx   1 root root   15 2007-05-26 19:18 K21mysql -> ../init.d/mysql
lrwxrwxrwx   1 root root   19 2007-05-26 19:18 K22mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx   1 root root   23 2007-05-26 19:18 K23mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx   1 root root   20 2007-05-25 21:03 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx   1 root root   20 2007-05-25 21:03 K50alsa-utils -> ../init.d/alsa-utils
-rw-r--r--   1 root root  355 2007-04-10 16:45 README
lrwxrwxrwx   1 root root   41 2007-05-25 21:03 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx   1 root root   22 2007-05-25 21:03 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx   1 root root   18 2007-05-25 21:03 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx   1 root root   17 2007-05-25 21:03 S30urandom -> ../init.d/urandom
lrwxrwxrwx   1 root root   22 2007-05-25 21:03 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx   1 root root   18 2007-05-25 21:03 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx   1 root root   20 2007-05-25 21:03 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx   1 root root   14 2007-05-25 21:03 S90halt -> ../init.d/halt


So please show me the output from every /etc/rcX.d/ directory.

---

### Post by Neobuntu on 2007-06-11
Thank you! See my next post for details.

---

### Post by Neobuntu on 2007-06-11
lspci -v```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 745 Host (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8083
        Flags: bus master, medium devsel, latency 32
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e7000000-e7ffffff
        Prefetchable memory behind bridge: eff00000-febfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at e600 [size=32]

00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8083
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at e6800000 (32-bit, non-prefetchable) [size=4K]

00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8083
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at e6000000 (32-bit, non-prefetchable) [size=4K]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8083
        Flags: bus master, fast devsel, latency 128
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at d800 [size=16]

00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: ASUSTeK Computer Inc. CMI8738 6ch-MX
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 19
        I/O ports at b000 [size=256]
        Capabilities: <access denied>

00:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Abocom Systems Inc Unknown device ab90
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at e5800000 (32-bit, non-prefetchable) [size=8K]
        Memory at e5000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <access denied>

00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at a800 [size=256]
        Memory at e4800000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 30000000 [disabled] [size=64K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 18
        Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at efff0000 [disabled] [size=64K]
        Capabilities: <access denied>

```

dmesg```

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fefc000 end: 000000001fffc000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fffc000 size: 0000000000003000 end: 000000001ffff000 type: 3
[    0.000000] copy_e820_map() start: 000000001ffff000 size: 0000000000001000 end: 0000000020000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffc000 (usable)
[    0.000000]  BIOS-e820: 000000001fffc000 - 000000001ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131068) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131068
[    0.000000]   HighMem    131068 ->   131068
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131068
[    0.000000] On node 0 totalpages: 131068
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125981 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5e80
[    0.000000] ACPI: RSDT (v001 ASUS   A7S333   0x42302e31 MSFT 0x31313031) @ 0x1fffc000
[    0.000000] ACPI: FADT (v001 ASUS   A7S333   0x42302e31 MSFT 0x31313031) @ 0x1fffc0b2
[    0.000000] ACPI: BOOT (v001 ASUS   A7S333   0x42302e31 MSFT 0x31313031) @ 0x1fffc030
[    0.000000] ACPI: MADT (v001 ASUS   A7S333   0x42302e31 MSFT 0x31313031) @ 0x1fffc058
[    0.000000] ACPI: DSDT (v001   ASUS A7S333   0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:6 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Detected 1659.662 MHz processor.
[   22.558085] Built 1 zonelists.  Total pages: 130045
[   22.558090] Kernel command line: root=UUID=40af16f4-8844-4f23-ad09-47cd5e2afe82 ro quiet splash acpi=force
[   22.558298] mapped APIC to ffffd000 (fee00000)
[   22.558302] mapped IOAPIC to ffffc000 (fec00000)
[   22.558306] Enabling fast FPU save and restore... done.
[   22.558309] Enabling unmasked SIMD FPU exception support... done.
[   22.558323] Initializing CPU#0
[   22.558389] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   22.559581] Console: colour VGA+ 80x25
[   22.560069] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.560465] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.580558] Memory: 507448k/524272k available (1992k kernel code, 16284k reserved, 900k data, 328k init, 0k highmem)
[   22.580571] virtual kernel memory layout:
[   22.580573]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   22.580574]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.580576]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   22.580577]     lowmem  : 0xc0000000 - 0xdfffc000   ( 511 MB)
[   22.580579]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   22.580580]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   22.580582]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   22.580586] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.658233] Calibrating delay using timer specific routine.. 3320.97 BogoMIPS (lpj=6641947)
[   22.658290] Security Framework v1.0.0 initialized
[   22.658300] SELinux:  Disabled at boot.
[   22.658322] Mount-cache hash table entries: 512
[   22.658520] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   22.658532] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.658535] CPU: L2 Cache: 256K (64 bytes/line)
[   22.658538] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   22.658556] Compat vDSO mapped to ffffe000.
[   22.658563] Remapping vsyscall page to ffffe000
[   22.658575] Checking 'hlt' instruction... OK.
[   22.674372] SMP alternatives: switching to UP code
[   22.674720] Freeing SMP alternatives: 11k freed
[   22.675061] Early unpacking initramfs... done
[   23.110600] ACPI: Core revision 20060707
[   23.111428] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.112646] CPU0: AMD Athlon(TM) XP 1500+ stepping 02
[   23.112674] Total of 1 processors activated (3320.97 BogoMIPS).
[   23.112781] ENABLING IO-APIC IRQs
[   23.112975] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.257354] Brought up 1 CPUs
[   23.257688] Booting paravirtualized kernel on bare hardware
[   23.257784] Time:  5:21:50  Date: 05/11/107
[   23.257833] NET: Registered protocol family 16
[   23.257976] EISA bus registered
[   23.257981] ACPI: bus type pci registered
[   23.259225] PCI: PCI BIOS revision 2.10 entry at 0xf19a0, last bus=1
[   23.259228] PCI: Using configuration type 1
[   23.259230] Setting up standard PCI resources
[   23.271553] ACPI: Interpreter enabled
[   23.271558] ACPI: Using IOAPIC for interrupt routing
[   23.272367] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   23.272602] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.272826] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.273060] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   23.273314] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.273538] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.273767] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.274003] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   23.275039] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.275046] PCI: Probing PCI hardware (bus 00)
[   23.275405] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   23.275675] Enabling SiS 96x SMBus.
[   23.276074] Boot video device is 0000:01:00.0
[   23.276121] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.313822] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   23.320463] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.320483] pnp: PnP ACPI init
[   23.324226] pnp: PnP ACPI: found 14 devices
[   23.324232] PnPBIOS: Disabled by ACPI PNP
[   23.324322] PCI: Using ACPI for IRQ routing
[   23.324327] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.328176] NET: Registered protocol family 8
[   23.328179] NET: Registered protocol family 20
[   23.328494] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[   23.328499] pnp: 00:02: ioport range 0xe480-0xe4ff has been reserved
[   23.328503] pnp: 00:02: ioport range 0xe600-0xe61f has been reserved
[   23.328507] pnp: 00:02: ioport range 0x480-0x48f has been reserved
[   23.328523] pnp: 00:0d: ioport range 0x290-0x297 has been reserved
[   23.328526] pnp: 00:0d: ioport range 0x500-0x507 has been reserved
[   23.328927] PCI: Bridge: 0000:00:01.0
[   23.328930]   IO window: disabled.
[   23.328936]   MEM window: e7000000-e7ffffff
[   23.328941]   PREFETCH window: eff00000-febfffff
[   23.328956] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.328995] NET: Registered protocol family 2
[   23.353267] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   23.353402] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   23.353697] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   23.353851] TCP: Hash tables configured (established 16384 bind 8192)
[   23.353855] TCP reno registered
[   23.365285] checking if image is initramfs... it is
[   24.186111] Freeing initrd memory: 8091k freed
[   24.186394] Simple Boot Flag at 0x3a set to 0x1
[   24.186814] audit: initializing netlink socket (disabled)
[   24.186835] audit(1181539310.708:1): initialized
[   24.186989] VFS: Disk quotas dquot_6.5.1
[   24.187020] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.187093] io scheduler noop registered
[   24.187097] io scheduler anticipatory registered
[   24.187100] io scheduler deadline registered
[   24.187109] io scheduler cfq registered (default)
[   24.224028] isapnp: Scanning for PnP cards...
[   24.576800] isapnp: No Plug & Play device found
[   24.615000] Real Time Clock Driver v1.12ac
[   24.615066] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.616209] mice: PS/2 mouse device common for all mice
[   24.616939] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.617294] input: Macintosh mouse button emulation as /class/input/input0
[   24.617338] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.617344] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.617628] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.617970] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.617976] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.618129] EISA: Probing bus 0 at eisa.0
[   24.618167] EISA: Detected 0 cards.
[   24.648241] TCP cubic registered
[   24.648250] NET: Registered protocol family 1
[   24.648283] Using IPI No-Shortcut mode
[   24.648391] ACPI: (supports S0 S1 S3 S4 S5)
[   24.648446]   Magic number: 11:176:365
[   24.649229] Freeing unused kernel memory: 328k freed
[   24.651077] Time: tsc clocksource has been installed.
[   24.668133] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.922566] Capability LSM initialized
[   25.943820] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   25.982203] ACPI: Invalid PBLK length [5]
[   26.111229] md: linear personality registered for level -1
[   26.116160] md: multipath personality registered for level -4
[   26.120980] md: raid0 personality registered for level 0
[   26.126331] md: raid1 personality registered for level 1
[   26.131092] raid5: automatically using best checksumming function: pIII_sse
[   26.148692]    pIII_sse  :  2378.000 MB/sec
[   26.148695] raid5: using function: pIII_sse (2378.000 MB/sec)
[   26.220621] raid6: int32x1    643 MB/s
[   26.288498] raid6: int32x2    713 MB/s
[   26.356424] raid6: int32x4    618 MB/s
[   26.424271] raid6: int32x8    421 MB/s
[   26.492183] raid6: mmxx1     1337 MB/s
[   26.560063] raid6: mmxx2     2066 MB/s
[   26.627943] raid6: sse1x1    1252 MB/s
[   26.695833] raid6: sse1x2    2126 MB/s
[   26.695836] raid6: using algorithm sse1x2 (2126 MB/s)
[   26.695842] md: raid6 personality registered for level 6
[   26.695844] md: raid5 personality registered for level 5
[   26.695847] md: raid4 personality registered for level 4
[   26.743158] md: raid10 personality registered for level 10
[   27.268714] usbcore: registered new interface driver usbfs
[   27.268750] usbcore: registered new interface driver hub
[   27.268784] usbcore: registered new device driver usb
[   27.269901] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.269955] ACPI: PCI Interrupt 0000:00:02.2[D] -> GSI 19 (level, low) -> IRQ 16
[   27.269973] ohci_hcd 0000:00:02.2: OHCI Host Controller
[   27.270196] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[   27.270222] ohci_hcd 0000:00:02.2: irq 16, io mem 0xe6800000
[   27.336749] usb usb1: configuration #1 chosen from 1 choice
[   27.336791] hub 1-0:1.0: USB hub found
[   27.336808] hub 1-0:1.0: 3 ports detected
[   27.417853] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   27.442890] ACPI: PCI Interrupt 0000:00:02.3[A] -> GSI 23 (level, low) -> IRQ 17
[   27.442917] ohci_hcd 0000:00:02.3: OHCI Host Controller
[   27.442964] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[   27.442991] ohci_hcd 0000:00:02.3: irq 17, io mem 0xe6000000
[   27.461102] Floppy drive(s): fd0 is 1.44M
[   27.504695] usb usb2: configuration #1 chosen from 1 choice
[   27.504735] hub 2-0:1.0: USB hub found
[   27.504755] hub 2-0:1.0: 3 ports detected
[   27.528467] FDC 0 is a post-1991 82077
[   27.612377] SIS5513: IDE controller at PCI slot 0000:00:02.5
[   27.612402] SIS5513: chipset revision 208
[   27.612405] SIS5513: not 100% native mode: will probe irqs later
[   27.612411] SIS5513: SiS745 ATA 100 (2nd gen) controller
[   27.612431]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:pio
[   27.612446]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:DMA, hdd:pio
[   27.612457] Probing IDE interface ide0...
[   27.750097] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   27.909926] hda: ST3200822A, ATA DISK drive
[   27.983456] usb 1-2: configuration #1 chosen from 1 choice
[   28.003393] usbcore: registered new interface driver hiddev
[   28.032641] input: Logitech Logitech Racing Wheel as /class/input/input2
[   28.032653] input: USB HID v1.10 Joystick [Logitech Logitech Racing Wheel] on usb-0000:00:02.2-2
[   28.032678] usbcore: registered new interface driver usbhid
[   28.032683] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   28.585133] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   28.589614] Probing IDE interface ide1...
[   29.327700] hdc: AOPEN CD-RW CRW5232 1.04 20031128, ATAPI CD/DVD-ROM drive
[   29.779100] hdd: Pioneer DVD-ROM ATAPIModel DVD-115 0128, ATAPI CD/DVD-ROM drive
[   29.839352] ide1 at 0x170-0x177,0x376 on irq 15
[   29.851730] SCSI subsystem initialized
[   29.859264] libata version 2.20 loaded.
[   29.866475] 8139cp 0000:00:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   29.866482] 8139cp 0000:00:0c.0: Try the "8139too" driver instead.
[   29.869638] 8139too Fast Ethernet driver 0.9.28
[   29.870096] PCI: Enabling device 0000:00:0c.0 (0004 -> 0007)
[   29.870109] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 19 (level, low) -> IRQ 16
[   29.870725] eth0: RealTek RTL8139 at 0xe0870000, 00:50:bf:93:c3:ab, IRQ 16
[   29.870729] eth0:  Identified 8139 chip type 'RTL-8139C'
[   29.886130] hda: max request size: 512KiB
[   29.904287] hda: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[   29.905652] hda: cache flushes supported
[   29.905725]  hda: hda1 hda2 hda3 hda4
[   29.959956] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   29.959971] Uniform CD-ROM driver Revision: 3.20
[   29.971141] hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   30.295257] Attempting manual resume
[   30.295263] swsusp: Resume From Partition 3:4
[   30.295265] PM: Checking swsusp image.
[   30.295560] PM: Resume from disk failed.
[   30.330325] kjournald starting.  Commit interval 5 seconds
[   30.330346] EXT3-fs: mounted filesystem with ordered data mode.
[   42.196288] eth0: link down
[   42.389198] NET: Registered protocol family 10
[   42.389329] lo: Disabled Privacy Extensions
[   42.389412] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.730574] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
[   44.804187] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[   45.161516] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.163906] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.236509] Linux agpgart interface v0.102 (c) Dave Jones
[   45.530271] agpgart: Detected SiS 745 chipset
[   45.535218] agpgart: AGP aperture is 64M @ 0xe8000000
[   45.681321] nvidia: module license 'NVIDIA' taints kernel.
[   45.687302] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[   45.687938] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7184  Tue Aug  1 18:38:58 PDT 2006
[   45.805890] input: PC Speaker as /class/input/input3
[   45.815727] usbcore: registered new interface driver xpad
[   45.815735] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   45.949339] parport: PnPBIOS parport detected.
[   45.949395] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   45.957140] logips2pp: Detected unknown logitech mouse model 1
[   46.168404] input: PS/2 Logitech Mouse as /class/input/input4
[   46.545092] PCI: Enabling device 0000:00:05.0 (0084 -> 0085)
[   46.545111] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 19
[   46.794240] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   46.888739] ndiswrapper: driver tnet1130 (Texas Instruments,06/17/2004,6.0.5.30) loaded
[   46.889196] PCI: Enabling device 0000:00:09.0 (0004 -> 0006)
[   46.889206] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 19
[   47.486793] ndiswrapper: using IRQ 19
[   48.037925] wlan0: ethernet device 00:e0:98:c6:50:89 using NDIS driver: tnet1130, version: 0x5000200, NDIS version: 0x501, vendor: 'TNET1130', 104C:9066.5.conf
[   48.038343] wlan0: encryption modes supported: WEP; TKIP with WPA
[   48.040996] usbcore: registered new interface driver ndiswrapper
[   48.080274] lp0: using parport0 (interrupt-driven).
[   48.161476] fuse init (API version 7.8)
[   48.161826] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.306391] EXT3 FS on hda2, internal journal
[   49.378437] NET: Registered protocol family 17
[   49.491760] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.320464] kjournald starting.  Commit interval 5 seconds
[   50.320478] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   50.433469] EXT3 FS on hda3, internal journal
[   50.433484] EXT3-fs: mounted filesystem with ordered data mode.
[   52.989354] input: Power Button (FF) as /class/input/input5
[   52.996387] ACPI: Power Button (FF) [PWRF]
[   53.044946] input: Power Button (CM) as /class/input/input6
[   53.051985] ACPI: Power Button (CM) [PWRB]
[   53.077899] Using specific hotkey driver
[   53.120624] No dock devices found.
[   53.181239] ibm_acpi: ec object not found
[   53.434334] pcc_acpi: loading...
[   57.510992] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   57.511020] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   57.511048] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   58.021793] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   58.021942] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   58.022062] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   58.207637] ppdev: user-space parallel port driver
[   58.924871] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   58.924880] apm: overridden by ACPI.
[   59.622982] wlan0: no IPv6 routers present
[   93.458650] Bluetooth: Core ver 2.11
[   93.459242] NET: Registered protocol family 31
[   93.459247] Bluetooth: HCI device and connection manager initialized
[   93.459252] Bluetooth: HCI socket layer initialized
```

uname -r
> 2.6.20-16-generic

/etc/rc0.d$ ls -la
```
total 16
drwxr-xr-x   2 root root 4096 2007-06-09 12:30 .
drwxr-xr-x 152 root root 8192 2007-06-11 05:23 ..
lrwxrwxrwx   1 root root   13 2006-11-19 19:56 K01gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   13 2006-10-27 11:31 K01kdm -> ../init.d/kdm
lrwxrwxrwx   1 root root   17 2006-06-15 03:48 K01usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root   16 2006-06-15 03:48 K19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root   15 2007-03-01 23:07 K19samba -> ../init.d/samba
lrwxrwxrwx   1 root root   19 2006-10-27 23:52 K19setserial -> ../init.d/setserial
lrwxrwxrwx   1 root root   23 2006-07-25 16:40 K20clamav-daemon -> ../init.d/clamav-daemon
lrwxrwxrwx   1 root root   26 2006-07-25 16:40 K20clamav-freshclam -> ../init.d/clamav-freshclam
lrwxrwxrwx   1 root root   14 2006-06-15 03:48 K20dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root   21 2006-07-10 02:55 K20firestarter -> ../init.d/firestarter
lrwxrwxrwx   1 root root   16 2006-10-28 16:25 K20hdparm -> ../init.d/hdparm
lrwxrwxrwx   1 root root   21 2006-06-15 03:48 K20laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root   17 2006-12-16 17:01 K20postfix -> ../init.d/postfix
lrwxrwxrwx   1 root root   20 2007-03-13 18:59 K20virtualbox -> ../init.d/virtualbox
lrwxrwxrwx   1 root root   20 2007-06-09 12:30 K20wifi-radar -> ../init.d/wifi-radar
lrwxrwxrwx   1 root root   15 2006-06-15 03:48 K21hplip -> ../init.d/hplip
lrwxrwxrwx   1 root root   24 2006-12-16 17:18 K24mythtv-backend -> ../init.d/mythtv-backend
lrwxrwxrwx   1 root root   20 2007-04-21 14:37 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx   1 root root   15 2006-06-15 03:48 K25mdadm -> ../init.d/mdadm
lrwxrwxrwx   1 root root   23 2006-10-27 23:51 K30etc-setserial -> ../init.d/etc-setserial
lrwxrwxrwx   1 root root   20 2006-06-15 03:48 K50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx   1 root root   13 2006-06-15 03:48 K86ppp -> ../init.d/ppp
-rw-r--r--   1 root root  355 2007-04-10 17:45 README
lrwxrwxrwx   1 root root   41 2006-06-15 03:48 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx   1 root root   22 2006-10-27 10:31 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx   1 root root   18 2006-06-15 03:48 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx   1 root root   17 2006-06-15 03:48 S30urandom -> ../init.d/urandom
lrwxrwxrwx   1 root root   22 2006-06-15 03:48 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx   1 root root   18 2006-06-15 03:48 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx   1 root root   14 2006-06-15 03:48 S49evms -> ../init.d/evms
lrwxrwxrwx   1 root root   13 2006-06-15 03:48 S50lvm -> ../init.d/lvm
lrwxrwxrwx   1 root root   20 2006-06-15 03:48 S50mdadm-raid -> ../init.d/mdadm-raid
lrwxrwxrwx   1 root root   20 2006-06-15 03:48 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx   1 root root   14 2006-06-15 03:48 S90halt -> ../init.d/halt

```

---

