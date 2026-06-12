---
title: "Ubuntu logging out when I sign in after sleep mode"
date: 2017-12-17
forum: General Help
---

### Post by jupitteer on 2017-12-17
Ubuntu 17.10. About half the time when I open up my laptop and log in after sleep mode, it will switch to the login screen when first opening up ubuntu out of a reboot instead of going into gnome. Any reason why this is happening? It's getting extremely frustrating.

---

### Post by ian-weisser on 2017-12-17
That kind of "switch" usually means a display stack crash.
Are you logged into a Wayland session or an X session?
Do you have the same problem if you log into the other kind of session?

Note the EXACT time you wakeup the machine a few times. Check your logs (/var/log/syslog). Compare successful and crashed wakeups. If possible, show us both.

---

