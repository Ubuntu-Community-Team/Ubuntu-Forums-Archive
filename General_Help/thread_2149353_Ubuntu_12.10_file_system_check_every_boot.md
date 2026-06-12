---
title: "Ubuntu 12.10 file system check every boot"
date: 2013-05-28
forum: General Help
---

### Post by drfreq on 2013-05-28
hello,  i have used a command which i cant remember anymore, to force a file system check at next boot... but since then, ubuntu performes a file system check everytime on boot...  i have ubuntu 12.10 64 and a crypt homefolder...   thanks for any help

---

### Post by dino99 on 2013-05-28
usually fsck is ran either when the counter has reached the limit, or when the system detect lost inodes due to hardware errors.
so you might glance closely at your logs : /var/log/dmesg , and also upstart/ureadahead logs  and .xsession-errors

---

### Post by drfreq on 2013-05-28
log file only shows some warnings about acpi driver (probably thinkpad driver hmm...), the second file dont exist, and the .xerrors shows some errors about icons or fail startup webapplications and stuff... but nothing what might relates to harddrive failure

well, as i have said, i used a command, i think ist was ```
sudo touch /forcefsck
``` and since then ubuntu performes the fschk every time, it also could have been a diffrent command not sure anymore...

i have tried also this one ```
tune2fs -C 30 /dev/sdXY
``` here i get the error cant find superblock... doesent matter which i use sda1 to 5.. maybe because it is crypt? anyways, there schould be a way to turn of the fschk?

---

### Post by drfreq on 2013-05-28
i have tried 

```
sudo dumpe2fs -h /dev/sda1
```

Result:

```

Filesystem state:         not clean
Errors behavior:          Continue

```

---

### Post by Rebelli0us on 2013-05-28
You may have "sudo touch /forcefsck" in Startup Applications. I do because sometimes I go many weeks between reboots. It only takes a few seconds to check several disks so it's not a big deal.

---

### Post by Charlotte18 on 2013-05-28
You may be able to stop the check by setting the fsck option in fstab to 0.

---

