---
title: "Why is aptitude wanting to remove my KDE?"
date: 2007-10-10
forum: General Help
---

### Post by marx2k on 2007-10-10
Here's the issue.  When I go do "sudo aptitude update; sudo aptitude upgrade" I get:

```

marx2k@UbuntuDrive:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater
  akregator amarok amarok-xine apport-qt ark arts debtags digikam digikamimageplugins exiv2
  fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine karm
  katapult kate kbstate kcron kde-guidance kde-guidance-powermanager kde-icons-mono
  kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards
  kdeprint kdm kdnssd keep kexi khelpcenter kio-apt kio-locate kipi-plugins kitchensync
  klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base
  kmplayer-konq-plugins knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka korganizer kpdf kpersonalizer kpf kppp krdc
  kregexpeditor krfb kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwin-style-crystal
  language-selector-qt latex-xft-fonts libavahi-compat-libdnssd1 libexiv2-0.12 libflac++5c2
  libgmp3c2 libgpgme11 libifp4 libimlib2 libiso9660-4 libjasper-runtime libjpeg-progs libk3b2
  libkcal2b libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1c2a libmtp5
  libmysqlclient15off libnjb5 libofa0 libopenobex1 libpoppler1-qt libpq5 libpth20
  libpythonize0 libqt-perl libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1
  libruby1.8 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libvcdinfo0 mysql-common
  ncompress ocrad openoffice.org-kde poster procmail psutils pykdeextensions python-all
  python-all-dev python-dev python-elementtree python-kde3 python-pylibacl python-pyxattr
  python-qt4 python2.4 python2.4-dev python2.4-minimal python2.5-dev qca-tls qobex
  qt4-qtconfig rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch
  vcdimager zoo
0 packages upgraded, 0 newly installed, 179 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 445MB will be freed.
Do you want to continue? [Y/n/?]  

```

I do NOT want to remove KDE so I hit no, but how do I tell Linux I want to keep KDE?

here's my repository list:
```

marx2k@UbuntuDrive:~$ cat /etc/apt/sources.list
#Provided with VMWare Install Instructions
#http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html
deb http://archive.canonical.com/ubuntu feisty-commercial main

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

I DID hit 'y' before and it did remove kde and I had to reinstall kubuntu-desktop :( And now it's wanting to do it again!

---

### Post by por100pre1 on 2007-10-10
Check if installing the packages as a direct request fix the issue:

```
sudo aptitude install adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam digikamimageplugins exiv2 fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine karm katapult kate kbstate kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdm kdnssd keep kexi khelpcenter kio-apt kio-locate kipi-plugins kitchensync klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knode knotes koffice-data koffice-libs konq-plugins konqueror-nsplugins kontact konversation kooka korganizer kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwin-style-crystal language-selector-qt latex-xft-fonts libavahi-compat-libdnssd1 libexiv2-0.12 libflac++5c2libgmp3c2 libgpgme11 libifp4 libimlib2 libiso9660-4 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1c2a libmtp5 libmysqlclient15off libnjb5 libofa0 libopenobex1 libpoppler1-qt libpq5 libpth20 libpythonize0 libqt-perl libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libvcdinfo0 mysql-common ncompress ocrad openoffice.org-kde poster procmail psutils pykdeextensions python-all python-all-dev python-dev python-elementtree python-kde3 python-pylibacl python-pyxattr python-qt4 python2.4 python2.4-dev python2.4-minimal python2.5-dev qca-tls qobex qt4-qtconfig rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vcdimager zoo
```

EDIT: If that doesn't work try the reinstall command instead of install.

---

### Post by marx2k on 2007-10-12
most excellent. reinstall worked. I still am not sure what triggered this originally

---

### Post by hugmenot on 2007-10-12
those package likely used to be depended on by something that you removed. kde-desktop or so? then aptitude saw the stale or stray packages lying around and proposed to remove them. After you installed those packages explicitly they weren't unused packages anymore.

It&#8217;s a feature, not a bug.

Did you start to use aptitude recently?

---

### Post by por100pre1 on 2007-10-12
It seems the dependency that kept these files in place was no longer in apt, it's quite weird. Now the packages are individually installed and are no longer dependent of kubuntu-desktop or whatever package used to install them. :)

---

### Post by Seisen on 2007-10-12
Aptitude is also notorious for wanting to go crazy when removing packages, all thou this isn't a everyday occurrence with aptitude.

---

