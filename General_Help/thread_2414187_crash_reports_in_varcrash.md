---
title: "crash reports in /var/crash"
date: 2019-03-06
forum: General Help
---

### Post by Skaperen on 2019-03-06
i have been deleting crash reports i have been getting in /var/crash because of all the message that keep popping up if i leave them there.  now i am archiving them in a directory i created called /var/crasharchive.  i just move each file from  /var/crash to /var/crasharchive with this script:
```

#!/usr/bin/env python3
# -*- coding: utf-8 -*-
from os import chdir,listdir,lstat,mkdir,rename,remove,rmdir
from time  import localtime,strftime,time as secs
chdir('/var')
for c in sorted(listdir('crash')):
    if c=='.lock':
        remove('crash/'+c)
        continue
    s=lstat('crash/'+c)
    t=strftime('%Y%m%d%H%M%S.',localtime(s.st_mtime))
    t+=str(s.st_mtime).split('.')[1]
    m='crasharchive/' if c[0]=='_' else '.junk/'
    rename('crash/'+c,m+t+c)
```

is there anything i should do with all these files, besides save them for the next generation of cyberarcheologists?

---

### Post by CatKiller on 2019-03-06
> **Skaperen said:**
> is there anything i should do with all these files?

Just delete them.

---

