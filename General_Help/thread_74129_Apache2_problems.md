---
title: "Apache2 problems"
date: 2005-10-11
forum: General Help
---

### Post by comradevik on 2005-10-11
I installed apache2 and everything worked.. then i rebooted my computer and when i went back online apache wouldnt start .. it said
```
(98 )Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
```

so i did killall apache2 and then sudo /etc/init.d/apache2 start and it said it started it but i go in my browser and type in localhost and it gives me an errorwhen connecting to localhost
i tried reinstalling apache2 and it gave me exactly the same error even with remove --purge apache2 
so then i backed up my data .. dead a clean install of ubuntu again and apache worked but then when i rebooted same thing happened

is there any way i could completly uninstall the apache or fix the problem? 
thanks

---

### Post by comradevik on 2005-10-11
.. i'm using breezy but i didnt find a support forum for breezy since its not released yet

---

### Post by pgmario on 2005-10-14
I "fixed" my apache problem by doing a
```
dpkg -l | grep apache
``` and running 
```
sudo apt-get remove --purge
``` on the results.
Then installed apache2 and php4 again and everything was fine.

---

