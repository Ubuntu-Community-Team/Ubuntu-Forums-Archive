---
title: "Cannot login from lock screen"
date: 2015-06-11
forum: General Help
---

### Post by Stvn66 on 2015-06-11
On a new 14.04 setup I am having an issue where I cannot login from  the lock screen.  When my screen locks, the only way I can login is by  selecting to login as a different user, which takes me back to the main  login page, then login as myself.  I can also login to one of the shells  available using Ctrl+F# but this does not help me get back to my workspace.

I also tried creating another account and verified it has the same problem.

Following [this]("http://ubuntuforums.org/showthread.php?t=1006366") post, I verified the user and group settings/permissions using the following with no change.  
```
sudo chown root:shadow /etc/gshadow
sudo chown root:shadow /etc/gshadow-
sudo chown root:shadow /etc/shadow
sudo chown root:shadow /etc/shadow-
sudo chown root:shadow /sbin/unix_chkpwd 
sudo chmod 2755 /sbin/unix_chkpwd

```

---

