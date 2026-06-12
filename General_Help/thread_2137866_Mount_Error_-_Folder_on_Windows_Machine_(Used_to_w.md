---
title: "Mount Error - Folder on Windows Machine (Used to work before upgrade)"
date: 2013-04-22
forum: General Help
---

### Post by Alan5127 on 2013-04-22
Hi,

I recently upgraded from Ubuntu 11.10 to 12.04 LTS.

Previously, I could use this command to mount a folder which resides on a Windows XP machine:

```
sudo mount -t cifs -o username=AlanWin,password={passwordonwindows},uid=alanub,gid=users //192.168.1.103/e/music /media/data2/shared/music
```

This worked flawlessly.

Now, since upgrading, it no longer works, and fails with this error message:

> mount: wrong fs type, bad option, bad superblock on //192.168.1.103/e/music,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

If I do a 'dmesg | tail', I get:

> [194953.056451] Key type cifs.idmap registered
[194953.056930] CIFS: no cache= option specified, using "cache=loose". This default will change to "cache=strict" in 3.7.
[194953.089119] CIFS VFS: Connecting to DFS root not implemented yet
[194953.090004] CIFS VFS: cifs_mount failed w/return code = -22
[194965.563680] CIFS VFS: Connecting to DFS root not implemented yet
[194965.563789] CIFS VFS: cifs_mount failed w/return code = -22
[194974.370932] CIFS VFS: Connecting to DFS root not implemented yet
[194974.371032] CIFS VFS: cifs_mount failed w/return code = -22
[195120.995636] CIFS VFS: Connecting to DFS root not implemented yet
[195120.995736] CIFS VFS: cifs_mount failed w/return code = -22

Neither of those is helping me much :-(

To the best of my knowledge, the only thing that has changed is that the Ubuntu machine has upgraded to 12.04 LTS.  I am as sure as I can be, that nothing has changed on the WinXP machine.

Also, I can browse to that directory on the Win machine from the file manager on Ubuntu and it works fine (as it did before too).

Can anyone help me diagnose the problem?

Thanks,

Alan.

---

### Post by Alan5127 on 2013-04-30
{Bumppity}

---

