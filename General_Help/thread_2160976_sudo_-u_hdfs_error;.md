---
title: "sudo -u hdfs error;"
date: 2013-07-09
forum: General Help
---

### Post by dinoopms on 2013-07-09
installed hive.....command hive working fine.........
while trying it as hdfs user its not working........


$ sudo -u hdfs hive
sudo: hive: command not found

please give solutions!!!

---

### Post by Elfy on 2013-07-09
*Thread moved to **General Help**.*

---

### Post by Habitual on 2013-07-09
```
su - hdfs
``` to switch *to* that user.
```
man sudo
``` for how to run commands as another user.

---

