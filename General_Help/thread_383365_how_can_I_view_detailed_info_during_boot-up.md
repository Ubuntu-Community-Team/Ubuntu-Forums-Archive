---
title: "how can I view detailed info during boot-up?"
date: 2007-03-13
forum: General Help
---

### Post by g0l3m on 2007-03-13
Hello all,

I was wondering if there's a way to see what's happening behind the scenes when the system boots up.  Currently you get the Ubuntu logo and a progress bar.
I'd like to see more detailed info regarding what services are starting, which bits take longer than others to load up, etc.

It's quite beneficial to see this info because you may find you can speed up your boot up process.

thx in advance,
g.

---

### Post by daou on 2007-03-13
Remove the quiet option from the boot options... when you get to GRUB, press 'e' to edit the boot options, or edit your /boot/grub/menu.lst file.

---

### Post by g0l3m on 2007-03-13
There are 2 quiet options:

One for the kernel (which I'm assuming is the one you mean) and one on the line after the initrd:

title       Ubuntu, kernel 2.6.17-10-generic
root        (hd0,0)
kernel      /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro **quiet** splash
initrd      /boot/initrd.img-2.6.17-10-generic
**quiet**
savedefault
boot

Do you know what each one does?

cheers,
g.

---

### Post by IcemanV9 on 2007-03-13
OR you can view (investigate) dmesg.

```
dmesg |less
```

---

