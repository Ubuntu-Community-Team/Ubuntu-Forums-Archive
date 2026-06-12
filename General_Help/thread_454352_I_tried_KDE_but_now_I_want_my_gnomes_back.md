---
title: "I tried KDE but now I want my gnomes back"
date: 2007-05-25
forum: General Help
---

### Post by the lemming on 2007-05-25
I managed to kick out all my little gnomes this morning and now I've decided I want them back.

Could somebody please tell me how to get rid of KDE please?

---

### Post by olieviya on 2007-05-25
You can have both KDE and Gnome if you like or just gnome or just KDE, all you need is to use Synaptic or apt-get to install/remove the ones you want to.

---

### Post by the lemming on 2007-05-25
> **olieviya said:**
> You can have both KDE and Gnome if you like or just gnome or just KDE, all you need is to use Synaptic or apt-get to install/remove the ones you want to.

Which packages do I get rid of?

There seems to be n awful lot of stuff in the synaptic package panager.

---

### Post by Happy_Man on 2007-05-25
if you installed KDE using Aptitude from Ubuntu:

```
sudo aptitude remove kubuntu-desktop
```

Or, if you didn't...
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools && sudo apt-get install ubuntu-desktop
```

---

### Post by the lemming on 2007-05-25
Hello

I tried both commands but got error messages

A couple of which are 


E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?




Seeing as it was fairly straight forward to install KDE I would have thought that getting gnome back was a simple process.

Would it be better to do a fresh install of ubuntu?

---

### Post by Arisna on 2007-05-25
You have to close Adept/Synaptic/whatever software manager you have open before you will be able to run the commands posted above.

---

### Post by merlinus on 2007-05-25
FWIW, I ran into the same problems.  I did a re-install.

Something to think about though, is creating a separate /home partition.

-merlin

---

### Post by the lemming on 2007-05-25
> **Happy_Man said:**
> if you installed KDE using Aptitude from Ubuntu:

```
sudo aptitude remove kubuntu-desktop
```

Or, if you didn't...
[code]sudo apt-get remove adept 

I tried both commands again but still booted into kubuntu.

Looks like my only option is to reinstall ubuntu.  Which is not a problem because I'm still learning what's going on.

---

### Post by ChameleonDave on 2008-03-25
> **the lemming said:**
> I tried both commands again but still booted into kubuntu.

Looks like my only option is to reinstall ubuntu.  Which is not a problem because I'm still learning what's going on.

What do you mean, "booted into kubuntu"?  Kubuntu is not an operating system separate from Ubuntu.  I suspect that you mean that you booted into Ubuntu and the splash screen and/or log-in manager used Kubuntu branding.  If so, you need to realise that all that is just cosmetic.

---

### Post by knutschr on 2008-03-25
> **the lemming said:**
> I tried both commands again but still booted into kubuntu.

Looks like my only option is to reinstall ubuntu.  Which is not a problem because I'm still learning what's going on.

You don't see anything about that you have removed Gnome, just added KDE,
In that case you should still have the option in login screen under Sessions to choose Gnome.

---

