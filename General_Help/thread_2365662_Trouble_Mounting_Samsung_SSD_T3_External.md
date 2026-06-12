---
title: "Trouble Mounting Samsung SSD T3 External"
date: 2017-07-09
forum: General Help
---

### Post by thomlignator on 2017-07-09
I have a new Zareason “Ultralap 5330” Notebook with Ubuntu 16.04 LST O/S.
I am trying mount a Samsung SSD T3 solid state external harddrive (Model MU-PT1T0B).
When I attached this external Harddrive to my Notebook’s USB port my Notebook gives the following message:	

[.Error mounting /dev/sdb1 at /media/mount/Samsung_T3: Command-line `mount -t "exfat"o"uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=
0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/mount/Samsung_T3"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'	]

Any ideas on how to mount it or should I ask for my money back? :confused:

---

### Post by jim_deadlock on 2017-07-12
It's not a hardware issue, there's probably nothing wrong with it. Try this:

```
sudo apt install exfat-utils exfat-fuse
```

If that doesn't work then you could try reformatting it with ext4 or ntfs.

---

