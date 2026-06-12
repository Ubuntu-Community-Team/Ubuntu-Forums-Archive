---
title: "Backup script produces weird behaviour"
date: 2017-01-08
forum: General Help
---

### Post by chris137 on 2017-01-08
Hi,
today my server got blocked for the second time by my hoster already due to the suspicion I'd use the server for ddos.
After I've convinced him again that this is just my backup server he unblocked the server again.

As I don't want to lose the server eventually and I myself have no idea where the issue is I ask for help here.
I use a - what I thought was a simple scp-based bash-backup script to pull data from the server in question to my backup server. The relevant lines are these:
```
#!/bin/bash
ssh board "mysqldump -u username -v database -ppassword > /some/path/here/backup.sql"
scp -r board:/some/path/here/* /local/backup/dir
ssh board "rm /some/path/here/backup.sql"
scp -r board:/other/path/* /other/backup/dir
```
Above script is run every 6 hours.
First scp covers almost 2GB in about 4760 files.
Second scp copies around 80MB in just over 1600 files.

The hoster now confronts me with his logs which show the following:
```
2017-01-07 18:05:52.707610 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 2966 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.707653 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 2966 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.707680 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 4414 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.707719 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 5862 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.707773 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 4414 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.707807 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 5862 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.707854 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 4414 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.707904 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 5862 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.707964 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 7310 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708029 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 5862 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708077 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 7310 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708138 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 7310 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708221 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 8758 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708279 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 7310 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708357 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 8758 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708433 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 8758 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708554 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 8758 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708618 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 11654 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708674 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 10206 bytes ttl: 0 sample ratio: 1
2017-01-07 18:05:52.708764 server:sshport > backupserver:remoteport protocol: tcp flags: ack frag: 0 packets: 1 size: 2966 bytes ttl: 0 sample ratio: 1
```
I'm not quite sure how big ACK packets can get but they seem rather large to me. Why is that?

---

### Post by TheFu on 2017-01-08
Uh ... use **rsync -avz source target** instead of scp.  Why send all the files when you really only want changed data?

Or it would be better to use **rdiff-backup** (which is based on rsync) to get versions of the backups.  The current backup looks like a mirror and prior versions are gzip-diffs.  Very efficient both in storage AND in network bandwidth.  If only 5MB of data changes, then only 5MB would be transferred.

Of course, the first time the backup is run, all the data has to be transferred.

Plus, but rsync and rdiff-backup use ssh automatically and honor the ~/.ssh/config file, which makes things easier.

Don't know anything about those logs. Sorry.

---

### Post by Habitual on 2017-01-09
Some of that code *looks* funny to me. ;)
As I'm sure my code look hilarious to some folks...
ssh board "mysqldump ..." seems inefficient (not saying it is) but I'd like to see the complete life of backup.sql
```
mysqldump -h -u<user> -p <pass> db > /path/to/backup.sql
```
is what I use

I think the "hoster" is actually doing you a solid by inquiring.
and moving every thing, every time, naw!
Rsync only the changed stuff and a fresh mysqldump in there also.

[Simple, Secure Backups for Linux with rsync]("http://rsync.net/resources/howto/rsync.html")
I'd use **rsync** as it would look a lot less (IMO) like a DDoS.
Chances are, your host providerer uses it also. 
or stick an email to your "guy" with ```
mail -s "Backup Complete" < dude@hoster.co
```
in your script. Just kidding, or am I? Mail "someone" or log "something". <wink><nudge>

Your "guy" (that's his nomenclature now) should easily be able to tell the difference on the wire
between rsync traffic and binary data launched at a receiving host.

Just another Host Providers point of view.

Good Luck.

---

### Post by chris137 on 2017-01-11
Thanks for your answers!
You're both right and helped me a bit, even though you didn't really answer the question :D

I'll check out rdiff-backup as I do want several versions to choose from in case of needing a backup.

The script (above is just an excerpt) grew over time and I've used remote commands all the time.
Mysqldump's remote function just didn't occur to me.
However, this would probably create even more logs like the above and is better done on the remote host and only then copied using e.g. rdiff-backup (or am I wrong?)

It would be great if someone would be able to tell me how a simple 2GB scp-filetransfer looks like a DDoS to my hoster.

---

### Post by TheFu on 2017-01-11
Grabbing 6K files .... that could look like a DDOS when only 5 of them actually changed.  

Why not put a bandwidth limit on the transfers?  I know rsync can do it. Would have to check the manpages for the option in scp.  

Sucking all the bandwidth on a shared host for 1-2 minutes is rude, assuming both sides of the connection have a bunch of bandwidth. If only 1-side does, then the throttling should be automatic.  If 1-side has poor connectivity, the fast restarting TCP connections _could_ appear as a DDOS.

But I'm inclined to agree with you. If they want the connections throttled, then their network equipment should do it.  OTOH, most ToS say you have to be a nice neighbor on shared hosting.  If you own both sides of the connection, I don't see why they'd care.

---

### Post by chris137 on 2017-01-11
Well, and what if my actual folder size would be larger and rsync grabs the same amount of data as I do right now - because many files actually did change?
This would then produce the same effect => Lots of small files being transferred quickly.

---

