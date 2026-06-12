---
title: "rsnapshot just backups the first interval"
date: 2008-05-12
forum: General Help
---

### Post by SoleroTG on 2008-05-12
Hi,

I'm using Ubuntu 8.04 and experience the following Problem:
[b]
rsnapshot just follows the first interval hourly and ignores the other ones daily, weekly, monthly and yearly.
[/b]
The rotation works fine:
eg. if I create a folder monthly.0 manually then every execution with the parameter monthly will lead to incrementing the number but not creating a backup anyway.

If I comment everything out except yearly then yearly works.
If I comment everything out except yearly and monthly then only monthly works etc

The execution is done via /etc/cron.d/rsnapshot

```

*/30  *         * * *           root    /usr/bin/rsnapshot -c /etc/rsnapshot-server.de.conf hourly
30 3            * * *           root    /usr/bin/rsnapshot -c /etc/rsnapshot-server.de.conf daily
0  3            * * 0           root    /usr/bin/rsnapshot -c /etc/rsnapshot-server.de.conf weekly
30 2            1 * *           root    /usr/bin/rsnapshot -c /etc/rsnapshot-server.de.conf monthly
0  2            1 1 *           root    /usr/bin/rsnapshot -c /etc/rsnapshot-server.de.conf yearly

```

diff /etc/rsnapshot.conf /etc/rsnapshot-server.de.conf gives
(/etc/rsnapshot.conf is in its original state, of course)

```

27c27
< snapshot_root /var/cache/rsnapshot/
---
> snapshot_root /var/cache/rsnapshot/server.de
106a107,112
> interval      hourly  48
> interval      daily   7
> interval      weekly  4
> interval      monthly 12
> interval      yearly  99
> 
129c135
< logfile               /var/log/rsnapshot.log
---
> logfile               /var/log/rsnapshot-server.de.log
136c142
< lockfile      /var/run/rsnapshot.pid
---
> lockfile      /var/run/rsnapshot-server.de.pid
168a175,181
> exclude               /var/cache
> exclude               /var/www/img
> exclude               /var/www/service/oliver/ftp_cache
> exclude               tmp/
> exclude               nobackup/
> exclude               /home/ftp
> 
202a216,223
> backup        root@server.de:/etc/                    server.de/
> backup        root@server.de:/var/www/                server.de/
> backup        root@server.de:/usr/lib/cgi-bin/        server.de/
> #backup       root@server.de:/var/log/                server.de/
> backup        root@server.de:/home/                   server.de/
> backup        root@server.de:/root/                   server.de/
> 
> 
204,206c225,227
< backup        /home/          localhost/
< backup        /etc/           localhost/
< backup        /usr/local/     localhost/
---
> #backup       /home/          localhost/
> #backup       /etc/           localhost/
> #backup       /usr/local/     localhost/


```

Yes, the hourly execution is crucial same for the other ones.
I noticed one time while I was debugging that hourly and daily worked both. I removed daily.* to check wether it recreates them which was not the case.

---

### Post by HermanAB on 2008-05-12
You may have better luck with rdiff-backup:
[http://www.nongnu.org/rdiff-backup/index.html](http://www.nongnu.org/rdiff-backup/index.html)

It does the same thing - only better.

Cheers,

Herman

---

### Post by SoleroTG on 2008-05-12
As far as I know rdiff-backup doesn't support grandfather-father-son backup without extra scripting. I also allow access to the backup by remounting it ro which would be quite difficult/impossible to do with rdiff-backup.
I started to really like the concept of hardlink incremental backups and I dont want to switch away from it.

Thanks anyway,
Solero

---

### Post by mlissner on 2008-07-18
I think I am having the same problem. With rsnapshot, when I run it from cron, it rotates the files, but doesn't do a backup. Looking at the log doesn't reveal anything interesting. I have noticed that if I run the script manually (as opposed to by cron), then it seems to work.

Any other folks have this problem?

---

### Post by SoleroTG on 2008-07-20
I've noticed something what kinda solves the problem. If rsnapshot is called via cron it ignores the first call but does its job on the next call. eg: the first weekly job is ignored, then all the daily jobs are done and if the weekly job is called again one week later rsnapshot starts the backup just like it should.
I expect this still to be a bug but this is a bug I can accept.

PS. I just checked through the backups and noticed whether the backups are ok, when I noticed that the backup for may is done but the one for june is missing. Don't know why. (No, the machine was not down it is up for 54 days)

Solero

---

### Post by mlissner on 2008-07-20
Sorry, I forgot to post back yesterday. I found a solution to this for me. Try installing mailx on the machine. Apparently cron needs that to function properly. 

Here's the thread: [http://ubuntuforums.org/showthread.php?t=500687&highlight=rsnapshot+crontab](http://ubuntuforums.org/showthread.php?t=500687&highlight=rsnapshot+crontab)

---

