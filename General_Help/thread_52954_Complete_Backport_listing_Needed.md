---
title: "Complete Backport listing Needed"
date: 2005-07-29
forum: General Help
---

### Post by diffuser78 on 2005-07-29
Hey,

I need a complete list of backports. I want to update my 

etc/apt/sources.list

with most recent and updated list of repositories/backports.

Could somebody attach the file,

Dan

---

### Post by JPatrick on 2005-07-29
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by diffuser78 on 2005-07-29
[QUOTE=JPatrick][http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)[/QUOTE]

Is it the most updated one because I couldnt update firefox to 1.0.6. 

At my laptop It did thats why I am wondering is it the backport issue or what ?

Dan

---

### Post by ephman on 2005-07-29
this is what i've been using and i've updated my firefox to 1.06


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-backports main universe multiverse restricted
deb [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/) hoary-extras main universe multiverse restricted


see yah,
ephman

---

### Post by SymGeosis on 2005-07-29
diffuser78, yes it's the "most updated."

If you're having problems with upgrading Firefox you may need to do a:
```
apt-get dist-upgrade
``` I know I've had to do that before to upgrade to Firefox.

---

