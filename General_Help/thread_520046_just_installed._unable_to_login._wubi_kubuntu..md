---
title: "just installed. unable to login. wubi kubuntu."
date: 2007-08-07
forum: General Help
---

### Post by cp3rap on 2007-08-07
i just intalled kubuntu using wubi on an nfts partition. everything installed clean and seems to work fine. when i go to login however i am unable to. it responds wrong username or password. but i use the same password and username for everything. is there a way to bypass or reset this login information?

---

### Post by Aesir09 on 2007-08-07
try pressing ctrl+alt+F1 or 2 3 4 5 
this logs you into a terminal
sorry dude idk

---

### Post by bodhi.zazen on 2007-08-07
Boot to recovery mode. This will log you on as root, CLI

enter : ```
nano /etc/shadow
```

Confirm user name ... don't forget Linux is CASE SENSATIVE

then reset the password with :```
passwd <user_name>
```Substitude the appropriate user name ....

Reboot ...

*Note I do not think you can use ntfs as the file system for ubuntu, so if you did not format the root partition as ext3 or a linux native alternate you will need to re-install ...

---

