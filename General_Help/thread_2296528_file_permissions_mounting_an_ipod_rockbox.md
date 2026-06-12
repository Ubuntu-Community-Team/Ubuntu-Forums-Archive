---
title: "file permissions mounting an ipod rockbox"
date: 2015-09-26
forum: General Help
---

### Post by phoenix137 on 2015-09-26
[COLOR=#000000][FONT=Verdana]I am trying to access the files on an ipod rockbox on a kubuntu 14.04 system; but can only seem to do so as root as the mount command does not seem to pay any attention to the mounting options I give it.  [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I mount with: [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]sudo mount -t vfat /dev/sdc2 /media/wjason/Zen-Black/ -o rw,uid=1001,gid=1001,umask=000,dmask=000[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]My understanding is that this should mount a FAT system read/write with all files owned by user wjason (uid 1001) and group wjason (gid 1001) and such that file and directory permissions for owner, group, and others are read, write, and execute[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]and yet, ls -l shows these permissions:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]drwxr-xr-x 2 root root 4096 Nov 28  2010 Calendars[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]...[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]and for files on the device:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-rwxr-xr-x 1 root root 10704477 Sep 18 07:54 Bill Yosses _ Christine Kalafus.mp3[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Since the owner/group are still root and group and others do not have write permissions, I can only sync files to the rockbox as root.[/FONT][/COLOR]

---

### Post by yancek on 2015-09-26
> [COLOR=#000000][FONT=Verdana]the mount command does not seem to pay any attention to the mounting options [/FONT][/COLOR]

That's correct and is part of the default design of the system and is not likely to change.  FAT32 filesystems just don't deal with Linux permissions.  Change the owner:group and check the owner:group for the directory above:  /media/wjason.

---

### Post by phoenix137 on 2015-10-02
Did a software update and rebooted and now the issue is magically fixed.  The rockbox now mounts as the user:group I told it to and with the permissions I gave it.  :D

---

