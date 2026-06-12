---
title: "Disabling integrated graphics to use a PCI graphics controller"
date: 2007-04-28
forum: General Help
---

### Post by RAKninja on 2007-04-28
I have followed the directions on blacklisting my integrated graphics card (intell)  and for installing NVIDIA drivers.

currently, my VGA cord is plugged into the PCI card.  the BIOS is set for integrated control.  if i change BIOS to PCI control, ubuntu page faults, and crashes before offering me a command line interface.

i get some functionality out of the card, but not much.

---

### Post by pseudonym on 2007-04-28
You sure you installed the right driver? If the card is PCI I'm guessing that it might need the 'legacy' 7184 version...

---

