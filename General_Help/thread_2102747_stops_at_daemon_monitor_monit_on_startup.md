---
title: "stops at daemon monitor monit on startup"
date: 2013-01-08
forum: General Help
---

### Post by frogman222 on 2013-01-08
Hi,

I have a 12.04 version Ubuntu server that has been working fine until today when I rebooted it.  It stalled on start up with a message about monit not having the proper credentials.  I have managed to fix this problem (by editing the monit file and adding allow user-password) and in recovery mode if I start the service manually is works fine (says [OK]) and returns to the prompt.  however, when I reboot the computer it gets to the monit command and stops (it says [OK] on the right. it says...
Starting Daemon monitor monit              [OK]

and then nothing!  does anyone have any idea what might be stopping this from continuing?

Regards

Greg J

---

