---
title: "Sshfs mount shows as different user"
date: 2014-04-20
forum: General Help
---

### Post by CaptainMark on 2014-04-20
I have my raspberry pi acting as a server for some documents and the home folder from it is mounted on my Ubuntu laptop under ~/Raspberrypi
when I use the ls -l command on the mounted directory it shows up as being owned by another user than it actually is, it doesn't seem to cause any real trouble as I still have read+write permissions but I was wondering what causes it and if it's an easy fix```
[22:13:11] mark@eeepc ~/Raspberrypi $ ls -l
total 28
drwxr-xr-x 1 lorraine 1002 4096 Apr 17 20:49 Desktop
drwxr-xr-x 1 lorraine 1002 4096 Jan 21 21:57 Documents
drwxr-xr-x 1 lorraine 1002 4096 Oct 12  2013 Downloads
drwxr-xr-x 1 lorraine 1002 4096 Oct  7  2013 Music
drwxr-xr-x 1 lorraine 1002 4096 Apr 18 09:44 Pictures
drwxrwx--- 1 lorraine 1002 4096 Apr 17 21:08 Torrents
drwxr-xr-x 1 lorraine 1002 4096 Oct  7  2013 Videos
[22:13:16] mark@eeepc ~/Raspberrypi $ ssh raspberrypi
Last login: Sun Apr 20 22:12:26 2014 from 192.168.1.103
Hello mark
Welcome to raspberrypi
The system has been running for 4 weeks 6 days and 6 hours
and was last updated on Saturday 19 April 2014


[22:13:23] mark@raspberrypi ~ $ ls -l
total 28
drwxr-xr-x  3 mark mark 4096 Apr 17 20:49 Desktop
drwxr-xr-x 11 mark mark 4096 Jan 21 21:57 Documents
drwxr-xr-x  2 mark mark 4096 Oct 12  2013 Downloads
drwxr-xr-x  2 mark mark 4096 Oct  7  2013 Music
drwxr-xr-x 14 mark mark 4096 Apr 18 09:44 Pictures
drwxrwx---  5 mark mark 4096 Apr 17 21:08 Torrents
drwxr-xr-x  2 mark mark 4096 Oct  7  2013 Videos

```

---

### Post by SeijiSensei on 2014-04-20
Unless both machines have identical /etc/passwd files, so that UIDs and usernames match, you'll see that result.  I'd copy /etc/passwd, /etc/group, and /etc/shadow from the server to each of the individual clients so they will all match.  Alternatively you can edit the copy on the machine that maps to lorraine.

If you use "ls -n" you'll see the UIDs and GIDs for each file/directory rather than the usernames.

---

### Post by CaptainMark on 2014-04-21
And thats all it was, thanks for helping me see what I should have noticed on my own

---

