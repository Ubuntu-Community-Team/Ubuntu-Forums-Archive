---
title: "Going mad trying to install alien"
date: 2006-12-11
forum: General Help
---

### Post by glendavee on 2006-12-11
There's got to be a better way!!
I'm trying to install alien in order to convert files to .deb.
I download alien, try to install and get dependency message telling  me I need debhelper. I get debhelper and try to install, get message telling me I need dpkg-dev. Get that, install it, retry debhelper, message tells me I need html2text. Get that, install it, and retry debhelper -it installs. Then retry to install alien - get message need rpm. Get rpm, try to install it, get message I need libbeecrypt6. I don't have internet access on my ubuntu system, so have to switch to Windows each time I need to access the internet, so I have given up for the moment. Question is - there must be a better way to do this, to get all dependencies in one go - if so, how do I do this??

---

### Post by wpshooter on 2006-12-11
Search for (by name) and find this software in Synaptic and then install it from there.  I believe it will either install or warning you of all these various dependencies that also need to be installed.

---

### Post by taurus on 2006-12-11
```
sudo aptitude update
sudo aptitude install alien
```

[http://packages.ubuntu.com/edgy/admin/alien](http://packages.ubuntu.com/edgy/admin/alien)

---

### Post by glendavee on 2006-12-11
Will this work without internet access??

---

### Post by PrinceArithon on 2006-12-11
The sudo aptitude stuff will not work without the internet, because you have to download it.  Neither will it work in the synaptic manager, because again you have to download it.

---

### Post by taurus on 2006-12-11
The link will tell you what you need so just download everything from that list and transfer them to your computer...

---

