---
title: "Ubuntu 16.04.1 LTS : php7.0-mbstring unmet dependencies issue"
date: 2016-10-12
forum: General Help
---

### Post by davidbouche on 2016-10-12
Hello,

I can't install php7.0-mbstring on my fresh new Ubuntu 16.04.1 LTS.

System information : 

```
# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"

# cat /etc/apt/sources.list.d/*
deb [arch=amd64] http://fr.archive.ubuntu.com/ubuntu/ xenial-backports main
deb [arch=amd64] http://fr.archive.ubuntu.com/ubuntu/ xenial main universe
deb [arch=amd64] http://fr.archive.ubuntu.com/ubuntu/ xenial-proposed main
deb [arch=amd64] http://security.ubuntu.com/ubuntu xenial-security main
deb [arch=amd64] http://fr.archive.ubuntu.com/ubuntu/ xenial-updates main
```

Here's the problem : 

```
# apt update
Hit:1 http://fr.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:2 http://security.ubuntu.com/ubuntu xenial-security InRelease
Hit:3 http://fr.archive.ubuntu.com/ubuntu xenial InRelease
Hit:4 http://fr.archive.ubuntu.com/ubuntu xenial-proposed InRelease
Hit:5 http://fr.archive.ubuntu.com/ubuntu xenial-updates InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.


# apt install libapache2-mod-php7.0 phpmyadmin php7.0-mbstring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 php7.0-mbstring : Depends: php7.0-common (= 7.0.4-7ubuntu2) but 7.0.8-0ubuntu0.16.04.3 is to be installed
E: Unable to correct problems, you have held broken packages.

```

 I do not know how to deal with it ... :(

Any ideas ? Thanks for helping.


David

---

### Post by davidbouche on 2016-10-12
The solution I've found : added "universe" on the xenial-updates


[FONT=courier new]# cat /etc/apt/sources.list.d/*[/FONT]
[FONT=courier new]deb [arch=amd64] [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-backports main[/FONT]
[FONT=courier new]deb [arch=amd64] [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial main universe[/FONT]
[FONT=courier new]deb [arch=amd64] [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-proposed main[/FONT]
[FONT=courier new]deb [arch=amd64] [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main[/FONT]
[FONT=courier new]deb [arch=amd64] [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) xenial-updates main **universe**[/FONT]

---

### Post by stadja on 2016-11-22
YES !!!!
It worked for me !!!!!

THANK YOU :)

I spend months looking for a way to correct this f***ing bug !!!!

Now it works and I can dist-upgrade ! Yes, thank you very very much !!!!

---

