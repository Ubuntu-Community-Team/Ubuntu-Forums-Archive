---
title: "kernel panic: not syncing vfs unable to mount root fs on unknown block (0,0)"
date: 2008-04-14
forum: General Help
---

### Post by nmsmith on 2008-04-14
I know that this thread title is well used on this and other forums, but none of the other threads I've read so far seem to match my symptoms. Unlike most issues, I have not recently (to my knowledge) updated the kernel. I may have done so through system-updates in gnome.

Nonetheless one common theme to all of these threads is that many of them concern the 2.6.22-14 kernel.

Following the advice at [this thread]("http://http://ubuntuforums.org/showpost.php?p=1711279&postcount=2") I have tried chrooting into my root partition (sda4 or hd0,0) and doing ```
sudo update-initramfs -u
``` but the output is:

```
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
cpio: ./sbin/udevd: Cannot stat: Input/output error
```

[This thread]("http://ubuntuforums.org/showpost.php?p=2207883&postcount=2") asked for a load of data. I don't know whether it's relevant as that was in Feb 2007, but I have attached the requested files. Note that I didn't have a file at /boot/grub/grub.conf, and that fdisk -l produced only the details of my flash drive. To get anything meaningful I had to do sudo fdisk -l /dev/sda.

---

