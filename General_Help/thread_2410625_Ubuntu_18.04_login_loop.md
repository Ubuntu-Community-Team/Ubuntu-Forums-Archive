---
title: "Ubuntu 18.04 login loop"
date: 2019-01-18
forum: General Help
---

### Post by 700 on 2019-01-18
PROBLEM:
Login loop while trying to login to the system.
I can login after I change Sign In settings from Ubuntu to Unity, but I'm missing all my settings on Launcher and Workspace Grid (Gnome Tweak Manager).

CONDITIONS:
- System: Ubuntu 18.04.1 LTS
- Machine: Dell Optiplex 990
- Processor: Intel Core i5-2400 CPU @ 3.10GHz × 4 
- GPU: *NV106* (on Ubuntu) **or** *GeForce GT 710/PCIe/SSE2* (on Unity)
- GNOME: 3.28.2
- OS type: 32-bit

---

### Post by drlamb on 2019-01-18
Have you made any modifications to your . files? Improper settings can cause GDM to fail in a similar manner.

---

### Post by 700 on 2019-01-18
It looks like it was a > ~/.config/compiz-1 problem.
Is it possible to bring back my previous compiz settings or I have to set everything back again?

RESULT:
Instead of my "Workspace Grid" I have now a "Workspace Ladder". 
Why compiz triggered problem, while I'm using Tweak Manager? Is this the same manager?

---

### Post by drlamb on 2019-01-28
As I don't use compiz I'm unsure. Though I imagine one could just remove the offending line...if one knew which it was.

---

