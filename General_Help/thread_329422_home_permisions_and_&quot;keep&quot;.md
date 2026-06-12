---
title: "home permisions and &quot;keep&quot;"
date: 2007-01-01
forum: General Help
---

### Post by t1m on 2007-01-01
Hi, this his is my first post here but I have been using (K)ubuntu for about a year or so.

I recently switched my backup program from rsnapshot to "keep". I told it up to backup the /home/ and /var/www/ directories to "/keep_backups/". All goes well until it starts to backup /home/. It only backups some configuration files (I think that's what they are) but not really anything "important". The keep "log" Has lots of "backup "error"s in it. I noticed that the /var/www/ backup works and that everyone (user group and others) "can View & Modify Content". The /home/ file is only "viewable", and the /home/tim (my username) is modifyable by only me. I tried to make all the files in /home/ have read/write permisions but then I can't login becuase certain files (gnome/kde "preferences") need to be only readable (I'm gessing).
Anyway because of all this permision stuff most of the home directory doesn't get backed up :( 

Anyone else able to get their /home/ files backed up with keep?

Tnx

[SIZE="1"]
-------
GO UBUNTU [/SIZE]

---

### Post by thelocust on 2007-01-01
**Try running Keep as root.**

---

### Post by t1m on 2007-01-03
Thanks for the reply. I tried that and it still didn't work.
Just now I went to the backup settings and told it not to exclude special files. I'll see if that works next time it does a backup.

;)

---

### Post by t1m on 2007-01-08
Bugger! Still isn't working. I viewed "backup.log" in the "rdiff-backup-data" folder and noticed that all the errors say "permision denied". :( 

Anyone no a way aroud?

---

