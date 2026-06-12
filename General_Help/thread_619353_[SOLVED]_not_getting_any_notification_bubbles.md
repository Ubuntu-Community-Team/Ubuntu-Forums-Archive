---
title: "[SOLVED] not getting any notification bubbles"
date: 2007-11-21
forum: General Help
---

### Post by spanella47 on 2007-11-21
am not getting any notification bubbles when:
- updates available
- music changes
- drives unmounted (safely or unsafely)

from what i can tell the notification-daemon isn't running at all, but is installed.  How do i fix this?

---

### Post by Super TWiT on 2007-11-21
I broke this once on my computer and it drove me crazy.  I finally figured out that its a thing that you add to your panel.  Try right clicking the panel that you want it on and clicking on Add to Panel, then clicking on Notification Area.  It took me forever even to find that in the add to panel dialog.

---

### Post by spanella47 on 2007-11-21
already have a notification area on my panel...

---

### Post by spanella47 on 2007-11-24
anyone else have any ideas?

---

### Post by spanella47 on 2007-12-07
for some reason my notification-daemon theme was set to "standard" rather than "ubuntu" within gconf and that seems to have been part of the problem.  the other part was that notification-daemon does need to run all the time.  added it to sessions as:
/usr/lib/notification-daemon/notification-daemon.

---

