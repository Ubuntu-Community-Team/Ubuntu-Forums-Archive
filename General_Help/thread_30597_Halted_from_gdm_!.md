---
title: "Halted from gdm ?!"
date: 2005-04-29
forum: General Help
---

### Post by neokod on 2005-04-29
hi,

I have installed Ubuntu yesterday (from Internet, so I used the Hoary version)
When I wait approximatively one hour, the system is shutting down by gdm.

I have run a kernel compilation and the message above have appear :
  LD      lib/built-in.o
  CC      lib/bitmap.o

Broadcast message from root (tty1) (Fri Apr 29 15:05:44 2005):

Halted from gdm menu.
The system is going down for system halt NOW!

Any ideas ?
Thanks

---

### Post by defkewl on 2005-04-29
Try removing halt or reboot from /etc/init.d

---

### Post by neokod on 2005-05-03
This works !

Thanks

---

