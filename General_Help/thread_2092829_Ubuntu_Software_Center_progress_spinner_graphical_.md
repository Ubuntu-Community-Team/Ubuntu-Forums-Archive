---
title: "Ubuntu Software Center progress spinner graphical glitch"
date: 2012-12-08
forum: General Help
---

### Post by dmaxel on 2012-12-08
Hey everyone,

I'm not sure if this has been seen before, but the progress spinner is glitching out on my system, as shown in the screenshot. Doesn't seem to appear on other computers running updated versions of Ubuntu 12.10.

I tried reinstalling the software-center package, but that didn't help. Don't want to try removing the package first, because it wants to remove ubuntu-desktop as well.

Can anyone help with this? I know it's a very minor gripe, but it's still annoying.

---

### Post by Kirk Schnable on 2012-12-09
It would be worthwhile to know exactly which Ubuntu version and Software Center version you have. 

Please post the output of:
```
lsb_release -a
```

```
uname -r
```

```
dpkg -p software-center
```

---

### Post by dmaxel on 2012-12-09
> **Kirk Schnable said:**
> It would be worthwhile to know exactly which Ubuntu version and Software Center version you have. 

Please post the output of:
```
lsb_release -a
```

```
uname -r
```

```
dpkg -p software-center
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal





3.5.0-19-generic






Package: software-center
Priority: optional
Section: gnome
Installed-Size: 4380
Maintainer: Michael Vogt <mvo@ubuntu.com>
Architecture: all
Version: 5.4.1.2
Replaces: gnome-app-install
Provides: gnome-app-install
Depends: python (>= 2.7.1-0ubuntu2), iso-codes, app-install-data (>= 0.4.0), aptdaemon (>= 0.40), software-center-aptdaemon-plugins, humanity-icon-theme, gir1.2-glib-2.0 (>= 1.31), gir1.2-gtk-3.0, gir1.2-gmenu-3.0 (>= 3.1.5), gir1.2-webkit-3.0, python-gi, python-gi-cairo, python-xapian, python-apt (>= 0.8.3ubuntu4), python-aptdaemon (>= 0.40), python-aptdaemon.gtk3widgets, python-dbus, python-defer, python-lxml, policykit-1, policykit-1-gnome | policykit-1-kde, python-xdg, ubuntu-sso-client, python-piston-mini-client (>= 0.1+bzr29), oneconf (>= 0.2.6), python-debtagshw, ubuntu-extras-keyring
Recommends: lsb-release, apt-xapian-index (>= 0.38ubuntu1), update-notifier, software-properties-gtk, sessioninstaller, xz-utils (>= 5.1.1alpha+20120614-1)
Conflicts: gnome-app-install (<< 1), oneconf (<< 0.2.6.1)
Size: 626600
Description: Utility for browsing, installing, and removing software
 Ubuntu Software Center lets you browse and install thousands of
 free and paid applications available for Ubuntu. You can view available
 software by category, or search quickly by name or description.
 You can also examine the software already installed, and remove items
 you no longer need.
 .
 To install or remove software using USC, you need administrator access
 on the computer.
Homepage: [https://launchpad.net/software-center](https://launchpad.net/software-center)

---

### Post by Kirk Schnable on 2012-12-09
Now that we know what versions you're running, I'd be curious to hear from other forum members running Ubuntu 12.10 and Software Center 5.4.1.2 to find out if they are experiencing this issue.

---

### Post by Dabo Ross on 2013-01-08
I am having the same glitch. It isn't affecting anything, it just seems like it shouldn't look like that.
this is the output I get from those:
```
daboross@DaboUbuntu:~$ lsb_release -a && uname -r && dpkg -p software-center
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
3.5.0-21-generic
Package: software-center
Priority: optional
Section: gnome
Installed-Size: 4416
Maintainer: Michael Vogt <mvo@ubuntu.com>
Architecture: all
Version: 5.4.1.3
Replaces: gnome-app-install
Provides: gnome-app-install
Depends: python (>= 2.7.1-0ubuntu2), iso-codes, app-install-data (>= 0.4.0), aptdaemon (>= 0.40), software-center-aptdaemon-plugins, humanity-icon-theme, gir1.2-glib-2.0 (>= 1.31), gir1.2-gtk-3.0, gir1.2-gmenu-3.0 (>= 3.1.5), gir1.2-webkit-3.0, python-gi (>= 3.4.0-1ubuntu0.1), python-gi-cairo, python-xapian, python-apt (>= 0.8.3ubuntu4), python-aptdaemon (>= 0.40), python-aptdaemon.gtk3widgets, python-dbus, python-defer, python-lxml, policykit-1, policykit-1-gnome | policykit-1-kde, python-xdg, ubuntu-sso-client, python-piston-mini-client (>= 0.1+bzr29), oneconf (>= 0.2.6), python-debtagshw, ubuntu-extras-keyring
Recommends: lsb-release, apt-xapian-index (>= 0.38ubuntu1), update-notifier, software-properties-gtk, sessioninstaller, xz-utils (>= 5.1.1alpha+20120614-1)
Conflicts: gnome-app-install (<< 1), oneconf (<< 0.2.6.1)
Size: 628054
Description: Utility for browsing, installing, and removing software
 Ubuntu Software Center lets you browse and install thousands of
 free and paid applications available for Ubuntu. You can view available
 software by category, or search quickly by name or description.
 You can also examine the software already installed, and remove items
 you no longer need.
 .
 To install or remove software using USC, you need administrator access
 on the computer.
Homepage: https://launchpad.net/software-center

```

I am just posting this here to confirm that it isn't just you who is having that glitch.

---

### Post by adblair on 2013-02-23
I sometimes see exactly the same problem with Software Centre 5.4.1.4.  Is there an existing bug report for this or should I create a new one?

---

### Post by Dabo Ross on 2013-02-23
I am no longer having this bug, but I think this is where you would post if you are.

---

