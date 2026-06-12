---
title: "webmin shorewall trouble"
date: 2004-10-29
forum: General Help
---

### Post by cacofonix on 2004-10-29
I installed the webmin config for shorewall and I cant log in. I put in my username and password and I get an authentication message and after 3 attempts it bans the ip until I log in again, has anyone been able to get it to work?

---

### Post by flygmaskin on 2004-10-29
You need to activate the root account before installing webmin.

1.) Uninstall webmin
2.) Set a root password ```
$ sudo passwd root
```
3.) Install webmin again

---

### Post by cacofonix on 2004-10-29
Thanks for your help fly:D

---

