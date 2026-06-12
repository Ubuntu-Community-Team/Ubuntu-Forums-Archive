---
title: "missing applications"
date: 2005-10-19
forum: General Help
---

### Post by belred on 2005-10-19
we just upgraded one of our boxes from hoary to breezy.   this is our sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

we executed:

sudo apt-get ugrade
sudo apt-get dist-upgrade

after the upgrade, the kernel upgraded to 2.6.12.9 and kde went to 3.4.3.  but no other apps got installed.  no usplash, no openoffice2, no adept, so systemsettings, etc.

i've tried upgrade and dist-upgrade several times from the US and global repositories several times with no luck.   if i go into kynaptic, i can see all the apps and i've even installed adept successfully. so there doesn't seem to be any dependency problems.

so my question is what do i have to do to get all the missing breezy applications and features?

thanks,

bryan

---

### Post by Aikurn on 2005-10-19
Do you have the kubuntu-desktop package installed?

---

### Post by aysiu on 2005-10-19
[QUOTE=belred]we just upgraded one of our boxes from hoary to breezy.   this is our sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse[/QUOTE] Is this your entire sources.list? Try following these instructions

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

Also, check to see that you installed kubuntu-desktop

---

