---
title: "Periodic Slow Boot"
date: 2016-11-29
forum: General Help
---

### Post by box02-0 on 2016-11-29
Ubuntu 14.04 LTS

Hi.

A normal boot takes about 6 seconds on my system. Periodically, I get a 40 second boot. I can't find a pattern as to why every so many boots causes this extra boot time. A purple blank screen is displayed with no messages while I am waiting the 40 odd seconds.

I tries the 'dmesg' command after a 40 second boot and found where the delay is:

...
...
...
[    0.008794] ACPI: Core revision 20131115
[    0.014899] ACPI: All ACPI Tables successfully acquired
[   37.682149] ftrace: allocating 28664 entries in 112 pages
[   37.690030] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
....
...
...

Then I tried the 'dmesg' command after a regular 6 second boot:
...
...
...
[    0.008784] ACPI: Core revision 20131115
[    0.015048] ACPI: All ACPI Tables successfully acquired
[    0.043489] ftrace: allocating 28664 entries in 112 pages
[    0.051358] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
...
...
...

From the above 2 excerpts, I can't see a reason why there is a delay between lines 2 & 3.


Any ideas?

Thanks,

M...

---

