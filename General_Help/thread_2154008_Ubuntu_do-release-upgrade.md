---
title: "Ubuntu do-release-upgrade"
date: 2013-06-13
forum: General Help
---

### Post by GordonCopestake on 2013-06-13
I have been getting a notification that there is a new release for some time and today got around to attempting to apply it.

However i'm getting conflicting messages. Can someone point me in the right direction?

```
login as: administrator
administrator@192.168.51.80's password:
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-37-generic i686)

 * Documentation:  https://help.ubuntu.com/

New release '12.10' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Thu Jun 13 10:08:51 2013 from 192.168.51.72
administrator@wiki:~$ sudo do-release-upgrade
[sudo] password for administrator:
Checking for a new Ubuntu release
No new release found
administrator@wiki:~$

```

apt-get update and apt-get upgrade both work fine and the machine has internet access without issue.

---

### Post by fantab on 2013-06-13
Edit your update/upgrade notifications from'Software Center' -> Edit -> Software Sources -> Updates, at the bottom you will find a dropdown menu for 'Notify me of a new Ubuntu version', choose "for long-term support versions". And you will not be bothered with those upgrade notifications. That is, if you don't want to upgrade and don't want those notifications either.

---

### Post by GordonCopestake on 2013-06-13
Ahhhhhhh, it's the LTS thing that was confusing me. I guess there will be a release 13.10 that will suit this box

Thanks fantab

---

### Post by slickymaster on 2013-06-13
_If you really want to update from a LTS version to a non-LTS one_, you have to check your **/etc/update-manager/release-upgrades** file. The Prompt parameter should equal normal.
To change it, run the following:```
gksudo geany /etc/update-manager/release-upgrades
```and edit the line```
Prompt=lts
```to```
Prompt=normal
```.
After that you can run```
do-release-upgrade
```but keep in mind that you'll be updating to a non-LTS version of Ubuntu.

---

