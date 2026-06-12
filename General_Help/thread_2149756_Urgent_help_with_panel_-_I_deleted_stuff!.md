---
title: "Urgent help with panel - I deleted stuff!"
date: 2013-05-29
forum: General Help
---

### Post by Juniorr on 2013-05-29
I deleted an icon on the panel (from gnome-panel) and now my buttons on the top-right are gone! Hehehehe
Could somebody help? I can't seem to find this anywhere else.

---

### Post by CatKiller on 2013-05-29
Right-click (or right-click-with-some-combination-of-modifier-keys-that-I-can-never-remember if you're using Unity/Gnome 3 - Alt-Super would be my guess) and select Add to Panel. It's probably one of the indicator applets that you want.

---

### Post by Juniorr on 2013-05-29
> **CatKiller said:**
> Right-click (or right-click-with-some-combination-of-modifier-keys-that-I-can-never-remember if you're using Unity/Gnome 3 - Alt-Super would be my guess) and select Add to Panel. It's probably one of the indicator applets that you want.
Yes! That was it, thanks!

Just one problem, after trying to remove it with "sudo apt-get remove --purge gnome-panel", unity has only the desktop icons, nothing else.

---

### Post by CatKiller on 2013-05-29
I don't know much about Unity. It's a Compiz plugin, so CompizConfig-Settings-Manager will help you enable it if it isn't already. You'll also want to make sure that you're logging into a Unity session rather than some Gnome fallback.

---

### Post by Juniorr on 2013-05-30
I'm am logging into Unity, all I did was apt-get --purge gnome-panel, and then that happened. I can't even open the terminal on Unity so I'm hoping someone has been through this as well. I don't want to re-install the system.

---

### Post by Juniorr on 2013-05-30
Oh well, after installing compiz and compiz-extra, everything got back. Weir, but worked. Thank you =)

---

