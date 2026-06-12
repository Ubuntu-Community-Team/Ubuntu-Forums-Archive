---
title: "&quot;Fathom&quot; folders in /media/ from previously auto-mounted partitions"
date: 2008-04-04
forum: General Help
---

### Post by Splat on 2008-04-04
Hi,

Running v8.04 Beta. I have 4 drives/partitions that are auto-mounted to /media/ at startup: Data, Archive and two unnamed partitions.

```
$ cd /media/
$ ls -l
total 76
drwx------ 2 root root  4096 2008-04-04 02:15 Archive
drwx------ 2 root root  4096 2008-04-04 06:26 Archive_
drwxrwxrwx 1 root root  8192 2008-03-27 20:12 Archive__
lrwxrwxrwx 1 root  999     6 2008-03-29 06:15 cdrom -> cdrom0
drwxr-xr-x 2 root  999  4096 2008-03-29 06:15 cdrom0
drwx------ 2 root root  4096 2008-04-04 02:15 Data
drwx------ 2 root root  4096 2008-04-04 06:26 Data_
drwxrwxrwx 1 root root 16384 2008-03-27 20:12 Data__
drwx------ 2 root root  4096 2008-04-04 02:15 disk
drwx------ 2 root root  4096 2008-04-04 02:15 disk-1
drwx------ 2 root root  4096 2008-04-04 06:26 disk-2
drwx------ 2 root root  4096 2008-04-04 06:26 disk-3
drwxr-xr-x 5 user user   104 2008-02-25 17:42 disk-4
drwx------ 4 user root 16384 1970-01-01 01:00 disk-5
```

As you can see there are a bunch of "fathom" folders, apparently from previous startups/reboots. The correct ones (and the ones linked on the desktop) here are Data__, Archive__, disk-4 and disk-5 although they *should* be Data, Archive, disk and disk-1. The fathom folders are empty:

```
$ sudo ls -l ./Data/ 
total 0
```

Besides filling /media/ with junk, this breaks anything that references files on these drives (such as a playlist in a music player) since the names change on every startup/reboot. This didn't happen when I first installed Ubuntu, it just started today for no apparent reason. Possibly an update broke it?

The system didn't crash; this happened from normal shutdowns/restarts. I'm guessing something is going wrong after the partitions are unmounted and the folders aren't deleted? Or possibly they're not even being unmounted at all? I'm not too familiar with the automount/unmount process, so I can't say...

I could of course just delete them and everything should work fine on the next startup... but would break again on the one after that.

Any help or ideas appreciated. Thanks!

EDIT: Woops, just realized I posted this in General Help instead of in Development. Can't find a way to delete my own threads though and I don't want to just make a second one there. Could a mod move this if you see it, please?

[color=red]**EDIT2:**[/color] Just found [this thread](http://ubuntuforums.org/showthread.php?t=744469) on exactly the same subject. Since this is in the wrong section anyway, please reply there instead of here. If a mod sees this, could you please close this topic?

---

