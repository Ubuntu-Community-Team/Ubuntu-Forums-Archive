---
title: "Same separate /home for two distros problem"
date: 2008-07-06
forum: General Help
---

### Post by red_team316 on 2008-07-06
I myself like having a separate /home partion. Just the other day though, I installed Fedora 8 alongside of my ubuntu install. I pointed my existing /home partition so that it should be mounted correctly in both installs. I've done this in the past but this time I used the same username for both fedora and ubuntu. The result = now I can't graphically log in at all with either distro :P. Something to do with conflicting desktop settings I think.

Should I create a new username for each distro? It's making me think that from now on I should forego the separate /home partition and keep all my personal data on a sepatate partition and just mount it in /home/username/datapartition

---

### Post by aysiu on 2008-07-06
You should not share a /home partition between two distros. I would go with the separate /data partition and maybe just symlink your web browser and email settings to both distros.

---

