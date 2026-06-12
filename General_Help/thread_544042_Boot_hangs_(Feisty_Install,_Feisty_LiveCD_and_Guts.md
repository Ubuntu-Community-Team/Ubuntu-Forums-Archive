---
title: "Boot hangs (Feisty Install, Feisty LiveCD and Gutsy LiveCD)"
date: 2007-09-05
forum: General Help
---

### Post by vthokiestm on 2007-09-05
I had a working installation of Feisty that all of a sudden won't boot! I can't even get into the system to see error messages.

If I edit the grub command to remove quiet splash, I can see that the system freezes at:
PCI: Using ACPI for IRQ routing
ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 20 (level, low) -> IRQ 16

If I add noapic to the grub line it still freezes. The same thing happens with the liveCD.

I was able to get the alternate install disc to work, but after the install was finished, I'm unable to boot the clean installation.

Anyone have any suggestions for what I can try? My system is dead!

---

### Post by vthokiestm on 2007-09-06
Bump....

I've tried Gentoo and Linux Mint. Gentoo works fine, but Linux Mint hangs at the same spot (since it is Ubuntu based). This is a Shuttle XPC SN85G4 V3 with an AMD Sempron.

I'd really like to stick with Ubuntu!

---

