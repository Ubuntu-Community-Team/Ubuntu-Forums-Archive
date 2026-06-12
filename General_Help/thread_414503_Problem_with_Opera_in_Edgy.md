---
title: "Problem with Opera in Edgy"
date: 2007-04-19
forum: General Help
---

### Post by loyal one on 2007-04-19
In Synaptic:

The following packages have unresolvable dependencies:

opera:
  Depends: libc6 (>=2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
  Depends: libgcc1 (>=1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
  Depends: libqt3-mt (>=3:3.3.8really3.3.7) but 3:3.3.6-3ubuntu3.1 is to be installed
  Depends: libstdc++6 (>=4.1.2) but 4.1.1-13ubuntu5 is to be installed

Using Ubuntu 6.10 Edgy EFT.

All repository sources have been added using Synaptic.

Opera was installed but crashed when opened, so I removed it using add-remove applications, then tried to reinstall.

Opera was originally installed using Automatix, and I uninstalled it in Automatix as well.

What is the meaning of the dependencies comments, and what to do about them ? I will be very grateful for any help with this matter. Thanks !

---

### Post by sudo_nym on 2007-04-20
> **loyal one said:**
> In Synaptic:

The following packages have unresolvable dependencies:

opera:
  Depends: libc6 (>=2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
  Depends: libgcc1 (>=1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
  Depends: libqt3-mt (>=3:3.3.8really3.3.7) but 3:3.3.6-3ubuntu3.1 is to be installed
  Depends: libstdc++6 (>=4.1.2) but 4.1.1-13ubuntu5 is to be installed

Using Ubuntu 6.10 Edgy EFT.

All repository sources have been added using Synaptic.

Opera was installed but crashed when opened, so I removed it using add-remove applications, then tried to reinstall.

Opera was originally installed using Automatix, and I uninstalled it in Automatix as well.

What is the meaning of the dependencies comments, and what to do about them ? I will be very grateful for any help with this matter. Thanks !

Strange.  I'm using Opera right now...

Dependancies are other software, usually libraries, that a program needs in order to run.  Basically they extend the system's capabilities in some way, to better suit the program's needs.

Have you had a look in Synaptic Package Manager, to see if these libs are due for an upgrade?  They would show up with a green status icon [meaning already installed] and a gold star added [meaning upgradable].  Looks like Opera needs higher versions than you've got right now.

Sorry, I don't know anything about Automatix.  Have you tried GDebi, for packages downloaded off the web, or anywhere else besides the regular software channells?  It probably came with your system.

GDebi's good for installing a single package, and can even download and install its dependancies for you, but might refuse to perform upgrades, or replace anything that's already installed.  I think it did download libqt3-mt for me though, which was not installed at the time.


Hope it helps,

Patrick.

---

