---
title: "Sharing a network drive without samba"
date: 2014-05-03
forum: General Help
---

### Post by Tim_Johnson on 2014-05-03
I've used linux for many years, but I have always used samba to do sharing.

I'd like to be able to share a network drive _without_ samba. I haven't been successful
'googling' this topic. I would welcome pointers to docs and discussions.

My goal is to use an external hard drive attached to `**machine_a**' to do backup for `**machine_b**',
so I will need to know how to mount the drive as well.

TIA
- tim -

---

### Post by TheFu on 2014-05-03
nfs?
sshfs?
iSCSI?
AoE?
GlusterFS?
webdav?

That would be my order of preference.

However, for backups ... you don't need file sharing at all.  Use something that works over ssh like ... duplicity, rdiff-backup, rsync, rsnapshot, rbackup, or any of the 50 other choices. Of course, if there is any non-UNIX-like OS involved, many of these things just don't work.

---

### Post by Tim_Johnson on 2014-05-03
> **TheFu said:**
> nfs?
sshfs?
iSCSI?
AoE?
GlusterFS?
webdav?

That would be my order of preference.

However, for backups ... you don't need file sharing at all.  Use something that works over ssh like ... duplicity, rdiff-backup, rsync, rsnapshot, rbackup, or any of the 50 other choices. Of course, if there is any non-UNIX-like OS involved, many of these things just don't work.
Let's see .... if I used nfs, then I could use deja dup. 
But, rsync would be a good option. I use it with drush
Where are some good examples for nfs? I can research myself, but
any pointers are welcome. Thanks, we're down to rsync and nfs.
cheers
P.S. found good rsync examples here
[http://www.thegeekstuff.com/2010/09/rsync-command-examples/](http://www.thegeekstuff.com/2010/09/rsync-command-examples/)

---

### Post by TheFu on 2014-05-03
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) ?

rsync really isn't the best tool for nominal backups. It is great for 1-time mirrors and for media files, but systems and /home directories need smart, differential, versioned backups that have next-to-bonehead restoration capabilities WITHOUT any proprietary file formats or 20 extra steps needed.  Having 60 days of versioned backups for 10% more storage than a mirror seems like a bargain to me.

---

### Post by Tim_Johnson on 2014-05-03
> **TheFu said:**
> [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) ?

rsync really isn't the best tool for nominal backups. It is great for 1-time mirrors and for media files, but systems and /home directories need smart, differential, versioned backups that have next-to-bonehead restoration capabilities WITHOUT any proprietary file formats or 20 extra steps needed.  Having 60 days of versioned backups for 10% more storage than a mirror seems like a bargain to me.
Thanks for the recommendation. Your link is bookmarked...
;)

---

