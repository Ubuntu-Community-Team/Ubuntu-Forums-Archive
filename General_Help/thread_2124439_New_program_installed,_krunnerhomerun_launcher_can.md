---
title: "New program installed, krunner/homerun launcher cannot locate."
date: 2013-03-11
forum: General Help
---

### Post by Roasted on 2013-03-11
I'm running Kubuntu 12.04 with KDE 4.10.1. I have the Homerun launcher installed and I have krunner configured for use with Homerun. By doing that, I can open my launcher and just start typing and it'll find the application for me, similar to Unity's dash or Gnome Shell's search. I just installed the ownCloud sync client, and it now resides under Utilities. When I search for it, the system doesn't pick it up. If I favorite it, however, it is picked up just fine. I'm just curious if krunner has to do some sort of indexing to pick up new applications like this via search or if this is a limitation of the actual program (in this case, ownCloud) which results in the system not being able to scan for it. Any thoughts?

---

### Post by Roasted on 2013-03-11
I talked to the dev who manages homerun. He said it's a current bug that's already been filed.

[https://bugs.kde.org/show_bug.cgi?id=310714](https://bugs.kde.org/show_bug.cgi?id=310714)

He did say that running killall homerunviewer in terminal will reset and quietly restart homerun, resulting in it picking up newly installed applications. Otherwise it seems as if a restart fixes it as well.

EDIT - For what it's worth, a simple work around is to just create a keyboard shortcut which launches the command "killall homerunviewer". I set mine to ALT F12. That way if I install a new application and immediately want to search for it, I can hit that key combo and do my thing. This serves as a quick and super easy work around until the bug is fixed.

---

### Post by Roasted on 2013-04-29
For what it's worth, this issue is fixed in Homerun 0.2.2.

[http://agateau.com/2013/04/23/homerun-0.2.2-is-out/](http://agateau.com/2013/04/23/homerun-0.2.2-is-out/)

---

