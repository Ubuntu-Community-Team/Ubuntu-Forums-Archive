---
title: "rdiff-backup file list"
date: 2020-04-09
forum: General Help
---

### Post by rbmorse on 2020-04-09
If I understand the rdiff-backup docs correctly, I can use a file list to both exclude and include files/directories.  

Files to be excluded are preceded by a "-" character and the same precedence rules as used at the command line apply. 

So, if my exclude file consists of:

```

/etc/boo.conf
-/etc

```

the file /etc/boo.conf would be included in the backup, but the other objects under /etc would be excluded.  If the syntax used in the file was:

```

/etc/boo.conf
-/etc/

```

the file /etc/boo.conf would be included in the backup, but the **directory /etc** and the other objects under /etc would be excluded.  

The rdiff-backup output of the first example would include /etc/boo.conf.  The output of the second would just include the file boo.conf in the root of the backup store. 

Is this correct?

---

### Post by TheFu on 2020-04-09
> **rbmorse said:**
>  
Is this correct?

Try  it and let us know, please.  After all, the backup of /etc is tiny, so even a worst case would be 5 seconds and 35MB.
Plus, you'll still need to test the full backup command and that always, always, requires a source and a target.

My basic desktop system backups have an rdiff-backup cmd like this:

```
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc --include /root   --include  /home \
  --exclude '**'    /  /Backups/$(hostname)
```

SOURCE = /
TARGET =  /Backups/$(hostname)
The last exclude of '**' means to exclude everything not specifically included earlier in the command.

i get all of /etc, all of /home, all of /root.

/etc is tiny, so why not?  The file we need is always the one we didn't backup.

/root is where is store system info like the list of manually installed packages, LVM layout, partition layout, and other stuff that could be sensitive (some firewall rules-bad ufw!), but not in /etc/.

/home should be obvious.  Cache dirs are cleaned out before the backup runs ... well, in my real scripts, there's an --exclude '**/.[Cc]ache' pattern. Similar for the many different .trash locations.  We don't need trash since we have versioned backups.  ;)

---

### Post by rbmorse on 2020-04-09
Yes, of course.  I'm sitting in an airport and waiting for a flight and just noodling out the broad outlines of a project.

---

