---
title: "sbin/ plymouthd internal error"
date: 2016-01-10
forum: General Help
---

### Post by miner2 on 2016-01-10
This is killing my performance and I have no idea what to do. Has anyone encountered it before? Attached.

---

### Post by miner2 on 2016-01-10
No ideas?

---

### Post by deadflowr on 2016-01-10
Are you sure plymouth is causing the slow down and not the crash reporting system?

Try disabling apport, this is normal thing to try.

Open a terminal and run
```
sudo nano /etc/default/apport
```
change the entry from enabled=1 to enabled=0
then press ctrl +X, then press Y (for yes), then press enter 
which will save and exit back to the terminal prompt.

Then see how performance is.

Bonus: you might also look into disabling plymouth, if you want to try that.
Reference on how to do that here:
[http://askubuntu.com/questions/98566/how-do-deactivate-plymouth-boot-screen](http://askubuntu.com/questions/98566/how-do-deactivate-plymouth-boot-screen)

Hope it helps

---

