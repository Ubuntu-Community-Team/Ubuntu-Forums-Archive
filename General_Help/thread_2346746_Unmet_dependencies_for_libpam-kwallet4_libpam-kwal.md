---
title: "Unmet dependencies for libpam-kwallet4 libpam-kwallet5..."
date: 2016-12-18
forum: General Help
---

### Post by orange2k on 2016-12-18
Recently I installed Kubuntu 16.10 but after updating the system and adding the backports repository I have 2 packages that can't be installed because of unmet dependencies...

These are: libpam-kwallet4 libpam-kwallet5

How do I solve this?

edit: sorry for this double post, I posted this because I didn't see the other thread being posted in the installations and upgrade category...

---

### Post by Bashing-om on 2016-12-18
orange2k; Hey ...

Show us what you are seeing;
Post back the outputs - between code tags - of terminal commands :
```

sudo apt update
sudo apt upgrade
apt-cache policy libpam-kwallet4 libpam-kwallet5

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Such that we see what the package manger is wanting for guidance to accomplish your desires .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by orange2k on 2016-12-19
Here we go: (note that I have a croatian version of Kubuntu)

```
&#268;itanje popisa paketa... Završeno
Izgradnja stabla zavisnosti       
&#268;itanje informacija stanja... Završeno
2 paketa se mogu nadograditi. Pokrenite 'apt list --upgradable' kako bi ih vidjeli.
orange@kryptos:~$ sudo apt upgrade
&#268;itanje popisa paketa... Završeno
Izgradnja stabla zavisnosti        
&#268;itanje informacija stanja... Završeno
Izra&#269;unavanje nadogradnje... Završeno
Sljede&#263;i paketi su zadržani:
  libpam-kwallet4 libpam-kwallet5
0 nadogra&#273;enih, 0 novo instaliranih, 0 za uklanjanje i 2 bez nadogradnje.
orange@kryptos:~$ apt-cache policy libpam-kwallet4 libpam-kwallet5
libpam-kwallet4:
  Instalirano: 4:5.7.5-0ubuntu1
  Kandidat:    4:5.8.4-0ubuntu1~ubuntu16.10~ppa1
  Tablica ina&#269;ice:
     4:5.8.4-0ubuntu1~ubuntu16.10~ppa1 500
        500 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu yakkety/main amd64 Packages
 *** 4:5.7.5-0ubuntu1 500
        500 http://hr.archive.ubuntu.com/ubuntu yakkety/universe amd64 Packages
        100 /var/lib/dpkg/status
libpam-kwallet5:
  Instalirano: 4:5.7.5-0ubuntu1
  Kandidat:    4:5.8.4-0ubuntu1~ubuntu16.10~ppa1
  Tablica ina&#269;ice:
     4:5.8.4-0ubuntu1~ubuntu16.10~ppa1 500
        500 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu yakkety/main amd64 Packages
 *** 4:5.7.5-0ubuntu1 500
        500 http://hr.archive.ubuntu.com/ubuntu yakkety/universe amd64 Packages
        100 /var/lib/dpkg/status
orange@kryptos:~$ 

```

---

### Post by ian-weisser on 2016-12-19
The easiest way to resolve this *version conflict* is by disabling the PPA.
The PPA Author has not made those updated versions compatible with your current packages.

---

