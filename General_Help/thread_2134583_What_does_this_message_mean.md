---
title: "What does this message mean?"
date: 2013-04-11
forum: General Help
---

### Post by donsy on 2013-04-11
I get the following message conistently upon wakeup from suspend:
```
[ 6947.833247] i2400m_usb 2-1.6:1.0: TX: can't get autopm: -13

```(xubuntu 12.04)

---

### Post by TheFu on 2013-04-11
If memory serves, -13 is permissions.  Are you in the correct group to control the power management stuff?  Also, thanks to plugdev, connecting remotely and logging in locally do not result in the same outcomes.

---

