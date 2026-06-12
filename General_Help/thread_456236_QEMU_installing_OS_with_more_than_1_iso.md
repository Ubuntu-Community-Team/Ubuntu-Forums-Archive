---
title: "QEMU: installing OS with more than 1 iso"
date: 2007-05-27
forum: General Help
---

### Post by marianom on 2007-05-27
Hi, I need to install Red Hat 7.3 virtually. It comes with 3 .iso. I burned them to CD and I still have the images in my machine too.
I'm using QEMU but while installing it asks me for the 2nd CD and I don't know how to make QEMU use it.
I tried using the CD and I change from the first to the second CD when it asked it but the installation process tells me it cannot be mounted.

Anyone can tell me how to make QEMU use the additional CDs when required?

TIA,

---

### Post by earobinson on 2007-05-27
maybe try mounting the isos then telling QEMU to use the mount location, then u can unmount and remount iso 1 2 and 3.

But I know nothing about qemu

---

### Post by marianom on 2007-05-27
Thanks for your suggestion, earobinson.

I just happen to find the right answer (it seems I was not looking hard enough).

In case anybody wonders the same thing: you need to add the following to your qemu installation process:

```
qemu -monitor stdio *the other options*
```

this will add a CLI to your installation process. When you need to change the cd/iso, just type in the CLI (e.g.):

```
qemu change cdrom redhat_valhalla_disk2.iso
```

It should do the trick.

---

