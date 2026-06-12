---
title: "best backup tool for KUbuntu"
date: 2015-09-22
forum: General Help
---

### Post by alain.roger on 2015-09-22
Hi,

i read several posts (e.g. [http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools) or [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)) about backup tools under Ubuntu/KUbuntu but articles are quite old and i was wondering if something has been updated and improved.
Basically i need to backup several directories or disks to different targets and to do a full+incremental backups of my KUbuntu disk.

Till now i was trying to use Luckybackup but the lack of support and the frozen dev status, makes me doubt it is the best solution.

Any great idea would be welcomed.

Thanks a lot.

---

### Post by CharlesA on 2015-09-23
I use rdiff-backup on my system. It's not super user friendly but it gets the job done.

---

### Post by mastablasta on 2015-09-23
if you need a GUI check Areca, Duplicati, DejaDup, Backintime, grsync, puresync. but non GUI rsync and rdiff-backup seem to do the job.

---

### Post by alain.roger on 2015-09-23
I read that people were complaining about DejaDup as it does not work for partition/file restoring.
rdiff-backup has not been updated since 2009, so it is not a very good choice as support, i guess, is discontinued.
Duplicati is not anymore updated since 2013.

it seems that the only one that is still maintained is Areca.



> **mastablasta said:**
> if you need a GUI check Areca, Duplicati, DejaDup, Backintime, grsync, puresync. but non GUI rsync and rdiff-backup seem to do the job.

---

### Post by mikodo on 2015-09-23
Since you were looking at a gui backup solution with Luckybackup, I assume you would like to try one with gui.

I use BackinTime, for my data partition, just because of its' easy incremental backup and restore. The gui is minimal, and functional. Very little to learn. The dev/maintainer is active.

I use the cli rsync for backups to other nodes too, and like it for file transfers also. But, doing incremental backup with it is beyond me.

Someday, I might have the time to learn  rdiff-backup. But, until then, what I use works for me.

So, I suggest BackinTime as the gui option.

---

### Post by alain.roger on 2015-09-23
I tried areca and it needed 7h43 for backuping 370GB which is very very very slow comparing to my windows 7 backup tools NovaBackup.
I'm very surprised it took so long for a simple directory backup in regards to size.

---

### Post by mastablasta on 2015-09-24
Duplicati is preparing new version in 2014 - [http://www.duplicati.com/howtos/how-to-install-and-run-duplicati-2-0-preview](http://www.duplicati.com/howtos/how-to-install-and-run-duplicati-2-0-preview)
yes the old version is as it is. it works in the way they planned the project as I understand it. and for the record you will get support from them.

rdiff-backup - yeah it is old but if it works and does it's job well.... I mean many Linux progs are old and not updated. they have all their bugs fixed and they work (maybe they are only updated enough so they work?!). and all it means is they don't get new features. what with the constant updating :-)

similar goes for lucky backup - few bugs are left open but they are known and documented. the rest works (in Linux at least).

I am not sure what the issue with areca was but I didn't get any slowdown issue. is it possible that some setting is off? then again it does do compression on local disk first and similar things and then links and what not. also could be latest version ( I haven't tried it yet) is causing some issues. what were your speeds compared to Novabackup?

---

### Post by mikodo on 2015-09-24
> **mastablasta said:**
> 
rdiff-backup - yeah it is old but if it works and does it's job well.... I mean many Linux progs are old and not updated. they have all their bugs fixed and they work (maybe they are only updated enough so they work?!). and all it means is they don't get new features. what with the constant updatingYep.

 Here is how it went through testing in Debian. [URL="https://tracker.debian.org/pkg/rdiff-backup"]https://tracker.debian.org/pkg/rdiff-backup
[/URL]
Very few bugs with Ubuntu filed against it.      [URL="https://bugs.launchpad.net/ubuntu/+source/rdiff-backup"]https://bugs.launchpad.net/ubuntu/+source/rdiff-backup




[/URL]

---

### Post by rslater on 2015-09-25
Another vote for Back in Time.  very simple to configure and use and to date has been very reliable.

---

### Post by alain.roger on 2015-10-12
In fact,

i was thinking to mix solutions.

for example i have 3 computers and i need to have a full backup of each of them each week + each day incremental.
It would be great if i could find a tool/solution that allows me just to boot on CD/USB in case of crash and just to connect to my NAS server to retrieve the whole backup and install it back to crashed computer.

For data that need to be exchanged or worked on several computers, i was thinking to us a synchronization tool like backintime or areca that seems to be nicely packaged into a simple gui.
that way if i work on my computer, i can synchronise data onto NAS and later on take the laptop synchronize data from NAS to laptop and go to appointment for example.

i'm trying to find the best way to save space on NAS (only 4 TB - raid 10) and to have for sure a fast crash/recovery solution.

I tried clonezilla last year but it was very slow and not great in terms on recovery.

If someone has a better solution just let me know it.

thx.

---

### Post by idef1x on 2016-02-08
Why bother backing up te OS? If my workstation(s) crash I just reinstall it. Good for cleaning up as well ;)

Anyway I only backup my home dir with plain rsync to my NAS. My NAS is running on Ubuntu server with ZFS. The NAS takes snapshots on a regular basis, so I can do a roll-back/retrieve old files when I need to.
My NAS makes backups to a cloudprovider with webdav enabled access. Again with plain rsync. For making it more secure I use the S3QL filesystem on top of webdav for encryption, deduplication, compression and again snapshotting. The cloud backup is solely used in case my house burns down or so...

---

