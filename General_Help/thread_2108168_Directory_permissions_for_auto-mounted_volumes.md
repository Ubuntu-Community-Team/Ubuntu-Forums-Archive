---
title: "Directory permissions for auto-mounted volumes"
date: 2013-01-23
forum: General Help
---

### Post by feilb on 2013-01-23
I've been banging my head against the rock trying to figure this out and haven't been successful thus far.

I have a media server. It's running 12.10 and Plex Media Server. The media is all stored on a RAID array that Ubuntu has kindly automounted to /media/feilb/raid/.

Plex Media Server is run by the user "plex". This user is part of a group "plexgrp". I've made "plexgrp" the owning group for /media, /media/feilb, and /media/feilb/raid. Permissions on all said directories are 775. Owner is root.

No matter what I've tried, I cannot get the plex user to decent into /media/feilb, much less /media/feilb/raid

Any idea where I might start to tackle this one?

---

### Post by fdrake on 2013-01-23
can you post the output of :
```

groups plex
ls -al /media

```

---

### Post by feilb on 2013-01-24
```
total 12
drwxrwxr-x   3 root plexgrp 4096 Dec 18 22:26 .
drwxr-xr-x  25 root plexgrp 4096 Dec 19 07:44 ..
drwxrwxr-x+  3 root plexgrp 4096 Jan 23 22:04 feilb
```

Aha! You've triggered the solution!

I had never noticed the +!

After a quick read, I understand now that this indicates that the directory was governed by an Access Control List.

I used:

```
setfacl -m group:plexgrp:rwx
``` 

to add the group to the ACL and give it permissions. Thanks!

---

### Post by fdrake on 2013-01-24
> **feilb said:**
> ```
total 12
drwxrwxr-x   3 root plexgrp 4096 Dec 18 22:26 .
drwxr-xr-x  25 root plexgrp 4096 Dec 19 07:44 ..
drwxrwxr-x+  3 root plexgrp 4096 Jan 23 22:04 feilb
```

Aha! You've triggered the solution!

I had never noticed the +!

After a quick read, I understand now that this indicates that the directory was governed by an Access Control List.

I used:

```
setfacl -m group:plexgrp:rwx
``` 

to add the group to the ACL and give it permissions. Thanks!

glad to hear you fixed it! :D

---

