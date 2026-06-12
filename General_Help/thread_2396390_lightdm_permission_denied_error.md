---
title: "lightdm permission denied error"
date: 2018-07-14
forum: General Help
---

### Post by moppa007 on 2018-07-14
I am running 18.04 (64bit) and after an upgrade from 17.10 I could not login to my desktop. After learning some basics, I have found a ‘Permission denied’ error after running: $ lightdm —test-mode —debug. The specific output is 
DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0 /bin/rm: cannot remove ‘/var/lib/lightdm-data/lightdm’ : Permission denied. 


After this the X server process is terminated and the X server is stopped and the Display manager goes down. 


Anyone seen this who can help?

---

### Post by steeldriver on 2018-07-15
I'm not really surprised - I would expect only root can do that?

---

