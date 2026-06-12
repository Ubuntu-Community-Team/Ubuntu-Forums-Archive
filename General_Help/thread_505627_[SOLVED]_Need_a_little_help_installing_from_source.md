---
title: "[SOLVED] Need a little help installing from source"
date: 2007-07-20
forum: General Help
---

### Post by rillip on 2007-07-20
I'm trying to install an older program from source.  It's failing ,/configure due to qt2 not being found.  It's not found because I have qt3 and qt4, but not 2.  Would it make more sense to try and install qt2 or to try and change the configuration files to use qt3/4?  It's looking in /usr/lib/qt2.  Could I just symlink that to qt3?

Edit: tried the symlink, that didn't work.

---

### Post by Happy_Man on 2007-07-20
What program? Because, if it needs qt2 libraries, it's too old for anything practical. More than likely there's a replacement for qt3.

---

### Post by rillip on 2007-07-21
It's an old browser, called NetRaider.  I'm pretty sure it's discontiued, this is the newed source I could find on SourceForge.  I'm mostly just building it as a toy project

Edit: eh, forget it.  Decided this wasn't worth the trouble

---

