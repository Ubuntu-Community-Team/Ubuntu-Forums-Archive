---
title: "Error with apt-get"
date: 2007-05-13
forum: General Help
---

### Post by kmslinux on 2007-05-13
Every time I 'apt-get', it says this message.
```
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog evolution-common krdc krfb kppp libktnef1 konversation
  kubuntu-default-settings libkscan1 supertux-data gcalctool libopenal0a
  kdeprint gnome-nettool ksvg kscreensaver epiphany-browser libdc1394-13
  openoffice.org-impress libavahi-compat-libdnssd1 kio-locate libk3b2
  libpythonize0 vorbis-tools libxvidcore4 openoffice.org-draw ksnapshot
  liblockdev1 kdebluetooth kooka gucharmap libkipi0 industrial-cursor-theme
  gnome-games mplayer-skins libkcal2b libflac++5c2 evolution
  openoffice.org-kde libsane esound libexchange-storage1.2-3 gnome-cards-data
  kdegraphics-kfile-plugins libgtksourceview1.0-0 konqueror-nsplugins gedit
  gwenview bluez-cups libpoppler1-qt kdepim-kio-plugins brltty libieee1284-3
  libqt4-qt3support hwdb-client-kde libpisock9 qca-tls libmimelib1c2a klipper
  gnome-themes kubuntu-artwork-usplash kontact libsqlite0
  kdeadmin-kfile-plugins whois ksmserver ksysguard kde-icons-mono
  libavformat0d kmenuedit pykdeextensions gtkhtml3.14 ksplash-engine-moodin
  kubuntu-konqueror-shortcuts ksplash libkleopatra1 gedit-common gnome-utils
  kipi-plugins korganizer k3b kdenetwork-kfile-plugins libgnome-pilot2 kbstate
  akregator kio-apt kwin-style-crystal bluez-utils arts
  fast-user-switch-applet kcron libjasper-runtime hwdb-client-common
  gnome-volume-manager libgmp3c2 openoffice.org-math eog libggi2
  gnome-backgrounds libgii1 libksieve0 digikam bug-buddy tuxtype-data
  speedcrunch libkpimidentities1 kpf bogofilter-bdb libkdepim1a
  libgtksourceview-common kdnssd vino libphysfs-1.0-0 gnome-keyring-manager
  kdemultimedia-kfile-plugins katapult poster kdenetwork-filesharing
  kubuntu-docs knotes libbluetooth2 bogofilter gnome-games-data kde-guidance
  libqt4-sql libifp4 libgii1-target-x fping libgsl0 libgsm1 khelpcenter
  totem-gstreamer kaddressbook libkpimexchange1 kmailcvt libgnomevfs2-bin
  rdiff-backup knetworkconf ksysguardd konq-plugins libkmime2 psutils
  language-selector-qt gnome-core qobex libavcodec0d xorg ktorrent libgpgme11
  scim-qtimm gconf-editor libtotem-plparser1 gnome-system-tools kopete karm
  kate kmail keep gstreamer0.10-gnomevfs totem bogofilter-common
  openoffice.org-calc kde-guidance-powermanager python-gnome2-desktop
  kde-systemsettings libmpcdec3 liblame0 librsync1 kmousetool kmag bluez-pin
  libgtkhtml3.14-19 kdepim-kresources kdepim-wizards kmilo python-kde3
  sound-juicer libpisync0 kdepasswd kmix libfaac0
Use 'apt-get autoremove' to remove them.
```
What the heck?! I *need* all that stuff!

---

### Post by zvacet on 2007-05-13
I don´t know.Ttry 

```
sudo aptitude update && sudo aptitude upgrade
```

and see if it help

---

### Post by aidanr on 2007-05-13
you probably installed kubuntu-desktop, went to remove some program that came with and had to remove the kubuntu-desktop metapackage in order to do that and now it thinks you wanted to get rid of kubuntu-desktop and all that you installed with it

---

### Post by kmslinux on 2007-05-13
Well now I think my apt-get is broken.  I tried installing something and it said "E: Broken Packages"

---

### Post by zvacet on 2007-05-13
**synaptic>edit<fix broken packages**

---

### Post by kmslinux on 2007-05-14
> **zvacet said:**
> **synaptic>edit<fix broken packages**

I Googled around and found that already but it didn't work. More specifically, it didn't show any sign of doing anything. Do you know the command-line equivalent of "fix broken packages"?

Edit: By the way, the long "apt-get autoremove" message was removed after I "apt-get install kubuntu-desktop"-ed. For some strange reason unbeknownst to me it deleted KDE.

---

### Post by pianoboy3333 on 2007-05-14
If you need the stuff then just ignore it, I had something like that in edgy, it's no big deal, it's not gonna harm your system. Sometimes that shows up for programs you compiled that depend on some libraries you manually installed, etc.

---

### Post by wwoollff on 2007-05-15
I have the same problem, but I cannot ignore the problem.For some reason, konqueror is missing.When I try to install it, it says that kcontrol,kfind ... don't have all the dependencies :( and that they are 'broken packages'

---

### Post by az on 2007-05-15
The autoremove message is independant of the broken packages message.

run
sudo apt-get -f install

and post the result.

If it says to run

sudo dpkg --configure -a

run

sudo dpkg --configure -a

---

### Post by wwoollff on 2007-05-15
:)) that would be great;))

here's my 'apt-get -f install'

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  knetwalk kpat ksokoban kolf korn libattr1-dev kshisen kmahjongg
  klaptopdaemon ksig kdelibs4-dev ksim kwifimanager kcharselect kjumpingcube
  kdessh ktip libaspell-dev libtunepimp-bin kspy katomic libcvsservice0
  kleopatra kdesdk-kio-plugins kdegames-card-data kgoldrunner kbackgammon
  kpoker dirmngr kdepim-kfile-plugins libicu36 libstlport5.1 kenolaba
  kblackbox konsolekalendar libpcre3-dev kfloppy ksame kpager kapptemplate
  liblualib50-dev libkdegames1 kcalc libapr0 kandy libnspr4-0d
  kdemultimedia-kappfinder-data libkexiv2-0 ksirc librss1 klickety libkrb5-dev
  qt3-dev-tools libsasl2-dev linux-headers-2.6.17-11-generic libogg-dev
  libjasper-1.701-dev libwavpack0 mpeglib kicker-applets kdict libpcrecpp0
  ktnef khexedit libsvn0 kedit kbounce kdesdk-kfile-plugins liblua50-dev tidy
  libtidy-0.99-0 lua50 libavahi-qt3-dev libdb4.3++c2 ktron libacl1-dev ksync
  cvs libqt3-mt-dev hspell kwin4 libxslt1-dev libssl-dev kreversi kdf libksba8
  libxmu-dev kspaceduel gnupg-agent kbugbuster juk klines lskat
  openoffice.org-hyphenation libarts1-mpeglib kaddressbook-plugins kcachegrind
  libtiff4-dev networkstatus libwps-0.1-1 kaboodle libindex0 libqt3-headers
  libtiffxx0c2 liblcms1-dev ksmiletris libkadm55 poxml libarts1-audiofile
  kbattleship kpilot kasteroids myspell-en-za kompare kfouleggs libmyspell3c2
  libmal1 linux-headers-2.6.17-11 libkgantt0 knewsticker ksnake libsynaptics0
  kunittest kappfinder libopenexr-dev kdesdk-misc kdelirc kjots libmng-dev
  ksirtet kmines kget pinentry-qt desktop-file-utils kdesdk-scripts
  libcupsys2-dev kgpg libvorbis-dev konquest kate-plugins libnss3-0d gpgsm
  gnupg2 kdeaddons-kfile-plugins x-dev gettext-kde kuiviewer libarts1-xine
  libidn11-dev ktuberling ktimer kmid libarts1-dev kmtrace
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
```

ok...and now 'sudo apt-get install konqueror'

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  konqueror: Depends: kcontrol (= 4:3.5.6-0ubuntu20) but 4:3.5.6-0ubuntu20.1 is to be installed
             Depends: kdebase-kio-plugins (= 4:3.5.6-0ubuntu20) but 4:3.5.6-0ubuntu20.1 is to be installed
             Depends: kdesktop (= 4:3.5.6-0ubuntu20) but 4:3.5.6-0ubuntu20.1 is to be installed
             Depends: kfind (= 4:3.5.6-0ubuntu20) but 4:3.5.6-0ubuntu20.1 is to be installed
E: Broken packages

```

and thx for all your help

---

### Post by az on 2007-05-15
Do you have mixed repos in your sources.list?  You should only have one version of Ubuntu there.  You shouldn't mix debian and Ubuntu repos, either.

The apt-get -f install reveals no broken packages.

Other than that, have you run an

sudo apt-get update
first?

---

### Post by wwoollff on 2007-05-17
fixed. I've found a repository from kubuntu.org for kde 3.5.6,  and know it works perfectly. thx alot.

---

### Post by kmslinux on 2007-05-20
I've fixed everything; all I had to do was downgrade a package so it would be compatible.

---

