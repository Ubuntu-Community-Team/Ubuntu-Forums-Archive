---
title: "[SOLVED] dpkg data files : where are them?"
date: 2013-11-26
forum: General Help
---

### Post by landeel on 2013-11-26
As the title says, I want to know where dpkg stores information about which packages are installed.

---

### Post by deadflowr on 2013-11-26
/var/lib/dpkg/info

---

### Post by TQLeaman on 2013-11-26
Hi,

Normally the raw .deb packages are stored in /var/cache/apt/archives.

If you are looking for a list of installed packages then you can run the following command in a terminal:
[INDENT]dpkg --get-selections[/INDENT]

You can use that command as the basis for creating a standard package set for installing on multiple devices, [this link]("https://kura.io/2010/07/02/using-dpkg-selections-to-backup-and-install-packages/") has a good description.

Hope that helps,

TQ

---

### Post by Bashing-om on 2013-11-26
landeel; Hi !

The package management system can be a complex issue. Here is a fairly complete list of the control and index files:

Files for the package management system:
/etc/apt/sources.list: Locations to fetch packages from.
/etc/apt/sources.list.d/: Additional source list fragments.
/etc/apt/apt.conf: APT configuration file.
/etc/apt/apt.conf.d/: APT configuration file fragments.
/etc/apt/preferences: version preferences file. This is where you would specify "pinning", i.e. a preference to get certain packages from a separate source or from a different version of a distribution.
/var/cache/apt/archives/: storage area for retrieved package files.
/var/cache/apt/archives/partial/: storage area for package files in transit.
/var/lib/apt/extended_states :stores its locally generated installation state information 
/var/lib/apt/lists/: storage area for state information for each package resource specified in sources.list
/var/lib/apt/lists/partial/: storage area for state information in transit.
/var/lib/dpkg/available :dpkg keeps its record of available packages
/var/lib/dpkg/info/ ->>>
/var/lib/dpkg/info/<package_name>.conffiles :list of configuration files. (user modifiable)
/var/lib/dpkg/info/<package_name>.list :list of files and directories installed by the package
/var/lib/dpkg/info/<package_name>.md5sums : list of MD5 hash values for files installed by the package. The installation of debsums enables verification of installed package files against MD5sum values in the this file.
/var/lib/dpkg/info/<package_name>.preinst : package script to be run before the package installation
/var/lib/dpkg/info/<package_name>.postinst : package script to be run after the package installation
/var/lib/dpkg/info/<package_name>.prerm : package script to be run before the package removal
/var/lib/dpkg/info/<package_name>.postrm : package script to be run after the package removal
/var/lib/dpkg/info/<package_name>.config : package script for debconf system
/var/lib/dpkg/alternatives/<package_name> : the alternative information used by the update-alternatives command, The Debian alternatives system keeps its selection as symlinks in "/etc/alternatives/". The selection process uses corresponding file in this file.
/var/lib/dpkg/available : the availability information for all the package
/var/lib/dpkg/diversions : the diversions information used by dpkg(1) and set by dpkg-divert(8)
/var/lib/dpkg/statoverride : the stat override information used by dpkg(1) and set by dpkg-statoverride(8)
/var/lib/dpkg/status : the status information for all the packages
/var/lib/dpkg/status-old : the first-generation backup of the "var/lib/dpkg/status" file
/var/backups/dpkg.status* : the second-generation backup and older ones of the "var/lib/dpkg/status" file

/var/lib/apt/extended_states :locally generated installation state information for only aptitude uses it.


Maybe more than you wanted to know, But you did ask !

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by landeel on 2013-11-26
Exactly what I needed. Thank you!!! :D

---

