---
title: "[SOLVED] simple fstab-entry problem"
date: 2008-05-15
forum: General Help
---

### Post by stoppage on 2008-05-15
Could somebody please explain to me which entry I need to change in following fstab entry so that sda9 mounts automatically at startup (Feisty installation and sda9 is logical partition, manual mount o.k).

/dev/sda9				   /media/sda9    ext3         defaults,auto,umask=000,gid=46      0  1

---

### Post by chrisccoulson on 2008-05-15
I think the umask and gid are both invalid mount options for ext3 volumes. Try removing them.

---

### Post by ibuclaw on 2008-05-15
Remove umask=000 and gid=46. They are windows filesystem specific arguments.

If you want to set those permissions, set them while the partition is mounted. The filesystem will remember what everything is set to.
```

sudo chmod 777 /media/sda9 -R
sudo chgrp plugdev /media/sda9 -R

```

Also, don't forget, once you've saved the fstab file.
```
sudo mount -a
```

Regards
Iain

---

### Post by stoppage on 2008-05-15
Worked! Just one other thing.....how do I delete symbolic link sda9 on desktop please?

---

### Post by ibuclaw on 2008-05-16
Unmount the partition.

Change the mount point from "**/media/sda9**" to "**/mnt/sda9**" in your fstab entry.

Remount.

That should fix it.

If you want quick access to it in the future, you'll have to create a soft-symlink for all users who need it
[PHP]ln -s /mnt/sda9 ~/Desktop/sda9[/PHP]

Regards
Iain

---

### Post by stoppage on 2008-05-16
Obliged to you both

---

