---
title: "Install packages/applications to a different partician"
date: 2007-11-06
forum: General Help
---

### Post by Augustus on 2007-11-06
Hey everyone.

On my infamous asus eee, I have installed Xubuntu on one partician.  Unforutnately, I did not leave enough room for installing lots of applications/packages on this partician, and my home folder is in a separate partician.  I was wondering if there would be a way to install applications/packages to the other partician -- I've tried googling, but I can't seem to find a way to do it.

Thanks,

~Augustus

---

### Post by ohzopants on 2007-11-06
I'm not 100% certain about this, but here goes anyway.

A "package" is simply a program that has been precompiled for a particular architecture and dependencies, the ones you install using apt or synaptic are just bunches of files which must be placed in particular folders in order to work properly.

You can most definitely install programs onto a different partition, but you will have to compile them by hand and provide the installer with the path you want.  Typically this is done at the "configure" stage by providing a "prefix".  Check out the documentation of the program you want to compile for specifics.

---

### Post by zvacet on 2007-11-07
resize your partitions with Gparted live CD.

[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

Take some space from home and add  it to your root partition.

---

