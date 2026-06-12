---
title: "[SOLVED] What's the program that starts before grub in gutsy?"
date: 2007-10-19
forum: General Help
---

### Post by olavjunior on 2007-10-19
I used the beta of gutsy earlier, and then I had a nice little thing hiding the grub for 3 seconds. I had to push esc if I wanted to enter grub. I liked it, cleaner then grub. 

but after installing gutsy from scratch, this is no longer present. Why? And what is it called? Can I install it now?

---

### Post by pointone on 2007-10-19
It's a GRUB option. Edit /boot/grub/menu.lst and uncomment hiddenmenu.

---

### Post by strabes on 2007-10-19
> **pointone said:**
> It's a GRUB option. Edit /boot/grub/menu.lst and uncomment hiddenmenu.

To avoid confusion, you can simply run:```
gksudo gedit /boot/grub/menu.lst
```Then remove the # sign in front of "hiddenmenu"

---

### Post by olavjunior on 2007-10-20
Thanx

---

