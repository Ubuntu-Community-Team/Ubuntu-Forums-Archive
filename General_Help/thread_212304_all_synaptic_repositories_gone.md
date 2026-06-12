---
title: "all synaptic repositories gone"
date: 2006-07-09
forum: General Help
---

### Post by guine on 2006-07-09
All of my repositories in synaptic have disappeared.  I was using automatix to try and get flash working properly and when it was done I told it to go back to the original source list and it did this and closed much faster than it had taken to close in previous times where I used automatix.  When I launched synaptic all of my repositories were gone and I couldnt find anything in synaptic to restore them.  Are there any other methods that I can use to restore my repositories?  Thanks.

---

### Post by tonyr on 2006-07-09
Yeah, Automatix screws up the repositories if any other package managing
process is running at the same time.  I filed a bug.

Look in the directory **/etc/apt**.  Automatix may actually have
created a backup copy in there.  Look for any files that start with
**sources.list**.  There may be some with a date number string on 
the end.

---

### Post by guine on 2006-07-09
Yeah, I have 2 backups there, is it possible to just replace my current list with one of the backups?

---

### Post by tonyr on 2006-07-09
Absolutamente!  You have to do it as root.  You can do it with root based **nautilus**es, or in a terminal with
**sudo cp /etc/apt/<backup-file>  /etc/apt/sources.list**

You can get a root based **nautilus** with ALT+F2, and entering
**gksudo nautilus**.

---

### Post by guine on 2006-07-09
k, that fixed the problem, thanks for the help

---

### Post by Laynix on 2006-07-09
I was having a similar problem.  When I tried to open the repositories in Synaptic, it flashed and went away.  My source.list file was not there, I just copied the backup and it works now.

Thanks tonyr!

---

