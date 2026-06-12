---
title: "[solved]Why su command fails?"
date: 2014-08-25
forum: General Help
---

### Post by Jahidul_Hamid on 2014-08-25
why su command fails with my admin password. It says authentication failure...

---

### Post by slickymaster on 2014-08-25
**su** asks for the root password. Since ubuntu doesn't use a root account, you normally do not have this password set. 

Instead, use sudo to run a command as root:```
sudo command...
```
If you want a root shell like you get with su, run:```
sudo -s
```

---

### Post by sotiris2 on 2014-08-25
```
su
```
Requires the ROOT user password which is not even set in Ubuntu. If you want to get a root terminal do ```
sudo su
``` and type your password.

---

### Post by Jahidul_Hamid on 2014-08-25
marking thread as solved...

---

### Post by lisati on 2014-08-25
> **Jahidul_Hamid said:**
> marking thread as solved...

Please use the "Thread tools" drop-down menu to do so.

---

