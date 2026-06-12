---
title: "How to change boot order of grub?"
date: 2008-06-27
forum: General Help
---

### Post by Landscapeman on 2008-06-27
I have a triple boot and I want it to automaticly start on ubuntu rather than Open SUSE. How would I go about changing the order and the amount of time? Thanks

---

### Post by Xgen on 2008-06-27
If you're booting from Grub in Ubuntu then:

gksu gedit /boot/grub/menu.lst

timeout (seconds)
default (boot number starting from 0 as the first one)

Other options in there that you might want to read too.

---

