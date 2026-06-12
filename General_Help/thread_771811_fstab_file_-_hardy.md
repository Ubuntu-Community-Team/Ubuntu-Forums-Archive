---
title: "fstab file - hardy"
date: 2008-04-27
forum: General Help
---

### Post by owen_cook on 2008-04-27
fstab does not appear to do anything! 

I added this line:

/dev/sdb2       /backup         ext3    none    0       0

and rebooted, but had to manually mount the device.

The 7.04 fstab file does not exhibit this behaviour.

I guess something has changed, but I cannot find references to the change

Any advice or pointers that I should read?

TIA

Owen

---

### Post by cm.squared on 2008-04-28
Try:

/dev/sdb2 /backup ext3 defaults 0 0

---

### Post by owen_cook on 2008-04-28
Thank you, that fixed it. Need my head read


Owen

---

