---
title: "Accidentally deleted /lib/modules/`uname -r`/kernel/drivers/net folder"
date: 2007-02-14
forum: General Help
---

### Post by nyinge on 2007-02-14
[SOLVED]
I have accidentally deleted the folder:
/lib/modules/2.6.17-11-generic/kernel/drivers/net/

After reboot, I've lost the eth0(wired) interface.  What do I do now to get back the folder with many net drivers?  Is reinstall the only solution?  Thank you.

---

### Post by nyinge on 2007-02-14
Actually, I figured it out.
```
apt-get install --reinstall linux-image-`uname -r`
``` solved the problem.  :)

---

