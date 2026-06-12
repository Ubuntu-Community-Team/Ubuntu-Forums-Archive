---
title: "Is KGraphViewer in the repos?"
date: 2007-10-07
forum: General Help
---

### Post by leonidas666 on 2007-10-07
Hi, 

I would like to install KGraphViewer. This Programm is supposedly part of KDE, in the "extragear" package. 
When i search in synaptic for "extragear" or "Kgraphviewer" i find nothing. Is this programm really not in the repositories? Beeing part of KDE, it actually should be included somewhere, right?

---

### Post by jynyl on 2007-12-30
The kgraphviewer app doesn't seem to be in the repos, but a source tarball can be downloaded from 
[http://extragear.kde.org/apps/kgraphviewer/]("http://extragear.kde.org/apps/kgraphviewer/").

But when I try to compile this on Kubuntu 7.10, it gives lots of errors.  Installing xorg-dev and qt3-apps-dev seems to resolve some of these, but there is an error about KDE prefix, and I'm not sure how to resolve this one. > checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
Any tips or suggestions on this one most appreciated.

TIA

Peter

---

### Post by jynyl on 2007-12-30
ok, it wasn't a problem with prefix.  Installing kdebase-dev seems to have cleared the configure errors, and enabled the app to configure and compile.

---

