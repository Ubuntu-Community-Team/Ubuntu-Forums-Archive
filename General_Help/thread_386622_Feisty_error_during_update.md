---
title: "Feisty error during update"
date: 2007-03-17
forum: General Help
---

### Post by jej2003 on 2007-03-17
I have been running feisty for a while now but lately when I go to perform updates using Update Manager I have been getting errors like the one below 

```
E: linux-image-2.6.20-11-generic: subprocess post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.20-11-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured


```

Is there a way to fix this?  I have considered reinstalling the OS and installing herd 5 to get away from this, but will take other options if available.

---

### Post by Arby on 2007-03-18
try running ```
sudo apt-get dist-upgrade
``` instead of just a regular upgrade. From the apt-get man pages ```
upgrade
          upgrade is used to install the newest versions of all packages currently installed on the
          system from the sources enumerated in /etc/apt/sources.list. Packages currently installed
          with new versions available are retrieved and upgraded; under no circumstances are currently
          installed packages removed, or packages not already installed retrieved and installed. New
          versions of currently installed packages that cannot be upgraded without changing the install
          status of another package will be left at their current version.

 dist-upgrade
          dist-upgrade in addition to performing the function of upgrade, also intelligently handles
          changing dependencies with new versions of packages;

```

The packages you are trying to upgrade are a new kernel and associated files. It is likely that this requires either the removal of some old packages or the installation of new stuff to satisfy the dependencies of the new kernel. As the manual says, upgrade doesn't attempt to resolve this but dist-upgrade should.

Hope that helps

Arby

---

### Post by CSandman on 2007-03-19
Wow thats Great.  I'm pretty sure that was part of my problem too!

---

### Post by DougieFresh4U on 2007-03-19
I always do updates via terminal. When updates are finished I run **sudo apt-get -f install** and then **sudo dpkg --configure -a**  Just my two cents worth

---

