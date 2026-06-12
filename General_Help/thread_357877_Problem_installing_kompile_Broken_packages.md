---
title: "Problem installing kompile: Broken packages"
date: 2007-02-10
forum: General Help
---

### Post by abhiomkar on 2007-02-10
hi,
I have recently installed kubuntu-desktop. I couldn't able to install kompile, because of the Broken Packages

```
~$ sudo apt-get install kompile
Password:
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
  kompile: Depends: kdesu but it is not installable
E: Broken packages


```

Lets try installing kompile using aptitude , i get this ....

```

~$ sudo aptitude install kompile
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  kompile
The following packages are unused and will be REMOVED:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater amarok
  amarok-xine apt-index-watcher ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam
  digikamimageplugins flac gtk2-engines-gtk-qt hwdb-client-kde karm katapult kate kaudiocreator kbstate kcron
  kde-guidance kde-guidance-powermanager kde-icons-mono kde-systemsettings kdeadmin-kfile-plugins
  kdebluetooth kdemultimedia-kfile-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kresources kdepim-wizards kdm kdnssd keep khelpcenter kio-apt kio-locate kitchensync klipper kmag
  kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knode knotes
  koffice-data koffice-libs konq-plugins konqueror-nsplugins kontact konversation kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb krita krita-data kscd kscreensaver kscreensaver-xsavers
  ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager
  kwin-style-crystal language-selector-qt latex-xft-fonts libavahi-compat-libdnssd1 libexif-dev libgmp3c2
  libgphoto2-2-dev libgsl0 libifp4 libkpimexchange1 libnjb5 libopenobex1 libpythonize0 libqt-perl libqt4-core
  libqt4-gui libqt4-qt3support libqt4-sql librsync1 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp3
  ncompress openoffice.org-kde p7zip-full pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4
  python2.4-dev qca-tls qobex qt4-qtconfig rdiff-backup scim-qtimm skim speedcrunch wlassistant zoo
The following packages have been automatically kept back:
  fuse-utils libfuse2 libntfs-3g0 linux-image-generic linux-restricted-modules-common
  linux-restricted-modules-generic
The following packages have been kept back:
  bind9-host dnsutils libbind9-0 libdns21 libisc11 libisccc0 libisccfg1 liblwres9 libsmbclient libwnck-common
  linux-generic linux-headers-generic ntfs-3g samba-common smbclient wine
0 packages upgraded, 1 newly installed, 134 to remove and 22 not upgraded.
Need to get 175kB of archives. After unpacking 352MB will be freed.
The following packages have unmet dependencies:
  kompile: Depends: kdesu which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
kompile [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?] n
Resolving dependencies...

*** No more solutions available ***

The following actions will resolve these dependencies:

Keep the following packages at their current version:
kompile [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?]q
```


What iam gonna do now ? :guitar: 
:D
Help ? :confused:

---

### Post by ingo on 2007-02-11
The kdesu dependency from kompile is your downfall, compare [http://packages.ubuntulinux.org/edgy/kde/kompile](http://packages.ubuntulinux.org/edgy/kde/kompile)

How to resolve that? Is it worth it? Up to you...

---

