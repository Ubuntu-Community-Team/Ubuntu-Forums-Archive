---
title: "What are my BIOS bugs and how do I fix them?"
date: 2007-06-28
forum: General Help
---

### Post by Arenlor on 2007-06-28
When I boot I get these BIOS bugs reported
```
[   18.886248] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   19.047369] PCI: BIOS BUG # 81[49435000] found
```
I may have misread my writing and it may be a 1 not a 7 there, I'll check later, and some spacing in the second line may be off, otherwise it's correct. Any ideas?

---

### Post by dcstar on 2007-06-28
> **Arenlor said:**
> When I boot I get these BIOS bugs reported
```
[   18.886248] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   19.047369] PCI: BIOS BUG # 81[49435000] found
```
I may have misread my writing and it may be a 1 not a 7 there, I'll check later, and some spacing in the second line may be off, otherwise it's correct. Any ideas?

Possibly you have a motherboard with dual CPU sockets but only have one CPU installed, or the kernel is just detecting something that it doesn't quite understand.

I have seen similar messages on old server hardware that has Linux installed, you can usually ignore them as there generally isn't much you can do about them.

---

### Post by Arenlor on 2007-06-28
I figured I could ignore it, thanks, I have an Inspiron 1501 so it's not old, I got it in March. I hope I have the dual CPU issue, because that means later I can install a second.

---

### Post by bradmayne on 2007-07-03
the is the partial output of what i found in dmesg.  I have a toshiba satellite a135 s4527 with petium dual core.  It is a phoenix BIOS.  

this is a partial output from the "dmesg" command

 40.968000] apm: BIOS not found.



the following is the complete output of the "dmesg | less"    command|


    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1
.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16
.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 en
d: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 en
d: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 en
d: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f580000 en
d: 000000003f680000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f680000 size: 0000000000080000 en
d: 000000003f700000 type: 4
[    0.000000] copy_e820_map() start: 000000003f700000 size: 0000000000900000 en
d: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 en
d: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 en
:

does anyone have any ideas?

---

### Post by Slammer64 on 2007-07-03
APM is Advanced Power Management and it isn't used on modern machines, especially dual-core, it's safe to ignore that one, unless you feel like recompiling your kernel? :p

---

