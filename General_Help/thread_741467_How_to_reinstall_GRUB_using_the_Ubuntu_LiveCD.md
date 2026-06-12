---
title: "How to reinstall GRUB using the Ubuntu LiveCD?"
date: 2008-03-31
forum: General Help
---

### Post by FastMady123 on 2008-03-31
I got an error 17. I can't boot into Ubuntu and/or Windows XP. Should I reinstall GRUB. How to do that?

---

### Post by Jose Catre-Vandis on 2008-03-31
Boot from live CD
Open terminal
```
sudo grub
find /boot/grub/stage1
```
the find command will return the location of your grub install, e.g. (hd0,0) Enter whatever it is into the next command
```
root (hd?,?)
setup (hd0)
quit
```
Reboot

---

