---
title: "Software Sources"
date: 2012-11-29
forum: General Help
---

### Post by raven2099 on 2012-11-29
Are there more or alternative open-sourced/free Software Sources/Packages/Archives i can link to?
and how?


sorry if i'm posting in the wrong area(s)

---

### Post by ibjsb4 on 2012-11-29
There are two that can be enabled from software sources.

 Canonical's 'partner' repository.
This software is not part of Ubuntu, but is offered by Canonical and the
respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

Ubuntu's 'extras' repository.
This software is not part of Ubuntu, but is offered by third-party
developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

Just have to check the boxes.

[ATTACH]227928[/ATTACH]

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

---

### Post by Uncle Spellbinder on 2012-11-29
[PPAs](https://launchpad.net/ubuntu/+ppas)

Part of the reason I love Ubuntu. The ability to customize your sources.list.

A quick way to get the "popular" PPAs and a current Ubuntu sources.list is with the [Ubuntu Sources List Generator](http://repogen.simplylinux.ch/).

sudo gedit /etc/apt/sources.list gets you to the list in order to edit

Here's mine on my Xubuntu 12.10 install:

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu quantal partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu quantal main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos


#### GetDeb - http://www.getdeb.net
## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu quantal-getdeb apps

#### WebUpd8 - https://launchpad.net/~nilarimogard/+archive/webupd8
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4C9D234C
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu quantal main

#### WebUpd8 Themes - https://launchpad.net/~webupd8team/+archive/themes
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb http://ppa.launchpad.net/webupd8team/themes/ubuntu quantal main

#### Xubuntu Developers: XFCE 4.12 - https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 142986CE
deb http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu quantal main

#### Gimp - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu quantal main

#### LibreOffice - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu quantal main

#### OpenShot - http://www.openshotvideo.com
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu quantal main

#### qBittorrent - http://qbittorrent.sourceforge.net/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 47B4D1C4
deb http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu quantal main

#### Clementine Development - https://launchpad.net/~me-davidsansome/+archive/clementine-dev
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 044A3B98
deb http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu quantal main
```

---

### Post by raven2099 on 2012-11-30
thanks  but how to install implement?

---

### Post by dino99 on 2012-11-30
why do want more sources ? have you a special need ?
Note that free software (good and junk) are all around the world; and if you want to try each, then first go to your hardware shop to buy all the hdd/sdd available because you will need a lot of space, and your life is too short to try each one by the way. Life means doing choices.

ubuntu repo already have thousands of packages (more than you need)

and to answer your previous question: post #3 above already have explained with details what/how to do. So read first.

---

### Post by Uncle Spellbinder on 2012-11-30
> **raven2099 said:**
> thanks  but how to install implement?

One you have your sources.list edited the way you like, either update in Synaptic, Ubuntu Software Center or Terminal. Then, browse and/or install as you normally wood.

---

### Post by raven2099 on 2012-11-30
thank you all soo much

---

