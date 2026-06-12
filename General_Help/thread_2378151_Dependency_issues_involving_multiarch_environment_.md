---
title: "Dependency issues involving multiarch environment 16.04"
date: 2017-11-20
forum: General Help
---

### Post by lopspp on 2017-11-20
I am trying to install teamviewer on ubuntu 16.04 LTS.
```
sudo dpkg -i teamviewer_12.0.85001_i386.deb
```

returns ERROR:

```

Selecting previously unselected package teamviewer:i386.
(Reading database ... 268061 files and directories currently installed.)
Preparing to unpack teamviewer_12.0.85001_i386.deb ...
Unpacking teamviewer:i386 (12.0.85001) ...
dpkg: dependency problems prevent configuration of teamviewer:i386:
 teamviewer:i386 depends on libc6 (>= 2.11).
 teamviewer:i386 depends on libgcc1.
 teamviewer:i386 depends on libasound2.
 teamviewer:i386 depends on libdbus-1-3.
 teamviewer:i386 depends on libexpat1.
 teamviewer:i386 depends on libfontconfig1.
 teamviewer:i386 depends on libfreetype6.
 teamviewer:i386 depends on libjpeg62.
 teamviewer:i386 depends on libsm6.
 teamviewer:i386 depends on libxdamage1.
 teamviewer:i386 depends on libxext6.
 teamviewer:i386 depends on libxfixes3.
 teamviewer:i386 depends on libxinerama1.
 teamviewer:i386 depends on libxrandr2.
 teamviewer:i386 depends on libxrender1.
 teamviewer:i386 depends on libxtst6.
 teamviewer:i386 depends on zlib1g.

```

**After manually installing some packages, I was able to narrow down the problem to this:**

```
sudo dpkg -i teamviewer_12.0.85001_i386.deb
Selecting previously unselected package teamviewer:i386.
(Reading database ... 268433 files and directories currently installed.)
Preparing to unpack teamviewer_12.0.85001_i386.deb ...
Unpacking teamviewer:i386 (12.0.85001) ...
dpkg: dependency problems prevent configuration of teamviewer:i386:
 teamviewer:i386 depends on libfontconfig1.
 teamviewer:i386 depends on libfreetype6.

```

**libfontconfig1:i386 depends on libfreetype6:i386 so I tried to insall libfreetype6:i386 first and here is the error message:**

```
sudo apt install libfreetype6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 colord : Depends: libsane (>= 1.0.24) but it is not going to be installed
 gvfs : Depends: gvfs-daemons (>= 1.28.2-1ubuntu1~16.04.2)
        Depends: gvfs-daemons (< 1.28.2-1ubuntu1~16.04.2.1~)
 libfreetype6 : Depends: libpng12-0 (>= 1.2.13-4) but it is not going to be installed
 libgtk2.0-0 : Depends: libcairo2 (>= 1.6.4-6.1) but it is not going to be installed
               Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
               Depends: libpangocairo-1.0-0 (>= 1.28.3) but it is not going to be installed
               Depends: libpangoft2-1.0-0 (>= 1.28.3) but it is not going to be installed
               Recommends: libgtk2.0-bin
 libonline-accounts-daemon1 : Depends: libonline-accounts-client1 but it is not going to be installed
 libqmenumodel0 : Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed or
                           libqt5gui5-gles (>= 5.0.2) but it is not going to be installed
 libqt5svg5 : Depends: libqt5gui5 (>= 5.3.0) but it is not going to be installed or
                       libqt5gui5-gles (>= 5.3.0) but it is not going to be installed
              Depends: libqt5widgets5 (>= 5.3.0) but it is not going to be installed
 libqt5x11extras5 : Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed or
                             libqt5gui5-gles (>= 5.0.2) but it is not going to be installed
 libubuntugestures5 : Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed or
                               libqt5gui5-gles (>= 5.0.2) but it is not going to be installed
                      Depends: libqt5quick5 (>= 5.0.2) but it is not going to be installed or
                               libqt5quick5-gles (>= 5.0.2) but it is not going to be installed
 libubuntutoolkit5 : Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed or
                              libqt5gui5-gles (>= 5.0.2) but it is not going to be installed
 libzvbi0 : Depends: libpng12-0 (>= 1.2.13-4) but it is not going to be installed
 qml-module-io-thp-pyotherside : Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed or
                                          libqt5gui5-gles (>= 5.0.2) but it is not going to be installed
                                 Depends: libqt5quick5 (>= 5.0.2) but it is not going to be installed or
                                          libqt5quick5-gles (>= 5.0.2) but it is not going to be installed
 qml-module-qtquick-layouts : Depends: libqt5gui5 (>= 5.5.0) but it is not going to be installed or
                                       libqt5gui5-gles (>= 5.5.0) but it is not going to be installed
                              Depends: libqt5quick5 (>= 5.2.0) but it is not going to be installed or
                                       libqt5quick5-gles (>= 5.2.0) but it is not going to be installed
 qml-module-qtquick-window2 : Depends: libqt5quick5 (>= 5.0.2) but it is not going to be installed or
                                       libqt5quick5-gles (>= 5.0.2) but it is not going to be installed
 qml-module-ubuntu-layouts : Depends: libqt5quick5 (>= 5.0.2) but it is not going to be installed or
                                      libqt5quick5-gles (>= 5.0.2) but it is not going to be installed
 qml-module-ubuntu-performancemetrics : Depends: libqt5gui5 (>= 5.0.2) but it is not going to be installed or
                                                 libqt5gui5-gles (>= 5.0.2) but it is not going to be installed
                                        Depends: libqt5quick5 (>= 5.0.2) but it is not going to be installed or
                                                 libqt5quick5-gles (>= 5.0.2) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

I have updated and upgrade/dist-upgrade and there were no problem reported. 
I have also used apt clean/autoclean/autoremove operation completed with no error. 
```
apt install -f
```
gives the same error

Any suggestions on how the held packages problems could be solved?

---

### Post by #&amp;thj^% on 2017-11-20
Did you forget to run first:
```
sudo dpkg --add-architecture i386
```
And Then:
```
sudo apt update 
sudo apt full-upgrade
```

---

### Post by lopspp on 2017-11-20
> **1fallen said:**
> Did you forget to run first:
```
sudo dpkg --add-architecture i386
```
And Then:
```
sudo apt update 
sudo apt full-upgrade
```
I already did that.
```

sudo dpkg --print-foreign-architectures 
i386
```
And after update, full-upgrade prints:
```

sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by #&amp;thj^% on 2017-11-20
> **lopspp said:**
> I already did that.
```

sudo dpkg --print-foreign-architectures 
i386
```
And after update, full-upgrade prints:
```

sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Very Odd then?
As a last work around then give this a shot:
```
sudo apt install gdebi
```
Then remove/install the "teamviewer.deb" with gdebi

---

### Post by lopspp on 2017-11-20
> **1fallen said:**
> Very Odd then?
As a last work around then give this a shot:
```
sudo apt install gdebi
```
Then install the "teamviewer.deb" with gdebi

Already tried gdebi, but no luck. 
```
gdebi teamviewer_12.0.85001_i386.deb 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
This package is uninstallable
Cannot install 'libfontconfig1:i386'
```

---

### Post by mc4man on 2017-11-20
run & post 
```
apt-cache policy libfreetype6:i386 libfreetype6 libpng12-0:i386 libpng12-0
```

---

### Post by lopspp on 2017-11-20
> **mc4man said:**
> run & post 
```
apt-cache policy libfreetype6:i386 libfreetype6 libpng12-0:i386 libpng12-0
```

Here you go:

```
apt-cache policy libfreetype6:i386 libfreetype6 libpng12-0:i386 libpng12-0
libfreetype6:i386:
  Installed: (none)
  Candidate: 2.6.1-0.1ubuntu2.3
  Version table:
     2.6.1-0.1ubuntu2.3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
     2.6.1-0.1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
libfreetype6:
  Installed: 2.6.1-0.1ubuntu2.3
  Candidate: 2.6.1-0.1ubuntu2.3
  Version table:
 *** 2.6.1-0.1ubuntu2.3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.6.1-0.1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
libpng12-0:i386:
  Installed: (none)
  Candidate: 1.2.54-1ubuntu1
  Version table:
     1.2.54-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
libpng12-0:
  Installed: 1.2.54-1ubuntu1k1
  Candidate: 1.2.54-1ubuntu1k1
  Version table:
 *** 1.2.54-1ubuntu1k1 100
        100 /var/lib/dpkg/status
     1.2.54-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages


```

---

### Post by mc4man on 2017-11-20
You need to get rid of that 1.2.54-1ubuntu1[COLOR="#FF0000"]k1[/COLOR] package. This should probably do that, then try installing teamviewer again if successful in downgrading..
```
sudo apt install libpng12-0=1.2.54-1ubuntu1
```

---

### Post by lopspp on 2017-11-20
> **mc4man said:**
> You need to get rid of that 1.2.54-1ubuntu1[COLOR=#FF0000]k1[/COLOR] package. This should probably do that, then try installing teamviewer again if successful in downgrading..
```
sudo apt install libpng12-0=1.2.54-1ubuntu1
```

Thank you, this solved the problem

---

