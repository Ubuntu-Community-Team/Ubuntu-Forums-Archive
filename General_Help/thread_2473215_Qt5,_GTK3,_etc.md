---
title: "Qt5, GTK3, etc"
date: 2022-03-28
forum: General Help
---

### Post by wyattwhiteeagle on 2022-03-28
Before installing app's, what is the easiest way to see if the app is Qt5, GTK3, etc?

---

### Post by &amp;KyT$0P# on 2022-03-28
For what kind of packaging?

If the app is a .deb from a repository, you could look at the "Depends:" line in the output of
```
apt-cache show [COLOR="#FF0000"]<packagename>[/COLOR]
```
(replacing [COLOR="#FF0000"]<packagename>[/COLOR] with the specific package you're wondering about)

If the app is a .deb you downloaded, you can extract its contents and look at its [FONT=Courier New]control[/FONT] file for dependency information.  Depending what archive manager you use, it could be either at [FONT=Courier New]DEBIAN/control[/FONT] or packed inside a [FONT=Courier New]control.tar.xz[/FONT] along with other metadata.

If the app is a flatpak from Flathub, you could look at Flathub's Github repository for that app's Flathub packaging to see which runtime(s) and/or bundled dependencies the app uses.

---

### Post by Yellow Pasque on 2022-03-28
I've always found Synaptic to be a great package manager. It has an option to show the dependencies of a package.

---

### Post by wyattwhiteeagle on 2022-03-28
So...I guess the dependecies of a package determine whether the package is Qt5 or GTK3 or whatever?

I would imagine there are packages (not many though) that have dependencies of most or all of the different...oh what are they called...Qt5, GTK3, etc...whatever they are known as.

Looking at stacer's depends line, most say they are Qt5...
So stacer is a Qt5?

Looking at bleachbit's dependencies...gtk3?

---

### Post by guiverc on 2022-03-28
You've already got a good responses from @halogen2 and @Yellow Pasque

In a Lubuntu/Kubuntu or Qt5 environment, use [*Muon Package Manager*]("https://manual.lubuntu.me/stable/4/4.2/muon.html") (Qt5) instead of Synaptic (GTK3) as it offers the same detail as well.

I'll add you can use a browser too; eg. I still use `hexchat` as my IRC client even though I'm using Lubuntu/LXQt almost all the time, and if I'm not then Xubuntu/Xfce or Ubuntu/GNOME are both GTK3 & not GTK2.

[https://packages.ubuntu.com/jammy/hexchat](https://packages.ubuntu.com/jammy/hexchat)  shows a *depends* for [https://packages.ubuntu.com/jammy/libgtk2.0-0](https://packages.ubuntu.com/jammy/libgtk2.0-0)  ie. a GTK2 library so it'll be *somewhat* inefficient on both Qt5 & GTK3 environments... Thankfully GTK2 is old/somewhat-light, so it's less of a hit than a GTK3 app used on a GTK2, or GTK3 app on Qt5 - but if your machine is resource limited (*inc. old like my 2009 desktop!*) you take it into account (esp. if RAM is limited!)

The online packages.ubuntu.com equivalent to CLI commands in the first answer, are actually great for answering, or in fact asking questions on forums/support sites.

Most apps use a single **toolkit**; ie. GTK2 (*deprecated*), GTK3, GTK4 (*new development*), Qt5 (*I won't list older [Qt4 as it was removed before 20.04]("https://discourse.ubuntu.com/t/removing-qt-4-from-ubuntu-before-the-20-04-release/12295")*), but GTK2/GTK3/GTK4/Qt5 are usually easy to spot in lists of dependencies/requirements/libraries given the toolkit is used in that form within the package name.

Also FYI:   LXQt uses Qt5, but in keeping Qt5 *light* many features needed by KDE aren't found there, so KDE also requires/uses KF5 or the KDE Frameworks 5 which adds functionality; thus is a requirement for many Qt5 apps written for KDE. Some Lubuntu packages use KDE tools, thus some KF5 is required (eg. Lubuntu uses KDE Partition Manager etc), but KF5 ***libraries*** are easy to spot again just using the KF5.

> **wyattwhiteeagle said:**
> 
Looking at bleachbit's dependencies...gtk3?

As for [https://packages.ubuntu.com/jammy/bleachbit](https://packages.ubuntu.com/jammy/bleachbit)  

Yep I see GTK3 in the first 2 *depends* or requirements

CLI tools like list rules for your current release (*by default*); using the online tools you can look up any release; I used *jam**my* as it's what I'm using..

---

### Post by DuckHook on 2022-03-29
While the above is all accurate, it's sometimes hard for new users to decipher those rather dense and arcane references. It doesn't help that many libraries will then drag in additional dependencies that won't show up in the initial dependency list. Last but not least: how can we make heads or tails of something like:```
gir1.2-wnck-3.0
```
So here's a simple trick that I use to see what will get dragged in on any given install:```
sudo apt install -s <name-of-package>
```The -s flag means "simulate". This will invoke a "pretend" install without actually doing the install. The result is a long list of dependencies that apt would have installed had the command been real.

Perhaps an example would illustrate this better. Since I run vanilla Ubuntu, my environment is pure GTK. Here's what happens when I simulate the installation of the QT app, Dolphin:```
duckhook@Zeus:~$  sudo apt install -s dolphin
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  baloo-kf5 catdoc ffmpegthumbs gamin kactivities-bin kactivitymanagerd kded5 kdegraphics-thumbnailers keditbookmarks
  kimageformat-plugins kinit kio kio-extras kio-extras-data kpackagelauncherqml kpackagetool5 kuserfeedback-doc
  kwayland-data kwayland-integration libappimage0 libavif13 libcddb2 libdbusmenu-qt5-2 libdc1394-25 libdca0
  libdolphinvcs5 libdvbpsi10 libebml5 libepub0 libfaad2 libfuse2 libgamin0 libgav1-0 libhfstospell11 libilmbase25
  libixml10 libkate1 libkdsoap1 libkf5activities5 libkf5activitiesstats1 libkf5archive5 libkf5attica5 libkf5auth-data
  libkf5auth5 libkf5authcore5 libkf5baloo5 libkf5balooengine5 libkf5baloowidgets-bin libkf5baloowidgets-data
  libkf5baloowidgets5 libkf5bookmarks-data libkf5bookmarks5 libkf5codecs-data libkf5codecs5 libkf5completion-data
  libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5 libkf5configwidgets-data
  libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data
  libkf5dbusaddons5 libkf5declarative-data libkf5declarative5 libkf5dnssd-data libkf5dnssd5 libkf5doctools5
  libkf5filemetadata-bin libkf5filemetadata-data libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel-data
  libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons-bin libkf5guiaddons-data libkf5guiaddons5
  libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5
  libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5 libkf5kcmutils-data libkf5kcmutils5
  libkf5kdcraw5 libkf5kexiv2-15.0.0 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiontlm5
  libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff-data libkf5newstuff5 libkf5newstuffcore5 libkf5notifications-data
  libkf5notifications5 libkf5package-data libkf5package5 libkf5parts-data libkf5parts-plugins libkf5parts5
  libkf5quickaddons5 libkf5service-bin libkf5service-data libkf5service5 libkf5solid5 libkf5solid5-data
  libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5syndication5abi1 libkf5syntaxhighlighting-data
  libkf5syntaxhighlighting5 libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5
  libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5
  libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libkuserfeedbackcore1 libkuserfeedbackwidgets1 libkwalletbackend5-5
  liblua5.2-0 libmad0 libmatroska7 libmpcdec6 libopenexr25 libopenmpt-modplug1 libpackagekitqt5-1 libphonon4qt5-4
  libphonon4qt5-data libplacebo192 libpolkit-qt5-1-1 libpoppler-qt5-1 libprotobuf-lite23 libproxy-tools
  libqmobipocket2 libqt5printsupport5 libqt5qml5 libqt5qmlmodels5 libqt5qmlworkerscript5 libqt5quick5
  libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5sql5 libqt5sql5-sqlite libqt5texttospeech5
  libqt5waylandclient5 libqt5waylandcompositor5 libqt5xml5 libresid-builder0c2a libsdl-image1.2 libsdl1.2debian
  libsidplay2 libsndio7.0 libspatialaudio0 libsquashfuse0 libupnp13 libvlc-bin libvlc5 libvlccore9 libvoikko1 libyuv0
  libzip4 phonon4qt5 phonon4qt5-backend-vlc qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-newstuff qml-module-org-kde-userfeedback qml-module-qtgraphicaleffects qml-module-qtqml-models2
  qml-module-qtquick-controls2 qml-module-qtquick-layouts qml-module-qtquick-templates2 qml-module-qtquick-window2
  qml-module-qtquick2 qtspeech5-speechd-plugin qtwayland5 sonnet-plugins vlc-data vlc-plugin-base
  vlc-plugin-video-output
Suggested packages:
  tk | wish dolphin-plugins qt5-qmltooling-plugins sndiod voikko-fi phonon4qt5-backend-gstreamer hspell libdvdcss2
The following NEW packages will be installed:
  baloo-kf5 catdoc dolphin ffmpegthumbs gamin kactivities-bin kactivitymanagerd kded5 kdegraphics-thumbnailers
  keditbookmarks kimageformat-plugins kinit kio kio-extras kio-extras-data kpackagelauncherqml kpackagetool5
  kuserfeedback-doc kwayland-data kwayland-integration libappimage0 libavif13 libcddb2 libdbusmenu-qt5-2 libdc1394-25
  libdca0 libdolphinvcs5 libdvbpsi10 libebml5 libepub0 libfaad2 libfuse2 libgamin0 libgav1-0 libhfstospell11
  libilmbase25 libixml10 libkate1 libkdsoap1 libkf5activities5 libkf5activitiesstats1 libkf5archive5 libkf5attica5
  libkf5auth-data libkf5auth5 libkf5authcore5 libkf5baloo5 libkf5balooengine5 libkf5baloowidgets-bin
  libkf5baloowidgets-data libkf5baloowidgets5 libkf5bookmarks-data libkf5bookmarks5 libkf5codecs-data libkf5codecs5
  libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5
  libkf5configwidgets-data libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5
  libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5 libkf5declarative-data libkf5declarative5
  libkf5dnssd-data libkf5dnssd5 libkf5doctools5 libkf5filemetadata-bin libkf5filemetadata-data libkf5filemetadata3
  libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons-bin
  libkf5guiaddons-data libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin libkf5iconthemes-data
  libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5
  libkf5kcmutils-data libkf5kcmutils5 libkf5kdcraw5 libkf5kexiv2-15.0.0 libkf5kiocore5 libkf5kiofilewidgets5
  libkf5kiogui5 libkf5kiontlm5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff-data libkf5newstuff5
  libkf5newstuffcore5 libkf5notifications-data libkf5notifications5 libkf5package-data libkf5package5 libkf5parts-data
  libkf5parts-plugins libkf5parts5 libkf5quickaddons5 libkf5service-bin libkf5service-data libkf5service5 libkf5solid5
  libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5syndication5abi1
  libkf5syntaxhighlighting-data libkf5syntaxhighlighting5 libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin
  libkf5wallet-data libkf5wallet5 libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5
  libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libkuserfeedbackcore1
  libkuserfeedbackwidgets1 libkwalletbackend5-5 liblua5.2-0 libmad0 libmatroska7 libmpcdec6 libopenexr25
  libopenmpt-modplug1 libpackagekitqt5-1 libphonon4qt5-4 libphonon4qt5-data libplacebo192 libpolkit-qt5-1-1
  libpoppler-qt5-1 libprotobuf-lite23 libproxy-tools libqmobipocket2 libqt5printsupport5 libqt5qml5 libqt5qmlmodels5
  libqt5qmlworkerscript5 libqt5quick5 libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5sql5
  libqt5sql5-sqlite libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5 libqt5xml5 libresid-builder0c2a
  libsdl-image1.2 libsdl1.2debian libsidplay2 libsndio7.0 libspatialaudio0 libsquashfuse0 libupnp13 libvlc-bin libvlc5
  libvlccore9 libvoikko1 libyuv0 libzip4 phonon4qt5 phonon4qt5-backend-vlc qml-module-org-kde-kirigami2
  qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff qml-module-org-kde-userfeedback
  qml-module-qtgraphicaleffects qml-module-qtqml-models2 qml-module-qtquick-controls2 qml-module-qtquick-layouts
  qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2 qtspeech5-speechd-plugin qtwayland5
  sonnet-plugins vlc-data vlc-plugin-base vlc-plugin-video-output
---SNIP---
```
Clearly, bad news.

Even if you don't know whether these dependencies are QT or GTK, is it really worth dragging in so many dependencies for a simple file manager?

The -s flag serves as a sober reality check on my curiosity and has saved me from bloating up my system on many an occasion. In the end, it doesn't matter so much that an app is GTK or QT or something else: what matters is avoiding system bloat of all kinds.

---

### Post by DuckHook on 2022-03-29
It occurs to me that, although I provided practical advice, I did not actually answer your question. So, in an effort to address that:

The candid answer is that it's not really that easy to make this determination. It requires some insider knowledge, some general familiarity with Linux libraries in general and some skill at parsing arcane library names.

Using the same Dolphin example as in my post #6, note the presence (about 80% of the way down) of libraries starting with libqt5*. It's a pretty good bet that anything so named is a Qt5 library: ergo, Dolphin is a Qt5 app. But note that some apps may be Qt5, yet not use libraries so obviously named.

halogen2's suggestion is very useful. I rely on *apt show* all the time to give me info about packages. But again, not all package descriptions contain obvious references to their development frameworks: To keep flogging Dolphin, here is its apt show output:```
duckhook@Zeus:~$  apt show dolphin
Package: dolphin
Version: 4:21.12.3-0ubuntu1
Priority: optional
Section: universe/kde
Origin: Ubuntu
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 11.8 MB
Depends: baloo-kf5, kinit, kio, libc6 (>= 2.34), libdolphinvcs5 (= 4:21.12.3-0ubuntu1), libkf5activities5 (>= 5.81.0~), libkf5baloo5 (>= 5.81.0~), libkf5baloowidgets5 (>= 4:21.12.3~), libkf5bookmarks5 (>= 5.81.0~), libkf5codecs5 (>= 4.96.0), libkf5completion5 (>= 5.81.0~), libkf5configcore5 (>= 5.81.0~), libkf5configgui5 (>= 5.81.0~), libkf5configwidgets5 (>= 5.81.0), libkf5coreaddons5 (>= 5.81.0~), libkf5crash5 (>= 5.81.0~), libkf5dbusaddons5 (>= 5.81.0~), libkf5filemetadata3 (>= 5.81.0~), libkf5i18n5 (>= 5.81.0~), libkf5iconthemes5 (>= 5.81.0~), libkf5itemviews5 (>= 4.96.0), libkf5jobwidgets5 (>= 5.70.0), libkf5kcmutils5 (>= 5.81.0~), libkf5kiocore5 (>= 5.82.0), libkf5kiofilewidgets5 (>= 5.81.0~), libkf5kiogui5 (>= 5.83.0), libkf5kiowidgets5 (>= 5.84.0), libkf5newstuff5 (>= 5.81.0~), libkf5notifications5 (>= 5.81.0~), libkf5parts5 (>= 5.81.0~), libkf5service-bin, libkf5service5 (>= 4.96.0), libkf5solid5 (>= 5.81.0~), libkf5textwidgets5 (>= 5.81.0~), libkf5widgetsaddons5 (>= 5.78.0), libkf5windowsystem5 (>= 5.83.0), libkf5xmlgui5 (>= 5.88.0), libkuserfeedbackcore1 (>= 1.0.0), libkuserfeedbackwidgets1 (>= 1.0.0), libpackagekitqt5-1 (>= 1.0.2), libphonon4qt5-4 (>= 4:4.8.0), libqt5core5a (>= 5.15.1), libqt5dbus5 (>= 5.15.0~), libqt5gui5 (>= 5.15.0~) | libqt5gui5-gles (>= 5.15.0~), libqt5widgets5 (>= 5.15.1), libqt5xml5 (>= 5.15.0~), libstdc++6 (>= 5), phonon4qt5
Recommends: ffmpegthumbs, kdegraphics-thumbnailers, kimageformat-plugins, kio-extras
Suggests: dolphin-plugins
Conflicts: dolphin-plugins (<< 4:21.04.0~)
Homepage: https://apps.kde.org/en/dolphin
Task: kubuntu-desktop, kubuntu-full, ubuntustudio-desktop
Download-Size: 4,242 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
Description: file manager
 Dolphin is the default file manager in the Plasma, intended
 to be both powerful and easy to use.
 .
 Features include:
   Customisable sidebars
   "Breadcrumb" navigation
   View properties remembered for each folder
   Split views
   Network transparency
   Undo/redo functionality
   Ratings, comments, and tags
```
There's no field that forthrightly states the app is Qt5. The description refers to it as a "file manager in Plasma". You need to know that Plasma is Qt&#8209;based to make the connection. Likewise, the Maintainer is "Kubuntu Developers" requiring the prior knowledge that Kubuntu is Qt&#8209;based. The best indicator is "Original-Maintainer: Debian Qt/KDE Maintainers", but this is just fortuitous. Other apps will not have such pedigree.

However, if we now drill down further into one of the dependencies&#8230;```
duckhook@Zeus:~$  apt show libqt5gui5
Package: libqt5gui5
Version: 5.15.2+dfsg-15
Priority: optional
Section: universe/libs
Source: qtbase-opensource-src
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 13.1 MB
Depends: fontconfig, libc6 (>= 2.34), libdrm2 (>= 2.4.62), libegl1, libfontconfig1 (>= 2.12.6), libfreetype6 (>= 2.6), libgbm1 (>= 8.1~0), libgcc-s1 (>= 3.4), libgl1, libglib2.0-0 (>= 2.12.0), libharfbuzz0b (>= 1.6.0), libice6 (>= 1:1.0.0), libinput10 (>= 0.15.0), libjpeg8 (>= 8c), libmd4c0 (>= 0.2.7), libmtdev1 (>= 1.0.8), libpng16-16 (>= 1.6.2-1), libqt5core5a (>= 5.15.1), libqt5dbus5 (>= 5.14.1), libqt5network5 (>= 5.0.2), libsm6, libstdc++6 (>= 11), libudev1 (>= 183), libx11-6, libx11-xcb1 (>= 2:1.7.2), libxcb-glx0, libxcb-icccm4 (>= 0.4.1), libxcb-image0 (>= 0.2.1), libxcb-keysyms1 (>= 0.4.0), libxcb-randr0 (>= 1.3), libxcb-render-util0, libxcb-render0, libxcb-shape0, libxcb-shm0 (>= 1.10), libxcb-sync1, libxcb-xfixes0, libxcb-xinerama0, libxcb-xinput0 (>= 1.14), libxcb-xkb1, libxcb1 (>= 1.8), libxkbcommon-x11-0 (>= 0.5.0), libxkbcommon0 (>= 0.5.0), libxrender1, qtbase-abi-5-15-2, zlib1g (>= 1:1.1.4)
Recommends: libqt5svg5, qt5-gtk-platformtheme
Suggests: qt5-image-formats-plugins, qtwayland5
Conflicts: libqt5gui5-gles
Breaks: libqt5egldeviceintegration5 (<< 5.6.0~beta+dfsg-5~), libqt5xcbqpa5 (<< 5.6.0~beta+dfsg-5~)
Replaces: libqt5egldeviceintegration5 (<< 5.6.0~beta+dfsg-5~), libqt5xcbqpa5 (<< 5.6.0~beta+dfsg-5~)
Homepage: https://www.qt.io/developers/
Task: kubuntu-desktop, lubuntu-desktop, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop
Download-Size: 3,721 kB
APT-Manual-Installed: no
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
Description: Qt 5 GUI module
 Qt is a cross-platform C++ application framework. Qt's primary feature
 is its rich set of widgets that provide standard GUI functionality.
 .
 The QtGui module extends QtCore with GUI functionality.
```
&#8230;we get a lot more clarity. This is an obvious Qt library.

This is all my long&#8209;winded way of saying that development frameworks cannot be determined without some elbow grease and some insider knowledge. The need for such detective work is just part of Linux's DNA.

---

### Post by dragonfly41 on 2022-03-29
Since you mention Stacer these commands will help understand dependencies:

$ whereis stacer
stacer: /usr/bin/stacer /usr/share/stacer

$ ldd /usr/bin/stacer

and you see Qt5 libraries

Link to Qt5 development framework
Two options: closed source and open source

[https://www.qt.io/](https://www.qt.io/)
[FONT=monospace]
[/FONT]

---

### Post by Yellow Pasque on 2022-03-29
Some thoughts from a Debian/KDE user:
- The last time I tried Muon, it wasn't as fast as Synaptic. It's been a while, so maybe I should give it another look.
- "apt install -s " is a nice command for keeping an initial install minimal, but once you've already pulled in Qt5/gtk3 dependencies, it won't be effective, as the requisite packages will already be installed.
- The Dolphin file manager isn't a "simple" one. It's heavily integrated with KDE, so it's no surprise it brings in a ton of KDE packages.

---

### Post by wyattwhiteeagle on 2022-03-30
Thank you all for the simple to understand, in-depth responses.

quiverc seems to be very information in which flavour's are GTK3, KDE, Qt5, etc.

Even though any user can follow his specific posts about it,

Are there command line's to tell what a flavour is?

Example:
I'm using Xubuntu 20.04.
Now, through specific posts, I know Xubuntu is a GTK3.

That's knowledge gained ONLY by reading specific post's here on the forums.

A general rule I live by is...
"If it works, consider using it."
But here in Linux...there are limitations to that rule when the user takes into account the resource usage.
Especially when RAM is very limited.

---

### Post by DuckHook on 2022-03-30
You need to recognize two very important things:

[LIST=1]
[*]Linux is a geek's OS. It is designed for power, flexibility, privacy, security and independence. It is most definitely NOT designed to be easy to understand. You may think that your request is simple, but it is actually an inquiry into the guts of an app/flavour. If you want to see/understand such guts, you have to train to become a surgeon.
[*]The limitations to your rule do not just apply to Linux. For example, it is impossible to run AutoCAD on less than 8GB of RAM in Windows. It is impossible to install Windows itself on less than 30 GB of disk space. Frankly, limitations are more severe in the two big proprietary OSes than anything you will find on Linux. And while Linux has indeed suffered from resource bloat these last few years, it's behaved like a choir boy next to the escapades that the naughty ones have been up to.
[/LIST]

---

### Post by wyattwhiteeagle on 2022-04-08
Depends...Does it specify what a package depends on or does it specify what all depends on the specific package?

---

### Post by wyattwhiteeagle on 2022-04-08
Depends...Does it specify what a package depends on or does it specify what all depends on the specific package?> **DuckHook said:**
> You need to recognize two very important things:1. Linux is a geek's OS. It is designed for power, flexibility, privacy, security and independence. It is most definitely NOT designed to be easy to understand. You may think that your request is simple, but it is actually an inquiry into the guts of an app/flavour. If you want to see/understand such guts, you have to train to become a surgeon.-Yep, I agree...But isn't that one of the MANY reasons the UbuntuForums exists?-For people to learn the "in's and out's" of the Ubuntu flavour the person may be using?

---

### Post by wyattwhiteeagle on 2022-04-20
Is there a *buntu flavour that uses md5?

oops...nevermind...md5 is a checksum thing.

---

