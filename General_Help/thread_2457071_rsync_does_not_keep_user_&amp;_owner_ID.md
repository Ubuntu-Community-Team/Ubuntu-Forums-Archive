---
title: "rsync does not keep user &amp; owner ID"
date: 2021-01-25
forum: General Help
---

### Post by zkab on 2021-01-25
I have Ubuntu 20.10 and rsync 3.2.3
I made a rsync between my computer and a Synology NAS backup (/nfs/BackUp).
NFS is installed with 'autofs 5.1.6' where I have specified '-fstype=nfs4'
This is what I do:

sudo rsync -rhlv --delete    /home/john/xxx /nfs/BackUp

rsync does not display any error ...
If I check the file 'xxx' with 'ls -la' it looks like this:

1) /home/john/xxx  gives me userID=1000,groupID=1000   which is OK
2) /nfs/BackUP/xxx gives me userID=1024,groupID=users  which is not OK
3) NAS login       gives me userID=admin,groupID=users which is not OK

Why can't rsync keep userID,groupID?
Is it a rsync problem or Synology NAS problem?

Totally lost ...

---

### Post by ActionParsnip on 2021-01-25
[https://linux.die.net/man/1/rsync](https://linux.die.net/man/1/rsync)

May help. There are example commands with explanation. I suggest you setup some dummy data to play with then go prime time

---

### Post by zkab on 2021-01-25
Well ... that's basically man page
I have tried to change owner, group and both but it complains 'Operation not permitted'
Still on square one ...

---

### Post by oldfred on 2021-01-25
What is actual format of partitions you are copying to?

---

### Post by zkab on 2021-01-25
Since Synology NAS use a Linux operating system it is ext4

---

### Post by SeijiSensei on 2021-01-25
Use the -a ("archive") switch.
```
rsync -av source target
```
is all you need. It will recurse through directories and preserve ownerships, modification times, etc.

The -v switch generates a list of all the files transferred. You can omit that if you like and just use "rsync -a". I recommend doing a "dry run" first with "-avn" to make sure the correct files are being transferred.  Then drop the "n" to execute the transfer.

---

### Post by zkab on 2021-01-26
'rsync -av source target' tells me that I don't have permission ... it seems that Synology NAS has its own internal rules

---

### Post by SeijiSensei on 2021-01-26
Run it as root with sudo.
```
sudo rsync -av source target
```

---

### Post by zkab on 2021-01-26
I did

---

### Post by oldfred on 2021-01-26
Check ID
[https://www.synoforum.com/resources/how-to-find-uid-userid-and-gid-groupid.77/](https://www.synoforum.com/resources/how-to-find-uid-userid-and-gid-groupid.77/)

Discussion of ID type issues.
[https://superuser.com/questions/860553/user-id-mapping-with-nfs-on-synology-nas](https://superuser.com/questions/860553/user-id-mapping-with-nfs-on-synology-nas)

---

### Post by zkab on 2021-01-27
This is what Synology support said ... Unfortunately I do not believe it would be possible to preserve the userID as instead of starting at 1000 our UserID starts at 1024 with the default admin.

---

