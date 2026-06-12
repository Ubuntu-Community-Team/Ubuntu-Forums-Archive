---
title: "unknown users"
date: 2007-10-12
forum: General Help
---

### Post by BDNiner on 2007-10-12
When i check the system monitor there are some processes that have users other than the ones setup on my computer. I figured that they belonged to the system processes but how do i administer those users. for example the printing process cupsd lists its user as cupsys. and all the apache processes have apache-ssl as their user.

---

### Post by thirddeep on 2007-10-12
How do you want to "administer" those users ?  They are specific users for specific applications.

To see a list of all users on your system:
```
cat /etc/passwd
```

Note that for example cupsys has /bin/false at the end.  It means that user can not log on.

Thd.

---

