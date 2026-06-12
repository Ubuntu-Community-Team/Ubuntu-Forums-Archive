---
title: "[SOLVED] How do I configure my server to email me under certain circumstances?"
date: 2007-06-11
forum: General Help
---

### Post by blueturtl on 2007-06-11
This is to all you Linux-guru sysadmin types out there:

I recently had to reconfigure a file server for my mother-in-law. The system runs Debian and Samba so I knew my way around mostly and it was succesfully brought back online. The server's purpose is to provide a network storage for all the laptops in the household with limited hard-disk capacity. It also allows easy sharing of photos etc.

Anyway, the server has 160 gigabyte hard-disk in it. While nowhere near full, I would like to arrange it so that the server would email me when the storage drive fills up to about 80% so that in the future I can take the appropriate measures before the system starts spitting "disk full" errors at the users. Since I mostly run Linux on the desktop this kind of thing is new to me.

How do I configure the system to send me an email when the drive is filling up?

---

### Post by disposable on 2007-06-11
```
#!/bin/bash

DRV=/dev/sda1
MAX=80

USE=$(df -h | grep $DRV | awk '{print $5}' | sed 's/%$//')

if [ $USE -gt $MAX ]; then
        echo "Check disk..." | mail -s "Disk at $MAX%!" user@host     
fi
```

Run it as a cron job, and of course, change as appropriate. It should get you started. Good luck with your job..er, mother-in-law. :p

---

