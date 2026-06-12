---
title: "Why won't /home/username/.cache/dconf and /home/username/.gvsf back up?"
date: 2015-01-09
forum: General Help
---

### Post by angelo8 on 2015-01-09
I'm trying to use the ubuntu backup utility to backup my hard drive. Each time I try to back it up I get an error saying /home/username/.cache/dconf and /home/usernae/.gvsf failed to back up. What could be the reason causing this? I could put them on the ignore list, but I'd like to know why I'm getting the error.

BTW I'm using Ubuntu 14.04

Thanks!

---

### Post by mc4man on 2015-01-09
Maybe because root owns them?
(- neither is used in a default 14.04 install anymore but can be created when using sudo for gui apps 

Or could possibly be from a previous install if you upgraded, in any event you can remove them.

---

### Post by cmcanulty on 2015-05-14
bugs me too i change it to me and it changes itself back, grsync gives an error on it in backup also root files shouldn't be in home

---

