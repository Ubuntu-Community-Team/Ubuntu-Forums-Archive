---
title: "Problem while creating swap space after Wubi install"
date: 2008-04-24
forum: General Help
---

### Post by Nikell on 2008-04-24
I'm trying to install Ubuntu using Wubi.
My computer is a laptop, AMD 64 Turion, 1GB of memory, 50GB disk space, and 12 free for now, using Windows XP. 

I asked Wubi to give 8GB to Ubuntu. I've downloaded the iso manually (8.04 desktop i386) and the md5 checksum match. 

The Windows part of the install worked fine, then I rebooted. I can choose Ubuntu on the boot. And the I pass trough the black splashscreen with the Ubuntu Logo and the Orange Thing playing unidimensional pong.
 
Then, it comes to a beautiful screen with that stylized Heron, and a window called in French (roughly translated, my English is pretty poor) Install Verification. And subtitled : System Install. With a filling bar and a percentage. 

Everything seems to go well, but when it comes to something called : "Creation of swap space in the partition n°1 of /host/..." (or something like that, in french : "Création de l'espace d'échange sur la partition n°1 de /host/..." it goes back to 0% and nothing more happens. I can close the window, or minimze it. But then I can do nothing more except shutdown by pressing the power button (but its a clear shutdown with white text over a black screen before the shutdown and everthing that seems normal, not like a hardcut)

About my Windows : I defragmented it a long time ago, like 1 year and a half. And my disk is partitionned in two parts, one for regular usage, and another created by the manufacturer, for recovery matters. 

(I'm a Newbie in Linux :), and this Wubi thing gived me courage to install Ubuntu. So even if there is no solution, I think I'll find another way to get to Ubuntu.)

---

### Post by ago on 2008-04-24
it might be that the swap file got fragmented. Try to replace c:\ubuntu\disks\swap.disk with another file of ~ 100MB (and check that it is contiguous using jkdefrag or similar).

---

### Post by scythe000 on 2008-04-24
> **Nikell said:**
> I'm trying to install Ubuntu using Wubi.
My computer is a laptop, AMD 64 Turion, 1GB of memory, 50GB disk space, and 12 free for now, using Windows XP. 

I asked Wubi to give 8GB to Ubuntu. I've downloaded the iso manually (8.04 desktop i386) and the md5 checksum match. 

The Windows part of the install worked fine, then I rebooted. I can choose Ubuntu on the boot. And the I pass trough the black splashscreen with the Ubuntu Logo and the Orange Thing playing unidimensional pong.
 
Then, it comes to a beautiful screen with that stylized Heron, and a window called in French (roughly translated, my English is pretty poor) Install Verification. And subtitled : System Install. With a filling bar and a percentage. 

Everything seems to go well, but when it comes to something called : "Creation of swap space in the partition n°1 of /host/..." (or something like that, in french : "Création de l'espace d'échange sur la partition n°1 de /host/..." it goes back to 0% and nothing more happens. I can close the window, or minimze it. But then I can do nothing more except shutdown by pressing the power button (but its a clear shutdown with white text over a black screen before the shutdown and everthing that seems normal, not like a hardcut)

About my Windows : I defragmented it a long time ago, like 1 year and a half. And my disk is partitionned in two parts, one for regular usage, and another created by the manufacturer, for recovery matters. 

(I'm a Newbie in Linux :), and this Wubi thing gived me courage to install Ubuntu. So even if there is no solution, I think I'll find another way to get to Ubuntu.)

Same error here. It reports that the partition manager has failed on install, just after I pick my timezone.

---

### Post by ago on 2008-04-24
please report the issue here: [https://bugs.launchpad.net/wubi/+bug/206113](https://bugs.launchpad.net/wubi/+bug/206113)

---

