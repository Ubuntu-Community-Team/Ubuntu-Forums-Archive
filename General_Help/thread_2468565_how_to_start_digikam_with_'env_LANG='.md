---
title: "how to start digikam with 'env LANG='"
date: 2021-11-03
forum: General Help
---

### Post by jojo552 on 2021-11-03
Hi
I moved from Fedora Mate to Ubuntu 20.04 recently. My default language in this installation is english, but for certain reasons I would like to start different application like digikam with a german user interface. I was used to achieve that by modifying the start of the application, e.g. to change the start properties of digikam from
```
[COLOR=#00000A]digikam -qwindowtitle %c[/COLOR]
```
into
```
**env LANG=de_DE.utf8**[COLOR=#00000A] digikam -qwindowtitle %c[/COLOR]
```

Unfortunately I do not know where and how to modify the start icon of the application to use the modified command with locale.

Thank you in advance.
[COLOR=#00000A]
[/COLOR]

---

### Post by jojo552 on 2021-11-05
meanwhile I see that /snap/digikam/48/usr/share/applications/org.kde.digikam.desktop might be are place where to change the code as described above. But /snap and/or the file is read-only, I get message: [ File 'org.kde.digikam.desktop' is unwritable ]

---

### Post by ajgreeny on 2021-11-05
I presume from what you say that you are using digikam as a snap.

Have you considered installing the version from the repos .deb package, version 4.6.4.0.
I have no idea what version the snap is as I have removed all snap infrastructure from my computers but the 4.6.4.0 version works very well, even on my Xubuntu 20.04, though it had to bring in a lot of KDE and QT libraries to install it.

I suspect if using a snap version that you will not be able to make changes to the desktop file that will actually work as so may limitations are placed on snap packages that such things may be impossible even if you made that desktop file writeable, though not having any snaps, I have no way to check any of that.

---

### Post by deadflowr on 2021-11-05
I think this might point you into the right direction in terms of how the desktop files go:
[https://forum.snapcraft.io/t/overriding-desktop-files-on-ubuntu-snaps/6599]("https://forum.snapcraft.io/t/overriding-desktop-files-on-ubuntu-snaps/6599")

---

### Post by jojo552 on 2021-11-12
Thank you for your hints.
Meanwhile I detected that digikam.desktop resides in /snap/digikam/48/meta/gui . This file is not changeable, I assume because it resides in a snap.
When I installed digikam using Budgie's 'Software' app I did not choose or decide to install from snap. I even did not know anything snap architecture in Ubuntu (I migrated from Fedora ;-) ). Obviously I need to check how to install digikam from the repos.

---

