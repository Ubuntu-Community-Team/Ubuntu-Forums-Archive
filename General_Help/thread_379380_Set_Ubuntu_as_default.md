---
title: "Set Ubuntu as default"
date: 2007-03-08
forum: General Help
---

### Post by mrmonday on 2007-03-08
Hi everyone,

I have decided that I would like to set Ubuntu as my default operating system so I don't have to hit enter (or wait) at start-up. Is this possible? I would still like to be able to boot into windows... I still have things that I need to use it for. Can I set Grub so that It will load Ubuntu, or if I hit a key, I get the boot menu? Can I set it so It automatically updates the default OS (Ubuntu 6.10)  when there is a kernel update (I have noticed it seems to add another operating system to the list).

Thanks for any help.

---

### Post by ArieT on 2007-03-08
Edit /boot/grub/menu.lst as root and change the value of timeout into a lower value, 0 in your case. If you don't want to load the default OS you must hit the arrow-keys when the computer starts booting.

It's recommed to make a copy of your menu.lst first before doing something stupid ;-)

---

### Post by bloodniece on 2007-03-08
Change your Grub file.

Backup your Grub menu.lst file.
```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```Edit /boot/grub/menu.lst 
```
sudo gedit /boot/grub/menu.lst
```I have Ubuntu as my default and XP last in my list.
```
title        Ubuntu, kernel 2.6.17-11-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.17-11-generic
boot

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
Vista/Longhorn title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by mrmonday on 2007-03-08
Thanks everyone. I have noticed that no the value is set to 0, so that Ubuntu automatically loads, I can't access windows. I have tried using the arrow keys, as suggested by ArieT,but I can't get to the menu. How can I do this? Also, when there is a kernel update, is the default OS automatically change to the new kernel?

---

### Post by bukwirm on 2007-03-08
Yes, the default is automatically changed to the new kernel.

You could just have a very short delay, say 5s.

---

### Post by mrmonday on 2007-03-08
Can I set a decimal value?

---

### Post by cookfromfrozen on 2007-03-08
> **mrmonday said:**
> Can I set a decimal value?
Probably not.

---

### Post by mrmonday on 2007-03-08
OK. Thanks for your help.:)

---

