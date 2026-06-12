---
title: "[SOLVED] Grub"
date: 2007-04-11
forum: General Help
---

### Post by dstein on 2007-04-11
Yesterday I logged in to Ubuntu and performed a software update (I'm not sure what was updated). After rebooting (which was required for the update), the option to boot to Windows XP is missing from my GRUB menu. How should I go about getting this option back? Thanks.

---

### Post by paparucino on 2007-04-11
> **dstein said:**
> Yesterday I logged in to Ubuntu and performed a software update (I'm not sure what was updated). After rebooting (which was required for the update), the option to boot to Windows XP is missing from my GRUB menu. How should I go about getting this option back? Thanks.

```

sudo gedit /boot/menu.lst

```
Then add

```

title		Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

before or after the linux boot.
Something like this

```

title		Bertie
root		(hd1,2)
kernel	/boot/vmlinuz-2.6.20-14-generic root=UUID=89fadb32-51ad-42c8-9ddd-c6695eed8ad3 ro quiet splash
initrd	/boot/initrd.img-2.6.20-14-generic
quiet
savedefault
boot

title		Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```
If you put the windos boot in the first position, this will be the default boot OS.

Save and try :-)

---

### Post by Herman on 2007-04-12
Yes, that is partially correct, that will cause Windows to boot first by default for a while... until the next kernel update.
 
Then your Windows entry will be automagically deleted again and you'll have to type it in manually all over again.

The problem is that you are pasting your Windows entry inside the debian automagic kernels list.

The beginning and ending of the debian automagic kernels list is clearly marked. 
You can safely place boot entries for other operating systems either before or after the debian automagic kernels list. 
Then they won't be deleted, but inside the debian automagic kernels list, everything that doesn't belong will be deleted. :D

Why not click on my third sig link and try some of the other interesting ways you can customize your Grub menus? Grub is lots of fun. :D

Regards, Herman :D

---

