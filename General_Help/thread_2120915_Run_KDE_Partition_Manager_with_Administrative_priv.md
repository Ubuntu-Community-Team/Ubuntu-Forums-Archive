---
title: "Run KDE Partition Manager with Administrative privileges"
date: 2013-02-27
forum: General Help
---

### Post by daldude on 2013-02-27
How do I run KDE Partition Manager with administrative privileges? Every time I try to run it I get an message from the program   p, li { white-space: pre-wrap; }  Warning: You do not have administrative privileges. 
 It is possible to run KDE Partition Manager without these privileges. You will, however, *not* be allowed to apply operations. 
 Do you want to continue running KDE Partition Manager?


Thanks.

---

### Post by montenik on 2013-03-04
I don't have this program installed, but try opening a terminal and type in:
**sudo partitionmanager**
Then enter the password for your User account. This should run the program with administrative privileges .

---

### Post by whatthefunk on 2013-03-04
> **montenik said:**
> I don't have this program installed, but try opening a terminal and type in:
**sudo partitionmanager**
Then enter the password for your User account. This should run the program with administrative privileges .

You really shouldnt do this.  When running GUI programs in KDE with root privileges you need to use **kdesudo**.

```
kdesudo partitionmanager
```

KDE Partition Manager always asks you for root privileges when it opens, but it needs the KDEsudo package and if you are using Ubuntu you probably dont have it.  You could install it, or use a GTK partition manager like Gparted.

---

