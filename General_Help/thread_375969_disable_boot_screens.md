---
title: "disable boot screens"
date: 2007-03-04
forum: General Help
---

### Post by t94xr on 2007-03-04
im wanting to disable the boot screen and have the defualt services list like ubuntu server?

this possible?

---

### Post by taurus on 2007-03-04
You just remove the "**quiet splash**" from the entry for the kernel in /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```

---

