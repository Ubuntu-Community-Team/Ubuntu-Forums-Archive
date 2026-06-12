---
title: "[SOLVED] Need help getting verbose boot screen"
date: 2008-02-22
forum: General Help
---

### Post by Nate9009 on 2008-02-22
Hi everyone!  I've been trying to remove my current bootsplash screen and get a text based boot that is verbose enough for my needs.

I've tried downloading and using startupmanager, but everytime I reboot my computer all I get is a blank screen.  No splash image, text, nothing.

I've edited my /boot/grub/menu.lst (removed the "quiet") to be verbose, but so far I've got nothing.

```
 

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe990c37-f192-460d-8d95-56f8d1bf3920 ro vga=normal
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe990c37-f192-460d-8d95-56f8d1bf3920 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fe990c37-f192-460d-8d95-56f8d1bf3920 ro vga=normal
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fe990c37-f192-460d-8d95-56f8d1bf3920 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


```

Any ideas where I should go from here?

---

### Post by yabbadabbadont on 2008-02-22
Remove the splash option from your grub.conf and replace it with verbose.  If all else fails, add "vga=normal", as that should force 80x25 text mode boot.

---

