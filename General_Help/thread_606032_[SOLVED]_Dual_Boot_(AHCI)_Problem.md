---
title: "[SOLVED] Dual Boot (AHCI) Problem"
date: 2007-11-07
forum: General Help
---

### Post by Tosa on 2007-11-07
I had a problem with installing Kubuntu 7.10 on a P35 motherboard with PATA (boot) + SATA drives. Then I saw a post that said AHCI should be enabled. After fiddling with menu.lst to make Grub find both Windows and Kubuntu everything seemed to work fine...

Except that I've just realized that there were no SATA drives in Windows (XP), only PATA! I thought that probably it was a problem with drivers, but after reinstalling them, again nothing. Well, it's probably that I should disable AHCI, install drivers, enable AHCI, and everything would be fine...

Only, it's not. When I disable AHCI I can't boot at all... I guess that Grub somehow got very confused, but how can I fix it?

---

### Post by fjgaude on 2007-11-07
I've been thinking of giving an Intel P35 motherboard, but have been holding off. Wonder if more folks will post stating their finding?

---

### Post by Tosa on 2008-02-13
This was apparently a kernel problem. After updating to 2.6.22-14 51 couple of days ago, Grub and Kubuntu function normally with AHCI disabled in bios.

---

