---
title: "Failed to fetch, Connection Failed in apt-get"
date: 2006-07-03
forum: General Help
---

### Post by programgeek on 2006-07-03
Here is my sources.list (I've tried to plain one, and a few others, to no avail)
```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
## only uncomment it if you need it
## deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
## deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

## Dapper PLF
## only uncomment it if you need it
## deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb http://wine.budgetdedicated.com/apt dapper main
## deb-src http://wine.budgetdedicated.com/apt dapper main

## skype (official)
## only uncomment it if you need it
## deb http://download.skype.com/linux/repos/debian/ stable non-free

```

and here are my errors
```
tony@tony-laptop:~$ sudo apt-get update
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 85.133.25.7 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 85.133.25.7 80]
Ign http://security.ubuntu.com dapper-security Release
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 85.133.25.7 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Ign http://archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://archive.ubuntu.com dapper/restricted Sources
Ign http://security.ubuntu.com dapper-security/multiverse Sources
Ign http://archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/multiverse Packages
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://archive.ubuntu.com dapper/multiverse Sources
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/main Packages
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/main Sources
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Err http://security.ubuntu.com dapper-security/multiverse Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-backports/main Packages
Ign http://archive.ubuntu.com dapper-backports/restricted Packages
Ign http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://archive.ubuntu.com dapper-backports/main Sources
Ign http://archive.ubuntu.com dapper-backports/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/universe Sources
Ign http://archive.ubuntu.com dapper-backports/multiverse Sources
Err http://archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/universe Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/multiverse Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/main Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/universe Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/main Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/restricted Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/universe Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Sources
  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  Connection failed [IP: 85.133.25.7 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  Connection failed [IP: 85.133.25.7 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
tony@tony-laptop:~$

```

It happens on my laptop and desktop.  It's quite curious.  Quite. :O

[http://www.ubuntuforums.org/showthread.php?t=207620&highlight=connection+failed](http://www.ubuntuforums.org/showthread.php?t=207620&highlight=connection+failed) and [http://ubuntuforums.org/showthread.php?t=196121](http://ubuntuforums.org/showthread.php?t=196121) also had the same problem.

---

### Post by programgeek on 2006-07-04
Bumpy:KS

---

### Post by professor_chaos on 2006-07-04
I'm not having a problem using the same sources. Also, that address is responding.

What happens when you "ping 85.133.25.7"?

---

### Post by programgeek on 2006-07-04
I just download through bittorrent and burned again.

I got the same trouble, I also I would to mention that during installation I got a popup saying "Failed to [get] security updates".

I just tried to update after my fresh installation, and here are the errors:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060614_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.06+20060614_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.4.8-3ubuntu1.1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/acpi-support/acpi-support_0.85_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.10.3-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.10.3-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-extra_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-0_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-common_2.14.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.8.18-0ubuntu2_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.12.3-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.12.3-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.8.18-0ubuntu2_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.18-0ubuntu2_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/libmetacity0_2.14.5-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.14.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/desktop-file-utils/desktop-file-utils_0.10-1ubuntu13_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/gnome-control-center_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/capplets-data_2.14.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprint/libgnomeprint2.2-0_2.12.1-3ubuntu2_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprint/libgnomeprint2.2-data_2.12.1-3ubuntu2_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/eog/eog_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_0.5.2-0ubuntu3_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/file-roller/file-roller_2.14.3-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-session/gnome-session_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity_2.14.5-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte4_0.12.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.12.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal-data_2.14.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.14.9-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit_2.14.3-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit-common_2.14.3-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-highcontrast_2.7.4.is.2.6.9-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-themes/gnome-accessibility-themes_2.14.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.1.33_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck-common_2.14.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck18_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.14.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.14.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-doc-utils/gnome-doc-utils_0.6.1-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.14.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus-cd-burner/libnautilus-burn3_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-media/gnome-media_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.8.18-0ubuntu2_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-thinice_2.7.4.is.2.6.9-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-crux_2.7.4.is.2.6.9-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-redmond95_2.7.4.is.2.6.9-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-lighthouseblue_2.7.4.is.2.6.9-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-smooth_2.7.4.is.2.6.9-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-mist_2.7.4.is.2.6.9-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-clearlooks_2.7.4.is.2.6.9-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-themes/gnome-themes_2.14.2-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-industrial_2.7.4.is.2.6.9-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.8/libgtkhtml3.8-15_3.10.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.8/gtkhtml3.8_3.10.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-bin_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsoup/libsoup2.2-8_2.2.93-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus-cd-burner/nautilus-cd-burner_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyorbit/python2.4-pyorbit_2.14.1-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyorbit/python-pyorbit_2.14.1-0ubuntu1_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/python-vte_0.12.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sound-juicer/sound-juicer_2.14.4-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_6.06.2_all.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-mouse/xserver-xorg-input-mouse_1.0.3.1+cvs.20060109-0ubuntu1.1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/y/yelp/yelp_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/z/zenity/zenity_2.14.2-0ubuntu1_i386.deb
  Connection failed [IP: 146.137.96.7 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcmcia-cs/pcmcia-cs_3.2.8-5.2ubuntu7_i386.deb
  Connection failed [IP: 146.137.96.7 80]



```

This is me using the standed sources.list

It seems to be happening at alot of these repositories.  I don't understand. :KS

---

### Post by programgeek on 2006-07-04
Also worth noting - I am using a WRT54G 2.0 router on a WEP connection w/ the Firmware Version : v4.70.8, Hyperwrt 2.1b1 + Thibor14

---

### Post by programgeek on 2006-07-04
Bump

---

### Post by walkerx on 2006-07-04
did u actually check the download image against its md5sum value - maybe corrupted

---

### Post by Wd2048 on 2006-07-06
I too get the errors:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 85.133.25.8 80]


just to name a few. When I burned this ISO, the MD5 sum checked out.

---

### Post by Al3xanR0 on 2006-07-06
[QUOTE=Wd2048]I too get the errors:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 85.133.25.8 80]


just to name a few. When I burned this ISO, the MD5 sum checked out.[/QUOTE]

Are you accessing the net via proxy?

---

### Post by silk on 2006-07-09
Hi!

I have the same problems. I dont't access the internet via a proxy. I use a router, but since other internet applications work well this shouldn't be the source of the trouble..

Christian

---

### Post by silk on 2006-07-09
I fixed the problem.

I found out that this problem seems to be quiet common.

Try: 
- Switch off ipv6 (some routers have problems with ipv6)
- Change your nameservers to others then the nameservers from your router (if there is one).
- Use mirror servers in sources.list. They worked for me while the normal ones didn't worked. It's just a workaround but it works..

---

### Post by Wd2048 on 2006-07-20
not using a proxy. I really liked 5.10... not sure about this 6.06

---

### Post by Wd2048 on 2006-07-31
I tried Silk's workaround (disabling ipv6, etc.) and still having problems. I even tried loading on some different hardware, and still getting problems. Tried with DHCP and with Static assigned... still no worky... any ideas out there?

---

### Post by ps- on 2006-08-01
same problem here. I never had something like this - neither with my router at home, with ip cop or with a "telefonica" modem/router.

but since we installed a netgear FVS318v3, it does not work. Not sure if this is the reason - everything else works like expected (dns works, http works, (s)ftp, ...)
If i navigate the update servers with the browser I see all files, can download them, etc.

But "aptitude" has problems I cant understand ... :/ this must be a bad bug. any suggestions?

---

### Post by Wd2048 on 2006-08-02
interesting... i have the same firewall... i wonder if that has something to do with it? i'm trying something a little different. i'll let you know how it turns out. I installed breezy and am upgrading to dapper drake. The install finished last night, but i will have to wait till i get home from work to check on it. more to come....

---

### Post by caspian154 on 2006-08-02
I am also having this problem - I have a netgear wgr14 wireless router. apt-get works fine if I connect directly to the cable modem, but if I am trying to update from inside the firewall i get the same errors.

I've seen several posts (the best being: [http://ubuntuforums.org/showthread.php?t=113334](http://ubuntuforums.org/showthread.php?t=113334)) and have tried using a static ip, setting my dns servers explicitly, tried wireless and wired connections and like I've said, i've only been able to update when directly plugged into the cable modem.

---

### Post by Wd2048 on 2006-08-02
Well, I found a fix for my problem (albeit long). I still had a copy of Breezy burned off (Actually i had the commercial CD, but who's counting?) and I installed it. Then I updated it to the gills, then let the update-manager upgrade me to Dapper Drake. Now I can use apt, synaptic, etc, without any problems even in Dapper Drake. Don't know what is different. Maybe I got an updated version of apt with the Dapper Drake upgrade. I don't know. But I am now on a Dapper box. Feel free to let me know if you have any questions about this way. It takes about a day to install, update, and then upgrade, but I let it run overnight, and that worked out well with me.

---

### Post by xristoforosth on 2006-08-25
[This]("http://www.ubuntuforums.org/showpost.php?p=1364819&postcount=4") fixed my problem(i had internet but i couldnt update like you)

---

### Post by mrO on 2006-08-31
Thanks xristoforosth. My /etc/apt/apt.conf had

Acquire::http::Proxy "false";

Changed to 
Acquire::http::DIRECT;

and all is good. No idea why it had the proxy in the first place.

---

### Post by snowdogdb on 2006-11-14
Has anyone ever found a solution to this problem?
I've be unable to get apt-get update to work on any Ubuntu system.  I installed SuSE and installed apt-get and it works great.  I just seem to be unable to get it to work on Ubunutu.  No proxy, but I am on a NATed network. 
So many people report the same problem, but I've never seen a solution.
Anyone?



> **silk said:**
> Hi!

I have the same problems. I dont't access the internet via a proxy. I use a router, but since other internet applications work well this shouldn't be the source of the trouble..

Christian

---

### Post by snowdogdb on 2006-11-14
Ah!  Problem Solved.  The answer in this post:
[http://www.ubuntuforums.org/showpost.php?p=1364819&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1364819&postcount=4)

Worked!  Thank You Ubuntu Community!

---

