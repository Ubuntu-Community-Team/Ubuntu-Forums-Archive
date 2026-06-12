---
title: "how to start a GUI with cron when not logged in"
date: 2008-06-11
forum: General Help
---

### Post by EdwardTheThird on 2008-06-11
Hi,

it took me quite some effort to get gui program started through a cron task .
I had to add stuff like "xhost +" and "export DISPLAY=:0.0 && command" but it finally worked.

_However: _
If my PC is restarted, and noone is logged in, the task will still run, but the GUI application (firefox) just won't start (probably because there is no active display ) .
Can anyone please help me out on how to solve this  because I'm a newbie to linux...

Thanks already for any advice.

---

