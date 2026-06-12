---
title: "Ubuntu installer slow at 82%"
date: 2008-01-06
forum: General Help
---

### Post by lancest on 2008-01-06
The Ubuntu installer hangs for 20 minutes often at 82% while scanning the mirror. Tried changing to faster mirror- but of no help. Any way to get around this? Will the installer in Hardy be improved? Seems unreasonably slow.

---

### Post by rubicon on 2008-01-06
I suggest you turn your Internet connection off (either by network manager or by plugging out a cable) before installation.

Currently there are some blueprints for Hardy. One of them is about LZMA compression of packages and indexes. This will slightly reduce amount of data fetched from Internet,

The second... The second is about behaviour that installer shows, If you disable Internet at install-time, you have to re-enable your repositories via Synaptic. That's because installer thinks you don't have connection at all and disables not only all updates, but all on-line repos.

Hope this helps.

---

### Post by lancest on 2008-01-06
Good idea thanks.  When I installed Debian it was considerably faster and I think that part of the Ubuntu installation should be retooled.

---

