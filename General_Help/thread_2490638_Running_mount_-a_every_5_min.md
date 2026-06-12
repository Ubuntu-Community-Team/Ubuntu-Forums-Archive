---
title: "Running mount -a every 5 min"
date: 2023-09-10
forum: General Help
---

### Post by rhysers07 on 2023-09-10
Is there any reason I shouldn't run mount -a every 5 min? I have a script that checks the status of several services and restarts them if necessary. I realized that some of those services fail to start because if my VMs don't boot fast enough, the mount point isn't available yet and the services depend on files. I only just added the mount -a, but I want to be sure it wouldn't cause any problems.

---

### Post by MAFoElffen on 2023-09-11
Why not check if the mounts you want and think are required exist first? then if they do not, then remount? That way, if they do exist, if just does nothing... I think that would be the smarter approach to that.

---

### Post by TheFu on 2023-09-11
Or use **autofs**, which is much cleaner.

---

