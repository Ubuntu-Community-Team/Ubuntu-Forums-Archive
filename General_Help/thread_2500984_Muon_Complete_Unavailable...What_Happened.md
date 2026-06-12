---
title: "Muon Complete Unavailable...What Happened?"
date: 2024-09-18
forum: General Help
---

### Post by wyattwhiteeagle on 2024-09-18
I noticed muon wasn't installed by default in 24.04 Noble.
I typed into terminal ```
   sudo /usr/bin/apt-get install -y muon
```
Terminal returned ```
muon not found
```
Where did it go?

---

### Post by Yellow Pasque on 2024-09-18
Muon is dead upstream: [https://apps.kde.org/muon/](https://apps.kde.org/muon/) (I guess KDE wanted to focus on its app store, "Plasma Discover", and leave package management to the distros.
The muon package was removed from Debian early last year.
Use Synaptic.

---

