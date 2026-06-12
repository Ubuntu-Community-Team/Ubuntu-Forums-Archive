---
title: "Still says 'Development Branch' on my grub menu"
date: 2008-05-07
forum: General Help
---

### Post by anando on 2008-05-07
Hi 

I have been running Hardy since beta and have regularly updated my packages (once a day at least). Why does it still say 'Development Branch' on my grub menu ? Isn't this a released version ? Do I need to upgrade in some special way to the 'official' released version ?


Thanks,
Anand.

---

### Post by lswest on 2008-05-07
your grub entries were just not updated, you can edit the titles in /boot/grub/menu.lst and remove it if you want.  to open it:
```
sudo gedit /boot/grub/menu.lst
``` (in case you need it)

---

