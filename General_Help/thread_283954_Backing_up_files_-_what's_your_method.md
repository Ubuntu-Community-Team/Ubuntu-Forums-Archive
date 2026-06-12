---
title: "Backing up files - what's your method?"
date: 2006-10-24
forum: General Help
---

### Post by neumeka on 2006-10-24
Now that I use my ubuntu machine for all of what I consider my important files - pictures, documents, emails, etc., I need to start backing them up.  I'd also like to start backing up settings too, like .bachrc and .vimrc files and such. I am just curious about the various ways/tricks/programs that people in this forum use to back up their files.

---

### Post by aysiu on 2006-10-24
I use *rsync* to back up.

---

### Post by matthewstory on 2006-10-24
I use a bash script in /etc/cron.daily to make a backup - mysql, svn, etc - and then tar them up with gz compression, and using a pre-defined key I sftp them to a remote server.

---

### Post by neumeka on 2006-10-25
I am specifically wanting to backup to a DVD...maybe once a week.  I'd like to backup only the files that haven't been modified since the last back up. But I am open to any clever ideas.

---

### Post by firebadger on 2006-10-25
Nice incremental backups - only stores the differences...

[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

---

### Post by scrook on 2006-10-25
If you haven't already tried this, check out Sbackup. It was a project sponsored by Ubuntu for Google's summer of code. It has a nice front end for doing incremental backups on a regular schedule. I don't know if it has an option to make DVD sized chunks since I backup to an external hard drive.

You can find Sbackup in the Dapper and Edgy repos I don't know about earlier versions of Ubuntu.

Scott

---

### Post by skymt on 2006-10-25
My backup method? tar, of course! With a shell script, so I don't have to do it manually. It's a bit old school, but it's simple and it works.

---

