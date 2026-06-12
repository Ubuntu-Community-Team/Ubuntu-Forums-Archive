---
title: "[SOLVED] Extra Kernels in Grub"
date: 2008-06-18
forum: General Help
---

### Post by kl324 on 2008-06-18
So right now my grub boot menu is a bit crowded with old linux kernels. I only boot from the latest kernel, so I'm thinking of deleting the other kernel options and the files associated. Is it safe to just remove the entries in grub (/boot/grub/menu.lst) and then delete the related kernels from /boot ?

---

### Post by rune0077 on 2008-06-18
I just uninstall them with Synaptic, that also seems to fix the grub-menus. But it's safe, as long as you don't accidentally delete the kernel you're currently using :)

---

### Post by drs305 on 2008-06-18
Removing kernels with synaptic is a safe way to remove them from grub. Another excellent method is to use startup-manager (System, Admin, Startup-Manager). If you don't see it, install it with:
```
sudo aptitude install startupmanager
```

Startup-Manager allows you to tweak many aspects of the grub menu display and is far less prone to mistakes than manually editing grub's menu.lst. Read more about it here:
[HOWTO: Grub Menu Kernel Display ]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by kl324 on 2008-06-18
> **rune0077 said:**
> I just uninstall them with Synaptic, that also seems to fix the grub-menus. But it's safe, as long as you don't accidentally delete the kernel you're currently using :)

Ah, thanks. Synaptic really is quite useful. Thanks, I'll be doing that.

---

### Post by Beernut on 2008-06-18
I have never used startupmanager but will need to look into it.  Another option is [GrubED script]("http://ubuntuforums.org/showthread.php?t=228104").

---

