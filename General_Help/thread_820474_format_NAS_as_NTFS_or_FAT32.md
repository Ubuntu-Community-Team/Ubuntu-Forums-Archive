---
title: "format NAS as NTFS or FAT32"
date: 2008-06-06
forum: General Help
---

### Post by e24ohm on 2008-06-06
Forum,

Not sure where this post would go, so I am posting it here – I hope this is not out of topic.

I was able to personally get an older Dell PowerVault from one of my clients, and being new to Linux I wanted to know the best solution or deployment for formatting the array.

Should I format the drive(s) in NTFS or FAT32?

Has anyone seen issue with NTFS partitions and files becoming corrupted in Linux?

Suggestions for/with deployment and solution are welcomed.

Thank you,

---

### Post by e24ohm on 2008-06-06
Forgot to mention, that win. and linux based machines will be accessing the NAS. No MAC...

---

### Post by danwood76 on 2008-06-09
I would choose a native linux format.
EXT3 is the default for the moment.

When you share with the windows machines you would use samba and so it doesnt matter on the filesystem type, and the linux boxes would use NFS (or samba if youy like)
The filesystem should be a natyive linux one for speed and stability, there is no need to use a windows format like NTFS unless a windows box will be accessing it directly.

---

### Post by e24ohm on 2008-07-19
Understand. Thank you.

---

