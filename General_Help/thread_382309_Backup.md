---
title: "Backup"
date: 2007-03-11
forum: General Help
---

### Post by MadMac on 2007-03-11
Howdy!

I need some assistance.  I have tried sbackup and bacula, along with a couple of others, and I am still not able to find a backup program that will simply do a simple backup to a cd/dvd.  ](*,) 

Anyone have a recommendations for a simple backup program that backs up to cd/dvd?

Thanks!

---

### Post by yabbadabbadont on 2007-03-11
You might look into using dar.

---

### Post by yabbadabbadont on 2007-03-11
Also, have you seen this?  [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Marsolin on 2007-03-11
There is also a graphical version of dar called [KDar]("http://linuxappfinder.com/package/kdar").

---

### Post by MadMac on 2007-03-12
Gad, I feel like such a goof.  I neglected to say that I am running Ubuntu 6.10 with the basic Gnome desktop.

Thanks for the good replies, but I can't seem to get any of them to write to cd/dvd, only to a directory/hard drive.  I don't really want to use tar or kde unless absolutely necessary (I have enough problems already  :) ).

Thanks anyway!

Any more good ideas, though?

---

### Post by Marsolin on 2007-03-12
> **MadMac said:**
> Gad, I feel like such a goof.  I neglected to say that I am running Ubuntu 6.10 with the basic Gnome desktop.

Thanks for the good replies, but I can't seem to get any of them to write to cd/dvd, only to a directory/hard drive.  I don't really want to use tar or kde unless absolutely necessary (I have enough problems already  :) ).

Thanks anyway!

Any more good ideas, though?

Run KDar from within Gnome. It doesn't need KDE.

An alternative not in the repos is [pyBackPack]("http://linuxappfinder.com/package/pybackpack").

[CDBackup]("http://linuxappfinder.com/package/cdbackup") and [Cedar Backup]("http://linuxappfinder.com/package/cedar-backup2") are two more command line options.

---

### Post by rebootme on 2007-12-08
I have had very good results with Mondo.  It is very flexible.  One option is to backup your whole system to ISO files that can be burned to DVD or CD.  I have used it to do a bare metal restore and it worked flawlessly.

To install ```
sudo apt-get install mondo
```

See [http://www.mondorescue.org/]("http://www.mondorescue.org/") for more info.

---

