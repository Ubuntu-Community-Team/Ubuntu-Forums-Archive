---
title: "completely remove the Intel driver from 15.04 (and future releases)"
date: 2015-08-02
forum: General Help
---

### Post by eival on 2015-08-02
the driver keeps re-enabling itself from time to time and plus it still lists itself in the additional drivers even though i ran the code to purge the installer and removed the intel-microcode file with synaptic

i want to keep it from even being seen by my system if it cant be removed entirely, which is exactly what happens if you were to install anything prior to 15.04

to reiterate i just want the default vesa driver on my system

---

### Post by deadflowr on 2015-08-02
intel-microcode?
That has nothing to do with graphics cards.
It's cpu related.

---

### Post by eival on 2015-08-02
> **deadflowr said:**
> intel-microcode?
That has nothing to do with graphics cards.
It's cpu related.

well thats what it says on the additional drivers menu intel-microcode

---

### Post by kerry_s on 2015-08-02
intel-microcode is for intel cpu firmware updates via the kernel, so you don't have to update the bios to get the latest fixes.

---

### Post by buzzingrobot on 2015-08-02
> **eival said:**
> well thats what it says on the additional drivers menu intel-microcode

"Additional Drivers" is not confined to video drivers. E.g., if you have a wifi chip with an available proprietary driver, you'll see it there, as well.

---

