---
title: "system seems to be waiting for something"
date: 2020-10-25
forum: General Help
---

### Post by jgw on 2020-10-25
I have been noticing that some programs will take a long time to do something that used to not take any time at all.  I blamed it on the programs.  However, I then did a command that began with 'sudo' in the terminal.  It took somewhere from 12 to 20 seconds to get the password request.  This used to be almost instantaneous.  I think this is an ubuntu problem and I can't figure out what is causing it.  I have turned off any running programs that might get in the way and it made no difference.  I also ran it with stacer showing the cpu, memory and disk usage and they all seemed to be fine and never went up to the 50% at the top of the curve.   I have also done a 'sudo' and entered my password before the request appeared.  My password appeared as I wrote it, remained and was used, after the wait by 'sudo'.

Everything being said this is a mystery to me. 

Thank you..................

---

### Post by dino99 on 2020-10-26
After getting that delay, open a terminal and run 'journalctl -b' to know about error (red line) and warning(s) (yellow lines). You might find something usefull, either an error and/or a race or maybe some apparmor trouble.

---

### Post by jgw on 2020-10-26
Thanks for the reply.  

Its getting stranger.  First I ran the 'sudo' thing  and got the below response.  I ran "journalctl -b' whilst starting up thunderbird (takes a while).  I got the following.  The really strange thing is that I got the same response from both the 'sudo' AND from the 'journalctl -b' whilst Thunderbird was loading.  The really strange thing is that I got it no fewer than 37 times! (each one was separated by something like 23 lines and then the last one which was different)

```

greg@gregdown:~$ journalctl -b
-- Logs begin at Tue 2020-10-20 14:48:59 PDT, end at Mon 2020-10-26 11:49:11 PD>
Oct 26 09:38:37 gregdown kernel: Linux version 5.4.0-52-generic (buildd@lgw01-a>
Oct 26 09:38:37 gregdown kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-5>
Oct 26 09:38:37 gregdown kernel: KERNEL supported cpus:
Oct 26 09:38:37 gregdown kernel:   Intel GenuineIntel
Oct 26 09:38:37 gregdown kernel:   AMD AuthenticAMD
Oct 26 09:38:37 gregdown kernel:   Hygon HygonGenuine
Oct 26 09:38:37 gregdown kernel:   Centaur CentaurHauls
Oct 26 09:38:37 gregdown kernel:   zhaoxin   Shanghai  
Oct 26 09:38:37 gregdown kernel: random: get_random_u32 called from bsp_init_am>
Oct 26 09:38:37 gregdown kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 >
Oct 26 09:38:37 gregdown kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE >
Oct 26 09:38:37 gregdown kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX >
Oct 26 09:38:37 gregdown kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[>
Oct 26 09:38:37 gregdown kernel: x86/fpu: Enabled xstate features 0x7, context >
Oct 26 09:38:37 gregdown kernel: BIOS-provided physical RAM map:
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000>
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x000000000009f000-0x000000000>
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x00000000000e2000-0x000000000>
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000c>
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x00000000cfe80000-0x00000000c>
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x00000000cfe98000-0x00000000c>
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x00000000cfec0000-0x00000000c>
lines 1-23

```

The last group, however was different:

```
-- 
Logs begin at Tue 2020-10-20 14:48:59 PDT, end at Mon 2020-10-26 11:51:01 PDT. --
Oct 26 09:38:37 gregdown kernel: Linux version 5.4.0-52-generic (buildd@lgw01-amd64-060) (gcc version 9.3.0 (Ubuntu 9.3.0-17ubuntu1~20.04)) #57-Ubuntu SMP Thu Oct 15 10:57:00 UTC 2020 (Ubuntu 5.4.0-52.57-gener>
Oct 26 09:38:37 gregdown kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-52-generic root=UUID=99ef22a0-5e2f-45b4-81a3-5b39584e0cef ro quiet splash
Oct 26 09:38:37 gregdown kernel: KERNEL supported cpus:
Oct 26 09:38:37 gregdown kernel:   Intel GenuineIntel
Oct 26 09:38:37 gregdown kernel:   AMD AuthenticAMD
-- Logs begin at Tue 2020-10-20 14:48:59 PDT, end at Mon 2020-10-26 11:51:01 PDT. --
Oct 26 09:38:37 gregdown kernel: Linux version 5.4.0-52-generic (buildd@lgw01-amd64-060) (gcc version 9.3.0 (Ubuntu 9.3.0-17ubuntu1~20.04)) #57-Ubuntu SMP Thu Oct 15 10:57:00 UTC 2020 (Ubuntu 5.4.0-52.57-gener>
Oct 26 09:38:37 gregdown kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-52-generic root=UUID=99ef22a0-5e2f-45b4-81a3-5b39584e0cef ro quiet splash
Oct 26 09:38:37 gregdown kernel: KERNEL supported cpus:
Oct 26 09:38:37 gregdown kernel:   Intel GenuineIntel
Oct 26 09:38:37 gregdown kernel:   AMD AuthenticAMD
Oct 26 09:38:37 gregdown kernel:   Hygon HygonGenuine
Oct 26 09:38:37 gregdown kernel:   Centaur CentaurHauls
Oct 26 09:38:37 gregdown kernel:   zhaoxin   Shanghai  
Oct 26 09:38:37 gregdown kernel: random: get_random_u32 called from bsp_init_amd+0x217/0x2c0 with crng_init=0
Oct 26 09:38:37 gregdown kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
Oct 26 09:38:37 gregdown kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Oct 26 09:38:37 gregdown kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Oct 26 09:38:37 gregdown kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Oct 26 09:38:37 gregdown kernel: x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
Oct 26 09:38:37 gregdown kernel: BIOS-provided physical RAM map:
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x00000000000e2000-0x00000000000fffff] reserved
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000cfe7ffff] usable
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x00000000cfe80000-0x00000000cfe97fff] ACPI data
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x00000000cfe98000-0x00000000cfebffff] ACPI NVS
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x00000000cfec0000-0x00000000cfefffff] reserved
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
Oct 26 09:38:37 gregdown kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021effffff] usable
Oct 26 09:38:37 gregdown kernel: NX (Execute Disable) protection: active
Oct 26 09:38:37 gregdown kernel: SMBIOS 2.5 present.
Oct 26 09:38:37 gregdown kernel: DMI: System manufacturer System Product Name/M5A78L-M PLUS/USB3, BIOS 0502    11/18/2016
Oct 26 09:38:37 gregdown kernel: tsc: Fast TSC calibration using PIT
Oct 26 09:38:37 gregdown kernel: tsc: Detected 3515.637 MHz processor
Oct 26 09:38:37 gregdown kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Oct 26 09:38:37 gregdown kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
Oct 26 09:38:37 gregdown kernel: AGP: No AGP bridge found
Oct 26 09:38:37 gregdown kernel: last_pfn = 0x21f000 max_arch_pfn = 0x400000000
Oct 26 09:38:37 gregdown kernel: MTRR default type: uncachable
Oct 26 09:38:37 gregdown kernel: MTRR fixed ranges enabled:
Oct 26 09:38:37 gregdown kernel:   00000-9FFFF write-back
Oct 26 09:38:37 gregdown kernel:   A0000-EFFFF uncachable
Oct 26 09:38:37 gregdown kernel:   F0000-FFFFF write-protect
Oct 26 09:38:37 gregdown kernel: MTRR variable ranges enabled:
Oct 26 09:38:37 gregdown kernel:   0 base 000000000000 mask FFFF80000000 write-back
Oct 26 09:38:37 gregdown kernel:   1 base 000080000000 mask FFFFC0000000 write-back
Oct 26 09:38:37 gregdown kernel:   2 base 0000C0000000 mask FFFFF0000000 write-back
Oct 26 09:38:37 gregdown kernel:   3 disabled
Oct 26 09:38:37 gregdown kernel:   4 disabled
Oct 26 09:38:37 gregdown kernel:   5 disabled
Oct 26 09:38:37 gregdown kernel:   6 disabled
Oct 26 09:38:37 gregdown kernel:   7 disabled
Oct 26 09:38:37 gregdown kernel: TOM2: 000000022f000000 aka 8944M
Oct 26 09:38:37 gregdown kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
Oct 26 09:38:37 gregdown kernel: e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Oct 26 09:38:37 gregdown kernel: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
Oct 26 09:38:37 gregdown kernel: found SMP MP-table at [mem 0x000ff780-0x000ff78f]
Oct 26 09:38:37 gregdown kernel: check: Scanning 1 areas for low memory corruption
Oct 26 09:38:37 gregdown kernel: Using GB pages for direct mapping
Oct 26 09:38:37 gregdown kernel: RAMDISK: [mem 0x32169000-0x350abfff]
Oct 26 09:38:37 gregdown kernel: ACPI: Early table checksum verification disabled
Oct 26 09:38:37 gregdown kernel: ACPI: RSDP 0x00000000000FB490 000024 (v02 ACPIAM)
lines 36-58
Oct 26 09:38:37 gregdown kernel: MTRR fixed ranges enabled:
Oct 26 09:38:37 gregdown kernel:   00000-9FFFF write-back
Oct 26 09:38:37 gregdown kernel:   A0000-EFFFF uncachable
Oct 26 09:38:37 gregdown kernel:   F0000-FFFFF write-protect
Oct 26 09:38:37 gregdown kernel: MTRR variable ranges enabled:
Oct 26 09:38:37 gregdown kernel:   0 base 000000000000 mask FFFF80000000 write-back
Oct 26 09:38:37 gregdown kernel:   1 base 000080000000 mask FFFFC0000000 write-back
Oct 26 09:38:37 gregdown kernel:   2 base 0000C0000000 mask FFFFF0000000 write-back
Oct 26 09:38:37 gregdown kernel:   3 disabled
Oct 26 09:38:37 gregdown kernel:   4 disabled
Oct 26 09:38:37 gregdown kernel:   5 disabled
Oct 26 09:38:37 gregdown kernel:   6 disabled
Oct 26 09:38:37 gregdown kernel:   7 disabled
Oct 26 09:38:37 gregdown kernel: TOM2: 000000022f000000 aka 8944M
Oct 26 09:38:37 gregdown kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
Oct 26 09:38:37 gregdown kernel: e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Oct 26 09:38:37 gregdown kernel: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
Oct 26 09:38:37 gregdown kernel: found SMP MP-table at [mem 0x000ff780-0x000ff78f]
Oct 26 09:38:37 gregdown kernel: check: Scanning 1 areas for low memory corruption
Oct 26 09:38:37 gregdown kernel: Using GB pages for direct mapping
Oct 26 09:38:37 gregdown kernel: RAMDISK: [mem 0x32169000-0x350abfff]
Oct 26 09:38:37 gregdown kernel: ACPI: Early table checksum verification disabled
Oct 26 09:38:37 gregdown kernel: ACPI: RSDP 0x00000000000FB490 000024 (v02 ACPIAM)
lines 36-58
Oct 26 09:38:37 gregdown kernel: MTRR fixed ranges enabled:
Oct 26 09:38:37 gregdown kernel:   00000-9FFFF write-back
Oct 26 09:38:37 gregdown kernel:   A0000-EFFFF uncachable
Oct 26 09:38:37 gregdown kernel:   F0000-FFFFF write-protect
Oct 26 09:38:37 gregdown kernel: MTRR variable ranges enabled:
Oct 26 09:38:37 gregdown kernel:   0 base 000000000000 mask FFFF80000000 write-back
Oct 26 09:38:37 gregdown kernel:   1 base 000080000000 mask FFFFC0000000 write-back
Oct 26 09:38:37 gregdown kernel:   2 base 0000C0000000 mask FFFFF0000000 write-back
Oct 26 09:38:37 gregdown kernel:   3 disabled
Oct 26 09:38:37 gregdown kernel:   4 disabled
Oct 26 09:38:37 gregdown kernel:   5 disabled
Oct 26 09:38:37 gregdown kernel:   6 disabled
Oct 26 09:38:37 gregdown kernel:   7 disabled
Oct 26 09:38:37 gregdown kernel: TOM2: 000000022f000000 aka 8944M
Oct 26 09:38:37 gregdown kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
Oct 26 09:38:37 gregdown kernel: e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Oct 26 09:38:37 gregdown kernel: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
Oct 26 09:38:37 gregdown kernel: found SMP MP-table at [mem 0x000ff780-0x000ff78f]
Oct 26 09:38:37 gregdown kernel: check: Scanning 1 areas for low memory corruption
Oct 26 09:38:37 gregdown kernel: Using GB pages for direct mapping
Oct 26 09:38:37 gregdown kernel: RAMDISK: [mem 0x32169000-0x350abfff]
Oct 26 09:38:37 gregdown kernel: ACPI: Early table checksum verification disabled
Oct 26 09:38:37 gregdown kernel: ACPI: RSDP 0x00000000000FB490 000024 (v02 ACPIAM)
lines 36-58
Oct 26 09:38:37 gregdown kernel: MTRR fixed ranges enabled:
Oct 26 09:38:37 gregdown kernel:   00000-9FFFF write-back
Oct 26 09:38:37 gregdown kernel:   A0000-EFFFF uncachable
Oct 26 09:38:37 gregdown kernel:   F0000-FFFFF write-protect
Oct 26 09:38:37 gregdown kernel: MTRR variable ranges enabled:
Oct 26 09:38:37 gregdown kernel:   0 base 000000000000 mask FFFF80000000 write-back
Oct 26 09:38:37 gregdown kernel:   1 base 000080000000 mask FFFFC0000000 write-back
Oct 26 09:38:37 gregdown kernel:   2 base 0000C0000000 mask FFFFF0000000 write-back
Oct 26 09:38:37 gregdown kernel:   3 disabled
Oct 26 09:38:37 gregdown kernel:   4 disabled
Oct 26 09:38:37 gregdown kernel:   5 disabled
Oct 26 09:38:37 gregdown kernel:   6 disabled
Oct 26 09:38:37 gregdown kernel:   7 disabled
Oct 26 09:38:37 gregdown kernel: TOM2: 000000022f000000 aka 8944M
Oct 26 09:38:37 gregdown kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
Oct 26 09:38:37 gregdown kernel: e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Oct 26 09:38:37 gregdown kernel: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
Oct 26 09:38:37 gregdown kernel: found SMP MP-table at [mem 0x000ff780-0x000ff78f]
Oct 26 09:38:37 gregdown kernel: check: Scanning 1 areas for low memory corruption
Oct 26 09:38:37 gregdown kernel: Using GB pages for direct mapping
Oct 26 09:38:37 gregdown kernel: RAMDISK: [mem 0x32169000-0x350abfff]
Oct 26 09:38:37 gregdown kernel: ACPI: Early table checksum verification disabled
Oct 26 09:38:37 gregdown kernel: ACPI: RSDP 0x00000000000FB490 000024 (v02 ACPIAM)
lines 36-58
Oct 26 09:38:37 gregdown kernel: MTRR fixed ranges enabled:
Oct 26 09:38:37 gregdown kernel:   00000-9FFFF write-back
Oct 26 09:38:37 gregdown kernel:   A0000-EFFFF uncachable
Oct 26 09:38:37 gregdown kernel:   F0000-FFFFF write-protect
Oct 26 09:38:37 gregdown kernel: MTRR variable ranges enabled:
Oct 26 09:38:37 gregdown kernel:   0 base 000000000000 mask FFFF80000000 write-back
Oct 26 09:38:37 gregdown kernel:   1 base 000080000000 mask FFFFC0000000 write-back
Oct 26 09:38:37 gregdown kernel:   2 base 0000C0000000 mask FFFFF0000000 write-back
Oct 26 09:38:37 gregdown kernel:   3 disabled
Oct 26 09:38:37 gregdown kernel:   4 disabled
Oct 26 09:38:37 gregdown kernel:   5 disabled
Oct 26 09:38:37 gregdown kernel:   6 disabled
Oct 26 09:38:37 gregdown kernel:   7 disabled
Oct 26 09:38:37 gregdown kernel: TOM2: 000000022f000000 aka 8944M
Oct 26 09:38:37 gregdown kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
Oct 26 09:38:37 gregdown kernel: e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Oct 26 09:38:37 gregdown kernel: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
Oct 26 09:38:37 gregdown kernel: found SMP MP-table at [mem 0x000ff780-0x000ff78f]
Oct 26 09:38:37 gregdown kernel: check: Scanning 1 areas for low memory corruption
Oct 26 09:38:37 gregdown kernel: Using GB pages for direct mapping
Oct 26 09:38:37 gregdown kernel: RAMDISK: [mem 0x32169000-0x350abfff]
Oct 26 09:38:37 gregdown kernel: ACPI: Early table checksum verification disabled
Oct 26 09:38:37 gregdown kernel: ACPI: RSDP 0x00000000000FB490 000024 (v02 ACPIAM)
lines 36-58
Oct 26 09:38:37 gregdown kernel: MTRR fixed ranges enabled:
Oct 26 09:38:37 gregdown kernel:   00000-9FFFF write-back
Oct 26 09:38:37 gregdown kernel:   A0000-EFFFF uncachable
Oct 26 09:38:37 gregdown kernel:   F0000-FFFFF write-protect
Oct 26 09:38:37 gregdown kernel: MTRR variable ranges enabled:
Oct 26 09:38:37 gregdown kernel:   0 base 000000000000 mask FFFF80000000 write-back
Oct 26 09:38:37 gregdown kernel:   1 base 000080000000 mask FFFFC0000000 write-back
Oct 26 09:38:37 gregdown kernel:   2 base 0000C0000000 mask FFFFF0000000 write-back
Oct 26 09:38:37 gregdown kernel:   3 disabled
Oct 26 09:38:37 gregdown kernel:   4 disabled
Oct 26 09:38:37 gregdown kernel:   5 disabled
Oct 26 09:38:37 gregdown kernel:   6 disabled
Oct 26 09:38:37 gregdown kernel:   7 disabled
Oct 26 09:38:37 gregdown kernel: TOM2: 000000022f000000 aka 8944M
Oct 26 09:38:37 gregdown kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
Oct 26 09:38:37 gregdown kernel: e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Oct 26 09:38:37 gregdown kernel: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
Oct 26 09:38:37 gregdown kernel: found SMP MP-table at [mem 0x000ff780-0x000ff78f]
Oct 26 09:38:37 gregdown kernel: check: Scanning 1 areas for low memory corruption
Oct 26 09:38:37 gregdown kernel: Using GB pages for direct mapping
Oct 26 09:38:37 gregdown kernel: RAMDISK: [mem 0x32169000-0x350abfff]
Oct 26 09:38:37 gregdown kernel: ACPI: Early table checksum verification disabled
Oct 26 09:38:37 gregdown kernel: ACPI: RSDP 0x00000000000FB490 000024 (v02 ACPIAM)
lines 36-58
Oct 26 09:38:37 gregdown kernel: MTRR fixed ranges enabled:
Oct 26 09:38:37 gregdown kernel:   00000-9FFFF write-back
Oct 26 09:38:37 gregdown kernel:   A0000-EFFFF uncachable
Oct 26 09:38:37 gregdown kernel:   F0000-FFFFF write-protect
Oct 26 09:38:37 gregdown kernel: MTRR variable ranges enabled:
Oct 26 09:38:37 gregdown kernel:   0 base 000000000000 mask FFFF80000000 write-back
Oct 26 09:38:37 gregdown kernel:   1 base 000080000000 mask FFFFC0000000 write-back
Oct 26 09:38:37 gregdown kernel:   2 base 0000C0000000 mask FFFFF0000000 write-back
Oct 26 09:38:37 gregdown kernel:   3 disabled
Oct 26 09:38:37 gregdown kernel:   4 disabled
Oct 26 09:38:37 gregdown kernel:   5 disabled
Oct 26 09:38:37 gregdown kernel:   6 disabled
Oct 26 09:38:37 gregdown kernel:   7 disabled
Oct 26 09:38:37 gregdown kernel: TOM2: 000000022f000000 aka 8944M
Oct 26 09:38:37 gregdown kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
Oct 26 09:38:37 gregdown kernel: e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Oct 26 09:38:37 gregdown kernel: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
Oct 26 09:38:37 gregdown kernel: found SMP MP-table at [mem 0x000ff780-0x000ff78f]
Oct 26 09:38:37 gregdown kernel: check: Scanning 1 areas for low memory corruption
Oct 26 09:38:37 gregdown kernel: Using GB pages for direct mapping
Oct 26 09:38:37 gregdown kernel: RAMDISK: [mem 0x32169000-0x350abfff]
Oct 26 09:38:37 gregdown kernel: ACPI: Early table checksum verification disabled
Oct 26 09:38:37 gregdown kernel: ACPI: RSDP 0x00000000000FB490 000024 (v02 ACPIAM)
lines 36-58

```

Then I did it again.  This time the same thing but with yellow notifications about 18 times:

```

Oct 26 09:38:37 gregdown kernel: ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has valid Length but zero Address: 0x0000000000000000/0x1 (20190816/tbfadt-615)
Oct 26 09:38:37 gregdown kernel: ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 64/32 (20190816/tbfadt-564)

```

This is, if nothing else - bizarre!

---

### Post by jgw on 2020-10-27
The only thing I can see with running journalctl -b is that stuff repeats a lot.  I have now run it for a long time whilst I do stuff and there is a LOT of stuff that just repeats and that may be just dandy (I have no idea)  I do know that there are some yellow things, sometimes but not often and no red errors.  My suspicion is that the system waits are something that just are and I get to live with it until it gets fixed.  That's ok with me but I would re3ally appreciate it if somebody could tell me that's the case.  The wait states occur no matter what is happening.  It just waits for something when doing whatever.

I would mark this as solved if there are no replies within, say, a week.

---

