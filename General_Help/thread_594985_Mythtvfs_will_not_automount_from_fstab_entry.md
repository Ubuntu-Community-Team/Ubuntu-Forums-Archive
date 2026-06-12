---
title: "Mythtvfs will not automount from fstab entry"
date: 2007-10-28
forum: General Help
---

### Post by dmfrey on 2007-10-28
I have two entries my fstab that I would like mounted when the machine starts up.  One is an nfs mount to a server which holds music and photos.  The second is a mythtvfs mount to a location local to the machine.

Here is the entry:
```
mythtvfs#/var/lib/mythtv/recordings  /media/mythtvfs fuse  auto,user,ro,host=mythcenter,allow_other,nonempty 0 0
```

The nfs mount mounts as it should at boot time, however, the mythtvfs mount does not and I have to manually issue the mount command whenever I want access to that mount.

Does anyone have any suggestions on how to allow this mount to happen automatically?  I have seen other posts about creating a script to do this, but I was thinking that this should be able to happen without any other scripts.

Thanks,
Dan

---

