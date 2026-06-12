---
title: "[SOLVED] Access C: drive via Wubi/Ubuntu installed on D:"
date: 2008-06-03
forum: General Help
---

### Post by oreomike on 2008-06-03
I installed Ubuntu on my D: drive via Wubi.  I can't see how to access my C: drive from within Ubuntu!  Help!  The only thing I see in /host is the contents of my D: drive.

me@laptop:/host$ ls -l
total 201
drwxrwxrwx 1 root root      0 2006-10-11 18:30 RECYCLER
drwxrwxrwx 1 root root   4096 2006-10-10 17:53 System Volume Information
drwxrwxrwx 1 root root   4096 2008-06-03 16:02 ubuntu
-rwxrwxrwx 1 root root     26 2008-06-03 14:12 wep.txt
-rwxrwxrwx 1 root root 186463 2008-04-22 09:57 wubildr
-rwxrwxrwx 1 root root   8192 2008-04-22 09:57 wubildr.mbr

me@laptop:/media$ ls -l
total 4
lrwxrwxrwx 1 root root    6 2008-06-03 12:14 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-06-03 12:14 cdrom0

---

### Post by oreomike on 2008-06-03
UPDATE:

Just found, under Places, a reference to 86GB Media, and when I click on it, Ubuntu mounts the drive as /media/disk.

So ignore my request.  Guess I'll leave this here for someone else who has the same problem!

---

