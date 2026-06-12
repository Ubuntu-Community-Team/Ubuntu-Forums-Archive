---
title: "upgrading driver help"
date: 2008-03-06
forum: General Help
---

### Post by 4dognight on 2008-03-06
I applied a patch to a driver.
I can succesfully use rmmod and modprobe to insert the new driver.

When I reboot, it reverts back to the old driver.
How do I make it permanent?

---

### Post by geraldm on 2008-03-06
Find the directory where the old driver exists, and move it to a hold area.  Then copy the new driver to that kernel directory with the name of the older driver module.

Gerald

---

### Post by 4dognight on 2008-03-06
Thats the odd thing. I copied over the old driver. They dont exist anymore.

---

