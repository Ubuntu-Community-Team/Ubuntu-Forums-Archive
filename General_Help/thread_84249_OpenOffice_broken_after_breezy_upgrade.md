---
title: "OpenOffice broken after breezy upgrade"
date: 2005-10-30
forum: General Help
---

### Post by *nix_noob on 2005-10-30
After upgrading to breezy I tried to start OpenOffice programs and I got: 

"Failed to execute child process "/usr/bin/(filename)" (No such file or directory)"

But synaptic says its intalled...

Any ideas?

---

### Post by NewbieNik on 2005-10-30
[QUOTE=*nix_noob]After upgrading to breezy I tried to start OpenOffice programs and I got: 

"Failed to execute child process "/usr/bin/(filename)" (No such file or directory)"

But synaptic says its intalled...

Any ideas?[/QUOTE]

DId you have Hoary and change repos to upgrade or have you installed from scratch? I would try running "sudo apt-get -f install" to chaeck for fixes or remove OpenOffice and re-install.

---

### Post by funkydan2 on 2005-10-30
Or try install the ubuntu-desktop metapackage, to ensure that openoffice.org2 is installed.

---

### Post by *nix_noob on 2005-10-30
fixed it sudo apt-get install openoffice.org2

it removes old open office and installs 2.0

---

