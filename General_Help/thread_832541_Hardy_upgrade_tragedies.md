---
title: "Hardy upgrade tragedies"
date: 2008-06-17
forum: General Help
---

### Post by Excalibre on 2008-06-17
Okay, maybe the title is a bit of an exaggeration, but after downloading everything, and installing virtually everything, the upgrader said it couldn't install something (virtualbox, which I think was as a result of me accidentally telling it NOT to upgrade it earlier when it popped up a prompt warning me I'd lose my snapshots.) A dialog box popped up saying the upgrade was aborting and it might leave my system in an unusable state and a recovery tool would run, which it didn't. I restarted. It seems to think I'm running Hardy now, but it didn't finish the cleanup. What do I do? Everything's working okay, and I think it's just the "cleanup" step that didn't go, but I'd feel better if I knew everything was right.

Also, I had installed kubuntu-desktop before, just to screw around with KDE. That's still installed and Synaptic claims I don't have it installed (or KDE, or KDE4), presumably because what I do have is an earlier version than what's in the Hardy repositories. I tried removing kubuntu-desktop with aptitude, and that worked, but all the included KDE applications are still there. How do I dig all of KDE out of my system?

---

### Post by ibuclaw on 2008-06-17
Here is a very, very, very long command that should purify you from KDE. :)
```
sudo aptitude purge adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop
```
[EDIT]
Run the altered above command instead. You'll want to **purge** the applications (remove all residual config), else, there would be a lot of unused clutter on your system.

Also, if you are sure that you don't use any KDE apps on your Gnome system (such as amarok), you should remove these directories too.
```
ls -lA ~/ | grep kde
```
They'll be located in your home (/home/**name**/) directory.


Regards
Iain

---

### Post by Excalibre on 2008-06-17
Heh, okay, thanks.

---

### Post by mezhaka on 2008-06-21
how is your ubuntu doing? any more problems scince? i just saw this "unusable state" on my own pc (and a bunch of errors) and now afraid to reboot.

---

### Post by Excalibre on 2008-06-21
> **mezhaka said:**
> how is your ubuntu doing? any more problems scince? i just saw this "unusable state" on my own pc (and a bunch of errors) and now afraid to reboot.
I ended up doing a fresh install of Hardy on another partition, and that's working fine. :-) Far as I could tell, though, the upgraded one, despite the dire warning, was working okay. I don't know if yours is, but I'll cross my fingers.

---

