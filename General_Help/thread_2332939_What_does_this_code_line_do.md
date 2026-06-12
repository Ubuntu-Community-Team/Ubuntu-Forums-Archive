---
title: "What does this code line do?"
date: 2016-08-05
forum: General Help
---

### Post by jack0987 on 2016-08-05
What does this code line do?

export DISPLAY=:0

---

### Post by steeldriver on 2016-08-05
It sets the value of variable DISPLAY to :0 and then exports it to the environment (so that it is available to other processes started from that environment)

Usually it's only required when trying to talk to processes in a user's GUI session from outside of that session (such as from an SSH session or a virtual terminal)

---

### Post by ajgreeny on 2016-08-05
It is also needed if you want to start a GUI process using cron

---

### Post by 1clue on 2016-08-05
> **ajgreeny said:**
> It is also needed if you want to start a GUI process using cron

While this is true and it's sometimes beneficial, I strongly urge anyone who wants to try it to have significant experience both with cron and with X in whatever context you intend to mix them before putting it all together.

---

