---
title: "Providing a simple log out button that saves panel changes"
date: 2007-09-16
forum: General Help
---

### Post by imbjr on 2007-09-16
Basically, I just need a way to provide a log out button so my son does not shutdown/restart the PC.

Neither: 
skill -KILL -u <user>
nor:
pkill -KILL -u <user>

appear to save any changes made to panels though and I've been accusing him of deleting buttons!

---

### Post by imbjr on 2007-09-24
Solution:

gnome-session-save --kill --silent

That logs the user out and saves their session.

---

