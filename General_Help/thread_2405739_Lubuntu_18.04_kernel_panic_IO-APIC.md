---
title: "Lubuntu 18.04 kernel panic IO-APIC"
date: 2018-11-10
forum: General Help
---

### Post by juseeh on 2018-11-10
Hi guys, first post!

I have a problem with my computer: M2N4-SLI motherboard, AMD 3500+ CPU and a nVIDIA Geforce 7100 GS.

I made a upgrade from Lubuntu 16.04 with kernel 4.4.0-138 with "acpi_enforce_resources=lax" (only way that I find to make fancontrol to work) to 
Lubuntu 18.10 with kernel 4.15.0-38 and when boot show me this:

[I]kernel panic-not sycning: IO-APIC + timer doesn't work. try booting with
apic=debug and send a report. Then try booting with the 'noapic'option

[/I]Only boots with "noapic acpi=off", but this way the monitor resolution is low.

Is this a bug? or my hardware is not supported? Should I send a report or something?

---

