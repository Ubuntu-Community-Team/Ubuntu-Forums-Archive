---
title: "No longer own .dbus after attempted upgrade"
date: 2020-10-07
forum: General Help
---

### Post by klundermann on 2020-10-07
I tried and failed to upgrade from 18.04 to 20.04.1.  Since then, whenever I attempt a backup with Déjà Dup, I get the following error message:

```
Backup Finished

Could not back up the following files. Please make sure you are able to open them.

/home/<my login ID>/.dbus
```


I presume I can change the permissions on .dbus with sudo chmod, but what *should* the permissions be?

---

### Post by Impavidus on 2020-10-08
Your title says you don't own .dbus, in the body you ask about changing permissions with chmod.

Anyway, the owner should be you and permissions are 0700.

---

### Post by spjackson on 2020-10-08
Beaten to it.

---

