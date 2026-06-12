---
title: "Packages won't download"
date: 2013-02-06
forum: General Help
---

### Post by Jake Sweeney on 2013-02-06
Hello everybody :)
I wanted to install docky for my Ubuntu 12.04 machine, so I entered the apt-get into the Terminal and all of a sudden the package isn't downloading, only displaying this:
```
jake@jake-N130:~$ sudo apt-get install docky -y
[sudo] password for jake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dockmanager libgnome-desktop-2-17 libgnome-keyring1.0-cil
  libgnomedesktop2.20-cil libmono-data-tds4.0-cil libmono-sqlite4.0-cil
  libmono-system-data4.0-cil libmono-system-enterpriseservices4.0-cil
  libmono-system-transactions4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-services4.0-cil libmono-system-web4.0-cil
  libmono-system-xml-linq4.0-cil libmono-web4.0-cil librsvg2-2.18-cil
  libwnck2.20-cil python-mpd python-mutagen
Suggested packages:
  monodoc-gtk2.0-manual
The following NEW packages will be installed
  dockmanager docky libgnome-desktop-2-17 libgnome-keyring1.0-cil
  libgnomedesktop2.20-cil libmono-data-tds4.0-cil libmono-sqlite4.0-cil
  libmono-system-data4.0-cil libmono-system-enterpriseservices4.0-cil
  libmono-system-transactions4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-services4.0-cil libmono-system-web4.0-cil
  libmono-system-xml-linq4.0-cil libmono-web4.0-cil librsvg2-2.18-cil
  libwnck2.20-cil python-mpd python-mutagen
0 upgraded, 19 newly installed, 0 to remove and 5 not upgraded.
Need to get 2,720 kB of archives.
After this operation, 9,853 kB of additional disk space will be used.
0% [Connecting to 10.104.0.5 (10.104.0.5)]

```

I've tried with other packages and my internet connection is fine as I can browse the internet, but I really don't know what's happening :(

---

### Post by gifford on 2013-02-06
I'm not sure if you are stating that it hangs without downloading the listed files, or if you expected only one file to be downloaded. If it is the later, all the files listed to be installed are part of the docky dependency packages.

---

### Post by Jake Sweeney on 2013-02-06
I'm stating that it hangs without downloading the listed files. The connection times out for some reason

---

### Post by kanikilu on 2013-02-06
> **Jake Sweeney said:**
> I'm stating that it hangs without downloading the listed files. The connection times out for some reason What happens when you update (**sudo apt-get update**)? Have you tried another mirror? You can set that in Software Sources...

---

### Post by ajgreeny on 2013-02-06
I am not sure what web address you were trying to connect to > Connecting to 10.104.0.5 but I can not ping it so I must assume that it is not a live repository site, not a Ubuntu server that is working.  Using network-tools it shows as ```
Source    TTL    Address Type    Record Type1    Resolution
10.in-addr.arpa.    300    IN    SOA    prisoner.iana.org. hostmaster.root-servers.org. 2002040800 1800 900 604800 604800
```
What is your sources.list file like? Let's see the output of  ```
cat /etc/apt/sources.list
```

---

### Post by Jake Sweeney on 2013-02-07
My Sources.list file looks like this:
```
jake@jake-N130:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner

```

---

### Post by ajgreeny on 2013-02-07
I can not see anything wrong with that sources.list, so I wonder if there is a problem with any additional sources you may have added.

What is the content of the sources.list.d folder? ```
ls /etc/apt/sources.list.d
```

---

### Post by Jake Sweeney on 2013-02-07
Here is the list:
```
jake@jake-N130:~$ ls /etc/apt/sources.list.d
google-chrome.list
google-chrome.list.save
gwendal-lebihan-dev-cinnamon-stable-precise.list
gwendal-lebihan-dev-cinnamon-stable-precise.list.save
kokoto-java-omgubuntu-stuff-precise.list
kokoto-java-omgubuntu-stuff-precise.list.save
scopes-packagers-ppa-precise.list
scopes-packagers-ppa-precise.list.save
sgringwe-beatbox-precise.list
sgringwe-beatbox-precise.list.save
tiheum-equinox-precise.list
tiheum-equinox-precise.list.save
jake@jake-N130:~$ 

```

My internet connection seems to run only when I'm at college (Where I'm posting from now). yesterday when I was first signed up to the network I may have indirectly changed the proxy settings or something for my network. Maybe when I try to download packages at home the package finder is trying to find packages from the colleges IP address rather than my home's one. It's just a suggestion, but it sort of makes sense.

---

### Post by ajgreeny on 2013-02-07
> **Jake Sweeney said:**
> My internet connection seems to run only when I'm at college (Where I'm posting from now). yesterday when I was first signed up to the network I may have indirectly changed the proxy settings or something for my network. Maybe when I try to download packages at home the package finder is trying to find packages from the colleges IP address rather than my home's one. It's just a suggestion, but it sort of makes sense.
Could be, I suppose, but I have never used a proxy for internet connection so will leave possible answers to others to deal with.

---

### Post by Jake Sweeney on 2013-02-07
I'm probably just thinking of wiping the system and installing Lubuntu because my netbook only has 1GB RAM and when running Ubuntu
I find it to be slow
Thanks anyway, I'll mark the thread as solved.
:D

---

