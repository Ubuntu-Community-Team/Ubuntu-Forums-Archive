---
title: "K9Copy Beta Installation"
date: 2006-07-20
forum: General Help
---

### Post by J0s3ph on 2006-07-20
Hi there

I have a bit of a problem with installing the latest K9Copy beta DEB. I've been following the instructions at [https://help.ubuntu.com/community/K9Copy]("https://help.ubuntu.com/community/K9Copy").

So far I've performed...

```
wget http://thepiratecove.org/files/k9copy-1.1.0-beta1_i386.deb
sudo dpkg -i k9copy-1.1.0-beta1_i386.deb
sudo ln -s /usr/local/kde/bin/k9copy /usr/local/bin/k9copy
```

When I try and run it from the shell I get...

```
error while loading shared libraries: libkparts.so.2: cannot open shared object file: No such file or directory
```

From what I understand libkparts.so.2 is part of KDE. Do I need to install a perticular package to get this library?

---

### Post by The Mekon on 2006-07-20
The following [link]("http://abowman.com/2006/07/18/scratch-copies-of-your-dvds/") from another thread may be of use

---

### Post by J0s3ph on 2006-07-21
kdelibs4-dev is the one. Thanks for your help The Mekon.

---

