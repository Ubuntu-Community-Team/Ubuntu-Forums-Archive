---
title: "Bios bug = no new distros"
date: 2007-08-31
forum: General Help
---

### Post by canadianwriterman on 2007-08-31
Googling "MP-BIOS bug: 8254 timer not connected to IO-APIC" brings up pages of complaints about this bios bug. In most cases, Ubuntu and other distros ignore the bug. Fixes include a bios update or adding "noapic" as a boot parameter, but those solutions only work for a small number of people. For me, the solutions have not worked, but Feisty ignores the bug, so it's no big deal.

However, with newer kernels the bug is a show stopper. I've tried a number of new distros, including alpha Gutsy, and all result in kernel panic. "noapic" does not help. For all practical purposes, that means that people like me must stay with our current versions of GNU/Linux distros until we upgrade our machines (preferably to an Ubuntu pre-install).

I'm interested if anyone else who has this bug has found success with a distro with a kernel newer than Feisty?

---

