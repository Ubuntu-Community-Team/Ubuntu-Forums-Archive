---
title: "[SOLVED] KDE apps startup delay in Ubuntu"
date: 2007-10-20
forum: General Help
---

### Post by Sisophon2001 on 2007-10-20
After startup each day, the first time I start a KDE application in Ubuntu it is very slow loading. There is no delay when I start subsequent KDE applications. This is in contrast with SUSE 10.2 which I used before switching to Ubuntu. My assumption is that SUSE 10.2 must be loading the libraries needed by KDE applications during start-up. Is there a way that Ubuntu can be adjusted to load KDE libraries on start-up, or is there other solutions to this problem?

I prefer the Gnome desktop, but I find some KDE applications to be better than their Gnome counterparts, so I like to mix and match.

Thanks

Garvan

---

### Post by Sisophon2001 on 2007-10-31
The solution was to add kdeinit to the start-up programs in System->Preferences->Sessions.

---

