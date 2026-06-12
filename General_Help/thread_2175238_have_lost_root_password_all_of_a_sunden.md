---
title: "have lost root password all of a sunden"
date: 2013-09-18
forum: General Help
---

### Post by unixisit on 2013-09-18
Do no longer have su password is there a way to restore it? with out  having to totaly restore the hole system. I am running UBUNTU 13.04 with the 3.8.0-30 generic kernel

---

### Post by coffeecat on 2013-09-18
Ubuntu does not have a (usable) root password by default. Did you enable the root account yourself and set a root password? Whether or not you did, you need to read through this, which details the drawbacks of enabling the root account:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It describes enabling the root account as "rarely necessary". Personally, I'd go further and say unnecessary, at least for desktop installations.

---

### Post by jamesisin on 2013-09-18
Yeah, as coffeecat suggests, you should have no need to ever su to root.  By default that's not even possible.  Use sudo instead.  That being said, you should be able to use sudo to change the root password.

---

### Post by grahammechanical on 2013-09-18
Have you lost the password? Or have you noticed that gksu is not installed by default in Ubuntu 13.04?

---

### Post by jamesisin on 2013-09-18
grahammechanical - This is from a fresh install of 13.04 32 bit:

```
$ which gksu
/usr/bin/gksu
```

---

