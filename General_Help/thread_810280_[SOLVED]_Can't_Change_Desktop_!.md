---
title: "[SOLVED] Can't Change Desktop !"
date: 2008-05-28
forum: General Help
---

### Post by drsox1899 on 2008-05-28
I'm dual booting WinXp and U7.10 and have 2 drives.

On my U7.10 desktop are icons of the WinXp partitions that I don't use at all in U7.10.  
I can't get rid of them (unnecessary clutter) as I have to be root to delete the icons (unmount the volumes)

How do I do this without deleting the volumes ?

Thanks

---

### Post by happy-and-lost on 2008-05-28
Comment out the volumes in /etc/fstab to stop them mounting at boot.

---

### Post by pedro_orange on 2008-05-28
```
sudo umount /dev/hdb1
```

Or whatever the filesystem is mounted as.(Replace the /hdb1 to whatever you need)

---

