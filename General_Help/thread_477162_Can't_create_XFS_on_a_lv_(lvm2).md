---
title: "Can't create XFS on a lv (lvm2)"
date: 2007-06-18
forum: General Help
---

### Post by bpont on 2007-06-18
```
sudo mkfs.xfs -f /dev/foo/foo
dm_task_set_name: Device /dev/mapper/foo-foo not found
Command failed
```
```

sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/foo/foo
  VG Name                home
  LV UUID                3xVX00-LGQi-YSOD-OoG8-OnGh-mSLI-1rRSUE
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                92.00 GB
  Current LE             23552
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:0
```

```
sudo ls -l /dev/foo/foo
lrwxrwxrwx 1 root root 21 2007-06-17 22:53 /dev/foo/foo -> /dev/mapper/foo-foo
```

---

### Post by kuja on 2007-06-19
Does it make any different if you run mkfs.xfs on /dev/mapper/foo-foo instead? Bearing in mind that /dev/foo/foo is just a symbolic link to that.

---

