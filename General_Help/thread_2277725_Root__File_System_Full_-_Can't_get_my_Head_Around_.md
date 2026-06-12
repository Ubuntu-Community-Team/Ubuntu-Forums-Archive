---
title: "Root \ File System Full - Can't get my Head Around It"
date: 2015-05-11
forum: General Help
---

### Post by Quarkrad on 2015-05-11
Sorry - this is the third time I've had this problem and I still cannot get my head around the fix.  I have a \ partition (sda5) that is full - the partition is 30GB that should only contain 14.04.  I have a separate \home partition (sda6) that is 70GB and another storage partition  731GB (sda7)  (see attached picture - I'm ignoring sda1, a win7 partition).  I have unplugged my backup hd so it is not showing - that is normally sdb1.   I have a backup script that backs-up \home\user and \store to my backup disk.  All this works ok but my (repeated) problem is when I manually force the the pc switch off instantly - it seems the backup runs but instead of backing up to sdb1 it's fills up \.  I need to 'look' in \ and delete anything to do with \home\user or \store - but I cannot get my head out of thinking in terms of partitions.  File managers show everything under \ so when I look in File System \media\ I'm not sure whether I'm seeing something in \ (sda5) that shouldn't be there or I'm looking at my actual \store partition (sda7).  At this point I do not want to delete media/store because it could be sda7.  How do I know when I'm looking at  media\store whether it is sda7 or a copy that sits on sda5 and filling up my root directory/partition?

---

### Post by Lars Noodén on 2015-05-11
Run the "Disk Usage Analyzer" and it will show in a graph where your system is filling up.  Once you know which parts are full, you have an idea about what the cause might be.  Often it's something in /var, either /var/log/ or /var/cache/

---

### Post by Quarkrad on 2015-05-11
Is it the case that if, in Nautilus, I unmount store (that is sda7) then it will not be seen by the system?   I have unmount store and note that when I look in Computer/File System/media/ I have folders called dad (that is me the user), store, win7, winxp.  (I use to dual boot ubuntu and winxp - I deleted winxp and install win7).   As I have unmounted store/sda7 I'm not sure what I'm looking at in file system/media - is it save to delete /media?

---

### Post by Lars Noodén on 2015-05-11
> **Quarkrad said:**
> Is it the case that if, in Nautilus, I unmount store (that is sda7) then it will not be seen by the system?   I have unmount store and note that when I look in Computer/File System/media/ I have folders called dad (that is me the user), store, win7, winxp.  (I use to dual boot ubuntu and winxp - I deleted winxp and install win7).   As I have unmounted store/sda7 I'm not sure what I'm looking at in file system/media - is it save to delete /media?

Unmounted filesystems will not be seen.  The directory /media is empty but it is needed as a mount point for removable media.  So it is best to leave it.  You will not save any space by deleting it and will create some problems if it is gone.  Try running the "Disk Usage Analyzer".  It will show you where the space is being used so you can get to the cause of the problem rather than deleting randomly.

---

### Post by sudodus on 2015-05-11
Please run the "Disk Usage Analyzer" and it will show in a graph where your system is filling up. If you want help, you can attach a screenshot picture of the graph.

---

### Post by Quarkrad on 2015-05-11
OK - thanks, that did it.  I have attached baobab 1, 2 and 3 - it looks (to me) like I have a dad (me the user) - so I'm expecting to see /backup/dad in the trash folder.  I could not see it so I looked via gksudo nautilus and still nothing there - see gksudo.png.  Not sure what to do now.

---

### Post by sudodus on 2015-05-11
**/root/.local/share/Trash** contains a lot of cruft (old files that were moved to the wastepaper basket). You need to remove the cruft from there (from the wastepaper basket). It belongs to root, so you need elevated permissions (for example ***gksudo nautilus*** or with sudo and plain command lines)

---

### Post by Quarkrad on 2015-05-11
Many thanks - that did it.  Disk Analyzer is now showing **\** as 9.0 GB / 31.3 GB.

---

### Post by sudodus on 2015-05-11
I'm glad I could help you :-)

---

### Post by yancek on 2015-05-11
The GParted image in your initial post shows that both your / (root filesystem) and /media/store are nearly full.  The images in post # 6 show that the /root directory, which is the directory for the root user has a lot of data.  This would indicated that you are moving files to the Trash while logged in with sudo privileges.  There should be a  .local/share/Trash directory for your user as well as for root.  If you move to Trash while logged in as a user, they would go to the /home/dad/.local/Trash sub-directory.

With your / partition so full, I'm surprised you can boot at all.

---

### Post by Quarkrad on 2015-05-11
Something very wrong has happened and I'm more confused.  Having got \ back down to 9GB I connected in my 2nd HD (Backup) and all seemed fine until I decided to do a manual backup via rsync.   As normal I backed up dad(me the user - on sda5) and Store (sda 7) to my Backup HD (sdb1).   I filled up \ again - it seems to me that /media/backup (that is sdb1) was mounted under \.   So .....  \ is now 100% full again.  Disk Analyzer showed /media/backup under \ so I deleted it.  Problem now is when I look at nautilus There is no store (sda7).  Actually it is sitting in \/.local/share/Trash/files/media - in fact in media is store and win7.   How is it that  /media (that should have store, backup, win7 in it) is now sitting in \/.local/share/Trash/files rather than in home/dad/ where it should be?   I'm a little afraid at this stage to do anything in fear of loosing everything.

---

### Post by Quarkrad on 2015-05-11
Hopefully this will help.

---

### Post by Quarkrad on 2015-05-11
This is fstab

---

### Post by walttheboss on 2015-05-11
This has happened to me a few times.  The issue is this.  When you run a command and the target does not exist it may be created and be created in root.  We were trying to rsync a backup```
rsync -a --delete source /media/superuser/target
``` But we had the name slightly wrong and it filled the root and nearly shut down my server.  Dumb on my part. 

The second thing to check is that your partitions are mounting correctly.  If they automount all available partitions and drives then you are okay.  BUT you have to get the names exactly write. If they are mounting as /media/Target and you are syncing to /media/target it will break.

Clearly what is happening is that when you run a backup it cannot find the target and is making one, mounting it in root and filling it up.

---

### Post by Quarkrad on 2015-05-11
In nautilus I use to see **backup** (that is, my mounted sdb1 HD) - at the moment nautilus is showing **1.0 T Volume**.  (Having re-booted everything now looks normal \ is back to 9GB).  It looks like you are right - I'm automounting something called **1.0 T Volume** - it should be **backup**.   How do I change this (fstab shows #Entry for /dev/sdb1 :
UUID=370E3F565B2F641D	/media/backup	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0 - there is no mention of 1,0 T Volume in fstab).

---

### Post by Quarkrad on 2015-05-11
Something strange to me.  In nautilus (user.png) it shows 1.0 TB Volume but when I look as sudo it shows backup.

---

### Post by Quarkrad on 2015-05-11
Managed to sort name via Preferences/Disks.  Run a test via gadminrsync and looks like I am back up and running.  Many thanks.

---

### Post by walttheboss on 2015-05-11
I have learned to let the system mount the disk and then make sure I know the path.  Normally the non-root user path.  Then I use that in my commands.  Putting the entry in fstab is normally not necessary.  But not bad either.

---

### Post by sudodus on 2015-05-12
Let us hope that you are back up and running, but if you need more help, I suggest that you show us the ***rsync command line*** that you are using.

---

