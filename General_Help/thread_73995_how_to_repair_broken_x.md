---
title: "how to repair broken x ?"
date: 2005-10-10
forum: General Help
---

### Post by soonindallas on 2005-10-10
I was trying to fix the fglrx issue with my ati card.  i ended up deleting (with synaptic) some apparently critical x packages.

how do I reinstall x from the command line after boot ?

---

### Post by invalid on 2005-10-10
You could reinstall using apt:

sudo apt-get --reinstall install xserver-xorg

Cheers,
Cb

---

### Post by az on 2005-10-10
..Or x-window-system-core, if that is not the package you deleted.

dpkg-reconfigure xserver-xorg 

from recovery mode will fix most x configuration problems.

---

### Post by soonindallas on 2005-10-10
that fixed it, thank you.

---

