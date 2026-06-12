---
title: "get error when opening ubuntu software center"
date: 2020-06-23
forum: General Help
---

### Post by mickee384 on 2020-06-23
Every time I open the ubuntu software center I get the following error: 
[HTML]Don't know how to handle 'file:///home/mickee'[/HTML]
at the top. The application appears unaffected, just getting tired of the error. When I click on the X it doesn't come back until the next time I launch it.

[IMG]https://othersideoz.ca/blog_images/uforumscenter.jpg[/IMG]

Any ideas will be most welcomed!

---

### Post by guiverc on 2020-06-24
You haven't provided your release details (legacy Lubuntu or modern Lubuntu, or something different), however I'd be checking your sources for an invalid entry.

I rarely use GUI software/package tools so aren't familiar with errors when things are done wrong, but I'd likely jump to a terminal (ctrl+alt+T) then `sudo apt update` and look for errors or entries containing  "/home/mickee".  It may not be your cause, but it's what I'd look for first (if that's it, remove it from your sources (myself I'd use `vim`, but [https://manual.lubuntu.me/stable/4/4.3/software_sources.html](https://manual.lubuntu.me/stable/4/4.3/software_sources.html) for the Lubuntu manual page on that detail)

---

### Post by mickee384 on 2020-06-27
I use terminal alot and there are no errors with apt - there are no errors in the sources. I am using Ubuntu 18.04 LTS. That said I appreciate the answer and will double check the sources.list

---

### Post by mickee384 on 2020-06-27
```
sudo apt-get update
[sudo] password for mickee: 
Hit:1 http://ppa.launchpad.net/atareao/atareao/ubuntu bionic InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable InRelease                                       
Hit:3 http://ppa.launchpad.net/gencfsm/ppa/ubuntu bionic InRelease                                 
Hit:4 http://ppa.launchpad.net/mark-pcnetspec/conky-manager-pm9/ubuntu bionic InRelease            
Hit:5 http://ca.archive.ubuntu.com/ubuntu bionic InRelease                                         
Get:6 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]                        
Hit:7 http://archive.canonical.com/ubuntu xenial InRelease                                         
Hit:8 http://ca.archive.ubuntu.com/ubuntu xenial InRelease                                         
Hit:9 https://brave-browser-apt-release.s3.brave.com stable InRelease                              
Get:10 http://ca.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]        
Get:11 http://ca.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]                      
Get:12 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]          
Get:13 http://ca.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [294 kB]
Get:14 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [46.0 kB]
Get:15 http://ca.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [279 kB]  
Get:16 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [49.2 kB]  
Get:17 http://ca.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:18 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Fetched 1,069 kB in 3s (342 kB/s)                                             
Reading package lists... Done

```

---

### Post by mickee384 on 2020-06-27
My sources list:
```
# deb cdrom:[Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ bionic main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial universe
deb http://ca.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb http://download.virtualbox.org/virtualbox/debian bionic contrib
# deb-src http://download.virtualbox.org/virtualbox/debian bionic contrib
# deb https://dl.winehq.org/wine-builds/ubuntu/bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
```

---

### Post by Impavidus on 2020-06-28
It could be unrelated, but there are several xenial repositories mixed with your bionic repositories. Edit your /etc/apt/sources.list to change these to bionic. Most people don't need the source repositories, so maybe you want to put a # at the start of every line beginning with deb-src. Most of the xenial repositories are for source code, but the partner repo is of xenial too.

---

### Post by mickee384 on 2020-07-03
Thanks for noticing that! I edited the file. However I don't know what to do with the entry on line 1...

---

### Post by mickee384 on 2020-08-16
It seems that there was the error only if loading Software Center from Cairo Dock. Doesn't happen otherwise.

---

