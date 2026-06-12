---
title: "SBackup exclude list (sbackup 0.10.4 + Gutsy)"
date: 2008-04-16
forum: General Help
---

### Post by supermarchino on 2008-04-16
Despite I only have this
```

[exclude]
maxsize = -1

```
In proper section of my /etc/sbackup.conf file, SBackup does not make any backup of some file types, from this list (from 'excludes' file in backup's directory):
```

(lp1
S'\\.mp3'
p2
aS'\\.avi'
p3
aS'\\.mpeg'
p4
aS'\\.mkv'
p5
aS'\\.ogg'
p6
aS'\\.iso'
p7
a.

```

Is it a bug? A default setting which can be overridden?

---

