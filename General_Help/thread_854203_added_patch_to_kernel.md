---
title: "added patch to kernel?"
date: 2008-07-09
forum: General Help
---

### Post by raedbenz on 2008-07-09
Hi,,,
after unpacking the Kernel source, and adding a certain the patch(".patch.gz") according to architecture and version by typing, e.g.:
```
zcat ../linux-2.6.24-rc8_ep93xx_mmc.patch.gz|patch -p1
```
how can i see if the patch has been added successfully?
is there a command shows the patches added to Kernel source?
or i have to browse kernel's directories?
thanks

---

### Post by sdennie on 2008-07-09
Just the output from the command you mention above should be sufficient.  If you've cleanly applied the patch, you shouldn't have gotten any errors.

---

