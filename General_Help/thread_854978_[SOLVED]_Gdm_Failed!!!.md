---
title: "[SOLVED] Gdm Failed!!!"
date: 2008-07-10
forum: General Help
---

### Post by 4t0m1c_w07f on 2008-07-10
Gdm Failed!!!

Help Help Help

---

### Post by iaculallad on 2008-07-10
> **4t0m1c_w07f said:**
> Gdm Failed!!!

Help Help Help

Give us an idea of what happened. Did it start after you updated Ubuntu? Did it start after you edited a configuration? Did it start after an upgrade?

---

### Post by 4t0m1c_w07f on 2008-07-10
> **iaculallad said:**
> Give us an idea of what happened. Did it start after you updated Ubuntu? Did it start after you edited a configuration? Did it start after an upgrade?

I just booted up my machine and it decided that gdm would fail but just the night before it was working fine. And I did no updates.

Well now I got no GDM anymore and I can't download it because I havn't been given an IP.

---

### Post by iaculallad on 2008-07-10
If you're booted on a terminal, try to type:

```
startx
```

EDIT: Or try to check if you're /etc/X11/default-display-manager file content equals:

> /usr/bin/gdm

since you're using GNOME.

---

### Post by 4t0m1c_w07f on 2008-07-10
Ok I'm in

---

