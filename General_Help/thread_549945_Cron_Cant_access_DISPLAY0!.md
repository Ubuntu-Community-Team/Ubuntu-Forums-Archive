---
title: "Cron Cant access DISPLAY:0!"
date: 2007-09-13
forum: General Help
---

### Post by mister_p_1998 on 2007-09-13
Can anyone help with this?
none of my (GUI) cron schedules work anymore.

More Here.
[http://ubuntuforums.org/showthread.php?t=547489&highlight=cron](http://ubuntuforums.org/showthread.php?t=547489&highlight=cron)


Steve

---

### Post by thedarkwinter on 2007-09-14
Hi

If you are running the cron jobs as root that may be the problem. Try running the cron jobs as your user (the same that is logged in gui).

Cheers,
tdw

---

