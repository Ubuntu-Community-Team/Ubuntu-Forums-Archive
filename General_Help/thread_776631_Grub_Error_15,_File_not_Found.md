---
title: "Grub Error 15, File not Found"
date: 2008-04-30
forum: General Help
---

### Post by Dr Small on 2008-04-30
In my attempt to make a bootable floppy disk with GRUB bootloader on it, everything works thus far, save one thing.

When I press enter to load my default entry to boot the computer, I get:
```
GRUB Error 15
File Not Found

Press any key...
```

Well, I thought that was strange, since I copied the same file that boots my computer now, over to the floppy. But here is what mystifies me further... If I select the Recovery Mode, it boots fine and takes me to the root prompt.

There must be something I am doing wrong. I will even show the entries for my menu.lst:
```
title           Ubuntu, 7.04 [DARKGHOST]
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=3cd432b2-b8af-4b54-815f-5ae2ebc931b4 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, 7.04 [DARKGHOST] (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=3cd432b2-b8af-4b54-815f-5ae2ebc931b4 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

```

Both, as I have noticed, are directing GRUB to the same file, only the first entry has "quiet splash" whereas the second one simply has "single".

If anyone can give me some hints or suggestions, I would greatly appreciate it :)

By the way, this should be my 3,000th post! :D

Dr Small

---

### Post by Dr Small on 2008-04-30
In less than 10 minutes, I solved my problem :)
I simply removed:
```
quiet
savedefault
```

From the first entry, and she booted just fine :D

Dr Small

---

