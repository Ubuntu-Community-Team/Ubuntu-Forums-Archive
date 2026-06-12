---
title: "Huge Fstab problem"
date: 2006-11-19
forum: General Help
---

### Post by JC_Starter on 2006-11-19
Hi,
i screwed /etc/fstab up, by adding noatime at the wrong place. I only can boot in ro mode. How can i change to rw mode and make the fstab changes undone? 

TIA

---

### Post by bettlebrox on 2006-11-19
mount -o rw,remount  /

And then edit your /etc/fstab . Post your fstab file if you want us to help U with it.

---

### Post by c00w on 2006-11-19
Boot w/ the live cd adn then modify the file

---

### Post by JC_Starter on 2006-11-19
Hi 

i get an error like
mount : unknown filesystem noatime 

can i overrule this with
mount / -t ext3 -o rw

but i am not sure of the exact syntax

---

