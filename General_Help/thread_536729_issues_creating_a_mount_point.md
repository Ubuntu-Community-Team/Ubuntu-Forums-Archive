---
title: "issues creating a mount point"
date: 2007-08-28
forum: General Help
---

### Post by fearevilleet on 2007-08-28
Hi

I am trying to create a mount point for an external drive I have. The drive is mounted at /media/disk and is working fine. I added the following line to my fstab 

```
/media/disk /home/evilleet/externaldrive ext3 defaults  0 0
```

and made sure the mount point was created. When I go to mount the drive using mount -a I get the error

mount: /media/disk is not a block device

Any idea what i am doing wrong?

---

### Post by tzulberti on 2007-08-28
Instead of /media/disk you should put the partition that belongs to the external drive. It should be /dev/XXX##, you could check it with "less /proc/partitions", once that the external drive is mounted.

I hope it helps.

---

### Post by vanadium on 2007-08-28
Indeed, you are not creating a mount point because you already have it : /media/disk is the mount point. It is an empty folder under the /media directory.

What you want is add the drive to fstab so that it mounts automatically during startup. FOR AN EXTERNAL DRIVE, I DON'T RECOMMEND THAT. An external drive can be unplugged and plugged in. Normally, Ubuntu should mount the drive automatically when it is connected. There is no need for you to fiddle with /etc/fstab.

Perhaps you should describe more precisely what problem, if any (you state it is working fine)  you have with the drive.

---

