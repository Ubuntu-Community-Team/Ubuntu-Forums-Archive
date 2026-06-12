---
title: "Random Freeze?"
date: 2012-12-06
forum: General Help
---

### Post by alexandari on 2012-12-06
Hello,this is yet another random freeze thread. I'm using Debian Squeeze (but I don't think it matters because it might be a linux issue,not a distro one) and KDE. As I was doing my thing,the system just froze. The X server went down and that's that. It's a fresh install,2 days old. Please help :KS

---

### Post by 2F4U on 2012-12-06
> 'm using Debian Squeeze (but I don't think it matters because it might be a linux issue,not a distro one) and KDE.

How comes you think its not a distro issue? Debian Squeeze and Ubuntu use quite different versions of packages. The kernel, for example, is 2.6.32 in Squeeze according to Distrowatch, while it is 3.2 or 3.5 in Ubuntu, depending on the version.

Additionally, you don't provide any relevant information such as hardware specs, log files, circumstances under which the freeze occurs, so I guess you might not get much feedback on your problem.

---

### Post by alexandari on 2012-12-07
I am willing to give any kind of info needed. Tell me what do you want me to post and I'll do it.

---

### Post by Bashing-om on 2012-12-07
alexandari; Hi !

---Freezing is so general, could be a lot of causes. May I suggest that you look in your logs and see if there is any indications of where the fault lies ? (/var/log/<filename>) and in your home directory .xseesion-errors file.

[INDENT]wish there was a way to help more <== BDQ

[/INDENT]

---

### Post by alexandari on 2012-12-07
So here is the huge xsession error output (The system hasn't freezed since I logged in today)
```
 kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kdeinit4: preparing to launch /usr/bin/dolphin
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
"/usr/bin/dolphin(4127)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(4127)" Soprano: "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/dolphin(4127)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(4127)" Soprano: "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/dolphin(4127)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(4127)" Soprano: "QLocalSocket::connectToServer: Connection refused"
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
dolphin(4127)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4127)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4127)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4127)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4127)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4127)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4127)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kDebugStream called after destruction (from void KDirWatchPrivate::removeEntry(KDirWatch*, KDirWatchPrivate::Entry*, KDirWatchPrivate::Entry*) file ../../kio/kio/kdirwatch.cpp line 950)
Cancelled INotify (fd 10, 1) for "/home/alexandar/.local/share"
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
[2190:2190:1207/213255:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
[2190:2190:1207/213413:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
[2190:2190:1207/213544:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kdeinit4: preparing to launch /usr/bin/dolphin
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
"/usr/bin/dolphin(4550)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(4550)" Soprano: "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/dolphin(4550)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(4550)" Soprano: "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/dolphin(4550)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(4550)" Soprano: "QLocalSocket::connectToServer: Connection refused"
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
dolphin(4550)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
dolphin(4550)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/alexandar/.local/share/mime/magic"
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kded(2076)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kio_thumbnail(4552)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kio_thumbnail(4552)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/alexandar/.local/share/mime/magic"
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
klauncher(2074)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2074)/kio (KLauncher): SlavePool: No communication with slave. 

kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kio_thumbnail(4691)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kio_thumbnail(4691)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/alexandar/.local/share/mime/magic"
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kio_thumbnail(4694)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kio_thumbnail(4694)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/alexandar/.local/share/mime/magic"
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
Error: Directory Olympus with 6144 entries considered invalid; not read.
kio_thumbnail(4695)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kio_thumbnail(4695)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/alexandar/.local/share/mime/magic"
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
Error: Thumbnail pointer references previously read Photo directory. Ignored.
kio_thumbnail(4696)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kio_thumbnail(4696)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/alexandar/.local/share/mime/magic"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
klauncher(2074)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2074)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2074)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2074)/kio (KLauncher): SlavePool: No communication with slave. 

kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/bin/audacious2
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
[2190:2190:1207/213938:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
[2190:2190:1207/214132:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
plasma-desktop(2132)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
plasma-desktop(2132)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
[2190:2190:1207/214358:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
Couldn't find node center. Skipping rendering.
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
plasma-desktop(2132)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+Tab" = "Walk Through Windows"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kdeinit4: preparing to launch /usr/bin/kinfocenter
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setFont: Painter not active
QPainter::setPen: Painter not active
QPainter::end: Painter not active, aborted
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setFont: Painter not active
QPainter::setPen: Painter not active
QPainter::end: Painter not active, aborted
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kdeinit4: preparing to launch /usr/bin/systemsettings
"KConfigIni: In file /home/alexandar/.kde/share/icons/Iceglass 4.0/index.theme, line 30: " Invalid entry (missing '=') 
"KConfigIni: In file /home/alexandar/.kde/share/icons/Iceglass 4.0/index.theme, line 30: " Invalid entry (missing '=') 
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_sheet"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_mousemark"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_slidingpopups"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_magiclamp"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_wobblywindows"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_fade"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_fadedesktop"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_shadow"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_thumbnailaside"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_slide"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_fallapart"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_login"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_explosion"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_taskbarthumbnail"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_logout"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_scalein"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_translucency"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_highlightwindow"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_minimizeanimation"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_invert"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_lookingglass"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_magnifier"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_sharpen"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_snaphelper"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_trackmouse"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_zoom"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_dialogparent"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_diminactive"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_dimscreen"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_slideback"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_boxswitch"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_coverswitch"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_cube"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_cubeslide"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_desktopgrid"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_flipswitch"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_presentwindows"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_resize"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_snow"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_showfps"
systemsettings(7607)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_showpaint"
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kdesu
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kdesud
kdesu(8062)/kdesu (kdelibs) KDESu::PtyProcess::exec: [ ../../kdesu/process.cpp : 295 ]  Running "/bin/su"
kdesu(8062)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "Password: "
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kdesu(8062)/kdesu (kdelibs) KDESu::PtyProcess::exec: [ ../../kdesu/process.cpp : 295 ]  Running "/bin/su"
kdesu(8062)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "Password: "
kdesu(8062)/kdesu (kdelibs) KDESu::PtyProcess::WaitSlave: [ ../../kdesu/process.cpp : 381 ]  Child pid 8069
kdesu(8062)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line ""
kdesu(8062)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "kdesu_stub"
kdesu(8062)/kdesu (kdelibs) KDESu::PtyProcess::exec: [ ../../kdesu/process.cpp : 295 ]  Running "/bin/su"
kdesu(8062)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "Password: "
kdesu(8062)/kdesu (kdelibs) KDESu::PtyProcess::WaitSlave: [ ../../kdesu/process.cpp : 381 ]  Child pid 8085
kdesu(8062)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line ""
kdesu(8062)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "kdesu_stub"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kdeinit4: preparing to launch /usr/bin/systemsettings
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+0" for "kwin" : "view_actual_size"
kglobalaccel(2128) KGlobalAccelDPrivate::_k_newGlobalShortcutNotification: Showing Notification for component "kwin"
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 2 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 2 
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+0" for "kwin" : "view_actual_size"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F7" for "kwin" : "ExposeClass"
krunner(2146): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+0" for "kwin" : "view_actual_size"
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
krunner(2146): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
Couldn't find node center. Skipping rendering.
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2405f2b
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2405511
yakuake(2487)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
yakuake(2487)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x241163b
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x24111b6
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
yakuake(2487)/kdeui (kdelibs): Attempt to use QAction "change-profile" with KXMLGUIFactory! 
yakuake(2487)/kdeui (kdelibs): Attempt to use QAction "manage-profiles" with KXMLGUIFactory! 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+0" for "kwin" : "view_actual_size"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F7" for "kwin" : "ExposeClass"
krunner(2146): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+0" for "kwin" : "view_actual_size"
Couldn't find node center. Skipping rendering.
Couldn't find node center. Skipping rendering.
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+0" for "kwin" : "view_actual_size"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+0" for "kwin" : "view_actual_size"
Couldn't find node center. Skipping rendering.
Couldn't find node center. Skipping rendering.
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+0" for "kwin" : "view_actual_size"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F7" for "kwin" : "ExposeClass"
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+0" for "kwin" : "view_actual_size"
Couldn't find node center. Skipping rendering.
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+0" for "kwin" : "view_actual_size"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+0" for "kwin" : "view_actual_size"
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 2 
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+0" for "kwin" : "view_actual_size"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::registerKey: Registering key "Meta+0" for "kwin" : "view_actual_size"
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F9" for "kwin" : "Expose"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F10" for "kwin" : "ExposeAll"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F7" for "kwin" : "ExposeClass"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+=" for "kwin" : "view_zoom_in"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+-" for "kwin" : "view_zoom_out"
kglobalaccel(2128) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+0" for "kwin" : "view_actual_size"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
Couldn't find node center. Skipping rendering.
Couldn't find node center. Skipping rendering.
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
krunner(2146): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
Couldn't find node center. Skipping rendering.
Couldn't find node center. Skipping rendering.
Couldn't find node center. Skipping rendering.
krunner(2146): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
krunner(2146): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
Couldn't find node center. Skipping rendering.
QGraphicsLinearLayout::removeAt: invalid index 1
krunner(2146): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
krunner(2146): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
krunner(2146): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 2 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
Couldn't find node center. Skipping rendering.
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+F2" = "Run Command"
kdeinit4: preparing to launch /usr/bin/konsole
Couldn't find node center. Skipping rendering.
konsole(8876)/kdeui (kdelibs): Attempt to use QAction "change-profile" with KXMLGUIFactory! 
systemsettings(7607)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2419303
yakuake(2487)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
yakuake(2487)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x241b721
yakuake(2487)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
yakuake(2487)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x241dcee
yakuake(2487)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
yakuake(2487)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2132): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kdeinit4: preparing to launch /usr/bin/systemsettings
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_sheet"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_mousemark"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_slidingpopups"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_magiclamp"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_wobblywindows"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_fade"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_fadedesktop"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_shadow"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_thumbnailaside"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_slide"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_fallapart"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_login"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_explosion"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_taskbarthumbnail"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_logout"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_scalein"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_translucency"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_highlightwindow"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_minimizeanimation"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_invert"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_lookingglass"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_magnifier"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_sharpen"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_snaphelper"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_trackmouse"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_zoom"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_dialogparent"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_diminactive"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_dimscreen"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_slideback"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_boxswitch"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_coverswitch"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_cube"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_cubeslide"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_desktopgrid"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_flipswitch"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_presentwindows"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_resize"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_snow"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  1  offers for  "kwin4_effect_showfps"
systemsettings(9054)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "kwin4_effect_showpaint"
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
krunner(2146): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
Couldn't find node center. Skipping rendering.
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 2 
kwin(2126): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
systemsettings(9054)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Couldn't find node center. Skipping rendering.
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
[2190:2190:1207/222417:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
[2190:2190:1207/222855:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
[2190:2190:1207/222919:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
[2190:2190:1207/223847:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
[2190:2190:1207/224721:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
plasma-desktop(2132)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
[2190:2190:1207/225632:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
[2190:2190:1207/225904:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2487)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "Alt+F2" = "Run Command"
krunner(2146): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
krunner(2146): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
krunner(2146): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
krunner(2146): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
konsole(13510)/kdeui (kdelibs): Attempt to use QAction "change-profile" with KXMLGUIFactory! 
kglobalaccel(2128) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2128) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
alexandar@debian:~$ 

```

The dmesg output

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-5-686 (Debian 2.6.32-46) (dannf@debian.org) (gcc version 4.3.5 (Debian 4.3.5-4) ) #1 SMP Sun Sep 23 09:49:36 UTC 2012
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077e70000 (usable)
[    0.000000]  BIOS-e820: 0000000077e70000 - 0000000077e83000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077e83000 - 0000000077e85000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077e85000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x77e70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01800000
[    0.000000] init_memory_mapping: 0000000000000000-00000000373fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037000000 page 2M
[    0.000000]  0037000000 - 00373fe000 page 4k
[    0.000000] kernel direct mapping tables up to 373fe000 @ 7000-d000
[    0.000000] RAMDISK: 377a1000 - 37fef901
[    0.000000] Allocated new RAMDISK: 00100000 - 0094e901
[    0.000000] Move RAMDISK from 00000000377a1000 - 0000000037fef900 to 00100000 - 0094e900
[    0.000000] ACPI: RSDP 000f7260 00024 (v02 TOSCPL)
[    0.000000] ACPI: XSDT 77e7aa9a 00064 (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 77e82939 000F4 (v03 TOSCPL Herring  06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 77e7aafe 07E3B (v01 TOSCPL    SB600 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 77e84fc0 00040
[    0.000000] ACPI: TCPA 77e82aa1 00032 (v02 TOSCPL          06040000 PTEC 00000000)
[    0.000000] ACPI: SLIC 77e82ad3 00176 (v01 TOSCPL TOSCPL00 06040000 LOHR 00000000)
[    0.000000] ACPI: SSDT 77e82c49 001C4 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 77e82e0d 00054 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 77e82e61 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 77e82e9d 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: ASF! 77e82ed5 0012B (v32    DMA AMDTBL   06040000 PTL  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1034MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 0 - 373fe000
[    0.000000]   node 0 low ram: 00000000 - 373fe000
[    0.000000]   node 0 bootmap 00009000 - 0000fe80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0001000000 - 00014ccd0c]    TEXT DATA BSS ==> [0001000000 - 00014ccd0c]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [00014cd000 - 00014d30f4]              BRK ==> [00014cd000 - 00014d30f4]
[    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #7 [0000100000 - 000094e901]      NEW RAMDISK ==> [0000100000 - 000094e901]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00f7300] f7300
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x00077e70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00077e70
[    0.000000] On node 0 totalpages: 491021
[    0.000000] free_area_init_node: node 0, pgdat c13b48c0, node_mem_map c14d5000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3965 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2069 pages used for memmap
[    0.000000]   HighMem zone: 262749 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:32 nr_cpumask_bits:32 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s34328 r0 d23016 u2097152
[    0.000000] pcpu-alloc: s34328 r0 d23016 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487184
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-5-686 root=UUID=414cb778-1b9b-4629-9c98-203c2a2a8715 ro quiet
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (000373fe:00077e70)
[    0.000000] Memory: 1933232k/1964480k available (2506k kernel code, 29796k reserved, 1326k data, 380k init, 1059272k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xffd56000 - 0xfffff000   (2724 kB)
[    0.000000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.000000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.000000]       .init : 0xc13bf000 - 0xc141e000   ( 380 kB)
[    0.000000]       .data : 0xc1272b9b - 0xc13be4c4   (1326 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1272b9b   (2506 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:1280
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1795.639 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.27 BogoMIPS (lpj=7182556)
[    0.004025] Security Framework initialized
[    0.004032] SELinux:  Disabled at boot.
[    0.004040] Mount-cache hash table entries: 512
[    0.004191] Initializing cgroup subsys ns
[    0.004195] Initializing cgroup subsys cpuacct
[    0.004199] Initializing cgroup subsys devices
[    0.004202] Initializing cgroup subsys freezer
[    0.004204] Initializing cgroup subsys net_cls
[    0.004229] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004232] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004234] CPU: Physical Processor ID: 0
[    0.004236] CPU: Processor Core ID: 0
[    0.004240] mce: CPU supports 5 MCE banks
[    0.004254] using C1E aware idle routine
[    0.004263] Performance Events: AMD PMU driver.
[    0.004268] ... version:                0
[    0.004270] ... bit width:              48
[    0.004272] ... generic registers:      4
[    0.004274] ... value mask:             0000ffffffffffff
[    0.004276] ... max period:             00007fffffffffff
[    0.004278] ... fixed-purpose events:   0
[    0.004280] ... event mask:             000000000000000f
[    0.004285] Checking 'hlt' instruction... OK.
[    0.021015] ACPI: Core revision 20090903
[    0.021018] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.024856] ACPI: Forced DSDT copy: length 0x07E3B copied locally, original unmapped
[    0.028073] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028495] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.032001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.032001] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.032001] ..... (found apic 0 pin 0) ...
[    0.072143] ....... works.
[    0.072145] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.160091] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.160128] Brought up 2 CPUs
[    0.160131] Total of 2 processors activated (7182.25 BogoMIPS).
[    0.160127] System has AMD C1E enabled
[    0.160127] Switch to broadcast mode on CPU1
[    0.160509] CPU0 attaching sched-domain:
[    0.160514]  domain 0: span 0-1 level MC
[    0.160518]   groups: group c2403778 cpus 0 group c2603778 cpus 1
[    0.160525] CPU1 attaching sched-domain:
[    0.160528]  domain 0: span 0-1 level MC
[    0.160530]   groups: group c2603778 cpus 1 group c2403778 cpus 0
[    0.160610] Switch to broadcast mode on CPU0
[    0.160610] devtmpfs: initialized
[    0.160610] regulator: core version 0.5
[    0.160610] NET: Registered protocol family 16
[    0.160610] ACPI: bus type pci registered
[    0.160610] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 26
[    0.160610] PCI: MCFG area at e0000000 reserved in E820
[    0.160610] PCI: Using MMCONFIG for extended config space
[    0.160610] PCI: Using configuration type 1 for base access
[    0.160610] bio: create slab <bio-0> at 0
[    0.160622] ACPI: EC: Look up EC in DSDT
[    0.162054] ACPI Error: No handler for Region [ERAM] (f6c18938) [EmbeddedControl] (20090903/evregion-319)
[    0.162054] ACPI Error: Region EmbeddedControl(3) has no handler (20090903/exfldio-295)
[    0.162054] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.HTEV] (Node f6c10e10), AE_NOT_EXIST
[    0.162054] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node f6c19d08), AE_NOT_EXIST
[    0.162054] ACPI: BIOS _OSI(Linux) query ignored
[    0.172080] ACPI: Interpreter enabled
[    0.172083] ACPI: (supports S0 S3 S4 S5)
[    0.172105] ACPI: Using IOAPIC for interrupt routing
[    0.172829] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.224321] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.224704] ACPI: EC: GPE = 0x13, I/O: command/status = 0x66, data = 0x62
[    0.224976] ACPI: No dock devices found.
[    0.226060] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.226192] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.226195] pci 0000:00:05.0: PME# disabled
[    0.226239] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.226243] pci 0000:00:06.0: PME# disabled
[    0.226287] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.226290] pci 0000:00:07.0: PME# disabled
[    0.226344] pci 0000:00:12.0: reg 10 io port: [0x8440-0x8447]
[    0.226353] pci 0000:00:12.0: reg 14 io port: [0x8434-0x8437]
[    0.226361] pci 0000:00:12.0: reg 18 io port: [0x8438-0x843f]
[    0.226369] pci 0000:00:12.0: reg 1c io port: [0x8430-0x8433]
[    0.226377] pci 0000:00:12.0: reg 20 io port: [0x8400-0x840f]
[    0.226386] pci 0000:00:12.0: reg 24 32bit mmio: [0xf8709000-0xf87093ff]
[    0.226406] pci 0000:00:12.0: set SATA to AHCI mode
[    0.226458] pci 0000:00:13.0: reg 10 32bit mmio: [0xf8704000-0xf8704fff]
[    0.226521] pci 0000:00:13.1: reg 10 32bit mmio: [0xf8705000-0xf8705fff]
[    0.226583] pci 0000:00:13.2: reg 10 32bit mmio: [0xf8706000-0xf8706fff]
[    0.226645] pci 0000:00:13.3: reg 10 32bit mmio: [0xf8707000-0xf8707fff]
[    0.226707] pci 0000:00:13.4: reg 10 32bit mmio: [0xf8708000-0xf8708fff]
[    0.226788] pci 0000:00:13.5: reg 10 32bit mmio: [0xf8709400-0xf87094ff]
[    0.226859] pci 0000:00:13.5: supports D1 D2
[    0.226861] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.226866] pci 0000:00:13.5: PME# disabled
[    0.226914] pci 0000:00:14.0: reg 10 io port: [0x8410-0x841f]
[    0.226996] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.227005] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.227013] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.227021] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.227029] pci 0000:00:14.1: reg 20 io port: [0x8420-0x842f]
[    0.227089] pci 0000:00:14.2: reg 10 64bit mmio: [0xf8700000-0xf8703fff]
[    0.227145] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.227150] pci 0000:00:14.2: PME# disabled
[    0.227360] pci 0000:01:05.0: reg 10 64bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.227367] pci 0000:01:05.0: reg 18 64bit mmio: [0xf8100000-0xf810ffff]
[    0.227372] pci 0000:01:05.0: reg 20 io port: [0x9000-0x90ff]
[    0.227378] pci 0000:01:05.0: reg 24 32bit mmio: [0xf8000000-0xf80fffff]
[    0.227395] pci 0000:01:05.0: supports D1 D2
[    0.227416] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.227420] pci 0000:00:01.0: bridge 32bit mmio: [0xf8000000-0xf81fffff]
[    0.227425] pci 0000:00:01.0: bridge 64bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.227477] pci 0000:00:05.0: bridge io port: [0x00-0xfff]
[    0.227481] pci 0000:00:05.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.227531] pci 0000:0e:00.0: reg 10 io port: [0xa000-0xa0ff]
[    0.227550] pci 0000:0e:00.0: reg 18 64bit mmio: [0xf8300000-0xf8300fff]
[    0.227569] pci 0000:0e:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.227635] pci 0000:0e:00.0: supports D1 D2
[    0.227638] pci 0000:0e:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.227643] pci 0000:0e:00.0: PME# disabled
[    0.227675] pci 0000:0e:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.227754] pci 0000:00:06.0: bridge io port: [0xa000-0xafff]
[    0.227758] pci 0000:00:06.0: bridge 32bit mmio: [0xf8300000-0xf83fffff]
[    0.227827] pci 0000:14:00.0: reg 10 64bit mmio: [0xf8200000-0xf820ffff]
[    0.227982] pci 0000:14:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.228073] pci 0000:00:07.0: bridge 32bit mmio: [0xf8200000-0xf82fffff]
[    0.228131] pci 0000:1a:04.0: reg 10 32bit mmio: [0xf8404000-0xf8404fff]
[    0.228172] pci 0000:1a:04.0: supports D1 D2
[    0.228175] pci 0000:1a:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.228181] pci 0000:1a:04.0: PME# disabled
[    0.228230] pci 0000:1a:04.1: reg 10 32bit mmio: [0xf8406000-0xf84067ff]
[    0.228241] pci 0000:1a:04.1: reg 14 32bit mmio: [0xf8400000-0xf8403fff]
[    0.228317] pci 0000:1a:04.1: supports D1 D2
[    0.228320] pci 0000:1a:04.1: PME# supported from D0 D1 D2 D3hot
[    0.228326] pci 0000:1a:04.1: PME# disabled
[    0.228374] pci 0000:1a:04.2: reg 10 32bit mmio: [0xf8405000-0xf8405fff]
[    0.228452] pci 0000:1a:04.2: supports D1 D2
[    0.228455] pci 0000:1a:04.2: PME# supported from D0 D1 D2 D3hot
[    0.228461] pci 0000:1a:04.2: PME# disabled
[    0.228509] pci 0000:1a:04.3: reg 10 32bit mmio: [0xf8406800-0xf84068ff]
[    0.228587] pci 0000:1a:04.3: supports D1 D2
[    0.228590] pci 0000:1a:04.3: PME# supported from D0 D1 D2 D3hot
[    0.228596] pci 0000:1a:04.3: PME# disabled
[    0.228663] pci 0000:00:14.4: transparent bridge
[    0.228671] pci 0000:00:14.4: bridge 32bit mmio: [0xf8400000-0xf84fffff]
[    0.228711] pci_bus 0000:00: on NUMA node 0
[    0.228716] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.228830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.228898] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.228959] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    0.229023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB5_._PRT]
[    0.229121] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.229192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.234889] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.234995] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.235098] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.235202] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.235308] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.235411] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.235515] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.235618] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.235745] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.235752] vgaarb: loaded
[    0.236047] PCI: Using ACPI for IRQ routing
[    0.236053] pci 0000:00:05.0: BAR 13: can't allocate resource
[    0.236056] pci 0000:00:05.0: BAR 14: can't allocate resource
[    0.240050] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.240056] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.242097] Switching to clocksource hpet
[    0.242105] pnp: PnP ACPI init
[    0.242105] ACPI: bus type pnp registered
[    0.265117] pnp: PnP ACPI: found 11 devices
[    0.265120] ACPI: ACPI bus type pnp unregistered
[    0.265123] PnPBIOS: Disabled by ACPI PNP
[    0.265138] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.265142] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.265153] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.265158] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.265161] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.265165] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.265168] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.265172] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.265176] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.265179] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.265183] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.265186] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.265190] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.265194] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.265198] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.265201] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.265205] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.265209] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.265213] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.265216] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.265220] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.265224] system 00:08: ioport range 0xfd60-0xfddf has been reserved
[    0.265235] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.265239] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
[    0.300095] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.300099] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.300103] pci 0000:00:01.0:   MEM window: 0xf8000000-0xf81fffff
[    0.300107] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.300112] pci 0000:00:05.0: PCI bridge, secondary bus 0000:08
[    0.300116] pci 0000:00:05.0:   IO window: 0x2000-0x2fff
[    0.300119] pci 0000:00:05.0:   MEM window: 0x84000000-0x841fffff
[    0.300123] pci 0000:00:05.0:   PREFETCH window: 0x00000084200000-0x000000843fffff
[    0.300129] pci 0000:00:06.0: PCI bridge, secondary bus 0000:0e
[    0.300132] pci 0000:00:06.0:   IO window: 0xa000-0xafff
[    0.300136] pci 0000:00:06.0:   MEM window: 0xf8300000-0xf83fffff
[    0.300140] pci 0000:00:06.0:   PREFETCH window: 0x84400000-0x844fffff
[    0.300144] pci 0000:00:07.0: PCI bridge, secondary bus 0000:14
[    0.300147] pci 0000:00:07.0:   IO window: disabled
[    0.300151] pci 0000:00:07.0:   MEM window: 0xf8200000-0xf82fffff
[    0.300154] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.300161] pci 0000:1a:04.0: CardBus bridge, secondary bus 0000:1b
[    0.300164] pci 0000:1a:04.0:   IO window: 0x003000-0x0030ff
[    0.300173] pci 0000:1a:04.0:   IO window: 0x003400-0x0034ff
[    0.300179] pci 0000:1a:04.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.300185] pci 0000:1a:04.0:   MEM window: 0x88000000-0x8bffffff
[    0.300191] pci 0000:00:14.4: PCI bridge, secondary bus 0000:1a
[    0.300195] pci 0000:00:14.4:   IO window: 0x3000-0x3fff
[    0.300202] pci 0000:00:14.4:   MEM window: 0xf8400000-0xf84fffff
[    0.300207] pci 0000:00:14.4:   PREFETCH window: 0x80000000-0x83ffffff
[    0.300223] pci 0000:00:05.0: enabling device (0000 -> 0003)
[    0.300228] pci 0000:00:05.0: setting latency timer to 64
[    0.300234] pci 0000:00:06.0: setting latency timer to 64
[    0.300240] pci 0000:00:07.0: setting latency timer to 64
[    0.300262] pci 0000:1a:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.300270] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.300273] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.300276] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.300279] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xf81fffff]
[    0.300283] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
[    0.300286] pci_bus 0000:08: resource 0 io:  [0x2000-0x2fff]
[    0.300290] pci_bus 0000:08: resource 1 mem: [0x84000000-0x841fffff]
[    0.300293] pci_bus 0000:08: resource 2 pref mem [0x84200000-0x843fffff]
[    0.300296] pci_bus 0000:0e: resource 0 io:  [0xa000-0xafff]
[    0.300300] pci_bus 0000:0e: resource 1 mem: [0xf8300000-0xf83fffff]
[    0.300303] pci_bus 0000:0e: resource 2 pref mem [0x84400000-0x844fffff]
[    0.300307] pci_bus 0000:14: resource 1 mem: [0xf8200000-0xf82fffff]
[    0.300310] pci_bus 0000:1a: resource 0 io:  [0x3000-0x3fff]
[    0.300313] pci_bus 0000:1a: resource 1 mem: [0xf8400000-0xf84fffff]
[    0.300317] pci_bus 0000:1a: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.300320] pci_bus 0000:1a: resource 3 io:  [0x00-0xffff]
[    0.300323] pci_bus 0000:1a: resource 4 mem: [0x000000-0xffffffff]
[    0.300327] pci_bus 0000:1b: resource 0 io:  [0x3000-0x30ff]
[    0.300330] pci_bus 0000:1b: resource 1 io:  [0x3400-0x34ff]
[    0.300333] pci_bus 0000:1b: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.300337] pci_bus 0000:1b: resource 3 mem: [0x88000000-0x8bffffff]
[    0.300376] NET: Registered protocol family 2
[    0.300474] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.300857] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.301559] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.301897] TCP: Hash tables configured (established 131072 bind 65536)
[    0.301900] TCP reno registered
[    0.302002] NET: Registered protocol family 1
[    0.302046] pci 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.302074] pci 0000:00:13.0: PCI INT A disabled
[    0.302082] pci 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.302096] pci 0000:00:13.1: PCI INT B disabled
[    0.302105] pci 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.302118] pci 0000:00:13.2: PCI INT C disabled
[    0.302126] pci 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.302139] pci 0000:00:13.3: PCI INT B disabled
[    0.302146] pci 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.302160] pci 0000:00:13.4: PCI INT C disabled
[    0.302172] pci 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.302189] pci 0000:00:13.5: PCI INT D disabled
[    0.302206] pci 0000:01:05.0: Boot video device
[    0.302280] Unpacking initramfs...
[    0.562151] Freeing initrd memory: 8506k freed
[    0.567514] audit: initializing netlink socket (disabled)
[    0.567530] type=2000 audit(1354914630.565:1): initialized
[    0.571373] highmem bounce pool size: 64 pages
[    0.571379] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.573092] VFS: Disk quotas dquot_6.5.2
[    0.573158] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.573236] msgmni has been set to 1725
[    0.573553] alg: No test for stdrng (krng)
[    0.573635] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.573639] io scheduler noop registered
[    0.573641] io scheduler anticipatory registered
[    0.573644] io scheduler deadline registered
[    0.573687] io scheduler cfq registered (default)
[    0.573826] pcieport 0000:00:05.0: irq 24 for MSI/MSI-X
[    0.573833] pcieport 0000:00:05.0: setting latency timer to 64
[    0.573927] pcieport 0000:00:06.0: irq 25 for MSI/MSI-X
[    0.573932] pcieport 0000:00:06.0: setting latency timer to 64
[    0.574004] pcieport 0000:00:07.0: irq 26 for MSI/MSI-X
[    0.574009] pcieport 0000:00:07.0: setting latency timer to 64
[    0.574146] isapnp: Scanning for PnP cards...
[    0.930739] isapnp: No Plug & Play device found
[    0.932350] Linux agpgart interface v0.103
[    0.932715] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.933145] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.959431] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.959440] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.959507] mice: PS/2 mouse device common for all mice
[    0.959552] rtc_cmos 00:04: RTC can wake from S4
[    0.959586] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.959616] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.959628] cpuidle: using governor ladder
[    0.959630] cpuidle: using governor menu
[    0.959635] No iBFT detected.
[    0.960059] TCP cubic registered
[    0.960217] NET: Registered protocol family 10
[    0.961172] Mobile IPv6
[    0.961175] NET: Registered protocol family 17
[    0.961191] Using IPI No-Shortcut mode
[    0.961258] PM: Resume from disk failed.
[    0.961270] registered taskstats version 1
[    0.961694] rtc_cmos 00:04: setting system clock to 2012-12-07 21:10:32 UTC (1354914632)
[    0.961761] Initalizing network drop monitor service
[    0.961796] Freeing unused kernel memory: 380k freed
[    0.962094] Write protecting the kernel text: 2508k
[    0.962124] Write protecting the kernel read-only data: 920k
[    0.981894] udev[56]: starting version 164
[    0.983656] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    1.127074] SCSI subsystem initialized
[    1.138317] usbcore: registered new interface driver usbfs
[    1.138347] usbcore: registered new interface driver hub
[    1.138381] usbcore: registered new device driver usb
[    1.146191] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.146231] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.146257] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    1.146291] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    1.146327] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    1.146342] ehci_hcd 0000:00:13.5: debug port 1
[    1.146370] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf8709400
[    1.146399] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.146415] r8169 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.146453] r8169 0000:0e:00.0: setting latency timer to 64
[    1.146511] r8169 0000:0e:00.0: irq 27 for MSI/MSI-X
[    1.147222] r8169 0000:0e:00.0: eth0: RTL8101e at 0xf7d66000, 00:1b:38:15:41:e9, XID 14000000 IRQ 27
[    1.148909] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.157033] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    1.157079] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.157083] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.157086] usb usb1: Product: EHCI Host Controller
[    1.157089] usb usb1: Manufacturer: Linux 2.6.32-5-686 ehci_hcd
[    1.157091] usb usb1: SerialNumber: 0000:00:13.5
[    1.157194] usb usb1: configuration #1 chosen from 1 choice
[    1.157229] hub 1-0:1.0: USB hub found
[    1.157240] hub 1-0:1.0: 10 ports detected
[    1.166598] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.166622] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.166644] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    1.166676] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf8704000
[    1.191266] libata version 3.00 loaded.
[    1.199631] firewire_ohci 0000:1a:04.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.201839] sdhci: Secure Digital Host Controller Interface driver
[    1.201843] sdhci: Copyright(c) Pierre Ossman
[    1.224068] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.224072] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.224075] usb usb2: Product: OHCI Host Controller
[    1.224078] usb usb2: Manufacturer: Linux 2.6.32-5-686 ohci_hcd
[    1.224080] usb usb2: SerialNumber: 0000:00:13.0
[    1.224176] usb usb2: configuration #1 chosen from 1 choice
[    1.224216] hub 2-0:1.0: USB hub found
[    1.224232] hub 2-0:1.0: 2 ports detected
[    1.224302] ahci 0000:00:12.0: version 3.0
[    1.224324] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.224357] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.224456] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.224461] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.224951] scsi0 : ahci
[    1.225064] scsi1 : ahci
[    1.225130] scsi2 : ahci
[    1.225191] scsi3 : ahci
[    1.225336] ata1: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709100 irq 22
[    1.225341] ata2: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709180 irq 22
[    1.225346] ata3: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709200 irq 22
[    1.225351] ata4: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709280 irq 22
[    1.225394] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.225437] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.225537] scsi4 : pata_atiixp
[    1.225616] scsi5 : pata_atiixp
[    1.226252] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    1.226256] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    1.226299] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.226332] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.226353] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    1.226383] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf8705000
[    1.269027] firewire_ohci: Added fw-ohci device 0000:1a:04.1, OHCI version 1.10
[    1.269065] sdhci-pci 0000:1a:04.3: SDHCI controller found [104c:803c] (rev 0)
[    1.269089] sdhci-pci 0000:1a:04.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.269179] Registered led device: mmc0::
[    1.269219] mmc0: SDHCI controller on PCI [0000:1a:04.3] using DMA
[    1.281070] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.281074] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.281077] usb usb3: Product: OHCI Host Controller
[    1.281080] usb usb3: Manufacturer: Linux 2.6.32-5-686 ohci_hcd
[    1.281082] usb usb3: SerialNumber: 0000:00:13.1
[    1.281175] usb usb3: configuration #1 chosen from 1 choice
[    1.281210] hub 3-0:1.0: USB hub found
[    1.281225] hub 3-0:1.0: 2 ports detected
[    1.281289] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.281313] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    1.281322] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    1.281346] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf8706000
[    1.336068] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.336071] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.336074] usb usb4: Product: OHCI Host Controller
[    1.336077] usb usb4: Manufacturer: Linux 2.6.32-5-686 ohci_hcd
[    1.336080] usb usb4: SerialNumber: 0000:00:13.2
[    1.336146] usb usb4: configuration #1 chosen from 1 choice
[    1.336175] hub 4-0:1.0: USB hub found
[    1.336185] hub 4-0:1.0: 2 ports detected
[    1.336236] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.336252] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    1.336261] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    1.336276] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf8707000
[    1.393082] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.393085] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.393089] usb usb5: Product: OHCI Host Controller
[    1.393091] usb usb5: Manufacturer: Linux 2.6.32-5-686 ohci_hcd
[    1.393094] usb usb5: SerialNumber: 0000:00:13.3
[    1.393162] usb usb5: configuration #1 chosen from 1 choice
[    1.393191] hub 5-0:1.0: USB hub found
[    1.393201] hub 5-0:1.0: 2 ports detected
[    1.393253] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.393268] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    1.393276] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    1.393292] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf8708000
[    1.404732] ata5.00: ATAPI: PIONEER DVD-RW DVR-K17LF, 4.53, max UDMA/33
[    1.436708] ata5.00: configured for UDMA/33
[    1.448278] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.448281] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.448285] usb usb6: Product: OHCI Host Controller
[    1.448287] usb usb6: Manufacturer: Linux 2.6.32-5-686 ohci_hcd
[    1.448290] usb usb6: SerialNumber: 0000:00:13.4
[    1.448356] usb usb6: configuration #1 chosen from 1 choice
[    1.448385] hub 6-0:1.0: USB hub found
[    1.448395] hub 6-0:1.0: 2 ports detected
[    1.544064] ata3: SATA link down (SStatus 0 SControl 300)
[    1.544099] ata2: SATA link down (SStatus 0 SControl 300)
[    1.544151] ata4: SATA link down (SStatus 0 SControl 300)
[    1.580040] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    1.708029] ata1: softreset failed (device not ready)
[    1.708076] ata1: applying SB600 PMP SRST workaround and retrying
[    1.726479] usb 1-8: New USB device found, idVendor=04f2, idProduct=b008
[    1.726483] usb 1-8: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.726487] usb 1-8: Product: Chicony USB 2.0 Camera
[    1.726490] usb 1-8: Manufacturer: Chicony Electronics Co., Ltd.
[    1.726492] usb 1-8: SerialNumber: SN0001
[    1.726593] usb 1-8: configuration #1 chosen from 1 choice
[    1.769113] firewire_core: created device fw0: GUID 00023f76c04179d3, S400
[    1.864031] usb 5-1: new full speed USB device using ohci_hcd and address 2
[    1.872047] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.872696] ata1.00: ATA-8: FUJITSU MHX2250BT, 0040000C, max UDMA/100
[    1.872700] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.872722] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.873492] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.873496] ata1.00: configured for UDMA/100
[    1.889172] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHX2250B 0040 PQ: 0 ANSI: 5
[    1.899197] scsi 4:0:0:0: CD-ROM            PIONEER  DVD-RW DVR-K17LF 4.53 PQ: 0 ANSI: 5
[    2.031081] usb 5-1: New USB device found, idVendor=09da, idProduct=054f
[    2.031085] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.031088] usb 5-1: Product: USB Device
[    2.031090] usb 5-1: Manufacturer: A4TECH
[    2.031163] usb 5-1: configuration #1 chosen from 1 choice
[    2.046276] usbcore: registered new interface driver hiddev
[    2.049694] input: A4TECH USB Device as /devices/pci0000:00/0000:00:13.3/usb5/5-1/5-1:1.0/input/input1
[    2.049812] generic-usb 0003:09DA:054F.0001: input,hiddev0,hidraw0: USB HID v1.11 Keyboard [A4TECH USB Device] on usb-0000:00:13.3-1/input0
[    2.053398] input: A4TECH USB Device as /devices/pci0000:00/0000:00:13.3/usb5/5-1/5-1:1.1/input/input2
[    2.053460] generic-usb 0003:09DA:054F.0002: input,hidraw1: USB HID v1.11 Mouse [A4TECH USB Device] on usb-0000:00:13.3-1/input1
[    2.053483] usbcore: registered new interface driver usbhid
[    2.053486] usbhid: v2.6:USB HID core driver
[    2.077242] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.077365] sd 0:0:0:0: [sda] Write Protect is off
[    2.077370] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.077416] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.077669]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.107054] Uniform CD-ROM driver Revision: 3.20
[    2.107156] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.118555]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.140461] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.147033] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.148001] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.893193] PM: Starting manual resume from disk
[    2.893198] PM: Resume from partition 8:5
[    2.893201] PM: Checking hibernation image.
[    2.893430] PM: Error -22 checking image file
[    2.893432] PM: Resume from disk failed.
[    2.977176] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    5.070845] udev[430]: starting version 164
[    5.522737] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    5.525869] acpi device:25: registered as cooling_device0
[    5.526059] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:23/LNXVIDEO:01/input/input3
[    5.526068] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    5.828714] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input4
[    5.828795] ACPI: Lid Switch [LID]
[    5.829159] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input5
[    5.829166] ACPI: Power Button [PWRB]
[    5.829306] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input6
[    5.829310] ACPI: Power Button [PWRF]
[    5.833901] ACPI: processor limited to max C-state 1
[    5.833938] processor LNXCPU:00: registered as cooling_device1
[    5.833980] processor LNXCPU:01: registered as cooling_device2
[    5.887153] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    5.926549] input: PC Speaker as /devices/platform/pcspkr/input/input7
[    5.953969] ACPI: Battery Slot [BAT1] (battery present)
[    5.956601] ACPI: AC Adapter [ACAD] (on-line)
[    6.061291] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.101958] yenta_cardbus 0000:1a:04.0: CardBus bridge found [1179:ff00]
[    6.101983] yenta_cardbus 0000:1a:04.0: Enabling burst memory read transactions
[    6.101990] yenta_cardbus 0000:1a:04.0: Using CSCINT to route CSC interrupts to PCI
[    6.101993] yenta_cardbus 0000:1a:04.0: Routing CardBus interrupts to PCI
[    6.102000] yenta_cardbus 0000:1a:04.0: TI: mfunc 0x10a01b22, devctl 0x64
[    6.109462] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    6.334036] yenta_cardbus 0000:1a:04.0: ISA IRQ mask 0x0cf8, PCI irq 20
[    6.334045] yenta_cardbus 0000:1a:04.0: Socket status: 30000006
[    6.334050] pci_bus 0000:1a: Raising subordinate bus# of parent bus (#1a) from #1b to #1e
[    6.334061] yenta_cardbus 0000:1a:04.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[    6.334066] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[    6.334326] yenta_cardbus 0000:1a:04.0: pcmcia: parent PCI bridge Memory window: 0xf8400000 - 0xf84fffff
[    6.334331] yenta_cardbus 0000:1a:04.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[    6.445931] cfg80211: Using static regulatory domain info
[    6.445935] cfg80211: Regulatory domain: US
[    6.445938]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.445942]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[    6.445945]  (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[    6.445949]  (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[    6.445952]  (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[    6.445955]  (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[    6.445959]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[    6.446275] cfg80211: Calling CRDA for country: US
[    6.448534] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[    6.452550] tifm_7xx1 0000:1a:04.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    6.527174] Linux video capture interface: v2.00
[    6.671944] [drm] Initialized drm 1.1.0 20060810
[    6.774834] ath5k 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    6.774845] ath5k 0000:14:00.0: setting latency timer to 64
[    6.774907] ath5k 0000:14:00.0: registered as 'phy0'
[    7.159838] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[    7.194167] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[    7.272671] ath: EEPROM regdomain: 0x64
[    7.272675] ath: EEPROM indicates we should expect a direct regpair map
[    7.272679] ath: Country alpha2 being used: 00
[    7.272682] ath: Regpair used: 0x64
[    7.325144] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[    7.328365] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:13.5/usb1/1-8/1-8:1.0/input/input10
[    7.328430] usbcore: registered new interface driver uvcvideo
[    7.328433] USB Video Class driver (v0.1.0)
[    7.587541] phy0: Selected rate control algorithm 'minstrel'
[    7.588316] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[    7.728417] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[    7.730375] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[    7.731208] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    7.731863] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    7.732625] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    8.171291] [drm] radeon kernel modesetting enabled.
[    8.171379] radeon 0000:01:05.0: power state changed by ACPI to D0
[    8.171388] radeon 0000:01:05.0: power state changed by ACPI to D0
[    8.171398] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.173253] [drm] radeon: Initializing kernel modesetting.
[    8.173425] [drm] register mmio base: 0xF8100000
[    8.173429] [drm] register mmio size: 65536
[    8.173583] ATOM BIOS: ATI
[    8.173805] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[    8.173829] [drm] radeon: VRAM 128M
[    8.173832] [drm] radeon: VRAM from 0x78000000 to 0x7FFFFFFF
[    8.173834] [drm] radeon: GTT 512M
[    8.173837] [drm] radeon: GTT from 0x80000000 to 0x9FFFFFFF
[    8.173868] [drm] radeon: irq initialized.
[    8.174106] [drm] Detected VRAM RAM=128M, BAR=128M
[    8.174111] [drm] RAM width 128bits DDR
[    8.174240] [TTM] Zone  kernel: Available graphics memory: 441950 kiB.
[    8.174244] [TTM] Zone highmem: Available graphics memory: 971586 kiB.
[    8.174268] [drm] radeon: 128M of VRAM memory ready
[    8.174270] [drm] radeon: 512M of GTT memory ready.
[    8.174288] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    8.178249] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[    8.178267] [drm] radeon: cp idle (0x10000C03)
[    8.178314] [drm] Loading RS690/RS740 Microcode
[    8.178318] platform radeon_cp.0: firmware: requesting radeon/RS690_cp.bin
[    8.226065] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.256689] radeon_cp: Failed to load firmware "radeon/RS690_cp.bin"
[    8.256735] [drm:r100_cp_init] *ERROR* Failed to load firmware!
[    8.256778] radeon 0000:01:05.0: failled initializing CP (-2).
[    8.256820] radeon 0000:01:05.0: Disabling GPU acceleration
[    8.256862] [drm] radeon: cp finalized
[    8.257667] [drm] Default TV standard: NTSC
[    8.257695] [drm] Radeon Display Connectors
[    8.257698] [drm] Connector 0:
[    8.257699] [drm]   VGA
[    8.257703] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[    8.257705] [drm]   Encoders:
[    8.257707] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    8.257709] [drm] Connector 1:
[    8.257711] [drm]   LVDS
[    8.257714] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[    8.257716] [drm]   Encoders:
[    8.257718] [drm]     LCD1: INTERNAL_LVTM1
[    8.257720] [drm] Connector 2:
[    8.257722] [drm]   S-video
[    8.257723] [drm]   Encoders:
[    8.257725] [drm]     TV1: INTERNAL_KLDSCP_DAC1
[    8.389293] hda_codec: ALC268: BIOS auto-probing.
[    8.389805] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input11
[    8.813225] [drm] fb mappable at 0xF0040000
[    8.813229] [drm] vram apper at 0xF0000000
[    8.813232] [drm] size 4096000
[    8.813234] [drm] fb depth is 24
[    8.813236] [drm]    pitch is 5120
[    9.139149] Console: switching to colour frame buffer device 160x50
[    9.149247] fb0: radeondrmfb frame buffer device
[    9.149248] registered panic notifier
[    9.149254] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[    9.946518] Adding 2928632k swap on /dev/sda5.  Priority:-1 extents:1 across:2928632k 
[   10.339079] loop: module loaded
[   11.863636] fuse init (API version 7.13)
[   13.933623] input: ACPI Virtual Keyboard Device as /devices/virtual/input/input12
[   14.824295] apm: BIOS not found.
[   16.959004] Bluetooth: Core ver 2.15
[   16.959080] NET: Registered protocol family 31
[   16.959082] Bluetooth: HCI device and connection manager initialized
[   16.959086] Bluetooth: HCI socket layer initialized
[   17.135881] Bluetooth: L2CAP ver 2.14
[   17.135885] Bluetooth: L2CAP socket layer initialized
[   17.612939] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.612944] Bluetooth: BNEP filters: protocol multicast
[   17.732466] Bridge firewalling registered
[   18.061743] r8169 0000:0e:00.0: eth0: link down
[   18.062011] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.067337] Bluetooth: SCO (Voice Link) ver 0.6
[   18.067340] Bluetooth: SCO socket layer initialized
[   18.080252] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.008469] lp: driver loaded but no devices found
[   21.026110] ppdev: user-space parallel port driver
[   22.761974] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00)
[   22.762032] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x12
[   22.762035] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   22.762038] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   23.004041] Clocksource tsc unstable (delta = -119744122 ns)
[  104.219573] wlan0: direct probe to AP fc:75:16:9c:91:a2 (try 1)
[  104.224522] wlan0: direct probe responded
[  104.224532] wlan0: authenticate with AP fc:75:16:9c:91:a2 (try 1)
[  104.232002] wlan0: authenticated
[  104.232287] wlan0: associate with AP fc:75:16:9c:91:a2 (try 1)
[  104.234232] wlan0: RX AssocResp from fc:75:16:9c:91:a2 (capab=0x431 status=0 aid=1)
[  104.234241] wlan0: associated
[  104.235750] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  104.358912] padlock: VIA PadLock not detected.
[  114.532038] wlan0: no IPv6 routers present
[  329.000057] wlan0: deauthenticating from fc:75:16:9c:91:a2 by local choice (reason=3)
[  329.988974] wlan0: direct probe to AP fc:75:16:9c:91:a2 (try 1)
[  329.992876] wlan0: direct probe responded
[  329.992888] wlan0: authenticate with AP fc:75:16:9c:91:a2 (try 1)
[  329.996857] wlan0: authenticated
[  329.996911] wlan0: associate with AP fc:75:16:9c:91:a2 (try 1)
[  329.999099] wlan0: RX AssocResp from fc:75:16:9c:91:a2 (capab=0x431 status=0 aid=1)
[  329.999108] wlan0: associated
[  819.601059] wlan0: deauthenticating from fc:75:16:9c:91:a2 by local choice (reason=3)
[  820.686755] wlan0: direct probe to AP fc:75:16:9c:91:a2 (try 1)
[  820.692044] wlan0: direct probe responded
[  820.692057] wlan0: authenticate with AP fc:75:16:9c:91:a2 (try 1)
[  820.693457] wlan0: authenticated
[  820.693500] wlan0: associate with AP fc:75:16:9c:91:a2 (try 1)
[  820.695657] wlan0: RX AssocResp from fc:75:16:9c:91:a2 (capab=0x431 status=0 aid=1)
[  820.695665] wlan0: associated
[  829.725085] wlan0: deauthenticating from fc:75:16:9c:91:a2 by local choice (reason=3)
[  830.711885] wlan0: direct probe to AP fc:75:16:9c:91:a2 (try 1)
[  830.908041] wlan0: direct probe to AP fc:75:16:9c:91:a2 (try 2)
[  830.911435] wlan0: direct probe responded
[  830.911439] wlan0: authenticate with AP fc:75:16:9c:91:a2 (try 1)
[  830.913160] wlan0: authenticated
[  830.913196] wlan0: associate with AP fc:75:16:9c:91:a2 (try 1)
[  830.915421] wlan0: RX AssocResp from fc:75:16:9c:91:a2 (capab=0x431 status=0 aid=1)
[  830.915425] wlan0: associated

```

---

### Post by Rebelli0us on 2012-12-07
What computer are you using? Video?

If you have new hardware you'll need the latest kernel.

---

### Post by alexandari on 2012-12-07
My hardware is far from new,a Toshiba Satellite laptop A215 S4757

---

### Post by Rebelli0us on 2012-12-08
Does it hang in Windows too? If so it's probably a hardware problem, if not then it's a software problem. :popcorn:

Random freezes in my experience are usually video drivers.

---

### Post by Bashing-om on 2012-12-08
Looking over the provided logs;
1. --in >xsession-error file, lots of keyboard activity- stuck keys ? From dmesg it looks like A4tech is an external keyboard.
2. demesg is not happy with acpi. Try booting up with acpi_osi="linux" parameter.
3. dmesg says the driver for the external monitor "radeon" is failing.

What I suggest you do at this time is strip your system down to bare necessities, disconnect all external devices. Boot up with the above boot parameter and compare the logs then to what is shown now. If all looks good, then (re)connect one device at a time and look at the logs for errors. One at a time. 

Then we look again <== BDQ

---

### Post by alexandari on 2012-12-09
the keyboard activity is from a terminal emulator which I use,A4tech is an external mouse but that doesn't matter. dmesg has never been happy with acpi. radeon seems to be working fine when I'm logged into the system and run some graphic card checks. THANK YOU for the suggestion,I will try it and post the results :)

---

### Post by alexandari on 2012-12-21
here we go again

```
Xsession: X session started for alexandar at Fri Dec 21 19:51:52 EET 2012
startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/kde4/libkdeinit/libkdeinit4_klauncher.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/kde4/libkdeinit/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libkdeinit/libkdeinit4_kconf_update.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kded(2168)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_hal_power.so" does not offer a qt_plugin_instance function.
Invalid D-BUS member name 'idle-hint' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'is-local' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'remote-host-name' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'session-type' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'unix-user' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
QObject::connect: Cannot connect (null)::accessibilityChanged(bool, const QString) to DeviceAutomounter::deviceMountChanged(bool, const QString)
QObject::connect: Cannot connect (null)::accessibilityChanged(bool, const QString) to DeviceAutomounter::deviceMountChanged(bool, const QString)
kded(2168)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kdeinit4: preparing to launch /usr/lib/kde4/libkdeinit/libkdeinit4_kcminit_startup.so
kdeinit4: preparing to launch /usr/lib/kde4/libkdeinit/libkdeinit4_ksmserver.so
<unknown program name>(2165)/ KStartupInfo::createNewStartupId: creating:  "debian;1356112320;127657;2165_TIME0" : "unnamed app"
kephald starting up 
XRANDR error base:  162 
RRInput mask is set!! 
RandRScreen::loadSettings - adding mode:  68 1280 x 800 
RandRScreen::loadSettings - adding mode:  69 1280 x 720 
RandRScreen::loadSettings - adding mode:  70 1152 x 768 
RandRScreen::loadSettings - adding mode:  71 1024 x 768 
RandRScreen::loadSettings - adding mode:  72 800 x 600 
RandRScreen::loadSettings - adding mode:  73 848 x 480 
RandRScreen::loadSettings - adding mode:  74 720 x 480 
RandRScreen::loadSettings - adding mode:  75 640 x 480 
RandRScreen::loadSettings - adding crtc:  63 
RandRScreen::loadSettings - adding crtc:  64 
RandRScreen::loadSettings - adding output:  65 
Setting CRTC 0 on output "VGA-0" (previous 0 ) 
RandRScreen::loadSettings - adding output:  66 
Setting CRTC 63 on output "LVDS" (previous 0 ) 
CRTC outputs: (66) 
Output name: "LVDS" 
Output refresh rate: 60.0038 
Output rect: QRect(0,0 1280x800) 
Output rotation: 1 
RandRScreen::loadSettings - adding output:  67 
Setting CRTC 0 on output "S-video" (previous 0 ) 
XRandROutputs::init 
  added output  65 
  added output  66 
  added output  67 
output: "LVDS" QRect(0,0 1280x800) 0 false false 
output: "S-video" QRect(0,0 0x0) 0 false false 
output: "VGA-0" QRect(0,0 0x0) 0 false false 
load xml 
connected: 1 
looking for current "LVDS" 
known "*" has score: 0.25 
screen: 0 QRect(0,0 1280x800) 
looking for a matching configuration... 
connected: 1 
looking for current "LVDS" 
known "*" has score: 0.25 
found outputs, known: false 
connected: 1 
looking for current "LVDS" 
known "*" has score: 0.25 
activate external configuration!! 
registered the service: true 
screens registered on the bus: true 
outputs registered on the bus: true 
configurations registered on the bus: true 
kwin(2219): ""fsrestore1" - conversion of "0,0,0,0" to QRect failed" 
kwin(2219): ""restore2" - conversion of "0,0,0,0" to QRect failed" 
kwin(2219): ""fsrestore2" - conversion of "0,0,0,0" to QRect failed" 
kwin(2219): ""fsrestore3" - conversion of "0,0,0,0" to QRect failed" 
kwin(2219): ""restore4" - conversion of "0,0,0,0" to QRect failed" 
kwin(2219): ""fsrestore4" - conversion of "0,0,0,0" to QRect failed" 
kdeinit4: preparing to launch /usr/bin/kglobalaccel
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(2221) GlobalShortcutsRegistry::loadSettings: Loading group  "kmix"
kglobalaccel(2221) GlobalShortcutsRegistry::loadSettings: Loading group  "kwin"
kglobalaccel(2221) GlobalShortcutsRegistry::loadSettings: Loading group  "krunner"
kglobalaccel(2221) GlobalShortcutsRegistry::loadSettings: Loading group  "plasma-desktop"
kglobalaccel(2221) GlobalShortcutsRegistry::loadSettings: Loading group  "khotkeys"
kglobalaccel(2221) GlobalShortcutsRegistry::loadSettings: Loading group  "kded"
kglobalaccel(2221) GlobalShortcutsRegistry::loadSettings: Loading group  "yakuake"
kglobalaccel(2221) GlobalShortcutsRegistry::loadSettings: Loading group  "klipper"
kglobalaccel(2221) GlobalShortcutsRegistry::loadSettings: Loading group  "ktorrent"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Right" for "kwin" : "Switch Window Right"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Left" for "kwin" : "Switch Window Left"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kdeinit4: preparing to launch /usr/bin/knotify4
kdeinit4: preparing to launch /usr/bin/plasma-desktop
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.8'
knotify(2224) KNotify::event: 1  ref= 0
QDBusConnection: name 'org.kde.knotify' had owner '' but we thought it was ':1.10'
QDBusObjectPath: invalid path ""
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F1" for "plasma-desktop" : "activate widget 17"
QGraphicsLinearLayout::removeAt: invalid index 0
knotify(2224) KNotify::event: 2  ref= 0
plasma-desktop(2225)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "systemsettings" not found
plasma-desktop(2225)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/alexandar/.kde/share/apps/RecentDocuments/Downloads.desktop" not found
plasma-desktop(2225)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/alexandar/.kde/share/apps/RecentDocuments/alexandar.desktop" not found
plasma-desktop(2225)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/alexandar/.kde/share/apps/RecentDocuments/Source.zip.desktop" not found
plasma-desktop(2225)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/alexandar/.kde/share/apps/RecentDocuments/retard.php.desktop" not found
plasma-desktop(2225)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/alexandar/.kde/share/apps/RecentDocuments/index.php.desktop" not found
plasma-desktop(2225)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/alexandar/.kde/share/apps/RecentDocuments/xampp-linux-1.8.1.tar.gz.desktop" not found
plasma-desktop(2225)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "/home/alexandar/.kde/share/apps/RecentDocuments/virtual-tables.desktop" not found
plasma-desktop(2225)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_hal_power.so" does not offer a qt_plugin_instance function.
knotify(2224) NotifyByPopup::slotServiceOwnerChanged: "org.freedesktop.Notifications" "" ":1.12"
QGraphicsLinearLayout::removeAt: invalid index 0
Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
kcminit(2215)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_keyboard.so"
kdeinit4: preparing to launch /usr/bin/kaccess
<unknown program name>(2229)/ kdemain: Xlib XKB extension major= 1  minor= 0
kcminit(2215)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_hotkeys.so"
kcminit(2215)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_keys.so"
kaccess(2229) kdemain: X server XKB extension major= 1  minor= 0
kcminit(2215)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_kttsd.so"
kcminit(2215)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcminit_nsplugins.so"
kcminit(2215)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkcm_emoticons.so"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XMappingNotify event
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Right" for "kwin" : "Switch Window Right"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Meta+Alt+Left" for "kwin" : "Switch Window Left"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(2221) GlobalShortcutsRegistry::unregisterKey: Unregistering key "Alt+F1" for "plasma-desktop" : "activate widget 17"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
kdeinit4: preparing to launch /usr/bin/krunner
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Print" for "kwin" : "Desktop Screenshot to Clipboard"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Tab" for "kwin" : "Walk Through Windows"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F3" for "kwin" : "Window Operations Menu"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Print" for "kwin" : "Window Screenshot to Clipboard"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Right" for "kwin" : "Switch Window Right"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Alt+Left" for "kwin" : "Switch Window Left"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F12" for "kwin" : "Mouse Emulation"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F4" for "kwin" : "Window Close"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+F12" for "plasma-desktop" : "Show Dashboard"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F1" for "plasma-desktop" : "activate widget 17"
kdeinit4: preparing to launch /usr/bin/kmixctrl
kdeinit4: preparing to launch /usr/bin/nepomukserver
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+F2" for "krunner" : "Run Command"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Alt+Shift+F2" for "krunner" : "Run Command on clipboard contents"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Esc" for "krunner" : "Show System Activity"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Ins" for "krunner" : "Switch User"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+L" for "krunner" : "Lock Session"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Del" for "krunner" : "Log Out"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+Del" for "krunner" : "Log Out Without Confirmation"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgDown" for "krunner" : "Halt Without Confirmation"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Ctrl+Alt+Shift+PgUp" for "krunner" : "Reboot Without Confirmation"
"/usr/bin/krunner(2239)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/krunner(2239)" Soprano: "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/krunner(2239)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/krunner(2239)" Soprano: "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/krunner(2239)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/krunner(2239)" Soprano: "QLocalSocket::connectToServer: Connection refused"
krunner(2239)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/alexandar/.kde/share/apps/kabc" 
krunner(2239)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "" not found
kdeinit4: preparing to launch /usr/lib/kde4/libexec/polkit-kde-authentication-agent-1
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
kdeinit4: preparing to launch /usr/bin/kmix
New PolkitAgentListener  0x900e730 
Adding new listener  PolkitQt1::Agent::Listener(0x9046680) for  0x900e730 

(process:2243): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(process:2243): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
kdeinit4: preparing to launch /usr/bin/yakuake
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Volume Up" for "kmix" : "increase_volume"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Volume Down" for "kmix" : "decrease_volume"
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Volume Mute" for "kmix" : "mute"
kdeinit4: preparing to launch /usr/bin/skype
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "F12" for "yakuake" : "toggle-window-state"
yakuake(2249)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
yakuake(2249)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkonsolepart.so"
kmix(2247): _refcount already 0 
knotify(2224) NotifyBySound::notify:  going to play  "/usr/share/sounds/KDE-Sys-Special.ogg"
kdeinit4: preparing to launch /usr/bin/dolphin
kdeinit4: preparing to launch /usr/bin/yakuake
kdeinit4: preparing to launch 
Yakuake is already running, opening window....
Could not find 'start-pulseaudio-kde' executable.
kdeinit4: preparing to launch /usr/bin/disk-manager
yakuake(2249)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 
kdeinit4: preparing to launch /usr/lib/kde4/libexec/polkit-kde-authentication-agent-1
kdeinit4: preparing to launch /usr/bin/kerneloops-applet
PolicyKitKDE is already running!

kdeinit4: preparing to launch /usr/bin/kmix
kdeinit4: preparing to launch /usr/bin/knetworkmanager
kded(2168)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_networkmanager07.so" does not offer a qt_plugin_instance function.
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Display" for "kded" : "display"
kdeinit4: preparing to launch /usr/bin/google-chrome
kglobalaccel(2221) GlobalShortcutsRegistry::registerKey: Registering key "Print" for "khotkeys" : "{a79ef7d4-6556-4487-85eb-300839bd417e}"
kglobalaccel(2221) KdeDGlobalAccel::Component::cleanUp: 1
/usr/bin/skype: unrecognized option '-session'
QGraphicsLinearLayout::removeAt: invalid index 1
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
"/usr/bin/dolphin(2270)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2270)" Soprano: "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/dolphin(2270)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2270)" Soprano: "QLocalSocket::connectToServer: Connection refused"
"/usr/bin/dolphin(2270)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2270)" Soprano: "QLocalSocket::connectToServer: Connection refused"
knetworkmanager(2281)/kdeui (Wallet): The kwalletd service has been disabled 
knetworkmanager(2281)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_networkmanager07.so" does not offer a qt_plugin_instance function.

Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
"/usr/bin/dolphin(2270)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2270)" Soprano: "QLocalSocket::connectToServer: Connection refused"
plasma-desktop(2225): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2225): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 

params.c:OpenConfFile() - Unable to open configuration file "/home/alexandar/.smb/smb.conf":
        No such file or directory

params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
        No such file or directory


QLayout: Attempting to add QLayout "" to InterfaceConnectionItem "", which already has a layout
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
plasma-desktop(2225)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_thumbnail.so
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
Traceback (most recent call last):
  File "/usr/bin/disk-manager", line 111, in <module>
    main(args, opts)
  File "/usr/bin/disk-manager", line 47, in main
    if probe_new_device() :
  File "/usr/share/disk-manager/DiskManager/AddWizard.py", line 186, in probe_new_device
    fstab = FstabHandler(FSTAB)
  File "/usr/share/disk-manager/DiskManager/Fstab/FstabHandler.py", line 74, in __init__
    shutil.copy(filename, bckup)
  File "/usr/lib/python2.6/shutil.py", line 84, in copy
    copyfile(src, dst)
  File "/usr/lib/python2.6/shutil.py", line 51, in copyfile
    with open(dst, 'wb') as fdst:
IOError: [Errno 13] Permission denied: '/etc/fstab-disk-manager-save'
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Down" = "decrease_volume"
kmix(2247): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2225): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kmix(2247): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2225): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kmix(2247): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
plasma-desktop(2225): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kmix(2247): Failed to lock file "/var/tmp/kdecache-alexandar/kpc/plasma_theme_Silicon.lock" , last result = 1 
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "Volume Up" = "increase_volume"
Couldn't find node center. Skipping rendering.
[2286:2402:1221/195247:ERROR:backend_impl.cc(1168)] Critical error found -8
Couldn't find node center. Skipping rendering.
Object::disconnect: Unexpected null parameter
QGraphicsLinearLayout::removeAt: invalid index 1
plasma-desktop(2225)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Corrupt JPEG data: premature end of data segment
[2286:2397:1221/195345:ERROR:object_proxy.cc(495)] Failed to call method: org.kde.KWallet.isEnabled: object_path= /modules/kwalletd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.kde.kwalletd was not provided by any .service files
[2286:2397:1221/195345:ERROR:native_backend_kwallet_x.cc(175)] Error contacting kwalletd (isEnabled)
kdeinit4: preparing to launch /usr/bin/kwalletd
[2286:2397:1221/195345:ERROR:object_proxy.cc(495)] Failed to call method: org.kde.KWallet.isEnabled: object_path= /modules/kwalletd: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
[2286:2397:1221/195345:ERROR:native_backend_kwallet_x.cc(175)] Error contacting kwalletd (isEnabled)
kwalletd(2582): Communication problem with  "kwalletd" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.kwalletd was not provided by any .service files" " 

kglobalaccel(2221) KGlobalAccelImpl::x11Event: Got XKeyPress event
kglobalaccel(2221) GlobalShortcutsRegistry::keyPressed: "F12" = "toggle-window-state"
yakuake(2249)/kdeui (KWindowInfo) KWindowInfo::desktop: Pass NET::WMDesktop to KWindowInfo 

```

---

### Post by abrianb on 2012-12-28
Have you seen or signed on to this bug ?
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

---

