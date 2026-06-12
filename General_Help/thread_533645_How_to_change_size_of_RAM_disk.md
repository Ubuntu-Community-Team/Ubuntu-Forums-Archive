---
title: "How to change size of RAM disk?"
date: 2007-08-24
forum: General Help
---

### Post by dpsharp on 2007-08-24
I'm using Ubuntu Feisty Fawn running from a live cd. It's on a work laptop so i don't want to install anything permanent. I want to create a 1GB RAM disk to temporarily store data while I copy it between media cards.

I can create a RAM drive by doing the following
  /sbin/mke2fs -q -m 0 /dev/ram0
  mkdir /mnt/rd
  /bin/mount /dev/ram0 /mnt/rd

But it's only 64Mb in size, how can I increase the size of the RAM disk?

I've read elsewhere articles about changing grub.conf for when the kernel initialises but I can't find this file and am not sure I'd be able to change it as I'm running from a live cd?

Cheers
Dave

---

### Post by zucche on 2008-05-31
I'm using 500 Mbytes ramdisk by adding ramdisk_size=500000 to the kernel line in /boot/grub/menu.lst:

```
kernel /boot/vmlinuz-xxx root=UUID=123-xxx ro quiet splash ramdisk_size=500000
```

---

