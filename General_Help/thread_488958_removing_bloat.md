---
title: "removing bloat"
date: 2007-06-30
forum: General Help
---

### Post by Milambar on 2007-06-30
Ok, trying to remove the bloat thats creeping into my installation of Ubuntu...

apport? I never sent M$ dump reports to M$, and Im not going to send crash reports to the Ubuntu developers either, sorry. I have no clue what data its sending, for all I know, it could be my online banking details! Unlikely, I know, but I do value my privacy in this modern day surveillance world. 

How do I remove this please? It can't be removed via apt-get, as it thinks it must also remove xserver-xorg, ubuntu-desktop.. etc. Presumably set up that way by the packagers, to stop people removing it.

evms-engine? I have no idea what this even is! A quick look on google just turns up instructions for compiling and installing it, nothing telling me what it is, or why it's needed. What is it, and is it really really really needed? If not, how do I remove it?

---

### Post by Songwind on 2007-06-30
Removing ubuntu-desktop won't uninstall any software. You can go ahead and do it, if you want to.  Basically, those are "metapackages" that make it easy to install all the default software.  Since you are removing part of the default software, the default metapackage no longer has its dependencies met.  It's okay, though.

---

