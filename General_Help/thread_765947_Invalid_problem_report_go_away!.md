---
title: "Invalid problem report go away!"
date: 2008-04-24
forum: General Help
---

### Post by kakalaky on 2008-04-24
I just upgraded to 8.04 and everything is working great after manually configuring grub as always (dmraid) except one thing.  I had a screenlet crash the first time I booted into 8.04 and the problem report app went crazy.  Now I get a popup every few seconds that says "Invalid Problem Report."  I know it's invalid and I didn't even tell it to send a problem report.  Anybody know how to get it to stop trying to send it.  The popup is really starting to annoy me.

Edit:  apport seems to think any running screenlet is crashing every few seconds.  I deleted the relevant files from /var/crash and they reappear every few seconds. Anybody kow how to stop apport from thinking the screelets are crashing?

Edit again:  Reinstalled the screenlets and now everything is fine.

---

