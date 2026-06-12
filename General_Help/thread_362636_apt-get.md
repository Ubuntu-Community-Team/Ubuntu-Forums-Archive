---
title: "apt-get"
date: 2007-02-15
forum: General Help
---

### Post by glennzo on 2007-02-15
Using Fedora, to find out if a package is installed I would type at the command line 'rpm -q packagename', and rpm returns the name and version of the installed package or it says 'package xyz.123 is not installed. How does one do the same in Ubuntu?

---

### Post by Maestro23 on 2007-02-15
One way:

apt-cache showpkg "name of package"

---

### Post by dcstar on 2007-02-15
> **glennzo said:**
> Using Fedora, to find out if a package is installed I would type at the command line 'rpm -q packagename', and rpm returns the name and version of the installed package or it says 'package xyz.123 is not installed. How does one do the same in Ubuntu?

Start up Synaptic, do a search for the package name.

---

### Post by glennzo on 2007-02-15
Thank you both. I'll try apt-cache showpkg "name of package". I'll look at Synaptic too. Never thought of that. Thanks again.

---

