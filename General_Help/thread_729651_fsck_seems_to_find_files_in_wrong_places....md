---
title: "fsck seems to find files in wrong places..."
date: 2008-03-20
forum: General Help
---

### Post by effort on 2008-03-20
Hi all,

Running software raid over three Samsung Spinpoint 500GB drives in raid5, using a Silicon Image 3114 SATA controller. I've got a partition on the raid formatted as JFS. It's always behaved rather oddly, shedding files every day or so, but I assumed that was due to files copied from a failing drive. But recently it's been doing something odd. 

The raid drive /dev/md0 is mounted as /raid. Every few day or so, I get the error 

[FONT="Courier New"]ERROR: (device md0): JFS:Dtree error: ino = 217248, bn=0, index = 2[/FONT]

at about half six in the morning, so am assuming problems are being unearthed by something in cron.daily. But when I run a read-only fsck to check what's been going on, I get this:

[FONT="Courier New"]rich@futility:~$ sudo fsck -n /dev/md0
fsck 1.40.2 (12-Jul-2007)
fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 3/20/2008 8.19.35
Filesystem is currently mounted.
WARNING: Checking a mounted filesystem does not produce dependable results.
The current device is:  /dev/md0
Block size in bytes:  4096
Filesystem size in blocks:  244191968
**Phase 1 - Check Blocks, Files/Directories, and  Directory Entries
**Phase 2 - Count links
Incorrect link counts detected in the aggregate.
**Phase 3 - Duplicate Block Rescan and Directory Connectedness
**Phase 4 - Report Problems
File system object FF78040 is linked as: /music/chris/Compilations/Oh What A Night Disc 2/desktop.ini
cannot repair the data format error(s) in this file.
cannot repair FF78040.
File system object FF86215 is linked as: /music/chris/e/Emerson, Lake & Palmer/The Best Of Emerson, Lake And Palmer [UK]/04 - Fanfare For The Common Man - Emerson, Lake & Palmer.mp3
cannot repair the data format error(s) in this file.
cannot repair FF86215.
File system object FF86232 is linked as: /music/chris/e/Elvis Presley/30 #1 hits/desktop.ini
cannot repair the data format error(s) in this file.
cannot repair FF86232.
**Phase 5 - Check Connectivity
**Phase 6 - Perform Approved Corrections
**Phase 7 - Verify File/Directory Allocation Maps
Errors detected in the Fileset File/Directory Allocation Map control information. (F)
**Phase 8 - Verify Disk Allocation Maps
Incorrect data detected in disk allocation structures.
Incorrect data detected in disk allocation control structures.
976767872 kilobytes total disk space.
    24966 kilobytes in 4069 directories.
717672806 kilobytes in 68924 user files.
        8 kilobytes in extended attributes
  1995836 kilobytes reserved for system use.
257124188 kilobytes are available for use.
File system checked READ ONLY.
ERRORS HAVE BEEN DETECTED.  Run fsck with the -f parameter to repair.
Filesystem is dirty.
Filesystem is dirty but is marked clean.  In its present state,
the results of accessing /dev/md0 (except by this utility) are undefined.[/FONT]

The music files you see above in /music/chris are actually present in /raid/music/chris.

What's going on? I upgraded to version 2.6.4 of mdadm and 1.1.12 of jfsutils to try to stop my raid shedding files, but this seems to be causing problems too.

The drives have been badblocksed for a day and my machine has been memtested for a day also. I run bonnie for six hours to check the raid was fine. I'm not sure what's going on to cause me to keep losing files in this bizarre way.

---

### Post by fjgaude on 2008-03-20
I believe you problem is caused by fsck doing its work on a mounted filesystem.

You should** never** check files on a mounted system. Unmount then check. What you have done could have caused lots of little issues with the file structure.

**Hope you have a full backup of all files on raid5 arrays.**

Arrays can fail, drives can fail... make backups.

---

### Post by effort on 2008-03-20
Really? Running fsck -n on a mounted filesystem could cause problems? Didn't read that anywhere. Guess some people (me) get to learn things the hard way...

---

### Post by fjgaude on 2008-03-20
Well, I guess I didn't notice the -n... maybe you are okay. But likely you have a bad drive, one going bad anyway.

My own feelings about fsck is I never use it on a mounted partition, period.

---

