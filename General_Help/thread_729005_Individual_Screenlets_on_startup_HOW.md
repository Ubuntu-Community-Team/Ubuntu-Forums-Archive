---
title: "Individual Screenlets on startup? HOW?"
date: 2008-03-19
forum: General Help
---

### Post by kelinu on 2008-03-19
Hi,
I use Gutsy and I have screenlets installed on my machine.  I was wondering if it was possible to make individual screenlets start automatically when i log in...How could i do this?

---

### Post by aashay on 2008-03-19
The screenlets manager has a "autostart on login" option which can be enabled to do this.
Else you can add such a command to startup:
python ~/.screenlets/CircleSensors/CircleSensorsScreenlet.py > /dev/null
Just replace the Screenlet name and folder with one of your choice

---

