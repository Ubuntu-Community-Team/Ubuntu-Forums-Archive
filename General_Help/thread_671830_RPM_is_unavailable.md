---
title: "RPM is unavailable"
date: 2008-01-18
forum: General Help
---

### Post by Will Pittenger on 2008-01-18
In order to install Java, I appear to need to deal with a RPM file.  However, my system can't find the program "rpm" and the Archive Manager can't deal with the file.  What do I do?

---

### Post by gaylapdancer on 2008-01-19
A RPM file is a Red Hat Package Manager file. RPM Distro's like SuSE and Fedora install packages with these, but Ubuntu is a Debian based distro, so uses deb files for installation, I don't think it is possible to install RPMs on any debian distro. If you want Java, it is in the repos. Open Synaptic and search for Java.

---

### Post by LaRoza on 2008-01-19
> **gaylapdancer said:**
> , I don't think it is possible to install RPMs on any debian distro. If you want Java, it is in the repos. Open Synaptic and search for Java.

It is possible, using Alien.

I also recommend the repos version.

---

### Post by gaylapdancer on 2008-01-19
> **LaRoza said:**
> It is possible, using Alien.

The more you know I guess :) I'll remember that thanks LaRoza

---

### Post by zvacet on 2008-01-19
```
sudo apt-get install ubuntu-restricted-extras
```

That will install Java,Flash,plugins....

---

