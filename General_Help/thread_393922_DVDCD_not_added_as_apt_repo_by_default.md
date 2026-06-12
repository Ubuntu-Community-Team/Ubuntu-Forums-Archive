---
title: "DVD/CD not added as apt repo by default"
date: 2007-03-26
forum: General Help
---

### Post by OsireS on 2007-03-26
Hi

Just wanted to know why the CD/DVD that is installed from is not added as a default repo to apt after installation. I found today the Feisty would not enable restricted drivers and after a little digging around it was because the DVD had not been added as a repo and the nvidia-glx package could not be picked up (even though some already installed packages referenced it).

Is this by design? Just asking as a number of times I've had this issue is quite straggering, especially when the computer by default is not on a network.

---

### Post by taurus on 2007-03-26
Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
```

---

### Post by OsireS on 2007-03-27
Hi

I know exactly how to do it .. been using Ubuntu since back in the day. My question was more general as I know a lot of schools in South Africa (and really anywhere with limited internet connectivity) use it and they might not necessarily have internet access straight away after install. 

Now a lot of the packages (nvidia-glx for example) are available on the CD/DVD but when its not added by default they cannot be installed, users need to go through an extra step and at worse it breaks things like the Restricted drivers panel (as I discovered 2 days ago) because apt-get knows the package exists as its referenced but doesn't actually have the package on hand as there is no internet and the CD/DVD used for install hasn't been scanned.

Just an observation ...

---

