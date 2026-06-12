---
title: "Problem on running &quot;find&quot;"
date: 2016-05-11
forum: General Help
---

### Post by satimis on 2016-05-11
Hi all,

Ubuntu 16.04

On terminal
&#10219; sudo find / -name Transfer_Directory_PC1A
[sudo] password for satimis: ```

find: ‘/run/user/1000/gvfs’: Permission denied

```

Please advise how to fix the problem.

gksudo is NOT on repo

Regards
satimis

---

### Post by steeldriver on 2016-05-11
gvfs directories are mounted with user permissions only - if you want to search within a gvfs mounted directory, run the command as your user (not root)

---

