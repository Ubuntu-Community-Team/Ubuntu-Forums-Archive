---
title: "Ubuntu 12.04 won't initiate user session"
date: 2012-10-29
forum: General Help
---

### Post by gopaleen on 2012-10-29
Hi,

I'm running Ubuntu 12.04 and after I ran the latest updates my Ubuntu is stuck on the login screen. It just says "initiating user session" but nothing happens. It doesn't freeze it (I can click on the panel) it  just doesn't load.

Last night I added the following repository [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)  ( for Samsung printer drivers) but I'm not sure if that's relevant.

Any help would be appreciated. Thanks!

---

### Post by dino99 on 2012-10-29
can you create an other user account for testing ?

---

### Post by netopalis45 on 2012-10-29
Before you try logging in hit Ctrl+Alt+F1 to change to tty1. Use your normal username and password to log in. Remove the repository by going through your history and using the same command you used to add it except with a ```
-r
``` before the repository name. Reboot and try logging in again. If it works it was a problem with the repository, if not there may be a problem with the user session.

---

