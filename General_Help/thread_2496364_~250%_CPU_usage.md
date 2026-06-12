---
title: "~250% CPU usage??"
date: 2024-03-25
forum: General Help
---

### Post by matty-ct on 2024-03-25
Think I solved it.

---

### Post by The Cog on 2024-03-25
I think it depends how many cores you have. I think it just reports how much CPU time has been used divided by the elapsed time. I think the top process has two cores pegged at 100% - presumably by two threads working as hard as they can.
If you have 4 cores, you can get up to 4 seconds of active core time used in each second, which would report 400%.

---

### Post by matty-ct on 2024-03-25
Disabled mod_php

---

