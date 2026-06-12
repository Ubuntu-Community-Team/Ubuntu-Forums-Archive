---
title: "Lubuntu nautilus??"
date: 2014-04-21
forum: General Help
---

### Post by matt96 on 2014-04-21
hi
i installed lubuntu 14.04 recently and i was trying to open nautilus
by
in terminal--"gksudo nautilus"

it asks for password and i enter it and i think it accepts it but nothing happens

any help??

---

### Post by shadytv on 2014-04-21
Hi, Nautilus is the GNOME file manager, the tool in LXDE is pcmanfm.

try:

```
gksudo pcmanfm
```

hope this helps

---

### Post by vasa1 on 2014-04-21
> **shadytv said:**
> Hi, Nautilus is the GNOME file manager, the tool in LXDE is pcmanfm.
...
+1.

By the way, why do you want to use **gksudo**? There's a danger of wrecking your system because you'll be able to modify/delete files that the system needs.

---

### Post by matt96 on 2014-04-22
i got nautilus to work

i was trying to share my hard drives on lubuntu on my network?
when i open nautilus and right-click on my hard drive and try to share it gives usershare 255 error

anyone know how to do that?

should i start a new thread?

---

