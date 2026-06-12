---
title: "REQUEST - I need latest sources.list for 18.04LTS"
date: 2020-04-30
forum: General Help
---

### Post by pegasusp on 2020-04-30
when i run [FONT=Consolas]sudo apt-get install update && sudo apt-get install upgrade i am getting these errors:[/FONT]

E: Unable to locate package update
E: Unable to locate package upgrade 

i'll be really happy if someone help to fix it :)

---

### Post by slickymaster on 2020-04-30
Check this thread, please: [https://askubuntu.com/questions/388541/e-unable-to-locate-package-update-when-i-try-to-update-my-system-why](https://askubuntu.com/questions/388541/e-unable-to-locate-package-update-when-i-try-to-update-my-system-why)

---

### Post by dino99 on 2020-04-30
Here is mine:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-proposed multiverse restricted universe main


---

### Post by deadflowr on 2020-04-30
You sources aren't the problem.
The issue is you are trying to install packages called update and upgrade which don't exist.
remove install from the commands.

---

### Post by ActionParsnip on 2020-04-30
From the original post

```

sudo apt-get install upgrade

```

"upgrade" isn't a package in Ubuntu. If you run:

```

sudo apt-get upgrade
sudo apt-get dist-upgrade

```

It will install the upgrades

---

