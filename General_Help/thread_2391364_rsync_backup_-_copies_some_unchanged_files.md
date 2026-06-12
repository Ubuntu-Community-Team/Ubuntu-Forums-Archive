---
title: "rsync backup - copies some unchanged files"
date: 2018-05-08
forum: General Help
---

### Post by Skaperen on 2018-05-08
i just finished a re-install of a small VPS server so now it and my laptop are running 16.04.4 at a very recent upgrade (yesterday for the server, 3 days ago for the laptop).  "_rsync --version_" shows me:

```
rsync  version 3.1.1  protocol version 31
Copyright (C) 1996-2014 by Andrew Tridgell, Wayne Davison, and others.
Web site: http://rsync.samba.org/
Capabilities:
    64-bit files, 64-bit inums, 64-bit timestamps, 64-bit long ints,
    socketpairs, hardlinks, symlinks, IPv6, batchfiles, inplace,
    append, ACLs, xattrs, iconv, symtimes, prealloc

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.
```

i have set up a backup of *most* of the server files (a little more than 14GB) using _rsync_.  i have repeated the backup a few times with the _--backup-dir=_ option to save the old files in a hierarchy (named in the option) if they have been updated.  i do this to a new hierarchy each time i run the backup script (it make a new name based on date and time each time it runs).  i can see what was updated by seeing what old files are saved or reading the log files (output of _rsync_ is also saved under a like name).

the issue i am seeing in this, and have also seen in some manual runs of _rsync_, is that in addition to all the *genuine* updates, _rsync_ is also updating (transferring) some files that are *not* changed (have the same modification date/time, same size, and same contents).  it is the same few files that get transferred every day.  one curious thing is if i run this extra times per day, these files are not transferred the extra times; they are only transferred *once* per day.

**any ideas what i should look at to understand what _rsync_ is doing and why?**  although i do have some decent bandwidth, i still want to avoid transferring what does not need to be transferred.  i am thinking of adding the _-c_ option to have _rsync_ checksum the files since this seems to be some kind of date and/or time issue.

---

### Post by Xian on 2018-05-08
What is the complete rsync command w/options that you are using when this issue appears?

---

### Post by Skaperen on 2018-05-09
this is the commamd line taken from the log file:

```
00:08:07 EXECUTING: rsync --backup-dir=/home/backups/kepler/arch/2018-05-09 -aAbHimSvX --stats --del --force --numeric-ids --block-size=8192 --temp-dir=/home/backups/kepler/tmp-2018-05-09-000807-321190499 --timeout=4000 --exclude=*/noback/** --exclude=*/noback --exclude=*/tmp/** --exclude=*/tmp --exclude=/home/*/.gvfs/** --exclude=/home/*/.gvfs --include=/bin --include=/bin/** --include=/etc --include=/etc/** --include=/home --include=/home/** --include=/lib --include=/lib/** --include=/lib32 --include=/lib32/** --include=/lib64 --include=/lib64/** --exclude=/media/** --exclude=/media --exclude=/mnt/** --exclude=/mnt --include=/opt --include=/opt/** --exclude=/proc/** --exclude=/proc --include=/root --include=/root/** --include=/sbin --include=/sbin/** --include=/selinux --include=/selinux/** --include=/srv --include=/srv/** --exclude=/sys/** --exclude=/sys --exclude=/tmp/** --exclude=/tmp --include=/usr --include=/usr/** --include=/var --include=/var/** --exclude=** root@kepler+96:/. /home/backups/kepler/sync
```

---

### Post by HermanAB on 2018-05-09
Hmm... 'include, include, include, exclude...'
In general it is best to include everything and then exclude some generic things - that way you have a maintenance free script.

Regarding your actual problem - note that files have more than one time stamp, but normally you only see one.
[https://superuser.com/questions/387042/how-to-check-all-timestamps-of-a-file](https://superuser.com/questions/387042/how-to-check-all-timestamps-of-a-file)

---

### Post by Skaperen on 2018-05-12
a big script builds "the ludes list" from a rule list in a config file for each backup.  it is based on how rsync scans the ludes list in the order given.  for example, to exclude a small tree branch inside of a large tree branch that is included, that small branch exclude must be before the larger branch include.

from "man rsync" (emphasis is mine):

> As the list of files/directories to transfer is built, **rsync checks each name to be transferred against the list of include/exclude patterns _in turn_**, and the **_first matching_ pattern is acted on**: if it is an exclude pattern, then that file is skipped; if it is an include pattern then that filename is no skipped; if no matching pattern is found, then the filename is not skipped.

the -u or --update option is designated to enable checking of modification (see the man page)./

---

### Post by Skaperen on 2018-05-23
this issue is _unreproducible_.  unfortunately, there is no marker for that conclusion.  it is *not* solved.

---

### Post by ddunham on 2018-06-02
Run with the `-i` flag.  It's a lot more output, but when a file is copied that you don't understand why, it should show you a flag that explains the difference.

Such as:
[FONT=Courier New]sending incremental file list
>f..t...... /tmp/syncsrc/file[/FONT]

tells you that the contents of file are being sent (not just attribute updates)
the the file is a regular 'f'ile and
the modification 't'ime is being updated to the source.

So I know that rsync thought the time on the destination wasn't properly up-to-date.

---

