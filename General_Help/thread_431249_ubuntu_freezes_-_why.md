---
title: "ubuntu freezes - why?"
date: 2007-05-02
forum: General Help
---

### Post by r2d22 on 2007-05-02
i have a the 7.04 version of ubuntu installed on my VIA KTS 600a motherboard, with 1256 megs of RAM, and using both IDE and SATA for HD.

ubuntu simply freezes when it feels like it. there's no logical reason behind it. sometimes i just move the mouse with nothing running in the background, and it'll just freeze.

when i say freeze i mean the mouse gets stuck, and i'm pretty sure the system is down.

as a newbie who wants to continue using this OS, i simply don't know what to do.

help!

---

### Post by mishranurag on 2007-05-02
I am experiencing same problem today.  Sometimes it would just halt during the boot process. God know what got it stuck.

---

### Post by RTrev on 2007-05-02
> **r2d22 said:**
> i have a the 7.04 version of ubuntu installed on my VIA KTS 600a motherboard, with 1256 megs of RAM, and using both IDE and SATA for HD.

ubuntu simply freezes when it feels like it. there's no logical reason behind it. sometimes i just move the mouse with nothing running in the background, and it'll just freeze.

when i say freeze i mean the mouse gets stuck, and i'm pretty sure the system is down.

as a newbie who wants to continue using this OS, i simply don't know what to do.

help!

That happened to me when I simultaneously built a new machine and installed the new Feisty.  Turned out we had the memory in the wrong slots.  It hasn't frozen on me once since we fixed that.   It's only your mention of a memory value I haven't often seen that reminded me of this.. and I figure it can't hurt to mention it.  :)

---

### Post by RTrev on 2007-05-02
> **mishranurag said:**
> I am experiencing same problem today.  Sometimes it would just halt during the boot process. God know what got it stuck.

Have you looked at the log files from the times it got hung?  That might give you a clue..

---

### Post by r2d22 on 2007-05-02
(blush)

where are they?

i will try the memory thing now.

---

### Post by mishranurag on 2007-05-02
My system was working fine under UBUNTU for last one and half years and my Windows is absolutely ok. So I guess memory slot is not an issue.  Regarding logs, how to get that, when UBUNTU freezes within seconds of login, and sometimes halts during boot.

Anurag

---

### Post by r2d22 on 2007-05-02
regarding memory: i stand corrected. i have 2 1GB cards in there. there are 3 slot, so i moved one of them to the other slot. we'll see...

ok, the logs are in /var/log/ what are they called?

(p.s. mishranurag, you could start it up in the recovery mode and reach them that way. i think...)

---

### Post by RTrev on 2007-05-02
Well, I'm new to this stuff, but I've looked at the log files to see what's going on during boot.  Sometimes I've gotten lucky and it's been obvious what was wrong.. like a typo in xorg.conf which led to the system not finding any screens to use.

The logs are in /var/logs, and can also be gotten to via the menus - System | Administration | System Log.

Beyond that, I probably can't help much.  I'm not sure what happens to old logs, but I believe they get rotated and probably stored in compressed format somewhere for a given length of time.  There is a menu option in the log viewer, which shows you which dates you can view, but I just noticed in mine that today is the only date available.  I need to learn more about Linux basics!  I believe that if you reboot successfully after a failure, you should be able to see whatever got written to the log during the failed boot.  That is, if you reboot the previous log for the same day should be viewable.  Hopefully somebody more knowledgeable will happen along.  

There is another option you could try, which is turning off the "uslpash" screen so you can see the messages as the system is actually booting.  I'm not certain how to do that, and a Google for it didn't find an explicit way to do it.. but if you can find that then you should be able to see where the hang occurs.

Addendum: just found that at the top of the viewed log files is a little triangle you can click on to close the current log being viewed and look at previous dates.  Hope this helps!

---

### Post by RTrev on 2007-05-03
> **r2d22 said:**
> regarding memory: i stand corrected. i have 2 1GB cards in there. there are 3 slot, so i moved one of them to the other slot. we'll see...

ok, the logs are in /var/log/ what are they called?

(p.s. mishranurag, you could start it up in the recovery mode and reach them that way. i think...)

Do you have access to the manual for your BIOS?  Mine was very specific about where the memory had to be put, depending on how many slots were going to be used.  Maybe you can find your BIOS manual on-line somewhere?

---

### Post by ubnewbie2 on 2007-05-03
To eliminate doubts on memory, boot off the live install disk, and choose the memory test from the menu.  Let that run for a while.  It is surprising sometimes how systems can suddenly fail under a newly installed system.  What usually happens is the old system was just lucky not to use the bad memory locations, and the new one is not so lucky :(

---

### Post by r2d22 on 2007-05-03
hmm. my motherboard manual says "you must install at least one module in any of the 3 slots". so, even though the system is not crashing AS OFTEN as it did yesterday (every 20 minutes or so yesterday, every few hours today), it's not that.

i checked the logs (thanks for the location!), and i can't seem to find any error messages. when it crashes, it doesn't leave anything behind.

here's my syslog - can anyone find out what's going on (next post, this one is too long)?

---

### Post by r2d22 on 2007-05-03
May  3 14:38:41 big-room-ubuntu syslogd 1.4.1#20ubuntu4: restart.
May  3 14:38:41 big-room-ubuntu anacron[5266]: Job `cron.daily' terminated
May  3 14:38:41 big-room-ubuntu anacron[5266]: Normal exit (1 job run)
May  3 14:38:45 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  3 14:38:54 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  3 14:39:03 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
May  3 14:39:04 big-room-ubuntu dhclient: No DHCPOFFERS received.
May  3 14:39:04 big-room-ubuntu dhclient: No working leases in persistent database - sleeping.
May  3 14:42:17 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May  3 14:42:20 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  3 14:42:28 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May  3 14:42:42 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  3 14:42:48 big-room-ubuntu dhclient: No DHCPOFFERS received.
May  3 14:42:48 big-room-ubuntu dhclient: No working leases in persistent database - sleeping.
May  3 14:46:34 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May  3 14:46:37 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  3 14:46:42 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May  3 14:46:54 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May  3 14:47:05 big-room-ubuntu dhclient: No DHCPOFFERS received.
May  3 14:47:05 big-room-ubuntu dhclient: No working leases in persistent database - sleeping.
May  3 15:14:44 big-room-ubuntu syslogd 1.4.1#20ubuntu4: restart.
May  3 15:14:44 big-room-ubuntu kernel: Inspecting /boot/System.map-2.6.20-15-generic
May  3 15:14:44 big-room-ubuntu kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
May  3 15:14:44 big-room-ubuntu kernel: Symbols match kernel version 2.6.20.
May  3 15:14:44 big-room-ubuntu kernel: No module symbols loaded - kernel modules not enabled. 
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] sanitize start
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] sanitize end
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009dc00 end: 000000000009dc00 type: 1
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() start: 000000000009dc00 size: 0000000000002400 end: 00000000000a0000 type: 2
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fef0000 end: 000000007fff0000 type: 1
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() start: 000000007fff0000 size: 0000000000003000 end: 000000007fff3000 type: 4
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() start: 000000007fff3000 size: 000000000000d000 end: 0000000080000000 type: 3
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] 1151MB HIGHMEM available.
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] 896MB LOWMEM available.
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] found SMP MP-table at 000f5290
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] Zone PFN ranges:
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]   DMA             0 ->     4096
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]   Normal       4096 ->   229376
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]   HighMem    229376 ->   524272
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]     0:        0 ->   524272
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] On node 0 totalpages: 524272
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]   HighMem zone: 2303 pages used for memmap
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] DMI 2.2 present.
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: RSDP (v000 KT600                                 ) @ 0x000f6c50
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: RSDT (v001 KT600  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff3000
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: FADT (v001 KT600  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff3040
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: MADT (v001 KT600  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff7a80
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: DSDT (v001 KT600  AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] Processor #0 6:8 APIC version 16
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
May  3 15:14:44 big-room-ubuntu kernel: [    0.000000] Detected 2158.209 MHz processor.
May  3 15:14:44 big-room-ubuntu kernel: [   20.391018] Built 1 zonelists.  Total pages: 520177
May  3 15:14:44 big-room-ubuntu kernel: [   20.391022] Kernel command line: root=UUID=6701695f-4e45-42d9-916b-3a572587662b ro quiet splash
May  3 15:14:44 big-room-ubuntu kernel: [   20.391180] mapped APIC to ffffd000 (fee00000)
May  3 15:14:44 big-room-ubuntu kernel: [   20.391183] mapped IOAPIC to ffffc000 (fec00000)
May  3 15:14:44 big-room-ubuntu kernel: [   20.391186] Enabling fast FPU save and restore... done.
May  3 15:14:44 big-room-ubuntu kernel: [   20.391189] Enabling unmasked SIMD FPU exception support... done.
May  3 15:14:44 big-room-ubuntu kernel: [   20.391200] Initializing CPU#0
May  3 15:14:44 big-room-ubuntu kernel: [   20.391277] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  3 15:14:44 big-room-ubuntu kernel: [   20.392506] Console: colour VGA+ 80x25
May  3 15:14:44 big-room-ubuntu kernel: [   20.393350] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  3 15:14:44 big-room-ubuntu kernel: [   20.394646] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  3 15:14:44 big-room-ubuntu kernel: [   20.483408] Memory: 2068140k/2097088k available (1992k kernel code, 27648k reserved, 893k data, 328k init, 1179584k highmem)
May  3 15:14:44 big-room-ubuntu kernel: [   20.483418] virtual kernel memory layout:
May  3 15:14:44 big-room-ubuntu kernel: [   20.483419]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
May  3 15:14:44 big-room-ubuntu kernel: [   20.483420]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May  3 15:14:44 big-room-ubuntu kernel: [   20.483421]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
May  3 15:14:44 big-room-ubuntu kernel: [   20.483422]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
May  3 15:14:44 big-room-ubuntu kernel: [   20.483424]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
May  3 15:14:44 big-room-ubuntu kernel: [   20.483425]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
May  3 15:14:44 big-room-ubuntu kernel: [   20.483426]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
May  3 15:14:44 big-room-ubuntu kernel: [   20.483429] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May  3 15:14:44 big-room-ubuntu kernel: [   20.563109] Calibrating delay using timer specific routine.. 4319.94 BogoMIPS (lpj=8639890)
May  3 15:14:44 big-room-ubuntu kernel: [   20.563163] Security Framework v1.0.0 initialized
May  3 15:14:44 big-room-ubuntu kernel: [   20.563173] SELinux:  Disabled at boot.
May  3 15:14:44 big-room-ubuntu kernel: [   20.563193] Mount-cache hash table entries: 512
May  3 15:14:44 big-room-ubuntu kernel: [   20.563383] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
May  3 15:14:44 big-room-ubuntu kernel: [   20.563393] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  3 15:14:44 big-room-ubuntu kernel: [   20.563395] CPU: L2 Cache: 256K (64 bytes/line)
May  3 15:14:44 big-room-ubuntu kernel: [   20.563398] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
May  3 15:14:44 big-room-ubuntu kernel: [   20.563411] Compat vDSO mapped to ffffe000.
May  3 15:14:44 big-room-ubuntu kernel: [   20.563418] Remapping vsyscall page to ffffe000
May  3 15:14:44 big-room-ubuntu kernel: [   20.563431] Checking 'hlt' instruction... OK.
May  3 15:14:44 big-room-ubuntu kernel: [   20.579265] SMP alternatives: switching to UP code
May  3 15:14:44 big-room-ubuntu kernel: [   20.579603] Freeing SMP alternatives: 11k freed
May  3 15:14:44 big-room-ubuntu kernel: [   20.579884] Early unpacking initramfs... done
May  3 15:14:44 big-room-ubuntu kernel: [   20.864579] ACPI: Core revision 20060707
May  3 15:14:44 big-room-ubuntu kernel: [   20.867078] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
May  3 15:14:44 big-room-ubuntu kernel: [   20.870982] CPU0: AMD Athlon(tm) XP 2700+ stepping 01
May  3 15:14:44 big-room-ubuntu kernel: [   20.871009] Total of 1 processors activated (4319.94 BogoMIPS).
May  3 15:14:44 big-room-ubuntu kernel: [   20.871743] ENABLING IO-APIC IRQs
May  3 15:14:44 big-room-ubuntu kernel: [   20.872047] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May  3 15:14:44 big-room-ubuntu kernel: [   21.018701] Brought up 1 CPUs
May  3 15:14:44 big-room-ubuntu kernel: [   21.018985] Booting paravirtualized kernel on bare hardware
May  3 15:14:44 big-room-ubuntu kernel: [   21.019084] Time: 15:14:16  Date: 04/03/107
May  3 15:14:44 big-room-ubuntu kernel: [   21.019123] NET: Registered protocol family 16
May  3 15:14:44 big-room-ubuntu kernel: [   21.019231] EISA bus registered
May  3 15:14:44 big-room-ubuntu kernel: [   21.019236] ACPI: bus type pci registered
May  3 15:14:44 big-room-ubuntu kernel: [   21.024135] PCI: PCI BIOS revision 2.10 entry at 0xfb360, last bus=1
May  3 15:14:44 big-room-ubuntu kernel: [   21.024137] PCI: Using configuration type 1
May  3 15:14:44 big-room-ubuntu kernel: [   21.024139] Setting up standard PCI resources
May  3 15:14:44 big-room-ubuntu kernel: [   21.035135] ACPI: Interpreter enabled
May  3 15:14:44 big-room-ubuntu kernel: [   21.035142] ACPI: Using IOAPIC for interrupt routing
May  3 15:14:44 big-room-ubuntu kernel: [   21.035830] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  3 15:14:44 big-room-ubuntu kernel: [   21.035836] PCI: Probing PCI hardware (bus 00)
May  3 15:14:44 big-room-ubuntu kernel: [   21.035926] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
May  3 15:14:44 big-room-ubuntu kernel: [   21.036162] Boot video device is 0000:00:0a.0
May  3 15:14:44 big-room-ubuntu kernel: [   21.036720] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  3 15:14:44 big-room-ubuntu kernel: [   21.067816] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
May  3 15:14:44 big-room-ubuntu kernel: [   21.068119] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
May  3 15:14:44 big-room-ubuntu kernel: [   21.068427] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
May  3 15:14:44 big-room-ubuntu kernel: [   21.068736] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *5
May  3 15:14:44 big-room-ubuntu kernel: [   21.069002] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.069270] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.069531] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.069801] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.070145] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.070478] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.070845] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.071186] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.073675] Linux Plug and Play Support v0.97 (c) Adam Belay
May  3 15:14:44 big-room-ubuntu kernel: [   21.073690] pnp: PnP ACPI init
May  3 15:14:44 big-room-ubuntu kernel: [   21.077448] pnp: PnP ACPI: found 13 devices
May  3 15:14:44 big-room-ubuntu kernel: [   21.077454] PnPBIOS: Disabled by ACPI PNP
May  3 15:14:44 big-room-ubuntu kernel: [   21.077525] PCI: Using ACPI for IRQ routing
May  3 15:14:44 big-room-ubuntu kernel: [   21.077530] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May  3 15:14:44 big-room-ubuntu kernel: [   21.100080] NET: Registered protocol family 8
May  3 15:14:44 big-room-ubuntu kernel: [   21.100082] NET: Registered protocol family 20
May  3 15:14:44 big-room-ubuntu kernel: [   21.100433] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
May  3 15:14:44 big-room-ubuntu kernel: [   21.100437] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
May  3 15:14:44 big-room-ubuntu kernel: [   21.100739] PCI: Bridge: 0000:00:01.0
May  3 15:14:44 big-room-ubuntu kernel: [   21.100741]   IO window: disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.100745]   MEM window: disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.100748]   PREFETCH window: disabled.
May  3 15:14:44 big-room-ubuntu kernel: [   21.100765] PCI: Setting latency timer of device 0000:00:01.0 to 64
May  3 15:14:44 big-room-ubuntu kernel: [   21.100795] NET: Registered protocol family 2
May  3 15:14:44 big-room-ubuntu kernel: [   21.130645] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  3 15:14:44 big-room-ubuntu kernel: [   21.130902] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  3 15:14:44 big-room-ubuntu kernel: [   21.132828] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  3 15:14:44 big-room-ubuntu kernel: [   21.133805] TCP: Hash tables configured (established 131072 bind 65536)
May  3 15:14:44 big-room-ubuntu kernel: [   21.133809] TCP reno registered
May  3 15:14:44 big-room-ubuntu kernel: [   21.142690] checking if image is initramfs... it is
May  3 15:14:44 big-room-ubuntu kernel: [   21.676676] Freeing initrd memory: 6751k freed
May  3 15:14:44 big-room-ubuntu kernel: [   21.677214] audit: initializing netlink socket (disabled)
May  3 15:14:44 big-room-ubuntu kernel: [   21.677232] audit(1178205257.364:1): initialized
May  3 15:14:44 big-room-ubuntu kernel: [   21.677306] highmem bounce pool size: 64 pages
May  3 15:14:44 big-room-ubuntu kernel: [   21.677373] VFS: Disk quotas dquot_6.5.1
May  3 15:14:44 big-room-ubuntu kernel: [   21.677399] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  3 15:14:44 big-room-ubuntu kernel: [   21.677461] io scheduler noop registered
May  3 15:14:44 big-room-ubuntu kernel: [   21.677463] io scheduler anticipatory registered
May  3 15:14:44 big-room-ubuntu kernel: [   21.677466] io scheduler deadline registered
May  3 15:14:44 big-room-ubuntu kernel: [   21.677473] io scheduler cfq registered (default)
May  3 15:14:44 big-room-ubuntu kernel: [   21.677545] PCI: Bypassing VIA 8237 APIC De-Assert Message
May  3 15:14:44 big-room-ubuntu kernel: [   21.677789] isapnp: Scanning for PnP cards...
May  3 15:14:44 big-room-ubuntu kernel: [   22.031218] isapnp: No Plug & Play device found
May  3 15:14:44 big-room-ubuntu kernel: [   22.061894] Real Time Clock Driver v1.12ac
May  3 15:14:44 big-room-ubuntu kernel: [   22.061950] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May  3 15:14:44 big-room-ubuntu kernel: [   22.062061] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  3 15:14:44 big-room-ubuntu kernel: [   22.062320] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  3 15:14:44 big-room-ubuntu kernel: [   22.063031] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  3 15:14:44 big-room-ubuntu kernel: [   22.063385] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  3 15:14:44 big-room-ubuntu kernel: [   22.063681] mice: PS/2 mouse device common for all mice
May  3 15:14:44 big-room-ubuntu kernel: [   22.064248] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May  3 15:14:44 big-room-ubuntu kernel: [   22.064520] input: Macintosh mouse button emulation as /class/input/input0
May  3 15:14:44 big-room-ubuntu kernel: [   22.064554] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May  3 15:14:44 big-room-ubuntu kernel: [   22.064559] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May  3 15:14:44 big-room-ubuntu kernel: [   22.064798] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  3 15:14:44 big-room-ubuntu kernel: [   22.064800] PNP: PS/2 controller doesn't have AUX irq; using default 12
May  3 15:14:44 big-room-ubuntu kernel: [   22.065175] serio: i8042 KBD port at 0x60,0x64 irq 1
May  3 15:14:44 big-room-ubuntu kernel: [   22.065180] serio: i8042 AUX port at 0x60,0x64 irq 12
May  3 15:14:44 big-room-ubuntu kernel: [   22.065315] EISA: Probing bus 0 at eisa.0
May  3 15:14:44 big-room-ubuntu kernel: [   22.065336] Cannot allocate resource for EISA slot 4
May  3 15:14:44 big-room-ubuntu kernel: [   22.065338] Cannot allocate resource for EISA slot 5
May  3 15:14:44 big-room-ubuntu kernel: [   22.065350] EISA: Detected 0 cards.
May  3 15:14:44 big-room-ubuntu kernel: [   22.095426] TCP cubic registered
May  3 15:14:44 big-room-ubuntu kernel: [   22.095434] NET: Registered protocol family 1
May  3 15:14:44 big-room-ubuntu kernel: [   22.095462] Using IPI No-Shortcut mode
May  3 15:14:44 big-room-ubuntu kernel: [   22.095577] ACPI: (supports S0 S1 S4 S5)
May  3 15:14:44 big-room-ubuntu kernel: [   22.095626]   Magic number: 7:974:233
May  3 15:14:44 big-room-ubuntu kernel: [   22.095683]   hash matches device ttyv3
May  3 15:14:44 big-room-ubuntu kernel: [   22.096273] Freeing unused kernel memory: 328k freed
May  3 15:14:44 big-room-ubuntu kernel: [   22.097554] Time: tsc clocksource has been installed.
May  3 15:14:44 big-room-ubuntu kernel: [   22.111443] input: AT Translated Set 2 keyboard as /class/input/input1
May  3 15:14:44 big-room-ubuntu kernel: [   23.327758] Capability LSM initialized
May  3 15:14:44 big-room-ubuntu kernel: [   23.365101] ACPI: Fan [FAN] (on)
May  3 15:14:44 big-room-ubuntu kernel: [   23.369369] ACPI: CPU0 (power states: C1[C1] C2[C2])
May  3 15:14:44 big-room-ubuntu kernel: [   23.370690] ACPI: Thermal Zone [THRM] (40 C)
May  3 15:14:44 big-room-ubuntu kernel: [   23.882857] Linux Tulip driver version 1.1.14 (December 15, 2004)
May  3 15:14:44 big-room-ubuntu kernel: [   23.882913] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 16
May  3 15:14:44 big-room-ubuntu kernel: [   23.919828] eth0: Lite-On PNIC-II rev 37 at Port 0x9400, 00:A0:CC:37:7F:CC, IRQ 16.
May  3 15:14:44 big-room-ubuntu kernel: [   23.924743] SCSI subsystem initialized
May  3 15:14:44 big-room-ubuntu kernel: [   23.929614] libata version 2.20 loaded.
May  3 15:14:44 big-room-ubuntu kernel: [   23.930899] sata_via 0000:00:0f.0: version 2.1
May  3 15:14:44 big-room-ubuntu kernel: [   23.931298] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
May  3 15:14:44 big-room-ubuntu kernel: [   23.931301] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
May  3 15:14:44 big-room-ubuntu kernel: [   23.931311] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
May  3 15:14:44 big-room-ubuntu kernel: [   23.931332] sata_via 0000:00:0f.0: routed to hard irq line 11
May  3 15:14:44 big-room-ubuntu kernel: [   23.931406] ata1: SATA max UDMA/133 cmd 0x00019800 ctl 0x00019c02 bmdma 0x0001a800 irq 17
May  3 15:14:44 big-room-ubuntu kernel: [   23.931443] ata2: SATA max UDMA/133 cmd 0x0001a000 ctl 0x0001a402 bmdma 0x0001a808 irq 17
May  3 15:14:44 big-room-ubuntu kernel: [   23.931460] scsi0 : sata_via
May  3 15:14:44 big-room-ubuntu kernel: [   23.947224] usbcore: registered new interface driver usbfs
May  3 15:14:44 big-room-ubuntu kernel: [   23.947252] usbcore: registered new interface driver hub
May  3 15:14:44 big-room-ubuntu kernel: [   23.947280] usbcore: registered new device driver usb
May  3 15:14:44 big-room-ubuntu kernel: [   23.993251] USB Universal Host Controller Interface driver v3.0
May  3 15:14:44 big-room-ubuntu kernel: [   24.002677] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
May  3 15:14:44 big-room-ubuntu kernel: [   24.099796] Floppy drive(s): fd0 is 1.44M
May  3 15:14:44 big-room-ubuntu kernel: [   24.131518] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  3 15:14:44 big-room-ubuntu kernel: [   24.136144] FDC 0 is a post-1991 82077
May  3 15:14:44 big-room-ubuntu kernel: [    3.696000] Time: acpi_pm clocksource has been installed.
May  3 15:14:44 big-room-ubuntu kernel: [    3.800000] ATA: abnormal status 0x7F on port 0x00019807
May  3 15:14:44 big-room-ubuntu kernel: [    3.816000] ATA: abnormal status 0x7F on port 0x00019807
May  3 15:14:44 big-room-ubuntu kernel: [    3.864000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
May  3 15:14:44 big-room-ubuntu kernel: [    3.864000] ata1.00: ATA-7: ST3500630AS, 3.AAE, max UDMA/133
May  3 15:14:44 big-room-ubuntu kernel: [    3.864000] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  3 15:14:44 big-room-ubuntu kernel: [    3.932000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
May  3 15:14:44 big-room-ubuntu kernel: [    3.932000] ata1.00: configured for UDMA/133
May  3 15:14:44 big-room-ubuntu kernel: [    3.932000] scsi1 : sata_via
May  3 15:14:44 big-room-ubuntu kernel: [    4.136000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  3 15:14:44 big-room-ubuntu kernel: [    4.296000] ATA: abnormal status 0x7F on port 0x0001a007
May  3 15:14:44 big-room-ubuntu kernel: [    4.312000] ATA: abnormal status 0x7F on port 0x0001a007
May  3 15:14:44 big-room-ubuntu kernel: [    4.360000] ata2.00: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
May  3 15:14:44 big-room-ubuntu kernel: [    4.360000] ata2.00: ATA-7: ST3750640AS, 3.AAJ, max UDMA/133
May  3 15:14:44 big-room-ubuntu kernel: [    4.360000] ata2.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  3 15:14:44 big-room-ubuntu kernel: [    4.428000] ata2.00: ata_hpa_resize 1: sectors = 1465149168, hpa_sectors = 1465149168
May  3 15:14:44 big-room-ubuntu kernel: [    4.428000] ata2.00: configured for UDMA/133
May  3 15:14:44 big-room-ubuntu kernel: [    4.428000] scsi 0:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
May  3 15:14:44 big-room-ubuntu kernel: [    4.428000] scsi 1:0:0:0: Direct-Access     ATA      ST3750640AS      3.AA PQ: 0 ANSI: 5
May  3 15:14:44 big-room-ubuntu kernel: [    4.432000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
May  3 15:14:44 big-room-ubuntu kernel: [    4.432000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
May  3 15:14:44 big-room-ubuntu kernel: [    4.432000] VP_IDE: chipset revision 6
May  3 15:14:44 big-room-ubuntu kernel: [    4.432000] VP_IDE: not 100%% native mode: will probe irqs later
May  3 15:14:44 big-room-ubuntu kernel: [    4.432000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
May  3 15:14:44 big-room-ubuntu kernel: [    4.432000]     ide0: BM-DMA at 0xb000-0xb007, BIOS settings: hda:DMA, hdb:DMA
May  3 15:14:44 big-room-ubuntu kernel: [    4.432000]     ide1: BM-DMA at 0xb008-0xb00f, BIOS settings: hdc:DMA, hdd:pio
May  3 15:14:44 big-room-ubuntu kernel: [    4.432000] Probing IDE interface ide0...
May  3 15:14:44 big-room-ubuntu kernel: [    4.452000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
May  3 15:14:44 big-room-ubuntu kernel: [    4.452000] sda: Write Protect is off
May  3 15:14:44 big-room-ubuntu kernel: [    4.452000] sda: Mode Sense: 00 3a 00 00
May  3 15:14:44 big-room-ubuntu kernel: [    4.452000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  3 15:14:44 big-room-ubuntu kernel: [    4.452000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
May  3 15:14:44 big-room-ubuntu kernel: [    4.452000] sda: Write Protect is off
May  3 15:14:44 big-room-ubuntu kernel: [    4.452000] sda: Mode Sense: 00 3a 00 00
May  3 15:14:44 big-room-ubuntu kernel: [    4.452000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  3 15:14:44 big-room-ubuntu kernel: [    4.452000]  sda: [LDM] sda1
May  3 15:14:44 big-room-ubuntu kernel: [    4.524000] sd 0:0:0:0: Attached scsi disk sda
May  3 15:14:44 big-room-ubuntu kernel: [    4.524000] SCSI device sdb: 1465149168 512-byte hdwr sectors (750156 MB)
May  3 15:14:44 big-room-ubuntu kernel: [    4.524000] sdb: Write Protect is off
May  3 15:14:44 big-room-ubuntu kernel: [    4.524000] sdb: Mode Sense: 00 3a 00 00
May  3 15:14:44 big-room-ubuntu kernel: [    4.524000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  3 15:14:44 big-room-ubuntu kernel: [    4.524000] SCSI device sdb: 1465149168 512-byte hdwr sectors (750156 MB)
May  3 15:14:44 big-room-ubuntu kernel: [    4.524000] sdb: Write Protect is off
May  3 15:14:44 big-room-ubuntu kernel: [    4.524000] sdb: Mode Sense: 00 3a 00 00
May  3 15:14:44 big-room-ubuntu kernel: [    4.524000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  3 15:14:44 big-room-ubuntu kernel: [    4.524000]  sdb: [LDM] sdb1
May  3 15:14:44 big-room-ubuntu kernel: [    4.632000] sd 1:0:0:0: Attached scsi disk sdb
May  3 15:14:44 big-room-ubuntu kernel: [    4.636000] sd 0:0:0:0: Attached scsi generic sg0 type 0
May  3 15:14:44 big-room-ubuntu kernel: [    4.640000] sd 1:0:0:0: Attached scsi generic sg1 type 0
May  3 15:14:44 big-room-ubuntu kernel: [    4.856000] hda: HDS722525VLAT80, ATA DISK drive
May  3 15:14:44 big-room-ubuntu kernel: [    5.152000] hdb: WDC WD1000BB-00CAA0, ATA DISK drive
May  3 15:14:44 big-room-ubuntu kernel: [    5.212000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
May  3 15:14:44 big-room-ubuntu kernel: [    5.236000] Probing IDE interface ide1...
May  3 15:14:44 big-room-ubuntu kernel: [    6.156000] hdc: DVD RW DRU-820A, ATAPI CD/DVD-ROM drive
May  3 15:14:44 big-room-ubuntu kernel: [    6.516000] ide1 at 0x170-0x177,0x376 on irq 15
May  3 15:14:44 big-room-ubuntu kernel: [    6.524000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
May  3 15:14:44 big-room-ubuntu kernel: [    6.524000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
May  3 15:14:44 big-room-ubuntu kernel: [    6.524000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
May  3 15:14:44 big-room-ubuntu kernel: [    6.524000] uhci_hcd 0000:00:10.0: UHCI Host Controller
May  3 15:14:44 big-room-ubuntu kernel: [    6.524000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
May  3 15:14:44 big-room-ubuntu kernel: [    6.524000] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000b400
May  3 15:14:44 big-room-ubuntu kernel: [    6.524000] usb usb1: configuration #1 chosen from 1 choice
May  3 15:14:44 big-room-ubuntu kernel: [    6.524000] hub 1-0:1.0: USB hub found
May  3 15:14:44 big-room-ubuntu kernel: [    6.524000] hub 1-0:1.0: 2 ports detected
May  3 15:14:44 big-room-ubuntu kernel: [    6.532000] hda: max request size: 512KiB
May  3 15:14:44 big-room-ubuntu kernel: [    6.548000] hda: 488397168 sectors (250059 MB) w/7938KiB Cache, CHS=30401/255/63, UDMA(100)
May  3 15:14:44 big-room-ubuntu kernel: [    6.548000] hda: cache flushes supported
May  3 15:14:44 big-room-ubuntu kernel: [    6.548000]  hda: hda1 hda2 hda3 < hda5 >
May  3 15:14:44 big-room-ubuntu kernel: [    6.576000] hdb: max request size: 128KiB
May  3 15:14:44 big-room-ubuntu kernel: [    6.576000] hdb: 195371568 sectors (100030 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
May  3 15:14:44 big-room-ubuntu kernel: [    6.576000] hdb: cache flushes not supported
May  3 15:14:44 big-room-ubuntu kernel: [    6.576000]  hdb: hdb1
May  3 15:14:44 big-room-ubuntu kernel: [    6.596000] hdc: ATAPI 94X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
May  3 15:14:44 big-room-ubuntu kernel: [    6.596000] Uniform CD-ROM driver Revision: 3.20
May  3 15:14:44 big-room-ubuntu kernel: [    6.628000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
May  3 15:14:44 big-room-ubuntu kernel: [    6.628000] uhci_hcd 0000:00:10.1: UHCI Host Controller
May  3 15:14:44 big-room-ubuntu kernel: [    6.628000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
May  3 15:14:44 big-room-ubuntu kernel: [    6.628000] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000b800
May  3 15:14:44 big-room-ubuntu kernel: [    6.628000] usb usb2: configuration #1 chosen from 1 choice
May  3 15:14:44 big-room-ubuntu kernel: [    6.628000] hub 2-0:1.0: USB hub found
May  3 15:14:44 big-room-ubuntu kernel: [    6.628000] hub 2-0:1.0: 2 ports detected
May  3 15:14:44 big-room-ubuntu kernel: [    6.732000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
May  3 15:14:44 big-room-ubuntu kernel: [    6.732000] uhci_hcd 0000:00:10.2: UHCI Host Controller
May  3 15:14:44 big-room-ubuntu kernel: [    6.732000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
May  3 15:14:44 big-room-ubuntu kernel: [    6.732000] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000bc00
May  3 15:14:44 big-room-ubuntu kernel: [    6.732000] usb usb3: configuration #1 chosen from 1 choice
May  3 15:14:44 big-room-ubuntu kernel: [    6.732000] hub 3-0:1.0: USB hub found
May  3 15:14:44 big-room-ubuntu kernel: [    6.732000] hub 3-0:1.0: 2 ports detected
May  3 15:14:44 big-room-ubuntu kernel: [    6.836000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
May  3 15:14:44 big-room-ubuntu kernel: [    6.836000] uhci_hcd 0000:00:10.3: UHCI Host Controller
May  3 15:14:44 big-room-ubuntu kernel: [    6.836000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
May  3 15:14:44 big-room-ubuntu kernel: [    6.836000] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000c000
May  3 15:14:44 big-room-ubuntu kernel: [    6.836000] usb usb4: configuration #1 chosen from 1 choice
May  3 15:14:44 big-room-ubuntu kernel: [    6.836000] hub 4-0:1.0: USB hub found
May  3 15:14:44 big-room-ubuntu kernel: [    6.836000] hub 4-0:1.0: 2 ports detected
May  3 15:14:44 big-room-ubuntu kernel: [    6.940000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
May  3 15:14:44 big-room-ubuntu kernel: [    6.940000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
May  3 15:14:44 big-room-ubuntu kernel: [    6.940000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19
May  3 15:14:44 big-room-ubuntu kernel: [    6.944000] eth1: VIA Rhine II at 0x1cc00, 00:0d:87:9d:7a:be, IRQ 19.
May  3 15:14:44 big-room-ubuntu kernel: [    6.944000] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
May  3 15:14:44 big-room-ubuntu kernel: [    6.944000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
May  3 15:14:44 big-room-ubuntu kernel: [    6.944000] ehci_hcd 0000:00:10.4: EHCI Host Controller
May  3 15:14:44 big-room-ubuntu kernel: [    6.944000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
May  3 15:14:44 big-room-ubuntu kernel: [    6.944000] ehci_hcd 0000:00:10.4: irq 18, io mem 0xe9021000
May  3 15:14:44 big-room-ubuntu kernel: [    6.944000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  3 15:14:44 big-room-ubuntu kernel: [    6.944000] usb usb5: configuration #1 chosen from 1 choice
May  3 15:14:44 big-room-ubuntu kernel: [    6.944000] hub 5-0:1.0: USB hub found
May  3 15:14:44 big-room-ubuntu kernel: [    6.944000] hub 5-0:1.0: 8 ports detected
May  3 15:14:44 big-room-ubuntu kernel: [    6.996000] Attempting manual resume
May  3 15:14:44 big-room-ubuntu kernel: [    6.996000] swsusp: Resume From Partition 3:5
May  3 15:14:44 big-room-ubuntu kernel: [    6.996000] PM: Checking swsusp image.
May  3 15:14:44 big-room-ubuntu kernel: [    7.000000] PM: Resume from disk failed.
May  3 15:14:44 big-room-ubuntu kernel: [    7.016000] EXT3-fs: INFO: recovery required on readonly filesystem.
May  3 15:14:44 big-room-ubuntu kernel: [    7.016000] EXT3-fs: write access will be enabled during recovery.
May  3 15:14:44 big-room-ubuntu kernel: [    8.160000] usb 1-2: new low speed USB device using uhci_hcd and address 3
May  3 15:14:44 big-room-ubuntu kernel: [    8.340000] usb 1-2: configuration #1 chosen from 1 choice

---

### Post by r2d22 on 2007-05-03
continues:

May  3 15:14:44 big-room-ubuntu kernel: [    8.360000] usbcore: registered new interface driver hiddev
May  3 15:14:44 big-room-ubuntu kernel: [    8.376000] input: Microsoft Microsoft IntelliMouse® Optical as /class/input/input2
May  3 15:14:44 big-room-ubuntu kernel: [    8.380000] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse® Optical] on usb-0000:00:10.0-2
May  3 15:14:44 big-room-ubuntu kernel: [    8.380000] usbcore: registered new interface driver usbhid
May  3 15:14:44 big-room-ubuntu kernel: [    8.380000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
May  3 15:14:44 big-room-ubuntu kernel: [   11.108000] kjournald starting.  Commit interval 5 seconds
May  3 15:14:44 big-room-ubuntu kernel: [   11.108000] EXT3-fs: recovery complete.
May  3 15:14:44 big-room-ubuntu kernel: [   11.108000] EXT3-fs: mounted filesystem with ordered data mode.
May  3 15:14:44 big-room-ubuntu kernel: [   18.880000] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
May  3 15:14:44 big-room-ubuntu kernel: [   20.000000] NET: Registered protocol family 17
May  3 15:14:44 big-room-ubuntu kernel: [   20.912000] Linux agpgart interface v0.102 (c) Dave Jones
May  3 15:14:44 big-room-ubuntu kernel: [   20.920000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  3 15:14:44 big-room-ubuntu kernel: [   20.920000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  3 15:14:44 big-room-ubuntu kernel: [   21.108000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
May  3 15:14:44 big-room-ubuntu kernel: [   21.116000] agpgart: AGP aperture is 128M @ 0xd0000000
May  3 15:14:44 big-room-ubuntu kernel: [   21.624000] input: PC Speaker as /class/input/input3
May  3 15:14:44 big-room-ubuntu kernel: [   22.044000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
May  3 15:14:44 big-room-ubuntu kernel: [   22.044000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
May  3 15:14:44 big-room-ubuntu kernel: [   22.044000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
May  3 15:14:44 big-room-ubuntu kernel: [   22.044000] PCI: Setting latency timer of device 0000:00:11.5 to 64
May  3 15:14:44 big-room-ubuntu kernel: [   22.052000] parport: PnPBIOS parport detected.
May  3 15:14:44 big-room-ubuntu kernel: [   22.052000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
May  3 15:14:44 big-room-ubuntu kernel: [   22.760000] lp0: using parport0 (interrupt-driven).
May  3 15:14:44 big-room-ubuntu kernel: [   22.796000] Adding 2273156k swap on /dev/disk/by-uuid/926c5865-8650-4687-8a15-1592c0596598.  Priority:-1 extents:1 across:2273156k
May  3 15:14:44 big-room-ubuntu kernel: [   22.900000] EXT3 FS on hda2, internal journal
May  3 15:14:44 big-room-ubuntu kernel: [   23.036000] NET: Registered protocol family 10
May  3 15:14:44 big-room-ubuntu kernel: [   23.036000] lo: Disabled Privacy Extensions
May  3 15:14:44 big-room-ubuntu kernel: [   23.116000] NTFS driver 2.1.28 [Flags: R/O MODULE].
May  3 15:14:44 big-room-ubuntu kernel: [   23.164000] NTFS volume version 3.1.
May  3 15:14:44 big-room-ubuntu kernel: [   23.200000] NTFS volume version 3.1.
May  3 15:14:44 big-room-ubuntu kernel: [   23.244000] NTFS volume version 3.1.
May  3 15:14:44 big-room-ubuntu kernel: [   23.288000] NTFS volume version 3.1.
May  3 15:14:44 big-room-ubuntu kernel: [   27.548000] input: Power Button (FF) as /class/input/input4
May  3 15:14:44 big-room-ubuntu kernel: [   27.556000] ACPI: Power Button (FF) [PWRF]
May  3 15:14:44 big-room-ubuntu kernel: [   27.592000] input: Power Button (CM) as /class/input/input5
May  3 15:14:44 big-room-ubuntu kernel: [   27.596000] ACPI: Power Button (CM) [PWRB]
May  3 15:14:44 big-room-ubuntu kernel: [   27.632000] input: Sleep Button (CM) as /class/input/input6
May  3 15:14:44 big-room-ubuntu kernel: [   27.640000] ACPI: Sleep Button (CM) [SLPB]
May  3 15:14:44 big-room-ubuntu kernel: [   27.664000] Using specific hotkey driver
May  3 15:14:44 big-room-ubuntu kernel: [   27.704000] No dock devices found.
May  3 15:14:44 big-room-ubuntu kernel: [   27.752000] ibm_acpi: ec object not found
May  3 15:14:44 big-room-ubuntu kernel: [   27.880000] pcc_acpi: loading...
May  3 15:14:45 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  3 15:14:48 big-room-ubuntu dhcdbd: Started up.
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^Istarting... 
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'via-rhine'. 
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Found user 'avahi' (UID 104) and group 'avahi' (GID 108).
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Successfully dropped root privileges.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: avahi-daemon 0.6.17 starting up.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Successfully called chroot().
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Successfully dropped remaining capabilities.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: No service found in /etc/avahi/services.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.15.113.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: New relevant interface eth1.IPv4 for mDNS.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Network interface enumeration completed.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Registering new address record for fe80::20d:87ff:fe9d:7abe on eth1.*.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Registering new address record for 192.168.15.113 on eth1.IPv4.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Registering new address record for fe80::2a0:ccff:fe37:7fcc on eth0.*.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Registering HINFO record with values 'I686'/'LINUX'.
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth1'. 
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^IDeactivating device eth1. 
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Withdrawing address record for 192.168.15.113 on eth1.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.15.113.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Interface eth1.IPv4 no longer relevant for mDNS.
May  3 15:14:48 big-room-ubuntu avahi-daemon[4871]: Withdrawing address record for fe80::20d:87ff:fe9d:7abe on eth1.
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'tulip'. 
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
May  3 15:14:48 big-room-ubuntu NetworkManager: <information>^IDeactivating device eth0. 
May  3 15:14:49 big-room-ubuntu avahi-daemon[4871]: Withdrawing address record for fe80::2a0:ccff:fe37:7fcc on eth0.
May  3 15:14:49 big-room-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
May  3 15:14:49 big-room-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IWill activate wired connection 'eth1' because it now has a link. 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth1'. 
May  3 15:14:49 big-room-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IWill activate connection 'eth1'. 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IDevice eth1 activation scheduled... 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) started... 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) successful. 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
May  3 15:14:49 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) started... 
May  3 15:14:49 big-room-ubuntu kernel: [   33.228000] [drm] Initialized drm 1.1.0 20060810
May  3 15:14:49 big-room-ubuntu kernel: [   33.236000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 21
May  3 15:14:49 big-room-ubuntu kernel: [   33.240000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
May  3 15:14:50 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May  3 15:14:50 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Beginning DHCP transaction. 
May  3 15:14:50 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
May  3 15:14:50 big-room-ubuntu NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth1 
May  3 15:14:50 big-room-ubuntu kernel: [   34.020000] ppdev: user-space parallel port driver
May  3 15:14:50 big-room-ubuntu hpiod: 1.7.3 accepting connections at 2208... 
May  3 15:14:51 big-room-ubuntu kernel: [   34.896000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May  3 15:14:51 big-room-ubuntu kernel: [   34.896000] apm: overridden by ACPI.
May  3 15:14:51 big-room-ubuntu NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth1 
May  3 15:14:52 big-room-ubuntu dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
May  3 15:14:52 big-room-ubuntu dhclient: DHCPACK from 192.168.15.1
May  3 15:14:52 big-room-ubuntu avahi-daemon[4871]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.15.113.
May  3 15:14:52 big-room-ubuntu avahi-daemon[4871]: New relevant interface eth1.IPv4 for mDNS.
May  3 15:14:52 big-room-ubuntu avahi-daemon[4871]: Registering new address record for 192.168.15.113 on eth1.IPv4.
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth1 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) started... 
May  3 15:14:52 big-room-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
May  3 15:14:52 big-room-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
May  3 15:14:52 big-room-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^I  address 192.168.15.113 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^I  netmask 255.255.255.0 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^I  broadcast 192.168.15.255 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^I  gateway 192.168.15.1 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^I  nameserver 4.2.2.2 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^I  nameserver 4.2.2.3 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^I  domain name 'gateway.2wire.net' 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
May  3 15:14:52 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
May  3 15:14:52 big-room-ubuntu avahi-daemon[4871]: Withdrawing address record for 192.168.15.113 on eth1.
May  3 15:14:52 big-room-ubuntu avahi-daemon[4871]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.15.113.
May  3 15:14:52 big-room-ubuntu avahi-daemon[4871]: Interface eth1.IPv4 no longer relevant for mDNS.
May  3 15:14:52 big-room-ubuntu avahi-daemon[4871]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.15.113.
May  3 15:14:52 big-room-ubuntu avahi-daemon[4871]: New relevant interface eth1.IPv4 for mDNS.
May  3 15:14:52 big-room-ubuntu avahi-daemon[4871]: Registering new address record for 192.168.15.113 on eth1.IPv4.
May  3 15:14:52 big-room-ubuntu dhclient: bound to 192.168.15.113 -- renewal in 35202 seconds.
May  3 15:14:52 big-room-ubuntu kernel: [   35.908000] [drm] Setting GART location based on new memory map
May  3 15:14:52 big-room-ubuntu kernel: [   35.908000] [drm] Loading R200 Microcode
May  3 15:14:52 big-room-ubuntu kernel: [   35.908000] [drm] writeback test succeeded in 2 usecs
May  3 15:14:52 big-room-ubuntu hcid[5200]: Bluetooth HCI daemon
May  3 15:14:52 big-room-ubuntu NetworkManager: <debug info>^I[1178230492.771293] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May  3 15:14:52 big-room-ubuntu kernel: [   36.416000] Bluetooth: Core ver 2.11
May  3 15:14:52 big-room-ubuntu kernel: [   36.416000] NET: Registered protocol family 31
May  3 15:14:52 big-room-ubuntu kernel: [   36.416000] Bluetooth: HCI device and connection manager initialized
May  3 15:14:52 big-room-ubuntu kernel: [   36.416000] Bluetooth: HCI socket layer initialized
May  3 15:14:52 big-room-ubuntu hcid[5200]: Starting SDP server
May  3 15:14:52 big-room-ubuntu kernel: [   36.468000] Bluetooth: L2CAP ver 2.8
May  3 15:14:52 big-room-ubuntu kernel: [   36.468000] Bluetooth: L2CAP socket layer initialized
May  3 15:14:52 big-room-ubuntu kernel: [   36.588000] Bluetooth: RFCOMM socket layer initialized
May  3 15:14:52 big-room-ubuntu kernel: [   36.588000] Bluetooth: RFCOMM TTY layer initialized
May  3 15:14:52 big-room-ubuntu kernel: [   36.588000] Bluetooth: RFCOMM ver 1.8
May  3 15:14:52 big-room-ubuntu anacron[5239]: Anacron 2.3 started on 2007-05-03
May  3 15:14:53 big-room-ubuntu anacron[5239]: Normal exit (0 jobs run)
May  3 15:14:53 big-room-ubuntu /usr/sbin/cron[5266]: (CRON) INFO (pidfile fd = 3)
May  3 15:14:53 big-room-ubuntu /usr/sbin/cron[5267]: (CRON) STARTUP (fork ok)
May  3 15:14:53 big-room-ubuntu /usr/sbin/cron[5267]: (CRON) INFO (Running @reboot jobs)
May  3 15:14:53 big-room-ubuntu NetworkManager: <information>^IClearing nscd hosts cache. 
May  3 15:14:53 big-room-ubuntu NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May  3 15:14:53 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) successful, device activated. 
May  3 15:14:53 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Finish handler scheduled. 
May  3 15:14:53 big-room-ubuntu NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
May  3 15:14:53 big-room-ubuntu ntpdate[5335]: step time server 82.211.81.145 offset -1.173823 sec
May  3 15:14:53 big-room-ubuntu avahi-daemon[4871]: Registering new address record for fe80::20d:87ff:fe9d:7abe on eth1.*.
May  3 15:15:02 big-room-ubuntu gconfd (ra-5515): starting (version 2.18.0.1), pid 5515 user 'ra'
May  3 15:15:02 big-room-ubuntu gconfd (ra-5515): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  3 15:15:02 big-room-ubuntu gconfd (ra-5515): Resolved address "xml:readwrite:/home/ra/.gconf" to a writable configuration source at position 1
May  3 15:15:02 big-room-ubuntu gconfd (ra-5515): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  3 15:15:02 big-room-ubuntu gconfd (ra-5515): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May  3 15:15:02 big-room-ubuntu gconfd (ra-5515): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May  3 15:15:02 big-room-ubuntu kernel: [   47.388000] eth1: no IPv6 routers present
May  3 15:15:03 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  3 15:15:05 big-room-ubuntu gconfd (ra-5515): Resolved address "xml:readwrite:/home/ra/.gconf" to a writable configuration source at position 0
May  3 15:15:10 big-room-ubuntu dhclient: No DHCPOFFERS received.
May  3 15:15:10 big-room-ubuntu dhclient: No working leases in persistent database - sleeping.
May  3 15:15:10 big-room-ubuntu avahi-autoipd(eth0)[5623]: Found user 'avahi-autoipd' (UID 109) and group 'avahi-autoipd' (GID 115).
May  3 15:15:10 big-room-ubuntu avahi-autoipd(eth0)[5623]: Successfully called chroot().
May  3 15:15:10 big-room-ubuntu avahi-autoipd(eth0)[5623]: Successfully dropped root privileges.
May  3 15:15:10 big-room-ubuntu avahi-autoipd(eth0)[5623]: fopen() failed: Permission denied
May  3 15:15:10 big-room-ubuntu avahi-autoipd(eth0)[5623]: Starting with address 169.254.8.214
May  3 15:15:12 big-room-ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
May  3 15:15:12 big-room-ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May  3 15:15:14 big-room-ubuntu avahi-autoipd(eth0)[5623]: Callout BIND, address 169.254.8.214 on interface eth0
May  3 15:15:14 big-room-ubuntu avahi-daemon[4871]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.214.
May  3 15:15:14 big-room-ubuntu avahi-daemon[4871]: New relevant interface eth0.IPv4 for mDNS.
May  3 15:15:14 big-room-ubuntu avahi-daemon[4871]: Registering new address record for 169.254.8.214 on eth0.IPv4.
May  3 15:15:18 big-room-ubuntu avahi-autoipd(eth0)[5623]: Successfully claimed IP address 169.254.8.214
May  3 15:15:18 big-room-ubuntu avahi-autoipd(eth0)[5623]: fopen() failed: Permission denied
May  3 15:15:19 big-room-ubuntu ntpdate[5686]: adjust time server 82.211.81.145 offset 0.001131 sec
May  3 15:15:49 big-room-ubuntu gconfd (root-5731): starting (version 2.18.0.1), pid 5731 user 'root'
May  3 15:15:49 big-room-ubuntu gconfd (root-5731): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  3 15:15:49 big-room-ubuntu gconfd (root-5731): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May  3 15:15:49 big-room-ubuntu gconfd (root-5731): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  3 15:15:49 big-room-ubuntu gconfd (root-5731): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May  3 15:15:49 big-room-ubuntu gconfd (root-5731): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May  3 15:16:19 big-room-ubuntu gconfd (root-5731): SIGHUP received, reloading all databases
May  3 15:16:19 big-room-ubuntu gconfd (root-5731): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  3 15:16:19 big-room-ubuntu gconfd (root-5731): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May  3 15:16:19 big-room-ubuntu gconfd (root-5731): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  3 15:16:19 big-room-ubuntu gconfd (root-5731): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May  3 15:16:19 big-room-ubuntu gconfd (root-5731): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May  3 15:16:19 big-room-ubuntu gconfd (root-5731): GConf server is not in use, shutting down.
May  3 15:16:19 big-room-ubuntu gconfd (root-5731): Exiting
May  3 15:17:01 big-room-ubuntu /USR/SBIN/CRON[5826]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  3 15:18:48 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  3 15:18:52 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  3 15:18:57 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May  3 15:19:09 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  3 15:19:18 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
May  3 15:19:19 big-room-ubuntu dhclient: No DHCPOFFERS received.
May  3 15:19:19 big-room-ubuntu dhclient: No working leases in persistent database - sleeping.
May  3 15:24:39 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  3 15:24:43 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  3 15:24:52 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May  3 15:25:04 big-room-ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  3 15:25:10 big-room-ubuntu dhclient: No DHCPOFFERS received.
May  3 15:25:10 big-room-ubuntu dhclient: No working leases in persistent database - sleeping.

---

### Post by mishranurag on 2007-05-03
I removed nvidia and system is working fine now.

---

### Post by ewz on 2007-05-03
What type of video card do you have?

Ive had this problem with nvidia cards mainly the MX models 
to fix it I edited the  xorg.conf file and added the line 

**Option "NvAGP" "1"**


eg.

##########################################################################
# Graphics device section(s)
##########################################################################

Section "Device"
    Identifier  "NV AGP"
    VendorName  "nvidia"
    Driver   "nvidia"
    BusID       "PCI:1:0:0"
   Option "NvAGP" "1"
EndSection

Ive had this problem with other linux dist- too
it's not just a ubuntu problem

EWZ..:)

---

### Post by r2d22 on 2007-05-04
it's a ATI Radeon 9250...

ran memtest, cycled through it 4 times. it passed every time...

---

### Post by Ric95 on 2007-05-05
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/94739](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/94739) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Try turning off 3d and see if it still locks up. This may be related to a reported conflict with 64 bit 3d and Pownernowd  ( cpu freq controler ).

---

