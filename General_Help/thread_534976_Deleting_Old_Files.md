---
title: "Deleting Old Files"
date: 2007-08-25
forum: General Help
---

### Post by daengbo on 2007-08-25
I have a laptop I have been using for a couple of years, and there are a lot of old files in the home directory. I do daily backups with sbackup, so they're all safe. I want to locate all the files which haven't been accessed in over 90 days and delete them, excluding any configuration files (files beginning with ".").

I suppose I could write a script for this, then use cron, but I'd prefer an out-of-the-box solution. Does anyone know one? I would love if there were a backup solution which did this automatically.

On a side note, although the description for sbackup says that it supposts file transfer to remote computers over Gnome VFS, it apparently does not. The remote computers aren't available in the location selection dialog.

---

### Post by daengbo on 2007-08-25
The answer is trivially easy with scripting:

 To remove (with prompting) all files starting in the /mydir directory that have not been accessed in over 100 days, enter:
find /mydir -atime +100 -ok rm {} \;

Thanks to [http://www.apluskb.com/scripts/In_Unix_what_is_answer483.html](http://www.apluskb.com/scripts/In_Unix_what_is_answer483.html)

---

### Post by daengbo on 2007-08-25
Apparently find can handle delete without using -exec as well.

find /path -atime +90 -delete

---

