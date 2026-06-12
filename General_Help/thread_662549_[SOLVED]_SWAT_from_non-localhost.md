---
title: "[SOLVED] SWAT from non-localhost"
date: 2008-01-09
forum: General Help
---

### Post by descentspb on 2008-01-09
Please, help me with such a problem.

I can load and control SWAT via localhost:901, and a few days ago i could do it through my network (something like [http://IP:901](http://IP:901)), and now it just shows a blank page when i try to connect (exactly a blank page, not just "sorry, i can't connect".

What can i be doing wrong? My smb.conf looks exactly like it was a few days ago, when it was working. Maybe some kind of a process/daemon or something?

---

### Post by descentspb on 2008-01-09
it was a variable in xinetd.conf (somehing like "only connect from = localhost")

---

