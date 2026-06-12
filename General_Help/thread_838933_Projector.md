---
title: "Projector"
date: 2008-06-24
forum: General Help
---

### Post by Dragonlaw on 2008-06-24
How do I get Ubuntu on a projector? When I press Fn+F7 nothing happens on the projection screen.

I'm using a Thinkpad T61 with a Nvidia Quandro NVS 140M

---

### Post by iaculallad on 2008-06-24
When the projector is connected to your Thinkpad, try reconfiguring your xorg file:

Backup first:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

Then do the reconfiguration:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Dragonlaw on 2008-06-24
Thanks. If it doesnt work out then how do I use the backup?

---

### Post by iaculallad on 2008-06-24
> **Dragonlaw said:**
> Thanks. If it doesnt work out then how do I use the backup?

Just reverse it:

```
sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
```

---

