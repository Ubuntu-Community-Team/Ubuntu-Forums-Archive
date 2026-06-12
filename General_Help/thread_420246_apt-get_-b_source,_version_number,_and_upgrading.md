---
title: "apt-get -b source, version number, and upgrading"
date: 2007-04-23
forum: General Help
---

### Post by strider1551 on 2007-04-23
Hey all,

  After reading [this]("http://doc.gwos.org/index.php/Recompile_packages"), I made myself a quick python script to recompile whatever package I tell it so that I can have the benefit of things being compiled for my specific hardware.  After recompiling a few things I came across an interesting problem.  The update manage will pester me to upgrade some of the packages but not others.

For example, I recompiled gedit and spe.  The update manager wants me to upgrade spe to the same exact version, but doesn't mention gedit.  I looked in synaptic and looked at the versions available under the properties of spe:
```
0.8.2a+repack-1 (feisty)
0.8.2a+repack-1 (now)
```
Gedit only lists a feisty version, not a "now" version.

Anyone know what's going on?

---

