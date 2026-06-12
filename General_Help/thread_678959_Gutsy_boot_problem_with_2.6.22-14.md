---
title: "Gutsy boot problem with 2.6.22-14"
date: 2008-01-26
forum: General Help
---

### Post by tgabi on 2008-01-26
I have a problem booting 2.6.22-24. Older kernel 2.6.20-16 works fine on the same computer. The motherboard is Asus M2A-VM (AMD chipset), Sempron CPU, IDE (PATA) disc. The boot stops at IDE detection - if the sequence is the same as 2.6.20-16- but it can be restarted by <CTRL><ALT><DEL>. I've tried also 2.6.24-5 that lock the computer solid at about same stage. Any ideas ?

---

### Post by tgabi on 2008-02-01
The BIOS was old (0302) and I guess ACPI was not working right. After upgrade to latest BIOS (1604) all is well.

---

### Post by matey3 on 2008-02-01
hit the escape to see the menu, then edit those lines. I had a similar problem after installing xen the other day and it was in my menu file. edit menu.lst and compare it to the old one specially where it points to the (hd0,2) , make sure the new one is like the old one...

btw did u wait a while to see if the ramdrive loads?
good luck!

---

