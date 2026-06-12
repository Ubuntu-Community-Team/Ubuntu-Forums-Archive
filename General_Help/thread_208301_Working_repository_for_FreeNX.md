---
title: "Working repository for FreeNX?"
date: 2006-07-03
forum: General Help
---

### Post by nameiwantistaken on 2006-07-03
I've tried going through the HOWTO for FreeNX but after adding in the new repositories and doing an update, apt-get errors when I try to get anything related to FreeNX.  It gives a 403 error and says that access is forbidden.  Also, when I try downloading the gpg key it says that there are no trusted keys found.  Anyone isntalled this recently?  Ideas?

---

### Post by Jagot on 2006-07-03
Check the 'Installing the FreeNX server' section here:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by nameiwantistaken on 2006-07-03
Thanks for the quick response.  The page has a dead link in it for the packages.  Are there any other ways of getting this?

---

### Post by jay_cee on 2006-07-03
[http://www.ubuntuforums.org/showthread.php?t=204976&highlight=nxserver](http://www.ubuntuforums.org/showthread.php?t=204976&highlight=nxserver)

See the 2nd post in this thread. I went through it yesterday and didn't have any real problems. Remember to install openssh.

---

### Post by QUASAR_FREAK on 2006-07-03
When i installed, i used this repo:
deb [http://free.linux.hp.com/~brett/seveas/freenx/]("http://free.linux.hp.com/%7Ebrett/seveas/freenx/") breezy-seveas freenx

---

### Post by Jagot on 2006-07-03
[QUOTE=nameiwantistaken]Thanks for the quick response.  The page has a dead link in it for the packages.  Are there any other ways of getting this?[/QUOTE]

Oops.  Add these lines to your /etc/apt/sources.list:

```
deb http://free.linux.hp.com/~brett/seveas/freenx dapper-seveas freenx
deb-src http://free.linux.hp.com/~brett/seveas/freenx dapper-seveas freenx
```

---

