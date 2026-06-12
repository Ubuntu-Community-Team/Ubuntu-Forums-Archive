---
title: "Can GParted move a partition from one place to another on HDD"
date: 2019-04-01
forum: General Help
---

### Post by swarup on 2019-04-01
I am in the process of installing 18.04, and there is 4 GB of unallocated space on the other side of a restoration partition, from the partition where I will be installing 18.04. Can GParted move the restoration partition so that the 4 GB of unallocated space can be joined together with the partition where I'll install 18.04?

---

### Post by Dennis N on 2019-04-02
Open gparted and look at View > File System Support
This will tell you what operations are supported for each file system type shown on the left. Note the required software on the right side. Moving a partition is not risk-free and could fail, so back up your data. If the move is possible and it succeeds, you can expand the partition you plan to use into the unallocated space.

---

### Post by swarup on 2019-04-02
Thanks, got it. 
Yes, I saw in gparted just before reading your post that I could actually move the entire restoration partition. I didn't give the order to execute it yet, but it does allow me to set up the action. Hopefully the execution will be successful. Thanks!

---

