---
title: "Can I save/dd a current running LiveCD to a USB stick or ISO image"
date: 2014-12-10
forum: General Help
---

### Post by merrittr on 2014-12-10
Hello LinuxPals :)

I have a PC that i borrowed and was not allowed to install ubuntu to the hard drive , so to do some switch testing i booted up a live try it cd and proceeded to apt-get what i needed ...now that i have done all this work Id like to save what i have can I do so by "imaging" the live cd instance currently running to a .iso .bin USB ????


its ubuntu 14.04

---

### Post by nerdtron on 2014-12-10
Doesn't the Live CD have persistence? That way, anything your change/install will be saved.

OR
How big is the USB? It would be better if you can just perform a full installation on the USB drive.

---

### Post by merrittr on 2014-12-10
Not sure how do you have persistence for the booted cd?
usb is 32gb so its big enough would be cool if i could just write it to the usb

---

### Post by ajgreeny on 2014-12-10
I think, but I'm not certain, that if you run a live DVD and use the startup-disk-creator in the live session, it will by default make a live USB of the running live DVD.

I've just checked this with a DVD with Lubuntu 14.04.1 and it does indeed offer to make a live USB direct from the DVD, and if you have enough space on the USB you can have up to 4GB persistent space.

---

### Post by westie457 on 2014-12-10
Posted by nerdtron

> [COLOR=#000000] It would be better if you can just perform a full installation on the USB drive.[/COLOR]

+1
This is a better solution.
To be on the safe side disconnect the internal drive/s of the computer you are using. Then you can use any install you want and know the original drive/s will be safe. Grub will be installed to the USB drive only.

Keep the installation simple. It is probably better **not **&#8203;to use a 'LVM' partitioning scheme.

---

