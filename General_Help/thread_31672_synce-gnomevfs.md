---
title: "synce-gnomevfs"
date: 2005-05-04
forum: General Help
---

### Post by veskonedev on 2005-05-04
That is the package i miss, since i moved from fedora to ubuntu. I cannot brouse my ipaq file system within gnome like i used to. I did not find that package for debian, but it is there for fedora at sourceforge.net. Any sugestions on how to invlude that package in ubuntu, as i think i have to make the .deb by mysef :-/
at sourceforge i see:
synce-gnomevfs-0.9.0.tar.gz, synce-gnomevfs-0.9.0-1.src.rpm, synce-gnomevfs-0.9.0-1.i386.rpm but no deb packages there

---

### Post by kmyram on 2005-05-04
download synce-gnomevfs-0.9.0-1.i386.rpm and create/install a .deb-package with

$ sudo alien -i synce-gnomevfs-0.9.0-1.i386.rpm

Should do it.

---

### Post by veskonedev on 2005-05-04
thank you. that did work as expected.

---

