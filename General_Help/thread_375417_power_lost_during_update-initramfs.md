---
title: "power lost during update-initramfs"
date: 2007-03-03
forum: General Help
---

### Post by sardion on 2007-03-03
Anyone know how to use a livecd to rebuild an initramfs?  The power died while I was doing an update-initramfs (without a backup, being brilliant me).  The computer boots fine but never gets past the hardware loading, almost like no root= was passed to the kernel (well exactly like that) except there is a correct root= line.

I booted from the livecd.  Mounted drive.  Chrooted to it.  Called update-initramfs.  No dice.

Anyone?
I really dont want to have to reinstall ubuntu, it will take me forever to remember al lof what I've done in /etc.

---

### Post by DagMan on 2007-03-03
can't you just install a generic kernel from the chroot and then boot into it and work from there?

---

