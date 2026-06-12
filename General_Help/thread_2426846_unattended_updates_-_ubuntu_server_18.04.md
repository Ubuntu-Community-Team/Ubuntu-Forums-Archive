---
title: "unattended updates - ubuntu server 18.04"
date: 2019-09-14
forum: General Help
---

### Post by doktor2 on 2019-09-14
Hi,

I would like to update ubuntu 18.04 on boot without login(restart if needed), if there are no updates wait for a minute then shutdown.

go ;)

---

### Post by TheFu on 2019-09-14
Google found this: [https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html)
Don't know if it meets your needs or not.

I've had issues where an update of packages made a server stop performing the primary purpose for that server. I would warn to be extremely cautious doing this plan.  It took me about 4 hrs to recover from the automated update. 

 I would have been better off just restoring from the backups the day prior than trying to figure out what happened, undoing it, and putting back the packages which the dependencies decided to swap for the packages I had installed.  Restoring a system from backups, once I begin, takes 30-45 min.  Alas, it was a project management server and some of the PMs were probably up all night managing their projects.

---

### Post by doktor2 on 2019-09-14
thanks

---

