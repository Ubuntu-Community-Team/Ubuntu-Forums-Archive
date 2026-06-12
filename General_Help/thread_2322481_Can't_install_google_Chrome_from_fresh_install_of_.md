---
title: "Can't install google Chrome from fresh install of ubuntu 16.04 x64"
date: 2016-04-28
forum: General Help
---

### Post by Hewjr100 on 2016-04-28
See Tilte.

Henry

---

### Post by howefield on 2016-04-28
Presuming that you have downloaded the .deb package from the Chrome website and Software Centre won't install it, is that about it ?

There is an issue with Software Centre not installing local deb packages that is the subject of [this bug]("https://bugs.launchpad.net/ubuntustudio/+bug/1573206") report.

A workaround is to install gdebi, then you can right click the deb package and select open with gdebi which should allow the installation to proceed.

---

### Post by slickymaster on 2016-04-28
Other howefield suggestion, another way to get it would be by command line```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i --force-depends google-chrome-stable_current_amd64.deb
```In case dpkg complains about any missing dependencies just run```
sudo apt-get install -f 
```

---

### Post by Hewjr100 on 2016-04-28
Thanks for your replies. Got it working.

Henry

---

