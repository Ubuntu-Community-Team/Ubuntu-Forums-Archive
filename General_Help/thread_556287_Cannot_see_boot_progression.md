---
title: "Cannot see boot progression"
date: 2007-09-21
forum: General Help
---

### Post by lakelovers on 2007-09-21
With Dapper and now Feisty I cannot see the booting progression prior to the splash screen. When I boot, I get a black screen until the splash screen appears. I don't really need to see what happening when booting but the blank screen make the boot time seem longer.

---

### Post by arkara on 2007-09-21
if you have not a dual boot machine this is normal
if you have solo boot this is weird..

---

### Post by lakelovers on 2007-09-21
Arkara. . . Well I guess I have a weird Feisty installation. I don't have a dual boot and I only boot to Ubuntu.  I made a fresh install a few weeks ago and the boot has always acted as I described. I misspoke on my first post, Dapper booted normally. It was when I installed Edgy that the "no-seeum" boot began. I'm running Gnome. only, though I may install Kubuntu.

Jerry

---

### Post by Chewie8 on 2007-09-21
I think you have to change your GRUB settings.  Change menu.lst

```
sudo gedit /boot/grub/menu.lst
``` 

Change your kernel line

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(xxx, X)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e1fe8290-c29b-4682-9844-ecf1114075de ro **quiet** splash
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
```

Remove **quiet**.  This will display all the output of the startup sequence.  I think this is what you are looking for.

---

### Post by lakelovers on 2007-09-21
Chewie8. . . Thanks for your response. Do I remove all the "quiet" references in this menu? I have backed up the file but I'm still hesitant to start removing stuff until I know for sure what I'm doing. Let me know whether I should remove all "quiets."



[PHP]title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a6aae71a-dd97-46e5-b965-fd0582768341 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a6aae71a-dd97-46e5-b965-fd0582768341 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a6aae71a-dd97-46e5-b965-fd0582768341 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a6aae71a-dd97-46e5-b965-fd0582768341 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet[/PHP]


**Edit: I removed all the "quiet" elements then rebooted. I did get the boot progression for about one-half the time then it when to black until the splash screen appeared. I guess that's normal. Right?**

---

