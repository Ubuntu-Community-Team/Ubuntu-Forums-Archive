---
title: "Backup software similar to Backup Exec?"
date: 2007-07-25
forum: General Help
---

### Post by dmorlow on 2007-07-25
Hi, I'm looking for a way to backup my data similar to the GUI of Backup Exec.  I like how I can just choose what folders to backup.  It's too much work to use TAR because I have to write out each folder, the whole path.    I tried to use TAR to backup my profile, and the file was 40 GB.  Some of the GUI one's I've seen so far, if you select a parent folder, you cannot deselect a child folder if you don't want to backup every single child folder of a parent folder.  I need to use something GUI so I can go down and individually pick what folders I'm backing up.

---

### Post by dando80 on 2007-07-28
Kdar is pretty good. It does compression, encryption, splitting of archives, incremental backups and allows you to save your backup profile so you can easily run the same backup again in the future.

apt-get install kdar

This will install some KDE libraries if they aren't already installed. Unfortunately I haven't seen anything as good for gnome. Have had no luck with sbackup. Doesn't ever seem to work :-)

---

### Post by wieman01 on 2007-07-28
Unison and the GTK GUI would be an option as well. I use it and find it quite convenient & easy to use.

[http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html]("http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html")

---

### Post by Koybe on 2007-07-28
BackupPC is a nice soft too. Managed trough a web interface.
[http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)

---

### Post by az on 2007-07-28
Hubackup does not allow you to pick child folders, but it is smart enough to be able to do a sync backup, which means it will update the backup image with new files and remove deleted files.  Is that useful?

---

