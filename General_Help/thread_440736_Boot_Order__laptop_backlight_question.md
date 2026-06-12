---
title: "Boot Order / laptop backlight question"
date: 2007-05-11
forum: General Help
---

### Post by Penumber on 2007-05-11
I have a quick question about where the scripts can be found for the initial actions performed when Linux boots.
I'm trying to trace an issue with my laptop's backlight turning way way down on boot.
I can watch it go from bright to absolute dark somewhere along the boot sequence, I've narrowed it down to a few lines but I have no idea where the scripts are that run this sort of thing; it's among the first things performed, I know that much.
Anyhow, here are the lines that I suspect (it's an issue with acpi, it goes away if I boot with acpi=off, but that gives me other problems).
This is the very first chunk of lines that dmesg gives.
```

[    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=2b84f281-05d8-4b1b-b1a8-2708d8994418 ro
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[    0.000000]  BIOS-e820: 000000001fef0000 - 000000001fefb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fefb000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 130800) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x00000000000f8360
[    0.000000] ACPI: RSDT (v001 Arima  161Fh    0x06040000  LTP 0x00000000) @ 0x000000001fef6b6e
[    0.000000] ACPI: FADT (v001 Arima  161Fh    0x06040000 PTL_ 0x000f4240) @ 0x000000001fefae66
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000001fefaeda
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x000000001fefafb0
[    0.000000] ACPI: DSDT (v001  Arima 161Fh    0x06040000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24

```

It happens in among one of the ACPI lines. I was hoping to get to the script and tinker until I isolated what the precise cause of this is; but I can't find the script that does all this.

Of course, any other suggestions for solutions are welcome. Googling has failed me.

Thanks in advance.

---

### Post by Penumber on 2007-05-13
Bump, I really need this solved.

---

