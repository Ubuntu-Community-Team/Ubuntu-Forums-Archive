---
title: "Backup options"
date: 2007-02-15
forum: General Help
---

### Post by digilink on 2007-02-15
I have an Ubuntu 6.06 desktop and an Ubuntu 6.06 server with 100gb allocated to the /home directories. I am going to be setting up file serving on the server for backups for my wife and I using Samba and probably NFS. 

She is running a laptop with Windows XP Home edition. I would like the ability to backup some pre-defined directories on both her laptop as well as my Ubuntu desktop, and I'm not sure what the best tool for the job would be. 

Just curious if anyone out there is currently doing this and has some suggestions. I would like something that will only back stuff up if say, the contents of whatever directory I have chosen to backup has changed. If no changes, then nothing to backup for example. 

Any ideas?

---

### Post by brad.m.sims on 2007-02-15
> **digilink said:**
> I have an Ubuntu 6.06 desktop and an Ubuntu 6.06 server with 100gb allocated to the /home directories. I am going to be setting up file serving on the server for backups for my wife and I using Samba and probably NFS. 

She is running a laptop with Windows XP Home edition. I would like the ability to backup some pre-defined directories on both her laptop as well as my Ubuntu desktop, and I'm not sure what the best tool for the job would be. 

Just curious if anyone out there is currently doing this and has some suggestions. I would like something that will only back stuff up if say, the contents of whatever directory I have chosen to backup has changed. If no changes, then nothing to backup for example. 

Any ideas?

Hrm, rdiff-backup or rsync to an external hard drive is exactly what you want...
at least for the linux side

Both only copy changes, rdiff-backup will let you restore as of a set date...
rsync is just a mirror.

I havn't done the samba share thing myself but it shouldn't that hard to do.

Unison will work for both widnows and linux [http://www.cis.upenn.edu/~bcpierce/unison/download.html]("http://www.cis.upenn.edu/~bcpierce/unison/download.html")

---

