---
title: "Xfce4"
date: 2005-10-16
forum: General Help
---

### Post by JediPottsy on 2005-10-16
How can i upgrade XFCE from 4.2 to 4.2.2?

---

### Post by ecobuntu on 2005-10-16
sudo apt-get update && apt-get upgrade

I did apt-cache search xfce4 and here it is...presuming your running Breezy (if not, change repositories to breezy then sudo apt-get update && apt-get dist-upgrade)

chris@ubuntu:~$ apt-cache show xfce4
Package: xfce4
Priority: optional
Section: universe/x11
Installed-Size: 64
Maintainer: Debian Xfce Maintainers <pkg-xfce-devel@lists.alioth.debian.org>
Architecture: all
Version: 4.2.2
Replaces: xfce4-themes (<= 4.0.0+cvs.20030301-1), xfce4-dev (<< 4.0.0+cvs.20030421)
Depends: xfwm4 (>= 4.2.2-1), xfwm4-themes (>= 4.2.2-1), xfce4-mcs-plugins (>= 4.2.2-1), xfce4-panel (>= 4.2.2-1), xfce4-icon-theme (>= 4.2.2-1), xfdesktop4 (>= 4.2.2-1), xffm4 (>= 4.2.2-1), xfce4-utils (>= 4.2.2-1), gtk2-engines-xfce, xfce4-session (>= 4.2.2-1)
Recommends: xfce4-iconbox, xfce4-mixer, xfce4-systray, xfce4-toys, xfce4-trigger-launcher, xfprint4, xfcalendar
Filename: pool/universe/x/xfce4/xfce4_4.2.2_all.deb
Size: 4842
MD5sum: 9af23bfe73a979601e4806490aeaa21a
Description: Installs Xfce4 core and scripts to set it up
 This package is a pseudo meta package: It basically installs the
 core modules of the Xfce4 desktop environment and some scripts to
 get it work (for example a launch script for GDM and a script
 that does the necessary things to create a local Xfce4 setup in
 a user's $HOME-dir). If you intend to Xfce4, installing this
 package is a good point to start with and highly recommended.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

