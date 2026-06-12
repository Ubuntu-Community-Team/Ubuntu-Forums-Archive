---
title: "rdiff-backup of an rdiff-backup ?"
date: 2021-08-16
forum: General Help
---

### Post by freeflyjohn on 2021-08-16
I have used rdiff-backup to backup the files from my Mac Book Pro to an internal HDD in my server (Dell T30 PowerEdge running Ubuntu 20.01).

I then use rdiff-backup again to perform another backup of the Mac from the internal HDD on the server to an external USB HDD connected to the server.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288989&stc=1[/IMG]


This means the original rdiff-backup-data folder on the server, is then backed up again using rdiff-backup to the external USB HDD.

Is it ok to perform an rdiff-backup of another rdiff-backup ?

Or should I exclude the rdiff-backup-data folder when performing the rdiff-backup from the server to the external USB HDD ?

Or should I rsycn the rdiff-backup from the server to the external USB HDD ?

---

### Post by TheFu on 2021-08-16
You should use **rdiff-backup** for the first level only.
After that, use **rsync --delete** to the next location.
The *pull* and *push* seem fine, assuming the Mac cannot access the backup storage on the backup server.  That's an important part. Also, the backup server shouldn't be used in high risk activities, like email, web browsing, you know, end-user stuff.  It would be best if the backup server didn't have any GUI and ran Ubuntu Server to prevent all the GUI cruft too.  Cruft adds risks.

---

### Post by HermanAB on 2021-08-17
I’ve been pondering this.  Rdiff backup uses rsync and hard links.  If you run a backup of a backup, the result should be exactly the same as if you use straight up rsync to make a copy of the backup.

---

### Post by TheFu on 2021-08-17
rdiff-backup DOES NOT USE HARDLINKS!!!!!

---

### Post by HermanAB on 2021-08-17
Hmm, good catch, I was thinking of rsnapshot - gosh, the ‘diff’ should have given me a clue…  so yes, best to backup a rdiff backup with straight up rsync.

---

### Post by freeflyjohn on 2021-08-17
Thanks all, especially TheFu once again !

I will use rsync to mirror the rdiff-backup from the internal HDD in the server to the external USB HDD, I expect all the rdiff-backup versions will be retained on the external USB as it will simply be a mirror of the original rdiff-backup.

The Mac has access all the HDDs in the server via samba or ssh, but you're saying this is a bad thing, could you explain why ?

One of the HDDs in the server is called 'Storage' and at the root level I have folders for Media, Nextcloud, SVN and timeshift.  

At the same root level on that HDD is a folder called 'Backup', which is where the rdif-backup of my Mac is stored.

Is it just the case of setting permissions of this 'Backup' folder so that the Mac cannot access that folder ? Is there an easy way to do this ?

---

### Post by TheFu on 2021-08-17
> **freeflyjohn said:**
>  The Mac has access all the HDDs in the server via samba or ssh, but you're saying this is a bad thing, could you explain why ?
Malware on the Mac, especially crypto-locker stuff looks for networked storage to destroy.  That's WHY the "pull" in the backups is so critical. Definitely don't use samba or NFS or any other connection that doesn't require unlocking in credentials manually.

> **freeflyjohn said:**
> One of the HDDs in the server is called 'Storage' and at the root level I have folders for Media, Nextcloud, SVN and timeshift.
At the same root level on that HDD is a folder called 'Backup', which is where the rdif-backup of my Mac is stored. Well that's not good, especially if the access isn't read-only.  

IMHO, shares should be for specific needs, not "I'm lazy and share everything."

> **freeflyjohn said:**
> Is it just the case of setting permissions of this 'Backup' folder so that the Mac cannot access that folder ? Is there an easy way to do this ?
Someone running hacking tools seldom cares about root or file permissions if those permissions can be controlled by the system they've already cracked.

I share NFS storage as read-only to my nextcloud instance.  The NFS storage is located on a fairly secure system.  I would never, ever, use CIFS/samba between Unix systems for many reasons.  Use NFS where permissions aren't ignored like they are with Samba/CIFS. Also, do not override NFS defaults to allow the client root account full control. Too many Linux people do this. There are subtle reasons not to allow that. Until someone understands those subtle reasons, they aren't ready to accept the responsibility for why the default NOT to allow client-side root much access is highly important.

BTW, I have another thread post that was rejected due to overly aggressive filters. Someone is looking at it and I hope to post it later. It was about some rdiff-backup v.1.x limitations that can impact people, mainly running servers or with virtual machines. In v2.x (Ubuntu 20.04+), those were addressed.

---

### Post by TheFu on 2021-08-18
Got notified that the forums filter was fixed.  That msg I threatened ;) earlier:

> **HermanAB said:**
> Hmm, good catch, I was thinking of rsnapshot - gosh, the &#8216;diff&#8217; should have given me a clue&#8230;  so yes, best to backup a rdiff backup with straight up rsync.

rdiff-backup does some other things that rsync+hardlinks fail to do as well that directly relate to restore-ability.  I used rsync+hardlinks for about a decade, before being burned by the lack of metadata for each file being versioned too.  rdiff-backup handles that too.  

In older versions of rdiff-backup, it didn't handle sparse files nicely (without a patch), so that was an issue for a few of my needs. v2 of the program added sparse file support along with the change from python2 into python3.  [https://opensource.com/article/20/9/rdiff-backup-linux](https://opensource.com/article/20/9/rdiff-backup-linux)  Having a sparse file (2MB) explode during a backup (25GB) was a real problem on a few occasions. Before the rdiff-backup patch, the workaround was to exclude the file and use tar to convert that file into a sparse-friendly tgz for rdiff-backup to capture.  

```
# ll /opt/zimbra/data/ldap/mdb/db/
total 2276
drwxr-xr-x 2 zimbra zimbra        4096 Aug 17 03:24 ./
drwxr-xr-x 3 zimbra zimbra        4096 Apr 27  2019 ../
-rw------- 1 zimbra zimbra 24516902912 Aug 17 11:10 data.mdb
-rw-r----- 1 zimbra zimbra      377082 Aug 17 03:00 data.mdb.tgz
-rw------- 1 zimbra zimbra        8192 Aug 17 11:10 lock.mdb
```
data.mdb is a sparse file.
```
# du -k *
1892    data.mdb
372     data.mdb.tgz
4       lock.mdb
```
it isn't 24GB large. 

I say it all the time, rdiff-backup isn't perfect, but for my needs it is the best of the available options.

---

