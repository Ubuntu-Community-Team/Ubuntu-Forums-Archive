---
title: "GRSync question"
date: 2021-05-05
forum: General Help
---

### Post by sofasurfer on 2021-05-05
In GRSync, under advanced options there us a check box for 'backups'. The tool tip says "make backup of existing files on destination". I don't get it. The whole purpose is to make a backup. So why am I given an option to make a backup of a backup...if that is what its saying.

---

### Post by Tadaen_Sylvermane on 2021-05-05
(G)rsync is just a tool. It is not a backup tool specifically. That being said the option likely maintains permissions such that you can restore easily enough. Problem with gui though is they aren't always documented easily. Command line rsync you can find exactly the flags you want with little difficulty via the man pages.

---

