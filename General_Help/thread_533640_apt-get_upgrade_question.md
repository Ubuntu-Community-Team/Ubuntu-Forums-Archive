---
title: "apt-get upgrade question"
date: 2007-08-24
forum: General Help
---

### Post by Bernd Nowak on 2007-08-24
Since a few days apt-get upgrade displays this:

> 
name@host:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  gnupg
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


I don't think this is correct but how can I solve/force gnupg to be installed or what can I do ?

System is Feisty.

---

### Post by sharke on 2007-08-24
> **Bernd Nowak said:**
> Since a few days apt-get upgrade displays this:



I don't think this is correct but how can I solve/force gnupg to be installed or what can I do ?

System is Feisty.
Have you updated the source
sudo apt-get update
then
sudo apt-get dist-upgrade
Dont worry about held back pachages you shoud not need them.
Regards
Sharke

---

### Post by Seisen on 2007-08-24
Sometimes they have problems with certain packages that they have uploaded to the repositories so they hold them back so thier isn't  a major problem. This happened before with kernel update, I believe it was with Edgy. Its really no big deal just give it a couple of days.

---

### Post by Bernd Nowak on 2007-08-24
> **sharke said:**
> Have you updated the source
sudo apt-get update
then
sudo apt-get dist-upgrade
Dont worry about held back pachages you shoud not need them.
Regards
Sharke

This did the trick but how on earth should I know this :D

So what is the difference between:

sudo apt-get dist-upgrade
and
sudo apt-get upgrade

I ask because I have not done a Distro Update recently :D

---

### Post by sharke on 2007-08-24
> **Bernd Nowak said:**
> This did the trick but how on earth should I know this :D

So what is the difference between:

sudo apt-get dist-upgrade
and
sudo apt-get upgrade

I ask because I have not done a Distro Update recently :D
apt-get update refreshes the /etc/apt/sources.list with the latest updates in the ubuntu repo.
apt-get upgrade will install the latest updates.
apt-get dist-update is used to do a upgrade to the latest ubuntu release if you have chaged your sources file to match the latest if not it is the same as apt-get upgrade.
Regards
Sharke
Ps 
take a look at the ubuntu wiki most commands are explained

---

### Post by Seisen on 2007-08-24
Doing apt-get dist-upgrade like that can mess your system up, so watch using for packages that are being held back, they do that for a reason.

---

### Post by por100pre1 on 2007-08-24
> **Seisen said:**
> Doing apt-get dist-upgrade like that can mess your system up, so watch using for packages that are being held back, they do that for a reason.

That's right. The best way would be to check the package with Synaptic to see which changes are required by that package update. :)

---

### Post by Bernd Nowak on 2007-08-24
To late now but maybe a little help text why a package isn't updated would help then ?
And by the way it's the server installation and I checked the logs but could not find any explenation why the gnupg was hold back. :)

---

### Post by IcemanV9 on 2007-08-24
FWIW, there is a security notice on [gnupg]("http://www.ubuntu.com/usn/usn-432-1") (back in March 2007). And, you just installed server edition of Ubuntu, right? If so, maybe it has been fixed and the gnupg security patch is no longer needed? OR, it is a new one, but in a testing/qa mode. Just sit tight for a few days, then you'll know soon enough when they announce in the security news.

---

