---
title: "Why  when I restart  Kubuntu 22.04 konqueror is opened ?"
date: 2024-03-31
forum: General Help
---

### Post by nilovsergey on 2024-03-31
At some moment on my fresh Kubuntu 22.04 installation when I restart OS konqueror is opened by default.
I checked “System Settings” -> “Startup and Shutdown” -> “Autostart" has no any items.
I also checked konqueror options, but I did not find any options like “Run at system restart”
Are there some option I have to switch off ?

```
$ lsb_release -d; uname -r; uname -i
Description:    Ubuntu 22.04.4 LTS
6.5.0-26-generic
x86_64
$ kf5-config --version
Qt: 5.15.3
KDE Frameworks: 5.92.0
kf5-config: 1.0
$ dpkg -s  konqueror
Package: konqueror
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 21426
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Architecture: amd64
Version: 4:21.12.3-0ubuntu1
Replaces: konq-plugins (<< 4:20.12.0-4~)
Provides: info-browser, man-browser, www-browser
Depends: dolphin, install-info, kio, libc6 (>= 2.34), libkf5archive5 (>= 5.71.0~), libkf5bookmarks5 (>= 5.69.0), libkf5codecs5 (>= 4.96.0), libkf5completion5 (>= 4.97.0), libkf5configcore5 (>= 5.24.0), libkf5configgui5 (>= 4.97.0), libkf5configwidgets5 (>= 5.78.0), libkf5coreaddons5 (>= 5.77.0), libkf5crash5 (>= 5.71.0~), libkf5dbusaddons5 (>= 5.71.0~), libkf5i18n5 (>= 4.97.0), libkf5iconthemes5 (>= 5.71.0~), libkf5itemviews5 (>= 4.96.0), libkf5jobwidgets5 (>= 5.70.0), libkf5kcmutils5 (>= 5.84.0), libkf5kiocore5 (>= 5.69.0), libkf5kiofilewidgets5 (>= 5.37.0~), libkf5kiogui5 (>= 5.73.0), libkf5kiowidgets5 (>= 5.70.0), libkf5konq6 (>= 4:21.12.3), libkf5parts5 (>= 5.81.0), libkf5service-bin, libkf5service5 (>= 5.69.0), libkf5sonnetcore5 (>= 5.54.0), libkf5sonnetui5 (>= 5.69.0), libkf5textwidgets5 (>= 5.0.0), libkf5wallet-bin, libkf5wallet5 (>= 5.71.0~), libkf5widgetsaddons5 (>= 5.77.0), libkf5windowsystem5 (>= 5.71.0~), libkf5xmlgui5 (>= 5.84.0), libqt5core5a (>= 5.15.1), libqt5dbus5 (>= 5.14.1), libqt5gui5 (>= 5.12.0~) | libqt5gui5-gles (>= 5.12.0~), libqt5network5 (>= 5.12.2), libqt5printsupport5 (>= 5.12.0~), libqt5webenginecore5 (>= 5.12.2), libqt5webenginewidgets5 (>= 5.14.1), libqt5widgets5 (>= 5.14.1), libqt5x11extras5 (>= 5.6.0), libqt5xml5 (>= 5.12.0~), libstdc++6 (>= 4.5)
Recommends: kfind
Suggests: konq-plugins
Breaks: konq-plugins (<< 4:20.12.0-4~)
Conffiles:
 /etc/xdg/autostart/konqy_preload.desktop 08b106dc3f6cbb348cb631c9965765d9
 /etc/xdg/konqsidebartngrc dbc48316a399ce7b836eaf9b270eee9d
Description: advanced file manager, web browser and document viewer
 Konqueror is the KDE web browser and advanced file manager.
 .
 Konqueror is a standards-compliant web browser, supporting HTML 4.01, Java,
 JavaScript, CSS3, and Netscape plugins such as Flash.
 .
 It supports advanced file management on local UNIX filesystems, with flexible
 views, network transparency, and embedded file viewing.
 .
 It is the canvas for many KDE technologies, from remote file access via KIO to
 component embedding via the KParts object interface, making it one of the most
 customizable applications available.
 .
 This package is part of the KDE base applications module.
Homepage: https://apps.kde.org/en/konqueror
Original-Maintainer: Debian/Kubuntu Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>

```

---

### Post by deadflowr on 2024-03-31
I've had this happen to me before and what it was was in that same settings page go to Desktop Session and check the option for "When logging in".
The default is to save the previous session, change it to Start with an empty session.
See if that does anything?

---

