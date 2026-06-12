---
title: "Installing custom compiled 2.4.26/27 kernel into grub; boot issues"
date: 2008-01-31
forum: General Help
---

### Post by tgrimley on 2008-01-31
So I compiled 2.4.26 from source after putting in the openmosix patch.

used make-kpkg and dpkg to install.

Took a while but got that to work fine.

Now I can't get the machine to boot with that kernel.

entry in menu.lst (grub)
```

root (hd0,0)
kernel /boot/vmlinuz-2.4.26-om1 root=/dev/sda1 ro quiet splash
savedefault
boot
```

When I boot I get 

```
Kernel panic: VFS: Unable to mount root fs on 08:01
```

I've tried a number of things and there are a few threads on this but none seem to work for me.  I've had varying success trying to generate an initrd image to make sure it had the proper drivers but I could sure use a bit of help troubleshooting this.

Thanks in advance for any help!

---

### Post by imtheguru on 2008-01-31
Assuming that you have compiled in devfs and support for your root filesystem, perhaps remove the line "savedefault" from menu.lst?

---

### Post by tgrimley on 2008-02-01
Both those are there.  Tried with no savedefault but same thing.

Perhaps it can't find the sata drivers it needs?  How do I find out which it needs/if that might be the problem?

---

