---
title: "Whats a real good backing up software?"
date: 2008-02-07
forum: General Help
---

### Post by Baarhisveiki on 2008-02-07
Hi all,

Since my pc is getting clogged with masses of pics and homemovies (and since the same pc running on linux is gettin older and older) we wanted to buy an external hard disk drive to make regular backups. I bought one on a sale, the infamous Maxtor Onetouch4... .
Regardless the fact it took me a while to get it mounted by Ubuntu i dont really trust the software thats allready on this Maxtor external drive (even while i am pretty sure it will work with wine)... .

So has anyone used this maxtor software? What do you think of it?
I could of course use another third party software but then...has anyone a recomendation. Preferably a free software but if another one non free is better pleaze share your experiences with me.

Thnx,

---

### Post by Keith Hedger on 2008-02-07
I have been using  dump/restore for three years now and it works like a charm its in the rpos

---

### Post by fictivetoast on 2008-02-07
Flyback has been working very well for me.  It's fairly user friendly, and seems stable enough for regular use.  It uses a linking scheme instead of backing up EVERYTHING you've got - so if you take a second snapshot of your photos a week later, it'll link to the ones already backed up and only create new copies of what's actually changed, saving a lot of space.  See:
[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

It's not in the Repos, but to install, open a terminal and try : 

```
sudo apt-get install python python-glade2 python-gnome2 python-sqlite3 python-gconf rsync

svn checkout http://flyback.googlecode.com/svn/trunk/ flyback
```

Then CD into the directory and type "python flyback.py"

(If you like it and want to use it regularly, you can make a simple little bash script to execute "pathto/python flyback.py" and then make a launcher linking to that like any other program.)

Alternatively, Timevault looks very interesting... but at the moment, I've heard it's not really stable for regular use.  Also, there don't seem to be any debs for 64-bit, and I've had no luck finding the newest beta source to build it.  If you're curious though, it's at:
[https://launchpad.net/timevault/+download](https://launchpad.net/timevault/+download)

---

### Post by sancho panza on 2008-02-07
Check this thread: [http://ubuntuforums.org/showthread.php?t=592445]("http://ubuntuforums.org/showthread.php?t=592445")

---

### Post by macogw on 2008-02-07
I just want to point out that if you're removing them from the computer and keeping them only on the external, that's archiving, not backing up.  You still only have one copy of the data then, so if the disk goes, it's still gone.  Backing up means you have redundancy.

I use cron + rsync to backup.  Just write a little script (which pretty much just means you put #!/bin/bash on the first line and your rsync command on the second and save it) then in /etc/cronttab put the user as root and list the path to wherever the script is located and tell it to run when you want.  At work, I set it for every night at midnight (so * in the dom [Day of Month], dow [Day of Week], mon [Month] and 0 in m [minute] and h [hour]... so 00:00 every day).   That would run the rsync script (which I'd just put as /usr/local/bin/backup.sh) every night at midnight.

Rsync is nice because it can go over the internet using ssh keys if you want to backup remotely (so that if your house burns down, the backup is off-site).  That's not really necessary for most people, but businesses like it.  It can be customized to only backup certain directories, of course.  The first time it runs takes a while because it copies *everything*.  Each subsequent run, though, is very fast.  It just updates the last backup to match your system's current state.  You can set it to not delete things which were deleted from your computer too, so that if you accidentally delete things you can get them back (though then you might want a bigger disk to hold all the undeleted stuff).  I'm pretty sure you can also tell it to not delete files that have been deleted unless they were deleted over a month ago or something like that.  I haven't done anything that complicated with it, but I'm pretty sure, from looking through the manpage, that it's possible.

---

### Post by Baarhisveiki on 2008-02-08
Thanks for the tip!

---

### Post by Het Irv on 2008-02-08
The QuickStart Link in my sig is a nice program that I use.

---

### Post by newlinux on 2008-02-08
I use an rsync script with a daily cron as well. Once a week I purge files that have been deleted on the source from the backup and I have it log what happened in a log file each night (I keep a month of history). If you don't want a script and just want to do this periodically grsync is a good graphical frontend to rsync.

---

