---
title: "How to disable restore from session Kubuntu"
date: 2007-10-14
forum: General Help
---

### Post by markk1994 on 2007-10-14
I have Compiz Fusion on right now and it keeps restoring itself along with other apps at startup how do I disable things from startup?

---

### Post by ajgreeny on 2007-10-14
Not sure about compiz-fusion, but most apps are started in kde at boot by simply linking to them in the ~/.kde/Autostart folder.  Just remove, or rename the xxx.desktop file to xxx.desktop~ and it will not load again at boot.  However, I have a suspicion that compiz-fusion is started at a different point to these, and if that is the case, I will have to defer to others with more knowledge than me.
You may also be using the session manager to use the last session you were running.  Check that in System settings> Sessions, and if so chose to use an empty session at startup.

---

