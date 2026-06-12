---
title: "How do you alter etc/fstab to add and remove /dev"
date: 2007-02-28
forum: General Help
---

### Post by acwspoon on 2007-02-28
Hey, I'm completely new with Ubuntu but it really interests me.
I installed Ubuntu it and have a shared FAT32 hard drive between Windows and Ubuntu and I figured out how to mount it but every time I shutdown and restart the dev/sda2 is no longer there... this is what I did...

I created a /osshare directory and then mounted /dev/sda2 to there and now I have to do that every time I log into Ubuntu unless it's in hibernation or on stand by.  I know it has something to do with etc/fstab but i have no idea how to alter it.

I would really appreciate some help. Thanks!

---

### Post by Ramses de Norre on 2007-02-28
Add following line to /etc/fstab:
```
/dev/sda2    /osshare    vfat    defaults,auto,utf8,umask=0000,gid=46    0    2
```

---

### Post by acwspoon on 2007-02-28
Thanks,  I appreciate that it worked like a charm. :guitar:

---

