---
title: "Update Manager, but when?"
date: 2005-04-01
forum: General Help
---

### Post by NVRO on 2005-04-01
Hello,
I have set Update Manager to check for updates once a day. But where do I set the time for the updates?

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=NVRO]Hello,
I have set Update Manager to check for updates once a day. But where do I set the time for the updates?[/QUOTE]
 the time of all your daily jobs is specified in in your /etc/crontab

you can edit this file. The standard setting is nice if your pc is permanent on because it's doing it in the middle of the night. If your pc isn't on at that time it will do it the next day somewhere after booting up.

---

