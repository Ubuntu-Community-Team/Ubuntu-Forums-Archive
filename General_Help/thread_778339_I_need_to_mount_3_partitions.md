---
title: "I need to mount 3 partitions"
date: 2008-05-02
forum: General Help
---

### Post by onesojourner on 2008-05-02
I have 3 partitions I need to mount. 2 ntfs and on ext 3. Can some one walk me through the steps of doin this? I need to have sda2 mounted as windows, sda4 mounted as storage and sdb1 mounted as storage 2 and I need them to be mounted to media and the desktop at start up.

---

### Post by logos34 on 2008-05-02
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

create mount points /media/storage, /media/storage2, etc. and add them to /etc/fstab so they automount at startup. Show Desktop icons option should be enabled in nautilus:

Press Alt + F2 and type

gconf-editor

>Apps>nautilus>desktop>volumes_visible

---

### Post by onesojourner on 2008-05-02
thanks that was just what I needed.

---

