---
title: "Better backup than Redo"
date: 2016-12-03
forum: General Help
---

### Post by Jack_Shankle on 2016-12-03
I am a windows user helping wiffie on her Ubuntu mate OS.
Is there a better backup program than REDO???
Please don't be technical as I am an Ubuntu novice.

Stats:
  Ubuntu mate
  Redo livecd-1.0.4.iso

I want to backup to an external HD. It does this but puts
the backup in the wrong place.
Also verify ought to be automatic and it isn't.
Thanks for Ubuntu and this forum.

---

### Post by oldrocker99 on 2016-12-03
Grsync is in the repos, and it's what I use. Just set the source as /home/username and the destination as whatever your external drive is called (/media/username/drivename, **not** Drivename/username. It works like a charm, and after the first backup, it only copies new or changed files.

---

### Post by RobGoss on 2016-12-03
Hello and welcome, I use **Clonezilla **it's great if you need to image the whole system and or different parts of your partitions. There are a lot of different options so you'll have to see what works for you [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Jack_Shankle on 2016-12-03
Thanks Roc Goss for your reply.
I used Clonezilla-live for years. It works ONLY if you go from a smaller disk to a larger disk.
EX: I backup to a 1T hd. Recently I bought a 256G SSD. When I tried to restore from the 1T hd
Clonezilla-live through a fit. Consequently I dumped Clonezilla. Be Warned...... 

To: Thanks  OldRocker,
I don't want differential backups.
I like to image the entire file every time I do a backup.
Sounds like your suggestion won't work.

---

