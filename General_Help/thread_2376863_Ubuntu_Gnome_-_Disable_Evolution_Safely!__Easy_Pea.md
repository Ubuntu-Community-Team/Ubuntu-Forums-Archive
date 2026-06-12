---
title: "Ubuntu Gnome - Disable Evolution Safely!  Easy Peasy"
date: 2017-11-06
forum: General Help
---

### Post by markackerman8@gmail.com on 2017-11-06
Disable Evolution from loading SAFELY!

- One can't un-install it, since other programs (from Gnome) depend on it. But by renaming the folders it is located in, you can prevent it from starting up after reboot:

```
sudo mv /usr/lib/evolution-data-server /usr/lib/evolution-data-server-disabled
```
```
sudo mv /usr/lib/evolution /usr/lib/evolution-disabled
```

After a reboot it is no longer eating up CPU or RAM WooHoo, and it does NOT break Gnome!

Sharing the good news, 

As Always - trying to help, Mark :D
p.s  If your reading this you know that if you try to uninstall it it uninstalls almost all of Gnomes Meta Package with, as it is tightly woven into the AWESOME Gnome 1.2.&3 DE!

---

### Post by JonPaul on 2017-11-08
It will come back if there is an update...;)

---

