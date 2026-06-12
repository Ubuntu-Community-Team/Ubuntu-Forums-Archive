---
title: "[SOLVED] Mount?"
date: 2008-05-12
forum: General Help
---

### Post by pbeesley on 2008-05-12
Can someone please help me :(

I don't understand mount points? Is there a real easy guide somewhere?

I'm trying to "backup" :---) a DVD and the software is asking for the mount point of my DVD rom drive. Is there a terminal command to list this?

Thanks

---

### Post by kesman on 2008-05-12
You can view all your mounted partitions, including cd-rom drives with
```

cat /etc/fstab

```
there you'll see where each device is mounted. I think your cd/dvd-rom is mounted in /media/cdrom

---

### Post by pbeesley on 2008-05-12
Thanks :) Quick Reply

---

### Post by WakkiTabakki on 2008-05-12
The /etc/fstab file contains the static mounts of your system. Those aren't necessarily mounted...

You can get a list of what currently is mounted by running this command in a terminal
```
mount
```

/N

---

