---
title: "HDA permission changing"
date: 2007-05-16
forum: General Help
---

### Post by steve_o on 2007-05-16
I set up ubuntu on a laptop with 4 partitions, one I can view but dont have permission to write too it, how do I change it so I have full permission on that drive?

Mount Point: /media/hda3
File System: ext3
Mount options: rw data=ordered

Cheers

---

### Post by aquavitae on 2007-05-16
Try adding "uid=YourUserName" and "users" to the mount options.

---

