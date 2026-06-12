---
title: "Incremental Backup"
date: 2008-04-23
forum: General Help
---

### Post by yahooadam on 2008-04-23
Hey guys (not sure if this is the right category, but nothing else looked right)

I'm trying to do incremental backups of my Ubuntu PCs

I would like to have a file that stores most of the data on my PC (/home, /boot, /etc, and the rest)
that's all well and good

However, i would like to be able to make incremental backups
By an "Incremental Backup" i don't mean updating the files in the original backup
An incremental backup should create a new file, storing the updated files
This way, you can restore to any time/date, without using obscene amounts of space

For example, i want to backup once a week (incrementally) and a full backup every few months

However, everything I've found has only showed how to make a full backup, then update that full backup with the newer files (not helpful if a new file is corrupt/wrong/updated with wrong data)

Does anyone know of a program, or script, that is capable of doing this
Preferably i would like to be able to say "restoreBackup latestDiffFile" and the program would work out which full backup, and which incremental to restore (although this may not be possible)

Thanks for any help
Yahooadam

---

### Post by SpaceTeddy on 2008-04-24
**rsnapshot** would be my answer to your question .

i use it, and it works perfect. It only stored the "new" files, but keeps the full strucuture of every snapshot in place so you can browse through the snapshots for every backup. 

[[COLOR="Blue"]rsnapshot[/COLOR]]("http://www.rsnapshot.org/") is in the repositories and can just be installed via them.

furthermore, if you wanted automated backups from to be pulled from remote pc's to a central rsnapshot repository, [[COLOR="Blue"]this[/COLOR]]("http://troy.jdmz.net/rsnapshot/") might help you (it's pretty technical and probably a little hard to get into at the start :( )

---

### Post by justleen on 2008-04-24
i'm using something like this : [http://www.petesprojects.com/perl/backup/bashbackup.html](http://www.petesprojects.com/perl/backup/bashbackup.html)

works great..


there is a lot of info on this gentoo page: [http://gentoo-wiki.com/HOWTO_Backup](http://gentoo-wiki.com/HOWTO_Backup)

---

### Post by qrwe on 2008-05-05
I wonder if there's any way to point rsnapshot to place the backup at two locations redundantly, in my case a mounted ext3 partition on my hard drive and a nfs share at a NAS on a different physical location. A sort mirroring, in other words.
Any thoughts?

---

### Post by SpaceTeddy on 2008-05-05
just use two different rsnapshot confs ? copy them over and just change the path for one of them... or is that too difficult ?

---

### Post by daz4126 on 2008-05-05
rsnapshot looks like something that could really do with a gui frontend where you can just push a button and get a 'snapshot' of your system....

DAZ

---

### Post by nami on 2008-05-05
I would recommend, rdiff-backup with cron.

It lets you backup any directory to any location and only backsup if the file has been modified, so if it has not been modified, it does not bother backing it up to save space.  you can retrieve the files at anytime in the past by typing in the date and time.

---

### Post by SpaceTeddy on 2008-05-05
rsnapshot is based on rsync. It only copies files that changed as rsync would do it. Also, it keeps backups of a given period of time, giving you more than one backup to go back to (like the last x days, y month, z years, etc). 
because of hardlinks, it uses only the space that the different versions of the files take. Twice the same file will NOT use twice the diskspace...

just thought i'd mention that...

---

### Post by qrwe on 2008-05-08
> **SpaceTeddy said:**
> just use two different rsnapshot confs ? copy them over and just change the path for one of them... or is that too difficult ?

This will not mirror the backups, instead it will run two separate backup jobs simultaneously. They could diff in the end.
Is there no application for user space disk clustering or similar? Or maybe I'm just making things harder than they actually are.. ;-)

---

### Post by SpaceTeddy on 2008-05-08
mhm...ok. Then run one rsnapshot, and run an rsync (with preserve hardlinks) on the rsnapshot hive. Then you have twice the same backup... 

i think i am really confused on what you want to do...  :)

---

### Post by hyper_ch on 2008-05-08
I created my own little shell script for that... keekps incremental snapshot-style backups back for 90 days and I make a backup every 6h.

---

### Post by songshu on 2008-05-08
rsnapshot can make backups from different locations and store them in different locations

something like this will definetely work

backup  root@192.168.1.8:/home/share/   local/shares/
backup  local/shares/                   root@192.168.1.8:/home/share/
backup  local/shares/                   root@192.168.1.12:/home/share/

not sure if this will work but you might give it a try and let me know if it works

backup  root@192.168.1.8:/home/share/   local/shares/
backup  local/shares/ root@192.168.1.8:/home/share/ root@192.168.1.12:/home/share/




please do mind!!!!! TABS SEPARATE

---

### Post by qrwe on 2008-05-09
> **songshu said:**
> rsnapshot can make backups from different locations and store them in different locations

something like this will definetely work

backup  root@192.168.1.8:/home/share/   local/shares/
backup  local/shares/                   root@192.168.1.8:/home/share/
backup  local/shares/                   root@192.168.1.12:/home/share/

not sure if this will work but you might give it a try and let me know if it works

backup  root@192.168.1.8:/home/share/   local/shares/
backup  local/shares/ root@192.168.1.8:/home/share/ root@192.168.1.12:/home/share/




please do mind!!!!! TABS SEPARATE

Ah, nice solution.
What i first asked for was something I would like to describe as RAID1, but to different mounted shares/devices, e.g "/mnt/backup" + "/mnt/nfs_share". But this solution could do as well, thank you!

---

### Post by qrwe on 2008-05-16
OK, I was a little hasty here. This gives:

> ERROR: backup ./ /mnt/nas/ - Backup destination /mnt/nas/ must be a \
         local, relative path

Did this really work for you?

---

### Post by MONODA on 2008-05-16
google flyback

---

### Post by songshu on 2008-05-16
> **qrwe said:**
> Ah, nice solution.
What i first asked for was something I would like to describe as RAID1, but to different mounted shares/devices, e.g "/mnt/backup" + "/mnt/nfs_share". But this solution could do as well, thank you!

a little late reply, bit this also works to different directories or disks just like it does to IP's.

---

