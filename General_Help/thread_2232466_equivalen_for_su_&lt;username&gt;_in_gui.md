---
title: "equivalen for su &lt;username&gt; in gui"
date: 2014-07-02
forum: General Help
---

### Post by Ruud_Uphoff on 2014-07-02
System is Kubuntu 14.04 LTS
This is about logging in as a user without admin rights, thus unable to use sudo or kdesu

From the therminal he can get root rights using
```
 su <username>
```
But I need this to work with superuser access to the gui. Thus superuser access as a different user. Any idea?

CU
Ruud

---

### Post by lisati on 2014-07-02
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by grahammechanical on 2014-07-02
A user set up as a Standard user should not need Administrator privileges. If we can trust the user then we can make the user an Administrator and then sudo will work with their password. In Kubuntu there should be a utility called something like User Accounts (that is the name in Ubuntu 14.04) and if we are the original user who is set up as Administrator we can make any Standard user into an Administrator.

Regards.

---

