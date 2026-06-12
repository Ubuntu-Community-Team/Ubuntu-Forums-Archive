---
title: "[SOLVED] Downloading sources for every installed Package"
date: 2007-10-19
forum: General Help
---

### Post by tcort on 2007-10-19
**Background**
I'm building a virtual machine inside [qemu]("http://fabrice.bellard.free.fr/qemu/") for a demo of a software project I'm working on, and I eventually want to distribute it. I've read the [License Information for CD vendors]("http://www.debian.org/CD/vendors/legal") page on [debian.org]("http://debian.org") and it looks like I have to provide the source code for many of the packages. The virtual machine won't include every package that exists (just the base install and a few additional packages), so I don't want/need to do a full mirror. I just want the source code to the installed packages.

**Question**
How can I fetch the source code for every package that is installed?

---

### Post by tcort on 2007-10-19
I figured it out...

```

for pkg in $(dpkg --get-selections | cut -f 1)
do
  apt-get --download-only source ${pkg}
done

```

---

