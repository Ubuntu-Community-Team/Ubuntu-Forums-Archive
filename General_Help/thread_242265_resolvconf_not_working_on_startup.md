---
title: "resolvconf not working on startup"
date: 2006-08-23
forum: General Help
---

### Post by Elephantium on 2006-08-23
After installing, I added a second, larger hard drive to my Ubuntu box.  I figured that having more space for /var would be useful, so I created /mnt/var, mounted it on /dev/hda2, and then copied all my files in /var to /mnt/var.

Then, I made a backup copy of /var to /var.old and replaced /var with a symlink to /mnt/var (this part was done after doing init 1).

Now, resolvconf fails to work properly at startup.  It complains about "mkdir:  Unable to create /var/run/network"

A couple of other things fail, too, including mysqld - which breaks the applications I'm trying to run on this server.

Does anyone have any hints on getting resolvconf working again?  It looks to me like several processes are trying to access /var before it actually points to anything.

---

