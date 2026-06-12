---
title: "back up/sync help"
date: 2008-01-22
forum: General Help
---

### Post by mickfitz on 2008-01-22
Hello

Since loosing a large amount of data a few years back I have become paranoid and probably go OTT with backing up :)

On my home network is a 300gig network drive. On the XP boxes I use a superb freeware proggie called AlwaySync that sync's all the XP PC's with the network drive.

I am hoping to achieve something similar with the Ubuntu box. Is it possible to do this with Ubuntu?

Many thanks in advance ... Mick

---

### Post by wolfen69 on 2008-01-22
a quick search of "backup" in synaptic yielded many results. start there.

---

### Post by gvartser on 2008-01-22
I use sbackup "Simple Backup", works perfectly for backing up the system.

#) sudo apt-get install sbackup

Best Regz,
/G

---

### Post by mickfitz on 2008-01-22
Many thanks for that ... will it also synchronise folders?

Also ... I'm fairly new to ubuntu and not sure what you mean with:

#) sudo apt-get install sbackup

Mick

---

### Post by gvartser on 2008-01-22
"sudo apt-get install sbackup" is the way to install sbackup from a shell, you could also do it using synaptic.

To synchronize folders, take a look at rsync.

Best regz,
/robban

---

### Post by spupy on 2008-01-22
Rsync is a very good program. But since you asked what the "sudo apt-get.." command means, i guess you are new to the terminal. Since rsync has a HUGE ammount of options, take a look at **grsync**. It is a simple graphical frontend to rsync, not bloated, the basic/important options.
EDIT: When you want to sync, you must run the program manualy (grsync or another). To schedule automatic syncing, you will need to use cron, but that is another story...

---

