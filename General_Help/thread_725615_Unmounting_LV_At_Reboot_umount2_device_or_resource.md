---
title: "Unmounting LV At Reboot: umount2: device or resource busy"
date: 2008-03-15
forum: General Help
---

### Post by presync on 2008-03-15
Hi There,

I recently resized two of my LVM volumes using:

```

umount /var
resize2fs /dev/volgrpname/var 5G
lvreduce -L -10G /dev/volgrpname/var
mount /dev/volgrpname/var /var

```

Now whenever i reboot the system the shutdown process complains that the /var mount is busy and that it was re-mounted as read-only:

```

umount2: device or resource busy
umount: /dev/volgrpname--var busy re-mounted as read only

```

Firstly is this something to worry about? i.e. data loss, and secondly how do i fix this error/warning.

Thanks!
Presync

*first post woohoo*

---

