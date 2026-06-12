---
title: "Screwed up my boot!"
date: 2013-01-25
forum: General Help
---

### Post by oxf on 2013-01-25
OK I hate asking silly questions like this which have an easy answer (I hope) but.....

I have Ubuntu on SDA1
I just installed Lubuntu 12.04 on a new partition SDA2

When prompted to restart the laptop to complete installation I did but I forgot to remove the USB drive so it booted from the USB again. I looked at options and choose number 4 "boot from first hard disk" thinking it would take me back to my HD.

Instead it dropped me to shell and I had no choice but to shut down the PC.

When I boot now and select SDA2 it says "no such device" and  a string of error messages.

I assume I just screwed up some config file so probably not major but how do I fix this?

Thanks

---

### Post by dino99 on 2013-01-25
when you get the command line, reinstall grub:

sudo grub-install /dev/sda1
sudo update-grub

---

### Post by oxf on 2013-01-25
> **dino99 said:**
> when you get the command line, reinstall grub:

sudo grub-install /dev/sda1
sudo update-grub

Thanks..
I'm a bit confused here.

Ubuntu:    /dev/sda1  (boots ok)
lubuntu             /sda2     (problem)

Ubuntu bootloader is in control on sda

When I try to install grub using Ubuntu terminal in sda1   it tells me it's a "bad idea"
"can only be install by blocklists" "but blocklists unreliable" 
End of install

---

### Post by kc1di on 2013-01-25
Hello dino99,

I would go [here]("https://help.ubuntu.com/community/Boot-Repair") and download and run boot-repair follow the instructions on the page , think it will fix your problem.
Cheers!

---

