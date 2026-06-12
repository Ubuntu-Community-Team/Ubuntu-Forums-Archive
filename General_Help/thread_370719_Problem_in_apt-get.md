---
title: "Problem in apt-get"
date: 2007-02-26
forum: General Help
---

### Post by geniusvicks on 2007-02-26
My apt-get isn't working.  The error is given below. Plz. Help
______________________________________________________________________________________________
geniusvicks@Home:/var/lib/dpkg$ dir
alternatives   cmethopt        info     parts             status      updates
available      diversions      lock     statoverride      status-old
available-old  diversions-old  methods  statoverride-old  tmp.ci
geniusvicks@Home:/var/lib/dpkg$ sudo rm lock
Password:
geniusvicks@Home:/var/lib/dpkg$ dir
alternatives   cmethopt        info     statoverride      status-old
available      diversions      methods  statoverride-old  tmp.ci
available-old  diversions-old  parts    status            updates
geniusvicks@Home:/var/lib/dpkg$ sudo aptitude remove sun-java5-bin
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
geniusvicks@Home:/var/lib/dpkg$ dpjg --configure -a
bash: dpjg: command not found
geniusvicks@Home:/var/lib/dpkg$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
geniusvicks@Home:/var/lib/dpkg$ sudo dpkg --configure -a
geniusvicks@Home:/var/lib/dpkg$ dir
alternatives   cmethopt        info     parts             status      updates
available      diversions      lock     statoverride      status-old
available-old  diversions-old  methods  statoverride-old  tmp.ci
geniusvicks@Home:/var/lib/dpkg$ sudo rm lock
geniusvicks@Home:/var/lib/dpkg$ sudo aptitude remove sun-java5-bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings
  beryl-settings-bindings emerald emerald-themes libberyldecoration0
  libberylsettings0 libemeraldengine0 linux-image-2.6.17-10-generic
  linux-image-generic linux-restricted-modules-2.6.17-10-generic
  linux-restricted-modules-common linux-restricted-modules-generic
The following packages have been kept back:
  avahi-daemon beryl bind9-host dbus dnsutils gnupg info
  kdenetwork-filesharing kdenetwork-kfile-plugins kdnssd koffice-data
  koffice-libs kopete kpf kppp krdc krfb krita krita-data language-pack-en
  language-pack-kde-en libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core4 libavahi-qt3-1
  libbind9-0 libc6 libc6-dev libc6-i686 libdbus-1-3 libdns21 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libimlib2 libisc11 libisccc0 libisccfg1
  libkrb53 liblwres9 libmagick++9c2a libmagick9 libpng12-0 libpoppler1
  libpoppler1-qt libpq4 libruby1.8 libsmbclient libvolumeid0 libxine1
  linux-generic linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic
  linux-headers-generic linux-libc-dev openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-impress openoffice.org-java-common
  openoffice.org-kde openoffice.org-math openoffice.org-style-crystal
  openoffice.org-style-default openoffice.org-writer poppler-utils
  python-uno ruby1.8 samba-common screen slocate smbclient sun-java5-jre
  tar ttf-opensymbol tzdata udev volumeid w3m wine wlassistant x11-common
  xbase-clients xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-video-all xutils
The following packages will be REMOVED:
  sun-java5-bin
0 packages upgraded, 0 newly installed, 1 to remove and 110 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-jre package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

---

### Post by bapoumba on 2007-02-26
> **geniusvicks said:**
> My apt-get isn't working.  The error is given below. Plz. Help
______________________________________________________________________________________________
geniusvicks@
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-jre package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

Hello,
try with **sudo dpkg -i sun-java5-jre**
[http://ubuntuforums.org/showthread.php?t=324478]("http://ubuntuforums.org/showthread.php?t=324478")
(see posts #14 and #16).

---

### Post by geniusvicks on 2007-02-26
This is what I get after doing the above mentioned steps: 


dpkg: error processing sun-java5-jre (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-java5-jre

geniusvicks@Home:~$ sudo dpkg -r sun-java5-bin
dpkg: error processing sun-java5-bin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 sun-java5-bin

---

### Post by geniusvicks on 2007-03-01
Some one help.

---

### Post by Kateikyoushi on 2007-03-01
Try to reinstall the package.

```
sudo aptitude reinstall sun-java5-jre
```

---

### Post by geniusvicks on 2007-03-04
Not working!!!

---

### Post by rudiz on 2007-03-04
sudo apt-get install --reinstall packagename

---

