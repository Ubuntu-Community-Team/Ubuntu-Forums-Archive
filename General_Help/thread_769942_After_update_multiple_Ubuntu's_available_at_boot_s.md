---
title: "After update multiple Ubuntu's available at boot screen"
date: 2008-04-27
forum: General Help
---

### Post by TBelmont on 2008-04-27
I recently updated Ubuntu. When I rebooted I noticed multiple Ubuntu choices in the boot screen. I choose the first and was presented with no wireless network access and multiple applications crashing. I rebooted into the secound choice and booted into a stable Ubuntu with Network access. Is there any way to reduce the number of choices in the boot screen?

---

### Post by tamoneya on 2008-04-27
just comment out the unnecessary lines in /boot/grub/menu.lst```
gksudo gedit /boot/grub/menu.lst
```

---

