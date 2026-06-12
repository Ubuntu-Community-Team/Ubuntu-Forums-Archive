---
title: "Bluetooth &quot;deactivates&quot; after long idle time"
date: 2007-12-25
forum: General Help
---

### Post by |Porsche on 2007-12-25
Hey all,
Evey time I come back to my computer I have to issue an ```
/etc/init.d/bluetooth restart
``` for all my devices to become active. Is there a way to keep them alive while I am gone. 

Any help is welcome. 
Ubuntu 7.10

---

### Post by |Porsche on 2007-12-31
I solved the problem by adding the following to root's crontab ```
1,31 * * * * /etc/init.d/bluetooth restart
```

```
sudo bash
gedit crontab
```
add ```
1,31 * * * * /etc/init.d/bluetooth restart
``` to the file
save and close.

This will restart the bluetooth deamon every hour on 1 and 31 minutes of every day of every year of every century. 
I hope this helps someone.

---

