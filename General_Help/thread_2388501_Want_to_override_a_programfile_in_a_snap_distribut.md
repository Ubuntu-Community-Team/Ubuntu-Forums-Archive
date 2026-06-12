---
title: "Want to override a program/file in a snap distribution ?"
date: 2018-04-03
forum: General Help
---

### Post by ptro on 2018-04-03
Can I or how to override (program) files in a (confined) snap ?


Busy using snap (containers) on Ubuntu 16.04, great way to distribute/get packages but it limits me from tweaks by changing/overriding the code.

I want to override one of the files/programs with my own version of the (python ) program because the original crashes.
The repo where I got the snap is unwilling, has no time or has not yet removed the bug.
I simply need to remove some code in a python source.
FYI: In this particular case I&#7743; talking about homeassitant@ubuntu  whoch has a bug in the FritzRouter device and openHAB@Ubuntu which seem to refuse to accept added modules in the addons directory.

Note: By design, /snap filespace where the package is installed via "snap install"  is read-only/confined mounted.

Please let me know where to go, if and how I can override program by my user version as one could do with regular debian packages by inserted the (called) program in a user-path

Note: I'm aware of the purpose of snaps which gives the developer the consistency distribution control on the end-users package version.
One can hate or love that as a feature. I'm aware that one can could/make own snaps via "snapcraft" which in turn require publishing etc.etc. which imho is a bit overdone for simple tweaks.

TIA, Peter

---

### Post by dino99 on 2018-04-04
using snap is hasardous, as it has many issues known, not mature nor stable.

---

### Post by monkeybrain20122 on 2018-04-04
> **dino99 said:**
> using snap is hasardous, as it has many issues known, not mature nor stable.

+1. Just uninstall the snap version and install the .deb version with apt or use synaptic, the software centre is pushing snap so it will offer a snap version if available. Get synaptic.

---

### Post by mc4man on 2018-04-04
If you want to change a snap (not user configuration options) then your only option is to build that snap yourself locally & install locally
(you don't need to publish a snap to install it, you may need to use the --dangerous snap install option..

---

