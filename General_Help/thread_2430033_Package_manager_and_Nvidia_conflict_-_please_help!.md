---
title: "Package manager and Nvidia conflict - please help!"
date: 2019-10-26
forum: General Help
---

### Post by Daniel_Rosehill on 2019-10-26
I attempted to upgrade form Ubuntu 19.04 to 19.10. After the upgrade, my Nvidia driver seemed totally dead and I only had one low resolution default display active.

Unfortunately, before using Timeshift to roll back to a previous snapshot, I attempted to change the Nvidia driver in the hope of fixing the problem.

Now, when I try to install packages, I am presented with this error.

I can't make sense of the web of conflicts and dependencies. If anybody can and could point me in the right direction I would be very grateful!

**
```

sudo apt-get install git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'git' instead of 'git-core'
git is already the newest version (1:2.20.1-2ubuntu1).
git set to manually installed.
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 dconf-gsettings-backend : Depends: dconf-service (< 0.30.1-2.1~)
 dconf-service : Depends: libdconf1 (= 0.34.0-1) but 0.30.1-2 is to be installed
 gir1.2-atk-1.0 : Depends: libatk1.0-0 (>= 2.33.1) but 2.32.0-1 is to be installed
 gir1.2-gdkpixbuf-2.0 : Depends: libgdk-pixbuf2.0-0 (>= 2.39.2) but 2.38.1+dfsg-1 is to be installed
 gir1.2-udisks-2.0 : Depends: libudisks2-0 (>= 2.8.3) but 2.8.2-1 is to be installed
 iptables : Depends: libip4tc2 (= 1.8.3-2ubuntu5) but it is not installable
            Depends: libip6tc2 (= 1.8.3-2ubuntu5) but it is not installable
            Depends: libiptc0 (= 1.8.3-2ubuntu5) but 1.6.1-2ubuntu3 is to be installed
            Depends: libxtables12 (= 1.8.3-2ubuntu5) but 1.6.1-2ubuntu3 is to be installed
            Depends: libnftnl11 (>= 1.1.3) but it is not going to be installed
 libdrm-dev : Depends: libdrm-intel1 (= 2.4.97-1ubuntu1) but 2.4.99-1ubuntu1 is to be installed
              Depends: libdrm-radeon1 (= 2.4.97-1ubuntu1) but 2.4.99-1ubuntu1 is to be installed
 libegl-mesa0 : Depends: libgbm1 (= 19.0.8-0ubuntu0~19.04.1) but 19.2.1-1ubuntu1 is to be installed
 libgdk-pixbuf2.0-dev : Depends: gir1.2-gdkpixbuf-2.0 (= 2.38.1+dfsg-1) but 2.40.0+dfsg-1build1 is to be installed
 libgl1-mesa-dri : Depends: libllvm9 (>= 1:9~svn298832-1~) but it is not installable
 libgl1-mesa-dri:i386 : Depends: libllvm9:i386 (>= 1:9~svn298832-1~) but it is not installable
 libkf5dnssd5 : Depends: libkf5dnssd-data (= 5.62.0-0ubuntu1) but 5.56.0-0ubuntu1 is to be installed
 libmagick++-6-headers : Depends: libmagickwand-6-headers (= 8:6.9.10.23+dfsg-2.1ubuntu3) but 8:6.9.10.14+dfsg-7ubuntu2.2 is to be installed
                         Depends: libmagickcore-6-headers (= 8:6.9.10.23+dfsg-2.1ubuntu3) but 8:6.9.10.14+dfsg-7ubuntu2.2 is to be installed
                         Depends: imagemagick-6-common (= 8:6.9.10.23+dfsg-2.1ubuntu3) but 8:6.9.10.14+dfsg-7ubuntu2.2 is to be installed
 libmagick++-6.q16-dev : Depends: libmagick++-6-headers (= 8:6.9.10.14+dfsg-7ubuntu2.2) but 8:6.9.10.23+dfsg-2.1ubuntu3 is to be installed
 libnvidia-decode-418 : Conflicts: libnvidia-decode
                        Conflicts: libnvidia-decode:i386
 libnvidia-decode-418:i386 : Conflicts: libnvidia-decode
                             Conflicts: libnvidia-decode:i386
 libnvidia-decode-430 : Depends: libnvidia-compute-430 (= 430.50-0ubuntu2) but it is not installable
                        Conflicts: libnvidia-decode
                        Conflicts: libnvidia-decode:i386
 libnvidia-decode-430:i386 : Depends: libnvidia-compute-430:i386 (= 430.50-0ubuntu2) but it is not installable
                             Conflicts: libnvidia-decode
                             Conflicts: libnvidia-decode:i386
 libnvidia-ifr1-418 : Conflicts: libnvidia-ifr1
                      Conflicts: libnvidia-ifr1:i386
 libnvidia-ifr1-418:i386 : Conflicts: libnvidia-ifr1
                           Conflicts: libnvidia-ifr1:i386
 libnvidia-ifr1-430 : Depends: libnvidia-gl-430 but it is not installable
                      Conflicts: libnvidia-ifr1
                      Conflicts: libnvidia-ifr1:i386
 libnvidia-ifr1-430:i386 : Depends: libnvidia-gl-430:i386 but it is not installable
                           Conflicts: libnvidia-ifr1
                           Conflicts: libnvidia-ifr1:i386
 libpango1.0-0 : Depends: libpango-1.0-0 (= 1.42.4-6ubuntu0.1) but 1.42.4-7 is to be installed
 libpython-stdlib : Depends: libpython2-stdlib (= 2.7.16-1) but 2.7.17-1 is to be installed
 libpython2-stdlib : Depends: libpython2.7-stdlib (>= 2.7.17~rc1-1~) but 2.7.16-2ubuntu0.2 is to be installed
 libqapt3-runtime : Depends: libapt-pkg5.90 (>= 1.9~) but it is not installable
 libqca-qt5-2-plugins : Depends: libqca-qt5-2 (= 2.2.1-1) but 2.1.3-2ubuntu2 is to be installed
 libqmi-proxy : Depends: libqmi-glib5 (= 1.22.0-1.2) but 1.22.4-0.1 is to be installed
 libqt5xmlpatterns5 : Depends: qtbase-abi-5-12-4 but it is not installable
 libwmf-dev : Depends: libwmf0.2-7 (= 0.2.8.4-14) but 0.2.8.4-15 is to be installed
 libx11-dev : Depends: libx11-6 (= 2:1.6.8-1) but 2:1.6.7-1 is to be installed
 libzbar-dev : Depends: libzbar0 (= 0.21-3) but 0.23-1.1 is to be installed
 mate-menus : Depends: gir1.2-matemenu-2.0 (>= 1.22.1-0ubuntu1) but it is not going to be installed
 parted : Depends: libparted2 (= 3.2-26) but 3.2-25 is to be installed
 php-bz2 : Depends: php7.3-bz2 but it is not installable
 php7.3-readline : Depends: php7.3-common (= 7.3.8-1) but it is not installable
 plymouth : Depends: libplymouth4 (>= 0.9.4git20190712) but 0.9.4-1ubuntu1 is to be installed
 plymouth-label : Depends: plymouth (= 0.9.4-1ubuntu1) but 0.9.4git20190712-0ubuntu4 is to be installed
 plymouth-theme-ubuntu-logo : Depends: plymouth (= 0.9.4-1ubuntu1) but 0.9.4git20190712-0ubuntu4 is to be installed
 plymouth-theme-ubuntu-text : Depends: plymouth (= 0.9.4-1ubuntu1) but 0.9.4git20190712-0ubuntu4 is to be installed
 python-zbar : Depends: libzbar0 (= 0.21-3) but 0.23-1.1 is to be installed
 python2 : Depends: libpython2-stdlib (= 2.7.16-1) but 2.7.17-1 is to be installed
 python2.7 : Depends: python2.7-minimal (= 2.7.17~rc1-1) but 2.7.16-2ubuntu0.2 is to be installed
             Depends: libpython2.7-stdlib (= 2.7.17~rc1-1) but 2.7.16-2ubuntu0.2 is to be installed
 python2.7-dev : Depends: python2.7 (= 2.7.16-2ubuntu0.2) but 2.7.17~rc1-1 is to be installed
 python3 : PreDepends: python3-minimal (= 3.7.5-1) but 3.7.3-1 is to be installed
           Depends: python3.7 (>= 3.7.5~rc1-1~) but 3.7.3-2ubuntu0.2 is to be installed
           Depends: libpython3-stdlib (= 3.7.5-1) but 3.7.3-1 is to be installed
 python3-dev : Depends: python3 (= 3.7.3-1) but 3.7.5-1 is to be installed
 qapt-batch : Depends: libqapt3-runtime (= 3.0.4-1ubuntu1) but 3.0.4-1ubuntu4 is to be installed
 qapt-deb-installer : Depends: libqapt3-runtime (= 3.0.4-1ubuntu1) but 3.0.4-1ubuntu4 is to be installed
 qdbus-qt5 : Depends: qtbase-abi-5-12-4 but it is not installable
 vlc : Depends: vlc-bin (= 3.0.8-0ubuntu19.04.1) but 3.0.8-2 is to be installed
 vlc-bin : Depends: libvlc-bin (= 3.0.8-2) but 3.0.8-0ubuntu19.04.1 is to be installed
 xserver-xorg-core : Depends: xserver-common (>= 2:1.20.5+git20191008-0ubuntu1) but 2:1.20.4-1ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by mörgæs on 2019-10-26
Quoting your output:

> **Daniel_Rosehill said:**
> 
```

E: Unmet dependencies. Try 'apt --fix-broken install' with no packages...
```

Not sure that it helps but worth a try before a clean reinstall of 19.10.

---

### Post by Daniel_Rosehill on 2019-10-27
Pleased to report that Timeshift saved the day (and thank goodness I have daily and weekly restore points). Weirdly enough, restoring via the GUI did not fix the problem or revert the driver. But I dropped to a shell in advanced options and gave the CLI a shot. Same restore point but for some reason only the latter fixed everything.
I'm now back to where I was with a fully functional 19.04.

---

