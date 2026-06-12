---
title: "How do you backup over the network with Luckybackup?"
date: 2015-09-23
forum: General Help
---

### Post by 777funk on 2015-09-23
See title. Thanks.

---

### Post by cmcanulty on 2015-10-04
I also need this

---

### Post by bengy103 on 2015-11-20
yeah, I'm stuck on this too.

---

### Post by cariboo on 2015-11-20
It looks like Luckybackup uses whatever protocols are available to the file manager. The documentation suggest you us smb/cifs or nfs to backup to a remote system eg:

```
smb://server/path to directory
```

The other suggestion is to mount the remote directory via /etc/fstab and back up to the mount point eg:

```
/media/directory
```

---

