---
title: "Azureus problems"
date: 2005-08-10
forum: General Help
---

### Post by rogersmith84 on 2005-08-10
I have a broadband cable connection and I am running Azureus.  My current download has 31 seeds and normally in windows, that download would be booking.  however, the peak speed has only reached 100 kb/s I havent seen any higher.  is there a way that i can speed this up??  Also it keeps giving an error about my incoming TCP on port 6881.  any suggestions?

---

### Post by Caboose on 2005-08-11
Do you have a firewall? Is the connection in Azureus green, or yellow?

---

### Post by rogersmith84 on 2005-08-11
I have a router and I have enabled Port Forwarding for that port.  I think that is the correct thing to do but im not completely sure.  I don't have a firewall on my linux sytem though.  and I believe that it is green.  I am not at home right now so i cant check.

---

### Post by bored2k on 2005-08-11
[QUOTE=rogersmith84]I have a router and I have enabled Port Forwarding for that port.  I think that is the correct thing to do but im not completely sure.  I don't have a firewall on my linux sytem though.  and I believe that it is green.  I am not at home right now so i cant check.[/QUOTE]
 When you start downloading , go to pcflank.com and do an advanced port scan on the port azureus is using (6881, or so you say). If it's correctly forwarded, the result should show an opened port. If it is open and you do do get a green status on azureus, its a tracker/torrent/seeders problem, not linux nor blue.frog. You can also re-run the azureus wizard and test the 6881 port.

---

### Post by rogersmith84 on 2005-08-12
I did this and the port isnt free so i changed the port that it uses in Azureus.  No more errors.  but it is still slower than I would think it would be.  It could just be coincedence. thanx for the help!!

---

