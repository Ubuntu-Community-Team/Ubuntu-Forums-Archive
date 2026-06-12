---
title: "How do I get more information on boot"
date: 2007-05-13
forum: General Help
---

### Post by ghell on 2007-05-13
I used to like seeing things like "Mounting root filesystem            [   OK   ]" when I turned my machine on. Edgy and Feisty don't have this by default. Is there a way of turning it back on in Feisty?

---

### Post by taurus on 2007-05-13
You can edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and remove the **quiet** (near the end of the line) from the entry for kernel.

---

### Post by ghell on 2007-05-20
OK, thanks, I thought that just made it display the kernel loading messages etc before the ubuntu progress bar comes up. I'll try that now.

---

