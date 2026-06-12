---
title: "Conflicting memory useage statistics seen"
date: 2012-12-31
forum: General Help
---

### Post by rocketman987654 on 2012-12-31
When I load most any System monitor applicaton, the memory in use is 1.9 GIG of 11.7 GIG, but that cannot be as I have VMWare 9 Workstation running with 8 VMWare Guests running.

free -m shows :
  
root@robert-Precision-WorkStation-T3400:~# free -m
                    total        used          free   shared  buffers   cached
Mem:         11952      11652        300          0           46          9765
-/+ buffers/cache:     1840    10111

Swap:        23436         57       23379

NOTE: I have Ubuntu 12.04, 64-bit, on a Dell Precision T3400 Core 2 Quad, 12 GIG of RAM

Performance on this linux box is NOT slow

Any clues/suggestions ?

Thank You,
Bob Perez (bperez@novell.com)

---

### Post by Cheesemill on 2012-12-31
You are using only 1.9GB of RAM, the rest is being used for cache.

Take a look at this site for the difference between the outputs of free and system monitor:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by rocketman987654 on 2012-12-31
Thank You for your help on this...

---

