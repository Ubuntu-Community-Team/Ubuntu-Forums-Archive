---
title: "moving directories to a new partition"
date: 2005-06-09
forum: General Help
---

### Post by Wolki on 2005-06-09
Hi!

I need more disk space on my Ubuntu System and can't afford a new hdd ^^;;; i have a gentoo install that I don't use anymore, and I want to reclaim that space. One is a 2.8 gig partition that seems like a perfect fit for my /usr/lib/ directory (currently 1.4 gig, so there should be enough space for any programs I might want to install). How do i move them the smartest way?

I thought about deleting the gentoo /, copying the /usr/lib/ directory there and editing the fstab so that this partition is mounted as /usr/lib/. Do i have to delete the /usr/lib/ on my ubuntu, and if yes, can I do that on a running system?

Wolki

---

### Post by Alexander Kirillov on 2005-06-09
[QUOTE=Wolki]Hi!

I need more disk space on my Ubuntu System and can't afford a new hdd ^^;;; i have a gentoo install that I don't use anymore, and I want to reclaim that space. One is a 2.8 gig partition that seems like a perfect fit for my /usr/lib/ directory (currently 1.4 gig, so there should be enough space for any programs I might want to install). How do i move them the smartest way?

I thought about deleting the gentoo /, copying the /usr/lib/ directory there and editing the fstab so that this partition is mounted as /usr/lib/. Do i have to delete the /usr/lib/ on my ubuntu, and if yes, can I do that on a running system?

Wolki[/QUOTE]
 
Probably a safer way would be to get a a live CD (or system rescue CD) and do all these operations (copying /usr/lib to new partition, editing /etc/fstab, and then removing everything inside /usr/lib) while running the live CD. 

BTW: you realize that to mount something on /usr/lib, this directory should exist (so do not remove it) but be empty (so remove everything in it). Just making sure...

---

### Post by Wolki on 2005-06-09
Thanks! I'll probably do it from my Mandriva install, the joys of double booting :)

---

