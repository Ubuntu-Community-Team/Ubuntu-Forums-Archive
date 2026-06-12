---
title: "Can only mount windows share after REMOVING sticky bit from /bin/mount"
date: 2008-06-28
forum: General Help
---

### Post by Meson on 2008-06-28
Does this make sense?  To mount a windows share I need to:

```

sudo chmod u+s /sbin/mount.cifs
sudo chmod u-s /bin/mount
mount -t cifs -ouid=$USER,credentials=/win.cert,file_mode=0600,dir_mode=0700 //win/user /mnt/win/user

```

---

