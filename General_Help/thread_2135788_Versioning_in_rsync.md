---
title: "Versioning in rsync?"
date: 2013-04-15
forum: General Help
---

### Post by 777funk on 2013-04-15
I think I've got rsync's concept figured out. Seems pretty simple to run and to automate in Cron. However I'd like to keep a daily backup and if any files have been modified to have the old versions available (just incase).

Is there an easy way to do this?

---

### Post by ajgreeny on 2013-04-15
From man rsync; you can use the -b option:-
```
-b, --backup
              With  this  option,  preexisting  destination files are renamed as each file is transferred or deleted.
              You can control where the  backup  file  goes  and  what  (if  any)  suffix  gets  appended  using  the
              --backup-dir and --suffix options.

              Note  that  if you don’t specify --backup-dir, (1) the --omit-dir-times option will be implied, and (2)
              if --delete is also in effect (without --delete-excluded), rsync will add a "protect"  filter-rule  for
              the  backup suffix to the end of all your existing excludes (e.g. -f "P *~").  This will prevent previ&#8208;
              ously backed-up files from being deleted.  Note that if you are supplying your own  filter  rules,  you
              may  need  to  manually insert your own exclude/protect rule somewhere higher up in the list so that it
              has a high enough priority to be effective (e.g., if your rules specify a trailing  inclusion/exclusion
              of ’*’, the auto-added rule would never be reached).

       --backup-dir=DIR
              In  combination with the --backup option, this tells rsync to store all backups in the specified direc&#8208;
              tory on the receiving side.  This can be used for incremental backups.  You can additionally specify  a
              backup  suffix using the --suffix option (otherwise the files backed up in the specified directory will
              keep their original filenames).

              Note that if you specify a relative path, the backup directory will  be  relative  to  the  destination
              directory,  so  you  probably want to specify either an absolute path or a path that starts with "../".
              If an rsync daemon is the receiver, the backup dir cannot go outside the module’s  path  hierarchy,  so
              take extra care not to delete it or copy into it.
```

---

### Post by oldfred on 2013-04-15
Charles posted some examples using dates.

 [http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)

      
 Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

 Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)

---

### Post by Zill on 2013-04-15
I am very pleased with luckyBackup which uses rsync "under the hood" but also has a nice user-friendly GUI. :-)

In addition to manual backups on request, it can also do automatic and unattended backups via cron.  Snapshots of previous backups can be kept so that you have an historical record and so can restore any particular backup.

For more info see [http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)
```
sudo apt-get install luckybackup
```

---

