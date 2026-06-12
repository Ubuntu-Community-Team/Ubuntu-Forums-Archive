---
title: "hdb=noprobe ---- alternative?"
date: 2007-12-08
forum: General Help
---

### Post by helix on 2007-12-08
title		Ubuntu 7.10, kernel 2.6.17-12-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=d088adcc-ba98-4461-961b-ace3d5800095 ro quiet splash hdb=noprobe irqpoll all_generic_ide
initrd		/boot/initrd.img-2.6.17-12-386

^^ My entry in grub


Anyways, I need to use "hdb=nprobe" so my boot won't take 6-8 minutes. Obviously when I do this I don't get use of my hdb.

Apparently this issue was fixed in later kernel issues but the other kernels run like crap on my computer and won't even boot up unless I use "irqpoll all_generic_ide" and turn off the quiet splash.

Any ideas? :popcorn:

---

### Post by helix on 2007-12-09
bump

---

