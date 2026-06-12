---
title: "File monitor and backup"
date: 2008-01-23
forum: General Help
---

### Post by reets on 2008-01-23
Is there a program that will monitor a specified directory (and/or sub directories) for changes to the files and automatically make a new backup or revision copy of that file? I don't want anything like SVN or CVS, I just need something super lightweight, gui would be nice but not required, and relatively easy to use. (FileHamster for windows is a good example of this).

---

### Post by mocoloco on 2008-01-24
Check out simple backup/restore, you can find it in Add/Remove or Synaptic. [http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html]("http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")
I believe it uses rsync on the back end, so you could schedule it for every hour without too much of a hit on resources.
Or if you want to go command line just user rsync itself, it's very powerful with lots of options.

---

### Post by reets on 2008-01-24
I need something for on-the-fly. Like if I am coding or something and save the file, it automatically notices the changed file and makes a copy of it in another folder with a timestamp of some sort.

Thank you for the suggestion though, I am looking into rsync further.

---

### Post by mocoloco on 2008-01-24
There may or may not be existing apps that will do that, but you could easily write a script that checks for changes in a certain folder, then kicks of rsync if there are any.  Put it in cron to run every minute and you're set.

---

