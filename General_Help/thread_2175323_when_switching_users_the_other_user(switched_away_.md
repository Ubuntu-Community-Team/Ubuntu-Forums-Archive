---
title: "when switching users the other user(switched away from) goes into a frozen state?"
date: 2013-09-18
forum: General Help
---

### Post by afonit on 2013-09-18
I have two users:
users -a
users -b


I loginto user -a that does some automation (gui testing using xpresser application)
I then switch to user -b
after switching back to user -a I noticed that the automation paused, then resumed when I came back into user -a.


Is there a setting in ubuntu somewhere so that when you switch to another user, the user you switched from keeps on working?

---

### Post by afonit on 2013-09-19
Upon further investigation - It looks like this is actually an issue with adobe-flash in firefox pausing.
(which the automation is using (looking at a flash based website and clicking around).

Does anyone know how to keep the flash-plugin from pausing when in another user profile on the same machine?

---

