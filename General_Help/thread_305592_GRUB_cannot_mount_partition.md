---
title: "GRUB cannot mount partition"
date: 2006-11-23
forum: General Help
---

### Post by kimara on 2006-11-23
Hi

I want it to try out Arch linux, so I installed it to other partition and put this in to my grubs menu.lst

```
title  Arch Linux
root   (hd0,6)
kernel  /boot/vmlinuz26 root=/dev/hda7 ro
initrd  /boot/initrd26.img
```

but grub game me error 17: Cannot mount selected partition

Grubs manual says:
17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Filesystem is ext3, same as ubuntu has.

Does anyone knows how to make it work.

I use Feisty.

---

### Post by ingo on 2006-11-25
afraid I don't know, but apparently this 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

little helper might do the trick. Please report back if you use it. Thanks

---

