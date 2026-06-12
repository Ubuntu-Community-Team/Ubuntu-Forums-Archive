---
title: "Launching Update Manager at a specific time"
date: 2007-07-29
forum: General Help
---

### Post by ant1060 on 2007-07-29
Hi :
I am currently in a place where my internet downloads are limited but free between 11 pm and 6 am.  I want to make Update Manager launch the updates at 11.15 pm every night.  Can someone please help as I cannot find any way to do this despite searching the forums for a long time...
Many thanks.
Ant

---

### Post by luisromangz on 2007-07-29
You can set up tasks starting at specific times using anacron. There are guis, as KCron for example (for KDE of course), or you can use the cli. 

You shouldn't use the update-manager command in the task imho, but the apt-get or aptitude commands for those task.

Hope this help you.

---

### Post by ant1060 on 2007-07-29
Thanks!
I have now scheduled update manager to start at midnight, but how can I make update manager then download the update files without me telling it to INSTALL?  I think cron will just start the update manager and I'll have to give it the manual command afterwards.  If I change PREFERENCES in update manager, then it will presumably start immediately without waiting for midnight!
Thanks for any help.
Ant

---

