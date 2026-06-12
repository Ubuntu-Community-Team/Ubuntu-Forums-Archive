---
title: "BitTornado Yellow"
date: 2005-09-25
forum: General Help
---

### Post by ngms27 on 2005-09-25
No matter what I do I cannot get BitTornado to download quickly and always get a yellow light.

I'm using version T-0.3.12

My DSL Router is set up to port forward TCP on ports 6681-6699 and 6881-6899 (different sites suggest these different ranges and one must be wrong!). It shows that it is not blocking packets.

It looks to me that Ubuntu is the issue. Any ideas?

---

### Post by Keffin on 2005-09-25
Go to the "prefs" menu in bittornado and you can see/set the ports that it uses. Mine uses 6881 to 6889, I think I might have had to set it to that though. I have firestarter installed and also had to make a rule in that to let bittorrent packets through.

---

### Post by ngms27 on 2005-09-25
Thanks, that fixed it

 :)

---

### Post by Trajan on 2005-10-11
I still get the same problem it always stays yellow no matter what even if the download rate is at 200kbps. 
How would i configure this to accept all the seeders taht are ready and available since it does limit them. :/ (I was seeing more seeders around 200 and was only being connected to 13 of them. :/

---

