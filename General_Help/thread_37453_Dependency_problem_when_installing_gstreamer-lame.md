---
title: "Dependency problem when installing gstreamer-lame"
date: 2005-05-27
forum: General Help
---

### Post by davegahan on 2005-05-27
Using synaptic to download and install gstreamer0.8-lame I get the following error from synaptic:

gstreamer0.8-lame:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

However, 2.3.2.ds1-20ubuntu13 is already installed, whats wrong ?

---

### Post by David Kaisemann on 2005-05-27
[QUOTE=davegahan]Using synaptic to download and install gstreamer0.8-lame I get the following error from synaptic:

gstreamer0.8-lame:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

However, 2.3.2.ds1-20ubuntu13 is already installed, whats wrong ?[/QUOTE]

Different versions. Look: *ds1-**21*** needed, *ds1-**20*** installed. I'm was have same problem and just installed new library and then all going OK.

---

