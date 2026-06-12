---
title: "Installing Wine"
date: 2007-03-07
forum: General Help
---

### Post by lacroserocks on 2007-03-07
I have switched from windows to linux just a few days ago and have been figuring things out, but one thing I havnt been able to figure out, is installing Wine.

I follow the guide on the website, but when i get to 
```
apt-get build-dep wine
```

it replies this:

```
eric@eric-desktop:~$ apt-get build-dep wine
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

have been searching around for anyone else having this problem and havnt found anything.

Anyone have an answer?

---

### Post by wigglydiggly on 2007-03-07
use 
sudo apt-get 

stands for "superuser do" some commands need admin (root) access.

When it asks for a password, use yours.  Basically its granting you root access and making sure you really want to run that command.

---

