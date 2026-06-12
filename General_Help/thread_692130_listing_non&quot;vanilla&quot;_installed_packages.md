---
title: "listing non&quot;vanilla&quot; installed packages"
date: 2008-02-09
forum: General Help
---

### Post by irish_flu on 2008-02-09
Hey folks,

Wondering if anyone has any ideas to help me figure this out; I'm stumped.

OK: I have a system, running 7.10 (desktop. i386).

This system has had a group of students (who are working on a project) installing packages without much oversight, and now they need to pin down the configuration of the server (because it works, and they need to be able to replicate the system from scratch).

All non-standard packages have been installed via these three methods:
- synaptic
- apt-get
- python easy_install  (for python stuff)

Does anybody have a good idea for how I might find out what packages have been installed over-and-above the "vanilla" Ubuntu 7.10 Desktop install?  Ideally, I'll end up with a text file listing those packages.


The only method I've been able to figure out so far is to sort Synaptic's list be "installed or not", manually list those in a text file, then create a virtual Ubuntu install, list what packages are installed, then figure out the differences between those two lists.

There has got to be a better way than that, though.  I'd be happy to get just the apt-get and synaptic stuff, I can probably figure out the python packages separately.

---

### Post by pointone on 2008-02-09
If this has all been done recently, Synaptic has a "history" feature that shows you what packages have been installed.

---

