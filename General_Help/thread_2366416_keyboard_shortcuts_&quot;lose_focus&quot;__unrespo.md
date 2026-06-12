---
title: "keyboard shortcuts &quot;lose focus&quot; / unresponsive without mouse click"
date: 2017-07-17
forum: General Help
---

### Post by cedardoc on 2017-07-17
Sometimes my keyboard shortcuts don't work until I click something on the screen with the mouse, and then they work.  Kind of defeats the purpose of having keyboard shortcuts, ha ha.

Any suggestions?

---

### Post by cedardoc on 2017-07-18
I think I posted this on the wrong section.  I'll post it in general help

---

### Post by oldos2er on 2017-07-18
Moved to GH.

---

### Post by again? on 2017-07-18
Are you running any desktop apps like conky?

---

### Post by cedardoc on 2017-07-18
Yes I am running conky.  Should I post the config file?

---

### Post by cedardoc on 2017-07-18
Thanks for the hint.  I googled it with conky now and came up with this: change own_window_type to "override"

seems to be working so far.   I'll update if I'm wrong.

---

### Post by again? on 2017-07-20
Ok, looks like you have it sorted.
With different window managers you need to try different settings for "own_window_type".
Either  normal, desktop or override usually solves it.

---

