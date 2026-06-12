---
title: "Cleaning up bloat"
date: 2005-10-22
forum: General Help
---

### Post by sisooktom on 2005-10-22
I'm new to Ubuntu; I've used mostly RH/Fedora in the past, and am trying to get used to a Debian based distro.  I'm wondering how to clean up some of the bloat that gets installed with Breezy by default.  I guess I'm just used to having a little more control over what gets put on my system.  For example, a quick lsmod lists more modules loaded into my kernel than I knew existed.  And, it was a 386 optimized kernel to boot!  Stuff gets loaded like Bluetooth, which might be fine if I wasn't running Breezy on a 6 year old PIII 600 Desktop.  And when I try to uninstall the stuff using Synaptic, it tells me there's a dependancy on Ubuntu-Desktop!  I don't mean to slam Ubuntu, I guess that having some bloat is the price we pay for having a distro that "just works".  But surely there has to be more configurability here, right?

---

### Post by Xian on 2005-10-22
[QUOTE=sisooktom]And when I try to uninstall the stuff using Synaptic, it tells me there's a dependancy on Ubuntu-Desktop![/QUOTE]
This is just a meta-pkg that is used during the initial setup of the system. It can be removed afterwards with no ill effects. It gets pulled in as a dependency because of the packages which are tied to it during the first install to disk.

---

### Post by sisooktom on 2005-10-23
Thanks a lot, I successfully cleaned up a bunch of junk.

---

