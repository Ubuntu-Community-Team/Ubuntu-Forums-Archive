---
title: "Python seems broken on 16.04 LTS"
date: 2019-04-15
forum: General Help
---

### Post by rsteinmetz70112 on 2019-04-15
In trying to solve a problem on one of my 16.04 LTS machines I've discovered that python seems to be broken I've not sure how to fix it.
A reinstall of python 2.7 didn't help

```
$ ls -ld /usr/bin/python
lrwxrwxrwx 1 root root 9 Nov 23  2017 /usr/bin/python -> python2.7
```

This appears correct for 16.04

```
~$ ls /usr/lib | grep python
python2.4
python2.5
python2.6
python2.7
python3
python3.5
```

This appears to match other working system.

```
$ update-alternatives --display python
update-alternatives: error: no alternatives for python
```

This appears correct at least for some configurations.

---

### Post by ttrott101 on 2019-04-15
> **rsteinmetz70112 said:**
> In trying to solve a problem on one of my 16.04 LTS machines I've discovered that python seems to be broken I've not sure how to fix it.
A reinstall of python 2.7 didn't help

```
$ ls -ld /usr/bin/python
lrwxrwxrwx 1 root root 9 Nov 23  2017 /usr/bin/python -> python2.7
```

This appears correct for 16.04

```
~$ ls /usr/lib | grep python
python2.4
python2.5
python2.6
python2.7
python3
python3.5
```

This appears to match other working system.

```
$ update-alternatives --display python
update-alternatives: error: no alternatives for python
```

This appears correct at least for some configurations.

Python 2 end of life comes shortly and will be phased out switching apps that depend to Python 3. Python 2.7 In Ubuntu it has been corrupted for some time, bug was reported some time ago but apparently never addressed probably since conversion will soon take place to python 3. There are some appsm such as gimp and samba etc that depend on Python 2 and so that will take some time. Perhaps completely removing Python 2.7 file and reinstalling from repos might solve your problem.

---

### Post by rsteinmetz70112 on 2019-04-15
> **ttrott101 said:**
> Python 2 end of life comes shortly and will be phased out switching apps that depend to Python 3. Python 2.7 In Ubuntu it has been corrupted for some time, bug was reported some time ago but apparently never addressed probably since conversion will soon take place to python 3. There are some appsm such as gimp and samba etc that depend on Python 2 and so that will take some time. Perhaps completely removing Python 2.7 file and reinstalling from repos might solve your problem.

I am preparing to move this system to 18.04 LTS, so the obsolescence should be resolved soon.

I did a re-installation of python2.7 ```
#apt install --reinstall python2.7
``` That should have reinstalled from the repositories but I'm still having problems.

If I try to remove python 2.7
```
# apt remove python2.7

```

This is what I get:
```
# apt remove python2.7
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  argyll argyll-ref attr bijiben cifs-utils dconf-editor dconf-tools
  dleyna-renderer fairymax finger five-or-more fonts-cantarell four-in-a-row
  geoclue-2.0 gimp-data gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-champlain-0.12 gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdm-1.0
  gir1.2-geocodeglib-1.0 gir1.2-gfbgraph-0.2 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0
  gir1.2-gnomebluetooth-1.0 gir1.2-grilo-0.2 gir1.2-gtkchamplain-0.12
  gir1.2-gweather-3.0 gir1.2-mediaart-2.0 gir1.2-mutter-3.0
  gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0 gir1.2-rest-0.7
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-tracker-1.0
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs gnome-backgrounds
  gnome-chess gnome-clocks gnome-color-manager gnome-control-center-data
  gnome-dictionary gnome-documents gnome-games gnome-getting-started-docs
  gnome-klotski gnome-logs gnome-maps gnome-music gnome-nettool gnome-nibbles
  gnome-online-accounts gnome-online-miners gnome-photos gnome-robots
  gnome-shell-common gnome-sound-recorder gnome-tetravex gnome-themes-standard
  gnome-themes-standard-data goobox hitori hoichess iagno icu-devtools libaio1
  libamd2.4.1 libbabl-0.1-0 libbonoboui2-0 libbonoboui2-common
  libcairo-script-interpreter2 libcamd2.4.1 libcaribou-common
  libcaribou-gtk-module libcaribou-gtk3-module libcaribou0 libccolamd2.9.1
  libcdio-cdda1 libcdio-paranoia1 libcholmod3.0.6 libcolord-gtk1 libcoverart1
  libcoverartcc1v5 libdbus-1-dev libdecoration0-dev libdiscid0 libdrm-dev
  libegl1-mesa-dev libepoxy-dev libfontconfig1-dev libfreetype6-dev
  libgdict-1.0-9 libgdict-common libgegl-0.3-0 libgeoclue-2-0
  libgfbgraph-0.2-0 libgimp2.0 libgl1-mesa-dev libglade2-0 libgmp-dev
  libgmpxx4ldbl libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0
  libgnomeui-common libgoa-backend-1.0-1 libgsf-bin libgsound0 libharfbuzz-dev
  libharfbuzz-gobject0 libice-dev libicu-dev libidl-2-0 libimage-magick-perl
  libimage-magick-q16-perl libjansson4 libldb1 libmagick++-6.q16-5v5
  libmate-desktop-2-17 libmatekbd-common libmatekbd4 libmatemixer-common
  libmatemixer0 libmirclient-dev libmircommon-dev libmircookie-dev
  libmircookie2 libmircore-dev libopencc1 liborbit2 libpcre3-dev libpcre32-3
  libpcrecpp0v5 libpixman-1-dev libpng12-dev libprotobuf-dev
  libpthread-stubs0-dev libpython-all-dev libpython-dev libpython-stdlib
  libpython2.7 libpython2.7-dev libpyzy-1.0-0v5 libqt4-designer libqt4-help
  libqt4-opengl libqt4-scripttools libqt4-test libqtassistantclient4
  libqtwebkit4 librsync1 librygel-core-2.6-2 librygel-db-2.6-2
  librygel-renderer-2.6-2 librygel-renderer-gst-2.6-2 librygel-server-2.6-2
  libsdl1.2debian libsigc++-2.0-dev libsm-dev libsofia-sip-ua-glib3
  libsofia-sip-ua0 libstartup-notification0-dev libtalloc2 libtevent0
  libumfpack5.7.1 libwayland-bin libwayland-dev libwbclient0 libwnck-common
  libwnck22 libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev
  libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev
  libxcb-render0-dev libxcb-shape0-dev libxcb-shm0-dev libxcb-sync-dev
  libxcb-xfixes0-dev libxcb1-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxkbcommon-dev libxml2-dev libxrandr-dev libxrender-dev
  libxshmfence-dev libxslt1-dev libxtst-dev libxxf86vm-dev libzapojit-0.0-0
  lightsoff mate-desktop-common mate-settings-daemon
  mate-settings-daemon-common mesa-common-dev nettle-dev oneconf-common polari
  python3-oneconf python3-piston-mini-client realmd rygel rygel-playbin
  rygel-tracker samba-common swell-foop tali tdb-tools telepathy-rakia
  ubuntu-mate-wallpapers-common ubuntuone-client-data unoconv
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xboard
  xorg-sgml-doctools xtrans-dev zlib1g-dev
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  alacarte caribou caribou-antler chrome-gnome-shell compiz-dev compiz-mate
  compiz-plugins-main-dev compizconfig-settings-manager deja-dup-backend-gvfs
  duplicity gdm gdm3 gimp gnome gnome-control-center gnome-core gnome-shell
  gnome-shell-extension-weather gnome-shell-extensions gnome-tweak-tool
  gvfs-backends hamster-applet hamster-indicator ibus-pinyin inkscape
  landscape-client-ui-install libatk-bridge2.0-dev libatk1.0-dev
  libatspi2.0-dev libcairo2-dev libgdk-pixbuf2.0-dev libglib2.0-dev
  libglibmm-2.4-dev libgtk-3-dev libnss-winbind libpam-winbind libpango1.0-dev
  libsmbclient ndiff oneconf python python-all python-all-dev
  python-appindicator python-apt python-aptdaemon python-aptdaemon.gtk3widgets
  python-attr python-blinker python-bs4 python-cairo python-cffi-backend
  python-chardet python-compizconfig python-crypto python-cryptography
  python-cups python-dbus python-debian python-debtagshw python-defer
  python-dev python-dirspec python-dnspython python-enum34 python-gconf
  python-gi python-gi-cairo python-glade2 python-gnome2 python-gobject
  python-gobject-2 python-gtk2 python-html5lib python-httplib2 python-idna
  python-imaging python-ipaddress python-jwt python-ldb python-lockfile
  python-lxml python-ndg-httpsclient python-notify python-numpy
  python-oauthlib python-oneconf python-openssl python-pam python-pil
  python-pip python-piston-mini-client python-pkg-resources python-pyasn1
  python-pyasn1-modules python-pyatspi python-pyorbit python-qt4
  python-qt4-dbus python-samba python-serial python-service-identity
  python-setuptools python-sip python-six python-talloc python-tdb python-tk
  python-twisted-bin python-twisted-core python-twisted-web
  python-ubuntu-sso-client python-urllib3 python-wheel python-wnck
  python-xapian python-xdg python-zeitgeist python-zope.interface python2.7
  python2.7-dev samba samba-common-bin samba-dsdb-modules samba-libs
  samba-vfs-modules sbackup sbackup-gtk smbclient software-center
  software-center-aptdaemon-plugins ubuntu-sso-client ubuntu-sso-client-qt
  winbind zeitgeist
0 upgraded, 0 newly installed, 135 to remove and 0 not upgraded.
After this operation, 302 MB disk space will be freed.
Do you want to continue? [Y/n]
```

I'm confused by the autoremove list at the beginning since when I run:
```
# apt autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

No packages are shown being removed.
```
# dpkg --configure -a
```
Produces no output. Neither does:
```
# dpkg-reconfigure python2.7
```

---

### Post by monkeybrain20122 on 2019-04-15
Well you haven't explained what your problem is, and why do you have so many versions of python2 and 3???

DO NOT try to remove python-2.7 since it is a dependency for many system components and if you remove it your system will break beyond repair.

FYI 18.04 still uses python-2.7 as default so "upgrading" will not give you python3 as default, but it doesn't really matter though, as long as Ubuntu's team maintains it, the system's default python is just for maintenance, running and installing things.

 On the other hand you can use different versions of python in your work without tempering with the system's . But update-alternatives is NOT the way to do it because many system components are compiled based on the version that comes with the system, and by changing the default via update alternatives again you break your system (**that is probably what caused your issue in the first place**)

There are many ways to use different versions of python safely, e.g anaconda or virtualenv. I compiled python3.7 in my $HOME from source and invoke it with a script that sets all the environmental variables (Ubuntu 16.04), --I prefer it to Anaconda because the latter installs other stuffs I don't need, but Anaconda is a lot easier to setup if you are not very experienced, --but I don't remove the system's python3.5, nor do I try to override it with update-alternatives.

---

### Post by monkeybrain20122 on 2019-04-15
Oops too late. Looks like already you have removed python2 and all the "autoremoves" hence broken your system. At this point may be a reinstallation is the least painful way. And why do you login as root?? Again this may be another reason that caused your issue in the first place.

---

### Post by monkeybrain20122 on 2019-04-15
> **ttrott101 said:**
> Python 2 end of life comes shortly and will be phased out switching apps that depend to Python 3. Python 2.7 In Ubuntu it has been corrupted for some time, bug was reported some time ago but apparently never addressed probably since conversion will soon take place to python 3. There are some appsm such as gimp and samba etc that depend on Python 2 and so that will take some time.** Perhaps completely removing Python 2.7 file and reinstalling from repos might solve your problem**.

This is a terrible advice.

---

### Post by ttrott101 on 2019-04-15
I don`t agree as many of the dependencies that some apps depend on are as we now speak being phased out due to the fact that the end of life is to take place 01/01/2020 for Python 2. I removed Python 2 with no adverse effects and I know Arch is removing dependencies and phasing it out also. More importantly why hasn`t Ubuntu fixed the problems with Python 2 as it was reported as a bug and I personally reported it as a corrupted file that was downloaded during installation of Xubuntu 18.04.2 even to the developers and if you search the report there has been no fix for some time now despite the fact that problems were reported many months ago. You are correct though, it was indeed not the best advice as I do not know what applications they are running nor the dependencies required for those apps. My apologies for that, I assume to much.

---

### Post by monkeybrain20122 on 2019-04-15
> **ttrott101 said:**
> I don`t agree as many of the dependencies that some apps depend on are as we now speak being phased out due to the fact that the end of life is to take place 01/01/2020 for Python 2. I removed Python 2 with no adverse effects and I know Arch is removing dependencies and phasing it out also..

Ubuntu is not Arch, Arch is a rolling release so it can replace components after it is released, but Ubuntu doesn't work that way. Debian based systems are much more rigid. If you change system python while the other things remain the same you have a broken system.

---

### Post by ttrott101 on 2019-04-16
I know that I use both those distros however therein lies the problem. Bugs don`t get fixed for an inordinate amount of time leaving the user to fix the problem and furthermore when the problem is system wide affecting all the flavors it then becomes an even bigger problem, to each their own I suppose. If I am not mistaken I believe I did apologize and agree with your assessment, still no excuse to not fix the bug for all users.

---

### Post by oldfred on 2019-04-16
With 18.04, you get python3.
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)
> **Python 2** is no longer installed by default. Python 3 has been updated to 3.6. This is the last LTS release to include Python 2 in main. 

But there are still many apps that have not converted. As soon as I installed some of my normal default list of additional apps python 2 was installs.
And at least one developer is so stubborn, he says he will always use python2, even if he has to maintain it himself.
[https://www.reddit.com/r/linux/comments/9wodtq/calibre_wont_migrate_to_python_3_author_says_i_am/](https://www.reddit.com/r/linux/comments/9wodtq/calibre_wont_migrate_to_python_3_author_says_i_am/)

---

### Post by monkeybrain20122 on 2019-04-16
> **oldfred said:**
> With 18.04, you get python3.
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)



That is strange

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic
$ which python
/usr/bin/python
$ python --version
Python 2.7.15rc1

```

---

### Post by rsteinmetz70112 on 2019-04-16
> **monkeybrain20122 said:**
> Oops too late. Looks like already you have removed python2 and all the "autoremoves" hence broken your system. At this point may be a reinstallation is the least painful way. And why do you login as root?? Again this may be another reason that caused your issue in the first place.

I haven't removed it, since there were so many dependencies. 
When I ```
# apt autoremove
``` I don't seen any packages to be removed.
When I ```
apt -remove python2.7
``` I see what I posted.
That's odd.
Typically when doing serious administration or trouble shooting I sudo -i to keep from typing sudo over and over again. I exit as soon as I'm finished.
I've been administering Unix systems for a long time so I'm comfortable as root.

---

### Post by rsteinmetz70112 on 2019-04-16
> **monkeybrain20122 said:**
> Well you haven't explained what your problem is, and why do you have so many versions of python2 and 3???
I tried to run ```
# do-release-upgrade 
```and[ the script failed to run see my other thread]("https://ubuntuforums.org/showthread.php?t=2416694") 
> DO NOT try to remove python-2.7 since it is a dependency for many system components and if you remove it your system will break beyond repair.
I haven't

> FYI 18.04 still uses python-2.7 as default so "upgrading" will not give you python3 as default, but it doesn't really matter though, as long as Ubuntu's team maintains it, the system's default python is just for maintenance, running and installing things.
That's why I need to fix this. The other versions of python were likely installed as dependencies of other packages. I didn't install them. IN fact the first part of the upgrade runs a script named bionic 
```
#!/usr/bin/python3

from DistUpgrade.DistUpgradeMain import main
import sys


if __name__ == "__main__":
    sys.exit(main())

```
that refers to python3 which is linked to python3.5
```
# ls -ld /usr/bin/python3
lrwxrwxrwx 1 root root 9 Mar 23  2016 /usr/bin/python3 -> python3.5

```
>  On the other hand you can use different versions of python in your work without tempering with the system's . But update-alternatives is NOT the way to do it because many system components are compiled based on the version that comes with the system, and by changing the default via update alternatives again you break your system (**that is probably what caused your issue in the first place**)
The default has not been changed on purpose.

> There are many ways to use different versions of python safely, e.g anaconda or virtualenv. I compiled python3.7 in my $HOME from source and invoke it with a script that sets all the environmental variables (Ubuntu 16.04), --I prefer it to Anaconda because the latter installs other stuffs I don't need, but Anaconda is a lot easier to setup if you are not very experienced, --but I don't remove the system's python3.5, nor do I try to override it with update-alternatives.
I haven't done any of that.

---

### Post by oldfred on 2019-04-16
Python will be python2 as link. Not sure if they can change that as then it would break python2 apps.
But default install will not include python2, just python3. But many apps still use python2, so it gets installed with that app.
Updated apps will specify python3, so they do not call python.

---

### Post by rsteinmetz70112 on 2019-04-16
> **oldfred said:**
> Python will be python2 as link. Not sure if they can change that as then it would break python2 apps.
But default install will not include python2, just python3. But many apps still use python2, so it gets installed with that app.
Updated apps will specify python3, so they do not call python.

That's how I understand it except:
```
# ls -ld python
lrwxrwxrwx 1 root root 9 Nov 23  2017 python -> python2.7
# ls -ld python2
lrwxrwxrwx 1 root root 9 Nov 23  2017 python2 -> python2.7
# ls -ld python3
lrwxrwxrwx 1 root root 9 Mar 23  2016 python3 -> python3.5
```

My remaining 16.04 LTS computers are all like this.

---

### Post by dragonfly41 on 2019-04-16
Be aware that if on Ubuntu 16.04 python > 3.5 (such as 3.6) is installed, gnome-terminal ceases to launch. In Ubuntu 16.04 it depends on python 3.5 and does not run in 3.6. For this reason I now use virtualenv to switch between 2.7, 3.5, 3.6.

---

### Post by rsteinmetz70112 on 2019-04-16
> **dragonfly41 said:**
> Be aware that if on Ubuntu 16.04 python > 3.5 (such as 3.6) is installed, gnome-terminal ceases to launch. In Ubuntu 16.04 it depends on python 3.5 and does not run in 3.6. For this reason I now use virtualenv to switch between 2.7, 3.5, 3.6.

As far as I can see python3.6 is not installed on my systems, python 3.5 is.

---

### Post by rsteinmetz70112 on 2019-04-23
I've been reinstalling python packages. I finally got lucky. I reinstalled  python3-pkg-resources and things seem to be working.

```
 apt install --reinstall python3-pkg-resources
```

Now to se if do-release-upgrade runs. Unfortunately it will be some time before I can test it.

---

