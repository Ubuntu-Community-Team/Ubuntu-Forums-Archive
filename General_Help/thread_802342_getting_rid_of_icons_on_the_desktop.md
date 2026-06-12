---
title: "getting rid of icons on the desktop"
date: 2008-05-21
forum: General Help
---

### Post by hampshire_tux on 2008-05-21
everytime i plug my mobile phone into my pc these icons come up but they dont leave after ive unplugged my phone.help on getting rid of them please.
[IMG]http://s1.directupload.net/images/080521/5j875jqu.png[/IMG]

---

### Post by drs305 on 2008-05-21
I don't know if they are considered volumes, but you could try this command:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

Change the value back to true if it doesn't work or you want to see them again.

---

