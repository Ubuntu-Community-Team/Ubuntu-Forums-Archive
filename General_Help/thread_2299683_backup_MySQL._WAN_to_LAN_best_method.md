---
title: "backup MySQL. WAN to LAN best method?"
date: 2015-10-20
forum: General Help
---

### Post by Drenriza on 2015-10-20
Hey all

I am currently thinking about how to best make a MySQL backup from a server on the WAN to server on the LAN (both behind firewalls).
And would like to ask the community what you think of my thoughts / solution so far, and what your own are.

My initial thoughts

[LIST]
[*]Create a WAN and LAN backup user with no added groups or permissions. 
[*]Create a backup RSA key pair (WAN server) no passphrase. 
[*]Setup (forward / redirect) FW (LAN) SSH rule
[LIST]
[*]iptables -t nat -A PREROUTING -p tcp --sport [port-other-than-22] -j DNAT --to-destination [LAN server ip]:22 
[/LIST]
  
[*]Copy RSA public key to local server
[LIST]
[*]ssh-copy-id -p [port] -i ~/[WAN-BACKUP-USER]/.ssh/backup.key.pub [LAN-BACKUP-USER]@LAN-FW-IP 
[/LIST]
  
[*]AppArmor
[LIST]
[*]Give the LAN backup user permission to rw the backup directory (placed outside of the users home directory like /srv/mountpoint) 
[*]Give the WAN backup user permission to dump MySQL and nothing else. 
[/LIST]
  
[*]Stream MySQL dump
[LIST]
[*]mysqldump ${mysqlOptions} -u $SQLUSER -p$SQLPASS $i | $NICE gzip -c | ssh ${remoteUser}@${LAN-FW-IP} "cat >> /backup/path/dump.sql.gz" 
[/LIST]
    
[/LIST]

Current problems (that i see) in this solution so far
If an MySQL dump is several GB's in size and fail mid way, the backup would need to start over.
Is their a way for SSH or another tool to calculate
[LIST]
[*]What has been streamed 
[*]What needs to be streamed 
[*]Streams rest 
[/LIST]
Or is it straight up just a do-over?

I know rsync has this feature with data files but don't know if their is an equivalent for streams.

The reason for a stream versus doing a local dump and rsync it, is if a MySQL dump is bigger than the local storage available.

Thanks to all in advance who takes the time to read and or reply.
Kind regards.

---

### Post by Lars Noodén on 2015-10-20
The appending redirect >> probably should be a plain redirect > because adding to a gzipped file will just make garbage.  

> **Drenriza said:**
> 
If an MySQL dump is several GB's in size and fail mid way, the backup would need to start over.
Is their a way for SSH or another tool to calculate
[LIST]
[*]What has been streamed 
[*]What needs to be streamed 
[*]Streams rest 
[/LIST]
Or is it straight up just a do-over?

I know rsync has this feature with data files but don't know if their is an equivalent for streams.

The reason for a stream versus doing a local dump and rsync it, is if a MySQL dump is bigger than the local storage available.


The pipes you chose above are also close to what I would try.  But if the dump is bigger than the local storage then, in the event of an interruption, you are stuck starting the transfer over, as far as I know, a do-over as you call it.  The ideal, I think, would be if there is space and then dump to disk and then use 'rsync' for the transfer.  

I'm wondering if 'split' might be worked in somehow, but if you don't save the dump to disk then the content will likely be different each time anyway and not able to be resumed.

---

### Post by Drenriza on 2015-10-21
Thanks for the reply Lars.

> The appending redirect >> probably should be a plain redirect >  because adding to a gzipped file will just make garbage.
What do you mean with garbage? Do you might have a small example.

I used the >> instead of > after looking through the gzip doc, which under advanced usage says
> 
ADVANCED USAGE
       Multiple compressed files can be concatenated. In this case, gunzip will extract all members at once. For example:

             gzip -c file1  > foo.gz
             gzip -c file2 >> foo.gz


But if you have experience with this and garbage i would very much like to hear about it.

> but if you don't save the dump to disk then the content will likely be different each time anyway and not able to be resumed.
That is most likely. I was thinking (hoping) that their might was a smart feature / script / other that could determine if their was changes from a failed dump and what would be needed to be downloaded to get the full backup.

Something like diffing the difference between the dump that failed and the mysql dump in progress and just take differences :)

---

### Post by Lars Noodén on 2015-10-21
> **Drenriza said:**
> What do you mean with garbage? Do you might have a small example.

I used the >> instead of > after looking through the gzip doc, which under advanced usage says


But if you have experience with this and garbage i would very much like to hear about it.


Yes, gzipped files can be concatenated.  However, I was thinking of dealing with the SQL dump specifically.  I could be wrong, I guess you'd have to try and see what really happens with the dump and concatenating partial, gzipped dumps.  

 > **Drenriza said:**
> Something like diffing the difference between the dump that failed and the mysql dump in progress and just take differences 

If the database is being used, then it will be changing.  Since the dump is a snapshot as it was at a particular time, if you do a new dump, you are getting a new snapshot.  So I'm not sure if it is even theoretically possible, at least in that way.  Depending on the database structure, you might be able to transfer one table at a time, but with records that exist across multiple tables, that is not possible.

There used to be a mysqlbackup program that claimed to do incremental backups but I've not used it.

---

### Post by btindie on 2015-10-21
You might want to take a look at [https://launchpad.net/mydumper](https://launchpad.net/mydumper) as an alternative way of backing up your MySQL database.

---

### Post by Lars Noodén on 2015-10-22
Another option might be to use the built-in [replication](https://dev.mysql.com/doc/refman/5.7/en/replication.html) capabilities.  You'd have to have MySQL running on that second machine but there's no reason it would have to be available to anyone or anything.

---

### Post by Drenriza on 2015-10-22
> **Lars Noodén said:**
> Another option might be to use the built-in [replication]("https://dev.mysql.com/doc/refman/5.7/en/replication.html") capabilities.  You'd have to have MySQL running on that second machine but there's no reason it would have to be available to anyone or anything.

Thats an good idea.

But if you with that method how would MySQL2 (backup) react if data is deleted by mistake on MySQL1.
I suppose it would be replicated to MySQL2 and than loosing the backed up data.

Another solution also could be using ZFS (how good has ZFS on ubuntu become?).
WIth ZFS we can create a zpool and mount it to (for example) /mysql1
Than for keeping downtime low we can create a second zpool called /mysqlbackup

Make a snapshop from /mysql1 to /mysqlbackup and than backup /mysqlbackup.
Now i am not 100% sure BUT! zfs has a built in tool for backing up a zpool from one zfs machine to another
```
zfs send poolname/filesystem@snapname | ssh user@remote "zfs recv"
```
AND maybe this tool have some rsync features, that if the connection goes down in transfer you can pick up where you left of.

The awesome thing about the snapshot is that it only takes up disk space when changes happen.
So when you create any snapshot it initial takes up 0 MB's and as changes occure it takes more and more place.
But if u create a backup and than delete the snapshot all is good for low storage systems (low secondary storage).

> You might want to take a look at [https://launchpad.net/mydumper](https://launchpad.net/mydumper) as an alternative way of backing up your MySQL database.
Awesome thanks will take a look at it

---

### Post by lukeiamyourfather on 2015-10-22
> **Drenriza said:**
> Another solution also could be using ZFS (how good has ZFS on ubuntu become?).

In a nutshell, pretty good. I've been using it now for a few years in a production environment with several machines and hundreds of terabytes of data. Use ZFS on Linux which is a kernel port of ZFS, not the old FUSE implementation which was slow and not feature complete.

[http://zfsonlinux.org/](http://zfsonlinux.org/)
[http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf](http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf)

> **Drenriza said:**
> Now i am not 100% sure BUT! zfs has a built in tool for backing up a zpool from one zfs machine to another
```
zfs send poolname/filesystem@snapname | ssh user@remote "zfs recv"
```
AND maybe this tool have some rsync features, that if the connection goes down in transfer you can pick up where you left of.

Snapshots can be sent incrementally like rsync. Last time I tried it interrupted transfers couldn't be resumed but that's changing so you can resume. I'm not sure if it has made it's way into ZFS on Linux yet but it will soon if it hasn't. If it's not in ZFS on Linux yet you can wrap the connection in something else that can resume after interruption. There are several shell scripts floating around to do this but I haven't tried any of them.

[https://github.com/illumos/illumos-gate/commit/9c3fd1216fa7fb02cfbc78a2518a686d54b48ab8](https://github.com/illumos/illumos-gate/commit/9c3fd1216fa7fb02cfbc78a2518a686d54b48ab8)

---

### Post by Lars Noodén on 2015-10-23
> **Drenriza said:**
> 
But if you with that method how would MySQL2 (backup) react if data is deleted by mistake on MySQL1.
I suppose it would be replicated to MySQL2 and than losing the backed up data.


Yes, you could probably lose the data if it is deleted from the first and then the deletion is replicated to the second.  But if you had enough space on the second, you could try the dump on it instead.  

A problem with other options, including possibly ZFS, is that a non-MySQL-based snapshot could grab partial or broken records if only part of the record is written or deleted at the exact time of the snapshot.  So I think you might have to focus on variations of the replication or dump.

---

### Post by Drenriza on 2015-10-23
Nothing

---

### Post by lukeiamyourfather on 2015-10-23
> **Lars Noodén said:**
> A problem with other options, including possibly ZFS, is that a non-MySQL-based snapshot could grab partial or broken records if only part of the record is written or deleted at the exact time of the snapshot.  So I think you might have to focus on variations of the replication or dump.

If the application is something internal or otherwise controllable then it could flush all transactions once in a while and pause for like two seconds at which point the application could trigger a snapshot during the pause. The ZFS snapshots are instantaneous. To me this makes a lot more sense than backup at the application database level. Data can't accidentally be destroyed while creating a snapshot, the same can't be said for the other option. The snapshots in time are also nice for lots of other reasons like being to go back in time in a read-only mode or duplicating a snapshot to recreate issues for developers (without using live data).

---

### Post by Drenriza on 2015-11-03
> **Lars Noodén said:**
> A problem with other options, including possibly ZFS, is that a non-MySQL-based snapshot could grab partial or broken records if only part of the record is written or deleted at the exact time of the snapshot.  So I think you might have to focus on variations of the replication or dump.

Been a little while since i tried to write a reply (aka my "Nothing" reply). But what i found out is that you can flush MySQL (let all requests complete) store new connections, do the dump (one second to dump several xx GBs) and restore normal MySQL functionality.

Afterwards you can do something along the lines discussed above
```

zfs send poolname/filesystem@snapname | ssh user@remote "zfs recv"

```
Where you can send the dump either as a separate file tar.gz from the dump (mount). Or send it directly to another zfs mount.
Also the SSH command has recovery functionality, meaning that if the connection breaks for w/e reason. It wont start from scratch on the
next transfer, but instead continue from where it last stopped something along the lines what rsync does.

After scratching my head about this predicament for a little while i believe that this would be the best way that i have found so far.
Since replication, clusters with more have their own challenges.

Thanks all for the feedback so far and for helping with several different views of viewing the predicament!
Its enormously helpful.

Kind regards

---

