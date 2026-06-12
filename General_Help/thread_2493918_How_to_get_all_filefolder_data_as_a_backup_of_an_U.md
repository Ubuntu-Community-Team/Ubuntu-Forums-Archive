---
title: "How to get all file/folder data as a backup of an Ubuntu computer?"
date: 2023-12-29
forum: General Help
---

### Post by norvel4 on 2023-12-29
sudo rsync -vrlDAXpHogtU --delete --open-noatime --exclude=(copy to directory) --exclude=(USB mounted at) / (copy to directory)

That is like best I got so far for backups. What I would prefer is a program that writes all exact to system exactness properties of an Ubuntu system and can have most of them on a USB and restore those properties to new system exactness on any Ubuntu computer. I already have like my own Ruby file properties recorder for like my home directory. If such a program or similar exists maybe tell me. For backups anything that transfers created at would be an improvement. Anyway, trying for a full backup that can be understood on a Windows computer or maybe any computer and is not a system image. Why I do not want a system image is simplicity of copy to other things, no need to install extra stuff. Is there any automated way to do this so I do not have to do one by one all files and folders? Feel free to use this idea and maybe some day a full backup like this will be possible. I heard rsync could transfer all this back to an Ubuntu computer and overwrite system files, but to be sure, can that be done? Maybe do not do that --delete on rsync back to computer first time then a second time do it. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

### Post by MAFoElffen on 2023-12-29
or...
```

sudo rsync -aAXP --one-file-system / /mnt/backups/backup 

```
That would copy entire file system hierarchy from logical drive to the backup point, avoids crossing a filesystem boundary when recursing, and excludes the backup point.

You can still use excludes and other options to that... I use -P instead of -r, to see progress instead of a files list.

That would be initial. Vary that for incrementals.

Restore:
```

sudo rsync -aAXP &#8211;delete /mnt/backups/backup /

```

---

### Post by norvel4 on 2023-12-29
[B]Backup
sudo rsync -vrlDAXpHogtUP --delete --open-noatime --one-file-system --exclude=(USB at) / (copy to directory)

Restore:
[/B]**sudo rsync -vrlDAXpHogtUP --delete --open-noatime ****--one-file-system**** (copy from directory) /**

So that is what I should use to backup full? I notice yours lacks some options for getting some data. Still want creation times. Thanks for that. Anyway, I guess I may need to make like my own program for created at times. I already have a Ruby one. On restore, how do I make sure that USB contents are not overridden upon restore? All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

### Post by norvel4 on 2023-12-29
I just realized I should have E directly after P on that maybe or maybe not, maybe.

---

### Post by HermanAB on 2024-01-01
Maybe look at fsarchiver.

---

### Post by aljames2 on 2024-01-01
-a is the same thing as -rlptgoD

You should review the manpage for rsync.  It is a great tool for keeping two directories in sync.  I also use it for one way copying of files.

I only use rsync for our household documents, pictures, videos, music, etc. 

For system files on ext4+LVM, or just ext4, I prefer rdiff-backup.  This is a versioning backup tool.  I run this command consistently every day to pull backups of certain root locations that I know have custom configuration files that I would want to have should I need to restore my system?  My restore is always a fresh install and then go to my rdiff-backups to get the custom configs I need.

I never attempt a system clone or replication, and ever expected that to work.

---

### Post by dragonfly41 on 2024-01-01
There is LuckyBackup GUI  .. and GRsync GUI .. for first testing .. see "dry run" feature

---

### Post by TheFu on 2024-01-01
> **aljames2 said:**
> -a is the same thing as -rlptgoD

You should review the manpage for rsync.  It is a great tool for keeping two directories in sync.  I also use it for one way copying of files.

I only use rsync for our household documents, pictures, videos, music, etc. 

For system files on ext4+LVM, or just ext4, I prefer rdiff-backup.  This is a versioning backup tool.  I run this command consistently every day to pull backups of certain root locations that I know have custom configuration files that I would want to have should I need to restore my system?  My restore is always a fresh install and then go to my rdiff-backups to get the custom configs I need.

I never attempt a system clone or replication, and ever expected that to work.


^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
This, 1000x this ... er ... except I use rsync only for large, static, media files.  Documents and other small files are versioned using rdiff-backup.  I don't have enough money to support having 180 copies of media files, but I can easily hold 180 versions of smaller files, easily, as provided by rdiff-backup.

But the OP has something set in his brain about having 100% exact restores (including creation times) for some reason and anything less won't fit that mindset.  Screw that creation time is a security consideration.

---

### Post by MAFoElffen on 2024-01-01
+1 to TheFu & aljames2

I was going to suggest searching this Forum on threads started by TheFu, on rdiff-backup... He is spot on with that.

Him and I, having similar backgrounds coming from Unix, and our views on "Disaster Recovery" are similar: Volume managers to take snap shots and incremental backup strategies of what you need beyond the OS itself. The Basic OS can be reinstalled much faster than it can be restored. Tailoring and using the backups to restore where you need to be beyond that, for recovery or migrations. His writings on that are well thought out, easy to follow, and sound.

I have to admit that many decades ago, the strategy was to do full disk imaging and restores from that. Usually done about once a month. 

Decades of experience has shown me that that methodology doesn't make sense anymore, when the primary goal is "uptime" and to be back up within a very short window of acceptable loss... Or how long will it take to be back up (online) with your services.

That is a learning and perspective change from what things used to be, from maybe about 30 years ago. It can still be done, but that doesn't mean it's a good idea. 

I am still rewriting and adapting my backup strategies in my own scripts from lessons learned.

---

### Post by norvel4 on 2024-01-05
I know this may not be what you want to hear but I would prefer a full backup no matter how long it takes to reinstall. If it helps I made a property recorder and restoration script set that includes all timestamps and user and group. Also, am I missing anything for a full or as full as I can get backup with rsync. rsync is a step up from system image because it is incremental and with like my Bash scripts I can get practically all. Anyway, I seem to have solved like my own problem. 

Also, I do not want a multiple "versions" of like my computer saved, one is plenty. Sure it takes about 220MB for me to have timestamps but I think it is worth it. Also, store it on ext4, it stores more of what is on Ubuntu than FAT or NTFS. For Windows compatibility use an ext4 reader and maybe open up like with nogroup and nobody your important files that should be accessible on any computer. I understand there are other tools that **mostly** back up but I prefer a full backup even if like once a month is more practical. Thanks for trying to help, I think I got this. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

### Post by norvel4 on 2024-01-06
MAFoElffen, have you ever done that rsync restore you described with aAXP?

---

### Post by norvel4 on 2024-01-06
Does it help that I am on an Ubuntu Desktop?

---

### Post by dragonfly41 on 2024-01-06
Perhaps you just need to invest in a StarTech duplicator of drives .. as I use for dual SSD docking.
I don't actually use the duplicating feature but that is what it is designed for - drive cloning.

---

