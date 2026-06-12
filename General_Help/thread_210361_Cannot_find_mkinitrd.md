---
title: "Cannot find mkinitrd"
date: 2006-07-06
forum: General Help
---

### Post by plutonium83 on 2006-07-06
I'm trying to make an initrd file for Xen to run on Ubuntu. For some reason, the mkinitrd command does not exist! All I can find is /etc/mkinitrd, which has nothing useful. 

I've recently switched from Fedora, is the mkinitrd command something different in Ubuntu?

(I have xgl installed)

---

### Post by tonyr on 2006-07-06
Install package **initrd-tools**.  **mkinitrd** shows up as **/usr/sbin/mkinitrd**.

---

### Post by Randomskk on 2006-07-06
Odd, I had the same problem as you and found it on /sbin/mkinitrd I believe (may have been /bin, one of those).

Looking around again, it seems to have gone o_o;
YAIRD is installable from the archives and that might work for you.

Edit: Ok, I guess that's where you get it from :P

---

### Post by plutonium83 on 2006-07-07
Hey thanks guys, I installed the package and it worked!

---

