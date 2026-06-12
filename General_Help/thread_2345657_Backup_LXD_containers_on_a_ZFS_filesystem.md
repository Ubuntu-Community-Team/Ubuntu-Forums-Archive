---
title: "Backup LXD containers on a ZFS filesystem"
date: 2016-12-06
forum: General Help
---

### Post by courtney2 on 2016-12-06
I'm trying to find the best way to do a regular backup of my system that runs LXD containers on a ZFS drive. The ZFS pool got its own drive to use. I'd like to do it in such a way that I don't have to stop the containers to do the backups. I have seen some people say backing up snapshots of the zpool, but I'm pretty n00b at this stuff. I mostly understand snapshots, just not backing them up. I can't find anything that really helps either. Does anyone know how to do this? Also if I do a backup, how would I properly restore them? I have a backup external hard drive that has its own ZFS filesystem on it

---

### Post by courtney2 on 2016-12-08
bump...no one here is backing up lxd on zfs that can offer help?

---

### Post by courtney2 on 2016-12-10
Is there a place where I can go where people know stuff more advanced than the norm? I can't even find documentation on this.

---

### Post by kingneutron on 2016-12-12
--Here are a couple of places to start:

[https://pthree.org/2012/12/20/zfs-administration-part-xiii-sending-and-receiving-filesystems/](https://pthree.org/2012/12/20/zfs-administration-part-xiii-sending-and-receiving-filesystems/)

[https://www.howtoforge.com/tutorial/how-to-use-snapshots-clones-and-replication-in-zfs-on-linux/](https://www.howtoforge.com/tutorial/how-to-use-snapshots-clones-and-replication-in-zfs-on-linux/)

[https://forums.freenas.org/index.php?threads/zfs-send-to-external-backup-drive.17850/](https://forums.freenas.org/index.php?threads/zfs-send-to-external-backup-drive.17850/)

--I'm a big ZFS on Linux fan myself, and admittedly the docs for what you are trying to do are both lacking and somewhat confusing.

---

### Post by courtney2 on 2016-12-15
I gotta say, I love what it offers but it's a huge headache when you're inexperienced. So here's what I have with no luck so far:

I create a snapshot: sudo zfs snapshot -r lxd@backup_2016-12-15

Then I have a zpool called backups (external hdd), I want to send a stream from my lxd zpool to my backups zpool:

sudo zfs send -R lxd@backup_2016-12-15 | zfs receive -vF backups

I then get a broken pipe error. What did I do wrong?

---

### Post by kpatz on 2016-12-15
A broken pipe means the receive process quit while the send was still sending.  You should have seen an error message from the receive side prior to the broken pipe.

You have the backups pool imported before you did this, right?

Oh, looks like you forgot the sudo on the receive side:

```
sudo zfs send -R lxd@backup_2016-12-15 | **sudo** zfs receive -vF backups
```

---

### Post by courtney2 on 2017-01-16
Hey sorry for getting back to this late, been sick and had holiday distractions. Here's what I have now. I added sudo to my zfs receive command so it all looks like this now:

sudo zfs send -R lxd@backup_2016-01-16 | sudo zfs receive -vF backups

I did import the pool before I did this, yes. And here is my error:

sudo zfs send -R lxd@backup_2017-01-16 | sudo zfs receive -vF backups 
cannot receive new filesystem stream: destination has snapshots (eg. backups@backup_2016-12-15)
must destroy them to overwrite it
warning: cannot send 'lxd/images@backup_2017-01-16': Broken pipe


So it seems zfs is making me delete old snapshots before I can put in the new one, which is weird

EDIT:
I deleted the old backups snapshot and send/receive works now. But how do I then make my next backup without deleting the old snapshot? I'd like to keep old snapshots so IF I find say, my system was compromised 4 weeks prior, I could find the last safe snapshot and restore that one.

---

### Post by courtney2 on 2017-01-16
Another new problem I have is it appears doing a zfs import of my backup makes it try to mount my lxd container subvolumes:

cannot mount '/var/lib/lxd/containers/backupSamba.zfs': directory is not empty
cannot mount '/var/lib/lxd/containers/nextcloud.zfs': directory is not empty
cannot mount '/var/lib/lxd/containers/reverseProxy.zfs': directory is not empty
cannot mount '/var/lib/lxd/containers/wordpress.zfs': directory is not empty
cannot mount '/var/lib/lxd/images/683cdd3938706deeb66f19854ee27ef0c75e2594ce60ad4525357c3ce46f9772.zfs': directory is not empty

I'll continue to search all these things, but any help is appreciated!

---

### Post by #&amp;thj^% on 2017-01-16
I have only played with ZFS for a short time...but I keep them seperated with something like this:
You can hold a snapshot or set of snapshots. For example, the following syntax puts a hold tag, keep, on tank/home/cindys/snap@1.
Example:
```
# zfs hold keep tank/home/cindys@snap1
```
You can use the -r option to recursively hold the snapshots of all descendent file systems. For example:

```
# zfs snapshot -r tank/home@now
# zfs hold -r keep tank/home@now

```
This syntax adds a single reference, keep, to the given snapshot or set of snapshots. Each snapshot has its own tag namespace and hold tags must be unique within that space. If a hold exists on a snapshot, attempts to destroy that held snapshot by using the zfs destroy command will fail. For example:

```
# zfs destroy tank/home/cindys@snap1
cannot destroy 'tank/home/cindys@snap1': dataset is busy
```

If you want to destroy a held snapshot, use the -d option. For example:

```
# zfs destroy -d tank/home/cindys@snap1
```

Use the zfs holds command to display a list of held snapshots. For example:

```
# zfs holds tank/home@now
NAME           TAG   TIMESTAMP                 
tank/home@now  keep  Thu Jul 15 11:25:39 2010  
```

```
# zfs holds -r tank/home@now
NAME                  TAG   TIMESTAMP                 
tank/home/cindys@now  keep  Thu Jul 15 11:25:39 2010  
tank/home/mark@now    keep  Thu Jul 15 11:25:39 2010  
tank/home@now         keep  Thu Jul 15 11:25:39 2010  
```

You can use the zfs release command to release a hold on a snapshot or set of snapshots. For example:

```
# zfs release -r keep tank/home@now
```

If the snapshot is released, the snapshot can be destroyed by using the zfs destroy command.
Hope this useful.

---

