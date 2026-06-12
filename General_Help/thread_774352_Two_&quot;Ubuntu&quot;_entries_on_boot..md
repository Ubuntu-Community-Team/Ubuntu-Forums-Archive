---
title: "Two &quot;Ubuntu&quot; entries on boot."
date: 2008-04-29
forum: General Help
---

### Post by jdv1800 on 2008-04-29
I have two "ubuntu" entries when I boot up in addition to Microsoft Windows Vista. How do I get rid of the extra "Ubuntu" entry?

---

### Post by ago on 2008-04-29
Probably because you run two different versions of Wubi (7.04 + 8.04)?
Anyway, EasyBCD is your friend ;)

---

### Post by bilal.17 on 2008-04-29
the second entry is probably the failsafe mode or the memtest, if you want to remove it just remove it form the grub entry using this.

```
sudo gedit /boot/grub/menu.lst
```

But i'd be very careful and save the original copy before editing in case something goes wrong

---

