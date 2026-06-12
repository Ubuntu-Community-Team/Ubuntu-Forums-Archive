---
title: "Removing Required Packages (solved)"
date: 2006-10-11
forum: General Help
---

### Post by Apple 101 on 2006-10-11
Hi everyone,

Ubuntu currently installs the libportaudio package which I do not want, as it is too old.  I would like to upgrade to the latest version by compiling from sources.  Anyway, I cannot uninstall this package without removing OpenOffice and Ubuntu-Desktop as well.  Is there any way to do this, and keep the other packages?

Thankyou for your help.

---

### Post by nikhilk on 2006-10-11
I assume you know what you want to do! This can be dangerous.
You can remove a package without removing it's dependencies by "dpkg -r --ignore-depends <package>"

---

### Post by Apple 101 on 2006-10-12
Fantastic.  That solution worked perfectly.  Thankyou for your help.

---

### Post by PriceChild on 2006-10-12
I would suggest compiling your package then replacing the old one with it.

You can created debs using "checkinstall" rather than "make install"

Although you may like to keep openoffice, ubuntu-desktop is a meta-package, it only depends on other packages and is therfore safe to remove.

---

