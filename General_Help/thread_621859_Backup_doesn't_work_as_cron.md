---
title: "Backup doesn't work as cron"
date: 2007-11-24
forum: General Help
---

### Post by JiminyJones on 2007-11-24
I have a simple backup script:

```
#!/bin/bash

rsync -r -v --progress --delete --exclude Cache/ /home/sharpie/.mozilla/firefox/ /media/sdb1/Linux/Backup/Firefox/
rsync -r -v --progress --delete --ignore-existing --exclude *.ini /media/sda4/Music/ /media/sdb1/Shared/Music/
rsync -r -v --progress --delete --ignore-existing /home/sharpie/Pictures/ /media/sdb1/Shared/Pictures/
rsync -r -v --progress --delete --ignore-existing /media/sda4/GP\ Songs/ /media/sdb1/Shared/GP\ Songs/
rsync -r -v --progress --delete /home/sharpie/Scripts/ /media/sdb1/Linux/Backup/Scripts/
```

When i run this script myself (either with sudo or without it) it works, but when i let crontab run it, it skips the files inside sub-directories in my firefox profile (such as files inside add-on dirs).
This problem, btw, happens when the Firefox folder (in the backup HDD) doesn't exist when crontab runs the script (and, again, when i run the script myself it successfully copies all folders and files).

What can I do to fix it?

EDIT: btw, here's my crontab:
```

# m h  dom mon dow   command
00 21 * * * /home/sharpie/Scripts/bkup.sh
```

---

