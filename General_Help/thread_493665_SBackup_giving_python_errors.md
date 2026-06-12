---
title: "SBackup giving python errors"
date: 2007-07-06
forum: General Help
---

### Post by mattmcmanus on 2007-07-06
Im having some issues with SBackup and its starting to drive me nuts. I do not know any python so I have no idea really where to go to start fixing this. 

When I run a manual sbackup it says backup process started but then nothing ever happens. When I run it from the command line to see what errors it is giving a get the following.

> I: Securing permissions at: /media/backup/minibetty/2007-06-01_19.35.28.260340.minibetty.ful
Traceback (most recent call last):
  File "/usr/sbin/sbackupd", line 404, in <module>
    upgrader.upgrade_target( target, purge )
  File "/usr/sbin/upgrade_backups.py", line 60, in upgrade_target
    self.upgrade_tdir( target+"/"+adir )
  File "/usr/sbin/upgrade_backups.py", line 78, in upgrade_tdir
    v = self.openfile( tdir + "/ver" )
  File "/usr/sbin/upgrade_backups.py", line 307, in openfile
    return gnomevfs.open( uri, 1 )
gnomevfs.NotFoundError: File not found


This all started after my computer crashed while running a backup.

Any ideas? Is there any more information you need? Thanks so much for the help.

---

### Post by mattmcmanus on 2007-07-07
bump

---

