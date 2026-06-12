---
title: "Application keeps crashing *Killed* - not finding relevant log info."
date: 2023-10-18
forum: General Help
---

### Post by nofunever on 2023-10-18
I've had this problem for a while now both in 22.04 and now again in 23.10. Reaper keeps crashing while loading projects.

When I run from the terminal it will be loading plugins when it suddenly outputs "Killed". It happens after a different plugin for each project so I can't point to a specific plugin, but it does only happen when i'm loading larger projects with more tracks and plugins.

My understanding is this is caused by the OOM Killer ruining my day. I've tried looking at dmesg for more details as to why it's killing reaper but nothing can be found there that is relevant. Supposedly one can check /var/logs/messages* for OOM Killer output but this doesn't exist on my system.
Where is OOM activity logged too? It would really help to understand why it's sporadically crashing during loads.

---

### Post by TheFu on 2023-10-20
I'd use **free -hm** to see if memory is tight or not.

---

