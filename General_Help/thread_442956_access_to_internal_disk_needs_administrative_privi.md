---
title: "access to internal disk needs administrative privileges"
date: 2007-05-14
forum: General Help
---

### Post by stijngysemans on 2007-05-14
After I installed ubuntustudio, is stumbled upon this "feature". I was previously using Feisty beta. Does anybody knows how to disable this feature, or to automount my internal hard drive?

---

### Post by stijngysemans on 2007-05-15
any ideas?

---

### Post by sudo on 2007-07-31
Any ideas on this?  I have the same situation....

---

### Post by merlinus on 2007-07-31
Post output of:

```

sudo fdisk -l
cat etc/fstab

```and the partition you are trying to access.

-merlin

---

### Post by stijngysemans on 2007-08-02
i solved the problem myself.
The problem was that i accessed my drive with the ntfs-3g driver, but i erased the driver or something... i don't know it exactly. To solve it: just configure your stab to use the 3g driver and install that driver also!

---

