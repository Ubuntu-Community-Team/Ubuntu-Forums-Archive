---
title: "Help with formatting CRON job correctly"
date: 2015-04-16
forum: General Help
---

### Post by kosmokramer314 on 2015-04-16
```
0 1 * * * find /mnt/owncloud/mrblue/files/InstantUpload/$(date +%Y%m)*.jpg -type f -exec mv '{}' /mnt/owncloud/mrblue/files/InstantUpload/$(date +%Y-%m)/ \;
5 1 * * * find /mnt/owncloud/mrblue/files/InstantUpload/*.mp4 -type f -exec mv '{}' /mnt/owncloud/mrblue/files/InstantUpload/Movies/ \;
```



Above is my CRON job that doesn't work.  The commands work beautifully when executed manually, but when I checked the logs for why this wasn't working, I can see that CRON isn't interpreting correctly.  Logs show this as the command being passed:

```
 CMD (find /mnt/owncloud/mrblue/files/InstantUpload/$(date +)
```

Obviously I'm doing something wrong, but I can't seem the figure out how to update the CRON job to run correctly.  Any tips?

---

### Post by kosmokramer314 on 2015-04-16
need to escape the %....

---

### Post by spjackson on 2015-04-16
It used to be the case that the percent sign had special meaning in crontab (see [http://manpages.ubuntu.com/manpages/precise/man5/crontab.5.html](http://manpages.ubuntu.com/manpages/precise/man5/crontab.5.html)). However, I am not sure whether that is still the case. If in doubt, I would be inclined to put the complex command into a script and simply evoke the script from crontab.

---

### Post by Keith_Helms on 2015-04-17
I don't think that shell wildcards like * work in crontab.   Try changing your command to
```

/bin/bash  -c "find /mnt/owncloud/mrblue/files/InstantUpload/$(date +%Y%m)*.jpg  -type f -exec mv '{}' /mnt/owncloud/mrblue/files/InstantUpload/$(date  +%Y-%m)/ \;"

```

---

