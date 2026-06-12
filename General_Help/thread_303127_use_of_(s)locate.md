---
title: "use of (s)locate"
date: 2006-11-19
forum: General Help
---

### Post by coldrick on 2006-11-19
Dumb question: I have a cron task that runs updatedb - with no parameters - regularly from root. However, when I use locate to find something, I never get any files from mounted directories under /media.

Do I have to do something different than just a plain updatedb/ locate to search these volumes?

Regards,
David

---

### Post by DaveBorealis on 2006-11-19
Hello,
You have to change the following in '/etc/updatedb.conf'
```
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs /media"

```
Best regards,
Dave

---

### Post by coldrick on 2006-11-19
Excellent! Thanks and regards,
David

---

