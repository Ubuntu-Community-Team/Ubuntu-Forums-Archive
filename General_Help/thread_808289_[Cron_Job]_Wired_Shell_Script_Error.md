---
title: "[Cron Job] Wired Shell Script Error"
date: 2008-05-26
forum: General Help
---

### Post by untubu on 2008-05-26
Today I just try to configure a cron job and facing a wired error.   I wrote a shell script and try to run it from cron. My script is look like this............

```
#!/bin/sh
folder='/home/user/test';

if [ Condition ]
then
 chmod ugo+rwx -R $folder
else
chmod 577 -R $folder

fi

```

and the error look like this

```
chmod: cannot access `-R': No such file or directory
```

OS: Ubuntu Desktop 8.04
And using Gnome Schedule for manage cron job.

Script run fine when I run it from shell. Any one have any Idea??:confused::confused:

---

### Post by bingoUV on 2008-05-26
give -R option before other switches. Like 
```

chmod -R ugo+rwx *.txt

```

---

### Post by Gunman1982 on 2008-05-26
Try to use absolute paths for chmod '/bin/chmod' since the PATH variable isn't set when the script is run by cron.

---

### Post by untubu on 2008-05-26
Thanx bingoUV and Gunman1982. 

but bingoUV's suggestion is works for me. 

I am curious what is the reason behind this??

---

