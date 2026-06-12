---
title: "mounted samba volumes do not show up on desktop"
date: 2008-04-26
forum: General Help
---

### Post by mjbarker1 on 2008-04-26
In Gusty all of my samba shares showed up on the desktop as separate drives automatically when they were mounted at start up. In Hardy they get mounted where my fstab tells them too, but I wish they showed up on my desktop automatically. Does anyone know how to fix this?
Thanks,
Matt

---

### Post by hernaaan on 2009-05-01
If you are using GNOME:

```
$ gconf-editor
```

apps > nautilus > desktop > volumes_visible

Hope that helps.

---

