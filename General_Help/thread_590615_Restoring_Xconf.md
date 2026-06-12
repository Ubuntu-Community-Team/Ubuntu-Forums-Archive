---
title: "Restoring Xconf"
date: 2007-10-24
forum: General Help
---

### Post by netbotix on 2007-10-24
Is there a possible way to restore the default xoncf or something similar?
I thought I had made a backup (guess i did not) and I tried to edit my mouse settings and then X went crazy.  I have not used the recovery console for anything before so some guidance would be appreciated.  When I start ubuntu normally, it does nothing. BTW running 7.1
Thanks!

---

### Post by taurus on 2007-10-25
Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
```

---

