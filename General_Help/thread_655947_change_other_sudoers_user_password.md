---
title: "change other sudoers user password"
date: 2008-01-02
forum: General Help
---

### Post by nsr79 on 2008-01-02
My colleague forgot his sudo password to our Ubuntu server, and his user user has sudoers/admin privillege (not Root). How to reset or change his password from my user or Root?

Please help immediately.

---

### Post by aysiu on 2008-01-02
```
sudo passwd *username*
``` should do it.

---

### Post by p_quarles on 2008-01-02
> **nsr79 said:**
> My colleague forgot his sudo password to our Ubuntu server, and his user user has sudoers/admin privillege (not Root). How to reset or change his password from my user or Root?

Please help immediately.
Login as your user, and run the following:
```
sudo passwd *colleague's-username*
```Enter the new password twice, and you're set. :)

---

### Post by Furat on 2008-01-02
```
 sudo su -
```
now you are the root 
```
passwd username 
```
when usernmae is the user you want to change its password 
and I think If you use the below command will work too
```
sudo passwd username
```

---

