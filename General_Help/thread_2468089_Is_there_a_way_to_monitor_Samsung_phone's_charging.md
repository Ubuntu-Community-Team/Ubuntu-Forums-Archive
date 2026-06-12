---
title: "Is there a way to monitor Samsung phone's charging status in Xubuntu's battery applet"
date: 2021-10-18
forum: General Help
---

### Post by ardouronerous on 2021-10-18
[IMG]https://web.archive.org/web/20211018104339if_/https://i.redd.it/5ti5ilg0u6u71.png[/IMG]

Is there a way to monitor Samsung phone's charging status in Xubuntu's battery applet, just like it monitors my iPad charging status?

---

### Post by SeijiSensei on 2021-10-18
KDEConnect has many useful applications to integrate your phone and PC including a battery monitor. Though it's a KDE app, you can install it on all flavors of Ubuntu. There's a companion app in the Play Store that you load on your phone. Very handy.

---

### Post by ardouronerous on 2021-10-18
> **SeijiSensei said:**
> KDEConnect has many useful applications to integrate your phone and PC including a battery monitor. Though it's a KDE app, you can install it on all flavors of Ubuntu. There's a companion app in the Play Store that you load on your phone. Very handy.

Thanks, but the dependencies are too much though:

```
sudo apt-get install kdeconnect
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  kactivities-bin kactivitymanagerd kde-cli-tools kde-cli-tools-data
  keditbookmarks kio kpackagelauncherqml kpackagetool5 kpeople-vcard
  kwayland-data kwayland-integration libdbusmenu-qt5-2 libfakekey0 libfam0
  libhfstospell10 libkf5activities5 libkf5archive5 libkf5attica5
  libkf5auth-data libkf5auth5 libkf5authcore5 libkf5bookmarks-data
  libkf5bookmarks5 libkf5calendarevents5 libkf5codecs-data libkf5codecs5
  libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data
  libkf5configcore5 libkf5configgui5 libkf5configwidgets-data
  libkf5configwidgets5 libkf5contacts-data libkf5contacts5
  libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin
  libkf5dbusaddons-data libkf5dbusaddons5 libkf5declarative-data
  libkf5declarative5 libkf5doctools5 libkf5globalaccel-bin
  libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5
  libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin
  libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data
  libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5 libkf5kcmutils-data
  libkf5kcmutils5 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiogui5
  libkf5kiontlm5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5notifications-data
  libkf5notifications5 libkf5package-data libkf5package5 libkf5parts-data
  libkf5parts-plugins libkf5parts5 libkf5people-data libkf5people5
  libkf5peoplebackend5 libkf5peoplewidgets5 libkf5plasma5 libkf5plasmaquick5
  libkf5pty-data libkf5pty5 libkf5pulseaudioqt2 libkf5quickaddons5
  libkf5service-bin libkf5service-data libkf5service5 libkf5solid5
  libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5
  libkf5su-bin libkf5su-data libkf5su5 libkf5textwidgets-data
  libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5
  libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5
  libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin
  libkf5xmlgui-data libkf5xmlgui5 libkwalletbackend5-5 libkworkspace5-5
  libpolkit-qt5-1-1 libqca-qt5-2 libqca-qt5-2-plugins libqt5multimedia5
  libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5sql5-sqlite
  libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5 libvoikko1
  libxcb-composite0 libxcb-damage0 libxcb-res0 media-player-info
  plasma-framework qml-module-org-kde-kconfig qml-module-org-kde-kirigami2
  qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-people qml-module-qtgraphicaleffects
  qml-module-qtqml-models2 qml-module-qtquick-controls
  qml-module-qtquick-controls2 qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets
  qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2
  qtwayland5 sonnet-plugins sshfs
Suggested packages:
  python-nautilus fam voikko-fi hspell
The following NEW packages will be installed:
  kactivities-bin kactivitymanagerd kde-cli-tools kde-cli-tools-data
  kdeconnect keditbookmarks kio kpackagelauncherqml kpackagetool5
  kpeople-vcard kwayland-data kwayland-integration libdbusmenu-qt5-2
  libfakekey0 libfam0 libhfstospell10 libkf5activities5 libkf5archive5
  libkf5attica5 libkf5auth-data libkf5auth5 libkf5authcore5
  libkf5bookmarks-data libkf5bookmarks5 libkf5calendarevents5
  libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5
  libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5
  libkf5configwidgets-data libkf5configwidgets5 libkf5contacts-data
  libkf5contacts5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5
  libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5
  libkf5declarative-data libkf5declarative5 libkf5doctools5
  libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5
  libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5
  libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5
  libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data
  libkf5jobwidgets5 libkf5kcmutils-data libkf5kcmutils5 libkf5kiocore5
  libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiontlm5 libkf5kiowidgets5
  libkf5kirigami2-5 libkf5notifications-data libkf5notifications5
  libkf5package-data libkf5package5 libkf5parts-data libkf5parts-plugins
  libkf5parts5 libkf5people-data libkf5people5 libkf5peoplebackend5
  libkf5peoplewidgets5 libkf5plasma5 libkf5plasmaquick5 libkf5pty-data
  libkf5pty5 libkf5pulseaudioqt2 libkf5quickaddons5 libkf5service-bin
  libkf5service-data libkf5service5 libkf5solid5 libkf5solid5-data
  libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5su-bin
  libkf5su-data libkf5su5 libkf5textwidgets-data libkf5textwidgets5
  libkf5wallet-bin libkf5wallet-data libkf5wallet5 libkf5waylandclient5
  libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data
  libkf5windowsystem5 libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5
  libkwalletbackend5-5 libkworkspace5-5 libpolkit-qt5-1-1 libqca-qt5-2
  libqca-qt5-2-plugins libqt5multimedia5 libqt5quickcontrols2-5
  libqt5quicktemplates2-5 libqt5sql5-sqlite libqt5texttospeech5
  libqt5waylandclient5 libqt5waylandcompositor5 libvoikko1 libxcb-composite0
  libxcb-damage0 libxcb-res0 media-player-info plasma-framework
  qml-module-org-kde-kconfig qml-module-org-kde-kirigami2
  qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-people qml-module-qtgraphicaleffects
  qml-module-qtqml-models2 qml-module-qtquick-controls
  qml-module-qtquick-controls2 qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets
  qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2
  qtwayland5 sonnet-plugins sshfs
0 upgraded, 146 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.5 MB of archives.
After this operation, 132 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
```

I've tried the flathub version of KDE Connect:
```
flatpak install flathub com.github.bajoja.indicator-kdeconnect 
```

But I'm getting this error though when I click on it:
```
cannot connect to KDE Connect DBus Service
```

---

