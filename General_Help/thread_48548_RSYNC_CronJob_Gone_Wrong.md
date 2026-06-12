---
title: "RSYNC CronJob Gone Wrong"
date: 2005-07-12
forum: General Help
---

### Post by kvidell on 2005-07-12
This is what I have right now... It's supposed to backup two directories to an nfs mounted backup drive on a network.. backup house box thinger. This part works fine..
It's supposed to do this once every five hours and e-mail me upon succesful completion... however... it does it once a minute for 62 minutes every 2 hours. And e-mails me upon success... every time.```
#!/bin/sh

TESTFILE=/bout/.nfstest
LOCKFILE=/bout/.backup_lock
MAILTO=xxxxxxx@xxxxxxxxx.tld

if [ -f ${TESTFILE} ]; then
        if [ -f ${LOCKFILE} ]; then
                mail -s "Backup failed: LOCKFILE exists" $MAILTO </dev/null
        else
                touch ${LOCKFILE}
                rsync --delete -av /data/public /home /bout/ >/dev/null 2>&1
                mail -s "Backup succeeded" $MAILTO </dev/null
                rm -f ${LOCKFILE}
        fi
else
        mail -s "Backup NFS directory unavailable" $MAILTO </dev/null
fi
``````
* */5 * * * /root/rsync-script.sh >/dev/null 2>&1
```Any ideas?
- Kev

---

### Post by twowheeler on 2005-07-13
[QUOTE=kvidell]
It's supposed to do this once every five hours and e-mail me upon succesful completion... however... it does it once a minute for 62 minutes every 2 hours. And e-mails me upon success... every time.

<snip>

```
* */5 * * * /root/rsync-script.sh >/dev/null 2>&1
```Any ideas?
- Kev[/QUOTE]
Sure.  The first field is saying to run the script every minute, and the second field says to do it once every fifth hour.  You are getting a goofy result as cron tries to make sense of this.  Try:
```
0 */5 * * * /root/rsync-script.sh >/dev/null 2>&1
```
That would mean run it at the top of the hour, once every fifth hour.

Cheers.

---

### Post by kvidell on 2005-07-13
[QUOTE=twowheeler][...][/QUOTE]Ah ha! Thank you _very_ much :-D
My poor inbox was getting confused ^.-

We'll see if this fixes it (it should, it makes much more sense logically)
- Kev

---

### Post by kvidell on 2005-07-13
Much better :) Thank you.
- Kev

---

