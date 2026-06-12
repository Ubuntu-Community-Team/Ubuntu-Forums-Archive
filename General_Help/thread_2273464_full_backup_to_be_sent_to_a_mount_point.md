---
title: "full backup to be sent to a mount point"
date: 2015-04-13
forum: General Help
---

### Post by fernando47 on 2015-04-13
Hi all

I am new to ubuntu, I have ubuntu 10 running on a server, and I would like to perform a full backup, unfortunately the system does not have a backup device, so I need to plave the backup archive in a different mount point instead of root, because there are 3 file systems that are big:

```
 df -hFilesystem            Size  Used Avail Use% Mounted on
/dev/sda1             388G  210G  158G  58% /
none                   16G  352K   16G   1% /dev
none                   16G  164K   16G   1% /dev/shm
none                   16G  128K   16G   1% /var/run
none                   16G     0   16G   0% /var/lock
none                   16G     0   16G   0% /lib/init/rw
none                  388G  210G  158G  58% /var/lib/ureadahead/debugfs
dumps                  98G   55G   44G  56% /dumps
mcelnetapp            441G  221G  221G  50% /mcelnetapp
netappbk              441G  334G  108G  76% /netappbk
testdb                985G  612G  373G  63% /testdb
```

My question is how to redirect the output of the backup command to a new file system to be created. My tar command is like this:

```
tar -cvpzf backup_db01.tgz --exclude=/var/lib/ureadahead/debugfs --exclude=backup_db01.tgz / 2>/error.log
```

---

### Post by papibe on 2015-04-13
Hi fernando47. Welcome to the forum ):P

A few thoughts:

The new destination has to be mounted somewhere. Let's say you buy a new hard drive. Once you formated it, you could mount it in, say, /backup:
```
sudo mount /backup
```
You would need to add an exclude rule to your tar command to exclude the mount point:
```
tar ... --exclude=/backup ...
```
In order to write the tar file on the new disk, you have to options:

Use paths:
```
tar -cvpzf /backup/backup_db01.tgz ...
```
Or, change your current directory to where you want to file to be created, and then run the tar command:
```
cd /backup

tar -cvpzf backup_db01.tgz ...
```
Does that help? Let us know how it goes.
Regards.

---

### Post by coffeecat on 2015-04-13
Not an Ubuntu, Linux & OS Chat question, so...

*Thread moved to **General Help**.*

I've moved this to General Help rather than the server section because it has general relevance.

> **fernando47 said:**
> I am new to ubuntu, I have ubuntu 10 running on a server

Do you mean Ubuntu 10.04? If you do, please be aware that it goes end-of-life (no more support or updates) on April 30 this year, that is in a few days. If you did install 10.04 and are new to Ubuntu, was there a reason for choosing a near-obsolete version? You need to update to a supported version or re-install. The latest long-term support version, 14.04, might be the best choice.

---

### Post by fernando47 on 2015-04-14
Thank you very much for your help

---

### Post by btindie on 2015-04-14
Are you really sure you want to backup / ? If so you'd want to also exclude the system directories /dev /sys /proc /tmp and probably /cdrom

You'd be better off splitting it up into smaller backups. System files will change less frequently so won't need to be backed up so often. Plus some of your mounted filesystems are quite large and would take a very long time to back up.

And also don't redirect stderr to / (2>/error.log) instead put it in /tmp or that'd also be included in the backup. And also by using the -v switch to tar it'll list every single file it backs up which would result in quite a lot of output and also slow it down slightly.

You're also asking tar to gzip the resultant archive "-z" which for a 900GB archive would take some time and may not be necessary when some of the files will not always be compressible. Which is why you'd be better off breaking it up into smaller archives.

---

