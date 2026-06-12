---
title: "Software &amp; Updates and Update Manager Crash on open"
date: 2016-09-07
forum: General Help
---

### Post by jesusguevarautomotriz on 2016-09-07
Hi,

On my Lubuntu 14.04.5 LTS, "Software and Updates" and "Software Updater" apps is broken since some time.

I try open "Software and Updates": Brings dialog box, Sorry, Ubuntu 14.04 has experienced an internal error.
I try open "Software Updater": Brings dialog box, Crash Report, The application Software Updater has closed unexpectedly.

I Always  have to use the terminal for install, uninstall and updates.
I tried unninstall and reinstall both but not luck. How could I fix this?

Output from starting the applications via the terminal:
```

$ software-properties-gtk
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 37, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 46, in <module>
    from .DialogCacheOutdated import DialogCacheOutdated
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/DialogCacheOutdated.py", line 28, in <module>
    from aptdaemon.gtk3widgets import AptErrorDialog, AptProgressDialog
  File "/usr/lib/python3/dist-packages/aptdaemon/gtk3widgets.py", line 42, in <module>
    gi.require_version("Vte", "2.91")
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 83, in require_version
    (namespace, version))
ValueError: Namespace Vte not available for version 2.91

```

```

$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 115, in <module>
    app.start_update()
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 214, in start_update
    update_backend = get_backend(self, InstallBackend.ACTION_UPDATE)
  File "/usr/lib/python3/dist-packages/UpdateManager/backend/__init__.py", line 92, in get_backend
    from .InstallBackendAptdaemon import InstallBackendAptdaemon
  File "/usr/lib/python3/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py", line 12, in <module>
    from aptdaemon.gtk3widgets import (AptCancelButton,
  File "/usr/lib/python3/dist-packages/aptdaemon/gtk3widgets.py", line 42, in <module>
    gi.require_version("Vte", "2.91")
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 83, in require_version
    (namespace, version))
ValueError: Namespace Vte not available for version 2.91

```

Thanks.

---

### Post by howefield on 2016-09-07
You have posted the same output twice, was one of them meant to be for the update-manager ?

What's the output of..

```
apt-cache show gir1.2-vte-2.90
```
```
apt-cache show gir1.2-vte-2.91
```

---

### Post by jesusguevarautomotriz on 2016-09-07
Thanks for yout answers,

I edited first message and updated $ update-manager output.

Other outputs:
```

Package: gir1.2-vte-2.90
Priority: optional
Section: libs
Installed-Size: 436
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: vte3
Version: 1:0.34.9-1ubuntu2
Depends: gir1.2-gtk-3.0, gir1.2-pango-1.0, libvte-2.90-9 (>= 1:0.34.2)
Filename: pool/main/v/vte3/gir1.2-vte-2.90_0.34.9-1ubuntu2_amd64.deb
Size: 6554
MD5sum: 3513a214577554d5718c3317b1211639
SHA1: dca812430d9bc017ec37d8e4d37382ff43e6e8ff
SHA256: c8ba4d29d208c13db3b67aed4a12336d402d5cbb698e7f6e9c7fecc773a6d8a2
Description-en: GObject introspection data for the VTE library
 This package contains introspection data for VTE, a terminal emulator
 widget for GTK+.
 .
 It can be used by interpreters understanding the GIRepository format to
 write programs using the VTE widget for GTK+ 3.0.
Description-md5: 41cb5d8a8e27456cf39b3e3fdc888730
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master, lubuntu-desktop, ubuntustudio-desktop, ubuntu-gnome-desktop

Package: gir1.2-vte-2.90
Priority: optional
Section: libs
Installed-Size: 436
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: vte3
Version: 1:0.34.9-1ubuntu1
Depends: gir1.2-gtk-3.0, gir1.2-pango-1.0, libvte-2.90-9 (>= 1:0.34.2)
Filename: pool/main/v/vte3/gir1.2-vte-2.90_0.34.9-1ubuntu1_amd64.deb
Size: 6558
MD5sum: 3da4520d1fd74c2c39d1de42cbeee13f
SHA1: 5b70564ac8ea979717cdb20191dffbe3c4b2ec4f
SHA256: 7a863e0e33f59b53d256c66e700bd677a421171d81e8fea0cda08d9f674b0f5c
Description-en: GObject introspection data for the VTE library
 This package contains introspection data for VTE, a terminal emulator
 widget for GTK+.
 .
 It can be used by interpreters understanding the GIRepository format to
 write programs using the VTE widget for GTK+ 3.0.
Description-md5: 41cb5d8a8e27456cf39b3e3fdc888730
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master, lubuntu-desktop, ubuntustudio-desktop, ubuntu-gnome-desktop

```

```

$ apt-cache show gir1.2-vte-2.91
N: Unable to locate package gir1.2-vte-2.91
N: Couldn't find any package by regex 'gir1.2-vte-2.91'
E: No packages found

```

---

