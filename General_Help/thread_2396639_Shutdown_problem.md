---
title: "Shutdown problem"
date: 2018-07-18
forum: General Help
---

### Post by t.scottfp on 2018-07-18
Ubuntu 16.04 LTS with kernel 4.4.0-130-generic

Occasionally I may get the following message after typing **shutdown -Ph now **command. I am scratching my head, what may cause this issue? And how to solve this? That seems to me another process is also using the system like updater? Is there any place I can check which process needed to be cleanup or accomplished (so I can wait or at least check what's going on)? 

Thanks    

```

Operation inhibited by "UpdateManager" (PID 4496 "update-manager", user ), reason is "Updating System".
Please retry operation after closing inhibitors and logging out other users.
Alternatively, ignore inhibitors and users with 'systemctl poweroff -i'.

```

---

### Post by Skaperen on 2018-07-18
your apt database is probably locked due to an ongoing package update.  do you have automatic updating enabled?

---

