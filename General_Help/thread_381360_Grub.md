---
title: "Grub"
date: 2007-03-10
forum: General Help
---

### Post by Rhaddad on 2007-03-10
Hello,
can someone please tell me how to edit grub so it lasts 3 seconds then boots into ubuntu?

---

### Post by ~LoKe on 2007-03-10
```
gksudo gedit /boot/grub/menu.lst
```
Look for this section:
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3
It should look exactly like mine.

---

