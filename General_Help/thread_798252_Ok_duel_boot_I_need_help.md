---
title: "Ok duel boot I need help"
date: 2008-05-18
forum: General Help
---

### Post by Kilroth on 2008-05-18
Okay I have SATA 80GB HDD that has Windows Vista on it and then I have a 400GB SATA HDD that has ubuntu 8.04 on it for the life of me I can't get them to do a dual boot and I don't have the option of reinstalling Vista I had a bad time trying to convince them on the phone I please for the love of what ever HELP

---

### Post by LaRoza on 2008-05-18
You'll have to be more specific about what is going on.

When you start the computer, what happens? Do you see Grub? Does Vista boot automatically?

If you see Grub, you'll have to add Vista to Grub. If Vista boots with no hint of Grub, then you will have to select the Ubuntu disk to boot first. Exactly how you do that depends on the computer.

---

### Post by Kilroth on 2008-05-18
ok I see Grub and then it boots into UBUNTU

---

### Post by NightwishFan on 2008-05-18
What was the method you used to install Ubuntu?

---

### Post by Kilroth on 2008-05-18
Ok I think your asking if I Installed from a cd or not well yes I first installed windows then I installed Ubuntu onto the 400GB HDD

---

### Post by ZabiGG on 2008-05-18
All the info you need should be in there:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Cheers

---

### Post by cdtech on 2008-05-18
This is my /boot/grub/menu.lst for my dual boot setup. I'm using my secondary drive for Ubuntu and select the drive through my bios at bootup. If your using your primary drive for Ubuntu you just need to add your Windows OS to the menu.lst.

Ubuntu see's the drives as hd0, hd1 - primary, secondary respectivly.

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
chainloader     +1
```

---

