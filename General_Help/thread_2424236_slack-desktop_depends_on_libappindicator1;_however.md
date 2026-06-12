---
title: "slack-desktop depends on libappindicator1; however:   Package libappindicator1 is not"
date: 2019-08-05
forum: General Help
---

### Post by jiapei100 on 2019-08-05
I wonder if there is an **AUTOMATIC** way to try the **INSTALLED** new package **RATHER THAN** searching for a **REQUIRED** old version of the same package?

Be more specific:

[LIST=1]
[*] **slack-desktop-4.0.1-amd64.deb** requires **libappindicator1**
```

&#10140;  tools sudo dpkg -i slack-desktop-4.0.1-amd64.deb
(Reading database ... 507021 files and directories currently installed.)
Preparing to unpack slack-desktop-4.0.1-amd64.deb ...
Unpacking slack-desktop (4.0.1) over (4.0.1) ...
dpkg: dependency problems prevent configuration of slack-desktop:
 slack-desktop depends on libappindicator1; however:
  Package libappindicator1 is not installed.

dpkg: error processing package slack-desktop (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-4ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Errors were encountered while processing:
 slack-desktop

```

[*] I've **ALREADY** installed **libappindicator3-1**
```

&#10140;  tools apt show libappindicator3-1
Package: libappindicator3-1
Version: 12.10.1+18.04.20180322.1-0ubuntu2
Status: install ok installed
Priority: optional
Section: libs
Source: libappindicator
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Installed-Size: 95.2 kB
Pre-Depends: multiarch-support
Depends: libc6 (>= 2.4), libdbusmenu-glib4 (>= 0.4.2), libdbusmenu-gtk3-4 (>= 0.4.2), libglib2.0-0 (>= 2.37.3), libgtk-3-0 (>= 3.0.0)
Suggests: indicator-application (>= 0.2.93)
Homepage: https://launchpad.net/libappindicator
Download-Size: unknown
APT-Manual-Installed: no
APT-Sources: /var/lib/dpkg/status
Description: Application Indicators
 A library and indicator to take menus from applications and place them in
 the panel.
 .
 This package contains shared libraries to be used by applications.

```

[*] What's more, I couldn't find a suitable **libappindicator1** for my Ubuntu 19.04.
[/LIST]


I just wonder if there is a way to overlook the **OLD libappindicator1**, but try the **INSTALLED libappindicator3-1** ?


Thank you very much.
Pei

---

