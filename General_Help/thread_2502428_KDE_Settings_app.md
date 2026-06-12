---
title: "KDE Settings app"
date: 2024-11-14
forum: General Help
---

### Post by Hewjr100 on 2024-11-14
Does anyone know why I have a KDE Settings app in my default Ubuntu 24.04 with Gnome.  I do not install any other desktops on my system, and I cannot delete it.  Not through the software app anyway.

I forgot to say that I use the following command to remove snaps, then install Gnome Software and Flatpak:
"[COLOR=#000000][FONT=&amp]sudo bash -c "$(wget -qO- https://raw.githubusercontent.com/polkaulfield/ubuntu-debullshit/main/ubuntu-debullshit.sh)"

[/FONT][/COLOR]I have used this in the past and did not have a KDE Settings app on my system.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294513&stc=1[/IMG]

---

### Post by &amp;KyT$0P# on 2024-11-14
What is the output of
```
apt-cache policy systemsettings
```

If it shows this package is installed, check [FONT=monospace]/var/log/apt/history.log[/FONT] to see when it got installed, and if it's not obvious from the log entry, you can run
```
apt-cache --installed rdepends systemsettings
```
to see what might have pulled it in.  And you can see what would happen if you were to remove it by running
```
apt -s purge systemsettings
```

---

### Post by Hewjr100 on 2024-11-14
This is the first output:

> sudo apt-cache policy systemsettingssystemsettings:
  Installed: 4:5.27.11-0ubuntu2
  Candidate: 4:5.27.11-0ubuntu2
  Version table:
 *** 4:5.27.11-0ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble/universe amd64 Packages
        100 /var/lib/dpkg/status

Next:

> sudo apt-cache --installed rdepends systemsettingssystemsettings
Reverse Depends:

Next

> sudo apt -s purge systemsettingsReading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kactivities-bin kactivitymanagerd kded5 kio kpackagelauncherqml
  kpackagetool5 kwayland-data kwayland-integration libdbusmenu-qt5-2
  libdouble-conversion3 libgpgmepp6t64 libhfstospell11 libkf5activities5
  libkf5archive-data libkf5archive5 libkf5attica5 libkf5auth-data libkf5auth5
  libkf5authcore5 libkf5codecs-data libkf5codecs5 libkf5completion-data
  libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5
  libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5
  libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin
  libkf5dbusaddons-data libkf5dbusaddons5 libkf5declarative-data
  libkf5declarative5 libkf5doctools5 libkf5globalaccel-bin
  libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5
  libkf5guiaddons-bin libkf5guiaddons-data libkf5guiaddons5 libkf5i18n-data
  libkf5i18n5 libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5
  libkf5itemmodels5 libkf5itemviews-data libkf5itemviews5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kcmutils-data libkf5kcmutils5
  libkf5kcmutilscore5 libkf5kiocore5 libkf5kiogui5 libkf5kiontlm5
  libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuffcore5
  libkf5notifications-data libkf5notifications5 libkf5package-data
  libkf5package5 libkf5plasma5 libkf5quickaddons5 libkf5runner5
  libkf5service-bin libkf5service-data libkf5service5 libkf5solid5
  libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5
  libkf5syndication5abi1 libkf5textwidgets-data libkf5textwidgets5
  libkf5threadweaver5 libkf5wallet-bin libkf5wallet-data libkf5wallet5
  libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5
  libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin
  libkf5xmlgui-data libkf5xmlgui5 libkwalletbackend5-5 libkworkspace5-5
  libmd4c0 libpcre2-16-0 libpolkit-qt5-1-1 libqca-qt5-2 libqca-qt5-2-plugins
  libqt5core5t64 libqt5dbus5t64 libqt5gui5t64 libqt5network5t64
  libqt5printsupport5t64 libqt5qml5 libqt5qmlmodels5 libqt5qmlworkerscript5
  libqt5quick5 libqt5quickcontrols2-5 libqt5quickshapes5
  libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5sql5-sqlite libqt5sql5t64
  libqt5svg5 libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5
  libqt5widgets5t64 libqt5x11extras5 libqt5xml5t64 libvoikko1 libxcb-record0
  libxcb-xinerama0 libxcb-xinput0 media-player-info qml-module-org-kde-kcm
  qml-module-org-kde-kcmutils qml-module-org-kde-kirigami2
  qml-module-org-kde-kitemmodels qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-newstuff qml-module-org-kde-runnermodel
  qml-module-qtgraphicaleffects qml-module-qtqml qml-module-qtqml-models2
  qml-module-qtquick-controls qml-module-qtquick-controls2
  qml-module-qtquick-layouts qml-module-qtquick-shapes
  qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2
  qt5-gtk-platformtheme qtspeech5-speechd-plugin qttranslations5-l10n
  qtwayland5 sonnet-plugins
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  systemsettings*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Purg systemsettings [4:5.27.11-0ubuntu2]

sudo apt autoremove does not remove anything.

Henry

---

### Post by tea for one on 2024-11-14
halogen2, quite correctly, offered the command with the simulation flag -s, which prevents anything untoward happening without knowing more info about your system. 

The dependencies would not be autoremoved until the parent package had been removed.
If you wish to remove systemsettings and, consequently the dependencies:-
```
sudo apt remove systemsettings
```
```
sudo apt autoremove
```

> Enables gnome integration with QT apps
This is one of the features of the script you ran.
Possibly the reason that KDE systemsettings appeared?

By the way, the the github page states  "An automated script to set-up Ubuntu as it should be. Tested on Ubuntu 22.04 and 23.04"
No mention of a test for 24.04

---

### Post by Hewjr100 on 2024-11-14
Thank you, [COLOR=#000000][FONT=&quot]sudo apt remove systemsettings removed KDE Settings, and I still have the regular settings app.

Henry[/FONT][/COLOR]

---

