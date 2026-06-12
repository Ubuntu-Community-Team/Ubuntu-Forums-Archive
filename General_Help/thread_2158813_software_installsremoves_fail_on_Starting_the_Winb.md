---
title: "software installs/removes fail on Starting the Winbind daemon winbind"
date: 2013-06-30
forum: General Help
---

### Post by JimTheSailor on 2013-06-30
I have tried to install then remove several software applications but they all (installs & removes) have failed in the same way. I have attempted to remove Wine and am pasting the end of the failure details below. The details on the others are the same.
Thanks for any help you may give me.
Jim


dconfig deferred processing now taking place 
Processing triggers for python-support ... 
Setting up winbind (2:3.4.7~dfsg-1ubuntu3.10) ... 
 * Starting the Winbind daemon winbind 
   ...fail! 
invoke-rc.d: initscript winbind, action "start" failed. 
dpkg: error processing winbind (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 winbind 
Setting up winbind (2:3.4.7~dfsg-1ubuntu3.10) ... 
 * Starting the Winbind daemon winbind 
   ...fail! 
invoke-rc.d: initscript winbind, action "start" failed. 
dpkg: error processing winbind (--configure): 
 subprocess installed post-installation script returned error exit status 1

---

### Post by JimTheSailor on 2013-06-30
I was able to uninstall winbind which has resolved the problem.
Thanks

---

