---
title: "Update Manager: Unauthenticated sources roundabout"
date: 2013-03-27
forum: General Help
---

### Post by t0p on 2013-03-27
Tried to update through Update Manager:
[ATTACH=CONFIG]240615[/ATTACH]

Clicked to install updates, got warning about unauthenticated sources:
[ATTACH=CONFIG]240616[/ATTACH]

Clicked 'Close', got this:
[ATTACH=CONFIG]240615[/ATTACH]

Clicked Install Updates, the merry-go-round continues...
[ATTACH=CONFIG]240616[/ATTACH]

So how am I supposed to get this update done?

---

### Post by oldos2er on 2013-03-27
Can you post the output of ```
sudo apt-get update
``` ?

---

### Post by freechelmi on 2013-05-18
I has the same problem.

Try to restore the default keys in the authentification tab of your software sources dialog

---

