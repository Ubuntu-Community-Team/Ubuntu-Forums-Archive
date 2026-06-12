---
title: "deja-dup and NFS mount"
date: 2013-01-13
forum: General Help
---

### Post by phoenix1963 on 2013-01-13
Hi all, I need to start backing-up and plan to use deja-dup to back up onto a synology NAS. I aim to use deja-dup as it seems about the right level of sophistication for a fairly ignorant user and a couple of home PCs.

I've read that NFS offers faster transfer than an smb mount and I've set up the synology box to accept NFS mounts.
What I'd like deja-dup to do is mount the drive only when performing a backup, so as to keep it isolated and therefore at less risk at other times. Is this possible?

I note the "backup location" menu offers "ftp", "ssh", "webdav", "windows share" and "custom location" options. Are any of these configurable as nfs mounts, if so what is the syntax? Do I have to go back to smb?

Thanks,
phoenix1963

---

### Post by MrKaliman on 2013-02-17
I have no experience using deja-dup, but I think the following approach should work.

Make sure that NFS is configured on your synology box (configuration).
Also make sure that the NFS permissions are set for the shared folder (ex. backup)

Create a local folder on your pc (ex. /mnt/backup)
Mount the shared folder 'backup' manually onto your pc (/mnt/backup).

Configure deja-dup to create backup to the folder that you just created.

unmount the NFS.

Create a bash script


[LIST]
[*]mount shared folder from synology
[*]execute deja-dup backup
[*]get exit code from ( for ex. ret_code="${?}" )
[*]unmount nfs
[*]sent e-mail
[/LIST]
Execute the script using crontab

Good Luck !!

---

### Post by phoenix1963 on 2013-03-30
Thanks for the thoughts Kaliman. It's taken me a while to cable the house with cat 6 to enable reliable backup, so I'm nearly ready to deal with the software side.

I now realise that deja-dup is a gui for duplicity, so prob my best bet is to do some thing similar to what you suggest, but using the command-line duplicity run from cron.
There are a number of issues to solve before I get there. The NFS mount to my Synology box seems scarily insecure, now novice me realises NFS seems to have no user based access control (maybe that's why Kerberos was invented?), even a Samba mount can be made to require a login of some sort. There's so much to I need to understand, and I've got 30+ years experience programming scientific software!

Maybe when I've got this solved I'll write a guide...

phoenix1963

---

### Post by phoenix1963 on 2013-03-30
For anyone else with a Synology NAS, there's a rather useful blog here[http://othell.com/wp/?tag=synology]("http://othell.com/wp/?tag=synology") .

phoenix1963

---

