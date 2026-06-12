---
title: "armitage database.yml error"
date: 2018-08-25
forum: General Help
---

### Post by funeoz on 2018-08-25
I'm trying to run Armitage but it can't find the database.yml file.

So i redirected MSF_DATABASE_CONFIG to /opt/metasploit-framework/database.yml and added a line at /etc/profile :
```
# export MSF_DATABASE_CONFIG=/opt/metasploit-framework/database.yml
```
But it didn't work.:(

So i tried another thing i redirected MSF_DATABASE_CONFIG to /home/(myusername)/.msf4/database.yml and changed the line at /etc/profile:
```
# export MSF_DATABASE_CONFIG=/home/theo/.msf4/database.yml
```

Didn't work too.

If someone can help me, I will be very pleased.:D

---

### Post by The Cog on 2018-08-25
I know nothing about Armitage but the two lines of code you posted are commented out: the '#' at the front causes them to be ignored. Remove the # and they may do what you are trying yo do.

---

### Post by funeoz on 2018-08-25
I tested but it didn't work.:(

---

