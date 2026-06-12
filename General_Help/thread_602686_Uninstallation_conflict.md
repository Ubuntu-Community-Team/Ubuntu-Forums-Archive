---
title: "Uninstallation conflict"
date: 2007-11-04
forum: General Help
---

### Post by desklamp on 2007-11-04
I want to uninstall ntpdate.  But the uninstallation is bundled with ubuntu-minimal.

> This package depends on all of the packages in the Ubuntu minimal system, that is a functional command-line system with the following capabilities: 

 - Boot
 - Detect hardware
 - Connect to a network
 - Install packages
 - Perform basic diagnostics

It is also used to help ensure proper upgrades, so it is recommended that it not be removed.
[http://packages.ubuntu.com/gutsy/metapackages/ubuntu-minimal](http://packages.ubuntu.com/gutsy/metapackages/ubuntu-minimal)

I do not need the ntpdate.  How do I uninstall it without uninstalling the ubuntu-minimal too?  I find the ntpdate a rather nuisanse.

---

### Post by MrFSL on 2007-11-04
Dependency management is extremely important when dealing with stable operating systems. There are ways to break dependencies, disable ntp, and fool the package manager but the result is a less-stable O/S.

My suggestion... live with it. It's a dependency.

If you really don't want to live with it (and I DO NOT suggest this) but you can download the deb file from packages.ubuntu.com - extract it - find the files that it installs and remove them manually.

This will break your system.

---

