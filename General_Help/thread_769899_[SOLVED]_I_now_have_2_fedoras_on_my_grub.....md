---
title: "[SOLVED] I now have 2 fedoras on my grub...."
date: 2008-04-26
forum: General Help
---

### Post by mandrill on 2008-04-26
installed hardy - everything mostly ok so far, but instead of 1 instance of
fedora as an os on boot, I now have 2. (FC8 is installed 2nd partition sda)

prognosis?

cure?

Please help me before my other personality decides its ok to have 2......

---

### Post by tamoneya on 2008-04-26
just comment out the excess lines in /boot/grub/menu.lst```
gksudo gedit /boot/grub/menu.lst
```

---

