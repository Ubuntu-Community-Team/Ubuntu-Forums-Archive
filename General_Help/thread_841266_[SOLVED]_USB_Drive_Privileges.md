---
title: "[SOLVED] USB Drive Privileges"
date: 2008-06-26
forum: General Help
---

### Post by stevanbt on 2008-06-26
Hi,
I'm having trouble with privileges when mounting my camera via USB.  When I plug in the camera via USB it shows up as a drive and I can view/edit the pictures - no problem.

However, when my wife wants to use the pc and does a switch user she can see the drive but cannot view the pictures.  I'm not at the pc now, but I think the drive is mounted ```
-rw------
```.

The minor complication is that the pc is actually running Mythbuntu (but I don't think this is a Mythbuntu specific issue), I can't log myself off the pc as Mythbackend is running under my user session.

I don't have any entries for this drive in /etc/fstab - and I don't think I need any.  The best solution for me would be that the drive is mounted -rw-rw-rw.

Thanks in advance, Steve.

---

### Post by chrisccoulson on 2008-06-26
What happens if you unmount the drive, switch user, and then get your wife to mount the drive?

When you plug in the drive, it is mounted on your behalf. If you do a 'ls -l /media', you should see that your user owns the mount, and the group should be plugdev. However, permissions should be read-write for both the user who mounted it and the plugdev group (I think), meaning that anyone belonging to plugdev can read and write to it. 

There is a gconf key for specifying mount options for automatically mounted volumes. Can't remember what it is at the moment, so I'll check when I get home. Maybe there is something there which is causing your problem.

---

### Post by stevanbt on 2008-06-26
Hi,
Previously I thought I'd connected the camera when my wife was logged on - but I can't have... I've just done it and it's mounted as :-
```

drwx------ 4 sam  root 16384 1970-01-01 01:00 disk

```

Thanks for your help, Steve.

---

