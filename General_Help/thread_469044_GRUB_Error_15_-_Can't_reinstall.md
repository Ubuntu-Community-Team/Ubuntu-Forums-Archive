---
title: "GRUB: Error 15 - Can't reinstall"
date: 2007-06-09
forum: General Help
---

### Post by JulianRoot on 2007-06-09
Hello!

I edited my partition table and now GRUB doesn't start (Error 15).
Now I booted from a Desktop-CD an chrooted my Ubuntu partition and executed "grub-install /dev/sda", but it doesn't work.
I get this error:
```
The file /boot/grub/stage1 not read correctly.
```

Julian

---

### Post by merlinus on 2007-06-09
Since you re-sized partitions, the UUIDs have changed.  Therefore, the references to your kernels in grub are probably incorrect.

The following may be useful.

After booting from the live cd, in a terminal:

```

sudo fdisk -l

```

This will give you a list of your partitions and filesystems.

(l is a lowercase L)

Then:

```

blkid

```

This will give you the UUIDs.

Compare these with those listed in /boot/grub/menu.lst and /etc/fstab.

But be sure you are looking at these files on your hard disk, not in RAM, which is where the live cd runs.

Another option is to try supergrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Good luck!

-merlin

---

