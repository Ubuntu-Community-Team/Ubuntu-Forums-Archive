---
title: "wubi install problem: install step failed"
date: 2008-01-16
forum: General Help
---

### Post by therealtigger on 2008-01-16
ok, so I decided to install xubuntu, using wubi to install it.

It's an oldish laptop that belongs to my brother, so im installing to an external usb hard drive ( drive K: in windows).
I downloaded the wubi installer (to drive K), ran it, selected drive K, xubuntu etc. and it all seemed fine. I was prompted to restart, so I did, chose to boot to ubuntu, and was presented with the installer thingummy. This was ok, except that it kept giving me a message: install step failed. I think it was partitioning that failed. After that, I could not get any further with installing it, so I booted back to windows. Does anyone know if I'm doing something wrong, or how I can fix it?

thanks for your help.

---

### Post by ago on 2008-01-16
If it is 7.04
reinstall and when it stops press alt+f4 to get more details

---

### Post by therealtigger on 2008-01-16
ok, I reinstalled wubi ( a fresh install on a formatted drive). It installed ok ( I think) I got to the "please reboot" stage, rebooted, chose ubuntu, and was presented with:


```
Booting 'find /wubi/boot/grub/menu.lst
Booting 'find /menu.lst
find --set-root --ignore-floppies /menu.lst '
Error 17: File not found
Press any key to continue
```

The screen after that is not particularly helpful, just a list of files, and the option to reboot i think.

Thanks for your help.


edit: btw, it is 7.04, plain ubuntu installation.
I think I know how to fix this problem (change things from hd0,0 to hd1,0 or w/e, but I'm reluctant to try just now as I don't want to mess it all up completely)

---

### Post by ago on 2008-01-17
Check that you have /wubi/boot/grub/menu.lst on some of the drives
You may want to try wubi 7.10 ([http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/) )

---

### Post by therealtigger on 2008-01-17
ok, I tried a fresh install, 7.10, NTFS formatted hard drive, xubuntu. (I had previously tried FAT32).

I got as far as rebooting my comp, chose "ubuntu-linux", and was soon presented with a busybox shell. So I booted back to xp :( and wrote this message.

---

