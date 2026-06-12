---
title: "nemo : Depends: libxapp1 but it is not installable"
date: 2017-11-23
forum: General Help
---

### Post by jamaas on 2017-11-23
I'm stuck trying to install new nemo on 16.04, getting these errors.  I'd be pleased to go back to 2.8 if I could but would be nice to find conflict and get this one working.  Can anyone tell me the correct version to get that runs on gnome?

Thanks

J

The following packages have unmet dependencies.
 nemo : Depends: libxapp1 but it is not installable
        Recommends: nemo-fileroller but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by mc4man on 2017-11-23
It's not installable (libxapp1) because it's not in 16.04 repos.
Have you ever used either of these 2 ppa's? (nemo from the first one requires libxapp1..
[https://launchpad.net/~embrosyn/+archive/ubuntu/cinnamon](https://launchpad.net/~embrosyn/+archive/ubuntu/cinnamon)
[https://launchpad.net/~embrosyn/+archive/ubuntu/xapps](https://launchpad.net/~embrosyn/+archive/ubuntu/xapps)

Post 
```
apt policy nemo 
```
```
apt show nemo 
```

---

### Post by jamaas on 2017-11-24
Thanks Mc4man, No I've not tried either of these.  If I understand correctly what you are saying is that attempting to install for the top one  ..../cinnamon will not work because it will need the libxapp1 library?  Is that correct?  Will downloading/installing from the bottom  .../xapps is likely to work?

Thanks
J

$ apt policy nemo
nemo:
  Installed: 2.8.6-2
  Candidate: 3.6.4-1~webupd8~xenial02
  Version table:
     3.6.4-1~webupd8~xenial02 500
        500 [http://ppa.launchpad.net/webupd8team/nemo3/ubuntu](http://ppa.launchpad.net/webupd8team/nemo3/ubuntu) xenial/main amd64 Packages
 *** 2.8.6-2 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

    
$ apt show nemo
Package: nemo
Version: 3.6.4-1~webupd8~xenial02
Priority: optional
Section: gnome
Maintainer: Jacob Zimmermann <ppa@jzimm.net>
Original-Maintainer: Linux Mint <root@linuxmint.com>
Installed-Size: 4,598 kB
Depends: libatk1.0-0 (>= 1.32.0), libc6 (>= 2.14), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdbusmenu-glib4 (>= 0.4.2), libexempi3 (>= 2.2.0), libexif12 (>= 0.6.21-1~), libgail-3-0 (>= 3.0.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.41.1), libgnome-desktop-3-12 (>= 3.18.1), libgtk-3-0 (>= 3.9.12), libnemo-extension1, libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libunity9 (>= 3.8.4), libx11-6, libxapp1, libxml2 (>= 2.7.4), libzeitgeist-1.0-1 (>= 0.3.14), dconf-gsettings-backend | gsettings-backend, nemo-data (= 3.6.4-1~webupd8~xenial02), shared-mime-info (>= 0.50), desktop-file-utils (>= 0.7), gvfs (>= 1.3.2), libglib2.0-data, gsettings-desktop-schemas, cinnamon-l10n
Recommends: eject, librsvg2-common, gvfs-backends, nemo-fileroller
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, xdg-user-dirs
Conflicts: nemo-data (<< 2.2.4-2~)
Breaks: gnome-bluetooth (<< 3.0), gnome-session (<< 2.28), gnome-volume-manager (<< 2.24), rhythmbox (<< 0.12)
Download-Size: 897 kB
APT-Sources: [http://ppa.launchpad.net/webupd8team/nemo3/ubuntu](http://ppa.launchpad.net/webupd8team/nemo3/ubuntu) xenial/main amd64 Packages
Description: File manager and graphical shell for Unity
 Nemo is the official file manager for the Cinnamon desktop.
 This Nemo package includes Unity-specific patches (should also work
 with GNOME, Xfce). It allows to browse directories, preview files
 and launch applications associated with them. It is also responsible
 for handling the icons on the Cinnamon desktop. It works on local
 and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.

N: There is 1 additional record. Please use the '-a' switch to see it

---

### Post by mc4man on 2017-11-24
The deal is the webupd8team/nemo3 ppa has set a dep on libxapp1 but isn't providing libxapp1. I've contacted the maintainer about this.
You could,
Wait for ppa to address
Install libxapp1 & nemo from the 2nd ppa listed above (ppa-purge webupd8 ppa if anything was installed from it
Keep webupd8 ppa but see if libxapp1 from other ppa works
Remove the webupd8 ppa & install the Ubuntu version of nemo.

---

