---
title: "Grub problem?"
date: 2006-08-12
forum: General Help
---

### Post by Just4 on 2006-08-12
Ok, so everything works fine, I can dual boot fine with XP and Ubuntu, however, everytime I boot into Ubuntu  a odd glitch occurs, it adds multiple entries for Ubuntu (all duplicates) and when I go and deleted them and boot back into Ubuntu again, it happens again, what causes this?

Heres a sample of the menu.lst as to what happens:

```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.15-22-386
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-22-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-22-386
boot

title		Ubuntu, kernel 2.6.15-20-386
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-20-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-20-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-20-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-20-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-20-386
boot

title		Ubuntu, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Thats what happens to my menu.lst after I boot Ubuntu, but I like to keep my list like this:

```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

But everytime I change it back to that and reboot (Its fine if I don't boot Ubuntu, only changes when I do boot Ubuntu) it comes back with all the extra entries, its very annoying, is there ANYWAY I can fix this? - Thanks for any help.

---

### Post by DJ Scribblinni on 2006-08-12
Those aren't necessarily duplicates, they are different versions of the specific kernel you are running on.  The easiest way I know is to go to Synaptic and remove the older kernels.

---

### Post by Tomosaur on 2006-08-13
This will keep happening unless you limit the number of kernels Grub is allowed to show. You can remove the older kernels, but once a new updated version comes along, that will be added to the list. You can change the number of kernels by editing your menu.lst file and finding the section relating to the number of kernels. By default it is set to 'all', but I keep mine on 1.

You can also alter this setting with the script in my sig :)

---

