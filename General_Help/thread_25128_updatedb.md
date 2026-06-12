---
title: "updatedb"
date: 2005-04-09
forum: General Help
---

### Post by amerigo5 on 2005-04-09
It is now a default behavior of 'updatedb' to automatically run in the background?

---

### Post by p!=f on 2005-04-09
[QUOTE=amerigo5]It is now a default behavior of 'updatedb' to automatically run in the background?[/QUOTE]
```

[~] > cat /etc/cron.daily/slocate
#! /bin/sh

if [ -x /usr/bin/slocate ]
then
        if [ -f /etc/updatedb.conf ]
        then
                /usr/bin/updatedb
        else
                /usr/bin/updatedb -f proc
        fi
        chown root.slocate /var/lib/slocate/slocate.db
fi

```
So yes, slocate runs from cron daily.

---

### Post by amerigo5 on 2005-04-09
Should I just delete the file to disable the 'updatedb' from running daily? Or is there any other way to disable it? Thanks.

---

### Post by void_false on 2005-04-09
Ah... Now I understand why sometimes cpu load is 99% while i´m doing nothing.  :-)

---

### Post by skoal on 2005-04-09
[QUOTE=amerigo5]Should I just delete the file to disable the 'updatedb' from running daily? Or is there any other way to disable it? Thanks.[/QUOTE]

I have no need to run any cron tasks, so I stop that service from starting by removing that entry in the appropriate rcX (runlevels).  I'm not in Ubuntu at the moment so I don't remember which runlevels I do that.  It may just be rcS?

Or you can just stop the cron daemon all together with '/etc/rc.d(?)/cron stop' (the rc.d syntax/path might be wrong again here, but you get the idea).

---

### Post by Xian on 2005-05-10
[QUOTE=p!=f]```

[~] > cat /etc/cron.daily/slocate
#! /bin/sh

if [ -x /usr/bin/slocate ]
then
        if [ -f /etc/updatedb.conf ]
        then
                /usr/bin/updatedb
        else
                /usr/bin/updatedb -f proc
        fi
        chown root.slocate /var/lib/slocate/slocate.db
fi

```
So yes, slocate runs from cron daily.[/QUOTE]
Is there a method by which it will only index certain partitions?
Can I say tell it not to index /ntfs if that is automounted upon boot?

---

### Post by Xerampelinae on 2005-05-10
[QUOTE=Xian]Is there a method by which it will only index certain partitions?
Can I say tell it not to index /ntfs if that is automounted upon boot?[/QUOTE]
 Simply removing the script from /etc/cron.daily (and perhaps weekly or anywhere else it appears) is sufficient to stop the behavior.  You probably don't want to disable cron entirely... I could be wrong.

To tell updatedb to exclude a certain directory, modify /etc/cron.daily so the call to updatedb includes the -e /ntfs option.  To see all the options to updatedb, use man updatedb.

Alternatively, and perhaps better... edit /etc/updatedb.conf and add /ntfs to the PRUNEPATHS="..." variable.  The file is commented a bit and should be straightforward to edit.

---

### Post by Xian on 2005-05-10
[QUOTE=Xerampelinae]Simply removing the script from /etc/cron.daily (and perhaps weekly or anywhere else it appears) is sufficient to stop the behavior.  You probably don't want to disable cron entirely... I could be wrong.

To tell updatedb to exclude a certain directory, modify /etc/cron.daily so the call to updatedb includes the -e /ntfs option.  To see all the options to updatedb, use man updatedb.

Alternatively, and perhaps better... edit /etc/updatedb.conf and add /ntfs to the PRUNEPATHS="..." variable.  The file is commented a bit and should be straightforward to edit.[/QUOTE]

Thanks! Just what I needed..... :)

---

