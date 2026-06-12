---
title: "Ubuntu 20.04 eSata drives won't stay connected"
date: 2021-12-11
forum: General Help
---

### Post by Rick P. on 2021-12-11
So I'm finally in the process of upgrading my home server from 16.04 to 20.04, a task I've put off for a long time because I didn't want to have to reconfigure everything from scratch. In the process I've found that an external drive bay I've been using for years (Orico 5-disk 3.5" HDD enclosure) will not stay connected using eSata. The drives will connect as usual, then disconnect and cycle back through the connection process again every 20 seconds or so, repeating as long as I leave the drive enclosure power turned on. I don't know why it would make a difference but I changed the eSata cable since i have others and it still does it. The enclosure works fine with Ubuntu 16.04. Any suggestions on getting it to connect and stay connected using 20.04 would be welcome. I could use USB 3.0 and am using it for the time being but prefer to use eSata for my drives since I've found it to be more stable for permanently-attached drives, which these are.

---

### Post by sudodus on 2021-12-11
I think the problem is the electronics in the enclosure, it is not compatible with the Linux driver of the newer kernel in Ubuntu 20.04.x LTS.

---

