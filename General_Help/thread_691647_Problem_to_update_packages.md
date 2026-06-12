---
title: "Problem to update packages"
date: 2008-02-08
forum: General Help
---

### Post by guill3 on 2008-02-08
Hello im using ubuntu 6.06 TLS, and my sources.list is this;

deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main
#deb [http://ubuntuguide.org/extrarepositories](http://ubuntuguide.org/extrarepositories)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse

But i cant update any package, for example, trying to install mplayer and mencoder i receive 

root@guille-desktop:/home/guille/download/peliculas# apt-get install mencoder mplayer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mencoder: Depends: libasound2 (> 1.0.14) but 1.0.10-2ubuntu4 is to be installed
            Depends: libc6 (>= 2.6-1) but 2.3.6-0ubuntu20.5 is to be installed
            Depends: libdvdread3 (>= 0.9.6) but 0.9.4-5.1 is to be installed
            Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
            Depends: libfreetype6 (>= 2.3.5) but 2.1.10-1ubuntu2.4 is to be installed
            Depends: libgcc1 (>= 1:4.2.1) but 1:4.0.3-1ubuntu5 is to be installed
            Depends: liblame0 (>= 3.97) but 3.96.1-1 is to be installed
            Depends: libncurses5 (>= 5.6) but 5.5-1ubuntu3 is to be installed
            Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5ubuntu0.3 is to be installed
            Depends: libstdc++6 (>= 4.2.1) but 4.0.3-1ubuntu5 is to be installed
            Depends: libx264-54 but it is not installable
            Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-6ubuntu4 is to be installed
  mplayer: Depends: libasound2 (> 1.0.14) but 1.0.10-2ubuntu4 is to be installed
           Depends: libatk1.0-0 (>= 1.13.2) but 1.11.4-0ubuntu1 is to be installed
           Depends: libc6 (>= 2.6-1) but 2.3.6-0ubuntu20.5 is to be installed
           Depends: libcaca0 (>= 0.99.beta11-1) but it is not installable
           Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1.2 is to be installed
           Depends: libcucul0 (>= 0.99.beta11-1) but it is not installable
           Depends: libdbus-1-3 (>= 1.1.1) but it is not installable
           Depends: libdbus-glib-1-2 (>= 0.74) but 0.60-6ubuntu8.1 is to be installed
           Depends: libdvdread3 (>= 0.9.6) but 0.9.4-5.1 is to be installed
           Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
           Depends: libfreetype6 (>= 2.3.5) but 2.1.10-1ubuntu2.4 is to be installed
           Depends: libgcc1 (>= 1:4.2.1) but 1:4.0.3-1ubuntu5 is to be installed
           Depends: libggi2 (>= 1:2.2.1) but it is not going to be installed
           Depends: libglib2.0-0 (>= 2.14.0) but 2.10.3-0ubuntu1 is to be installed
           Depends: libgtk2.0-0 (>= 2.12.0) but 2.8.20-0ubuntu1.1 is to be installed
           Depends: liblame0 (>= 3.97) but 3.96.1-1 is to be installed
           Depends: libncurses5 (>= 5.6) but 5.5-1ubuntu3 is to be installed
           Depends: libpango1.0-0 (>= 1.18.2) but 1.12.3-0ubuntu3 is to be installed
           Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5ubuntu0.3 is to be installed
           Depends: libpulse0 but it is not installable
           Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.9-0.0ubuntu2 is to be installed
           Depends: libstdc++6 (>= 4.2.1) but 4.0.3-1ubuntu5 is to be installed
           Depends: libx264-54 but it is not installable
           Depends: libxcomposite1 (>= 1:0.3-1) but it is not going to be installed
           Depends: libxdamage1 (>= 1:1.1) but 1:1.0.2.2-0ubuntu2 is to be installed
           Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is to be installed
           Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is to be installed
           Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-6ubuntu4 is to be installed
E: Broken packages

what kind of repositories i should add to get them and other nice software.

Thanks in advance.

---

### Post by taurus on 2008-02-08
Why in the world did you include both Edgy and Gutsy repos when you are running Dapper (and automatix)?  You need to edit your /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and remove these lines.

```

deb http://www.beerorkid.com/automatix/apt dapper main
#deb http://ubuntuguide.org/extrarepositories
deb http://packages.medibuntu.org/ gutsy free non-free

deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse

```
Save it with <Ctrl>o and exit with <Ctrl>x.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by PmDematagoda on 2008-02-08
Do:-
```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```

Post any errors you get.

---

