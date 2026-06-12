---
title: "How to recover from home directory corruption?"
date: 2007-06-15
forum: General Help
---

### Post by sling-shot on 2007-06-15
While installing PCLinuxOS on my PC I gave a user name the same as my default Ubuntu user name. Now PCLinuxOS went ahead and created its own user under that name while corrupting things for Ubuntu so much so that I cant login to my primary Ubuntu user account. (Unfortunately it is the only one!) I have a common home partition for all Linux distros.
If I reinstall Ubuntu, it will remove all the stuff I already downloaded (since am on dial-up I hate to do that, will take weeks) further it might format the whole home partition and cause considerable grief to other distros.
A similar situation in PCLinuxOS was easily remedied by logging in as root and deleting/recreating a new account. However this cant be done in Ubuntu because I cant login to my primary account and recovery console/startx to get to user accounts says i dont have permission. Further I cant enable root account because GDM is not running. I am stuck in a catch-22 situation.
Thanks for any help particularly in recreating the primary user's home partition from command line.
-SS.

---

### Post by dreadlord_chris on 2007-06-15
log into the *Ubuntu* Recovery Console:
```

chown -hR UNAME:UNAME /home/UNAME

```
Replace UNAME with your user name. This will reset the owner/group for your Ubuntu install. I think the problem probably stems from PCLinuxOS giving the user a different UID even though the names were the same. Since it's the UID that the OS 'understands', while the name is basically just for us humans, you effectivly have 2 different users trying to share the same home.

---

### Post by sling-shot on 2007-06-16
[dreadlord_chris]

Thanks a lot :-) it simply worked!
-SS.

---

