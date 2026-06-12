---
title: "The infamouos &quot;can't access tty; job control turned off &quot;"
date: 2006-11-12
forum: General Help
---

### Post by Tadhg on 2006-11-12
Well, I'm having this problem on booting, after trying to resize a partition with gparted. 
While booting, I get nowhere except the error

[B]"hda1 doesn't have sbin/init"
"can't access tty; job control turned off"[/B]

Now, I understand that this is a partition problem, and seems the partition table is fubared, so i've booted up into a live CD, mounted my /dev/hda1 under /media/drive and thankfully everything is there. When i try to go into any of the sbin or etc directories and *ls* though, i get a 

"bad entry #8402: directory entry across blocks ..."

Anytime I've had a superblock/partition problem before, I've been able to fix it using an Install Cd partitoner and just rewriting it. Unfortunatly this won't work now, so what can i do to fix this up?

---

### Post by Tadhg on 2006-11-12
bump

---

### Post by Rui Pais on 2006-11-12
Hi,
try from the liveCD:
```
sudo e2fsck -f /dev/hda1
```
with hda1 not mounted.

---

