---
title: "UUID is showing up in Nautilus titlebar on separate partition"
date: 2016-01-01
forum: General Help
---

### Post by Matt_Dyck on 2016-01-01
Hey, I'm wondering if there's a way to change the name of my media partition on my computer. When in Nautilus the sidebar shows my partition with the name I gave it (Shared Partition) while the top bar shows the UUID instead. I'll just post my settings from fstab for now so you can see what I'm dealing with. (I'm a total beginner when it comes to this stuff, so please go easy on me if it's something obvious).
```

/dev/disk/by-uuid/5812318012316462 /mnt/5812318012316462 auto nosuid,nodev,nofail,x-gvfs-show,uid=1000,gid=1000,dmask=027,fmask=137 0 0
```

It's an NTFS partition, so I had to add some of these so I could be listed as owner of the drive and it's contents. [Also, I set it up to automount through the GUI before I ever saw it in fstab]

---

### Post by Matt_Dyck on 2016-01-01
Nevermind, I tried simply changing /mnt/58123...... to /mnt/Media and it worked. Also, I couldn't figure out how to delete this thread entirely. I apologize for my ignorance.

---

### Post by col48 on 2016-01-01
No apology needed.  Ignorance is where we all start from and the thread may help someone else with a similar question.  The dumbest question is the one which has not been answered simply because it has not been asked.

I believe that only a moderator can delete or move a thread.

---

