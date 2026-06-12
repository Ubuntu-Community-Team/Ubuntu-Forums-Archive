---
title: "[SOLVED] kernel update not listed in menu.lst"
date: 2008-05-26
forum: General Help
---

### Post by alienexplorers on 2008-05-26
I just ran update manager and it loaded the new 17-generic kernel.  It popped up a box asking something about the new kernel and I must have missed what it was asking.  When the update was finished I rebooted and was only given the option of booting the 16-generic kernel.
I ran sudo update-grub and it recognized both kernels and said they were written to menu.lst file.  Did a cat of menu.lst and noticed the 17-generic kernel was still missing.
How would I add the new kernel to the menu.lst file manually.  My problem is I don't know the uuid to use.  Also I do not know how to generate the uuid.

---

### Post by bwhite82 on 2008-05-26
You don't need the UUID. Copy and paste the previous kernel lines and simply change the 16 to a 17.

---

### Post by werries on 2008-05-26
yeah thats right.
the UUID only tells it what harddrive to boot from.

---

