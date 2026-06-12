---
title: "Logout troubles"
date: 2007-02-09
forum: General Help
---

### Post by justin on 2007-02-09
Recently, when logging out, and possibly when switching user, gnome does not return to the gdm properly. Instead, it just returns to a black screen with a flashing cursor, but now prompt, and I am unable to type. Is there anything that can be done to prevent this, or, is there a way to fix it and return to the gdm without rebooting the computer?

It doesn't happen everytime, probably 10% of the time. It may happen when two users are logged in at a time.

---

### Post by ingo on 2007-02-10
Do 
> sudo dpkg --reconfigure -a
and see whether it works now. If it still does not, install kdm and try that.

---

