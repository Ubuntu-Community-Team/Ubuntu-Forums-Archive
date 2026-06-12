---
title: "Can't access hard drive after changing its name"
date: 2013-07-02
forum: General Help
---

### Post by whitesmith on 2013-07-02
Hello *

I'm new to Ubuntu and Linux. This morning I changed the name of my hard drive from SLA310 to SLA360 (using the Disks utility) and now I have no write privileges. I cannot, for example, create a folder on this hard drive. A friend mentioned something about fstab, but his explanation left me in the dark. Can anyone please explain what needs to be done to allow access? The present owner of the drive appears to be root.

---

### Post by The Cog on 2013-07-02
Is this an internal disk, or a removable one? 
How did you used to gain access?

With the disk in place, can you run these commands and post the output please:
```

sudo fdisk -l
sudo blkid
cat /etc fstab
```

---

