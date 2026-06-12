---
title: "BACKUP App Like FWBACKUPS for User Files/Folders with Incremental &amp; Sets/Profiles?"
date: 2021-02-11
forum: General Help
---

### Post by OzzyFrank on 2021-02-11
Hi. I was happily using FWBACKUPS for backing up specific personal files/folders, but after a recent system update (for 20.04) it looks like my system got rid of it. And it's no longer in the repos. So, going to the author's site, where he said he is no longer maintaining DEBs for it, and unsuccessfully trying to install from source via the commands he outlined, I've been scouring the web looking for a replacement. But the ones I've comes across, and the few that I've tried, are either for backing up the entire system (I want to be able to backup my music, etc), or have no option for incremental backups (I don't want every file copied over every time - just the new and updated ones), or you cannot definite "sets" or profiles or tasks (like one for my music, another for videos, etc - especially important for being able to backup folders from one portable hard-drive to another). So here I am asking for your expertise.

So what I am after is a full-featured app with GUI like FWBACKUPS that:

* Allows you to specify specific folders for backup
* Allows you to create multiple sets/profiles/tasks for different backup jobs for folders on internal and external hard-drives
* Performs Incremental Backups (and is clever enough to know when an existing file has been modified or replaced)
* Allows files to be backed up individually/uncompressed (some only do backups to tarballs, etc)
* Works with any filesystem (I need it for both EXT4 and NTFS)

Déjà Dup is useless, KBackup allows creation of Profiles for different tasks but there doesn't seem to be an option for Incremental backups, and KUP Backup allows me to add Plans for different tasks but I cannot run them (there's a big red shield with an X in it for bother Plans I have created?). So any suggestions are welcome, as long as the apps do those simple things like FWBACKUPS could. I would also welcome any info on how to successfully reinstall FWBACKUPS, as that was great, and I already have backup jobs defined. Many thanks in advance, comrades!

---

### Post by HermanAB on 2021-02-12
You could see this: [https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by OzzyFrank on 2021-03-06
I ended up finding a great app for incremental backups: [COLOR=#ff0000]**Grsync**[/COLOR]. While it's not *quite* as user-friendly as **FWBackups** - in the latter all you have to do is check the box for incremental backups, while in **Grsync** you have manually choose the backup options - it's very fast, and gives you greater control over the backup if you want that. And of course it allows you to create multiple *Sessions* for different backup tasks.

[IMG]https://i.ibb.co/kJY6gvv/Grsync.jpg[/IMG]

Basically, to get an incremental backup, just check [COLOR=#800080]***Delete on destination***[/COLOR] to delete any files that no longer exist on the source - this way your source and destination are basically mirrored. Basically, that's all is needed, as it compares modification times between files that exist on both source and target.

But some of the other options are useful. I also check ***[COLOR=#800080]Preserve time[/COLOR]*** so that files will be copied with the time stamp of their last modification, rather than the time when you copied them (this was the default in FWBackups, but at least you can enable it in Grsync, too). And for those who wish to be cautious, in **Advanced options** you can check ***[COLOR=#800080]Always checksum[/COLOR]***, which means that it will decide which files have been modified via checksum, rather than modification time; you shouldn't need to enable that, but know that it's there in case you have issues with the default method of determining what needs to be backed up (I gather this will significantly add to the backup time).

While Grsync seems to be what I need, and seems to have done an incremental backup as expected, and is really fast compared to FWBackups, I won't mark this thread as [SOLVED], because if anyone knows of another great program to use, I'd love to know about it. Cheers.

---

### Post by OzzyFrank on 2021-03-06
Grsync in action:

[IMG]https://i.ibb.co/3vcZJ2N/backup.png[/IMG]

---

### Post by HermanAB on 2021-03-08
There are many front-ends for rsync.  This one is decent.  However, I prefer to just read the rsync man page and make my own scripts, so that I can set it and forget it.

---

