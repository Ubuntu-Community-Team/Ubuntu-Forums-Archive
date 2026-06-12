---
title: "grub"
date: 2014-12-05
forum: General Help
---

### Post by kccv42 on 2014-12-05
How do i have grub automatically select ubuntu?

---

### Post by grahammechanical on 2014-12-05
Load into Ubuntu and run in a terminal

```
sudo update-grub
sudo grub-install /dev/sda
```

Assuming that there is only one hard drive. That will put the Grub of Ubuntu back in charge of the boot menu and Ubuntu will be at the top of the menu and automatically loaded once the time delay has ended.

Regards.

---

### Post by kccv42 on 2014-12-09
it worked thanks.

---

