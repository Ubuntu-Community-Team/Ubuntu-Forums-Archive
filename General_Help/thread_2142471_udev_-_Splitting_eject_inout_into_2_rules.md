---
title: "udev - Splitting eject in/out into 2 rules"
date: 2013-05-05
forum: General Help
---

### Post by Sworddragon on 2013-05-05
I'm having an udev rule which triggers on any eject event and starts a script:

```
KERNEL=="sr*", ENV{DISK_EJECT_REQUEST}!="?*", RUN+="/usr/local/share/python/automount.py -m /media/$kernel /dev/$kernel"
```


Now I want to split this rule into 2 rules - the first shall trigger only on an eject out and the other on an eject in. I'm assuming every of these actions does write another value into DISK_EJECT_REQUEST. But I couldn't find any documentation that describes all the values for this variable.

---

