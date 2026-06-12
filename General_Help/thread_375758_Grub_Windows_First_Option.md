---
title: "Grub: Windows First Option"
date: 2007-03-04
forum: General Help
---

### Post by shironeko on 2007-03-04
I'm just installing Ubuntu on my father's computer, but knowing how he is, he'll prefer to have Windows as the first option on Grub.

What do I have to do to change that?

thanks,

---

### Post by Kateikyoushi on 2007-03-04
You have to edit the menu.lst it provides information about how to chagne the default boot option. You need to change the "default" Number and numbering begins with zero, just count which is your windows entry and change the number.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```

---

### Post by dwarner30uk on 2008-01-26
Thanks very much Kateik... that looks like just what I was looking for. You are a star.

---

