---
title: "Grub restores irqpoll every time i install a new kernel"
date: 2006-11-15
forum: General Help
---

### Post by ilbozo on 2006-11-15
I started my ubuntu edgy live installation cd with irqpoll option. Now, every time i install a new kernel, grub restores this option that causes me many problems.
How can i disable this dis-function?

---

### Post by Ramses de Norre on 2006-11-15
There is a line "#defoptions" in your menu.lst, add your kernel option at that line. And don't remove the '#', it has to be there.

---

### Post by ilbozo on 2006-11-15
Thank you very much!

---

