---
title: "How to remove a desktop environment in favor of another"
date: 2008-05-09
forum: General Help
---

### Post by jis on 2008-05-09
Referring to [a closed thread]("http://ubuntuforums.org/showthread.php?t=761557&highlight=remove+kubuntu-desktop+hardy"), I wonder why 'sudo apt-get autoremove kubuntu-desktop' does not remove all applications installed by 'sudo apt-get install kubuntu-desktop'? On the other hand, I wouldn't want to remove xorg, for instance, if I am running the command from GUI.

I couldn't remove all of them by removing everythin from "Kde Desktop Environment" group by Synaptic. E.g. KTorrent is still installed.

---

### Post by NightwishFan on 2008-05-09
(this is for hardy)

I believe the code to remove kubuntu and add ubuntu is:
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop
```
Just remove the ```
&& sudo apt-get install ubuntu-desktop
``` at the end if you have ubuntu already installed.

---

### Post by jis on 2008-05-09
More instructions seem to be at [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/). See Pure Gnome, Pure KDE and Pure XFCE.

(I have xubuntu-desktop installed and going to remove kubuntu specific packages.)

---

### Post by jis on 2008-05-09
It seems that the "Pure XFCE" instructions for removing Kubuntu removes too much packages from my point of view, such as ekiga, skype, gxine, qamix, links2, vlc and alsaplayer-common even though those are not part of kubuntu-desktop and they are not automatically installed. I think it would be better to remove certain subset of kubuntu-desktop's dependencies and remove further dependencies only, if they are not needed elsewhere by using 'sudo apt-get autoremove'.

---

### Post by anaconda on 2008-05-09
> **jis said:**
> Referring to [a closed thread]("http://ubuntuforums.org/showthread.php?t=761557&highlight=remove+kubuntu-desktop+hardy"), I wonder why 'sudo apt-get autoremove kubuntu-desktop' does not remove all applications installed by 'sudo apt-get install kubuntu-desktop'? On the other hand, I wouldn't want to remove xorg, for instance, if I am running the command from GUI.

I couldn't remove all of them by removing everythin from "Kde Desktop Environment" group by Synaptic. E.g. KTorrent is still installed.

Kubuntu-desktop is a meta-packkage, which just depends on the whole kubuntu.. if you remove kubuntu-desktop, then you only remove that meta-packkage and nothing else. SO all kubuntu programs remain..

The same goes with ubuntu-desktop, and xubuntu-desktop..

---

### Post by jis on 2008-05-09
I undestand, but I suppose not all of the packages listed to remove by Aysiu are independent of each other. I think there could be applied "sudo apt-get autoremove" somehow.

---

