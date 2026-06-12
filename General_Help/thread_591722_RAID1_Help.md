---
title: "RAID1 Help"
date: 2007-10-25
forum: General Help
---

### Post by xlr8ed on 2007-10-25
I have my file server up and running 7.10, everything is working just dandy, no issues.

I have plugged into it, two 750 Gig USB drives. One is shared via samba and is just about half full, both contain the exact same data. Due to the fact that I was worried about having everything on one drive, I just copied everything over to the second drive with just a simple "cd *".

I would like to create a RAID1 array out of them and was wondering how and if I can do that without having to move the data again. They are both formatted NTFS, and I need to keep them that way in case the file server ever dies...I would just want to move them to my main desktop and share them from there.

If that is not possible, is there something that will replicate the effects of RAID1, other then rsync?

---

### Post by xlr8ed on 2007-10-26
Bump

---

### Post by thirddeep on 2007-10-26
You can not build a RAID array without destroying what is there.

Back it up, build your RAID array, copy data over.

Thd.

---

