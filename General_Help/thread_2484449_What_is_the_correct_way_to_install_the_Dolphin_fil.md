---
title: "What is the correct way to install the Dolphin file manager?"
date: 2023-02-27
forum: General Help
---

### Post by SpaceManJack on 2023-02-27
Is there anyone here who uses Dolphin file manager on Ubuntu 22.04? What's the correct way to install Dolphin file manager?

---

### Post by guiverc on 2023-02-27
Have you tried 
```

sudo apt install dolphin

```
[https://packages.ubuntu.com/jammy/dolphin](https://packages.ubuntu.com/jammy/dolphin)

You didn't say what Ubuntu 22.04 LTS you're using (desktop? server? or *flavor*?) as that will make a difference in what needs to be *pulled in* due to *depends* rules, but the issue maybe you've not *enabled* the 'universe' or *community* repository

Have you enabled *universe* ?  as if you check the package link I provided; that is where its located (*22.04 flavors will already have it enabled, but a Ubuntu Desktop/Server install required it to be enabled manually, as packages found in 'universe' have different security warranties/guarantees*)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by TheFu on 2023-02-27
Exactly.

```
$ apt search dolphin
p   dolphin                         - file manager                              
```
So it is available in the default repos.

Trying to run it from a shell, 
```
$ dolphin
Command 'dolphin' not found, but can be installed with:
sudo apt install dolphin
```

Of course, any APT front-end you like can be used.

However, it has 174MB of dependencies on a Gnome-based system, so perhaps there's a better file manager for most people who aren't running KDE or LXQt.
```
The following additional packages will be installed:
  baloo-kf5 ffmpegthumbs gamin kactivities-bin kactivitymanagerd kded5
  kdegraphics-thumbnailers keditbookmarks kimageformat-plugins kinit kio
  kio-extras kio-extras-data kpackagelauncherqml kpackagetool5
  kuserfeedback-doc kwayland-data kwayland-integration libappimage0 libavif13
  libcddb2 libdbusmenu-qt5-2 libdolphinvcs5 libdvbpsi10 libebml5 libepub0
  libgamin0 libgav1-0 libhfstospell11 libixml10 libkdsoap1 libkf5activities5
  libkf5activitiesstats1 libkf5archive5 libkf5attica5 libkf5auth-data
  libkf5auth5 libkf5authcore5 libkf5baloo5 libkf5balooengine5
  libkf5baloowidgets-bin libkf5baloowidgets-data libkf5baloowidgets5
  libkf5bookmarks-data libkf5bookmarks5 libkf5codecs-data libkf5codecs5
  libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data
  libkf5configcore5 libkf5configgui5 libkf5configwidgets-data
  libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5
  libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5
  libkf5declarative-data libkf5declarative5 libkf5dnssd-data libkf5dnssd5
  libkf5doctools5 libkf5filemetadata-bin libkf5filemetadata-data
  libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel-data
  libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons-bin
  libkf5guiaddons-data libkf5guiaddons5 libkf5i18n-data libkf5i18n5
  libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5
  libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data
  libkf5jobwidgets5 libkf5kcmutils-data libkf5kcmutils5 libkf5kdcraw5
  libkf5kexiv2-15.0.0 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiogui5
  libkf5kiontlm5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff-data
  libkf5newstuff5 libkf5newstuffcore5 libkf5notifications-data
  libkf5notifications5 libkf5package-data libkf5package5 libkf5parts-data
  libkf5parts-plugins libkf5parts5 libkf5quickaddons5 libkf5service-bin
  libkf5service-data libkf5service5 libkf5solid5 libkf5solid5-data
  libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5syndication5abi1
  libkf5syntaxhighlighting-data libkf5syntaxhighlighting5
  libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data
  libkf5wallet5 libkf5waylandclient5 libkf5widgetsaddons-data
  libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5
  libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libkuserfeedbackcore1
  libkuserfeedbackwidgets1 libkwalletbackend5-5 libmatroska7
  libopenmpt-modplug1 libpackagekitqt5-1 libphonon4qt5-4 libphonon4qt5-data
  libpolkit-qt5-1-1 libpoppler-qt5-1 libprotobuf-lite23 libproxy-tools
  libqmobipocket2 libqt5printsupport5 libqt5qml5 libqt5qmlmodels5
  libqt5qmlworkerscript5 libqt5quick5 libqt5quickcontrols2-5
  libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5sql5 libqt5sql5-sqlite
  libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5 libqt5xml5
  libresid-builder0c2a libsdl-image1.2 libsidplay2 libspatialaudio0
  libsquashfuse0 libssh2-1 libupnp13 libvlc-bin libvlc5 libvlccore9 libvoikko1
  libyuv0 phonon4qt5 phonon4qt5-backend-vlc qml-module-org-kde-kirigami2
  qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff
  qml-module-org-kde-userfeedback qml-module-qtgraphicaleffects
  qml-module-qtqml-models2 qml-module-qtquick-controls2
  qml-module-qtquick-layouts qml-module-qtquick-templates2
  qml-module-qtquick-window2 qml-module-qtquick2 qtspeech5-speechd-plugin
  qtwayland5 sonnet-plugins vlc-data vlc-plugin-base vlc-plugin-video-output

```
I won't be installing it. That's just a bit more bloat than I'm willing to add to my desktop.

---

### Post by SpaceManJack on 2023-03-03
My computer is a desktop PC.

---

### Post by monkeybrain20122 on 2023-03-03
It is easy to install but it is going to pull in a lot of KDE stuffs(see TheFu's outputs). This is the general problem for installing KDE apps on non KDE systems. Too many dependencies.

 Moreover after installing it you have to do some work to set it the default file manager. There are many tutorials online for nemo so I suppose it is similar for dolphin.

---

### Post by SeijiSensei on 2023-03-03
> **TheFu said:**
> I won't be installing it. That's just a bit more bloat than I'm willing to add to my desktop.
I try to avoid using Gnome apps on my Kubuntu system for the same reason.

---

### Post by TheFu on 2023-03-03
> **SeijiSensei said:**
> I try to avoid using Gnome apps on my Kubuntu system for the same reason.

+100!  Big time!

---

### Post by SpaceManJack on 2023-03-12
> **SeijiSensei said:**
> I try to avoid using Gnome apps on my Kubuntu system for the same reason.

So what is Gnome and why is Gnome bad for Ubuntu?

---

### Post by SpaceManJack on 2023-03-12
What is your guys's preferred file manager for Ubuntu?

---

### Post by Dennis N on 2023-03-12
> What is your guys's preferred file manager for Ubuntu? 
I wouldn't use a foreign (something not gtk based) File Manager in Ubuntu. Gnome Files (a.k.a. Nautilus) is thematically aligned with the Gnome Desktop, the style of other Gnome applications, and designed work with the built-in gtk3 or gtk4 depending on the Ubuntu release.

---

