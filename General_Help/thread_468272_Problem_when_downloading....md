---
title: "Problem when downloading..."
date: 2007-06-08
forum: General Help
---

### Post by Lufkin on 2007-06-08
When i'm trying to download something with the Add/Remove or the Update Manager, the download stops and a window opens, saying :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What i have to do exactly ? Please, help !

Thank you very much !!! ;)

---

### Post by Shazaam on 2007-06-08
You have un-configured packages. Type this in the terminal=

sudo dpkg --configure -a

You should be good to go.

---

### Post by Lufkin on 2007-06-08
Aaah ! Ok... It's working. Stupid little problem, lool ! (I feel like a noob, maybe because i am. But it is so simple ! lol)

...Anyways, sorry for that, and thank you very much ! :D

---

