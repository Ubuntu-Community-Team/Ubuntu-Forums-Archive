---
title: "What would happen if 2 different PPAs were added for the same game or software?"
date: 2014-12-12
forum: General Help
---

### Post by Rytron on 2014-12-12
Hi.

What would happen if 2 different PPAs were added for the same game or software e.g. Liferea? How would it know which PPA to update to? Would there be 2 different versions installed at the same time?

Thanks.

---

### Post by ajgreeny on 2014-12-12
No, I don't think so.  You would by default get the most up to date version of the package, which is the default update method, ie, to always prefer the highest version of packages.

---

### Post by Dennis N on 2014-12-12
You don't need two PPAs for this situation - it exists whenever the PPA has the same software package as the Ubuntu repositories, but a different version. The package manager offers the newest version it can find from any of its sources and ignores the others.

---

### Post by ian-weisser on 2014-12-12
The package manager doesn't care about the source (Ubuntu Repository vs PPA). It only cares about the apparent version number.

Example:

Upstream releases it's game Foo 1.5
A Debian packager uploads the package as Foo_1.5.1 (Debian add the .1 for several good reasons)
Ubuntu imports the Debian package as Foo_1.5.1ubuntu0 (Ubuntu adds the suffix for the same good reasons)

Meanwhile, Sue packages Foo 1.5 independently for her PPA as Foo_1.5.0~ppa
And Jared also packages the pre-1.5 release candidate in his PPA as Foo_1.5rc

Now apt tries to sort this all out: Which should it install?
Foo_1.5.1ubuntu0 ?
Foo_1.5~ppa ?
Foo_1.5rc ?

This is an example of well-intentioned PPA maintainers using non-standard versioning and thereby polluting the sources and breaking user systems. The package manager mistakenly decides that '1.5.1u' must be a higher version than '1.5.0' or '1.5r', and --by mere chance-- happens to install the Ubuntu repository version.

Now let's take it a step farther. Foo releases new version 1.6 in January.
Sue, an enthusiast, pushes it to her PPA In early February as Foo_1.6~ppa
Debian picks it up in March as Foo_1.6.1
Ubuntu picks it up too late for the April release, so April is Foo_1.5.1ubuntu0, and October is Foo_1.6.1_ubuntu0

When you update your system in early February, '1.6~' is higher than '1.5.1u', so the package manager installs the PPA version.
Then, in April, you update to the next version of Ubuntu.
And -BLAM-, maybe that PPA is compatible with the next version of Ubuntu, maybe not. The PPA version number is still higher, but perhaps all the underlying dependencies have changed. The result can be a broken system.

 
I generally recommend against long-term subscription to non-Ubuntu sources for precisely this reason. Many users install from PPAs, forget they did so, enjoy the latest software...until one day their system is broken and they cannot determine why. Turns out the PPA provides a different file than the Ubuntu version, causing a conflict, or the PPA versioning prevents an upgrade.

---

### Post by Rytron on 2014-12-13
Thanks for the info guys. ):P

---

