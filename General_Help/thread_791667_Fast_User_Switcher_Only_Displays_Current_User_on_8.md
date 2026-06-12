---
title: "Fast User Switcher Only Displays Current User on 8.04 after latest update."
date: 2008-05-12
forum: General Help
---

### Post by YankeeTransplant on 2008-05-12
Fast user switcher no longer works as of May 11. I see only the current user displayed, regardless of which user is logged in.

---

### Post by YankeeTransplant on 2008-05-12
UPDATE - It shows all logged in users in the deskbar applet, (with a checkmark next to their names as always), but does not show users not logged in, which previously were visible without checkmarks next to their names. Fast user switching among active users works properly.

WORKAROUND - Use System... Quit... Switch User... and login as the desired user. Then both users should be available in the applet. If it's not appearing, or just as a keyboard shortcut, use ctl-atl + f7 and ctl-atl + f9 to switch between desktop sessions. Additional sessions should be created on f10+. If you've somehow changed your tty session settings to use something other than 6 tty terminals, cycle through the F1-F12 function keys while holding ctl-atl to see all available tty terminals and desktops and find yours.

---

### Post by YankeeTransplant on 2008-05-13
SECOND UPDATE - Once the second user is closed, it remains in the fast user switcher applet menu and appears properly, without a checkmark. Clicking it logs in that user, but the only way to exit the new users session was via ctl-atl + backspace.

---

### Post by Malac on 2008-05-13
There's a bug to do with login/fast user applet the fix is:
```
sudo /usr/sbin/add-shell /bin/bash
sudo /usr/sbin/add-shell /bin/rbash
```Report is here:
[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/228931](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/228931)

Hope this helps.

---

### Post by YankeeTransplant on 2008-05-13
Fixed with Bash update available today, May 13th.

---

