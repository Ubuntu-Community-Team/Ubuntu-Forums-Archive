---
title: "Installing gpart package"
date: 2015-05-31
forum: General Help
---

### Post by matthew90 on 2015-05-31
In gparted, when I attempt to do a data rescue, a dialog box appears that says I need to install gpart. Naturally, I went into Terminal and typed ```
sudo apt-get install gpart
```, which returned ```
No installation candidate in pagage 'gpart'.
``` How do I install it?

---

### Post by deadflowr on 2015-05-31
Is this from a livecd?
Or else, what version of Ubuntu.

gpart is in the community repository (universe)
so that needs to be enabled.

Typically open Software and Updates enable the community repo, then close software and updates, and when it closes choose the reload option when it asks.
The reload refreshes the package lists you can get and the newly enabled repo (with all of it's available package) will be part of it.

^^^This advice is pertinent upon using a newer version of Ubuntu.
As older versions have different names for where things are/were.

It is also dependent in having a internet connection (but I assume you probably know that)...

---

