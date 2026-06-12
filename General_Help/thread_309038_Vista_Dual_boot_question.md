---
title: "Vista Dual boot question"
date: 2006-11-29
forum: General Help
---

### Post by mwob on 2006-11-29
Hi all,

I currently dual boot XP with Ubuntu, and I need tp upgrade XP to vista. I fully expect Vista to crap all over GRUB and remove my boot loader so that it just boots straight into vista. My question is will it be easy for me to re-install GRUB to get back into Ubuntu - can I just install it from an Ubuntu install CD or something similar?

Thanks!

MAtt

---

### Post by reclusivemonkey on 2006-11-29
> **mwob said:**
> I currently dual boot XP with Ubuntu, and I need tp upgrade XP to vista. I fully expect Vista to crap all over GRUB and remove my boot loader so that it just boots straight into vista. My question is will it be easy for me to re-install GRUB to get back into Ubuntu - can I just install it from an Ubuntu install CD or something similar?

I had a whole load of trouble when I installed Vista for a look. Luckily I installed it on a second HD, so I just unplugged it for now. Vista seems to steal the bootable partition, despite all settings pointing to the first HD with Grub that works just fine without Vista.

Apparently, Vista boots differently to XP and you may run into problems. However, Grub did pick up both my XP install and Vista, so we know where the problem lies. Are you planning to install on the same HD?

---

### Post by mwob on 2006-11-29
Yep, I'm planning on just "upgrading" my XP, which is on the same harddisk.....Hmmm, this is not going to be fun!

---

### Post by reclusivemonkey on 2006-11-29
> **mwob said:**
> Yep, I'm planning on just "upgrading" my XP, which is on the same harddisk.....Hmmm, this is not going to be fun!

At worst you should be able to delete the vista partition and get your Ubuntu back. This link might help you out;

[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)

---

