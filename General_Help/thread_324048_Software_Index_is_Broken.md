---
title: "Software Index is Broken"
date: 2006-12-23
forum: General Help
---

### Post by phiz on 2006-12-23
I'm a complete noob, and this has been a long night... i started updating breezy to dapper, and that all went fine, but except when i tried to fix the repositories in dapper, some links werent working when i tried to apt-get update, so i put a # to hide them, or whatever. Then i followed the instructions to update to Edgy, and it downloaded all the files, but when it was installing it, hung up, aborted, and basically when i restarted my computer, x-server crashed, and eventually i figured out a way to boot into the system to relay my problem. I'm getting errors all over the place, and when i try to do a system-update i get Software Index Broken errors, and then whe ni try to run sudo apt-get install -f, it looks like this. 

```
root@Mulberry:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libxft-dev but it is not installed
  openoffice.org-base: Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed
  openoffice.org-calc: Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed
  openoffice.org-core: Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed
                       Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is installed
  openoffice.org-draw: Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed
  openoffice.org-evolution: Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed
  openoffice.org-gnome: Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed
  openoffice.org-gtk: Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed
  openoffice.org-impress: Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed
  openoffice.org-writer: Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed
                         Depends: python-uno (>= 2.0.4) but 2.0.2-2ubuntu12.1 is installed
  xserver-xorg-core: Depends: x11-common (>= 1:7.0.0) but 7.0.0-0ubuntu45 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

my source file looks like this.
```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
#deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
#deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#deb http://archive.ubuntu.com/ubuntu dapper multiverse
#deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

#deb http://archive.canonical.com/ubuntu dapper-commercial main

#deb http://packages.freecontrib.org/plf/ dapper free non-free
#deb-src http://packages.freecontrib.org/plf/ dapper free non-free
```

and before i get to the source file, the terminal does this... 

```
root@Mulberry:~# sudo gedit /etc/apt/sources.list

(gedit:6027): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:6027): Gdk-WARNING **: locale not supported by C library

(gedit:6027): Gtk-WARNING **: Unable to locate theme engine in module_path: "thinice",

(gedit:6027): Gtk-WARNING **: Unable to locate theme engine in module_path: "redmond95",

(gedit:6027): Gtk-WARNING **: Unable to locate theme engine in module_path: "redmond95",

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:6027): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

** (gedit:6027): WARNING **: Could not load the spinner file.

** (gedit:6027): WARNING **: Could not load the spinner file.

** (gedit:6027): WARNING **: Could not load the spinner file.

** (gedit:6027): WARNING **: Could not load the spinner file.

** (gedit:6027): WARNING **: Could not load the spinner file.

```

also, when i try to fix broken packages in synaptic i receive this error

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by phiz on 2006-12-23
bump

---

### Post by PuleX on 2006-12-24
Can you open your /etc/apt/sources.list using nano? 
```
sudo nano /etc/apt/sources.list
``` 
If so, then I would start with changing all instances of dapper to edgy. Also, change the adressess to a local mirror for faster downloading. My sources.list looks like this (notice all the **nl.** for the Dutch mirror: 
```
##### OFFICIAL REPOS #####

## Ubuntu
deb http://nl.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Updates
deb http://nl.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Backports
deb http://nl.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe mulitiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe
``` 

After that, try following the upgrade instructions here (method B): 
[http://ubuntuforums.org/showthread.php?t=227052](http://ubuntuforums.org/showthread.php?t=227052) 

That would be: 
```
sudo aptitude update 
sudo aptitude dist-upgrade
``` 

I hope that works.   :)

---

### Post by der_joachim on 2006-12-24
I second PuleX's (implicit) remark to use aptitude instead of apt-get. Aptitude handles dependencies better than apt-get.

---

