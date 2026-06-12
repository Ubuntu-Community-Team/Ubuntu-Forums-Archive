---
title: "Firefox won't update past version 33 on Ubuntu 14.10/apt-get not updating?"
date: 2015-04-09
forum: General Help
---

### Post by andrewrz on 2015-04-09
I am running multiple installations of lubuntu and one installation seems to have an issue with Firefox not updating past version 33. My other installations have upgraded to 37 and I can't find any reason it would stop at 33 by searching online. I was originally running as a 14.04.2 LTS but I switched it to normal and upgraded it to 14.10 thinking that would allow the update to Firefox. I am thinking there might be something wrong with apt-get because I was getting the "0 upgraded 0 installed etc" message with update upgrade.

---

### Post by Elfy on 2015-04-09
Try 

```
sudo apt-get update && sudo apt-get -s dist-upgrade
```

That will simulate the upgrade.

Paste the whole terminal output here.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by andrewrz on 2015-04-09
```
 
Hit http://us.archive.ubuntu.com utopic/main Sources
Hit http://us.archive.ubuntu.com utopic/restricted Sources
Hit http://archive.canonical.com quantal/partner Sources
Hit http://extras.ubuntu.com utopic/main Sources
Hit http://us.archive.ubuntu.com utopic/universe Sources
Hit http://extras.ubuntu.com utopic/main i386 Packages
Hit http://us.archive.ubuntu.com utopic/multiverse Sources
Hit http://us.archive.ubuntu.com utopic/main i386 Packages
Hit http://us.archive.ubuntu.com utopic/restricted i386 Packages
Hit http://us.archive.ubuntu.com utopic/universe i386 Packages
Hit http://us.archive.ubuntu.com utopic/multiverse i386 Packages
Hit http://us.archive.ubuntu.com utopic/main Translation-en
Hit http://us.archive.ubuntu.com utopic/multiverse Translation-en
Hit http://us.archive.ubuntu.com utopic/restricted Translation-en
Hit http://us.archive.ubuntu.com utopic/universe Translation-en
Ign http://extras.ubuntu.com utopic/main Translation-en_US
Ign http://extras.ubuntu.com utopic/main Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by plucky on 2015-04-09
Can you post your sources.list?

```
cat /etc/apt/sources.list
``` and cut and paste to the forum.

---

### Post by andrewrz on 2015-04-09
```

#

# deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017)]/ quantal main multiverse restricted universe

# deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017)]/ quantal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ utopic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ utopic main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ utopic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ utopic universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ utopic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ utopic multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu utopic main
deb-src http://extras.ubuntu.com/ubuntu utopic main

```

---

### Post by plucky on 2015-04-09
Your sources.list is missing utopic-updates and utopic-security repositories.

Also you should change > # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

to
```
deb http://archive.canonical.com/ubuntu utopic partner
#deb-src http://archive.canonical.com/ubuntu utopic partner
```



Go [Here](http://repogen.simplylinux.ch/) and generate a new sources.list and make a backup of your current list and replace it with the list generated at that website.

You do not need the deb-src repositories unless you want the source code.

Good Luck

---

### Post by andrewrz on 2015-04-09
Thanks everyone! Using a new sources.list from "http://repogen.simplylinux.ch/generate.php" solved the problem.
[h=1][/h]

---

