---
title: "damn progress bar"
date: 2007-03-05
forum: General Help
---

### Post by vincentvee on 2007-03-05
anyone got any idea hoe to remove the progrss bar from edgy?
all i seem to be able to find is info on restoring process listing, which i already knew and applied
the problem is i really like the edgy splash but i hate those M$ looking progress bars
LOL
any help greatly appreciated

---

### Post by strabes on 2007-03-05
Do you mean the progress bar on the bootsplash screen? The bootsplash screen is the screen that first comes up when you boot into linux from GRUB. You can either disable the bootsplash and just have a text boot or get a different bootsplash image. To disable the bootsplash image, simply remove the word "splash" from the "kernel" line in /boot/grub/menu.lst:

> 
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-9-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-9-generic root=UUID=09d2e5f8-c128-4244-b2ba-6259c0515588 ro quiet **splash** vga=792 resume=/dev/sda6
initrd          /boot/initrd.img-2.6.20-9-generic
quiet
savedefault


You could also get a different bootsplash image. Try installing the packages debian-edu-artwork-usplash, ichthux-artwork-usplash, and kubuntu-artwork-usplash. To configure which bootsplash screen displays, use this command: ```
sudo update-alternatives --config usplash-artwork.so
```

Hope this helps.

---

### Post by mcduck on 2007-03-06
You should also remove the 'splash' under the default options, otherwise you'll have to do this again after next kernel update ;)

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=792
```

(yeah, the line is commented out. forget about that, as it's used when regenerating the menu.lst file after kernel upgrades..)

---

### Post by vincentvee on 2007-03-06
> **strabes said:**
> Do you mean the progress bar on the bootsplash screen? The bootsplash screen is the screen that first comes up when you boot into linux from GRUB. You can either disable the bootsplash and just have a text boot or get a different bootsplash image. To disable the bootsplash image, simply remove the word "splash" from the "kernel" line in /boot/grub/menu.lst:



You could also get a different bootsplash image. Try installing the packages debian-edu-artwork-usplash, ichthux-artwork-usplash, and kubuntu-artwork-usplash. To configure which bootsplash screen displays, use this command: ```
sudo update-alternatives --config usplash-artwork.so
```Hope this helps.
yeah thats what i mean, but what i want is to remove the progress bar, but still have the ubuntu logo that is there......you think this is possible?

---

### Post by mcduck on 2007-03-09
> **vincentvee said:**
> yeah thats what i mean, but what i want is to remove the progress bar, but still have the ubuntu logo that is there......you think this is possible?
You could try to find a usplash theme that has no progress bar, or perhaps make your own. I remember seeing a tutorial somewhere and it wasn't really that hard..

---

### Post by vincentvee on 2007-03-10
> **mcduck said:**
> You could try to find a usplash theme that has no progress bar, or perhaps make your own. I remember seeing a tutorial somewhere and it wasn't really that hard..
yeah thats what i'm gonna do when i get the time....llets face it it is not system essential for me to do this
just something that i am not fond of, i always hated the one in winXP too, but then again i hate winXP too

---

