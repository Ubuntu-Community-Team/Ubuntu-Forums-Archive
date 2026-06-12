---
title: "How do I boot kubuntu without the progress splash and showing info?"
date: 2007-04-03
forum: General Help
---

### Post by yarr on 2007-04-03
Hi,
I'm running kubuntu (feisty) on my laptop and it's all been fine for ages - no problems whatsover.
Today it's started, when booting, to appear to freeze at a certain point and the cpu starts to sound like it's working at 100%. It stays like this for 6-10 seconds before continuing as normal.

I had a look at dmesg but nothing stood out at me.

How do I boot without the progress splash and showing the normal boot activity output so that I can see what it's doing duting this period?

Thanks

---

### Post by aysiu on 2007-04-03
Boot into recovery mode. Log in. Type ```
sudo nano -B /boot/grub/menu.lst
``` Find the kernel you normally boot from and remove the word *splash* from the end of the line. For example... before removal: ```
title           Ubuntu, kernel 2.6.20-13-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-13-386 root=UUID=274686a3-f373-4e8f-b073-8df7c138c933 ro quiet splash
initrd          /boot/initrd.img-2.6.20-13-386
savedefault

``` after removal: ```
title           Ubuntu, kernel 2.6.20-13-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-13-386 root=UUID=274686a3-f373-4e8f-b073-8df7c138c933 ro quiet
initrd          /boot/initrd.img-2.6.20-13-386
savedefault

``` Save (Control-X, Y, Enter). Reboot: ```
reboot
```

---

### Post by yarr on 2007-04-04
ah yes, thanks
i can edit that from the grub menu can't i
i hadn't noticed the splash at the end of the long kernel string before

thanks

---

### Post by aysiu on 2007-04-04
I don't really know much about editing from the Grub menu, but you can try that.

My instructions about using Recovery Mode should work, though.

---

### Post by yarr on 2007-04-04
sorry, that was more of a rhetorical question - typing as i thought sort of thing :)

yeah, pressing e on a grub boot option allows you to edit it before using it

---

