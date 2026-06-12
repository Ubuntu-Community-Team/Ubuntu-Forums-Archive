---
title: "How do I switch to a mounted drive?"
date: 2006-11-26
forum: General Help
---

### Post by Kittie Rose on 2006-11-26
I've currently got a terminal running but I can't figure this out. I've never had to do it before in any other linux distro for that matter.

PSP7 won't run in WINE and it's meant to so I want to try and find out why.

---

### Post by dmartinsca on 2006-11-26
Generally, mounted drives in ubuntu appear as a directory in the /media directory.

To get there from a terminal and view the mounted drives, run:

```
cd /media
ls
```

This will show the contents of the /media folder. Use the cd command again to go to the drive you want.

I take it you are trying to run a program which is already installed in windows using WINE? What filesystem is your windows installed on, NTFS or FAT32?

I ask because linux cannot write to NTFS drives so running PSP7 which is already installed on a NTFS drive isn't going to work.

What you should do is install PSP7 again using wine. This will install it to a folder in your home directory and that way linux will be able to alter it's files.

If you are still stuck trying to access your windows drive, post the output of:
[B]
sudo fdisk -l[/B]
and
**mount**

(Run from a terminal)

---

