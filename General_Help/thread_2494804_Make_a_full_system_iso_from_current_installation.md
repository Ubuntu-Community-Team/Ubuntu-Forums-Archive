---
title: "Make a full system iso from current installation"
date: 2024-01-27
forum: General Help
---

### Post by Gordonbp531 on 2024-01-27
Is it possible, to create an iso from a currently installed system that contains all the installed apps and all the User accounts plus data?
MXLinux has such a function and it makes re-installing a system much much easier.
It's akin to the Windows System Image function if that helps....
Apps like Clonezilla are OK but they take a very long time to a) save a disk image and b) to reinstall that image.

---

### Post by TheFu on 2024-01-27
Not using any Ubuntu built-in tools.  There are ways, but they have issues.  Ubuntu used to have this feature before they started supporting all sorts of other file systems, encryption, EUFI, systemd, and a bunch of other "improvements."

For most Debian-based systems, the best solution is to backup your data and settings (both user and system), include a list of manually installed packages and any manually installed non-package manager items, then start your restore using a fresh install from a normal distribution ISO.  Bring back all the data, then selectively bring back system settings (blindly copying them all will turn out badly), then finally, shoveling the list of manually installed packages into the package manager for installation.  When the packages are installing, they will see the old data and old settings and use those. It is sorta slick, plus it is fast. Less than 30 minutes, unless you have a bunch of data.

The method I describe is what I've been doing for desktops and servers for about 15 yrs.  It works and allows automatic, daily, versioned, backups of the stuff I backup, without wasting space on dumb things like binary packages.  For one of my gateway systems, a years worth of daily backups fits into less than 100MB.  That system is all about processing and protection. It doesn't have any data, just a bunch of anti-spam rules and firewall rules.

Perhaps that is something you can consider.  Also, it works across all distros, provided you can get a list of packages manually installed by the package manager.  It isn't the end of the world if you get the huge list of all packages installed, but the more there are, the more likely conflicts will happen.

---

