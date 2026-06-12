---
title: "gconf-- x startup hangs"
date: 2005-10-19
forum: General Help
---

### Post by r0ric on 2005-10-19
After logging in to gui prompt, the screen goes brown.
I've got a working mouse cusor, and I can log in on tty1.
The system hangs out in this state for about six minutes,
then the desktop comes up and things seem okay.
log files show this six minute delay always ending with a message
from gconf, resolving /home/user/.gconf to writable config src.
this happens at every boot.
e.g.
----------------------
Oct 17 23:46:10 localhost gconfd (ryan-7702): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Oct 17 23:46:10 localhost gconfd (ryan-7702): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Oct 17 23:46:10 localhost gconfd (ryan-7702): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7

 /* Oct 17 23:46:11 localhost kernel: [4294726.359000] Bluetooth: L2CAP ver 2.7
  ...
  */  (a few bluetooth messages)

Oct 17 23:52:36 localhost gconfd (ryan-7702): Resolved address "xml:readwrite:/home/ryan/.gconf" to a writable configuration source at position 0
------------------------

---

### Post by secundar on 2005-11-11
I have the same problem after changing a setting in the Services app. I think i unchecked GDM - if that's possible - and the session crashed - screen garbled and now i'm stuck on the brown screen with cursor.

I've tried purging/installing gconf2 with no success.

Using Xfce now. Any ideas?

---

