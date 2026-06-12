---
title: "Ubuntu quit booting"
date: 2007-04-13
forum: General Help
---

### Post by yg17 on 2007-04-13
I have Feisty installed on my Core 2 Duo iMac and it was working great.

Tonight I installed some updates that the update manager said I needed, something about the kernel. It had me reboot after the updates. The Ubuntu boot splash screen came up for about 5 minutes, but the progress bar didn't go anywhere. Then it gave me this error:

BusyBox v1.13 (Debian....blah blah blah)

/bin/sh: can't access tty: job control turned off


How can I fix this, I can't get into the OS at all. 

Thanks

---

### Post by deevus on 2007-04-13
Im currently having the same problem. Help!

```
title           Windows XP on SATA drive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1
savedefault

title		Ubuntu, kernel 2.6.20-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=97ac078e-a135-41bb-99c1-743adbd533a7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-14-generic

title		Ubuntu, kernel 2.6.20-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=97ac078e-a135-41bb-99c1-743adbd533a7 ro single
initrd		/boot/initrd.img-2.6.20-14-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=97ac078e-a135-41bb-99c1-743adbd533a7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=97ac078e-a135-41bb-99c1-743adbd533a7 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=97ac078e-a135-41bb-99c1-743adbd533a7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=97ac078e-a135-41bb-99c1-743adbd533a7 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

Only Ubuntu, kernel 2.6.17-10-generic is working. Any ideas?

---

### Post by saxin on 2007-04-13
Yes, same problem here. What can I do to fix it?

---

### Post by deevus on 2007-04-13
Look here mate.

[http://ubuntuforums.org/showpost.php?p=2444593&postcount=28](http://ubuntuforums.org/showpost.php?p=2444593&postcount=28)

You can also do it by booting into an older kernel instead of using a LiveCD. Good luck.
I'm yet to reboot so I don't know if its going to work for me, but it has worked for several others.

---

