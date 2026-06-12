---
title: "why does my shutdown go to the log in screen instead of....shutting down"
date: 2013-10-29
forum: General Help
---

### Post by ripx2 on 2013-10-29
always happens. I pick shut down because I want to be done, but then it goes to the log in and i have to pick shut down again....

what can I do??

---

### Post by ripx2 on 2013-10-30
wow, no one knows?

---

### Post by ian-weisser on 2013-10-30
It usually means something is crashing your X server (display server), aborting the command in process.
The server restarts automatically...taking you to the login screen.

Solving the problem means a bit of you digging around in /var/log/syslog and /var/log/Xorg and other logs trying to find the exact error that occurred.

Is there anything you can do about it? Perhaps. We won't know until we know why it crashes for you but not for other users.
For example, I can logout just fine, without X crashing. It's difficult to investigate a problem that we do not have.

---

### Post by philinux on 2013-10-30
Also look at the .xsession-errors file in your home folder.

---

