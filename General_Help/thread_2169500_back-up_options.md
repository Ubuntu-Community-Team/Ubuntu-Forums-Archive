---
title: "back-up options"
date: 2013-08-22
forum: General Help
---

### Post by my3X8wP on 2013-08-22
I have an old laptop with Ubuntu 12.04 installed, running as a server for all my pictures. 
While this solution works just fine, I haven't found a satisfactory solution for backing up these photos.

What I want to do, is to have these pictures backed up at a weekly schedule to either a USB drive or a cloud service (Box)

I do not want to create a back-up file / snapshot - I want to have the backed up pictures organized the same way as they are on the server (so they can be easily accessed if necessary).

Sure, I can drag and drop once a week, but I want to automate this process.

Is this possible?

---

### Post by HereInOz on 2013-08-22
You can use rsync to do the backup.  It is an excellent tool and properly configured it will only back up files which are new or which have changed, leaving the rest as they are.

Then you can set up a cron job to schedule the copy, or just create a simple script file which you run every Sunday morning or such.  This is the way I do it, anyway.

---

### Post by SeijiSensei on 2013-08-22
Create a file as root with sudo like this:

```

#!/bin/bash

/usr/bin/rsync -av /path/to/your/pictures [user@]server:/path/to/backup/directory


```

If you are not using a remote server, you can replace the target with a path to an external drive.  Suppose you have an external USB drive mounted as /media/external with a directory on it called backup.  Then use this syntax instead:

```
/usr/bin/rsync -av /path/to/your/pictures /media/external/backup
```

Let's suppose you called this file /root/backup.  Make sure root can execute the file with the command:

```
chmod u+x /root/backup
```

then go to the directory /etc/cron.weekly and use this command:

```
sudo ln -s /root/backup
```

That will create a "symbolic link," or "symlink," to the file.  The backup will be run early Sunday mornings.

---

