---
title: "Odd issue with cups updates."
date: 2017-03-28
forum: General Help
---

### Post by exploder on 2017-03-28
Yesterday I installed updates, they were updates for cups. Last night I noticed all the cups packages are in Installed (local or obsolete) in Synaptic. The versions are 2.1.3-4ubuntu0.2(Now) and 2.1.3-4(xenial). Why are theses packages installed like this when they are not installed local or obsolete?This is on Ubuntu 16.04.2 x64.

---

### Post by ajgreeny on 2017-03-28
Same here on my Xubuntu 16.04 64bit system, tho0ugh in my case I wonder if this is related to the bug in the cups packages in 16.04 that caused cups to stop a few minutes after booting the system, meaning printing was sometimes difficult depending on the printer in use, and **localhost:631** was totally unavaiable.
See [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300) for details of the bug

This was solved for many users, including, me by enabling proposed repos, updating all the cups packages, and only those, to the newer version, then disabling proposed repos again to avoid potential breakages.

I have no idea if other proposed repos packages that are installed would also show in the **local or obsolete **status list as I don't normally enable proposed repos.

---

### Post by exploder on 2017-03-28
Thank you for the reply! I have never used the proposed repo on this install. I wonder though if the issue is caused by the version number when the packages were moved to the the main repos?

---

