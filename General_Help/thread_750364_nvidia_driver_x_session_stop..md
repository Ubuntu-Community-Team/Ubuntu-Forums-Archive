---
title: "nvidia driver x session stop."
date: 2008-04-09
forum: General Help
---

### Post by systembreak on 2008-04-09
hi all, 

I'm trying to install the newest driver for my nvidia (I've searched the forum for answers but I could not find a post) and it says that I have to have no x session running before I can install the .run file which I've downloaded from nvidia's website.

How do I do that? (when I used 6.10 it was /etc/init.d/xdm stop, but it seems to be otherwise now) I'm using 7.10 ubuntu. 

-systembreak

---

### Post by Ptero-4 on 2008-04-09
It's sudo /etc/init.d/gdm stop.

---

