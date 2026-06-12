---
title: "where to get source code of iwlist&amp;iwconfig?"
date: 2008-03-17
forum: General Help
---

### Post by lewang on 2008-03-17
I tried the below commands, but it can not find the source code.

sudo apt-get build-depiwlist
sudo apt-get source iwlist

Where can I find the source codes?
Thanks in advance.

BR,
Le

---

### Post by nick_h on 2008-03-17
If you run the command:
```
dpkg -S /sbin/iwlist
```
you will find that it is in the package wireless-tools.  Download the source with:
```
sudo apt-get source wireless-tools
```

---

### Post by lewang on 2008-03-17
Thank you very much.

---

