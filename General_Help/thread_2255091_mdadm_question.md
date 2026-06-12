---
title: "mdadm question"
date: 2014-12-02
forum: General Help
---

### Post by hop5uk on 2014-12-02
Can Anybody tell me if this command can be used without losing the data on my raid 5 array
mdadm --assemble --force /dev/md4 /dev/sdd1 /dev/sde1 /dev/sdf1

At the moment the array looks like this and a simple assemble of md4 does not work

md4 : inactive sde1[1](S) sdf1[3](S) sdd1[0](S)
      5860147414 blocks super 1.2

---

### Post by hop5uk on 2014-12-02
I decided to try it anyway and it reported that the disks were 'busy'. After a bit of research i realised that you must stop the array first before you run this command:
mdadm --stop /dev/md4

After doing this and running the assemble command, the array is now active.

---

