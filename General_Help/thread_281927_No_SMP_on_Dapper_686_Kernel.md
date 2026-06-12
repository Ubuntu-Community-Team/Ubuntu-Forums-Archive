---
title: "No SMP on Dapper 686 Kernel"
date: 2006-10-21
forum: General Help
---

### Post by muken on 2006-10-21
Hello!

I have read many threads about SMP problems, but have not yet found a solution for my problem.

I have a Celeron D in an Asus P5P800-VM motherboard with the lates BIOS version. The kernel does only detect one CPU.

I have fiddled with ACPI and ACPI APIC support in the BIOS (as mentioned in other threads) but without any luck.

Any ideas what to?

Here are some more information:
$ dmesg
[17179569.184000] Linux version 2.6.15-27-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003f7b0000 (usable)
[17179569.184000]  BIOS-e820: 000000003f7b0000 - 000000003f7c0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003f7c0000 - 000000003f7f0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003f7f0000 - 000000003f800000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 119MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 260016
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 30640 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v002 ACPIAM                                ) @ 0x000faf50
[17179569.184000] ACPI: XSDT (v001 A M I  OEMXSDT  0x09000612 MSFT 0x00000097) @ 0x3f7b0100
[17179569.184000] ACPI: FADT (v003 A M I  OEMFACP  0x09000612 MSFT 0x00000097) @ 0x3f7b0290
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x09000612 MSFT 0x00000097) @ 0x3f7b0390
[17179569.184000] ACPI: OEMB (v001 A M I  OEMBIOS  0x09000612 MSFT 0x00000097) @ 0x3f7c0040
[17179569.184000] ACPI: DSDT (v001  A0495 A0495036 0x00000036 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3f800000:c0380000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2800.856 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.560000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.560000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.584000] Memory: 1018776k/1040064k available (2115k kernel code, 20544k reserved, 595k data, 332k init, 122560k highmem)
[17179572.584000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.664000] Calibrating delay using timer specific routine.. 5606.82 BogoMIPS (lpj=11213657)
[17179572.664000] Security Framework v1.0.0 initialized
[17179572.664000] SELinux:  Disabled at boot.
[17179572.664000] Mount-cache hash table entries: 512
[17179572.664000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[17179572.664000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[17179572.664000] monitor/mwait feature present.
[17179572.664000] using mwait in idle threads.
[17179572.664000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179572.664000] CPU: L2 cache: 256K
[17179572.664000] CPU: Hyper-Threading is disabled
[17179572.664000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080 0000651d 00000000 00000001
[17179572.664000] mtrr: v2.0 (20020519)
[17179572.664000] Enabling fast FPU save and restore... done.
[17179572.664000] Enabling unmasked SIMD FPU exception support... done.
[17179572.664000] Checking 'hlt' instruction... OK.
[17179572.680000] SMP alternatives: switching to UP code

... SNIP ...

Regards
// Magnus

---

### Post by deanjm1963 on 2006-10-21
I know this is going to sound crazy, but what kind of mouse are you using? If I plug my 4 year old logitech USB scrollwheel mouse in, I only get one cpu booting, and the same with my brand new microsoft USB mouse... I went to a cheap ps2 mouse and I've had no kernel problems since. I get both cpu's going.

---

### Post by jdunn on 2006-10-21
First, does your processor support hyperthreading?
If it does, then do this:

use your favorite editor to edit /boot/grub/menu.lst
add the "ht=on" parameter so you have a line that looks something like this
kernel       /boot/vmlinuz-2.6.15-27-686 root=/dev/hda1 ro quiet splash ht=on
Save menu.lst and reboot
do 'dmesg | grep CPU' and you should notice that the "Hyper-Threading is disabled" message is gone.  This means your 686 kernel is using SMP.

---

### Post by muken on 2006-10-21
> I know this is going to sound crazy, but what kind of mouse are you using?

You're right, it really sounds crazy ;-)

I have a wireless logithech mouse connected to PS/2.
However I have a SilverStone HTPC case, which have a display and IR reciever attached to USB. I tried to disconnect it, but without any luck...

Regards
// Magnus

---

