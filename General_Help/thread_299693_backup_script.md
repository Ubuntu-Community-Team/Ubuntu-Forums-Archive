---
title: "backup script"
date: 2006-11-14
forum: General Help
---

### Post by SKF on 2006-11-14
Good day,

i have a backup scripts that i run daily to backup Daily changed files, when i run  command from command line it works but from script it fails

backup script:
```

#!/bin/bash
days=1
DATE=`/bin/date +%Y.%m.%d`
/bin/mount /dev/sdb1 /mnt/backup
/bin/touch /mnt/backup/filechangedon$DATE
/usr/bin/find /backupdir -mtime -$days  -type f -print > /mnt/backup/filechangedon$DATE
/bin/touch /mnt/backup/backuplog/backuplog$DATE.log
/usr/bin/find /mnt/marsd -mtime -$days  -type f -print | xargs /bin/tar cvf /mnt/backup/backup.$DATE.tar -T - >/mnt/backup/backuplog/backuplog$DATE.log

```

some how this script is not working can some one tell me where i am going wrong?

Thank you

SKF

---

### Post by aysiu on 2006-11-14
Have you considered using *rdiff-backup*?

[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

---

### Post by SKF on 2006-11-14
every one points to rdiff and rsync, it will take me another day just to figure this out.

I started reading and looks like you can use cp to retore :)

Thanks alot.

SKF

---

