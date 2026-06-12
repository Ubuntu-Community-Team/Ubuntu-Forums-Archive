---
title: "how to change vnc port in ubuntu"
date: 2008-04-16
forum: General Help
---

### Post by taimur on 2008-04-16
hi
can you tell me how to change port of vnc in ubuntu

---

### Post by Blues- on 2008-05-08
- Open up gconf-editor (Alt+F2, run gconf-editor).
- Browse to the key /desktop/gnome/remote_access/use_alternative_port
and check the checkbox.
- Modify the value of the alternative_port key.
- Restart vino with the remote desktop config dialog.

---

