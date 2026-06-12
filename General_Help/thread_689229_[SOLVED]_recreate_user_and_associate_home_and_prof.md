---
title: "[SOLVED] recreate user and associate home and profile"
date: 2008-02-06
forum: General Help
---

### Post by rickyble on 2008-02-06
I moved a user home directory and it didnt go well.  Thru various actions I deleted the user and was trying to recreate it and associate the old  home directory with the new user of the same name.  I have keep the entire home directory but the new user even with the same user id will not use or associate with the home directory.  Any help at all will be appreciated.  All my mail and directories and desktop setting are associated with the original deleted user.

---

### Post by rickyble on 2008-02-06
I got it. I recreated the original user.  Change the UID to the original users id.  I chown the entire home directory and subdirectorires for that user. I chrg the entire home directory and subdirectories too.  I edited the etc\password and etc\password- files to redirect the users home and changed the userid there too.  I worked.

---

