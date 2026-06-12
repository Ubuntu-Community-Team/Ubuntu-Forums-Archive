---
title: "Turn off PC with power button. Is it possible?"
date: 2006-09-01
forum: General Help
---

### Post by PryGuy on 2006-09-01
Good day! Is it possible to turn off PC with a power button? I tried to find some parameter that allows to do that but the best thing I've done so far is the logoff when I press the power button after I unchecked the "Ask on logout" checkbox in the Preferences\Sessions window. Please help!

---

### Post by viciouslime on 2006-09-01
Press alt+F2 and enter gconf-editor, then goto apps > gnome-power-manager > action-button-power and change it from interactive to shutdown.

---

### Post by hw-tph on 2006-09-01
Thanks, I didn't know that. It has been bothering me since I upgraded to Dapper but it didn't annoy me enough to look it up. :)


Håkan

---

### Post by PryGuy on 2006-09-01
Works cool for me, thanks!!!:D

---

