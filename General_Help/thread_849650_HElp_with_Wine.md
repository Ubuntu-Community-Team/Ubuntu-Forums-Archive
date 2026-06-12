---
title: "HElp with Wine"
date: 2008-07-04
forum: General Help
---

### Post by jugganinja0 on 2008-07-04
ineed to know how to reset wine back to the default settings the hard way because my wine desktop resolution is stuck on 1440x900 so that i cant move the configure window to access the graphics resolution pulldown menu. I have already tried reinstalling wine and that did not help and tried to get to the reg edit thru wine but its so big inside that little window that i cant do anything with it.

---

### Post by Darkade on 2008-07-04
try deleting the folder .wine in your home

```
rm ~/.wine
```

N.B: This WILL delete you wine installed apps. So if you can reinstall them go for it.

---

### Post by lightstream on 2008-07-05
> **Darkade said:**
> try deleting the folder .wine in your home
```
rm ~/.wine
```

.. and then run winecfg to re-create with the defaults ..

actually, this would also delete wine's C drive, so probably not what you want?

---

### Post by Tomatz on 2008-07-05
Try this:
```

sudo apt-get remove --purge wine && sudo apt-get install wine
```

;)

---

