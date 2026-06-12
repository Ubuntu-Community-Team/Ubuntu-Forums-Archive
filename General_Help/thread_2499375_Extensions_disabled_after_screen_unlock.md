---
title: "Extensions disabled after screen unlock"
date: 2024-07-24
forum: General Help
---

### Post by caterhamfan on 2024-07-24
I recently upgraded from 22.04 to 24.04 and everything has gone well so far. Just one issue. When I lock my screen and unlock it ubuntu boots with my extensions disabled.

I've googled around to see if there are any fixes for this. I have tried reinstalling my drivers with no luck.
Anyone else know what I could try?

Thank you,

---

### Post by currentshaft on 2024-07-24
Which extensions?

Any messages in the output of the following command after it happens?

journalctl --since "5 minutes ago"

---

### Post by Claus7 on 2024-07-26
Hello,

verify also that none of them is out of date. I would advice you to track them down on paper, (there is also an extension that can do that, yet anyway), remove them all and install them anew.

Regards!

---

