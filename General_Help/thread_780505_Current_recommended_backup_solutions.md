---
title: "Current recommended backup solutions?"
date: 2008-05-03
forum: General Help
---

### Post by gstuart on 2008-05-03
Hello - I am currently backing up my system (Ubuntu 6.06 LTS, ...) using a rsync-based solution (rsnapshot).

I am about to purchase a new system; I plan to do a fresh install (Ubuntu 8.04 LTS), then migrate my current profile, files, etc. to the new computer.

Regarding my backups, what do people recommend, currently?  At this time I am backing up (via rsnapshot) to a second hard drive, but I'm willing to consider other options.

I'm aware of - but unfamiliar with - RAID; is RAID commonly used (e.g., in a home setting)?  How is it implemented; it is worth the "trouble?"

Thank you, appreciated!  Greg   :-)

---

### Post by damis648 on 2008-05-03
Well for me i just copy / paste the files to an ext drive, however to make this automated i use [http://code.google.com/p/flyback/](http://code.google.com/p/flyback/) (flyback). This works similarly to apple's time machine. I just back up every day with it so if i upgrade or something i can just restore from these backups.

---

### Post by p_quarles on 2008-05-03
RAID can be used in a home setting, sure, but it's not really a backup solution. It is useful for redundancy in case of *physical* hard drive failure, but will not help (as I understand it) with anything involving software or user errors. 

rsync based solutions, using external storage media/servers, are pretty much the standard way to back up data.

edit: Flyback, mentioned in the previous post, is a good one too. It's just a Python front-end for rsync, though, so it shouldn't have any huge advantages or disadvantages when compared with rsnapshot.

---

### Post by idipous on 2008-05-03
Using a raid in home setup is a bit extravagant. It is prefered for business enviroments. What I would suggest is getting an external usb disk and mount it (i.e /mnt/mybackupdrive). Then use cron (crontab files) and tar to back up your data and settings. There are many graphical tools as well. 

Check: [http://www.desktoplinux.com/articles/AT2280165098.html](http://www.desktoplinux.com/articles/AT2280165098.html)

and give the command man crontab and cron. 

Is is really very simple.

---

