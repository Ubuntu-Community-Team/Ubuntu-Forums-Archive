---
title: "Loving Ubuntu so far, just need some help :)"
date: 2007-04-19
forum: General Help
---

### Post by Mb0742 on 2007-04-19
Hiya everyone, 

Ubuntu is my leisure OS Windows is my work Os and every morning I wake up turn on my comp and go out and eat my breakky. So I was hoping there was some way of having Windows at the top of my boot list, so I can walk out like always and it will just fire up windows after the 20something seconds :) Any [safe] ways?

Thanks people :)
~Matt

---

### Post by lizzard on 2007-04-19
The Windows boot option should be the first entry in your /boot/grub/menu.lst (I assume you use grub) so it will be booted by default.

---

### Post by Mb0742 on 2007-04-19
Really sorry but what does that mean? How do I access it?

---

### Post by lizzard on 2007-04-19
> **Mb0742 said:**
> Really sorry but what does that mean? How do I access it?

No problem. In terminal type:
```
sudo nano /boot/grub/menu.lst
```
Now you edit your menu.lst-file. You'll probably find something like this:
```


title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=c1515247-7a50-486f-891d-87a25a10810c ro quiet splash locale=de_DE
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=c1515247-7a50-486f-891d-87a25a10810c ro single
initrd          /initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /memtest86+.bin
quiet



[### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
[b]title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1[/b]

```

You'll have to put the bold marked part (Windows boot section) on top of the other sections (Ubuntu, recovery mode, memtest) to start it by default.

---

### Post by Mb0742 on 2007-04-19
So just copy the bold above the highest thing on the list?

---

### Post by lizzard on 2007-04-19
> **Mb0742 said:**
> So just copy the bold above the highest thing on the list?
Exactly, that's what I tried to say. :mrgreen:

---

### Post by Mb0742 on 2007-04-19
Worked a dream thanks :)

---

