---
title: "sata_sil broken in 8.04??"
date: 2008-06-16
forum: General Help
---

### Post by nkonstas on 2008-06-16
Hi

[Have a look here]("http://www.backports.ubuntuforums.org/showthread.php?t=829779") for some background info first.

I've been looking at this problem for a day now and it seems to me that the sata_sil driver doesn't not function correctly in 8.04 (kernel 2.6.24-18-generic). It works fine in the previous version (kernel 2.6.22-14-generic) which I'm currently forced to use.

[Here's a diff in the sata_sil driver code for the two builds]("http://lxr.free-electrons.com/diff/drivers/ata/sata_sil.c?v=2.6.24;diffval=2.6.22;diffvar=v")

Has anyone managed to fix this problem? It's not a minor issue...

([This may be the same problem]("http://bugs.archlinux.org/task/9706"))

[EDIT]
My mistake: the drive names have changed following the upgrade to 8.04. It all works fine now.

thank you.

---

