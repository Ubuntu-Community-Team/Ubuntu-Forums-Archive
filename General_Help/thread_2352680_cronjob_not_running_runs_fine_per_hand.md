---
title: "cronjob not running/ runs fine per hand"
date: 2017-02-14
forum: General Help
---

### Post by alexander15454 on 2017-02-14
Hey guys.


So im trying to run a python script every minute over a cronjob, but for some reasons it wont run, it pops up in the process list for a second but disappears then. The script runs fine if i executed it manually.


The command:


    ```
python wifi.py 
```


This is what i placed in crontab -e :


    ```
* * * * * /usr/bin/python /root/wifi.py 
```


Hopefully someone can help me out with this :)

---

### Post by SeijiSensei on 2017-02-14
Is that in root's crontab, one created using "sudo crontab -e"?  Root's home directory, /root, is only readable by the root user since it has default permissions of 700.  If you're running this command from an ordinary user's crontab, it is likely failing because of permissions.

---

### Post by alexander15454 on 2017-02-15
Yep its done over root, thats not the issue, other things which need root permissions are also running fine.

---

### Post by SeijiSensei on 2017-02-15
What entries do you see in /var/log/syslog when cron tries to run this process?

---

