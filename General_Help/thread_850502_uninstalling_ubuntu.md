---
title: "uninstalling ubuntu"
date: 2008-07-05
forum: General Help
---

### Post by joordee on 2008-07-05
How do I uninstall ubuntu within ubuntu

---

### Post by theshadowwithanmp5n on 2008-07-05
there's an uninstaller
i think you can get it from ubuntu's home page.
that's where i heard about it

but why would you want to uninstall ubuntu?

---

### Post by joordee on 2008-07-05
I want to uninstall because it wont let me boot vista

---

### Post by ajgreeny on 2008-07-05
What exactly do you mean "it won't let me boot vista"?  If Vista booted before you installed ubuntu, it is likely to simply be a problem with the /boot/grub/menu.lst file.  Post the output of sudo fdisk -l and cat /boot/grub/menu.lst and someone will probably be able to come to your rescue.
I am assuming you didn't install with wubi.  If you did, I am not sure this will help, and you may need more help than I can give.

---

### Post by joordee on 2008-07-05
yes I installed with wubi, anyway the screen says loading grub please wait..., then it says error 2 underneath

---

### Post by L337_K3y5 on 2008-07-05
> **joordee said:**
> yes I installed with wubi, anyway the screen says loading grub please wait..., then it says error 2 underneath

I never used Wubi, I would install from live cd, much easier to work with.  I don't like installing a OS within another...don't trust them to play well.

---

### Post by joordee on 2008-07-05
> **L337_K3y5 said:**
> I never used Wubi, I would install from live cd, much easier to work with.  I don't like installing a OS within another...don't trust them to play well.

well uh im just trying to uninstall ubuntu now

---

