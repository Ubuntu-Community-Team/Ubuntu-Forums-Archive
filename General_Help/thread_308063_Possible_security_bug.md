---
title: "Possible security bug"
date: 2006-11-27
forum: General Help
---

### Post by zapcojake on 2006-11-27
Hello, I just configured my box for nfs and samba.  When I did this I was never asked for a root password. and i had to install the nfs and samba packages.

---

### Post by po0f on 2006-11-27
zapcojake,

Did you do this in the terminal?  And did you previously use sudo during the same session?  IIRC, sudo let's you keep privileges for ~15 minutes after entering your password if used in the same terminal session.  Now, if you configured it without using sudo *and* it not complaining, that's a different story.

---

### Post by zapcojake on 2006-11-28
Not for sure on the sudo part but no I did the point and click method for installing samba and nfs

---

### Post by rioghal on 2006-11-28
> **zapcojake said:**
> Not for sure on the sudo part but no I did the point and click method for installing samba and nfs

If you run an admin app, for instance gdmsetup, and then run another admin app, for instance synaptic, within a certain time period, the system won't ask you for the admin user's password again. There's a timeframe where the system keeps your admin user's password so you don't have to enter it every time you run an admin app.. this goes for both command line apps and gui apps, but I'm not sure what that timeframe is.

---

