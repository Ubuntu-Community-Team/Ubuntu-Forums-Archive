---
title: "how  set gdm as default"
date: 2008-01-22
forum: General Help
---

### Post by nene on 2008-01-22
hi boys 
how do set gdm as default???


th

---

### Post by LaRoza on 2008-01-22
(Don't exclude girls...)

In the login screen, select Options->Sessions and chose GNOME as the default.

---

### Post by pointone on 2008-01-22
That only makes the GNOME session the default *session*. In order to make GDM the default *display manager*, try running:

```
dpkg-reconfigure gdm
```

It should ask you whether you want GDM to be the default display manager or not.

---

