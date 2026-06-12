---
title: "Other users can't login after upgrade"
date: 2022-12-30
forum: General Help
---

### Post by phillwright on 2022-12-30
I just upgraded a computer to Ubuntu Budgie 22.04. It most recently had probably Ubuntu 22.04, and before that, it had an older Ubuntu Budgie version.

My hard drives are partitioned with a separate /home partition that does not get formatted during install. I've done this for years, and after install, created other users for my family. Normally (I've done this quite a few times, on this and other systems), everyone can access their home folder.

After installing, my admin account can login ok, and I have access to my home folder. Everyone else's home folder is present. I add the other users normally, and log out. When I try to log in as another user, the screen goes blank, and then the login screen returns, without any error (such as bad password).

Any suggestions?

---

### Post by MAFoElffen on 2022-12-31
Try resetting the /home/user_name/.Xauthority file to be owned by that user, with permission of 600.

---

