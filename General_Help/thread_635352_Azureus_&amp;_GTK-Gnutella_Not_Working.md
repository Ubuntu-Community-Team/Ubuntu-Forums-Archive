---
title: "Azureus &amp; GTK-Gnutella Not Working"
date: 2007-12-08
forum: General Help
---

### Post by Bungo Pony on 2007-12-08
I've been trying like crazy to get both of these working without success. GTK-Gnutella is complaining about an old version, but when I do a sudo apt-get upgrade, it basically says the newest version is installed.

In Azureus, I can't get any port to work for me. I've been trying to allow ports on the linksys router, but that's not helping anything either.

Any suggestions?

---

### Post by cbiere on 2007-12-09
Gutsy and Hardy have the latest gtk-gnutella 0.96.4. The others only have an outdated version.

You can easily compile gtk-gnutella yourself from the sources in a few steps:
[https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/README.Debian](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/README.Debian)

You'll find the sources of releases and snapshots at SourceForge:
[https://sourceforge.net/project/platformdownload.php?group_id=4467](https://sourceforge.net/project/platformdownload.php?group_id=4467)

---

