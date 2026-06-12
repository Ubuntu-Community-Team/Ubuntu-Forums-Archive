---
title: "Can't unbind Hide All Windows in Ubuntu 12.10"
date: 2012-11-17
forum: General Help
---

### Post by MidnightJava on 2012-11-17
After upgrading to 12.10, a familiar problem occurred again, but the familiar solution is not working. When I connect to Ubuntu via NX Client from a Mac, the d key minimizes all windows. In the Keyboard system preference, the "Hide all windows" command was already bound to ctr-alt-D, not d. I disabled it while connected via NX Client, and then rebooted the Ubuntu system. Still I can't type a d character without closing the terminal window.

I checked all the other bindings, and I don't see anything else bound to the d character. Is anyone else having this problem in 12.10?

---

### Post by MidnightJava on 2012-11-17
After the fourth reboot, the problem finally cleared. The first three re-boots were doen from an ssh session. Maybe it didn't do a full reboot for some reason, although the connection would drop and the system would be unreachable for a minute or so. When I rebooted it from the workstation, the key binding issue cleared.

---

